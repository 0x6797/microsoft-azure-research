# IoT Hub に関する `az` コマンドのチートシート

## TOC

- [Microsoft Azure IoT Extension for Azure CLI を Cloud Shell に追加する](#1)
- [デバイスを IoT Hub に登録する](#create-device)
- [デバイスの接続文字列を取得する](#query-connection-string)
- [デバイスのシミュレートを行う](#simulate-device)
- [Event Hubs 互換エンドポイントを取得する](#query-event-hub-endpoint)
- [Event Hubs 互換パスを取得する](#query-event-hub-path)
- [サービス主キーを取得する](#query-service-primary-key)
- [サービス接続文字列を取得する](#query-service-connection-string)

## <a id="1">Microsoft Azure IoT Extension for Azure CLI を Cloud Shell に追加する</a>

```bash
az extension add --name azure-cli-iot-ext
```

## <a id="create-device">デバイスを IoT Hub に登録する</a>

```bash
export IoTHub="<IoTHubの名前>"
export DeviceId="<デバイスID>"
az iot hub device-identity create --hub-name ${IoTHub} --device-id ${DeviceId}
```

## <a id="query-connection-string">デバイスの接続文字列を取得する</a>

```bash
export IoTHub="<IoTHubの名前>"
export DeviceId="<デバイスID>"
az iot hub device-identity show-connection-string --hub-name ${IoTHub} --device-id ${DeviceId} --output table
```

## <a id="simulate-device">デバイスのシミュレーションを行う</a>

```bash
export IoTHub="<IoTHubの名前>"
export DeviceId="<デバイスID>"
az iot device simulate -d simulate -d ${DeviceId} -n ${IoTHub}
```

## <a id="query-event-hub-entpoint">Event Hubs 互換エンドポイントを取得する</a>

```bash
az iot hub show --query properties.eventHubEndpoints.events.endpoint --name ${IoTHub}
```

## <a id="query-event-hub-path">Event Hubs 互換パスを取得する</a>

```bash
az iot hub show --query properties.eventHubEndpoints.events.path --name ${IoTHub}
```

## <a id="query-service-primary-key">サービス主キーを取得する</a>

```bash
az iot hub policy show --name service --query primaryKey --hub-name ${IoTHub}
```

## <a id="query-service-connection-string">サービス接続文字列を取得する</a>

```bash
az iot hub show-connection-string --policy-name service --name ${IoTHub} --output table
```