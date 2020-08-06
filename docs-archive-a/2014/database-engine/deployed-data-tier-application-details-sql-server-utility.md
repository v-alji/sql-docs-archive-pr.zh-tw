---
title: " (SQL Server 公用程式) 部署的資料層應用程式詳細資料 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.dac.details.F1
helpviewer_keywords:
- utility, management
- Utility
- SQL Server Utility [SQL Server]
- data-tier application [SQL Server], utility details
- Multi-server management [SQL Server]
ms.assetid: 79c41dd9-abcb-434e-9326-00a341d5c867
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58d0933dcb7682210dde24c3c6d3a9a539d02b1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593565"
---
# <a name="deployed-data-tier-application-details-sql-server-utility"></a><span data-ttu-id="f8728-102">部署的資料層應用程式詳細資料 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="f8728-102">Deployed Data-tier Application Details (SQL Server Utility)</span></span>
  <span data-ttu-id="f8728-103">公用程式總管之 [部署的資料層應用程式] 檢視中的資訊提供了個別資料層應用程式的使用量資料、CPU 使用量歷程記錄、檔案層級的儲存使用量詳細資料，以及檢視和更新原則臨界值的功能。</span><span class="sxs-lookup"><span data-stu-id="f8728-103">Information in the Deployed Data-tier Applications view of Utility Explorer provides utilization data for individual data-tier applications, CPU utilization history, storage utilization details at the file level, and the ability to view and update policy thresholds.</span></span> <span data-ttu-id="f8728-104">原則臨界值可以針對 CPU 使用量及資料庫的資料檔案和記錄檔，於資料層應用程式層級進行控制。</span><span class="sxs-lookup"><span data-stu-id="f8728-104">Policy thresholds can be controlled at the data-tier application level for CPU utilization and for database data files and log files.</span></span> <span data-ttu-id="f8728-105">您也可以針對個別的資料層應用程式來檢視屬性詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f8728-105">You can also view property details for individual data-tier applications.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="f8728-106">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="f8728-106">UI element list</span></span>  
 <span data-ttu-id="f8728-107">[清單] 檢視</span><span class="sxs-lookup"><span data-stu-id="f8728-107">List view</span></span>  
 <span data-ttu-id="f8728-108">上方窗格中的清單檢視會顯示有關個別資料層應用程式的資料。</span><span class="sxs-lookup"><span data-stu-id="f8728-108">The list view in the top pane displays data about individual data-tier applications.</span></span> <span data-ttu-id="f8728-109">健全狀態圖示會依據使用量類別提供每一個資料層應用程式的狀態摘要：</span><span class="sxs-lookup"><span data-stu-id="f8728-109">Health state icons provide summary status for each data-tier application by utilization category:</span></span>  
  
-   <span data-ttu-id="f8728-110">綠色核取符號 - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - 不違反資源使用量原則的資料層應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="f8728-110">Green check - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - Number of data-tier application which are not violating resource utilization policies.</span></span> <span data-ttu-id="f8728-111">資源的使用情況良好。</span><span class="sxs-lookup"><span data-stu-id="f8728-111">Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="f8728-112">綠色向下箭頭 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - 資源使用量過低。</span><span class="sxs-lookup"><span data-stu-id="f8728-112">Green down arrow - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="f8728-113">紅色向上箭頭 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - 資源使用量過高。</span><span class="sxs-lookup"><span data-stu-id="f8728-113">Red up arrow - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="f8728-114">您可以變更清單檢視中資料行的順序，其方式是將資料行拖曳到左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="f8728-114">The sequence of columns in the list view can be changed by dragging them to the left or the right.</span></span> <span data-ttu-id="f8728-115">您可以加入或刪除清單檢視中的資料行，其方式是以滑鼠右鍵按一下資料行標題，並選取或取消選取資料行。</span><span class="sxs-lookup"><span data-stu-id="f8728-115">Columns in the list view can be added or deleted by right-clicking on the column headings and selecting or unselecting columns.</span></span> <span data-ttu-id="f8728-116">右鍵功能表也會提供排序選項。</span><span class="sxs-lookup"><span data-stu-id="f8728-116">The right-click menu also provides sort options.</span></span> <span data-ttu-id="f8728-117">您也可以按一下資料行名稱的上方來啟動排序。</span><span class="sxs-lookup"><span data-stu-id="f8728-117">Sorting can also be activated by clicking at the top of a column name.</span></span>  
  
 <span data-ttu-id="f8728-118">若要存取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式清單檢視的篩選選項，請在 [公用程式總管] 瀏覽窗格中以滑鼠右鍵按一下 [部署的資料層應用程式] 節點，並選取 [篩選]。</span><span class="sxs-lookup"><span data-stu-id="f8728-118">To access filter options for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility list view, right-click on the **Deployed Data-tier applications** node in the Utility Explorer navigation pane, and select **Filter**.</span></span> <span data-ttu-id="f8728-119">當實作篩選設定之後，[公用程式總管] 中的 [部署的資料層應用程式] 節點會標示 [部署的資料層應用程式 (已篩選)]。</span><span class="sxs-lookup"><span data-stu-id="f8728-119">After filter settings have been implemented, the **Deployed Data-tier Applications** node in Utility Explorer will be labeled **Deployed Data-tier Applications (filtered)**.</span></span> <span data-ttu-id="f8728-120">如需詳細資訊，請參閱[篩選設定 &#40;物件總管與公用程式總管&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="f8728-120">For more information, see [Filter Settings &#40;Object Explorer and Utility Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).</span></span>  
  
 <span data-ttu-id="f8728-121">根據預設，下列資料行會顯示有關每一個資料層應用程式的健全狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="f8728-121">By default, the following columns display health state information about each data-tier application.</span></span>  
  
-   <span data-ttu-id="f8728-122">名稱 - 資料層應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="f8728-122">Name - the data-tier application name.</span></span>  
  
-   <span data-ttu-id="f8728-123">應用程式 CPU - 顯示此資料層應用程式之處理器使用量的健全狀態。</span><span class="sxs-lookup"><span data-stu-id="f8728-123">Application CPU - Displays the health state of processor utilization for this data-tier application.</span></span> <span data-ttu-id="f8728-124">這個參數的健全狀態是根據針對資料層應用程式設定的 CPU 使用量原則及動態資源評估原則的組態設定所決定。</span><span class="sxs-lookup"><span data-stu-id="f8728-124">The health state for this parameter is determined according to CPU utilization policy set for the data-tier application and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="f8728-125">如需詳細資訊，請參閱[降低 CPU 使用量原則的雜訊 &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="f8728-125">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="f8728-126">若要檢視這個資料層應用程式的處理器使用量歷程記錄，或是檢視或變更原則限制，請按一下 [CPU 使用量] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8728-126">To view the processor utilization history for this data-tier application, or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="f8728-127">電腦 CPU - 顯示電腦處理器使用量的健全狀態。</span><span class="sxs-lookup"><span data-stu-id="f8728-127">Computer CPU - Displays the health state of computer processor utilization.</span></span> <span data-ttu-id="f8728-128">這個參數的健全狀態是根據針對電腦設定的 CPU 使用量原則及動態資源評估原則的組態設定所決定。</span><span class="sxs-lookup"><span data-stu-id="f8728-128">The health state for this parameter is determined according to CPU utilization policy set for the computer and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="f8728-129">如需詳細資訊，請參閱[降低 CPU 使用量原則的雜訊 &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="f8728-129">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="f8728-130">若要檢視這個資料層應用程式的處理器使用量歷程記錄，或是檢視或變更原則限制，請按一下 [CPU 使用量] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8728-130">To view the processor utilization history for this data-tier application, or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="f8728-131">檔案空間 - 針對每一個資料層應用程式顯示檔案空間使用量的健全狀態摘要。</span><span class="sxs-lookup"><span data-stu-id="f8728-131">File Space - Displays a summary of health states of file space utilization for each data-tier application.</span></span>  
  
    -   <span data-ttu-id="f8728-132">綠色核取符號 - 所有檔案群組和記錄檔群組的健全狀態既不是使用量過高，也不是使用量過低。</span><span class="sxs-lookup"><span data-stu-id="f8728-132">Green check - The health states for all filegroups and the log file group are neither overutilized or underutilized.</span></span>  
  
    -   <span data-ttu-id="f8728-133">綠色向下箭頭 - 至少一個檔案群組或記錄檔群組的健全狀態表示使用量過低，而沒有任何檔案群組或記錄檔群組的使用量過高。</span><span class="sxs-lookup"><span data-stu-id="f8728-133">Green down arrow - The health state for at least one filegroup or log file group is underutilized, and no filegroup or log file group is overutilized.</span></span>  
  
    -   <span data-ttu-id="f8728-134">紅色向上箭頭 - 至少一個檔案群組或記錄檔群組的健全狀態指出使用量過高。</span><span class="sxs-lookup"><span data-stu-id="f8728-134">Red up arrow - The health state for at least one filegroup or the log file group is overutilized.</span></span> <span data-ttu-id="f8728-135">請注意，如果資料庫處於「緊急」狀態，則健康狀態會顯示記錄檔空間過度使用。</span><span class="sxs-lookup"><span data-stu-id="f8728-135">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
     <span data-ttu-id="f8728-136">若要檢視或變更檔案空間原則限制，請按一下 [儲存使用量] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8728-136">To view or change the file space policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="f8728-137">磁碟區空間 - 針對包含了屬於選定資料層應用程式之資料庫的所有磁碟區來顯示磁碟區空間使用量的健全狀態摘要。</span><span class="sxs-lookup"><span data-stu-id="f8728-137">Volume Space - Displays a summary of the health states of volume space utilization for all volumes that contain databases belonging to the selected data-tier application.</span></span> <span data-ttu-id="f8728-138">如果任何磁碟區的健全狀態指出使用量過高，則磁碟區空間健全狀態將會在清單檢視中報告為使用量過高。</span><span class="sxs-lookup"><span data-stu-id="f8728-138">If the health state of any volume is overutilized, then the volume space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="f8728-139">如果任何磁碟區的健全狀態指出使用量過低，而且沒有任何磁碟區使用量過高，則磁碟區空間健全狀態將會在清單檢視中報告為使用量過低。</span><span class="sxs-lookup"><span data-stu-id="f8728-139">If the health state of any volume is underutilized, and no volume is overutilized, then the volume space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="f8728-140">否則，磁碟區空間健全狀態將會在清單檢視中報告為使用良好。</span><span class="sxs-lookup"><span data-stu-id="f8728-140">Otherwise, the volume space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="f8728-141">若要檢視或變更原則限制，請按一下 [儲存使用量] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8728-141">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="f8728-142">原則類型 - 指出「全域」預設原則還是「覆寫」自訂原則對於資料層應用程式有效。</span><span class="sxs-lookup"><span data-stu-id="f8728-142">Policy Type - Indicates whether "Global" default policies or "Override" custom policies are in effect for the data-tier application.</span></span>  
  
-   <span data-ttu-id="f8728-143">執行個體名稱 - 顯示主控資料層應用程式的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="f8728-143">Instance Name - Displays the name of the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that hosts the data-tier application.</span></span>  
  
 <span data-ttu-id="f8728-144">可以使用清單檢視中資料行標題區域內的右鍵功能表來顯示的其他資料行：</span><span class="sxs-lookup"><span data-stu-id="f8728-144">Other columns that can be displayed using the right-click menu in the column heading area of the list view:</span></span>  
  
-   <span data-ttu-id="f8728-145">資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="f8728-145">Database Name</span></span>  
  
-   <span data-ttu-id="f8728-146">部署日期</span><span class="sxs-lookup"><span data-stu-id="f8728-146">Deployed Date</span></span>  
  
-   <span data-ttu-id="f8728-147">可信任：(True 或 False)</span><span class="sxs-lookup"><span data-stu-id="f8728-147">Trustworthy: (True or False)</span></span>  
  
-   <span data-ttu-id="f8728-148">定序</span><span class="sxs-lookup"><span data-stu-id="f8728-148">Collation</span></span>  
  
-   <span data-ttu-id="f8728-149">相容性層級：(例如 Version100)</span><span class="sxs-lookup"><span data-stu-id="f8728-149">Compatibility Level: (for example, Version100)</span></span>  
  
-   <span data-ttu-id="f8728-150">加密已啟用：(True 或 False)</span><span class="sxs-lookup"><span data-stu-id="f8728-150">Encryption Enabled: (True or False)</span></span>  
  
-   <span data-ttu-id="f8728-151">復原模式：(簡單、完整或大量記錄)</span><span class="sxs-lookup"><span data-stu-id="f8728-151">Recovery Model: (Simple, Full, or Bulk-Logged)</span></span>  
  
-   <span data-ttu-id="f8728-152">上次報告時間：此資料行會使用 datetime 資料類型來顯示 UCP 本機日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f8728-152">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="f8728-153">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主題。</span><span class="sxs-lookup"><span data-stu-id="f8728-153">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="f8728-154">當您使用公用程式物件模型時，請注意 SSMS 會使用 datetimeoffset 資料類型。</span><span class="sxs-lookup"><span data-stu-id="f8728-154">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="f8728-155">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主題。</span><span class="sxs-lookup"><span data-stu-id="f8728-155">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="f8728-156">CPU 使用量索引標籤</span><span class="sxs-lookup"><span data-stu-id="f8728-156">CPU Utilization tab</span></span>  
 <span data-ttu-id="f8728-157">[CPU 使用量] 索引標籤會針對資料層應用程式和電腦的 CPU 使用量顯示歷程記錄資料的並排圖形。</span><span class="sxs-lookup"><span data-stu-id="f8728-157">The CPU utilization tab shows side-by-side graphs of historical data for data-tier application and computer CPU utilization.</span></span>  
  
 <span data-ttu-id="f8728-158">此圖形會針對顯示區域右邊的選項按鈕中指定的間隔，顯示處理器使用量歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f8728-158">The graph displays the processor utilization history for the interval specified in the radio buttons on the right side of the display area.</span></span> <span data-ttu-id="f8728-159">若要變更顯示間隔並重新整理資料集，請從清單中選取選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8728-159">To change the display interval and refresh the data set, select a radio button from the list.</span></span>  
  
 <span data-ttu-id="f8728-160">間隔選項如下：</span><span class="sxs-lookup"><span data-stu-id="f8728-160">Interval options are as follows:</span></span>  
  
-   <span data-ttu-id="f8728-161">1 天，每隔 15 分鐘顯示。</span><span class="sxs-lookup"><span data-stu-id="f8728-161">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="f8728-162">1 週，每隔 1 天顯示。</span><span class="sxs-lookup"><span data-stu-id="f8728-162">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="f8728-163">1 個月，每隔 1 週顯示。</span><span class="sxs-lookup"><span data-stu-id="f8728-163">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="f8728-164">1 年，每隔 1 個月顯示。</span><span class="sxs-lookup"><span data-stu-id="f8728-164">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="f8728-165">儲存使用量索引標籤</span><span class="sxs-lookup"><span data-stu-id="f8728-165">Storage Utilization tab</span></span>  
 <span data-ttu-id="f8728-166">[儲存使用量] 索引標籤的樹狀檢視會針對屬於清單檢視中選取之資料層應用程式的資料庫檔案和記錄檔來顯示儲存使用量詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f8728-166">The Storage Utilization tab has a tree view that displays storage utilization details for database files and log files that belong to the data-tier application selected in the list view.</span></span> <span data-ttu-id="f8728-167">請注意，時間資料會使用 datetime 資料類型來顯示 UCP 本機日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f8728-167">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="f8728-168">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主題。</span><span class="sxs-lookup"><span data-stu-id="f8728-168">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="f8728-169">當您使用公用程式物件模型時，請注意 SSMS 會使用 datetimeoffset 資料類型。</span><span class="sxs-lookup"><span data-stu-id="f8728-169">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="f8728-170">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主題。</span><span class="sxs-lookup"><span data-stu-id="f8728-170">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="f8728-171">顯示畫面可以依檔案群組或磁碟區來分組。</span><span class="sxs-lookup"><span data-stu-id="f8728-171">Display can be grouped by filegroup or by volume.</span></span> <span data-ttu-id="f8728-172">若要使用檔案群組樹狀檢視，請選取 [檔案群組依據] 選項中的 [檔案群組] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8728-172">To use the filegroup tree view, select the **Filegroup** radio button in the **Group files by:** selection.</span></span>  
  
 <span data-ttu-id="f8728-173">儲存使用量歷程記錄圖形中顯示的資料會因為樹狀檢視中選取的節點而有所不同：</span><span class="sxs-lookup"><span data-stu-id="f8728-173">Data displayed in the graph of storage utilization history changes depending on the node selected in the tree view:</span></span>  
  
-   <span data-ttu-id="f8728-174">選取檔案群組節點，以顯示屬於選定檔案群組之所有資料檔案所使用的檔案空間圖形。</span><span class="sxs-lookup"><span data-stu-id="f8728-174">Select the file group node to display a graph of file space used by all data files that belong to the selected file group.</span></span>  
  
-   <span data-ttu-id="f8728-175">選取記錄檔節點，以顯示屬於選定資料庫之所有記錄檔所使用的檔案空間圖形。</span><span class="sxs-lookup"><span data-stu-id="f8728-175">Select the log file node to display a graph of file space used by all log files that belong to the selected database.</span></span>  
  
-   <span data-ttu-id="f8728-176">選取資料庫節點來顯示一個圖形，此圖形會加入屬於選定資料庫之所有資料檔案和記錄檔所使用的檔案空間。</span><span class="sxs-lookup"><span data-stu-id="f8728-176">Select the database node to display a graph that adds file space used by all data files and all log files that belong to the selected database.</span></span>  
  
 <span data-ttu-id="f8728-177">若要檢視個別檔案的儲存使用量狀態，請按一下樹狀檢視中檔案名稱旁邊的加號。</span><span class="sxs-lookup"><span data-stu-id="f8728-177">To view storage utilization status for individual files, click on the plus sign next to a file name in the tree view.</span></span>  
  
 <span data-ttu-id="f8728-178">健全狀態圖示會提供每一個檔案群組相較於原則臨界值的大致狀態：</span><span class="sxs-lookup"><span data-stu-id="f8728-178">Health state icons provide at-a-glance status for each filegroup compared to policy thresholds:</span></span>  
  
-   <span data-ttu-id="f8728-179">綠色核取符號 - 檔案群組中至少有一個資料檔案的檔案空間使用量既不是使用量過高，也不是使用量過低。</span><span class="sxs-lookup"><span data-stu-id="f8728-179">Green check - File space utilization for at least one data file in the filegroup is neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="f8728-180">綠色向下箭頭 - 檔案群組中至少有一個資料檔案的檔案空間使用量過低，而且檔案群組中沒有任何檔案的使用量過高。</span><span class="sxs-lookup"><span data-stu-id="f8728-180">Green down arrow - File space utilization for at least one data file in the filegroup is underutilized, and no files in the filegroup are overutilized.</span></span>  
  
-   <span data-ttu-id="f8728-181">紅色向上箭頭 - 檔案群組中所有資料檔案的檔案空間使用量過高。</span><span class="sxs-lookup"><span data-stu-id="f8728-181">Red up arrow - File space utilization for all data files in the filegroup are overutilized.</span></span> <span data-ttu-id="f8728-182">請注意，如果資料庫處於「緊急」狀態，則健康狀態會顯示記錄檔空間過度使用。</span><span class="sxs-lookup"><span data-stu-id="f8728-182">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
 <span data-ttu-id="f8728-183">若要依磁碟區檢視檔案，請選取 [檔案群組依據] 選項中的 [磁碟區] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8728-183">To view files by volume, select the **Volume** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="f8728-184">儲存使用量歷程記錄的圖形會顯示存放磁碟區上所有資料檔案和記錄檔所使用的檔案空間。</span><span class="sxs-lookup"><span data-stu-id="f8728-184">The graph of storage utilization history displays file space used by all data files and all log files on the storage volume.</span></span> <span data-ttu-id="f8728-185">針對個別資料庫資料檔案和記錄檔展開此樹狀目錄來檢視詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f8728-185">Expand the tree to view details for individual database data files and log files.</span></span>  
  
 <span data-ttu-id="f8728-186">狀態圖示用來提供每個磁碟區的狀態：</span><span class="sxs-lookup"><span data-stu-id="f8728-186">Status icons are used to provide status for each volume:</span></span>  
  
-   <span data-ttu-id="f8728-187">綠色核取符號 - 資源使用情況良好。</span><span class="sxs-lookup"><span data-stu-id="f8728-187">Green check - Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="f8728-188">綠色向下箭頭 - 資源使用量過低。</span><span class="sxs-lookup"><span data-stu-id="f8728-188">Green down arrow - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="f8728-189">紅色向上箭頭 - 資源使用量過高。</span><span class="sxs-lookup"><span data-stu-id="f8728-189">Red up arrow - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="f8728-190">[儲存使用量] 索引標籤上每一個檔案名稱旁邊的量測計都代表檔案所使用的空間量 (相較於檔案的有效容量)。</span><span class="sxs-lookup"><span data-stu-id="f8728-190">The gauge next to each file name on the Storage Utilization tab represents the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="f8728-191">量測計旁邊所顯示的百分比值為檔案所使用的空間量比率 (相較於檔案的有效容量)。</span><span class="sxs-lookup"><span data-stu-id="f8728-191">The percentage value displayed next to the gauge is the ratio of the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="f8728-192">工具提示所提供的資料是用來計算每一個磁碟區和每一個檔案相較於有效容量的百分比。</span><span class="sxs-lookup"><span data-stu-id="f8728-192">Tool tips provide data used to calculate percentages for each volume and each file compared to effective capacity.</span></span>  
  
 <span data-ttu-id="f8728-193">如果檔案未設定為自動成長，有效容量就是配置給檔案的空間數量。</span><span class="sxs-lookup"><span data-stu-id="f8728-193">If the file is not configured to auto-grow, then the effective capacity is the amount of space allocated to the file.</span></span> <span data-ttu-id="f8728-194">如果檔案設定為自動成長，則有效容量就是目前配置給檔案之空間數量與目前磁碟區上可用空間數量的總和。</span><span class="sxs-lookup"><span data-stu-id="f8728-194">If the file is configured to auto-grow, then the effective capacity is the sum of the amount of space currently allocated to the file and the amount of free space currently available on the volume.</span></span>  
  
 <span data-ttu-id="f8728-195">可以針對資料檔案和記錄檔設定儲存使用量原則。</span><span class="sxs-lookup"><span data-stu-id="f8728-195">Storage utilization policies can be configured for data files and for log files.</span></span> <span data-ttu-id="f8728-196">若要檢視或變更檔案的儲存使用量原則臨界值，請按一下 [儲存使用量] 窗格底部的 [檔案原則] 連結。</span><span class="sxs-lookup"><span data-stu-id="f8728-196">To view or change the storage utilization policy thresholds for files, click on the **File Policy** link at the bottom of the Storage Utilization pane.</span></span> <span data-ttu-id="f8728-197">若要檢視或變更存放磁碟區的儲存使用量原則臨界值，請按一下 [儲存使用量] 窗格底部的 [磁碟區原則] 連結。</span><span class="sxs-lookup"><span data-stu-id="f8728-197">To view or change the storage utilization policy thresholds for a storage volume, click on the **Volume Policy** link at the bottom of the Storage Utilization pane.</span></span>  
  
 <span data-ttu-id="f8728-198">若要覆寫預設原則閾值，請按一下 [覆寫預設原則] 選項按鈕，並指定上限和下限值，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="f8728-198">To override the default policy thresholds, click on the radio button to **Override the default policy**, specify values for the upper and lower limits, then click **OK**.</span></span>  
  
 <span data-ttu-id="f8728-199">如需變更原則違規容錯的詳細資訊，請參閱[降低 CPU 使用量原則的雜訊 &#40;SQL Server 公用程式&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="f8728-199">For more information about changing the tolerance for policy violations, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="f8728-200">屬性詳細資料索引標籤</span><span class="sxs-lookup"><span data-stu-id="f8728-200">Property Details tab</span></span>  
 <span data-ttu-id="f8728-201">針對資料層應用程式列出的屬性詳細資料包括以下類別：</span><span class="sxs-lookup"><span data-stu-id="f8728-201">Property details listed for data-tier applications include the following categories:</span></span>  
  
-   <span data-ttu-id="f8728-202">資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="f8728-202">Database Name</span></span>  
  
-   <span data-ttu-id="f8728-203">部署日期</span><span class="sxs-lookup"><span data-stu-id="f8728-203">Deployed Date</span></span>  
  
-   <span data-ttu-id="f8728-204">可信任：(True 或 False)</span><span class="sxs-lookup"><span data-stu-id="f8728-204">Trustworthy: (True or False)</span></span>  
  
-   <span data-ttu-id="f8728-205">定序</span><span class="sxs-lookup"><span data-stu-id="f8728-205">Collation</span></span>  
  
-   <span data-ttu-id="f8728-206">相容性層級：(例如 Version100)</span><span class="sxs-lookup"><span data-stu-id="f8728-206">Compatibility Level: (for example, Version100)</span></span>  
  
-   <span data-ttu-id="f8728-207">加密已啟用：(True 或 False)</span><span class="sxs-lookup"><span data-stu-id="f8728-207">Encryption Enabled: (True or False)</span></span>  
  
-   <span data-ttu-id="f8728-208">復原模式：(簡單、完整或大量記錄)</span><span class="sxs-lookup"><span data-stu-id="f8728-208">Recovery Model: (Simple, Full, or Bulk-Logged)</span></span>  
  
-   <span data-ttu-id="f8728-209">上次報告時間：此資料行會使用 datetime 資料類型來顯示 UCP 本機日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f8728-209">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="f8728-210">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主題。</span><span class="sxs-lookup"><span data-stu-id="f8728-210">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="f8728-211">當您使用公用程式物件模型時，請注意 SSMS 會使用 datetimeoffset 資料類型。</span><span class="sxs-lookup"><span data-stu-id="f8728-211">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="f8728-212">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主題。</span><span class="sxs-lookup"><span data-stu-id="f8728-212">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8728-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8728-213">See Also</span></span>  
 <span data-ttu-id="f8728-214">[受管理的執行個體詳細資料 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f8728-214">[Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="f8728-215">[公用程式儀表板 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f8728-215">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="f8728-216">[監視 SQL Server 公用程式中的 SQL Server 執行個體](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f8728-216">[Monitor Instances of SQL Server in the SQL Server Utility](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="f8728-217">SQL Server 公用程式的功能與工作</span><span class="sxs-lookup"><span data-stu-id="f8728-217">SQL Server Utility Features and Tasks</span></span>](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
