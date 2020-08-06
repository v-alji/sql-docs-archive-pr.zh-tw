---
title: " (中繼資料採礦教學課程建立時間序列預測) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fb22cffa-ac99-4d34-ac4a-9c93068e33e8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1175cdffd1512e0cb876b9565dd0727a9f094c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593245"
---
# <a name="creating-time-series-predictions-intermediate-data-mining-tutorial"></a><span data-ttu-id="cde13-102">建立時間序列預測 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="cde13-102">Creating Time Series Predictions (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="cde13-103">在本課之前的工作中，您已經建立一個時間序列模型並瀏覽結果。</span><span class="sxs-lookup"><span data-stu-id="cde13-103">In the previous tasks in this lesson, you created a time series model and explored the results.</span></span> <span data-ttu-id="cde13-104">根據預設，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 一定會建立一組五個的時間數列模型預測，並將預測值顯示為預測圖表的一部分。</span><span class="sxs-lookup"><span data-stu-id="cde13-104">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] always creates a set of five (5) predictions for a time series model and displays the predicted values as part of the forecasting chart.</span></span> <span data-ttu-id="cde13-105">但是，您也可以建立資料採礦延伸模組 (DMX) 預測查詢來建立預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-105">However, you can also create forecasts by building Data Mining Extensions (DMX) prediction queries.</span></span>  
  
 <span data-ttu-id="cde13-106">在此工作中，您將會建立預測查詢，此查詢會產生與您在檢視器中所見相同的預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-106">In this task, you will create a prediction query that generates the same predictions that you saw in the viewer.</span></span> <span data-ttu-id="cde13-107">此工作假設您已經完成「基本資料採礦教學課程」中的課程，而且很熟悉如何使用預測查詢產生器。</span><span class="sxs-lookup"><span data-stu-id="cde13-107">This task assumes that you have already completed the lessons in the Basic Data Mining Tutorial and are familiar with how to use Prediction Query Builder.</span></span> <span data-ttu-id="cde13-108">您現在將要學習如何建立時間序列模型特有的查詢。</span><span class="sxs-lookup"><span data-stu-id="cde13-108">You will now learn how to create queries specific to time series models.</span></span>  
  
## <a name="creating-time-series-predictions"></a><span data-ttu-id="cde13-109">建立時間序列預測</span><span class="sxs-lookup"><span data-stu-id="cde13-109">Creating Time Series Predictions</span></span>  
 <span data-ttu-id="cde13-110">一般來說，建立預測查詢的第一個步驟是選取採礦模型和輸入資料表。</span><span class="sxs-lookup"><span data-stu-id="cde13-110">Typically, the first step in creating a prediction query is to select a mining model and input table.</span></span> <span data-ttu-id="cde13-111">但是，時間序列模型不需要額外輸入，也能夠進行一般預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-111">However, a time series model does not require additional input for a regular prediction.</span></span> <span data-ttu-id="cde13-112">因此，當您做預測時，不需要指定新的資料來源，除非您要在模型中加入資料或是取代資料。</span><span class="sxs-lookup"><span data-stu-id="cde13-112">Therefore, you do not need to specify a new source of data when making predictions, unless you are adding data to the model or replacing the data.</span></span>  
  
 <span data-ttu-id="cde13-113">在這一課中，您必須指定預測步驟的數目。</span><span class="sxs-lookup"><span data-stu-id="cde13-113">For this lesson, you must specify the number of prediction steps.</span></span> <span data-ttu-id="cde13-114">您可以指定數列名稱，以取得產品和地區之特定組合的預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-114">You can specify the series name, to get a prediction for a particular combination of a product and a region.</span></span>  
  
#### <a name="to-select-a-model-and-input-table"></a><span data-ttu-id="cde13-115">若要選取模型和輸入資料表</span><span class="sxs-lookup"><span data-stu-id="cde13-115">To select a model and input table</span></span>  
  
1.  <span data-ttu-id="cde13-116">在資料採礦設計工具的 [**採礦模型預測**] 索引標籤上，按一下 [**採礦模型**] 方塊中的 [**選取模型**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-116">On the **Mining Model Prediction** tab of the Data Mining Designer, in the **Mining Model** box, click **Select Model**.</span></span>  
  
2.  <span data-ttu-id="cde13-117">在 [**選取採礦模型**] 對話方塊中，展開 [預測] 結構，從清單中選取**預測**模型，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="cde13-117">In the **Select Mining Model** dialog box, expand the Forecasting structure, select the **Forecasting** model from the list, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="cde13-118">忽略 (s) 方塊中的 [**選取輸入資料表**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-118">Ignore the **Select Input Table(s)** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde13-119">如果是時間序列模型，您不需要指定個別輸入，除非您要執行交叉預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-119">For a time series model, you do not need to specify a separate input unless you are doing cross-prediction.</span></span>  
  
4.  <span data-ttu-id="cde13-120">在 [**源**資料行] 中，于 [**採礦模型預測**] 索引標籤上的方格中，按一下第一個空白資料列中的資料格，然後選取 [預測] [**採礦模型**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-120">In the **Source** column, in the grid on the **Mining Model Prediction** tab, click the cell in the first empty row, and then select **Forecasting mining model**.</span></span>  
  
5.  <span data-ttu-id="cde13-121">在 [**欄位**] 資料行中，選取 [**模型區域**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-121">In the **Field** column, select **Model Region**.</span></span>  
  
     <span data-ttu-id="cde13-122">這個動作會將數列識別碼加入到預測查詢中，以表示此預測會套用到哪一個模型和地區組合。</span><span class="sxs-lookup"><span data-stu-id="cde13-122">This action adds the series identifier to the prediction query to indicate the combination of model and region to which the prediction applies.</span></span>  
  
6.  <span data-ttu-id="cde13-123">按一下 [**來源**] 資料行中的下一個空白資料列，然後選取 [**預測函數**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-123">Click the next empty row in the **Source** column, and then select **Prediction Function**.</span></span>  
  
7.  <span data-ttu-id="cde13-124">在 [**欄位**] 資料行中，選取 [ **PredictTimeSeries**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-124">In the **Field** column, select **PredictTimeSeries**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde13-125">您也可以搭配時間序列模型使用 `Predict` 函數。</span><span class="sxs-lookup"><span data-stu-id="cde13-125">You can also use the `Predict` function with time series models.</span></span> <span data-ttu-id="cde13-126">但是根據預設，Predict 函數只會針對每一個數列各建立一項預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-126">However, by default, the Predict function creates only one prediction for each series.</span></span> <span data-ttu-id="cde13-127">因此，若要指定多個預測步驟，您必須使用**PredictTimeSeries**函數。</span><span class="sxs-lookup"><span data-stu-id="cde13-127">Therefore, to specify multiple prediction steps, you must use the **PredictTimeSeries** function.</span></span>  
  
8.  <span data-ttu-id="cde13-128">在 [**採礦模型**] 窗格中，選取 [採礦模型] 資料行 [**金額]。**</span><span class="sxs-lookup"><span data-stu-id="cde13-128">In the **Mining Model** pane, select the mining model column, **Amount.**</span></span> <span data-ttu-id="cde13-129">將 [數量] 拖曳至您稍早新增的**PredictTimeSeries**函式的 [**準則/引數**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="cde13-129">Drag Amount to the **Criteria/Arguments** box for the **PredictTimeSeries** function that you added earlier.</span></span>  
  
9. <span data-ttu-id="cde13-130">按一下 [**準則/引數**] 方塊，然後在功能變數名稱後面輸入逗號，後面加上**5**。</span><span class="sxs-lookup"><span data-stu-id="cde13-130">Click the **Criteria/Arguments** box, and type a comma, followed by **5**, after the field name.</span></span>  
  
     <span data-ttu-id="cde13-131">[**準則/引數**] 方塊中的文字現在應該會顯示下列內容：</span><span class="sxs-lookup"><span data-stu-id="cde13-131">The text in the **Criteria/Arguments** box should now display the following:</span></span>  
  
     `[Forecasting].[Amount],5`  
  
10. <span data-ttu-id="cde13-132">在 [**別名**] 資料行中，輸入 `PredictAmount` 。</span><span class="sxs-lookup"><span data-stu-id="cde13-132">In the **Alias** column, type `PredictAmount`.</span></span>  
  
11. <span data-ttu-id="cde13-133">按一下 [**來源**] 資料行中的下一個空白資料列，然後再次選取 [**預測函數**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-133">Click the next empty row in the **Source** column, and then select **Prediction Function** again.</span></span>  
  
12. <span data-ttu-id="cde13-134">在 [**欄位**] 資料行中，選取 [ **PredictTimeSeries**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-134">In the **Field** column, select **PredictTimeSeries**.</span></span>  
  
13. <span data-ttu-id="cde13-135">在 [**採礦模型**] 窗格中，選取資料行數量，然後將它拖曳到第二個**PredictTimeSeries**函數的 [**準則/引數**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="cde13-135">In the **Mining Model** pane, select the column Quantity, and then drag it into the **Criteria/Arguments** box for the second **PredictTimeSeries** function.</span></span>  
  
14. <span data-ttu-id="cde13-136">按一下 [**準則/引數**] 方塊，然後在功能變數名稱後面輸入逗號，後面加上**5**。</span><span class="sxs-lookup"><span data-stu-id="cde13-136">Click the **Criteria/Arguments** box, and type a comma, followed by **5**, after the field name.</span></span>  
  
     <span data-ttu-id="cde13-137">[**準則/引數**] 方塊中的文字現在應該會顯示下列內容：</span><span class="sxs-lookup"><span data-stu-id="cde13-137">The text in the **Criteria/Arguments** box should now display the following:</span></span>  
  
     `[Forecasting].[ Quantity],5`  
  
15. <span data-ttu-id="cde13-138">在 [**別名**] 資料行中，輸入 `PredictQuantity` 。</span><span class="sxs-lookup"><span data-stu-id="cde13-138">In the **Alias** column, type `PredictQuantity`.</span></span>  
  
16. <span data-ttu-id="cde13-139">按一下 [**切換到查詢結果檢視**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-139">Click **Switch to query result view**.</span></span>  
  
     <span data-ttu-id="cde13-140">查詢的結果會以表格格式顯示。</span><span class="sxs-lookup"><span data-stu-id="cde13-140">The results of the query are displayed in tabular format.</span></span>  
  
 <span data-ttu-id="cde13-141">請記得，您已經在查詢產生器中建立三種不同類型的結果，其中一種是使用資料行內的值，另外兩種會從預測函數取得預測值。</span><span class="sxs-lookup"><span data-stu-id="cde13-141">Remember that you created three different types of results in the query builder, one that uses values from a column, and two that get predicted values from a prediction function.</span></span> <span data-ttu-id="cde13-142">因此，查詢的結果包含三個不同的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde13-142">Therefore, the results of the query contain three separate columns.</span></span> <span data-ttu-id="cde13-143">第一個資料行包含產品和地區組合的清單。</span><span class="sxs-lookup"><span data-stu-id="cde13-143">The first column contains the list of product and region combinations.</span></span> <span data-ttu-id="cde13-144">第二和第三個資料行各包含預測結果的巢狀資料表，</span><span class="sxs-lookup"><span data-stu-id="cde13-144">The second and third columns each contain a nested table of prediction results.</span></span> <span data-ttu-id="cde13-145">每一個巢狀資料表都包含時間步驟和預測值，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="cde13-145">Each nested table contains the time step and predicted values, such as the following table:</span></span>  
  
 <span data-ttu-id="cde13-146">範例結果 (金額截斷為兩個小數位數)：</span><span class="sxs-lookup"><span data-stu-id="cde13-146">Example results (amounts are truncated to two decimal places):</span></span>  
  
 <span data-ttu-id="cde13-147">**M200 歐洲 PredictAmount**</span><span class="sxs-lookup"><span data-stu-id="cde13-147">**M200 Europe PredictAmount**</span></span>  
  
|<span data-ttu-id="cde13-148">$TIME</span><span class="sxs-lookup"><span data-stu-id="cde13-148">$TIME</span></span>|<span data-ttu-id="cde13-149">金額</span><span class="sxs-lookup"><span data-stu-id="cde13-149">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="cde13-150">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-150">7/25/2008</span></span>|<span data-ttu-id="cde13-151">99978.00</span><span class="sxs-lookup"><span data-stu-id="cde13-151">99978.00</span></span>|  
|<span data-ttu-id="cde13-152">2008 年 8 月 25 日</span><span class="sxs-lookup"><span data-stu-id="cde13-152">8/25/2008</span></span>|<span data-ttu-id="cde13-153">145575.07</span><span class="sxs-lookup"><span data-stu-id="cde13-153">145575.07</span></span>|  
|<span data-ttu-id="cde13-154">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-154">9/25/2008</span></span>|<span data-ttu-id="cde13-155">116835.19</span><span class="sxs-lookup"><span data-stu-id="cde13-155">116835.19</span></span>|  
|<span data-ttu-id="cde13-156">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-156">10/25/2008</span></span>|<span data-ttu-id="cde13-157">116537.38</span><span class="sxs-lookup"><span data-stu-id="cde13-157">116537.38</span></span>|  
|<span data-ttu-id="cde13-158">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-158">11/25/2008</span></span>|<span data-ttu-id="cde13-159">107760.55</span><span class="sxs-lookup"><span data-stu-id="cde13-159">107760.55</span></span>|  
  
 <span data-ttu-id="cde13-160">**M200 歐洲 PredictQuantity**</span><span class="sxs-lookup"><span data-stu-id="cde13-160">**M200 Europe PredictQuantity**</span></span>  
  
|<span data-ttu-id="cde13-161">$TIME</span><span class="sxs-lookup"><span data-stu-id="cde13-161">$TIME</span></span>|<span data-ttu-id="cde13-162">數量</span><span class="sxs-lookup"><span data-stu-id="cde13-162">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="cde13-163">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-163">7/25/2008</span></span>|<span data-ttu-id="cde13-164">52</span><span class="sxs-lookup"><span data-stu-id="cde13-164">52</span></span>|  
|<span data-ttu-id="cde13-165">2008 年 8 月 25 日</span><span class="sxs-lookup"><span data-stu-id="cde13-165">8/25/2008</span></span>|<span data-ttu-id="cde13-166">67</span><span class="sxs-lookup"><span data-stu-id="cde13-166">67</span></span>|  
|<span data-ttu-id="cde13-167">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-167">9/25/2008</span></span>|<span data-ttu-id="cde13-168">58</span><span class="sxs-lookup"><span data-stu-id="cde13-168">58</span></span>|  
|<span data-ttu-id="cde13-169">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-169">10/25/2008</span></span>|<span data-ttu-id="cde13-170">57</span><span class="sxs-lookup"><span data-stu-id="cde13-170">57</span></span>|  
|<span data-ttu-id="cde13-171">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-171">11/25/2008</span></span>|<span data-ttu-id="cde13-172">54</span><span class="sxs-lookup"><span data-stu-id="cde13-172">54</span></span>|  
  
 <span data-ttu-id="cde13-173">**M200 北美洲-PredictAmount**</span><span class="sxs-lookup"><span data-stu-id="cde13-173">**M200 North America - PredictAmount**</span></span>  
  
|<span data-ttu-id="cde13-174">$TIME</span><span class="sxs-lookup"><span data-stu-id="cde13-174">$TIME</span></span>|<span data-ttu-id="cde13-175">金額</span><span class="sxs-lookup"><span data-stu-id="cde13-175">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="cde13-176">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-176">7/25/2008</span></span>|<span data-ttu-id="cde13-177">348533.93</span><span class="sxs-lookup"><span data-stu-id="cde13-177">348533.93</span></span>|  
|<span data-ttu-id="cde13-178">2008 年 8 月 25 日</span><span class="sxs-lookup"><span data-stu-id="cde13-178">8/25/2008</span></span>|<span data-ttu-id="cde13-179">340097.98</span><span class="sxs-lookup"><span data-stu-id="cde13-179">340097.98</span></span>|  
|<span data-ttu-id="cde13-180">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-180">9/25/2008</span></span>|<span data-ttu-id="cde13-181">257986.19</span><span class="sxs-lookup"><span data-stu-id="cde13-181">257986.19</span></span>|  
|<span data-ttu-id="cde13-182">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-182">10/25/2008</span></span>|<span data-ttu-id="cde13-183">374658.24</span><span class="sxs-lookup"><span data-stu-id="cde13-183">374658.24</span></span>|  
|<span data-ttu-id="cde13-184">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-184">11/25/2008</span></span>|<span data-ttu-id="cde13-185">379241.44</span><span class="sxs-lookup"><span data-stu-id="cde13-185">379241.44</span></span>|  
  
 <span data-ttu-id="cde13-186">**M200 北美洲-PredictQuantity**</span><span class="sxs-lookup"><span data-stu-id="cde13-186">**M200 North America - PredictQuantity**</span></span>  
  
|<span data-ttu-id="cde13-187">$TIME</span><span class="sxs-lookup"><span data-stu-id="cde13-187">$TIME</span></span>|<span data-ttu-id="cde13-188">數量</span><span class="sxs-lookup"><span data-stu-id="cde13-188">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="cde13-189">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-189">7/25/2008</span></span>|<span data-ttu-id="cde13-190">272</span><span class="sxs-lookup"><span data-stu-id="cde13-190">272</span></span>|  
|<span data-ttu-id="cde13-191">2008 年 8 月 25 日</span><span class="sxs-lookup"><span data-stu-id="cde13-191">8/25/2008</span></span>|<span data-ttu-id="cde13-192">152</span><span class="sxs-lookup"><span data-stu-id="cde13-192">152</span></span>|  
|<span data-ttu-id="cde13-193">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-193">9/25/2008</span></span>|<span data-ttu-id="cde13-194">250</span><span class="sxs-lookup"><span data-stu-id="cde13-194">250</span></span>|  
|<span data-ttu-id="cde13-195">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-195">10/25/2008</span></span>|<span data-ttu-id="cde13-196">181</span><span class="sxs-lookup"><span data-stu-id="cde13-196">181</span></span>|  
|<span data-ttu-id="cde13-197">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="cde13-197">11/25/2008</span></span>|<span data-ttu-id="cde13-198">290</span><span class="sxs-lookup"><span data-stu-id="cde13-198">290</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="cde13-199">範例資料庫中使用的日期已在此版本中變更。</span><span class="sxs-lookup"><span data-stu-id="cde13-199">The dates that are used in the sample database have changed for this release.</span></span> <span data-ttu-id="cde13-200">如果您使用的是舊版的範例資料，可能會看到不同的結果。</span><span class="sxs-lookup"><span data-stu-id="cde13-200">If you are using an earlier version of the sample data, you might see different results.</span></span>  
  
## <a name="saving-the-prediction-results"></a><span data-ttu-id="cde13-201">儲存預測結果</span><span class="sxs-lookup"><span data-stu-id="cde13-201">Saving the Prediction Results</span></span>  
 <span data-ttu-id="cde13-202">您有數個選項可以使用此預測結果。</span><span class="sxs-lookup"><span data-stu-id="cde13-202">You have several different options for using the prediction results.</span></span> <span data-ttu-id="cde13-203">可以將結果扁平化，並從 [結果] 檢視複製資料，然後貼到 Excel 工作表或其他檔案中。</span><span class="sxs-lookup"><span data-stu-id="cde13-203">You can flatten the results, copy the data from the Results view, and paste it into an Excel worksheet or other file.</span></span>  
  
 <span data-ttu-id="cde13-204">為了簡化儲存結果的程序，資料採礦設計師也提供將資料儲存至資料來源檢視的能力。</span><span class="sxs-lookup"><span data-stu-id="cde13-204">To simplify the process of saving results, Data Mining Designer also provides the ability to save the data to a data source view.</span></span> <span data-ttu-id="cde13-205">將結果儲存至資料來源檢視的功能只能在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中使用。</span><span class="sxs-lookup"><span data-stu-id="cde13-205">The functionality for saving results to a data source view is available only in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="cde13-206">結果只能使用扁平化的格式儲存。</span><span class="sxs-lookup"><span data-stu-id="cde13-206">The results can only be stored in a flattened format.</span></span>  
  
#### <a name="to-flatten-the-results-in-the-results-pane"></a><span data-ttu-id="cde13-207">若要在結果窗格中扁平化結果</span><span class="sxs-lookup"><span data-stu-id="cde13-207">To flatten the results in the Results pane</span></span>  
  
1.  <span data-ttu-id="cde13-208">在預測查詢產生器中，按一下 [**切換到查詢設計視圖**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-208">In the Prediction Query Builder, click **Switch to query design view**.</span></span>  
  
     <span data-ttu-id="cde13-209">此檢視會變更，好讓您手動編輯 DMX 查詢文字。</span><span class="sxs-lookup"><span data-stu-id="cde13-209">The view changes to allow manual editing of the DMX query text.</span></span>  
  
2.  <span data-ttu-id="cde13-210">在 `FLATTENED` 關鍵字之後輸入 `SELECT` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cde13-210">Type the `FLATTENED` keyword after the `SELECT` keyword.</span></span> <span data-ttu-id="cde13-211">完整查詢文字應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="cde13-211">The complete query text should be as follows:</span></span>  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    ```  
  
3.  <span data-ttu-id="cde13-212">或者，您可以輸入一子句以限制結果，例如以下範例：</span><span class="sxs-lookup"><span data-stu-id="cde13-212">Optionally, you can type a clause to restrict the results, such as the following example:</span></span>  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    WHERE [Forecasting].[Model Region] = 'M200 North America'   
    OR [Forecasting].[Model Region] = 'M200 Europe'  
  
    ```  
  
4.  <span data-ttu-id="cde13-213">按一下 [**切換到查詢結果檢視**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-213">Click **Switch to query result view**.</span></span>  
  
#### <a name="to-export-prediction-query-results"></a><span data-ttu-id="cde13-214">若要匯出預測查詢結果</span><span class="sxs-lookup"><span data-stu-id="cde13-214">To export prediction query results</span></span>  
  
1.  <span data-ttu-id="cde13-215">按一下 [**儲存查詢結果**]。</span><span class="sxs-lookup"><span data-stu-id="cde13-215">Click **Save query results**.</span></span>  
  
2.  <span data-ttu-id="cde13-216">在 [**儲存資料採礦查詢結果**] 對話方塊中，針對 [**資料來源**] 選取 [] [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cde13-216">In the **Save Data Mining Query Result** dialog box, for **Data Source**, select [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span> <span data-ttu-id="cde13-217">如果您想要將資料儲存到不同的關聯式資料庫，您也可以建立資料來源。</span><span class="sxs-lookup"><span data-stu-id="cde13-217">You can also create a data source if you want to save the data to a different relational database.</span></span>  
  
3.  <span data-ttu-id="cde13-218">在 [**資料表名稱**] 資料行中，輸入新的臨時表名稱，例如**測試預測**。</span><span class="sxs-lookup"><span data-stu-id="cde13-218">In the **Table Name** column, type a new temporary table name, such as **Test Predictions**.</span></span>  
  
4.  <span data-ttu-id="cde13-219">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="cde13-219">Click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde13-220">若要檢視您所建立的資料表，請建立與您儲存資料之執行個體的資料庫引擎之間的連接，並建立查詢。</span><span class="sxs-lookup"><span data-stu-id="cde13-220">To view the table that you created, create a connection to the database engine of the instance where you saved the data, and create a query.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="cde13-221">結論</span><span class="sxs-lookup"><span data-stu-id="cde13-221">Conclusion</span></span>  
 <span data-ttu-id="cde13-222">您已經學會如何建立基本的時間序列模型，解譯預測，以及建立預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-222">You have learned how to build a basic time series model, interpret the forecasts, and create predictions.</span></span>  
  
 <span data-ttu-id="cde13-223">本教學課程中的剩餘工作是選擇性的，描述進階時間序列預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-223">The remaining tasks in this tutorial are optional, and describe advanced time series predictions.</span></span> <span data-ttu-id="cde13-224">如果您決定要繼續，您將學習如何將新資料加入至模型，以及在擴充數列上建立預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-224">If you decide to go on, you will learn how to add new data to your model and create predictions on the extended series.</span></span> <span data-ttu-id="cde13-225">您也將會學習如何使用模型中的趨勢，但以新的資料數列取代資料，藉此執行交叉預測。</span><span class="sxs-lookup"><span data-stu-id="cde13-225">You will also learn how to perform cross-prediction, by using the trend in the model but replacing the data with a new series of data.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="cde13-226">下一課</span><span class="sxs-lookup"><span data-stu-id="cde13-226">Next Lesson</span></span>  
 [<span data-ttu-id="cde13-227">&#40;中繼資料採礦教學課程的先進時間序列預測&#41;</span><span class="sxs-lookup"><span data-stu-id="cde13-227">Advanced Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="cde13-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cde13-228">See Also</span></span>  
 [<span data-ttu-id="cde13-229">時間序列模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="cde13-229">Time Series Model Query Examples</span></span>](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
