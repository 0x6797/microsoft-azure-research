# Azure Kubernetes Services (AKS) における Kubernetes の中心概念

## Kubernetes クラスターのアーキテクチャ

- コントロールプレーン
- ノード

コントロールプレーンとノードの間はセキュリティで保護された通信を行う。(暗号化？)

コントロールプレーンには直接アクセスできない。(AKS固有)

- ノードは Azure Virtual Machine である。
    - 対応OSは
        - Ubuntu Linux
        - Windows Server 2019

- ノードのスペックを決めるのはユーザーの責任

- Windows Server ノードではイングレスコントローラーは実行不可（プレビュー中）

- AKS は Helm を使用している。

- 特定のノードのログコレクションには DaemonSet を使うと良い。

- AKS のマスターは シングルテナント
- AKS のマスターにはパブリック　IP が必要

