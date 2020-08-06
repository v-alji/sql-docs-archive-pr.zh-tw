---
title: 資料來源視圖 (Cube 結構索引標籤、Cube 設計師)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.datasourcepane.f1
ms.assetid: 1e39c910-5c10-4624-be27-ca02a461b46b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c949eaa17ec9d8bf585a5d595f31779382c41ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702138"
---
# <a name="data-source-view-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="94a27-102">資料來源檢視 (Cube 結構索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="94a27-102">Data Source View (Cube Structure Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="94a27-103">使用 **[資料來源檢視]** 窗格，即可檢視來自與所選取 Cube 相關聯之資料來源檢視的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="94a27-103">Use the **Data Source View** pane to view tables and columns from the data source view associated with the selected cube.</span></span> <span data-ttu-id="94a27-104">此窗格會用來建立量值群組和量值，方法是從 **[資料來源檢視]** 窗格中，將資料行拖曳至 **[量值]** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="94a27-104">This pane is used to create measure groups and measures by dragging columns from the **Data Source View** pane to the **Measures** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="94a27-105">選項</span><span class="sxs-lookup"><span data-stu-id="94a27-105">Options</span></span>  
 <span data-ttu-id="94a27-106">**[資料來源檢視]**</span><span class="sxs-lookup"><span data-stu-id="94a27-106">**Data Source View**</span></span>  
 <span data-ttu-id="94a27-107">顯示與所選取 Cube 相關聯的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="94a27-107">Displays the data source view associated with the selected cube.</span></span>  
  
 <span data-ttu-id="94a27-108">**(移動視點)**</span><span class="sxs-lookup"><span data-stu-id="94a27-108">**(Move viewpoint)**</span></span>  
 <span data-ttu-id="94a27-109">按一下窗格右下角的捲軸之間，即可選取要檢視的 [資料來源檢視]\*\*\*\* 窗格區域。</span><span class="sxs-lookup"><span data-stu-id="94a27-109">Click the lower right corner of the pane, between the scrollbars, to select an area of the **Data Source View** pane to view.</span></span>  
  
## <a name="diagram-context-menu"></a><span data-ttu-id="94a27-110">圖表內容功能表</span><span class="sxs-lookup"><span data-stu-id="94a27-110">Diagram Context Menu</span></span>  
 <span data-ttu-id="94a27-111">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格的圖表背景，即可顯示提供下列選項的操作功能表：</span><span class="sxs-lookup"><span data-stu-id="94a27-111">The following options are available in the context menu displayed by right-clicking the diagram background of the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="94a27-112">**顯示資料表**</span><span class="sxs-lookup"><span data-stu-id="94a27-112">**Show Tables**</span></span>  
 <span data-ttu-id="94a27-113">顯示 [顯示資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="94a27-113">Displays the **Show Table** dialog box.</span></span> <span data-ttu-id="94a27-114">如需 [顯示資料表]\*\*\*\* 對話方塊的詳細資訊，請參閱[顯示資料表對話方塊 &#40;Analysis Services - 多維度資料&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="94a27-114">For more information about the **Show Table** dialog box, see [Show Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="94a27-115">**顯示所有資料表**</span><span class="sxs-lookup"><span data-stu-id="94a27-115">**Show All Tables**</span></span>  
 <span data-ttu-id="94a27-116">在窗格中顯示與 Cube 相關聯之資料來源檢視包含的所有資料表。</span><span class="sxs-lookup"><span data-stu-id="94a27-116">Displays in the pane all tables included in the data source view associated with the cube.</span></span>  
  
 <span data-ttu-id="94a27-117">**僅顯示使用過的資料表**</span><span class="sxs-lookup"><span data-stu-id="94a27-117">**Show Only Used Tables**</span></span>  
 <span data-ttu-id="94a27-118">在窗格中只顯示相關聯資料來源檢視之 Cube 所使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="94a27-118">Displays in the pane only those tables used by the cube from the associated data source view.</span></span>  
  
 <span data-ttu-id="94a27-119">**顯示易記名稱**</span><span class="sxs-lookup"><span data-stu-id="94a27-119">**Show Friendly Names**</span></span>  
 <span data-ttu-id="94a27-120">選取在窗格中顯示物件的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="94a27-120">Selects to show friendly names for the objects in the pane.</span></span>  
  
 <span data-ttu-id="94a27-121">**全選**</span><span class="sxs-lookup"><span data-stu-id="94a27-121">**Select All**</span></span>  
 <span data-ttu-id="94a27-122">選取窗格中的所有物件。</span><span class="sxs-lookup"><span data-stu-id="94a27-122">Selects all of the objects in the pane.</span></span>  
  
 <span data-ttu-id="94a27-123">**尋找資料表**</span><span class="sxs-lookup"><span data-stu-id="94a27-123">**Find Table**</span></span>  
 <span data-ttu-id="94a27-124">顯示 [尋找資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="94a27-124">Displays the **Find Table** dialog box.</span></span> <span data-ttu-id="94a27-125">如需 [尋找資料表]\*\*\*\* 對話方塊的詳細資訊，請參閱[尋找資料表對話方塊 &#40;Analysis Services - 多維度資料&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="94a27-125">For more information about the **Find Table** dialog box, see [Find Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="94a27-126">**排列資料表**</span><span class="sxs-lookup"><span data-stu-id="94a27-126">**Arrange Tables**</span></span>  
 <span data-ttu-id="94a27-127">選取 [切換到對角線配置]\*\*\*\* 或 [切換到矩形配置]\*\*\*\* 之後，會根據指定的配置來排列窗格中的物件。</span><span class="sxs-lookup"><span data-stu-id="94a27-127">Arranges the objects in the pane according to the layout specified by selecting either **Switch to Diagonal Layout** or **Switch to Rectangular Layout**.</span></span>  
  
 <span data-ttu-id="94a27-128">**切換到對角線配置**</span><span class="sxs-lookup"><span data-stu-id="94a27-128">**Switch to Diagonal Layout**</span></span>  
 <span data-ttu-id="94a27-129">選取以對角線模式排列物件。</span><span class="sxs-lookup"><span data-stu-id="94a27-129">Select to arrange objects in a diagonal pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94a27-130">唯有選取 [切換到矩形配置]\*\*\*\* 之後，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="94a27-130">This option is displayed only if **Switch to Rectangular Layout** is selected.</span></span>  
  
 <span data-ttu-id="94a27-131">**切換到矩形配置**</span><span class="sxs-lookup"><span data-stu-id="94a27-131">**Switch to Rectangular Layout**</span></span>  
 <span data-ttu-id="94a27-132">選取以矩形模式排列物件。</span><span class="sxs-lookup"><span data-stu-id="94a27-132">Select to arrange objects in a rectangular pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94a27-133">唯有選取 [切換到對角線配置]\*\*\*\* 之後，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="94a27-133">This option is displayed only if **Switch to Diagonal Layout** is selected.</span></span>  
  
 <span data-ttu-id="94a27-134">**編輯資料來源檢視**</span><span class="sxs-lookup"><span data-stu-id="94a27-134">**Edit Data Source View**</span></span>  
 <span data-ttu-id="94a27-135">顯示與物件相關聯之資料來源檢視的資料來源檢視設計師。</span><span class="sxs-lookup"><span data-stu-id="94a27-135">Displays Data Source View Designer for the data source view associated with the object.</span></span> <span data-ttu-id="94a27-136">如需資料來源檢視設計工具的詳細資訊，請參閱[資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="94a27-136">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="94a27-137">**顯示資料來源檢視於**</span><span class="sxs-lookup"><span data-stu-id="94a27-137">**Show Data Source View In**</span></span>  
 <span data-ttu-id="94a27-138">選取下列其中一個選項，以下列模式來切換檢視 [資料來源檢視]\*\*\*\* 窗格：</span><span class="sxs-lookup"><span data-stu-id="94a27-138">Select one of the following options to toggle between viewing the **Data Source View** pane in the following modes:</span></span>  
  
-   <span data-ttu-id="94a27-139">圖表</span><span class="sxs-lookup"><span data-stu-id="94a27-139">Diagram</span></span>  
  
     <span data-ttu-id="94a27-140">顯示與目前 Cube 相關聯之資料表和資料行的圖表。</span><span class="sxs-lookup"><span data-stu-id="94a27-140">Displays a diagram of the tables and columns associated with the current cube.</span></span>  
  
-   <span data-ttu-id="94a27-141">樹狀結構</span><span class="sxs-lookup"><span data-stu-id="94a27-141">Tree</span></span>  
  
     <span data-ttu-id="94a27-142">顯示樹狀檢視，其中包含與目前 Cube 相關聯的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="94a27-142">Displays a tree view containing the tables and columns associated with the current cube.</span></span>  
  
 <span data-ttu-id="94a27-143">**複製圖表來源**</span><span class="sxs-lookup"><span data-stu-id="94a27-143">**Copy Diagram From**</span></span>  
 <span data-ttu-id="94a27-144">選取與 Cube 相關聯之資料來源檢視所包含的其中一個圖表，以顯示在 [資料來源檢視]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="94a27-144">Select one of the diagrams included in the data source view associated with the cube to display it in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="94a27-145">**縮放**</span><span class="sxs-lookup"><span data-stu-id="94a27-145">**Zoom**</span></span>  
 <span data-ttu-id="94a27-146">選取可用的顯示比例選項。</span><span class="sxs-lookup"><span data-stu-id="94a27-146">Select an available zoom option.</span></span>  
  
 <span data-ttu-id="94a27-147">**屬性**</span><span class="sxs-lookup"><span data-stu-id="94a27-147">**Properties**</span></span>  
 <span data-ttu-id="94a27-148">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中顯示與 Cube 相關聯之資料來源檢視的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="94a27-148">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the data source view associated with the cube.</span></span>  
  
## <a name="table-context-menu"></a><span data-ttu-id="94a27-149">資料表內容功能表</span><span class="sxs-lookup"><span data-stu-id="94a27-149">Table Context Menu</span></span>  
 <span data-ttu-id="94a27-150">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的資料表或檢視名稱，即可顯示提供下列選項的操作功能表：</span><span class="sxs-lookup"><span data-stu-id="94a27-150">The following options are available in the context menu displayed by right-clicking the name of a table or view in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="94a27-151">**顯示相關資料表**</span><span class="sxs-lookup"><span data-stu-id="94a27-151">**Show Related Tables**</span></span>  
 <span data-ttu-id="94a27-152">在窗格中顯示與資料來源檢視中所選取資料表相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="94a27-152">Displays in the pane the tables related to the selected table in the data source view.</span></span>  
  
 <span data-ttu-id="94a27-153">**隱藏資料表**</span><span class="sxs-lookup"><span data-stu-id="94a27-153">**Hide Table**</span></span>  
 <span data-ttu-id="94a27-154">從窗格中移除資料表。</span><span class="sxs-lookup"><span data-stu-id="94a27-154">Removes the table from the pane.</span></span>  
  
 <span data-ttu-id="94a27-155">**探索資料**</span><span class="sxs-lookup"><span data-stu-id="94a27-155">**Explore Data**</span></span>  
 <span data-ttu-id="94a27-156">顯示所選取資料表的 [瀏覽資料]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="94a27-156">Display the **Explore Data** dialog box for the selected table.</span></span>  
  
 <span data-ttu-id="94a27-157">**編輯資料來源檢視**</span><span class="sxs-lookup"><span data-stu-id="94a27-157">**Edit Data Source View**</span></span>  
 <span data-ttu-id="94a27-158">針對包含選定資料表的資料來源檢視顯示 [資料來源檢視設計師]。</span><span class="sxs-lookup"><span data-stu-id="94a27-158">Displays Data Source View Designer for the data source view that contains the selected table.</span></span> <span data-ttu-id="94a27-159">如需資料來源檢視設計工具的詳細資訊，請參閱[資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="94a27-159">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="94a27-160">**從資料表新增量值群組**</span><span class="sxs-lookup"><span data-stu-id="94a27-160">**New Measure Group from Table**</span></span>  
 <span data-ttu-id="94a27-161">在 [量值]\*\*\*\* 窗格中，依據所選取資料表定義新的量值群組。</span><span class="sxs-lookup"><span data-stu-id="94a27-161">Defines a new measure group in the **Measures** pane based on the selected table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94a27-162">只有在 [量值]\*\*\*\* 窗格中的量值群組尚未參考資料表時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="94a27-162">This option is enabled only if the table is not yet referenced by a measure group in the **Measures** pane.</span></span>  
  
 <span data-ttu-id="94a27-163">**屬性**</span><span class="sxs-lookup"><span data-stu-id="94a27-163">**Properties**</span></span>  
 <span data-ttu-id="94a27-164">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中顯示所選取資料表的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="94a27-164">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected table.</span></span>  
  
## <a name="column-context-menu"></a><span data-ttu-id="94a27-165">資料行內容功能表</span><span class="sxs-lookup"><span data-stu-id="94a27-165">Column Context Menu</span></span>  
 <span data-ttu-id="94a27-166">在 [資料來源檢視]\*\*\*\* 窗格中，以滑鼠右鍵按一下資料表或檢視中的資料行名稱，即可顯示提供下列選項的操作功能表：</span><span class="sxs-lookup"><span data-stu-id="94a27-166">The following options are available in the context menu displayed by right-clicking the name of a column in a table or view in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="94a27-167">**從資料行新增量值**</span><span class="sxs-lookup"><span data-stu-id="94a27-167">**New Measure from Column**</span></span>  
 <span data-ttu-id="94a27-168">在 [量值]\*\*\*\* 窗格中，依據所選取資料行定義新的量值。</span><span class="sxs-lookup"><span data-stu-id="94a27-168">Defines a new measure in the **Measures** pane based on the selected column.</span></span>  
  
 <span data-ttu-id="94a27-169">**探索資料**</span><span class="sxs-lookup"><span data-stu-id="94a27-169">**Explore Data**</span></span>  
 <span data-ttu-id="94a27-170">顯示包含所選取資料行之資料表的 [瀏覽資料]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="94a27-170">Display the **Explore Data** dialog box for the table that contains the selected column.</span></span>  
  
 <span data-ttu-id="94a27-171">**編輯資料來源檢視**</span><span class="sxs-lookup"><span data-stu-id="94a27-171">**Edit Data Source View**</span></span>  
 <span data-ttu-id="94a27-172">針對包含選定資料行的資料來源檢視顯示 [資料來源檢視設計師]。</span><span class="sxs-lookup"><span data-stu-id="94a27-172">Displays Data Source View Designer for the data source view that contains the selected column.</span></span> <span data-ttu-id="94a27-173">如需資料來源檢視設計工具的詳細資訊，請參閱[資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="94a27-173">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="94a27-174">**屬性**</span><span class="sxs-lookup"><span data-stu-id="94a27-174">**Properties**</span></span>  
 <span data-ttu-id="94a27-175">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中顯示所選取資料行的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="94a27-175">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected column.</span></span>  
  
## <a name="relationship-context-menu"></a><span data-ttu-id="94a27-176">關聯性內容功能表</span><span class="sxs-lookup"><span data-stu-id="94a27-176">Relationship Context Menu</span></span>  
 <span data-ttu-id="94a27-177">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的關聯性，即可顯示提供下列選項的操作功能表：</span><span class="sxs-lookup"><span data-stu-id="94a27-177">The following options are available in the context menu displayed by right-clicking a relationship in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="94a27-178">**編輯資料來源檢視**</span><span class="sxs-lookup"><span data-stu-id="94a27-178">**Edit Data Source View**</span></span>  
 <span data-ttu-id="94a27-179">顯示包含所選取關聯性之資料來源檢視的資料來源檢視設計師。</span><span class="sxs-lookup"><span data-stu-id="94a27-179">Displays Data Source View Designer for the data source view that contains the selected relationship.</span></span> <span data-ttu-id="94a27-180">如需資料來源檢視設計工具的詳細資訊，請參閱[資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="94a27-180">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="94a27-181">**屬性**</span><span class="sxs-lookup"><span data-stu-id="94a27-181">**Properties**</span></span>  
 <span data-ttu-id="94a27-182">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，顯示所選取關聯性的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="94a27-182">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a27-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94a27-183">See Also</span></span>  
 <span data-ttu-id="94a27-184">[工具列 &#40;Cube 結構索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="94a27-184">[Toolbar &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="94a27-185">[量值 &#40;Cube 結構索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="94a27-185">[Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="94a27-186">[維度 &#40;Cube 結構索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="94a27-186">[Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="94a27-187">Cube 結構 &#40;Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="94a27-187">Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-structure-cube-designer-analysis-services-multidimensional-data.md)  
  
  
