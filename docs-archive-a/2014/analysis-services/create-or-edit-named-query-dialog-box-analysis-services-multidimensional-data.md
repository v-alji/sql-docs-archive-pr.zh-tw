---
title: 建立或編輯已命名的查詢對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createnamedquery.f1
helpviewer_keywords:
- Create Named Query dialog box
ms.assetid: 8e192ad6-a0b1-4e21-bb3f-087c93e62941
author: minewiskan
ms.author: owend
ms.openlocfilehash: cb255a44d2dde18e8d5e20343c7c5396f2e867d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594280"
---
# <a name="create-or-edit-named-query-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="312b3-102">建立或編輯具名查詢對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="312b3-102">Create or Edit Named Query Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="312b3-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [建立/編輯具名查詢]\*\*\*\* 對話方塊，即可建立或編輯 [資料來源檢視設計師]\*\*\*\* 中的具名查詢。</span><span class="sxs-lookup"><span data-stu-id="312b3-103">Use the **Create/Edit Named Query** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create or edit a named query in **Data Source View Designer**.</span></span> <span data-ttu-id="312b3-104">具名查詢可以當成資料表處理，並以此作為其他 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的基礎。</span><span class="sxs-lookup"><span data-stu-id="312b3-104">A named query can be treated as a table, on which you can base other [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="312b3-105">您可以執行下列動作來顯示 [建立/編輯具名查詢]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="312b3-105">You can display the **Create/Edit Named Query** dialog box by:</span></span>  
  
-   <span data-ttu-id="312b3-106">在 [資料來源檢視設計師]\*\*\*\* 的 [工具列]\*\*\*\* 窗格上，按一下 [新增具名查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="312b3-106">Clicking **New Named Query** on the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="312b3-107">以滑鼠右鍵按一下 [資料來源檢視設計師]\*\*\*\* 的 [圖表]\*\*\*\* 窗格，然後選取 [新增具名查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="312b3-107">Right-clicking the **Diagram** pane of **Data Source View Designer** and selecting **New Named Query**.</span></span>  
  
-   <span data-ttu-id="312b3-108">在 [資料來源檢視設計師]\*\*\*\* 的 [圖表]\*\*\*\* 或 [資料表]\*\*\*\* 窗格中，以滑鼠右鍵按一下具名查詢的名稱，然後選取 [編輯具名查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="312b3-108">Right-clicking the name of a named query in the **Diagram** or **Tables** pane of **Data Source View Designer** and selecting **Edit Named Query**.</span></span>  
  
 <span data-ttu-id="312b3-109">輸入的查詢必須是基礎提供者的有效查詢命令。</span><span class="sxs-lookup"><span data-stu-id="312b3-109">The query entered must be a valid query command for the underlying provider.</span></span> <span data-ttu-id="312b3-110">此查詢會由基礎提供者進行驗證，以及識別傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="312b3-110">The query is prepared with the underlying provider for validation, and to identify the columns returned.</span></span> <span data-ttu-id="312b3-111">對話方塊可呈現兩種檢視：</span><span class="sxs-lookup"><span data-stu-id="312b3-111">The dialog box can present two views:</span></span>  
  
-   <span data-ttu-id="312b3-112">Visual Database Tools (VDT) 查詢產生器</span><span class="sxs-lookup"><span data-stu-id="312b3-112">Visual Database Tools (VDT) Query Builder</span></span>  
  
     <span data-ttu-id="312b3-113">對於所有使用者，VDT 查詢產生器的檢視所提供的使用者介面工具集，能夠以視覺化方式建構及測試 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="312b3-113">For all users, the VDT Query Builder view provides a set of user interface tools for visually constructing and testing a SQL query.</span></span>  
  
-   <span data-ttu-id="312b3-114">一般查詢產生器</span><span class="sxs-lookup"><span data-stu-id="312b3-114">Generic Query Builder</span></span>  
  
     <span data-ttu-id="312b3-115">對於進階使用者，一般查詢產生器檢視提供更簡單、更直接的使用者介面，可以用來建構及測試 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="312b3-115">For advanced users, the Generic Query Builder view provides a simpler, more direct user interface for constructing and testing a SQL query.</span></span>  
  
## <a name="options"></a><span data-ttu-id="312b3-116">選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-116">Options</span></span>  
 <span data-ttu-id="312b3-117">**名稱**</span><span class="sxs-lookup"><span data-stu-id="312b3-117">**Name**</span></span>  
 <span data-ttu-id="312b3-118">鍵入查詢的名稱。</span><span class="sxs-lookup"><span data-stu-id="312b3-118">Type the name of the query.</span></span>  
  
 <span data-ttu-id="312b3-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="312b3-119">**Description**</span></span>  
 <span data-ttu-id="312b3-120">鍵入查詢的選用性描述。</span><span class="sxs-lookup"><span data-stu-id="312b3-120">Type the optional description of the query.</span></span>  
  
 <span data-ttu-id="312b3-121">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="312b3-121">**Data Source**</span></span>  
 <span data-ttu-id="312b3-122">指定查詢的資料來源。</span><span class="sxs-lookup"><span data-stu-id="312b3-122">Specifies the data source for the query.</span></span>  
  
 <span data-ttu-id="312b3-123">**查詢定義**</span><span class="sxs-lookup"><span data-stu-id="312b3-123">**Query definition**</span></span>  
 <span data-ttu-id="312b3-124">視選取的檢視而定，查詢定義會提供工具列和窗格，以定義及測試查詢。</span><span class="sxs-lookup"><span data-stu-id="312b3-124">The query definition provides a toolbar and panes in which to define and test the query, depending on the selected view.</span></span>  
  
 <span data-ttu-id="312b3-125">**工具列**</span><span class="sxs-lookup"><span data-stu-id="312b3-125">**Toolbar**</span></span>  
 <span data-ttu-id="312b3-126">使用工具列即可管理資料集、選取要顯示的窗格和控制各種查詢功能。</span><span class="sxs-lookup"><span data-stu-id="312b3-126">Use the toolbar to manage datasets, select panes to display, and control various query functions.</span></span>  
  
|<span data-ttu-id="312b3-127">值</span><span class="sxs-lookup"><span data-stu-id="312b3-127">Value</span></span>|<span data-ttu-id="312b3-128">描述</span><span class="sxs-lookup"><span data-stu-id="312b3-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="312b3-129">**切換到一般查詢產生器**</span><span class="sxs-lookup"><span data-stu-id="312b3-129">**Switch to Generic Query Builder**</span></span>|<span data-ttu-id="312b3-130">選取即可只顯示一般查詢產生器檢視可用的選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-130">Select to display only the options available to the Generic Query Builder view.</span></span> <span data-ttu-id="312b3-131">僅會顯示下列選項：</span><span class="sxs-lookup"><span data-stu-id="312b3-131">Only the following options are displayed:</span></span><br /><span data-ttu-id="312b3-132">**SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-132">**SQL pane**</span></span><br /><span data-ttu-id="312b3-133">**結果窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-133">**Result pane**</span></span><br /><span data-ttu-id="312b3-134">**工具列**，只包含 **[切換到 VDT 查詢產生器]** 和 **[執行]**</span><span class="sxs-lookup"><span data-stu-id="312b3-134">**Toolbar**, containing only **Switch to VDT Query Builder** and **Run**</span></span><br /><br /> <br /><br /> <span data-ttu-id="312b3-135">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-135">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-136">**[切換到 VDT 查詢產生器]**</span><span class="sxs-lookup"><span data-stu-id="312b3-136">**Switch to VDT Query Builder**</span></span>|<span data-ttu-id="312b3-137">選取即可顯示 Visual Database Tools (VDT) 查詢產生器檢視可用的所有選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-137">Select to display all of the options available to the Visual Database Tools (VDT) Query Builder view.</span></span><br /><br /> <span data-ttu-id="312b3-138">注意：唯有選取 [切換到一般查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-138">Note: This option is displayed only if **Switch to Generic Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-139">**顯示/隱藏圖表窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-139">**Show/Hide Diagram Pane**</span></span>|<span data-ttu-id="312b3-140">顯示或隱藏 [**圖表] 窗格**。</span><span class="sxs-lookup"><span data-stu-id="312b3-140">Shows or hides the **Diagram pane**.</span></span><br /><br /> <span data-ttu-id="312b3-141">**注意**只有選取 [**切換到 VDT 查詢**產生器] 時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-141">**Note** This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-142">**顯示/隱藏方格窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-142">**Show/Hide Grid Pane**</span></span>|<span data-ttu-id="312b3-143">顯示或隱藏 [**方格] 窗格**。</span><span class="sxs-lookup"><span data-stu-id="312b3-143">Shows or hides the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="312b3-144">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-144">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-145">**顯示/隱藏 SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-145">**Show/Hide SQL Pane**</span></span>|<span data-ttu-id="312b3-146">顯示或隱藏 **[SQL 窗格]**。</span><span class="sxs-lookup"><span data-stu-id="312b3-146">Shows or hides the **SQL pane**.</span></span><br /><br /> <span data-ttu-id="312b3-147">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-147">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-148">**顯示/隱藏結果窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-148">**Show/Hide Result Pane**</span></span>|<span data-ttu-id="312b3-149">顯示或隱藏 **[結果窗格]**。</span><span class="sxs-lookup"><span data-stu-id="312b3-149">Shows or hides the **Result pane**.</span></span><br /><br /> <span data-ttu-id="312b3-150">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-150">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-151">**執行**</span><span class="sxs-lookup"><span data-stu-id="312b3-151">**Run**</span></span>|<span data-ttu-id="312b3-152">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="312b3-152">Runs the query.</span></span> <span data-ttu-id="312b3-153">結果會顯示在 **[結果窗格]** 中。</span><span class="sxs-lookup"><span data-stu-id="312b3-153">Results are displayed in the **Result pane**.</span></span>|  
|<span data-ttu-id="312b3-154">**確認 SQL**</span><span class="sxs-lookup"><span data-stu-id="312b3-154">**Verify SQL**</span></span>|<span data-ttu-id="312b3-155">驗證查詢中的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="312b3-155">Verifies the SQL statement in the query.</span></span><br /><br /> <span data-ttu-id="312b3-156">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-156">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-157">**昇冪**</span><span class="sxs-lookup"><span data-stu-id="312b3-157">**Sort Ascending**</span></span>|<span data-ttu-id="312b3-158">依遞增順序排序 **[方格窗格]** 中所選取資料行的輸出資料列。</span><span class="sxs-lookup"><span data-stu-id="312b3-158">Sorts output rows on the selected column in the **Grid pane**, in ascending order.</span></span><br /><br /> <span data-ttu-id="312b3-159">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-159">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-160">**遞減排序**</span><span class="sxs-lookup"><span data-stu-id="312b3-160">**Sort Descending**</span></span>|<span data-ttu-id="312b3-161">依遞減順序排序在 **[方格窗格]** 中所選取資料行的輸出資料列。</span><span class="sxs-lookup"><span data-stu-id="312b3-161">Sorts output rows on the selected column in the **Grid pane**, in descending order.</span></span><br /><br /> <span data-ttu-id="312b3-162">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-162">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-163">**移除篩選**</span><span class="sxs-lookup"><span data-stu-id="312b3-163">**Remove Filter**</span></span>|<span data-ttu-id="312b3-164">如果適用的話，移除 **[方格窗格]** 中所選取資料列的排序準則。</span><span class="sxs-lookup"><span data-stu-id="312b3-164">Removes sort criteria, if applicable, for the selected row in the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="312b3-165">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-165">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-166">**使用群組依據**</span><span class="sxs-lookup"><span data-stu-id="312b3-166">**Use Group By**</span></span>|<span data-ttu-id="312b3-167">將群組功能加入查詢中。</span><span class="sxs-lookup"><span data-stu-id="312b3-167">Adds grouping functionality to the query.</span></span><br /><br /> <span data-ttu-id="312b3-168">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-168">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="312b3-169">**加入資料表**</span><span class="sxs-lookup"><span data-stu-id="312b3-169">**Add Table**</span></span>|<span data-ttu-id="312b3-170">顯示 **[加入資料表]** 對話方塊，將新的資料表或檢視加入查詢中。</span><span class="sxs-lookup"><span data-stu-id="312b3-170">Displays the **Add Table** dialog box to add a new table or view to the query.</span></span> <span data-ttu-id="312b3-171">如需 [加入資料表]\*\*\*\* 對話方塊的詳細資訊，請參閱[加入資料表對話方塊 &#40;Analysis Services - 多維度資料&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="312b3-171">For more information about the **Add Table** dialog box, see [Add Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="312b3-172">注意：唯有選取 [切換到 VDT 查詢產生器] \*\*\*\* 才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="312b3-172">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
  
 <span data-ttu-id="312b3-173">**圖表窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-173">**Diagram pane**</span></span>  
 <span data-ttu-id="312b3-174">以圖表顯示查詢所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="312b3-174">Displays the objects referenced by the query as a diagram.</span></span> <span data-ttu-id="312b3-175">此圖表顯示查詢所包括的資料表及其聯結方式。</span><span class="sxs-lookup"><span data-stu-id="312b3-175">The diagram shows the tables included in the query, and how they are joined.</span></span> <span data-ttu-id="312b3-176">選取或清除資料表之資料行旁邊的核取方塊，以便在查詢輸出中加入或移除。</span><span class="sxs-lookup"><span data-stu-id="312b3-176">Select or clear the check box next to a column in a table to add or remove it from the query output.</span></span>  
  
 <span data-ttu-id="312b3-177">當您在查詢中加入資料表時，對話方塊會依據資料表中的索引鍵，在資料表之間建立聯結。</span><span class="sxs-lookup"><span data-stu-id="312b3-177">When you add tables to the query, the dialog box creates joins between tables based on the keys in the table.</span></span> <span data-ttu-id="312b3-178">若要加入聯結，請將欄位從一個資料表拖曳至另一個資料表的欄位。</span><span class="sxs-lookup"><span data-stu-id="312b3-178">To add a join, drag a field from one table onto a field in another table.</span></span> <span data-ttu-id="312b3-179">若要管理聯結，請以滑鼠右鍵按一下聯結。</span><span class="sxs-lookup"><span data-stu-id="312b3-179">To manage a join, right-click the join.</span></span>  
  
 <span data-ttu-id="312b3-180">以滑鼠右鍵按一下 [圖表窗格]\*\*\*\*，即可加入或移除資料表、選取所有資料表以及顯示或隱藏窗格。</span><span class="sxs-lookup"><span data-stu-id="312b3-180">Right-click the **Diagram pane** to add or remove tables, select all the tables, and show or hide panes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="312b3-181">**[圖表窗格]**、 **[方格窗格]** 和 **[SQL 窗格]** 的內容會同步處理，因此一個窗格的變更會反映在其他兩個窗格中。</span><span class="sxs-lookup"><span data-stu-id="312b3-181">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="312b3-182">此對話方塊不支援變更查詢類型。</span><span class="sxs-lookup"><span data-stu-id="312b3-182">Changing query types is not supported by the dialog box.</span></span>  
  
 <span data-ttu-id="312b3-183">**[方格] 窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-183">**Grid pane**</span></span>  
 <span data-ttu-id="312b3-184">以方格的方式顯示查詢所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="312b3-184">Displays the objects referenced by the query in a grid.</span></span> <span data-ttu-id="312b3-185">您可以使用此方格，在查詢中加入和移除資料行，以及變更每一個資料行的設定。</span><span class="sxs-lookup"><span data-stu-id="312b3-185">You can use this pane to add and remove columns to the query and change the settings for each column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="312b3-186">**[圖表窗格]**、 **[方格窗格]** 和 **[SQL 窗格]** 的內容會同步處理，因此一個窗格的變更會反映在其他兩個窗格中。</span><span class="sxs-lookup"><span data-stu-id="312b3-186">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="312b3-187">**SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-187">**SQL pane**</span></span>  
 <span data-ttu-id="312b3-188">以 SQL 陳述式顯示查詢。</span><span class="sxs-lookup"><span data-stu-id="312b3-188">Displays the query as a SQL statement.</span></span> <span data-ttu-id="312b3-189">鍵入資料，以變更查詢的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="312b3-189">Type to change the SQL statement for the query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="312b3-190">**[圖表窗格]**、 **[方格窗格]** 和 **[SQL 窗格]** 的內容會同步處理，因此一個窗格的變更會反映在其他兩個窗格中。</span><span class="sxs-lookup"><span data-stu-id="312b3-190">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="312b3-191">**結果窗格**</span><span class="sxs-lookup"><span data-stu-id="312b3-191">**Result pane**</span></span>  
 <span data-ttu-id="312b3-192">按一下 [工具列]\*\*\*\* 窗格上的 [執行]\*\*\*\* 時，會顯示查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="312b3-192">Displays the results of the query when you click **Run** on the **Toolbar** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="312b3-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="312b3-193">See Also</span></span>  
 <span data-ttu-id="312b3-194">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="312b3-194">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="312b3-195">在資料來源檢視中定義具名查詢 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="312b3-195">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)  
  
  
