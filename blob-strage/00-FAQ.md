# Azure Blob Storage に関するよくありそうな質問

## 目次

- [Blob Storage とは何ですか？](#q-about)
- [他のストレージサービスと何が違うのですか？](#q-about2)
- [どのくらい大量のデータを格納できるのですか？](#q-volume)
- [AWS S3 のように静的 Web サイトをホスティングできますか？](#q-static-web)
- [BLOB データをフルテキスト検索できますか？](#q-text-search)
- [ストレージアカウントとは何ですか？](#q-account)

## <a id="q-about">Blob Storage とは何ですか？</a>

Blob Storage は、テキストデータやバイナリデータなどの大量の飛行増加データを格納するために最適化されたストレージサービスです。

## <a id="q-about2">他のストレージサービスと何が違うのですか？</a>

大量のデータを格納する点が他のストレージサービスと違います。

他のストレージサービスの一例と特徴は次のとおりです。

| サービス | 特徴 |
| :------ | :------ |
| StorSimple | オンプレミスとのストレージタスク共有 |
| Disk Storage | VM 用のセキュリティ保護された永続ディスク |
| Managed Disks | VM 用の 永続ディスク |
| Queue Storage | メッセージ用(〜64KB のストレージ） |
| Azure Files | SMB 3.0 のファイルシステム |
| Data Box | オフラインで物理ディスクのやり取り |
| Archive Storage | アクセス頻度がごく少ないデータ向けの永続ストレージ |
| NetApp Files | NFS サービス |

## <a id="q-volume">どのくらい大量のデータを格納できるのですか？</a>

Blob Storage は 3種類の BLOB がサポートされ、それぞれの最大サイズは次のとおりです。

- ブロック BLOB<br />約 4.7TB のテキストとバイナリデータが格納されます。
- 追加 BLOB <br />約 4.7TB で、ログ記録などの追加操作用に最適化されています。
- ページ BLOB<br />最大 8TB のランダムアクセスファイルが格納されます。VHD ファイルを格納し、Azure 仮想マシン用のディスクとして機能します。

## <a id="q-account">ストレージアカウントとは何ですか？</a>

ストレージ用の一意の名前空間です。Azure のストレージサービスを使用する際には必ず必要です。

Blob Storage を使用する場合、ストレージアカウント名に対して、一意のエンドポイントが `http://アカウント名.blob.core.windows.net` のように与えられます

ストレージアカウントは5種類あり、それぞれ次のような特徴があります。

- 汎用 v2<br />Azure Storage を使用するほとんどのシナリオに対応
- 汎用 v1<br />互換性用。可能な限り v2 アカウントを使用して下さい。
- ブロック BLOB ストレージ<br />トランザクションレートが高く、比較的小さなオブジェクトが使用される、あるいはストレージ待ち時間が一貫して短いことが要求されるシナリオに推奨されます。
- FileStorage<br />エンタープライズまたはハイパフォーマンススケールアプリケーションにお勧めします。
- BLOB ストレージ<br />互換性用。可能な限り v2 アカウントを使用して下さい。

| ストレージアカウントの種類 | サポートされているサービス | サポートされているパフォーマンスレベル | サポートされているアクセス層 | レプリケーションオプション | デプロイメントモデル | 暗号化 |
| :------ | :------- | :------- | :--------- | :-------- | :--------- | :------- |
| 汎用 v2 | BLOB<br />ファイル<br />キュー<br />テーブル<br />ディスク | Standard<br />Premium | ホット<br />クール<br />アーカイブ | LRS<br />GRS<br />RA-GRS<br />ZRS<br />GZRS<br />RA-GZRS | リソースマネージャー | 暗号化 |
| 汎用 v1 | BLOB<br />ファイル<br />キュー<br />テーブル<br />ディスク | Standard<br />Premium | 該当なし | LRS<br />GRS<br />RA-GRS | リソースマネージャー<br />クラシック | 暗号化 |
| ブロック BLOB ストレージ | BLOB（ブロック BLOB と 追加 BLOB のみ） | Premium | 該当なし | LRS | リソースマネージャー | 暗号化 |
| FileStorage | ファイル専用 | Premium | 該当なし | LRS | リソースマネージャー | 暗号化 |
| BLOB ストレージ | BLOB（ブロック BLOB と追加 BLOB のみ） | Standard | ホット<br />クール<br />アーカイブ | LRS<br />GRS<br />RA-GRS | リソースマネージャー | 暗号化 |

## <a id="q-static-web">AWS S3 のように静的 Web サイトをホスティングできますか？</a>

はい。SSL 証明書を使用しカスタムドメインを使用したい場合は、Azure CDN を使用して下さい。

## <a id="q-text-search">BLOB データをフルテキスト検索できますか？</a>

はい。Azure Cognitive Search を使用して BLOB コンテンツにインデックスを作成しテキスト検索することが可能です。
