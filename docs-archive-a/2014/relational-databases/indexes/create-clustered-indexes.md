---
title: 建立叢集索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index creation [SQL Server], clustered indexes
- clustered indexes, creating
- clustered indexes, PRIMARY KEY constraint
- clustered indexes, UNIQUE constraint
- indexes [SQL Server], clustered
ms.assetid: 47148383-c2c7-4f08-a9e4-7016bf2d1d13
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 567ff9a01bd93323149168b9e3aa0f34d78aee39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594999"
---
# <a name="create-clustered-indexes"></a><span data-ttu-id="bc6df-102">建立叢集索引</span><span class="sxs-lookup"><span data-stu-id="bc6df-102">Create Clustered Indexes</span></span>
  <span data-ttu-id="bc6df-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的資料表上建立叢集索引。</span><span class="sxs-lookup"><span data-stu-id="bc6df-103">You can create clustered indexes on tables in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="bc6df-104">除了極少數的例外狀況之外，每個資料表都應該要有叢集索引。</span><span class="sxs-lookup"><span data-stu-id="bc6df-104">With few exceptions, every table should have a clustered index.</span></span> <span data-ttu-id="bc6df-105">除了可以改善查詢效能以外，叢集索引還能夠視需要加以重建或重新組織，以便控制資料表分散程度。</span><span class="sxs-lookup"><span data-stu-id="bc6df-105">Besides improving query performance, a clustered index can be rebuilt or reorganized on demand to control table fragmentation.</span></span> <span data-ttu-id="bc6df-106">檢視上也可以建立叢集索引。</span><span class="sxs-lookup"><span data-stu-id="bc6df-106">A clustered index can also be created on a view.</span></span> <span data-ttu-id="bc6df-107">(叢集索引是在 [叢集與非叢集索引說明](clustered-and-nonclustered-indexes-described.md)主題中進行定義。)</span><span class="sxs-lookup"><span data-stu-id="bc6df-107">(Clustered indexes are defined in the topic [Clustered and Nonclustered Indexes Described](clustered-and-nonclustered-indexes-described.md).)</span></span>  
  
 <span data-ttu-id="bc6df-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="bc6df-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bc6df-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="bc6df-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bc6df-110">一般實作</span><span class="sxs-lookup"><span data-stu-id="bc6df-110">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="bc6df-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="bc6df-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="bc6df-112">安全性</span><span class="sxs-lookup"><span data-stu-id="bc6df-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bc6df-113">**使用下列方法在資料表上建立叢集索引：**</span><span class="sxs-lookup"><span data-stu-id="bc6df-113">**To create a clustered index on a table, using:**</span></span>  
  
     [<span data-ttu-id="bc6df-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bc6df-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bc6df-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bc6df-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bc6df-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="bc6df-116">Before You Begin</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="bc6df-117">一般實作</span><span class="sxs-lookup"><span data-stu-id="bc6df-117">Typical Implementations</span></span>  
 <span data-ttu-id="bc6df-118">實作叢集索引的方法如下：</span><span class="sxs-lookup"><span data-stu-id="bc6df-118">Clustered indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="bc6df-119">**PRIMARY KEY 與 UNIQUE 條件約束**</span><span class="sxs-lookup"><span data-stu-id="bc6df-119">**PRIMARY KEY and UNIQUE constraints**</span></span>  
  
     <span data-ttu-id="bc6df-120">建立 PRIMARY KEY 條件約束時，若資料表上沒有存在叢集索引，而且您未指定唯一的非叢集索引，則資料行上會自動建立唯一的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="bc6df-120">When you create a PRIMARY KEY constraint, a unique clustered index on the column or columns is automatically created if a clustered index on the table does not already exist and you do not specify a unique nonclustered index.</span></span> <span data-ttu-id="bc6df-121">主索引鍵資料行不允許 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="bc6df-121">The primary key column cannot allow NULL values.</span></span>  
  
     <span data-ttu-id="bc6df-122">當您建立 UNIQUE 條件約束時，依預設會建立唯一的非叢集索引，以強制 UNIQUE 條件約束。</span><span class="sxs-lookup"><span data-stu-id="bc6df-122">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="bc6df-123">若資料表上還沒有叢集索引，您可以指定唯一叢集索引。</span><span class="sxs-lookup"><span data-stu-id="bc6df-123">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span>  
  
     <span data-ttu-id="bc6df-124">隨條件約束一起建立的索引，會自動採用與條件約束名稱相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="bc6df-124">An index created as part of the constraint is automatically given the same name as the constraint name.</span></span> <span data-ttu-id="bc6df-125">如需相關資訊，請參閱 [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) 及 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="bc6df-125">For more information, see [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) and [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
-   <span data-ttu-id="bc6df-126">**獨立於條件限制之外的索引**</span><span class="sxs-lookup"><span data-stu-id="bc6df-126">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="bc6df-127">如果已指定非叢集的主索引鍵條件約束，您可以在主索引鍵資料行以外的資料行上建立叢集索引。</span><span class="sxs-lookup"><span data-stu-id="bc6df-127">You can create a clustered index on a column other than primary key column if a nonclustered primary key constraint was specified.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bc6df-128">限制事項</span><span class="sxs-lookup"><span data-stu-id="bc6df-128">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="bc6df-129">建立叢集索引結構時，個別的檔案和檔案群組中都必須有磁碟空間來保存舊 (來源) 結構和新 (目標) 結構。</span><span class="sxs-lookup"><span data-stu-id="bc6df-129">When a clustered index structure is created, disk space for both the old (source) and new (target) structures is required in their respective files and filegroups.</span></span> <span data-ttu-id="bc6df-130">除非認可整個交易，否則舊結構的配置不會取消。</span><span class="sxs-lookup"><span data-stu-id="bc6df-130">The old structure is not deallocated until the complete transaction commits.</span></span> <span data-ttu-id="bc6df-131">此外，可能還需要額外的暫存磁碟空間以供排序之用。</span><span class="sxs-lookup"><span data-stu-id="bc6df-131">Additional temporary disk space for sorting may also be required.</span></span> <span data-ttu-id="bc6df-132">如需詳細資訊，請參閱 [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="bc6df-132">For more information, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
-   <span data-ttu-id="bc6df-133">若叢集的索引建立於含多個現有非叢集索引的堆積上，所有的非叢集索引都必須重建，以便讓它們包含叢集索引鍵值，而非資料列識別碼 (RID)。</span><span class="sxs-lookup"><span data-stu-id="bc6df-133">If a clustered index is created on a heap with several existing nonclustered indexes, all the nonclustered indexes must be rebuilt so that they contain the clustering key value instead of the row identifier (RID).</span></span> <span data-ttu-id="bc6df-134">同樣地，若擁有多個非叢集索引之資料表上的叢集索引被卸除了，非叢集索引將會全部重建，做為 DROP 作業的一部份。</span><span class="sxs-lookup"><span data-stu-id="bc6df-134">Similarly, if a clustered index is dropped on a table that has several nonclustered indexes, the nonclustered indexes are all rebuilt as part of the DROP operation.</span></span> <span data-ttu-id="bc6df-135">在大型資料表中，這可能會花許多時間。</span><span class="sxs-lookup"><span data-stu-id="bc6df-135">This may take significant time on large tables.</span></span>  
  
     <span data-ttu-id="bc6df-136">在大型資料表上建立索引的較佳方式是以叢集索引開始，然後建立任何非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="bc6df-136">The preferred way to build indexes on large tables is to start with the clustered index and then build any nonclustered indexes.</span></span> <span data-ttu-id="bc6df-137">當您在現有資料表上建立索引時，請考慮將 ONLINE 選項設定為 ON。</span><span class="sxs-lookup"><span data-stu-id="bc6df-137">Consider setting the ONLINE option to ON when you create indexes on existing tables.</span></span> <span data-ttu-id="bc6df-138">設定為 ON 時，將不會長期鎖定資料表。</span><span class="sxs-lookup"><span data-stu-id="bc6df-138">When set to ON, long-term table locks are not held.</span></span> <span data-ttu-id="bc6df-139">這樣一來，基礎資料表上就可以繼續執行查詢或更新動作。</span><span class="sxs-lookup"><span data-stu-id="bc6df-139">This enables queries or updates to the underlying table to continue.</span></span> <span data-ttu-id="bc6df-140">如需詳細資訊，請參閱 [Perform Index Operations Online](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="bc6df-140">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
-   <span data-ttu-id="bc6df-141">叢集索引的索引鍵所包含的 `varchar` 資料行不能在 ROW_OVERFLOW_DATA 配置單位中有現有的資料。</span><span class="sxs-lookup"><span data-stu-id="bc6df-141">The index key of a clustered index cannot contain `varchar` columns that have existing data in the ROW_OVERFLOW_DATA allocation unit.</span></span> <span data-ttu-id="bc6df-142">如果在 `varchar` 資料行上建立叢集索引，且現有的資料在 IN_ROW_DATA 配置單位中，則後續在可能發送資料非資料列的資料行上進行的插入或更新動作會失敗。</span><span class="sxs-lookup"><span data-stu-id="bc6df-142">If a clustered index is created on a `varchar` column and the existing data is in the IN_ROW_DATA allocation unit, subsequent insert or update actions on the column that would push the data off-row will fail.</span></span> <span data-ttu-id="bc6df-143">若要取得可能包含資料列溢位資料之資料表的相關資訊，請使用 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) 動態管理函數。</span><span class="sxs-lookup"><span data-stu-id="bc6df-143">To obtain information about tables that might contain row-overflow data, use the [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) dynamic management function.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bc6df-144">Security</span><span class="sxs-lookup"><span data-stu-id="bc6df-144">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bc6df-145">權限</span><span class="sxs-lookup"><span data-stu-id="bc6df-145">Permissions</span></span>  
 <span data-ttu-id="bc6df-146">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="bc6df-146">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="bc6df-147">使用者必須是 **系統管理員** 固定伺服器角色的成員，或是 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="bc6df-147">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bc6df-148">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bc6df-148">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-clustered-index-by-using-object-explorer"></a><span data-ttu-id="bc6df-149">若要使用物件總管建立叢集索引</span><span class="sxs-lookup"><span data-stu-id="bc6df-149">To create a clustered index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="bc6df-150">在 [物件總管] 中，展開要在其中建立叢集索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="bc6df-150">In Object Explorer, expand the table on which you want to create a clustered index.</span></span>  
  
2.  <span data-ttu-id="bc6df-151">以滑鼠右鍵按一下 [索引]  資料夾，指向 [新增索引]  ，然後選取 [叢集索引…]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-151">Right-click the **Indexes** folder, point to **New Index**, and select **Clustered Index...**.</span></span>  
  
3.  <span data-ttu-id="bc6df-152">在 **[新增索引]** 對話方塊，於 **[一般]** 頁面上的 **[索引名稱]** 方塊中輸入新索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="bc6df-152">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
4.  <span data-ttu-id="bc6df-153">按一下 [索引鍵資料行]  下的 [新增...]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-153">Under **Index key columns**, click **Add...**.</span></span>  
  
5.  <span data-ttu-id="bc6df-154">在 [**從**_Table_name_選取資料行] 對話方塊中，選取要加入至叢集索引之資料表資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bc6df-154">In the **Select Columns from**_table_name_ dialog box, select the check box of the table column to be added to the clustered index.</span></span>  
  
6.  <span data-ttu-id="bc6df-155">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-155">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="bc6df-156">在 **[新增索引]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="bc6df-156">In the **New Index** dialog box, click **OK**.</span></span>  
  
#### <a name="to-create-a-clustered-index-by-using-the-table-designer"></a><span data-ttu-id="bc6df-157">若要使用資料表設計工具建立叢集索引</span><span class="sxs-lookup"><span data-stu-id="bc6df-157">To create a clustered index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="bc6df-158">在 [物件總管] 中，展開要在其中建立包含叢集索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="bc6df-158">In Object Explorer, expand the database on which you want to create a table with a clustered index.</span></span>  
  
2.  <span data-ttu-id="bc6df-159">以滑鼠右鍵按一下 [資料表]  資料夾，然後按一下 [新增資料表…]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-159">Right-click the **Tables** folder and click **New Table...**.</span></span>  
  
3.  <span data-ttu-id="bc6df-160">像平常一樣，建立新資料表。</span><span class="sxs-lookup"><span data-stu-id="bc6df-160">Create a new table as you normally would.</span></span> <span data-ttu-id="bc6df-161">如需詳細資訊，請參閱[建立資料表 &#40;Database Engine&#41;](../tables/create-tables-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="bc6df-161">For more information, see [Create Tables &#40;Database Engine&#41;](../tables/create-tables-database-engine.md).</span></span>  
  
4.  <span data-ttu-id="bc6df-162">以滑鼠右鍵按一下上面建立的新資料表，然後按一下 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-162">Right-click the new table created above and click **Design**.</span></span>  
  
5.  <span data-ttu-id="bc6df-163">在 [資料表設計工具]  功能表上，按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-163">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
6.  <span data-ttu-id="bc6df-164">在 [索引/索引鍵]  對話方塊中，按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-164">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
7.  <span data-ttu-id="bc6df-165">從 [選取的主索引鍵/唯一索引鍵或索引]  文字方塊中選取新索引。</span><span class="sxs-lookup"><span data-stu-id="bc6df-165">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
8.  <span data-ttu-id="bc6df-166">在方格中，選取 [建立成 CLUSTERED]  ，然後從屬性右邊的下拉式清單中選擇 [是]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-166">In the grid, select **Create as Clustered**, and choose **Yes** from the drop-down list to the right of the property.</span></span>  
  
9. <span data-ttu-id="bc6df-167">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="bc6df-167">Click **Close**.</span></span>  
  
10. <span data-ttu-id="bc6df-168">在 [檔案]\*\*\*\* 功能表上，按一下 [儲存 _資料表名稱_]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bc6df-168">On the **File** menu, click **Save**_table_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bc6df-169">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bc6df-169">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-clustered-index"></a><span data-ttu-id="bc6df-170">若要建立叢集索引</span><span class="sxs-lookup"><span data-stu-id="bc6df-170">To create a clustered index</span></span>  
  
1.  <span data-ttu-id="bc6df-171">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc6df-171">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bc6df-172">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="bc6df-172">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bc6df-173">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="bc6df-173">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Create a new table with three columns.  
    CREATE TABLE dbo.TestTable  
        (TestCol1 int NOT NULL,  
         TestCol2 nchar(10) NULL,  
         TestCol3 nvarchar(50) NULL);  
    GO  
    -- Create a clustered index called IX_TestTable_TestCol1  
    -- on the dbo.TestTable table using the TestCol1 column.  
    CREATE CLUSTERED INDEX IX_TestTable_TestCol1   
        ON dbo.TestTable (TestCol1);   
    GO  
    ```  
  
 <span data-ttu-id="bc6df-174">如需詳細資訊，請參閱 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bc6df-174">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6df-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc6df-175">See Also</span></span>  
 <span data-ttu-id="bc6df-176">[建立主索引鍵](../tables/create-primary-keys.md) </span><span class="sxs-lookup"><span data-stu-id="bc6df-176">[Create Primary Keys](../tables/create-primary-keys.md) </span></span>  
 [<span data-ttu-id="bc6df-177">建立唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="bc6df-177">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)  
  
  
