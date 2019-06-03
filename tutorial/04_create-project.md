<!-- markdownlint-disable MD002 MD041 -->

コマンドプロンプトを開き、ファイルを作成する権限があるディレクトリに移動し、次のコマンドを実行して、新しい .NET Core 「Microsoft.aspnet.webapi.tracing」 app を作成します。

```shell
dotnet new webapi -o msgraphapp
```

コマンドが終了したら、次のコマンドを実行して、新しいプロジェクトが正常に実行されるようにします。

```shell
cd msgraphapp
dotnet add package Microsoft.Identity.Client
dotnet add package Microsoft.Graph
dotnet run
```

アプリケーションが起動し、次のように出力されます。

```shell
Now listening on: http://localhost:5000
```

この出力が表示されない場合、またはエラーメッセージが表示される場合は、続行する前に修正する必要がある[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)に関する問題が開発コンピューターにインストールされている可能性があります。

<kbd>CTRL</kbd>+<kbd></kbd>キーを押して、実行中のアプリケーションを停止します。

次のコマンドを使用して、Visual Studio Code でアプリケーションを開きます。

```shell
code .
```

必要なアセットをプロジェクトに追加するかどうかを確認するダイアログボックスが表示されたら、[**はい**] を選択します。
