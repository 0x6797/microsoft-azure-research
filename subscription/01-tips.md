# 課金に関するヒント

## 目次

- [全体の支出ではなく支出の項目を絞り込みたい](#q-filter)

## <a id="q-filter">全体の支出ではなく支出の項目を絞り込みたい</a>

リソースグループとタグを活用します。

たとえば、あるプロジェクトをひとつのリソースグループ `SomeProjectRG` にまとめ、以下のリソースの各タグにひとつのグループ名 `VMGroup` に `仮想マシン名-Group` と設定した例で説明します。

- 仮想マシン
- 仮想ネットワーク
- ネットワークインターフェイス
- ディスク

これで、Azure ポータルより、**サブスクリプション** から **リソースグループ**、**SomeProjectRG**、**コスト分析** を選択し、フィルターで **タグ** を選択肢、`vmgroup`、`仮想マシン-Group` を選択することで、項目に絞り込んだ支出額の把握ができます。