---
title: 預先載入快取 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- cache [Reporting Services]
- preloading cache
ms.assetid: 152a1051-8aa5-4c01-bc85-f8be8971b0cd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b60b74f7ab5c0c843b848c09ee574fd59a99c682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700798"
---
# <a name="preload-the-cache-report-manager"></a><span data-ttu-id="6fd1f-102">預先載入快取 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="6fd1f-102">Preload the Cache (Report Manager)</span></span>
  <span data-ttu-id="6fd1f-103">您可以為共用資料集建立快取重新整理計劃，為共用資料集預先載入快取。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-103">You can preload the cache for a shared dataset by creating a cache refresh plan for the shared dataset.</span></span>  
  
 <span data-ttu-id="6fd1f-104">您有兩種方式，可以預先載入報表的快取：</span><span class="sxs-lookup"><span data-stu-id="6fd1f-104">You can preload the cache for a report in two ways:</span></span>  
  
1.  <span data-ttu-id="6fd1f-105">建立報表的快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-105">Create a cache refresh plan for the report.</span></span> <span data-ttu-id="6fd1f-106">這是慣用的方法。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-106">This is the preferred method.</span></span>  
  
2.  <span data-ttu-id="6fd1f-107">使用資料驅動訂閱，以預先載入有參數化報表執行個體的快取。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-107">Use a data-driven subscription to preload the cache with instances of parameterized reports.</span></span> <span data-ttu-id="6fd1f-108">這是在早於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)][!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]的版本中預先載入快取的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-108">This was the only way to preload the cache in versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] earlier than [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="6fd1f-109">如需詳細資訊，請參閱 [快取報表 &#40;SSRS&#41;](caching-reports-ssrs.md)的版本中預先載入快取的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-109">For more information, see [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
 <span data-ttu-id="6fd1f-110">快取報表或共用資料集之前，必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="6fd1f-110">The following conditions must be met before you can cache a report or a shared dataset:</span></span>  
  
-   <span data-ttu-id="6fd1f-111">共用資料集或報表必須已啟用快取。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-111">The shared dataset or the report must have caching enabled.</span></span>  
  
-   <span data-ttu-id="6fd1f-112">共用資料集或報表的共用資料來源必須設定為使用預存的認證或無認證。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-112">The shared data sources for the shared dataset or the report must be configured to use stored credentials or no credentials.</span></span>  
  
-   <span data-ttu-id="6fd1f-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務必須執行。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service must be running.</span></span>  
  
### <a name="to-preload-the-cache-by-creating-a-cache-refresh-plan"></a><span data-ttu-id="6fd1f-114">若要透過建立快取重新整理計劃以預先載入快取</span><span class="sxs-lookup"><span data-stu-id="6fd1f-114">To preload the cache by creating a cache refresh plan</span></span>  
  
1.  <span data-ttu-id="6fd1f-115">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-115">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="6fd1f-116">在報表管理員中，導覽到 **[內容]** 頁面，然後導覽到您要快取的項目。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-116">In Report Manager, navigate to the **Contents** page, and then navigate to the item that you want to cache.</span></span>  
  
3.  <span data-ttu-id="6fd1f-117">將滑鼠停留在該項目上方，按一下下拉式清單，然後按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-117">Hover over the item, click the drop-down list, and then click **Manage**.</span></span>  
  
4.  <span data-ttu-id="6fd1f-118">按一下 **[快取重新整理選項]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-118">Click the **Cache Refresh Options** tab.</span></span>  
  
5.  <span data-ttu-id="6fd1f-119">按一下工具列上的 **[新增快取重新整理計劃]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-119">On the toolbar, click **New Cache Refresh Plan**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6fd1f-120">如果項目並沒有啟用快取，系統會提示您啟用快取。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-120">If the item does not have caching enabled, you will be prompted to enable caching.</span></span> <span data-ttu-id="6fd1f-121">若要啟用快取，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-121">To enable caching, click **OK**.</span></span>  
  
     <span data-ttu-id="6fd1f-122">[快取重新整理計劃] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-122">The Cache Refresh Plan page opens.</span></span>  
  
6.  <span data-ttu-id="6fd1f-123">選擇性地輸入重新整理計劃的描述。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-123">Optionally type a description for the refresh plan.</span></span>  
  
7.  <span data-ttu-id="6fd1f-124">針對共用排程，按一下 **[共用排程]**，然後選取要使用的排程名稱。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-124">For a shared schedule, click **Shared schedule**, and then select the name of the schedule to use.</span></span>  
  
     <span data-ttu-id="6fd1f-125">針對自訂排程，按一下 [項目特定排程]\*\*\*\*，然後按一下 [設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-125">For a custom schedule, click **Item-specific schedule**, and then click **Configure**.</span></span>  
  
8.  <span data-ttu-id="6fd1f-126">設定排程</span><span class="sxs-lookup"><span data-stu-id="6fd1f-126">Configure the schedule</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-preload-the-cache-with-a-user-specific-report-by-using-a-data-driven-subscription"></a><span data-ttu-id="6fd1f-127">若要透過使用資料驅動訂閱以預先載入含使用者專屬報表的快取</span><span class="sxs-lookup"><span data-stu-id="6fd1f-127">To preload the cache with a user-specific report by using a data-driven subscription</span></span>  
  
1.  <span data-ttu-id="6fd1f-128">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-128">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="6fd1f-129">在報表管理員中，導覽至 **[內容]** 頁面，然後導覽至您要建立訂閱的報表。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-129">In Report Manager, navigate to the **Contents** page, and then navigate to the report you want to create a subscription for.</span></span>  
  
3.  <span data-ttu-id="6fd1f-130">按一下報表，按一下 [訂閱]\*\*\*\* 索引標籤，然後按一下 [新增資料驅動訂閱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-130">Click the report, click the **Subscriptions** tab, and then click **New Data-Driven Subscription**.</span></span>  
  
4.  <span data-ttu-id="6fd1f-131">選擇性地輸入訂閱的描述。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-131">Optionally type a description for the subscription.</span></span>  
  
5.  <span data-ttu-id="6fd1f-132">從 **[指定通知收件者的方式]** 清單中，選取 **[Null 傳遞提供者]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-132">From the **Specify how recipients are notified** list, select **Null Delivery Provider**.</span></span>  
  
6.  <span data-ttu-id="6fd1f-133">指定資料來源類型，然後按 **[下一步]** 以設定資料來源。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-133">Specify a data source type and then click **Next** to configure the data source.</span></span>  
  
7.  <span data-ttu-id="6fd1f-134">指定連接類型、連接字串和認證，以存取包含訂閱者資料的資料來源。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-134">Specify the connection type, connection string, and credentials for accessing the data source that contains subscriber data.</span></span> <span data-ttu-id="6fd1f-135">下列範例將說明用來連接到名為 Subscribers 之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的連接字串：</span><span class="sxs-lookup"><span data-stu-id="6fd1f-135">The following example illustrates a connection string used to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database called Subscribers:</span></span>  
  
    ```  
    data source=<servername>; initial catalog=Subscribers  
    ```  
  
8.  <span data-ttu-id="6fd1f-136">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-136">Click **Next**.</span></span>  
  
9. <span data-ttu-id="6fd1f-137">指定擷取訂閱者資料的查詢或命令。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-137">Specify the query or command that retrieves subscriber data.</span></span> <span data-ttu-id="6fd1f-138">選擇性地增加花較長時間處理之查詢的逾時期間。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-138">Optionally increase the time-out period for queries that take a long time to process.</span></span> <span data-ttu-id="6fd1f-139">例如：</span><span class="sxs-lookup"><span data-stu-id="6fd1f-139">For example:</span></span>  
  
    ```  
    Select * from UserInfo  
    ```  
  
10. <span data-ttu-id="6fd1f-140">按一下 **[驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-140">Click **Validate**.</span></span> <span data-ttu-id="6fd1f-141">必須先驗證查詢，才能繼續。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-141">The query must be validated before you continue.</span></span> <span data-ttu-id="6fd1f-142">出現 **[成功驗證查詢]** 訊息時，請按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-142">When the **Query validated successfully** message appears, click **Next**.</span></span>  
  
11. <span data-ttu-id="6fd1f-143">您無法設定 Null 傳遞提供者之傳遞延伸模組的設定，所以請按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-143">Because you cannot configure delivery extension settings for the null delivery provider, click **Next**.</span></span>  
  
12. <span data-ttu-id="6fd1f-144">指定訂閱的報表參數值，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-144">Specify report parameter values for the subscription, and click **Next**.</span></span>  
  
13. <span data-ttu-id="6fd1f-145">指定處理訂閱的時間。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-145">Specify when the subscription is processed.</span></span> <span data-ttu-id="6fd1f-146">請勿選擇 **[更新報表伺服器上的報表資料時]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-146">Do not choose **When the report data is updated on the report server**.</span></span> <span data-ttu-id="6fd1f-147">該設定僅適用於快照集。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-147">That setting is for snapshots only.</span></span> <span data-ttu-id="6fd1f-148">如果您想要使用預先存在的排程，請選取 [在共用排程上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-148">If want to use a pre-existing schedule, select **On a shared schedule**.</span></span>  
  
     <span data-ttu-id="6fd1f-149">或者，若要建立自訂排程，請按一下 **[在為此訂閱建立的排程上]** ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-149">Or, to create a custom schedule, click **On a schedule created for this subscription** and then click **Next**.</span></span> <span data-ttu-id="6fd1f-150">設定排程，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-150">Configure the schedule and then click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6fd1f-151">為了讓訂閱者能夠接收到最新的報表，您設定的排程應該與您為訂閱者所定義的報表傳遞排程一致。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-151">In order for the subscribers to receive the newest report, the schedule that you configure should be consistent with the report delivery schedule that you have defined for the subscribers.</span></span> <span data-ttu-id="6fd1f-152">如需詳細資訊，請參閱[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-152">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
14. <span data-ttu-id="6fd1f-153">設定報表的執行選項，如下。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-153">Configure the Execution options for the report as follows.</span></span> <span data-ttu-id="6fd1f-154">在報表頁面上，按一下 **[屬性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-154">On the report page, click the **Properties** tab.</span></span>  
  
15. <span data-ttu-id="6fd1f-155">在左框架內，按一下 **[執行]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-155">In the left frame, click the **Execution** tab.</span></span>  
  
16. <span data-ttu-id="6fd1f-156">在頁面上，選取 **[以最新的資料轉譯此報表]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-156">On the page, select **Render this report with the most recent data**.</span></span>  
  
17. <span data-ttu-id="6fd1f-157">選擇下列兩個快取選項的其中之一並設定逾期，如下：</span><span class="sxs-lookup"><span data-stu-id="6fd1f-157">Choose one of the following two cache options and configure the expiration as follows:</span></span>  
  
    -   <span data-ttu-id="6fd1f-158">若要使快取副本在特定時間週期之後過期，請按一下 **[快取報表的暫存副本。報表複本會在下列分鐘數後過期]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-158">To make the cached copy expire after a particular time period, click **Cache a temporary copy of the report. Expire copy of report after a number of minutes.**</span></span> <span data-ttu-id="6fd1f-159">輸入報表過期的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-159">Type the number of minutes for report expiration.</span></span>  
  
    -   <span data-ttu-id="6fd1f-160">若要使快取複本依據排程過期，請按一下 **[快取報表的暫存複本。報表複本會在下列排程過期]**。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-160">To make the cached copy expire on a schedule, click **Cache a temporary copy of the report. Expire copy of report on the following schedule.**</span></span> <span data-ttu-id="6fd1f-161">按一下 **[設定]**，或選取共用排程來設定報表過期的排程。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-161">Click **Configure**, or select a shared schedule to set a schedule for report expiration.</span></span>  
  
18. <span data-ttu-id="6fd1f-162">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="6fd1f-162">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd1f-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fd1f-163">See Also</span></span>  
 <span data-ttu-id="6fd1f-164">[Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="6fd1f-164">[Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="6fd1f-165">[建立資料驅動訂閱 &#40;SSRS 教學課程&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="6fd1f-165">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="6fd1f-166">[效能、快照、快取 &#40;Reporting Services&#41;](performance-snapshots-caching-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="6fd1f-166">[Performance, Snapshots, Caching &#40;Reporting Services&#41;](performance-snapshots-caching-reporting-services.md) </span></span>  
 <span data-ttu-id="6fd1f-167">[設定報表處理屬性](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6fd1f-167">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="6fd1f-168">快取報表 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6fd1f-168">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
  
  
