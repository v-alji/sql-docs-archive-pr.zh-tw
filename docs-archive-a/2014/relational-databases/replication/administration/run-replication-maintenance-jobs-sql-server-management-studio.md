---
title: 執行複寫維護作業 (SQL Server Management Studio) | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9dc27c65e96a9f956ffa6d3edf9c72ed52f721a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705081"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a><span data-ttu-id="1b1b8-102">執行複寫維護作業 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1b1b8-102">Run Replication Maintenance Jobs (SQL Server Management Studio)</span></span>
  <span data-ttu-id="1b1b8-103">複寫會使用下列維護作業：</span><span class="sxs-lookup"><span data-stu-id="1b1b8-103">Replication uses the following maintenance jobs:</span></span>  
  
-   <span data-ttu-id="1b1b8-104">**重新初始化具有資料驗證失敗的訂閱**</span><span class="sxs-lookup"><span data-stu-id="1b1b8-104">**Reinitialize subscriptions having data validation failures**</span></span>
-   <span data-ttu-id="1b1b8-105">**代理程式記錄清除：散發**</span><span class="sxs-lookup"><span data-stu-id="1b1b8-105">**Agent history clean up: distribution**</span></span>
-   <span data-ttu-id="1b1b8-106">**散發的複寫監視重新整理器。**</span><span class="sxs-lookup"><span data-stu-id="1b1b8-106">**Replication monitoring refresher for distribution.**</span></span>
-   <span data-ttu-id="1b1b8-107">**檢查複寫代理程式**</span><span class="sxs-lookup"><span data-stu-id="1b1b8-107">**Replication agents checkup**</span></span>
-   <span data-ttu-id="1b1b8-108">**散發清除：散發**</span><span class="sxs-lookup"><span data-stu-id="1b1b8-108">**Distribution clean up: distribution**</span></span>
-   <span data-ttu-id="1b1b8-109">**清除已過期的訂閱**</span><span class="sxs-lookup"><span data-stu-id="1b1b8-109">**Expired subscription clean up**</span></span>  
  
 <span data-ttu-id="1b1b8-110">從 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 的 [作業] 資料夾，以及從複寫監視器的 [代理程式] 索引標籤啟動和停止這些作業。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-110">Start and stop these jobs from the **Jobs** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor.</span></span> <span data-ttu-id="1b1b8-111">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-111">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span> <span data-ttu-id="1b1b8-112">在 [作業屬性 - \<Job>] 對話方塊中檢視及修改各作業的屬性，此對話方塊位於相同的資料夾和索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-112">View and modify properties for each job in the **Job Properties - \<Job>** dialog box, which is available from the same folder and tab.</span></span>  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a><span data-ttu-id="1b1b8-113">在 Management Studio 中啟動或停止複寫維護作業</span><span class="sxs-lookup"><span data-stu-id="1b1b8-113">To start or stop a replication maintenance job in Management Studio</span></span>  
  
1.  <span data-ttu-id="1b1b8-114">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的散發者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-114">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="1b1b8-115">展開 **[SQL Server Agent]** 資料夾，然後展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-115">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="1b1b8-116">以滑鼠右鍵按一下作業，然後按一下 **[啟動作業]** 或 **[停止作業]** 。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-116">Right-click a job, and then click **Start Job** or **Stop Job**.</span></span>  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a><span data-ttu-id="1b1b8-117">在複寫監視器中啟動或停止複寫維護作業</span><span class="sxs-lookup"><span data-stu-id="1b1b8-117">To start or stop a replication maintenance job in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="1b1b8-118">在複寫監視器中展開發行者群組，然後選取發行者。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-118">Expand a Publisher group in Replication Monitor, and then select a Publisher.</span></span>  
  
2.  <span data-ttu-id="1b1b8-119">按一下 **[代理程式]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-119">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="1b1b8-120">以滑鼠右鍵按一下方格中的作業，然後按一下 **[啟動作業]** 或 **[停止作業]** 。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-120">Right-click a job in the grid, and then click **Start Job** or **Stop Job**.</span></span>  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a><span data-ttu-id="1b1b8-121">在 Management Studio 中檢視及修改複寫維護作業的屬性</span><span class="sxs-lookup"><span data-stu-id="1b1b8-121">To view and modify properties for a replication maintenance job in Management Studio</span></span>  
  
1.  <span data-ttu-id="1b1b8-122">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的散發者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-122">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="1b1b8-123">展開 **[SQL Server Agent]** 資料夾，然後展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-123">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="1b1b8-124">以滑鼠右鍵按一下作業，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-124">Right-click a job, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1b1b8-125">在 [作業屬性 - \<Job>] 對話方塊中，視需要修改任何屬性，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-125">In the **Job Properties - \<Job>** dialog box, modify any properties if necessary, and then click **OK**.</span></span>  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a><span data-ttu-id="1b1b8-126">在複寫監視器中檢視及修改複寫維護作業的屬性</span><span class="sxs-lookup"><span data-stu-id="1b1b8-126">To view and modify properties for a replication maintenance job in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="1b1b8-127">在複寫監視器中展開發行者群組，然後選取發行者。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-127">Expand a Publisher group in Replication Monitor, and then select a Publisher.</span></span>  
  
2.  <span data-ttu-id="1b1b8-128">按一下 **[代理程式]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-128">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="1b1b8-129">以滑鼠右鍵按一下方格中的作業，再按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-129">Right-click a job in the grid, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1b1b8-130">在 [作業屬性 - \<Job>] 對話方塊中，視需要修改任何屬性，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1b1b8-130">In the **Job Properties - \<Job>** dialog box, modify any properties if necessary, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1b8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b1b8-131">See Also</span></span>  
 <span data-ttu-id="1b1b8-132">[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1b1b8-132">[Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="1b1b8-133">[使用複寫監視器來檢視資訊及執行工作](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="1b1b8-133">[View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="1b1b8-134">複寫代理程式管理</span><span class="sxs-lookup"><span data-stu-id="1b1b8-134">Replication Agent Administration</span></span>](../agents/replication-agent-administration.md)  
  
  
