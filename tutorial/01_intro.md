<!-- markdownlint-disable MD002 MD041 -->

このチュートリアルでは、Azure Active Directory (Azure AD) でユーザーアカウントが変更されたときに通知 (webhooks) を使用してクエリを実行し、ユーザーにすべての変更を反映するためにデルタクエリ API を使用してクエリを実行する .NET コアアプリを構築する方法について説明します。最後のクエリが実行されてからのアカウント。

> [!TIP]
> 完成したチュートリアルをダウンロードするだけで済む場合は、 [GitHub リポジトリ](https://github.com/microsoftgraph/msgraph-training-changenotifications)をダウンロードするか、クローンを作成できます。

## <a name="prerequisites"></a>前提条件

このチュートリアルを開始する前に、開発用コンピューターに[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)と[Visual Studio コード](https://code.visualstudio.com/)をインストールしておく必要があります。

> [!NOTE]
> このチュートリアルは、.NET コアバージョン2.2 で記述されています。 このガイドの手順は、他のバージョンでは動作しますが、テストされていません。

## <a name="watch-the-tutorial"></a>チュートリアルを見る

このモジュールは、Office 開発 YouTube チャネルで記録されており、利用できます。

<!-- markdownlint-disable MD033 MD034 -->
<br/>

> [!VIDEO https://www.youtube-nocookie.com/embed/fThiCZmIcMQ]
<!-- markdownlint-enable MD033 MD034 -->

## <a name="feedback"></a>フィードバック

このチュートリアルに関するフィードバックは、 [GitHub リポジトリ](https://github.com/microsoftgraph/msgraph-training-changenotifications)に記入してください。
