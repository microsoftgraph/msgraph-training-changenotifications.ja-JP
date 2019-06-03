<!-- markdownlint-disable MD002 MD041 -->

このチュートリアルでは、Azure Active Directory (Azure AD) でユーザーアカウントが変更されたときに通知 (webhooks) を使用してクエリを実行し、ユーザーにすべての変更を反映するためにデルタクエリ API を使用してクエリを実行する .NET コアアプリを構築する方法について説明します。最後のクエリが実行されてからのアカウント。

> [!TIP]
> 完成したチュートリアルをダウンロードするだけで済む場合は、 [GitHub リポジトリ](https://github.com/microsoftgraph/msgraph-training-changenotifications)をダウンロードするか、クローンを作成できます。

## <a name="prerequisites"></a>前提条件

このチュートリアルを開始する前に、開発用コンピューターに[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)と[Visual Studio コード](https://code.visualstudio.com/)をインストールしておく必要があります。 インストールされていない場合は、「ダウンロードオプション」の前のリンクを参照してください。

> [!NOTE]
> このチュートリアルは、.NET コアバージョン2.2 で記述されています。 このガイドの手順は、他のバージョンでは動作しますが、テストされていません。

## <a name="feedback"></a>フィードバック

このチュートリアルに関するフィードバックは、 [GitHub リポジトリ](https://github.com/microsoftgraph/msgraph-training-changenotifications)に記入してください。