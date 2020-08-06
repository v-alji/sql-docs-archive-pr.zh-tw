---
title: 建立非叢集索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index creation [SQL Server], nonclustered indexes
- nonclustered indexes [SQL Server], creating
- nonclustered indexes [SQL Server], UNIQUE constraint
- indexes [SQL Server], nonclustered
- nonclustered indexes [SQL Server], PRIMARY KEY constraint
ms.assetid: 9402029a-1227-46c4-93aa-c2122eb1b943
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fae0c06b1f562dc3fc518a319df1787b3384c0cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708297"
---
# <a name="create-nonclustered-indexes"></a><span data-ttu-id="2ef43-102">建立非叢集索引</span><span class="sxs-lookup"><span data-stu-id="2ef43-102">Create Nonclustered Indexes</span></span>
  <span data-ttu-id="2ef43-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2ef43-103">You can create nonclustered indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2ef43-104">非叢集索引是與資料表中所儲存之資料不同的索引結構，可重新排序一個或多個選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="2ef43-104">A nonclustered index is an index structure separate from the data stored in a table that reorders one or more selected columns.</span></span> <span data-ttu-id="2ef43-105">非叢集索引經常可協助您以比搜尋基礎資料表更快的速度找到資料；查詢的結果有時會完全來自非叢集索引中的資料，或是非叢集索引可能會將 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 指向基礎資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="2ef43-105">Nonclustered indexes can often help you find data more quickly than searching the underlying table; queries can sometimes be answered entirely by the data in the nonclustered index, or the nonclustered index can point the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to the rows in the underlying table.</span></span> <span data-ttu-id="2ef43-106">一般而言，建立非叢集索引是為了改善叢集索引未涵蓋但經常使用之查詢的效能，或尋找沒有叢集索引之資料表中的資料列 (稱為堆積)。</span><span class="sxs-lookup"><span data-stu-id="2ef43-106">Generally, nonclustered indexes are created to improve the performance of frequently used queries not covered by the clustered index or to locate rows in a table without a clustered index (called a heap).</span></span> <span data-ttu-id="2ef43-107">您可以在資料表或索引檢視表上建立多個非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2ef43-107">You can create multiple nonclustered indexes on a table or indexed view.</span></span>  
  
 <span data-ttu-id="2ef43-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2ef43-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2ef43-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2ef43-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2ef43-110">一般實作</span><span class="sxs-lookup"><span data-stu-id="2ef43-110">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="2ef43-111">安全性</span><span class="sxs-lookup"><span data-stu-id="2ef43-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2ef43-112">**若要建立非叢集索引，使用：**</span><span class="sxs-lookup"><span data-stu-id="2ef43-112">**To create a nonclustered index, using:**</span></span>  
  
     [<span data-ttu-id="2ef43-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ef43-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2ef43-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ef43-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2ef43-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="2ef43-115">Before You Begin</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a><span data-ttu-id="2ef43-116">一般的實現</span><span class="sxs-lookup"><span data-stu-id="2ef43-116">Typical Implementations</span></span>  
 <span data-ttu-id="2ef43-117">非叢集索引的實作方法如下：</span><span class="sxs-lookup"><span data-stu-id="2ef43-117">Nonclustered indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="2ef43-118">**UNIQUE 條件約束**</span><span class="sxs-lookup"><span data-stu-id="2ef43-118">**UNIQUE constraints**</span></span>  
  
     <span data-ttu-id="2ef43-119">當您建立 UNIQUE 條件約束時，依預設會建立唯一的非叢集索引，以強制 UNIQUE 條件約束。</span><span class="sxs-lookup"><span data-stu-id="2ef43-119">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="2ef43-120">若資料表上還沒有叢集索引，您可以指定唯一叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2ef43-120">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span> <span data-ttu-id="2ef43-121">如需詳細資訊，請參閱 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="2ef43-121">For more information, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
-   <span data-ttu-id="2ef43-122">**獨立於條件限制之外的索引**</span><span class="sxs-lookup"><span data-stu-id="2ef43-122">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="2ef43-123">依預設，若是未指定叢集索引，則會建立非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2ef43-123">By default, a nonclustered index is created if clustered is not specified.</span></span> <span data-ttu-id="2ef43-124">每個資料表可建立的最大非叢集索引數目是 999 個。</span><span class="sxs-lookup"><span data-stu-id="2ef43-124">The maximum number of nonclustered indexes that can be created per table is 999.</span></span> <span data-ttu-id="2ef43-125">這包含 PRIMARY KEY 或 UNIQUE 條件約束所建立的任何索引，但不包含 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="2ef43-125">This includes any indexes created by PRIMARY KEY or UNIQUE constraints, but does not include XML indexes.</span></span>  
  
-   <span data-ttu-id="2ef43-126">**索引檢視上的非叢集索引**</span><span class="sxs-lookup"><span data-stu-id="2ef43-126">**Nonclustered index on an indexed view**</span></span>  
  
     <span data-ttu-id="2ef43-127">在檢視上建立唯一的叢集索引後，就可以建立非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2ef43-127">After a unique clustered index has been created on a view, nonclustered indexes can be created.</span></span> <span data-ttu-id="2ef43-128">如需詳細資訊，請參閱 [建立索引檢視表](../views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="2ef43-128">For more information, see [Create Indexed Views](../views/views.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2ef43-129">Security</span><span class="sxs-lookup"><span data-stu-id="2ef43-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2ef43-130">權限</span><span class="sxs-lookup"><span data-stu-id="2ef43-130">Permissions</span></span>  
 <span data-ttu-id="2ef43-131">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="2ef43-131">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="2ef43-132">使用者必須是 **系統管理員** 固定伺服器角色的成員，或是 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="2ef43-132">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2ef43-133">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ef43-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-nonclustered-index-by-using-the-table-designer"></a><span data-ttu-id="2ef43-134">若要使用資料表設計工具建立非叢集索引</span><span class="sxs-lookup"><span data-stu-id="2ef43-134">To create a nonclustered index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="2ef43-135">在 [物件總管] 中，展開包含您要建立非叢集索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ef43-135">In Object Explorer, expand the database that contains the table on which you want to create a nonclustered index.</span></span>  
  
2.  <span data-ttu-id="2ef43-136">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ef43-136">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="2ef43-137">以滑鼠右鍵按一下要建立非叢集索引的資料表，然後選取 [設計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ef43-137">Right-click the table on which you want to create a nonclustered index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="2ef43-138">在 [**資料表設計工具**] 功能表上，按一下 [**索引/索引鍵**]。</span><span class="sxs-lookup"><span data-stu-id="2ef43-138">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="2ef43-139">在 [索引/索引鍵]\*\*\*\* 對話方塊中，按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ef43-139">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="2ef43-140">從 [選取的主索引鍵/唯一索引鍵或索引]\*\*\*\* 文字方塊中選取新索引。</span><span class="sxs-lookup"><span data-stu-id="2ef43-140">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
7.  <span data-ttu-id="2ef43-141">在方格中，選取 [建立成 CLUSTERED]\*\*\*\*，然後從屬性右邊的下拉式清單中選擇 [否]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ef43-141">In the grid, select **Create as Clustered**, and choose **No** from the drop-down list to the right of the property.</span></span>  
  
8.  <span data-ttu-id="2ef43-142">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="2ef43-142">Click **Close**.</span></span>  
  
9. <span data-ttu-id="2ef43-143">在 [檔案]\*\*\*\* 功能表上，按一下 [儲存 _資料表名稱_]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ef43-143">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="to-create-a-nonclustered-index-by-using-object-explorer"></a><span data-ttu-id="2ef43-144">若要使用物件總管建立非叢集索引</span><span class="sxs-lookup"><span data-stu-id="2ef43-144">To create a nonclustered index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="2ef43-145">在 [物件總管] 中，展開包含您要建立非叢集索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ef43-145">In Object Explorer, expand the database that contains the table on which you want to create a nonclustered index.</span></span>  
  
2.  <span data-ttu-id="2ef43-146">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ef43-146">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="2ef43-147">展開您要建立非叢集索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="2ef43-147">Expand the table on which you want to create a nonclustered index.</span></span>  
  
4.  <span data-ttu-id="2ef43-148">以滑鼠右鍵按一下 [索引] 資料夾，指向 [新增索引]，然後選取 [非叢集索引…]。</span><span class="sxs-lookup"><span data-stu-id="2ef43-148">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="2ef43-149">在 **[新增索引]** 對話方塊，於 **[一般]** 頁面上的 **[索引名稱]** 方塊中輸入新索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ef43-149">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="2ef43-150">按一下 [索引鍵資料行] 下的 [新增...]。</span><span class="sxs-lookup"><span data-stu-id="2ef43-150">Under **Index key columns**, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="2ef43-151">在 [從 _資料表名稱_ 選取資料行]\*\*\*\* 對話方塊中，選取要加入非叢集索引之一或多個資料表資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef43-151">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the nonclustered index.</span></span>  
  
8.  <span data-ttu-id="2ef43-152">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="2ef43-152">Click **OK**.</span></span>  
  
9. <span data-ttu-id="2ef43-153">在 **[新增索引]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef43-153">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2ef43-154">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ef43-154">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-nonclustered-index-on-a-table"></a><span data-ttu-id="2ef43-155">若要在資料表上建立非叢集索引</span><span class="sxs-lookup"><span data-stu-id="2ef43-155">To create a nonclustered index on a table</span></span>  
  
1.  <span data-ttu-id="2ef43-156">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ef43-156">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2ef43-157">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef43-157">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2ef43-158">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef43-158">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named IX_ProductVendor_VendorID and delete it if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
                WHERE name = N'IX_ProductVendor_VendorID')   
        DROP INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor;   
    GO  
    -- Create a nonclustered index called IX_ProductVendor_VendorID   
    -- on the Purchasing.ProductVendor table using the BusinessEntityID column.   
    CREATE NONCLUSTERED INDEX IX_ProductVendor_VendorID   
        ON Purchasing.ProductVendor (BusinessEntityID);   
    GO  
    ```  
  
 <span data-ttu-id="2ef43-159">如需詳細資訊，請參閱 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ef43-159">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
