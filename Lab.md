# <a name="using-change-notifications-and-track-changes-with-microsoft-graph"></a><span data-ttu-id="9a34c-101">Microsoft Graph による変更通知の使用と変更の追跡</span><span class="sxs-lookup"><span data-stu-id="9a34c-101">Using Change Notifications and Track Changes with Microsoft Graph</span></span>

<span data-ttu-id="9a34c-102">このラボでは、Azure Active Directory (Azure AD) のユーザーアカウントに対して更新が行われたときに、Microsoft Graph から変更通知を受け取る .NET コアコンソールアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9a34c-102">In this lab you will create a .NET Core console application that receives change notifications from the Microsoft Graph when an update is made to a users account in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="9a34c-103">アプリケーションは変更通知サブスクリプションを管理し、Microsoft Graph で変更履歴を使用して、変更が失われないようにします。</span><span class="sxs-lookup"><span data-stu-id="9a34c-103">The application will managed the Change Notification subscription and use Track Changes in the Microsoft Graph to ensure no changes are missed.</span></span>

## <a name="in-this-lab"></a><span data-ttu-id="9a34c-104">このラボの場合</span><span class="sxs-lookup"><span data-stu-id="9a34c-104">In this lab</span></span>

1. [<span data-ttu-id="9a34c-105">ラボの概要</span><span class="sxs-lookup"><span data-stu-id="9a34c-105">Introduction to the lab</span></span>](./tutorial/01_intro.md)
1. [<span data-ttu-id="9a34c-106">Microsoft Graph のアプリケーションに登録して同意を付与する</span><span class="sxs-lookup"><span data-stu-id="9a34c-106">Register and grant consent to the application in Microsoft Graph</span></span>](./tutorial/02_create-app.md)
1. [<span data-ttu-id="9a34c-107">Ngrok のインストール</span><span class="sxs-lookup"><span data-stu-id="9a34c-107">Install ngrok</span></span>](./tutorial/03_ngrok.md)
1. [<span data-ttu-id="9a34c-108">.NET コアプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="9a34c-108">Create the .NET Core project</span></span>](./tutorial/04_create-project.md)
1. [<span data-ttu-id="9a34c-109">HTTP API のコード</span><span class="sxs-lookup"><span data-stu-id="9a34c-109">Code the HTTP API</span></span>](./tutorial/05_add-code.md)
1. [<span data-ttu-id="9a34c-110">アプリケーションを実行する</span><span class="sxs-lookup"><span data-stu-id="9a34c-110">Run the application</span></span>](./tutorial/06_run.md)
1. [<span data-ttu-id="9a34c-111">通知サブスクリプションの管理</span><span class="sxs-lookup"><span data-stu-id="9a34c-111">Manage notification subscriptions</span></span>](./tutorial/07_subbscription-management.md)
1. [<span data-ttu-id="9a34c-112">変更のクエリ</span><span class="sxs-lookup"><span data-stu-id="9a34c-112">Query for changes</span></span>](./tutorial/08_deltaquery.md)
1. [<span data-ttu-id="9a34c-113">完了したラボ</span><span class="sxs-lookup"><span data-stu-id="9a34c-113">Completed Lab</span></span>](./tutorial/09_completed.md)

## <a name="prerequisites"></a><span data-ttu-id="9a34c-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="9a34c-114">Prerequisites</span></span>

<span data-ttu-id="9a34c-115">このチュートリアルを開始する前に、開発用コンピューターに[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)と[Visual Studio コード](https://code.visualstudio.com/)をインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a34c-115">Before you start this tutorial, you should have [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/) installed on your development machine.</span></span> <span data-ttu-id="9a34c-116">インストールされていない場合は、「ダウンロードオプション」の前のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a34c-116">If you do not have them installed, visit the previous links for download options.</span></span>

## <a name="completed-exercises"></a><span data-ttu-id="9a34c-117">完了した演習</span><span class="sxs-lookup"><span data-stu-id="9a34c-117">Completed Exercises</span></span>

<span data-ttu-id="9a34c-118">完成したソリューションは、「[デモ](./Demos)」フォルダーに表示されます (行き詰まった場合)。</span><span class="sxs-lookup"><span data-stu-id="9a34c-118">Finished solutions are provided in the [Demos](./Demos) folder if you get stuck.</span></span>