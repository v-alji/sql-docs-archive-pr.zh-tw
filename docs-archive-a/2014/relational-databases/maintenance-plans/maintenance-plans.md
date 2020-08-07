---
title: 維護計畫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- SQL12.AG.MAINTPLAN.LEGACY.F1
helpviewer_keywords:
- maintenance plans [SQL Server], about database maintenance plans
- maintenance plans [SQL Server], database compatibility level displayed in designer
- maintenance plans [SQL Server]
ms.assetid: 5982ca65-74fe-44e3-aef9-00a65a0db169
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2f614e2cfad78cb1efddc49cc897ca57087fec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584499"
---
# <a name="maintenance-plans"></a><span data-ttu-id="5d74f-102">維護計畫</span><span class="sxs-lookup"><span data-stu-id="5d74f-102">Maintenance Plans</span></span>
  <span data-ttu-id="5d74f-103">維護計畫會建立必要的工作流程，確保資料庫已最佳化、定期備份，而且沒有任何不一致性。</span><span class="sxs-lookup"><span data-stu-id="5d74f-103">Maintenance plans create a workflow of the tasks required to make sure that your database is optimized, regularly backed up, and free of inconsistencies.</span></span> <span data-ttu-id="5d74f-104">「維護計畫精靈」也會建立核心維護計畫，但手動建立計畫能提供更大的彈性。</span><span class="sxs-lookup"><span data-stu-id="5d74f-104">The Maintenance Plan Wizard also creates core maintenance plans, but creating plans manually gives you much more flexibility.</span></span>  
  
## <a name="benefits-of-maintenance-plans"></a><span data-ttu-id="5d74f-105">維護計畫的優點</span><span class="sxs-lookup"><span data-stu-id="5d74f-105">Benefits of Maintenance Plans</span></span>  
 <span data-ttu-id="5d74f-106">在 [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)] 中，維護計畫會建立 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，再由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業執行。</span><span class="sxs-lookup"><span data-stu-id="5d74f-106">In [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)], maintenance plans create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package, which is run by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="5d74f-107">維護計畫可以依排程間隔手動或自動執行。</span><span class="sxs-lookup"><span data-stu-id="5d74f-107">Maintenance plans can be run manually or automatically at scheduled intervals.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="5d74f-108">維護計畫提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="5d74f-108">maintenance plans provide the following features:</span></span>  
  
-   <span data-ttu-id="5d74f-109">使用各種典型的維護工作來建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="5d74f-109">Workflow creation using a variety of typical maintenance tasks.</span></span> <span data-ttu-id="5d74f-110">您也可以建立您自己的自訂 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="5d74f-110">You can also create your own custom [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span>  
  
-   <span data-ttu-id="5d74f-111">概念階層。</span><span class="sxs-lookup"><span data-stu-id="5d74f-111">Conceptual hierarchies.</span></span> <span data-ttu-id="5d74f-112">每項計畫都可以讓您建立或編輯工作流程。</span><span class="sxs-lookup"><span data-stu-id="5d74f-112">Each plan lets you create or edit task workflows.</span></span> <span data-ttu-id="5d74f-113">每項計畫中的工作可以再分為子計畫，然後排定在不同時間執行。</span><span class="sxs-lookup"><span data-stu-id="5d74f-113">Tasks in each plan can be grouped into subplans, which can be scheduled to run at different times.</span></span>  
  
-   <span data-ttu-id="5d74f-114">支援多伺服器計畫，可用於主要伺服器/目標伺服器環境。</span><span class="sxs-lookup"><span data-stu-id="5d74f-114">Support for multiserver plans that can be used in master server/target server environments.</span></span>  
  
-   <span data-ttu-id="5d74f-115">支援記錄計畫記錄到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="5d74f-115">Support for logging plan history to remote servers.</span></span>  
  
-   <span data-ttu-id="5d74f-116">支援 Windows 驗證和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="5d74f-116">Support for Windows Authentication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="maintenace-plan-functionality"></a><span data-ttu-id="5d74f-117">維護計畫功能</span><span class="sxs-lookup"><span data-stu-id="5d74f-117">Maintenace Plan Functionality</span></span>  
 <span data-ttu-id="5d74f-118">您可以建立維護計畫來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="5d74f-118">Maintenance plans can be created to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="5d74f-119">以新的填滿因數重建索引，重新整理資料以及索引頁上的資料。</span><span class="sxs-lookup"><span data-stu-id="5d74f-119">Reorganize the data on the data and index pages by rebuilding indexes with a new fill factor.</span></span> <span data-ttu-id="5d74f-120">使用新的填滿因數重建索引時，可以確保資料庫頁面包含平均分佈的資料量和可用空間。</span><span class="sxs-lookup"><span data-stu-id="5d74f-120">Rebuilding indexes with a new fill factor makes sure that database pages contain an equally distributed amount of data and free space.</span></span> <span data-ttu-id="5d74f-121">也可以在未來快速擴展。</span><span class="sxs-lookup"><span data-stu-id="5d74f-121">It also enables faster growth in the future.</span></span> <span data-ttu-id="5d74f-122">如需詳細資訊，請參閱 [指定索引的填滿因素](../indexes/specify-fill-factor-for-an-index.md)。</span><span class="sxs-lookup"><span data-stu-id="5d74f-122">For more information, see [Specify Fill Factor for an Index](../indexes/specify-fill-factor-for-an-index.md).</span></span>  
  
-   <span data-ttu-id="5d74f-123">藉由移除空的資料庫頁面來壓縮資料檔案。</span><span class="sxs-lookup"><span data-stu-id="5d74f-123">Compress data files by removing empty database pages.</span></span>  
  
-   <span data-ttu-id="5d74f-124">更新索引統計資料，以確保查詢最佳化工具對於資料表中的資料值分佈，擁有最新的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d74f-124">Update index statistics to make sure the query optimizer has current information about the distribution of data values in the tables.</span></span> <span data-ttu-id="5d74f-125">由於查詢最佳化工具對資料庫儲存的資料已掌握詳細資訊，因此可以更準確地判斷存取資料的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="5d74f-125">This enables the query optimizer to make better judgments about the best way to access data, because it has more information about the data stored in the database.</span></span> <span data-ttu-id="5d74f-126">雖然 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會定期自動更新索引統計資料，但此選項可以強制統計資料立即更新。</span><span class="sxs-lookup"><span data-stu-id="5d74f-126">Although index statistics are automatically updated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically, this option can force the statistics to update immediately.</span></span>  
  
-   <span data-ttu-id="5d74f-127">對資料庫內的資料及資料頁執行內部一致性檢查，確保系統或軟體問題未損毀資料。</span><span class="sxs-lookup"><span data-stu-id="5d74f-127">Perform internal consistency checks of the data and data pages within the database to make sure that a system or software problem has not damaged data.</span></span>  
  
-   <span data-ttu-id="5d74f-128">備份資料庫及交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5d74f-128">Back up the database and transaction log files.</span></span> <span data-ttu-id="5d74f-129">資料庫及記錄備份可以保留至特定的時間。</span><span class="sxs-lookup"><span data-stu-id="5d74f-129">Database and log backups can be retained for a specified period.</span></span> <span data-ttu-id="5d74f-130">這樣可讓您建立備份的記錄，當您需要將資料庫還原到比上一次資料庫備份更早之前的時間，即可使用此一記錄。</span><span class="sxs-lookup"><span data-stu-id="5d74f-130">This lets you create a history of backups to be used if you have to restore the database to a time earlier than the last database backup.</span></span> <span data-ttu-id="5d74f-131">您也可以執行差異備份。</span><span class="sxs-lookup"><span data-stu-id="5d74f-131">You can also perform differential backups.</span></span>  
  
-   <span data-ttu-id="5d74f-132">執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="5d74f-132">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="5d74f-133">這可用來建立執行各種動作的作業，以及執行這些作業的維護計畫。</span><span class="sxs-lookup"><span data-stu-id="5d74f-133">This can be used to create jobs that perform a variety of actions and the maintenance plans to run those jobs.</span></span>  
  
 <span data-ttu-id="5d74f-134">維護工作產生的結果可以當做報表寫入文字檔，或寫入 `sysmaintplan_log` 中的維護計畫資料表 `sysmaintplan_logdetail` 和 `msdb`。</span><span class="sxs-lookup"><span data-stu-id="5d74f-134">The results generated by the maintenance tasks can be written as a report to a text file or to the maintenance plan tables (`sysmaintplan_log` and `sysmaintplan_logdetail`) in `msdb`.</span></span> <span data-ttu-id="5d74f-135">若要在記錄檔檢視器中檢視結果，請以滑鼠右鍵按一下 [維護計畫]，然後按一下 [檢視記錄]。</span><span class="sxs-lookup"><span data-stu-id="5d74f-135">To view the results in the log file viewer, right-click **Maintenance Plans**, and then click **View History**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="5d74f-136">相關工作</span><span class="sxs-lookup"><span data-stu-id="5d74f-136">Related Tasks</span></span>  
 <span data-ttu-id="5d74f-137">若要開始使用維護計畫，請使用下列主題。</span><span class="sxs-lookup"><span data-stu-id="5d74f-137">Use the following topics to get started with maintenance plans.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d74f-138">**說明**</span><span class="sxs-lookup"><span data-stu-id="5d74f-138">**Description**</span></span>|<span data-ttu-id="5d74f-139">**主題**</span><span class="sxs-lookup"><span data-stu-id="5d74f-139">**Topic**</span></span>|  
|<span data-ttu-id="5d74f-140">描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建立維護計畫。</span><span class="sxs-lookup"><span data-stu-id="5d74f-140">Describes how to create a maintenance plan by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|[<span data-ttu-id="5d74f-141">建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="5d74f-141">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)|  
|<span data-ttu-id="5d74f-142">描述如何使用維護計畫設計介面建立維護計畫。</span><span class="sxs-lookup"><span data-stu-id="5d74f-142">Describes how to create a maintenance plan by using the Maintenance Plan Design Surface.</span></span>|[<span data-ttu-id="5d74f-143">建立維護計畫 &#40;維護計畫設計介面&#41;</span><span class="sxs-lookup"><span data-stu-id="5d74f-143">Create a Maintenance Plan &#40;Maintenance Plan Design Surface&#41;</span></span>](create-a-maintenance-plan-maintenance-plan-design-surface.md)|  
|<span data-ttu-id="5d74f-144">記載 [物件總管] 中可用的維護計畫功能。</span><span class="sxs-lookup"><span data-stu-id="5d74f-144">Documents maintenance plan functionality available in Object Explorer.</span></span>|[<span data-ttu-id="5d74f-145">維護計畫節點 &#40;物件總管&#41;</span><span class="sxs-lookup"><span data-stu-id="5d74f-145">Maintenance Plans Node &#40;Object Explorer&#41;</span></span>](../../ssms/object/object-explorer.md)|  
  
  
