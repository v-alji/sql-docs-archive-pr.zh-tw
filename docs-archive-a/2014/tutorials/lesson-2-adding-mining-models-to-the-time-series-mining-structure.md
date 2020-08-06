---
title: 第2課：將採礦模型加入至時間序列的採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75c2a74b-21ce-44fb-a26b-68be4c685c12
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ae0bb91fafb53c0c077a4e0d82558b550d0e6070
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584922"
---
# <a name="lesson-2-adding-mining-models-to-the-time-series-mining-structure"></a><span data-ttu-id="044e0-102">第 2 課：將採礦模型新增至時間序列採礦結構</span><span class="sxs-lookup"><span data-stu-id="044e0-102">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>
  <span data-ttu-id="044e0-103">在這一課，您會將新的採礦模型加入至您剛在[第1課：建立時間序列](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)的「採礦模型」和「採礦結構」中所建立的「採礦結構」。</span><span class="sxs-lookup"><span data-stu-id="044e0-103">In this lesson, you will add a new mining model to the mining structure that you just created in [Lesson 1: Creating a Time Series Mining Model and Mining Structure](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md).</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="044e0-104">ALTER MINING STRUCTURE 陳述式</span><span class="sxs-lookup"><span data-stu-id="044e0-104">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="044e0-105">若要將新的採礦模型加入至現有的採礦結構，請使用[ALTER 採礦結構 &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)語句。</span><span class="sxs-lookup"><span data-stu-id="044e0-105">In order to add a new mining model to an existing mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="044e0-106">陳述式中的程式碼可分成下列各部份：</span><span class="sxs-lookup"><span data-stu-id="044e0-106">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="044e0-107">識別採礦結構</span><span class="sxs-lookup"><span data-stu-id="044e0-107">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="044e0-108">命名採礦模型</span><span class="sxs-lookup"><span data-stu-id="044e0-108">Naming the mining model</span></span>  
  
-   <span data-ttu-id="044e0-109">定義索引鍵資料行</span><span class="sxs-lookup"><span data-stu-id="044e0-109">Defining the key column</span></span>  
  
-   <span data-ttu-id="044e0-110">定義可預測的資料行</span><span class="sxs-lookup"><span data-stu-id="044e0-110">Defining the predictable columns</span></span>  
  
-   <span data-ttu-id="044e0-111">指定演算法和任何參數變更</span><span class="sxs-lookup"><span data-stu-id="044e0-111">Specifying the algorithm and any parameter changes</span></span>  
  
 <span data-ttu-id="044e0-112">以下是 ALTER MINING STRUCTURE 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="044e0-112">The following is a generic example of the ALTER MINING STRUCTURE statement:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
   ([<key columns>],  
    <mining model columns>  
   )  
USING <algorithm name>([<algorithm parameters>])  
[WITH DRILLTHROUGH]  
```  
  
 <span data-ttu-id="044e0-113">程式碼的第一行會識別將加入採礦模型的現有採礦結構：</span><span class="sxs-lookup"><span data-stu-id="044e0-113">The first line of the code identifies the existing mining structure to which the mining models will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="044e0-114">程式碼的下一行命名要加入採礦結構中的採礦模型：</span><span class="sxs-lookup"><span data-stu-id="044e0-114">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="044e0-115">如需在 DMX 中命名物件的詳細資訊，請參閱[dmx&#41;&#40;的識別碼](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="044e0-115">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="044e0-116">接下來幾行的程式碼定義採礦結構中將由採礦模型使用的資料行：</span><span class="sxs-lookup"><span data-stu-id="044e0-116">The next lines of the code define columns from the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key columns>],  
<mining model columns>  
```  
  
 <span data-ttu-id="044e0-117">您只能使用已存在於採礦結構中的資料行，且清單中的第一個資料行必須是採礦結構中的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="044e0-117">You can only use columns that already exist in the mining structure, and the first column in the list must be the key column from the mining structure.</span></span>  
  
 <span data-ttu-id="044e0-118">程式碼的下一行會定義產生採礦模型的採礦演算法，以及您可以在演算法上設定的演算法參數，並指定您是否可以從採礦模型向下鑽研到定型案例中的檢視詳細資料：</span><span class="sxs-lookup"><span data-stu-id="044e0-118">The next lines of the code defines the mining algorithm that generates the mining model and the algorithm parameters that you can set on the algorithm, and specify whether you can drill down from the mining model into view detailed data in the training cases:</span></span>  
  
```  
USING <algorithm name>([<algorithm parameters>])  
WITH DRILLTHROUGH  
```  
  
 <span data-ttu-id="044e0-119">如需您可以調整之演算法參數的詳細資訊，請參閱[Microsoft 時間序列演算法技術參考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="044e0-119">For more information about the algorithm parameters that you can adjust, see [Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="044e0-120">您可以使用下列語法來指定採礦模型中要用於預測的資料行：</span><span class="sxs-lookup"><span data-stu-id="044e0-120">You can specify that a column in the mining model be used for prediction by using the following syntax:</span></span>  
  
```  
<mining model column> PREDICT  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="044e0-121">課程工作</span><span class="sxs-lookup"><span data-stu-id="044e0-121">Lesson Tasks</span></span>  
 <span data-ttu-id="044e0-122">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="044e0-122">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="044e0-123">將新的時間序列採礦模型加入到結構中。</span><span class="sxs-lookup"><span data-stu-id="044e0-123">Add a new time series mining model to the structure.</span></span>  
  
-   <span data-ttu-id="044e0-124">變更演算法參數，以使用不同的分析和預測方法。</span><span class="sxs-lookup"><span data-stu-id="044e0-124">Change the algorithm parameters to use a different method of analysis and prediction</span></span>  
  
## <a name="adding-an-arima-time-series-model-to-the-structure"></a><span data-ttu-id="044e0-125">將 ARIMA 時間序列模型加入到結構中</span><span class="sxs-lookup"><span data-stu-id="044e0-125">Adding an ARIMA Time Series Model to the Structure</span></span>  
 <span data-ttu-id="044e0-126">第一個步驟是將新的預測採礦模型加入到現有的結構中。</span><span class="sxs-lookup"><span data-stu-id="044e0-126">The first step is to add a new forecasting mining model to the existing structure.</span></span> <span data-ttu-id="044e0-127">根據預設，[!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列演算法會使用兩個演算法 (ARIMA 和 ARTXP) 建立時間序列採礦模型，並混和結果。</span><span class="sxs-lookup"><span data-stu-id="044e0-127">By default, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm creates time series mining models by using two algorithms, ARIMA and ARTXP, and blending the results.</span></span> <span data-ttu-id="044e0-128">但是，您可以指定所要使用的單一演算法，或是指定確切的演算法混和。</span><span class="sxs-lookup"><span data-stu-id="044e0-128">However, you can specify a single algorithm to use, or you can specify the exact blend of algorithms.</span></span> <span data-ttu-id="044e0-129">在這個步驟中，您將會加入只使用 ARIMA 演算法的新模型。</span><span class="sxs-lookup"><span data-stu-id="044e0-129">In this step, you will add a new model that uses only the ARIMA algorithm.</span></span> <span data-ttu-id="044e0-130">此演算法已針對長期預測而最佳化。</span><span class="sxs-lookup"><span data-stu-id="044e0-130">This algorithm is optimized for long-term prediction.</span></span>  
  
#### <a name="to-add-an-arima-time-series-mining-model"></a><span data-ttu-id="044e0-131">若要加入 ARIMA 時間序列採礦模型</span><span class="sxs-lookup"><span data-stu-id="044e0-131">To add an ARIMA time series mining model</span></span>  
  
1.  <span data-ttu-id="044e0-132">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX** ] 以開啟 [查詢編輯器] 和新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="044e0-132">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="044e0-133">將 ALTER MINING STRUCTURE 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="044e0-133">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="044e0-134">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="044e0-134">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="044e0-135">成為：</span><span class="sxs-lookup"><span data-stu-id="044e0-135">with:</span></span>  
  
    ```  
    [Forecasting_MIXED_Structure]  
    ```  
  
4.  <span data-ttu-id="044e0-136">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="044e0-136">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="044e0-137">成為：</span><span class="sxs-lookup"><span data-stu-id="044e0-137">with:</span></span>  
  
    ```  
    Forecasting_ARIMA  
    ```  
  
5.  <span data-ttu-id="044e0-138">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="044e0-138">Replace the following:</span></span>  
  
    ```  
    <key columns>,  
    ```  
  
     <span data-ttu-id="044e0-139">成為：</span><span class="sxs-lookup"><span data-stu-id="044e0-139">with:</span></span>  
  
    ```  
    [ReportingDate],  
    [ModelRegion]  
    ```  
  
     <span data-ttu-id="044e0-140">請注意，您不需要重複您在 CREATE MINING MODEL 陳述式中所提供的任何資料類型或內容類型資訊，因為這項資訊已經儲存在採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="044e0-140">Note that you do not need to repeat any of the date type or content type information that you provided in the CREATE MINING MODEL statement, because this information is already stored in the mining structure.</span></span>  
  
6.  <span data-ttu-id="044e0-141">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="044e0-141">Replace the following:</span></span>  
  
    ```  
    <mining model columns>  
    ```  
  
     <span data-ttu-id="044e0-142">成為：</span><span class="sxs-lookup"><span data-stu-id="044e0-142">with:</span></span>  
  
    ```  
    ([Quantity] PREDICT,  
    [Amount] PREDICT  
    )  
    ```  
  
7.  <span data-ttu-id="044e0-143">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="044e0-143">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>([<algorithm parameters>])   
    [WITH DRILLTHROUGH]  
    ```  
  
     <span data-ttu-id="044e0-144">成為：</span><span class="sxs-lookup"><span data-stu-id="044e0-144">with:</span></span>  
  
    ```  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="044e0-145">現在，產生的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="044e0-145">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARIMA]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
8.  <span data-ttu-id="044e0-146">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="044e0-146">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
9. <span data-ttu-id="044e0-147">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Forecasting_ARIMA.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="044e0-147">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_ARIMA.dmx`.</span></span>  
  
10. <span data-ttu-id="044e0-148">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="044e0-148">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-an-artxp-time-series-model-to-the-structure"></a><span data-ttu-id="044e0-149">將 ARTXP 時間序列模型加入到結構中</span><span class="sxs-lookup"><span data-stu-id="044e0-149">Adding an ARTXP Time Series Model to the Structure</span></span>  
 <span data-ttu-id="044e0-150">ARTXP 演算法是 SQL Server 2005 中的預設時間序列演算法，而且已針對長期預測而最佳化。</span><span class="sxs-lookup"><span data-stu-id="044e0-150">The ARTXP algorithm was the default time series algorithm in SQL Server 2005 and is optimized for short-term prediction.</span></span> <span data-ttu-id="044e0-151">為了使用所有的這三種時間序列演算法來比較預測，您將會再加入一個根據 ARTXP 演算法的模型。</span><span class="sxs-lookup"><span data-stu-id="044e0-151">To compare predictions by using all three time series algorithms, you will add one more model that is based on the ARTXP algorithm.</span></span>  
  
#### <a name="to-add-an-artxp-time-series-mining-model"></a><span data-ttu-id="044e0-152">若要加入 ARTXP 時間序列採礦模型</span><span class="sxs-lookup"><span data-stu-id="044e0-152">To add an ARTXP time series mining model</span></span>  
  
1.  <span data-ttu-id="044e0-153">複製下列程式碼，並貼入空白查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="044e0-153">Copy the following code into a blank query window.</span></span>  
  
     <span data-ttu-id="044e0-154">請注意，除了新採礦模型的名稱及 FORECAST_METHOD 參數值以外，您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="044e0-154">Note that you do not need to change anything except the name of the new mining model, and the value of the FORECAST_METHOD parameter.</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARTXP]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARTXP')  
    WITH DRILLTHROUGH  
    ```  
  
2.  <span data-ttu-id="044e0-155">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="044e0-155">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
3.  <span data-ttu-id="044e0-156">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Forecasting_ARTXP.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="044e0-156">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_ARTXP.dmx`.</span></span>  
  
4.  <span data-ttu-id="044e0-157">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="044e0-157">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="044e0-158">在下一課，您將處理所有的模型和採礦結構。</span><span class="sxs-lookup"><span data-stu-id="044e0-158">In the next lesson, you will process all of the models and the mining structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="044e0-159">下一課</span><span class="sxs-lookup"><span data-stu-id="044e0-159">Next Lesson</span></span>  
 [<span data-ttu-id="044e0-160">第 3 課：處理時間序列結構和模型</span><span class="sxs-lookup"><span data-stu-id="044e0-160">Lesson 3: Processing the Time Series Structure and Models</span></span>](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="044e0-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="044e0-161">See Also</span></span>  
 <span data-ttu-id="044e0-162">[Microsoft 時間序列演算法](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="044e0-162">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 [<span data-ttu-id="044e0-163">Microsoft 時間序列演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="044e0-163">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
