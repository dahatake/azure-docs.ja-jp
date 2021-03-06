---
title: Azure と Azure Stack でハイブリッド クラウド接続を構成する | Microsoft Docs
description: Azure と Azure Stack でハイブリッド クラウド接続を構成する方法について説明します。
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
editor: ''
ms.service: azure-stack
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.date: 05/07/2018
ms.author: mabrigg
ms.reviewer: Anjay.Ajodha
ms.openlocfilehash: 048e2636aabe406728c8fe1b93ef861f13346256
ms.sourcegitcommit: 909469bf17211be40ea24a981c3e0331ea182996
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="tutorial-configure-hybrid-cloud-connectivity-with-azure-and-azure-stack"></a>チュートリアル: Azure と Azure Stack でハイブリッド クラウド接続を構成する

*適用先: Azure Stack 統合システムと Azure Stack 開発キット*

ハイブリッド接続パターンを使用して、グローバル Azure および Azure Stack 内のリソースに安全な方法でアクセスできます。 

このチュートリアルでは、以下を実現するためのサンプル環境を構築します。

> [!div class="checklist"]
> - プライバシーまたは規制要件に合わせてデータをオンプレミスで保管する一方で、グローバル Azure のリソースにアクセスする。
> - グローバル Azure のクラウド スケールのアプリのデプロイとリソースを使用しながら、レガシー システムを維持する。

## <a name="prerequisites"></a>前提条件

ハイブリッド接続のデプロイを構築するにはいくつかのコンポーネントが必要で、準備に多少時間がかかることがあります。 

Azure OEM/ハードウェア パートナーは、運用 Azure Stack をデプロイできます。すべてのユーザーは、ASDK をデプロイできます。 さらに、Azure Stack オペレーターは、App Service のデプロイ、プランとオファーの作成、テナント サブスクリプションの作成、および Windows Server 2016 イメージの追加を行う必要があります。 

これらのコンポーネントの一部を既に持っている場合は、開始する前にそれらが要件を満たしていることを確認してください。

このトピックは、Azure と Azure Stack について一定の知識があることを前提にしています。 続行する前に知識を深めておく場合は、以下の各トピックから開始するようにしてください。
 - [Azure 入門](https://azure.microsoft.com/overview/what-is-azure/)
 - [Azure Stack の主要概念](https://docs.microsoft.com/azure/azure-stack/azure-stack-key-features)

### <a name="azure"></a>Azure
 - Azure サブスクリプションをお持ちでない場合は、開始する前に [無料アカウント](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) を作成してください。
 - Azure で [Web アプリ](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/aspnet-core-to-azure-webapp?view=vsts&tabs=vsts#create-an-azure-web-app-using-the-portal)を作成します。 後で使用するため、新しい Web アプリの URL を書き留めておきます。

### <a name="azure-stack"></a>Azure Stack
 - 運用 Azure Stack を使用するか、以下にリンクされている Azure Stack Development Kit をデプロイします。
    - https://github.com/mattmcspirit/azurestack/blob/master/deployment/ConfigASDK.ps1 
    - 通常、インストールが完了するまで数時間かかるため、それに応じて計画を立ててください。
 - [App Service](https://docs.microsoft.com/azure/azure-stack/azure-stack-app-service-deploy) PaaS サービスを Azure Stack にデプロイします。 
 - Azure Stack 環境内で[プラン/オファーを作成](https://docs.microsoft.com/azure/azure-stack/azure-stack-plan-offer-quota-overview)します。 
 - Azure Stack 環境内で[テナント サブスクリプションを作成](https://docs.microsoft.com/azure/azure-stack/azure-stack-subscribe-plan-provision-vm)します。 


### <a name="before-you-begin"></a>開始する前に

構成を開始する前に、以下の条件を満たしていることを確認します。

 - VPN デバイスの外部接続用パブリック IPv4 アドレスがあることを確認します。 この IP アドレスを NAT の内側に割り当てることはできません。
 - すべてのリソースが同じリージョン/場所にデプロイされていることを確認します。

#### <a name="example-values"></a>値の例

この記事の例では、次の値を使用します。 この値を使用して、テスト環境を作成できます。また、この値を参考にしながら、この記事の例を確認していくこともできます。 VPN ゲートウェイの一般的な設定の詳細については、[VPN Gateway の設定](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings)に関するページを参照してください。

接続の仕様:
 - **VPN の種類**: ルート ベース
 - **接続の種類:** サイト対サイト (IPsec)
 - **ゲートウェイの種類**: VPN
 - **Azure 接続名**: Azure-Gateway-AzureStack-S2SGateway (この値はポータルによって自動入力されます)
 - **Azure Stack 接続名**: AzureStack-Gateway-Azure-S2SGateway (この値はポータルによって自動入力されます)
 - **共有キー**: VPN ハードウェアと互換性があり、接続の両側で値が一致していること
 - **サブスクリプション**: 任意のサブスクリプション
 - **リソース グループ**: Test-Infra

| Azure/Azure Stack 接続 | Name | サブネット | IP アドレス |
|-------------------------------------|---------------------------------------------|---------------------------------------|-----------------------------|
| Azure vNet | ApplicationvNet<br>10.100.102.9/23 | ApplicationSubnet<br>10.100.102.0/24 |  |
|  |  | GatewaySubnet<br>10.100.103.0/24 |  |
| Azure Stack vNet | ApplicationvNet<br>10.100.100.0/23 | ApplicationSubnet <br>10.100.100.0/24 |  |
|  |  | GatewaySubnet <br>10.100101.0/24 |  |
| Azure 仮想ネットワーク ゲートウェイ | Azure-Gateway |  |  |
| Azure Stack 仮想ネットワーク ゲートウェイ | AzureStack-Gateway |  |  |
| Azure パブリック IP | Azure-GatewayPublicIP |  | 作成時に決定されます |
| Azure Stack パブリック IP | AzureStack-GatewayPublicIP |  | 作成時に決定されます |
| Azure ローカル ネットワーク ゲートウェイ | AzureStack-S2SGateway<br>   10.100.100.0/23 |  | Azure Stack パブリック IP 値 |
| Azure Stack ローカル ネットワーク ゲートウェイ | Azure-S2SGateway<br>10.100.102.0/23 |  | Azure パブリック IP 値 |

## <a name="create-a-virtual-network-in-global-azure-and-azure-stack"></a>グローバル Azure および Azure Stack に仮想ネットワークを作成する

> [!Note]  
> Azure または Azure Stack の vNet アドレス空間に IP の重複がないことを確認する必要があります。 

Azure portal を使用して Resource Manager デプロイ モデルで vNet を作成します。 これらの手順をチュートリアルとして使用する場合は、[例として示されている値](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal#values)を使用してください。 これらの手順をチュートリアルとして使用しない場合は、必ず独自の値に置き換えてください。 

1. ブラウザーから [Azure ポータル](http://portal.azure.com/) に移動し、Azure アカウントでサインインします。
2. **[リソースの作成]** をクリックします。 **[Marketplace を検索]** フィールドに「`virtual network`」と入力します。 検索結果の一覧から **[仮想ネットワーク]** を探し、**[仮想ネットワーク]** ページを開きます。
3. [仮想ネットワーク] ページの下の方にある **[デプロイ モデルの選択]** の一覧で、**[リソース マネージャー]** を選択し、**[作成]** を選択します。 [仮想ネットワークの作成] ページが開きます。
4. **[仮想ネットワークの作成]** ページで、VNet の設定を構成します。 フィールドへの入力時、入力された文字が有効であれば、赤色の感嘆符が緑色のチェック マークに変わります。
5. Azure Stack の**テナント ポータル**からこれらの手順を繰り返します。

## <a name="add-a-gateway-subnet"></a>ゲートウェイ サブネットの追加

仮想ネットワークをゲートウェイに接続する前に、まず、接続先の仮想ネットワークのゲートウェイ サブネットを作成する必要があります。 ゲートウェイ サービスでは、ゲートウェイ サブネット内に指定された IP アドレスを使用します。

[ポータル](http://portal.azure.com/)で、仮想ネットワーク ゲートウェイを作成する Resource Manager 仮想ネットワークに移動します。

1. VNet のページの **[設定]** セクションで、**[サブネット]** を選択して **[サブネット]** ページを展開します。
2. **[サブネット]** ページで **[+ゲートウェイ サブネット]** を選択して **[サブネットの追加]** ページを開きます。

    ![](media/azure-stack-solution-hybrid-connectivity/image4.png)

3. サブネットの **[名前]** には、"GatewaySubnet" という値が自動的に入力されます。 この値は、Azure がゲートウェイ サブネットとしてこのサブネットを認識するために必要になります。 自動入力される **[アドレス範囲]** の値を実際の構成要件に合わせて調整し、ページの下部にある **[OK]** を選択してサブネットを作成します。

## <a name="create-a-virtual-network-gateway-in-azure-and-azure-stack"></a>Azure および Azure Stack に仮想ネットワーク ゲートウェイを作成する

1. ポータル ページの左側にある [+] を選択し、検索ボックスに「仮想ネットワーク ゲートウェイ」と入力します。 **[結果]** から **[仮想ネットワーク ゲートウェイ]** を探して選択します。
2. **[仮想ネットワーク ゲートウェイ]** ページの下部にある **[作成]** を選択します。 **[仮想ネットワーク ゲートウェイの作成]** ページが開きます。
3. **[仮想ネットワーク ゲートウェイの作成]** ページで、「値の例」と次に説明する追加の値を参考にして、仮想ネットワーク ゲートウェイの値を指定します。
    - **[SKU]**: Basic
    - **[仮想ネットワーク]**: 前に作成した仮想ネットワークを選択します。 前に作成したゲートウェイ サブネットが自動的に選択されます。 
    - **[最初の IP 構成]**: これが、ゲートウェイのパブリック IP です。 
        - **[ゲートウェイ IP 構成の作成]** をクリックします。**[パブリック IP アドレスの選択]** ページが開きます。
        - **[+ 新規作成]** をクリックして **[パブリック IP アドレスの作成]** ページを開きます。
        - パブリック IP アドレスの**名前**を入力します。 SKU は **[Basic]** のままにしておきます。このページの下部にある **[OK]** を選択して変更を保存します。

    > [!Note]  
    > VPN Gateway では現在、パブリック IP アドレスの動的割り当てのみサポートしています。 もっとも、VPN ゲートウェイに割り当てられた IP アドレスが後から変わることは基本的にありません。 パブリック IP アドレスが変わるのは、ゲートウェイが削除され、再度作成されたときのみです。 VPN ゲートウェイのサイズ変更、リセット、その他の内部メンテナンス/アップグレードでは、IP アドレスは変わりません。

4. 設定を確認します。 
5. **[作成]** をクリックして、VPN ゲートウェイの作成を開始します。 設定が検証され、ダッシュボードに [Deploying Virtual network gateway]\(仮想ネットワーク ゲートウェイのデプロイ\) タイルが表示されます。 ゲートウェイの作成には、最大で 45 分かかる場合があります。 完了状態を確認するために、ポータル ページの更新が必要な場合があります。

    ゲートウェイの作成後、ポータルの仮想ネットワークを調べることで、ゲートウェイに割り当てられている IP アドレスを確認します。 ゲートウェイは、接続されたデバイスとして表示されます。 接続されているデバイス (仮想ネットワーク ゲートウェイ) を選択すると、詳細情報を表示できます。
6. Azure Stack デプロイでこれらの手順を繰り返します。

## <a name="create-the-local-network-gateway-in-azure-and-azure-stack"></a>Azure および Azure Stack にローカル ネットワーク ゲートウェイを作成する

ローカル ネットワーク ゲートウェイは通常、オンプレミスの場所を指します。 サイトに Azure または Azure Stack が参照できる名前を付け、接続を作成するオンプレミス VPN デバイスの IP アドレスを指定します。 また、VPN ゲートウェイを介して VPN デバイスにルーティングされる IP アドレスのプレフィックスも指定します。 指定するアドレスのプレフィックスは、オンプレミス ネットワークのプレフィックスです。 オンプレミスのネットワークが変更された場合、または VPN デバイスのパブリック IP アドレスを変更する必要がある場合、これらの値を後で簡単に更新できます。

1. ポータルで、**[+リソースの作成]** を選択します。
2. 検索ボックスに「**ローカル ネットワーク ゲートウェイ**」と入力し、**Enter** キーを押して検索します。 これにより、結果の一覧が返されます。 **[ローカル ネットワーク ゲートウェイ]** をクリックし、**[作成]** ボタンを選択して **[ローカル ネットワーク ゲートウェイの作成]** ページを開きます。
3. **[ローカル ネットワーク ゲートウェイの作成]** ページで、「値の例」と次に説明する追加の値を参考にして、ローカル ネットワーク ゲートウェイの値を指定します。
    - **[IP アドレス]:** これは、Azure または Azure Stack が接続する VPN デバイスのパブリック IP アドレスです。 有効なパブリック IP アドレスを指定します。 IP アドレスは NAT の背後にすることができず、Azure から到達可能でなければなりません。 現時点で IP アドレスを持っていない場合は、例に示されている値を使用できますが、プレースホルダーとして指定したこの IP アドレスを後で VPN デバイスのパブリック IP アドレスに置き換える必要があります。 そうしないと、Azure は接続を行うことができません。
    - **[アドレス空間]** は、このローカル ネットワークが表すネットワークのアドレス範囲を参照します。 複数のアドレス領域の範囲を追加することができます。 ここで指定した範囲が、接続先となる他のネットワークの範囲と重複しないようにしてください。 指定したアドレス範囲が、Azure によってオンプレミスの VPN デバイスの IP アドレスにルーティングされます。 オンプレミスのサイトに接続する場合は、例に示されている値を使用せず、ここで独自の値を使用してください。
    - **[BGP 設定の構成]:** BGP を構成する場合にのみ使用します。 それ以外の場合は選択しないでください。
    - **[サブスクリプション]:** 正しいサブスクリプションが表示されていることを確認します。
    - **[リソース グループ]:** 使用するリソース グループを選択します。 新しいリソース グループを作成することも、作成済みのリソース グループを選択することもできます。
    - **[場所]:** このオブジェクトが作成される場所を選択します。 VNet が存在するのと同じ場所を選択することもできますが、必須ではありません。
4. 値の指定が完了したら、ページの下部にある **[作成]** ボタンを選択して、ローカル ネットワーク ゲートウェイを作成します。
5. Azure Stack デプロイでこれらの手順を繰り返します。

## <a name="configure-your-connection"></a>接続を構成する

オンプレミス ネットワークとのサイト間接続には VPN デバイスが必要です。 この手順では、接続と呼ばれる VPN デバイスを構成します。 接続を構成する際に、次の情報が必要になります。
    - 共有キー。 サイト間 VPN 接続を作成するときにも、これと同じ共有キーを指定します。 ここで紹介している例では、基本的な共有キーを使用しています。 実際には、もっと複雑なキーを生成して使用することをお勧めします。
    - 仮想ネットワーク ゲートウェイのパブリック IP アドレス。 パブリック IP アドレスは、Azure Portal、PowerShell、または CLI を使用して確認できます。 Azure portal を使用して VPN ゲートウェイのパブリック IP アドレスを調べるには、[仮想ネットワーク ゲートウェイ] に移動し、該当するゲートウェイの名前を選択します。
仮想ネットワーク ゲートウェイとオンプレミス VPN デバイスとの間にサイト間 VPN 接続を作成します。
1. ポータルで、**[+リソースの作成]** を選択します。
2. 検索ボックスに「**接続**」と入力し、**Enter** キーを押して検索します。 これにより、結果の一覧が返されます。 **[接続]** をクリックし、[作成] ボタンを選択して **[接続の作成]** ページを開きます。
3. **[接続の作成]** ページで、接続の値を構成します。
     - 基本:
        1. **[接続の種類]:** [サイト対サイト (IPSec)] を選択します。
        2. **[リソース グループ]**: (テスト リソース グループを選択します)
     - 以下のように設定します。
        1. **[仮想ネットワーク ゲートウェイ]**: 前に作成した仮想ネットワーク ゲートウェイを選択します。
        2. **[ローカル ネットワーク ゲートウェイ]**: 前に作成したローカル ネットワーク ゲートウェイを選択します。 
        3. **[接続名]**: 2 つのゲートウェイの値が自動的に入力されます。 
        4. **[共有キー]:** この値は、ローカルのオンプレミス VPN デバイスで使用している値と一致させる必要があります。 この例では "abc123" を使用していますが、より複雑な値を使用することもできます (推奨)。 重要なのは、ここで指定する値は、VPN デバイスを構成する際に指定する値と同じにする必要があることです。
    - **[サブスクリプション]**、**[リソース グループ]**、**[場所]** の残りの値は固定されています。
4. **[OK]** をクリックして、接続を作成します。 画面に "接続を作成しています" というメッセージが点滅表示されます。
5. 仮想ネットワーク ゲートウェイの **[接続] ページで接続を確認できます。 状態は、**[不明]** から **[接続中]** に変わり、その後 **[成功]** に変わります。

## <a name="next-steps"></a>次の手順

- Azure のクラウド パターンの詳細については、「[クラウド設計パターン](https://docs.microsoft.com/azure/architecture/patterns)」を参照してください。
