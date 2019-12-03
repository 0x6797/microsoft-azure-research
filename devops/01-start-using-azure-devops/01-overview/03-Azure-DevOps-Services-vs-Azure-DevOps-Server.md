# Azure DevOps Services vs. Azure DevOps Server

Azure DevOps ServicesおよびAzure DevOps Serverは、以前はVisual Studio Team Services（VSTS）およびTeam Foundation Server（TFS）と呼ばれていました。
どちらの製品も、作業を計画および追跡するためのGit、継続的インテグレーション、およびアジャイルツールをサポートする統合されたコラボレーション環境を提供します。

Azure DevOps Servicesは、スケーラブルで信頼性が高く、グローバルに利用可能なホストサービスを提供するクラウドサービスです。 24時間年中無休の運用チームが監視し、99.9％のSLAに支えられており、世界中のローカルデータセンターで利用できます。

Azure DevOps Serverは、SQL Serverバックエンド上に構築されたオンプレミス製品です。
企業は通常、ネットワーク内にデータを保持する必要がある場合や、Azure DevOpsのデータとツールと統合するSQL Serverレポートサービスへのアクセスが必要な場合に、オンプレミスを選択します。

どちらの製品もAzure DevOps Serverと比較して同じ重要なサービスを提供しますが、Azure DevOps Servicesには次の追加の利点があります。

- サーバー管理の簡素化。
- 最新かつ最高の機能へすぐにアクセス
- リモートサイトとの接続の改善。
- 設備投資（サーバーなど）から運用支出（サブスクリプション）への移行。

クラウドまたはオンプレミスのどちらがニーズを満たすかを判断するには、次の重要な違いを考慮してください。

## Azure DevOps ServicesとAzure DevOps Serverの基本的な違い

必要なプラットフォームを選択する場合、またはオンプレミスからクラウドへの移行を検討している場合は、次の点を考慮してください。

- [データの範囲とスケール](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops#scope-scale-data)
- [認証](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops#authentication)
- [ユーザーおよびグループ](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops#users-groups)
- [ユーザーアクセス管理](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops#manage-user-access)
- [セキュリティおよびデータ保護](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops#security-data)

### 特定の機能領域の違い

Azure DevOps ServicesはAzure DevOps Serverのクラウドホストバージョンですが、機能にはいくつかの違いがあります。
Azure DevOps Serverの一部の機能は、Azure DevOps Servicesではサポートされていません。
たとえば、Azure DevOps Servicesは、レポートをサポートするためのSQL Server Analysis Servicesとの統合をサポートしていません。

次の2つの追加領域は、サポートが異なります。

- [プロセスのカスタマイズ](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops#process-customization)
- [リポート](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops#reporting)

Azure DevOps Serverを使用していて、移動を検討している場合は、[移行オプション](https://docs.microsoft.com/ja-jp/azure/devops/migrate/migrate-from-tfs?view=azure-devops)を読んで、オプションを理解してください。

## データの範囲とスケール

### 組織とプロジェクトを使用してAzure DevOps Servicesを拡張

Azure DevOps Servicesは、Azure DevOps Serverとは少し異なります。
現在、データのスコーピングとスケーリングには、組織とプロジェクトの2つのオプションしかありません。 Azure DevOps Servicesの組織は独自のURL（たとえば、`https：//dev.azure.com/fabrikamfiber`）を取得し、常に1つのプロジェクトコレクションを持っています。
組織は、コレクション内に多くのプロジェクトを持つことができます。

Azure DevOps Serverでコレクションを作成する場合は、Azure DevOps Servicesで組織を作成することをお勧めします。 次のシナリオが適用されます。

- 組織ごとにAzure DevOps Servicesユーザーを購入できます―有料ユーザーは、支払いが行われた組織にのみアクセスできます。多くの組織へのアクセスが必要なユーザーがいる場合、Visual Studioサブスクリプションは魅力的なオプションです。Visual Studioサブスクライバーは、任意の数の組織に無料で追加できます。また、単一の組織にグループ化された多くの組織がアクセスできるようにする他の方法も検討しています。
- 現在、組織を1つずつ管理する必要があります。 多くの組織がある場合、このプロセスは面倒です。

詳細：[Azure DevOpsで組織構造を計画する](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/plan-your-azure-devops-org-structure?view=azure-devops)

### Azure DevOps Serverは、デプロイ、プロジェクトコレクション、およびプロジェクトを使用してスケーリングします

Azure DevOps Serverには、データのスコープとスケーリングに関する次の3つのオプションがあります：デプロイ、プロジェクトコレクション、プロジェクト。 最も単純なケースでは、デプロイメントは単なるサーバーです。

ただし、デプロイはより複雑になる可能性があります。

- SQLが別のマシンに分割される2サーバーへのデプロイ
- 多数のサーバーを備えた高可用性ファーム

プロジェクトコレクションは、セキュリティと管理、および物理的なデータベース境界のコンテナとして機能します。 また、関連するプロジェクトをグループ化するためにも使用されます。

最後に、プロジェクトは、ソースコード、作業項目などを含む個々のソフトウェアプロジェクトの資産をカプセル化するために使用されます。

詳細：[Azure DevOpsで組織構造を計画する](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/plan-your-azure-devops-org-structure?view=azure-devops)

## 認証

Azure DevOps Servicesでは、パブリックインターネット（`https://contoso.visualstudio.com` など）を介して接続します。 
組織のセットアップに応じて、Microsoftアカウントの資格情報またはAzure ADの資格情報で認証します。 また、Azure ADをセットアップして、多要素認証、IPアドレスの制限などの機能を要求することもできます。

MicrosoftアカウントではなくAzure ADを使用するように組織を構成することをお勧めします。 この方法は、多くのシナリオでより良いエクスペリエンスを提供し、セキュリティを強化するためのオプションを増やします。

詳細：[Azure Active Directoryを使用してAzure DevOps Servicesにアクセスする](https://docs.microsoft.com/ja-jp/azure/devops/organizations/accounts/access-with-azure-ad?view=azure-devops)

## ユーザーおよびグループ管理

Azure DevOps Servicesでは、同様のメカニズムを使用して[ユーザーグループへのアクセス](https://docs.microsoft.com/ja-jp/azure/devops/organizations/accounts/manage-azure-active-directory-groups?view=azure-devops)を提供できます。
Azure ADグループをAzure DevOps Servicesグループに追加できます。
Azure ADの代わりにMicrosoftアカウントを使用する場合は、[ユーザーを1つずつ追加](https://docs.microsoft.com/ja-jp/azure/devops/organizations/accounts/add-organization-users?view=azure-devops)する必要があります。

Azure DevOps Serverでは、Active Directory（AD）グループをさまざまなAzure DevOpsグループ（たとえば、個々のプロジェクトのContributorsグループ）に追加することで、ユーザーにデプロイメントへのアクセスを提供します。
ADグループのメンバーシップは同期されます。 ADでユーザーが追加および削除されると、Azure DevOps Serverへのアクセスも取得および失われます。

## ユーザーアクセス管理

Azure DevOps ServicesとAzure DevOps Serverの両方で、ユーザーに[アクセスレベル](https://docs.microsoft.com/ja-jp/azure/devops/organizations/security/access-levels?view=azure-devops)を割り当てることにより、機能へのアクセスを管理します。
すべてのユーザーに単一のアクセスレベルを割り当てる必要があります。
クラウドサービスとオンプレミスサービスの両方で、無制限の数のステークホルダーにワークアイテム機能への無料アクセスを提供できます。
また、無制限の数のVisual Studioサブスクライバーが追加料金なしですべての基本機能にアクセスできます。 アクセスが必要な他のユーザーに対してのみ料金を支払います。

Azure DevOps Servicesでは、組織内の各ユーザーに[アクセスレベルを割り当て](https://docs.microsoft.com/ja-jp/azure/devops/organizations/accounts/add-organization-users?view=azure-devops)る必要があります。
Azure DevOps Servicesは、サインイン時にVisual Studioサブスクライバーを検証します。VisualStudioサブスクリプションを持たない5人のユーザーに基本アクセスを無料で割り当てることができます。

より多くのユーザーに基本アクセス以上を付与するには、組織の[課金を設定](https://docs.microsoft.com/ja-jp/azure/devops/organizations/billing/set-up-billing-for-your-organization-vs?view=azure-devops)し、より多くの[ユーザーに支払い](https://docs.microsoft.com/ja-jp/azure/devops/organizations/billing/buy-basic-access-add-users?view=azure-devops)ます。
それ以外の場合、他のすべてのユーザーはステークホルダーのアクセス権を取得します。

Azure ADグループを使用してユーザーのグループにアクセスを許可する場合、アクセスレベルは最初のサインイン時に自動的に割り当てられます。
サインインにMicrosoftアカウントを使用するように構成されている組織の場合、各ユーザーにアクセスレベルを明示的に割り当てる必要があります。

Azure DevOps Serverでは、すべての使用は規則を強制しないシステムに基づいています。
ライセンスに基づいてユーザーのアクセスレベルを設定するには、管理ページで[アクセスレベル](https://docs.microsoft.com/ja-jp/azure/devops/organizations/security/change-access-levels?view=azure-devops)を指定します。
たとえば、ライセンスのないユーザーにステークホルダーのアクセスのみを割り当てます。

Azure DevOps Server / TFSクライアントアクセスライセンス（CAL）を持つユーザーは、基本アクセス権を持つことができます。
Visual Studioサブスクライバーは、サブスクリプションに応じて、基本アクセスまたは詳細アクセスのいずれかを持つことができます。
Azure DevOps Serverは、これらのライセンスの検証やコンプライアンスの実施を試みません。

## セキュリティおよびデータ保護

多くの企業は、クラウドへの移行を検討する際に、データ保護について詳しく知りたいと考えています。
Azure DevOps Servicesはプロジェクトの安全性を確保することに取り組んでいます。
このコミットメントを実現するための技術的な機能とビジネスプロセスが用意されています。
データを保護するための手順を実行することもできます。 詳細については、[データ保護の概要](https://docs.microsoft.com/ja-jp/azure/devops/organizations/security/data-protection?view=azure-devops)をご覧ください。

## プロセスのカスタマイズ

サポートされているプロセスモデルに応じて、2つの異なる方法でワークトラッキングエクスペリエンスをカスタマイズします。

- Azure DevOps Servicesの場合、WYSIWYGカスタマイズをサポートする **継承** プロセスモデルを使用します。
- Azure DevOps Serverでは、**継承** プロセスモデルまたは **オンプレミスXML** プロセスモデルを選択できます。これは、作業追跡オブジェクトのXML定義ファイルのインポートまたはエクスポートによるカスタマイズをサポートします。
- Azure DevOps Server 2018以前のバージョンでは、**オンプレミスXML** プロセスモデルにのみアクセスできます。

**オンプレミスXML** プロセスモデルオプションは強力ですが、さまざまな問題を引き起こす可能性があります。
主な問題は、既存のプロジェクトのプロセスが自動的に更新されないことです。

たとえば、Azure DevOps Server 2013では、新しい作業項目の種類やその他のプロセステンプレートの変更に依存するいくつかの新しい機能が導入されました。
2012から2013にアップグレードすると、各プロジェクトコレクションは、これらの変更を含む「in the box」プロセステンプレートのそれぞれの新しいバージョンを取得します。
ただし、これらの変更は既存のプロジェクトに自動的には組み込まれません。
代わりに、アップグレードの完了後、[機能の構成ウィザード](https://docs.microsoft.com/ja-jp/azure/devops/reference/configure-features-after-upgrade?view=azure-devops)またはより手動のプロセスを使用して、各プロジェクトに変更を含める必要があります。

Azure DevOps Servicesでこれらの問題を回避するために、カスタムプロセステンプレートと `witadmin.exe` ツールは常に無効になっています。
このアプローチにより、Azure DevOps Servicesのアップグレードごとにすべてのプロジェクトを自動的に更新できます。
一方、製品チームは、簡単かつ継続的にサポートできる方法でカスタマイズプロセスを可能にするための作業に懸命に取り組んでいます。
私たちは先程、これらの変更の最初のものを紹介しましたが、さらに変更が行われています。

新しいプロセスカスタマイズ機能を使用すると、Webユーザーインターフェイス（UI）内で直接変更を加えることができます。
プログラムでプロセスをカスタマイズする場合は、RESTエンドポイントを使用してカスタマイズできます。
この方法でプロジェクトをカスタマイズすると、Azure DevOps Servicesのアップグレードでベースプロセスの新しいバージョンをリリースすると、プロジェクトが自動的に更新されます。

詳細については、[ワークトラッキングエクスペリエンスのカスタマイズ](https://docs.microsoft.com/ja-jp/azure/devops/reference/customize-work?view=azure-devops)を参照してください。

## レポート

Azure DevOps ServicesとAzure DevOps Serverは、ソフトウェアプロジェクトの進捗と品質に関する洞察を提供する多くのツールを提供します。 次のツールが含まれています。

- クラウドプラットフォームとオンプレミスプラットフォームの両方で利用可能な[ダッシュボー](https://docs.microsoft.com/ja-jp/azure/devops/report/dashboards/dashboards?view=azure-devops)ドと[軽量チャート](https://docs.microsoft.com/ja-jp/azure/devops/report/dashboards/charts?view=azure-devops)。 これらのツールは、セットアップと使用が簡単です。

Azure DevOps ServicesおよびAzure DevOps Server 2019は、次のサービスへのアクセスも提供します。

- [Analytics サービス](https://docs.microsoft.com/ja-jp/azure/devops/report/powerbi/what-is-analytics?view=azure-devops)および [Analytics ウィジェット](https://docs.microsoft.com/ja-jp/azure/devops/report/dashboards/analytics-widgets?view=azure-devops)。Analytics サービスは、高速の読み取りアクセスおよびサーバーベースの集約用に最適化されています。
- [Microsft Power BI 統合](https://docs.microsoft.com/ja-jp/azure/devops/report/powerbi/overview?view=azure-devops)は、Analytics データのPower BIレポートへの取り込みをサポートし、シンプルさとパワーの組み合わせを提供します。
- [OData のサポート](https://docs.microsoft.com/ja-jp/azure/devops/report/extend-analytics/index?view=azure-devops)は、サポートされているブラウザからAnalyticsサービスに直接クエリを実行し、返されたJSONデータを必要に応じて使用できます。多くのプロジェクトまたは組織全体にまたがるクエリを生成できます。

Analyticsサービスと今後のリリースの詳細については、[レポートのロードマップ](https://docs.microsoft.com/ja-jp/azure/devops/report/powerbi/reporting-roadmap?view=azure-devops)をご覧ください。

[SQL Server Reporting Services（SSRS）レポート](https://docs.microsoft.com/ja-jp/azure/devops/report/sql-reports/reporting-services-reports?view=azure-devops)は、SQL Server Analysis Servicesで構成されている場合、Azure DevOps ServerまたはTFSから利用できます。

## 関連記事

- [基本サービス](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/services?view=azure-devops)
- [クライアント・サーバーツール](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/tools?view=azure-devops)
- [ソフトウェア開発のロール](https://docs.microsoft.com/ja-jp/azure/devops/user-guide/roles?view=azure-devops)
- [Azure DevOps Services の価格](https://visualstudio.microsoft.com/team-services/pricing/)
- [Azure DevOps Server の価格](https://visualstudio.microsoft.com/team-services/tfs-pricing/)


