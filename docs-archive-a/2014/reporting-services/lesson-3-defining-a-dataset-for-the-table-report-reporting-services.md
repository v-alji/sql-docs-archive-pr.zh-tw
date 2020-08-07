---
title: 第 3 課：定義資料表報表的資料集 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 33fe48a60db2e7d15d205a4bff6205347f95c61c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593858"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a><span data-ttu-id="cae5f-102">第 3 課：定義資料表報表的資料集 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="cae5f-102">Lesson 3: Defining a Dataset for the Table Report (Reporting Services)</span></span>
  <span data-ttu-id="cae5f-103">當您定義資料來源之後，就需要定義資料集。</span><span class="sxs-lookup"><span data-stu-id="cae5f-103">After you define the data source, you need to define a dataset.</span></span> <span data-ttu-id="cae5f-104">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中，報表所用的資料是包含在「資料集」\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="cae5f-104">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], data that you use in reports is contained in a *dataset*.</span></span> <span data-ttu-id="cae5f-105">資料集含有指向資料來源的指標和報表要用的查詢，以及計算的欄位和變數。</span><span class="sxs-lookup"><span data-stu-id="cae5f-105">A dataset includes a pointer to a data source and a query to be used by the report, as well as calculated fields and variables.</span></span>  
  
 <span data-ttu-id="cae5f-106">您可以使用報表設計師中的查詢設計工具來設計查詢。</span><span class="sxs-lookup"><span data-stu-id="cae5f-106">You can use the query designer in Report Designer to design the query.</span></span> <span data-ttu-id="cae5f-107">在本教學課程中，您將建立可從2008資料庫中抓取銷售訂單資訊的查詢 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] **2008** 。</span><span class="sxs-lookup"><span data-stu-id="cae5f-107">For this tutorial, you will create a query that retrieves sales order information from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]**2008** database.</span></span>  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a><span data-ttu-id="cae5f-108">若要定義報表資料的 Transact-SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="cae5f-108">To define a Transact-SQL query for report data</span></span>  
  
1.  <span data-ttu-id="cae5f-109">在 [**報表資料**] 窗格中，按一下 [**新增**]，然後按一下 [**資料集**...]。[**資料集屬性**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="cae5f-109">In the **Report Data** pane, click **New**, and then click **Dataset...**. The **Dataset Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="cae5f-110">在 [名稱]\*\*\*\* 方塊中，鍵 **AdventureWorksDataset**。</span><span class="sxs-lookup"><span data-stu-id="cae5f-110">In the **Name** box, type **AdventureWorksDataset**.</span></span>  
  
3.  <span data-ttu-id="cae5f-111">按一下 **[使用內嵌在我的報表中的資料集]**。</span><span class="sxs-lookup"><span data-stu-id="cae5f-111">Click **Use a dataset embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="cae5f-112">請確定您的資料來源名稱 AdventureWorks2012 是在 [**資料來源**] 文字方塊中，而且**查詢類型**是 [**文字**]。</span><span class="sxs-lookup"><span data-stu-id="cae5f-112">Make sure the name of your data source, AdventureWorks2012, is in the **Data source** text box, and that the **Query type** is **Text**.</span></span>  
  
5.  <span data-ttu-id="cae5f-113">在 [查詢]\*\*\*\* 方塊中，鍵入 (或複製和貼上) 下列 Transact-SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="cae5f-113">Type, or copy and paste, the following Transact-SQL query into the **Query** box.</span></span>  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
6.  <span data-ttu-id="cae5f-114">(選擇性) 按一下 [查詢設計工具]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cae5f-114">(Optional) Click the **Query Designer** button.</span></span> <span data-ttu-id="cae5f-115">查詢會顯示在以文字為基礎的查詢設計工具中。</span><span class="sxs-lookup"><span data-stu-id="cae5f-115">The query is displayed in the text-based query designer.</span></span> <span data-ttu-id="cae5f-116">您可以按一下 [當成文字編輯]\*\*\*\*，切換到圖形化查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="cae5f-116">You can toggle to the graphical query designer by clicking **Edit As Text**.</span></span> <span data-ttu-id="cae5f-117">按一下 [查詢設計工具] 工具列上的 [執行\*\* (！ ) \*\* ] 按鈕，以查看查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="cae5f-117">View the results of the query by clicking the run **(!)** button on the query designer toolbar.</span></span>  
  
     <span data-ttu-id="cae5f-118">您可以在 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫中看到 4 個不同資料表的 6 個欄位。</span><span class="sxs-lookup"><span data-stu-id="cae5f-118">You see the data from six fields from four different tables in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="cae5f-119">查詢會使用別名之類的 Transact-SQL 功能。</span><span class="sxs-lookup"><span data-stu-id="cae5f-119">The query makes use of Transact-SQL functionality such as aliases.</span></span> <span data-ttu-id="cae5f-120">例如，SalesOrderHeader 資料表稱為 soh。</span><span class="sxs-lookup"><span data-stu-id="cae5f-120">For example, the SalesOrderHeader table is called soh.</span></span>  
  
     <span data-ttu-id="cae5f-121">按一下 [確定]\*\*\*\* 結束查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="cae5f-121">Click **OK** to exit the query designer.</span></span>  
  
7.  <span data-ttu-id="cae5f-122">按一下 [確定]\*\*\*\* 結束 [資料集屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cae5f-122">Click **OK** to exit the **Dataset Properties** dialog box.</span></span>  
  
     <span data-ttu-id="cae5f-123">您的 **AdventureWorksDataset** 資料集和欄位會顯示在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="cae5f-123">Your **AdventureWorksDataset** dataset and fields appear in the Report Data pane.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="cae5f-124">下一項工作</span><span class="sxs-lookup"><span data-stu-id="cae5f-124">Next Task</span></span>  
 <span data-ttu-id="cae5f-125">您已順利指定一項擷取報表資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="cae5f-125">You have successfully specified a query that retrieves data for your report.</span></span> <span data-ttu-id="cae5f-126">之後，您要建立報表配置。</span><span class="sxs-lookup"><span data-stu-id="cae5f-126">Next, you will create the report layout.</span></span> <span data-ttu-id="cae5f-127">請參閱[第 4 課：將資料表新增至報表 &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cae5f-127">See [Lesson 4: Adding a Table to the Report &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae5f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cae5f-128">See Also</span></span>  
 <span data-ttu-id="cae5f-129">[報表設計師 SQL Server Data Tools &#40;SSRS&#41;中的查詢設計工具](report-data/query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cae5f-129">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) </span></span>  
 <span data-ttu-id="cae5f-130">[SQL Server &#40;SSRS&#41;的連線類型](report-data/sql-server-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cae5f-130">[SQL Server Connection Type &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) </span></span>  
 [<span data-ttu-id="cae5f-131">教學課程：撰寫 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="cae5f-131">Tutorial: Writing Transact-SQL Statements</span></span>](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
