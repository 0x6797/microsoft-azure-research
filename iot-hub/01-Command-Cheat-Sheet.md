# IoT Hub に関する `az` コマンドのチートシート

## TOC

- [Microsoft Azure IoT Extension for Azure CLI を Cloud Shell に追加する](#1)
- [デバイスを IoT Hub に登録する](#create-device)
- [デバイスの接続文字列を取得する](#query-connection-string)

## <a href="#1">Microsoft Azure IoT Extension for Azure CLI を Cloud Shell に追加する</a>

```bash
az extension add --name azure-cli-iot-ext
```

## <a href="#create-device>デバイスを IoT Hub に登録する</a>

```bash
export IoTHub="<IoTHubの名前>"
export DeviceId="<デバイスID>"
az iot hub device-identity create --hub-name ${IoTHub} --device-id ${DeviceId}
```

## <a href="#query-connection-string">デバイスの接続文字列を取得する</a>

```bash
export IoTHub="<IoTHubの名前>"
export DeviceId="<デバイスID>"
az iot hub device-identity show-connection-string --hub-name ${IoTHub} --device-id ${DeviceId} --output table
```