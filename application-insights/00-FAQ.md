# Application Insights に関するよくありそうな質問

## 目次

- [Application Insights とは何ですか？](#q-about)
- [Application Insights はどう利用されるのですか？](#q-about2)
- [Application Insights は何を監視するのですか？](#q-monitoring)
- [アプリに監視モジュールをインストールするのですか？](#q-module)
- [Application Insights SDK のオーバーヘッドが気になります…](#q-overhead)
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

## <a id="q-price">Application Insights の価格について教えて下さい</a>

Application Insights はアプリケーションが送信した利用統計情報のボリュームと、選択した Web テストの実行回数に基づいて課金されます。

| 機能 | 含まれている無料ユニット | 料金 |
| :---- | :----- | :----- |
| データインジェスト | 顧客あたり 5 GB/月 | 374.08 JPY/GB |
| データ保持 | 90日 | 16.80 JPY/GB |
| 複数ステップ Web テスト | なし | 1,120 JPY/テスト/月 |
| Web テストの ping | 無制限 | 無料 |
