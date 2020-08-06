---
title: 在資料來源視圖中定義已命名的查詢 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- named queries [Analysis Services], creating
- modifying named queries
- data source views [Analysis Services], named queries
ms.assetid: f09ba8aa-950e-4c0d-961e-970de13200be
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfe2dbc6081e0c33f681ba894b16057c8890e0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593658"
---
# <a name="define-named-queries-in-a-data-source-view-analysis-services"></a><span data-ttu-id="1e6e4-102">在資料來源檢視中定義具名查詢 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1e6e4-102">Define Named Queries in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="1e6e4-103">具名查詢是以資料表代表的 SQL 運算式。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-103">A named query is a SQL expression represented as a table.</span></span> <span data-ttu-id="1e6e4-104">在具名查詢中，您可以指定 SQL 運算式，來選取在一個或多個資料來源中的一個或多個資料表所傳回的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-104">In a named query, you can specify an SQL expression to select rows and columns returned from one or more tables in one or more data sources.</span></span> <span data-ttu-id="1e6e4-105">具名查詢就像資料來源檢視 (DSV) 中具有資料列和關聯性的其他任何資料表一樣，差別在於具名查詢是以運算式為基礎。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-105">A named query is like any other table in a data source view (DSV) with rows and relationships, except that the named query is based on an expression.</span></span>  
  
 <span data-ttu-id="1e6e4-106">具名查詢可讓您擴充 DSV 中之現有資料表的關聯式結構描述，不需修改基礎資料來源。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-106">A named query lets you extend the relational schema of existing tables in DSV without modifying the underlying data source.</span></span> <span data-ttu-id="1e6e4-107">例如，一系列具名查詢可以將複雜的維度資料表分割為較小、較簡單的維度資料表，以供資料庫維度使用。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-107">For example, a series of named queries can be used to split up a complex dimension table into smaller, simpler dimension tables for use in database dimensions.</span></span> <span data-ttu-id="1e6e4-108">具名查詢也可以用來將一個或多個資料來源中的多個資料庫資料表聯結到單一資料來源檢視資料表中。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-108">A named query can also be used to join multiple database tables from one or more data sources into a single data source view table.</span></span>  
  
## <a name="creating-a-named-query"></a><span data-ttu-id="1e6e4-109">建立具名查詢</span><span class="sxs-lookup"><span data-stu-id="1e6e4-109">Creating a Named Query</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e6e4-110">您無法將具名計算加入具名查詢中，也不可以用包含具名計算的資料表做為具名查詢的基礎。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-110">You cannot add a named calculation to a named query, nor can you base a named query on a table that contains a named calculation.</span></span>  
  
 <span data-ttu-id="1e6e4-111">在建立具名查詢時，您需要指定名稱、傳回資料表的資料行和資料的 SQL 查詢，以及 (選擇性) 具名查詢的描述。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-111">When you create a named query, you specify a name, the SQL query returning the columns and data for the table, and optionally, a description of the named query.</span></span> <span data-ttu-id="1e6e4-112">SQL 運算式可以參考資料來源檢視中的其他資料表。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-112">The SQL expression can refer to other tables in the data source view.</span></span> <span data-ttu-id="1e6e4-113">定義具名查詢之後，具名查詢中的 SQL 查詢會傳送至資料來源的提供者，並以整體方式驗證。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-113">After the named query is defined, the SQL query in a named query is sent to the provider for the data source and validated as a whole.</span></span> <span data-ttu-id="1e6e4-114">如果提供者在 SQL 查詢中找不到任何錯誤，資料行就會加入資料表中。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-114">If the provider does not find any errors in the SQL query, the column is added to the table.</span></span>  
  
 <span data-ttu-id="1e6e4-115">SQL 查詢中被參考的資料表和資料行不應該限定，或應該只以資料表名稱來限定。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-115">Tables and columns referenced in the SQL query should not be qualified or should be qualified by the table name only.</span></span> <span data-ttu-id="1e6e4-116">例如，若要參考資料表中的 SaleAmount 資料行， `SaleAmount` 或 `Sales.SaleAmount` 為有效，但 `dbo.Sales.SaleAmount` 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-116">For example, to refer to the SaleAmount column in a table, `SaleAmount` or `Sales.SaleAmount` is valid, but `dbo.Sales.SaleAmount` generates an error.</span></span>  
  
 <span data-ttu-id="1e6e4-117">**注意** ：定義查詢 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 資料來源的具名查詢時，包含相關子查詢與 GROUP BY 子句的具名查詢將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-117">**Note** When defining a named query that queries a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 data source, a named query that contains a correlated subquery and a GROUP BY clause will fail.</span></span> <span data-ttu-id="1e6e4-118">如需詳細資訊，請參閱 [知識庫中的](https://support.microsoft.com/kb/274729) Internal Error with SELECT Statement Containing Correlated Subquery and GROUP BY [!INCLUDE[msCoName](../../includes/msconame-md.md)] (包含相互關聯之子查詢和 GROUP BY 的 SELECT 陳述式發生內部錯誤)。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-118">For more information, see [Internal Error with SELECT Statement Containing Correlated Subquery and GROUP BY](https://support.microsoft.com/kb/274729) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base.</span></span>  
  
## <a name="add-or-edit-a-named-query"></a><span data-ttu-id="1e6e4-119">加入或編輯具名查詢</span><span class="sxs-lookup"><span data-stu-id="1e6e4-119">Add or Edit a Named Query</span></span>  
  
1.  <span data-ttu-id="1e6e4-120">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟含有您想在其中加入具名查詢之資料來源檢視的專案，或連接到包含此資料來源檢視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to add a named query.</span></span>  
  
2.  <span data-ttu-id="1e6e4-121">在方案總管中，展開 [資料來源檢視]\*\*\*\* 資料夾，然後按兩下資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-121">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="1e6e4-122">在 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格中，以滑鼠右鍵按一下開放區域，然後按一下 [新增具名查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-122">In the **Tables** or **Diagram** pane, right-click an open area and then click **New Named Query**.</span></span>  
  
4.  <span data-ttu-id="1e6e4-123">在 [建立具名查詢]\*\*\*\* 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1e6e4-123">In the **Create Named Query** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="1e6e4-124">在 [名稱]\*\*\*\* 文字方塊中，輸入查詢名稱。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-124">In the **Name** text box, type a query name.</span></span>  
  
    2.  <span data-ttu-id="1e6e4-125">可以選擇在 [描述]\*\*\*\* 文字方塊中輸入查詢的描述。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-125">Optionally, in the **Description** text box, type a description for the query.</span></span>  
  
    3.  <span data-ttu-id="1e6e4-126">在 [資料來源]\*\*\*\* 清單方塊中，選取具名查詢執行時所要針對的資料來源。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-126">In the **Data Source** list box, select the data source against which the named query will execute.</span></span>  
  
    4.  <span data-ttu-id="1e6e4-127">在下方窗格中輸入查詢，或是使用圖形化查詢建立工具來建立查詢。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-127">Type the query in the bottom pane, or use the graphical query building tools to create a query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1e6e4-128">請注意，建立查詢的使用者介面 (UI) 需視資料來源而定；</span><span class="sxs-lookup"><span data-stu-id="1e6e4-128">The query-building user interface (UI) depends on the data source.</span></span> <span data-ttu-id="1e6e4-129">您可以取得一般文字式 UI，而非圖形 UI。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-129">Instead of getting a graphical UI, you can get a generic UI, which is text-based.</span></span> <span data-ttu-id="1e6e4-130">您可以使用不同的 UI 來完成相同的工作，但必須以不同的方式執行。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-130">You can accomplish the same things with these different UIs, but you must do so in different ways.</span></span> <span data-ttu-id="1e6e4-131">如需詳細資訊，請參閱[建立/編輯具名查詢對話方塊 &#40;Analysis Services - 多維度資料&#41;](../create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-131">For more information, see [Create or Edit Named Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
5.  <span data-ttu-id="1e6e4-132">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-132">Click **OK**.</span></span> <span data-ttu-id="1e6e4-133">資料表頁首會出現表示兩個重疊資料表的圖示，指出資料表已取代為具名查詢。</span><span class="sxs-lookup"><span data-stu-id="1e6e4-133">An icon showing two overlapping tables appears in the table header to indicate that the table has been replaced by a named query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e6e4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e6e4-134">See Also</span></span>  
 <span data-ttu-id="1e6e4-135">[多維度模型中的資料來源視圖](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="1e6e4-135">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="1e6e4-136">在資料來源檢視中定義具名計算 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1e6e4-136">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
