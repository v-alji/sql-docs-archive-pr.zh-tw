---
title: 公用程式儀表板 (SQL Server 公用程式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 999eb741-4a60-43f6-ab37-2df7dce845c1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1e6f59eca0aaaee0d0fc79f267a781b650fb3d58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700165"
---
# <a name="utility-dashboard-sql-server-utility"></a><span data-ttu-id="1eb6f-102">公用程式儀表板 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="1eb6f-102">Utility Dashboard (SQL Server Utility)</span></span>
  <span data-ttu-id="1eb6f-103">若要查看 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式儀表板中的資料，請在公用程式總管樹狀目錄中，選取最上方的節點，也就是標示為 "Utility<UCP_Name>\\(ComputerName\UCP)" 的節點。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-103">To see data in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility dashboard, select the top node in the Utility Explorer tree - labeled "Utility<UCP_Name>\\(ComputerName\UCP)."</span></span> <span data-ttu-id="1eb6f-104">此儀表板包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式內所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Managed 執行個體及所有資料層應用程式中的摘要和詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-104">The dashboard includes summary and detail data from all managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and all data-tier applications in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="1eb6f-105">若要重新整理儀表板中的資料，請以滑鼠右鍵按一下公用程式總管樹狀目錄中的最上方節點，然後選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-105">To refresh data in the dashboard, right-click the top node in the Utility Explorer tree, and select **Refresh**.</span></span>  
  
 <span data-ttu-id="1eb6f-106">如需如何建立公用程式控制點的詳細資訊，請參閱 [建立 SQL Server 公用程式控制點 &#40;SQL Server 公用程式&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-106">For more information about how to create a utility control point, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span> <span data-ttu-id="1eb6f-107">如需如何將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體加入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式的詳細資訊，請參閱 [註冊 SQL Server 的執行個體 &#40;SQL Server 公用程式&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-107">For more information about how to add an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="1eb6f-108">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="1eb6f-108">UI element list</span></span>  
 <span data-ttu-id="1eb6f-109">Managed 執行個體健全狀況</span><span class="sxs-lookup"><span data-stu-id="1eb6f-109">Managed Instance Health</span></span>  
 <span data-ttu-id="1eb6f-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Managed 執行個體的健全狀態會顯示在 [公用程式總管] 內容窗格的左邊。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-110">Health status for managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is displayed on the left side of the Utility Explorer content pane.</span></span>  
  
 <span data-ttu-id="1eb6f-111">Managed 執行個體健全狀況的參數如下：</span><span class="sxs-lookup"><span data-stu-id="1eb6f-111">Managed Instance Health parameters are as follows:</span></span>  
  
-   <span data-ttu-id="1eb6f-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體的 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-112">CPU utilization for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1eb6f-113">資料庫檔案使用量。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-113">Database file utilization.</span></span>  
  
-   <span data-ttu-id="1eb6f-114">存放磁碟區空間使用量。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-114">Storage volume space utilization.</span></span>  
  
-   <span data-ttu-id="1eb6f-115">電腦的 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-115">CPU utilization for the computer.</span></span>  
  
-   <span data-ttu-id="1eb6f-116">每個參數的狀態可分為三個類別：</span><span class="sxs-lookup"><span data-stu-id="1eb6f-116">Status for each parameter is divided into three categories:</span></span>  
  
-   <span data-ttu-id="1eb6f-117">使用情況良好 - 不違反資源使用量原則的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Managed 執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-117">Well-utilized - Number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] which are not violating resource utilization policies.</span></span>  
  
-   <span data-ttu-id="1eb6f-118">使用量過低 - 違反資源使用量過低原則的 Managed 資源數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-118">Underutilized - Number of managed resources which are violating resource underutilization policies.</span></span>  
  
-   <span data-ttu-id="1eb6f-119">使用量過高 - 違反資源使用量過高原則的 Managed 資源數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-119">Overutilized - Number of managed resources which are violating resource overutilization policies.</span></span>  
  
-   <span data-ttu-id="1eb6f-120">沒有可用的資料 - 沒有資料可供 SQL Server 的 Managed 執行個體使用，因為剛剛註冊 SQL Server 執行個體而且尚未完成第一次的資料收集作業，或是因為 SQL Server 的 Managed 執行個體發生問題，而無法收集資料並將資料上傳到 UCP。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-120">No Data Available - Data is not available for managed instances of SQL Server either because the instance of SQL Server has just been enrolled and the first data collection operation has not completed, or because there is a problem with the managed instance of SQL Server collecting and uploading data to the UCP.</span></span>  
  
 <span data-ttu-id="1eb6f-121">每一個健全狀態參數的詳細狀態會列在滑動指標中。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-121">Detailed status for each health parameter is listed in sliding indicators.</span></span> <span data-ttu-id="1eb6f-122">滑動指標右邊的片段會顯示每一個狀態類別中的 Managed 執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-122">The fraction to the right of the sliding indicators shows how many managed instances are in each status category.</span></span>  
  
 <span data-ttu-id="1eb6f-123">若要建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Managed 執行個體或資料層應用程式的篩選檢視，請按一下 [公用程式儀表板] 中滑動指標旁的使用量類別連結。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-123">To create a filtered view of a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or a data-tier application, click on the link for a utilization category next to its sliding indicator in the Utility dashboard.</span></span> <span data-ttu-id="1eb6f-124">例如，如果您按一下 **[公用程式總管內容]** 窗格中的 **[使用量過高的執行個體 CPU]** ，SSMS 便會建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Managed 執行個體的篩選清單檢視，其中包含根據目前原則設定之使用量過高的 CPU。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-124">For example, if you click on **Overutilized Instance CPU** in the **Utility Explorer Content** pane, SSMS creates a filtered list view of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that have overutilized CPU based on current policy settings.</span></span>  
  
 <span data-ttu-id="1eb6f-125">請注意，當您按一下使用量類別連結時，公用程式總管瀏覽窗格中對應的節點後面會加上 [(已篩選)]，意即 [受管理的執行個體] 會標示為 [受管理的執行個體 (已篩選) ]。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-125">Notice that when you click on a link for a utilization category, the corresponding node in the Utility Explorer navigation pane is appended with **(filtered)** - that is, **Managed Instances** is labeled **Managed Instances (filtered)**.</span></span> <span data-ttu-id="1eb6f-126">若要檢視篩選設定，請以滑鼠右鍵按一下瀏覽窗格中的節點，然後選取 [篩選]，再按一下 [篩選設定]。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-126">To view filter settings, right-click on the node in the navigation pane and select **Filter**, then click on **Filter Settings**.</span></span> <span data-ttu-id="1eb6f-127">若要清除篩選設定，請以滑鼠右鍵按一下瀏覽窗格中的節點，然後選取 [篩選]，再按一下 [移除篩選]。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-127">To clear filter settings, right-click on the node in the navigation pane and select **Filter**, then click on **Remove Filter**.</span></span>  
  
 <span data-ttu-id="1eb6f-128">如需檢視個別 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的健全狀態或是檢視或變更原則組態設定的詳細資訊，請參閱[受管理的執行個體詳細資料 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-128">For more information about viewing health status for individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change policy configuration settings, see [Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="1eb6f-129">公用程式摘要</span><span class="sxs-lookup"><span data-stu-id="1eb6f-129">Utility Summary</span></span>  
 <span data-ttu-id="1eb6f-130">顯示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式所管理之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Managed 執行個體及資料層應用程式的數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-130">Displays the number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the number of data-tier applications managed by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span>  
  
 <span data-ttu-id="1eb6f-131">資料層應用程式健全狀況</span><span class="sxs-lookup"><span data-stu-id="1eb6f-131">Data-tier Application Health</span></span>  
 <span data-ttu-id="1eb6f-132">資料層應用程式的健全狀態會顯示在 [公用程式總管] 內容窗格的右邊。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-132">Health status for data-tier applications is displayed on the right side of the Utility Explorer content pane.</span></span>  
  
 <span data-ttu-id="1eb6f-133">資料層應用程式健全狀況的參數如下：</span><span class="sxs-lookup"><span data-stu-id="1eb6f-133">Data-tier Application Health parameters are as follows:</span></span>  
  
-   <span data-ttu-id="1eb6f-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體的 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-134">CPU utilization for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1eb6f-135">資料庫檔案使用量。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-135">Database file utilization.</span></span>  
  
-   <span data-ttu-id="1eb6f-136">存放磁碟區空間使用量。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-136">Storage volume space utilization.</span></span>  
  
-   <span data-ttu-id="1eb6f-137">電腦的 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-137">CPU utilization for the computer.</span></span>  
  
 <span data-ttu-id="1eb6f-138">每個參數的狀態可分為三個類別：</span><span class="sxs-lookup"><span data-stu-id="1eb6f-138">Status for each parameter is divided into three categories:</span></span>  
  
-   <span data-ttu-id="1eb6f-139">使用情況良好 - 不違反資源使用量原則的資料層應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-139">Well-utilized - Number of data-tier applications which are not violating resource utilization policies.</span></span>  
  
-   <span data-ttu-id="1eb6f-140">使用量過高 - 違反資源使用量過高原則的資料層應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-140">Overutilized - Number of data-tier applications which are violating resource overutilization policies.</span></span>  
  
-   <span data-ttu-id="1eb6f-141">使用量過低 - 違反資源使用量過低原則的資料層應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-141">Underutilized - Number of data-tier applications which are violating resource underutilization policies.</span></span>  
  
-   <span data-ttu-id="1eb6f-142">沒有可用的資料 - 資料層應用程式沒有可用的資料，因為包含資料層應用程式的 SQL Server Managed 執行個體並未報告資料。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-142">No Data Available - Data is not available for data-tier applications because the managed instance of SQL Server that contains the data-tier application is not reporting data.</span></span>  
  
 <span data-ttu-id="1eb6f-143">每一個健全狀態參數的詳細狀態會列在滑動指標中。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-143">Detailed status for each health parameter is listed in sliding indicators.</span></span> <span data-ttu-id="1eb6f-144">滑動指標右邊的片段會顯示每一個狀態類別中的資料層應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-144">The fraction to the right of the sliding indicators shows how many data-tier applications are in each status category.</span></span> <span data-ttu-id="1eb6f-145">如需檢視個別資料層應用程式的健全狀態或是檢視或變更原則組態設定的詳細資訊，請參閱[部署的資料層應用程式詳細資料 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-145">For more information about viewing health status for individual data-tier applications, or to view or change policy configuration settings, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="1eb6f-146">公用程式儲存使用量歷程記錄</span><span class="sxs-lookup"><span data-stu-id="1eb6f-146">Utility Storage Utilization History</span></span>  
 <span data-ttu-id="1eb6f-147">使用量歷程記錄會顯示在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式儀表板底部的時間圖中。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-147">Utilization history is shown in a time graph at the bottom of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility dashboard.</span></span> <span data-ttu-id="1eb6f-148">請注意，時間資料會使用 datetime 資料類型來顯示 UCP 本機日期和時間。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-148">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="1eb6f-149">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主題。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-149">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="1eb6f-150">當您使用公用程式物件模型時，請注意 SSMS 會使用 datetimeoffset 資料類型。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-150">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="1eb6f-151">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主題。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-151">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="1eb6f-152">使用顯示區域左邊的選項按鈕來變更圖形的報表期間。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-152">Use the radio buttons to the left of the display area to change the reporting period for the graph.</span></span>  
  
 <span data-ttu-id="1eb6f-153">報表間隔的選項如下：</span><span class="sxs-lookup"><span data-stu-id="1eb6f-153">Options for the reporting interval are:</span></span>  
  
-   <span data-ttu-id="1eb6f-154">1 天，每隔 15 分鐘顯示。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-154">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="1eb6f-155">1 週，每隔 1 天顯示。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-155">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="1eb6f-156">1 個月，每隔 1 週顯示。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-156">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="1eb6f-157">1 年，每隔 1 個月顯示。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-157">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="1eb6f-158">當您變更報表間隔後，資料會自動重新整理。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-158">After you make a change to the reporting interval, the data refreshes automatically.</span></span>  
  
 <span data-ttu-id="1eb6f-159">公用程式儲存使用量</span><span class="sxs-lookup"><span data-stu-id="1eb6f-159">Utility Storage Utilization</span></span>  
 <span data-ttu-id="1eb6f-160">在儀表板的右下方，儲存使用量圓形圖會顯示包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Managed 執行個體之電腦磁碟區上的使用空間與可用空間的比率。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-160">In the bottom right of the dashboard, the storage utilization pie chart displays the ratio of used space to free space on volumes residing on computers that contain managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1eb6f-161">此顯示畫面的資料每隔 15 分鐘會重新整理一次。</span><span class="sxs-lookup"><span data-stu-id="1eb6f-161">Data for this display are refreshed every 15 minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb6f-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1eb6f-162">See Also</span></span>  
 <span data-ttu-id="1eb6f-163">[使用公用程式總管來管理 SQL Server 公用程式](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="1eb6f-163">[Use Utility Explorer to Manage the SQL Server Utility](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 <span data-ttu-id="1eb6f-164">[註冊 SQL Server &#40;SQL Server 公用程式的實例&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="1eb6f-164">[Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="1eb6f-165">修改資源健康情況原則定義 &#40;SQL Server 公用程式&#41;</span><span class="sxs-lookup"><span data-stu-id="1eb6f-165">Modify a Resource Health Policy Definition &#40;SQL Server Utility&#41;</span></span>](../relational-databases/manage/modify-a-resource-health-policy-definition-sql-server-utility.md)  
  
  
