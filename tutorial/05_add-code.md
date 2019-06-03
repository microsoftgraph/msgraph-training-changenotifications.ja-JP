<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="c9a21-101">**Startup.cs**ファイルを開き、次の行をコメントにして ssl リダイレクトを無効にします。</span><span class="sxs-lookup"><span data-stu-id="c9a21-101">Open the **Startup.cs** file and comment out the following line to disable ssl redirection.</span></span>

```csharp
//app.UseHttpsRedirection();
```

### <a name="add-model-classes"></a><span data-ttu-id="c9a21-102">モデルクラスを追加する</span><span class="sxs-lookup"><span data-stu-id="c9a21-102">Add model classes</span></span>

<span data-ttu-id="c9a21-103">アプリケーションは、Microsoft Graph との間でのメッセージのシリアル化 (de) に対して、いくつかの新しいモデルクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c9a21-103">The application uses several new model classes for (de)serialization of messages to/from the Microsoft Graph.</span></span>

<span data-ttu-id="c9a21-104">プロジェクトファイルツリーを右クリックし、[**新しいフォルダー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9a21-104">Right-click in the project file tree and select **New Folder**.</span></span> <span data-ttu-id="c9a21-105">名前の**モデル**を作成する [**モデル**] フォルダーを右クリックして、3つの新しいファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="c9a21-105">Name it **Models** Right-click the **Models** folder and add three new files:</span></span>

- <span data-ttu-id="c9a21-106">**Notification.cs**</span><span class="sxs-lookup"><span data-stu-id="c9a21-106">**Notification.cs**</span></span>
- <span data-ttu-id="c9a21-107">**ResourceData.cs**</span><span class="sxs-lookup"><span data-stu-id="c9a21-107">**ResourceData.cs**</span></span>
- <span data-ttu-id="c9a21-108">**MyConfig.cs**</span><span class="sxs-lookup"><span data-stu-id="c9a21-108">**MyConfig.cs**</span></span>

<span data-ttu-id="c9a21-109">**Notification.cs**の内容を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c9a21-109">Replace the contents of **Notification.cs** with the following:</span></span>

```csharp
using Newtonsoft.Json;
using System;

namespace msgraphapp.Models
{
  public class Notifications
  {
    [JsonProperty(PropertyName = "value")]
    public Notification[] Items { get; set; }
  }

  // A change notification.
  public class Notification
  {
    // The type of change.
    [JsonProperty(PropertyName = "changeType")]
    public string ChangeType { get; set; }

    // The client state used to verify that the notification is from Microsoft Graph. Compare the value received with the notification to the value you sent with the subscription request.
    [JsonProperty(PropertyName = "clientState")]
    public string ClientState { get; set; }

    // The endpoint of the resource that changed. For example, a message uses the format ../Users/{user-id}/Messages/{message-id}
    [JsonProperty(PropertyName = "resource")]
    public string Resource { get; set; }

    // The UTC date and time when the webhooks subscription expires.
    [JsonProperty(PropertyName = "subscriptionExpirationDateTime")]
    public DateTimeOffset SubscriptionExpirationDateTime { get; set; }

    // The unique identifier for the webhooks subscription.
    [JsonProperty(PropertyName = "subscriptionId")]
    public string SubscriptionId { get; set; }

    // Properties of the changed resource.
    [JsonProperty(PropertyName = "resourceData")]
    public ResourceData ResourceData { get; set; }
  }
}
```

<span data-ttu-id="c9a21-110">**ResourceData.cs**の内容を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c9a21-110">Replace the contents of **ResourceData.cs** with the following:</span></span>

```csharp
using Newtonsoft.Json;

namespace msgraphapp.Models
{
  public class ResourceData
  {
    // The ID of the resource.
    [JsonProperty(PropertyName = "id")]
    public string Id { get; set; }

    // The OData etag property.
    [JsonProperty(PropertyName = "@odata.etag")]
    public string ODataEtag { get; set; }

    // The OData ID of the resource. This is the same value as the resource property.
    [JsonProperty(PropertyName = "@odata.id")]
    public string ODataId { get; set; }

    // The OData type of the resource: "#Microsoft.Graph.Message", "#Microsoft.Graph.Event", or "#Microsoft.Graph.Contact".
    [JsonProperty(PropertyName = "@odata.type")]
    public string ODataType { get; set; }
  }
}
```

<span data-ttu-id="c9a21-111">**MyConfig.cs**の内容を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c9a21-111">Replace the contents of **MyConfig.cs** with the following:</span></span>

```csharp
namespace msgraphapp
{
    public class MyConfig
    {
        public string AppId { get; set; }
        public string AppSecret { get; set; }
        public string TenantId { get; set; }
        public string Ngrok { get; set; }
    }
}
```

<span data-ttu-id="c9a21-112">**Startup.cs**ファイルを開き、コンテンツを次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c9a21-112">Open the **Startup.cs** file and replace the contents with the following.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
    var config = new MyConfig();
    Configuration.Bind("MyConfig", config);
    services.AddSingleton(config);
}
```

<span data-ttu-id="c9a21-113">**Appsettings**ファイルを開き、コンテンツを次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c9a21-113">Open the **appsettings.json** file and replace the content the following.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "MyConfig":
  {
    "AppId": "<APP ID>",
    "AppSecret": "<APP SECRET>",
    "TenantId": "<TENANT ID>",
    "Ngrok": "<NGROK URL>"
  }
}
```

<span data-ttu-id="c9a21-114">次の変数を、前の手順でコピーした値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c9a21-114">Replace the following variables with the values you copied earlier:</span></span>

    - <span data-ttu-id="c9a21-115">`<NGROK URL>`以前にコピーした https ngrok url に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9a21-115">`<NGROK URL>` should be set to the https ngrok url you copied earlier.</span></span>
    - <span data-ttu-id="c9a21-116">`<TENANT ID>`たとえば、Office 365 テナント id である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9a21-116">`<TENANT ID>` should be your Office 365 tenant id, for example.</span></span> <span data-ttu-id="c9a21-117">**contoso.onmicrosoft.com**。</span><span class="sxs-lookup"><span data-stu-id="c9a21-117">**contoso.onmicrosoft.com**.</span></span>
    - <span data-ttu-id="c9a21-118">`<APP ID>`、 `<APP SECRET>`アプリケーション登録の作成時に前にコピーしたアプリケーション id とシークレットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9a21-118">`<APP ID>` and `<APP SECRET>` should be the application id and secret you copied earlier when you created the application registration.</span></span>

### <a name="add-notification-controller"></a><span data-ttu-id="c9a21-119">通知コントローラーの追加</span><span class="sxs-lookup"><span data-stu-id="c9a21-119">Add notification controller</span></span>

<span data-ttu-id="c9a21-120">アプリケーションには、サブスクリプションと通知を処理するための新しいコントローラーが必要です。</span><span class="sxs-lookup"><span data-stu-id="c9a21-120">The application requires a new controller to process the subscription and notification.</span></span>

<span data-ttu-id="c9a21-121">`Controllers`フォルダーを右クリックし、[**新しいファイル**] を選択して、コントローラーに**NotificationsController.cs**という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9a21-121">Right-click the `Controllers` folder, select **New File**, and name the controller **NotificationsController.cs**.</span></span>

<span data-ttu-id="c9a21-122">**NotificationController.cs**の内容を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c9a21-122">Replace the contents of **NotificationController.cs** with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using msgraphapp.Models;
using Newtonsoft.Json;
using System.Net;
using System.Net.Http.Formatting;
using System.Threading;
using Microsoft.Graph;
using Microsoft.Identity.Client;
using System.Net.Http.Headers;

namespace msgraphapp.Controllers
{
  [Route("api/[controller]")]
  [ApiController]
  public class NotificationsController : ControllerBase
  {
    private readonly MyConfig config;

    public NotificationsController(MyConfig config)
    {
      this.config = config;
    }

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

      return $"Subscribed. Id: {newSubscription.Id}, Expiration: {newSubscription.ExpirationDateTime}";
    }

    public ActionResult<string> Post([FromQuery]string validationToken = null)
    {
      // handle validation
      if(!string.IsNullOrEmpty(validationToken))
      {
        Console.WriteLine($"Received Token: '{validationToken}'");
        return Ok(validationToken);
      }

      // handle notifications
      using (StreamReader reader = new StreamReader(Request.Body))
      {
        string content = reader.ReadToEnd();

        Console.WriteLine(content);

        var notifications = JsonConvert.DeserializeObject<Notifications>(content);

        foreach(var notification in notifications.Items)
        {
          Console.WriteLine($"Received notification: '{notification.Resource}', {notification.ResourceData?.Id}");
        }
      }

      return Ok();
    }

    private GraphServiceClient GetGraphClient()
    {
      var graphClient = new GraphServiceClient(new DelegateAuthenticationProvider((requestMessage) => {

          // get an access token for Graph
          var accessToken = GetAccessToken().Result;

          requestMessage
              .Headers
              .Authorization = new AuthenticationHeaderValue("bearer", accessToken);

          return Task.FromResult(0);
      }));

      return graphClient;
    }

    private async Task<string> GetAccessToken()
    {
        ClientCredential clientCredentials = new ClientCredential(secret: config.AppSecret);

        var app = new ConfidentialClientApplication(
            clientId: config.AppId,
            authority: $"https://login.microsoftonline.com/{config.TenantId}",
            redirectUri: "https://daemon",
            clientCredential: clientCredentials,
            userTokenCache: null,
            appTokenCache: new TokenCache()
        );

        string[] scopes = new string[] { "https://graph.microsoft.com/.default" };

        var result = await app.AcquireTokenForClientAsync(scopes);

        return result.AccessToken;
    }
  }
}
```

<span data-ttu-id="c9a21-123">すべてのファイルを**保存**します。</span><span class="sxs-lookup"><span data-stu-id="c9a21-123">**Save** all files.</span></span>