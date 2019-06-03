<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="f98d3-101">コマンドプロンプトを開き、ファイルを作成する権限があるディレクトリに移動し、次のコマンドを実行して、新しい .NET Core 「Microsoft.aspnet.webapi.tracing」 app を作成します。</span><span class="sxs-lookup"><span data-stu-id="f98d3-101">Open your command prompt, navigate to a directory where you have rights to create files, and run the following commands to create a new .NET Core WebApi app.</span></span>

```shell
dotnet new webapi -o msgraphapp
```

<span data-ttu-id="f98d3-102">コマンドが終了したら、次のコマンドを実行して、新しいプロジェクトが正常に実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="f98d3-102">Once the command finishes, run the following commands to ensure your new project runs correctly.</span></span>

```shell
cd msgraphapp
dotnet add package Microsoft.Identity.Client
dotnet add package Microsoft.Graph
dotnet run
```

<span data-ttu-id="f98d3-103">アプリケーションが起動し、次のように出力されます。</span><span class="sxs-lookup"><span data-stu-id="f98d3-103">The application will start and output:</span></span>

```shell
Now listening on: http://localhost:5000
```

<span data-ttu-id="f98d3-104">この出力が表示されない場合、またはエラーメッセージが表示される場合は、続行する前に修正する必要がある[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)に関する問題が開発コンピューターにインストールされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f98d3-104">If you don't see this output, or you see error messages, there is likely a problem with the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) installed on your development machine that needs to be fixed before continuing.</span></span>

<span data-ttu-id="f98d3-105"><kbd>CTRL</kbd>+<kbd></kbd>キーを押して、実行中のアプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="f98d3-105">Stop the application running by pressing <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="f98d3-106">次のコマンドを使用して、Visual Studio Code でアプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="f98d3-106">Open the application in Visual Studio Code using the following command:</span></span>

```shell
code .
```

<span data-ttu-id="f98d3-107">必要なアセットをプロジェクトに追加するかどうかを確認するダイアログボックスが表示されたら、[**はい**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f98d3-107">When a dialog box asks if you want to add required assets to the project, select **Yes**.</span></span>
