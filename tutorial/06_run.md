<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="cdbdd-101">[デバッグ **> デバッグ開始**] を選択して、アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-101">Select **Debug > Start debugging** to run the application.</span></span> <span data-ttu-id="cdbdd-102">アプリケーションをビルドすると、ブラウザーウィンドウが404ページに開かれます。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-102">After building the application a browser window will open to a 404 page.</span></span> <span data-ttu-id="cdbdd-103">これは、アプリケーションが web ページではなく API であるため、ok です。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-103">This is ok since our application is an API and not a webpage.</span></span>

<span data-ttu-id="cdbdd-104">ユーザーの変更通知をサブスクライブするには、次の`http://localhost:5000/api/notifications`url に移動します。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-104">To subscribe for change notifications for users navigate to the following url `http://localhost:5000/api/notifications`.</span></span> <span data-ttu-id="cdbdd-105">成功した場合は、次のようなサブスクリプション id を含む出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-105">If successful you will see output that includes a subscription id like the one below:</span></span>

```shell
Subscribed. Id: e2dbfbe1-160b-42b0-9b9f-8ab79bf8dfed
```

<span data-ttu-id="cdbdd-106">アプリケーションは、Office 365 テナントのユーザーに更新が行われたときに Microsoft Graph から通知を受信するようにサブスクライブされました。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-106">Your application is now subscribed to receive notifications from the Microsoft Graph when an update is made on any users in the Office 365 tenant.</span></span>

<span data-ttu-id="cdbdd-107">ブラウザーを開き、 [Microsoft 365 管理センター](https://admin.microsoft.com/AdminPortal)にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-107">Open a browser and visit the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal).</span></span> <span data-ttu-id="cdbdd-108">管理者アカウントを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-108">Sign-in using an administrator account.</span></span> <span data-ttu-id="cdbdd-109">[**ユーザー > アクティブユーザー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-109">Select **Users > Active users**.</span></span> <span data-ttu-id="cdbdd-110">アクティブなユーザーを選択し、**連絡先情報**として [**編集**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-110">Select an active user and select **Edit** for their **Contact information**.</span></span> <span data-ttu-id="cdbdd-111">新しい番号を使用して**携帯電話**の値を更新し、[**保存**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-111">Update the **Mobile phone** value with a new number and Select **Save**.</span></span>

![ユーザーの詳細のスクリーンショット](./images/03.png)

<span data-ttu-id="cdbdd-113">Visual Studio の**デバッグコンソール**に、通知が受信されたことが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-113">In the **DEBUG CONSOLE** of Visual Studio you will see a notification has been received.</span></span> <span data-ttu-id="cdbdd-114">場合によっては、到着までに数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-114">Sometimes this may take a few minutes to arrive.</span></span> <span data-ttu-id="cdbdd-115">出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-115">An example of the output is below:</span></span>

```shell
Received notification: 'Users/7a7fded6-0269-42c2-a0be-512d58da4463', 7a7fded6-0269-42c2-a0be-512d58da4463
```

<span data-ttu-id="cdbdd-116">これは、アプリケーションが、出力で指定されたユーザーの Microsoft Graph から通知を正常に受信したことを示します。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-116">This indicates the application successfully received the notification from the Microsoft Graph for the user specified in the output.</span></span> <span data-ttu-id="cdbdd-117">その後、この情報を使用して、ユーザーの詳細をアプリケーションに同期する場合に、ユーザーの詳細をグラフに表示することができます。</span><span class="sxs-lookup"><span data-stu-id="cdbdd-117">You can then use this information to query the graph for the users full details if you want to synchronize their details into your application.</span></span>