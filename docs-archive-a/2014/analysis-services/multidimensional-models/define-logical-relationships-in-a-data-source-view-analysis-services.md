---
title: 在資料來源視圖中定義邏輯關聯性 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- adding relationships
- relationships [Analysis Services], data source views
- data source views [Analysis Services], relationships
ms.assetid: a20d6dae-e769-4131-8a59-7ef56f174220
author: minewiskan
ms.author: owend
ms.openlocfilehash: c46c2b360a4528aeb0eb88348d0d1242b22d8ef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596386"
---
# <a name="define-logical-relationships-in-a-data-source-view-analysis-services"></a><span data-ttu-id="7d1ad-102">在資料來源檢視中定義邏輯關聯性 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="7d1ad-102">Define Logical Relationships in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="7d1ad-103">[資料來源檢視精靈] 和資料來源檢視設計工具會根據基礎資料庫關聯性，或是根據您所指定的名稱比對準則，自動定義加入到資料來源檢視 (DSV) 之資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-103">The Data Source View Wizard and Data Source View Designer automatically define relationships between tables added to a data source view (DSV) based on underlying database relationships or name matching criteria you specify.</span></span>  
  
 <span data-ttu-id="7d1ad-104">在使用多個資料來源之資料的情況下，您可能需要在 DSV 中手動定義邏輯關聯性，以補充那些自動定義的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-104">In cases where you are working with data from multiple data sources, you may need to manually define logical relationships in the DSV to supplement those relationships that are defined automatically.</span></span> <span data-ttu-id="7d1ad-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 需要關聯性來識別事實資料表和維度資料表、建構查詢以從基礎資料來源擷取資料和中繼資料，以及利用進階的商業智慧功能。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-105">Relationships are required in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to identify fact and dimension tables, to construct queries for retrieving data and metadata from underlying data sources, and to take advantage of advanced business intelligence features.</span></span>  
  
 <span data-ttu-id="7d1ad-106">您可以在資料來源檢視設計師中定義以下類型的關聯性：</span><span class="sxs-lookup"><span data-stu-id="7d1ad-106">You can define the following types of relationships in Data Source View Designer:</span></span>  
  
-   <span data-ttu-id="7d1ad-107">相同資料來源中不同資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-107">A relationship from one table to another table in the same data source.</span></span>  
  
-   <span data-ttu-id="7d1ad-108">資料表與本身的關聯性，如同父子關聯性一樣。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-108">A relationship from one table to itself, as in a parent-child relationship.</span></span>  
  
-   <span data-ttu-id="7d1ad-109">不同資料來源的不同資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-109">A relationship from one table in a data source to another table in a different data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d1ad-110">DSV 中所定義的關聯性是邏輯關聯性，可能無法反映基礎資料來源中所定義的實際關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-110">The relationships defined in a DSV are logical and may not reflect the actual relationships defined in the underlying data source.</span></span> <span data-ttu-id="7d1ad-111">您可以在資料來源檢視設計師中，建立不存在於基礎資料來源的關聯性，也可以從基礎資料來源的現有外部索引鍵關聯性，移除資料來源檢視設計師所建立的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-111">You can create relationships in Data Source View Designer that do not exist in the underlying data source, and remove relationships created by Data Source View Designer from existing foreign key relationships in the underlying data source.</span></span>  
  
 <span data-ttu-id="7d1ad-112">關聯性具有方向性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-112">Relationships are directed.</span></span> <span data-ttu-id="7d1ad-113">針對來源資料行中的每一個值，在目的地資料行中均有一個對應值。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-113">For every value in the source column, there is a corresponding value in the destination column.</span></span> <span data-ttu-id="7d1ad-114">在資料來源檢視圖表 (例如 [圖表]\*\*\*\* 窗格中所顯示的圖表) 中，兩個資料表間線條上的箭頭會指出關聯性的方向。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-114">In a data source view diagram, such as the diagrams displayed in the **Diagram** pane, an arrow on the line between two tables indicates the direction of the relationship.</span></span>  
  
 <span data-ttu-id="7d1ad-115">這個主題包括下列各節：</span><span class="sxs-lookup"><span data-stu-id="7d1ad-115">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="7d1ad-116">在資料表、具名查詢或檢視表之間加入關聯性</span><span class="sxs-lookup"><span data-stu-id="7d1ad-116">To add a relationship between tables, named queries, or views</span></span>](#bkmk_addRel)  
  
 [<span data-ttu-id="7d1ad-117">在圖表窗格中檢視或修改關聯性</span><span class="sxs-lookup"><span data-stu-id="7d1ad-117">To view or modify a relationship in the Diagram pane</span></span>](#bkmk_diagrampane)  
  
 [<span data-ttu-id="7d1ad-118">在資料表窗格中檢視或修改關聯性</span><span class="sxs-lookup"><span data-stu-id="7d1ad-118">To view or modify a relationship in the Tables pane</span></span>](#bkmk_tablespane)  
  
##  <a name="to-add-a-relationship-between-tables-named-queries-or-views"></a><a name="bkmk_addRel"></a><span data-ttu-id="7d1ad-119">若要在資料表、命名查詢或 views 之間加入關聯性</span><span class="sxs-lookup"><span data-stu-id="7d1ad-119">To add a relationship between tables, named queries, or views</span></span>  
  
1.  <span data-ttu-id="7d1ad-120">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟含有您想在其中加入邏輯關聯性之資料來源檢視的專案，或連接到包含此資料來源檢視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to add a logical relationship.</span></span>  
  
2.  <span data-ttu-id="7d1ad-121">在方案總管中，展開 [資料來源檢視]\*\*\*\* 資料夾，然後按兩下資料來源檢視在 [資料來源檢視設計工具]\*\*\*\* 中開啟檢視。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-121">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view to open it in **Data Source View Designer**.</span></span>  
  
3.  <span data-ttu-id="7d1ad-122">在 [資料表]\*\*\*\* 窗格中，以滑鼠右鍵按一下您要加入關聯性的資料表、具名查詢或檢視表，然後按一下 [新增關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-122">Right-click the table, named query or view to which you want to add a relationship in either the **Tables** pane and then click **New Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7d1ad-123">若要尋找資料表、檢視表或具名查詢，您可以按一下 [資料來源檢視]\*\*\*\* 功能表，或是以滑鼠右鍵按一下 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格的開放區域，即可使用 [尋找資料表]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-123">To locate a table, view or named query, you can use the **Find Table** option by either clicking the **Data Source View** menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>  
  
4.  <span data-ttu-id="7d1ad-124">在 [指定關聯性]\*\*\*\* 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="7d1ad-124">In the **Specify Relationship** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="7d1ad-125">在 [來源 (外部索引鍵) 資料表]\*\*\*\* 清單中，選取適當的資料表、具名查詢或檢視表。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-125">Select the appropriate table, named query, or view in the **Source (foreign key) table** list.</span></span>  
  
    2.  <span data-ttu-id="7d1ad-126">在 [目的地 (主索引鍵) 資料表]\*\*\*\* 清單中，選取適當的資料表、具名查詢或檢視表。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-126">Select the appropriate table, named query, or view in the **Destination (primary key) table** lists.</span></span>  
  
    3.  <span data-ttu-id="7d1ad-127">從 [來源資料行]\*\*\*\* 和 [目的地資料行]\*\*\*\* 清單中選取資料行，來建立兩個資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-127">Select columns from the **Source Columns** and **Destination Columns** lists to create a relationship between the two tables.</span></span>  
  
         <span data-ttu-id="7d1ad-128">如果 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 藉由取樣基礎資料表、檢視表或具名查詢中的資料而偵測到您已經定義了錯誤方向的關聯性 (從主索引鍵到外部索引鍵，而不是從外部索引鍵到主索引鍵)，則會出現提示，要求您反轉此順序。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-128">If [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] detects, by sampling the data in the underlying table, view, or named query, that you have defined the relationship in the wrong direction (from the primary key to the foreign key rather than from the foreign key to the primary key), you will be prompted to reverse the order.</span></span> <span data-ttu-id="7d1ad-129">若要快速反轉此順序，請按一下 [反轉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-129">To quickly reverse the order, click **Reverse**.</span></span>  
  
         <span data-ttu-id="7d1ad-130">如果 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 偵測到您已選取的資料行中已經有關聯性存在，將會出現提示。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-130">If [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] detects that a relationship already exists for the columns you have selected, you will be prompted.</span></span> <span data-ttu-id="7d1ad-131">您不能定義重複的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-131">You cannot define duplicate relationships.</span></span>  
  
    4.  <span data-ttu-id="7d1ad-132">選擇性地在 [描述]\*\*\*\* 方塊中輸入關聯性的描述。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-132">Optionally, in the **Description** box, type a description for the relationship.</span></span>  
  
##  <a name="to-view-or-modify-a-relationship-in-the-diagram-pane"></a><a name="bkmk_diagrampane"></a><span data-ttu-id="7d1ad-133">若要在圖表窗格中查看或修改關聯性</span><span class="sxs-lookup"><span data-stu-id="7d1ad-133">To view or modify a relationship in the Diagram pane</span></span>  
  
-   <span data-ttu-id="7d1ad-134">在 [資料來源檢視設計工具]\*\*\*\* 的 [圖表]\*\*\*\* 窗格中，以滑鼠右鍵按一下您要檢視的關聯性，然後按一下 [編輯關聯性]\*\*\*\* (或直接按兩下關聯性箭頭)。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-134">In the **Diagram** pane in **Data Source View Designer**, right-click the relationship that you want to view and click **Edit Relationship** (or simply double-click the relationship arrow).</span></span>  <span data-ttu-id="7d1ad-135">使用 [編輯關聯性]\*\*\*\* 對話方塊修改關聯性。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-135">Use the **Edit Relationship** dialog box to modify the relationship.</span></span>  
  
##  <a name="to-view-or-modify-a-relationship-in-the-tables-pane"></a><a name="bkmk_tablespane"></a><span data-ttu-id="7d1ad-136">若要在 [資料表] 窗格中查看或修改關聯性</span><span class="sxs-lookup"><span data-stu-id="7d1ad-136">To view or modify a relationship in the Tables pane</span></span>  
  
1.  <span data-ttu-id="7d1ad-137">在 [資料來源檢視設計工具]\*\*\*\* 的 [資料表]\*\*\*\* 窗格中，尋找含有您想要檢視或修改之關聯性的資料表、檢視表或具名查詢，並加以展開。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-137">In the **Tables** pane in **Data Source View Designer**, locate and then expand the table, view or named query containing the relationship that you wish to view or modify.</span></span>  
  
2.  <span data-ttu-id="7d1ad-138">展開 [關聯性]\*\*\*\* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-138">Expand the **Relationships** folder.</span></span>  <span data-ttu-id="7d1ad-139">會出現選定資料表、檢視表或具名查詢以及其他資料表、檢視表和具名查詢之間的關聯性，並列出關聯性資料行。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-139">The relationships between the selected table, view or named query and other tables, views and named queries appear with the relationship column listed.</span></span>  
  
3.  <span data-ttu-id="7d1ad-140">以滑鼠右鍵按一下您要修改的關聯性，然後按一下 [編輯關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d1ad-140">Right-click the relationship you want to modify, and then click **Edit Relationship**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1ad-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d1ad-141">See Also</span></span>  
 [<span data-ttu-id="7d1ad-142">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="7d1ad-142">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
