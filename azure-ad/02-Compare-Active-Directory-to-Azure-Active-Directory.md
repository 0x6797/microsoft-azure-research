# Active Directory と Azure Active Directory の比較(詳細)

Azure Active Directory は、クラウド向けの ID およびアクセス管理ソリューションの次の進化系です。


## ユーザー

| コンセプト | Active Directory (AD) | Azure Active Directory |
| :------ | :--------- | :------------ |
| プロビジョニング : 内部ユーザー | 組織は、内部ユーザーを手動で作成するか、Microsoft Identity Manager などで社内または自動プロビジョニングシステムを使用して、HR システムと統合します。 | 既存の AD 組織は Azure AD Connect を使用して ID おクラウドに同期します。Azure AD は、クラウド HR システムからユーザーを自動的に作成するサポートを追加します。<br /> Azure AD は SCIM 対応 SaaS アプリで ID をプロビジョニングして、ユーザーにアクセスを許可するために必要な詳細をアプリに自動的に提供できます。 |
| プロビジョニング : 外部 ID | 組織は、専用の外部 AD フォレストに通常のユーザーとして外部ユーザーを手動で作成し、外部 ID (ゲストユーザー)のライフサイクルを管理するための管理オーバーヘッドをもたらします。 | Azure AD は、外部 ID をサポートする特別なクラスの ID を提供します。Azure AD B2B は、組織ユーザー ID へのリンクを管理して、それらが有効であることを確認します。 |
| 資格情報とグループ | 管理者はユーザーをグループのメンバーにします。その後、アプリとリソースの所有者は、グループにアプリまたはリソースへのアクセスを許可します。 | グループは Azure AD でも使用でき、管理者はグループに使用してリソースにアクセス許可を付与することもできます。Azure AD では管理者はメンバーシップをグループに手動で割り当てるか、クエリを使用してユーザーをグループに動的に含めることができます。<br />管理差は、Azure AD の資格管理を使用して、ワークフローと、必要に応じて時間ベースの基準を使用して、ユザーがアプリとリソースのコレクションにアクセスできるようにします。 |
| 管理者のマネジメント | 組織は、AD のドメイン、組織ユニット、およびグループの組み合わせを使用して、管理するディレクトリとリソースを管理する管理権限を委任します。 | Azure AD は、ロールベースのアクセス制御(RBAC)システムを備えた組み込みロールを提供し、カスタムロールを作成して、ID システムとそれが制御するアプリとリソースへの特権アクセスを委任する機能を提供します。特権 ID 管理（PIM)を使用してロールの管理を強化し、ジャストインタイム、時間制限、またはワークフローベースの特権ロールへのアクセスを提供できます。 |
| 資格情報管理 | Active Directory の資格情報は、パスワード、証明書認証、およびスマートカード認証に基づいています。パスワードは、パスワードの長さ、有効期限、複雑さに基づいたパスワードポリシーを使用して管理されます。 | Azure AD はクラウドとオンプレミスに対して、インテリジェントなパスワード保護を使用します。保護には、スマートロックアウトに加えて、一般的およびカスタムのパスワードフレーズと置換のブロックがう組まれます。<br />Azure AD は、多要素認証と FIDO2 などのパスワードレスのテクノロジーにより、セキュリティを大幅に強化します。 <br />Azure AD はユーザーにセルフサービスのパスワードリセットシステムを提供することにより、サポートコストを削減します。 |

## アプリ

| コンセプト | Active Directory (AD) | Azure Active Directory |
| :------ | :--------- | :------------ |
| インフラストラクチャアプリ | Active Directory は、DNS、DHCP、IPSec、WiFi、NPS、VPNアクセスなど、多くのインフラストラクチャオンプレミスコンポーネントの基盤を形成します。 | 新しいクラウドの世界では、Azure AD は、ネットワークコントロールに依存するのではなく、アプリにアクセスするための新しいコントロールプレーンです。ユーザーが認証する場合、条件付きアクセス(CA)は、必要な条件下でどのユーザーがどのアプリにアクセスできるかを制御します。 |
| 従来のアプリとレガシーアプリ | ほとんどのオンプレミスアプリは、LDAP、Windows 統合認証(NTLM および Kerberos)、またはヘッダーベースの認証を使用してユーザーへのアクセスを制御します。 | Azure AD は、オンプレミスで実行される Azure AD アプリケーションプロキシエージェントを使用して、これらの種類のオンプレミスアプリへのアクセスを提供できます。この方法を使用すると、Azure AD は以降中またはレガシーアプリと共存する必要がある時に、Kerberos を使用してユーザーを認証できます。 |
| SaaS アプリ | Active Directory は SaaS アプリをネイティブにサポートしていないため、AD FS などのフェデレーションシステムが必要です。 | OAuth2、SAML、および WS-\* 認証をサポートする SaaS アプリを統合して、認証に Azure AD を使用できます。 |
| 最新の認証を備えた基幹業務(LOB)アプリ | 組織は Active Directory で AD FS を使用して、最新の認証を必要とする LOB アプリをサポートできます。 | 最新の認証を必要とする LOB アプリは、認証に Azure AD を使用するように構成できます。 |
| 中間層／デーモンサービス | オンプレミス環境で実行されているサービスは、通常 AD サービスアカウントを使用して実行されます。これらのアプリはサービスアカウントの権限を継承します。 | Azure AD はクラウド内の他のワークロードを実行するためのマネージド ID を提供します。これらの ID のライフサイクルは Azure AD によって管理され、リソースプロバイダーに関連付けられているため、他の目的でバックドアアクセスを取得することはできません。 |

## デバイス

| コンセプト | Active Directory (AD) | Azure Active Directory |
| :------ | :--------- | :------------ |
| モバイル | Active Directory はサードパーティのソリューションなしではモバイルデバイスをネイティブにサポートしません。 | Microsoft のモバイルデバイス管理ソリューションである Microsoft Intune は、Azure AD と統合されています。Microsoft Intune は、認証中に評価するために、デバイス状態情報を ID システムに提供します。 |
| Window デスクトップ | Active Directory は、Windows デバイスをドメインに参加させて、グループポリシー、System Center Configuration Manager、またはその他のサードパーティソリューションを使用してデバイスを管理する機能を提供します。　| Windows デバイスは Azure AD に参加できます。条件付きアクセスでは、認証プロセスの一部としてデバイスが Azure AD に参加しているかどうかを確認できます。Windows デバイスは、Microsoft Intune で管理することもできます。この場合、条件付きアクセスでは、アプリへのアクセスを許可する前に、デバイスが準拠している（たとえば、最新のセキュリティパッチやウィルス署名）かどうかを考慮します。 |
| Windows サーバー | Active Directory は、グループポリシーまたはその他の管理ソリューションを使用して、オンプレミスの Windows サーバーに強力な管理機能を提供します。 | Azure の Windows サーバー仮想マシンは、Azure AD Domain Services で管理できます。VM が ID システムのディレクトリまたはリソースにアクセスする必要がある場合、マネージド ID を使用できます。 |
| Linux／Unix ワークロード | Active Directory は、サードパーティソリューション無しで Windows 以外をネイティブにサポートしません。 | Linux／Unix VM は、マネージド ID を使用して ID システムまたはリソースアクセスできます。一部の組織では、これらのワークロードを管理された ID を使用できるクラウドコンテナーテクノロジーに移行します。 |