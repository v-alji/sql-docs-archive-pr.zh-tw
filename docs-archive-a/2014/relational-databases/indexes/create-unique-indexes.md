---
title: 建立唯一索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- unique indexes
- designing indexes [SQL Server], unique
- clustered indexes, unique
- indexes [SQL Server], unique
- nonclustered indexes [SQL Server], unique
- unique indexes, design guidelines
ms.assetid: 56b5982e-cb94-46c0-8fbb-772fc275354a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c96c4e17a8ce0863452db171302d650f6114919
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708302"
---
# <a name="create-unique-indexes"></a><span data-ttu-id="2cf16-102">建立唯一索引</span><span class="sxs-lookup"><span data-stu-id="2cf16-102">Create Unique Indexes</span></span>
  <span data-ttu-id="2cf16-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]的資料表建立唯一索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-103">This topic describes how to create a unique index on a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2cf16-104">唯一索引可保證索引鍵不包含重複值，因此資料表中的每一個資料列在某方面來說是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2cf16-104">A unique index guarantees that the index key contains no duplicate values and therefore every row in the table is in some way unique.</span></span> <span data-ttu-id="2cf16-105">建立 UNIQUE 條件約束與建立獨立於條件約束之外的唯一索引，兩者並無明顯差異。</span><span class="sxs-lookup"><span data-stu-id="2cf16-105">There are no significant differences between creating a UNIQUE constraint and creating a unique index that is independent of a constraint.</span></span> <span data-ttu-id="2cf16-106">資料驗證的方式相同，而且查詢最佳化工具不會區分由條件約束建立或由手動建立的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-106">Data validation occurs in the same manner, and the query optimizer does not differentiate between a unique index created by a constraint or manually created.</span></span> <span data-ttu-id="2cf16-107">不過，在資料行上建立 UNIQUE 條件約束，會使索引目標更明確。</span><span class="sxs-lookup"><span data-stu-id="2cf16-107">However, creating a UNIQUE constraint on the column makes the objective of the index clear.</span></span> <span data-ttu-id="2cf16-108">如需有關 UNIQUE 條件約束的詳細資訊，請參閱＜ [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2cf16-108">For more information on UNIQUE constraints, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
 <span data-ttu-id="2cf16-109">當您建立唯一的索引時，可以設定忽略重複之索引鍵的選項。</span><span class="sxs-lookup"><span data-stu-id="2cf16-109">When you create a unique index, you can set an option to ignore duplicate keys.</span></span> <span data-ttu-id="2cf16-110">如果此選項設定為 [是]  ，且您嘗試透過加入影響多個資料列的資料來建立重複的索引鍵 (使用 INSERT 陳述式)，則不會加入包含重複索引鍵的資料列。</span><span class="sxs-lookup"><span data-stu-id="2cf16-110">If this option is set to **Yes** and you attempt to create duplicate keys by adding data that affects multiple rows (with the INSERT statement), the row containing a duplicate is not added.</span></span> <span data-ttu-id="2cf16-111">如果此選項設定為 [ **否**]，則整個插入作業會失敗，且所有資料都會回復。</span><span class="sxs-lookup"><span data-stu-id="2cf16-111">If it is set to **No**, the entire insert operation fails and all the data is rolled back.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2cf16-112">如果一個以上的資料列中的某單一資料行為 NULL，您將無法建立該單一資料行的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-112">You cannot create a unique index on a single column if that column contains NULL in more than one row.</span></span> <span data-ttu-id="2cf16-113">同樣地，如果一個以上的資料列中的一組資料行全為 NULL 的話，您將無法在該組資料行上建立唯一索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-113">Similarly, you cannot create a unique index on multiple columns if the combination of columns contains NULL in more than one row.</span></span> <span data-ttu-id="2cf16-114">基於索引目的，這些會被視為重複的值。</span><span class="sxs-lookup"><span data-stu-id="2cf16-114">These are treated as duplicate values for indexing purposes.</span></span>  
  
 <span data-ttu-id="2cf16-115">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2cf16-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2cf16-116">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2cf16-116">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2cf16-117">唯一索引的優點</span><span class="sxs-lookup"><span data-stu-id="2cf16-117">Benefits of a Unique Index</span></span>](#Benefits)  
  
     [<span data-ttu-id="2cf16-118">一般實作</span><span class="sxs-lookup"><span data-stu-id="2cf16-118">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="2cf16-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="2cf16-119">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2cf16-120">安全性</span><span class="sxs-lookup"><span data-stu-id="2cf16-120">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2cf16-121">**使用下列方法在資料表上建立唯一索引：**</span><span class="sxs-lookup"><span data-stu-id="2cf16-121">**To create a unique index on a table, using:**</span></span>  
  
     [<span data-ttu-id="2cf16-122">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2cf16-122">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2cf16-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2cf16-123">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2cf16-124">開始之前</span><span class="sxs-lookup"><span data-stu-id="2cf16-124">Before You Begin</span></span>  
  
###  <a name="benefits-of-a-unique-index"></a><a name="Benefits"></a> <span data-ttu-id="2cf16-125">唯一索引的優點</span><span class="sxs-lookup"><span data-stu-id="2cf16-125">Benefits of a Unique Index</span></span>  
  
-   <span data-ttu-id="2cf16-126">多重資料行唯一索引可保證索引鍵的每一個值組合都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2cf16-126">Multicolumn unique indexes guarantee that each combination of values in the index key is unique.</span></span> <span data-ttu-id="2cf16-127">例如，若在 **LastName**、 **FirstName**和 **MiddleName** 資料行的組合上建立唯一索引，則該資料表中不得有兩個資料列具有這些資料行的相同值組合。</span><span class="sxs-lookup"><span data-stu-id="2cf16-127">For example, if a unique index is created on a combination of **LastName**, **FirstName**, and **MiddleName** columns, no two rows in the table could have the same combination of values for these columns.</span></span>  
  
-   <span data-ttu-id="2cf16-128">假設每個資料行中的資料是唯一的，您就可以在同一個資料表上建立一個唯一的叢集索引和多個唯一的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-128">Provided that the data in each column is unique, you can create both a unique clustered index and multiple unique nonclustered indexes on the same table.</span></span>  
  
-   <span data-ttu-id="2cf16-129">唯一索引可確保所定義資料行的資料完整性。</span><span class="sxs-lookup"><span data-stu-id="2cf16-129">Unique indexes ensure the data integrity of the defined columns.</span></span>  
  
-   <span data-ttu-id="2cf16-130">唯一索引提供額外資訊給查詢最佳化工具，有助於產生更有效率的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="2cf16-130">Unique indexes provide additional information helpful to the query optimizer that can produce more efficient execution plans.</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="2cf16-131">一般實作</span><span class="sxs-lookup"><span data-stu-id="2cf16-131">Typical Implementations</span></span>  
 <span data-ttu-id="2cf16-132">唯一索引的實作方式如下：</span><span class="sxs-lookup"><span data-stu-id="2cf16-132">Unique indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="2cf16-133">**PRIMARY KEY 或 UNIQUE 條件約束**</span><span class="sxs-lookup"><span data-stu-id="2cf16-133">**PRIMARY KEY or UNIQUE constraint**</span></span>  
  
     <span data-ttu-id="2cf16-134">建立 PRIMARY KEY 條件約束時，若資料表上沒有存在叢集索引，而且您未指定唯一的非叢集索引，則資料行上會自動建立唯一的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-134">When you create a PRIMARY KEY constraint, a unique clustered index on the column or columns is automatically created if a clustered index on the table does not already exist and you do not specify a unique nonclustered index.</span></span> <span data-ttu-id="2cf16-135">主索引鍵資料行不允許 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2cf16-135">The primary key column cannot allow NULL values.</span></span>  
  
     <span data-ttu-id="2cf16-136">當您建立 UNIQUE 條件約束時，依預設會建立唯一的非叢集索引，以強制 UNIQUE 條件約束。</span><span class="sxs-lookup"><span data-stu-id="2cf16-136">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="2cf16-137">若資料表上還沒有叢集索引，您可以指定唯一叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-137">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span>  
  
     <span data-ttu-id="2cf16-138">如需相關資訊，請參閱 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) 及 [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="2cf16-138">For more information, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) and [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).</span></span>  
  
-   <span data-ttu-id="2cf16-139">**獨立於條件限制之外的索引**</span><span class="sxs-lookup"><span data-stu-id="2cf16-139">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="2cf16-140">一個資料表上可定義多個唯一的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-140">Multiple unique nonclustered indexes can be defined on a table.</span></span>  
  
     <span data-ttu-id="2cf16-141">如需詳細資訊，請參閱 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2cf16-141">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
-   <span data-ttu-id="2cf16-142">**索引檢視表**</span><span class="sxs-lookup"><span data-stu-id="2cf16-142">**Indexed view**</span></span>  
  
     <span data-ttu-id="2cf16-143">若要建立索引檢視，您必須在一個或多個檢視資料行上定義唯一的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-143">To create an indexed view, a unique clustered index is defined on one or more view columns.</span></span> <span data-ttu-id="2cf16-144">將會執行檢視，而結果集會以資料表資料儲存在叢集索引中的相同方式，儲存在索引的分葉層級。</span><span class="sxs-lookup"><span data-stu-id="2cf16-144">The view is executed and the result set is stored in the leaf level of the index in the same way table data is stored in a clustered index.</span></span> <span data-ttu-id="2cf16-145">如需詳細資訊，請參閱 [建立索引檢視表](../views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="2cf16-145">For more information, see [Create Indexed Views](../views/views.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2cf16-146">限制事項</span><span class="sxs-lookup"><span data-stu-id="2cf16-146">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2cf16-147">如果資料中已存在重複的索引鍵值，則無法建立唯一索引、UNIQUE 條件約束或 PRIMARY KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="2cf16-147">A unique index, UNIQUE constraint, or PRIMARY KEY constraint cannot be created if duplicate key values exist in the data.</span></span>  
  
-   <span data-ttu-id="2cf16-148">唯一非叢集索引可有內含的非索引鍵之索引資料行。</span><span class="sxs-lookup"><span data-stu-id="2cf16-148">A unique nonclustered index can contain included nonkey columns.</span></span> <span data-ttu-id="2cf16-149">如需詳細資訊，請參閱 [建立內含資料行的索引](create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="2cf16-149">For more information, see [Create Indexes with Included Columns](create-indexes-with-included-columns.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2cf16-150">Security</span><span class="sxs-lookup"><span data-stu-id="2cf16-150">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2cf16-151">權限</span><span class="sxs-lookup"><span data-stu-id="2cf16-151">Permissions</span></span>  
 <span data-ttu-id="2cf16-152">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="2cf16-152">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="2cf16-153">使用者必須是 **系統管理員** 固定伺服器角色的成員，或是 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="2cf16-153">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2cf16-154">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2cf16-154">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-unique-index-by-using-the-table-designer"></a><span data-ttu-id="2cf16-155">若要使用資料表設計工具建立唯一索引</span><span class="sxs-lookup"><span data-stu-id="2cf16-155">To create a unique index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="2cf16-156">在 [物件總管] 中，展開包含您要建立唯一索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2cf16-156">In Object Explorer, expand the database that contains the table on which you want to create a unique index.</span></span>  
  
2.  <span data-ttu-id="2cf16-157">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2cf16-157">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="2cf16-158">以滑鼠右鍵按一下要建立唯一索引的資料表，然後選取 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-158">Right-click the table on which you want to create a unique index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="2cf16-159">在 [資料表設計工具]  功能表中，選取 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-159">On the **Table Designer** menu, select **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="2cf16-160">在 [索引/索引鍵]  對話方塊中，按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-160">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="2cf16-161">從 [選取的主索引鍵/唯一索引鍵或索引]  文字方塊中選取新索引。</span><span class="sxs-lookup"><span data-stu-id="2cf16-161">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
7.  <span data-ttu-id="2cf16-162">在主要方格的 [(一般)]  底下，選取 [類型]  ，然後從清單中選擇 [索引]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-162">In the main grid, under **(General)**, select **Type** and then choose **Index** from the list.</span></span>  
  
8.  <span data-ttu-id="2cf16-163">選取 [資料行]  ，然後按一下省略符號 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="2cf16-163">Select **Columns**, and then click the ellipsis **(...)**.</span></span>  
  
9. <span data-ttu-id="2cf16-164">在 **[索引資料行]** 對話方塊中的 **[資料行名稱]** 底下，選取要進行索引的資料行。</span><span class="sxs-lookup"><span data-stu-id="2cf16-164">In the **Index Columns** dialog box, under **Column Name**, select the columns you want to index.</span></span> <span data-ttu-id="2cf16-165">您最多可以選取 16 個資料行。</span><span class="sxs-lookup"><span data-stu-id="2cf16-165">You can select up to 16 columns.</span></span> <span data-ttu-id="2cf16-166">為了獲得最佳效能，每個索引最好只選取一或兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="2cf16-166">For optimal performance, select only one or two columns per index.</span></span> <span data-ttu-id="2cf16-167">針對每個選取的資料行，指示索引是要以遞增或遞減順序排列此資料行的值。</span><span class="sxs-lookup"><span data-stu-id="2cf16-167">For each column you select, indicate whether the index arranges values of this column in ascending or descending order.</span></span>  
  
10. <span data-ttu-id="2cf16-168">選取索引的所有資料行時，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="2cf16-168">When all columns for the index are selected, click **OK**.</span></span>  
  
11. <span data-ttu-id="2cf16-169">在方格的 [(一般)]  底下，選取 [是唯一的]  ，然後從清單中選擇 [是]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-169">In the grid, under **(General)**, select **Is Unique** and then choose **Yes** from the list.</span></span>  
  
12. <span data-ttu-id="2cf16-170">選擇性：在主要方格中的 **[資料表設計工具]** 底下，選取 **[忽略重複的索引鍵]** ，然後從清單選擇 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="2cf16-170">Optional: In the main grid, under **Table Designer**, select **Ignore Duplicate Keys** and then choose **Yes** from the list.</span></span> <span data-ttu-id="2cf16-171">如果您要忽略會在唯一的索引中建立重複索引鍵的加入資料嘗試，請執行這個動作。</span><span class="sxs-lookup"><span data-stu-id="2cf16-171">Do this if you want to ignore attempts to add data that would create a duplicate key in the unique index.</span></span>  
  
13. <span data-ttu-id="2cf16-172">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-172">Click **Close**.</span></span>  
  
14. <span data-ttu-id="2cf16-173">在 [檔案]\*\*\*\* 功能表上，按一下 [儲存 _資料表名稱_]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2cf16-173">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="create-a-unique-index-by-using-object-explorer"></a><span data-ttu-id="2cf16-174">使用物件總管建立唯一索引</span><span class="sxs-lookup"><span data-stu-id="2cf16-174">Create a unique index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="2cf16-175">在 [物件總管] 中，展開包含您要建立唯一索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2cf16-175">In Object Explorer, expand the database that contains the table on which you want to create a unique index.</span></span>  
  
2.  <span data-ttu-id="2cf16-176">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2cf16-176">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="2cf16-177">展開您要建立唯一索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="2cf16-177">Expand the table on which you want to create a unique index.</span></span>  
  
4.  <span data-ttu-id="2cf16-178">以滑鼠右鍵按一下 [索引]  資料夾，指向 [新增索引]  ，然後選取 [非叢集索引…]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-178">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="2cf16-179">在 **[新增索引]** 對話方塊，於 **[一般]** 頁面上的 **[索引名稱]** 方塊中輸入新索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="2cf16-179">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="2cf16-180">選取 **[唯一]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2cf16-180">Select the **Unique** check box.</span></span>  
  
7.  <span data-ttu-id="2cf16-181">按一下 [索引鍵資料行]  下的 [新增...]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-181">Under **Index key columns**, click **Add...**.</span></span>  
  
8.  <span data-ttu-id="2cf16-182">在 [**從**_Table_name_選取資料行] 對話方塊中，選取要加入至唯一索引之資料表資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2cf16-182">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the unique index.</span></span>  
  
9. <span data-ttu-id="2cf16-183">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2cf16-183">Click **OK**.</span></span>  
  
10. <span data-ttu-id="2cf16-184">在 **[新增索引]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="2cf16-184">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2cf16-185">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2cf16-185">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-unique-index-on-a-table"></a><span data-ttu-id="2cf16-186">在資料表上建立唯一索引</span><span class="sxs-lookup"><span data-stu-id="2cf16-186">To create a unique index on a table</span></span>  
  
1.  <span data-ttu-id="2cf16-187">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2cf16-187">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2cf16-188">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2cf16-188">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2cf16-189">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2cf16-189">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named AK_UnitMeasure_Name and delete it if found  
    IF EXISTS (SELECT name from sys.indexes  
               WHERE name = N'AK_UnitMeasure_Name')   
       DROP INDEX AK_UnitMeasure_Name ON Production.UnitMeasure;   
    GO  
    -- Create a unique index called AK_UnitMeasure_Name  
    -- on the Production.UnitMeasure table using the Name column.  
    CREATE UNIQUE INDEX AK_UnitMeasure_Name   
       ON Production.UnitMeasure (Name);   
    GO  
    ```  
  
 <span data-ttu-id="2cf16-190">如需詳細資訊，請參閱 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2cf16-190">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
