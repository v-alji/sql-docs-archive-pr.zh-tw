---
title: 監視資料層應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- monitoring [SQL Server], data-tier applications
- monitoring server performance [SQL Server], DACs
- data-tier application [SQL Server], monitor
ms.assetid: d2765828-2385-4019-aef2-1de3ab7d1b26
author: stevestein
ms.author: sstein
ms.openlocfilehash: 100ad85847c131b71ea6eff93346f283f70aaec0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606887"
---
# <a name="monitor-data-tier-applications"></a><span data-ttu-id="6ebc1-102">監視資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="6ebc1-102">Monitor Data-tier Applications</span></span>
  <span data-ttu-id="6ebc1-103">您可以從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) 中的 [公用程式總管] 與 [物件總管] 以及系統檢視表和資料表中監視資料層應用程式 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-103">A data-tier application (DAC) can be monitored from the **Utility Explorer** and **Object Explorer** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS), along with system views and tables.</span></span> <span data-ttu-id="6ebc1-104">此外，包含在 DAC 中之資料庫內的所有物件都可以使用標準資料庫與 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 監視技術進行監視。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-104">In addition, all objects in the database contained in the DAC can be monitored using standard database and [!INCLUDE[ssDE](../../includes/ssde-md.md)] monitoring techniques.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="6ebc1-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="6ebc1-105">Before You Begin</span></span>  
 <span data-ttu-id="6ebc1-106">若您將 DAC 部署至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的受管理執行個體，下次從執行個體將公用程式收集組傳送到公用程式控制點時，部署 DAC 的相關資訊就會合併至 SQL Server 公用程式。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-106">If you deploy a DAC to a managed instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], information about the deployed DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="6ebc1-107">然後，您可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的 [公用程式總管] 來檢視 DAC 基本健全狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-107">You can then view basic health information about the DAC by using the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="6ebc1-108">SSMS 的 **[物件總管]** 會顯示部署至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體之每個 DAC 的基本組態資訊，而不論是否在 SQL Server 公用程式中管理執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-108">The SSMS **Object Explorer** displays basic configuration information about each DAC deployed to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], regardless of whether the instance is managed in the SQL Server Utility.</span></span> <span data-ttu-id="6ebc1-109">而且，可以使用監視任何資料庫的相同程序，來監視與部署 DAC 相關聯的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-109">Also, the database associated with a deployed DAC can be monitored using the same procedures for monitoring any database.</span></span>  
  
## <a name="using-the-sql-server-utility"></a><span data-ttu-id="6ebc1-110">使用 SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="6ebc1-110">Using the SQL Server Utility</span></span>  
 <span data-ttu-id="6ebc1-111"> 公用程式總管[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]\ \*\*\** 中的 [部署的資料層應用程式\]\*\*\** 詳細資料頁面會顯示一個儀表板，這個儀表板會報告已部署至 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 之受管理執行個體的所有 DAC 資源使用情況。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-111">The **Deployed Data-tier Applications** detail page in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** displays a dashboard that reports the resource utilization of all DACs that have been deployed to managed instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="6ebc1-112">詳細資料頁面的上方窗格會列出每個已部署的 DAC 以及視覺指標，顯示其 CPU 的使用量與檔案資源是否超出針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式所定義的原則之外。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-112">The top pane of the details page lists each deployed DAC with visual indicators showing whether their utilization of CPU and file resources are outside the policies defined for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="6ebc1-113">如果您選取清單檢視中的任何 DAC，在頁面下方窗格的索引標籤中會顯示其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-113">If you select any DAC in the list view, further details are displayed in tabs in the bottom pane of the page.</span></span> <span data-ttu-id="6ebc1-114">如需詳細資料頁面上所呈現之資訊的詳細資訊，請參閱[部署的資料層應用程式詳細資料 &#40;SQL Server 公用程式&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-114">For more information about the information presented on the details page, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="6ebc1-115">使用 [部署的資料層應用程式] 詳細資料頁面快速識別使用不足或其硬體資源負荷過重的 DAC 之後，您可以做出處理所有問題的計畫。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-115">After using the **Deployed Data-tier Applications** detail page to quickly identify any DACs that are either under-utilizing or stressing their hardware resource, you can make plans to address any problems.</span></span> <span data-ttu-id="6ebc1-116">未充分使用其目前硬體資源的多個 DAC 可以合併到單一伺服器，釋出部分伺服器做為其他用途使用。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-116">Multiple DACs that are not fully utilizing their current hardware resources could be consolidated to a single server, freeing some of the servers for other uses.</span></span> <span data-ttu-id="6ebc1-117">如果 DAC 在目前伺服器上的資源負荷過重，可以將 DAC 移到更大的伺服器，或者將額外的資源加入至目前的伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-117">If a DAC is stressing the resources on its current server, the DAC can be moved to a larger server, or additional resources can be added to the current server.</span></span>  
  
 <span data-ttu-id="6ebc1-118">資源使用量的上下限是由 **[公用程式管理]** 詳細資料頁面中所定義的應用程式監視原則定義的。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-118">The minimum and maximum limits for resource usage are defined by application monitoring policies defined in the **Utility Administration** details page.</span></span> <span data-ttu-id="6ebc1-119">資料庫管理員可以量身訂作這些原則，以符合其組織所設立的限制。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-119">Database administrators can tailor the policies to match the limits established by their organizations.</span></span> <span data-ttu-id="6ebc1-120">例如，某家公司可能會設定 75% 做為 DAC 的 CPU 使用量上限，而另一家公司則可能將上限設定為 80%。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-120">For example, one company might set 75% as the maximum CPU utilization for a DAC, while another company might set the maximum at 80%.</span></span> <span data-ttu-id="6ebc1-121">如需有關設定應用程式監視原則的詳細資訊，請參閱[公用程式管理 &#40;SQL Server 公用程式&#41;](../../database-engine/utility-administration-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-121">For more information about setting application monitoring policies, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="6ebc1-122">若要檢視 [部署的資料層應用程式] 詳細資料頁面：</span><span class="sxs-lookup"><span data-stu-id="6ebc1-122">To view the **Deployed Data-tier Applications** detail page:</span></span>  
  
1.  <span data-ttu-id="6ebc1-123">選取 [檢視/公用程式總管] 功能表。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-123">Select the **View/Utility Explorer** menu.</span></span>  
  
2.  <span data-ttu-id="6ebc1-124">將 [公用程式總管] 連接至公用程式控制點 (UCP)。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-124">Connect the **Utility Explorer** to the utility control point (UCP).</span></span>  
  
3.  <span data-ttu-id="6ebc1-125">選取 [檢視/公用程式總管詳細資料] 功能表。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-125">Select the **View/Utility Explorer Details** menu.</span></span>  
  
4.  <span data-ttu-id="6ebc1-126">選取 [公用程式總管] 中的 [部署的資料層應用程式] 節點。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-126">Select the **Deployed Data-tier Applications** node in the **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="6ebc1-127">[部署的資料層應用程式] 詳細資料頁面中的資訊來自公用程式管理資料倉儲中的資料，此資料倉儲預設每 15 分鐘收集資料一次。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-127">The information in the **Deployed Data-tier Applications** detail page comes from the data in the utility management data warehouse, which defaults to collecting the data every 15 minutes.</span></span> <span data-ttu-id="6ebc1-128">其間隔可以使用 **[公用程式管理]** 詳細資料頁面自訂。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-128">The interval can also be tailored using the **Utility Administration** details page.</span></span>  
  
## <a name="using-object-explorer"></a><span data-ttu-id="6ebc1-129">使用物件總管</span><span class="sxs-lookup"><span data-stu-id="6ebc1-129">Using Object Explorer</span></span>  
 <span data-ttu-id="6ebc1-130">SSMS 的 **[物件總管]** 會顯示有關部署至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體之每個 DAC 的基本組態資訊。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-130">The SSMS **Object Explorer** displays basic configuration information about each DAC deployed to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="6ebc1-131">這同時包括已經在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式中註冊的受管理的執行個體，以及無法在 [公用程式總管]\*\*\*\* 中檢視的獨立執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-131">This includes both managed instances that have been enrolled in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, and stand-alone instances that cannot be viewed in the **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="6ebc1-132">若要檢視部署至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體之 DAC 的詳細資料：</span><span class="sxs-lookup"><span data-stu-id="6ebc1-132">To view the details of a DAC deployed to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]:</span></span>  
  
1.  <span data-ttu-id="6ebc1-133">選取 [檢視/物件總管] 功能表。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-133">Select the **View/Object Explorer** menu.</span></span>  
  
2.  <span data-ttu-id="6ebc1-134">從 [物件總管] 窗格連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-134">Connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]from the Object Explorer pane.</span></span>  
  
3.  <span data-ttu-id="6ebc1-135">選取 [檢視/物件總管詳細資料] 功能表。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-135">Select the **View/Object Explorer Details** menu.</span></span>  
  
4.  <span data-ttu-id="6ebc1-136">在 [物件總管] 中，選取對應至執行個體的伺服器節點，然後導覽至 [管理\資料層應用程式] 節點。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-136">Select the server node in **Object Explorer** that maps to the instance, and then navigate to the **Management\Data-tier Applications** node.</span></span>  
  
5.  <span data-ttu-id="6ebc1-137">在詳細資料頁面上方窗格中的清單檢視會列出部署至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的每個 DAC。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-137">The list view in the top pane of the details page lists each DAC deployed to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="6ebc1-138">選取 DAC 以便在頁面底部的詳細資料窗格中顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-138">Select a DAC to display the information in the detail pane at the bottom of the page.</span></span>  
  
 <span data-ttu-id="6ebc1-139">[資料層應用程式] 節點的滑鼠右鍵功能表也會用來部署新的 DAC 或刪除現有的 DAC。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-139">The right-click menu of the **Data-tier Applications** node is also used to deploy a new DAC or delete an existing DAC.</span></span>  
  
## <a name="using-the-dac-system-views-and-tables"></a><span data-ttu-id="6ebc1-140">使用 DAC 系統檢視表與資料表</span><span class="sxs-lookup"><span data-stu-id="6ebc1-140">Using the DAC System Views and Tables</span></span>  
 <span data-ttu-id="6ebc1-141">msdb.dbo.sysdac_history_internal 系統資料表會記錄針對 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體執行的所有 DAC 管理動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-141">The msdb.dbo.sysdac_history_internal system table records the success or failure of all DAC management actions performed on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="6ebc1-142">資料表會記錄每個動作發生的時間，以及起始動作的登入。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-142">The table records the time each action occurred, and which login initiated the action.</span></span> <span data-ttu-id="6ebc1-143">如需詳細資訊，請參閱 [sysdac_history_internal &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/data-tier-application-tables-sysdac-history-internal)。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-143">For more information, see [sysdac_history_internal &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/data-tier-application-tables-sysdac-history-internal).</span></span>  
  
 <span data-ttu-id="6ebc1-144">DAC 系統檢視表會報告基本目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-144">The DAC system views report basic catalog information.</span></span> <span data-ttu-id="6ebc1-145">如需詳細資訊，請參閱[資料層應用程式檢視表 &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances)。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-145">For more information, see [Data-tier Application Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances).</span></span>  
  
## <a name="monitoring-dac-databases"></a><span data-ttu-id="6ebc1-146">監視 DAC 資料庫</span><span class="sxs-lookup"><span data-stu-id="6ebc1-146">Monitoring DAC Databases</span></span>  
 <span data-ttu-id="6ebc1-147">成功部署 DAC 之後，包含在 DAC 中的資料庫會與其他任何資料庫的運作方式相同。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-147">After a DAC has been successfully deployed, the database contained in the DAC operates the same as any other database.</span></span> <span data-ttu-id="6ebc1-148">使用標準 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 技術與工具來監視資料庫的效能、記錄、事件與資源使用情況。</span><span class="sxs-lookup"><span data-stu-id="6ebc1-148">Use standard [!INCLUDE[ssDE](../../includes/ssde-md.md)] techniques and tools for monitoring the performance, log, events, and resource utilization of the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebc1-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ebc1-149">See Also</span></span>  
 <span data-ttu-id="6ebc1-150">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="6ebc1-150">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="6ebc1-151">部署資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="6ebc1-151">Deploy a Data-tier Application</span></span>](deploy-a-data-tier-application.md)  
  
  
