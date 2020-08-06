---
title: 在資料來源視圖中定義已命名的計算 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying named calculations
- data source views [Analysis Services], named calculations
- named calculations [Analysis Services]
ms.assetid: 729e7b12-6185-4b73-8bcb-cfe459b15355
author: minewiskan
ms.author: owend
ms.openlocfilehash: ae901c340fe29c042430d928a4abaea8e8cfe84b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596381"
---
# <a name="define-named-calculations-in-a-data-source-view-analysis-services"></a><span data-ttu-id="1a238-102">在資料來源檢視中定義具名計算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1a238-102">Define Named Calculations in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="1a238-103">具名計算是以導出資料行表示的 SQL 運算式。</span><span class="sxs-lookup"><span data-stu-id="1a238-103">A named calculation is a SQL expression represented as a calculated column.</span></span> <span data-ttu-id="1a238-104">此運算式的顯示和行為如同資料表中的資料行一樣。</span><span class="sxs-lookup"><span data-stu-id="1a238-104">This expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="1a238-105">具名計算可讓您在資料來源檢視中擴充現有資料表或檢視表的關聯式結構描述，而不必修改基礎資料來源中的資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="1a238-105">A named calculation lets you extend the relational schema of existing tables or views in a data source view without modifying the tables or views in the underlying data source.</span></span> <span data-ttu-id="1a238-106">請考慮以下範例：</span><span class="sxs-lookup"><span data-stu-id="1a238-106">Consider the following examples:</span></span>

-   <span data-ttu-id="1a238-107">建立衍生自事實資料表之多個資料行的單一具名計算 (例如透過將稅率乘以銷售價格來建立「稅額」)。</span><span class="sxs-lookup"><span data-stu-id="1a238-107">Create a single named calculation that is derived from multiple columns in a fact table (for example, creating Tax Amount by multiplying a tax rate by a sales price).</span></span>

-   <span data-ttu-id="1a238-108">為維度成員建構使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="1a238-108">Construct a user friendly name for a dimension member.</span></span>

-   <span data-ttu-id="1a238-109">在 DSV 中建立具名計算，而不是在 Cube 中建立導出成員，以提升查詢效能。</span><span class="sxs-lookup"><span data-stu-id="1a238-109">As a query performance enhancement, create a named calculation in the DSV instead of creating a calculated member in a cube.</span></span> <span data-ttu-id="1a238-110">具名計算是在處理期間所計算，而導出成員則是在查詢時所計算。</span><span class="sxs-lookup"><span data-stu-id="1a238-110">Named calculations are calculated during processing whereas calculated members are calculated at query time.</span></span>

## <a name="creating-named-calculations"></a><span data-ttu-id="1a238-111">建立具名計算</span><span class="sxs-lookup"><span data-stu-id="1a238-111">Creating Named Calculations</span></span>

> [!NOTE]
>  <span data-ttu-id="1a238-112">您無法將具名計算加入具名查詢中，也不可以用包含具名計算的資料表做為具名查詢的基礎。</span><span class="sxs-lookup"><span data-stu-id="1a238-112">You cannot add a named calculation to a named query, nor can you base a named query on a table that contains a named calculation.</span></span>

 <span data-ttu-id="1a238-113">當您建立具名計算時，要指定名稱、SQL 運算式和計算的描述 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="1a238-113">When you create a named calculation, you specify a name, the SQL expression, and, optionally, a description of the calculation.</span></span> <span data-ttu-id="1a238-114">SQL 運算式可以參考資料來源檢視中的其他資料表。</span><span class="sxs-lookup"><span data-stu-id="1a238-114">The SQL expression can refer to other tables in the data source view.</span></span> <span data-ttu-id="1a238-115">在定義具名計算之後，具名計算中的運算式會傳送給資料來源的提供者，並驗證為下列 SQL 陳述式，其中 `<Expression>` 包含定義具名計算的運算式。</span><span class="sxs-lookup"><span data-stu-id="1a238-115">After the named calculation is defined, the expression in a named calculation is sent to the provider for the data source and validated as the following SQL statement in which `<Expression>` contains the expression that defines the named calculation.</span></span>

```
SELECT 
   <Table Name in Data Source>.*, 
   <Expression> AS <Column Name> 
FROM 
   <Table Name in Data Source> AS <Table Name in Data Source View>
```

 <span data-ttu-id="1a238-116">資料行的資料類型是由運算式所傳回之純量值的資料類型來決定。</span><span class="sxs-lookup"><span data-stu-id="1a238-116">The data type of the column is determined by the data type of the scalar value returned by the expression.</span></span> <span data-ttu-id="1a238-117">如果提供者在運算式中找不到任何錯誤，則資料行會加入資料表中。</span><span class="sxs-lookup"><span data-stu-id="1a238-117">If the provider does not find any errors in the expression, the column is added to the table.</span></span>

 <span data-ttu-id="1a238-118">在運算式中所參考的資料行不應該限定，或只能由資料表名稱加以限定。</span><span class="sxs-lookup"><span data-stu-id="1a238-118">Columns referenced in the expression should not be qualified or should be qualified by the table name only.</span></span> <span data-ttu-id="1a238-119">例如，若要參考資料表中的 SaleAmount 資料行， `SaleAmount` 或 `Sales.SaleAmount` 為有效，但 `dbo.Sales.SaleAmount` 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a238-119">For example, to refer to the SaleAmount column in a table, `SaleAmount` or `Sales.SaleAmount` is valid, but `dbo.Sales.SaleAmount` generates an error.</span></span>

 <span data-ttu-id="1a238-120">運算式不會自動用括號括住。</span><span class="sxs-lookup"><span data-stu-id="1a238-120">The expression is not automatically enclosed between parentheses.</span></span> <span data-ttu-id="1a238-121">因此，如果運算式 (例如 SELECT 陳述式) 需要括號，您必須在 [運算式]\*\*\*\* 方塊中輸入括號。</span><span class="sxs-lookup"><span data-stu-id="1a238-121">Therefore, if an expression, such as a SELECT statement, requires parentheses, you must type the parentheses in the **Expression** box.</span></span> <span data-ttu-id="1a238-122">例如，唯有輸入括號，下列運算式才有效。</span><span class="sxs-lookup"><span data-stu-id="1a238-122">For example, the following expression is valid only if you type the parentheses.</span></span>

```
(SELECT Description FROM Categories WHERE Categories.CategoryID = CategoryID)
```

## <a name="add-or-edit-a-named-calculation"></a><span data-ttu-id="1a238-123">加入或編輯具名計算</span><span class="sxs-lookup"><span data-stu-id="1a238-123">Add or Edit a Named Calculation</span></span>

1.  <span data-ttu-id="1a238-124">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟含有您想在其中定義具名計算之資料來源檢視的專案，或連接到包含此資料來源檢視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a238-124">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to define a named calculation.</span></span>

2.  <span data-ttu-id="1a238-125">在方案總管中，展開 [資料來源檢視]\*\*\*\* 資料夾，然後按兩下資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="1a238-125">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>

3.  <span data-ttu-id="1a238-126">在 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格中，以滑鼠右鍵按一下您想要在其中定義具名計算的資料表，然後按一下 [新增具名計算]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1a238-126">Right-click the table in which you wish to define the named calculation in either the **Tables** or the **Diagram** pane, and then click **New Named Calculation**.</span></span> <span data-ttu-id="1a238-127">請務必在資料表名稱上按一下滑鼠右鍵，而不是在屬性上。</span><span class="sxs-lookup"><span data-stu-id="1a238-127">Be sure to right-click on the table name, and not on an attribute.</span></span> <span data-ttu-id="1a238-128">功能表應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="1a238-128">The menu should look like the following:</span></span>

     <span data-ttu-id="1a238-129">![圖表工作空間的螢幕擷取畫面，以滑鼠右鍵按一下功能表](../media/ssas-olapdsv-diagram.gif "圖表工作空間的螢幕擷取畫面，以滑鼠右鍵按一下功能表")</span><span class="sxs-lookup"><span data-stu-id="1a238-129">![Screenshot of diagram workspace, right-click menu](../media/ssas-olapdsv-diagram.gif "Screenshot of diagram workspace, right-click menu")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="1a238-130">若要尋找資料表或檢視表，您可以按一下 [資料來源檢視]\*\*\*\* 功能表，或是以滑鼠右鍵按一下 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格的開放區域，即可使用 [尋找資料表]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="1a238-130">To locate a table or view, you can use the **Find Table** option by either clicking the **Data Source View** menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>

4.  <span data-ttu-id="1a238-131">在 [建立具名計算]\*\*\*\* 對話方塊中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1a238-131">In the **Create Named Calculations** dialog box, do the following:</span></span>

    -   <span data-ttu-id="1a238-132">在 [資料行名稱]\*\*\*\* 文字方塊中，輸入新資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="1a238-132">In the **Column name** text box, type the name of the new column.</span></span>

    -   <span data-ttu-id="1a238-133">在 [描述]\*\*\*\* 文字方塊中，輸入新資料行的描述。</span><span class="sxs-lookup"><span data-stu-id="1a238-133">In the **Description** text box type a description for the new column.</span></span>

    -   <span data-ttu-id="1a238-134">在 [運算式]\*\*\*\* 文字方塊中，輸入會使用適合資料提供者的 SQL 用語來產生新資料行內容的運算式。</span><span class="sxs-lookup"><span data-stu-id="1a238-134">In the **Expression** text box, type the expression that yields the content of the new column in the SQL dialect appropriate for the data provider.</span></span>

5.  <span data-ttu-id="1a238-135">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="1a238-135">Click **OK**.</span></span>

     <span data-ttu-id="1a238-136">具名計算資料行會顯示為資料來源檢視資料表中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="1a238-136">The named calculation column appears as the last column in the data source view table.</span></span> <span data-ttu-id="1a238-137">計算機符號表示資料行包含具名計算。</span><span class="sxs-lookup"><span data-stu-id="1a238-137">A calculator symbol indicates that the column contains a named calculation.</span></span>

## <a name="delete-a-named-calculation"></a><span data-ttu-id="1a238-138">刪除具名計算</span><span class="sxs-lookup"><span data-stu-id="1a238-138">Delete a Named Calculation</span></span>
 <span data-ttu-id="1a238-139">當您嘗試刪除具名計算時，會出現一個提示，此提示會列出將會因為此刪除動作而變成無效之專案或資料庫中定義的物件清單。</span><span class="sxs-lookup"><span data-stu-id="1a238-139">When you attempt to delete a named calculation, you are prompted with a list of the objects defined in the project or database that will be invalidated by the deletion.</span></span> <span data-ttu-id="1a238-140">仔細檢閱清單，再刪除計算。</span><span class="sxs-lookup"><span data-stu-id="1a238-140">Review the list carefully before deleting the calculation.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a238-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a238-141">See Also</span></span>
 [<span data-ttu-id="1a238-142">在資料來源檢視中定義具名查詢 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1a238-142">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-queries-in-a-data-source-view-analysis-services.md)


