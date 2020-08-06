---
title: 建立內含資料行的索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index size [SQL Server]
- index keys [SQL Server]
- index columns [SQL Server]
- size [SQL Server], indexes
- key columns [SQL Server]
- included columns
- nonclustered indexes [SQL Server], included columns
- designing indexes [SQL Server], included columns
- nonkey columns
ms.assetid: d198648d-fea5-416d-9f30-f9d4aebbf4ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e5a464f9791ea635236069555647229bf1f0d79e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708310"
---
# <a name="create-indexes-with-included-columns"></a><span data-ttu-id="1296c-102">建立內含資料行的索引</span><span class="sxs-lookup"><span data-stu-id="1296c-102">Create Indexes with Included Columns</span></span>
  <span data-ttu-id="1296c-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中加入內含 (或非索引鍵) 資料行，以擴充非叢集索引的功能。</span><span class="sxs-lookup"><span data-stu-id="1296c-103">This topic describes how to add included (or nonkey) columns to extend the functionality of nonclustered indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1296c-104">藉由加入非索引鍵資料行，您可以建立涵蓋更多查詢的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="1296c-104">By including nonkey columns, you can create nonclustered indexes that cover more queries.</span></span> <span data-ttu-id="1296c-105">這是因為非索引鍵之索引資料行有下列好處：</span><span class="sxs-lookup"><span data-stu-id="1296c-105">This is because the nonkey columns have the following benefits:</span></span>  
  
-   <span data-ttu-id="1296c-106">與索引鍵資料行一樣，它們可以是不允許的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1296c-106">They can be data types not allowed as index key columns.</span></span>  
  
-   <span data-ttu-id="1296c-107">計算索引鍵資料行數或索引鍵大小時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 不會考慮它們。</span><span class="sxs-lookup"><span data-stu-id="1296c-107">They are not considered by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] when calculating the number of index key columns or index key size.</span></span>  
  
 <span data-ttu-id="1296c-108">查詢中所有的資料行在索引中當做索引鍵或非索引鍵資料行時，非索引鍵資料行的索引可以大幅改進查詢效能。</span><span class="sxs-lookup"><span data-stu-id="1296c-108">An index with nonkey columns can significantly improve query performance when all columns in the query are included in the index either as key or nonkey columns.</span></span> <span data-ttu-id="1296c-109">因為查詢最佳化工具可以在索引中找到所有資料行值，所以可以提高效能；不存取資料表或叢集索引資料，導致磁碟 I/O 作業變少。</span><span class="sxs-lookup"><span data-stu-id="1296c-109">Performance gains are achieved because the query optimizer can locate all the column values within the index; table or clustered index data is not accessed resulting in fewer disk I/O operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1296c-110">索引包含查詢參考的所有資料行時，通常就是指「涵蓋查詢」。</span><span class="sxs-lookup"><span data-stu-id="1296c-110">When an index contains all the columns referenced by a query it is typically referred to as *covering the query*.</span></span>  
  
 <span data-ttu-id="1296c-111">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1296c-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1296c-112">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1296c-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1296c-113">設計建議</span><span class="sxs-lookup"><span data-stu-id="1296c-113">Design Recommendations</span></span>](#DesignRecs)  
  
     [<span data-ttu-id="1296c-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="1296c-114">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1296c-115">安全性</span><span class="sxs-lookup"><span data-stu-id="1296c-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1296c-116">**使用下列方法建立非索引鍵資料行的索引：**</span><span class="sxs-lookup"><span data-stu-id="1296c-116">**To create an index with nonkey columns, using:**</span></span>  
  
     [<span data-ttu-id="1296c-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1296c-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1296c-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1296c-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1296c-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="1296c-119">Before You Begin</span></span>  
  
###  <a name="design-recommendations"></a><a name="DesignRecs"></a> <span data-ttu-id="1296c-120">設計建議</span><span class="sxs-lookup"><span data-stu-id="1296c-120">Design Recommendations</span></span>  
  
-   <span data-ttu-id="1296c-121">重新設計具有大型索引鍵大小的非叢集索引，如此僅有用於搜尋與查閱的資料行才會是索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="1296c-121">Redesign nonclustered indexes with a large index key size so that only columns used for searching and lookups are key columns.</span></span> <span data-ttu-id="1296c-122">讓涵蓋查詢的所有其他資料行都做為非索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="1296c-122">Make all other columns that cover the query into nonkey columns.</span></span> <span data-ttu-id="1296c-123">如此一來，您將擁有涵蓋查詢所需的所有資料行，但是索引鍵本身會變得很小而且很有效率。</span><span class="sxs-lookup"><span data-stu-id="1296c-123">In this way, you will have all columns needed to cover the query, but the index key itself is small and efficient.</span></span>  
  
-   <span data-ttu-id="1296c-124">在非叢集索引中包含非索引鍵資料行，以避免超出目前索引大小限制 (最大 16 個索引鍵資料行，最大 900 個位元組索引鍵大小)</span><span class="sxs-lookup"><span data-stu-id="1296c-124">Include nonkey columns in a nonclustered index to avoid exceeding the current index size limitations of a maximum of 16 key columns and a maximum index key size of 900 bytes.</span></span> <span data-ttu-id="1296c-125">計算索引鍵資料行數或索引鍵大小時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 不會考慮非索引鍵之索引資料行。</span><span class="sxs-lookup"><span data-stu-id="1296c-125">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not consider nonkey columns when calculating the number of index key columns or index key size.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1296c-126">限制事項</span><span class="sxs-lookup"><span data-stu-id="1296c-126">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1296c-127">非索引鍵資料行只能在非叢集索引上定義。</span><span class="sxs-lookup"><span data-stu-id="1296c-127">Nonkey columns can only be defined on nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="1296c-128">除了 `text`、`ntext` 和 `image`，所有資料類型都可以做為非索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="1296c-128">All data types except `text`, `ntext`, and `image` can be used as nonkey columns.</span></span>  
  
-   <span data-ttu-id="1296c-129">具決定性之精確或非精確的計算資料行都可以當做非索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="1296c-129">Computed columns that are deterministic and either precise or imprecise can be nonkey columns.</span></span> <span data-ttu-id="1296c-130">如需詳細資訊，請參閱 [計算資料行的索引](indexes-on-computed-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="1296c-130">For more information, see [Indexes on Computed Columns](indexes-on-computed-columns.md).</span></span>  
  
-   <span data-ttu-id="1296c-131">只要計算資料行資料類型可以做為非索引鍵索引資料行，則從 `image`、`ntext` 與 `text` 資料類型衍生的計算資料行即可以是非索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="1296c-131">Computed columns derived from `image`, `ntext`, and `text` data types can be nonkey columns as long as the computed column data type is allowed as a nonkey index column.</span></span>  
  
-   <span data-ttu-id="1296c-132">必須先卸除資料表的索引，才能從資料表卸除非索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="1296c-132">Nonkey columns cannot be dropped from a table unless that table's index is dropped first.</span></span>  
  
-   <span data-ttu-id="1296c-133">除非執行下列動作，否則無法變更非索引鍵之索引資料行：</span><span class="sxs-lookup"><span data-stu-id="1296c-133">Nonkey columns cannot be changed, except to do the following:</span></span>  
  
    -   <span data-ttu-id="1296c-134">將資料行的 Null 屬性從 NOT NULL 變更為 NULL。</span><span class="sxs-lookup"><span data-stu-id="1296c-134">Change the nullability of the column from NOT NULL to NULL.</span></span>  
  
    -   <span data-ttu-id="1296c-135">增加 `varchar`、`nvarchar` 或 `varbinary` 資料行的長度。</span><span class="sxs-lookup"><span data-stu-id="1296c-135">Increase the length of `varchar`, `nvarchar`, or `varbinary` columns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1296c-136">Security</span><span class="sxs-lookup"><span data-stu-id="1296c-136">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1296c-137">權限</span><span class="sxs-lookup"><span data-stu-id="1296c-137">Permissions</span></span>  
 <span data-ttu-id="1296c-138">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="1296c-138">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="1296c-139">使用者必須是 **系統管理員** 固定伺服器角色的成員，或是 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="1296c-139">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1296c-140">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1296c-140">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-index-with-nonkey-columns"></a><span data-ttu-id="1296c-141">建立非索引鍵資料行的索引</span><span class="sxs-lookup"><span data-stu-id="1296c-141">To create an index with nonkey columns</span></span>  
  
1.  <span data-ttu-id="1296c-142">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要建立非索引鍵資料行之索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="1296c-142">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to create an index with nonkey columns.</span></span>  
  
2.  <span data-ttu-id="1296c-143">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1296c-143">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="1296c-144">按一下加號展開要建立非索引鍵資料行之索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="1296c-144">Click the plus sign to expand the table on which you want to create an index with nonkey columns.</span></span>  
  
4.  <span data-ttu-id="1296c-145">以滑鼠右鍵按一下 [索引] 資料夾，指向 [新增索引]，然後選取 [非叢集索引…]。</span><span class="sxs-lookup"><span data-stu-id="1296c-145">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="1296c-146">在 **[新增索引]** 對話方塊，於 **[一般]** 頁面上的 **[索引名稱]** 方塊中輸入新索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="1296c-146">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="1296c-147">按一下 [索引鍵資料行] 索引標籤底下的 [加入...]。</span><span class="sxs-lookup"><span data-stu-id="1296c-147">Under the **Index key columns** tab, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="1296c-148">在 [**從**_Table_name_選取資料行] 對話方塊中，選取要加入至索引之資料表資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1296c-148">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the index.</span></span>  
  
8.  <span data-ttu-id="1296c-149">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1296c-149">Click **OK**.</span></span>  
  
9. <span data-ttu-id="1296c-150">按一下 [包含的資料行] 索引標籤底下的 [加入...]。</span><span class="sxs-lookup"><span data-stu-id="1296c-150">Under the **Included columns** tab, click **Add...**.</span></span>  
  
10. <span data-ttu-id="1296c-151">在 [**從**_Table_name_選取資料行] 對話方塊中，選取要加入至索引中做為非索引鍵資料行之資料表資料行或資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1296c-151">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the index as nonkey columns.</span></span>  
  
11. <span data-ttu-id="1296c-152">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1296c-152">Click **OK**.</span></span>  
  
12. <span data-ttu-id="1296c-153">在 **[新增索引]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="1296c-153">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1296c-154">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1296c-154">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-index-with-nonkey-columns"></a><span data-ttu-id="1296c-155">建立非索引鍵資料行的索引</span><span class="sxs-lookup"><span data-stu-id="1296c-155">To create an index with nonkey columns</span></span>  
  
1.  <span data-ttu-id="1296c-156">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1296c-156">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1296c-157">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="1296c-157">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1296c-158">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="1296c-158">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates a nonclustered index on the Person.Address table with four included (nonkey) columns.   
    -- index key column is PostalCode and the nonkey columns are  
    -- AddressLine1, AddressLine2, City, and StateProvinceID.  
    CREATE NONCLUSTERED INDEX IX_Address_PostalCode  
    ON Person.Address (PostalCode)  
    INCLUDE (AddressLine1, AddressLine2, City, StateProvinceID);  
    GO  
    ```  
  
 <span data-ttu-id="1296c-159">如需詳細資訊，請參閱 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1296c-159">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
