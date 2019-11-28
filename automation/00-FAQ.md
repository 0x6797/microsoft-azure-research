# Azure Automation に関するよくありそうな質問

## 目次

- [Azure Automation とは何ですか？](#q-about)
- [Azure Automation は具体的にどのような機能を提供するのですか？](#q-about2)
- [プロセスの自動化とは何を自動化してくれるのですか？](#q-process-auto)
- [構成管理とは何の構成を管理してくれるのですか？](#q-configuration-manage)
- [更新管理の更新対象は何ですか？](#q-update-manage)
- [共有リソースとは何ですか？](#q-shared-resources)
- [Automation アカウントとは何ですか？](#q-automation-account)
- [管理のための構成情報やスクリプトを一元管理したいです。](#q-source-control)
- [Azure Automation が対応するオペレーティングシステムは何ですか？](#q-operating-system)
- [Azure Automation の一般的なシナリオについて教えて下さい。](#q-scenario)

## <a id="q-about">Azure Automation とは何ですか？</a>

Azure Automation は Auzre 環境と非 Azure 環境を一貫性を持って展開、運用および使用停止するオートメーションと構成サービスです。

## <a id="q-about2">Azure Automation は具体的にどのような機能を提供するのですか？</a>

Azure Automation は大きく以下のような機能を提供します。

- プロセスの自動化
- 構成管理
- 更新管理

## <a id="q-process-auto">プロセスの自動化とは何を自動化してくれるのですか？</a>

Runbook、PowerShell または Python を使用して、管理タスクを自動化できるようにします。

## <a id="q-configuration-manage">構成管理とは何の構成を管理してくれるのですか？</a>

仮想マシンおよび物理コンピュータのソフトウェア構成、サービス、デーモン、ソフトウェア、設定などです。Desird State Configuration(DSC) を使用して管理します。

## <a id="q-update-manage">更新管理の更新対象は何ですか？</a>

Azure 上あるいはオンプレミス、その他のクラウド間のオペレーティングシステムの更新プログラムです。

## <a id="q-shared-resources">共有リソースとは何ですか？</a>

Azure Automation は、マシン環境を大きな規模で用意に自動化して構成するために一連の共有リソースで構成されます。

| 共有リソース | 説明    |
| :-------- | :------ |
| スケジュール | オートメーションを事前に定義した時間に起動するためにサービス内で使用されます。 |
| モジュール | モジュールは、Azure と他のシステムを管理するために使用されます。Microsoft、サードパーティ、コミュニティ、カスタム定義コマンドレット、および DSC リソース用の Automation アカウントにインポートします。 |
| モジュールギャラリー | Runbook を表示し、それらを Automation アカウントにインポートするための PowerShell ギャラリーへのネイティブな統合 |
| Python 2 パッケージ | Python Runbook で使用される Automation アカウントに Python 2 パッケージを追加します。 |
| 資格情報 | Runbook と構成で実行時に使用される可能性がある秘匿性の高い情報を安全に格納します。 |
| 接続 | 接続リソース無いのシステムに接続する時に、一般的な情報を含む情報の名前／値のペアを格納します。接続は、Runbook と構成の実行時に使用するためにモジュールの作成者によって定義されます。 |
| 証明書 | 証明書を格納し、実行時に認証と展開されるリソースのセキュリティ保護で使用できるようにします。 |
| 変数 | Runbook と構成間で使用できるコンテンツを保持する方法を提供します。Runbook とそれらを参照する構成を変更することなく値を変更できます。 |

## <a id="q-automation-account">Automation アカウントとは何ですか？</a>

Automation を利用するためのリソースです。アカウント内に共有リソースや Runbook、Automation の実行統計情報などを格納します。

## <a id="q-source-control">管理のための構成情報やスクリプトを一元管理したいです。</a>

Runbook または構成を GitHub、Azure Repo に統合する機能があります。

## <a id="q-operating-system">Azure Automation が対応するオペレーティングシステムは何ですか？</a>

Windows および Linux です。

## <a id="q-scenario">Azure Automation の一般的なシナリオについて教えて下さい。</a>

- リソースをビルド／展開する<br />Runbook と Azure Resource Manager テンプレートを使用して、ハイブリッド環境全体に VM を展開します。Jenkins や Azure DevOps などの開発ツールに統合します。
- VM を構成する<br />インフラストラクチャとアプリケーションにとって望ましい構成で Windows および Linux を構成します。
- 監視<br />問題の原因となっているコンピュータの変更を特定し、修復するか管理システムにエスカレートします。
- 保護<br />セキュリティ警告が発生した場合に VM を検疫します。ゲスト要件を設定します。
- 設定<br />チーム用のロールベースのアクセス制御を設定します。未使用のリソースを回収します。
