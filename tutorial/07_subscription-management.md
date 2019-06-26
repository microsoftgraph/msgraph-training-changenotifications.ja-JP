<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="ba443-101">通知のサブスクリプションの有効期限が切れ、定期的に更新する必要がある。</span><span class="sxs-lookup"><span data-stu-id="ba443-101">Subscriptions for notifications expire and need to be renewed periodically.</span></span> <span data-ttu-id="ba443-102">次の手順では、通知を更新する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba443-102">The following steps will demonstrate how to renew notifications</span></span>

<span data-ttu-id="ba443-103">**NotificationsController.cs ファイル > コントローラー**を開く</span><span class="sxs-lookup"><span data-stu-id="ba443-103">Open **Controllers > NotificationsController.cs** file</span></span>

<span data-ttu-id="ba443-104">`NotificationsController`クラスに次の2つのメンバー宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="ba443-104">Add the following two member declarations to the `NotificationsController` class:</span></span>

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;
```

<span data-ttu-id="ba443-105">次の新しいメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="ba443-105">Add the following new methods.</span></span> <span data-ttu-id="ba443-106">これらは、サブスクリプションの有効期限が切れているかどうかを確認するために15秒ごとに実行されるバックグラウンドタイマーを実装します。</span><span class="sxs-lookup"><span data-stu-id="ba443-106">These will implement a background timer that will run every 15 seconds to check if subscriptions have expired.</span></span> <span data-ttu-id="ba443-107">その場合は、更新されます。</span><span class="sxs-lookup"><span data-stu-id="ba443-107">If they have, they will be renewed.</span></span>

```csharp
private void CheckSubscriptions(Object stateInfo)
{
  AutoResetEvent autoEvent = (AutoResetEvent)stateInfo;

  Console.WriteLine($"Checking subscriptions {DateTime.Now.ToString("h:mm:ss.fff")}");
  Console.WriteLine($"Current subscription count {Subscriptions.Count()}");

  foreach(var subscription in Subscriptions)
  {
    // if the subscription expires in the next 2 min, renew it
    if(subscription.Value.ExpirationDateTime < DateTime.UtcNow.AddMinutes(2))
    {
      RenewSubscription(subscription.Value);
    }
  }
}

private void RenewSubscription(Subscription subscription)
{
  Console.WriteLine($"Current subscription: {subscription.Id}, Expiration: {subscription.ExpirationDateTime}");

  var graphServiceClient = GetGraphClient();

  subscription.ExpirationDateTime = DateTime.UtcNow.AddMinutes(5);

  var foo = graphServiceClient
    .Subscriptions[subscription.Id]
    .Request()
    .UpdateAsync(subscription).Result;

  Console.WriteLine($"Renewed subscription: {subscription.Id}, New Expiration: {subscription.ExpirationDateTime}");
}
```

<span data-ttu-id="ba443-108">この`CheckSubscriptions`メソッドは、タイマーによって15秒ごとに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ba443-108">The `CheckSubscriptions` method is called every 15 seconds by the timer.</span></span> <span data-ttu-id="ba443-109">運用のためには、この値をより適切な値に設定して、Microsoft Graph への不要な呼び出しの数を減らす必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba443-109">For production use this should be set to a more reasonable value to reduce the number of unnecessary calls to Microsoft Graph.</span></span>

<span data-ttu-id="ba443-110">この`RenewSubscription`メソッドは、サブスクリプションを更新し、次の2分以内にサブスクリプションの有効期限が切れる場合にのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ba443-110">The `RenewSubscription` method renews a subscription and is only called if a subscription is going to expire in the next two minutes.</span></span>

<span data-ttu-id="ba443-111">メソッド`Get()`を見つけて、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ba443-111">Locate the method `Get()` and replace it with the following code:</span></span>

```csharp
[HttpGet]
public ActionResult<string> Get()
{
    var graphServiceClient = GetGraphClient();

    var sub = new Microsoft.Graph.Subscription();
    sub.ChangeType = "updated";
    sub.NotificationUrl = config.Ngrok + "/api/notifications";
    sub.Resource = "/users";
    sub.ExpirationDateTime = DateTime.UtcNow.AddMinutes(5);
    sub.ClientState = "SecretClientState";

    var newSubscription = graphServiceClient
      .Subscriptions
      .Request()
      .AddAsync(sub).Result;

    Subscriptions[newSubscription.Id] = newSubscription;

    if(subscriptionTimer == null)
    {
        subscriptionTimer = new Timer(CheckSubscriptions, null, 5000, 15000);
    }

    return $"Subscribed. Id: {newSubscription.Id}, Expiration: {newSubscription.ExpirationDateTime}";
}
```

<span data-ttu-id="ba443-112">ファイルの先頭にある既存`using`のステートメントの後に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ba443-112">Add the following statement after the existing `using` statements at the top of the file:</span></span>

```csharp
using System.Threading;
```

### <a name="test-the-changes"></a><span data-ttu-id="ba443-113">変更内容をテストします。</span><span class="sxs-lookup"><span data-stu-id="ba443-113">Test the changes:</span></span>

<span data-ttu-id="ba443-114">Visual Studio Code 内で、[デバッグ **> デバッグ開始**] を選択して、アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ba443-114">Within Visual Studio Code, select **Debug > Start debugging** to run the application.</span></span>
<span data-ttu-id="ba443-115">次の url に移動**http://localhost:5000/api/notifications**します。</span><span class="sxs-lookup"><span data-stu-id="ba443-115">Navigate to the following url: **http://localhost:5000/api/notifications**.</span></span> <span data-ttu-id="ba443-116">これにより、新しいサブスクリプションが登録されます。</span><span class="sxs-lookup"><span data-stu-id="ba443-116">This will register a new subscription.</span></span>

<span data-ttu-id="ba443-117">Visual Studio Code**デバッグコンソール**ウィンドウで、約15秒ごとに、サブスクリプションの有効期限を確認するタイマーに注目してください。</span><span class="sxs-lookup"><span data-stu-id="ba443-117">In the Visual Studio Code **Debug Console** window, approximately every 15 seconds, notice the timer checking the subscription for expiration:</span></span>

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

<span data-ttu-id="ba443-118">数分待ってから、サブスクリプションの更新が必要になったときに次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba443-118">Wait a few minutes and you will see the following when the subscription needs renewing:</span></span>

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

<span data-ttu-id="ba443-119">これは、サブスクリプションが更新され、新しい有効期限を示していることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba443-119">This indicates that the subscription was renewed and shows the new expiry time.</span></span>