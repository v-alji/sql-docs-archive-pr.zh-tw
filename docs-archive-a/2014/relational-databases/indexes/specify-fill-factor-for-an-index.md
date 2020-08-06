---
title: 指定索引的填滿因素 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- fill factor [SQL Server]
- page splits [SQL Server]
ms.assetid: 237a577e-b42b-4adb-90cf-aa7fb174f3ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ac54f2b22de55ed74c4635ec0f86d008c7624a42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707521"
---
# <a name="specify-fill-factor-for-an-index"></a><span data-ttu-id="2ecda-102">指定索引的填滿因素</span><span class="sxs-lookup"><span data-stu-id="2ecda-102">Specify Fill Factor for an Index</span></span>
  <span data-ttu-id="2ecda-103">此主題描述何謂填滿因數，以及如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中指定索引的填滿因數值。</span><span class="sxs-lookup"><span data-stu-id="2ecda-103">This topic describes what fill factor is and how to specify a fill factor value on an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2ecda-104">提供填滿因數的用意，是為了微調索引資料的儲存與效能。</span><span class="sxs-lookup"><span data-stu-id="2ecda-104">The fill-factor option is provided for fine-tuning index data storage and performance.</span></span> <span data-ttu-id="2ecda-105">建立或重建索引時，填滿因數值會決定要在每個分葉層級頁面上填滿資料的空間百分比，進而保留每個頁面的剩餘百分比當做可用空間，以供未來成長使用。</span><span class="sxs-lookup"><span data-stu-id="2ecda-105">When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the remainder on each page as free space for future growth.</span></span> <span data-ttu-id="2ecda-106">例如，如果指定填滿因數值 80，則表示每個分葉層級的頁面將有百分之 20 的空間保留空白，在基礎資料表中加入資料時，將有空間可供索引擴充使用。</span><span class="sxs-lookup"><span data-stu-id="2ecda-106">For example, specifying a fill-factor value of 80 means that 20 percent of each leaf-level page will be left empty, providing space for index expansion as data is added to the underlying table.</span></span> <span data-ttu-id="2ecda-107">索引資料列之間 (而不是索引結尾處) 的空白空間將會予以保留。</span><span class="sxs-lookup"><span data-stu-id="2ecda-107">The empty space is reserved between the index rows rather than at the end of the index.</span></span>  
  
 <span data-ttu-id="2ecda-108">填滿因數值是 1 到 100 之間的百分比，而整個伺服器的預設值 0 則表示分葉層級頁面的容量填滿。</span><span class="sxs-lookup"><span data-stu-id="2ecda-108">The fill-factor value is a percentage from 1 to 100, and the server-wide default is 0 which means that the leaf-level pages are filled to capacity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ecda-109">填滿因數值 0 和 100 在各方面都是一樣的。</span><span class="sxs-lookup"><span data-stu-id="2ecda-109">Fill-factor values 0 and 100 are the same in all respects.</span></span>  
  
 <span data-ttu-id="2ecda-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2ecda-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2ecda-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2ecda-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2ecda-112">效能考量</span><span class="sxs-lookup"><span data-stu-id="2ecda-112">Performance Considerations</span></span>](#Performance)  
  
     [<span data-ttu-id="2ecda-113">安全性</span><span class="sxs-lookup"><span data-stu-id="2ecda-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2ecda-114">**使用下列方法指定索引的填滿因數：**</span><span class="sxs-lookup"><span data-stu-id="2ecda-114">**To specify a fill factor in an index, using:**</span></span>  
  
     [<span data-ttu-id="2ecda-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ecda-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2ecda-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ecda-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2ecda-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="2ecda-117">Before You Begin</span></span>  
  
###  <a name="performance-considerations"></a><a name="Performance"></a> <span data-ttu-id="2ecda-118">效能考量</span><span class="sxs-lookup"><span data-stu-id="2ecda-118">Performance Considerations</span></span>  
  
#### <a name="page-splits"></a><span data-ttu-id="2ecda-119">頁面分割</span><span class="sxs-lookup"><span data-stu-id="2ecda-119">Page Splits</span></span>  
 <span data-ttu-id="2ecda-120">選擇正確的填滿因數值，可以減少可能的頁面分割，因為當基礎資料表中加入資料時，將有足夠的空間來進行索引擴充。將新的資料列加入全文檢索頁面時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會將幾乎一半的資料列移到新的頁面，以留出空間給新的資料列。</span><span class="sxs-lookup"><span data-stu-id="2ecda-120">A correctly chosen fill-factor value can reduce potential page splits by providing enough space for index expansion as data is added to the underlying table.When a new row is added to a full index page, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] moves approximately half the rows to a new page to make room for the new row.</span></span> <span data-ttu-id="2ecda-121">這個重組動作稱為分頁分割。</span><span class="sxs-lookup"><span data-stu-id="2ecda-121">This reorganization is known as a page split.</span></span> <span data-ttu-id="2ecda-122">分頁分割可留出空間給新的記錄，但是執行時需要時間，而且是一項耗用大量資源的作業。</span><span class="sxs-lookup"><span data-stu-id="2ecda-122">A page split makes room for new records, but can take time to perform and is a resource intensive operation.</span></span> <span data-ttu-id="2ecda-123">此外，它也可能會造成資料片段過多，因而增加 I/O 作業。</span><span class="sxs-lookup"><span data-stu-id="2ecda-123">Also, it can cause fragmentation that causes increased I/O operations.</span></span> <span data-ttu-id="2ecda-124">如果頁面分割次數過於頻繁，可以使用新的或現有的填滿因數值重建索引，藉以重新分配資料。</span><span class="sxs-lookup"><span data-stu-id="2ecda-124">When frequent page splits occur, the index can be rebuilt by using a new or existing fill-factor value to redistribute the data.</span></span> <span data-ttu-id="2ecda-125">如需詳細資訊，請參閱 [重新組織與重建索引](reorganize-and-rebuild-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="2ecda-125">For more information, see [Reorganize and Rebuild Indexes](reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="2ecda-126">雖然非零的較低填滿函數值能夠減少索引成長時進行頁面分割的需求，但是索引將需要更多的儲存空間，而且可能會降低讀取效能。</span><span class="sxs-lookup"><span data-stu-id="2ecda-126">Although a low, nonzero fill-factor value may reduce the requirement to split pages as the index grows, the index will require more storage space and can decrease read performance.</span></span> <span data-ttu-id="2ecda-127">即使對於會大量執行插入和更新作業的應用程式而言，讀取資料庫的次數通常比寫入資料庫的次數還要高，因數為 5 比 10。</span><span class="sxs-lookup"><span data-stu-id="2ecda-127">Even for an application oriented for many insert and update operations, the number of database reads typically outnumber database writes by a factor of 5 to 10.</span></span> <span data-ttu-id="2ecda-128">因此，指定預設值以外的填滿因數，將可能以與填滿因數設定呈反比的數量，降低資料庫的讀取效能。</span><span class="sxs-lookup"><span data-stu-id="2ecda-128">Therefore, specifying a fill factor other than the default can decrease database read performance by an amount inversely proportional to the fill-factor setting.</span></span> <span data-ttu-id="2ecda-129">例如，一個 50 的填滿因數值，可能會使資料庫的讀取效能降低兩倍。</span><span class="sxs-lookup"><span data-stu-id="2ecda-129">For example, a fill-factor value of 50 can cause database read performance to decrease by two times.</span></span> <span data-ttu-id="2ecda-130">讀取效能降低是因為索引包含更多的分頁，造成擷取資料所需的磁碟 IO 作業增加所致。</span><span class="sxs-lookup"><span data-stu-id="2ecda-130">Read performance is decreased because the index contains more pages, therefore increasing the disk IO operations required to retrieve the data.</span></span>  
  
#### <a name="adding-data-to-the-end-of-the-table"></a><span data-ttu-id="2ecda-131">將資料加入資料表的結尾</span><span class="sxs-lookup"><span data-stu-id="2ecda-131">Adding Data to the End of the Table</span></span>  
 <span data-ttu-id="2ecda-132">如果新的資料在資料表內平均分配，則非零的填滿因數值 (0 或 100 以外) 對於效能將很有幫助。</span><span class="sxs-lookup"><span data-stu-id="2ecda-132">A nonzero fill factor other than 0 or 100 can be good for performance if the new data is evenly distributed throughout the table.</span></span> <span data-ttu-id="2ecda-133">但是，如果將所有資料加入資料表的結尾，索引頁面中的空白處將不會填滿。</span><span class="sxs-lookup"><span data-stu-id="2ecda-133">However, if all the data is added to the end of the table, the empty space in the index pages will not be filled.</span></span> <span data-ttu-id="2ecda-134">例如，如果索引鍵資料行為 IDENTITY 資料行，新資料列的索引鍵一定會增加，而且在邏輯上會將索引資料列加入索引的結尾。</span><span class="sxs-lookup"><span data-stu-id="2ecda-134">For example, if the index key column is an IDENTITY column, the key for new rows is always increasing and the index rows are logically added to the end of the index.</span></span> <span data-ttu-id="2ecda-135">如果現有的資料列將以增加資料列大小的資料進行更新，請使用小於 100 的填滿因數。</span><span class="sxs-lookup"><span data-stu-id="2ecda-135">If existing rows will be updated with data that lengthens the size of the rows, use a fill factor of less than 100.</span></span> <span data-ttu-id="2ecda-136">每個頁面上的額外位元組將有助於減少資料列中額外長度所導致的頁面分割。</span><span class="sxs-lookup"><span data-stu-id="2ecda-136">The extra bytes on each page will help to minimize page splits caused by extra length in the rows.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2ecda-137">Security</span><span class="sxs-lookup"><span data-stu-id="2ecda-137">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2ecda-138">權限</span><span class="sxs-lookup"><span data-stu-id="2ecda-138">Permissions</span></span>  
 <span data-ttu-id="2ecda-139">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="2ecda-139">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="2ecda-140">使用者必須是 **系統管理員** 固定伺服器角色的成員，或是 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="2ecda-140">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2ecda-141">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ecda-141">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-fill-factor-by-using-table-designer"></a><span data-ttu-id="2ecda-142">使用資料表設計工具指定填滿因數</span><span class="sxs-lookup"><span data-stu-id="2ecda-142">To specify a fill factor by using Table Designer</span></span>  
  
1.  <span data-ttu-id="2ecda-143">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要指定索引填滿因數的資料表。</span><span class="sxs-lookup"><span data-stu-id="2ecda-143">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to specify an index's fill factor.</span></span>  
  
2.  <span data-ttu-id="2ecda-144">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ecda-144">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="2ecda-145">以滑鼠右鍵按一下要指定索引填滿因數的資料表，然後選取 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="2ecda-145">Right-click the table on which you want to specify an index's fill factor and select **Design**.</span></span>  
  
4.  <span data-ttu-id="2ecda-146">在 [資料表設計工具]  功能表上，按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="2ecda-146">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="2ecda-147">選取包含您要指定填滿因數的索引。</span><span class="sxs-lookup"><span data-stu-id="2ecda-147">Select the index with the fill factor that you want to specify.</span></span>  
  
6.  <span data-ttu-id="2ecda-148">展開 **[填滿規格]** ，選取 **[填滿因數]** 資料列，在資料列中輸入所要的填滿因數。</span><span class="sxs-lookup"><span data-stu-id="2ecda-148">Expand **Fill Specification**, select the **Fill Factor** row and enter the fill factor you want in the row.</span></span>  
  
7.  <span data-ttu-id="2ecda-149">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="2ecda-149">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="2ecda-150">在 [檔案] 功能表上，選取 [儲存 _table_name_]。</span><span class="sxs-lookup"><span data-stu-id="2ecda-150">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-specify-a-fill-factor-in-an-index-by-using-object-explorer"></a><span data-ttu-id="2ecda-151">使用物件總管指定索引的填滿因數</span><span class="sxs-lookup"><span data-stu-id="2ecda-151">To specify a fill factor in an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="2ecda-152">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要指定索引填滿因數的資料表。</span><span class="sxs-lookup"><span data-stu-id="2ecda-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to specify an index's fill factor.</span></span>  
  
2.  <span data-ttu-id="2ecda-153">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ecda-153">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="2ecda-154">按一下加號展開要指定索引填滿因數的資料表。</span><span class="sxs-lookup"><span data-stu-id="2ecda-154">Click the plus sign to expand the table on which you want to specify an index's fill factor.</span></span>  
  
4.  <span data-ttu-id="2ecda-155">按一下加號展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ecda-155">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="2ecda-156">以滑鼠右鍵按一下包含您要指定填滿因數的索引，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="2ecda-156">Right-click the index with the fill factor that you want to specify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="2ecda-157">在 **[選取頁面]** 底下，選取 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="2ecda-157">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="2ecda-158">在 **[填滿因數]** 資料列中，輸入所要的填滿因數。</span><span class="sxs-lookup"><span data-stu-id="2ecda-158">In the **Fill factor** row, enter the fill factor that you want.</span></span>  
  
8.  <span data-ttu-id="2ecda-159">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2ecda-159">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2ecda-160">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ecda-160">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-fill-factor-in-an-existing-index"></a><span data-ttu-id="2ecda-161">若要在現有索引中指定填滿因數</span><span class="sxs-lookup"><span data-stu-id="2ecda-161">To specify a fill factor in an existing index</span></span>  
  
1.  <span data-ttu-id="2ecda-162">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ecda-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2ecda-163">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2ecda-163">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2ecda-164">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2ecda-164">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2ecda-165">這個範例會重建現有的索引，並且在重建作業期間套用指定的填滿因數。</span><span class="sxs-lookup"><span data-stu-id="2ecda-165">The example rebuilds an existing index and applies the specified fill factor during the rebuild operation.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Rebuilds the IX_Employee_OrganizationLevel_OrganizationNode index   
    -- with a fill factor of 80 on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD WITH (FILLFACTOR = 80);   
    GO  
    ```  
  
#### <a name="another-way-to-specify-a-fill-factor-in-an-index"></a><span data-ttu-id="2ecda-166">指定索引填滿因數的另一個方法</span><span class="sxs-lookup"><span data-stu-id="2ecda-166">Another way to specify a fill factor in an index</span></span>  
  
1.  <span data-ttu-id="2ecda-167">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ecda-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2ecda-168">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2ecda-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2ecda-169">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2ecda-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    /* Drops and re-creates the IX_Employee_OrganizationLevel_OrganizationNode index on the HumanResources.Employee table with a fill factor of 80.  
    */  
  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)   
    WITH (DROP_EXISTING = ON, FILLFACTOR = 80);   
    GO  
    ```  
  
 <span data-ttu-id="2ecda-170">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ecda-170">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
