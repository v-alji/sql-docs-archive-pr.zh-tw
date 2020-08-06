---
title: 將篩選套用至採礦模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filters [data mining]
- filtering input rows [Analysis Services]
- filtering data [Analysis Services]
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
author: minewiskan
ms.author: owend
ms.openlocfilehash: d9f3147c36e69d9c2249d5bf6d1ba201799c6e27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598062"
---
# <a name="apply-a-filter-to-a-mining-model"></a><span data-ttu-id="0c072-102">將篩選套用至採礦模型</span><span class="sxs-lookup"><span data-stu-id="0c072-102">Apply a Filter to a Mining Model</span></span>
  <span data-ttu-id="0c072-103">如果採礦結構包含巢狀資料表，則篩選可以套用至案例資料表、巢狀資料表或兩者。</span><span class="sxs-lookup"><span data-stu-id="0c072-103">If your mining structure contains a nested table, you can apply a filter to the case table, the nested table, or both.</span></span>  
  
 <span data-ttu-id="0c072-104">下列程序會示範如何建立兩種篩選：案例篩選及巢狀資料表資料列上的篩選。</span><span class="sxs-lookup"><span data-stu-id="0c072-104">The following procedure demonstrates how to create both kinds of filters: case filters, and filters on the nested table rows.</span></span>  
  
 <span data-ttu-id="0c072-105">案例資料表的條件將客戶限制為收入在 30000 和 40000 之間。</span><span class="sxs-lookup"><span data-stu-id="0c072-105">The condition on the case table restricts customers to those with income between 30000 and 40000.</span></span> <span data-ttu-id="0c072-106">巢狀資料表的條件則將客戶限制為未購買特定項目的對象。</span><span class="sxs-lookup"><span data-stu-id="0c072-106">The condition on the nested table restricts the customers to those who did not purchase a particular item.</span></span>  
  
 <span data-ttu-id="0c072-107">在此範例中建立的完整篩選條件如下：</span><span class="sxs-lookup"><span data-stu-id="0c072-107">The complete filter condition created in this example is as follows:</span></span>  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### <a name="to-create-a-case-filter-on-a-mining-model"></a><span data-ttu-id="0c072-108">若要建立採礦模型的案例篩選</span><span class="sxs-lookup"><span data-stu-id="0c072-108">To create a case filter on a mining model</span></span>  
  
1.  <span data-ttu-id="0c072-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的 [方案總管] 中，按一下包含要篩選的採礦模型的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="0c072-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model you want to filter.</span></span>  
  
2.  <span data-ttu-id="0c072-110">按一下 **[採礦模型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0c072-110">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="0c072-111">選擇模型，然後以滑鼠右鍵按一下，開啟快速鍵功能表。</span><span class="sxs-lookup"><span data-stu-id="0c072-111">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="0c072-112">-或-</span><span class="sxs-lookup"><span data-stu-id="0c072-112">-or-</span></span>  
  
     <span data-ttu-id="0c072-113">選取此模型。</span><span class="sxs-lookup"><span data-stu-id="0c072-113">Select the model.</span></span> <span data-ttu-id="0c072-114">然後在 [採礦模型]\*\*\*\* 功能表上，選取 [設定模組篩選器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c072-114">Then, on the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
4.  <span data-ttu-id="0c072-115">在 [模型篩選器]\*\*\*\* 對話方塊的 [採礦結構資料行]\*\*\*\* 文字方塊中，按一下方格中的上方資料列。</span><span class="sxs-lookup"><span data-stu-id="0c072-115">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
5.  <span data-ttu-id="0c072-116">如果資料來源包含單一的一般資料表，則下拉式清單僅會顯示該資料表中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="0c072-116">If the data source contains a single flat table, the drop-down list displays only the names of the columns in that table.</span></span>  
  
     <span data-ttu-id="0c072-117">如果採礦結構包含多個資料表，則清單會顯示來源資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c072-117">If the mining structure contains multiple tables, the list shows the names of the source tables.</span></span> <span data-ttu-id="0c072-118">在選取資料表之前，不會顯示資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="0c072-118">The column names do not display until a table has been selected.</span></span>  
  
     <span data-ttu-id="0c072-119">如果採礦結構包含案例資料表和巢狀資料表，則下拉式清單會顯示案例資料表的資料行以及巢狀資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c072-119">If the mining structure contains a case table and a nested table, the drop-down list shows columns from the case table, and the name of the nested table.</span></span>  
  
6.  <span data-ttu-id="0c072-120">從下拉式清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="0c072-120">Select a column from the drop-down list.</span></span>  
  
     <span data-ttu-id="0c072-121">文字方塊左側的圖示會變更，指出選取的項目是資料表或資料行。</span><span class="sxs-lookup"><span data-stu-id="0c072-121">The icon at the left side of the text box changes to indicate that the selected item is a table or a column.</span></span>  
  
7.  <span data-ttu-id="0c072-122">按一下 [運算子]\*\*\*\* 文字方塊，然後從清單選取運算子。</span><span class="sxs-lookup"><span data-stu-id="0c072-122">Click the **Operator** text box and select an operator from the list.</span></span> <span data-ttu-id="0c072-123">有效運算子會根據所選取資料行的資料類型而變更。</span><span class="sxs-lookup"><span data-stu-id="0c072-123">The valid operators change depending on the data type of the column you selected.</span></span>  
  
8.  <span data-ttu-id="0c072-124">按一下 [值]\*\*\*\* 文字方塊，然後在方塊中輸入值。</span><span class="sxs-lookup"><span data-stu-id="0c072-124">Click the **Value** text box, and type a value in the box.</span></span>  
  
     <span data-ttu-id="0c072-125">例如，選取 `Income` 做為資料行，選取大於運算子 ( # A0) ，然後輸入 `30000` 。</span><span class="sxs-lookup"><span data-stu-id="0c072-125">For example, select `Income` as the column, select the greater than operator (>), and then type `30000`.</span></span>  
  
9. <span data-ttu-id="0c072-126">在方格中，按下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="0c072-126">Click the next row in the grid.</span></span>  
  
     <span data-ttu-id="0c072-127">您所建立的篩選條件會自動加入 [運算式] 文字方塊。</span><span class="sxs-lookup"><span data-stu-id="0c072-127">The filter condition that you created is automatically added to the Expression text box.</span></span> <span data-ttu-id="0c072-128">例如， `[Income] > '30000'`</span><span class="sxs-lookup"><span data-stu-id="0c072-128">For example, `[Income] > '30000'`</span></span>  
  
10. <span data-ttu-id="0c072-129">在方格的下一個資料列中，按一下 [AND/OR]\*\*\*\* 文字方塊以加入條件。</span><span class="sxs-lookup"><span data-stu-id="0c072-129">Click the **AND/OR** text box in the next row of the grid to add a condition.</span></span>  
  
     <span data-ttu-id="0c072-130">例如，若要建立 BETWEEN 條件，請 `AND` 從邏輯運算元的下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="0c072-130">For example, to create a BETWEEN condition, select `AND` from the drop-down list of logical operands.</span></span>  
  
11. <span data-ttu-id="0c072-131">選取運算子並輸入值，如步驟 7 和 8 所述。</span><span class="sxs-lookup"><span data-stu-id="0c072-131">Select an operator and type a value as described in Steps 7 and 8.</span></span>  
  
     <span data-ttu-id="0c072-132">例如，再次選取 `Income` 做為資料行，選取小於運算子 ( # A0) ，然後輸入 `40000` 。</span><span class="sxs-lookup"><span data-stu-id="0c072-132">For example, select `Income` as the column again, select the less than operator (<), and then type `40000`.</span></span>  
  
12. <span data-ttu-id="0c072-133">在方格中，按下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="0c072-133">Click the next row in the grid.</span></span>  
  
13. <span data-ttu-id="0c072-134">在 [運算式] 文字方塊中的篩選條件會自動更新，以包含新的條件。</span><span class="sxs-lookup"><span data-stu-id="0c072-134">The filter condition in the Expression text box is automatically updated to include the new condition.</span></span> <span data-ttu-id="0c072-135">完成的運算式如下： `[Income] > '30000'AND [Income] < '40000'`</span><span class="sxs-lookup"><span data-stu-id="0c072-135">The completed expression is as follows: `[Income] > '30000'AND [Income] < '40000'`</span></span>  
  
### <a name="to-add-a-filter-on-the-nested-table-in-a-mining-model"></a><span data-ttu-id="0c072-136">若要在採礦模型中的巢狀資料表加入篩選</span><span class="sxs-lookup"><span data-stu-id="0c072-136">To add a filter on the nested table in a mining model</span></span>  
  
1.  <span data-ttu-id="0c072-137">在 [ \*\* \<name> 模型篩選器**] 對話方塊中，按一下 [**採礦結構\*\*資料行] 下方格中的空白資料列。</span><span class="sxs-lookup"><span data-stu-id="0c072-137">In the **\<name>Model Filter** Dialog box, click an empty row in the grid under **Mining Structure Column**.</span></span>  
  
2.  <span data-ttu-id="0c072-138">從下拉式清單選取巢狀資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c072-138">Select the name of the nested table from the drop-down list.</span></span>  
  
     <span data-ttu-id="0c072-139">文字方塊左側的圖示會變更，指出選取的項目是資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c072-139">The icon at the left side of the text box changes to indicate that the selected item is the name of a table.</span></span>  
  
3.  <span data-ttu-id="0c072-140">按一下 [運算子]\*\*\*\* 文字方塊，然後選取 [包含]\*\*\*\* 或 [不包含]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c072-140">Click the **Operator** text box and select **Contains** or **Not Contain**.</span></span>  
  
     <span data-ttu-id="0c072-141">這是 [模組篩選器]\*\*\*\* 對話方塊中，唯一可用於巢狀資料表的條件，因為您將案例資料表限制為僅在巢狀資料表中包含特定值的案例。</span><span class="sxs-lookup"><span data-stu-id="0c072-141">These are the only conditions available for the nested table in the **Model Filter** dialog box, because you are restricting the case table to only those cases that contain a certain value in the nested table.</span></span> <span data-ttu-id="0c072-142">下一個步驟將設定巢狀資料表的條件值。</span><span class="sxs-lookup"><span data-stu-id="0c072-142">You will set the value for the condition on the nested table in the next step.</span></span>  
  
4.  <span data-ttu-id="0c072-143">按一下 [**值**] 方塊，然後按一下 [ \*\* ( ...] ) \*\* ] 按鈕來建立運算式。</span><span class="sxs-lookup"><span data-stu-id="0c072-143">Click the **Value** box, and then click the **(...)** button to build an expression.</span></span>  
  
     <span data-ttu-id="0c072-144">[ \*\* \<name> 篩選\*\*] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0c072-144">The **\<name>Filter** dialog box opens.</span></span> <span data-ttu-id="0c072-145">這個對話方塊只能在目前的資料表上設定條件，在此例中為巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="0c072-145">This dialog box can set conditions only on the current table, which in this case is the nested table.</span></span>  
  
5.  <span data-ttu-id="0c072-146">按一下 [採礦結構資料列]\*\*\*\* 方塊，然後從巢狀資料表資料行的下拉式清單選取資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="0c072-146">Click the **Mining Structure Column** box and select a column name from the dropdown lists of nested table columns.</span></span>  
  
6.  <span data-ttu-id="0c072-147">按一下 [運算子]\*\*\*\*，然後從資料行的有效運算子清單選取運算子。</span><span class="sxs-lookup"><span data-stu-id="0c072-147">Click **Operator** and select an operator from the list of valid operators for the column.</span></span>  
  
7.  <span data-ttu-id="0c072-148">按一下 [值]\*\*\*\*，然後輸入值。</span><span class="sxs-lookup"><span data-stu-id="0c072-148">Click **Value** and type a value.</span></span>  
  
     <span data-ttu-id="0c072-149">例如，針對 [**採礦結構資料行]，** 選取 `Model` 。</span><span class="sxs-lookup"><span data-stu-id="0c072-149">For example, for **Mining Structure Column,** select `Model`.</span></span> <span data-ttu-id="0c072-150">針對 [**運算子**]，選取 `<>` ，然後輸入值 `Water Bottle` 。</span><span class="sxs-lookup"><span data-stu-id="0c072-150">For **Operator**, select `<>`, and type the value `Water Bottle`.</span></span> <span data-ttu-id="0c072-151">這種情況會建立下列篩選運算式：</span><span class="sxs-lookup"><span data-stu-id="0c072-151">This condition creates the following filter expression:</span></span>  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  <span data-ttu-id="0c072-152">由於巢狀資料表屬性的數目基本上並無限制，所以 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 不會提供可能值的清單以供選取。</span><span class="sxs-lookup"><span data-stu-id="0c072-152">Because the number of nested table attributes is potentially unlimited, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not supply a list of possible values from which to select.</span></span> <span data-ttu-id="0c072-153">您必須輸入確實的值。</span><span class="sxs-lookup"><span data-stu-id="0c072-153">You must type the exact value.</span></span> <span data-ttu-id="0c072-154">此外，您也不能在巢狀資料表中使用 LIKE 運算子。</span><span class="sxs-lookup"><span data-stu-id="0c072-154">Also, you cannot use a LIKE operator in a nested table.</span></span>  
  
1.  <span data-ttu-id="0c072-155">視需要新增更多條件， `AND` `OR` 並在 [**條件**] 方格左側的 [ **AND/or** ] 方塊中選取或來合併條件。</span><span class="sxs-lookup"><span data-stu-id="0c072-155">Add more conditions as necessary, combining the conditions by selecting `AND` or `OR` in the **AND/OR** box at the left side of the **Conditions** grid.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  <span data-ttu-id="0c072-156">在 [模型篩選器]\*\*\*\* 對話方塊中，檢閱您使用 [篩選器]\*\*\*\* 對話方塊建立的條件。</span><span class="sxs-lookup"><span data-stu-id="0c072-156">In the **Model Filter** dialog box, review the conditions that you created by using the **Filter** dialog box.</span></span> <span data-ttu-id="0c072-157">巢狀資料表的條件會附加至案例資料表的條件，完整的篩選條件集合會在 [運算式]\*\*\*\* 文字方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="0c072-157">The conditions for the nested table are appended to the conditions for the case table, and the complete set of filter conditions is displayed in the **Expression** text box.</span></span>  
  
3.  <span data-ttu-id="0c072-158">或者，您可以按一下 [編輯查詢]\*\*\*\*，手動變更篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="0c072-158">Optionally, click **Edit Query** to manually change the filter expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c072-159">如果您以手動方式變更篩選運算式的任何部分，則該方格會停用，之後就只能在文字編輯模式中使用篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="0c072-159">If you change any part of a filter expression manually, the grid will be disabled and thereafter you must work with the filter expression in text edit mode only.</span></span> <span data-ttu-id="0c072-160">若要還原方格編輯模式，必須清除篩選運算式並重新開始。</span><span class="sxs-lookup"><span data-stu-id="0c072-160">To restore grid editing mode, you must clear the filter expression and start over.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="0c072-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c072-161">See Also</span></span>  
 <span data-ttu-id="0c072-162">[&#40;Analysis Services 的採礦模型篩選-資料採礦&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0c072-162">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="0c072-163">[採礦模型工作和操作說明](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="0c072-163">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="0c072-164">從採礦模型刪除篩選</span><span class="sxs-lookup"><span data-stu-id="0c072-164">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
  
