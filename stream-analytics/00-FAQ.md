# Azure Stream Analytics に関するよくありそうな質問

## 目次

- [Stream Analytics とは何ですか？](#q-about)
- [Stream Analytics はどのような利用が想定されていますか？](#q-about2)
- [IoT Hub からのメッセージは Azure Functions で処理すれば Stream Analysis を使わなくて良いですか？](#q-comp-funcitons)
- [Kafka を使用しています。Stream Analysis は利用できますか？](#q-kafka)
- [Stream Analysis を利用するに当たって気をつける点はありますか？](#q-only-azure)

## <a id="q-about">Stream Analytics とは何ですか？</a>

1秒間に何百万もの大量のメッセージを、リアルタイムにデータ分析のために設計された複合イベント処理エンジンです。

## <a id="q-about">Stream Analytics はどのような利用が想定されていますか？</a>

IoT Hub や Event Hub から受け取ったデータを、他のサービスに受け渡すアダプタによく利用されます。

これは、他のサービスのスループットが IoT Hub などからの大量メッセージを処理できない場合に、Stream Analysis が一時キャッシュとしてスループットを調整し、他のサービスの処理ができるタイミングでデータの受け渡しができるためです。

あるいは、ストリーミングデータの異常検出で Azure Machine Learning と連携することもできます。

具体的なソリューションパターンについては [Azure Stream Analytics のソリューションパターン](https://docs.microsoft.com/ja-jp/azure/stream-analytics/stream-analytics-solution-patterns) を参照して下さい。

## <a id="q-comp-functions">IoT Hub からのメッセージは Azure Functions で処理すれば Stream Analysis を使わなくて良いですか？</a>

データストリームのデータ単体について処理する場合は Auzre Functions でもニーズを満たせますが、ストリーム全体のデータ分析をしたい場合は、Stream Analysis の使用を検討して下さい。

メッセージを自由に編集できる点では、Azure Functions の使用も有用です。しかし Stream Analysis はデータ分析のために利用されるので、以下の点で有用です。

- データの視覚化
- 一時的および空間的なパターンまたは異常検知アラート
- データの抽出／変換／データストアへのロード
- イベントソーシングパターン
- IoT Edge でのデータ分析

さらにストリーム処理エンジンとして以下の機能を備えています。

- ウィンドウ集計、一時的なデータ結合、一時的なデータ分析関数
- Event Hubs（または IoT Hub）からの入力から、Event Hubs に到着する出力までの待ち時間が 100 ミリ秒以下の高スループット
- ジョブ ダイアグラムを使用したデータ手動のデバッグ


## <a id="q-kafka">Kafka を使用しています。Stream Analysis は利用できますか？</a>

Stream Analysis は Apache Kafka の入力および出力アダプターがありません。

以下の選択肢があります。

- Event Hubs Kafka API を利用して、Stream Analysis に中継する
- Azure Databricks を使用する
- Azure HDInsight の Storm で完全サポートされている Spark Structured Streaming を使用する

## <a id="q-only-azure">Stream Analysis を利用するに当たって気をつける点はありますか？</a>

Azure Stream Analytics は　Microsoft の独占技術です。したがって、他のクラウドやオンプレミスに移植する可能性がある場合は、Stream Analytics ではなく、Spark Structured Stream や Storm などの他のストリーム処理エンジンの使用を検討して下さい。