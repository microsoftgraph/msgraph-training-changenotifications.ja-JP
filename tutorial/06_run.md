<!-- markdownlint-disable MD002 MD041 -->

Visual Studio Code でアプリケーションをデバッグするための起動構成を作成します。

Visual Studio Code 内で、[**デバッグ > 開く構成**] を選択します。

  ![Screencast の VS コードを開く起動構成](./images/vscode-debugapp-01.png)

環境の選択を求めるメッセージが表示されたら、[ **.Net Core**] を選択します。

  ![Screencast of VS Code .NET Core の起動構成を作成する](./images/vscode-debugapp-02.png)

> [!NOTE]
> 既定では、.NET コア起動構成はブラウザーを開き、デバッガーを起動するときにアプリケーションの既定の URL に移動します。 このアプリケーションでは、代わりに NGrok URL に移動します。 起動構成をそのままにしておくと、アプリケーションをデバッグするたびに、破損したページが表示されます。 URL のみを変更するか、起動構成を変更してブラウザーを起動しないようにすることができます。

Visual Studio デバッガーの起動構成を更新します。

  1. Visual Studio Code で、ファイル **. vscode/launch**を開きます。
  1. 既定の構成で、次のセクションを見つけます。

      ```json
      "launchBrowser": {
        "enabled": true
      },
      ```

  1. `enabled`プロパティをに`false`設定します。
  1. 変更内容を保存します。

### <a name="test-the-application"></a>アプリケーションをテストします。

Visual Studio Code で、[デバッグ **> デバッグ開始**] を選択して、アプリケーションを実行します。 VS コードによって、アプリケーションが構築され、星形になります。

**デバッグコンソール**ウィンドウに次のように表示されます。

![VS コードデバッグコンソールのスクリーンショット](./images/vscode-debugapp-03.png)

...ブラウザーを開き、に**http://localhost:5000/api/notifications**移動して、変更通知を購読します。 成功した場合は、次のようなサブスクリプション id を含む出力が表示されます。

![正常なサブスクリプションのスクリーンショット](./images/vscode-debugapp-04.png)

アプリケーションは、Office 365 テナントのユーザーに更新が行われたときに Microsoft Graph から通知を受信するようにサブスクライブされました。

通知をトリガーします。

1. ブラウザーを開き、 [Microsoft 365 管理センター (https://admin.microsoft.com/AdminPortal)](https://admin.microsoft.com/AdminPortal)) に移動します。
1. ログインするように求められた場合は、管理者アカウントを使用してサインインします。
1. [**ユーザー > アクティブユーザー**] を選択します。

    ![Microsoft 365 管理センターのスクリーンショット](./images/vscode-debugapp-05.png)

1. アクティブなユーザーを選択し、**連絡先情報**として [**編集**] を選択します。

    ![ユーザーの詳細を示すスクリーンショット](./images/vscode-debugapp-06.png)

1. **電話番号**の値を新しい番号で更新し、[**保存**] を選択します。

    Visual Studio Code**デバッグコンソール**に、通知が受信されたことが表示されます。 場合によっては、到着までに数分かかる場合があります。 出力の例を次に示します。

    ```shell
    Received notification: 'Users/7a7fded6-0269-42c2-a0be-512d58da4463', 7a7fded6-0269-42c2-a0be-512d58da4463
    ```

これは、アプリケーションが、出力で指定されたユーザーの Microsoft Graph から通知を正常に受信したことを示します。 その後、この情報を使用して、ユーザーの詳細をアプリケーションに同期する場合に、Microsoft Graph についての詳細情報を検索することができます。