---
title: 資料來源視圖設計工具 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.f1
helpviewer_keywords:
- Data Source View Designer
ms.assetid: 6f40a074-761f-440b-a999-09b755bd86ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 31e70f3f9b577f44b9ebb61b5ae2975c0a129828
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702141"
---
# <a name="data-source-view-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="60f5d-102">資料來源檢視設計工具 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="60f5d-102">Data Source View Designer (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="60f5d-103">資料來源檢視 (DSV) 是外部關聯式資料來源的邏輯檢視，用來建立多維度模型中的 Cube 和維度。</span><span class="sxs-lookup"><span data-stu-id="60f5d-103">A data source view (DSV) is a logical view of an external relational data source used to create cubes and dimensions in a multidimensional model.</span></span>

 <span data-ttu-id="60f5d-104">在產生 DSV 之後，您可以在 **中使用** [資料來源檢視設計工具] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，直接處理 DSV，如果基礎資料來源遺漏了多維度模型所需的資料元素，這個方法很實用。</span><span class="sxs-lookup"><span data-stu-id="60f5d-104">After a DSV is generated, you can use the **Data Source View Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to work directly on the DSV, which can be useful if the underlying data source is missing data elements needed in a multidimensional model.</span></span>

 <span data-ttu-id="60f5d-105">若要開啟 **[資料來源檢視設計工具]** ：</span><span class="sxs-lookup"><span data-stu-id="60f5d-105">To open **Data Source View Designer** :</span></span>

-   <span data-ttu-id="60f5d-106">在方案總管\*\*\*\* 中按兩下資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="60f5d-106">Double-click a data source view in **Solution Explorer**.</span></span>

-   <span data-ttu-id="60f5d-107">以滑鼠右鍵按一下方案總管\*\*\*\* 中的資料來源檢視，然後選取 [開啟]\*\*\*\* 或 [檢視表設計工具]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60f5d-107">Right-click a data source view in **Solution Explorer** and select **Open** or **View Designer**.</span></span>

 <span data-ttu-id="60f5d-108">**[資料來源檢視設計工具]** 包含工具列、顯示 DSV 物件和關聯性的圖表、按照字母順序列出資料表和具名查詢的資料表窗格，以及用來建立及檢視 DSV 的特定圖表的 [圖表組合管理] 窗格。</span><span class="sxs-lookup"><span data-stu-id="60f5d-108">The **Data Source View Designer** contains a toolbar, a diagram showing the objects and relationships in the DSV, a table pane listing tables and named queries in alphabetical order, and a Diagram Organizer pane used to create and view specific diagrams of the DSV.</span></span> <span data-ttu-id="60f5d-109">您可以用滑鼠右鍵按一下資料表或關聯性，存取內容相關的命令。</span><span class="sxs-lookup"><span data-stu-id="60f5d-109">You can right-click a table or relationship to access context-sensitive commands.</span></span>

 <span data-ttu-id="60f5d-110">![資料來源檢視設計工具](media/ssas-dsvdesigner.PNG "資料來源檢視設計工具")</span><span class="sxs-lookup"><span data-stu-id="60f5d-110">![Data Source View Designer](media/ssas-dsvdesigner.PNG "Data Source View Designer")</span></span>

 <span data-ttu-id="60f5d-111">基本上，DSV 會顯示在處理期間要用來擴展模型物件的關聯式資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="60f5d-111">At a minimum, a DSV shows the relational database tables that will be used to populate model objects during processing.</span></span> <span data-ttu-id="60f5d-112">DSV 通常是使用資料來源檢視精靈產生。</span><span class="sxs-lookup"><span data-stu-id="60f5d-112">A DSV is generated, usually by using the Data Source View wizard.</span></span> <span data-ttu-id="60f5d-113">DSV 中的資料表、資料行和關聯性會成為 Cube 維度和量值的基礎。</span><span class="sxs-lookup"><span data-stu-id="60f5d-113">Tables, columns, and relationships in the DSV become the basis for dimensions and measures in a cube.</span></span> <span data-ttu-id="60f5d-114">一旦建立 DSV，您可以使用資料來源檢視設計工具來修改它。</span><span class="sxs-lookup"><span data-stu-id="60f5d-114">Once the DSV is created, you can use the Data Source View Designer to modify it.</span></span>

 <span data-ttu-id="60f5d-115">大部分 Analysis Services 開發人員直接使用產生的 DSV，極少自訂。</span><span class="sxs-lookup"><span data-stu-id="60f5d-115">Most Analysis Services developers use a generated DSV as is, with few customizations.</span></span> <span data-ttu-id="60f5d-116">如果來源資料來自於 SQL Server 資料庫檢視，這更是特別常見。</span><span class="sxs-lookup"><span data-stu-id="60f5d-116">This is especially common if source data originates from a view in a SQL Server database.</span></span> <span data-ttu-id="60f5d-117">在此情況下，您可能會想在 T-SQL 檢視中管理資料關聯性和計算，而不是 Analysis Services DSV。</span><span class="sxs-lookup"><span data-stu-id="60f5d-117">In this case, you might prefer to manage data relationships and calculations in a T-SQL view rather than an Analysis Services DSV.</span></span> <span data-ttu-id="60f5d-118">不過，如果您不是基礎資料庫的擁有者，您可以在 Analysis Services 中修改 DSV，進一步開發模型中所使用的資料結構。</span><span class="sxs-lookup"><span data-stu-id="60f5d-118">However, if you are not the owner of the underlying database, you can modify the DSV in Analysis Services to further develop the data structures used in your model.</span></span>

## <a name="tasks-in-data-source-view-designer"></a><span data-ttu-id="60f5d-119">資料來源檢視設計工具中的工作</span><span class="sxs-lookup"><span data-stu-id="60f5d-119">Tasks in Data Source View Designer</span></span>
 <span data-ttu-id="60f5d-120">使用資料來源檢視設計工具，您可以對 DSV 執行下列編輯：</span><span class="sxs-lookup"><span data-stu-id="60f5d-120">Using Data Source View Designer, you can make the following edits to a DSV:</span></span>

|||
|-|-|
|<span data-ttu-id="60f5d-121">重新命名資料行或資料表，或建立新的導出資料行。</span><span class="sxs-lookup"><span data-stu-id="60f5d-121">Rename columns or tables, or create new calculated columns.</span></span> <span data-ttu-id="60f5d-122">例如，將姓氏和名字串連成新的全名資料行。</span><span class="sxs-lookup"><span data-stu-id="60f5d-122">For example, concatenate a first name and last name into a new full-name column.</span></span>|[<span data-ttu-id="60f5d-123">在資料來源檢視中定義具名計算 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="60f5d-123">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="60f5d-124">手動加入資料表關聯性</span><span class="sxs-lookup"><span data-stu-id="60f5d-124">Manually add table relationships</span></span>|[<span data-ttu-id="60f5d-125">在資料來源檢視中定義邏輯關聯性 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="60f5d-125">Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-logical-relationships-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="60f5d-126">建立具名查詢，依據 T-SQL 查詢定義新物件。</span><span class="sxs-lookup"><span data-stu-id="60f5d-126">Create a named query to define a new object based on a T-SQL query.</span></span>|[<span data-ttu-id="60f5d-127">在資料來源檢視中定義具名查詢 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="60f5d-127">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="60f5d-128">瀏覽基礎資料，檢視模型物件所代表的實際資料值。</span><span class="sxs-lookup"><span data-stu-id="60f5d-128">Explore underlying data to view actual data values represented by model objects.</span></span><br /><br /> <span data-ttu-id="60f5d-129">資料瀏覽可讓您以視覺化方式檢查及複製從基礎維度資料表或查詢傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="60f5d-129">Data exploration lets you visually inspect and copy data that is returned from the underlying dimensional table or query.</span></span> <span data-ttu-id="60f5d-130">根據預設，資料瀏覽使用最高計數取樣方法，取樣計數為 5000，但是您可以修訂這些設定。</span><span class="sxs-lookup"><span data-stu-id="60f5d-130">By default, data exploration uses the top count sampling methodology, with a sample count of 5000, but you can revise these settings.</span></span>|[<span data-ttu-id="60f5d-131">在資料來源檢視中瀏覽資料 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="60f5d-131">Explore Data in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/explore-data-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="60f5d-132">將 DSV 中全部或部分的資料表和關聯性建立成圖表</span><span class="sxs-lookup"><span data-stu-id="60f5d-132">Diagram all or part of the tables and relationships in a DSV</span></span>|[<span data-ttu-id="60f5d-133">在資料來源檢視設計工具中使用圖表 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="60f5d-133">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)|

## <a name="see-also"></a><span data-ttu-id="60f5d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60f5d-134">See Also</span></span>
 <span data-ttu-id="60f5d-135">多[維度模型中的資料來源視圖](multidimensional-models/data-source-views-in-multidimensional-models.md)[加入或移除資料來源視圖中的資料表或視圖 &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="60f5d-135">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) [Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)</span></span>


