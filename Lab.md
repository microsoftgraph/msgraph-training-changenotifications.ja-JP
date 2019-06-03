# <a name="using-change-notifications-and-track-changes-with-microsoft-graph"></a>Microsoft Graph による変更通知の使用と変更の追跡

このラボでは、Azure Active Directory (Azure AD) のユーザーアカウントに対して更新が行われたときに、Microsoft Graph から変更通知を受け取る .NET コアコンソールアプリケーションを作成します。 アプリケーションは変更通知サブスクリプションを管理し、Microsoft Graph で変更履歴を使用して、変更が失われないようにします。

## <a name="in-this-lab"></a>このラボの場合

1. [ラボの概要](./tutorial/01_intro.md)
1. [Microsoft Graph のアプリケーションに登録して同意を付与する](./tutorial/02_create-app.md)
1. [Ngrok のインストール](./tutorial/03_ngrok.md)
1. [.NET コアプロジェクトを作成する](./tutorial/04_create-project.md)
1. [HTTP API のコード](./tutorial/05_add-code.md)
1. [アプリケーションを実行する](./tutorial/06_run.md)
1. [通知サブスクリプションの管理](./tutorial/07_subbscription-management.md)
1. [変更のクエリ](./tutorial/08_deltaquery.md)
1. [完了したラボ](./tutorial/09_completed.md)

## <a name="prerequisites"></a>前提条件

このチュートリアルを開始する前に、開発用コンピューターに[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)と[Visual Studio コード](https://code.visualstudio.com/)をインストールしておく必要があります。 インストールされていない場合は、「ダウンロードオプション」の前のリンクを参照してください。

## <a name="completed-exercises"></a>完了した演習

完成したソリューションは、「[デモ](./Demos)」フォルダーに表示されます (行き詰まった場合)。