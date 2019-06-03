<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="2dee2-101">開発用コンピューターで実行しているアプリケーションに通知を送信するために Microsoft Graph を使用するには、ngrok などのツールを使用して、インターネットからコンピューターへの呼び出しをトンネリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dee2-101">In order for the Microsoft Graph to send notifications to your application running on your development machine you need to use a tool such as ngrok to tunnel calls from the internet to your machine.</span></span> <span data-ttu-id="2dee2-102">Ngrok では、ファイアウォール規則を作成することなく、インターネットからの呼び出しをローカルで実行しているアプリケーションに転送できます。</span><span class="sxs-lookup"><span data-stu-id="2dee2-102">Ngrok allows calls from the internet to be directed to your application running locally without needing to create firewall rules.</span></span>

<span data-ttu-id="2dee2-103">続行する前に、開発用のコンピューターに[ngrok](https://ngrok.com)がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dee2-103">Before you continue you should have [ngrok](https://ngrok.com) installed on your development machine.</span></span> <span data-ttu-id="2dee2-104">Ngrok がない場合は、「以前のリンク」にアクセスして、ダウンロードのオプションと手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dee2-104">If you do not have ngrok, visit the previous link for download options and instructions.</span></span>

<span data-ttu-id="2dee2-105">インストールしたら、ngrok を実行します。</span><span class="sxs-lookup"><span data-stu-id="2dee2-105">Once installed, run ngrok.</span></span>

```shell
ngrok http 5000
```

<span data-ttu-id="2dee2-106">これは ngrok を開始し、外部 ngrok url からの要求をポート5000の開発用コンピューターにトンネルします。</span><span class="sxs-lookup"><span data-stu-id="2dee2-106">This will start ngrok and will tunnel requests from an external ngrok url to your development machine on port 5000.</span></span>

<span data-ttu-id="2dee2-107">Https 転送アドレスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="2dee2-107">Copy the https forwarding address.</span></span> <span data-ttu-id="2dee2-108">その場合は、次の例`https://787b8292.ngrok.io`のようになります。</span><span class="sxs-lookup"><span data-stu-id="2dee2-108">In the example below that would be `https://787b8292.ngrok.io`.</span></span> <span data-ttu-id="2dee2-109">後で必要になります。</span><span class="sxs-lookup"><span data-stu-id="2dee2-109">You will need this later.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2dee2-110">Ngrok を再起動するたびに、新しいアドレスが生成され、再度コピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dee2-110">Each time ngrok is restarted a new address will be generated and you will need to copy it again.</span></span>

```shell
ngrok by @inconshreveable

Session Status                online
Account                       Basic
Version                       2.3.15
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://787b8292.ngrok.io -> http://localhost:5000
Forwarding                    https://787b8292.ngrok.io -> http://localhost:5000

Connections                   ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```
