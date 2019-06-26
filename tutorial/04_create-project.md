<!-- markdownlint-disable MD002 MD041 -->

コマンドプロンプトを開き、プロジェクトを作成する権限があるディレクトリに移動し、次のコマンドを実行して新しい .NET Core 「Microsoft.aspnet.webapi.tracing」アプリを作成します。

```shell
dotnet new webapi -o msgraphapp
```

アプリケーションを作成した後、次のコマンドを実行して、新しいプロジェクトが正常に実行されるようにします。

  ```shell
  cd msgraphapp
  dotnet add package Microsoft.Identity.Client
  dotnet add package Microsoft.Graph
  dotnet run
  ```

  アプリケーションが起動し、次の内容が出力されます。

  ```shell
  info: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[0] ...
  info: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[58] ...
  warn: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[35] ...
  info: Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository[39] ...
  Hosting environment: Development
  Content root path: /Users/ac/_play/graphchangenotifications/msgraphapp
  Now listening on: https://localhost:5001
  Now listening on: http://localhost:5000
  Application started. Press Ctrl+C to shut down.
  ```

<kbd>CTRL</kbd>+<kbd></kbd>キーを押して、実行中のアプリケーションを停止します。

次のコマンドを使用して、Visual Studio Code でアプリケーションを開きます。

```shell
code .
```

プロジェクトに必要なアセットを追加するかどうかを確認するダイアログボックスが Visual Studio code に表示された場合は、[**はい**] を選択します。
