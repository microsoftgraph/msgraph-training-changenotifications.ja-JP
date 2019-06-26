<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="235be-101">この演習では、Azure Active Directory 管理センターを使用して、新しい Azure AD web アプリケーション登録を作成し、必要なアクセス許可スコープに対して管理者の同意を付与します。</span><span class="sxs-lookup"><span data-stu-id="235be-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center and grant administrator consent to the required permission scopes.</span></span>

1. <span data-ttu-id="235be-102">ブラウザーを開き、 [Azure Active Directory 管理センター (https://aad.portal.azure.com)](https://aad.portal.azure.com)) に移動します。</span><span class="sxs-lookup"><span data-stu-id="235be-102">Open a browser and navigate to the [Azure Active Directory admin center (https://aad.portal.azure.com)](https://aad.portal.azure.com).</span></span> <span data-ttu-id="235be-103">**職場または学校のアカウント**を使用してログインします。</span><span class="sxs-lookup"><span data-stu-id="235be-103">Login using a **Work or School Account**.</span></span>

1. <span data-ttu-id="235be-104">左側のナビゲーションで [ **Azure Active Directory** ] を選択し、[**管理**] の下にある [**アプリの登録**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations** under **Manage**.</span></span>

    ![アプリの登録のスクリーンショット](./images/aad-portal-home.png)

1. <span data-ttu-id="235be-106">**[新規登録]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-106">Select **New registration**.</span></span> <span data-ttu-id="235be-107">[**アプリケーションの登録**] ページ</span><span class="sxs-lookup"><span data-stu-id="235be-107">On the **Register an application** page</span></span>

    ![アプリの登録ページのスクリーンショット](./images/aad-portal-newapp.png)

    <span data-ttu-id="235be-109">値を次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="235be-109">Set the values as follows:</span></span>

    - <span data-ttu-id="235be-110">**Name**: graphnotificationtutorial</span><span class="sxs-lookup"><span data-stu-id="235be-110">**Name**: GraphNotificationTutorial</span></span>
    - <span data-ttu-id="235be-111">**サポートされているアカウントの種類**: 任意の組織ディレクトリ内のアカウントと個人の Microsoft アカウント</span><span class="sxs-lookup"><span data-stu-id="235be-111">**Supported account types**: Accounts in any organizational directory and personal Microsoft accounts</span></span>
    - <span data-ttu-id="235be-112">**リダイレクト URI**: Web >http://localhost</span><span class="sxs-lookup"><span data-stu-id="235be-112">**Redirect URI**: Web > http://localhost</span></span>

    ![[アプリケーションの登録] ページのスクリーンショット](./images/aad-portal-newapp-01.png)

    <span data-ttu-id="235be-114">[**登録**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-114">Select **Register**.</span></span>

1. <span data-ttu-id="235be-115">**Graphnotificationtutorial**ページで、**アプリケーション (クライアント) id**と**ディレクトリ (テナント) id**の値をコピーします。保存するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="235be-115">On the **GraphNotificationTutorial** page, copy the value of the **Application (client) ID** and **Directory (tenant) ID** save it, you will need them in the next step.</span></span>

    ![新しいアプリの登録のアプリケーション ID のスクリーンショット](./images/aad-portal-newapp-details.png)

1. <span data-ttu-id="235be-117">[ **> 証明書 & シークレットを管理**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-117">Select **Manage > Certificates & secrets**.</span></span> 

    <span data-ttu-id="235be-118">[**新しいクライアントシークレット**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-118">Select **New client secret**.</span></span>

    <span data-ttu-id="235be-119">[**説明**] に値を入力して、[**有効期限**] のオプションの1つを選択し、[**追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-119">Enter a value in **Description** and select one of the options for **Expires** and select **Add**.</span></span>

    ![[クライアントシークレットの追加] ダイアログのスクリーンショット](./images/aad-portal-newapp-secret.png)

    ![[クライアントシークレットの追加] ダイアログのスクリーンショット](./images/aad-portal-newapp-secret-02.png)

1. <span data-ttu-id="235be-122">クライアント シークレットの値をコピーしてから、このページから移動します。</span><span class="sxs-lookup"><span data-stu-id="235be-122">Copy the client secret value before you leave this page.</span></span> <span data-ttu-id="235be-123">次の手順で行います。</span><span class="sxs-lookup"><span data-stu-id="235be-123">You will need it in the next step.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="235be-124">このクライアント シークレットは今後表示されないため、今必ずコピーするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="235be-124">This client secret is never shown again, so make sure you copy it now.</span></span>

    ![新しく追加されたクライアントシークレットのスクリーンショット](./images/aad-portal-newapp-secret-03.png)

1. <span data-ttu-id="235be-126">[ **Manage > API Permissions**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-126">Select **Manage > API Permissions**.</span></span>

    <span data-ttu-id="235be-127">[**アクセス許可の追加**] を選択し、[ **Microsoft Graph**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-127">Select **Add a permission** and select **Microsoft Graph**.</span></span>

    ![Microsoft Graph サービスを選択するスクリーンショット](./images/aad-portal-newapp-graphscope.png)

    <span data-ttu-id="235be-129">[**アプリケーションのアクセス許可**] を選択し、**ユーザー**グループを展開して、[**すべて**のスコープ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="235be-129">Select **Application Permission**, expand the **User** group and select **User.ReadWrite.All** scope.</span></span>

    <span data-ttu-id="235be-130">[**アクセス許可の追加**] を選択して変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="235be-130">Select **Add permissions** to save your changes.</span></span>

    ![Microsoft Graph スコープを選択するスクリーンショット](./images/aad-portal-newapp-graphscope-02.png)

    ![新しく追加されたクライアントシークレットのスクリーンショット](./images/aad-portal-newapp-graphscope-03.png)

<span data-ttu-id="235be-133">アプリケーションは、**ユーザーのすべて**のスコープでアプリケーションのアクセス許可を要求します。</span><span class="sxs-lookup"><span data-stu-id="235be-133">The application requests an application permission with the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="235be-134">このアクセス許可には、管理者の同意が必要です。</span><span class="sxs-lookup"><span data-stu-id="235be-134">This permission requires administrative consent.</span></span>

<span data-ttu-id="235be-135">[ **Contoso に対する管理者の同意を付与**する] を選択し、[**はい**] を選択して、このアプリケーションに同意し、指定した範囲を使用してテナントへのアプリケーションアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="235be-135">Select **Grant admin consent for Contoso**, then select **Yes** to consent this application and grant the application access to your tenant using the scopes you specified.</span></span>

![スクリーンショットの承認済み管理者の同意](./images/aad-portal-newapp-graphscope-04.png)
