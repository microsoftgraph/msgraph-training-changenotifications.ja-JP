<!-- markdownlint-disable MD002 MD041 -->

通知のサブスクリプションの有効期限が切れ、定期的に更新する必要がある。 次の手順では、通知を更新する方法について説明します。

**NotificationsController.cs ファイル > コントローラー**を開く

`NotificationsController`クラスに次の2つのメンバー宣言を追加します。

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;
```

次の新しいメソッドを追加します。 これらは、サブスクリプションの有効期限が切れているかどうかを確認するために15秒ごとに実行されるバックグラウンドタイマーを実装します。 その場合は、更新されます。

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

この`CheckSubscriptions`メソッドは、タイマーによって15秒ごとに呼び出されます。 運用のためには、この値をより適切な値に設定して、Microsoft Graph への不要な呼び出しの数を減らす必要があります。

この`RenewSubscription`メソッドは、サブスクリプションを更新し、次の2分以内にサブスクリプションの有効期限が切れる場合にのみ呼び出されます。

メソッド`Get()`を見つけて、次のコードに置き換えます。

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

ファイルの先頭にある既存`using`のステートメントの後に、次のステートメントを追加します。

```csharp
using System.Threading;
```

### <a name="test-the-changes"></a>変更内容をテストします。

Visual Studio Code 内で、[デバッグ **> デバッグ開始**] を選択して、アプリケーションを実行します。
次の url に移動**http://localhost:5000/api/notifications**します。 これにより、新しいサブスクリプションが登録されます。

Visual Studio Code**デバッグコンソール**ウィンドウで、約15秒ごとに、サブスクリプションの有効期限を確認するタイマーに注目してください。

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

数分待ってから、サブスクリプションの更新が必要になったときに次のように表示されます。

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

これは、サブスクリプションが更新され、新しい有効期限を示していることを示します。