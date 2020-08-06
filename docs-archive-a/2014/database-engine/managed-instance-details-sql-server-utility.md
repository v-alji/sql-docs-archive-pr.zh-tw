---
title: 受控執行個體詳細資料 (SQL Server 公用程式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 6e51b7bb-a733-4852-8c33-7f4dbdf931c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f895f9978511ab7b2b40b3f161185a68a497b2eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706702"
---
# <a name="managed-instance-details-sql-server-utility"></a><span data-ttu-id="70832-102">受管理的執行個體詳細資料 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="70832-102">Managed Instance Details (SQL Server Utility)</span></span>
  <span data-ttu-id="70832-103">公用程式總管之 Managed 執行個體檢視中的資訊提供了個別 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體的使用量資料、CPU 使用量歷程記錄、檔案層級的儲存使用量詳細資料，以及檢視和更新原則臨界值的功能。</span><span class="sxs-lookup"><span data-stu-id="70832-103">Information in the Managed Instances view of Utility Explorer provides utilization data for individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], CPU utilization history, storage utilization details at the file level, and the ability to view and update policy thresholds.</span></span> <span data-ttu-id="70832-104">原則臨界值可以針對電腦及資料庫檔案和記錄檔在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體層級控制，也可以在存放磁碟區的層級控制。</span><span class="sxs-lookup"><span data-stu-id="70832-104">Policy thresholds can be controlled at the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance level, for a computer, for database files and log files, and at the level of storage volumes.</span></span> <span data-ttu-id="70832-105">您也可以針對個別的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Managed 執行個體檢視屬性詳細資料。</span><span class="sxs-lookup"><span data-stu-id="70832-105">You can also view property details for individual managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="70832-106">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="70832-106">UI element list</span></span>  
 <span data-ttu-id="70832-107">[清單] 檢視</span><span class="sxs-lookup"><span data-stu-id="70832-107">List view</span></span>  
 <span data-ttu-id="70832-108">上方窗格的清單檢視會依據 ComputerName\InstanceName 顯示列於資料列中的個別 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="70832-108">The list view in the top pane displays data about individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] listed in rows by ComputerName\InstanceName.</span></span>  
  
 <span data-ttu-id="70832-109">健全狀態圖示會依據使用量類別提供每一個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的狀態摘要：</span><span class="sxs-lookup"><span data-stu-id="70832-109">Health state icons provide summary status for each instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by utilization category:</span></span>  
  
-   <span data-ttu-id="70832-110">綠色核取符號 - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - 不違反資源使用量原則的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 受控執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="70832-110">Green check - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - Number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] which are not violating resource utilization policies.</span></span> <span data-ttu-id="70832-111">資源的使用情況良好。</span><span class="sxs-lookup"><span data-stu-id="70832-111">Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="70832-112">綠色向下箭頭 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - 資源使用量過低。</span><span class="sxs-lookup"><span data-stu-id="70832-112">Green down arrow - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="70832-113">紅色向上箭頭 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - 資源使用量過高。</span><span class="sxs-lookup"><span data-stu-id="70832-113">Red up arrow - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="70832-114">您可以變更清單檢視中資料行的順序，其方式是將資料行拖曳到左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="70832-114">The sequence of columns in the list view can be changed by dragging them to the left or the right.</span></span> <span data-ttu-id="70832-115">您可以加入或刪除清單檢視中的資料行，其方式是以滑鼠右鍵按一下資料行標題，並選取或取消選取資料行。</span><span class="sxs-lookup"><span data-stu-id="70832-115">Columns in the list view can be added or deleted by right-clicking on the column headings and selecting or unselecting columns.</span></span> <span data-ttu-id="70832-116">右鍵功能表也會提供排序選項。</span><span class="sxs-lookup"><span data-stu-id="70832-116">The right-click menu also provides sort options.</span></span> <span data-ttu-id="70832-117">您也可以按一下資料行名稱的上方來啟動排序。</span><span class="sxs-lookup"><span data-stu-id="70832-117">Sorting can also be activated by clicking at the top of a column name.</span></span>  
  
 <span data-ttu-id="70832-118">若要存取公用程式清單檢視的篩選選項，請在 [公用程式總管] 瀏覽窗格中以滑鼠右鍵按一下 [Managed 執行個體] 節點，並選取 [篩選]。</span><span class="sxs-lookup"><span data-stu-id="70832-118">To access filter options for the Utility list view, right-click on the **Managed Instances** node in the Utility Explorer navigation pane, and select **Filter**.</span></span> <span data-ttu-id="70832-119">當已經實作篩選設定之後，公用程式總管中的 [受管理的執行個體] 節點將會標示 [受管理的執行個體 (已篩選)]。</span><span class="sxs-lookup"><span data-stu-id="70832-119">After filter settings have been implemented, the **Managed Instances** node in Utility Explorer will be labeled **Managed Instances (filtered)**.</span></span> <span data-ttu-id="70832-120">如需詳細資訊，請參閱[篩選設定 &#40;物件總管與公用程式總管&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="70832-120">For more information, see [Filter Settings &#40;Object Explorer and Utility Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).</span></span>  
  
 <span data-ttu-id="70832-121">根據預設，下列資料行會顯示有關每一個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Managed 執行個體的健全狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="70832-121">By default, the following columns display health state information about each managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="70832-122">執行個體 CPU - 顯示配置給這個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體之處理器使用量的健全狀態。</span><span class="sxs-lookup"><span data-stu-id="70832-122">Instance CPU - Displays the health state of processor utilization allocated to this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="70832-123">這個參數的健全狀態是根據針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體設定的 CPU 使用量原則及動態資源評估原則的組態設定所決定。</span><span class="sxs-lookup"><span data-stu-id="70832-123">The health state for this parameter is determined according to CPU utilization policy set for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="70832-124">如需詳細資訊，請參閱[降低 CPU 使用量原則的雜訊 &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="70832-124">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="70832-125">若要檢視這個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的處理器使用量歷程記錄，或是檢視或變更原則限制，請按一下 [CPU 使用量] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="70832-125">To view the processor utilization history for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="70832-126">電腦 CPU - 顯示電腦處理器使用量的健全狀態。</span><span class="sxs-lookup"><span data-stu-id="70832-126">Computer CPU - Displays the health state of computer processor utilization.</span></span> <span data-ttu-id="70832-127">這個參數的健全狀態是根據針對電腦設定的 CPU 使用量原則及動態資源評估原則的組態設定所決定。</span><span class="sxs-lookup"><span data-stu-id="70832-127">The health state for this parameter is determined according to CPU utilization policy set for the computer and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="70832-128">如需詳細資訊，請參閱[降低 CPU 使用量原則的雜訊 &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="70832-128">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="70832-129">若要檢視這個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的處理器使用量歷程記錄，或是檢視或變更原則限制，請按一下 [CPU 使用量] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="70832-129">To view the processor utilization history for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="70832-130">檔案空間 - 針對屬於選定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的所有資料庫來顯示檔案空間使用量的健全狀態摘要。</span><span class="sxs-lookup"><span data-stu-id="70832-130">File Space - Displays a summary of health states of file space utilization for all databases that belong to the selected instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="70832-131">如果任何資料庫的健全狀態指出使用量過高，則檔案空間健全狀態將會在清單檢視中報告為使用量過高。</span><span class="sxs-lookup"><span data-stu-id="70832-131">If the health state of any database is overutilized, then the file space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="70832-132">如果任何資料庫的健全狀態指出使用量過低，而且沒有任何資料庫使用量過高，則檔案空間健全狀態將會在清單檢視中報告為使用量過低。</span><span class="sxs-lookup"><span data-stu-id="70832-132">If the health state of any database is underutilized, and no database is overutilized, then the file space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="70832-133">否則，檔案空間健全狀態將會在清單檢視中報告為使用良好。</span><span class="sxs-lookup"><span data-stu-id="70832-133">Otherwise, the file space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="70832-134">若要檢視或變更原則限制，請按一下 [儲存使用量] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="70832-134">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="70832-135">磁碟區空間 - 針對包含了屬於選定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體之資料庫的所有磁碟區來顯示磁碟區空間使用量的健全狀態摘要。</span><span class="sxs-lookup"><span data-stu-id="70832-135">Volume Space - Displays a summary of the health states of volume space utilization for all volumes that contain databases belonging to the selected instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="70832-136">如果任何磁碟區的健全狀態指出使用量過高，則磁碟區空間健全狀態將會在清單檢視中報告為使用量過高。</span><span class="sxs-lookup"><span data-stu-id="70832-136">If the health state of any volume is overutilized, then the volume space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="70832-137">如果任何磁碟區的健全狀態指出使用量過低，而且沒有任何磁碟區使用量過高，則磁碟區空間健全狀態將會在清單檢視中報告為使用量過低。</span><span class="sxs-lookup"><span data-stu-id="70832-137">If the health state of any volume is underutilized, and no volume is overutilized, then the volume space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="70832-138">否則，磁碟區空間健全狀態將會在清單檢視中報告為使用良好。</span><span class="sxs-lookup"><span data-stu-id="70832-138">Otherwise, the volume space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="70832-139">若要檢視或變更原則限制，請按一下 [儲存使用量] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="70832-139">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="70832-140">原則類型 - 指出「全域」預設原則還是「覆寫」自訂原則對於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的 Managed 執行個體有效。</span><span class="sxs-lookup"><span data-stu-id="70832-140">Policy Type - Indicates whether "Global" default policies or "Override" custom policies are in effect for the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="70832-141">可以使用清單檢視中資料行標題區域內的右鍵功能表來顯示的其他資料行：</span><span class="sxs-lookup"><span data-stu-id="70832-141">Other columns that can be displayed using the right-click menu in the column heading area of the list view:</span></span>  
  
-   <span data-ttu-id="70832-142">處理器名稱：</span><span class="sxs-lookup"><span data-stu-id="70832-142">Processor Name:</span></span>  
  
-   <span data-ttu-id="70832-143">處理器速度 (MHz)：</span><span class="sxs-lookup"><span data-stu-id="70832-143">Processor Speed (MHz):</span></span>  
  
-   <span data-ttu-id="70832-144">處理器計數：</span><span class="sxs-lookup"><span data-stu-id="70832-144">Processor Count:</span></span>  
  
-   <span data-ttu-id="70832-145">實體記憶體 (MB)：</span><span class="sxs-lookup"><span data-stu-id="70832-145">Physical Memory (MB):</span></span>  
  
-   <span data-ttu-id="70832-146">作業系統版本：</span><span class="sxs-lookup"><span data-stu-id="70832-146">Operating System Version:</span></span>  
  
-   <span data-ttu-id="70832-147">SQL Server 版本：</span><span class="sxs-lookup"><span data-stu-id="70832-147">SQL Server Version:</span></span>  
  
-   <span data-ttu-id="70832-148">SQL Server 版本：</span><span class="sxs-lookup"><span data-stu-id="70832-148">SQL Server Edition:</span></span>  
  
-   <span data-ttu-id="70832-149">叢集：(True 或 False)</span><span class="sxs-lookup"><span data-stu-id="70832-149">Clustered: (True or False)</span></span>  
  
-   <span data-ttu-id="70832-150">備份目錄：</span><span class="sxs-lookup"><span data-stu-id="70832-150">Backup Directory:</span></span>  
  
-   <span data-ttu-id="70832-151">定序：</span><span class="sxs-lookup"><span data-stu-id="70832-151">Collation:</span></span>  
  
-   <span data-ttu-id="70832-152">區分大小寫：(True 或 False)</span><span class="sxs-lookup"><span data-stu-id="70832-152">Case Sensitive: (True or False)</span></span>  
  
-   <span data-ttu-id="70832-153">語言：</span><span class="sxs-lookup"><span data-stu-id="70832-153">Language:</span></span>  
  
-   <span data-ttu-id="70832-154">上次報告時間：此資料行會使用 datetime 資料類型來顯示 UCP 本機日期和時間。</span><span class="sxs-lookup"><span data-stu-id="70832-154">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="70832-155">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主題。</span><span class="sxs-lookup"><span data-stu-id="70832-155">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="70832-156">當您使用公用程式物件模型時，請注意 SSMS 會使用 datetimeoffset 資料類型。</span><span class="sxs-lookup"><span data-stu-id="70832-156">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="70832-157">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主題。</span><span class="sxs-lookup"><span data-stu-id="70832-157">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="70832-158">CPU 使用量索引標籤</span><span class="sxs-lookup"><span data-stu-id="70832-158">CPU Utilization tab</span></span>  
 <span data-ttu-id="70832-159">[CPU 使用量] 索引標籤會針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體和電腦的 CPU 使用量顯示歷程記錄資料的並排圖形。</span><span class="sxs-lookup"><span data-stu-id="70832-159">The CPU utilization tab shows side-by-side graphs of historical data for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and computer CPU utilization.</span></span>  
  
 <span data-ttu-id="70832-160">此圖形會針對顯示區域右邊的選項按鈕中指定的間隔，顯示處理器使用量歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="70832-160">The graph displays the processor utilization history for the interval specified in the radio buttons on the right side of the display area.</span></span> <span data-ttu-id="70832-161">若要變更顯示間隔並重新整理資料集，請從清單中選取選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="70832-161">To change the display interval and refresh the data set, select a radio button from the list.</span></span>  
  
 <span data-ttu-id="70832-162">間隔選項如下：</span><span class="sxs-lookup"><span data-stu-id="70832-162">Interval options are as follows:</span></span>  
  
-   <span data-ttu-id="70832-163">1 天，每隔 15 分鐘顯示。</span><span class="sxs-lookup"><span data-stu-id="70832-163">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="70832-164">1 週，每隔 1 天顯示。</span><span class="sxs-lookup"><span data-stu-id="70832-164">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="70832-165">1 個月，每隔 1 週顯示。</span><span class="sxs-lookup"><span data-stu-id="70832-165">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="70832-166">1 年，每隔 1 個月顯示。</span><span class="sxs-lookup"><span data-stu-id="70832-166">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="70832-167">儲存使用量索引標籤</span><span class="sxs-lookup"><span data-stu-id="70832-167">Storage Utilization tab</span></span>  
 <span data-ttu-id="70832-168">[儲存使用量] 索引標籤具有樹狀檢視，可顯示儲存使用量詳細資料。</span><span class="sxs-lookup"><span data-stu-id="70832-168">The Storage Utilization tab has a tree view that displays storage utilization details.</span></span> <span data-ttu-id="70832-169">請注意，時間資料會使用 datetime 資料類型來顯示 UCP 本機日期和時間。</span><span class="sxs-lookup"><span data-stu-id="70832-169">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="70832-170">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主題。</span><span class="sxs-lookup"><span data-stu-id="70832-170">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="70832-171">當您使用公用程式物件模型時，請注意 SSMS 會使用 datetimeoffset 資料類型。</span><span class="sxs-lookup"><span data-stu-id="70832-171">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="70832-172">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主題。</span><span class="sxs-lookup"><span data-stu-id="70832-172">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="70832-173">顯示畫面可以依資料庫或磁碟區來分組。</span><span class="sxs-lookup"><span data-stu-id="70832-173">Display can be grouped by database or by volume.</span></span> <span data-ttu-id="70832-174">若要使用資料庫樹狀檢視，請選取 [檔案群組依據:] 選項中的 [資料庫] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="70832-174">To use the database tree view, select the **Database** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="70832-175">若要檢視個別資料庫檔案的儲存使用量狀態，請按一下樹狀檢視中資料庫名稱旁邊的加號。</span><span class="sxs-lookup"><span data-stu-id="70832-175">To view storage utilization status for individual database files, click on the plus sign next to a database name in the tree view.</span></span> <span data-ttu-id="70832-176">列出的資料庫檔案包含了所有屬於您在清單檢視中選取之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 受管理的執行個體的系統資料庫和使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="70832-176">The database files listed include all system and user databases that belong to the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] you selected in the list view.</span></span>  
  
 <span data-ttu-id="70832-177">樹狀結構會對應到儲存階層。</span><span class="sxs-lookup"><span data-stu-id="70832-177">The tree structure corresponds to the storage hierarchy.</span></span> <span data-ttu-id="70832-178">樹狀檢視中的根節點為資料庫。</span><span class="sxs-lookup"><span data-stu-id="70832-178">The root node in the tree view is the database.</span></span> <span data-ttu-id="70832-179">樹狀檢視的下一層包含屬於資料庫的檔案群組節點，或是屬於資料庫之記錄的記錄檔節點。</span><span class="sxs-lookup"><span data-stu-id="70832-179">The next level of the tree view contains a filegroup node or nodes that belong to the database, and a log file node for the logs that belong to the database.</span></span> <span data-ttu-id="70832-180">下一層包含屬於檔案群組的資料檔。</span><span class="sxs-lookup"><span data-stu-id="70832-180">The next level contains the data files that belong to the filegroup.</span></span>  
  
 <span data-ttu-id="70832-181">儲存使用量歷程記錄圖形中顯示的資料會因為樹狀檢視中選取的節點而有所不同：</span><span class="sxs-lookup"><span data-stu-id="70832-181">Data displayed in the graph of storage utilization history changes depending on the node selected in the tree view:</span></span>  
  
-   <span data-ttu-id="70832-182">選取檔案群組節點，以顯示屬於選定檔案群組之所有資料檔案所使用的檔案空間圖形。</span><span class="sxs-lookup"><span data-stu-id="70832-182">Select the file group node to display a graph of file space used by all data files that belong to the selected file group.</span></span>  
  
-   <span data-ttu-id="70832-183">選取記錄檔節點，以顯示屬於選定資料庫之所有記錄檔所使用的檔案空間圖形。</span><span class="sxs-lookup"><span data-stu-id="70832-183">Select the log file node to display a graph of file space used by all log files that belong to the selected database.</span></span>  
  
-   <span data-ttu-id="70832-184">選取資料庫節點來顯示一個圖形，此圖形會加入屬於選定資料庫之所有資料檔案和記錄檔所使用的檔案空間。</span><span class="sxs-lookup"><span data-stu-id="70832-184">Select the database node to display a graph that adds file space used by all data files and all log files that belong to the selected database.</span></span>  
  
 <span data-ttu-id="70832-185">健全狀態圖示會提供資料庫檔案、檔案群組和記錄檔的大致狀態：</span><span class="sxs-lookup"><span data-stu-id="70832-185">Health state icons provide at-a-glance status for database files, filegroups, and log files:</span></span>  
  
 <span data-ttu-id="70832-186">如果是資料庫：</span><span class="sxs-lookup"><span data-stu-id="70832-186">For databases:</span></span>  
  
-   <span data-ttu-id="70832-187">綠色核取符號 - 所有檔案群組和記錄檔的健全狀態 (既不是使用量過高，也不是使用量過低)。</span><span class="sxs-lookup"><span data-stu-id="70832-187">Green check - Health states of all filegroups and log files a neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="70832-188">綠色向下箭頭 - 至少一個檔案群組或記錄檔的健全狀態表示使用量過低，而沒有任何健全狀態指出使用量過高。</span><span class="sxs-lookup"><span data-stu-id="70832-188">Green down arrow - Health states of at least one filegroup or log file is underutilized, and no health states are overutilized.</span></span>  
  
-   <span data-ttu-id="70832-189">紅色向上箭頭 - 至少一個檔案群組或記錄檔的健全狀態指出使用量過高。</span><span class="sxs-lookup"><span data-stu-id="70832-189">Red up arrow - The health state of at least one filegroup or log file is overutilized.</span></span>  
  
 <span data-ttu-id="70832-190">如果是檔案群組和記錄檔：</span><span class="sxs-lookup"><span data-stu-id="70832-190">For filegroups and log files:</span></span>  
  
-   <span data-ttu-id="70832-191">綠色核取符號 - 檔案群組中所有檔案的檔案空間使用量既不是使用量過高，也不是使用量過低。</span><span class="sxs-lookup"><span data-stu-id="70832-191">Green check - File space utilization for all files in the filegroup are neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="70832-192">綠色向下箭頭 - 檔案群組中至少一個檔案的檔案空間使用量過低，而且檔案群組中沒有任何檔案的使用量過高。</span><span class="sxs-lookup"><span data-stu-id="70832-192">Green down arrow - File space utilization for at least one file in the filegroup is underutilized, and no files in the filegroup are overutilized.</span></span>  
  
-   <span data-ttu-id="70832-193">紅色向上箭頭 - 檔案群組中所有資料檔案的檔案空間使用量過高。</span><span class="sxs-lookup"><span data-stu-id="70832-193">Red up arrow - File space utilization for all data files in the filegroup are overutilized.</span></span>  
  
 <span data-ttu-id="70832-194">若要依磁碟區檢視檔案，請選取 [檔案群組依據] 選項中的 [磁碟區] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="70832-194">To view files by volume, select the **Volume** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="70832-195">儲存使用量歷程記錄的圖形會顯示存放磁碟區上所有資料檔案和記錄檔所使用的檔案空間。</span><span class="sxs-lookup"><span data-stu-id="70832-195">The graph of storage utilization history displays file space used by all data files and all log files on the storage volume.</span></span> <span data-ttu-id="70832-196">針對個別資料庫資料檔案和記錄檔展開此樹狀目錄來檢視詳細資料。</span><span class="sxs-lookup"><span data-stu-id="70832-196">Expand the tree to view details for individual database data files and log files.</span></span>  
  
 <span data-ttu-id="70832-197">狀態圖示用來提供每個磁碟區的狀態：</span><span class="sxs-lookup"><span data-stu-id="70832-197">Status icons are used to provide status for each volume:</span></span>  
  
-   <span data-ttu-id="70832-198">綠色核取符號 - 資源使用情況良好。</span><span class="sxs-lookup"><span data-stu-id="70832-198">Green check - Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="70832-199">綠色向下箭頭 - 資源使用量過低。</span><span class="sxs-lookup"><span data-stu-id="70832-199">Green down arrow - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="70832-200">紅色向上箭頭 - 資源使用量過高。</span><span class="sxs-lookup"><span data-stu-id="70832-200">Red up arrow - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="70832-201">[儲存使用量] 索引標籤上每一個檔案名稱旁邊的量測計都代表檔案所使用的空間量 (相較於檔案的有效容量)。</span><span class="sxs-lookup"><span data-stu-id="70832-201">The gauge next to each file name on the Storage Utilization tab represents the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="70832-202">量測計旁邊所顯示的百分比值為檔案所使用的空間量比率 (相較於檔案的有效容量)。</span><span class="sxs-lookup"><span data-stu-id="70832-202">The percentage value displayed next to the gauge is the ratio of the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="70832-203">工具提示所提供的資料是用來計算每一個磁碟區和每一個檔案相較於有效容量的百分比。</span><span class="sxs-lookup"><span data-stu-id="70832-203">Tool tips provide data used to calculate percentages for each volume and each file compared to effective capacity.</span></span>  
  
 <span data-ttu-id="70832-204">如果檔案未設定為自動成長，有效容量就是配置給檔案的空間數量。</span><span class="sxs-lookup"><span data-stu-id="70832-204">If the file is not configured to auto-grow, then the effective capacity is the amount of space allocated to the file.</span></span> <span data-ttu-id="70832-205">如果檔案設定為自動成長，則有效容量就是目前配置給檔案之空間數量與目前磁碟區上可用空間數量的總和。</span><span class="sxs-lookup"><span data-stu-id="70832-205">If the file is configured to auto-grow, then the effective capacity is the sum of the amount of space currently allocated to the file and the amount of free space currently available on the volume.</span></span>  
  
 <span data-ttu-id="70832-206">可以針對資料檔案和記錄檔設定儲存使用量原則。</span><span class="sxs-lookup"><span data-stu-id="70832-206">Storage utilization policies can be configured for data files and for log files.</span></span> <span data-ttu-id="70832-207">若要檢視或變更檔案的儲存使用量原則臨界值，請按一下 [儲存使用量] 窗格底部的 [檔案原則] 連結。</span><span class="sxs-lookup"><span data-stu-id="70832-207">To view or change the storage utilization policy thresholds for files, click on the **File Policy** link at the bottom of the Storage Utilization pane.</span></span> <span data-ttu-id="70832-208">若要檢視或變更存放磁碟區的儲存使用量原則臨界值，請按一下 [儲存使用量] 窗格底部的 [磁碟區原則] 連結。</span><span class="sxs-lookup"><span data-stu-id="70832-208">To view or change the storage utilization policy thresholds for a storage volume, click on the **Volume Policy** link at the bottom of the Storage Utilization pane.</span></span>  
  
 <span data-ttu-id="70832-209">若要覆寫預設原則閾值，請按一下 [覆寫預設原則] 選項按鈕，並指定上限和下限值，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="70832-209">To override the default policy thresholds, click on the radio button to **Override the default policy**, specify values for the upper and lower limits, then click **OK**.</span></span>  
  
 <span data-ttu-id="70832-210">如需變更原則違規容錯的詳細資訊，請參閱[降低 CPU 使用量原則的雜訊 &#40;SQL Server 公用程式&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="70832-210">For more information about changing the tolerance for policy violations, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="70832-211">屬性詳細資料索引標籤</span><span class="sxs-lookup"><span data-stu-id="70832-211">Property Details tab</span></span>  
 <span data-ttu-id="70832-212">針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體列出的屬性詳細資料包括以下類別：</span><span class="sxs-lookup"><span data-stu-id="70832-212">Property details listed for instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] include the following categories:</span></span>  
  
-   <span data-ttu-id="70832-213">處理器名稱：</span><span class="sxs-lookup"><span data-stu-id="70832-213">Processor Name:</span></span>  
  
-   <span data-ttu-id="70832-214">處理器速度 (MHz)：</span><span class="sxs-lookup"><span data-stu-id="70832-214">Processor Speed (MHz):</span></span>  
  
-   <span data-ttu-id="70832-215">處理器計數：</span><span class="sxs-lookup"><span data-stu-id="70832-215">Processor Count:</span></span>  
  
-   <span data-ttu-id="70832-216">實體記憶體 (MB)：</span><span class="sxs-lookup"><span data-stu-id="70832-216">Physical Memory (MB):</span></span>  
  
-   <span data-ttu-id="70832-217">作業系統版本：</span><span class="sxs-lookup"><span data-stu-id="70832-217">Operating System Version:</span></span>  
  
-   <span data-ttu-id="70832-218">SQL Server 版本：</span><span class="sxs-lookup"><span data-stu-id="70832-218">SQL Server Version:</span></span>  
  
-   <span data-ttu-id="70832-219">SQL Server 版本：</span><span class="sxs-lookup"><span data-stu-id="70832-219">SQL Server Edition:</span></span>  
  
-   <span data-ttu-id="70832-220">叢集：(True 或 False)</span><span class="sxs-lookup"><span data-stu-id="70832-220">Clustered: (True or False)</span></span>  
  
-   <span data-ttu-id="70832-221">備份目錄：</span><span class="sxs-lookup"><span data-stu-id="70832-221">Backup Directory:</span></span>  
  
-   <span data-ttu-id="70832-222">定序：</span><span class="sxs-lookup"><span data-stu-id="70832-222">Collation:</span></span>  
  
-   <span data-ttu-id="70832-223">區分大小寫：(True 或 False)</span><span class="sxs-lookup"><span data-stu-id="70832-223">Case Sensitive: (True or False)</span></span>  
  
-   <span data-ttu-id="70832-224">語言：</span><span class="sxs-lookup"><span data-stu-id="70832-224">Language:</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70832-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70832-225">See Also</span></span>  
 <span data-ttu-id="70832-226">[部署的資料層應用程式詳細資料 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="70832-226">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="70832-227">[公用程式儀表板 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="70832-227">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="70832-228">[監視 SQL Server 公用程式中的 SQL Server 執行個體](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="70832-228">[Monitor Instances of SQL Server in the SQL Server Utility](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span></span>  
 <span data-ttu-id="70832-229">[SQL Server 公用程式的功能與工作](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="70832-229">[SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="70832-230">疑難排解 SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="70832-230">Troubleshoot the SQL Server Utility</span></span>](../../2014/database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
