---
title: Azure でのガバナンス | Microsoft Docs
description: クラウドベースのコンピューティング サービスについて学びます。これには、アプリケーションまたはエンタープライスのニーズを満たすために自動的にスケールアップとスケールダウンを行うことができる、コンピューティング インスタンスとサービスの多様な選択肢が含まれます。
services: security
documentationcenter: na
author: UnifyCloud
manager: mbaldwin
editor: TomSh
ms.assetid: ''
ms.service: security
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/01/2017
ms.author: TomSh
ms.openlocfilehash: a5f323b98fa30d2c4c89fa8fe8e75c1d89089b6e
ms.sourcegitcommit: 870d372785ffa8ca46346f4dfe215f245931dae1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="governance-in-azure"></a>Azure でのガバナンス

セキュリティはクラウドの最優先の課題であり、Azure セキュリティについての正確でタイムリーな情報を得ることがどれだけ重要かを、私たちは認識しています。 アプリケーションとサービスに Azure を使用する最大の理由の 1 つは、さまざまなセキュリティ ツールや機能を活用できることです。 これらのツールや機能により、Azure プラットフォーム上にセキュリティで保護されたソリューションを作成できるようになります。

Microsoft Azure に実装されている多数のガバナンス コントロールについて、お客様側と Microsoft 側の運用上の観点からご理解いただくために、この記事「Azure でのガバナンス」では、Microsoft Azure で提供されるガバナンスの機能について総合的に説明します。

## <a name="azure-platform"></a>Azure プラットフォーム

Azure は、オペレーティング システム、プログラミング言語、フレームワーク、ツール、データベース、デバイスにおいて幅広い選択肢をサポートするパブリック クラウド サービス プラットフォームです。 Docker を統合した Linux コンテナーの実行、JavaScript、Python、.NET、PHP、Java、Node.js によるアプリの構築、iOS、Android、Windows の各デバイスに対応したバックエンドの構築を行えます。 Azure パブリック クラウド サービスでは、何百万人もの開発者や IT プロフェッショナルから現在信頼が寄せられているのと同じテクノロジがサポートされています。

IT 資産を構築し、パブリック クラウド サービス プロバイダーに移行したとしましょう。このとき、移行したアプリケーションやデータをどこまで保護できるかは、採用したプロバイダーがクラウド ベースの資産のセキュリティ管理のためにどのようなサービスと体制を用意しているかに応じて変わってきます。

Azure のインフラストラクチャでは、数百万の顧客を同時にホストできるように施設からアプリケーションまでが設計されており、ビジネスのセキュリティ要件を満たす信頼性の高い基盤となっています。 また、Azure には多数のセキュリティ オプションと制御機能が用意されており、組織によるデプロイの独自の要件を満たすようにセキュリティをカスタマイズできます。

このドキュメントでは、Azure のガバナンス機能を使用して、これらの要件をどのように満たすことができるかをわかりやすく説明します。

## <a name="abstract"></a>要約

Microsoft Azure クラウド ガバナンスは、組織における Azure プラットフォームの使用状況を確認して通知するための、統合された監査およびコンサルティングの手段を提供します。 Microsoft Azure クラウド ガバナンスでは、クラウド コンピューティングのプランニング、アーキテクチャ、取得、デプロイ、運用、管理に関わる意思決定プロセス、基準、およびポリシーを扱います。

Microsoft Azure クラウド ガバナンスのプランを作成するには、現在配置されている人員、プロセス、テクノロジを深く掘り下げて洞察し、IT 部門によるビジネス ニーズの一貫したサポートを容易にしながら、エンド ユーザーが Microsoft Azure の強力な機能を柔軟に使用できるようにするためのフレームワークを作成する必要があります。

このホワイトペーパーでは、Microsoft Azure で高度な IT リソースのガバナンスを実現する方法について説明します。 このホワイトペーパーは Microsoft Azure に組み込まれているセキュリティとガバナンスの機能を理解するのに役立ちます。

このホワイトペーパーでは、ガバナンスに関する次の問題を主に取り上げます。

- 組織の目標に沿ったポリシー、プロセス、手順の実装

- セキュリティおよび組織の標準への継続的なコンプライアンス

- アラートと監視

## <a name="implementation-of-policies-processes-and-procedures"></a>ポリシー、プロセス、手順の実装 

管理部門は、Azure 全体で実装されている情報セキュリティ ポリシーと運用の継続性を監視する役割と責任を確立しています。 Microsoft Azure の管理機能を使って、各チーム内 (サード パーティも含む) でのセキュリティと継続性を監視し、セキュリティ ポリシー、プロセス、および標準へのコンプライアンスを促進します。

以下では次の項目について詳しく説明します。

- アカウント プロビジョニング

- サブスクリプションによる制御

- ロールベースのアクセス制御

- リソース管理

- リソースの追跡

- 重要なリソースの管理

- 請求情報への API アクセス

- ネットワークの管理

## <a name="account-provisioning"></a>アカウント プロビジョニング

アカウント階層の定義は、社内で Azure のサービスを使用および構成するための主要な手順であり、ガバナンス構造の中核をなす部分です。 エンタープライズ契約を結んでいるお客様は、この環境を部門、アカウント、サブスクリプションにさらに分割できます。

![アカウント プロビジョニング](./media/governance-in-azure/security-governance-in-azure-fig1.png)

エンタープライズ契約がないお客様は、サブスクリプション レベルで [Azure タグ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags)を使用して階層を定義することを検討してください。 Azure サブスクリプションは、すべてのリソースが含まれる基本単位です。 また、サブスクリプションによって Azure 内での制限 (コア数、リソース数など) が定められます。サブスクリプションには[リソース グループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)を含めることができ、リソース グループにはリソースを含めることができます。 [RBAC](https://docs.microsoft.com/azure/api-management/api-management-role-based-access-control) の原則は、これら 3 つのレベルで適用されます。

企業はそれぞれ異なるので、エンタープライズ契約がないお客様が Azure タグを使用して定義した階層は、その企業での Azure の構造に非常に柔軟に対応します。 Microsoft Azure でリソースをデプロイする前に、階層のモデルを作成し、請求、リソースへのアクセス、および複雑性に対する影響を理解しておく必要があります。

## <a name="subscription-controls"></a>サブスクリプションによる制御

サブスクリプションによって、リソースの使用量がどのように報告、課金されるかが決まります。 サブスクリプションは、個別の請求および支払いごとに設定できます。 前に説明したように、1 つの Azure アカウントには複数のサブスクリプションを設定できます。 サブスクリプションを使用して、企業の複数の部門における Azure リソースの使用量を判断することができます。

たとえば、企業の IT 部門、HR 部門、およびマーケティング部門がそれぞれ異なるプロジェクトを実行している場合、 各部門での Azure リソース (仮想マシンなど) の使用量に応じて課金することができます。 これにより、各部門のファイナンスを管理できます。

Azure サブスクリプションでは、次の 3 つのパラメーターを設定します。

- 一意のサブスクライバー ID

- 請求先

- 使用可能なリソースのセット

個人の場合は、1 つの Microsoft アカウント ID、クレジット カード番号、および Azure の全サービス (サブスクリプションの種類に応じて使用制限あり) が含まれます。

Azure 加入契約の階層では、エンタープライズ契約の範囲内でどのようにサービスを構成するかを定義します。 Enterprise Portal を使用し、組織の固有のニーズに合わせてカスタマイズできる柔軟な階層に基づいて、エンタープライズ契約に関連付けられている Azure リソースへのアクセスを分割することができます。 関連付けられている請求とリソースへのアクセスを正確に把握できるよう、階層のパターンは組織の管理上および地理的な構造と一致させる必要があります。

階層は大まかに、機能、部署、および地域の 3 パターンに分けられ、それぞれの部門を管理上の構成要素としてアカウントのグループ分けに使用します。 各部門内でアカウントにサブスクリプションを割り当てることができます。これにより、Azure での請求と主要な制限 (VM やストレージ アカウントの数など) のためのサイロが作成されます。

![サブスクリプションによる制御](./media/governance-in-azure/security-governance-in-azure-fig2.png)


エンタープライズ契約を結んでいる組織の場合、Azure のサブスクリプションは次の 4 階層になります。

- エンタープライズ加入契約管理者

- 部門管理者

- アカウント所有者

- サービス管理者

この階層は、次のものを制御します。

- 課金関係

- アカウント管理

- アーティファクトへのロールベースのアクセス制御 (RBAC)

- 境界と制限

- 境界

  - 使用量と請求 (プランの数に基づくレート カード)

  - 制限

  - Virtual Network

- 1 つの AAD へのアタッチ (1 つの AAD は多数のサブスクリプションと関連付けられる)

- エンタープライズ加入契約アカウントへの関連付け

## <a name="role-based-access-controls"></a>ロールベースのアクセス制御

Azure が最初にリリースされたときには、サブスクリプションに対するアクセス制御が基本でした (管理者または共同管理者)。 クラシック モデルでのサブスクリプションへのアクセスは、ポータルでのすべてのリソースへのアクセスを意味していました。 きめ細かく制御することができなかったため、Azure 加入契約に一定レベルの妥当なアクセス制御を提供するためにサブスクリプションが急増しました。

![ロールベースのアクセス制御](./media/governance-in-azure/security-governance-in-azure-fig3.png)

このようにサブスクリプションを急増させる必要はなくなりました。 ロールベースのアクセス制御により、ユーザーを標準ロール (一般的な "リーダー" および "ライター" タイプのロールなど) を割り当てることができます。 また、カスタム ロールを定義することもできます。

[Azure のロールベースのアクセス制御 (RBAC)](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles) では、Azure のアクセス権の詳細な管理を実現します。 RBAC を使用すると、職務に必要な範囲のアクセス権だけをユーザーに付与することができます。 セキュリティを重視する企業は、実際に必要となるアクセス許可を従業員に付与することに注力する必要があります。 アクセス許可が多すぎると、アカウントが攻撃者による悪用の対象になりかねません。 アクセス許可が少なすぎると、従業員が業務を効率的に遂行できなくなる可能性があります。 Azure のロールベースのアクセス制御 (RBAC) は、Azure のアクセス許可を詳細に管理を実現することでこの問題に対処できます。 RBAC を使用すると、チーム内で職務を分離し、職務に必要なアクセス許可のみをユーザーに付与することができます。 すべてのユーザーに Azure サブスクリプションまたはリソースで無制限のアクセス許可を付与するのではなく、特定の操作のみを許可することができます。

たとえば、RBAC を使用して、ある従業員にはサブスクリプションで仮想マシンを管理できるようにし、他の従業員にも同じサブスクリプション内で SQL データベースを管理できるようにします。

Azure RBAC には、すべてのリソースの種類に適用される 3 つの基本的なロールがあります。

- **所有者** は、他のユーザーへアクセス権を委任する権限を含め、すべてのリソースへのフル アクセス権を持ちます。

- **共同作成者**は、Azure リソースのすべてのタイプを作成および管理できますが、他のユーザーへアクセス権を付与することはできません。

- **閲覧者** は、既存の Azure リソースを表示できます。

残りの Azure RBAC ロールでは、特定の Azure リソースの管理が許可されます。 たとえば、仮想マシンの共同作成者ロールが割り当てられたユーザーには、仮想マシンの作成と管理が許可されます。 その一方で、仮想マシンが接続する仮想ネットワークまたはサブネットへのアクセス権は付与されません。

[RBAC: 組み込みのロール](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles) 」に、Azure で使用できる RBAC ロールが記載されています。 各組み込みロールによってユーザーに付与される操作とスコープが説明されています。

アクセス権を付与するには、ユーザー、グループ、およびアプリケーションに適切な RBAC ロールを特定のスコープで割り当てます。 ロール割り当てのスコープには、サブスクリプション、リソース グループ、または単独のリソースを指定できます。 親スコープでロールが割り当てられると、その親に含まれる子へのアクセス権も付与されます。

たとえば、リソース グループへのアクセス権を持つユーザーは、Web サイト、仮想マシン、サブネットなど、リソース グループに含まれるすべてのリソースを管理できます。

Azure RBAC は、Azure ポータルと Azure Resource Manager API での Azure リソースの管理操作のみに対応しています。 Azure リソースのデータ レベルの操作の中には、許可されていないものもあります。 たとえば、同じユーザーにストレージ アカウントを管理することを承認できますが、ストレージ アカウントでの BLOB またはテーブルの操作を許可することはできません。 同様に、SQL データベースは管理できますが、その中のテーブルは管理できません。

RBAC を使用した高度なアクセス管理については、「 [What is Role-Based Access Control (ロールベースのアクセス制御とは)](https://docs.microsoft.com/azure/role-based-access-control/overview)」を参照してください。

組み込みのロールの中にアクセス権に関する特定の要件を満たすものがない場合は、Azure のロールベースのアクセス制御 (RBAC) で[カスタム ロールを作成](https://docs.microsoft.com/azure/role-based-access-control/custom-roles)できます。 カスタム ロールは、[Azure PowerShell](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-powershell)、[Azure コマンド ライン インターフェイス (CLI)](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-cli)、および [REST API](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-rest) で作成することができます。 組み込みのロールと同様、カスタム ロールは、ユーザー、グループ、アプリケーションに対して、サブスクリプション、リソース グループ、リソースのスコープで割り当てることができます。

各サブスクリプション内では、最大 2,000 のロールの割り当てを許可できます。

## <a name="resource-management"></a>リソース管理

Azure では当初、クラシック デプロイ モデルのみ用意されていました。 このモデルでは、各リソースが独立して存在していたため、関連リソースをまとめてグループ化する方法がありませんでした。 それどころか、ソリューションまたはアプリケーションを構成するリソースを手動で追跡し、うまくバランスを取りながら管理する必要がありました。

ソリューションをデプロイするには、Azure Portal 経由で各リソースを個別に作成するか、すべてのリソースを正しい順序でデプロイするスクリプトを作成する必要がありました。 ソリューションを削除するには、各リソースを個別に削除するほかありませんでした。 関連リソースのアクセス制御ポリシーの適用と更新は、簡単ではありませんでした。 そのうえ、タグをリソースに適用し、リソースの監視と請求の管理に役立つ単語を使ってこれらのリソースにラベル付けすることもできませんでした。

2014 年、Azure に Resource Manager が導入され、リソース グループの概念が追加されました。 リソース グループとは、共通のライフサイクルが共有されるリソースのコンテナーです。 Resource Manager デプロイ モデルにはいくつかの利点があります。

- ソリューションのすべてのサービスを、個別に処理するのではなく、グループとしてデプロイ、管理、監視できます。

- ソリューションをそのライフサイクル全体で繰り返しデプロイできます。また、常にリソースが一貫した状態でデプロイされます。

- リソース グループに属するすべてのリソースにアクセス制御を適用できます。これらのポリシーは、リソース グループに新しいリソースが追加されたときに自動的に適用されます。

- タグをリソースに適用し、サブスクリプションのすべてのリソースを論理的に整理できます。

- JavaScript Object Notation (JSON) を使用してソリューションのインフラストラクチャを定義できます。 JSON ファイルは Resource Manager テンプレートと呼ばれます。

- 正しい順序でデプロイされるようにリソース間の依存性を定義できます。

![リソース管理](./media/governance-in-azure/security-governance-in-azure-fig4.png)

Resource Manager では、管理、課金、または自然なアフィニティのために、リソースを意味のあるグループに配置できます。 前述のように、Azure には 2 つのデプロイメント モデルがあります。 初期の[クラシック モデル](https://docs.microsoft.com/azure/azure-resource-manager/resource-manager-deployment-model)では、管理の基本単位はサブスクリプションでした。 サブスクリプション内でリソースを分類するのが難しかったことから、多数のサブスクリプションが作成されていました。 Resource Manager モデルでリソース グループが導入されました。

リソース グループは、Azure ソリューションの関連するリソースを保持するコンテナーです。 [リソース グループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)には、ソリューションのすべてのリソースか、グループとして管理したいリソースのみを含めることができます。 組織のニーズに合わせてリソースをリソース グループに割り当てる方法を指定してください。

テンプレートの推奨事項については、「[Azure Resource Manager テンプレートを作成するためのベスト プラクティス](https://docs.microsoft.com/azure/azure-resource-manager/resource-manager-template-best-practices)」を参照してください。

依存関係は Azure Resource Manager によって分析され、確実に正しい順序でリソースが作成されます。 リソースが別のリソースの値に依存する場合 (ディスクのストレージ アカウントを必要とする仮想マシンなど) は、依存関係を設定します。

>[!Note]
>詳細については、「 [Azure Resource Manager のテンプレートでの依存関係の定義](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-define-dependencies) 」に関するページを参照してください。

インフラストラクチャの更新にも、テンプレートを使用することができます。 たとえば、ソリューションにリソースを追加したり、既にデプロイされたリソースに構成ルールを追加したりできます。 テンプレートでリソースの作成を指定した際、そのリソースが既に存在する場合は、Azure Resource Manager では、新しい資産を作成する代わりに更新が実行されます。 Azure Resource Manager では、既存の資産が、新しい資産と同じ状態になるよう更新されます。

Resource Manager では、セットアップ時に含まれていなかったソフトウェアのインストールなど、追加の操作が必要なシナリオのための拡張機能を使用できます。

## <a name="resource-tracking"></a>リソースの追跡

組織のユーザーはサブスクリプションにリソースを追加するので、適切な部門、顧客、環境にリソースを関連付けることがますます重要になります。 タグを使用することで、リソースにメタデータを添付できます。 [タグ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags)を使用して、リソースや所有者に関する情報を提供します。 タグを使用すると、さまざまな方法でリソースを集計し、グループ化できるだけでなく、配賦のためにそのデータを使用できます。

リソース グループとリソースが複雑に絡み合っており、これらの資産をわかりやすく視覚化する必要がある場合は、タグを使用してください。 たとえば、組織内で同じロールを果たしている複数リソース、または同じ部門に属している複数リソースにタグを付けることができます。

タグがないと、組織内のユーザーは複数のリソースを作成できるものの、作成したリソースを後で特定して管理することが困難になる場合があります。 たとえば、プロジェクトに関するすべてのリソースを削除したい場合があります。 これらのリソースに対してプロジェクトに関するタグが設定されていない場合、手動で探す必要があります。 タグ付けは、サブスクリプションの不要なコストを削減するための重要な方法です。

タグを共有するために、リソースが同じリソース グループ内に格納されている必要はありません。 組織内のユーザーが類似したタグを誤って適用しないよう (「department」の代わりに「dep」など)、組織内のすべてのユーザーが共通のタグを使用できる独自のタグ分類法を作成することができます。

リソース ポリシーを使用して、組織の標準的なルールを作成することができます。 リソースが適切な値でタグ付けされることを保証するポリシーを作成することができます。

> [!Note]
> 詳細については、「[課金タグ ポリシーのイニシアティブ](../azure-policy/scripts/billing-tags-policy-init.md)」を参照してください。

Azure Portal からタグ付きのリソースを表示することもできます。

サブスクリプションの[使用状況レポート](https://docs.microsoft.com/azure/billing/billing-understand-your-bill)にはタグ名と値が含まれます。これにより、タグを使ってコストの計算を分けることができます。

> [!Note]
> タグの詳細については、「[課金タグ ポリシーのイニシアティブ](../azure-policy/scripts/billing-tags-policy-init.md)」を参照してください。

タグには次の制限事項が適用されます。

- 各リソースまたはリソース グループには、最大で 15 個のタグ キー/値のペアを含めることができます。 この制限は、リソース グループまたはリソースに直接適用されたタグにのみ適用されます。 リソース グループに、それぞれが 15 個のタグ キー/値ペアを持つリソースを多数含めることができます。

- タグの名前は 512 文字に制限されています。

- タグの値は 256 文字に制限されています。

- リソース グループに適用したタグは、そのリソース グループ内のリソースには継承されません。

リソースに関連付ける必要のある値が 15 個を超える場合は、タグ値に JSON 文字列を使用します。 JSON 文字列には、1 つのタグ キーに適用される値を多数含めることができます。

### <a name="tags-and-billing"></a>タグと課金

タグを使用して、課金データをグループ化できます。 たとえば、異なる組織向けに複数の VM を実行している場合は、タグを使用して、コスト センターごとに課金データをグループ化します。 また、タグを使用すると、運用環境で実行されている VM の課金データなどの、ランタイム環境ごとにコストを分類することもできます。

タグに関する情報は、 [Azure Resource Usage API と RateCard API](https://docs.microsoft.com/azure/billing/billing-usage-rate-card-overview) から、あるいはコンマ区切り値 (CSV) ファイルから取得できます。 使用状況ファイルは [Azure アカウント ポータル](https://account.windowsazure.com/)または [EA ポータル](https://ea.azure.com/)からダウンロードします。

>[!Note]
> 課金情報へのプログラムによるアクセスの詳細については、「 [Microsoft Azure リソースの消費を把握する](https://docs.microsoft.com/azure/billing/billing-usage-rate-card-overview)」を参照してください。 REST API の操作については、「 [Azure Billing REST API Reference (Azure Billing REST API リファレンス)](https://msdn.microsoft.com/library/azure/1ea5b323-54bb-423d-916f-190de96c6a3c)」を参照してください。

課金のタグがサポートされているサービスの使用状況 CSV ファイルをダウンロードした場合、タグは Tags 列に表示されます。

## <a name="critical-resource-controls"></a>重要なリソースの管理

組織ではサブスクリプションにコア サービスを追加するので、ビジネスが中断されないように、それらのサービスの可用性を確保することがますます重要になります。 [リソース ロック](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources)を使用すると、変更または削除したときにアプリケーションやクラウド インフラストラクチャに大きな影響を及ぼす価値の高いリソースに対する操作を制限できます。 ロックは、サブスクリプション、リソース グループ、またはリソースに適用できます。 通常は、仮想ネットワーク、ゲートウェイ、ストレージ アカウントなどの基本的なリソースにロックを適用します。

リソース ロックでは、CanNotDelete と ReadOnly の 2 つの値を現在サポートしています。 CanNotDelete では、(適切な権限を持つ) ユーザーはリソースの読み取りまたは変更を引き続き行うことができますが、リソースを削除することはできません。 ReadOnly では、許可されたユーザーがリソースを削除することも変更することもできません。

Resource Manager のロックは、管理ウィンドウで実行され、<https://management.azure.com> に送信される操作で構成される操作のみに適用されます。 ロックは、リソースが独自の機能を実行する方法を制限しません。 リソースの変更は制限されますが、リソースの操作は制限されません。 たとえば、SQL Database に対する ReadOnly ロックは、ユーザーによるデータベースの削除または変更を禁止しますが、データベースに対するデータの作成、更新、または削除は禁止しません。

**ReadOnly** を適用すると、読み取り操作のように見えるいくつかの操作には追加のアクションが必要となるため、予期しない結果を招く可能性があります。 たとえば、 **ReadOnly** ロックをストレージ アカウントに設定すると、すべてのユーザーがキーを一覧表示できなくなります。 返されるキーは書き込み操作に使用できるため、キーの一覧表示操作は POST 要求を介して処理されます。

![重要なリソースの管理](./media/governance-in-azure/security-governance-in-azure-fig5.png)

別の例として、ReadOnly ロックを App Service リソースに配置すると、Visual Studio のサーバー エクスプローラーの操作には書き込みアクセスが必要となるため、Visual Studio のサーバー エクスプローラーはリソース用のファイルを表示できなくなります。

ロールベースのアクセス制御とは異なり、管理ロックを使用すると、すべてのユーザーとロールに対して制限を適用することができます。 ユーザーとロールのアクセス許可を設定する方法については、「[Azure のロールベースのアクセス制御](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal)」を参照してください。

親スコープでロックを適用すると、そのスコープ内のすべてのリソースは同じロックを継承します。 後で追加するリソースも、親からロックを継承します。 継承されるロックの中で最も制限の厳しいロックが優先されます。

管理ロックを作成または削除するには、Microsoft.Authorization/ _または Microsoft.Authorization/locks/_ アクションにアクセスできる必要があります。 組み込みロールのうち、**所有者**と**ユーザー アクセス管理者**にのみこれらのアクションが許可されています。

## <a name="api-access-to-billing-information"></a>課金情報への API アクセス

Azure Billing API を使用すると、使用状況やリソースに関するデータを、お使いのデータ分析ツールで取得できます。 Azure Resource Usage API と Azure Resource RateCard API は、コストを正確に予測して管理するうえで役立ちます。 これらの API は、Azure Resource Manager が公開している API ファミリに含まれ、リソース プロバイダーとして実装されています。

### <a name="azure-resource-usage-api-preview"></a>Azure Resource Usage API (プレビュー)

[Azure Resource Usage API](https://msdn.microsoft.com/library/azure/mt219003) を使用すると、Azure の推定消費量データを取得できます。 この API には次の要素が含まれています。

- **Azure ロールベースのアクセス制御** - [Azure Portal](https://portal.azure.com/) または [Azure PowerShell コマンドレット](https://docs.microsoft.com/powershell/azure/overview)を使用して、アクセス ポリシーを構成し、サブスクリプションの使用状況データにアクセスできるユーザーやアプリケーションを指定できます。 呼び出し元は、認証に Azure Active Directory トークンを使用する必要があります。 また、呼び出し元が特定の Azure サブスクリプションの使用状況データにアクセスするには、請求閲覧者、閲覧者、所有者、共同作成者のいずれかのロールに呼び出し元を追加します。

- **時間単位または日単位の集計** - 呼び出し元は、時間単位のバケットまたは日単位のバケットのどちらで Azure 使用状況データを取得するかを指定できます。 既定値は日単位です。

- **インスタンス メタデータ (リソース タグなど)** - 完全修飾リソース URI (/subscriptions/{subscription-id}/..) などのインスタンスレベルの詳細情報、リソース グループ情報、リソース タグを取得できます。 これらのメタデータを利用すると、クロス課金のようなユースケースにおいて、プログラムでタグを使って確定的に使用状況を割り当てることができます。

- **リソース メタデータ** - 呼び出し元は、測定名、測定カテゴリ、測定サブカテゴリ、単位、リージョンなどのリソースの詳細情報をもとに、消費内容をより詳しく理解できます。 また、エクスペリエンス全体でデータを関連付けることができるように、現在、Azure Portal、Azure 使用状況 CSV、EA 課金 CSV など、一般公開されているエクスペリエンス全体でリソース メタデータの用語の調整を進めています。

- **すべてのプラン タイプの使用状況** - 従量課金制、MSDN、料金コミットメント、料金クレジット、EA など、すべてのプラン タイプについて使用状況データを取得できます。

**Azure resource RateCard API (プレビュー)**

Azure Resource RateCard API を使用して、使用可能な Azure リソースの一覧と、それぞれの推定料金情報を取得できます。 この API には次の要素が含まれています。

- **Azure ロールベースのアクセス制御** - Azure Portal または Azure PowerShell コマンドレットを使用して、アクセス ポリシーを構成し、RateCard データにアクセスできるユーザーやアプリケーションを指定できます。 呼び出し元は、認証に Azure Active Directory トークンを使用する必要があります。 また、呼び出し元が特定の Azure サブスクリプションの使用状況データにアクセスするには、リーダー、所有者、共同作成者のいずれかのロールに呼び出し元を追加します。

- **従量課金制、MSDN、料金コミットメント、料金クレジット プランのサポート (EA はサポートされていません)** - この API は、Azure のプラン レベルの料金情報を提供します。 この API の呼び出し元は、プラン情報を渡してリソースの詳細と料金を取得する必要があります。 EA プランには登録ごとにカスタマイズされた料金があるため、現在は EA 料金を提供できません。 Usage API と RateCard API を組み合わせて実現できるシナリオ例を次に示します。

- **月間の Azure 使用量** - Usage API と RateCard API を組み合わせて使うと、月間のクラウドの使用状況をより詳しく把握できます。 時間単位や日単位でバケットの使用状況と料金の推定値を分析できます。

- **アラートの設定** - Usage API と RateCard API を使用してクラウドの推定消費量と推定料金を取得し、リソースベースまたは料金ベースのアラートを設定することができます。

- **請求額の予測** – 推定の消費量とクラウド使用量を取得し、Machine Learning アルゴリズムを適用して、課金サイクルの終了時に請求される金額を予測することができます。

- **消費前のコスト分析** - RateCard API を使用して、ワークロードを Azure に移行した場合の想定使用量に対する請求金額を予測できます。 他のクラウドまたはプライベート クラウドに既存のワークロードがある場合、その使用状況を Azure の料金に対応付けることで、より正確な Azure の使用量を取得できます。 この情報をもとに、プランを決め、従量課金制以外のプラン タイプ (料金コミットメントや料金クレジットなど) との比較を行うことができます。 また、この API を使用してリージョンごとのコストの差異を確認し、what if コスト分析を実施して、デプロイに関する決定に役立てることができます。

- **What-if 分析** - Azure リソースのリージョンや構成を変えた場合に、コスト効率が高くなるかどうかを判断できます。 Azure リソースのコストは、使用している Azure リージョンによって異なります。

- 別の Azure プラン タイプの方が Azure リソースの料金が安くなるかどうかについても判断できます。

## <a name="networking-controls"></a>ネットワークの管理

リソースへのアクセスは内部 (企業のネットワーク内) の場合もあれば、外部 (インターネット経由) の場合もあります。 組織のユーザーは誤って不適切な場所にリソースを配置しがちであり、リソースが悪意のあるアクセスにさらされる可能性があります。 オンプレミスのデバイスと同様に、企業は Azure ユーザーが正しく判断できるように適切な制御を追加する必要があります。

![ネットワークの管理](./media/governance-in-azure/security-governance-in-azure-fig6.png)

Microsoft では、サブスクリプション ガバナンスのために、基本的なアクセス制御を提供するコア リソースを特定しました。 コア リソースは以下で構成されます。

### <a name="network-connectivity"></a>ネットワーク接続

[Virtual Networks](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) は、サブネットのコンテナー オブジェクトです。 必須ではありませんが、多くの場合、アプリケーションを内部の企業リソースに接続するときに使用されます。 Azure Virtual Network サービスでは、仮想ネットワーク (VNet) を使用して Azure リソースを安全に相互接続することができます。

VNet とは、クラウド内のユーザー独自のネットワークを表したものです。 サブスクリプション専用に Azure クラウドが論理的に分離されています。 VNet は、オンプレミス ネットワークに接続することもできます。

Azure Virtual Networks の機能を次に示します。

- **分離**: VNet は相互に分離されています。 同じ CIDR アドレス ブロックを使用する開発、テスト、運用環境に個別の VNet を作成できます。 逆に、異なる CIDR アドレス ブロックを使用する複数の VNet を作成し、ネットワークをまとめて接続することもできます。 VNet は、複数のサブネットに分割することができます。 Azure では、VNet に接続されている VM ロール インスタンスと Cloud Services ロール インスタンス用に内部名前解決が用意されています。 必要に応じて、Azure の内部名前解決を使用する代わりに、独自の DNS サーバーを使用するよう VNet を構成できます。

- **インターネット接続**: VNet に接続されているすべての Azure Virtual Machines (VM) ロール インスタンスと Cloud Services ロール インスタンスは、既定でインターネットにアクセスできます。 また、必要に応じて、特定のリソースへの着信アクセスを有効にすることもできます。

- **Azure リソース接続**: Cloud Services や VM などの Azure リソースを同じ VNet に接続できます。 リソースは、異なるサブネットに存在する場合でも、プライベート IP アドレスを使用して相互に接続できます。 Azure では、サブネット、VNet、オンプレミス ネットワークの間に既定のルーティングを提供しているため、ルートの構成と管理は必要ありません。

- **VNet 接続**: VNet は相互接続が可能なため、任意の VNet に接続されているリソースは他の VNet 上の任意のリソースと通信できます。

- **オンプレミス接続**: VNet は、自身のネットワークと Azure の間のプライベート ネットワーク接続、またはインターネットを介したサイト間 VPN 接続を使用して、オンプレミス ネットワークに接続できます。

- **トラフィック フィルタリング**: VM ロール インスタンスと Cloud Services ロール インスタンスのネットワーク トラフィックは、着信、送信方向ともに、送信元の IP アドレスとポート、送信先の IP アドレスとポート、およびプロトコルでフィルター処理できます。

- **ルーティング**: 必要に応じて、独自のルートを構成するかネットワーク ゲートウェイ経由で BGP ルートを使用することで、Azure の既定のルーティングを上書きできます。

## <a name="network-access-controls"></a>ネットワーク アクセス制御

[ネットワーク セキュリティ グループ](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg)はファイアウォールに似ており、リソースがネットワーク上で通信する方法に関するルールを提供します。 ネットワーク セキュリティ グループでは、サブネット (または仮想マシン) がインターネットや同じ仮想ネットワーク内の他のサブネットに接続する方法と条件を細かく制御できます。

ネットワーク セキュリティ グループ (NSG) には、Azure Virtual Network (VNet) に接続されたリソースへのネットワーク トラフィックを許可または拒否する一連のセキュリティ規則が含まれています。 NSG はサブネットに関連付けることができるほか、クラシック モデルについては個々の VM に、Resource Manager モデルについては VM にアタッチされた個々のネットワーク インターフェイス (NIC) に関連付けることができます。

NSG をサブネットに関連付けた場合、そのサブネットに接続されているすべてのリソースにその NSG のルールが適用されます。 加えて VM や NIC にも NSG を関連付けることで、トラフィックをさらに制限することができます。

## <a name="security-and-continuous-compliance-with-organizational-standards"></a>セキュリティおよび組織の標準への継続的なコンプライアンス

企業によってニーズは異なり、どのような企業でもクラウド ソリューションからそれぞれメリットを享受しています。 それにも関わらず、どの企業にも共通するのが、クラウドへの移行に対して基本的な懸念を持っているという点です。 企業はデータを自分たちで制御し、セキュリティとプライバシーを確保したいと考えていますが、それと同時に透明性とコンプライアンスを維持する必要もあります。

お客様がクラウド プロバイダーに求めるもの:

- **データのセキュリティ** - IT 部門の幹部はクラウドでのデータの安全性や管理性の高さを認識しているにも関わらず、クラウドに移行すると、現在の社内ソリューションよりもハッカーからの攻撃を受けやすくなるのではないかという懸念を抱いています。

- **データを自ら管理** - プライベート クラウド サービス特有のプライバシー問題が企業にとって課題となっています。 企業はインフラストラクチャにかかるコストの削減と柔軟性の向上を求めてクラウドへの移行を検討しますが、データの格納場所やユーザー アクセス、およびその使用方法を管理できなくなることを恐れています。

- **データの制御** - 企業は、数多くの革新的なソリューションをデプロイできるというクラウドのメリットを享受しているにも関わらず、データを自分たちで制御できなくなることを非常に心配しています。 最近、法律上または法律外の手段を通じて政府機関が顧客データにアクセスしていることが明らかになりましたが、それにより、一部の CIO はクラウドにデータを置くことに慎重になっています。

- **一段上の透明性** - ビジネスの意思決定者にとって、セキュリティ、プライバシー、コントロールは重要ですが、それと同時に、自社のデータがどのように格納され、アクセスされ、セキュリティで保護されているかを独立して検証できることも重要な要素のひとつです。

- **コンプライアンスの維持** - 企業がクラウド テクノロジの利用を拡大するにつれ、標準や規制は複雑さを増し、その範囲も広がり続けます。 企業は、コンプライアンス基準が今後も満たされることと、時間の経過と共に変化する規制に対応してコンプライアンスも進化するということを知っておく必要があります。

## <a name="security-configuration-monitoring-and-alerting"></a>セキュリティの構成、監視、アラート

Azure の利用者は、そのクラウド環境をさまざまなデバイスから管理できます。その中には管理ワークステーションや開発用 PC もあれば、タスク固有の権限を持った特権付きのエンド ユーザー デバイスもあります。 管理作業は、Azure Portal など、Web ベースのコンソールを介して実行する場合もあれば、 オンプレミス システムと Azure との間に直接接続が存在し、仮想プライベート ネットワーク (VPN) やターミナル サービス、クライアント アプリケーション プロトコルを介して実行したり、プログラムから Azure Service Management API (SMAPI) を介して実行したりする場合もあります。 また、クライアントのエンドポイントはドメインに参加している場合と、タブレット、スマートフォンなど、管理下にない孤立したデバイスである場合とがあります。

このように多彩なアクセスと管理が可能であることによって豊富な選択肢が存在する反面、そのばらつきがクラウド デプロイに深刻なリスクをもたらすこともあり、 管理、追跡、監査という管理上の工程が困難になる可能性があります。 そうした選択肢の多さから、クラウド サービスの管理用クライアント エンドポイントの利用に監視の目が行き届かず、セキュリティ上の脅威を招く場合もあります。 インフラストラクチャの開発と管理に共用ワークステーションや個人用ワークステーションを使用することは、Web 閲覧 (水飲み場型攻撃など) や電子メール (ソーシャル エンジニアリング、フィッシングなど) などの予測不可能な脅威要因にさらされる原因となります。

監視、ログ、監査は、管理作業の追跡と把握の基礎となるものですが、生成されるデータの量が膨大であるため、それですべてのアクションを常に細部まで監査できるわけではありません。 とはいえ、管理ポリシーの効果の監査は積極的に行うことをお勧めします。

AD DS GPO の Azure セキュリティ ガバナンスを使用すると、ファイル共有などの管理者の Windows インターフェイスをすべて制御できます。 監査、監視、ログのプロセスに管理ワークステーションを追加します。 管理者と開発者のすべてのアクセスと使用状況を追跡するようにします。

### <a name="azure-security-center"></a>Azure Security Center

[Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-intro) では、サブスクリプション内のリソースのセキュリティの状態を一元的に表示することができ、リソースの侵害を防ぐうえで役立つ推奨事項が提供されます。 また、より詳細なポリシーを設定することもできます (たとえば、特定のリソース グループにポリシーを適用して、企業が対処しようとしているリスクへの対策を調整できます)。

![Azure Security Center](./media/governance-in-azure/security-governance-in-azure-fig7.png)

Security Center は、Azure サブスクリプション全体に統合セキュリティの監視とポリシーの管理を提供し、気付かない可能性がある脅威を検出し、セキュリティ ソリューションの広範なエコシステムと連動します。 サブスクリプションのリソースに対して[セキュリティ ポリシー](https://docs.microsoft.com/azure/security-center/security-center-policies)を有効にすると、Security Center は、リソースのセキュリティを分析して潜在的な脆弱性を特定します。 ネットワークの構成に関する情報は、すぐに利用可能になります。

Azure Security Center には、Azure サブスクリプション内のすべてのリソースについてのベスト プラクティス分析とセキュリティ ポリシー管理の組み合わせが表示されます。 この強力で使いやすいツールによって、Azure リソース、ネットワーク、およびマルウェア対策プログラムやファイアウォールなどのパートナー ソリューションからセキュリティ データが自動的に収集、分析されるので、セキュリティ チームとリスク責任者はセキュリティの脅威を予防、検出し、これに対処することができます。

さらに、Azure Security Center は機械学習や行動分析を含む高度な分析を適用し、グローバルな脅威インテリジェンスを活用して、既知の有害因子を探します。情報源としては、Microsoft 製品とサービス、Microsoft Digital Crimes Unit (DCU)、Microsoft Security Response Center (MSRC)、外部フィードがあります。 [セキュリティ ガバナンス](https://www.credera.com/blog/credera-site/azure-governance-part-4-other-tools-in-the-toolbox/)は、サブスクリプション レベルで広範に適用することも、ポリシー定義を通じてより詳細な要件に絞り込んで個々のリソースに適用することもできます。

最後に、Azure Security Center はこれらのポリシーに基づいてリソースのセキュリテ正常性を分析し、その豊富な情報をダッシュボードで提供し、マルウェアが検出されたときや不正な IP 接続の試みが行われたときにアラートを生成します。

>[!Note]
> 推奨事項の適用方法の詳細については、「[Azure Security Center でのセキュリティに関する推奨事項の管理](https://docs.microsoft.com/azure/security-center/security-center-recommendations)」を参照してください。

Security Center では、仮想マシンからデータを収集して、そのセキュリティ状態の評価、セキュリティ推奨事項の提供、脅威についての警告を行います。 最初に Security Center にアクセスするときは、サブスクリプション内のすべての仮想マシンに対してデータ収集が有効になっています。 データ収集は有効にしておくことをお勧めしますが、セキュリティ センター ポリシーで [データ収集を無効](https://docs.microsoft.com/azure/security-center/security-center-faq) にして、オプトアウトすることもできます。

Azure Security Center はオープン プラットフォームです。Microsoft のパートナーと独立系ソフトウェア ベンダーは、Azure Security Center に接続して機能を強化するソフトウェアを作成できます。

Azure Security Center は、次の Azure リソースを監視します。

- 仮想マシン (VM) (Cloud Services を含む)

- Azure 仮想ネットワーク

- Azure SQL サービス

- Azure サブスクリプションに統合済みのパートナー ソリューション (VM 上および [App Service Environment](https://docs.microsoft.com/azure/app-service/app-service-app-service-environments-readme) 上の Web アプリケーション ファイアウォールなど)

### <a name="log-analytics"></a>Log Analytics

Log Analytics ソフトウェア開発およびサービス チームの情報セキュリティと[ガバナンスのプログラム](https://github.com/Microsoft/azure-docs/blob/master/articles/log-analytics/log-analytics-security.md)は、ビジネス要件をサポートしており、法律および [Microsoft Azure セキュリティ センター](https://azure.microsoft.com/support/trust-center/)と [Microsoft セキュリティ センターのコンプライアンス](https://www.microsoft.com/TrustCenter/Compliance/default.aspx)で説明されている規定を順守しています。 そこでは、Log Analytics によるセキュリティ要件の確立方法、セキュリティ制御の識別方法、リスクの管理と監視方法についても説明されています。 Microsoft では、ポリシー、標準、手順、およびガイドラインのレビューを毎年行っています。

Log Analytics 開発チームの各メンバーは、正規のアプリケーション セキュリティのトレーニングを受けています。 内部的には、ソフトウェア開発用に、バージョン管理システムを使用しています。 各ソフトウェア プロジェクトは、バージョン管理システムによって保護されています。

Microsoft には、Microsoft のすべてのサービスを監視して評価する、セキュリティとコンプライアンスのチームがあります。 情報セキュリティ責任者がチームを構成します。彼らは、Log Analytics を開発するエンジニアリング部門とは関係ありません。 セキュリティ責任者には独自の管理チェーンがあり、製品とサービスについて独立した評価を行い、セキュリティとコンプライアンスを確保します。

Azure は、最初からクラウド用に設計された一連の管理サービスです。 オンプレミスのリソースのデプロイと管理は行わず、これらのコンポーネント全体が Azure にホストされます。 構成が最小限で済むため、文字どおり数分で稼働させることができます。

![Operations Manager Suite](./media/governance-in-azure/security-governance-in-azure-fig8.png)

Log Analytics サービスがクラウドで実行されるからといって、オンプレミスの環境を効果的に管理できないわけではありません。

データ センター内の Windows コンピューターまたは Linux コンピューターにエージェントを配置すると、そのエージェントによって Log Analytics にデータが送信されます。Log Analytics で、このデータをクラウドまたはオンプレミスのサービスから収集されたその他すべてのデータと共に分析できます。 Azure Backup と Azure Site Recovery を使用すると、クラウドを活用して、オンプレミスのリソースのバックアップと高可用性を実現できます。

クラウドの Runbook は通常オンプレミスのリソースにアクセスできませんが、エージェントは、データ センターで Runbook をホストする 1 つ以上のコンピューターにもインストールできます。 Runbook を開始するときは、単に、クラウドで実行するかローカル worker で実行するかを指定します。

Log Analytics のコア機能は、Azure で実行される一連のサービスによって提供されます。 サービスごとに固有の管理機能があり、サービスを組み合わせてさまざまな管理シナリオを実現できます。

![Operations Manager Suite](./media/governance-in-azure/security-governance-in-azure-fig9.JPG)

Azure Operation Manager の機能は、管理ソリューションを提供することによって拡張されます。 [管理ソリューション](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-solutions)は、1 つ以上の管理サービスを活用する管理シナリオが実装された、パッケージになった一連のロジックです。

![Azure Operation Manager](./media/governance-in-azure/security-governance-in-azure-fig10.png)

さまざまなソリューションが Microsoft とパートナーによって提供されており、Azure サブスクリプションに簡単に追加して、Log Analytics への投資の価値を高めることができます。

パートナーは、アプリケーションとサービスをサポートする独自のソリューションを作成し、Azure Marketplace またはクイック スタート テンプレートを使用してユーザーに提供できます。

## <a name="performance-alerting-and-monitoring"></a>パフォーマンスのアラートと監視

### <a name="alerting"></a>アラート

アラートとは、Azure リソースのメトリック、イベント、またはログを監視し、指定した条件が満たされたときに通知するための手段です。

**さまざまな Azure サービスのアラート**

アラートは、次のようなさまざまなサービスで使用できます。

- Application Insights: Web テストとメトリックのアラートを有効にします。

>[!Note]
> 「[Application Insights のアラートの設定](https://docs.microsoft.com/azure/application-insights/app-insights-alerts)」と「[Web サイトの可用性と応答性の監視](https://docs.microsoft.com/azure/application-insights/app-insights-monitor-web-app-availability)」をご覧ください。

- Log Analytics: アクティビティ ログと診断ログの Log Analytics へのルーティングを有効にして、メトリック、ログ、その他のアラートの種類を可能にします。

>[!Note]
> 詳細については、「[Log Analytics のアラート](https://docs.microsoft.com/azure/log-analytics/log-analytics-alerts)」を参照してください。

- Azure Monitor: メトリック値とアクティビティ ログ イベントの両方に基づいてアラートを有効にします。 [Azure Monitor REST API](https://msdn.microsoft.com/library/dn931943.aspx) を使用して、アラートを管理できます。

>[!Note]
> 詳細については、[Azure Portal、PowerShell、またはコマンド ライン インターフェイスでのアラートの作成](https://docs.microsoft.com/azure/monitoring-and-diagnostics/insights-alerts-portal)に関するページをご覧ください。

### <a name="monitoring"></a>監視

クラウド アプリのパフォーマンスの問題は、ビジネスに影響を及ぼす場合があります。 複数の相互接続されたコンポーネントや頻繁なリリースにより、いつでもパフォーマンスの低下が生じる可能性があります。 さらに、アプリを開発している場合、通常、テストで見つからなかった問題はユーザーによって発見されます。 このような問題について即座に把握し、問題を診断して修正するためのツールを用意しておく必要があります。 Microsoft Azure には、このような問題を特定するためのさまざまなツールがあります。

**自身の Azure クラウド アプリを監視する方法**

Azure のアプリケーションとサービスを監視するためにさまざまなツールがあります。 それらの機能の一部は重複しています。 これは、歴史的な理由によるものもあれば、アプリケーションの開発と運用の間のずれによるものもあります。

主なツールを次に示します。

- **Azure Monitor** は、Azure 上で実行されているサービスを監視するための基本的なツールです。 サービスのスループットと周辺環境に関するインフラストラクチャ レベルのデータが示されます。 お使いのアプリすべてを Azure で管理している場合は、リソースをスケールアップするかスケールダウンするかを決定すると、Azure Monitor により、開始するために使用する情報が提示されます。

- **Application Insights** は、開発に使用することも、運用環境の監視ソリューションとして使用することもできます。 これは、アプリにパッケージをインストールすると動作します。これにより、状況のより詳しい情報が示されます。 Application Insights のデータには、依存関係、例外トレース、スナップショットのデバッグ、実行プロファイルの応答時間が含まれます。 Application Insights には、このテレメトリすべてを分析するための強力な洗練されたツールが用意されているため、アプリをデバッグする場合にも、ユーザーがそのアプリで行っている操作を把握する場合にも役立ちます。 応答時間の急激な増加の原因がアプリにあるのか、外部リソースの問題にあるのかを見分けることができます。 Visual Studio を使用していて、アプリに問題がある場合は、その問題を修正できるように問題のコード行にすぐに移動されることがあります。

- **Log Analytics** は、運用環境で実行されているアプリケーションのパフォーマンスの調整とメンテナンスの計画を必要とするユーザー向けです。 これは Azure に基づいています。 多くのソースからデータを収集して集計しますが、10 ～ 15 分の待ち時間を伴います。 Log Analytics では、Azure、オンプレミス、サード パーティ製のクラウドベースのインフラストラクチャ (Amazon ウェブ サービスなど) に対応する包括的な IT 管理ソリューションを提供しています。 また、多くのソース間でデータを分析するための豊富なツールを提供し、すべてのログを対象とした複雑なクエリを可能にして、指定された条件で事前に通知することができます。 カスタム データも、照会および視覚化できるように中央リポジトリに収集できます。

- **System Center Operations Manager (SCOM)** は、大規模なクラウド インストールの管理と監視向けです。 オンプレミスの Windows Sever および Hyper-V ベースのクラウド用の管理ツールとして既に使い慣れているかもしれませんが、Azure アプリと統合したり Azure アプリを管理したりすることもできます。 特に重要なこととして、既存のライブ アプリに Application Insights をインストールできます。 アプリがダウンすると、すぐに通知されます。


## <a name="next-steps"></a>次の手順

- [Azure Resource Manager テンプレートを作成するためのベスト プラクティス](https://docs.microsoft.com/azure/azure-resource-manager/resource-manager-template-best-practices)

- [Azure サブスクリプション ガバナンスの実装例](https://docs.microsoft.com/azure/azure-resource-manager/resource-manager-subscription-examples)

- [Microsoft Azure Government](https://docs.microsoft.com/azure/azure-government/)
