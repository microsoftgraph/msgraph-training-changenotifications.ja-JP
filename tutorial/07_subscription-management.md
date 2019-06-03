<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="76c83-101">通知のサブスクリプションの有効期限が切れ、定期的に更新する必要がある。</span><span class="sxs-lookup"><span data-stu-id="76c83-101">Subscriptions for notifications expire and need to be renewed periodically.</span></span>

<span data-ttu-id="76c83-102">**NotificationsController.cs**を開き、 `Get()`メソッドを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="76c83-102">Open **NotificationsController.cs** and replace the `Get()` method with the following code:</span></span>

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;

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

<span data-ttu-id="76c83-103">次の using ステートメントをファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="76c83-103">Add the following using statement at the top of the file.</span></span>

```csharp
using System.Threading;
```

<span data-ttu-id="76c83-104">上記のコードでは、15秒ごとに起動し、サブスクリプションの有効期限が切れているかどうかを確認するためのバックグラウンドタイマーを追加します。</span><span class="sxs-lookup"><span data-stu-id="76c83-104">This code above adds a background timer that will fire every 15 seconds and check subscriptions to see if they have expired.</span></span>

<span data-ttu-id="76c83-105">次の新しいメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="76c83-105">Add the following new methods:</span></span>

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

<span data-ttu-id="76c83-106">この`CheckSubscriptions`メソッドは、タイマーによって15秒ごとに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="76c83-106">The `CheckSubscriptions` method is called every 15 seconds by the timer.</span></span> <span data-ttu-id="76c83-107">運用環境で使用する場合は、グラフへの不要な呼び出しの数を減らすために、これをより適切な値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76c83-107">For production use this should be set to a more reasonable value to reduce the number of unnecessary calls to Graph.</span></span> <span data-ttu-id="76c83-108">この`RenewSubscription`メソッドは、サブスクリプションを更新し、次の2分以内にサブスクリプションの有効期限が切れる場合にのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="76c83-108">The `RenewSubscription` method renews a subscription and is only called if a subscription is going to expire in the next two minutes.</span></span>

<span data-ttu-id="76c83-109">[デバッグ **> デバッグ開始**] を選択して、アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="76c83-109">Select **Debug > Start debugging** to run the application.</span></span> <span data-ttu-id="76c83-110">次の url `*http://localhost:5000/api/notifications`に移動して、新しいサブスクリプションを登録します。</span><span class="sxs-lookup"><span data-stu-id="76c83-110">Navigate to the following url `*http://localhost:5000/api/notifications` to register a new subscription.</span></span>

<span data-ttu-id="76c83-111">Visual Studio コードの`DEBUG OUTPUT`ウィンドウには、約15秒ごとに次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="76c83-111">You will see the following output in the `DEBUG OUTPUT` window of Visual Studio Code approximately every 15 seconds.</span></span>  <span data-ttu-id="76c83-112">これは、サブスクリプションの有効期限を確認するタイマーです。</span><span class="sxs-lookup"><span data-stu-id="76c83-112">This is the timer checking the subscription for expiry.</span></span>

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

<span data-ttu-id="76c83-113">数分待ってから、サブスクリプションの更新が必要になったときに次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="76c83-113">Wait a few minutes and you will see the following when the subscription needs renewing:</span></span>

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

<span data-ttu-id="76c83-114">これは、サブスクリプションが更新され、新しい有効期限を示していることを示します。</span><span class="sxs-lookup"><span data-stu-id="76c83-114">This indicates that the subscription was renewed and shows the new expiry time.</span></span>
