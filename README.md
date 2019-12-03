# Microsoft Azure の調査

# 概要

以下のサービスを中心に Microsoft Azure を調査します。

![Azure IoT Solution Technology](paas-saas-technologies-solutions.png)

# 各技術要素について

## よくありそうな質問

- IoT
    - [Azure IoT Hub](iot-hub/00-FAQ.md)
    - [Azure IoT Device Provisioning Service](iot-hub-device-provisioning-service/00-FAQ.md)
    - [Azure IoT Edge](iot-edge/00-FAQ.md)
- アプリケーションロジック
    - [Azure Functions](functions/00-FAQ.md)
    - [Azure App Service](app-service/00-FAQ.md)
    - [Azure Logic Apps](logic-apps/00-FAQ.md)
- ストレージ
    - [Azure Blob Storage](blob-storage/00-FAQ.md)
    - [Azure Cosmos DB](cosmos-db/00-FAQ.md)
- 分析
    - [Azure Stream Analytics](stream-analytics/00-FAQ.md)
    - [Azure Time Series Insights](time-series-insights/00-FAQ.md)
    - [Azure HDInsight](hd-insight/00-FAQ.md)
- 運用監視
    - [Azure Monitor](azure-monitor/00-FAQ.md)
    - [Azure Log Analytics](log-analytics/00-FAQ.md)
    - [Azure Application Insights](application-insights/00-FAQ.md)
    - [Azure Automation](automation/00-FAQ.md)
- ID、ユーザーおよびロール管理
    - [Azure Active Directory](azure-ad/00-FAQ.md)]
    - [Azure Role Based Access Control](rbac/00-FAQ.md)
- 開発
    - [Azure DevOps](devops/01-Overview.md)

# Azure IoT Hub を中心とした参照アーキテクチャ

![Azure IoT Hub Reference Archtecture](iot.png)

# Azure IoT Hub のコンセプトモデル

![Azure IoT Hub のコンセプトモデル](azure-iot-hub-concept-model.vpd.png)

# Azure IoT Central、Azure IoT ソリューションアクセラレータ　および Azure IoT Hub の関係

- Azure IoT Central <br />IoT PnP 対応デバイスを用意すれば、すぐ使える Web アプリ
- Azure IoT ソリューションアクセラレータ<br />一般的な IoT シナリオを構築済みの IoT プラットフォーム
- Azure IoT Hub <br />PaaS 製品

# コード

## Azure IoT

- [クイックスタート(C#)](http://158.201.117.62/gitbucket/p0075317/azure-iot-samples-csharp-master)
- [デバイスシミュレータ](http://158.201.117.62/gitbucket/p0075317/device-simulation-dotnet)

## その他

- iPad あるいは iPhone アプリで Azure の状態を見ることができます。
- [Azure Stack Edge](https://azure.microsoft.com/ja-jp/services/databox/edge/)<br />Edge 用ハードウェア。Commercial シリーズ（ブレード）と Rougged シリーズ（現場用）がある。Azure VM と Azure AKS(Kubernetes) クラスタもサポート

### Commercial シリーズ

![Commercialシリーズ](commercial.png)

### Rugged シリーズ

![Rugged シリーズ](rugged.png)