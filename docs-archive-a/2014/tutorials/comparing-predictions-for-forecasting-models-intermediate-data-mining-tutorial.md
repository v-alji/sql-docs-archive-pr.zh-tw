---
title: 比較預測模型 (中繼資料採礦教學課程的預測) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ead8a1fe-60d8-4017-8fb8-6fe32168e46d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 63cf9c001298b0d2bfd2cf35ed42485a16817fd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704477"
---
# <a name="comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="c4a21-102">比較用來預測模型的預測 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="c4a21-102">Comparing Predictions for Forecasting Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="c4a21-103">在本教學課程的先前步驟中，您建立了多個時間序列模型：</span><span class="sxs-lookup"><span data-stu-id="c4a21-103">In the previous steps of this tutorial, you created multiple time series models:</span></span>  
  
-   <span data-ttu-id="c4a21-104">每一個地區和模型組合的預測 (僅根據個別模型和地區的資料)。</span><span class="sxs-lookup"><span data-stu-id="c4a21-104">Predictions for each combination of region and model, based only on data for the individual model and region.</span></span>  
  
-   <span data-ttu-id="c4a21-105">每個地區的預測 (根據更新的資料)。</span><span class="sxs-lookup"><span data-stu-id="c4a21-105">Predictions for each region, based on updated data.</span></span>  
  
-   <span data-ttu-id="c4a21-106">所有模型的全球預測 (根據彙總資料)。</span><span class="sxs-lookup"><span data-stu-id="c4a21-106">Predictions for all models on a worldwide basis, based on aggregated data.</span></span>  
  
-   <span data-ttu-id="c4a21-107">M200 模型在北美地區的預測 (根據彙總模型)。</span><span class="sxs-lookup"><span data-stu-id="c4a21-107">Predictions for the M200 model in the North America region, based on the aggregated model.</span></span>  
  
 <span data-ttu-id="c4a21-108">為了概述時間序列預測的功能，您將檢閱變更，了解使用擴充或取代資料的選項如何影響預測結果。</span><span class="sxs-lookup"><span data-stu-id="c4a21-108">To summarize the features for time series predictions, you will review the changes to see how the use of the options to extend or replace data affected forecasting results.</span></span>  
  
 [<span data-ttu-id="c4a21-109">EXTEND_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="c4a21-109">EXTEND_MODEL_CASES</span></span>](#bkmk_EXTEND)  
  
 [<span data-ttu-id="c4a21-110">REPLACE_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="c4a21-110">REPLACE_MODEL_CASES</span></span>](#bkmk_REPLACE)  
  
##  <a name="comparing-the-original-results-with-results-after-adding-data"></a><a name="bkmk_EXTEND"></a><span data-ttu-id="c4a21-111">在加入資料之後比較原始結果與結果</span><span class="sxs-lookup"><span data-stu-id="c4a21-111">Comparing the Original Results with Results after Adding Data</span></span>  
 <span data-ttu-id="c4a21-112">讓我們查看太平洋地區 M200 產品線的資料，以瞭解如何以新資料更新模型會影響結果。</span><span class="sxs-lookup"><span data-stu-id="c4a21-112">Let's look at the data for just the M200 product line in the Pacific region, to see how updating the model with new data affects the results.</span></span> <span data-ttu-id="c4a21-113">請記得原始資料數列在 2004 年 6 月結束，而我們取得 7 月、8 月和 9 月的新資料。</span><span class="sxs-lookup"><span data-stu-id="c4a21-113">Remember that the original data series ended in June 2004, and we obtained new data for July, August, and September.</span></span>  
  
-   <span data-ttu-id="c4a21-114">第一個資料行顯示加入的新資料。</span><span class="sxs-lookup"><span data-stu-id="c4a21-114">The first column shows the new data that was added.</span></span>  
  
-   <span data-ttu-id="c4a21-115">第二個資料行顯示 7 月以後根據原始資料數列的預測。</span><span class="sxs-lookup"><span data-stu-id="c4a21-115">The second column shows the forecast for July and later based on the original data series.</span></span>  
  
-   <span data-ttu-id="c4a21-116">第三個資料行顯示根據擴充資料的預測。</span><span class="sxs-lookup"><span data-stu-id="c4a21-116">The third column shows the forecast based on the extended data.</span></span>  
  
|<span data-ttu-id="c4a21-117">**M200 Pacific**</span><span class="sxs-lookup"><span data-stu-id="c4a21-117">**M200 Pacific**</span></span>|<span data-ttu-id="c4a21-118">更新的實際銷售資料</span><span class="sxs-lookup"><span data-stu-id="c4a21-118">Updated real sales data</span></span>|<span data-ttu-id="c4a21-119">加入資料之前的預測</span><span class="sxs-lookup"><span data-stu-id="c4a21-119">Forecast before data was added</span></span>|<span data-ttu-id="c4a21-120">擴充預測</span><span class="sxs-lookup"><span data-stu-id="c4a21-120">Extended prediction</span></span>|  
|----------------------|-----------------------------|------------------------------------|-------------------------|  
|<span data-ttu-id="c4a21-121">7-25-2008</span><span class="sxs-lookup"><span data-stu-id="c4a21-121">7-25-2008</span></span>|<span data-ttu-id="c4a21-122">**65**</span><span class="sxs-lookup"><span data-stu-id="c4a21-122">**65**</span></span>|<span data-ttu-id="c4a21-123">32</span><span class="sxs-lookup"><span data-stu-id="c4a21-123">32</span></span>|<span data-ttu-id="c4a21-124">**65**</span><span class="sxs-lookup"><span data-stu-id="c4a21-124">**65**</span></span>|  
|<span data-ttu-id="c4a21-125">8-25-2008</span><span class="sxs-lookup"><span data-stu-id="c4a21-125">8-25-2008</span></span>|<span data-ttu-id="c4a21-126">**54**</span><span class="sxs-lookup"><span data-stu-id="c4a21-126">**54**</span></span>|<span data-ttu-id="c4a21-127">37</span><span class="sxs-lookup"><span data-stu-id="c4a21-127">37</span></span>|<span data-ttu-id="c4a21-128">**54**</span><span class="sxs-lookup"><span data-stu-id="c4a21-128">**54**</span></span>|  
|<span data-ttu-id="c4a21-129">9-25-2008</span><span class="sxs-lookup"><span data-stu-id="c4a21-129">9-25-2008</span></span>|<span data-ttu-id="c4a21-130">**61**</span><span class="sxs-lookup"><span data-stu-id="c4a21-130">**61**</span></span>|<span data-ttu-id="c4a21-131">32</span><span class="sxs-lookup"><span data-stu-id="c4a21-131">32</span></span>|<span data-ttu-id="c4a21-132">**61**</span><span class="sxs-lookup"><span data-stu-id="c4a21-132">**61**</span></span>|  
|<span data-ttu-id="c4a21-133">10-25-2008</span><span class="sxs-lookup"><span data-stu-id="c4a21-133">10-25-2008</span></span>|<span data-ttu-id="c4a21-134">無資料</span><span class="sxs-lookup"><span data-stu-id="c4a21-134">No data</span></span>|<span data-ttu-id="c4a21-135">36</span><span class="sxs-lookup"><span data-stu-id="c4a21-135">36</span></span>|<span data-ttu-id="c4a21-136">32</span><span class="sxs-lookup"><span data-stu-id="c4a21-136">32</span></span>|  
|<span data-ttu-id="c4a21-137">11-25-2008</span><span class="sxs-lookup"><span data-stu-id="c4a21-137">11-25-2008</span></span>|<span data-ttu-id="c4a21-138">無資料</span><span class="sxs-lookup"><span data-stu-id="c4a21-138">No data</span></span>|<span data-ttu-id="c4a21-139">31</span><span class="sxs-lookup"><span data-stu-id="c4a21-139">31</span></span>|<span data-ttu-id="c4a21-140">41</span><span class="sxs-lookup"><span data-stu-id="c4a21-140">41</span></span>|  
|<span data-ttu-id="c4a21-141">12-25-2008</span><span class="sxs-lookup"><span data-stu-id="c4a21-141">12-25-2008</span></span>|<span data-ttu-id="c4a21-142">無資料</span><span class="sxs-lookup"><span data-stu-id="c4a21-142">No data</span></span>|<span data-ttu-id="c4a21-143">34</span><span class="sxs-lookup"><span data-stu-id="c4a21-143">34</span></span>|<span data-ttu-id="c4a21-144">32</span><span class="sxs-lookup"><span data-stu-id="c4a21-144">32</span></span>|  
  
 <span data-ttu-id="c4a21-145">您將會注意到使用擴充資料 (此處以粗體顯示) 的預測完全重複實際資料點。</span><span class="sxs-lookup"><span data-stu-id="c4a21-145">You will note that the forecasts using the extended data (shown here in bold) repeat the real data points exactly.</span></span> <span data-ttu-id="c4a21-146">重複是預設行為。</span><span class="sxs-lookup"><span data-stu-id="c4a21-146">The repetition is by design.</span></span> <span data-ttu-id="c4a21-147">只要有可用的實際資料點，預測查詢就會傳回實際值，只在新的實際資料點已經用完後才會輸出新的預測值。</span><span class="sxs-lookup"><span data-stu-id="c4a21-147">As long as there are real data points to use, the prediction query will return the actual values, and output new prediction values only after the new actual data points have been used up.</span></span>  
  
 <span data-ttu-id="c4a21-148">一般而言，相較於模型資料開頭的資料，演算法對新資料的變更賦予較重的加權。</span><span class="sxs-lookup"><span data-stu-id="c4a21-148">In general, the algorithm weights the changes in the new data more strongly than data from the beginning of the model data.</span></span> <span data-ttu-id="c4a21-149">不過，在此情況下，新銷售數字比起上一個週期增幅僅為 20-30%，因此對預計銷售造成些微的上揚，在此之後銷售預測轉而向下，重複加入新資料之前月份的趨勢。</span><span class="sxs-lookup"><span data-stu-id="c4a21-149">However, in this case, the new sales figures represent an increase of only 20-30 percent over the previous period, so there only was a slight uptick in projected sales, after which the sales projections drop again, more in line with the trend in the months before the new data.</span></span>  
  
##  <a name="comparing-the-original-and-cross-prediction-results"></a><a name="bkmk_REPLACE"></a><span data-ttu-id="c4a21-150">比較原始和交叉預測結果</span><span class="sxs-lookup"><span data-stu-id="c4a21-150">Comparing the Original and Cross-Prediction Results</span></span>  
 <span data-ttu-id="c4a21-151">請記得，原始採礦模型揭露地區之間和產品線之間有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="c4a21-151">Remember that the original mining model revealed big differences between regions and between product lines.</span></span> <span data-ttu-id="c4a21-152">例如，M200 模型的銷售非常強，而 T1000 模型的銷售則在所有地區都很低。</span><span class="sxs-lookup"><span data-stu-id="c4a21-152">For example, sales for the M200 model were very strong, while sales for the T1000 model were fairly low across all regions.</span></span> <span data-ttu-id="c4a21-153">此外，有些數列沒有太多資料。</span><span class="sxs-lookup"><span data-stu-id="c4a21-153">Moreover, some series didn't have much data.</span></span> <span data-ttu-id="c4a21-154">數列不完全，表示它們沒有相同的起點。</span><span class="sxs-lookup"><span data-stu-id="c4a21-154">Series were ragged, meaning they didn't have the same starting point.</span></span>  
  
 <span data-ttu-id="c4a21-155">![序列預測 M200 與 T1000 數量](../../2014/tutorials/media/6series-defaultforecasting.gif "序列預測 M200 與 T1000 數量")</span><span class="sxs-lookup"><span data-stu-id="c4a21-155">![Series predicting M200 and T1000 quantity](../../2014/tutorials/media/6series-defaultforecasting.gif "Series predicting M200 and T1000 quantity")</span></span>  
  
 <span data-ttu-id="c4a21-156">因此，當您根據一般模型做預測，此模型以全球銷售而不是以原始資料集為基礎，預測會如何變更？</span><span class="sxs-lookup"><span data-stu-id="c4a21-156">So how did the predictions change when you made your projections based on the general model, which was based on world-wide sales, rather than the original data sets?</span></span> <span data-ttu-id="c4a21-157">為確保不遺失任何資訊或扭曲預測，您可以將結果儲存至資料表，將預測的資料表聯結至歷程記錄資料的資料表，然後在圖形中顯示兩組歷程記錄資料和預測。</span><span class="sxs-lookup"><span data-stu-id="c4a21-157">To assure yourself that you have not lost any information or skewed the predictions, you can save the results to a table, join the table of predictions to the table of historical data, and then graph the two sets of historical data and predictions.</span></span>  
  
 <span data-ttu-id="c4a21-158">下圖只以 M200 一個產品線為基礎。</span><span class="sxs-lookup"><span data-stu-id="c4a21-158">The following diagram is based on just one product line, the M200.</span></span> <span data-ttu-id="c4a21-159">圖形將初始採礦模型中的預測與使用彙總採礦模型的預測相比較。</span><span class="sxs-lookup"><span data-stu-id="c4a21-159">The graph compares the predictions from the initial mining model against the predictions using the aggregated mining model.</span></span>  
  
 <span data-ttu-id="c4a21-160">![Excel 圖表比較預測](../../2014/tutorials/media/m200-predictions-compared.gif "Excel 圖表比較預測")</span><span class="sxs-lookup"><span data-stu-id="c4a21-160">![Excel chart comparing predictions](../../2014/tutorials/media/m200-predictions-compared.gif "Excel chart comparing predictions")</span></span>  
  
 <span data-ttu-id="c4a21-161">您可以從此圖中得知，彙總採礦模型保留值的整體範圍和趨勢，同時將個別資料數列中的波動降至最低。</span><span class="sxs-lookup"><span data-stu-id="c4a21-161">From this diagram, you can see that the aggregated mining model preserves the overall range and trends in values while minimizing the fluctuations in the individual data series.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="c4a21-162">結論</span><span class="sxs-lookup"><span data-stu-id="c4a21-162">Conclusion</span></span>  
 <span data-ttu-id="c4a21-163">您已經學會如何建立及自訂可用於預測的時間序列模型。</span><span class="sxs-lookup"><span data-stu-id="c4a21-163">You have learned how to create and to customize a time series model that can be used for forecasting.</span></span>  
  
 <span data-ttu-id="c4a21-164">您已經學會使用 EXTEND_MODEL_CASES 參數，加入新資料及建立預測來更新時間序列模型，而不需重新處理模型。</span><span class="sxs-lookup"><span data-stu-id="c4a21-164">You have learned to update your time series models without having to reprocess them, by adding new data and creating predictions using the parameter, EXTEND_MODEL_CASES.</span></span>  
  
 <span data-ttu-id="c4a21-165">您已經學會使用 REPLACE_MODEL_CASES 參數以及將模型套用至不同資料數列，建立可用於交叉預測的模型。</span><span class="sxs-lookup"><span data-stu-id="c4a21-165">You have learned to create models that can be used for cross-prediction, by using the REPLACE_MODEL_CASES parameter and applying the model to a different data series.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a21-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4a21-166">See Also</span></span>  
 <span data-ttu-id="c4a21-167">[元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c4a21-167">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="c4a21-168">時間序列模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="c4a21-168">Time Series Model Query Examples</span></span>](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
