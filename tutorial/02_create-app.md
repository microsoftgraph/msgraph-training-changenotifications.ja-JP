<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="dffa8-101">この演習では、Azure Active Directory 管理センターを使用して、新しい Azure AD web アプリケーション登録を作成し、必要なアクセス許可スコープに対して管理者の同意を付与します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center and grant administrator consent to the required permission scopes.</span></span>

1. <span data-ttu-id="dffa8-102">ブラウザーを開き、[Azure Active Directory 管理センター](https://portal.azure.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-102">Open a browser and navigate to the [Azure Active Directory admin center](https://portal.azure.com).</span></span> <span data-ttu-id="dffa8-103">**職場または学校のアカウント**を使用してログインします。</span><span class="sxs-lookup"><span data-stu-id="dffa8-103">Login using a **Work or School Account**.</span></span>

1. <span data-ttu-id="dffa8-104">左側のナビゲーションで **[Azure Active Directory]** を選択し、それから **[管理]** で **[アプリの登録 (プレビュー)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations (Preview)** under **Manage**.</span></span>

    ![<span data-ttu-id="dffa8-105">アプリの登録のスクリーンショット</span><span class="sxs-lookup"><span data-stu-id="dffa8-105">A screenshot of the App registrations</span></span> ](./images/01.png)

1. <span data-ttu-id="dffa8-106">**[新規登録]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-106">Select **New registration**.</span></span> <span data-ttu-id="dffa8-107">**[アプリケーションを登録]** ページで、次のように値を設定します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-107">On the **Register an application** page, set the values as follows.</span></span>

    - <span data-ttu-id="dffa8-108">`GraphNotificationTutorial` に **[名前]** を設定します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-108">Set **Name** to `GraphNotificationTutorial`.</span></span>
    - <span data-ttu-id="dffa8-109">**[サポートされているアカウントの種類]** を **[任意の組織のディレクトリ内のアカウントと個人用の Microsoft アカウント]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-109">Set **Supported account types** to **Accounts in any organizational directory and personal Microsoft accounts**.</span></span>
    - <span data-ttu-id="dffa8-110">**[リダイレクト URI]** で、最初のドロップダウン リストを `Web` に設定し、それから `http://localhost` に値を設定します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-110">Under **Redirect URI**, set the first drop-down to `Web` and set the value to `http://localhost`.</span></span>

    ![[アプリケーションの登録] ページのスクリーンショット](./images/02.png)

1. <span data-ttu-id="dffa8-112">[**登録**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-112">Select **Register**.</span></span> <span data-ttu-id="dffa8-113">**Graphnotificationtutorial**ページで、**アプリケーション (クライアント) id**と**ディレクトリ (テナント) id**の値をコピーします。保存するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dffa8-113">On the **GraphNotificationTutorial** page, copy the value of the **Application (client) ID** and **Directory (tenant) ID** save it, you will need them in the next step.</span></span>

    ![新しいアプリの登録のアプリケーション ID のスクリーンショット](./images/03.png)

1. <span data-ttu-id="dffa8-115">**[管理]** で **[証明書とシークレット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-115">Select **Certificates & secrets** under **Manage**.</span></span> <span data-ttu-id="dffa8-116">[**新しいクライアントシークレット**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-116">Select **New client secret**.</span></span> <span data-ttu-id="dffa8-117">[**説明**] に値を入力して、[**有効期限**] のオプションの1つを選択し、[**追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-117">Enter a value in **Description** and select one of the options for **Expires** and select **Add**.</span></span>

    ![[クライアントシークレットの追加] ダイアログのスクリーンショット](./images/04.png)

1. <span data-ttu-id="dffa8-119">クライアント シークレットの値をコピーしてから、このページから移動します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-119">Copy the client secret value before you leave this page.</span></span> <span data-ttu-id="dffa8-120">次の手順で行います。</span><span class="sxs-lookup"><span data-stu-id="dffa8-120">You will need it in the next step.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dffa8-121">このクライアント シークレットは今後表示されないため、今必ずコピーするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="dffa8-121">This client secret is never shown again, so make sure you copy it now.</span></span>

    ![新しく追加されたクライアントシークレットのスクリーンショット](./images/05.png)

1. <span data-ttu-id="dffa8-123">[**管理**] で、[ **API のアクセス許可**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-123">Select **API Permissions** under **Manage**.</span></span> <span data-ttu-id="dffa8-124">**アクセス許可を追加**して、[ **Microsoft Graph**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-124">**Add a permission** and select **Microsoft Graph**.</span></span> <span data-ttu-id="dffa8-125">[**アプリケーションのアクセス許可**] を選択し、[**ユーザー** ] を展開して、[ユーザー] の**すべて**のスコープを選択します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-125">Select **Application Permission** and expand **User** and select the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="dffa8-126">[**アクセス許可の追加**] を選択して変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-126">Select **Add permissions** to save your changes.</span></span>

    ![新しく追加されたクライアントシークレットのスクリーンショット](./images/06.png)

<span data-ttu-id="dffa8-128">アプリケーションは、**ユーザーのすべて**のスコープでアプリケーションのアクセス許可を要求します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-128">The application requests an application permission with the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="dffa8-129">このアクセス許可には、管理者の同意が必要です。</span><span class="sxs-lookup"><span data-stu-id="dffa8-129">This permission requires administrative consent.</span></span>

<span data-ttu-id="dffa8-130">[ **Contoso に対する管理者の同意を許可**する] を選択し、[**はい]** を選択して、このアプリケーションに同意し、指定した範囲を使用してテナントへのアプリケーションアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="dffa8-130">Select **Grant admin consent for Contoso** and then select **Yes** to consent this application and grant the application access to your tenant using the scopes you specified.</span></span>

![サインインのスクリーンショット](./images/07.png)
