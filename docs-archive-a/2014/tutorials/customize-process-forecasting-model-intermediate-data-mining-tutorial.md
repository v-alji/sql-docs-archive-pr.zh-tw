---
title: 自訂及處理預測模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4bd25e15-9d9e-4528-b7bc-ccb856643aec
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 03dc67907b22750eb1b8539feaddec58f61f702f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598087"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="b95c0-102">自訂及處理預測模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="b95c0-102">Customizing and Processing the Forecasting Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="b95c0-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列演算法提供會影響模型建立方式以及時間資料分析方式的參數。</span><span class="sxs-lookup"><span data-stu-id="b95c0-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm provides parameters that affect how a model is created, and how time data is analyzed.</span></span> <span data-ttu-id="b95c0-104">變更這些屬性會對採礦模型如何進行預測造成重大的影響。</span><span class="sxs-lookup"><span data-stu-id="b95c0-104">Changing these properties can significantly affect how the mining model makes predictions.</span></span>  
  
 <span data-ttu-id="b95c0-105">在本教學課程的這項工作中，您將執行下列工作以修改模型：</span><span class="sxs-lookup"><span data-stu-id="b95c0-105">For this task in the tutorial, you will perform the following tasks to modify the model:</span></span>  
  
1.  <span data-ttu-id="b95c0-106">您將會藉由加入*PERIODICITY_HINT*參數的新值，自訂您的模型處理時間週期的方式。</span><span class="sxs-lookup"><span data-stu-id="b95c0-106">You will customize the way your model handles time periods by adding a new value for the *PERIODICITY_HINT* parameter.</span></span>  
  
2.  <span data-ttu-id="b95c0-107">您將學習 Microsoft 時間序列演算法的兩個其他重要參數：FORECAST_METHOD 和 PREDICTION_SMOOTHING。前者讓您控制用於預測的方法，後者則讓您自訂長期和短期預測的混合。</span><span class="sxs-lookup"><span data-stu-id="b95c0-107">You will learn about two other important parameters for the Microsoft Time Series algorithm: FORECAST_METHOD, which lets you control the method used for forecasting, and PREDICTION_SMOOTHING, which lets you customize the blend of long-term and short-term predictions.</span></span>  
  
3.  <span data-ttu-id="b95c0-108">您可以選擇告知演算法要如何計算遺漏值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-108">Optionally, you will tell the algorithm how you want missing values to be imputed.</span></span>  
  
4.  <span data-ttu-id="b95c0-109">進行完所有變更之後，您將部署及處理模型。</span><span class="sxs-lookup"><span data-stu-id="b95c0-109">After all the changes have been made, you will deploy and process the model.</span></span>  
  
## <a name="setting-time-series-parameters"></a><span data-ttu-id="b95c0-110">設定時間序列參數</span><span class="sxs-lookup"><span data-stu-id="b95c0-110">Setting Time Series Parameters</span></span>  
 <span data-ttu-id="b95c0-111">**週期性提示**</span><span class="sxs-lookup"><span data-stu-id="b95c0-111">**Periodicity Hints**</span></span>  
  
 <span data-ttu-id="b95c0-112">*PERIODICITY_HINT*參數會提供演算法，其中包含您預期會在資料中看到的額外時間週期相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b95c0-112">The *PERIODICITY_HINT* parameter provides the algorithm with information about additional time periods that you expect to see in the data.</span></span> <span data-ttu-id="b95c0-113">根據預設，時間序列模型會嘗試自動在資料中偵測模式。</span><span class="sxs-lookup"><span data-stu-id="b95c0-113">By default, time series models will try to automatically detect a pattern in the data.</span></span> <span data-ttu-id="b95c0-114">不過，如果您已經知道預期的時間循環，提供週期性提示可能會改進模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="b95c0-114">However, if you already know the expected time cycle, providing a periodicity hint can potentially improve the accuracy of the model.</span></span> <span data-ttu-id="b95c0-115">提供錯誤的週期性提示則可能會降低精確度；因此，如果您不確定應該使用哪個值，最好使用預設值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-115">However, if you provide the wrong periodicity hint, it can decrease accuracy; therefore, if you are not sure what value should be used, it is best to use the default.</span></span>  
  
 <span data-ttu-id="b95c0-116">例如，此模型所用的檢視每月會從 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 彙總銷售資料。</span><span class="sxs-lookup"><span data-stu-id="b95c0-116">For example, the view used for this model aggregates sales data from [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] on a monthly basis.</span></span> <span data-ttu-id="b95c0-117">因此，模型所用的每個時間配量表示一個月，所有預測也是以月為單位。</span><span class="sxs-lookup"><span data-stu-id="b95c0-117">Therefore each time slice used by the model represents one month, and all predictions will also be in terms of months.</span></span> <span data-ttu-id="b95c0-118">由於一年有12個月，而您預期銷售模式會每年重複一次，因此您會將*PERIODICITY_HINT*參數設定為 `12` ，以指出12個時間配量 (月份) 組成一個完整的銷售週期。</span><span class="sxs-lookup"><span data-stu-id="b95c0-118">Since there are 12 months in a year and you expect that sales patterns more or less repeat on a yearly basis, you will set the *PERIODICITY_HINT* parameter to `12`, to indicate that 12 time slices (months) constitute one complete sales cycle.</span></span>  
  
 <span data-ttu-id="b95c0-119">**預測方法**</span><span class="sxs-lookup"><span data-stu-id="b95c0-119">**Forecasting Method**</span></span>  
  
 <span data-ttu-id="b95c0-120">*FORECAST_METHOD*參數可控制是否針對短期或長期預測優化時間序列演算法。</span><span class="sxs-lookup"><span data-stu-id="b95c0-120">The *FORECAST_METHOD* parameter controls whether the time series algorithm is optimized for short-term or long-term predictions.</span></span> <span data-ttu-id="b95c0-121">根據預設， *FORECAST_METHOD*參數會設定為 MIXED，這表示兩個不同的演算法會混合和平衡，以提供短期與長期預測的良好結果。</span><span class="sxs-lookup"><span data-stu-id="b95c0-121">By default, the *FORECAST_METHOD* parameter is set to MIXED, which means that two different algorithms are blended and balanced to provide good results for both short-term and long-term prediction.</span></span>  
  
 <span data-ttu-id="b95c0-122">但是，如果您知道要使用特定的演算法，可以將值變更為 ARIMA 或 ARTXP。</span><span class="sxs-lookup"><span data-stu-id="b95c0-122">However, if you know that you want to use a particular algorithm, you can change the value to either ARIMA or ARTXP.</span></span>  
  
 <span data-ttu-id="b95c0-123">**加權長期與短期預測的比較**</span><span class="sxs-lookup"><span data-stu-id="b95c0-123">**Weighting Long-Term vs. Short-Term Predictions**</span></span>  
  
 <span data-ttu-id="b95c0-124">您也可以使用 PREDICTION_SMOOTHING 參數來自訂長期和短期預測的混合方式。</span><span class="sxs-lookup"><span data-stu-id="b95c0-124">You can also customize the way that long-term and short-term predictions are combined by using the PREDICTION_SMOOTHING parameter.</span></span> <span data-ttu-id="b95c0-125">依預設，此參數設為 0.5，一般而言可以提供整體精確度的最佳平衡。</span><span class="sxs-lookup"><span data-stu-id="b95c0-125">By default, this parameter is set to 0.5, which generally provides the best balance for overall accuracy.</span></span>  
  
#### <a name="to-change-the-algorithm-parameters"></a><span data-ttu-id="b95c0-126">若要變更演算法參數</span><span class="sxs-lookup"><span data-stu-id="b95c0-126">To change the algorithm parameters</span></span>  
  
1.  <span data-ttu-id="b95c0-127">在 [**採礦模型**] 索引標籤上，以滑鼠右鍵按一下 [**預測**]，然後選取 [**設定演算法參數]**。</span><span class="sxs-lookup"><span data-stu-id="b95c0-127">On the **Mining Models** tab, right-click **Forecasting**, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="b95c0-128">在 `PERIODICITY_HINT` [**演算法參數**] 對話方塊的資料列中，按一下 [**值**] 資料行，然後輸入 `{12}` ，包括大括弧。</span><span class="sxs-lookup"><span data-stu-id="b95c0-128">In the `PERIODICITY_HINT` row of the **Algorithm Parameters** dialog box, click the **Value** column, then type `{12}`, including the braces.</span></span>  
  
     <span data-ttu-id="b95c0-129">根據預設，演算法也會加入 {1} 值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-129">By default, the algorithm will also add the value {1}.</span></span>  
  
3.  <span data-ttu-id="b95c0-130">在資料 `FORECAST_METHOD` 列中，確認 [**值**] 文字方塊為空白或設為 `MIXED` 。</span><span class="sxs-lookup"><span data-stu-id="b95c0-130">In the `FORECAST_METHOD` row, verify that the **Value** text box is either blank or set to `MIXED`.</span></span> <span data-ttu-id="b95c0-131">如果輸入了不同的值，請輸入，將 `MIXED` 參數變更回預設值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-131">If a different value has been entered, type `MIXED` to change the parameter back to the default value.</span></span>  
  
4.  <span data-ttu-id="b95c0-132">在 [ **PREDICTION_SMOOTHING** ] 資料列中，確認 [**值**] 文字方塊為空白或設為0.5。</span><span class="sxs-lookup"><span data-stu-id="b95c0-132">In the **PREDICTION_SMOOTHING** row, verify that the **Value** text box is either blank or set to 0.5.</span></span> <span data-ttu-id="b95c0-133">如果輸入了不同的值，請按一下 [**值**] 並輸入，將 `0.5` 參數變更回預設值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-133">If a different value has been entered, click **Value** and type `0.5` to change the parameter back to the default value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b95c0-134">PREDICTION_SMOOTHING 參數只適用於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise。</span><span class="sxs-lookup"><span data-stu-id="b95c0-134">The PREDICTION_SMOOTHING parameter is available only in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="b95c0-135">因此，您無法在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard 之中檢視或變更 PREDICTION_SMOOTHING 參數的值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-135">Therefore, you cannot view or change the value of the PREDICTION_SMOOTHING parameter in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard.</span></span> <span data-ttu-id="b95c0-136">不過，預設行為是使用兩種演算法並且平均分配其權重。</span><span class="sxs-lookup"><span data-stu-id="b95c0-136">However, the default behavior is to use both algorithms and weight them equally.</span></span>  
  
5.  <span data-ttu-id="b95c0-137">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b95c0-137">Click **OK**.</span></span>  
  
## <a name="handling-missing-data-optional"></a><span data-ttu-id="b95c0-138">處理遺漏資料 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="b95c0-138">Handling Missing Data (Optional)</span></span>  
 <span data-ttu-id="b95c0-139">在許多情況下，您的銷售資料可能有填滿 Null 的間距，或可能有某分店錯過了報告期限，導致序列結尾處出現空白資料格。</span><span class="sxs-lookup"><span data-stu-id="b95c0-139">In many cases, your sales data might have gaps that are filled with nulls, or a store might have failed to meet the reporting deadline, leaving an empty cell at the end of the series.</span></span> <span data-ttu-id="b95c0-140">在這種情況下，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會發出下列錯誤，而且不處理模型。</span><span class="sxs-lookup"><span data-stu-id="b95c0-140">In such scenarios, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] raises the following error and will not process the model.</span></span>  
  
 <span data-ttu-id="b95c0-141">「 (資料採礦) 時發生錯誤：從「採礦模型」的「數列」開始，時間戳記不會同步處理 \<series name> \<model name> 。</span><span class="sxs-lookup"><span data-stu-id="b95c0-141">"Error (Data mining): Time stamps not synchronized starting with series \<series name>, of the mining model, \<model name>.</span></span> <span data-ttu-id="b95c0-142">所有時間序列都必須在同一個時間標示結束，且不能有任意遺漏資料點。</span><span class="sxs-lookup"><span data-stu-id="b95c0-142">All time series must end at the same time mark and cannot have arbitrarily missing data points.</span></span> <span data-ttu-id="b95c0-143">將 MISSING_VALUE_SUBSTITUTION 參數設定為 Previous 或數值常數，即可在適用時自動修補遺漏的資料點。」</span><span class="sxs-lookup"><span data-stu-id="b95c0-143">Setting the MISSING_VALUE_SUBSTITUTION parameter to Previous or to a numeric constant will automatically patch missing data points where possible."</span></span>  
  
 <span data-ttu-id="b95c0-144">若要避免這個錯誤，您可以指定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 使用下列任何一個方法，自動提供新值以填滿間距：</span><span class="sxs-lookup"><span data-stu-id="b95c0-144">To avoid this error, you can specify that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatically provide new values to fill in the gaps by using any one of the following methods:</span></span>  
  
-   <span data-ttu-id="b95c0-145">使用平均值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-145">Using an average value.</span></span> <span data-ttu-id="b95c0-146">平均值是使用相同資料序列中的全部有效值來計算。</span><span class="sxs-lookup"><span data-stu-id="b95c0-146">The mean is calculated by using all valid values in the same data series.</span></span>  
  
-   <span data-ttu-id="b95c0-147">使用上一個值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-147">Using the previous value.</span></span> <span data-ttu-id="b95c0-148">您可以將多個遺漏的資料格取代為上一個值，但是不可以填入起始值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-148">You can substitute previous values for multiple missing cells, but you cannot fill starting values.</span></span>  
  
-   <span data-ttu-id="b95c0-149">使用您套用的常數值。</span><span class="sxs-lookup"><span data-stu-id="b95c0-149">Using a constant value that you supply.</span></span>  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a><span data-ttu-id="b95c0-150">若要指定以平均值填滿間距</span><span class="sxs-lookup"><span data-stu-id="b95c0-150">To specify that gaps be filled by averaging values</span></span>  
  
1.  <span data-ttu-id="b95c0-151">在 [**採礦模型**] 索引標籤上，以滑鼠右鍵按一下 [**預測**] 資料行，然後選取 [**設定演算法參數]**。</span><span class="sxs-lookup"><span data-stu-id="b95c0-151">On the **Mining Models** tab, right-click the **Forecasting** column, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="b95c0-152">在 [**演算法參數**] 對話方塊的 [ **MISSING_VALUE_SUBSTITUTION** ] 資料列中，按一下 [**值**] 資料行，然後輸入 `Mean` 。</span><span class="sxs-lookup"><span data-stu-id="b95c0-152">In the **Algorithm Parameters** dialog box, in the **MISSING_VALUE_SUBSTITUTION** row, click the **Value** column, and type `Mean`.</span></span>  
  
## <a name="build-the-model"></a><span data-ttu-id="b95c0-153">建立模型</span><span class="sxs-lookup"><span data-stu-id="b95c0-153">Build the Model</span></span>  
 <span data-ttu-id="b95c0-154">若要使用模型，您必須將它部署至伺服器，然後透過演算法執行定型資料來處理模型。</span><span class="sxs-lookup"><span data-stu-id="b95c0-154">To use the model, you must deploy it to a server, and process the model by running the training data through the algorithm.</span></span>  
  
#### <a name="to-process-the-forecasting-model"></a><span data-ttu-id="b95c0-155">若要處理預測模型</span><span class="sxs-lookup"><span data-stu-id="b95c0-155">To process the forecasting model</span></span>  
  
1.  <span data-ttu-id="b95c0-156">在的 [**採礦模型**] 功能表上 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，選取 [**處理採礦結構] 和 [所有模型**]。</span><span class="sxs-lookup"><span data-stu-id="b95c0-156">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], select **Process Mining Structure and All Models**.</span></span>  
  
2.  <span data-ttu-id="b95c0-157">在詢問您是否要建立及部署專案的警告中，按一下 [**是]**。</span><span class="sxs-lookup"><span data-stu-id="b95c0-157">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="b95c0-158">在 [**處理採礦結構-預測**] 對話方塊中，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="b95c0-158">In the **Process Mining Structure - Forecasting** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="b95c0-159">[**處理進度**] 對話方塊隨即開啟，以顯示模型處理的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b95c0-159">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="b95c0-160">處理模型可能需要花一些時間。</span><span class="sxs-lookup"><span data-stu-id="b95c0-160">Model processing may take some time.</span></span>  
  
4.  <span data-ttu-id="b95c0-161">處理完成之後，按一下 [**關閉**] 以結束 [**處理進度**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b95c0-161">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="b95c0-162">再按一次 [關閉]，**結束**[**處理採礦結構-預測**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b95c0-162">Click **Close** again to exit the **Process Mining Structure - Forecasting** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b95c0-163">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="b95c0-163">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b95c0-164">&#40;中繼資料採礦教學課程中探索預測模型&#41;</span><span class="sxs-lookup"><span data-stu-id="b95c0-164">Exploring the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b95c0-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b95c0-165">See Also</span></span>  
 <span data-ttu-id="b95c0-166">[Microsoft 時間序列演算法技術參考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b95c0-166">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="b95c0-167">[Microsoft 時間序列演算法](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="b95c0-167">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 [<span data-ttu-id="b95c0-168">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="b95c0-168">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
