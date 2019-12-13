# Azure Security Center に関するよくありそうな質問

## 目次

- [Azure Security Center とは何ですか？](#q-about)
- [Azure Security Center は何をしてくれるのですか？](#q-about2)
- [オンプレミス内のサーバーをどうやってセキュリティ強化するのですか？](#q-onpremises)



## <a id="q-about">Azure Security Center とは何ですか？</a>

Security Center はクラウド内およびオンプレミス上のハイブリッド環境全体を保護する高度な脅威防止などのセキュリティ管理システムです。

## <a id="q-about">Azure Security Center は何をしてくれるのですか？</a>

Free と Standard のレベルで提供する機能が違います。主な機能は次のとおりになります。

| 提供機能 | Free | Standard |
| :------ | :----: | :------: |
| 継続的な評価とセキュリティの推奨事項 | ✅ | ✅ |
| Azure Secure Score | ✅　| ✅ |
| Just In Time VM アクセス | 　| ✅ | 
| 適応型アプリケーション制御とネットワーク強化 |  |  ✅ |
| 規制コンプライアンスのダッシュボードとレポート |  | ✅ |
| Azure VM と Azure 以外のサーバーの脅威保護 |  |  ✅ |
| サポートされている PaaS の脅威保護 |  |  ✅ |



## <a id="q-onpremises">オンプレミス内のサーバーをどうやってセキュリティ強化するのですか？</a>

Microsoft monitoring Agent をインストールすることで、Windos サーバーとLinux サーバーのどちらからもセキュリティ情報を収集し Security Center で分析します。