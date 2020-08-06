---
title: 停用索引和條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.disableindexes.f1
helpviewer_keywords:
- disabled indexes [SQL Server], index operations
- nonclustered indexes [SQL Server], disabling
- disabled indexes [SQL Server], guidelines
- clustered indexes, disabling
- constraints [SQL Server], disabling
- disabled indexes [SQL Server], viewing
- FOREIGN KEY constraints, disabling
- statistical information [SQL Server], indexes
- index disabling [SQL Server]
- indexed views [SQL Server], disabled indexes
ms.assetid: 2198f1af-fa44-47e9-92df-f4fde322ba18
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 40f9de4108be4defeb2353a9e7835c289641a819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708285"
---
# <a name="disable-indexes-and-constraints"></a><span data-ttu-id="05c3c-102">停用索引和條件約束</span><span class="sxs-lookup"><span data-stu-id="05c3c-102">Disable Indexes and Constraints</span></span>
  <span data-ttu-id="05c3c-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用索引或條件約束。</span><span class="sxs-lookup"><span data-stu-id="05c3c-103">This topic describes how to disable an index or constraints in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="05c3c-104">停用索引會防止使用者存取索引，而停用叢集索引則會防止存取基礎資料表資料。</span><span class="sxs-lookup"><span data-stu-id="05c3c-104">Disabling an index prevents user access to the index, and for clustered indexes to the underlying table data.</span></span> <span data-ttu-id="05c3c-105">索引定義會保留在中繼資料內，而索引統計資料會保留在非叢集索引上。</span><span class="sxs-lookup"><span data-stu-id="05c3c-105">The index definition remains in metadata, and index statistics are kept on nonclustered indexes.</span></span> <span data-ttu-id="05c3c-106">停用檢視上的非叢集或叢集索引，實際上會刪除索引資料。</span><span class="sxs-lookup"><span data-stu-id="05c3c-106">Disabling a nonclustered or clustered index on a view physically deletes the index data.</span></span> <span data-ttu-id="05c3c-107">停用資料表上的叢集索引，則會防止存取資料；這些資料仍留在資料表中，但無法用於資料操作語言 (DML) 作業，除非卸除或重建索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-107">Disabling a clustered index on a table prevents access to the data; the data still remains in the table, but is unavailable for data manipulation language (DML) operations until the index is dropped or rebuilt.</span></span>  
  
 <span data-ttu-id="05c3c-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="05c3c-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="05c3c-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="05c3c-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="05c3c-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="05c3c-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="05c3c-111">安全性</span><span class="sxs-lookup"><span data-stu-id="05c3c-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="05c3c-112">**使用下列方法停用索引：**</span><span class="sxs-lookup"><span data-stu-id="05c3c-112">**To disable an index, using:**</span></span>  
  
     [<span data-ttu-id="05c3c-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="05c3c-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="05c3c-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="05c3c-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="05c3c-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="05c3c-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="05c3c-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="05c3c-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="05c3c-117">索引停用時，不會進行維護。</span><span class="sxs-lookup"><span data-stu-id="05c3c-117">The index is not maintained while it is disabled.</span></span>  
  
-   <span data-ttu-id="05c3c-118">查詢最佳化工具在建立查詢執行計畫時，不會考慮停用的索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-118">The query optimizer does not consider the disabled index when creating query execution plans.</span></span> <span data-ttu-id="05c3c-119">此外，使用資料表提示來參考已停用索引的查詢會失敗。</span><span class="sxs-lookup"><span data-stu-id="05c3c-119">Also, queries that reference the disabled index with a table hint fail.</span></span>  
  
-   <span data-ttu-id="05c3c-120">您不能建立與現有停用之索引同名的索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-120">You cannot create an index that uses the same name as an existing disabled index.</span></span>  
  
-   <span data-ttu-id="05c3c-121">已停用的索引可將其卸除。</span><span class="sxs-lookup"><span data-stu-id="05c3c-121">A disabled index can be dropped.</span></span>  
  
-   <span data-ttu-id="05c3c-122">停用唯一索引時，PRIMARY KEY 或 UNIQUE 條件約束，以及從其他資料表參考索引資料行的所有 FOREIGN KEY 條件約束，也會被停用。</span><span class="sxs-lookup"><span data-stu-id="05c3c-122">When disabling a unique index, the PRIMARY KEY or UNIQUE constraint and all FOREIGN KEY constraints that reference the indexed columns from other tables are also disabled.</span></span> <span data-ttu-id="05c3c-123">停用叢集索引時，基礎資料表上的所有內送和外送 FOREIGN KEY 條件約束也會停用。</span><span class="sxs-lookup"><span data-stu-id="05c3c-123">When disabling a clustered index, all incoming and outgoing FOREIGN KEY constraints on the underlying table are also disabled.</span></span> <span data-ttu-id="05c3c-124">當索引停用時，會在警告訊息中列出條件約束名稱。</span><span class="sxs-lookup"><span data-stu-id="05c3c-124">The constraint names are listed in a warning message when the index is disabled.</span></span> <span data-ttu-id="05c3c-125">重建索引之後，必須使用 ALTER TABLE CHECK CONSTRAINT 陳述式來手動啟用所有條件約束。</span><span class="sxs-lookup"><span data-stu-id="05c3c-125">After rebuilding the index, all constraints must be manually enabled by using the ALTER TABLE CHECK CONSTRAINT statement.</span></span>  
  
-   <span data-ttu-id="05c3c-126">當關聯的叢集索引停用時，非叢集索引也會自動停用。</span><span class="sxs-lookup"><span data-stu-id="05c3c-126">Nonclustered indexes are automatically disabled when the associated clustered index is disabled.</span></span> <span data-ttu-id="05c3c-127">直到啟用資料表或檢視上的叢集索引，或卸除資料表上的叢集索引時，才可以啟用非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-127">They cannot be enabled until either the clustered index on the table or view is enabled or the clustered index on the table is dropped.</span></span> <span data-ttu-id="05c3c-128">除非已使用 ALTER INDEX ALL REBUILD 陳述式啟用叢集索引，否則必須以明確方式啟用非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-128">Nonclustered indexes must be explicitly enabled, unless the clustered index was enabled by using the ALTER INDEX ALL REBUILD statement.</span></span>  
  
-   <span data-ttu-id="05c3c-129">ALTER INDEX ALL REBUILD 陳述式會重建和啟用資料表上所有已停用的索引，除了檢視上的已停用索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-129">The ALTER INDEX ALL REBUILD statement rebuilds and enables all disabled indexes on the table, except for disabled indexes on views.</span></span> <span data-ttu-id="05c3c-130">檢視上的索引必須在個別的 ALTER INDEX ALL REBUILD 陳述式中啟用。</span><span class="sxs-lookup"><span data-stu-id="05c3c-130">Indexes on views must be enabled in a separate ALTER INDEX ALL REBUILD statement.</span></span>  
  
-   <span data-ttu-id="05c3c-131">停用資料表上的叢集索引，也會停用參考該資料表之檢視上的所有叢集和非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-131">Disabling a clustered index on a table also disables all clustered and nonclustered indexes on views that reference that table.</span></span> <span data-ttu-id="05c3c-132">這些索引與被參考資料表上的那些索引一樣，都必須重建。</span><span class="sxs-lookup"><span data-stu-id="05c3c-132">These indexes must be rebuilt just as those on the referenced table.</span></span>  
  
-   <span data-ttu-id="05c3c-133">除了用於卸除或重建叢集索引，否則無法存取已停用叢集索引的資料列。</span><span class="sxs-lookup"><span data-stu-id="05c3c-133">The data rows of the disabled clustered index cannot be accessed except to drop or rebuild the clustered index.</span></span>  
  
-   <span data-ttu-id="05c3c-134">當資料表沒有已停用的叢集索引時，您可以在線上重建已停用的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-134">You can rebuild a disabled nonclustered index online when the table does not have a disabled clustered index.</span></span> <span data-ttu-id="05c3c-135">然而，如果您使用 ALTER INDEX REBUILD 或 CREATE INDEX WITH DROP_EXISTING 陳述式，則一定要以離線方式重建已停用的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-135">However, you must always rebuild a disabled clustered index offline if you use either the ALTER INDEX REBUILD or CREATE INDEX WITH DROP_EXISTING statement.</span></span> <span data-ttu-id="05c3c-136">如需線上索引作業的詳細資訊，請參閱 [線上執行索引作業](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="05c3c-136">For more information about online index operations, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
-   <span data-ttu-id="05c3c-137">在已停用叢集索引的資料表上，CREATE STATISTICS 陳述式無法成功執行。</span><span class="sxs-lookup"><span data-stu-id="05c3c-137">The CREATE STATISTICS statement cannot be successfully executed on a table that has a disabled clustered index.</span></span>  
  
-   <span data-ttu-id="05c3c-138">當已停用索引，且符合下列情況時，AUTO_CREATE_STATISTICS 資料庫選項會在資料行上建立新的統計資料：</span><span class="sxs-lookup"><span data-stu-id="05c3c-138">The AUTO_CREATE_STATISTICS database option creates new statistics on a column when the index is disabled and the following conditions exist:</span></span>  
  
    -   <span data-ttu-id="05c3c-139">AUTO_CREATE_STATISTICS 設為 ON。</span><span class="sxs-lookup"><span data-stu-id="05c3c-139">AUTO_CREATE_STATISTICS is set to ON</span></span>  
  
    -   <span data-ttu-id="05c3c-140">該資料行沒有統計資料。</span><span class="sxs-lookup"><span data-stu-id="05c3c-140">There are no existing statistics for the column.</span></span>  
  
    -   <span data-ttu-id="05c3c-141">查詢最佳化期間需要統計資料。</span><span class="sxs-lookup"><span data-stu-id="05c3c-141">Statistics are required during query optimization.</span></span>  
  
-   <span data-ttu-id="05c3c-142">如果叢集索引已停用， [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 便無法傳回基礎資料表的相關資訊；相反地，陳述式會報告該叢集索引已停用。</span><span class="sxs-lookup"><span data-stu-id="05c3c-142">If a clustered index is disabled, [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) cannot return information about the underlying table; instead, the statement reports that the clustered index is disabled.</span></span> <span data-ttu-id="05c3c-143">[DBCC INDEXDEFRAG](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql) 不能用來重組已停用的索引：陳述式會失敗並出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="05c3c-143">[DBCC INDEXDEFRAG](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql) cannot be used to defragment a disabled index; the statement fails with an error message.</span></span> <span data-ttu-id="05c3c-144">您可以使用 [DBCC DBREINDEX](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) 來重建已停用的索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-144">You can use [DBCC DBREINDEX](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) to rebuild a disabled index.</span></span>  
  
-   <span data-ttu-id="05c3c-145">建立新的叢集索引可啟用先前停用的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-145">Creating a new clustered index enables previously disabled nonclustered indexes.</span></span> <span data-ttu-id="05c3c-146">如需詳細資訊，請參閱 [Enable Indexes and Constraints](enable-indexes-and-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="05c3c-146">For more information, see [Enable Indexes and Constraints](enable-indexes-and-constraints.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="05c3c-147">Security</span><span class="sxs-lookup"><span data-stu-id="05c3c-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="05c3c-148">權限</span><span class="sxs-lookup"><span data-stu-id="05c3c-148">Permissions</span></span>  
 <span data-ttu-id="05c3c-149">若要執行 ALTER INDEX，至少需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="05c3c-149">To execute ALTER INDEX, at a minimum, ALTER permission on the table or view is required.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="05c3c-150">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="05c3c-150">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-an-index"></a><span data-ttu-id="05c3c-151">若要停用索引</span><span class="sxs-lookup"><span data-stu-id="05c3c-151">To disable an index</span></span>  
  
1.  <span data-ttu-id="05c3c-152">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要停用索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="05c3c-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to disable an index.</span></span>  
  
2.  <span data-ttu-id="05c3c-153">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="05c3c-153">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="05c3c-154">按一下加號展開要停用索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="05c3c-154">Click the plus sign to expand the table on which you want to disable an index.</span></span>  
  
4.  <span data-ttu-id="05c3c-155">按一下加號展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="05c3c-155">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="05c3c-156">以滑鼠右鍵按一下您要停用的索引，然後選取 [停用]  。</span><span class="sxs-lookup"><span data-stu-id="05c3c-156">Right-click the index you want to disable and select **Disable**.</span></span>  
  
6.  <span data-ttu-id="05c3c-157">在 **[停用索引]** 對話方塊中，確認 **[要停用的索引]** 方格中有正確索引，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="05c3c-157">In the **Disable Indexes** dialog box, verify that the correct index is in the **Indexes to disable** grid and click **OK**.</span></span>  
  
#### <a name="to-disable-all-indexes-on-a-table"></a><span data-ttu-id="05c3c-158">停用資料表上的所有索引</span><span class="sxs-lookup"><span data-stu-id="05c3c-158">To disable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="05c3c-159">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要停用索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="05c3c-159">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to disable the indexes.</span></span>  
  
2.  <span data-ttu-id="05c3c-160">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="05c3c-160">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="05c3c-161">按一下加號展開要停用索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="05c3c-161">Click the plus sign to expand the table on which you want to disable the indexes.</span></span>  
  
4.  <span data-ttu-id="05c3c-162">以滑鼠右鍵按一下 [索引]  資料夾，並選取 [全部停用]  。</span><span class="sxs-lookup"><span data-stu-id="05c3c-162">Right-click the **Indexes** folder and select **Disable All**.</span></span>  
  
5.  <span data-ttu-id="05c3c-163">在 **[停用索引]** 對話方塊中，確認 **[要停用的索引]** 方格中有正確索引，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="05c3c-163">In the **Disable Indexes** dialog box, verify that the correct indexes are in the **Indexes to disable** grid and click **OK**.</span></span> <span data-ttu-id="05c3c-164">若要從 **[要停用的索引]** 方格中移除索引，請選取索引，然後按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="05c3c-164">To remove an index from the **Indexes to disable** grid, select the index and then press the Delete key.</span></span>  
  
 <span data-ttu-id="05c3c-165">**[停用索引]** 對話方塊中提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="05c3c-165">The following information is available in the **Disable Indexes** dialog box:</span></span>  
  
 <span data-ttu-id="05c3c-166">**Index Name**</span><span class="sxs-lookup"><span data-stu-id="05c3c-166">**Index Name**</span></span>  
 <span data-ttu-id="05c3c-167">顯示索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="05c3c-167">Displays the name of the index.</span></span> <span data-ttu-id="05c3c-168">在執行期間，此資料行也會顯示代表其狀態的圖示。</span><span class="sxs-lookup"><span data-stu-id="05c3c-168">During execution, this column also displays an icon representing the status.</span></span>  
  
 <span data-ttu-id="05c3c-169">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="05c3c-169">**Table Name**</span></span>  
 <span data-ttu-id="05c3c-170">顯示建立索引的資料表名稱或檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="05c3c-170">Displays the name of the table or view that the index was created on.</span></span>  
  
 <span data-ttu-id="05c3c-171">**索引類型**</span><span class="sxs-lookup"><span data-stu-id="05c3c-171">**Index Type**</span></span>  
 <span data-ttu-id="05c3c-172">顯示索引的類型：[叢集]  、[非叢集]  、[空間]  或 [XML]  。</span><span class="sxs-lookup"><span data-stu-id="05c3c-172">Displays the type of the index: **Clustered**, **Nonclustered**, **Spatial**, or **XML**.</span></span>  
  
 <span data-ttu-id="05c3c-173">**狀態**</span><span class="sxs-lookup"><span data-stu-id="05c3c-173">**Status**</span></span>  
 <span data-ttu-id="05c3c-174">顯示停用作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="05c3c-174">Displays the status of the disable operation.</span></span> <span data-ttu-id="05c3c-175">執行之後可能的值：</span><span class="sxs-lookup"><span data-stu-id="05c3c-175">Possible values after execution are:</span></span>  
  
-   <span data-ttu-id="05c3c-176">Blank</span><span class="sxs-lookup"><span data-stu-id="05c3c-176">Blank</span></span>  
  
     <span data-ttu-id="05c3c-177">執行之前 **[狀態]** 為空白。</span><span class="sxs-lookup"><span data-stu-id="05c3c-177">Prior to execution **Status** is blank.</span></span>  
  
-   <span data-ttu-id="05c3c-178">**進行中**</span><span class="sxs-lookup"><span data-stu-id="05c3c-178">**In progress**</span></span>  
  
     <span data-ttu-id="05c3c-179">已經開始停用索引，但尚未完成。</span><span class="sxs-lookup"><span data-stu-id="05c3c-179">Disabling of the indexes has been started but is not complete.</span></span>  
  
-   <span data-ttu-id="05c3c-180">「成功」 </span><span class="sxs-lookup"><span data-stu-id="05c3c-180">**Success**</span></span>  
  
     <span data-ttu-id="05c3c-181">已成功地完成停用作業。</span><span class="sxs-lookup"><span data-stu-id="05c3c-181">The disable operation completed successfully.</span></span>  
  
-   <span data-ttu-id="05c3c-182">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="05c3c-182">**Error**</span></span>  
  
     <span data-ttu-id="05c3c-183">停用索引作業期間發生錯誤，未成功地完成作業。</span><span class="sxs-lookup"><span data-stu-id="05c3c-183">An error was encountered during the index disable operation, and the operation did not complete successfully.</span></span>  
  
-   <span data-ttu-id="05c3c-184">**Stopped**</span><span class="sxs-lookup"><span data-stu-id="05c3c-184">**Stopped**</span></span>  
  
     <span data-ttu-id="05c3c-185">因為使用者停止作業，所以未成功地完成停用索引。</span><span class="sxs-lookup"><span data-stu-id="05c3c-185">The disable of the index was not completed successfully because the user stopped the operation.</span></span>  
  
 <span data-ttu-id="05c3c-186">**訊息**</span><span class="sxs-lookup"><span data-stu-id="05c3c-186">**Message**</span></span>  
 <span data-ttu-id="05c3c-187">提供停用作業期間錯誤訊息的文字。</span><span class="sxs-lookup"><span data-stu-id="05c3c-187">Provides the text of error messages during the disable operation.</span></span> <span data-ttu-id="05c3c-188">在執行期間，會以超連結顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="05c3c-188">During execution, errors appear as hyperlinks.</span></span> <span data-ttu-id="05c3c-189">超連結的文字會描述錯誤的主體。</span><span class="sxs-lookup"><span data-stu-id="05c3c-189">The text of the hyperlinks describes the body of the error.</span></span> <span data-ttu-id="05c3c-190">**[訊息]** 資料行通常寬度不足以讀取完整訊息文字。</span><span class="sxs-lookup"><span data-stu-id="05c3c-190">The **Message** column is rarely wide enough to read the full message text.</span></span> <span data-ttu-id="05c3c-191">取得完整文字有兩種方式：</span><span class="sxs-lookup"><span data-stu-id="05c3c-191">There are two ways to get the full text:</span></span>  
  
-   <span data-ttu-id="05c3c-192">將滑鼠指標移至訊息資料格上，即可顯示具有錯誤文字的工具提示。</span><span class="sxs-lookup"><span data-stu-id="05c3c-192">Move the mouse pointer over the message cell to display a ToolTip with the error text.</span></span>  
  
-   <span data-ttu-id="05c3c-193">按一下超連結即可顯示含有完整錯誤的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="05c3c-193">Click the hyperlink to display a dialog box displaying the full error.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="05c3c-194">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="05c3c-194">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-an-index"></a><span data-ttu-id="05c3c-195">若要停用索引</span><span class="sxs-lookup"><span data-stu-id="05c3c-195">To disable an index</span></span>  
  
1.  <span data-ttu-id="05c3c-196">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="05c3c-196">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="05c3c-197">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="05c3c-197">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="05c3c-198">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="05c3c-198">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- disables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    DISABLE;  
    ```  
  
#### <a name="to-disable-all-indexes-on-a-table"></a><span data-ttu-id="05c3c-199">停用資料表上的所有索引</span><span class="sxs-lookup"><span data-stu-id="05c3c-199">To disable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="05c3c-200">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="05c3c-200">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="05c3c-201">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="05c3c-201">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="05c3c-202">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="05c3c-202">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Disables all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    DISABLE;  
    ```  
  
 <span data-ttu-id="05c3c-203">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="05c3c-203">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
