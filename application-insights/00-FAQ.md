# Application Insights に関するよくありそうな質問

## 目次

- [Application Insights とは何ですか？](#q-about)
- [Application Insights はどう利用されるのですか？](#q-about2)
- [Application Insights は何を監視するのですか？](#q-monitoring)
- [アプリに監視モジュールをインストールするのですか？](#q-module)
- [Application Insights SDK のオーバーヘッドが気になります…](#q-overhead)
- [Application Insghts は何を収集するのですか？](#q-data)
- [Azure にホストされた Web アプリケーションからしかデータを収集できないのでしょうか？](#q-apps)
- [私の C アプリケーションから Application Insights にデータを送信したいのですが、可能でしょうか？](#q-languages)
- [コードを埋め込むことでしか、Application Insights にデータを送信することができないのでしょうか？](#q-noncode)
- [Application Insights の価格について教えて下さい](#q-price)

## <a id="q-about">Application Insights とは何ですか？</a>

Azure Monitor の機能を使って、複数のプラットフォームで使用できる Web 開発者向けのアプリケーションパフォーマンス管理ツールです。

## <a id="q-about2">Application Insights はどう利用されるのですか？</a>

Application Insights は開発チームがアプリケーションのパフォーマンスや使用状況を把握し、パフォーマンス異常の自動検出やユーザーの動作分析などを行い、アプリケーションの改善に役立ちます。

## <a id="q-monitoring">Application Insights は何を監視するのですか？</a>

- 要求レート、応答時間およびエラー率
- 外部サービスの依存率、応答時間およびエラー率
- アプリケーション例外
- ページビューと読み込みのパフォーマンス
- Web ページからの AJAX 呼び出しレート、応答時間およびエラー率
- ユーザー数とセッション数
- Windows または Linux サーバーのCPU、メモリ、ネットワーク使用率
- Docker または Azure のホスト診断
- アプリケーションの診断トレースログ
- カスタムイベントとメトリック

## <a id="q-module">アプリに監視モジュールをインストールするのですか？</a>

はい。Application Insights SDK をインストールし、Azure Portal から専用キーを設定する必要があります。

## <a id="q-overhead">Application Insights SDK のオーバーヘッドが気になります…</a>

トレース呼び出しはノンブロッキングで、データ送信はバッチ処理された別スレッドで送信されるため、想定されるオーバーヘッドはわずかです。

## <a id="q-data">Application Insights は何を収集するのですか？</a>

Application Insights ではアプリケーションを作成すると、対応するアプリケーションが自動的に Azure monitor Logs に作成されます。

Application Insights のアプリケーションには固定のテーブルセットがあり、追加のテーブルは作成できません。

テーブルについては、次の表のようになります。

| テーブル | 説明 |
| :----- | :----- |
| `availablityResult` | 可用性テストの要約データ |
| `browserTimings` | 受信データの処理にかかった時間などのクライアントのパフォーマンスに関するデータ |
| `customEvents` | アプリケーションで作成されたカスタムイベント |
| `customMetrics` | アプリケーションで作成されとカスタムメトリック |
| `dependencies` | アプリケーションからの外部コンポーネントの呼び出し |
| `exceptions` | アプリケーションランタイムによってスローされた例外 |
| `pageViews` | 各 Web サイトのビューに関するデータとブラウザー情報 |
| `performanceCounters` | アプリケションを支えるコンピューティングリソースのパフォーマンス測定結果 |
| `requests` | 各アプリケーション要求の詳細 |
| `traces` | 分散トレースからの結果 |

## <a id="q-apps">Azure にホストされた Web アプリケーションからしかデータを収集できないのでしょうか？</a>

Azure でホストされている必要はありません。また、Web アプリケーションだけでなく、バックグラウンドコンポーネントや、Web ページ内の JavaScript 自体もインストルメント化できます。

## <a id="q-languages">私の C アプリケーションから Application Insights にデータを送信したいのですが、可能でしょうか？</a>

実際無理です。Application Insigths SDK に対応しているプログラミング言語は次のとおりです。

- .NET
- Java
- Node.js
- Python
- Web ページ内の JavaScript

## <a id="q-noncode">コードを埋め込むことでしか、Application Insights にデータを送信することができないのでしょうか？</a>

実際のアプリケーションではなく、Azure リソースのデータを Application Insights に送信することは可能です。

- Azure 仮想マシンにインストールされている .NET アプリケーション
- Azure 仮想マシンスケールセットにインストールされている .NET アプリケーション
- Azure App Service で実行されている ASP.NET および ASP.NET Core ベースの Web アプリケーション
- Azure クラウドサービスアプリ
- Azure Functions
- Kubernetes アプリケーション
  - AKS
  - Istio が必要
- PowerShell が実行できるオンプレミスのサーバー

## <a id="q-price">Application Insights の価格について教えて下さい</a>

Application Insights はアプリケーションが送信した利用統計情報のボリュームと、選択した Web テストの実行回数に基づいて課金されます。

| 機能 | 含まれている無料ユニット | 料金 |
| :---- | :----- | :----- |
| データインジェスト | 顧客あたり 5 GB/月 | 374.08 JPY/GB |
| データ保持 | 90日 | 16.80 JPY/GB |
| 複数ステップ Web テスト | なし | 1,120 JPY/テスト/月 |
| Web テストの ping | 無制限 | 無料 |
