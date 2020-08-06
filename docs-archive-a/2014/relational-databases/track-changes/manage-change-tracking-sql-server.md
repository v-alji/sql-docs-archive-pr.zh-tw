---
title: 管理變更追蹤 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tracking data changes [SQL Server]
- change tracking [SQL Server], overhead
- change tracking [SQL Server]
- change tracking [SQL Server], managing
ms.assetid: 94a8d361-e897-4d6d-9a8f-1bb652e7a850
author: rothja
ms.author: jroth
ms.openlocfilehash: 36409f2ce256325da1c9849e5bec7e7ce114cf25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595861"
---
# <a name="manage-change-tracking-sql-server"></a><span data-ttu-id="45db3-102">管理變更追蹤 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="45db3-102">Manage Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="45db3-103">本主題描述如何管理變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="45db3-103">This topic describes how to manage change tracking.</span></span> <span data-ttu-id="45db3-104">此外，本主題也會描述如何設定安全性，以及判斷使用變更追蹤對儲存和效能產生的影響。</span><span class="sxs-lookup"><span data-stu-id="45db3-104">It also describes how to configure security and determine the effects on storage and performance when change tracking is used.</span></span>  
  
## <a name="managing-change-tracking"></a><span data-ttu-id="45db3-105">管理變更追縱</span><span class="sxs-lookup"><span data-stu-id="45db3-105">Managing Change Tracking</span></span>  
 <span data-ttu-id="45db3-106">下列各節將列出與管理變更追蹤有關的目錄檢視、權限和設定。</span><span class="sxs-lookup"><span data-stu-id="45db3-106">The following sections list catalog views, permissions, and settings that are relevant for managing change tracking.</span></span>  
  
### <a name="catalog-views"></a><span data-ttu-id="45db3-107">目錄檢視</span><span class="sxs-lookup"><span data-stu-id="45db3-107">Catalog Views</span></span>  
 <span data-ttu-id="45db3-108">若要判斷哪些資料表和資料庫已啟用變更追蹤，您可以使用下列目錄檢視：</span><span class="sxs-lookup"><span data-stu-id="45db3-108">To determine which tables and databases have change tracking enabled, you can use the following catalog views:</span></span>  
  
-   [<span data-ttu-id="45db3-109">sys.change_tracking_databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="45db3-109">sys.change_tracking_databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases)  
  
-   [<span data-ttu-id="45db3-110">sys.change_tracking_tables &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="45db3-110">sys.change_tracking_tables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables)  
  
 <span data-ttu-id="45db3-111">此外，當針對使用者資料表啟用變更追蹤時， [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) 目錄檢視也會列出所建立的內部資料表。</span><span class="sxs-lookup"><span data-stu-id="45db3-111">Also, the [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) catalog view lists the internal tables that are created when change tracking is enabled for a user table.</span></span>  
  
### <a name="security"></a><span data-ttu-id="45db3-112">安全性</span><span class="sxs-lookup"><span data-stu-id="45db3-112">Security</span></span>  
 <span data-ttu-id="45db3-113">若要使用 [變更追蹤函數](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql)來存取變更追蹤資訊，主體必須具有以下權限：</span><span class="sxs-lookup"><span data-stu-id="45db3-113">To access change tracking information by using the [change tracking functions](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql), the principal must have the following permissions:</span></span>  
  
-   <span data-ttu-id="45db3-114">在所查詢的資料表上，變更追蹤資料表上至少具有主索引鍵資料行的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="45db3-114">SELECT permission on at least the primary key columns on the change-tracked table to the table that is being queried.</span></span>  
  
-   <span data-ttu-id="45db3-115">要取得變更之資料表上的 VIEW CHANGE TRACKING 權限。</span><span class="sxs-lookup"><span data-stu-id="45db3-115">VIEW CHANGE TRACKING permission on the table for which changes are being obtained.</span></span> <span data-ttu-id="45db3-116">需要 VIEW CHANGE TRACKING 權限的原因如下：</span><span class="sxs-lookup"><span data-stu-id="45db3-116">The VIEW CHANGE TRACKING permission is required for the following reasons:</span></span>  
  
    -   <span data-ttu-id="45db3-117">變更追蹤記錄包含已刪除之資料列的相關資訊，特別是已刪除之資料列的主索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="45db3-117">Change tracking records include information about rows that have been deleted, specifically the primary key values of the rows that have been deleted.</span></span> <span data-ttu-id="45db3-118">在刪除某些敏感性資料之後，主體可能已經被授與變更追蹤資料表的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="45db3-118">A principal could have been granted SELECT permission for a change tracked table after some sensitive data had been deleted.</span></span> <span data-ttu-id="45db3-119">在此情況下，您不想讓該主體能夠使用變更追蹤來存取已刪除的資訊。</span><span class="sxs-lookup"><span data-stu-id="45db3-119">In this case, you would not want that principal to be able to access that deleted information by using change tracking.</span></span>  
  
    -   <span data-ttu-id="45db3-120">變更追蹤資訊可儲存有關更新作業已變更哪些資料行的資訊。</span><span class="sxs-lookup"><span data-stu-id="45db3-120">Change tracking information can store information about which columns have been changed by update operations.</span></span> <span data-ttu-id="45db3-121">當資料行包含敏感性資訊時，可能會拒絕主體對此資料行的存取權限。</span><span class="sxs-lookup"><span data-stu-id="45db3-121">A principal could be denied permission to a column that contains sensitive information.</span></span> <span data-ttu-id="45db3-122">不過，由於可使用變更追蹤資訊，所以主體可以判斷資料行值已經更新，但是主體無法判斷此資料行的值。</span><span class="sxs-lookup"><span data-stu-id="45db3-122">However, because change tracking information is available, a principal can determine that a column value has been updated, but the principal cannot determine the value of the column.</span></span>  
  
## <a name="understanding-change-tracking-overhead"></a><span data-ttu-id="45db3-123">了解變更追蹤負擔</span><span class="sxs-lookup"><span data-stu-id="45db3-123">Understanding Change Tracking Overhead</span></span>  
 <span data-ttu-id="45db3-124">在針對資料表啟用變更追蹤時，某些管理作業會受到影響。</span><span class="sxs-lookup"><span data-stu-id="45db3-124">When change tracking is enabled for a table, some administration operations are affected.</span></span> <span data-ttu-id="45db3-125">下表將列出這些作業以及您應該考量的影響。</span><span class="sxs-lookup"><span data-stu-id="45db3-125">The following table lists the operations and the effects you should consider.</span></span>  
  
|<span data-ttu-id="45db3-126">作業</span><span class="sxs-lookup"><span data-stu-id="45db3-126">Operation</span></span>|<span data-ttu-id="45db3-127">啟用變更追蹤時</span><span class="sxs-lookup"><span data-stu-id="45db3-127">When change tracking is enabled</span></span>|  
|---------------|-------------------------------------|  
|<span data-ttu-id="45db3-128">DROP TABLE</span><span class="sxs-lookup"><span data-stu-id="45db3-128">DROP TABLE</span></span>|<span data-ttu-id="45db3-129">針對卸除的資料表移除了所有變更追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="45db3-129">All change tracking information for the dropped table is removed.</span></span>|  
|<span data-ttu-id="45db3-130">ALTER TABLE DROP CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="45db3-130">ALTER TABLE DROP CONSTRAINT</span></span>|<span data-ttu-id="45db3-131">嘗試卸除 PRIMARY KEY 條件約束但卻失敗。</span><span class="sxs-lookup"><span data-stu-id="45db3-131">An attempt to drop the PRIMARY KEY constraint will fail.</span></span> <span data-ttu-id="45db3-132">在可以卸除 PRIMARY KEY 條件約束之前，必須先停用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="45db3-132">Change tracking must be disabled before a PRIMARY KEY constraint can be dropped.</span></span>|  
|<span data-ttu-id="45db3-133">ALTER TABLE DROP COLUMN</span><span class="sxs-lookup"><span data-stu-id="45db3-133">ALTER TABLE DROP COLUMN</span></span>|<span data-ttu-id="45db3-134">如果所卸除的資料行屬於主索引鍵的一部分，則不允許卸除此資料行 (與變更追蹤無關)。</span><span class="sxs-lookup"><span data-stu-id="45db3-134">If a column that is being dropped is part of the primary key, dropping the column is not allowed, regardless of change tracking.</span></span><br /><br /> <span data-ttu-id="45db3-135">如果所卸除的資料行不屬於主索引鍵的一部分，則卸除此資料行將會成功。</span><span class="sxs-lookup"><span data-stu-id="45db3-135">If the column that is being dropped is not part of the primary key, dropping the column succeeds.</span></span> <span data-ttu-id="45db3-136">但是，應該要先了解對同步處理此資料之任何應用程式的影響。</span><span class="sxs-lookup"><span data-stu-id="45db3-136">However, the effect on any application that is synchronizing this data should be understood first.</span></span> <span data-ttu-id="45db3-137">如果已針對資料表啟用資料行變更追蹤，則仍然可能在變更追蹤資訊中傳回卸除的資料行。</span><span class="sxs-lookup"><span data-stu-id="45db3-137">If column change tracking is enabled for the table, the dropped column might still be returned as part of the change tracking information.</span></span> <span data-ttu-id="45db3-138">應用程式必須負責處理卸除的資料行。</span><span class="sxs-lookup"><span data-stu-id="45db3-138">It is the responsibility of the application to handle the dropped column.</span></span>|  
|<span data-ttu-id="45db3-139">ALTER TABLE ADD COLUMN</span><span class="sxs-lookup"><span data-stu-id="45db3-139">ALTER TABLE ADD COLUMN</span></span>|<span data-ttu-id="45db3-140">如果新的資料行加入至變更追蹤資料表，系統不會追蹤資料行的加入作業。</span><span class="sxs-lookup"><span data-stu-id="45db3-140">If a new column is added to the change tracked table, the addition of the column is not tracked.</span></span> <span data-ttu-id="45db3-141">系統只會追蹤對新資料行所做的更新和變更。</span><span class="sxs-lookup"><span data-stu-id="45db3-141">Only the updates and changes that are made to the new column are tracked.</span></span>|  
|<span data-ttu-id="45db3-142">ALTER TABLE ALTER COLUMN</span><span class="sxs-lookup"><span data-stu-id="45db3-142">ALTER TABLE ALTER COLUMN</span></span>|<span data-ttu-id="45db3-143">不會追蹤非主索引鍵資料行的資料類型變更。</span><span class="sxs-lookup"><span data-stu-id="45db3-143">Data type changes of a non-primary key columns are not tracked.</span></span>|  
|<span data-ttu-id="45db3-144">ALTER TABLE SWITCH</span><span class="sxs-lookup"><span data-stu-id="45db3-144">ALTER TABLE SWITCH</span></span>|<span data-ttu-id="45db3-145">如果其中一個或兩個資料表已啟用變更追蹤，則切換資料分割會失敗。</span><span class="sxs-lookup"><span data-stu-id="45db3-145">Switching a partition fails if one or both of the tables has change tracking enabled.</span></span>|  
|<span data-ttu-id="45db3-146">DROP INDEX 或 ALTER INDEX DISABLE</span><span class="sxs-lookup"><span data-stu-id="45db3-146">DROP INDEX, or ALTER INDEX DISABLE</span></span>|<span data-ttu-id="45db3-147">強制主索引鍵的索引無法加以卸除或停用。</span><span class="sxs-lookup"><span data-stu-id="45db3-147">The index that enforces the primary key cannot be dropped or disabled.</span></span>|  
|<span data-ttu-id="45db3-148">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="45db3-148">TRUNCATE TABLE</span></span>|<span data-ttu-id="45db3-149">截斷資料表的作業可以在已啟用變更追蹤的資料表上執行。</span><span class="sxs-lookup"><span data-stu-id="45db3-149">Truncating a table can be performed on a table that has change tracking enabled.</span></span> <span data-ttu-id="45db3-150">但是，不會追蹤此作業所刪除的資料列，而且會更新最小的有效版本。</span><span class="sxs-lookup"><span data-stu-id="45db3-150">However, the rows that are deleted by the operation are not tracked, and the minimum valid version is updated.</span></span> <span data-ttu-id="45db3-151">當應用程式檢查它的版本時，這項檢查會指示此版本太舊，而且需要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="45db3-151">When an application checks its version, the check indicates that the version is too old and a reinitialization is required.</span></span> <span data-ttu-id="45db3-152">這與針對資料表停用變更追蹤然後重新啟用相同。</span><span class="sxs-lookup"><span data-stu-id="45db3-152">This is the same as change tracking being disabled, and then reenabled for the table.</span></span>|  
  
 <span data-ttu-id="45db3-153">使用變更追蹤並不會對 DML 作業造成額外負擔，因為變更追蹤資訊會儲存成作業的一部分。</span><span class="sxs-lookup"><span data-stu-id="45db3-153">Using change tracking does add some overhead to DML operations because of the change tracking information that is being stored as part of the operation.</span></span>  
  
### <a name="effects-on-dml"></a><span data-ttu-id="45db3-154">對 DML 的影響</span><span class="sxs-lookup"><span data-stu-id="45db3-154">Effects on DML</span></span>  
 <span data-ttu-id="45db3-155">變更追蹤已經最佳化，可讓 DML 作業的效能負擔降到最低。</span><span class="sxs-lookup"><span data-stu-id="45db3-155">Change tracking has been optimized to minimize the performance overhead on DML operations.</span></span> <span data-ttu-id="45db3-156">與在資料表上使用變更追蹤有關的累加效能負擔，類似於針對資料表建立索引而且需要進行維護時所產生的負擔。</span><span class="sxs-lookup"><span data-stu-id="45db3-156">The incremental performance overhead that is associated with using change tracking on a table is similar to the overhead incurred when an index is created for a table and needs to be maintained.</span></span>  
  
 <span data-ttu-id="45db3-157">對於 DML 作業變更的每一個資料列而言，會將一個資料列新增到內部變更追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="45db3-157">For each row that is changed by a DML operation, a row is added to the internal change tracking table.</span></span> <span data-ttu-id="45db3-158">這項作業 (相對於 DML 作業) 的影響取決於各種因素，如下列所示：</span><span class="sxs-lookup"><span data-stu-id="45db3-158">The effect of this relative to the DML operation depends on various factors, such as the following:</span></span>  
  
-   <span data-ttu-id="45db3-159">主索引鍵資料行的數目</span><span class="sxs-lookup"><span data-stu-id="45db3-159">The number of primary key columns</span></span>  
  
-   <span data-ttu-id="45db3-160">在使用者資料表資料列中變更的資料數量</span><span class="sxs-lookup"><span data-stu-id="45db3-160">The amount of data that is being changed in the user table row</span></span>  
  
-   <span data-ttu-id="45db3-161">在交易中執行的作業數目</span><span class="sxs-lookup"><span data-stu-id="45db3-161">The number of operations that are being performed in a transaction</span></span>  
  
 <span data-ttu-id="45db3-162">如果您使用了快照隔離，它也會影響所有 DML 作業的效能 (不論是否啟用變更追蹤)。</span><span class="sxs-lookup"><span data-stu-id="45db3-162">Snapshot isolation, if used, also has an effect on performance for all DML operations, whether change tracking is enabled or not.</span></span>  
  
### <a name="effects-on-storage"></a><span data-ttu-id="45db3-163">對儲存的影響</span><span class="sxs-lookup"><span data-stu-id="45db3-163">Effects on Storage</span></span>  
 <span data-ttu-id="45db3-164">變更追蹤資料會儲存在下列內部資料表類型中：</span><span class="sxs-lookup"><span data-stu-id="45db3-164">Change tracking data is stored in the following types of internal tables:</span></span>  
  
-   <span data-ttu-id="45db3-165">內部變更資料表</span><span class="sxs-lookup"><span data-stu-id="45db3-165">Internal change table</span></span>  
  
     <span data-ttu-id="45db3-166">啟用變更追蹤的每個使用者資料表都會有一個內部變更資料表。</span><span class="sxs-lookup"><span data-stu-id="45db3-166">There is one internal change table for each user table that has change tracking enabled.</span></span>  
  
-   <span data-ttu-id="45db3-167">內部交易資料表</span><span class="sxs-lookup"><span data-stu-id="45db3-167">Internal transaction table</span></span>  
  
     <span data-ttu-id="45db3-168">每個資料庫都有一個內部交易資料表。</span><span class="sxs-lookup"><span data-stu-id="45db3-168">There is one internal transaction table for the database.</span></span>  
  
 <span data-ttu-id="45db3-169">這些內部資料表會以下列方式來影響儲存需求：</span><span class="sxs-lookup"><span data-stu-id="45db3-169">These internal tables affect storage requirements in the following ways:</span></span>  
  
-   <span data-ttu-id="45db3-170">對於使用者資料表內每一個資料列的每一項變更而言，會將一個資料列新增到內部變更資料表。</span><span class="sxs-lookup"><span data-stu-id="45db3-170">For each change to each row in the user table, a row is added to the internal change table.</span></span> <span data-ttu-id="45db3-171">這個資料列有少量固定的負擔，再加上等於主索引鍵資料行大小的變動負擔。</span><span class="sxs-lookup"><span data-stu-id="45db3-171">This row has a small fixed overhead plus a variable overhead equal to the size of the primary key columns.</span></span> <span data-ttu-id="45db3-172">此資料列可以包含應用程式所設定的選擇性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="45db3-172">The row can contain optional context information set by an application.</span></span> <span data-ttu-id="45db3-173">此外，如果啟用了資料行追蹤，則每一個變更的資料行在追蹤資料表內都需要 4 個位元組。</span><span class="sxs-lookup"><span data-stu-id="45db3-173">And, if column tracking is enabled, each changed column requires 4 bytes in the tracking table.</span></span>  
  
-   <span data-ttu-id="45db3-174">針對每個認可的交易，內部交易資料表都會加入一個資料列。</span><span class="sxs-lookup"><span data-stu-id="45db3-174">For each committed transaction, a row is added to an internal transaction table.</span></span>  
  
 <span data-ttu-id="45db3-175">如果是其他內部資料表，您可以使用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 預存程序來判斷用於變更追蹤資料表的空間。</span><span class="sxs-lookup"><span data-stu-id="45db3-175">As with other internal tables, you can determine the space used for the change tracking tables by using the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) stored procedure.</span></span> <span data-ttu-id="45db3-176">您可以使用 [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) 目錄檢視來取得內部資料表的名稱，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="45db3-176">The names of the internal tables can be obtained by using the [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) catalog view, as shown in the following example.</span></span>  
  
```sql  
sp_spaceused 'sys.change_tracking_309576141'  
sp_spaceused 'sys.syscommittab'  
```  
  
## <a name="see-also"></a><span data-ttu-id="45db3-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45db3-177">See Also</span></span>  
 <span data-ttu-id="45db3-178">[追蹤資料變更 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="45db3-178">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="45db3-179">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="45db3-179">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="45db3-180">[資料庫屬性 &#40;變更追蹤頁面&#41;](../databases/database-properties-changetracking-page.md) </span><span class="sxs-lookup"><span data-stu-id="45db3-180">[Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) </span></span>  
 <span data-ttu-id="45db3-181">[ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="45db3-181">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="45db3-182">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span><span class="sxs-lookup"><span data-stu-id="45db3-182">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span></span>  
 <span data-ttu-id="45db3-183">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span><span class="sxs-lookup"><span data-stu-id="45db3-183">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span></span>  
 <span data-ttu-id="45db3-184">[追蹤資料變更 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="45db3-184">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="45db3-185">[關於變更追蹤 &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="45db3-185">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 [<span data-ttu-id="45db3-186">使用異動資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="45db3-186">Work with Change Data &#40;SQL Server&#41;</span></span>](work-with-change-data-sql-server.md)  
  
  
