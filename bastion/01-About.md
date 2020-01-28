# Azure Bastion について

[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/bastion/)

## 何ができるか？

- 従来の踏み台サーバの作成が省略できる
  - セキュリテイの向上
  - パブリック IPの節約
- ブラウザ(Azure Portal)を介したリモート接続
  - RDP（リモートデスクトップ）接続 - Windows
  - SSH（接続）                - Linux

ブラウザから HTTPS でリモート接続できるので、社内プロキシに阻まれた環境には特に便利です。

## 対応ブラウザ

- Microsoft Edge
- Google Chrome

## 設定上の注意

仮想ネットワークのセグメントを `/27` 以上にする必要がある。

Bastion 配置用サブネットの名前は `AzureBastionSubnet` で固定

## 現状の制限

- 仮想ネットワークをまたがった Bastion の利用はできません。