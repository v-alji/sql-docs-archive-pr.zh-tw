---
title: 延遲交易 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- I/O [SQL Server], database recovery
- restoring pages [SQL Server]
- deferred transactions
- modifying transaction deferred state
ms.assetid: 6fc0f9b6-d3ea-4971-9f27-d0195d1ff718
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 188a0409fbad3f12283adacafbfcb5f176650b72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595141"
---
# <a name="deferred-transactions-sql-server"></a><span data-ttu-id="63191-102">延遲交易 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63191-102">Deferred Transactions (SQL Server)</span></span>
  <span data-ttu-id="63191-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 中，如果在資料庫啟動期間，回復 (復原) 所需的資料已離線，就會延期損毀的交易。</span><span class="sxs-lookup"><span data-stu-id="63191-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise, a corrupted transaction can become deferred if data required by rollback (undo) is offline during database startup.</span></span> <span data-ttu-id="63191-104">「延遲交易」  是在向前復原階段完成時尚未認可，而發生無法回復之錯誤的交易。</span><span class="sxs-lookup"><span data-stu-id="63191-104">A *deferred transaction* is a transaction that is uncommitted when the roll forward phase finishes and that has encountered an error that prevents it from being rolled back.</span></span> <span data-ttu-id="63191-105">因為交易無法回復，所以會延期。</span><span class="sxs-lookup"><span data-stu-id="63191-105">Because the transaction cannot be rolled back, it is deferred.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63191-106">只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 才會延期損毀的交易。</span><span class="sxs-lookup"><span data-stu-id="63191-106">Corrupted transactions are deferred only in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="63191-107">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的其他版本中，損毀的交易會造成啟動失敗。</span><span class="sxs-lookup"><span data-stu-id="63191-107">In other editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a corrupted transaction causes startup to fail.</span></span>  
  
 <span data-ttu-id="63191-108">發生延遲交易通常是因為，在向前復原資料庫時發生 I/O 錯誤，使得系統無法讀取交易所需的頁面。</span><span class="sxs-lookup"><span data-stu-id="63191-108">Generally, a deferred transaction occurs because, while the database was being rolled forward, an I/O error prevented reading a page that was required by the transaction.</span></span> <span data-ttu-id="63191-109">不過，檔案層級的錯誤也可能導致交易延遲。</span><span class="sxs-lookup"><span data-stu-id="63191-109">However, an error at the file level can also cause deferred transactions.</span></span> <span data-ttu-id="63191-110">當部分還原順序在需要進行交易回復時停止，且交易所需的資料已離線，就有可能發生交易延遲。</span><span class="sxs-lookup"><span data-stu-id="63191-110">A deferred transaction can also occur when a partial restore sequence stops at a point at which transaction rollback is necessary and a transaction requires data that is offline.</span></span>  
  
 <span data-ttu-id="63191-111">正在回復中且發生 I/O 錯誤的使用者交易，會導致整個資料庫離線。</span><span class="sxs-lookup"><span data-stu-id="63191-111">User transactions that are rolling back and hit an I/O error cause the whole database to go offline.</span></span> <span data-ttu-id="63191-112">當資料庫回到線上時，重做便會重新取得原先擁有的所有鎖定，並嘗試回復所有未認可的交易。</span><span class="sxs-lookup"><span data-stu-id="63191-112">When the database is brought back online, the redo reacquires all the locks it had and tries to roll back all the uncommitted transactions.</span></span> <span data-ttu-id="63191-113">交易修改的所有資料仍會適當地鎖定，直到可以回復該交易為止。</span><span class="sxs-lookup"><span data-stu-id="63191-113">All data modified by a transaction remains appropriately locked until the transaction can roll back.</span></span> <span data-ttu-id="63191-114">當修復損毀且重新啟動資料庫時，或者在線上還原之後，當資料庫仍在線上並解決了延遲交易的問題時，無法回復的交易將會放棄鎖定。</span><span class="sxs-lookup"><span data-stu-id="63191-114">Transactions that cannot be rolled back will give up their locks when the corruption is fixed and the database restarted or, after an online restore, when the deferred transactions are resolved while the database remains online.</span></span> <span data-ttu-id="63191-115">在此之前，延遲交易可以保留鎖定，以防止整個資料庫上的特定作業。</span><span class="sxs-lookup"><span data-stu-id="63191-115">Until that point, a deferred transaction can hold locks that prevent certain operations on the database as a whole.</span></span> <span data-ttu-id="63191-116">例如，如果延遲交易包含 CREATE TABLE 指示，則在解決延遲交易的問題之前，沒有任何使用者可以建立資料表。</span><span class="sxs-lookup"><span data-stu-id="63191-116">For example, if a deferred transaction contains a CREATE TABLE instruction, no user can create a table until the deferred transaction has been resolved.</span></span>  
  
 <span data-ttu-id="63191-117">發生延遲交易的原因也可能是，分次還原將資料庫復原到了某個時間點，而資料庫就在此時尚有未還原且離線的檔案群組受到一或多個使用中交易影響。</span><span class="sxs-lookup"><span data-stu-id="63191-117">Deferred transaction can also occur because a piecemeal restore recovers a database to a point at which one or more active transactions are affecting a filegroup that has not yet been restored and is offline.</span></span> <span data-ttu-id="63191-118">因為無法回復交易，所以就將它延遲。</span><span class="sxs-lookup"><span data-stu-id="63191-118">Because the transactions cannot be rolled back, they become deferred.</span></span>  
  
 <span data-ttu-id="63191-119">下表列出會導致資料庫執行復原的動作，以及如果發生 I/O 問題時的結果。</span><span class="sxs-lookup"><span data-stu-id="63191-119">The following table lists the actions that cause a database to perform recovery and the outcome if an I/O problem occurs.</span></span>  
  
|<span data-ttu-id="63191-120">動作</span><span class="sxs-lookup"><span data-stu-id="63191-120">Action</span></span>|<span data-ttu-id="63191-121">解決方法 (如果發生 I/O 問題，或所需的資料離線)</span><span class="sxs-lookup"><span data-stu-id="63191-121">Resolution (if I/O problems occur or required data is offline)</span></span>|  
|------------|-----------------------------------------------------------------------|  
|<span data-ttu-id="63191-122">伺服器啟動</span><span class="sxs-lookup"><span data-stu-id="63191-122">Server start</span></span>|<span data-ttu-id="63191-123">延遲交易</span><span class="sxs-lookup"><span data-stu-id="63191-123">Deferred transaction</span></span>|  
|<span data-ttu-id="63191-124">還原</span><span class="sxs-lookup"><span data-stu-id="63191-124">Restore</span></span>|<span data-ttu-id="63191-125">延遲交易</span><span class="sxs-lookup"><span data-stu-id="63191-125">Deferred transaction</span></span>|  
|<span data-ttu-id="63191-126">連結</span><span class="sxs-lookup"><span data-stu-id="63191-126">Attach</span></span>|<span data-ttu-id="63191-127">附加動作失敗</span><span class="sxs-lookup"><span data-stu-id="63191-127">Attach fails</span></span>|  
|<span data-ttu-id="63191-128">自動重新啟動</span><span class="sxs-lookup"><span data-stu-id="63191-128">Autorestart</span></span>|<span data-ttu-id="63191-129">延遲交易</span><span class="sxs-lookup"><span data-stu-id="63191-129">Deferred transaction</span></span>|  
|<span data-ttu-id="63191-130">建立資料庫或資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="63191-130">Create database or database snapshot</span></span>|<span data-ttu-id="63191-131">建立動作失敗</span><span class="sxs-lookup"><span data-stu-id="63191-131">Creation fails</span></span>|  
|<span data-ttu-id="63191-132">重做資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="63191-132">Redo on database mirroring</span></span>|<span data-ttu-id="63191-133">延遲交易</span><span class="sxs-lookup"><span data-stu-id="63191-133">Deferred transaction</span></span>|  
|<span data-ttu-id="63191-134">檔案群組離線</span><span class="sxs-lookup"><span data-stu-id="63191-134">Filegroup is offline</span></span>|<span data-ttu-id="63191-135">延遲交易</span><span class="sxs-lookup"><span data-stu-id="63191-135">Deferred transaction</span></span>|  
  
## <a name="moving-a-transaction-out-of-the-deferred-state"></a><span data-ttu-id="63191-136">將交易移出 DEFERRED 狀態</span><span class="sxs-lookup"><span data-stu-id="63191-136">Moving a Transaction Out of the DEFERRED State</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="63191-137">延遲交易會讓交易記錄保持在使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="63191-137">Deferred transactions keep the transaction log active.</span></span> <span data-ttu-id="63191-138">在這些交易移出延遲狀態之前，將無法截斷含有任何延遲交易的虛擬記錄檔。</span><span class="sxs-lookup"><span data-stu-id="63191-138">A virtual log file that contains any deferred transactions cannot be truncated until those transactions are moved out of the deferred state.</span></span> <span data-ttu-id="63191-139">如需記錄截斷的詳細資訊，請參閱[交易記錄 &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="63191-139">For more information about log truncation, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="63191-140">若要將交易移出延遲狀態，資料庫必須正確地啟動，沒有任何 I/O 錯誤。</span><span class="sxs-lookup"><span data-stu-id="63191-140">To move the transaction out of the deferred state, the database must start cleanly without any I/O errors.</span></span> <span data-ttu-id="63191-141">如果有延遲交易存在，您必須修正 I/O 錯誤的來源。</span><span class="sxs-lookup"><span data-stu-id="63191-141">If deferred transactions exist, you must fix the source of the I/O errors.</span></span> <span data-ttu-id="63191-142">以下依一般嘗試的順序，列出可用的解決方法：</span><span class="sxs-lookup"><span data-stu-id="63191-142">The available solutions, listed in the order in which they are typically tried, are as follows:</span></span>  
  
-   <span data-ttu-id="63191-143">重新啟動資料庫。</span><span class="sxs-lookup"><span data-stu-id="63191-143">Restart the database.</span></span> <span data-ttu-id="63191-144">如果問題是暫時性的，資料庫啟動時應該就不再有延遲交易。</span><span class="sxs-lookup"><span data-stu-id="63191-144">If the problem was transient, the database should start without deferred transactions.</span></span>  
  
-   <span data-ttu-id="63191-145">如果是因為檔案群組離線而導致交易延遲，請將檔案群組連回線上。</span><span class="sxs-lookup"><span data-stu-id="63191-145">If the transactions were deferred because a filegroup was offline, bring the filegroup back online.</span></span>  
  
     <span data-ttu-id="63191-146">若要讓離線的檔案群組恢復上線，請使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="63191-146">To bring an offline filegroup back online, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    RESTORE DATABASE database_name FILEGROUP=<filegroup_name>  
    ```  
  
-   <span data-ttu-id="63191-147">還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="63191-147">Restore the database.</span></span> <span data-ttu-id="63191-148">進行線上還原後，任何延遲的交易都會解決。</span><span class="sxs-lookup"><span data-stu-id="63191-148">After an online restore, any deferred transactions are resolved.</span></span>  
  
     <span data-ttu-id="63191-149">在完整或大量記錄復原模式下，如果延遲交易只是由少數的損毀頁面所造成，線上分頁還原可能就可以解決錯誤 (在支援的情況下)。</span><span class="sxs-lookup"><span data-stu-id="63191-149">Under the full or bulk-logged recovery model, if the deferred transactions were caused by only a few corrupted pages, an online page restore might resolve the errors (where supported).</span></span>  
  
-   <span data-ttu-id="63191-150">如果您不再需要用到某個因離線狀態引起延遲交易的檔案群組，請將離線檔案群組設定為無用 (不再使用)。</span><span class="sxs-lookup"><span data-stu-id="63191-150">If you are no longer require a filegroup whose offline status is causing deferred transactions, make the offline filegroup defunct.</span></span> <span data-ttu-id="63191-151">因檔案群組離線而延遲的交易會在檔案群組變成無用之後移出延遲狀態。</span><span class="sxs-lookup"><span data-stu-id="63191-151">Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="63191-152">無用的檔案群組永遠都不能復原。</span><span class="sxs-lookup"><span data-stu-id="63191-152">A defunct filegroup can never be recovered.</span></span>  
  
     <span data-ttu-id="63191-153">如需詳細資訊，請參閱 [移除無用的檔案群組 &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="63191-153">For more information, see [Remove Defunct Filegroups &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="63191-154">如果交易因錯誤的頁面而延遲，而且資料庫的完好備份不存在，請使用下列程序來修復資料庫：</span><span class="sxs-lookup"><span data-stu-id="63191-154">If transactions were deferred because of a bad page and if a good backup of the database does not exist, use the following process to repair the database:</span></span>  
  
    -   <span data-ttu-id="63191-155">首先執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，將資料庫置於緊急模式中：</span><span class="sxs-lookup"><span data-stu-id="63191-155">First put the database into emergency mode by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
        ```  
        ALTER DATABASE <database_name> SET EMERGENCY  
        ```  
  
         <span data-ttu-id="63191-156">如需緊急模式的詳細資訊，請參閱 [資料庫狀態](../databases/database-states.md)。</span><span class="sxs-lookup"><span data-stu-id="63191-156">For information about emergency mode, see [Database States](../databases/database-states.md).</span></span>  
  
    -   <span data-ttu-id="63191-157">接著，在下列其中一個 DBCC 陳述式內使用 DBCC REPAIR_ALLOW_DATA_LOSS 選項以修復資料庫：[DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)、[DBCC CHECKALLOC](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql) 或 [DBCC CHECKTABLE](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="63191-157">Then, repair the database by using the DBCC REPAIR_ALLOW_DATA_LOSS option in one of the following DBCC statements: [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql), [DBCC CHECKALLOC](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql), or [DBCC CHECKTABLE](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql).</span></span>  
  
         <span data-ttu-id="63191-158">當 DBCC 發現錯誤的頁面時，它會取消配置該頁面，並修復任何相關的錯誤。</span><span class="sxs-lookup"><span data-stu-id="63191-158">When DBCC encounters the bad page, DBCC deallocates it and repairs any related errors.</span></span> <span data-ttu-id="63191-159">此方式可以讓資料庫以實體上一致的狀態回到線上。</span><span class="sxs-lookup"><span data-stu-id="63191-159">This approach enables the database to be brought back online in a physically consistent state.</span></span> <span data-ttu-id="63191-160">不過，很可能遺失其他資料，因此除非不得已，盡量不要使用這個方式。</span><span class="sxs-lookup"><span data-stu-id="63191-160">However, additional data might also be lost; therefore, this approach should be used as a last resort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63191-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63191-161">See Also</span></span>  
 <span data-ttu-id="63191-162">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63191-162">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="63191-163">[移除無用的檔案群組 &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63191-163">[Remove Defunct Filegroups &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="63191-164">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="63191-164">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="63191-165">[檔案還原 &#40;簡單復原模式&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="63191-165">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="63191-166">[還原頁面 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63191-166">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="63191-167">[分次還原 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63191-167">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="63191-168">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63191-168">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="63191-169">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63191-169">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
