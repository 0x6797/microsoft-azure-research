# Azure Active Directory に関するよくありそうな質問

## 目次

- [Azure Active Directory とは何ですか？](#q-about)
- [Azure AD は誰が利用するのですか？](#q-users)
- [Azure AD の用語が独特でよくわかりません…](#q-terms)
- [Azure AD にはどんな機能があるんですか？](#q-features)
- [従来のオンプレミスの Active Directory とは違うのですか？](#q-onpremise-ad)
- [AWS の IAM と同じですか？](#q-iam)
- [VPN との違いはなんですか？](#q-vpn)
- [シングルサインオンができるという理解でいいですか？](#q-sso)
- [条件付きアクセスはどのようなことができるのですか？](#q-conditional-access)
- [Priviledged Identity Management とは何ですか？](#q-pim)
- [Linux でも Azure AD の認証はできますか？](#q-linux)
- [Azure AD のライセンスについて、それぞれの違いを教えて下さい](#q-licenses)
- [パスワードレス認証](#q-passwordless)


## <a id="q-about">Azure Active Directory とは何ですか？</a>

Azure Active Directory(Azure AD)は、クラウドベースの ID およびアクセス管理サービスであり、次のリソースへのサインインとアクセスを支援します。

- Microsoft Office 365、Azure Portal、その他の SaaS アプリケーションなど、外部リソース
- 企業ネットワークとイントラネット上のアプリや、自分の組織で開発したクラウドアプリなどの内部リソース

- [Azure AD は誰が利用するのですか？](#q-users)

## <a id="q-users">Azure AD は誰が利用するのですか？</a>

Azure AD は次の利用者を想定しています。

| 利用者 | 説明 |
| :----- | :------ |
| IT 管理者 | Azure AD を使用して自社のアプリやアプリリソースのアクセス制御をします。たとえば、重要な組織リソースへのアクセス時にマルチファクター認証を必須にすることができます。Azure AD と既存の Windows Server AD とクラウドアプリ（Office 365など）の間のユーザープロビジョニングを自動化できます。 |
| アプリ開発者 | アプリ開発者は、アプリにシングルサインオンを追加するための標準ベースのアプローチとして Azure AD を使用できます。 |
| Microsoft 365、Office 365、Azure または Dynamic CRM Online の購読者 | すでに Azure AD を使用しています。 |

## <a id="q-terms">Azure AD の用語が独特でよくわかりません…</a>

Azure AD をよく理解するために、次の用語の意味を確認して下さい。

| 用語または概念 | 説明 |
| :-------- | :-------- |
| ID | 認証を受けることができるオブジェクト。ID は、ユーザー名とパスワードを持つユーザーの可能性があります。ID には秘密キーまたは証明書による認証を必要とする可能性があるアプリケーションまたはその他のサーバーも含まれます。 |
| アカウント | データが関連付けられている ID。ID なしではアカウントを持つことができません。 |
| Azure AD アカウント | Azure AD またはそれ以外の Microsoft クラウドサービス（Office 365など）を通じて作成される ID です。ID は Azure AD に補完され、組織のクラウドサービスのサブスクリプションで利用できます。このアカウントは、職場まてゃ学校のアカウントと呼ばれることもあります。（個人アカウントではないらしい） |
| Azure サブスクリプション | Azure クラウドサービスの支払いに使用されます。多数のサブスクリプションを利用いただけます。サブスクリプションはクレジットカードにリンクされます。 |
| Azure テナント | Azure AD の信頼された専用インスタンスであり、組織が Microsoft Azure、Microsoft Intune、Office 365 などの Microsoft クラウドサービスのサブスクリプションにサインアップしたときに自動的に作成されます。ひとつの Azure テナントは単一の組織を表します。 |
| シングルテナント | 専用の環境で他のサービスにアクセスする Azure テナントは単一のテナントとみなされます。 |
| マルチテナント | 複数の組織の共用環境で他のサービスにアクセスする Azure テナントは、マルチテナントとみなされます。 |
| Azure AD ディレクトリ | Azure の各テナントには、信頼された専用の Azure AD ディレクトリが用意されます。Azure AD ディレクトリはテナントのユーザー、ユーザーグループおよびアプリを含み、テナントリソースに対して ID およびアクセス管理機能を実行するために使用されます。 |
| カスタムドメイン | 新しい Azure AD ディレクトリには、必ず `domainname.onmicrosoft.com` という初期ドメイン名がつけられます。その初期の名前に加えて、組織のドメイン名をリストに追加することもできます。カスタムドメイン名を追加すると、`user@****.com` などの馴染みのあるユーザー名を作成するのに役立ちます。 |
| アカウント管理者 | この従来のサブスクリプション管理者ロールは、概念亭には課金の所有者です。このロールは Azure アカウントセンターにアクセスでき、アカウント内の全サブスクリプションの管理を可能にします。 |
| サービス管理者 | この従来のサブスクリプション管理者ロルでは、アクセスを含め、すべての Azure リソースを管理することができます。このロールはサブスクリプションスコープで所有者ロールを割り当てられているユーザーと同等のアクセス権を持ちます。 |
| Owner | このロールは、アクセスを含め、すべての Azure リソースを管理するのに役立ちます。Azure リソースへのきめ細かなアクセス管理を提供するロールベースアクセス制御（RBAC）と呼ばれる新しい認可システムをベースに構築されています。 |
| Azure AD の全体管理者 | この管理者ロールは、Azure AD テナントを作成したユーザーに自動的に割り当てられます。全体管理者は、Azure AD と Azure AD にフェデレーションされたすべてのサービス（Exchange Online、SharePoint Online、Skype for Buisiness Online など）に対して、すべての管理機能を実行できます。全体管理者は複数人配置することができますが、管理者ロールをユーザーに割り当てることができるのは全体管理者にかぎられます。 |
| Microsoft アカウント | Outlook、OneDrive、Xbox LIVE、Office 365 など、コンシューマー向けの Microsoft 製品とクラウドサービスへのアクセスを提供する個人アカウントです。 |

## <a id="q-features">Azure AD にはどんな機能があるんですか？</a>

Azure AD ライセンスを選択すると、組織向けの次の機能の一部またはすべてにアクセスできるようになります。

| カテゴリ | 説明 |
| :------- | :-------- |
| アプリケーション管理 | アプリケーションプロキシ、シングルサインオン、マイアプリポータル（別称：アクセスパネル）、SaaS アプリを使用して、クラウドおよびオンプレミスのアプリを管理します。 |
| 認証 | Azure Active Directory のセルフサービスのパスワードリセット、Multi-Factor Authentication、カスタムの禁止パスワードリスト、スマートロックアウトを管理します。 |
| B2B | 自社データの管理を続けながら、ゲストユーザーと外部パートナーを管理します。 |
| B2C | アプリの使用時にユーザーがサインアップおよびサインインする方法や自分のプロファイルを管理する方法をカスタマイズして制御します。 |
| 条件付きアクセス | クラウドアプリへのアクセスを管理します。 |
| 開発者用の Azure Active Directory | すべての Microsoft ID にサインインし、Microsoft Graph、その他の Microsoft API、またはカスタム API を呼び出すトークンを取得するアプリを構築します。 |
| デバイスの管理 | クラウドまたはオンプレミスのデバイスが会社のデータにアクセスする方法を管理します。 |
| ドメインサービス | ドメインコントローラーを使用せずにドメインに Azure 仮想マシンを参加させます。 |
| エンタープライズユーザー | グループと管理者のロールを使用して、ライセンスの割り当てとアプリへのアクエスを管理し、委任を設定します。 |
| ハイブリッド ID | Azure Active Directory Connect と Connect Health を使用して、場所（ウラウドまたはオンプレミス）に関係なく、すべてのリソースに対する認証と認可のための単一のユーザー ID を提供します。 |
| Identity Governance | 従業員、ビジネスパートナー、ベンダー、サービス、およびアプリのアクセス制御を通じて、組織の ID を管理します。アクセスレビューを実行することもできます。 |
| Identity Protection | 組織の ID に影響を及ぼす潜在的な脆弱性を検出する他、疑わしいアクションに対応するようにポリシーを構成し、適切なアクションを行って解決します。 |
| Azure リソースのマネージド ID | Key Vault を含む、任意の Azure AD でサポートされている認証サービスに対して認証できる、Azure AD の自動化されたマネージド ID を Azure サービスに提供します。 |
| Privileged Identity Management | 組織内でのアクセスを管理、制御、および監視します。この機能には、Azure AD と Azure のリソースへのアクセスと、その他 Microsoft のクラウドサービス（Office 365、Intune など）へのアクセスが含まれます。 |
| レポートと監視 | 環境におけるセキュリティや使用パターンに関する分析情報を得ることができます。 |

## <a id="q-onpremise-ad">従来のオンプレミスの Active Directory とは違うのですか？</a>

組織のアカウント管理という点では同じですが、使用しているプロトコルなどその他は全く別物です。

## <a id="q-iam">AWS の IAM と同じですか？</a>

AWS の IAM に該当するサービスは RBAC(Role Based Access Control)です。

## <a id="q-vpn">VPN との違いはなんですか？</a>

VPN は企業ネットワーク内のセキュリティが安全という前提に成り立っていますが、Azure AD はゼロトラストネットワーキングを前提にしています。つまり、「侵入されることを前提にしたセキュリティ」モデルです。

## <a id="q-sso">作成した Web アプリにシングルサインオンができるという理解でいいですか？</a>

自社システム、作成した Web アプリ、SaaS アプリ、AWS などの他のクラウドへのシングルサインオンができます。

## <a id="q-conditional-access">条件付きアクセスはどのようなことができるのですか？</a>

一例として、以下のような条件で条件付きアクセスを設定できます。

- 特定のユーザーまたはグループか？
- 信頼された IP アドレス範囲か？違う国の IP からのアクセスではないか？
- 登録されたデバイスあるいは特定の状態であるとマークされたデバイスか？
- Azure　AD に参加しているデバイスか？
- 承認済みのクライアントアプリからのアクセスか？
- マルチファクター認証が必要か？

## <a id="q-pim">Priviledged Identity Management とは何ですか？</a>

重要なリソースへのアクセスや SaaS アプリケーションに対する特権操作を時間ベースおよび承認ベースのロールによって管理する機能です。これにより対象リソースにたいする過剰、不要または誤用であるアクセス許可のリスクを軽減し、さらに悪意のあるアクターによるアクセスを可能性を抑えます。

以下に、Privileged Identity Management の主な機能を示します。

- Azure AD と Azure のリソースに対する、適時の特権アクセスを提供する
- 開始日と終了日を使用した期限付きアクセス権をリソースに割り当てる
- 特権ロールをアクティブ化するために承認を要求する
- ロールをアクティブ化するためにマルチファクター認証を矯正する
- ユーザーをアクティブ化するのかを把握するために理由を使用する
- 特権ロールがアクティブ化された時に通知を受ける
- 継続してユーザーにロールが必要であることを確認するためにアクセスレビューを実施する
- 社内監査または外部監査に使用する監査履歴をダウンロードする

この機能を使用するには Azure AD Premium P2 ライセンスが必要です。

## <a id="q-linux">Linux でも Azure AD の認証はできますか？</a>

できます。デバイスの登録が必要です。

## <a id="q-licenses">Azure AD のライセンスについて、それぞれの違いを教えて下さい</a>

- Azure AD Free<br />クラウドサービスを使用するための必要最低限の機能を提供しています。ユーザーおよびグループ管理、デバイス登録、パスワード管理、マルチファクター認証などが使用できます。ただし、ディレクトリにつき 500,000 オブジェクト、SSOを使用できるアプリは 10個に制限されます。
- Azure AD Premium P1<br />Free の機能に加えて、クラウドとオンプレミスの両方のリソースにアクセスするための機能を提供しています。さらに条件付きアクセス機能、動的グループ、Microsoft Identity Manager の機能を提供しています。
- Azure AD Premium P2<br />Premium P1 の機能に加えて、ID に関する危険なアクティビティの自動検知、制限された情報に対するアクセス権管理の機能を提供します。
- 従量課金<br />コンシューマー向けのサービスのための ID およびアクセス管理のための Azure AD B2C などの機能ライセンスを別途取得することができます。

価格については、次の表になります。

| プラン | 価格 |
| :----- | ----: |
| Free | 無料 |
| Premium P1 | 672 JPY/月 |
| Premium P2 | 1,008 JPY/月 |