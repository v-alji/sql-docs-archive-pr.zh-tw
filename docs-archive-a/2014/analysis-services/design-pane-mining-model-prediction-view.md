---
title: '[設計] 窗格 ([) 的採礦模型預測視圖 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.design.f1
ms.assetid: 17f24c8d-43cd-4f4d-83b3-a41ee8fbe8e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32ac73a2d6fde38d15d1f45a8439293695749ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702103"
---
# <a name="design-pane-mining-model-prediction-view"></a><span data-ttu-id="db44f-102">設計窗格 (採礦模型預測檢視)</span><span class="sxs-lookup"><span data-stu-id="db44f-102">Design Pane (Mining Model Prediction View)</span></span>
  <span data-ttu-id="db44f-103">**[設計]** 窗格包含預測查詢產生器，可用來建立資料採礦預測。</span><span class="sxs-lookup"><span data-stu-id="db44f-103">The **Design** pane contains the Prediction Query Builder, which you can use to build data mining predictions.</span></span> <span data-ttu-id="db44f-104">您可以設計預測查詢來使用資料來源檢視中輸入資料的資料表，以便產生大量預測，或者可以建立單一預測查詢，好讓您提供個別值。</span><span class="sxs-lookup"><span data-stu-id="db44f-104">You can design prediction queries that use tables of input data from a data source view, to generate bulk predictions, or you can create singleton prediction queries, which let you provide individual values.</span></span>  
  
 <span data-ttu-id="db44f-105">若要執行查詢及檢視結果，請切換到查詢結果檢視。</span><span class="sxs-lookup"><span data-stu-id="db44f-105">To run the query and view the results, switch to query result view.</span></span>  
  
 <span data-ttu-id="db44f-106">[查詢]\*\*\*\* 檢視會顯示預測查詢產生器建立的資料採礦延伸模組 (DMX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="db44f-106">The **Query** view displays the Data Mining Extensions (DMX) query that Prediction Query Builder creates.</span></span> <span data-ttu-id="db44f-107">如果您很熟悉 DMX，可以自訂此查詢。</span><span class="sxs-lookup"><span data-stu-id="db44f-107">If you are familiar with DMX, you can customize this query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db44f-108">如果您對查詢做了任何手動變更，當您切換回 [設計] 檢視時，您的變更將會遺失。</span><span class="sxs-lookup"><span data-stu-id="db44f-108">If you make any manual changes to the query, your changes will be lost when you switch back to Design view.</span></span> <span data-ttu-id="db44f-109">如果您想要儲存 DMX 查詢，可以將此查詢複製到 Windows 剪貼簿，然後貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="db44f-109">If you want to save the DMX query, you can copy the query to the Windows Clipboard and then paste it to a text file.</span></span>  
  
 <span data-ttu-id="db44f-110">**如需詳細資訊，請參閱** [資料採礦查詢](data-mining/data-mining-queries.md)</span><span class="sxs-lookup"><span data-stu-id="db44f-110">**For More Information:** [Data Mining Queries](data-mining/data-mining-queries.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="db44f-111">選項</span><span class="sxs-lookup"><span data-stu-id="db44f-111">Options</span></span>  
 <span data-ttu-id="db44f-112">**切換到查詢結果檢視**</span><span class="sxs-lookup"><span data-stu-id="db44f-112">**Switch to query result view**</span></span>  
 <span data-ttu-id="db44f-113">按一下，即可在 [設計]\*\*\*\*、[查詢]\*\*\*\* 及 [結果]\*\*\*\* 窗格之間切換。</span><span class="sxs-lookup"><span data-stu-id="db44f-113">Click to switch between the **Design**, **Query**, and **Result** panes.</span></span> <span data-ttu-id="db44f-114">切換到 **[結果]** 窗格會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="db44f-114">Switching to the **Result** pane runs the query.</span></span>  
  
 <span data-ttu-id="db44f-115">**儲存查詢結果**</span><span class="sxs-lookup"><span data-stu-id="db44f-115">**Save the query result**</span></span>  
 <span data-ttu-id="db44f-116">開啟 [儲存資料採礦查詢結果]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db44f-116">Opens the **Save Data Mining Query Result** dialog box.</span></span>  
  
 <span data-ttu-id="db44f-117">**單一查詢**</span><span class="sxs-lookup"><span data-stu-id="db44f-117">**Singleton query**</span></span>  
 <span data-ttu-id="db44f-118">啟用建立單一查詢，可以直接為查詢提供值，而非提供資料表做為已知資料的來源。</span><span class="sxs-lookup"><span data-stu-id="db44f-118">Enables creating a singleton query, in which you can provide values directly for the query instead of providing a table as the source of the known data.</span></span> <span data-ttu-id="db44f-119">[選取輸入資料表]\*\*\*\* 資料表已由 [單一查詢輸入]\*\*\*\* 資料表取代。</span><span class="sxs-lookup"><span data-stu-id="db44f-119">The **Select Input Table(s)** table is replaced by a **Singleton Query Input** table.</span></span>  
  
 <span data-ttu-id="db44f-120">**重新整理查詢結果**</span><span class="sxs-lookup"><span data-stu-id="db44f-120">**Refresh query results**</span></span>  
 <span data-ttu-id="db44f-121">重新處理預測查詢。</span><span class="sxs-lookup"><span data-stu-id="db44f-121">Reprocesses the prediction query.</span></span> <span data-ttu-id="db44f-122">這只會在 **[結果]** 窗格中啟用。</span><span class="sxs-lookup"><span data-stu-id="db44f-122">This is enabled only in the **Result** pane.</span></span>  
  
 <span data-ttu-id="db44f-123">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="db44f-123">**Mining Model**</span></span>  
 <span data-ttu-id="db44f-124">顯示選取的採礦模型，並以此模型作為預測的基礎。</span><span class="sxs-lookup"><span data-stu-id="db44f-124">Displays the selected mining model on which you want to base predictions.</span></span>  
  
 <span data-ttu-id="db44f-125">**選取模型**</span><span class="sxs-lookup"><span data-stu-id="db44f-125">**Select Model**</span></span>  
 <span data-ttu-id="db44f-126">開啟 [選取採礦模型]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db44f-126">Opens the **Select Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="db44f-127">**選取輸入資料表**</span><span class="sxs-lookup"><span data-stu-id="db44f-127">**Select Input Table(s)**</span></span>  
 <span data-ttu-id="db44f-128">顯示選取的輸入資料表，其中包含做為預測基礎的已知資料。</span><span class="sxs-lookup"><span data-stu-id="db44f-128">Displays the selected input tables that contain known data on which to base the predictions.</span></span>  
  
 <span data-ttu-id="db44f-129">**刪除資料表**</span><span class="sxs-lookup"><span data-stu-id="db44f-129">**Delete Table**</span></span>  
 <span data-ttu-id="db44f-130">刪除選取的資料表。</span><span class="sxs-lookup"><span data-stu-id="db44f-130">Deletes the selected table.</span></span> <span data-ttu-id="db44f-131">如果尚未選取資料表，或者資料表不存在，這個按鈕就會停用。</span><span class="sxs-lookup"><span data-stu-id="db44f-131">This button is disabled if a table has not been selected or does not exist.</span></span>  
  
 <span data-ttu-id="db44f-132">**選取案例資料表**</span><span class="sxs-lookup"><span data-stu-id="db44f-132">**Select Case Table**</span></span>  
 <span data-ttu-id="db44f-133">開啟 [選取資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db44f-133">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="db44f-134">唯有未選取案例資料表時，才會顯示這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="db44f-134">This button appears only if a case table has not been selected.</span></span>  
  
 <span data-ttu-id="db44f-135">**選取巢狀資料表**</span><span class="sxs-lookup"><span data-stu-id="db44f-135">**Select Nested Table**</span></span>  
 <span data-ttu-id="db44f-136">開啟 [選取資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db44f-136">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="db44f-137">唯有選取了案例資料表時，才會顯示這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="db44f-137">This button appears only if a case table has been selected.</span></span> <span data-ttu-id="db44f-138">如果關聯的採礦結構未包含巢狀資料表，這個按鈕就會停用。</span><span class="sxs-lookup"><span data-stu-id="db44f-138">If the associated mining structure does not contain a nested table, this button is disabled.</span></span>  
  
 <span data-ttu-id="db44f-139">**修改聯結**</span><span class="sxs-lookup"><span data-stu-id="db44f-139">**Modify Join**</span></span>  
 <span data-ttu-id="db44f-140">開啟 [指定巢狀聯結]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db44f-140">Opens the **Specify Nested Join** dialog box.</span></span> <span data-ttu-id="db44f-141">唯有選取了巢狀資料表時，才可以使用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="db44f-141">This button is active only if the nested table is selected.</span></span>  
  
 <span data-ttu-id="db44f-142">**單一查詢輸入**</span><span class="sxs-lookup"><span data-stu-id="db44f-142">**Singleton Query input**</span></span>  
 <span data-ttu-id="db44f-143">當您選取 [單一查詢]\*\*\*\* 按鈕時，就會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="db44f-143">Enabled when you select the **Singleton query** button.</span></span> <span data-ttu-id="db44f-144">其中包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="db44f-144">Contains the following columns:</span></span>  
  
|<span data-ttu-id="db44f-145">值</span><span class="sxs-lookup"><span data-stu-id="db44f-145">Value</span></span>|<span data-ttu-id="db44f-146">描述</span><span class="sxs-lookup"><span data-stu-id="db44f-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db44f-147">**採礦模型資料行**</span><span class="sxs-lookup"><span data-stu-id="db44f-147">**Mining Model Column**</span></span>|<span data-ttu-id="db44f-148">列出在 **[採礦模型]** 資料表中所選取、包含在採礦模型中的採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="db44f-148">Lists the mining model columns contained within the mining model that is selected in the **Mining Model** table.</span></span>|  
|<span data-ttu-id="db44f-149">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="db44f-149">**Value**</span></span>|<span data-ttu-id="db44f-150">從包含所選取採礦模型之每一可能狀態的清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="db44f-150">Select a value from the list that contains each possible state of the selected mining model column.</span></span><br /><br /> <span data-ttu-id="db44f-151">如果資料行是巢狀資料表資料行，按一下值資料格即可開啟 **[巢狀資料表輸入]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db44f-151">If the column is a nested table column, clicking the value cell opens the **Nested Table Input** dialog box.</span></span>|  
  
 <span data-ttu-id="db44f-152">**Source**</span><span class="sxs-lookup"><span data-stu-id="db44f-152">**Source**</span></span>  
 <span data-ttu-id="db44f-153">選取來源，其中包含用於資料表的欄位。</span><span class="sxs-lookup"><span data-stu-id="db44f-153">Select the source that contains the field that you will use for the column.</span></span> <span data-ttu-id="db44f-154">您可以使用 [採礦模型]\*\*\*\* 資料表中選取的採礦模型、[選取輸入資料表]\*\*\*\* 資料表中選取的一或多個輸入資料表、預測函數或自訂演算式。</span><span class="sxs-lookup"><span data-stu-id="db44f-154">You can either use the mining model that is selected in the **Mining Model** table, the input table or tables that are selected in the **Select Input Table(s)** table, a prediction function, or a custom expression.</span></span>  
  
 <span data-ttu-id="db44f-155">可以從包含採礦模型的資料表和輸入資料表，將資料行拖曳到資料格。</span><span class="sxs-lookup"><span data-stu-id="db44f-155">Columns can be dragged from the tables containing the mining model and input tables onto the cell.</span></span>  
  
 <span data-ttu-id="db44f-156">**欄位**</span><span class="sxs-lookup"><span data-stu-id="db44f-156">**Field**</span></span>  
 <span data-ttu-id="db44f-157">從衍生自來源資料表的資料行清單中，選取一個資料行。</span><span class="sxs-lookup"><span data-stu-id="db44f-157">Select a column from the list of columns derived from the source table.</span></span> <span data-ttu-id="db44f-158">如果您在 **[來源]** 中選取 **[預測函數]**，這就會包含所選取採礦模型可以使用的預測函數。</span><span class="sxs-lookup"><span data-stu-id="db44f-158">If you selected **Prediction Function** in **Source**, this contains the prediction function available for the selected mining model.</span></span>  
  
 <span data-ttu-id="db44f-159">**群組**</span><span class="sxs-lookup"><span data-stu-id="db44f-159">**Group**</span></span>  
 <span data-ttu-id="db44f-160">配合 [及/或]\*\*\*\* 資料行，即可將運算式群組在一起。</span><span class="sxs-lookup"><span data-stu-id="db44f-160">Use with the **And/Or** column to group expressions together.</span></span> <span data-ttu-id="db44f-161">例如： `(expr1 Or expr2) And expr3` 。</span><span class="sxs-lookup"><span data-stu-id="db44f-161">For example, `(expr1 Or expr2) And expr3`.</span></span>  
  
 <span data-ttu-id="db44f-162">**和/或**</span><span class="sxs-lookup"><span data-stu-id="db44f-162">**And/Or**</span></span>  
 <span data-ttu-id="db44f-163">用於建立邏輯查詢。</span><span class="sxs-lookup"><span data-stu-id="db44f-163">Use to create a logical query.</span></span> <span data-ttu-id="db44f-164">例如： `(expr1 Or expr2) And expr3` 。</span><span class="sxs-lookup"><span data-stu-id="db44f-164">For example, `(expr1 Or expr2) And expr3`.</span></span>  
  
 <span data-ttu-id="db44f-165">**準則/引數**</span><span class="sxs-lookup"><span data-stu-id="db44f-165">**Criteria/Argument**</span></span>  
 <span data-ttu-id="db44f-166">指定套用至資料行的條件或使用者運算式。</span><span class="sxs-lookup"><span data-stu-id="db44f-166">Specify a condition or user expression that applies to the column.</span></span> <span data-ttu-id="db44f-167">可以從包含採礦模型的資料表和輸入資料表，將資料行拖曳到資料格。</span><span class="sxs-lookup"><span data-stu-id="db44f-167">Columns can be dragged from the tables containing the mining model and input tables onto the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db44f-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db44f-168">See Also</span></span>  
 <span data-ttu-id="db44f-169">[資料採礦延伸模組 &#40;DMX&#41; 語句參考](/sql/dmx/data-mining-extensions-dmx-statements) </span><span class="sxs-lookup"><span data-stu-id="db44f-169">[Data Mining Extensions &#40;DMX&#41; Statement Reference](/sql/dmx/data-mining-extensions-dmx-statements) </span></span>  
 <span data-ttu-id="db44f-170">[資料採礦查詢介面](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="db44f-170">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="db44f-171">預測查詢產生器 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="db44f-171">Prediction Query Builder &#40;Data Mining&#41;</span></span>](prediction-query-builder-data-mining.md)  
  
  
