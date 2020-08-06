---
title: 篩選模型中的嵌套資料表 (元資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1e6ce2936a3c6763ea41999b2724c0fe8c79301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706918"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="296b2-102">在採礦模型中篩選巢狀資料表 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="296b2-102">Filtering a Nested Table in a Mining Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="296b2-103">建立並探索模型之後，您決定要將焦點放在客戶資料子集上。</span><span class="sxs-lookup"><span data-stu-id="296b2-103">After you have created and explored the model, you decide that you want to focus on a subset of the customer data.</span></span> <span data-ttu-id="296b2-104">例如，您可能只要分析包含特定項目的購物籃，或是分析在特定期間未購買任何產品的客戶人口統計。</span><span class="sxs-lookup"><span data-stu-id="296b2-104">For example, you might want to analyze only the baskets that contain a specific item, or to analyze the demographics of customers who have not purchased anything in a certain period.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="296b2-105">提供了篩選採礦模型資料的功能。</span><span class="sxs-lookup"><span data-stu-id="296b2-105">provides the ability to filter the data that is used in a mining model.</span></span> <span data-ttu-id="296b2-106">這項功能很有用，因為您不需要設定新的資料來源視圖來使用不同的資料。</span><span class="sxs-lookup"><span data-stu-id="296b2-106">This feature is useful because you do not need to set up a new data source view to use different data.</span></span> <span data-ttu-id="296b2-107">在基本資料採礦教學課程中，您學會了如何對案例資料表套用條件，以篩選來自二維資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="296b2-107">In the Basic Data Mining Tutorial, you learned how to filter data from a flat table by applying conditions to the case table.</span></span> <span data-ttu-id="296b2-108">在這項工作中，您將建立套用至巢狀資料表的篩選。</span><span class="sxs-lookup"><span data-stu-id="296b2-108">In this task, you create a filter that applies to a nested table.</span></span>  
  
## <a name="filters-on-nested-vs-case-tables"></a><span data-ttu-id="296b2-109">巢狀和案例資料表的篩選</span><span class="sxs-lookup"><span data-stu-id="296b2-109">Filters on Nested vs. Case Tables</span></span>  
 <span data-ttu-id="296b2-110">如果您的資料來源檢視如同用於關聯模型的資料來源檢視，同樣包含一個案例資料表和一個巢狀資料表，您可以篩選來自案例資料表的值、巢狀資料表中存在或不存在的值，或是兩者的一些組合。</span><span class="sxs-lookup"><span data-stu-id="296b2-110">If your data source view contains a case table and a nested table, like the data source view used in the Association model, you can filter on values from the case table, the presence or absence of a value in the nested table, or some combination of both.</span></span>  
  
 <span data-ttu-id="296b2-111">在這項工作中，您要先建立一份關聯模型副本，然後將 IncomeGroup 和 Region 屬性加入新的相關模型中，以便在案例資料表中篩選這些屬性。</span><span class="sxs-lookup"><span data-stu-id="296b2-111">In this task, you will first make a copy of the Association model and then add the IncomeGroup and Region attributes to the new related model, so that you can filter on those attributes in the case table.</span></span>  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a><span data-ttu-id="296b2-112">建立並修改關聯模型副本</span><span class="sxs-lookup"><span data-stu-id="296b2-112">To create and modify a copy of the Association model</span></span>  
  
1.  <span data-ttu-id="296b2-113">在的 [**採礦模型**] 索引標籤中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，以滑鼠右鍵按一下 `Association` 模型，然後選取 [新增] [**採礦模型**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-113">In the **Mining Models** tab of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click the `Association` model, and select **New Mining Model**.</span></span>  
  
2.  <span data-ttu-id="296b2-114">針對 [**模型名稱**]，輸入 `Association Filtered` 。</span><span class="sxs-lookup"><span data-stu-id="296b2-114">For **Model Name**, type `Association Filtered`.</span></span> <span data-ttu-id="296b2-115">在 [**演算法名稱]** 中，選取 [ **Microsoft 關聯規則**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-115">For **Algorithm Name**, select **Microsoft Association Rules**.</span></span> <span data-ttu-id="296b2-116">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="296b2-116">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="296b2-117">在 [關聯] 篩選模型的資料行中，按一下 [IncomeGroup] 資料列，並將值從 [**忽略**] 變更為 [**輸入**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-117">In the column for the Association Filtered model, click the IncomeGroup row and change the value from **Ignore** to **Input**.</span></span>  
  
 <span data-ttu-id="296b2-118">接下來，您將在新的關聯模型中的案例資料表上建立篩選。</span><span class="sxs-lookup"><span data-stu-id="296b2-118">Next, you will create a filter on the case table in the new association model.</span></span> <span data-ttu-id="296b2-119">篩選只會將目標區域的客戶或是具有目標收入等級的客戶傳往模型。</span><span class="sxs-lookup"><span data-stu-id="296b2-119">The filter will pass to the model only the customers in the target region or with the target income level.</span></span> <span data-ttu-id="296b2-120">然後，您要加入第二組篩選條件，指定模型只使用購物籃至少包含一個項目的客戶。</span><span class="sxs-lookup"><span data-stu-id="296b2-120">Then, you will add a second set of filter conditions to specify that the model uses only customers whose shopping baskets contained at least one item.</span></span>  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a><span data-ttu-id="296b2-121">將篩選加入採礦模型</span><span class="sxs-lookup"><span data-stu-id="296b2-121">To add a filter to a mining model</span></span>  
  
1.  <span data-ttu-id="296b2-122">在 [**採礦模型**] 索引標籤中，以滑鼠右鍵按一下已篩選的模型關聯，然後選取 [**設定模型篩選**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-122">In the **Mining Models** tab, right-click the model Association Filtered, and select **Set Model Filter**.</span></span>  
  
2.  <span data-ttu-id="296b2-123">在 [模型篩選器]\*\*\*\* 對話方塊的 [採礦結構資料行]\*\*\*\* 文字方塊中，按一下方格中的上方資料列。</span><span class="sxs-lookup"><span data-stu-id="296b2-123">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
3.  <span data-ttu-id="296b2-124">在 [**採礦結構資料行**] 文字方塊中，選取 [IncomeGroup]。</span><span class="sxs-lookup"><span data-stu-id="296b2-124">In the **Mining Structure Column** text box, select IncomeGroup.</span></span>  
  
     <span data-ttu-id="296b2-125">文字方塊左側的圖示會變更，指出選取的項目是資料行。</span><span class="sxs-lookup"><span data-stu-id="296b2-125">The icon at the left side of the text box changes to indicate that the selected item is a column.</span></span>  
  
4.  <span data-ttu-id="296b2-126">按一下 [**運算子**] 文字方塊，然後 **=** 從清單中選取運算子。</span><span class="sxs-lookup"><span data-stu-id="296b2-126">Click the **Operator** text box and select the **=** operator from the list.</span></span>  
  
5.  <span data-ttu-id="296b2-127">按一下 [**值**] 文字方塊，然後 `High` 在方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="296b2-127">Click the **Value** text box, and type `High` in the box.</span></span>  
  
6.  <span data-ttu-id="296b2-128">在方格中，按下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="296b2-128">Click the next row in the grid.</span></span>  
  
7.  <span data-ttu-id="296b2-129">在方格的下一個資料列中，按一下 [ **AND/OR** ] 文字方塊，然後選取 [ **OR**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-129">Click the **AND/OR** text box in the next row of the grid and select **OR**.</span></span>  
  
8.  <span data-ttu-id="296b2-130">在 [**採礦結構資料行**] 文字方塊中，選取 [IncomeGroup]。</span><span class="sxs-lookup"><span data-stu-id="296b2-130">In the **Mining Structure Column** text box, select IncomeGroup.</span></span> <span data-ttu-id="296b2-131">在 [**值**] 文字方塊中，輸入 `Moderate` 。</span><span class="sxs-lookup"><span data-stu-id="296b2-131">In the **Value** text box, type `Moderate`.</span></span>  
  
     <span data-ttu-id="296b2-132">您所建立的篩選準則會自動加入 [**運算式**] 文字方塊中，而且應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="296b2-132">The filter condition that you created is automatically added to the **Expression** text box, and should appears as follows:</span></span>  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. <span data-ttu-id="296b2-133">按一下方格中的下一個資料列，將運算子保留為預設值**和**。</span><span class="sxs-lookup"><span data-stu-id="296b2-133">Click the next row in the grid, leaving the operator as the default, **AND**.</span></span>  
  
10. <span data-ttu-id="296b2-134">針對 [**運算子**]，保留預設值 [**包含**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-134">For **Operator**, leave the default value, **Contains**.</span></span> <span data-ttu-id="296b2-135">按一下 [**值**] 文字方塊。</span><span class="sxs-lookup"><span data-stu-id="296b2-135">Click the **Value** text box.</span></span>  
  
11. <span data-ttu-id="296b2-136">在 [**篩選**] 對話方塊中，于 [**採礦結構**資料行] 下的第一個資料列中，選取 `Model` 。</span><span class="sxs-lookup"><span data-stu-id="296b2-136">In the **Filter** dialog box, in the first row under **Mining Structure Column**, select `Model`.</span></span>  
  
12. <span data-ttu-id="296b2-137">針對 [**運算子**]，選取 [不**是 Null**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-137">For **Operator**, select **IS NOT NULL**.</span></span> <span data-ttu-id="296b2-138">將 [**值**] 文字方塊保留空白。</span><span class="sxs-lookup"><span data-stu-id="296b2-138">Leave the **Value** text box blank.</span></span> <span data-ttu-id="296b2-139">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="296b2-139">Click **OK**.</span></span>  
  
     <span data-ttu-id="296b2-140">[**模型篩選器**] 對話方塊之 [**運算式**] 文字方塊中的篩選準則會自動更新，以在嵌套資料表上包含新的條件。</span><span class="sxs-lookup"><span data-stu-id="296b2-140">The filter condition in the **Expression** text box of the **Model Filter** dialog box is automatically updated to include the new condition on the nested table.</span></span> <span data-ttu-id="296b2-141">完成的運算式如下：</span><span class="sxs-lookup"><span data-stu-id="296b2-141">The completed expression is as follows:</span></span>  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a><span data-ttu-id="296b2-142">啟用鑽研並處理篩選模型</span><span class="sxs-lookup"><span data-stu-id="296b2-142">To enable drillthrough and to process the filtered model</span></span>  
  
1.  <span data-ttu-id="296b2-143">在 [**採礦模型**] 索引標籤中，以滑鼠右鍵按一下 `Association Filtered` 模型，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-143">In the **Mining Models** tab, right-click the `Association Filtered` model, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="296b2-144">將 [ **AllowDrillThrough** ] 屬性變更為 [ **True**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-144">Change the **AllowDrillThrough** property to **True**.</span></span>  
  
3.  <span data-ttu-id="296b2-145">以滑鼠右鍵按一下 [ `Association Filtered` 採礦模型]，然後選取 [**處理模型**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-145">Right-click the `Association Filtered` mining model, and select **Process Model**.</span></span>  
  
4.  <span data-ttu-id="296b2-146">在錯誤訊息中按一下 **[是]** ，將新模型部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="296b2-146">Click **Yes** in the error message to deploy the new model to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
5.  <span data-ttu-id="296b2-147">在 [**處理採礦結構**] 對話方塊中，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="296b2-147">In the **Process Mining Structure** dialog box, click **Run**.</span></span>  
  
6.  <span data-ttu-id="296b2-148">當處理完成時，請按一下 [**關閉] 結束**[**處理進度**] 對話方塊，然後按一下 [關閉] 以**結束**[**處理常式採礦結構**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="296b2-148">When processing is complete click **Close** to exit the **Process Progress** dialog box, and click **Close** again to exit the **Process Mining Structure** dialog box.</span></span>  
  
 <span data-ttu-id="296b2-149">您可以使用 Microsoft 一般內容樹狀檢視器進行確認，並且針對所包含案例少於原始模型的篩選模型，查看 NODE_SUPPORT 的值。</span><span class="sxs-lookup"><span data-stu-id="296b2-149">You can verify by using the Microsoft Generic Content Tree viewer and looking at the value for NODE_SUPPORT that the filtered model contains fewer cases than the original model.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="296b2-150">備註</span><span class="sxs-lookup"><span data-stu-id="296b2-150">Remarks</span></span>  
 <span data-ttu-id="296b2-151">您剛建立的巢狀資料表篩選器只會檢查巢狀資料表中至少一個資料列的存在。不過，您也可以建立篩選條件，檢查特定產品的存在。</span><span class="sxs-lookup"><span data-stu-id="296b2-151">The nested table filter that you just created checks only for the presence of at least one row in the nested table; however, you can also create filter conditions that check for the presence of specific products.</span></span>  <span data-ttu-id="296b2-152">例如，您可以建立下列篩選：</span><span class="sxs-lookup"><span data-stu-id="296b2-152">For example, you could create the following filter:</span></span>  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 <span data-ttu-id="296b2-153">這個陳述式代表您要將案例資料表上的客戶限制在已購買水壺 (Water Bottle) 的客戶。</span><span class="sxs-lookup"><span data-stu-id="296b2-153">This statement means that you are restricting the customers from the case table to only those who have purchased a water bottle.</span></span> <span data-ttu-id="296b2-154">不過，由於巢狀資料表屬性的數目基本上並無限制，所以 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 不會提供可能值的清單以供選取。</span><span class="sxs-lookup"><span data-stu-id="296b2-154">However, because the number of nested table attributes is potentially unlimited, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not supply a list of possible values from which to select.</span></span> <span data-ttu-id="296b2-155">因此，您必須輸入確實的值。</span><span class="sxs-lookup"><span data-stu-id="296b2-155">Instead, you must type the exact value.</span></span>  
  
 <span data-ttu-id="296b2-156">您可以按一下 [**編輯查詢**]，手動變更篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="296b2-156">You can click **Edit Query** to manually change the filter expression.</span></span> <span data-ttu-id="296b2-157">不過，如果以手動方式變更了篩選運算式的任何部分，則該方格會停用，之後就只能在文字編輯模式中使用篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="296b2-157">However, if you change any part of a filter expression manually, the grid will be disabled and thereafter you must work with the filter expression in text edit mode only.</span></span> <span data-ttu-id="296b2-158">若要還原方格編輯模式，必須清除篩選運算式並重新開始。</span><span class="sxs-lookup"><span data-stu-id="296b2-158">To restore grid editing mode, you must clear the filter expression and start over.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="296b2-159">您無法在巢狀資料表篩選中使用 LIKE 運算子。</span><span class="sxs-lookup"><span data-stu-id="296b2-159">You cannot use the LIKE operator in a nested table filter.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="296b2-160">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="296b2-160">Next Task in Lesson</span></span>  
 [<span data-ttu-id="296b2-161">&#40;中繼資料採礦教學課程來預測關聯&#41;</span><span class="sxs-lookup"><span data-stu-id="296b2-161">Predicting Associations &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="296b2-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="296b2-162">See Also</span></span>  
 <span data-ttu-id="296b2-163">[模型篩選語法和範例 &#40;Analysis Services-資料採礦&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="296b2-163">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="296b2-164">採礦模型的篩選 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="296b2-164">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
