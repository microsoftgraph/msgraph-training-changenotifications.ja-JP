# <a name="microsoft-graph-training-module---using-change-notifications-and-track-changes-with-microsoft-graph"></a><span data-ttu-id="f3097-101">Microsoft Graph トレーニングモジュール-変更通知を使用し、Microsoft Graph で変更を追跡する</span><span class="sxs-lookup"><span data-stu-id="f3097-101">Microsoft Graph Training Module - Using Change Notifications and Track Changes with Microsoft Graph</span></span>

<span data-ttu-id="f3097-102">このモジュールでは、Microsoft Graph で変更履歴 (webhooks) & トラック変更 (デルタクエリ) を操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f3097-102">This module will introduce you to working with change notifications (webhooks) & track changes (delta query) in the Microsoft Graph.</span></span>

## <a name="lab---change-notifications-and-track-changes-with-the-microsoft-graph"></a><span data-ttu-id="f3097-103">ラボによる変更通知と、Microsoft Graph を使用した変更の追跡</span><span class="sxs-lookup"><span data-stu-id="f3097-103">Lab - Change Notifications and Track Changes with the Microsoft Graph</span></span>

<span data-ttu-id="f3097-104">このラボでは、Azure Active Directory (Azure AD) のユーザーアカウントに対して更新が行われたときに、Microsoft Graph から変更通知を受け取る .NET コアコンソールアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3097-104">In this lab you will create a .NET Core console application that receives change notifications from the Microsoft Graph when an update is made to a users account in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="f3097-105">アプリケーションは変更通知サブスクリプションを管理し、Microsoft Graph で変更履歴を使用して、変更が失われないようにします。</span><span class="sxs-lookup"><span data-stu-id="f3097-105">The application will managed the Change Notification subscription and use Track Changes in the Microsoft Graph to ensure no changes are missed.</span></span>

- [<span data-ttu-id="f3097-106">ラボマニュアル</span><span class="sxs-lookup"><span data-stu-id="f3097-106">Lab Manual</span></span>](./Lab.md)

## <a name="demos"></a><span data-ttu-id="f3097-107">デモ</span><span class="sxs-lookup"><span data-stu-id="f3097-107">Demos</span></span>

- [<span data-ttu-id="f3097-108">.NET コアアプリを作成する</span><span class="sxs-lookup"><span data-stu-id="f3097-108">Create a .NET Core app</span></span>](./demos/01-create-application)
- [<span data-ttu-id="f3097-109">サブスクリプションのライフサイクルを追加する</span><span class="sxs-lookup"><span data-stu-id="f3097-109">Add Subscription Lifecycle</span></span>](./demos/02-subscription-management)
- [<span data-ttu-id="f3097-110">変更履歴を追加する</span><span class="sxs-lookup"><span data-stu-id="f3097-110">Add Track Changes</span></span>](./demos/03-track-changes)

## <a name="watch-the-module"></a><span data-ttu-id="f3097-111">モジュールを見る</span><span class="sxs-lookup"><span data-stu-id="f3097-111">Watch the module</span></span>

<span data-ttu-id="f3097-112">このモジュールは、Office 開発の YouTube チャンネルで提供されています。[変更通知と Microsoft Graph での変更履歴](https://youtu.be/fThiCZmIcMQ)を記録します。</span><span class="sxs-lookup"><span data-stu-id="f3097-112">This module has been recorded and is available in the Office Development YouTube channel: [Change Notifications and Track Changes with the Microsoft Graph](https://youtu.be/fThiCZmIcMQ)</span></span>

## <a name="contributors"></a><span data-ttu-id="f3097-113">多様</span><span class="sxs-lookup"><span data-stu-id="f3097-113">Contributors</span></span>

|        <span data-ttu-id="f3097-114">ロール</span><span class="sxs-lookup"><span data-stu-id="f3097-114">Roles</span></span>         |                                       <span data-ttu-id="f3097-115">作成者 (s)</span><span class="sxs-lookup"><span data-stu-id="f3097-115">Author(s)</span></span>                                       |
| -------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="f3097-116">ラボのマニュアル/スライド</span><span class="sxs-lookup"><span data-stu-id="f3097-116">Lab Manuals / Slides</span></span> | <span data-ttu-id="f3097-117">Andrew Connell (Microsoft MVP、Voitanos) [@andrewconnell](//github.com/andrewconnell)</span><span class="sxs-lookup"><span data-stu-id="f3097-117">Andrew Connell (Microsoft MVP, Voitanos) [@andrewconnell](//github.com/andrewconnell)</span></span> |
| <span data-ttu-id="f3097-118">スポンサー/サポート</span><span class="sxs-lookup"><span data-stu-id="f3097-118">Sponsor / Support</span></span>    | <span data-ttu-id="f3097-119">Jeremy Thake (Microsoft) [@jthake](//github.com/jthake)</span><span class="sxs-lookup"><span data-stu-id="f3097-119">Jeremy Thake (Microsoft) [@jthake](//github.com/jthake)</span></span>                               |

## <a name="version-history"></a><span data-ttu-id="f3097-120">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="f3097-120">Version history</span></span>

| <span data-ttu-id="f3097-121">バージョン</span><span class="sxs-lookup"><span data-stu-id="f3097-121">Version</span></span> |      <span data-ttu-id="f3097-122">日付</span><span class="sxs-lookup"><span data-stu-id="f3097-122">Date</span></span>      |                     <span data-ttu-id="f3097-123">コメント</span><span class="sxs-lookup"><span data-stu-id="f3097-123">Comments</span></span>                     |
| ------- | -------------- | ------------------------------------------------ |
| <span data-ttu-id="f3097-124">1.3</span><span class="sxs-lookup"><span data-stu-id="f3097-124">1.3</span></span>     | <span data-ttu-id="f3097-125">2019年6月18日</span><span class="sxs-lookup"><span data-stu-id="f3097-125">June 18, 2019</span></span>  | <span data-ttu-id="f3097-126">更新された readme を screencast レコーディングに更新しました</span><span class="sxs-lookup"><span data-stu-id="f3097-126">Updated readme to refreshed screencast recording</span></span> |
| <span data-ttu-id="f3097-127">1.2</span><span class="sxs-lookup"><span data-stu-id="f3097-127">1.2</span></span>     | <span data-ttu-id="f3097-128">2019年5月30日</span><span class="sxs-lookup"><span data-stu-id="f3097-128">May 30, 2019</span></span>   | <span data-ttu-id="f3097-129">Fy2019Q4 コンテンツの更新</span><span class="sxs-lookup"><span data-stu-id="f3097-129">Fy2019Q4 content refresh</span></span>                         |
| <span data-ttu-id="f3097-130">1.1</span><span class="sxs-lookup"><span data-stu-id="f3097-130">1.1</span></span>     | <span data-ttu-id="f3097-131">2019 年 4 月 9 日</span><span class="sxs-lookup"><span data-stu-id="f3097-131">April 9, 2019</span></span>  | <span data-ttu-id="f3097-132">Screencast link が追加されました</span><span class="sxs-lookup"><span data-stu-id="f3097-132">Added screencast link</span></span>                            |
| <span data-ttu-id="f3097-133">1.0</span><span class="sxs-lookup"><span data-stu-id="f3097-133">1.0</span></span>     | <span data-ttu-id="f3097-134">2019 年 3 月 14 日</span><span class="sxs-lookup"><span data-stu-id="f3097-134">March 14, 2019</span></span> | <span data-ttu-id="f3097-135">送信された新しいモジュール</span><span class="sxs-lookup"><span data-stu-id="f3097-135">New module submitted</span></span>                             |

## <a name="disclaimer"></a><span data-ttu-id="f3097-136">免責事項</span><span class="sxs-lookup"><span data-stu-id="f3097-136">Disclaimer</span></span>

<span data-ttu-id="f3097-137">**このコードは、 __ 特定の目的、市販性、または非侵害に対する暗黙の保証を含め、明示的または黙示的ないかなる種類の保証なしに提供されます。**</span><span class="sxs-lookup"><span data-stu-id="f3097-137">**THIS CODE IS PROVIDED _AS IS_ WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**</span></span>

<img src="https://telemetry.sharepointpnp.com/msgraph-training-changenotifications" />
