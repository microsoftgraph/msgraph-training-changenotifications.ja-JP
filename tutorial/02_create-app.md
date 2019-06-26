<!-- markdownlint-disable MD002 MD041 -->

この演習では、Azure Active Directory 管理センターを使用して、新しい Azure AD web アプリケーション登録を作成し、必要なアクセス許可スコープに対して管理者の同意を付与します。

1. ブラウザーを開き、 [Azure Active Directory 管理センター (https://aad.portal.azure.com)](https://aad.portal.azure.com)) に移動します。 **職場または学校のアカウント**を使用してログインします。

1. 左側のナビゲーションで [ **Azure Active Directory** ] を選択し、[**管理**] の下にある [**アプリの登録**] を選択します。

    ![アプリの登録のスクリーンショット](./images/aad-portal-home.png)

1. **[新規登録]** を選択します。 [**アプリケーションの登録**] ページ

    ![アプリの登録ページのスクリーンショット](./images/aad-portal-newapp.png)

    値を次のように設定します。

    - **Name**: graphnotificationtutorial
    - **サポートされているアカウントの種類**: 任意の組織ディレクトリ内のアカウントと個人の Microsoft アカウント
    - **リダイレクト URI**: Web >http://localhost

    ![[アプリケーションの登録] ページのスクリーンショット](./images/aad-portal-newapp-01.png)

    [**登録**] を選択します。

1. **Graphnotificationtutorial**ページで、**アプリケーション (クライアント) id**と**ディレクトリ (テナント) id**の値をコピーします。保存するには、次の手順を実行する必要があります。

    ![新しいアプリの登録のアプリケーション ID のスクリーンショット](./images/aad-portal-newapp-details.png)

1. [ **> 証明書 & シークレットを管理**する] を選択します。 

    [**新しいクライアントシークレット**] を選択します。

    [**説明**] に値を入力して、[**有効期限**] のオプションの1つを選択し、[**追加**] を選択します。

    ![[クライアントシークレットの追加] ダイアログのスクリーンショット](./images/aad-portal-newapp-secret.png)

    ![[クライアントシークレットの追加] ダイアログのスクリーンショット](./images/aad-portal-newapp-secret-02.png)

1. クライアント シークレットの値をコピーしてから、このページから移動します。 次の手順で行います。

    > [!IMPORTANT]
    > このクライアント シークレットは今後表示されないため、今必ずコピーするようにしてください。

    ![新しく追加されたクライアントシークレットのスクリーンショット](./images/aad-portal-newapp-secret-03.png)

1. [ **Manage > API Permissions**] を選択します。

    [**アクセス許可の追加**] を選択し、[ **Microsoft Graph**] を選択します。

    ![Microsoft Graph サービスを選択するスクリーンショット](./images/aad-portal-newapp-graphscope.png)

    [**アプリケーションのアクセス許可**] を選択し、**ユーザー**グループを展開して、[**すべて**のスコープ] を選択します。

    [**アクセス許可の追加**] を選択して変更を保存します。

    ![Microsoft Graph スコープを選択するスクリーンショット](./images/aad-portal-newapp-graphscope-02.png)

    ![新しく追加されたクライアントシークレットのスクリーンショット](./images/aad-portal-newapp-graphscope-03.png)

アプリケーションは、**ユーザーのすべて**のスコープでアプリケーションのアクセス許可を要求します。 このアクセス許可には、管理者の同意が必要です。

[ **Contoso に対する管理者の同意を付与**する] を選択し、[**はい**] を選択して、このアプリケーションに同意し、指定した範囲を使用してテナントへのアプリケーションアクセス権を付与します。

![スクリーンショットの承認済み管理者の同意](./images/aad-portal-newapp-graphscope-04.png)
