---
title: 第4課：使用 DMX 建立時間序列預測 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 772e5f5f71ca82dd18fec48730522c80e907414f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686554"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a><span data-ttu-id="fbe6d-102">第 4 課：使用 DMX 建立時間序列預測</span><span class="sxs-lookup"><span data-stu-id="fbe6d-102">Lesson 4: Creating Time Series Predictions Using DMX</span></span>
  <span data-ttu-id="fbe6d-103">在這堂課和下列課程中，您將使用資料採礦延伸模組 (DMX) ，根據您在[第1課：建立時間序列的「採礦模型」和「採礦結構](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)」和[第2課：將採礦模型加入至時間序列採礦結構](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)中所建立的時間序列模型來建立不同類型的預測。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-103">In this lesson and the following lesson, you will use Data Mining Extensions (DMX) to create different types of predictions based on the time series models that you created in [Lesson 1: Creating a Time Series Mining Model and Mining Structure](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md) and [Lesson 2: Adding Mining Models to the Time Series Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md).</span></span>  
  
 <span data-ttu-id="fbe6d-104">有了時間序列模型，您有許多選擇可用來進行預測：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-104">With a time series model, you have many options for making predictions:</span></span>  
  
-   <span data-ttu-id="fbe6d-105">在採礦模型中使用現有的模式和資料。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-105">Use the existing patterns and data in the mining model</span></span>  
  
-   <span data-ttu-id="fbe6d-106">在採礦模型中使用現有的模式，但是提供新的資料。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-106">Use the existing patterns in the mining model but supply new data</span></span>  
  
-   <span data-ttu-id="fbe6d-107">將新的資料加入到模型中，或是更新模型。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-107">Add new data to the model or update the model.</span></span>  
  
 <span data-ttu-id="fbe6d-108">這些預測類型的語法摘要列在底下：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-108">The syntax for making these prediction types is summarized below:</span></span>  
  
 <span data-ttu-id="fbe6d-109">預設時間序列預測</span><span class="sxs-lookup"><span data-stu-id="fbe6d-109">Default time series prediction</span></span>  
 <span data-ttu-id="fbe6d-110">使用[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) ，以從定型的採礦模型傳回指定的預測數目。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-110">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) to return the specified number of predictions from the trained mining model.</span></span>  
  
 <span data-ttu-id="fbe6d-111">例如，請參閱[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)或[時間序列模型查詢範例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-111">For example, see [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) or [Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="fbe6d-112">EXTEND_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="fbe6d-112">EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="fbe6d-113">使用[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)搭配 EXTEND_MODEL_CASES 引數來加入新資料、擴充數列，並根據更新的採礦模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-113">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) with the EXTEND_MODEL_CASES argument to add new data, extend the series, and create predictions based on the updated mining model.</span></span>  
  
 <span data-ttu-id="fbe6d-114">本教學課程包含的範例將示範如何使用 EXTEND_MODEL_CASES。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-114">This tutorial contains an example of how to use EXTEND_MODEL_CASES.</span></span>  
  
 <span data-ttu-id="fbe6d-115">REPLACE_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="fbe6d-115">REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="fbe6d-116">使用[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)搭配 REPLACE_MODEL_CASES 引數，以新的資料數列取代原始資料，然後根據將採礦模型中的模式套用至新的資料數列來建立預測。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-116">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) with the REPLACE_MODEL_CASES argument to replace the original data with a new data series, and then create predictions based on applying the patterns in the mining model to the new data series.</span></span>  
  
 <span data-ttu-id="fbe6d-117">如需如何使用 REPLACE_MODEL_CASES 的範例，請參閱[第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-117">For an example of how to use REPLACE_MODEL_CASES, see [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="fbe6d-118">課程工作</span><span class="sxs-lookup"><span data-stu-id="fbe6d-118">Lesson Tasks</span></span>  
 <span data-ttu-id="fbe6d-119">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-119">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="fbe6d-120">根據現有的資料建立查詢來取得預設的預測。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-120">Create a query to get the default predictions based on existing data.</span></span>  
  
 <span data-ttu-id="fbe6d-121">在下一課中，您將會執行下列相關工作：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-121">In the following lesson you will perform the following related tasks:</span></span>  
  
-   <span data-ttu-id="fbe6d-122">建立查詢來提供新的資料，並取得更新的預測。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-122">Create a query to supply new data and get updated predictions.</span></span>  
  
 <span data-ttu-id="fbe6d-123">除了使用 DMX 手動建立查詢以外，您也可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中使用預測查詢產生器來建立預測。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-123">In addition to creating queries manually by using DMX, you can also create predictions by using the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="simple-time-series-prediction-query"></a><span data-ttu-id="fbe6d-124">簡單時間序列預測查詢</span><span class="sxs-lookup"><span data-stu-id="fbe6d-124">Simple Time Series Prediction Query</span></span>  
 <span data-ttu-id="fbe6d-125">第一個步驟是搭配 `SELECT FROM` 函數一起使用 `PredictTimeSeries` 陳述式來建立時間序列預測。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-125">The first step is to use the `SELECT FROM` statement together with the `PredictTimeSeries` function to create time series predictions.</span></span> <span data-ttu-id="fbe6d-126">時間序列模型支援用來建立預測的簡化語法：您不需要提供任何輸入，只需要指定所要建立的預測數。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-126">Time series models support a simplified syntax for creating predictions: you do not need to supply any inputs, but only have to specify the number of predictions to create.</span></span> <span data-ttu-id="fbe6d-127">以下是您將使用之陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-127">The following is a generic example of the statement you will use:</span></span>  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 <span data-ttu-id="fbe6d-128">選取清單可以包含模型中的資料行，例如您要為其建立預測的產品線名稱，或是預測函數（例如， [&#40;dmx&#41;](/sql/dmx/lag-dmx)或[PredictTimeSeries &#40;Dmx&#41;](/sql/dmx/predicttimeseries-dmx)的 Lag，特別是針對時間序列的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-128">The select list can contain columns from the model, such as the name of the product line that you are creating the predictions for, or prediction functions, such as [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) or [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx), which are specifically for time series mining models.</span></span>  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a><span data-ttu-id="fbe6d-129">若要建立簡單的時間序列預測查詢</span><span class="sxs-lookup"><span data-stu-id="fbe6d-129">To create a simple time series prediction query</span></span>  
  
1.  <span data-ttu-id="fbe6d-130">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-130">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="fbe6d-131">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-131">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="fbe6d-132">將此陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-132">Copy the generic example of the statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="fbe6d-133">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-133">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="fbe6d-134">成為：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-134">with:</span></span>  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     <span data-ttu-id="fbe6d-135">第一行會從可識別此數列的採礦模型中擷取值。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-135">The first line retrieves a value from the mining model that identifies the series.</span></span>  
  
     <span data-ttu-id="fbe6d-136">第二行和第三行會使用 `PredictTimeSeries` 函數。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-136">The second and third lines use the `PredictTimeSeries` function.</span></span> <span data-ttu-id="fbe6d-137">每一行都會預測不同的屬性 (`[Quantity]` 或 `[Amount]`)。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-137">Each line predicts a different attribute, `[Quantity]` or `[Amount]`.</span></span> <span data-ttu-id="fbe6d-138">可預測屬性名稱後面的數字會指定所要預測的時間步驟數。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-138">The numbers after the names of the predictable attributes specify the number of time steps to predict.</span></span>  
  
     <span data-ttu-id="fbe6d-139">`AS` 子句是用來針對每一個預測函數傳回的資料行提供一個名稱。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-139">The `AS` clause is used to provide a name for the column that is returned by each prediction function.</span></span> <span data-ttu-id="fbe6d-140">如果您不提供別名，則當傳回這兩個資料行時，預設都會將其加上 `Expression` 標籤。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-140">If you do not supply an alias, by default both columns are returned with the label, `Expression`.</span></span>  
  
4.  <span data-ttu-id="fbe6d-141">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-141">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="fbe6d-142">成為：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-142">with:</span></span>  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  <span data-ttu-id="fbe6d-143">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-143">Replace the following:</span></span>  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     <span data-ttu-id="fbe6d-144">成為：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-144">with:</span></span>  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     <span data-ttu-id="fbe6d-145">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="fbe6d-145">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  <span data-ttu-id="fbe6d-146">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-146">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="fbe6d-147">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `SimpleTimeSeriesPrediction.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-147">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SimpleTimeSeriesPrediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="fbe6d-148">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-148">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="fbe6d-149">此查詢會針對 `WHERE` 子句中指定之產品和區域的兩個組合，每個組合各傳回 6 個預測。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-149">The query returns 6 predictions for each of the two combinations of product and region that are specified in the `WHERE` clause.</span></span>  
  
 <span data-ttu-id="fbe6d-150">在下一課中，您將會建立查詢來提供新資料給模型，然後將該項預測的結果與您剛才建立的預測做比較。</span><span class="sxs-lookup"><span data-stu-id="fbe6d-150">In the next lesson, you will create a query that supplies new data to the model, and compare the results of that prediction with the one you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fbe6d-151">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="fbe6d-151">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fbe6d-152">第 5 課：擴充時間序列模型</span><span class="sxs-lookup"><span data-stu-id="fbe6d-152">Lesson 5: Extending the Time Series Model</span></span>](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="fbe6d-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbe6d-153">See Also</span></span>  
 <span data-ttu-id="fbe6d-154">[DMX&#41;的 PredictTimeSeries &#40;](/sql/dmx/predicttimeseries-dmx) </span><span class="sxs-lookup"><span data-stu-id="fbe6d-154">[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) </span></span>  
 <span data-ttu-id="fbe6d-155">[DMX&#41;的 Lag &#40;](/sql/dmx/lag-dmx) </span><span class="sxs-lookup"><span data-stu-id="fbe6d-155">[Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) </span></span>  
 <span data-ttu-id="fbe6d-156">[時間序列模型查詢範例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="fbe6d-156">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="fbe6d-157">第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="fbe6d-157">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
