# Azure Stream Analytics に関するよくありそうな質問

## 目次

- [Stream Analytics とは何ですか？](#q-about)
- [Stream Analytics はどのような利用が想定されていますか？](#q-about2)

## <a id="q-about">Stream Analytics とは何ですか？</a>

1秒間に何百万もの大量のメッセージを、リアルタイムにデータ分析のために設計された複合イベント処理エンジンです。

## <a id="q-about">Stream Analytics はどのような利用が想定されていますか？</a>

IoT Hub や Event Hub から受け取ったデータを、他のサービスに受け渡すアダプタによく利用されます。

これは、他のサービスのスループットが IoT Hub などからの大量メッセージを処理できない場合に、Stream Analysis が一時キャッシュとしてスループットを調整し、他のサービスの処理ができるタイミングでデータの受け渡しができるためです。

あるいは、ストリーミングデータの異常検出で Azure Machine Learning と連携することもできます。

具体的なソリューションパターンについては [Azure Stream Analytics のソリューションパターン](https://docs.microsoft.com/ja-jp/azure/stream-analytics/stream-analytics-solution-patterns) を参照して下さい。