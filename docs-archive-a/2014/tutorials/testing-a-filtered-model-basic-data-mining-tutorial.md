---
title: 測試已篩選的模型 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a97b5ca3523d1fc73405baba52b179a9bef04767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584874"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a><span data-ttu-id="9d22a-102">測試篩選過的模型 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="9d22a-102">Testing a Filtered Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="9d22a-103">既然您已判斷 `TM_Decision_Tree` 模型是最正確的，您將會自訂模型，以更符合 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 目標郵寄行銷活動的需求。</span><span class="sxs-lookup"><span data-stu-id="9d22a-103">Now that you have determined that the `TM_Decision_Tree` model is the most accurate, you will customize the model to better suit the needs of the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] targeted mailing campaign.</span></span> <span data-ttu-id="9d22a-104">具體而言，行銷部門想要知道男性和女性客戶之間是否有任何差異。</span><span class="sxs-lookup"><span data-stu-id="9d22a-104">Specifically, the Marketing department would like to know if there are any differences between male and female customers.</span></span> <span data-ttu-id="9d22a-105">這項資訊可協助該部門決定要使用哪些雜誌來登廣告，以及使用哪些產品當做郵寄活動的特色產品。</span><span class="sxs-lookup"><span data-stu-id="9d22a-105">The information could help them decide which magazines to use for advertising and which products to feature in their mailings.</span></span>  
  
## <a name="using-filters"></a><span data-ttu-id="9d22a-106">使用篩選</span><span class="sxs-lookup"><span data-stu-id="9d22a-106">Using Filters</span></span>  
 <span data-ttu-id="9d22a-107">篩選可讓您輕鬆地根據資料子集來建立模型。</span><span class="sxs-lookup"><span data-stu-id="9d22a-107">Filtering enables you to easily create models built on subsets of your data.</span></span> <span data-ttu-id="9d22a-108">篩選只會套用到模型中，而且不會變更基礎資料來源。</span><span class="sxs-lookup"><span data-stu-id="9d22a-108">The filter is applied only to the model and does not change the underlying data source.</span></span>  
  
 <span data-ttu-id="9d22a-109">在這一課，您將建立一個依性別篩選的模型，以便預測對於男性和女性購買行為最有影響力的特性。</span><span class="sxs-lookup"><span data-stu-id="9d22a-109">In this lesson, you will create a model that is filtered on gender, to predict the characteristics that most influence buying behavior in males and female.</span></span>  
  
 <span data-ttu-id="9d22a-110">首先，您會建立模型的複本 `TM_Decision_Tree` 。</span><span class="sxs-lookup"><span data-stu-id="9d22a-110">First you will make a copy of the `TM_Decision_Tree` model.</span></span>  
  
#### <a name="to-copy-the-decision-tree-model"></a><span data-ttu-id="9d22a-111">若要複製決策樹模型</span><span class="sxs-lookup"><span data-stu-id="9d22a-111">To copy the Decision Tree Model</span></span>  
  
1.  <span data-ttu-id="9d22a-112">在的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 方案總管中，選取 [ **BasicDataMining**]。</span><span class="sxs-lookup"><span data-stu-id="9d22a-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, select **BasicDataMining**.</span></span>  
  
2.  <span data-ttu-id="9d22a-113">按一下 **[採礦模型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9d22a-113">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="9d22a-114">以滑鼠右鍵按一下 `TM_Decision_Tree` 模型，然後選取 [新增] [**採礦模型]。**</span><span class="sxs-lookup"><span data-stu-id="9d22a-114">Right click the `TM_Decision_Tree` model, and select **New Mining Model.**</span></span>  
  
4.  <span data-ttu-id="9d22a-115">在 [**模型名稱**] 欄位中，輸入 `TM_Decision_Tree_Male` 。</span><span class="sxs-lookup"><span data-stu-id="9d22a-115">In the **Model name** field, type `TM_Decision_Tree_Male`.</span></span>  
  
5.  <span data-ttu-id="9d22a-116">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="9d22a-116">Click **OK**.</span></span>  
  
 <span data-ttu-id="9d22a-117">接下來，建立一個篩選來選取此模型的客戶 (根據客戶的性別)。</span><span class="sxs-lookup"><span data-stu-id="9d22a-117">Next, create a filter to select customers for the model based on their gender.</span></span>  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a><span data-ttu-id="9d22a-118">若要建立採礦模型的案例篩選</span><span class="sxs-lookup"><span data-stu-id="9d22a-118">To create a case filter on a mining model</span></span>  
  
1.  <span data-ttu-id="9d22a-119">以滑鼠右鍵按一下 [ `TM_Decision_Tree_Male` 採礦模型] 以開啟快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="9d22a-119">Right-click the `TM_Decision_Tree_Male` mining model to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="9d22a-120">-- 或 --</span><span class="sxs-lookup"><span data-stu-id="9d22a-120">-- or --</span></span>  
  
     <span data-ttu-id="9d22a-121">選取此模型。</span><span class="sxs-lookup"><span data-stu-id="9d22a-121">Select the model.</span></span> <span data-ttu-id="9d22a-122">在 **[採礦模型]** 功能表上，選取 **[設定模型篩選器]**。</span><span class="sxs-lookup"><span data-stu-id="9d22a-122">On the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
2.  <span data-ttu-id="9d22a-123">在 [模型篩選器]\*\*\*\* 對話方塊的 [採礦結構資料行]\*\*\*\* 文字方塊中，按一下方格中的上方資料列。</span><span class="sxs-lookup"><span data-stu-id="9d22a-123">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
     <span data-ttu-id="9d22a-124">下拉式清單只會顯示該資料表中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="9d22a-124">The drop-down list displays only the names of the columns in that table.</span></span>  
  
3.  <span data-ttu-id="9d22a-125">在 [採礦結構資料行] 文字方塊中，選取 [**性別**]。</span><span class="sxs-lookup"><span data-stu-id="9d22a-125">In the Mining Structure Column text box, select **Gender**.</span></span>  
  
     <span data-ttu-id="9d22a-126">文字方塊左側的圖示會變更，指出選取的項目是資料表或資料行。</span><span class="sxs-lookup"><span data-stu-id="9d22a-126">The icon at the left side of the text box changes to indicate that the selected item is a table or a column.</span></span>  
  
4.  <span data-ttu-id="9d22a-127">按一下 [**運算子**] 文字方塊，然後從清單中選取等於 (=) 運算子。</span><span class="sxs-lookup"><span data-stu-id="9d22a-127">Click the **Operator** text box and select the equal (=) operator from the list.</span></span>  
  
5.  <span data-ttu-id="9d22a-128">按一下 [**值**] 文字方塊，然後輸入**M**。</span><span class="sxs-lookup"><span data-stu-id="9d22a-128">Click the **Value** text box, and type **M**.</span></span>  
  
6.  <span data-ttu-id="9d22a-129">在方格中，按下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="9d22a-129">Click the next row in the grid.</span></span>  
  
7.  <span data-ttu-id="9d22a-130">按一下 **[確定]** 以關閉 [**模型篩選器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9d22a-130">Click **OK** to close the **Model Filter** dialog box.</span></span>  
  
     <span data-ttu-id="9d22a-131">篩選會顯示在 [**屬性**] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="9d22a-131">The filter displays in the **Properties** window.</span></span> <span data-ttu-id="9d22a-132">或者，您可以從 [**屬性**] 視窗啟動 [**模型篩選器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9d22a-132">Alternately, you can launch the **Model Filter** dialog from the **Properties** window.</span></span>  
  
8.  <span data-ttu-id="9d22a-133">重複上述步驟，但這次請在 `TM_Decision_Tree_Female` [**值**] 文字方塊中為模型命名並輸入**F** 。</span><span class="sxs-lookup"><span data-stu-id="9d22a-133">Repeat the above steps, but this time name the model `TM_Decision_Tree_Female` and type **F** in the **Value** text box.</span></span>  
  
## <a name="process-the-filtered-models"></a><span data-ttu-id="9d22a-134">處理篩選過的模型</span><span class="sxs-lookup"><span data-stu-id="9d22a-134">Process the Filtered Models</span></span>  
 <span data-ttu-id="9d22a-135">模型要等到部署及處理之後，才可以使用。</span><span class="sxs-lookup"><span data-stu-id="9d22a-135">Models cannot be used until they have been deployed and processed.</span></span> <span data-ttu-id="9d22a-136">如需處理模型的詳細資訊，請參閱在[目標郵寄結構中處理模型 &#40;基本資料採礦教學課程&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="9d22a-136">For more information on processing models, see [Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md).</span></span>  
  
#### <a name="to-process-the-filtered-model"></a><span data-ttu-id="9d22a-137">若要處理篩選過的模型</span><span class="sxs-lookup"><span data-stu-id="9d22a-137">To process the filtered model</span></span>  
  
1.  <span data-ttu-id="9d22a-138">以滑鼠右鍵按一下 `TM_Decision_Tree_Male` 模型，然後選取 [處理] [**採礦結構] 和 [所有模型**s]</span><span class="sxs-lookup"><span data-stu-id="9d22a-138">Right-click the `TM_Decision_Tree_Male` model and select **Process Mining Structure and all Model**s</span></span>  
  
2.  <span data-ttu-id="9d22a-139">按一下 [**執行**] 來處理新的模型。</span><span class="sxs-lookup"><span data-stu-id="9d22a-139">Click **Run** to process the new models.</span></span>  
  
3.  <span data-ttu-id="9d22a-140">處理完成之後，請按一下兩個處理視窗上的 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="9d22a-140">After processing is complete, click **Close** on both processing windows.</span></span>  
  
     <span data-ttu-id="9d22a-141">您現在會在 [**採礦模型**] 索引標籤中顯示兩個新模型。</span><span class="sxs-lookup"><span data-stu-id="9d22a-141">You now have two new models displayed in the **Mining Models** tab.</span></span>  
  
## <a name="evaluate-the-results"></a><span data-ttu-id="9d22a-142">評估結果</span><span class="sxs-lookup"><span data-stu-id="9d22a-142">Evaluate the Results</span></span>  
 <span data-ttu-id="9d22a-143">檢視結果，並評估篩選過之模型的正確性，就像之前三個模型的處理方式一樣。</span><span class="sxs-lookup"><span data-stu-id="9d22a-143">View the results and assess the accuracy of the filtered models in much the same way as you did for the previous three models.</span></span> <span data-ttu-id="9d22a-144">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="9d22a-144">For more information, see:</span></span>  
  
 [<span data-ttu-id="9d22a-145">流覽決策樹模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="9d22a-145">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="9d22a-146">使用增益圖測試精確度 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="9d22a-146">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a><span data-ttu-id="9d22a-147">若要探索篩選過的模型</span><span class="sxs-lookup"><span data-stu-id="9d22a-147">To explore the filtered models</span></span>  
  
1.  <span data-ttu-id="9d22a-148">在 [**資料採礦設計師**] 中選取 [**採礦模型檢視器**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9d22a-148">Select the **Mining Model Viewer** tab in **Data Mining Designer**.</span></span>  
  
2.  <span data-ttu-id="9d22a-149">在 [採礦模型] 方塊中，選取 `TM_Decision_Tree_Male` 。</span><span class="sxs-lookup"><span data-stu-id="9d22a-149">In the Mining Model box, select `TM_Decision_Tree_Male`.</span></span>  
  
3.  <span data-ttu-id="9d22a-150">將幻燈片**放映層級**設為 `3` 。</span><span class="sxs-lookup"><span data-stu-id="9d22a-150">Slide **Show Level** to `3`.</span></span>  
  
4.  <span data-ttu-id="9d22a-151">將 [**背景**] 值變更為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="9d22a-151">Change the **Background** value to `1`.</span></span>  
  
5.  <span data-ttu-id="9d22a-152">將游標放在標示為 [**全部**] 的節點上方，以查看自行車購買者與非自行車購買者的數目。</span><span class="sxs-lookup"><span data-stu-id="9d22a-152">Place your cursor over the node labeled **All** to see the number of bike buyers versus non-bike buyers.</span></span>  
  
6.  <span data-ttu-id="9d22a-153">針對，重複步驟 1-5 `TM_Decision_Tree_Female` 。</span><span class="sxs-lookup"><span data-stu-id="9d22a-153">Repeat steps 1 - 5 for `TM_Decision_Tree_Female`.</span></span>  
  
7.  <span data-ttu-id="9d22a-154">探索的結果 `TM_Decision_Tree` ，以及針對性別篩選的模型。</span><span class="sxs-lookup"><span data-stu-id="9d22a-154">Explore the results for the `TM_Decision_Tree` and the models filtered for gender.</span></span> <span data-ttu-id="9d22a-155">與所有自行車買主相較之下，男性和女性自行車買主與未篩選的自行車買主具有一些共同的特性，但是這三種買主也有一些有趣的差異。</span><span class="sxs-lookup"><span data-stu-id="9d22a-155">Compared to all bike buyers, male and female bike buyers share some of the same characteristics as the unfiltered bike buyers but all three have interesting differences as well.</span></span> <span data-ttu-id="9d22a-156">這是可用 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 來開發行銷活動的實用資訊。</span><span class="sxs-lookup"><span data-stu-id="9d22a-156">This is useful information that [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] can use to develop their marketing campaign.</span></span>  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a><span data-ttu-id="9d22a-157">若要測試篩選過之模型的增益</span><span class="sxs-lookup"><span data-stu-id="9d22a-157">To test the lift of the filtered models</span></span>  
  
1.  <span data-ttu-id="9d22a-158">在的資料採礦設計師中，切換至 [**挖掘精確度圖表**] 索引標籤 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，然後選取 [**輸入選擇**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9d22a-158">Switch to the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and select the **Input Selection** tab.</span></span>  
  
2.  <span data-ttu-id="9d22a-159">在 [**選取要用於精確度圖表的資料集**] 群組方塊中，選取 [**使用採礦結構測試案例**]。</span><span class="sxs-lookup"><span data-stu-id="9d22a-159">In the **Select data set to be used for Accuracy Chart** group box, select **Use mining structure test cases**.</span></span>  
  
3.  <span data-ttu-id="9d22a-160">在資料採礦設計師的 [**輸入選擇**] 索引標籤上，于 [**選取可預測的採礦模型資料行以顯示在增益圖中**] 底下，選取 [**同步處理預測資料行和值**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9d22a-160">On the **Input Selection** tab of Data Mining Designer, under **Select predictable mining model columns to show in the lift chart**, select the checkbox for **Synchronize Prediction Columns and Values**.</span></span>  
  
4.  <span data-ttu-id="9d22a-161">在 [**可預測的資料行名稱**] 資料行中，確認已為每個模型選取 [**自行車購買**者]。</span><span class="sxs-lookup"><span data-stu-id="9d22a-161">In the **Predictable Column Name** column, verify that **Bike Buyer** is selected for each model.</span></span>  
  
5.  <span data-ttu-id="9d22a-162">在 [**顯示**] 資料行中，選取每個模型。</span><span class="sxs-lookup"><span data-stu-id="9d22a-162">In the **Show** column, select each of the models.</span></span>  
  
6.  <span data-ttu-id="9d22a-163">在 [**預測值**] 資料行中，選取 `1` 。</span><span class="sxs-lookup"><span data-stu-id="9d22a-163">In the **Predict Value** column, select `1`.</span></span>  
  
7.  <span data-ttu-id="9d22a-164">選取 [增益**圖**] 索引標籤以顯示增益圖。</span><span class="sxs-lookup"><span data-stu-id="9d22a-164">Select the **Lift Chart** tab to display the lift chart.</span></span>  
  
     <span data-ttu-id="9d22a-165">您現在會注意到有三個決策樹模型與隨機猜測模型相較之下都有了顯著提升，而且也優於群集模型和貝氏機率分類模型。</span><span class="sxs-lookup"><span data-stu-id="9d22a-165">You will now notice that all three Decision Tree models provide significant lift compared to the random guess model, and also outperform the Clustering and Naive-Bayes models.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9d22a-166">相關工作</span><span class="sxs-lookup"><span data-stu-id="9d22a-166">Related Tasks</span></span>  
 <span data-ttu-id="9d22a-167">如需篩選的詳細資訊，請參閱[&#40;Analysis Services 資料採礦&#41;的採礦模型篩選](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="9d22a-167">For more information on filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="9d22a-168">如需如何將篩選套用至嵌套資料表的範例，請參閱[&#40;Analysis Services 資料採礦&#41;中的中繼資料採礦教學](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)課程。</span><span class="sxs-lookup"><span data-stu-id="9d22a-168">For an example of how to apply filters to nested tables, see [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="9d22a-169">本課程的前一項工作</span><span class="sxs-lookup"><span data-stu-id="9d22a-169">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="9d22a-170">使用增益圖測試精確度 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="9d22a-170">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="9d22a-171">下一課</span><span class="sxs-lookup"><span data-stu-id="9d22a-171">Next Lesson</span></span>  
 [<span data-ttu-id="9d22a-172">第 6 課：建立及處理預測 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="9d22a-172">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="9d22a-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d22a-173">See Also</span></span>  
 <span data-ttu-id="9d22a-174">[元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9d22a-174">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="9d22a-175">[採礦模型工作和操作說明](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="9d22a-175">[Mining Model Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="9d22a-176">[從採礦模型刪除篩選](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="9d22a-176">[Delete a Filter from a Mining Model](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md) </span></span>  
 [<span data-ttu-id="9d22a-177">採礦模型的篩選 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="9d22a-177">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
