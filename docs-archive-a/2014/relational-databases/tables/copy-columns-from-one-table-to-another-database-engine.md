---
title: 將資料行從一個資料表複製至另一個資料表 (Database Engine) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying columns
- columns [SQL Server], copying
ms.assetid: 5f5e70dc-69f9-44b8-bc48-b5d51ac20d77
author: stevestein
ms.author: sstein
ms.openlocfilehash: 37b98bf0910cbbb4c2a1d7fe01f11d52703ec88c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607348"
---
# <a name="copy-columns-from-one-table-to-another-database-engine"></a><span data-ttu-id="8ab9f-102">將資料行從一個資料表複製至另一個資料表 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="8ab9f-102">Copy Columns from One Table to Another (Database Engine)</span></span>
  <span data-ttu-id="8ab9f-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中將資料行從某個資料表複製到另一個資料表，但只複製資料行定義，或複製定義和資料。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-103">This topic describes how to copy columns from one table to another, copying either just the column definition, or the definition and data in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8ab9f-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="8ab9f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8ab9f-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8ab9f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8ab9f-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="8ab9f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8ab9f-107">安全性</span><span class="sxs-lookup"><span data-stu-id="8ab9f-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8ab9f-108">**使用下列方式複製資料行：**</span><span class="sxs-lookup"><span data-stu-id="8ab9f-108">**To coy columns, using:**</span></span>  
  
     [<span data-ttu-id="8ab9f-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8ab9f-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8ab9f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8ab9f-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8ab9f-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="8ab9f-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8ab9f-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="8ab9f-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8ab9f-113">當您在資料庫之間複製擁有別名資料類型的資料行時，別名資料類型可能無法在目的地資料庫中使用。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-113">When you copy a column that has an alias data type from one database to another, the alias data type may not be available in the destination database.</span></span> <span data-ttu-id="8ab9f-114">在這種狀況下，將指派資料庫中可用而最符合的基本資料類型給該資料行。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-114">In such a case, the column will be assigned the nearest matching base data type available in that database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8ab9f-115">Security</span><span class="sxs-lookup"><span data-stu-id="8ab9f-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8ab9f-116">權限</span><span class="sxs-lookup"><span data-stu-id="8ab9f-116">Permissions</span></span>  
 <span data-ttu-id="8ab9f-117">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8ab9f-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8ab9f-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a><span data-ttu-id="8ab9f-119">若要將資料行定義從一個資料表複製到另一個資料表</span><span class="sxs-lookup"><span data-stu-id="8ab9f-119">To copy column definitions from one table to another</span></span>  
  
1.  <span data-ttu-id="8ab9f-120">以滑鼠右鍵按一下含有要複製之資料行的資料表，以及您要複製到其中的目標資料表，再按一下 [設計]  ，加以開啟。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-120">Open the table with columns you want to copy and the one you want to copy into by right-clicking the tables, and then clicking **Design**.</span></span>  
  
2.  <span data-ttu-id="8ab9f-121">按一下您要複製資料行的資料表索引標籤，並選取這些資料行。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-121">Click the tab for the table with the columns you want to copy and select those columns.</span></span>  
  
3.  <span data-ttu-id="8ab9f-122">從 [ **編輯** ] 功能表中，按一下 [ **複製**]。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-122">From the **Edit** menu, click **Copy**.</span></span>  
  
4.  <span data-ttu-id="8ab9f-123">按一下資料行複製目的地的資料表之索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-123">Click the tab for the table into which you want to copy the columns.</span></span>  
  
5.  <span data-ttu-id="8ab9f-124">選取要在其前面插入資料行的資料行，並從 **[編輯]** 功能表中，按一下 **[貼上]** 。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-124">Select the column you want to follow the inserted columns and, from the **Edit** menu, click **Paste**.</span></span>  
  
#### <a name="to-copy-data-from-one-table-to-another"></a><span data-ttu-id="8ab9f-125">若要將資料從一個資料表複製到另一個資料表</span><span class="sxs-lookup"><span data-stu-id="8ab9f-125">To copy data from one table to another</span></span>  
  
1.  <span data-ttu-id="8ab9f-126">依照前述的指示複製資料行定義。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-126">Follow the directions for copying column definitions above.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ab9f-127">在開始將資料從一個資料表複製到另一個資料表之前，請確定目的資料行中的資料類型與來源資料行的資料類型是否相容。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-127">Before you begin to copy data from one table to another, make sure that the data types in the destination columns are compatible with the data types of the source columns</span></span>  
  
2.  <span data-ttu-id="8ab9f-128">在物件總管 中，以滑鼠右鍵按一下 [檢視]\*\*\*\* 節點，然後按一下 [新檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-128">In Object Explorer, right-click the **Views** node, and then click **New View**.</span></span>  
  
3.  <span data-ttu-id="8ab9f-129">在 [ **查詢設計工具** ] 功能表中指向 [ **變更類型**]，再按 [ **插入結果**]。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-129">From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.</span></span>  
  
4.  <span data-ttu-id="8ab9f-130">在 [ **選擇插入結果的目標資料表** ] 對話方塊中，選取要將資料複製到其中的資料表，再按 [ **確定**]。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-130">In the **Choose Target Table for Insert Results** dialog box, select the table into which you want to copy the data, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8ab9f-131">如果您是在資料表中複製資料列，您可以加入來源資料表做為目的資料表。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-131">If you are copying rows within a table, you can add the source table as a destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ab9f-132">[**查詢設計工具** ] 無法預先判斷您可以更新哪些資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-132">**Query Designer** cannot determine in advance which tables and views you can update.</span></span> <span data-ttu-id="8ab9f-133">因此，[ **選擇插入結果的目標資料表** ] 對話方塊中的資料表清單會顯示正在查詢之資料連接中的所有可用資料表和檢視，甚至包括您可能無法將資料列複製到其中的資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-133">Therefore, the list of tables in the **Choose Target Table for Insert Results** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.</span></span>  
  
5.  <span data-ttu-id="8ab9f-134">在 [圖表] 窗格的主體中按一下滑鼠右鍵，再從快速鍵功能表中按一下 [Add Table to Diagram (將資料表加入圖表)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-134">Right-click in the body of the diagram pane and, from the shortcut menu, click **Add Table to Diagram**.</span></span>  
  
6.  <span data-ttu-id="8ab9f-135">在 [ **加入資料表** ] 對話方塊中，選取要從中複製資料的每一個資料表，再按一下 [ **加入**]，再按 [ **關閉**]。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-135">In the **Add Table** dialog box, select each table from which you want to copy data, click **Add**, and then click **Close**.</span></span>  
  
     <span data-ttu-id="8ab9f-136">這些資料表會以縮寫格式顯示在 [圖表] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-136">The tables, in an abbreviated form, appear in the diagram pane.</span></span>  
  
7.  <span data-ttu-id="8ab9f-137">在縮寫的資料表中，核取要從中複製資料的每一個資料行的方塊。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-137">In the abbreviated tables, check the boxes for any columns from which you want to copy data.</span></span>  
  
8.  <span data-ttu-id="8ab9f-138">在 [準則] 窗格的 [ **附加** ] 欄中，為每一個目標資料行選擇您要從中複製資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-138">In the criteria pane, in the **Append** column, for each target column choose a column from which you want to copy data.</span></span>  
  
9. <span data-ttu-id="8ab9f-139">在 [準則] 窗格中輸入搜尋條件，以指定要複製的資料列。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-139">Specify the rows to copy by entering search conditions in the criteria pane.</span></span> <span data-ttu-id="8ab9f-140">如需詳細資訊，請參閱[指定搜尋條件 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-140">For details, see [Specify Search Conditions &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="8ab9f-141">如果沒有指定搜尋條件，便會將來源資料表的所有資料列複製到目的資料表中。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-141">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
10. <span data-ttu-id="8ab9f-142">如果您想要複製摘要資訊，請指定 [**群組依據**] 選項。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-142">If you want to copy summary information, specify **Group By** options.</span></span> <span data-ttu-id="8ab9f-143">如需詳細資訊，請參閱[摘要或彙總資料表中所有資料列的值 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-143">For details, see [Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md).</span></span>  
  
11. <span data-ttu-id="8ab9f-144">按一下 [ **執行 SQL** ] 按鈕 以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-144">Click the **Execute SQL button** to run the query.</span></span>  
  
     <span data-ttu-id="8ab9f-145">在執行插入結果查詢時， [結果窗格](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)中不會報告結果，</span><span class="sxs-lookup"><span data-stu-id="8ab9f-145">When you execute an insert results query, no results are reported in the [Results Pane](../../ssms/visual-db-tools/results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="8ab9f-146">而是出現訊息指出已經複製了多少資料列。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-146">Instead, a message appears indicating how many rows were copied.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8ab9f-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8ab9f-147">Using Transact-SQL</span></span>  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a><span data-ttu-id="8ab9f-148">若要將資料行定義從一個資料表複製到另一個資料表</span><span class="sxs-lookup"><span data-stu-id="8ab9f-148">To copy column definitions from one table to another</span></span>  
  
1.  <span data-ttu-id="8ab9f-149">您無法透過使用 Transact-SQL 陳述式將個別資料行從一個資料表複製到另一個現有資料表。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-149">You cannot copy individual columns from one table to another existing table by using Transact-SQL statements.</span></span> <span data-ttu-id="8ab9f-150">不過，可透過 SELECT INTO，在預設的檔案群組中建立新的資料表，然後將查詢的結果資料列插入其中。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-150">However, you can create a new table in the default filegroup and inserts the resulting rows from the query into it by using SELECT INTO.</span></span> <span data-ttu-id="8ab9f-151">如需詳細資訊，請參閱 [INTO 子句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-into-clause-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-151">For more information, see [INTO Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-into-clause-transact-sql).</span></span>  
  
#### <a name="to-copy-data-from-one-table-to-another"></a><span data-ttu-id="8ab9f-152">若要將資料從一個資料表複製到另一個資料表</span><span class="sxs-lookup"><span data-stu-id="8ab9f-152">To copy data from one table to another</span></span>  
  
1.  <span data-ttu-id="8ab9f-153">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-153">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8ab9f-154">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-154">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8ab9f-155">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="8ab9f-155">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.EmployeeSales  
    ( BusinessEntityID   varchar(11) NOT NULL,  
      SalesYTD money NOT NULL  
    );  
    GO  
    INSERT INTO dbo.EmployeeSales  
        SELECT BusinessEntityID, SalesYTD   
        FROM Sales.SalesPerson;  
    GO  
    ```  
  
  
