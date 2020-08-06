---
title: 以 SharePoint 整合模式 (Reporting Services 設定處理選項) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- snapshots [Reporting Services], creating
ms.assetid: 453b19a1-739a-4b67-aeea-2069b52204e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c33b205a702d4ab77abf74154232990da9840b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700768"
---
# <a name="set-processing-options-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="61464-102">設定處理選項 (SharePoint 整合模式的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="61464-102">Set Processing Options (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="61464-103">您可以對 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表設定處理選項，以指定資料開始處理的時間。</span><span class="sxs-lookup"><span data-stu-id="61464-103">You can set processing options on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report to determine when data processing occurs.</span></span> <span data-ttu-id="61464-104">您還可以設定報表處理的逾時值，以及決定是否要啟用目前報表之報表記錄的選項。</span><span class="sxs-lookup"><span data-stu-id="61464-104">You can also set a time-out value for report processing, and options that determine whether report history is enabled for the current report.</span></span>  
  
-   <span data-ttu-id="61464-105">您可以將報表以報表快照集的形式執行，以避免在任意時間 (例如，在排程備份期間) 執行報表。</span><span class="sxs-lookup"><span data-stu-id="61464-105">You can run a report as a report snapshot to prevent the report from being run at arbitrary times (for example, during a scheduled backup).</span></span> <span data-ttu-id="61464-106">報表快照集一般會按照排程建立和後續重新整理，讓您可以設定報表以及資料處理進行的正確時間。</span><span class="sxs-lookup"><span data-stu-id="61464-106">A report snapshot is usually created and subsequently refreshed on a schedule, allowing you to time exactly when report and data processing will occur.</span></span> <span data-ttu-id="61464-107">如果報表所依據的，是要花很長時間執行的查詢，或者使用您希望在幾個小時內沒有人能存取之資料來源中之資料的查詢，您應將報表當成快照集執行。</span><span class="sxs-lookup"><span data-stu-id="61464-107">If a report is based on queries that take a long time to run, or on queries that use data from a data source that you prefer no one access during certain hours, you should run the report as a snapshot.</span></span>  
  
-   <span data-ttu-id="61464-108">報表伺服器可以快取已處理報表的副本，並在使用者開啟報表時還原該副本。</span><span class="sxs-lookup"><span data-stu-id="61464-108">A report server can cache a copy of a processed report and return that copy when a user opens the report.</span></span> <span data-ttu-id="61464-109">快取是一種效能增強技術。</span><span class="sxs-lookup"><span data-stu-id="61464-109">Caching is a performance-enhancement technique.</span></span> <span data-ttu-id="61464-110">如果報表很大或存取頻繁，快取就可以縮短擷取報表所需的時間。</span><span class="sxs-lookup"><span data-stu-id="61464-110">Caching can shorten the time required to retrieve a report if the report is large or accessed frequently.</span></span>  
  
-   <span data-ttu-id="61464-111">報表記錄是之前所執行之報表副本的集合。</span><span class="sxs-lookup"><span data-stu-id="61464-111">Report history is a collection of previously run copies of a report.</span></span> <span data-ttu-id="61464-112">您可以使用報表記錄，以維護報表經過一段時間的記錄。</span><span class="sxs-lookup"><span data-stu-id="61464-112">You can use report history to maintain a record of a report over time.</span></span> <span data-ttu-id="61464-113">報表記錄不適用於包含機密或個人資料的報表。</span><span class="sxs-lookup"><span data-stu-id="61464-113">Report history is not intended for reports that contain confidential or personal data.</span></span> <span data-ttu-id="61464-114">因此，報表記錄只能包括使用一組認證 (預存認證或用於自動執行報表的認證) 來查詢資料來源的報表，此種認證是所有執行報表的使用者皆可使用的。</span><span class="sxs-lookup"><span data-stu-id="61464-114">For this reason, report history can include only those reports that query a data source using a single set of credentials (either stored credentials or credentials used for unattended report execution) that are available to all users who run a report.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="61464-115">使用 SharePoint 的簽出和簽入內容管理功能來儲存 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 內容類型的更新。</span><span class="sxs-lookup"><span data-stu-id="61464-115">integration with SharePoint uses the check out and check in content management features of SharePoint to save updates to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types.</span></span> <span data-ttu-id="61464-116">這包括建立報表快照集。</span><span class="sxs-lookup"><span data-stu-id="61464-116">This includes the creation of report snapshots.</span></span> <span data-ttu-id="61464-117">因此，如果您已經在文件庫上啟用版本控制，您將看到新報表記錄快照集建立時更新的報表版本。</span><span class="sxs-lookup"><span data-stu-id="61464-117">Therefore if you have enabled versioning on a document library, you will see the report version updated when a new report history snapshot is created.</span></span> <span data-ttu-id="61464-118">這是更新快照集的副作用。</span><span class="sxs-lookup"><span data-stu-id="61464-118">This is a side-effect of updating snapshots.</span></span> <span data-ttu-id="61464-119">當快照集更新時，它會使報表的 LastExecution 屬性變更，因此造成報表版本變更。</span><span class="sxs-lookup"><span data-stu-id="61464-119">When a snapshot is updated it causes the LastExecution property of the report to change and that will cause a change in the version of the report.</span></span>  
  
-   <span data-ttu-id="61464-120">您可以指定逾時值，以便設定系統資源的使用限制。</span><span class="sxs-lookup"><span data-stu-id="61464-120">You can specify time-out values to set limits on how system resources are used.</span></span>  
  
||  
|-|  
|<span data-ttu-id="61464-121">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="61464-121">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="61464-122">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="61464-122">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="61464-123">設定資料重新整理選項</span><span class="sxs-lookup"><span data-stu-id="61464-123">To set data refresh options</span></span>](#bkmk_set_data_refresh)  
  
-   [<span data-ttu-id="61464-124">設定報表快取選項</span><span class="sxs-lookup"><span data-stu-id="61464-124">To set report caching options</span></span>](#bkmk_set_report_caching)  
  
-   [<span data-ttu-id="61464-125">設定處理逾時值</span><span class="sxs-lookup"><span data-stu-id="61464-125">To set processing time-out values</span></span>](#bkmk_set_processing)  
  
-   [<span data-ttu-id="61464-126">設定報表記錄選項和限制</span><span class="sxs-lookup"><span data-stu-id="61464-126">To set report history options and limits</span></span>](#bkmk_set_report_history)  
  
-   [<span data-ttu-id="61464-127">設定資料庫逾時</span><span class="sxs-lookup"><span data-stu-id="61464-127">Set database timeout</span></span>](#bkmk_set_database_timeout)  
  
##  <a name="to-set-data-refresh-options"></a><a name="bkmk_set_data_refresh"></a><span data-ttu-id="61464-128">若要設定資料重新整理選項</span><span class="sxs-lookup"><span data-stu-id="61464-128">To set data refresh options</span></span>  
  
1.  <span data-ttu-id="61464-129">指向程式庫中的報表。</span><span class="sxs-lookup"><span data-stu-id="61464-129">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="61464-130">按一下向下箭頭，然後選取 **[管理處理選項]**。</span><span class="sxs-lookup"><span data-stu-id="61464-130">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="61464-131">在 **[資料重新整理選項]** 中，按一下 **[使用快照集資料]**。</span><span class="sxs-lookup"><span data-stu-id="61464-131">In **Data Refresh Options**, click **Use snapshot data**.</span></span> <span data-ttu-id="61464-132">如果您看見「此報表不可從快照集執行，因為有一或多個資料來源認證未儲存。」，表示報告未設定為自動執行，而且您必須先修改資料來源以使用儲存的認證，才能設定此選項。</span><span class="sxs-lookup"><span data-stu-id="61464-132">If you see "This report can not run from a snapshot because one or more of the data sources credentials are not stored", the report is not configured to run unattended and you must modify the data sources to use stored credentials before setting this option.</span></span>  
  
4.  <span data-ttu-id="61464-133">在 **[資料快照集選項]** 中，選取 **[排程資料處理]**。</span><span class="sxs-lookup"><span data-stu-id="61464-133">In **Data Snapshot Options**, select **Schedule data processing**.</span></span>  
  
5.  <span data-ttu-id="61464-134">如果要使用現有的共用排程，請選取 **[在共用排程上]** ，否則，請按一下 **[在自訂排程上]**，然後按一下 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="61464-134">Select **On a shared schedule** if you have an existing shared schedule that you want to use, otherwise click **On a custom schedule**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="61464-135">選取頻率、排程，以及開始和結束日期，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="61464-135">Select frequency, schedule, and start and end dates, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="61464-136">如果要立即建立搭配報表使用的快照集資料，而不想等到排程的資料處理發生，請在 **[資料快照集選項]** 中選取 **[儲存此頁面時建立或更新快照集]** 。</span><span class="sxs-lookup"><span data-stu-id="61464-136">In **Data Snapshot Options**, select **Create or update the snapshot when this page is saved** if you want to immediately create snapshot data to use with the report, without waiting for the scheduled data processing to occur.</span></span>  
  
##  <a name="to-set-report-caching-options"></a><a name="bkmk_set_report_caching"></a><span data-ttu-id="61464-137">若要設定報表快取選項</span><span class="sxs-lookup"><span data-stu-id="61464-137">To set report caching options</span></span>  
  
1.  <span data-ttu-id="61464-138">指向程式庫中的報表。</span><span class="sxs-lookup"><span data-stu-id="61464-138">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="61464-139">按一下向下箭頭，然後選取 **[管理處理選項]**。</span><span class="sxs-lookup"><span data-stu-id="61464-139">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="61464-140">在 **[資料重新整理選項]** 中，按一下 **[使用快取的資料]**。</span><span class="sxs-lookup"><span data-stu-id="61464-140">In **Data Refresh Options**, click **Use cached data**.</span></span> <span data-ttu-id="61464-141">如果您看見「無法快取此報表，因為有一或多個資料來源認證未儲存。」，表示報告未設定為自動執行，而且您必須先修改資料來源以使用儲存的認證，才能設定此選項。</span><span class="sxs-lookup"><span data-stu-id="61464-141">If you see "This report can not be cached because one or more of the data sources credentials are not stored", the report is not configured to run unattended and you must modify the data sources to use stored credentials before setting this option.</span></span>  
  
4.  <span data-ttu-id="61464-142">在 **[快取選項]** 中，指定快取過期的方式：</span><span class="sxs-lookup"><span data-stu-id="61464-142">In **Cache Options**, specify how the cache will expire:</span></span>  
  
    -   <span data-ttu-id="61464-143">輸入分鐘數，快取將在經過此分鐘數之後過期。</span><span class="sxs-lookup"><span data-stu-id="61464-143">Enter a number of minutes after which the cache will expire.</span></span>  
  
    -   <span data-ttu-id="61464-144">使用共用排程按照排程中指定的時間清除快取。</span><span class="sxs-lookup"><span data-stu-id="61464-144">Use a shared schedule to clear the cache at times specified in the schedule.</span></span>  
  
    -   <span data-ttu-id="61464-145">建立自訂排程按照指定的時間清除快取。</span><span class="sxs-lookup"><span data-stu-id="61464-145">Create a custom schedule to clear the cache at a time that you specify.</span></span>  
  
##  <a name="to-set-processing-time-out-values"></a><a name="bkmk_set_processing"></a><span data-ttu-id="61464-146">設定處理超時值</span><span class="sxs-lookup"><span data-stu-id="61464-146">To set processing time-out values</span></span>  
  
1.  <span data-ttu-id="61464-147">指向程式庫中的報表。</span><span class="sxs-lookup"><span data-stu-id="61464-147">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="61464-148">按一下向下箭頭，然後選取 **[管理處理選項]** 。</span><span class="sxs-lookup"><span data-stu-id="61464-148">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="61464-149">如果您要使用在報表伺服器層級指定的值，請在 [處理逾時]\*\*\*\* 中選取 [使用網站預設值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="61464-149">In **Processing Time-out**, select **Use site default setting** if you want to use the value specified at the report server level.</span></span> <span data-ttu-id="61464-150">否則，請選取 [報表處理不會逾時]\*\*\*\* 或 [限制報表處理的秒數]\*\*\*\*，使用無逾時或其他逾時值覆寫該值。</span><span class="sxs-lookup"><span data-stu-id="61464-150">Otherwise, select **Do not time out report processing** or **Limit report processing in seconds** if you want to override that value with no time-out or different time-out values.</span></span>  
  
##  <a name="to-set-report-history-options-and-limits"></a><a name="bkmk_set_report_history"></a><span data-ttu-id="61464-151">若要設定報表記錄選項和限制</span><span class="sxs-lookup"><span data-stu-id="61464-151">To set report history options and limits</span></span>  
  
1.  <span data-ttu-id="61464-152">指向程式庫中的報表。</span><span class="sxs-lookup"><span data-stu-id="61464-152">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="61464-153">按一下向下箭頭，然後選取 **[管理處理選項]**。</span><span class="sxs-lookup"><span data-stu-id="61464-153">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="61464-154">在 **[記錄快照集選項]** 中，指定資料處理發生和儲存的方式及時間。</span><span class="sxs-lookup"><span data-stu-id="61464-154">In **History Snapshot Options**, specify how and when data processing occurs and is saved.</span></span>  
  
4.  <span data-ttu-id="61464-155">如果要使用在報表伺服器層級指定的值，請在 **[記錄快照集限制]** 中選取 **[使用站台預設值]** 。</span><span class="sxs-lookup"><span data-stu-id="61464-155">In **History Snapshot Limits**, select **Use site default setting** if you want to use the value specified at the report server level.</span></span> <span data-ttu-id="61464-156">否則，請選取 **[不限制快照集數目]** 或 **[限制快照集數目為]** 指定自訂值。</span><span class="sxs-lookup"><span data-stu-id="61464-156">Otherwise, select **Do not limit the number of snapshots** or **Limit number of snapshots** to specify a custom value.</span></span>  
  
##  <a name="set-database-timeout"></a><a name="bkmk_set_database_timeout"></a><span data-ttu-id="61464-157">設定資料庫超時</span><span class="sxs-lookup"><span data-stu-id="61464-157">Set database timeout</span></span>  
  
1.  <span data-ttu-id="61464-158">使用 Windows PowerShell 設定的 SharePoint 報表伺服器資料庫逾時。</span><span class="sxs-lookup"><span data-stu-id="61464-158">Use Windows PowerShell to set the database timeout of a SharePoint report server.</span></span> <span data-ttu-id="61464-159">如需詳細資訊，請參閱 [Reporting Services SharePoint 模式的 PowerShell Cmdlet](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) 的＜取得及設定 Reporting Services 應用程式資料庫的屬性＞一節。</span><span class="sxs-lookup"><span data-stu-id="61464-159">For more information, see the "Get and set Properties of the Reporting Service Application Database" section of [PowerShell cmdlets for Reporting Services SharePoint Mode](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61464-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61464-160">See Also</span></span>  
 <span data-ttu-id="61464-161">[設定報表處理屬性](report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="61464-161">[Set Report Processing Properties](report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="61464-162">[快取多個報表 &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="61464-162">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 [<span data-ttu-id="61464-163">設定報表和共用資料集處理的逾時值 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="61464-163">Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;</span></span>](report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
  
  
