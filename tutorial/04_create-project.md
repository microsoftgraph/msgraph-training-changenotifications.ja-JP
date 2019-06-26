<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="7f18c-101">コマンドプロンプトを開き、プロジェクトを作成する権限があるディレクトリに移動し、次のコマンドを実行して新しい .NET Core 「Microsoft.aspnet.webapi.tracing」アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f18c-101">Open your command prompt, navigate to a directory where you have rights to create your project, and run the following command to create a new .NET Core WebApi app:</span></span>

```shell
dotnet new webapi -o msgraphapp
```

<span data-ttu-id="7f18c-102">アプリケーションを作成した後、次のコマンドを実行して、新しいプロジェクトが正常に実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="7f18c-102">After creating the application, run the following commands to ensure your new project runs correctly.</span></span>

  ```shell
  cd msgraphapp
  dotnet add package Microsoft.Identity.Client
  dotnet add package Microsoft.Graph
  dotnet run
  ```

  <span data-ttu-id="7f18c-103">アプリケーションが起動し、次の内容が出力されます。</span><span class="sxs-lookup"><span data-stu-id="7f18c-103">The application will start and output the following:</span></span>

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

<span data-ttu-id="7f18c-104"><kbd>CTRL</kbd>+<kbd></kbd>キーを押して、実行中のアプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="7f18c-104">Stop the application running by pressing <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="7f18c-105">次のコマンドを使用して、Visual Studio Code でアプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="7f18c-105">Open the application in Visual Studio Code using the following command:</span></span>

```shell
code .
```

<span data-ttu-id="7f18c-106">プロジェクトに必要なアセットを追加するかどうかを確認するダイアログボックスが Visual Studio code に表示された場合は、[**はい**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7f18c-106">If Visual Studio code displays a dialog box asking if you want to add required assets to the project, select **Yes**.</span></span>
