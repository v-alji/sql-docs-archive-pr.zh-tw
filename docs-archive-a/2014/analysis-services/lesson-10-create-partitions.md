---
title: 第11課：建立資料分割 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4db5edd5d47fe424ef6e6ad2a822106110209059
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584794"
---
# <a name="lesson-11-create-partitions"></a><span data-ttu-id="f9141-102">第 11 課：建立資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-102">Lesson 11: Create Partitions</span></span>
  <span data-ttu-id="f9141-103">在這一課，您將建立資料分割，以便將 [網際網路銷售] 資料表分成更小的邏輯部分，讓其他資料分割能夠單獨處理 (重新整理)。</span><span class="sxs-lookup"><span data-stu-id="f9141-103">In this lesson, you will create partitions to divide the Internet Sales table into smaller logical parts that can be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="f9141-104">根據預設，您在模型中包含的每個資料表都有一個資料分割，其中包含資料表的所有資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="f9141-104">By default, every table you include in your model has one partition which includes all of the table's columns and rows.</span></span> <span data-ttu-id="f9141-105">針對 [網際網路銷售] 資料表，我們想要依年份分割資料;每一個資料表的五年都會有一個資料分割。</span><span class="sxs-lookup"><span data-stu-id="f9141-105">For the Internet Sales table, we want to divide the data by year; one partition for each of the table's five years.</span></span>  <span data-ttu-id="f9141-106">接著，每個資料分割就可以單獨處理。</span><span class="sxs-lookup"><span data-stu-id="f9141-106">Each partition can then be processed independently.</span></span> <span data-ttu-id="f9141-107">如需詳細資訊，請參閱[資料分割 &#40;SSAS 表格式&#41;](tabular-models/partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="f9141-107">To learn more, see [Partitions &#40;SSAS Tabular&#41;](tabular-models/partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="f9141-108">完成本課程的估計時間： **15 分鐘**</span><span class="sxs-lookup"><span data-stu-id="f9141-108">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f9141-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f9141-109">Prerequisites</span></span>  
 <span data-ttu-id="f9141-110">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="f9141-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="f9141-111">在執行本課中的工作之前，您應已完成上一課： [第 10 課：建立階層](lesson-9-create-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="f9141-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 10: Create Hierarchies](lesson-9-create-hierarchies.md).</span></span>  
  
## <a name="create-partitions"></a><span data-ttu-id="f9141-112">建立資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-112">Create Partitions</span></span>  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a><span data-ttu-id="f9141-113">在 [網際網路銷售額] 資料表中建立資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-113">To create partitions in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="f9141-114">在模型設計師中，依序按一下 [網際網路銷售]\*\*\*\* 資料表、[資料表]\*\*\*\* 功能表和 [資料分割]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9141-114">In the model designer, click on the **Internet Sales** table, then click on the **Table** menu, and then click **Partitions**.</span></span>  
  
     <span data-ttu-id="f9141-115">[資料分割管理員]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f9141-115">The **Partition Manager** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="f9141-116">在 [資料**分割管理員**] 對話方塊的 [資料分割 **] 中，** 按一下 [**網際網路銷售**] 資料分割。</span><span class="sxs-lookup"><span data-stu-id="f9141-116">In the **Partition Manager** dialog box, in **Partitions**, click the **Internet Sales** partition.</span></span>  
  
3.  <span data-ttu-id="f9141-117">在 [資料**分割名稱**] 中，將名稱變更為 `Internet Sales 2005` 。</span><span class="sxs-lookup"><span data-stu-id="f9141-117">In **Partition Name**, change the name to `Internet Sales 2005`.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="f9141-118">在繼續進行下一步之前，您會發現 [資料表預覽] 視窗中的資料行名稱是以來源的資料行名稱顯示模型資料表中包含的資料行 (已核取)。</span><span class="sxs-lookup"><span data-stu-id="f9141-118">Before continuing to the next step, notice the column names in the Table Preview window display those columns included in the model table (checked) with the column names from the source.</span></span> <span data-ttu-id="f9141-119">這是因為 [資料表預覽] 視窗是從來源資料表顯示資料行，而不是從模型資料表。</span><span class="sxs-lookup"><span data-stu-id="f9141-119">This is because the Table Preview window displays columns from the source table, not from the model table.</span></span>  
  
4.  <span data-ttu-id="f9141-120">選取位於預覽視窗右側上方的 [查詢編輯器]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f9141-120">Select the **Query Editor** button just above the right side of the preview window.</span></span>  
  
     <span data-ttu-id="f9141-121">由於您希望資料分割只包含特定期間內的資料列，因此必須包含 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="f9141-121">Because you want the partition to include only those rows within a certain period, you must include a WHERE clause.</span></span> <span data-ttu-id="f9141-122">您只能使用 SQL 陳述式建立 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="f9141-122">You can only create a WHERE clause by using a SQL Statement.</span></span>  
  
5.  <span data-ttu-id="f9141-123">在 [SQL 陳述式]\*\*\*\* 欄位中貼入下列陳述式，以取代現有的陳述式：</span><span class="sxs-lookup"><span data-stu-id="f9141-123">In the **SQL Statement** field, replace the existing statement by pasting in the following statement:</span></span>  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2005-01-01 00:00:00') AND ([OrderDate] < N'2006-01-01 00:00:00'))  
    ```  
  
     <span data-ttu-id="f9141-124">這個陳述式會指定資料分割應包含 OrderDate 為 2005 日曆年度之資料列中的所有資料，如 WHERE 子句中所指定。</span><span class="sxs-lookup"><span data-stu-id="f9141-124">This statement specifies the partition should include all of the data in those rows where the OrderDate is for the 2005 calendar year as specified in the WHERE clause.</span></span>  
  
6.  <span data-ttu-id="f9141-125">按一下 **[驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="f9141-125">Click **Validate**.</span></span>  
  
     <span data-ttu-id="f9141-126">請注意，此時會顯示一個警告，指出特定資料行不存在來源中。</span><span class="sxs-lookup"><span data-stu-id="f9141-126">Notice a warning is displayed stating that certain columns are not present in source.</span></span> <span data-ttu-id="f9141-127">這是因為在[第3課：重新命名資料行](rename-columns.md)中，您將模型中的 [網際網路銷售] 資料表中的資料行重新命名，與來源上的相同資料行不同。</span><span class="sxs-lookup"><span data-stu-id="f9141-127">This is because in [Lesson 3: Rename Columns](rename-columns.md), you renamed those columns in the Internet Sales table in the model to be different from those same columns at the source.</span></span>  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a><span data-ttu-id="f9141-128">若要在網際網路銷售資料表中建立2006年的資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-128">To create a partition for the 2006 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="f9141-129">在 [資料**分割管理員**] 對話方塊的 [資料分割 **] 中，** 按一下 `Internet Sales 2005` 您剛才建立的資料分割，然後**複製**。</span><span class="sxs-lookup"><span data-stu-id="f9141-129">In the **Partition Manager** dialog box, in **Partitions**, click the `Internet Sales 2005` partition you just created, and then **Copy**.</span></span>  
  
2.  <span data-ttu-id="f9141-130">在 [資料**分割名稱**] 中，輸入 `Internet Sales 2006` 。</span><span class="sxs-lookup"><span data-stu-id="f9141-130">In **Partition Name**, type `Internet Sales 2006`.</span></span>  
  
3.  <span data-ttu-id="f9141-131">在 SQL 語句中，若要讓資料分割只包含2006年的資料列，請將 WHERE 子句取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="f9141-131">In the SQL Statement, in-order for the partition to include only those rows for the 2006 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a><span data-ttu-id="f9141-132">若要在網際網路銷售資料表中建立2007年的資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-132">To create a partition for the 2007 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="f9141-133">在 [資料分割管理員]\*\*\*\* 對話方塊中，按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9141-133">In the **Partition Manager** dialog box, click **Copy**.</span></span>  
  
2.  <span data-ttu-id="f9141-134">在 [資料**分割名稱**] 中，輸入 `Internet Sales 2007` 。</span><span class="sxs-lookup"><span data-stu-id="f9141-134">In **Partition Name**, type `Internet Sales 2007`.</span></span>  
  
3.  <span data-ttu-id="f9141-135">在 [**切換至**] 中，選取 [**查詢編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="f9141-135">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="f9141-136">在 SQL 語句中，若要讓資料分割只包含2007年的資料列，請將 WHERE 子句取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="f9141-136">In the SQL Statement, in-order for the partition to include only those rows for the 2007 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a><span data-ttu-id="f9141-137">若要在網際網路銷售資料表中建立2008年的資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-137">To create a partition for the 2008 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="f9141-138">在 [資料分割管理員]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9141-138">In the **Partition Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="f9141-139">在 [資料**分割名稱**] 中，輸入 `Internet Sales 2008` 。</span><span class="sxs-lookup"><span data-stu-id="f9141-139">In **Partition Name**, type `Internet Sales 2008`.</span></span>  
  
3.  <span data-ttu-id="f9141-140">在 [**切換至**] 中，選取 [**查詢編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="f9141-140">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="f9141-141">在 SQL 語句中，若要讓資料分割只包含2008年的資料列，請將 WHERE 子句取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="f9141-141">In the SQL Statement, in-order for the partition to include only those rows for the 2008 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a><span data-ttu-id="f9141-142">若要在網際網路銷售資料表中建立 2009 年度的資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-142">To create a partition for the 2009 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="f9141-143">在 [資料分割管理員]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9141-143">In the **Partition Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="f9141-144">在 [資料**分割名稱**] 中，輸入 `Internet Sales 2009` 。</span><span class="sxs-lookup"><span data-stu-id="f9141-144">In **Partition Name**, type `Internet Sales 2009`.</span></span>  
  
3.  <span data-ttu-id="f9141-145">在 [**切換至**] 中，選取 [**查詢編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="f9141-145">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="f9141-146">在 SQL 陳述式中，將 WHERE 子句取代為下列子句，以便讓資料分割只包含 2009 年度的資料列：</span><span class="sxs-lookup"><span data-stu-id="f9141-146">In the SQL Statement, in-order for the partition to include only those rows for the 2009 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2009-01-01 00:00:00') AND ([OrderDate] < N'2010-01-01 00:00:00'))  
    ```  
  
## <a name="process-partitions"></a><span data-ttu-id="f9141-147">處理資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-147">Process Partitions</span></span>  
 <span data-ttu-id="f9141-148">在 [資料分割管理員]\*\*\*\* 對話方塊中，您會發現剛才建立的每個新資料分割名稱旁邊都有星號 (**\***)。</span><span class="sxs-lookup"><span data-stu-id="f9141-148">In the **Partition Manager** dialog box, notice the asterisk (**\***) next to the partition names for each of the new partitions you just created.</span></span> <span data-ttu-id="f9141-149">這表示資料分割尚未處理 (重新整理)。</span><span class="sxs-lookup"><span data-stu-id="f9141-149">This indicates that the partition has not been processed (refreshed).</span></span> <span data-ttu-id="f9141-150">當您建立新的資料分割時，應執行 [處理資料分割] 或 [處理資料表] 作業，重新整理這些資料分割中的資料。</span><span class="sxs-lookup"><span data-stu-id="f9141-150">When you create new partitions, you should run a Process Partitions or Process Table operation to refresh the data in those partitions.</span></span>  
  
#### <a name="to-process-internet-sales-partitions"></a><span data-ttu-id="f9141-151">處理網際網路銷售資料分割</span><span class="sxs-lookup"><span data-stu-id="f9141-151">To process Internet Sales partitions</span></span>  
  
1.  <span data-ttu-id="f9141-152">按一下 [確定]\*\*\*\* 關閉 [資料分割管理員]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f9141-152">Click **OK** to close the **Partition Manager** dialog box.</span></span>  
  
2.  <span data-ttu-id="f9141-153">在模型設計師中，依序按一下 [網際網路銷售]\*\*\*\* 資料表和 [模型]\*\*\*\* 功能表，然後指向 [處理]\*\*\*\* (重新整理)，再按一下 [處理資料分割]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9141-153">In the model designer, click the **Internet Sales** table, then click the **Model** menu, then point to **Process** (Refresh), and then click **Process Partitions**.</span></span>  
  
3.  <span data-ttu-id="f9141-154">在 [處理資料分割]\*\*\*\* 對話方塊中，確認 [模式]\*\*\*\* 設定為 [處理預設]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9141-154">In the **Process Partitions** dialog box, verify the **Mode** is set to **Process Default**.</span></span>  
  
4.  <span data-ttu-id="f9141-155">對於您建立的五個分割區，將 [處理]\*\*\*\* 資料行的核取方塊全部選取，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9141-155">Select the checkbox in the **Process** column for each of the five partitions you created, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f9141-156">如果系統提示您輸入模擬認證，請輸入您在第 2 課的步驟 6 中指定的 Windows 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="f9141-156">If you are prompted for Impersonation credentials, enter the Windows user name and password you specified in Lesson 2, step 6.</span></span>  
  
     <span data-ttu-id="f9141-157">[**資料處理**] 對話方塊隨即出現，並顯示每個分割區的處理詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f9141-157">The **Data Process** dialog box then appears and displays process details for each partition.</span></span> <span data-ttu-id="f9141-158">請注意，傳送給每個分割區的資料列數目都不同。</span><span class="sxs-lookup"><span data-stu-id="f9141-158">Notice that a different number of rows for each partition are transferred.</span></span> <span data-ttu-id="f9141-159">這是因為每個資料分割只包含 SQL 陳述式中的 WHERE 子句所指定年度的資料列。</span><span class="sxs-lookup"><span data-stu-id="f9141-159">This is because each partition includes only those rows for the year specified in the WHERE clause in the SQL Statement.</span></span> <span data-ttu-id="f9141-160">2010 年則沒有資料。</span><span class="sxs-lookup"><span data-stu-id="f9141-160">There is no data for the 2010 year.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f9141-161">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f9141-161">Next Steps</span></span>  
 <span data-ttu-id="f9141-162">若要繼續進行本教學課程，請前往下一課： [第 12 課：建立角色](lesson-11-create-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="f9141-162">To continue this tutorial, go to the next lesson: Lesson: [Lesson 12: Create Roles](lesson-11-create-roles.md).</span></span>  
  
  
