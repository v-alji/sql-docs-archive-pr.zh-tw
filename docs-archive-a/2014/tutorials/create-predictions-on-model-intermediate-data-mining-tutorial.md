---
title: 在時序群集模型上建立預測 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 2402c28a564502df9ce12c5e3f97b9d19590cfea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584213"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="585a0-102">在時序群集模型上建立預測 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="585a0-102">Creating Predictions on a Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="585a0-103">在檢視器中流覽時序群集模型之後，您可以在 [資料採礦設計師] 的 [**採礦模型預測**] 索引標籤上使用預測查詢產生器來建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="585a0-103">After you understand the sequence clustering model better by browsing it in the viewer, you can create prediction queries by using Prediction Query Builder on the **Mining Model Prediction** tab in Data Mining Designer.</span></span> <span data-ttu-id="585a0-104">若要建立預測，請先選取時序群集模型，然後再選取輸入資料。</span><span class="sxs-lookup"><span data-stu-id="585a0-104">To create a prediction, you first select the sequence clustering model, and then select the input data.</span></span> <span data-ttu-id="585a0-105">對於輸入而言，您可以使用外部資料來源，或是建立單一查詢，並在對話方塊中提供值。</span><span class="sxs-lookup"><span data-stu-id="585a0-105">For inputs, you can use either an external data source, or you can build a singleton query and provide values in a dialog box.</span></span>  
  
 <span data-ttu-id="585a0-106">本課程假設您已經熟悉如何使用預測查詢產生器，並想要學習如何建立時序群集模型所特有的查詢。</span><span class="sxs-lookup"><span data-stu-id="585a0-106">This lesson assumes that you are already familiar with how to use the prediction query builder and want to learn how to build queries that are specific to a sequence clustering model.</span></span> <span data-ttu-id="585a0-107">如需如何使用預測查詢產生器的一般資訊，請參閱[資料採礦查詢介面](../../2014/analysis-services/data-mining/data-mining-query-tools.md)或基本資料採礦教學課程的一節，[建立預測 &#40;基本資料採礦教學課程&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="585a0-107">For general information about how to use Prediction Query Builder, see [Data Mining Query Interfaces](../../2014/analysis-services/data-mining/data-mining-query-tools.md) or the section of the Basic Data Mining tutorial, [Creating Predictions &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).</span></span>  
  
## <a name="creating-predictions-on-the-regional-model"></a><span data-ttu-id="585a0-108">在地區模型上建立預測</span><span class="sxs-lookup"><span data-stu-id="585a0-108">Creating Predictions on the Regional Model</span></span>  
 <span data-ttu-id="585a0-109">在此案例中，您會先建立某些單一預測查詢，以了解預測可能會因地區而異的大概情況。</span><span class="sxs-lookup"><span data-stu-id="585a0-109">For this scenario, you will first create some singleton prediction queries, to get an idea of how predictions might be different by region.</span></span>  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a><span data-ttu-id="585a0-110">若要在時序群集模型上建立單一查詢</span><span class="sxs-lookup"><span data-stu-id="585a0-110">To create a singleton query on a sequence clustering model</span></span>  
  
1.  <span data-ttu-id="585a0-111">按一下資料採礦設計師的 [**採礦模型預測**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="585a0-111">Click the **Mining Model Prediction** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="585a0-112">在 [**採礦模型**資料行] 功能表中，選取 [**單一查詢**]。</span><span class="sxs-lookup"><span data-stu-id="585a0-112">In the **Mining Model** column menu, select **Singleton Query**.</span></span>  
  
     <span data-ttu-id="585a0-113">[**採礦模型**窗格] 和 [**單一查詢輸入**] 窗格隨即出現。</span><span class="sxs-lookup"><span data-stu-id="585a0-113">The **Mining Model** pane and **Singleton Query Input** pane appear.</span></span>  
  
3.  <span data-ttu-id="585a0-114">在 [**採礦模型**] 窗格中，按一下 [**選取模型**]。</span><span class="sxs-lookup"><span data-stu-id="585a0-114">In the **Mining Model** pane, click **Select Model**.</span></span> <span data-ttu-id="585a0-115">(如果已經選取時序群集模型，您可以略過這個步驟)。</span><span class="sxs-lookup"><span data-stu-id="585a0-115">(You can skip this step if the sequence clustering mode is already selected.)</span></span>  
  
     <span data-ttu-id="585a0-116">[**選取採礦模型**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="585a0-116">The **Select Mining Model** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="585a0-117">展開代表**具有 [區域**] 之 [採礦結構序列叢集] 的節點，然後選取 [**具有區域**的模型順序叢集]。</span><span class="sxs-lookup"><span data-stu-id="585a0-117">Expand the node that represents the mining structure **Sequence Clustering with Region**, and select the model **Sequence Clustering with Region**.</span></span> <span data-ttu-id="585a0-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="585a0-118">Click **OK**.</span></span> <span data-ttu-id="585a0-119">現在請先忽略輸入窗格；當您設定完預測函數之後，您將會指定輸入。</span><span class="sxs-lookup"><span data-stu-id="585a0-119">For now, ignore the input pane; you will specify the inputs after you have set up the prediction functions.</span></span>  
  
5.  <span data-ttu-id="585a0-120">在方格中，按一下 [**來源**] 底下的空白資料格，然後選取 [**預測函數]。**</span><span class="sxs-lookup"><span data-stu-id="585a0-120">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="585a0-121">在 [**欄位**] 底下的資料格中，選取 [ **PredictSequence**]。</span><span class="sxs-lookup"><span data-stu-id="585a0-121">In the cell under **Field**, select **PredictSequence**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="585a0-122">您也可以使用**Predict**函數。</span><span class="sxs-lookup"><span data-stu-id="585a0-122">You can also use the **Predict** function.</span></span> <span data-ttu-id="585a0-123">如果您這樣做，請務必選擇採用資料表資料行做為引數的**Predict**函數版本。</span><span class="sxs-lookup"><span data-stu-id="585a0-123">If you do, be sure to choose the version of the **Predict** function that takes a table column as argument..</span></span>  
  
6.  <span data-ttu-id="585a0-124">在 [**採礦模型**] 窗格中，選取 [nested] 資料表 `v Assoc Seq Line Items` ，並將它拖曳到方格中，指向**PredictSequence**函數的 [**準則/引數**] 方塊。</span><span class="sxs-lookup"><span data-stu-id="585a0-124">In the **Mining Model** pane, select the nested table `v Assoc Seq Line Items`, and drag it into the grid, to the **Criteria/Argument** box for the **PredictSequence** function.</span></span>  
  
     <span data-ttu-id="585a0-125">拖曳資料表和資料行名稱可讓您建立複雜的陳述式，而不會發生語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="585a0-125">Dragging and dropping table and column names enables you to build complex statements without syntax errors.</span></span> <span data-ttu-id="585a0-126">不過，它會取代資料格的目前內容，其中包括**PredictSequence**函數的其他選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="585a0-126">However, it replaces the current contents of the cell, which include other optional arguments for the **PredictSequence** function.</span></span> <span data-ttu-id="585a0-127">若要檢視其他引數，您可以暫時將此函數的第二個執行個體加入至方格內以供參考。</span><span class="sxs-lookup"><span data-stu-id="585a0-127">To view the other arguments, you can temporarily add a second instance of the function to the grid for reference.</span></span>  
  
7.  <span data-ttu-id="585a0-128">按一下預測查詢產生器上方角落的 [**結果**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="585a0-128">Click the **Result** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="585a0-129">預期的結果會包含具有標題**運算式**的單一資料行。</span><span class="sxs-lookup"><span data-stu-id="585a0-129">The expected results contain a single column with the heading **Expression**.</span></span> <span data-ttu-id="585a0-130">[**運算式**] 資料行包含具有三個數據行的嵌套資料表，如下所示：</span><span class="sxs-lookup"><span data-stu-id="585a0-130">The **Expression** column contains a nested table with three columns as follows:</span></span>  
  
|<span data-ttu-id="585a0-131">$SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="585a0-131">$SEQUENCE</span></span>|<span data-ttu-id="585a0-132">Line Number</span><span class="sxs-lookup"><span data-stu-id="585a0-132">Line Number</span></span>|<span data-ttu-id="585a0-133">模型</span><span class="sxs-lookup"><span data-stu-id="585a0-133">Model</span></span>|  
|---------------|-----------------|-----------|  
|<span data-ttu-id="585a0-134">1</span><span class="sxs-lookup"><span data-stu-id="585a0-134">1</span></span>||<span data-ttu-id="585a0-135">Mountain-200</span><span class="sxs-lookup"><span data-stu-id="585a0-135">Mountain-200</span></span>|  
  
 <span data-ttu-id="585a0-136">這些結果代表什麼意思？</span><span class="sxs-lookup"><span data-stu-id="585a0-136">What do these results mean?</span></span> <span data-ttu-id="585a0-137">請記得您並未指定任何輸入。</span><span class="sxs-lookup"><span data-stu-id="585a0-137">Remember that you did not specify any inputs.</span></span> <span data-ttu-id="585a0-138">因此，將會針對整個案例母體擴展進行預測，而且 Analysis Services 會傳回整體上最有可能的預測。</span><span class="sxs-lookup"><span data-stu-id="585a0-138">Therefore, the prediction is made against the entire population of cases, and Analysis Services returns the most likely prediction overall.</span></span>  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a><span data-ttu-id="585a0-139">將輸入加入至單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="585a0-139">Adding Inputs to a Singleton Prediction Query</span></span>  
 <span data-ttu-id="585a0-140">在此之前，您並未指定任何輸入。</span><span class="sxs-lookup"><span data-stu-id="585a0-140">Until now, you have not specified any inputs.</span></span> <span data-ttu-id="585a0-141">在下一個工作中，您將使用 [**單一查詢輸入**] 窗格來指定查詢的某些輸入。</span><span class="sxs-lookup"><span data-stu-id="585a0-141">In the next task, you will use the **Singleton Query Input** pane to specify some inputs to the query.</span></span> <span data-ttu-id="585a0-142">首先，您將會使用 [地區] 當做地區時序群集模型的輸入，以判斷是否所有地區的預測時序都是相同的。</span><span class="sxs-lookup"><span data-stu-id="585a0-142">First, you will use [Region] as an input to the regional sequence clustering model, to determine whether the predicted sequences are the same for all regions.</span></span> <span data-ttu-id="585a0-143">然後您將學習如何修改查詢，為每一個預測增加機率，並讓結果扁平化，好讓您更輕鬆地檢視結果。</span><span class="sxs-lookup"><span data-stu-id="585a0-143">You will then learn how to modify the query to add the probability for each prediction, and flatten the results to make them easier to view.</span></span>  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a><span data-ttu-id="585a0-144">若要針對特定的客戶群組產生預測</span><span class="sxs-lookup"><span data-stu-id="585a0-144">To generate predictions for a specific customer group</span></span>  
  
1.  <span data-ttu-id="585a0-145">按一下預測查詢產生器左上角的 [**設計**] 按鈕，切換回查詢建立方格。</span><span class="sxs-lookup"><span data-stu-id="585a0-145">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="585a0-146">在 [**單一查詢輸入**] 對話方塊中，按一下的 [**值**] 方塊 `Region` ，然後選取 [**歐洲**]。</span><span class="sxs-lookup"><span data-stu-id="585a0-146">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select **Europe**.</span></span>  
  
3.  <span data-ttu-id="585a0-147">按一下 [**結果**] 按鈕，以查看歐洲客戶的預測。</span><span class="sxs-lookup"><span data-stu-id="585a0-147">Click the **Result** button to view predictions for customers in Europe.</span></span>  
  
4.  <span data-ttu-id="585a0-148">按一下預測查詢產生器左上角的 [**設計**] 按鈕，切換回查詢建立方格。</span><span class="sxs-lookup"><span data-stu-id="585a0-148">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
5.  <span data-ttu-id="585a0-149">在 [**單一查詢輸入**] 對話方塊中，按一下的 [**值**] 方塊 `Region` ，然後選取 [**北美洲**]。</span><span class="sxs-lookup"><span data-stu-id="585a0-149">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select **North America**.</span></span>  
  
6.  <span data-ttu-id="585a0-150">按一下 [**結果**] 按鈕，以在北美洲中查看客戶的預測。</span><span class="sxs-lookup"><span data-stu-id="585a0-150">Click the **Result** button to view predictions for customers in North America.</span></span>  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a><span data-ttu-id="585a0-151">使用自訂運算式增加機率</span><span class="sxs-lookup"><span data-stu-id="585a0-151">Adding Probabilities by Using a Custom Expression</span></span>  
 <span data-ttu-id="585a0-152">輸出每一個預測的機率稍微複雜一點，因為機率是預測的一個屬性，而且會輸出為巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="585a0-152">To output the probability for each prediction is slightly more complicated, because the probability is an attribute of the prediction and is output as a nested table.</span></span> <span data-ttu-id="585a0-153">如果您很熟悉資料採礦延伸模組 (DMX)，您可以輕鬆地改變查詢，以便在巢狀資料表上加入子 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="585a0-153">If you are familiar with Data Mining Extensions (DMX), you can easily alter the query to add a sub-select statement on the nested table.</span></span> <span data-ttu-id="585a0-154">但是，您也可以在預測查詢產生器中建立子 SELECT 陳述式，其方式是加入自訂運算式。</span><span class="sxs-lookup"><span data-stu-id="585a0-154">However, you can also create a sub-select statement in the Prediction Query Builder by adding a custom expression.</span></span>  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a><span data-ttu-id="585a0-155">使用自訂運算式輸出預測之時序的機率</span><span class="sxs-lookup"><span data-stu-id="585a0-155">To output probabilities for a predicted sequence by using a custom expression</span></span>  
  
1.  <span data-ttu-id="585a0-156">按一下預測查詢產生器左上角的 [**設計**] 按鈕，切換回查詢建立方格。</span><span class="sxs-lookup"><span data-stu-id="585a0-156">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="585a0-157">在方格的 [**來源**] 底下，按一下新的資料列，然後選取 [**自訂表格達式**]。</span><span class="sxs-lookup"><span data-stu-id="585a0-157">In the grid, under **Source**, click a new row, and select **Custom Expression**.</span></span>  
  
3.  <span data-ttu-id="585a0-158">將 [**欄位**] 底下的方塊保留空白。</span><span class="sxs-lookup"><span data-stu-id="585a0-158">Leave the box under **Field** blank.</span></span>  
  
4.  <span data-ttu-id="585a0-159">針對 [**別名**]，輸入 `t` 。</span><span class="sxs-lookup"><span data-stu-id="585a0-159">For **Alias**, type `t`.</span></span>  
  
5.  <span data-ttu-id="585a0-160">在 [**準則/引數**] 方塊中，輸入完整的子 select 語句，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="585a0-160">In the **Criteria/Argument** box, type the complete sub-select statement as shown in the following code sample.</span></span> <span data-ttu-id="585a0-161">請務必包含左右括號。</span><span class="sxs-lookup"><span data-stu-id="585a0-161">Be sure to include the starting and ending parentheses.</span></span>  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  <span data-ttu-id="585a0-162">按一下 [**結果**] 按鈕，以查看歐洲客戶的預測。</span><span class="sxs-lookup"><span data-stu-id="585a0-162">Click the **Result** button to view predictions for customers in Europe.</span></span>  
  
 <span data-ttu-id="585a0-163">結果現在包含兩個巢狀資料表，其中一個包含預測，另一個包含預測的機率。</span><span class="sxs-lookup"><span data-stu-id="585a0-163">The results now contain two nested tables, one with the prediction, and one with the probability for the prediction.</span></span> <span data-ttu-id="585a0-164">如果此查詢無效，您可以切換到查詢設計檢視，並檢閱完整的查詢陳述式，應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="585a0-164">If the query does not work, you can switch to query design view and review the complete query statement, which should be as follows:</span></span>  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a><span data-ttu-id="585a0-165">使用結果</span><span class="sxs-lookup"><span data-stu-id="585a0-165">Working with Results</span></span>  
 <span data-ttu-id="585a0-166">當結果中有許多巢狀資料表時，您可能會想要扁平化結果，以方便檢視。</span><span class="sxs-lookup"><span data-stu-id="585a0-166">When there are many nested tables in the results, you might want to flatten the results for easier viewing.</span></span> <span data-ttu-id="585a0-167">若要這樣做，您可以手動修改查詢，並加入 `FLATTENED` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="585a0-167">To do this, you can manually modify the query and add the `FLATTENED` keyword.</span></span>  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a><span data-ttu-id="585a0-168">若要扁平化預測查詢中的巢狀資料列集</span><span class="sxs-lookup"><span data-stu-id="585a0-168">To flatten nested rowsets in a prediction query</span></span>  
  
1.  <span data-ttu-id="585a0-169">按一下預測查詢產生器角落的 [**查詢**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="585a0-169">Click the **Query** button in the corner of the Prediction Query Builder.</span></span>  
  
     <span data-ttu-id="585a0-170">此方格會變成開啟的窗格，您可以在此窗格中檢視及修改之前由預測查詢產生器所建立的 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="585a0-170">The grid changes to an open pane where you can view and modify the DMX statement that was created by the Prediction Query Builder.</span></span>  
  
2.  <span data-ttu-id="585a0-171">在 `SELECT` 關鍵字之後輸入 `FLATTENED`。</span><span class="sxs-lookup"><span data-stu-id="585a0-171">After the `SELECT` keyword, type `FLATTENED`.</span></span>  
  
     <span data-ttu-id="585a0-172">查詢的完整文字應該類似底下所示：</span><span class="sxs-lookup"><span data-stu-id="585a0-172">The complete text of the query should be similar to the following:</span></span>  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  <span data-ttu-id="585a0-173">按一下預測查詢產生器上方角落的 [**結果**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="585a0-173">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="585a0-174">在您已經手動編輯了查詢之後，如果您切換回 [設計] 檢視，一定會遺失變更。</span><span class="sxs-lookup"><span data-stu-id="585a0-174">After you have manually edited a query, you will not be able to switch back to Design view without losing the changes.</span></span> <span data-ttu-id="585a0-175">但是，您可將手動建立的 DMX 陳述式儲存到文字檔中，然後再切換回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="585a0-175">You can, however, save the DMX statement that you created manually to a text file, and then change back to Design view.</span></span> <span data-ttu-id="585a0-176">如果您這樣做，此查詢會還原成之前在 [設計] 檢視中有效的上一個版本。</span><span class="sxs-lookup"><span data-stu-id="585a0-176">When you do so, the query is reverted to the last version that was valid in Design view.</span></span>  
  
## <a name="creating-predictions-on-the-related-model"></a><span data-ttu-id="585a0-177">在相關模型上建立預測</span><span class="sxs-lookup"><span data-stu-id="585a0-177">Creating Predictions on the Related Model</span></span>  
 <span data-ttu-id="585a0-178">之前的範例使用案例資料表資料行 Region 當做單一預測查詢的輸入，因為您很有興趣知道此模型在地區之間是否有找到任何差異。</span><span class="sxs-lookup"><span data-stu-id="585a0-178">The previous examples used a case table column, Region, as the input to the singleton prediction query, because you were interested in knowing whether the model had found any differences between regions.</span></span> <span data-ttu-id="585a0-179">但是，在瀏覽此模型之後，您覺得這些差異並不是那麼大，所以無法根據地區自訂產品建議。</span><span class="sxs-lookup"><span data-stu-id="585a0-179">However, after exploring the model, you decided that the differences are not strong enough to justify customizing product recommendations by region.</span></span> <span data-ttu-id="585a0-180">您真正有興趣預測的是客戶選取的項目。</span><span class="sxs-lookup"><span data-stu-id="585a0-180">What you are really interested in predicting is the items that customers select.</span></span> <span data-ttu-id="585a0-181">因此在隨後的查詢中，您將會使用不包括地區的時序群集模型，為所有客戶產生建議。</span><span class="sxs-lookup"><span data-stu-id="585a0-181">Therefore, in the queries that follow, you will use the sequence clustering model that does not include Region, to generate recommendations for all customers.</span></span>  
  
### <a name="using-nested-table-columns-as-input"></a><span data-ttu-id="585a0-182">使用巢狀資料表資料行當做輸入</span><span class="sxs-lookup"><span data-stu-id="585a0-182">Using Nested Table Columns as Input</span></span>  
 <span data-ttu-id="585a0-183">首先，您將會建立單一預測查詢，該查詢會使用單一項目當做輸入，並傳回下一個最有可能的項目。</span><span class="sxs-lookup"><span data-stu-id="585a0-183">First you will create a singleton prediction query that takes a single item as input and returns the next most likely item.</span></span> <span data-ttu-id="585a0-184">若要取得這種類型的預測，您必須使用巢狀資料表資料行當做輸入值。</span><span class="sxs-lookup"><span data-stu-id="585a0-184">To get a prediction of this kind, you have to use a nested table column as the input value.</span></span> <span data-ttu-id="585a0-185">這是因為您所預測的屬性 Model 是巢狀資料表的一部分。</span><span class="sxs-lookup"><span data-stu-id="585a0-185">This is because the attribute that you are predicting, Model, is part of a nested table.</span></span> <span data-ttu-id="585a0-186">Analysis Services 提供 [**嵌套資料表輸入**] 對話方塊，可協助您使用預測查詢產生器，輕鬆地在嵌套資料表屬性上建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="585a0-186">Analysis Services provides the **Nested Table Input** dialog box to help you easily create prediction queries on nested table attributes, by using the Prediction Query Builder.</span></span>  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a><span data-ttu-id="585a0-187">若要使用巢狀資料表當做預測的輸入</span><span class="sxs-lookup"><span data-stu-id="585a0-187">To use a nested table as input to a prediction</span></span>  
  
1.  <span data-ttu-id="585a0-188">按一下預測查詢產生器左上角的 [**設計**] 按鈕，切換回查詢建立方格。</span><span class="sxs-lookup"><span data-stu-id="585a0-188">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="585a0-189">在 [**單一查詢輸入**] 對話方塊中，按一下的 [**值**] 方塊 `Region` ，然後選取空白資料列，以清除此欄位的輸入。</span><span class="sxs-lookup"><span data-stu-id="585a0-189">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select the empty row to clear the input for this field.</span></span>  
  
3.  <span data-ttu-id="585a0-190">在 [**單一查詢輸入**] 對話方塊中，按一下的 [**值**] 方塊 `vAssocSeqLineItems` ，然後按一下 [ ( ... ) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="585a0-190">In the **Singleton Query Input** dialog box, click the **Value** box for `vAssocSeqLineItems`, and then click the (...) button.</span></span>  
  
4.  <span data-ttu-id="585a0-191">按一下 [**嵌套資料表輸入**] 對話方塊中的 [**加入**]。</span><span class="sxs-lookup"><span data-stu-id="585a0-191">In the **Nested Table Input** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="585a0-192">在新的資料列中，按一下底下的方塊 `Model` ，然後從清單中選取 [旅行輪胎]。</span><span class="sxs-lookup"><span data-stu-id="585a0-192">In the new row, click the box under `Model`, and select Touring Tire from the list.</span></span> <span data-ttu-id="585a0-193">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="585a0-193">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="585a0-194">按一下 [**結果**] 按鈕以查看預測。</span><span class="sxs-lookup"><span data-stu-id="585a0-194">Click the **Result** button to view the predictions.</span></span>  
  
 <span data-ttu-id="585a0-195">此模型會針對選擇 Touring Tire 當做第一個項目的所有客戶建議以下的項目。</span><span class="sxs-lookup"><span data-stu-id="585a0-195">The model recommends the following next items for all customers who choose the Touring Tire as the first item.</span></span> <span data-ttu-id="585a0-196">您已經從模型的瀏覽知道，客戶經常會同時購買 Touring Tire 和 Touring Tire Tube 產品，所以這些建議似乎不錯。</span><span class="sxs-lookup"><span data-stu-id="585a0-196">You already know from exploring the model that customers frequently purchase the products Touring Tire and Touring Tire Tube together, so these recommendations look good.</span></span>  
  
|<span data-ttu-id="585a0-197">$SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="585a0-197">$SEQUENCE</span></span>|<span data-ttu-id="585a0-198">Line Number</span><span class="sxs-lookup"><span data-stu-id="585a0-198">Line Number</span></span>|<span data-ttu-id="585a0-199">模型</span><span class="sxs-lookup"><span data-stu-id="585a0-199">Model</span></span>|  
|---------------|-----------------|-----------|  
|<span data-ttu-id="585a0-200">1</span><span class="sxs-lookup"><span data-stu-id="585a0-200">1</span></span>||<span data-ttu-id="585a0-201">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="585a0-201">Touring Tire Tube</span></span>|  
|<span data-ttu-id="585a0-202">2</span><span class="sxs-lookup"><span data-stu-id="585a0-202">2</span></span>||<span data-ttu-id="585a0-203">Sport-100</span><span class="sxs-lookup"><span data-stu-id="585a0-203">Sport-100</span></span>|  
|<span data-ttu-id="585a0-204">3</span><span class="sxs-lookup"><span data-stu-id="585a0-204">3</span></span>||<span data-ttu-id="585a0-205">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="585a0-205">Long-Sleeve Logo Jersey</span></span>|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="585a0-206">使用巢狀資料表輸入建立大量預測查詢</span><span class="sxs-lookup"><span data-stu-id="585a0-206">Creating a Bulk Prediction Query using Nested Table Inputs</span></span>  
 <span data-ttu-id="585a0-207">現在，此模型建立的預測種類可供您在建議中使用，您對於這樣的結果感到滿意，而且您將會建立一個對應至外部資料來源的預測查詢。</span><span class="sxs-lookup"><span data-stu-id="585a0-207">Now that you are satisfied that the model creates the kind of predictions that you can use in making recommendations, you will create a prediction query that is mapped to an external data source.</span></span> <span data-ttu-id="585a0-208">該資料來源將會提供代表目前產品的值。</span><span class="sxs-lookup"><span data-stu-id="585a0-208">That data source will provide values representing current products.</span></span> <span data-ttu-id="585a0-209">因為您對於建立預測查詢來提供客戶識別碼和產品清單當做輸入很感興趣，所以您將會加入客戶資料表當做案例資料表，並加入購買資料表當做巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="585a0-209">Because you are interested in creating a prediction query that provides Customer ID and a list of products as input, you will add the customer table as the case table, and the purchases table as the nested table.</span></span> <span data-ttu-id="585a0-210">然後您會跟之前一樣加入預測函數來產生建議。</span><span class="sxs-lookup"><span data-stu-id="585a0-210">Then you will add prediction functions as you did previously to create recommendations.</span></span>  
  
 <span data-ttu-id="585a0-211">這是您在第 3 課中用來針對購物籃分析建立預測的相同程序；但是在時序群集模型中，預測也需要訂單當做輸入。</span><span class="sxs-lookup"><span data-stu-id="585a0-211">This is the same procedure that you use to create predictions for the market basket scenario in Lesson 3; however, in a sequence clustering model predictions also need the order as input.</span></span>  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="585a0-212">若要使用巢狀資料表輸入來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="585a0-212">To create a prediction query using nested table inputs</span></span>  
  
1.  <span data-ttu-id="585a0-213">在 [**採礦模型**] 窗格中，選取 [時序群集模型] （如果尚未選取）。</span><span class="sxs-lookup"><span data-stu-id="585a0-213">In the **Mining Model** pane, select the Sequence Clustering model, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="585a0-214">在 [**選取輸入資料表 (s) \*\* ] 對話方塊中，按一下 [**選取案例資料表\*\*]。</span><span class="sxs-lookup"><span data-stu-id="585a0-214">In the **Select Input Table(s)** dialog box, click **Select Case Table**.</span></span>  
  
3.  <span data-ttu-id="585a0-215">在 [**選取資料表**] 對話方塊中，針對 [資料來源] 選取 [訂單]。</span><span class="sxs-lookup"><span data-stu-id="585a0-215">In the **Select Table** dialog box, for Data Source, select Orders.</span></span> <span data-ttu-id="585a0-216">在 [**資料表/視圖名稱**] 清單中，選取 [vAssocSeqOrders]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="585a0-216">In the **Table/View Name** list, select vAssocSeqOrders, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="585a0-217">在 [**選取輸入資料表 (s) \*\* ] 對話方塊中，按一下 [**選取嵌套資料表\*\*]。</span><span class="sxs-lookup"><span data-stu-id="585a0-217">In the **Select Input Table(s)** dialog box, click **Select Nested Table**.</span></span>  
  
5.  <span data-ttu-id="585a0-218">在 [**選取資料表**] 對話方塊中，針對 [**資料來源**] 選取 [訂單]。</span><span class="sxs-lookup"><span data-stu-id="585a0-218">In the **Select Table** dialog box, for **Data Source**, select Orders.</span></span> <span data-ttu-id="585a0-219">在 [**資料表/視圖名稱**] 清單中，選取 [vAssocSeqLineItems]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="585a0-219">In the **Table/View name** list, select vAssocSeqLineItems, and then click **OK**.</span></span>  
  
     <span data-ttu-id="585a0-220">Analysis Services 將會嘗試偵測關聯性，並在資料類型相符且資料行名稱類似時自動建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="585a0-220">Analysis Services will try to detect relationships and create them automatically if the data types match and the column names are similar.</span></span> <span data-ttu-id="585a0-221">如果它所建立的關聯性錯誤，您可以用滑鼠右鍵按一下聯結線，然後選取 [**修改連接**] 來編輯資料行對應，也可以用滑鼠右鍵按一下聯結線，然後選取 [**刪除**] 來完全移除關聯性。</span><span class="sxs-lookup"><span data-stu-id="585a0-221">If the relationships that it creates are wrong, you can right-click the join line and select **Modify Connections** to edit the column mapping, or you can right-click the join line and select **Delete** to remove the relationship completely.</span></span> <span data-ttu-id="585a0-222">在此案例中，因為資料表已經在資料來源檢視中聯結，所以這些關聯性會自動加入到 [設計] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="585a0-222">In this case, because the tables were already joined in the data source view, those relationships are automatically added to the design pane.</span></span>  
  
6.  <span data-ttu-id="585a0-223">將新的資料列加入方格中。</span><span class="sxs-lookup"><span data-stu-id="585a0-223">Add a new row to the grid.</span></span> <span data-ttu-id="585a0-224">針對 [**來源**]，選取 [vAssocSeqOrders]，然後針對 [**欄位**] 選取 [CustomerKey]。</span><span class="sxs-lookup"><span data-stu-id="585a0-224">For **Source**, select vAssocSeqOrders, and for **Field**, select CustomerKey.</span></span>  
  
7.  <span data-ttu-id="585a0-225">將新的資料列加入方格中。</span><span class="sxs-lookup"><span data-stu-id="585a0-225">Add a new row to the grid.</span></span> <span data-ttu-id="585a0-226">針對 [**來源**] 選取 [**預測函數**]，然後在 [**欄位**] 中選取 [ **PredictSequence**]。</span><span class="sxs-lookup"><span data-stu-id="585a0-226">For **Source**, select **Prediction Function**, and for **Field**, select **PredictSequence**.</span></span>  
  
8.  <span data-ttu-id="585a0-227">將 [vAssocSeqLineItems] 拖曳到 [**準則/引數**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="585a0-227">Drag vAssocSeqLineItems, into the **Criteria/Argument** box.</span></span> <span data-ttu-id="585a0-228">按一下 [**準則/引數**] 方塊的結尾，然後輸入下列引數： `2` 。</span><span class="sxs-lookup"><span data-stu-id="585a0-228">Click at the end of the **Criteria/Argument** box and then type the following arguments: `2`.</span></span>  
  
     <span data-ttu-id="585a0-229">[**準則/引數**] 方塊中的完整文字應該是：`[Sequence Clustering].[v Assoc Seq Line Items],2`</span><span class="sxs-lookup"><span data-stu-id="585a0-229">The complete text in the **Criteria/Argument** box should be: `[Sequence Clustering].[v Assoc Seq Line Items],2`</span></span>  
  
9. <span data-ttu-id="585a0-230">按一下 [**結果**] 按鈕，以查看每個客戶的預測。</span><span class="sxs-lookup"><span data-stu-id="585a0-230">Click the **Result** button to view the predictions for each customer.</span></span>  
  
 <span data-ttu-id="585a0-231">您已經完成時序群集模型上的教學課程。</span><span class="sxs-lookup"><span data-stu-id="585a0-231">You have completed the tutorial on sequence clustering models.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="585a0-232">後續步驟</span><span class="sxs-lookup"><span data-stu-id="585a0-232">Next Steps</span></span>  
 <span data-ttu-id="585a0-233">如果您已完成元資料採礦教學課程中的所有章節[&#40;Analysis Services 資料採礦&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)，下一個步驟可能是瞭解如何使用資料採礦延伸模組 (DMX) 語句來建立模型及產生預測。</span><span class="sxs-lookup"><span data-stu-id="585a0-233">If you have finished all the sections in the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md), the next step might be to learn to use Data Mining Extensions (DMX) statements to build models and generate predictions.</span></span> <span data-ttu-id="585a0-234">如需詳細資訊，請參閱[使用 DMX 建立和查詢資料採礦模型：教學課程 &#40;Analysis Services-資料採礦&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="585a0-234">For more information, see [Creating and Querying Data Mining Models with DMX: Tutorials &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).</span></span>  
  
 <span data-ttu-id="585a0-235">如果您很熟悉程式設計概念，您也可以使用分析管理物件 (AMO) 來以程式設計方式處理資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="585a0-235">If you are familiar with programming concepts, you can also use Analysis Management Objects (AMO) to programmatically work with data mining objects.</span></span> <span data-ttu-id="585a0-236">如需詳細資訊，請參閱 [AMO 資料採礦類別](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes)。</span><span class="sxs-lookup"><span data-stu-id="585a0-236">For more information, see [AMO Data Mining Classes](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="585a0-237">另請參閱</span><span class="sxs-lookup"><span data-stu-id="585a0-237">See Also</span></span>  
 <span data-ttu-id="585a0-238">[時序群集模型查詢範例](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="585a0-238">[Sequence Clustering Model Query Examples](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="585a0-239">時序叢集模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="585a0-239">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
