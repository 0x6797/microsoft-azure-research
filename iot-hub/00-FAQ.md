# Azure IoT Hub に関するよくあるかもしれない質問

## 目次

- [Azure IoT Hub とは何ですか？](#q1)
- [IoT Hub を使って何ができますか？](#q12)
- [デバイスの最大登録数は？](#q2)
- [私のデバイスで IoT Hub を利用できますか？](#q10)
- [モジュールとは何ですか？](#q3)
- [デバイスからクラウドへはどの程度のメッセージ送信ができますか？](#q4)
- [デバイスからクラウドへのメッセージサイズの上限は？](#q5)
- [デバイスからクラウドへのメッセージ送信の対応プロトコルは？](#q11)
- [メッセージのフォーマットは？](#q9)
- [メッセージ以外にもデバイスからクラウドへデータを送信する方法は？](#q6)
- [デバイスからのメッセージを IoT Hub 以外のサービスへ送信できますか？](#q7)
- [メッセージの内容によって違うサービスにメッセージを送信できますか？](#q8)

## <a id="q1">Azure IoT Hub とはなんですか？</a>

IoT Hub は非常に簡単にいうと以下の機能を提供しています。

- 百万台レベルのデバイス管理
  - デバイスの状態監視
  - ファームウェア更新の管理
  - デバイスのプロビジョニング（IoT Hub Device Provisioning サービスを使用）
- デバイスからクラウドへのメッセージ送信
  - 他サービスへのルーティング
  - セキュリティ
    - データ暗号化
    - デバイスのなりすまし防止など
- クラウドからデバイスへのメッセージ送信
  - デバイスの状態更新
- メッセージのメトリクスの監視

## <a id="q12">IoT Hub を使って何ができますか？</a>

IoT の一般的なシナリオとそれに対応する Azure のアーキテクチャについては、[IoTソリューションアクセラレータ](https://docs.microsoft.com/ja-jp/azure/iot-accelerators/)にショーケースがあります。

## <a id="#q2">デバイスの最大登録数は？</a>
デバイスとモジュールを併せて、1,000,000 です。ただし[Microsoft サポート](https://azure.microsoft.com/support/options/)に問い合わせることにより、上限数の引き上げは可能です。

## <a id="q10">私のデバイスで IoT Hub を利用できますか？</a>

### Microsoft がサポートしている構成

Azure IoT Hub SDK が使用できるプラットフォームであれば利用可能です。Microsoft では次の構成でテストされ、正式にサポートしています。

| OS | TLS ライブラリ | その他の要件 |
| :---- | :--------- | :----------- |
| Linux | OpenSSL、WolfSSL、BearSSL | Berkley ソケット、POSIX |
| iOS 12.2 | OpenSSL または ネイティブ OSX | OSX 1013.4 でエミュレートされる XCode |
| Windows 10 ファミリ | SChannel | |
| Mbed OS 5.4 | Mbd TLS 2 | [MXChip IoT 開発キット](https://microsoft.github.io/azure-iot-developer-kit/) |
| Azure Sphere OS | WolfSSL | [Azure Sphere MT3620](https://azure.microsoft.com/en-us/services/azure-sphere/get-started/) |
| MacOS High Sierra | | |
| Android API 28 | | Java 8 |

### パートナーがサポートする開発キット

| パートナー | デバイス | リンク | サポート |
| :---------- | :----------- | :------------ | :------------- |
| Espressif | EPS32, EPS8266 | [Esp-azure](https://github.com/espressif/esp-azure) | [GitHub](https://github.com/espressif/esp-azure) |
| Qualcomm | Qualcomm MDM9206 LTE IoT モデム | [Qualcomm LTE for IoT SDK](https://developer.qualcomm.com/software/lte-iot-sdk) | [フォーラム](https://developer.qualcomm.com/forums/software/lte-iot-sdk) |
| ST Microelectoronics | STM32L4, STM32F4 シリーズ | [X-CUBE-AZURE](https://www.st.com/en/embedded-software/x-cube-azure.html) | [サポート](https://www.st.com/content/st_com/en/support/support-home.html) |
| | STM32F7 シリーズ | [P-NUCLEO-AZURE](https://www.st.com/content/st_com/en/products/evaluation-tools/solution-evaluation-tools/communication-and-connectivity-solution-eval-boards/p-nucleo-azure1.html) | |
| | STM32L4 Discovery Kit for IoT ノード | [FP-CLD-AZURE](https://www.st.com/content/st_com/en/products/embedded-software/mcus-embedded-software/stm32-embedded-software/stm32-ode-function-pack-sw/fp-cld-azure1.html) | |
| Texas Instrument | CC3220SF LaunchPad<br />CC3220S LaunchPad<br />CC3235SF LaunchPad<br />CC3235S LaunchPad<br />MSP432E4 LaunchPad | [Azure IoT Plugin for SimpleLink](https://github.com/TexasInstruments/azure-iot-pal-simplelink) | [TI E2E フォーラム](https://e2e.ti.com/)<br />[CC3220 の TIE2E フォーラム](https://e2e.ti.com/support/wireless_connectivity/simplelink_wifi_cc31xx_cc32xx/)<br />[MSP432E3 の TI E2E フォーラム](https://e2e.ti.com/support/microcontrollers/msp430/) |

### SDK を使用せずに IoT Hub に接続する

IoT Hub デバイス SDK を使用できない場合は、HTTPS の要求と応答を送受信できる任意のアプリケーションから、[IoT Hub REST API](https://docs.microsoft.com/en-us/rest/api/iothub/) を使用して IoT Hub に直接接続できます。


## <a id="q3">モジュールとは何ですか？</a>

## <a id="q4">デバイスからクラウドへはどの程度のメッセージ送信ができますか？</a>
エディションによって異なります。

| エディション | スロットル制限 |
| :--------: | :----------------- |
| Free | 1秒あたり 100 送信。または、ユニットごとに 1秒あたり 12 送信 |
| B1 | 1秒あたり 100 送信。または、ユニットごとに 1秒あたり 12 送信 |
| S1 | 1秒あたり 100 送信。または、ユニットごとに 1秒あたり 12 送信 |
| B2 | ユニットごとに 1秒あたり 120 送信 |
| S2 | ユニットごとに 1秒あたり 120 送信 |
| B3 | ユニットごとに 1秒あたり 6,000 送信 |
| S3 | ユニットごとに 1秒あたり 6,000 送信 |

ユニットとはエディションのインスタンスのことです。

たとえば、以下の条件を考えてみましょう。
- S1 を 100 ユニット用意
- 接続デバイスは 1,000

IoT Hub で処理可能なデバイスからの送信は

100 ユニット * 12送信 = 1200 送信/秒 となります。

デバイス同時接続数は 1,000 なので、デバイス 1,000 台が 1秒毎に常にメッセージを送信したとしても、まだ余裕があります（ただし、デバイスが各ユニットに対して均等に接続している場合）。

次に、以下の条件を考えてみましょう
- S3 を　10 ユニット用意
- 接続デバイスは　1,000

10ユニット * 6,000送信 = 60,000 送信/秒

になります。したがって、各デバイスが170ミリ秒毎にメッセージを送信したとしても、理論値としては IoT Hub はメッセージを処理できる計算になります（ただし、各ユニットが均等にメッセージ処理を行っている場合に限る）。

## <a id="q5">デバイスからクラウドへのメッセージサイズの上限は？</a>

4KB 毎にチャンキングされ、最大メッセージサイズは 256KB です。

- [デバイスからクラウドへのメッセージ送信の対応プロトコルは？](#q11)

## <a id="q11">デバイスからクラウドへのメッセージ送信の対応プロトコルは？</a>

以下のプロトコルをネイティブでサポートしています。

- MQTT v3.1
- AMQP
- HTTPS

Azure IoT プロトコル ゲートウェイをカスタムゲートウェイとすることにより、他のプロトコルにも対応可能です（要開発）。

## <a id="q6">メッセージ以外にもデバイスからクラウドへデータを送信する方法は？</a>

デバイス毎に 10個のファイルを同時にアップロードできます。

## <a id="q9">メッセージのフォーマットは？</a>

IoT Hub のメッセージは以下の内容により構成されています。

- 事前定義された一連のシステムプロパティ
- アプリケーションで定義可能なアプリケーションプロパティ。文字列のディクショナリです
- 非透過的なバイナリ本文

## <a id="q7">デバイスからのメッセージを IoT Hub 以外のサービスへ送信できますか？</a>

メッセージ ルーティング機能を使用して、組み込みイベントハブ互換エンドポイントまたはカスタムエンドポイントにメッセージを送信できます。

カスタムエンドポイントを使用すると以下のサービスへ送信できます。

- BLOB ストレージ
- Service Bus キュー
- Service Bus トピック
- Event Hubs

## <a id="q8">メッセージの内容によって違うサービスにメッセージを送信できますか？</a>

カスタムエンドポイントを作成し、その中でルーティングクエリを設定することにより、エンドポイント毎に送信するメッセージをフィルタすることが可能です。