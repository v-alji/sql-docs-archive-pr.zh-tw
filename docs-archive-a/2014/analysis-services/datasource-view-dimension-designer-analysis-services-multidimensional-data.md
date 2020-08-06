---
title: 資料來源視圖 (維度結構索引標籤、維度設計師)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.datasourcepane.f1
ms.assetid: c4bd3c5e-8986-448f-b9db-3551f50f0696
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb2529e1835829bc84eec77c18b7ec05da5c4220
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606488"
---
# <a name="data-source-view-dimension-structure-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="67281-102">資料來源檢視 (維度結構索引標籤，維度設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="67281-102">Data Source View (Dimension Structure Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="67281-103">使用 [資料來源檢視]\*\*\*\* 窗格，即可從與選取之維度相關聯的資料來源檢視中檢視資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="67281-103">Use the **Data Source View** pane to view tables and columns from the data source view associated with the selected dimension.</span></span> <span data-ttu-id="67281-104">此窗格會用來建立屬性 (attribute)、成員屬性 (property)、階層以及層級，方式是藉由從 [資料來源檢視]\*\*\*\* 窗格拖曳資料行至 \*\*\*\*[屬性] 或 [階層和層級]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="67281-104">This pane is used to create attributes, member properties, hierarchies, and levels, by dragging columns from the **Data Source View** pane to the **Attributes** or **Hierarchies and Levels** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="67281-105">選項</span><span class="sxs-lookup"><span data-stu-id="67281-105">Options</span></span>  
 <span data-ttu-id="67281-106">**[資料來源檢視]**</span><span class="sxs-lookup"><span data-stu-id="67281-106">**Data Source View**</span></span>  
 <span data-ttu-id="67281-107">顯示與選取之維度相關聯的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="67281-107">Displays the data source view associated with the selected dimension.</span></span>  
  
 <span data-ttu-id="67281-108">**(移動視點)**</span><span class="sxs-lookup"><span data-stu-id="67281-108">**(Move viewpoint)**</span></span>  
 <span data-ttu-id="67281-109">按一下窗格右下角的捲軸之間，即可選取要檢視的 [資料來源檢視]\*\*\*\* 窗格區域。</span><span class="sxs-lookup"><span data-stu-id="67281-109">Click the lower right corner of the pane, between the scrollbars, to select an area of the **Data Source View** pane to view.</span></span>  
  
## <a name="diagram-context-menu"></a><span data-ttu-id="67281-110">圖表內容功能表</span><span class="sxs-lookup"><span data-stu-id="67281-110">Diagram Context Menu</span></span>  
 <span data-ttu-id="67281-111">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的圖表背景，即可顯示提供下表所列出之選項的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="67281-111">The options listed in the following table are available in the context menu displayed by right-clicking the diagram background of the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="67281-112">**顯示資料表**</span><span class="sxs-lookup"><span data-stu-id="67281-112">**Show Tables**</span></span>  
 <span data-ttu-id="67281-113">顯示 [顯示資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="67281-113">Displays the **Show Table** dialog box.</span></span> <span data-ttu-id="67281-114">如需 [顯示資料表]\*\*\*\* 對話方塊的詳細資訊，請參閱[顯示資料表對話方塊 &#40;Analysis Services - 多維度資料&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="67281-114">For more information about the **Show Table** dialog box, see [Show Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="67281-115">**顯示所有資料表**</span><span class="sxs-lookup"><span data-stu-id="67281-115">**Show All Tables**</span></span>  
 <span data-ttu-id="67281-116">在窗格中顯示與維度相關聯之資料來源檢視中包含的所有資料表。</span><span class="sxs-lookup"><span data-stu-id="67281-116">Displays in the pane all tables included in the data source view associated with the dimension.</span></span>  
  
 <span data-ttu-id="67281-117">**僅顯示使用過的資料表**</span><span class="sxs-lookup"><span data-stu-id="67281-117">**Show Only Used Tables**</span></span>  
 <span data-ttu-id="67281-118">在窗格中只顯示關聯資料來源檢視之維度所使用的那些資料表。</span><span class="sxs-lookup"><span data-stu-id="67281-118">Displays in the pane only those tables used by the dimension from the associated data source view.</span></span>  
  
 <span data-ttu-id="67281-119">**顯示易記名稱**</span><span class="sxs-lookup"><span data-stu-id="67281-119">**Show Friendly Names**</span></span>  
 <span data-ttu-id="67281-120">選取即可顯示窗格中之物件的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="67281-120">Select to show friendly names for the objects in the pane.</span></span>  
  
 <span data-ttu-id="67281-121">**全選**</span><span class="sxs-lookup"><span data-stu-id="67281-121">**Select All**</span></span>  
 <span data-ttu-id="67281-122">選取窗格中的所有物件。</span><span class="sxs-lookup"><span data-stu-id="67281-122">Selects all of the objects in the pane.</span></span>  
  
 <span data-ttu-id="67281-123">**尋找資料表**</span><span class="sxs-lookup"><span data-stu-id="67281-123">**Find Table**</span></span>  
 <span data-ttu-id="67281-124">顯示 [尋找資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="67281-124">Displays the **Find Table** dialog box.</span></span> <span data-ttu-id="67281-125">如需 [尋找資料表]\*\*\*\* 對話方塊的詳細資訊，請參閱[尋找資料表對話方塊 &#40;Analysis Services - 多維度資料&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="67281-125">For more information about the **Find Table** dialog box, see [Find Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="67281-126">**排列資料表**</span><span class="sxs-lookup"><span data-stu-id="67281-126">**Arrange Tables**</span></span>  
 <span data-ttu-id="67281-127">選取 [切換到對角線配置]\*\*\*\* 或 [切換到矩形配置]\*\*\*\* 之後，會根據指定的配置來排列窗格中的物件。</span><span class="sxs-lookup"><span data-stu-id="67281-127">Arranges the objects in the pane according to the layout specified by selecting either **Switch to Diagonal Layout** or **Switch to Rectangular Layout**.</span></span>  
  
 <span data-ttu-id="67281-128">**切換到對角線配置**</span><span class="sxs-lookup"><span data-stu-id="67281-128">**Switch to Diagonal Layout**</span></span>  
 <span data-ttu-id="67281-129">選取以對角線模式排列物件。</span><span class="sxs-lookup"><span data-stu-id="67281-129">Select to arrange objects in a diagonal pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67281-130">唯有選取 [切換到矩形配置]\*\*\*\* 之後，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="67281-130">This option is displayed only if **Switch to Rectangular Layout** is selected.</span></span>  
  
 <span data-ttu-id="67281-131">**切換到矩形配置**</span><span class="sxs-lookup"><span data-stu-id="67281-131">**Switch to Rectangular Layout**</span></span>  
 <span data-ttu-id="67281-132">選取以矩形模式排列物件。</span><span class="sxs-lookup"><span data-stu-id="67281-132">Select to arrange objects in a rectangular pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67281-133">唯有選取 [切換到對角線配置]\*\*\*\* 之後，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="67281-133">This option is displayed only if **Switch to Diagonal Layout** is selected.</span></span>  
  
 <span data-ttu-id="67281-134">**編輯資料來源檢視**</span><span class="sxs-lookup"><span data-stu-id="67281-134">**Edit Data Source View**</span></span>  
 <span data-ttu-id="67281-135">顯示與維度相關聯之資料來源檢視的 [資料來源檢視設計工具]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="67281-135">Displays **Data Source View Designer** for the data source view associated with the dimension.</span></span> <span data-ttu-id="67281-136">如需**資料來源檢視設計工具**的詳細資訊，請參閱[資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="67281-136">For more information about **Data Source View Designe**r, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="67281-137">**顯示資料來源檢視於**</span><span class="sxs-lookup"><span data-stu-id="67281-137">**Show Data Source View In**</span></span>  
 <span data-ttu-id="67281-138">選取下列其中一個選項，以下列模式來切換檢視 [資料來源檢視]\*\*\*\* 窗格：</span><span class="sxs-lookup"><span data-stu-id="67281-138">Select one of the following options to toggle between viewing the **Data Source View** pane in the following modes:</span></span>  
  
-   <span data-ttu-id="67281-139">圖表</span><span class="sxs-lookup"><span data-stu-id="67281-139">Diagram</span></span>  
  
     <span data-ttu-id="67281-140">顯示與目前維度相關聯之資料表與資料行的圖表。</span><span class="sxs-lookup"><span data-stu-id="67281-140">Displays a diagram of the tables and columns associated with the current dimension.</span></span>  
  
-   <span data-ttu-id="67281-141">樹狀結構</span><span class="sxs-lookup"><span data-stu-id="67281-141">Tree</span></span>  
  
     <span data-ttu-id="67281-142">顯示包含與目前維度相關聯之資料表與資料行的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="67281-142">Displays a tree view that contains the tables and columns associated with the current dimension.</span></span>  
  
 <span data-ttu-id="67281-143">**複製圖表來源**</span><span class="sxs-lookup"><span data-stu-id="67281-143">**Copy Diagram From**</span></span>  
 <span data-ttu-id="67281-144">選取與維度相關聯之資料來源檢視中包含的其中一個圖表，即可將它顯示在 [資料來源檢視]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="67281-144">Select one of the diagrams included in the data source view associated with the dimension to display it in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="67281-145">**縮放**</span><span class="sxs-lookup"><span data-stu-id="67281-145">**Zoom**</span></span>  
 <span data-ttu-id="67281-146">選取可用的顯示比例選項。</span><span class="sxs-lookup"><span data-stu-id="67281-146">Select an available zoom option.</span></span>  
  
 <span data-ttu-id="67281-147">**屬性**</span><span class="sxs-lookup"><span data-stu-id="67281-147">**Properties**</span></span>  
 <span data-ttu-id="67281-148">針對與維度相關聯的資料來源檢視，顯示 [SQL Server Data Tools]\*\*\*\* 中的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="67281-148">Displays the **Properties** window in **SQL Server Data Tools** for the data source view associated with the dimension.</span></span>  
  
## <a name="table-context-menu"></a><span data-ttu-id="67281-149">資料表內容功能表</span><span class="sxs-lookup"><span data-stu-id="67281-149">Table Context Menu</span></span>  
 <span data-ttu-id="67281-150">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的資料表或檢視名稱，即可顯示提供下表所列出之選項的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="67281-150">The options listed in the following table are available in the context menu displayed by right-clicking the name of a table or view in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="67281-151">**顯示相關資料表**</span><span class="sxs-lookup"><span data-stu-id="67281-151">**Show Related Tables**</span></span>  
 <span data-ttu-id="67281-152">在窗格中顯示與資料來源檢視中所選取資料表相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="67281-152">Displays in the pane the tables related to the selected table in the data source view.</span></span>  
  
 <span data-ttu-id="67281-153">**隱藏資料表**</span><span class="sxs-lookup"><span data-stu-id="67281-153">**Hide Table**</span></span>  
 <span data-ttu-id="67281-154">從窗格中移除資料表。</span><span class="sxs-lookup"><span data-stu-id="67281-154">Removes the table from the pane.</span></span>  
  
 <span data-ttu-id="67281-155">**探索資料**</span><span class="sxs-lookup"><span data-stu-id="67281-155">**Explore Data**</span></span>  
 <span data-ttu-id="67281-156">顯示所選取資料表的 [瀏覽資料]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="67281-156">Displays the **Explore Data** dialog box for the selected table.</span></span>  
  
 <span data-ttu-id="67281-157">**編輯資料來源檢視**</span><span class="sxs-lookup"><span data-stu-id="67281-157">**Edit Data Source View**</span></span>  
 <span data-ttu-id="67281-158">針對包含選取之資料表的資料來源視圖，顯示**資料來源視圖設計**工具。</span><span class="sxs-lookup"><span data-stu-id="67281-158">Displays **Data Source View Designer** for the data source view that contains the selected table.</span></span> <span data-ttu-id="67281-159">如需**資料來源檢視設計工具**的詳細資訊，請參閱[資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="67281-159">For more information about **Data Source View Designe**r, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="67281-160">**屬性**</span><span class="sxs-lookup"><span data-stu-id="67281-160">**Properties**</span></span>  
 <span data-ttu-id="67281-161">在 [SQL Server Data Tools]\*\*\*\* 中顯示所選資料表的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="67281-161">Displays the **Properties** window in **SQL Server Data Tools** for the selected table.</span></span>  
  
## <a name="column-context-menu"></a><span data-ttu-id="67281-162">資料行內容功能表</span><span class="sxs-lookup"><span data-stu-id="67281-162">Column Context Menu</span></span>  
 <span data-ttu-id="67281-163">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的資料表或檢視內的資料行，即可顯示提供下表所列出之選項的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="67281-163">The options listed in the following table are available in the context menu displayed by right-clicking the name of a column in a table or view in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="67281-164">**從資料行新增屬性**</span><span class="sxs-lookup"><span data-stu-id="67281-164">**New Attribute from Column**</span></span>  
 <span data-ttu-id="67281-165">在窗格中顯示與資料來源檢視中所選取資料表相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="67281-165">Displays in the pane the tables related to the selected table in the data source view.</span></span>  
  
 <span data-ttu-id="67281-166">**探索資料**</span><span class="sxs-lookup"><span data-stu-id="67281-166">**Explore Data**</span></span>  
 <span data-ttu-id="67281-167">顯示包含所選取資料行之資料表的 [瀏覽資料]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="67281-167">Display the **Explore Data** dialog box for the table that contains the selected column.</span></span>  
  
 <span data-ttu-id="67281-168">**編輯資料來源檢視**</span><span class="sxs-lookup"><span data-stu-id="67281-168">**Edit Data Source View**</span></span>  
 <span data-ttu-id="67281-169">顯示包含所選取資料行之資料來源視圖的**資料來源視圖設計**工具。</span><span class="sxs-lookup"><span data-stu-id="67281-169">Displays **Data Source View Designer** for the data source view that contains the selected column.</span></span> <span data-ttu-id="67281-170">如需**資料來源檢視設計工具**的詳細資訊，請參閱[資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="67281-170">For more information about **Data Source View Designe**r, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="67281-171">**屬性**</span><span class="sxs-lookup"><span data-stu-id="67281-171">**Properties**</span></span>  
 <span data-ttu-id="67281-172">在 [SQL Server Data Tools]\*\*\*\* 中顯示所選資料行的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="67281-172">Displays the **Properties** window in **SQL Server Data Tools** for the selected column.</span></span>  
  
## <a name="relationship-context-menu"></a><span data-ttu-id="67281-173">關聯性內容功能表</span><span class="sxs-lookup"><span data-stu-id="67281-173">Relationship Context Menu</span></span>  
 <span data-ttu-id="67281-174">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的關聯性，即可顯示提供下表所列出之選項的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="67281-174">The options listed in the following table are available in the context menu displayed by right-clicking a relationship in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="67281-175">**編輯資料來源檢視**</span><span class="sxs-lookup"><span data-stu-id="67281-175">**Edit Data Source View**</span></span>  
 <span data-ttu-id="67281-176">顯示包含所選取關聯性之資料來源視圖的**資料來源視圖設計**工具。</span><span class="sxs-lookup"><span data-stu-id="67281-176">Displays **Data Source View Designer** for the data source view that contains the selected relationship.</span></span> <span data-ttu-id="67281-177">如需**資料來源檢視設計工具**的詳細資訊，請參閱[資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="67281-177">For more information about **Data Source View Designe**r, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="67281-178">**屬性**</span><span class="sxs-lookup"><span data-stu-id="67281-178">**Properties**</span></span>  
 <span data-ttu-id="67281-179">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，顯示所選取關聯性的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="67281-179">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67281-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67281-180">See Also</span></span>  
 <span data-ttu-id="67281-181">[維度結構 &#40;維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="67281-181">[Dimension Structure &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="67281-182">[工具列 &#40;維度結構索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](toolbar-dimension-structure-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="67281-182">[Toolbar &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-dimension-structure-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="67281-183">[屬性 &#40;維度結構索引標籤、維度設計師&#41; &#40;Analysis Services 多維度資料&#41;](attributes-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="67281-183">[Attributes &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attributes-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="67281-184">階層 &#40;維度結構索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="67281-184">Hierarchies &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](hierarchies-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
