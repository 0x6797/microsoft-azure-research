# 継続的インテグレーションおよびデリバリをセットアップする

これは、Azure Pipelinesを使用してGitHubリポジトリを構築するためのステップバイステップガイドです。

## 事前条件

- リポジトリを作成できるGitHubアカウント。 持っていない場合は、[無料で作成](https://github.com/)できます。
- Azure DevOps組織。持っていない場合は、[無料で作成](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/pipelines-sign-up?view=azure-devops)できます。 （Azure DevOps組織はGitHub組織とは異なります。組織間の調整が必要な場合は、同じ名前を付けてください。）

## サンプルコードの取得

Azure Pipelinesを使用して、任意の言語で記述されたアプリを構築できます。 このクイックスタートでは、Javaを使用します。

開始するには、次のリポジトリをGitHubアカウントにフォークします。

```
https://github.com/MicrosoftDocs/pipelines-java
```

## 最初の実行

1. Azure DevOps組織にサインインし、プロジェクトに移動します。
1. プロジェクトで、**Pipelines** ページに移動します。 次に、新しいパイプラインを作成するアクションを選択します。
1. 最初にソースコードの場所として **GitHub** を選択して、ウィザードの手順を確認します。
1. サインインするためにGitHubにリダイレクトされる場合があります。その場合は、GitHub資格情報を入力します。
1. リポジトリのリストが表示されたら、目的のサンプルアプリリポジトリを選択します。
1. Azure Pipelinesはリポジトリを分析し、Mavenパイプラインテンプレートを推奨します。 **Save and run** を選択し、**Commit directly to the master branch** を選択して、再び **Save and run** を選択します。
1. 新しい実行が開始されます。 実行が完了するまで待ちます。

## リポジトリにステータスバッジを追加

多くの開発者は、リポジトリにステータスバッジを表示することで、コードの品質を高く維持していることを示したいと考えています。

![Azure Pipelines](azure-pipelines-succeeded.png)

ステータスバッジをクリップボードにコピーするには：

1. Azure Pipelinesで、**Pipelines** ページに移動してパイプラインのリストを表示します。 前のセクションで作成したパイプラインを選択します。
1. パイプラインのコンテキストメニューで、**Status badge** 選択します。
1. ステータスバッジパネルからサンプルマークダウンをコピーします。

クリップボードにマークダウンバッジが表示されたら、GitHubで次の手順を実行します。

1. ファイルのリストに移動し、`Readme.md` を選択します。 編集する鉛筆アイコンを選択します。
1. ファイルの先頭にステータスバッジマークダウンを貼り付けます。
1. 変更を `master` ブランチにコミットします。
1. リポジトリの説明にステータスバッジが表示されることに注意してください。

**バッジへの匿名アクセスを許可する** 設定を構成するには：

1. プロジェクト設定に移動します
1. **Pipelines** の下の **設定** タブを開きます
1. **全般** の下の **バッジへの匿名アクセスを許可する** チェックボックスをオンにします

<div style="background-color:#4527a0; padding: 0.8rem; color:white;">
注意

プライベートプロジェクトでも、匿名バッジアクセスはデフォルトで有効になっています。 匿名バッジアクセスを有効にすると、組織外のユーザーは、バッジステータスAPIを介してプロジェクト名、ブランチ名、ジョブ名、ビルドステータスなどの情報を照会できる場合があります。
</div>

このリポジトリの `Readme.md` ファイルを変更したため、Azure Pipelinesは、リポジトリのルートにある `azure-pipelines.yml` ファイルの構成に従って、コードを自動的に構築します。 Azure Pipelinesに戻り、新しい実行が表示されることを確認します。
編集を行うたびに、Azure Pipelinesは新しい実行を開始します。

## 次の手順

最初のAzure Pipelineの作成方法を学習しました。 これで、選択した言語のパイプラインを構成する準備ができました。

- [.NET Core](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/dotnet-core?view=azure-devops)
- [Containers](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/containers/build-image?view=azure-devops)
- [Go](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/go?view=azure-devops)
- [Java](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/java?view=azure-devops)
- [Node.js](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/javascript?view=azure-devops)
- [Python](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python?view=azure-devops)

または、作成した[パイプラインのカスタマイズ](https://docs.microsoft.com/en-us/azure/devops/pipelines/customize-pipeline?view=azure-devops)に進むことができます。

コンテナでパイプラインを実行するには、[コンテナジョブ](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/container-phases?view=azure-devops)をご覧ください。

GitHubリポジトリの構築の詳細については、[GitHubリポジトリの構築](https://docs.microsoft.com/en-us/azure/devops/pipelines/repos/github?view=azure-devops)を参照してください。

YAMLパイプラインで他にできることについては、[YAMLスキーマリファレンス](https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema?view=azure-devops)をご覧ください。

