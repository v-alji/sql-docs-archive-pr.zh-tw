---
title: 變更資料擷取和其他 SQL Server 功能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], other SQL Server features and
ms.assetid: 7dfcb362-1904-4578-8274-da16681a960e
author: rothja
ms.author: jroth
ms.openlocfilehash: acafd5ba49bec92fd4c6b93c4163affaa42ab7f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597688"
---
# <a name="change-data-capture-and-other-sql-server-features"></a><span data-ttu-id="764c9-102">異動資料擷取和其他 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="764c9-102">Change Data Capture and Other SQL Server Features</span></span>
  <span data-ttu-id="764c9-103">此主題描述下列功能如何與變更資料擷取互動：</span><span class="sxs-lookup"><span data-stu-id="764c9-103">This topic describes how the following features interact with change data capture:</span></span>  
  
-   [<span data-ttu-id="764c9-104">Change tracking</span><span class="sxs-lookup"><span data-stu-id="764c9-104">Change tracking</span></span>](#ChangeTracking)  
  
-   [<span data-ttu-id="764c9-105">資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="764c9-105">Database mirroring</span></span>](#DatabaseMirroring)  
  
-   [<span data-ttu-id="764c9-106">異動複寫</span><span class="sxs-lookup"><span data-stu-id="764c9-106">Transactional replication</span></span>](#TransReplication)  
  
-   [<span data-ttu-id="764c9-107">還原或附加啟用變更資料擷取的資料庫</span><span class="sxs-lookup"><span data-stu-id="764c9-107">Restoring or Attaching a Database Enabled for Change Data Capture</span></span>](#RestoreOrAttach)  
  
##  <a name="change-tracking"></a><a name="ChangeTracking"></a> <span data-ttu-id="764c9-108">變更追蹤</span><span class="sxs-lookup"><span data-stu-id="764c9-108">Change Tracking</span></span>  
 <span data-ttu-id="764c9-109">您可以在同一個資料庫上啟用變更資料擷取和 [變更追蹤](about-change-tracking-sql-server.md) 。</span><span class="sxs-lookup"><span data-stu-id="764c9-109">Change data capture and [change tracking](about-change-tracking-sql-server.md) can be enabled on the same database.</span></span> <span data-ttu-id="764c9-110">不需要進行任何特殊考量。</span><span class="sxs-lookup"><span data-stu-id="764c9-110">No special considerations are required.</span></span> <span data-ttu-id="764c9-111">如需詳細資訊，請參閱[使用變更追蹤 &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="764c9-111">For more information, see [Work with Change Tracking &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md).</span></span>  
  
##  <a name="database-mirroring"></a><a name="DatabaseMirroring"></a> <span data-ttu-id="764c9-112">資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="764c9-112">Database Mirroring</span></span>  
 <span data-ttu-id="764c9-113">啟用變更資料擷取的資料庫可以進行鏡像。</span><span class="sxs-lookup"><span data-stu-id="764c9-113">A database that is enabled for change data capture can be mirrored.</span></span> <span data-ttu-id="764c9-114">若要確保擷取和清除會在容錯移轉之後自動進行，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="764c9-114">To ensure that capture and cleanup happen automatically after a failover, follow these steps:</span></span>  
  
1.  <span data-ttu-id="764c9-115">請確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 是在新的主體伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="764c9-115">Ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running on the new principal server instance.</span></span>  
  
2.  <span data-ttu-id="764c9-116">在新的主體資料庫上建立擷取作業和清除作業 (之前的鏡像資料庫)。</span><span class="sxs-lookup"><span data-stu-id="764c9-116">Create the capture job and cleanup job on the new principal database (the former mirror database).</span></span> <span data-ttu-id="764c9-117">若要建立這些作業，請使用 [sp_cdc_add_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="764c9-117">To create the jobs, use the [sp_cdc_add_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql) stored procedure.</span></span>  
  
 <span data-ttu-id="764c9-118">若要檢視清除或擷取作業的目前組態，請在新的主體伺服器執行個體上使用 [sys.sp_cdc_help_jobs](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="764c9-118">To view the current configuration of a cleanup or capture job, use the [sys.sp_cdc_help_jobs](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql) stored procedure on the new principal server instance.</span></span> <span data-ttu-id="764c9-119">對於指定的資料庫而言，擷取作業會命名為 cdc.*database_name*_capture，而清除作業會命名為 cdc.*database_name*_cleanup，其中 *database_name* 是資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="764c9-119">For a given database, the capture job is named cdc.*database_name*_capture, and the cleanup job is named cdc.*database_name*_cleanup, where *database_name* is the name of the database.</span></span>  
  
 <span data-ttu-id="764c9-120">若要變更作業的組態，請使用 [sys.sp_cdc_change_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="764c9-120">To change the configuration of a job, use the [sys.sp_cdc_change_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql) stored procedure.</span></span>  
  
 <span data-ttu-id="764c9-121">如需資料庫鏡像的相關資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="764c9-121">For information about database mirroring, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
##  <a name="transactional-replication"></a><a name="TransReplication"></a><span data-ttu-id="764c9-122">異動複寫</span><span class="sxs-lookup"><span data-stu-id="764c9-122">Transactional Replication</span></span>  
 <span data-ttu-id="764c9-123">雖然變更資料擷取和異動複寫可以同時存在同一個資料庫中，但是同時啟用這兩項功能時，系統會以不同的方式處理變更資料表的擴展。</span><span class="sxs-lookup"><span data-stu-id="764c9-123">Change data capture and transactional replication can coexist in the same database, but population of the change tables is handled differently when both features are enabled.</span></span> <span data-ttu-id="764c9-124">變更資料擷取和異動複寫一定會使用相同的程序 [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql)，從交易記錄中讀取變更。</span><span class="sxs-lookup"><span data-stu-id="764c9-124">Change data capture and transactional replication always use the same procedure, [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql), to read changes from the transaction log.</span></span> <span data-ttu-id="764c9-125">單獨啟用變更資料擷取時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業就會呼叫 `sp_replcmds`。</span><span class="sxs-lookup"><span data-stu-id="764c9-125">When change data capture is enabled on its own, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job calls `sp_replcmds`.</span></span> <span data-ttu-id="764c9-126">當相同的資料庫上同時啟用這兩項功能時，記錄讀取器代理程式會呼叫 `sp_replcmds` 。</span><span class="sxs-lookup"><span data-stu-id="764c9-126">When both features are enabled on the same database, the Log Reader Agent calls `sp_replcmds`.</span></span> <span data-ttu-id="764c9-127">這個代理程式會同時擴展變更資料表和散發資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="764c9-127">This agent populates both the change tables and the distribution database tables.</span></span> <span data-ttu-id="764c9-128">如需詳細資訊，請參閱 [Replication Log Reader Agent](../replication/agents/replication-log-reader-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="764c9-128">For more information, see [Replication Log Reader Agent](../replication/agents/replication-log-reader-agent.md).</span></span>  
  
 <span data-ttu-id="764c9-129">假設您在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫上啟用了變更資料擷取，而且有兩份資料表啟用了擷取。</span><span class="sxs-lookup"><span data-stu-id="764c9-129">Consider a scenario in which change data capture is enabled on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and two tables are enabled for capture.</span></span> <span data-ttu-id="764c9-130">為了擴展變更資料表，擷取作業會呼叫 `sp_replcmds`。</span><span class="sxs-lookup"><span data-stu-id="764c9-130">To populate the change tables, the capture job calls `sp_replcmds`.</span></span> <span data-ttu-id="764c9-131">資料庫啟用了異動複寫，而且建立了發行集。</span><span class="sxs-lookup"><span data-stu-id="764c9-131">The database is enabled for transactional replication, and a publication is created.</span></span> <span data-ttu-id="764c9-132">此時，會針對資料庫建立記錄讀取器代理程式，並且刪除擷取作業。</span><span class="sxs-lookup"><span data-stu-id="764c9-132">Now, the Log Reader Agent is created for the database and the capture job is deleted.</span></span> <span data-ttu-id="764c9-133">記錄讀取器代理程式會繼續掃描記錄，從變更資料表所認可的最後一個記錄序號開始。</span><span class="sxs-lookup"><span data-stu-id="764c9-133">The Log Reader Agent continues to scan the log from the last log sequence number that was committed to the change table.</span></span> <span data-ttu-id="764c9-134">如此可確保變更資料表中的資料保持一致。</span><span class="sxs-lookup"><span data-stu-id="764c9-134">This ensures data consistency in the change tables.</span></span> <span data-ttu-id="764c9-135">如果這個資料庫停用了異動複寫，系統就會移除記錄讀取器代理程式並且重新建立擷取作業。</span><span class="sxs-lookup"><span data-stu-id="764c9-135">If transactional replication is disabled in this database, the Log Reader Agent is removed and the capture job is re-created.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="764c9-136">當記錄讀取器代理程式同時用於變更資料擷取和異動複寫時，複寫的變更會先寫入散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="764c9-136">When the Log Reader Agent is used for both change data capture and transactional replication, replicated changes are first written to the distribution database.</span></span> <span data-ttu-id="764c9-137">然後，擷取的變更才會寫入變更資料表。</span><span class="sxs-lookup"><span data-stu-id="764c9-137">Then, captured changes are written to the change tables.</span></span> <span data-ttu-id="764c9-138">這兩項作業會一起認可。</span><span class="sxs-lookup"><span data-stu-id="764c9-138">Both operations are committed together.</span></span> <span data-ttu-id="764c9-139">如果寫入散發資料庫時發生延遲，系統會建立對應的延遲，然後變更才會出現在變更資料表中。</span><span class="sxs-lookup"><span data-stu-id="764c9-139">If there is any latency in writing to the distribution database, there will be a corresponding latency before changes appear in the change tables.</span></span>  
  
 <span data-ttu-id="764c9-140">啟用變更資料擷取時，異動複寫的 **proc exec** 選項無法使用。</span><span class="sxs-lookup"><span data-stu-id="764c9-140">The **proc exec** option of transactional replication is not available when change data capture is enabled.</span></span>  
  
##  <a name="restoring-or-attaching-a-database-enabled-for-change-data-capture"></a><a name="RestoreOrAttach"></a><span data-ttu-id="764c9-141">還原或附加啟用變更資料捕獲的資料庫</span><span class="sxs-lookup"><span data-stu-id="764c9-141">Restoring or Attaching a Database Enabled for Change Data Capture</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="764c9-142">會使用下列邏輯來判斷在還原或附加資料庫之後，變更資料擷取是否會維持啟用狀態：</span><span class="sxs-lookup"><span data-stu-id="764c9-142">uses the following logic to determine if change data capture remains enabled after a database is restored or attached:</span></span>  
  
-   <span data-ttu-id="764c9-143">如果資料庫還原至具有相同資料庫名稱的相同伺服器，變更資料擷取就會維持啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="764c9-143">If a database is restored to the same server with the same database name, change data capture remains enabled.</span></span>  
  
-   <span data-ttu-id="764c9-144">如果資料庫還原至其他伺服器，預設會停用變更資料擷取並且刪除所有相關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="764c9-144">If a database is restored to another server, by default change data capture is disabled and all related metadata is deleted.</span></span>  
  
     <span data-ttu-id="764c9-145">若要保留變更資料擷取，請在還原資料庫時使用 `KEEP_CDC` 選項。</span><span class="sxs-lookup"><span data-stu-id="764c9-145">To retain change data capture, use the `KEEP_CDC` option when restoring the database.</span></span> <span data-ttu-id="764c9-146">如需有關這個選項的詳細資訊，請參閱＜ [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)＞。</span><span class="sxs-lookup"><span data-stu-id="764c9-146">For more information about this option, see [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
-   <span data-ttu-id="764c9-147">如果資料庫卸離並附加至相同伺服器或其他伺服器，變更資料擷取就會維持啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="764c9-147">If a database is detached and attached to the same server or another server, change data capture remains enabled.</span></span>  
  
-   <span data-ttu-id="764c9-148">如果您使用 `KEEP_CDC` 選項，將資料庫附加或還原至 Enterprise 以外的任何版本，此作業就會遭封鎖，因為異動資料擷取需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise。</span><span class="sxs-lookup"><span data-stu-id="764c9-148">If a database is attached or restored with the `KEEP_CDC` option to any edition other than Enterprise, the operation is blocked because change data capture requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="764c9-149">此時會顯示錯誤訊息 934：</span><span class="sxs-lookup"><span data-stu-id="764c9-149">Error message 934 is displayed:</span></span>  
  
     `SQL Server cannot load database '%.*ls' because change data capture is enabled. The currently installed edition of SQL Server does not support change data capture. Either disable change data capture in the database by using a supported edition of SQL Server, or upgrade the instance to one that supports change data capture.`  
  
 <span data-ttu-id="764c9-150">您可以使用 [sys.sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) ，從還原或附加的資料庫中移除變更資料擷取。</span><span class="sxs-lookup"><span data-stu-id="764c9-150">You can use [sys.sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) to remove change data capture from a restored or attached database.</span></span>  
  
## <a name="change-data-capture-and-alwayson"></a><span data-ttu-id="764c9-151">變更資料擷取和 AlwaysON</span><span class="sxs-lookup"><span data-stu-id="764c9-151">Change Data Capture and AlwaysON</span></span>  
 <span data-ttu-id="764c9-152">當您使用 AlwaysON 時，應該在次要複寫上完成變更列舉以減少主要複寫的磁碟負載。</span><span class="sxs-lookup"><span data-stu-id="764c9-152">When you use AlwaysON, change enumeration should be done on the Secondary replication to reduce the disk load on the primary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764c9-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="764c9-153">See Also</span></span>  
 [<span data-ttu-id="764c9-154">管理和監視異動資料擷取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="764c9-154">Administer and Monitor Change Data Capture &#40;SQL Server&#41;</span></span>](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
