<!-- markdownlint-disable MD002 MD041 -->

開発用コンピューターで実行しているアプリケーションに通知を送信するために Microsoft Graph を使用するには、ngrok などのツールを使用して、インターネットから開発マシンへの呼び出しをトンネリングする必要があります。 Ngrok では、ファイアウォール規則を作成することなく、インターネットからの呼び出しをローカルで実行しているアプリケーションに転送できます。

続行する前に、開発用のコンピューターに[ngrok](https://ngrok.com)がインストールされている必要があります。 Ngrok がない場合は、「以前のリンク」にアクセスして、ダウンロードのオプションと手順を参照してください。

コマンドラインから次を実行して、ngrok を実行します。

```shell
ngrok http 5000
```

これは ngrok を開始し、外部 ngrok url からの要求をポート5000の開発用コンピューターにトンネルします。

Https 転送アドレスをコピーします。 その場合は、次の例`https://787b8292.ngrok.io`のようになります。 後で必要になります。

> [!IMPORTANT]
> Ngrok を再起動するたびに、新しいアドレスが生成され、再度コピーする必要があります。

```shell
ngrok by @inconshreveable

Session Status                online
Account                       ???? ???? (Plan: Free)
Version                       2.3.15
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://787b8292.ngrok.io -> http://localhost:5000
Forwarding                    https://787b8292.ngrok.io -> http://localhost:5000

Connections                   ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```
