---
title: SQL Server 監視器概觀 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlservermonitor.main.f1
helpviewer_keywords:
- SQL Server Monitor [SQL Server]
ms.assetid: 048ae16d-31c3-489a-9f1e-1400a3bacd39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab90186ed493e616e672cfacf881fd61be166f88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585579"
---
# <a name="sql-server-monitor-overview"></a><span data-ttu-id="c8303-102">SQL Server 監視器概觀</span><span class="sxs-lookup"><span data-stu-id="c8303-102">SQL Server Monitor Overview</span></span>
  <span data-ttu-id="c8303-103">「SQL Server 監視器」不會執行監視功能，但是它所主控的模組會執行該項功能。</span><span class="sxs-lookup"><span data-stu-id="c8303-103">SQL Server Monitor does not perform monitoring functions, but it hosts modules that do.</span></span> <span data-ttu-id="c8303-104">「SQL Server 監視器」的模組包括「複寫監視器」和「資料庫鏡像監視器」。</span><span class="sxs-lookup"><span data-stu-id="c8303-104">The SQL Server Monitor modules include Replication Monitor and Database Mirroring Monitor.</span></span>  
  
 <span data-ttu-id="c8303-105">若要使用其中一個模組，請在 **[執行]** 功能表上選取該模組。</span><span class="sxs-lookup"><span data-stu-id="c8303-105">To use one of these modules, select that module on the **Go** menu.</span></span> <span data-ttu-id="c8303-106">目前選取的模組即擁有導覽窗格和詳細資料窗格的內容、使用者在詳細資料窗格中所做的動作，以及對內容和狀態的查詢。</span><span class="sxs-lookup"><span data-stu-id="c8303-106">The currently selected module owns the content of the navigation and detail panes, user interaction in the detail panes, and the queries for content and status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8303-107">如需這些監視器的詳細資訊，請參閱 [監視複寫](../../relational-databases/replication/monitoring-replication.md) 和 [監視資料庫鏡像 &#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c8303-107">For more information about these monitors, see [Monitoring Replication](../../relational-databases/replication/monitoring-replication.md) and [Monitoring Database Mirroring &#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c8303-108">權限</span><span class="sxs-lookup"><span data-stu-id="c8303-108">Permissions</span></span>  
  
-   <span data-ttu-id="c8303-109">複寫監視器</span><span class="sxs-lookup"><span data-stu-id="c8303-109">Replication Monitor</span></span>  
  
     <span data-ttu-id="c8303-110">若要監視複寫，您必須是「散發者」端 **sysadmin** 固定伺服器角色的成員，或是散發資料庫中 **replmonitor** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="c8303-110">To monitor replication, you must be a member of the **sysadmin** fixed server role at the Distributor or a member of the **replmonitor** fixed database role in the distribution database.</span></span> <span data-ttu-id="c8303-111">系統管理員可以將任何使用者新增到 **replmonitor** 角色，此角色允許該使用者在「複寫監視器」中檢視複寫活動；不過，使用者不能管理複寫。</span><span class="sxs-lookup"><span data-stu-id="c8303-111">A system administrator can add any user to the **replmonitor** role, which allows that user to view replication activity in Replication Monitor; however, the user cannot administer replication.</span></span>  
  
-   <span data-ttu-id="c8303-112">資料庫鏡像監視器</span><span class="sxs-lookup"><span data-stu-id="c8303-112">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="c8303-113">若要監視資料庫鏡像，您必須是伺服器執行個體上 **sysadmin** 固定伺服器角色或 **dbm_monitor** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="c8303-113">To monitor database mirroring, you must be a member of either the **sysadmin** fixed server role or the **dbm_monitor** fixed database role on the server instance.</span></span> <span data-ttu-id="c8303-114">如果您只是其中一個夥伴伺服器執行個體上 **系統管理員** 或 **dbm_monitor** 的成員，則監視器只能連接到該夥伴，不能從其他夥伴那裡擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="c8303-114">If you are a member of **sysadmin** or **dbm_monitor** on only one of the partner server instances, the monitor can connect only to that partner; the monitor cannot retrieve information from the other partner.</span></span> <span data-ttu-id="c8303-115">如需詳細資訊，請參閱 [Database Mirroring Monitor Overview](../database-mirroring/database-mirroring-monitor-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c8303-115">For more information, see [Database Mirroring Monitor Overview](../database-mirroring/database-mirroring-monitor-overview.md).</span></span>  
  
## <a name="menu-options"></a><span data-ttu-id="c8303-116">功能表選項</span><span class="sxs-lookup"><span data-stu-id="c8303-116">Menu Options</span></span>  
 <span data-ttu-id="c8303-117">「SQL Server 監視器」的功能表包含與「SQL Server 監視器」相關的命令。</span><span class="sxs-lookup"><span data-stu-id="c8303-117">SQL Server Monitor has a menu that contains commands that pertain to SQL Server Monitor.</span></span> <span data-ttu-id="c8303-118">這個功能表也可以包含選取之模組的命令。</span><span class="sxs-lookup"><span data-stu-id="c8303-118">This menu may also contain commands from the selected module.</span></span>  
  
 <span data-ttu-id="c8303-119">下列是與「SQL Server 監視器」相關的功能表選項：</span><span class="sxs-lookup"><span data-stu-id="c8303-119">The following menu options pertain to SQL Server Monitor.</span></span>  
  
 <span data-ttu-id="c8303-120">**檔案**</span><span class="sxs-lookup"><span data-stu-id="c8303-120">**File**</span></span>  
 <span data-ttu-id="c8303-121">這個功能表包含 [結束] 命令。</span><span class="sxs-lookup"><span data-stu-id="c8303-121">This menu contains the **Exit** command.</span></span>  
  
 <span data-ttu-id="c8303-122">**動作**</span><span class="sxs-lookup"><span data-stu-id="c8303-122">**Action**</span></span>  
 <span data-ttu-id="c8303-123">包含導覽樹狀目錄中選取之節點的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="c8303-123">Contains the context menu of the node selected in the navigation tree.</span></span>  
  
 <span data-ttu-id="c8303-124">**Go**</span><span class="sxs-lookup"><span data-stu-id="c8303-124">**Go**</span></span>  
 <span data-ttu-id="c8303-125">包含監視元件的清單：</span><span class="sxs-lookup"><span data-stu-id="c8303-125">Contains a list of monitoring components:</span></span>  
  
-   <span data-ttu-id="c8303-126">資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="c8303-126">Database Mirroring</span></span>  
  
-   <span data-ttu-id="c8303-127">複寫</span><span class="sxs-lookup"><span data-stu-id="c8303-127">Replication</span></span>  
  
 <span data-ttu-id="c8303-128">**若要使用 SQL Server Management Studio 監視資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="c8303-128">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="c8303-129">啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c8303-129">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="c8303-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8303-130">See Also</span></span>  
 [<span data-ttu-id="c8303-131">監視資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c8303-131">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-sql-server.md)  
  
  
