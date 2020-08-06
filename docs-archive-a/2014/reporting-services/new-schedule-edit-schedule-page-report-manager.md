---
title: 新增排程：編輯排程頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 52a4d250-e185-4116-a29c-d809940a00fb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 701c1729eac1c2cf683c966dca58f47b88a2dd32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706257"
---
# <a name="new-schedule-edit-schedule-page-report-manager"></a><span data-ttu-id="22ed7-102">新增排程：編輯排程頁面 (報表管理員) </span><span class="sxs-lookup"><span data-stu-id="22ed7-102">New Schedule: Edit Schedule Page (Report Manager)</span></span>
  <span data-ttu-id="22ed7-103">使用 [新增排程 / 編輯排程] 頁面，即可建立報表的排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-103">Use the New Schedule / Edit Schedule page to create a schedule for a report.</span></span> <span data-ttu-id="22ed7-104">排程可用於訂閱、重新整理快取報表，以及建立將快照集建立成獨立項目，或建立在報表歷程記錄中。</span><span class="sxs-lookup"><span data-stu-id="22ed7-104">Schedules are used with subscriptions, to refresh cached reports, and to create snapshots as standalone items or in report history.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22ed7-105">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="22ed7-105">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="22ed7-106">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="22ed7-106">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="22ed7-107">您只能為可以自動執行的報表建立排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-107">You can create schedules only for reports that can run unattended.</span></span> <span data-ttu-id="22ed7-108">您必須將報表資料來源認證儲存在報表伺服器資料庫中，才能自動執行報表。</span><span class="sxs-lookup"><span data-stu-id="22ed7-108">Running a report unattended requires that you store report data source credentials in the report server database.</span></span> <span data-ttu-id="22ed7-109">如需詳細資訊，請參閱[資料來源屬性頁面 &#40;報表管理員&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="22ed7-109">For more information, see [Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="22ed7-110">單一排程中無法支援所有的頻率組合。</span><span class="sxs-lookup"><span data-stu-id="22ed7-110">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="22ed7-111">例如，若要在每星期五下午 12:00</span><span class="sxs-lookup"><span data-stu-id="22ed7-111">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="22ed7-112">到下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="22ed7-112">and 4:00 P.M.</span></span> <span data-ttu-id="22ed7-113">就必須建立指定星期五為執行日期的兩個每日排程，一個開始時間為下午 12:00，</span><span class="sxs-lookup"><span data-stu-id="22ed7-113">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="22ed7-114">另一個開始時間為下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="22ed7-114">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="22ed7-115">排程處理是以主控和處理排程之報表伺服器的本機時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="22ed7-115">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="22ed7-116">導覽</span><span class="sxs-lookup"><span data-stu-id="22ed7-116">Navigation</span></span>  
 <span data-ttu-id="22ed7-117">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="22ed7-117">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-execution-properties-page-of-a-report"></a><span data-ttu-id="22ed7-118">若要從報表的執行屬性頁面開啟新增排程或編輯排程頁面</span><span class="sxs-lookup"><span data-stu-id="22ed7-118">To open the New Schedule or Edit Schedule page from the Execution properties page of a report</span></span>  
  
1.  <span data-ttu-id="22ed7-119">開啟報表管理員，然後找出您想要設定排程的報表。</span><span class="sxs-lookup"><span data-stu-id="22ed7-119">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="22ed7-120">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="22ed7-120">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="22ed7-121">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="22ed7-121">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="22ed7-122">這樣就會開啟該模型的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="22ed7-122">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="22ed7-123">選取 **[執行]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="22ed7-123">Select the **Execution** tab.</span></span>  
  
5.  <span data-ttu-id="22ed7-124">選取 **[從報表執行快照集轉譯此報表]** 選項。</span><span class="sxs-lookup"><span data-stu-id="22ed7-124">Select the **Render this report from a report execution snapshot option**.</span></span> <span data-ttu-id="22ed7-125">接著，選取 **[使用下列排程將快照集加入至報表記錄]** 並選取 **[報表特定排程]**。</span><span class="sxs-lookup"><span data-stu-id="22ed7-125">Then select **Use the following schedule to add snapshots to report history**, and select **Report-specific schedule**.</span></span> <span data-ttu-id="22ed7-126">然後，按一下 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="22ed7-126">Then click **Configure**.</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-history-properties-page-of-a-report"></a><span data-ttu-id="22ed7-127">若要從報表的記錄屬性頁面開啟新增排程或編輯排程頁面</span><span class="sxs-lookup"><span data-stu-id="22ed7-127">To open the New Schedule or Edit Schedule page from the History properties page of a report</span></span>  
  
1.  <span data-ttu-id="22ed7-128">開啟報表管理員，然後找出您想要設定排程的報表。</span><span class="sxs-lookup"><span data-stu-id="22ed7-128">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="22ed7-129">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="22ed7-129">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="22ed7-130">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="22ed7-130">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="22ed7-131">這樣就會開啟該模型的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="22ed7-131">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="22ed7-132">選取 **[記錄]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="22ed7-132">Select the **History** tab.</span></span>  
  
5.  <span data-ttu-id="22ed7-133">選取 **[使用下列排程將快照集加入至報表記錄]** 並選取 **[報表特定排程]**。</span><span class="sxs-lookup"><span data-stu-id="22ed7-133">Select **Use the following schedule to add snapshots to report history**, and select **Report-specific schedule**.</span></span> <span data-ttu-id="22ed7-134">然後，按一下 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="22ed7-134">Then click **Configure**.</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-subscriptions-page"></a><span data-ttu-id="22ed7-135">若要從訂閱頁面開啟新增排程或編輯排程頁面</span><span class="sxs-lookup"><span data-stu-id="22ed7-135">To open the New Schedule or Edit Schedule page from the Subscriptions page</span></span>  
  
1.  <span data-ttu-id="22ed7-136">開啟報表管理員，然後找出您想要設定排程的報表。</span><span class="sxs-lookup"><span data-stu-id="22ed7-136">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="22ed7-137">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="22ed7-137">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="22ed7-138">在下拉式功能表中，</span><span class="sxs-lookup"><span data-stu-id="22ed7-138">In the drop-down menu,</span></span>  
  
    -   <span data-ttu-id="22ed7-139">按一下 [管理] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22ed7-139">Click **Manage**.</span></span> <span data-ttu-id="22ed7-140">這樣就會開啟該報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="22ed7-140">This opens the General properties page for the report.</span></span> <span data-ttu-id="22ed7-141">然後，選取 **[訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="22ed7-141">Then select the **Subscriptions** tab.</span></span>  
  
    -   <span data-ttu-id="22ed7-142">按一下 **[訂閱]**。</span><span class="sxs-lookup"><span data-stu-id="22ed7-142">Click **Subscribe**.</span></span> <span data-ttu-id="22ed7-143">這樣就會開啟該報表的 **[訂閱]** 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="22ed7-143">This opens the **Subscriptions** properties page for the report.</span></span>  
  
4.  <span data-ttu-id="22ed7-144">在工具列中，按一下 **[新增訂閱]** 或選取要編輯的現有訂閱。</span><span class="sxs-lookup"><span data-stu-id="22ed7-144">In the toolbar, click **New Subscription** or select an existing subscription to edit.</span></span>  
  
5.  <span data-ttu-id="22ed7-145">在 **[訂閱處理選項]** 底下，按一下 **[新增排程]**。</span><span class="sxs-lookup"><span data-stu-id="22ed7-145">Under **Subscription Processing Options**, click **New Schedule**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="22ed7-146">選項</span><span class="sxs-lookup"><span data-stu-id="22ed7-146">Options</span></span>  
 <span data-ttu-id="22ed7-147">**排程詳細資料**</span><span class="sxs-lookup"><span data-stu-id="22ed7-147">**Schedule details**</span></span>  
 <span data-ttu-id="22ed7-148">選取決定何時執行報表及其執行頻率的選項。</span><span class="sxs-lookup"><span data-stu-id="22ed7-148">Select options that determine when and how often a report runs.</span></span> <span data-ttu-id="22ed7-149">頻率選項有層次之分。</span><span class="sxs-lookup"><span data-stu-id="22ed7-149">Frequency options are layered.</span></span> <span data-ttu-id="22ed7-150">第一組選項指定頻率的類別 (每小時、每日、每週等)。</span><span class="sxs-lookup"><span data-stu-id="22ed7-150">The first set of options specifies a category of frequency (hourly, daily, weekly, and so on).</span></span> <span data-ttu-id="22ed7-151">顯示的第二組選項是以您的初始選擇為基礎。</span><span class="sxs-lookup"><span data-stu-id="22ed7-151">The second set of options that appears is based on your initial selection.</span></span>  
  
-   <span data-ttu-id="22ed7-152">**[小時]** 會定義以每小時間隔執行的排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-152">**Hour** defines a schedule that runs at hourly intervals.</span></span> <span data-ttu-id="22ed7-153">使用 **[開始和結束日期]** 區段，即可指定要執行排程的日期。</span><span class="sxs-lookup"><span data-stu-id="22ed7-153">Use the **Start and end dates** section to specify the day on which to run the schedule.</span></span>  
  
-   <span data-ttu-id="22ed7-154">**[天]** 會定義在您所選取日子之特定時間執行的排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-154">**Day** defines a schedule that runs on the days you select at a specific hour and minute.</span></span> <span data-ttu-id="22ed7-155">您可以透過下列方式指定天數：每個 \<*day*> 、每個工作日和 \<*number*> 每天。</span><span class="sxs-lookup"><span data-stu-id="22ed7-155">You can specify days in the following ways: Every \<*day*>, Every weekday, and Every \<*number*> day.</span></span> <span data-ttu-id="22ed7-156">選擇一種方式就會使其他方式失效，即使其他日子看似已經選取也一樣。</span><span class="sxs-lookup"><span data-stu-id="22ed7-156">Choosing one approach voids the others, even if the other days appear to be selected.</span></span>  
  
-   <span data-ttu-id="22ed7-157">**[週]** 會定義在每週間隔之特定時間執行的排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-157">**Week** defines a schedule that runs at weekly intervals at a specific hour and minute.</span></span> <span data-ttu-id="22ed7-158">此間隔可以是整週 (例如每兩週) 或是其中的日期。</span><span class="sxs-lookup"><span data-stu-id="22ed7-158">The interval can be a complete week (for example, every two weeks), or days within a week.</span></span>  
  
-   <span data-ttu-id="22ed7-159">**[月]** 會定義以每月為基礎執行的排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-159">**Month** defines a schedule that runs on a monthly basis.</span></span> <span data-ttu-id="22ed7-160">在月份中可以根據模式來選擇日期 (例如每月的最後一個星期日) 或特定的日期 (例如 1 和 15 表示每月的第一和第十五日)。</span><span class="sxs-lookup"><span data-stu-id="22ed7-160">Within a month, you can choose a day based on a pattern (for example, the last Sunday of every month) or specific calendar dates (such as 1 and 15 to indicate the first and fifteenth day of every month).</span></span> <span data-ttu-id="22ed7-161">使用逗號和連字號，可以指定多天和範圍，例如 1、5、7-12、21。</span><span class="sxs-lookup"><span data-stu-id="22ed7-161">Using commas and hyphens, you can specify multiple days and ranges, for example, 1, 5, 7-12, 21.</span></span>  
  
-   <span data-ttu-id="22ed7-162">**[一次]** 會定義只執行一次的排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-162">**Once** defines a schedule that runs only once.</span></span> <span data-ttu-id="22ed7-163">使用 **[開始和結束日期]** 區段，即可指定要執行排程的日期。</span><span class="sxs-lookup"><span data-stu-id="22ed7-163">Use the **Start and end dates** section to specify the day on which to run the schedule.</span></span> <span data-ttu-id="22ed7-164">此排程在處理過後立即過期。</span><span class="sxs-lookup"><span data-stu-id="22ed7-164">This schedule expires as soon as it is processed.</span></span>  
  
 <span data-ttu-id="22ed7-165">**[開始和結束日期]**</span><span class="sxs-lookup"><span data-stu-id="22ed7-165">**Start and end dates**</span></span>  
 <span data-ttu-id="22ed7-166">指定決定排程生效的開始日期，以及決定排程過期的結束日期。</span><span class="sxs-lookup"><span data-stu-id="22ed7-166">Specify a start date that determines when the schedule takes effect and an end date that determines when the schedule expires.</span></span>  
  
 <span data-ttu-id="22ed7-167">不會通知排程過期。</span><span class="sxs-lookup"><span data-stu-id="22ed7-167">Schedules expire without notification.</span></span> <span data-ttu-id="22ed7-168">在結束日期之後，就不會再執行排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-168">After the end date, they no longer run.</span></span> <span data-ttu-id="22ed7-169">不會刪除過期的排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-169">Expired schedules are not deleted.</span></span> <span data-ttu-id="22ed7-170">只能手動刪除排程。</span><span class="sxs-lookup"><span data-stu-id="22ed7-170">Schedules can only be deleted manually.</span></span> <span data-ttu-id="22ed7-171">因此，如果選擇繼續執行排程，您可以延展其結束日期。</span><span class="sxs-lookup"><span data-stu-id="22ed7-171">That way, if you choose to continue the schedule, you can extend the end date.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ed7-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22ed7-172">See Also</span></span>  
 <span data-ttu-id="22ed7-173">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="22ed7-173">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="22ed7-174">[建立、修改和刪除共用排程](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="22ed7-174">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="22ed7-175">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="22ed7-175">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
