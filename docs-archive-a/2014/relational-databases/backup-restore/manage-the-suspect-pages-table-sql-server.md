---
title: 管理 suspect_pages 資料表 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
- restoring pages [SQL Server]
- pages [SQL Server], suspect
- pages [SQL Server], restoring
- suspect_pages system table
- suspect pages [SQL Server]
- restoring [SQL Server], pages
ms.assetid: f394d4bc-1518-4e61-97fc-bf184d972e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dd7aea63ae85a16e23ff532c7e18ace3c376a707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606912"
---
# <a name="manage-the-suspect_pages-table-sql-server"></a><span data-ttu-id="f20da-102">管理 suspect_pages 資料表 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f20da-102">Manage the suspect_pages Table (SQL Server)</span></span>
  <span data-ttu-id="f20da-103">本主題描述如何使用 **或** 管理 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] suspect_pages [!INCLUDE[tsql](../../includes/tsql-md.md)]資料表。</span><span class="sxs-lookup"><span data-stu-id="f20da-103">This topic describes how to manage the **suspect_pages** table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f20da-104">**suspect_pages** 資料表用於維護可疑頁面的相關資訊，有助於決定是否有必要進行還原。</span><span class="sxs-lookup"><span data-stu-id="f20da-104">The **suspect_pages** table is used for maintaining information about suspect pages, and is relevant in helping to decide whether a restore is necessary.</span></span> <span data-ttu-id="f20da-105">[suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 資料表位於 [msdb 資料庫](../databases/msdb-database.md)中。</span><span class="sxs-lookup"><span data-stu-id="f20da-105">The [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table resides in the [msdb database](../databases/msdb-database.md).</span></span>  
  
 <span data-ttu-id="f20da-106">頁面視為「可疑」的條件如下：當 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 嘗試讀取資料頁時，遇到下列其中一個錯誤：</span><span class="sxs-lookup"><span data-stu-id="f20da-106">A page is considered "suspect" when the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] encounters one of the following errors when it tries to read a data page:</span></span>  
  
-   <span data-ttu-id="f20da-107">由作業系統發出的迴圈冗余檢查 (CRC) 所造成的[823 錯誤](../errors-events/mssqlserver-823-database-engine-error.md)，例如磁片錯誤 (特定硬體錯誤) </span><span class="sxs-lookup"><span data-stu-id="f20da-107">An [823 error](../errors-events/mssqlserver-823-database-engine-error.md) that was caused by a cyclic redundancy check (CRC) issued by the operating system, such as a disk error (certain hardware errors)</span></span>  
  
-   <span data-ttu-id="f20da-108">[824 錯誤](../errors-events/mssqlserver-824-database-engine-error.md)，例如損毀頁 (任何邏輯錯誤) </span><span class="sxs-lookup"><span data-stu-id="f20da-108">An [824 error](../errors-events/mssqlserver-824-database-engine-error.md), such as a torn page (any logical error)</span></span>  
  
 <span data-ttu-id="f20da-109">每一個可疑頁面的頁面識別碼都會記錄在 **suspect_pages** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="f20da-109">The page ID of every suspect page is recorded in the **suspect_pages** table.</span></span> <span data-ttu-id="f20da-110">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會記錄正常處理期間 (例如下列時間) 發生的任何可疑頁面：</span><span class="sxs-lookup"><span data-stu-id="f20da-110">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] records any suspect pages encountered during regular processing, such as the following:</span></span>  
  
-   <span data-ttu-id="f20da-111">查詢必須讀取頁面。</span><span class="sxs-lookup"><span data-stu-id="f20da-111">A query has to read a page.</span></span>  
  
-   <span data-ttu-id="f20da-112">在 DBCC CHECKDB 作業期間。</span><span class="sxs-lookup"><span data-stu-id="f20da-112">During a DBCC CHECKDB operation.</span></span>  
  
-   <span data-ttu-id="f20da-113">在備份作業期間。</span><span class="sxs-lookup"><span data-stu-id="f20da-113">During a backup operation.</span></span>  
  
 <span data-ttu-id="f20da-114">在還原作業、DBCC 修復作業或卸除資料庫作業期間，也會視需要更新 **suspect_pages** 資料表。</span><span class="sxs-lookup"><span data-stu-id="f20da-114">The **suspect_pages** table is also updated as necessary during a restore operation, a DBCC repair operation, or a drop database operation.</span></span>  
  
 <span data-ttu-id="f20da-115">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f20da-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f20da-116">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f20da-116">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f20da-117">建議</span><span class="sxs-lookup"><span data-stu-id="f20da-117">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f20da-118">安全性</span><span class="sxs-lookup"><span data-stu-id="f20da-118">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f20da-119">**若要使用下列項目管理 suspect_pages 資料表：**</span><span class="sxs-lookup"><span data-stu-id="f20da-119">**To manage the suspect_pages table, using:**</span></span>  
  
     [<span data-ttu-id="f20da-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f20da-120">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f20da-121">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f20da-121">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f20da-122">開始之前</span><span class="sxs-lookup"><span data-stu-id="f20da-122">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f20da-123">建議</span><span class="sxs-lookup"><span data-stu-id="f20da-123">Recommendations</span></span>  
  
-   <span data-ttu-id="f20da-124">**記錄在 suspect_pages 資料表的錯誤**</span><span class="sxs-lookup"><span data-stu-id="f20da-124">**Errors Recorded in suspect_pages Table**</span></span>  
  
     <span data-ttu-id="f20da-125">**suspect_pages** 資料表每頁都會包含一個因 824 錯誤而失敗的資料列 (上限是 1,000 個資料列)。</span><span class="sxs-lookup"><span data-stu-id="f20da-125">The **suspect_pages** table contains one row per page that failed with an 824 error, up to a limit of 1,000 rows.</span></span> <span data-ttu-id="f20da-126">下表顯示在 **suspect_pages** 資料表的 **event_type** 資料行中所記錄的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f20da-126">The following table shows errors logged in the **event_type** column of the **suspect_pages** table.</span></span>  
  
    |<span data-ttu-id="f20da-127">錯誤描述</span><span class="sxs-lookup"><span data-stu-id="f20da-127">Error description</span></span>|<span data-ttu-id="f20da-128">**event_type** 值</span><span class="sxs-lookup"><span data-stu-id="f20da-128">**event_type** value</span></span>|  
    |-----------------------|---------------------------|  
    |<span data-ttu-id="f20da-129">作業系統 CRC 錯誤所導致的 823 錯誤，或是總和檢查碼錯誤或頁面損毀以外之原因 (例如，頁面識別碼不正確) 所導致的 824 錯誤</span><span class="sxs-lookup"><span data-stu-id="f20da-129">823 error caused by an operating system CRC error  or 824 error other than a bad checksum or a torn page (for example, a bad page ID)</span></span>|<span data-ttu-id="f20da-130">1</span><span class="sxs-lookup"><span data-stu-id="f20da-130">1</span></span>|  
    |<span data-ttu-id="f20da-131">錯誤的總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="f20da-131">Bad checksum</span></span>|<span data-ttu-id="f20da-132">2</span><span class="sxs-lookup"><span data-stu-id="f20da-132">2</span></span>|  
    |<span data-ttu-id="f20da-133">損毀頁面</span><span class="sxs-lookup"><span data-stu-id="f20da-133">Torn page</span></span>|<span data-ttu-id="f20da-134">3</span><span class="sxs-lookup"><span data-stu-id="f20da-134">3</span></span>|  
    |<span data-ttu-id="f20da-135">已還原 (在將頁面標示為錯誤頁面之後，還原該頁面)</span><span class="sxs-lookup"><span data-stu-id="f20da-135">Restored (The page was restored after it was marked bad)</span></span>|<span data-ttu-id="f20da-136">4</span><span class="sxs-lookup"><span data-stu-id="f20da-136">4</span></span>|  
    |<span data-ttu-id="f20da-137">已修復 (DBCC、AlwaysOn 或鏡像已修復頁面)</span><span class="sxs-lookup"><span data-stu-id="f20da-137">Repaired (DBCC, AlwaysOn, or mirroring repaired the page)</span></span>|<span data-ttu-id="f20da-138">5</span><span class="sxs-lookup"><span data-stu-id="f20da-138">5</span></span>|  
    |<span data-ttu-id="f20da-139">由 DBCC 取消配置</span><span class="sxs-lookup"><span data-stu-id="f20da-139">Deallocated by DBCC</span></span>|<span data-ttu-id="f20da-140">7</span><span class="sxs-lookup"><span data-stu-id="f20da-140">7</span></span>|  
  
     <span data-ttu-id="f20da-141">**suspect_pages** 資料表也會記錄暫時性錯誤。</span><span class="sxs-lookup"><span data-stu-id="f20da-141">The **suspect_pages** table also records transient errors.</span></span> <span data-ttu-id="f20da-142">暫時性錯誤的來源包括 I/O 錯誤 (例如，纜線連接斷開)，或暫時在重複總和檢查碼測試中失敗的頁面。</span><span class="sxs-lookup"><span data-stu-id="f20da-142">Sources of transient errors include an I/O error (for example, a cable was disconnected) or a page that temporarily fails a repeated checksum test.</span></span>  
  
-   <span data-ttu-id="f20da-143">**Database Engine 更新 suspect_pages 資料表的方式**</span><span class="sxs-lookup"><span data-stu-id="f20da-143">**How the Database Engine Updates the suspect_pages Table**</span></span>  
  
     <span data-ttu-id="f20da-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會對 **suspect_pages** 資料表採取下列動作：</span><span class="sxs-lookup"><span data-stu-id="f20da-144">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] takes the following actions on the **suspect_pages** table:</span></span>  
  
    -   <span data-ttu-id="f20da-145">如果資料表未滿，則為每個 824 錯誤更新一次，以指出發生錯誤，並使錯誤計數器遞增。</span><span class="sxs-lookup"><span data-stu-id="f20da-145">If the table is not full, it is updated for every 824 error, to indicate that an error has occurred, and the error counter is incremented.</span></span> <span data-ttu-id="f20da-146">如果經修復、還原或取消配置等方式修正錯誤後，頁面仍有錯誤，則其 **number_of_errors** 計數會遞增，而 **last_update** 資料行也會更新</span><span class="sxs-lookup"><span data-stu-id="f20da-146">If a page has an error after it is fixed by being repaired, restored, or deallocated, its **number_of_errors** count is incremented and its **last_update** column is updated</span></span>  
  
    -   <span data-ttu-id="f20da-147">經由還原或修復作業修正列出的頁面後，作業會更新 **suspect_pages** 資料列，指出該頁面已修復 (**event_type** = 5) 或還原 (**event_type** = 4) 該頁面。</span><span class="sxs-lookup"><span data-stu-id="f20da-147">After a listed page is fixed by a restore or a repair operation, the operation updates the **suspect_pages** row to indicate that the page is repaired (**event_type** = 5) or restored (**event_type** = 4).</span></span>  
  
    -   <span data-ttu-id="f20da-148">如果執行 DBCC 檢查，則該檢查會將任何沒有錯誤的頁面標示為已修復 (**event_type** = 5) 或已取消配置 (**event_type** = 7)。</span><span class="sxs-lookup"><span data-stu-id="f20da-148">If a DBCC check is run, the check marks any error-free pages as repaired (**event_type** = 5) or deallocated (**event_type** = 7).</span></span>  
  
-   <span data-ttu-id="f20da-149">**自動更新 suspect_pages 資料表**</span><span class="sxs-lookup"><span data-stu-id="f20da-149">**Automatic Updates to the suspect_pages Table**</span></span>  
  
     <span data-ttu-id="f20da-150">資料庫鏡像夥伴或 AlwaysOn 可用性複本會在嘗試從資料檔讀取頁面，但是因為以下其中一個原因而失敗之後，更新 **suspect_pages** 資料表。</span><span class="sxs-lookup"><span data-stu-id="f20da-150">A database mirroring partner or AlwaysOn availability replica updates the **suspect_pages** table after an attempt to read a page from a data file fails for one of the following reasons.</span></span>  
  
    -   <span data-ttu-id="f20da-151">作業系統 CRC 錯誤所造成的 823 錯誤。</span><span class="sxs-lookup"><span data-stu-id="f20da-151">An 823 error that is caused by an operating system CRC error.</span></span>  
  
    -   <span data-ttu-id="f20da-152">824 錯誤 (邏輯損毀，例如損毀頁)。</span><span class="sxs-lookup"><span data-stu-id="f20da-152">An 824 error (logical corruption such as a torn page).</span></span>  
  
     <span data-ttu-id="f20da-153">下列動作也會自動更新 **suspect_pages** 資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="f20da-153">The following actions also automatically update rows in the **suspect_pages** table.</span></span>  
  
    -   <span data-ttu-id="f20da-154">DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS 會更新 **suspect_pages** 資料表，以指出它所取消配置或修復的每個頁面。</span><span class="sxs-lookup"><span data-stu-id="f20da-154">DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS updates the **suspect_pages** table to indicate each page that it has deallocated or repaired.</span></span>  
  
    -   <span data-ttu-id="f20da-155">完整、檔案或分頁 RESTORE 會將頁面項目標示為已還原。</span><span class="sxs-lookup"><span data-stu-id="f20da-155">A full, file, or page RESTORE marks the page entries as restored.</span></span>  
  
     <span data-ttu-id="f20da-156">下列動作會從 **suspect_pages** 資料表自動刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="f20da-156">The following actions automatically delete rows from the **suspect_pages** table.</span></span>  
  
    -   <span data-ttu-id="f20da-157">ALTER DATABASE REMOVE FILE</span><span class="sxs-lookup"><span data-stu-id="f20da-157">ALTER DATABASE REMOVE FILE</span></span>  
  
    -   <span data-ttu-id="f20da-158">DROP DATABASE</span><span class="sxs-lookup"><span data-stu-id="f20da-158">DROP DATABASE</span></span>  
  
-   <span data-ttu-id="f20da-159">**資料庫管理員的維護角色**</span><span class="sxs-lookup"><span data-stu-id="f20da-159">**Maintenance Role of the Database Administrator**</span></span>  
  
     <span data-ttu-id="f20da-160">資料庫管理員負責管理資料表，主要是刪除舊的資料列。</span><span class="sxs-lookup"><span data-stu-id="f20da-160">Database administrators are responsible for managing the table, primarily by deleting old rows.</span></span> <span data-ttu-id="f20da-161">**suspect_pages** 資料表有大小限制，而且如果該資料表已滿，則不會記錄新的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f20da-161">The **suspect_pages** table is limited in size, and if it fills, new errors are not logged.</span></span> <span data-ttu-id="f20da-162">為了避免這個資料表被填滿，資料庫管理員或系統管理員必須手動刪除資料列，以清除這個資料表中的舊項目。</span><span class="sxs-lookup"><span data-stu-id="f20da-162">To prevent this table from filling up, the database administrator or system administrator must manually clear out old entries from this table by deleting rows.</span></span> <span data-ttu-id="f20da-163">建議您定期刪除或封存包含還原或修復而來之 **event_type** 的資料列，或包含舊 **last_update** 值的資料列。</span><span class="sxs-lookup"><span data-stu-id="f20da-163">Therefore, we recommend that you periodically delete or archive rows that have an **event_type** of restored or repaired, or rows that have an old **last_update** value.</span></span>  
  
     <span data-ttu-id="f20da-164">若要監視 suspect_pages 資料表上的活動，您可以使用 [Database Suspect Data Page 事件類別](../event-classes/database-suspect-data-page-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="f20da-164">To monitor the activity on the suspect_pages table, you can use the [Database Suspect Data Page Event Class](../event-classes/database-suspect-data-page-event-class.md).</span></span> <span data-ttu-id="f20da-165">資料列有時會因為暫時性錯誤而加入 **suspect_pages** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="f20da-165">Rows are sometimes added to the **suspect_pages** table because of transient errors.</span></span> <span data-ttu-id="f20da-166">但是，如果有許多資料列加入此資料表，則可能意味著 I/O 子系統發生問題。</span><span class="sxs-lookup"><span data-stu-id="f20da-166">If many rows are being added to the table, however, a problem probably exists with the I/O subsystem.</span></span> <span data-ttu-id="f20da-167">如果您注意到突然有許多資料列加入到此資料表，我們建議您最好調查 I/O 子系統是否有問題。</span><span class="sxs-lookup"><span data-stu-id="f20da-167">If you notice a sudden increase in the number of rows being added to the table, we recommend that you investigate possible problems in your I/O subsystem.</span></span>  
  
     <span data-ttu-id="f20da-168">資料庫管理員也可以插入或更新記錄。</span><span class="sxs-lookup"><span data-stu-id="f20da-168">A database administrator can also insert or update records.</span></span> <span data-ttu-id="f20da-169">例如，如果資料庫管理員知道某個疑問頁面其實沒問題，但想要保留記錄一段時間，則更新資料列會很有用。</span><span class="sxs-lookup"><span data-stu-id="f20da-169">For example, updating a row might useful when the database administrator knows that a particular suspect page is actually intact, but wants to preserve the record for a while.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f20da-170">Security</span><span class="sxs-lookup"><span data-stu-id="f20da-170">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f20da-171">權限</span><span class="sxs-lookup"><span data-stu-id="f20da-171">Permissions</span></span>  
 <span data-ttu-id="f20da-172">任何可以存取 **msdb** 的人員，均能讀取 **suspect_pages** 資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="f20da-172">Anyone with access to **msdb** can read the data in the **suspect_pages** table.</span></span> <span data-ttu-id="f20da-173">針對 suspect_pages 資料表擁有 UPDATE 權限的任何人都可以更新其記錄。</span><span class="sxs-lookup"><span data-stu-id="f20da-173">Anyone with UPDATE permission on the suspect_pages table can update its records.</span></span> <span data-ttu-id="f20da-174">**msdb** 上 **db_owner** 固定資料庫角色的成員或 **系統管理員** 固定伺服器角色的成員皆可插入、更新及刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="f20da-174">Members the **db_owner** fixed database role on **msdb** or the **sysadmin** fixed server role can insert, update, and delete records.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f20da-175">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f20da-175">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-manage-the-suspect_pages-table"></a><span data-ttu-id="f20da-176">若要管理 suspect_pages 資料表</span><span class="sxs-lookup"><span data-stu-id="f20da-176">To manage the suspect_pages table</span></span>  
  
1.  <span data-ttu-id="f20da-177">在 [物件總管]  中，連接到 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]的執行個體，展開該執行個體，然後展開 [資料庫]  。</span><span class="sxs-lookup"><span data-stu-id="f20da-177">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="f20da-178">依序展開 [系統資料庫]  、[msdb]  、[資料表]  和 [系統資料表]  。</span><span class="sxs-lookup"><span data-stu-id="f20da-178">Expand **System Databases**, expand **msdb**, expand **Tables**, and then expand **System Tables**.</span></span>  
  
3.  <span data-ttu-id="f20da-179">展開 **dbo.suspect_pages** ，然後以滑鼠右鍵按一下 [編輯前 200 個資料列]  。</span><span class="sxs-lookup"><span data-stu-id="f20da-179">Expand **dbo.suspect_pages** and right-click **Edit Top 200 Rows**.</span></span>  
  
4.  <span data-ttu-id="f20da-180">在查詢視窗中，編輯、更新或刪除所要的資料列。</span><span class="sxs-lookup"><span data-stu-id="f20da-180">In the query window, edit, update, or delete the rows that you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f20da-181">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f20da-181">Using Transact-SQL</span></span>  
  
#### <a name="to-manage-the-suspect_pages-table"></a><span data-ttu-id="f20da-182">若要管理 suspect_pages 資料表</span><span class="sxs-lookup"><span data-stu-id="f20da-182">To manage the suspect_pages table</span></span>  
  
1.  <span data-ttu-id="f20da-183">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f20da-183">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f20da-184">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f20da-184">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f20da-185">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f20da-185">Copy and paste the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="f20da-186">這個範例會刪除 `suspect_pages` 資料表中的部分資料列。</span><span class="sxs-lookup"><span data-stu-id="f20da-186">This example deletes some of the rows from the `suspect_pages` table.</span></span>  
  
```  
-- Delete restored, repaired, or deallocated pages.  
DELETE FROM msdb..suspect_pages  
   WHERE (event_type = 4 OR event_type = 5 OR event_type = 7);  
GO  
  
```  
  
 <span data-ttu-id="f20da-187">這個範例會傳回 `suspect_pages` 資料表中的錯誤頁面。</span><span class="sxs-lookup"><span data-stu-id="f20da-187">This example returns the bad pages in the `suspect_pages` table.</span></span>  
  
```  
-- Select nonspecific 824, bad checksum, and torn page errors.  
SELECT * FROM msdb..suspect_pages  
   WHERE (event_type = 1 OR event_type = 2 OR event_type = 3);  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="f20da-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f20da-188">See Also</span></span>  
 <span data-ttu-id="f20da-189">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f20da-189">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span></span>  
 <span data-ttu-id="f20da-190">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f20da-190">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="f20da-191">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f20da-191">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="f20da-192">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f20da-192">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span></span>  
 <span data-ttu-id="f20da-193">[還原頁面 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f20da-193">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="f20da-194">[suspect_pages &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f20da-194">[suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql) </span></span>  
 <span data-ttu-id="f20da-195">[MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="f20da-195">[MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md) </span></span>  
 [<span data-ttu-id="f20da-196">MSSQLSERVER_824</span><span class="sxs-lookup"><span data-stu-id="f20da-196">MSSQLSERVER_824</span></span>](../errors-events/mssqlserver-824-database-engine-error.md)  
  
  
