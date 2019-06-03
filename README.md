# <a name="microsoft-graph-training-module---using-change-notifications-and-track-changes-with-microsoft-graph"></a><span data-ttu-id="0ed1c-101">Microsoft Graph トレーニングモジュール-変更通知を使用し、Microsoft Graph で変更を追跡する</span><span class="sxs-lookup"><span data-stu-id="0ed1c-101">Microsoft Graph Training Module - Using Change Notifications and Track Changes with Microsoft Graph</span></span>

<span data-ttu-id="0ed1c-102">このモジュールでは、Microsoft Graph で変更履歴 (webhooks) & トラック変更 (デルタクエリ) を操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ed1c-102">This module will introduce you to working with change notifications (webhooks) & track changes (delta query) in the Microsoft Graph.</span></span>

## <a name="lab---change-notifications-and-track-changes-with-the-microsoft-graph"></a><span data-ttu-id="0ed1c-103">ラボによる変更通知と、Microsoft Graph を使用した変更の追跡</span><span class="sxs-lookup"><span data-stu-id="0ed1c-103">Lab - Change Notifications and Track Changes with the Microsoft Graph</span></span>

<span data-ttu-id="0ed1c-104">このラボでは、Azure Active Directory (Azure AD) のユーザーアカウントに対して更新が行われたときに、Microsoft Graph から変更通知を受け取る .NET コアコンソールアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="0ed1c-104">In this lab you will create a .NET Core console application that receives change notifications from the Microsoft Graph when an update is made to a users account in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="0ed1c-105">アプリケーションは変更通知サブスクリプションを管理し、Microsoft Graph で変更履歴を使用して、変更が失われないようにします。</span><span class="sxs-lookup"><span data-stu-id="0ed1c-105">The application will managed the Change Notification subscription and use Track Changes in the Microsoft Graph to ensure no changes are missed.</span></span>

- [<span data-ttu-id="0ed1c-106">ラボマニュアル</span><span class="sxs-lookup"><span data-stu-id="0ed1c-106">Lab Manual</span></span>](./Lab.md)

## <a name="demos"></a><span data-ttu-id="0ed1c-107">デモ</span><span class="sxs-lookup"><span data-stu-id="0ed1c-107">Demos</span></span>

- [<span data-ttu-id="0ed1c-108">.NET コアアプリを作成する</span><span class="sxs-lookup"><span data-stu-id="0ed1c-108">Create a .NET Core app</span></span>](./demos/01-create-application)
- [<span data-ttu-id="0ed1c-109">サブスクリプションのライフサイクルを追加する</span><span class="sxs-lookup"><span data-stu-id="0ed1c-109">Add Subscription Lifecycle</span></span>](./demos/02-subscription-management)
- [<span data-ttu-id="0ed1c-110">変更履歴を追加する</span><span class="sxs-lookup"><span data-stu-id="0ed1c-110">Add Track Changes</span></span>](./demos/03-track-changes)

## <a name="watch-the-module"></a><span data-ttu-id="0ed1c-111">モジュールを見る</span><span class="sxs-lookup"><span data-stu-id="0ed1c-111">Watch the module</span></span>

<span data-ttu-id="0ed1c-112">このモジュールは、Office 開発の YouTube チャンネルで提供されています。[変更通知と Microsoft Graph での変更履歴](https://youtu.be/MvJ15BHTdHA)を記録します。</span><span class="sxs-lookup"><span data-stu-id="0ed1c-112">This module has been recorded and is available in the Office Development YouTube channel: [Change Notifications and Track Changes with the Microsoft Graph](https://youtu.be/MvJ15BHTdHA)</span></span>

## <a name="contributors"></a><span data-ttu-id="0ed1c-113">多様</span><span class="sxs-lookup"><span data-stu-id="0ed1c-113">Contributors</span></span>

| <span data-ttu-id="0ed1c-114">ロール</span><span class="sxs-lookup"><span data-stu-id="0ed1c-114">Roles</span></span>                | <span data-ttu-id="0ed1c-115">作成者 (s)</span><span class="sxs-lookup"><span data-stu-id="0ed1c-115">Author(s)</span></span>                                               |
| -------------------- | ------------------------------------------------------- |
| <span data-ttu-id="0ed1c-116">ラボのマニュアル/スライド</span><span class="sxs-lookup"><span data-stu-id="0ed1c-116">Lab Manuals / Slides</span></span> | <span data-ttu-id="0ed1c-117">Andrew Connell (Microsoft MVP、Voitanos) @andrewconnell</span><span class="sxs-lookup"><span data-stu-id="0ed1c-117">Andrew Connell (Microsoft MVP, Voitanos) @andrewconnell</span></span> |
| <span data-ttu-id="0ed1c-118">スポンサー/サポート</span><span class="sxs-lookup"><span data-stu-id="0ed1c-118">Sponsor / Support</span></span>    | <span data-ttu-id="0ed1c-119">Jeremy Thake (Microsoft) @jthake</span><span class="sxs-lookup"><span data-stu-id="0ed1c-119">Jeremy Thake (Microsoft) @jthake</span></span>                        |

## <a name="version-history"></a><span data-ttu-id="0ed1c-120">バージョン履歴</span><span class="sxs-lookup"><span data-stu-id="0ed1c-120">Version history</span></span>

| <span data-ttu-id="0ed1c-121">バージョン</span><span class="sxs-lookup"><span data-stu-id="0ed1c-121">Version</span></span> | <span data-ttu-id="0ed1c-122">日付</span><span class="sxs-lookup"><span data-stu-id="0ed1c-122">Date</span></span>           | <span data-ttu-id="0ed1c-123">コメント</span><span class="sxs-lookup"><span data-stu-id="0ed1c-123">Comments</span></span>             |
| ------- | -------------- | -------------------- |
| <span data-ttu-id="0ed1c-124">1.1</span><span class="sxs-lookup"><span data-stu-id="0ed1c-124">1.1</span></span>     | <span data-ttu-id="0ed1c-125">2019 年 4 月 9 日</span><span class="sxs-lookup"><span data-stu-id="0ed1c-125">April 9, 2019</span></span> | <span data-ttu-id="0ed1c-126">Screencast link が追加されました</span><span class="sxs-lookup"><span data-stu-id="0ed1c-126">Added screencast link</span></span> |
| <span data-ttu-id="0ed1c-127">1.0</span><span class="sxs-lookup"><span data-stu-id="0ed1c-127">1.0</span></span>     | <span data-ttu-id="0ed1c-128">2019 年 3 月 14 日</span><span class="sxs-lookup"><span data-stu-id="0ed1c-128">March 14, 2019</span></span> | <span data-ttu-id="0ed1c-129">送信された新しいモジュール</span><span class="sxs-lookup"><span data-stu-id="0ed1c-129">New module submitted</span></span> |

## <a name="disclaimer"></a><span data-ttu-id="0ed1c-130">免責事項</span><span class="sxs-lookup"><span data-stu-id="0ed1c-130">Disclaimer</span></span>

<span data-ttu-id="0ed1c-131">**このコードは、 __ 特定の目的、市販性、または非侵害に対する暗黙の保証を含め、明示的または黙示的ないかなる種類の保証なしに提供されます。**</span><span class="sxs-lookup"><span data-stu-id="0ed1c-131">**THIS CODE IS PROVIDED _AS IS_ WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**</span></span>

<img src="https://telemetry.sharepointpnp.com/msgraph-training-changenotifications" />
