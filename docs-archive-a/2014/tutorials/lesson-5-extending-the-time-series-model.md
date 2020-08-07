---
title: 第5課：擴充時間序列模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7aad4946-c903-4e25-88b9-b087c20cb67d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2716e985897f8115d189d9410b7cdb13fb1af291
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593720"
---
# <a name="lesson-5-extending-the-time-series-model"></a><span data-ttu-id="097d8-102">第 5 課：擴充時間序列模型</span><span class="sxs-lookup"><span data-stu-id="097d8-102">Lesson 5: Extending the Time Series Model</span></span>
  <span data-ttu-id="097d8-103">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise 中，您可以將新的資料加入至時間序列模型，並自動將新的資料併入此模型中。</span><span class="sxs-lookup"><span data-stu-id="097d8-103">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise, you can add new data to a time series model and automatically incorporate the new data into the model.</span></span> <span data-ttu-id="097d8-104">您可以使用下列兩種方式的其中一種，將新的資料加入至時間序列採礦模型：</span><span class="sxs-lookup"><span data-stu-id="097d8-104">You add new data to a time series mining model in one of two ways:</span></span>  
  
-   <span data-ttu-id="097d8-105">使用 PREDICTION JOIN 將外部來源中的資料聯結至定型資料。</span><span class="sxs-lookup"><span data-stu-id="097d8-105">Use a PREDICTION JOIN to join data in an external source to the training data.</span></span>  
  
-   <span data-ttu-id="097d8-106">使用單一預測查詢，一次為資料提供一個配量。</span><span class="sxs-lookup"><span data-stu-id="097d8-106">Use a singleton prediction query to provide data one slice at a time.</span></span>  
  
 <span data-ttu-id="097d8-107">例如，假設您在幾個月以前已經針對現有的銷售資料定型採礦模型。</span><span class="sxs-lookup"><span data-stu-id="097d8-107">For example, assume that you trained the mining model on existing sales data some months ago.</span></span> <span data-ttu-id="097d8-108">當您取得新的銷售時，您可能會想要更新銷售預測來併入新的資料。</span><span class="sxs-lookup"><span data-stu-id="097d8-108">When you get new sales, you might want to update the sales predictions to incorporate the new data.</span></span> <span data-ttu-id="097d8-109">您可以在一個步驟中完成這項處理，其方式是提供新的銷售數字當做輸入資料，然後根據複合資料集來產生新的預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-109">You can do this in one step, by supplying the new sales figures as input data and generating new predictions based on the composite data set.</span></span>  
  
## <a name="making-predictions-with-extend_model_cases"></a><span data-ttu-id="097d8-110">使用 EXTEND_MODEL_CASES 做出預測</span><span class="sxs-lookup"><span data-stu-id="097d8-110">Making Predictions with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="097d8-111">下列是使用 EXTEND_MODEL_CASES 之時間序列預測的一般範例。</span><span class="sxs-lookup"><span data-stu-id="097d8-111">The following are generic examples of a time series prediction using EXTEND_MODEL_CASES.</span></span> <span data-ttu-id="097d8-112">第一個範例可讓您從原始模型的最後一個時間步驟開始指定預測數目：</span><span class="sxs-lookup"><span data-stu-id="097d8-112">The first example enables you to specify the number of predictions starting from the last time step of the original model:</span></span>  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>]  
```  
  
 <span data-ttu-id="097d8-113">第二個範例可讓您指定預測應該開始及應該結束的時間步驟。</span><span class="sxs-lookup"><span data-stu-id="097d8-113">The second example enables you to specify the time step where predictions should start, and where they should end.</span></span> <span data-ttu-id="097d8-114">當您要擴充模型案例時，這個選項非常重要，因為根據預設，用於預測查詢的時間步驟一定會從原始數列的結尾開始。</span><span class="sxs-lookup"><span data-stu-id="097d8-114">This option is important when you extend the model cases because, by default, the time steps used for prediction queries always start at the end of the original series.</span></span>  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n-start, n-end, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>}  
```  
  
 <span data-ttu-id="097d8-115">在本教學課程中，您將會建立這兩種查詢。</span><span class="sxs-lookup"><span data-stu-id="097d8-115">In this tutorial, you will create both kinds of queries.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query-on-a-time-series-model"></a><span data-ttu-id="097d8-116">若要針對時間序列模型建立單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="097d8-116">To create a singleton prediction query on a time series model</span></span>  
  
1.  <span data-ttu-id="097d8-117">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="097d8-117">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="097d8-118">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="097d8-118">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="097d8-119">將單一陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="097d8-119">Copy the generic example of the singleton statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="097d8-120">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="097d8-120">Replace the following:</span></span>  
  
    ```  
    SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
    ```  
  
     <span data-ttu-id="097d8-121">成為：</span><span class="sxs-lookup"><span data-stu-id="097d8-121">with:</span></span>  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    ```  
  
     <span data-ttu-id="097d8-122">第一行會從可識別此數列的模型中擷取值。</span><span class="sxs-lookup"><span data-stu-id="097d8-122">The first line retrieves a value from the model that identifies the series.</span></span>  
  
     <span data-ttu-id="097d8-123">第二行包含預測函數，該函數會取得 Quantity 的六項預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-123">The second line contains the prediction function, which gets 6 predictions for Quantity.</span></span> <span data-ttu-id="097d8-124">別名 `PredictQty` 會指派給預測結果資料行，讓您更輕鬆地了解結果。</span><span class="sxs-lookup"><span data-stu-id="097d8-124">An alias, `PredictQty`, is assigned to the prediction result column to make it easier to understand the results.</span></span>  
  
4.  <span data-ttu-id="097d8-125">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="097d8-125">Replace the following:</span></span>  
  
    ```  
    FROM <mining model>  
    ```  
  
     <span data-ttu-id="097d8-126">成為：</span><span class="sxs-lookup"><span data-stu-id="097d8-126">with:</span></span>  
  
    ```  
    FROM [Forecasting_MIXED]  
    ```  
  
5.  <span data-ttu-id="097d8-127">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="097d8-127">Replace the following:</span></span>  
  
    ```  
    PREDICTION JOIN <source query>  
    ```  
  
     <span data-ttu-id="097d8-128">成為：</span><span class="sxs-lookup"><span data-stu-id="097d8-128">with:</span></span>  
  
    ```  
    NATURAL PREDICTION JOIN   
    (  
       SELECT 1 AS [Reporting Date],  
       '10' AS [Quantity],  
       'M200 Europe' AS [Model Region]  
       UNION SELECT  
       2 AS [Reporting Date],  
       15 AS [Quantity]),  
       'M200 Europe' AS [Model Region]  
    ) AS t  
    ```  
  
6.  <span data-ttu-id="097d8-129">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="097d8-129">Replace the following:</span></span>  
  
    ```  
    [WHERE <criteria>]  
    ```  
  
     <span data-ttu-id="097d8-130">成為：</span><span class="sxs-lookup"><span data-stu-id="097d8-130">with:</span></span>  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     <span data-ttu-id="097d8-131">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="097d8-131">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    FROM  
       [Forecasting_MIXED]  
    NATURAL PREDICTION JOIN   
       SELECT 1 AS [ReportingDate],  
      '10' AS [Quantity],  
      'M200 Europe' AS [ModelRegion]  
    UNION SELECT  
      2 AS [ReportingDate],  
      15 AS [Quantity]),  
      'M200 Europe' AS [ModelRegion]  
    ) AS t  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
7.  <span data-ttu-id="097d8-132">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="097d8-132">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="097d8-133">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Singleton_TimeSeries_Query.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="097d8-133">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Singleton_TimeSeries_Query.dmx`.</span></span>  
  
9. <span data-ttu-id="097d8-134">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="097d8-134">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="097d8-135">此查詢會傳回 M200 自行車在歐洲和太平洋地區銷售數量的預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-135">The query returns predictions of sales quantity for the M200 bicycle in the Europe and Pacific regions.</span></span>  
  
## <a name="understanding-prediction-start-with-extend_model_cases"></a><span data-ttu-id="097d8-136">從 EXTEND_MODEL_CASES 開始了解預測</span><span class="sxs-lookup"><span data-stu-id="097d8-136">Understanding Prediction Start with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="097d8-137">現在您已經根據原始模型建立預測，而且有了新的資料之後，您就可以比較結果來查看更新銷售資料會如何影響預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-137">Now that you have created predictions based on the original model, and with new data, you can compare the results to see how updating the sales data affects the predictions.</span></span> <span data-ttu-id="097d8-138">在您這樣做之前，請先檢閱您剛才建立的程式碼，並注意以下事項：</span><span class="sxs-lookup"><span data-stu-id="097d8-138">Before you do so, review the code that you just created, and notice the following:</span></span>  
  
-   <span data-ttu-id="097d8-139">您只為歐洲地區提供新的資料。</span><span class="sxs-lookup"><span data-stu-id="097d8-139">You supplied new data for only the Europe region.</span></span>  
  
-   <span data-ttu-id="097d8-140">您只提供兩個月的新資料。</span><span class="sxs-lookup"><span data-stu-id="097d8-140">You supplied only two months' worth of new data.</span></span>  
  
 <span data-ttu-id="097d8-141">下表顯示為 M200 Europe 所提供的新值要如何影響預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-141">The following table shows how the new values supplied for M200 Europe affect predictions.</span></span> <span data-ttu-id="097d8-142">您並未提供 M200 產品在太平洋地區的任何新資料，但是會呈現這個數列進行比較：</span><span class="sxs-lookup"><span data-stu-id="097d8-142">You did not provide any new data for the M200 product in the Pacific region, but this series is presented for comparison:</span></span>  
  
 <span data-ttu-id="097d8-143">**產品和地區： M200 歐洲**</span><span class="sxs-lookup"><span data-stu-id="097d8-143">**Product and Region: M200 Europe**</span></span>  
  
|||||  
|-|-|-|-|  
|||<span data-ttu-id="097d8-144">現有的模型 (`PredictTimeSeries`)</span><span class="sxs-lookup"><span data-stu-id="097d8-144">Existing model (`PredictTimeSeries`)</span></span>|<span data-ttu-id="097d8-145">具有更新銷售資料的模型 (具有 `PredictTimeSeries` 的 `EXTEND_MODEL_CASES`)</span><span class="sxs-lookup"><span data-stu-id="097d8-145">Model with updated sales data (`PredictTimeSeries` with `EXTEND_MODEL_CASES`)</span></span>|  
|<span data-ttu-id="097d8-146">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-146">M200 Europe</span></span>|<span data-ttu-id="097d8-147">上午 7/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-147">7/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-148">77</span><span class="sxs-lookup"><span data-stu-id="097d8-148">77</span></span>|<span data-ttu-id="097d8-149">10</span><span class="sxs-lookup"><span data-stu-id="097d8-149">10</span></span>|  
|<span data-ttu-id="097d8-150">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-150">M200 Europe</span></span>|<span data-ttu-id="097d8-151">上午 8/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-151">8/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-152">64</span><span class="sxs-lookup"><span data-stu-id="097d8-152">64</span></span>|<span data-ttu-id="097d8-153">15</span><span class="sxs-lookup"><span data-stu-id="097d8-153">15</span></span>|  
|<span data-ttu-id="097d8-154">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-154">M200 Europe</span></span>|<span data-ttu-id="097d8-155">上午 9/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-155">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-156">59</span><span class="sxs-lookup"><span data-stu-id="097d8-156">59</span></span>|<span data-ttu-id="097d8-157">72</span><span class="sxs-lookup"><span data-stu-id="097d8-157">72</span></span>|  
|<span data-ttu-id="097d8-158">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-158">M200 Europe</span></span>|<span data-ttu-id="097d8-159">上午 10/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-159">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-160">56</span><span class="sxs-lookup"><span data-stu-id="097d8-160">56</span></span>|<span data-ttu-id="097d8-161">69</span><span class="sxs-lookup"><span data-stu-id="097d8-161">69</span></span>|  
|<span data-ttu-id="097d8-162">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-162">M200 Europe</span></span>|<span data-ttu-id="097d8-163">上午 11/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-163">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-164">56</span><span class="sxs-lookup"><span data-stu-id="097d8-164">56</span></span>|<span data-ttu-id="097d8-165">68</span><span class="sxs-lookup"><span data-stu-id="097d8-165">68</span></span>|  
|<span data-ttu-id="097d8-166">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-166">M200 Europe</span></span>|<span data-ttu-id="097d8-167">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="097d8-167">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-168">74</span><span class="sxs-lookup"><span data-stu-id="097d8-168">74</span></span>|<span data-ttu-id="097d8-169">89</span><span class="sxs-lookup"><span data-stu-id="097d8-169">89</span></span>|  
  
 <span data-ttu-id="097d8-170">**產品和地區： M200 太平洋**</span><span class="sxs-lookup"><span data-stu-id="097d8-170">**Product and Region: M200 Pacific**</span></span>  
  
|||||  
|-|-|-|-|  
|||<span data-ttu-id="097d8-171">現有的模型 (`PredictTimeSeries`)</span><span class="sxs-lookup"><span data-stu-id="097d8-171">Existing model (`PredictTimeSeries`)</span></span>|<span data-ttu-id="097d8-172">具有更新銷售資料的模型 (具有 `PredictTimeSeries` 的 `EXTEND_MODEL_CASES`)</span><span class="sxs-lookup"><span data-stu-id="097d8-172">Model with updated sales data (`PredictTimeSeries` with `EXTEND_MODEL_CASES`)</span></span>|  
|<span data-ttu-id="097d8-173">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="097d8-173">M200 Pacific</span></span>|<span data-ttu-id="097d8-174">上午 7/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-174">7/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-175">41</span><span class="sxs-lookup"><span data-stu-id="097d8-175">41</span></span>|<span data-ttu-id="097d8-176">41</span><span class="sxs-lookup"><span data-stu-id="097d8-176">41</span></span>|  
|<span data-ttu-id="097d8-177">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="097d8-177">M200 Pacific</span></span>|<span data-ttu-id="097d8-178">上午 8/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-178">8/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-179">44</span><span class="sxs-lookup"><span data-stu-id="097d8-179">44</span></span>|<span data-ttu-id="097d8-180">44</span><span class="sxs-lookup"><span data-stu-id="097d8-180">44</span></span>|  
|<span data-ttu-id="097d8-181">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="097d8-181">M200 Pacific</span></span>|<span data-ttu-id="097d8-182">上午 9/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-182">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-183">38</span><span class="sxs-lookup"><span data-stu-id="097d8-183">38</span></span>|<span data-ttu-id="097d8-184">38</span><span class="sxs-lookup"><span data-stu-id="097d8-184">38</span></span>|  
|<span data-ttu-id="097d8-185">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="097d8-185">M200 Pacific</span></span>|<span data-ttu-id="097d8-186">上午 10/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-186">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-187">41</span><span class="sxs-lookup"><span data-stu-id="097d8-187">41</span></span>|<span data-ttu-id="097d8-188">41</span><span class="sxs-lookup"><span data-stu-id="097d8-188">41</span></span>|  
|<span data-ttu-id="097d8-189">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="097d8-189">M200 Pacific</span></span>|<span data-ttu-id="097d8-190">上午 11/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-190">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-191">36</span><span class="sxs-lookup"><span data-stu-id="097d8-191">36</span></span>|<span data-ttu-id="097d8-192">36</span><span class="sxs-lookup"><span data-stu-id="097d8-192">36</span></span>|  
|<span data-ttu-id="097d8-193">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="097d8-193">M200 Pacific</span></span>|<span data-ttu-id="097d8-194">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="097d8-194">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-195">39</span><span class="sxs-lookup"><span data-stu-id="097d8-195">39</span></span>|<span data-ttu-id="097d8-196">39</span><span class="sxs-lookup"><span data-stu-id="097d8-196">39</span></span>|  
  
 <span data-ttu-id="097d8-197">您可以從這些結果看到兩件事：</span><span class="sxs-lookup"><span data-stu-id="097d8-197">From these results, you can see two things:</span></span>  
  
-   <span data-ttu-id="097d8-198">M200 Europe 數列的前兩個預測與您所提供的新資料完全相同。</span><span class="sxs-lookup"><span data-stu-id="097d8-198">The first two predictions for the M200 Europe series are exactly the same as the new data you supplied.</span></span> <span data-ttu-id="097d8-199">根據設計，Analysis Services 會傳回實際的新資料點，而不是做出預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-199">By design, Analysis Services returns the actual new data points instead of making a prediction.</span></span> <span data-ttu-id="097d8-200">這是因為當您要擴充模型案例時，用於預測查詢的時間步驟一定會從原始數列的結尾開始。</span><span class="sxs-lookup"><span data-stu-id="097d8-200">That is because when you extend the model cases, the time steps used for prediction queries always start at the end of the original series.</span></span> <span data-ttu-id="097d8-201">因此，如果您加入兩個新的資料點，則傳回的前兩個預測將會與新的資料重疊。</span><span class="sxs-lookup"><span data-stu-id="097d8-201">Therefore, if you add two new data points, the first two predictions returned overlap with the new data.</span></span>  
  
-   <span data-ttu-id="097d8-202">當所有新的資料點都使用完之後，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會根據更新的模型做預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-202">After all the new data points are used up, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] makes predictions based on the updated model.</span></span> <span data-ttu-id="097d8-203">因此從 2005 年九月開始，您可以看到左欄中原始模型的 M200 Europe 與右欄中使用 EXTEND_MODEL_CASES 的模型之間的預測差異。</span><span class="sxs-lookup"><span data-stu-id="097d8-203">Therefore, starting in September 2005, you can see the difference between predictions for M200 Europe from the original model, in the left-hand column, and the model that uses EXTEND_MODEL_CASES, in the right-hand column.</span></span> <span data-ttu-id="097d8-204">這兩個預測不同是因為已經使用新的資料來更新此模型。</span><span class="sxs-lookup"><span data-stu-id="097d8-204">The predictions are different because the model has been updated with the new data.</span></span>  
  
## <a name="using-start-and-end-time-steps-to-control-predictions"></a><span data-ttu-id="097d8-205">使用開始和結束時間步驟來控制預測</span><span class="sxs-lookup"><span data-stu-id="097d8-205">Using Start and End Time Steps to Control Predictions</span></span>  
 <span data-ttu-id="097d8-206">當您擴充模型時，新的資料一定會附加到數列的結尾。</span><span class="sxs-lookup"><span data-stu-id="097d8-206">When you extend a model, the new data is always attached to the end of the series.</span></span> <span data-ttu-id="097d8-207">但是，基於預測的目的，用於預測查詢的時間配量會開始於原始數列的結尾。</span><span class="sxs-lookup"><span data-stu-id="097d8-207">However, for the purpose of prediction, the time slices used for prediction queries start at the end of the original series.</span></span> <span data-ttu-id="097d8-208">如果您在加入新的資料時只要取得新的預測，則必須將起點指定為時間配量的數目。</span><span class="sxs-lookup"><span data-stu-id="097d8-208">If you want to obtain only the new predictions when you add the new data, you must specify the starting point as a number of time slices.</span></span> <span data-ttu-id="097d8-209">例如，如果您要加入兩個新的資料點，而且想要做出四個新預測，您應該會這樣做：</span><span class="sxs-lookup"><span data-stu-id="097d8-209">For example, if you are adding two new data points and want to make four new predictions, you would do the following:</span></span>  
  
-   <span data-ttu-id="097d8-210">在時間序列模型上建立 PREDICTION JOIN，並指定兩個月的新資料。</span><span class="sxs-lookup"><span data-stu-id="097d8-210">Create a PREDICTION JOIN on a time series model, and specify two months of new data.</span></span>  
  
-   <span data-ttu-id="097d8-211">要求四個時間配量的預測，其中的起點是 3，而結束點則是時間配量 6。</span><span class="sxs-lookup"><span data-stu-id="097d8-211">Request predictions for four time slices, where the starting point is 3, and the ending point is time slice 6.</span></span>  
  
 <span data-ttu-id="097d8-212">換句話說，如果您的新資料包含 n 個時間配量，而且您要求時間步驟1到 n 的預測，則預測將會與新資料的相同期間一致。</span><span class="sxs-lookup"><span data-stu-id="097d8-212">In other words, if your new data contains n time slices, and you request predictions for time steps 1 through n, the predictions will coincide with the same period as the new data.</span></span> <span data-ttu-id="097d8-213">若要取得資料未涵蓋之期間的新預測，您必須在新資料序列之後的時間配量 n+1 上開始預測，或是確定您有要求其他的時間配量。</span><span class="sxs-lookup"><span data-stu-id="097d8-213">To get new predictions for a time periods not covered by your data, you must either start predictions at the time slice n+1 after the new data series, or make sure that you request additional time slices.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="097d8-214">當您加入新的資料時，將無法做出歷程記錄預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-214">You cannot make historical predictions when you add new data.</span></span>  
  
 <span data-ttu-id="097d8-215">下列範例示範 DMX 陳述式，該陳述式可讓您針對上一個範例中的兩個數列僅取得新的預測。</span><span class="sxs-lookup"><span data-stu-id="097d8-215">The following example shows the DMX statement that lets you get only the new predictions for the two series in the previous example.</span></span>  
  
```  
SELECT [Model Region],  
PredictTimeSeries([Quantity],3,6, EXTEND_MODEL_CASES) AS PredictQty  
FROM  
   [Forecasting_MIXED]  
NATURAL PREDICTION JOIN   
   SELECT 1 AS [ReportingDate],  
  '10' AS [Quantity],  
  'M200 Europe' AS [ModelRegion]  
UNION SELECT  
  2 AS [ReportingDate],  
  15 AS [Quantity]),  
  'M200 Europe' AS [ModelRegion]  
) AS t  
WHERE [ModelRegion] = 'M200 Europe'  
```  
  
 <span data-ttu-id="097d8-216">預測結果從時間配量 3 開始，這是在您提供兩個月的新資料之後。</span><span class="sxs-lookup"><span data-stu-id="097d8-216">The prediction results start at time slice 3, which is after the 2 months of new data that you supplied.</span></span>  
  
 <span data-ttu-id="097d8-217">**產品和地區： M200 歐洲**</span><span class="sxs-lookup"><span data-stu-id="097d8-217">**Product and Region: M200 Europe**</span></span>  
  
 <span data-ttu-id="097d8-218">具有更新資料的模型 (具有 EXTEND_MODEL_CASES 的 PredictTimeSeries)</span><span class="sxs-lookup"><span data-stu-id="097d8-218">Model with updated data (PredictTimeSeries with EXTEND_MODEL_CASES)</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="097d8-219">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-219">M200 Europe</span></span>|<span data-ttu-id="097d8-220">上午 9/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-220">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-221">72</span><span class="sxs-lookup"><span data-stu-id="097d8-221">72</span></span>|  
|<span data-ttu-id="097d8-222">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-222">M200 Europe</span></span>|<span data-ttu-id="097d8-223">上午 10/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-223">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-224">69</span><span class="sxs-lookup"><span data-stu-id="097d8-224">69</span></span>|  
|<span data-ttu-id="097d8-225">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-225">M200 Europe</span></span>|<span data-ttu-id="097d8-226">上午 11/25/2008 12:00:00</span><span class="sxs-lookup"><span data-stu-id="097d8-226">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-227">68</span><span class="sxs-lookup"><span data-stu-id="097d8-227">68</span></span>|  
|<span data-ttu-id="097d8-228">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="097d8-228">M200 Europe</span></span>|<span data-ttu-id="097d8-229">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="097d8-229">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="097d8-230">89</span><span class="sxs-lookup"><span data-stu-id="097d8-230">89</span></span>|  
  
## <a name="making-predictions-with-replace_model_cases"></a><span data-ttu-id="097d8-231">使用 REPLACE_MODEL_CASES 做出預測</span><span class="sxs-lookup"><span data-stu-id="097d8-231">Making Predictions with REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="097d8-232">當您想要定型一組案例上的模型，然後將該模型套用到不同的資料數列時，取代模型案例會非常實用。</span><span class="sxs-lookup"><span data-stu-id="097d8-232">Replacing the model cases is useful when you want to train a model on one set of cases and then apply that model to a different data series.</span></span> <span data-ttu-id="097d8-233">本案例的詳細逐步解說會在[第2課：建立預測案例中顯示 &#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="097d8-233">A detailed walkthrough of this scenario is presented in [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097d8-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="097d8-234">See Also</span></span>  
 <span data-ttu-id="097d8-235">[時間序列模型查詢範例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="097d8-235">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="097d8-236">PredictTimeSeries &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="097d8-236">PredictTimeSeries &#40;DMX&#41;</span></span>](/sql/dmx/predicttimeseries-dmx)  
  
  
