---
title: 時間序列模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series algorithms [Analysis Services]
- MISSING_VALUE_SUBSTITUTION
- time series [Analysis Services]
- predictions [Analysis Services], time series
- EXTEND_MODEL_CASES parameter
- REPLACE_MODEL_CASES parameter
- prediction queries [DMX]
- PREDICTION_SMOOTHING
- content queries [DMX]
ms.assetid: 9a1c527e-2997-493b-ad6a-aaa71260b018
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f6b6ed2674d5f1d852b6281c6244af4f2f6ad3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605938"
---
# <a name="time-series-model-query-examples"></a><span data-ttu-id="c69e9-102">時間序列模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="c69e9-102">Time Series Model Query Examples</span></span>
  <span data-ttu-id="c69e9-103">當您針對資料採礦模型建立查詢時，可以建立內容查詢來提供有關分析期間所發現之模式的詳細資料，或是建立預測查詢來使用模型中的模式，為新的資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-103">When you create a query against a data mining model, you can create either a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="c69e9-104">例如，時間序列模型的內容查詢可能會提供有關所偵測到之週期性結構的其他詳細資料，而預測查詢則為您提供下 5-10 個時間配量的預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-104">For example, a content query for a time series model might provide additional details about the periodic structures that were detected, while a prediction query might give you predictions for the next 5-10 time slices.</span></span> <span data-ttu-id="c69e9-105">您也可以使用查詢來擷取有關模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="c69e9-106">本章節將說明如何針對以 Microsoft 時間序列演算法為根據的模型來建立兩種查詢。</span><span class="sxs-lookup"><span data-stu-id="c69e9-106">This section explains how to create both kinds of queries for models that are based on the Microsoft Time Series algorithm.</span></span>  
  
 <span data-ttu-id="c69e9-107">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="c69e9-107">**Content Queries**</span></span>  
  
 [<span data-ttu-id="c69e9-108">擷取模型的週期性提示</span><span class="sxs-lookup"><span data-stu-id="c69e9-108">Retrieving Periodicity Hints for the Model</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="c69e9-109">擷取 ARIMA 模型的方程式</span><span class="sxs-lookup"><span data-stu-id="c69e9-109">Retrieving the Equation for an ARIMA Model</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="c69e9-110">擷取 ARTxp 模型的方程式</span><span class="sxs-lookup"><span data-stu-id="c69e9-110">Retrieving the Equation for an ARTxp Model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="c69e9-111">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="c69e9-111">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="c69e9-112">了解取代和擴充時間序列資料的時機</span><span class="sxs-lookup"><span data-stu-id="c69e9-112">Understanding When to Replace and When to Extend Time Series Data</span></span>](#bkmk_ReplaceExtend)  
  
 [<span data-ttu-id="c69e9-113">使用 EXTEND_MODEL_CASES 進行預測</span><span class="sxs-lookup"><span data-stu-id="c69e9-113">Making Predictions with EXTEND_MODEL_CASES</span></span>](#bkmk_EXTEND)  
  
 [<span data-ttu-id="c69e9-114">使用 REPLACE_MODEL_CASES 進行預測</span><span class="sxs-lookup"><span data-stu-id="c69e9-114">Making Predictions with REPLACE_MODEL_CASES</span></span>](#bkmk_REPLACE)  
  
 [<span data-ttu-id="c69e9-115">時間序列模型中的遺漏值替代</span><span class="sxs-lookup"><span data-stu-id="c69e9-115">Missing Value Substitution in Time Series Models</span></span>](#bkmk_MissingValues)  
  
## <a name="getting-information-about-a-time-series-model"></a><span data-ttu-id="c69e9-116">取得有關時間序列模型的資訊</span><span class="sxs-lookup"><span data-stu-id="c69e9-116">Getting Information about a Time Series Model</span></span>  
 <span data-ttu-id="c69e9-117">模型內容查詢可以提供有關此模型的基本資訊，例如在建立模型時所使用的參數以及上次處理模型的時間。</span><span class="sxs-lookup"><span data-stu-id="c69e9-117">A model content query can provide basic information about the model, such as the parameters that were used when the model was created, the time the model was last processed.</span></span> <span data-ttu-id="c69e9-118">下列範例說明使用資料採礦結構描述資料列集來查詢模型內容的基本語法。</span><span class="sxs-lookup"><span data-stu-id="c69e9-118">The following example illustrates the basic syntax for querying the model content by using the data mining schema rowsets.</span></span>  
  
###  <a name="sample-query-1-retrieving-periodicity-hints-for-the-model"></a><a name="bkmk_Query1"></a> <span data-ttu-id="c69e9-119">範例查詢 1：擷取模型的週期性提示</span><span class="sxs-lookup"><span data-stu-id="c69e9-119">Sample Query 1: Retrieving Periodicity Hints for the Model</span></span>  
 <span data-ttu-id="c69e9-120">您可以擷取時間序列中所找到的週期性，其方式是查詢 ARIMA 樹狀結構或 ARTXP 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="c69e9-120">You can retrieve the periodicities that were found within the time series by querying the ARIMA tree or the ARTXP tree.</span></span> <span data-ttu-id="c69e9-121">但是，完成之模型中的週期性可能不會與當您建立模型時指定為提示的週期相同。</span><span class="sxs-lookup"><span data-stu-id="c69e9-121">However, the periodicities in the completed model might not be the same as the periods that you specified as hints when you created the model.</span></span> <span data-ttu-id="c69e9-122">若要擷取當您建立模型時提供為參數的提示，您可以使用下列 DMX 陳述式來查詢採礦模型內容結構描述資料列集：</span><span class="sxs-lookup"><span data-stu-id="c69e9-122">To retrieve the hints that were supplied as parameters when you created the model, you can query the mining model content schema rowset by using the following DMX statement:</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = '<model name>'  
```  
  
 <span data-ttu-id="c69e9-123">部分結果：</span><span class="sxs-lookup"><span data-stu-id="c69e9-123">Partial results:</span></span>  
  
|<span data-ttu-id="c69e9-124">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c69e9-124">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="c69e9-125">COMPLEXITY_PENALTY = 0.1，MINIMUM_SUPPORT = 10，PERIODICITY_HINT = {1,3} ,..。。</span><span class="sxs-lookup"><span data-stu-id="c69e9-125">COMPLEXITY_PENALTY=0.1,MINIMUM_SUPPORT=10,PERIODICITY_HINT={1,3},....</span></span>|  
  
 <span data-ttu-id="c69e9-126">預設週期性提示為 {1}，而且會出現在所有模型中；這個範例模型是使用其他提示所建立，這個提示可能不會出現在最終模型中。</span><span class="sxs-lookup"><span data-stu-id="c69e9-126">The default periodicity hint is {1} and appears in all models; this sample model was created with an additional hint that might not be present in the final model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c69e9-127">這裡的結果已被截斷來提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="c69e9-127">The results have been truncated here for readability.</span></span>  
  
###  <a name="sample-query-2-retrieving-the-equation-for-an-arima-model"></a><a name="bkmk_Query2"></a> <span data-ttu-id="c69e9-128">範例查詢 2：擷取 ARIMA 模型的方程式</span><span class="sxs-lookup"><span data-stu-id="c69e9-128">Sample Query 2: Retrieving the Equation for an ARIMA Model</span></span>  
 <span data-ttu-id="c69e9-129">您可以查詢個別樹狀結構中的任何節點來擷取 ARIMA 模型的方程式。</span><span class="sxs-lookup"><span data-stu-id="c69e9-129">You can retrieve the equation for an ARIMA model by querying any node in an individual tree.</span></span> <span data-ttu-id="c69e9-130">請記住，ARIMA 模型中的每一個樹狀結構都代表不同的週期性，而且如果有多個資料數列，每一個資料數列都將有它自己的一組週期性樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="c69e9-130">Remember that each tree within an ARIMA model represents a different periodicity, and if there are multiple data series, each data series will have its own set of periodicity trees.</span></span> <span data-ttu-id="c69e9-131">因此，若要擷取特定資料數列的方程式，您必須先識別此樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="c69e9-131">Therefore, to retrieve the equation for a specific data series you must identify the tree first.</span></span>  
  
 <span data-ttu-id="c69e9-132">例如，TA 前置詞告訴您此節點是 ARIMA 樹狀結構的一部分，而 TS 前置詞則用於 ARTXP 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="c69e9-132">For example, the TA prefix tells you that the node is part of an ARIMA tree, whereas the TS prefix is used for ARTXP trees.</span></span> <span data-ttu-id="c69e9-133">您可以尋找所有的 ARIMA 根樹狀結構，其方式是查詢具有 NODE_TYPE 值 27 之節點的模型內容。</span><span class="sxs-lookup"><span data-stu-id="c69e9-133">You can find all ARIMA root trees by querying the model content for nodes with a NODE_TYPE value of 27.</span></span> <span data-ttu-id="c69e9-134">您也可以使用 ATTRIBUTE_NAME 的值來尋找特定資料數列的 ARIMA 根節點。</span><span class="sxs-lookup"><span data-stu-id="c69e9-134">You can also use the value of ATTRIBUTE_NAME to find the ARIMA root node for a particular data series.</span></span> <span data-ttu-id="c69e9-135">此查詢範例會尋找代表在歐洲地區銷售之 R250 型號數量的 ARIMA 節點。</span><span class="sxs-lookup"><span data-stu-id="c69e9-135">This query example finds the ARIMA nodes that represent quantities sold of the R250 model in the Europe region.</span></span>  
  
```  
SELECT NODE_UNIQUE_NAME  
FROM Forecasting.CONTENT  
WHERE ATTRIBUTE_NAME = 'R250 Europe: Quantity"  
AND NODE_TYPE = 27  
```  
  
 <span data-ttu-id="c69e9-136">使用這個節點識別碼可以擷取有關此樹狀結構之 ARIMA 方程式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-136">By using this node ID, you can retrieve details about the ARIMA equation for this tree.</span></span> <span data-ttu-id="c69e9-137">下列 DMX 陳述式會擷取資料數列的簡短形式 ARIMA 方程式。</span><span class="sxs-lookup"><span data-stu-id="c69e9-137">The following DMX statement retrieves the short form of the ARIMA equation for the data series.</span></span> <span data-ttu-id="c69e9-138">此外，也會從巢狀資料表 NODE_DISTRIBUTION 擷取截距。</span><span class="sxs-lookup"><span data-stu-id="c69e9-138">It also retrieves the intercept from the nested table, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="c69e9-139">在此範例中，此方程式是藉由參考節點唯一識別碼 TA00000007 來取得。</span><span class="sxs-lookup"><span data-stu-id="c69e9-139">In this example, the equation is obtained by referencing the node unique ID TA00000007.</span></span> <span data-ttu-id="c69e9-140">但是，您可能必須使用不同的節點識別碼，而且可能會取得與模型稍微不同的結果。</span><span class="sxs-lookup"><span data-stu-id="c69e9-140">However, you may have to use a different node ID, and you may obtain slightly different results from your model.</span></span>  
  
```  
SELECT FLATTENED NODE_CAPTION as [Short equation],   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE   
FROM NODE_DISTRIBUTION) as t  
FROM Forecasting.CONTENT  
WHERE NODE_NAME = 'TA00000007'  
```  
  
 <span data-ttu-id="c69e9-141">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="c69e9-141">Example results:</span></span>  
  
|<span data-ttu-id="c69e9-142">簡短的方程式</span><span class="sxs-lookup"><span data-stu-id="c69e9-142">Short equation</span></span>|<span data-ttu-id="c69e9-143">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="c69e9-143">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="c69e9-144">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="c69e9-144">t.ATTRIBUTE_VALUE</span></span>|  
|--------------------|-----------------------|------------------------|  
|<span data-ttu-id="c69e9-145">ARIMA (2,0,7)x(1,0,2)(12)</span><span class="sxs-lookup"><span data-stu-id="c69e9-145">ARIMA (2,0,7)x(1,0,2)(12)</span></span>|<span data-ttu-id="c69e9-146">R250 Europe:Quantity(Intercept)</span><span class="sxs-lookup"><span data-stu-id="c69e9-146">R250 Europe:Quantity(Intercept)</span></span>|<span data-ttu-id="c69e9-147">15.24 ...。</span><span class="sxs-lookup"><span data-stu-id="c69e9-147">15.24....</span></span>|  
|<span data-ttu-id="c69e9-148">ARIMA (2,0,7)x(1,0,2)(12)</span><span class="sxs-lookup"><span data-stu-id="c69e9-148">ARIMA (2,0,7)x(1,0,2)(12)</span></span>|<span data-ttu-id="c69e9-149">R250 Europe:Quantity(Periodicity)</span><span class="sxs-lookup"><span data-stu-id="c69e9-149">R250 Europe:Quantity(Periodicity)</span></span>|<span data-ttu-id="c69e9-150">1</span><span class="sxs-lookup"><span data-stu-id="c69e9-150">1</span></span>|  
|<span data-ttu-id="c69e9-151">ARIMA (2,0,7)x(1,0,2)(12)</span><span class="sxs-lookup"><span data-stu-id="c69e9-151">ARIMA (2,0,7)x(1,0,2)(12)</span></span>|<span data-ttu-id="c69e9-152">R250 Europe:Quantity(Periodicity)</span><span class="sxs-lookup"><span data-stu-id="c69e9-152">R250 Europe:Quantity(Periodicity)</span></span>|<span data-ttu-id="c69e9-153">12</span><span class="sxs-lookup"><span data-stu-id="c69e9-153">12</span></span>|  
  
 <span data-ttu-id="c69e9-154">如需如何解譯這項資訊的詳細資訊，請參閱 [時間序列模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c69e9-154">For more information about how to interpret this information, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-3-retrieving-the-equation-for-an-artxp-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="c69e9-155">範例查詢 3：擷取 ARTXP 模型的方程式</span><span class="sxs-lookup"><span data-stu-id="c69e9-155">Sample Query 3: Retrieving the Equation for an ARTXP Model</span></span>  
 <span data-ttu-id="c69e9-156">如果是 ARTxp 模型，每一層的樹狀結構上會儲存不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="c69e9-156">For an ARTxp model, different information is stored at each level of the tree.</span></span> <span data-ttu-id="c69e9-157">如需 ARTxp 模型的結構及如何解譯方程式內資訊的詳細資訊，請參閱 [時間序列模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c69e9-157">For more information about the structure of an ARTxp model, and how to interpret the information in the equation, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="c69e9-158">下列 DMX 陳述式會擷取屬於 ARTxp 樹狀結構之一部分的資訊，該資訊代表在歐洲銷售之 R250 型號的數量。</span><span class="sxs-lookup"><span data-stu-id="c69e9-158">The following DMX statement retrieves information a part of the ARTxp tree that represents the quantity of sales for the R250 model in Europe.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c69e9-159">巢狀資料表資料行 VARIANCE 的名稱必須括在括號內，以便與同名的保留關鍵字區別。</span><span class="sxs-lookup"><span data-stu-id="c69e9-159">The name of the nested table column, VARIANCE, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span> <span data-ttu-id="c69e9-160">巢狀資料表資料行 PROBABILITY 和 SUPPORT 並未包括在其中，因為在大多數情況下，這兩者是空白的。</span><span class="sxs-lookup"><span data-stu-id="c69e9-160">The nested table columns, PROBABILITY and SUPPORT, are not included because they are blank in most cases.</span></span>  
  
```  
SELECT NODE_CAPTION as [Split information],   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE,  
   [VARIANCE]  
   FROM NODE_DISTRIBUTION) AS t  
FROM Forecasting.CONTENT  
WHERE NODE_ATTRIBUTE_NAME = 'R250 Europe:Quantity'  
AND NODE_TYPE = 15  
```  
  
 <span data-ttu-id="c69e9-161">如需如何解譯這項資訊的詳細資訊，請參閱 [時間序列模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c69e9-161">For more information about how to interpret this information, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="creating-predictions-on-a-time-series-model"></a><span data-ttu-id="c69e9-162">建立時間序列模型的預測</span><span class="sxs-lookup"><span data-stu-id="c69e9-162">Creating Predictions on a Time Series Model</span></span>  
 <span data-ttu-id="c69e9-163">從 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)]開始，您就可以將新的資料加入至時間序列模型，並自動將新的資料併入模型中。</span><span class="sxs-lookup"><span data-stu-id="c69e9-163">Beginning in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)], you can add new data to a time series model and automatically incorporate the new data into the model.</span></span> <span data-ttu-id="c69e9-164">您可以使用下列兩種方式的其中一種，將新的資料加入至時間序列採礦模型：</span><span class="sxs-lookup"><span data-stu-id="c69e9-164">You add new data to a time series mining model in one of two ways:</span></span>  
  
-   <span data-ttu-id="c69e9-165">使用 `PREDICTION JOIN` 將外部來源中的資料聯結至定型資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-165">Use a `PREDICTION JOIN` to join data in an external source to the training data.</span></span>  
  
-   <span data-ttu-id="c69e9-166">使用單一預測查詢，一次為資料提供一個配量。</span><span class="sxs-lookup"><span data-stu-id="c69e9-166">Use a singleton prediction query to provide data one slice at a time.</span></span> <span data-ttu-id="c69e9-167">如需如何建立單一預測查詢的詳細資訊，請參閱[資料採礦查詢介面](data-mining-query-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c69e9-167">For information about how to create a singleton prediction query, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
###  <a name="understanding-the-behavior-of-replace-and-extend-operations"></a><a name="bkmk_ReplaceExtend"></a> <span data-ttu-id="c69e9-168">了解取代和擴充作業的行為</span><span class="sxs-lookup"><span data-stu-id="c69e9-168">Understanding the Behavior of Replace and Extend Operations</span></span>  
 <span data-ttu-id="c69e9-169">當您將新的資料加入時間序列模型時，可以指定是要擴充還是取代定型資料：</span><span class="sxs-lookup"><span data-stu-id="c69e9-169">When you add new data to a time series model, you can specify whether to extend or replace the training data:</span></span>  
  
-   <span data-ttu-id="c69e9-170">**擴充：** 當您擴充資料數列時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會在現有定型資料的結尾加入新的資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-170">**Extend:** When you extend a data series, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] adds the new data at the end of the existing training data.</span></span> <span data-ttu-id="c69e9-171">定型案例的數目也會增加。</span><span class="sxs-lookup"><span data-stu-id="c69e9-171">The number of training cases also increases.</span></span>  
  
     <span data-ttu-id="c69e9-172">擴充此模型案例對於持續以新的資料更新模型非常實用。</span><span class="sxs-lookup"><span data-stu-id="c69e9-172">Extending the model cases is useful for continuously updating the model with new data.</span></span> <span data-ttu-id="c69e9-173">例如，如果您想要讓定型集隨著時間成長，只要擴充模型即可。</span><span class="sxs-lookup"><span data-stu-id="c69e9-173">For example, if you want to make the training set grow over time, you would simply extend the model.</span></span>  
  
     <span data-ttu-id="c69e9-174">若要擴充資料，您會在時間序列模型上建立 `PREDICTION JOIN`、指定新資料的來源，並使用 `EXTEND_MODEL_CASES` 引數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-174">To extend the data, you create a `PREDICTION JOIN` on a time series model, specify the source of the new data, and use the `EXTEND_MODEL_CASES` argument.</span></span>  
  
-   <span data-ttu-id="c69e9-175">**取代：** 當您取代資料數列中的資料時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會保留定型的模型，但是會使用新的資料來取代部分或所有現有的定型案例。</span><span class="sxs-lookup"><span data-stu-id="c69e9-175">**Replace:** When you replace the data in the data series, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] keeps the trained model, but uses the new data values to replace some or all of the existing training cases.</span></span> <span data-ttu-id="c69e9-176">因此，定型資料的大小絕對不會改變，但是案例本身則會持續被更新的資料所取代。</span><span class="sxs-lookup"><span data-stu-id="c69e9-176">Therefore, the size of the training data never changes, but the cases themselves are continually being replaced with newer data.</span></span> <span data-ttu-id="c69e9-177">如果您提供足夠的新資料，您可以使用完全新的序列來取代定型資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-177">If you supply enough new data, you can replace the training data with a completely new series.</span></span>  
  
     <span data-ttu-id="c69e9-178">當您想要定型一組案例上的模型，然後將該模型套用到不同的資料數列時，取代模型案例會非常實用。</span><span class="sxs-lookup"><span data-stu-id="c69e9-178">Replacing the model cases is useful when you want to train a model on one set of cases and then apply that model to a different data series.</span></span>  
  
     <span data-ttu-id="c69e9-179">若要取代資料，您會在時間序列模型上建立 `PREDICTION JOIN`、指定新資料的來源，並使用 `REPLACE_MODEL_CASES` 引數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-179">To replace the data, you create a `PREDICTION JOIN` on a time series model, specify the source of the new data, and use the `REPLACE_MODEL_CASES` argument.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c69e9-180">當您加入新的資料時，將無法做出歷程記錄預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-180">You cannot make historical predictions when you add new data.</span></span>  
  
 <span data-ttu-id="c69e9-181">不論您要擴充還是取代定型資料，預測一定會開始於原始定型集結束的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="c69e9-181">Regardless of whether you extend or replace the training data, predictions always begin at the time stamp that ends the original training set.</span></span> <span data-ttu-id="c69e9-182">換句話說，如果您的新資料包含 n 個時間配量，而且您要求時間步驟 1 到 n 的預測，則預測將會符合新資料的相同期間，而不會取得新的預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-182">In other words, if your new data contains n time slices, and you request predictions for time steps 1 through n, the predictions will coincide with the same period as the new data, and you will not get any new predictions.</span></span>  
  
 <span data-ttu-id="c69e9-183">若要取得未與新資料重疊之期間的新預測，您必須在時間配量 n+1 上開始預測，或是確定您有要求其他的時間配量。</span><span class="sxs-lookup"><span data-stu-id="c69e9-183">To get new predictions for time periods that do not overlap with the new data, you must either start predictions at the time slice n+1, or make sure that you request additional time slices.</span></span>  
  
 <span data-ttu-id="c69e9-184">例如，假設現有的模型有六個月的資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-184">For example, assume that the existing model has six months' worth of data.</span></span> <span data-ttu-id="c69e9-185">您想要加入最後三個月的銷售數字來擴充這個模型，</span><span class="sxs-lookup"><span data-stu-id="c69e9-185">You want to extend this model by adding the sales figures from the last three months.</span></span> <span data-ttu-id="c69e9-186">同時，您想要對未來三個月做出預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-186">At the same time, you want to make a prediction about the next three months.</span></span> <span data-ttu-id="c69e9-187">如果加入新的資料時只要取得新的預測，請將起點指定為時間配量 4，並將結束點指定為時間配量 7。</span><span class="sxs-lookup"><span data-stu-id="c69e9-187">To obtain only the new predictions when you add the new data, specify the starting point as time slice 4, and the ending point as time slice 7.</span></span> <span data-ttu-id="c69e9-188">您一共可以要求六個預測，但是前三個預測的時間配量會與剛加入的新資料重疊。</span><span class="sxs-lookup"><span data-stu-id="c69e9-188">You could also request a total of six predictions, but the time slices for the first three would overlap with the new data just added.</span></span>  
  
 <span data-ttu-id="c69e9-189">如需查詢範例以及使用和之語法的詳細 `REPLACE_MODEL_CASES` 資訊 `EXTEND_MODEL_CASES` ，請參閱[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)。</span><span class="sxs-lookup"><span data-stu-id="c69e9-189">For query examples and more information about the syntax for using `REPLACE_MODEL_CASES` and `EXTEND_MODEL_CASES`, see [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx).</span></span>  
  
###  <a name="making-predictions-with-extend_model_cases"></a><a name="bkmk_EXTEND"></a> <span data-ttu-id="c69e9-190">使用 EXTEND_MODEL_CASES 做出預測</span><span class="sxs-lookup"><span data-stu-id="c69e9-190">Making Predictions with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="c69e9-191">預測行為會因為您要擴充還是取代模型案例而異。</span><span class="sxs-lookup"><span data-stu-id="c69e9-191">Prediction behavior differs depending on whether you extend or replace the model cases.</span></span> <span data-ttu-id="c69e9-192">當您擴充模型時，新的資料會附加到序列的結尾，而且定型集的大小會增加。</span><span class="sxs-lookup"><span data-stu-id="c69e9-192">When you extend a model, the new data is attached to the end of the series and the size of the training set increases.</span></span> <span data-ttu-id="c69e9-193">但是，用於預測查詢的時間配量一定會開始於原始序列的結尾。</span><span class="sxs-lookup"><span data-stu-id="c69e9-193">However, the time slices used for prediction queries always start at the end of the original series.</span></span> <span data-ttu-id="c69e9-194">因此，如果您加入三個新的資料點，並要求六個預測，則傳回的前三個預測會與新的資料重疊。</span><span class="sxs-lookup"><span data-stu-id="c69e9-194">Therefore, if you add three new data points and request six predictions, the first three predictions returned overlap with the new data.</span></span> <span data-ttu-id="c69e9-195">在此情況下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會傳回實際的新資料點，而不是做出預測，直到所有新的資料點都用完為止。</span><span class="sxs-lookup"><span data-stu-id="c69e9-195">In this case, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns the actual new data points instead of making a prediction, until all the new data points are used up.</span></span> <span data-ttu-id="c69e9-196">然後， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會根據複合系列來做出預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-196">Then, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] makes predictions based on the composite series.</span></span>  
  
 <span data-ttu-id="c69e9-197">這個行為可讓您加入新的資料，然後在預測圖中顯示實際的銷售數字，而不是查看投影。</span><span class="sxs-lookup"><span data-stu-id="c69e9-197">This behavior lets you add new data, and then show your actual sales figures in the prediction chart, instead of seeing projections.</span></span>  
  
 <span data-ttu-id="c69e9-198">例如，若要加入三個新資料點，並做出三個新的預測，您會執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="c69e9-198">For example, to add three new data points and make three new predictions, you would do the following:</span></span>  
  
-   <span data-ttu-id="c69e9-199">在時間序列模型上建立 `PREDICTION JOIN`，並指定這三個月之新資料的來源。</span><span class="sxs-lookup"><span data-stu-id="c69e9-199">Create a `PREDICTION JOIN` on a time series model, and specify the source of three months' of new data.</span></span>  
  
-   <span data-ttu-id="c69e9-200">要求六個時間配量的預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-200">Request predictions for six time slices.</span></span> <span data-ttu-id="c69e9-201">若要這樣做，請指定 6 個時間配量，其中起點是時間配量 1，而結束點則是時間配量 7。</span><span class="sxs-lookup"><span data-stu-id="c69e9-201">To do this, specify 6 time slices, where the starting point is time slice 1, and the ending point is time slice 7.</span></span> <span data-ttu-id="c69e9-202">這個情況只適用於 EXTEND_MODEL_CASES。</span><span class="sxs-lookup"><span data-stu-id="c69e9-202">This is true only for EXTEND_MODEL_CASES.</span></span>  
  
-   <span data-ttu-id="c69e9-203">如果只要取得新的預測，請將起點指定為時間配量 4，並將結束點指定為時間配量 7。</span><span class="sxs-lookup"><span data-stu-id="c69e9-203">To get only the new predictions, you specify the starting point as 4 and the ending point as 7.</span></span>  
  
-   <span data-ttu-id="c69e9-204">您必須使用 `EXTEND_MODEL_CASES` 引數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-204">You must use the argument `EXTEND_MODEL_CASES`.</span></span>  
  
     <span data-ttu-id="c69e9-205">這樣會傳回前三個時間配量的實際銷售數字，並針對接下來三個時間配量傳回根據此擴充模型的預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-205">The actual sales figures are returned for the first three time slices, and predictions based on the extended model are returned for the next three time slices.</span></span>  
  
###  <a name="making-predictions-with-replace_model_cases"></a><a name="bkmk_REPLACE"></a> <span data-ttu-id="c69e9-206">使用 REPLACE_MODEL_CASES 做出預測</span><span class="sxs-lookup"><span data-stu-id="c69e9-206">Making Predictions with REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="c69e9-207">當您取代模型中的案例時，此模型的大小會維持相同，但是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會取代此模型中的個別案例。</span><span class="sxs-lookup"><span data-stu-id="c69e9-207">When you replace the cases in a model, the size of the model stays the same but [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] replaces the individual cases in the model.</span></span> <span data-ttu-id="c69e9-208">在交叉預測以及將訓練資料集維持一致大小非常重要的案例下，這種作法會很有用。</span><span class="sxs-lookup"><span data-stu-id="c69e9-208">This is useful for cross-prediction and scenarios in which maintaining the training data set at a consistent size is important.</span></span>  
  
 <span data-ttu-id="c69e9-209">例如，假設其中一個存放區的銷售資料不足。</span><span class="sxs-lookup"><span data-stu-id="c69e9-209">For example, one of your stores has insufficient sales data.</span></span> <span data-ttu-id="c69e9-210">您可以建立一般模型，其方式是將特定區域中所有存放區的銷售量加以平均，然後定型模型。</span><span class="sxs-lookup"><span data-stu-id="c69e9-210">You could create a general model by averaging sales for all stores in a particular region and then training a model.</span></span> <span data-ttu-id="c69e9-211">然後，若要在沒有足夠銷售資料的情況下為存放區做出預測，您可以只針對該存放區的新銷售資料建立 `PREDICTION JOIN`。</span><span class="sxs-lookup"><span data-stu-id="c69e9-211">Then, to make predictions for the store without sufficient sales data, you create a `PREDICTION JOIN` on the new sales data for just that store.</span></span> <span data-ttu-id="c69e9-212">當您這樣做時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會保留衍生自區域模型的模式，但是會使用個別存放區中的資料來取代現有的定型案例。</span><span class="sxs-lookup"><span data-stu-id="c69e9-212">When you do this, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] keeps the patterns derived from the regional model, but replaces the existing training cases with the data from the individual store.</span></span> <span data-ttu-id="c69e9-213">因此，您的預測值將會比較接近於個別存放區的趨勢線。</span><span class="sxs-lookup"><span data-stu-id="c69e9-213">As a result, your prediction values will be closer to the trend lines for the individual store.</span></span>  
  
 <span data-ttu-id="c69e9-214">當您使用 `REPLACE_MODEL_CASES` 引數時，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會持續將新的案例加入案例集的結尾，並從此案例集的開頭刪除對應的數字。</span><span class="sxs-lookup"><span data-stu-id="c69e9-214">When you use the `REPLACE_MODEL_CASES` argument, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] continually adds new cases to the end of the case set and deletes a corresponding number from the beginning of the case set.</span></span> <span data-ttu-id="c69e9-215">如果您加入的資料多於原始定型集中的資料， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會捨棄最早的資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-215">If you add more new data than was in the original training set, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] discards the earliest data.</span></span> <span data-ttu-id="c69e9-216">如果您提供足夠的新值，可以根據完全新的資料來做出預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-216">If you supply sufficient new values, the predictions can be based on completely new data.</span></span>  
  
 <span data-ttu-id="c69e9-217">例如，假設您在包含 1000 個資料列的案例資料集上定型您的模型，</span><span class="sxs-lookup"><span data-stu-id="c69e9-217">For example, you trained your model on a case data set that contained 1000 rows.</span></span> <span data-ttu-id="c69e9-218">然後您加入 100 列的新資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-218">You then add 100 rows of new data.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="c69e9-219">會從定型集中卸除前 100 個資料列，並將 100 列的新資料加入一共 1000 個資料列的集合結尾。</span><span class="sxs-lookup"><span data-stu-id="c69e9-219">drops the first 100 rows from the training set and adds the 100 rows of new data to the end of the set for a total of 1000 rows.</span></span> <span data-ttu-id="c69e9-220">如果您加入 1100 列的新資料，只會使用最近的 1000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="c69e9-220">If you add 1100 rows of new data, only the most recent 1000 rows are used.</span></span>  
  
 <span data-ttu-id="c69e9-221">以下是另一個範例。</span><span class="sxs-lookup"><span data-stu-id="c69e9-221">Here is another example.</span></span> <span data-ttu-id="c69e9-222">若要加入三個新月份的資料，並做出三個新的預測，您會執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="c69e9-222">To add three new month's worth of data and make three new predictions, you would do the following actions:</span></span>  
  
-   <span data-ttu-id="c69e9-223">在時間序列模型上建立 `PREDICTION JOIN`，並使用 `REPLACE_MODEL_CASE` 引數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-223">Create a `PREDICTION JOIN` on a time series model and use the `REPLACE_MODEL_CASE` argument.</span></span>  
  
-   <span data-ttu-id="c69e9-224">指定三個月新資料的來源。</span><span class="sxs-lookup"><span data-stu-id="c69e9-224">Specify the source of three months' of new data.</span></span> <span data-ttu-id="c69e9-225">這些資料可能與原始定型資料的來源完全不同。</span><span class="sxs-lookup"><span data-stu-id="c69e9-225">This data might be from a completely different source than the original training data.</span></span>  
  
-   <span data-ttu-id="c69e9-226">要求六個時間配量的預測。</span><span class="sxs-lookup"><span data-stu-id="c69e9-226">Request predictions for six time slices.</span></span> <span data-ttu-id="c69e9-227">若要這樣做，請指定 6 個時間配量，或是將起點指定為時間配量 1，而將結束點指定為時間配量 7。</span><span class="sxs-lookup"><span data-stu-id="c69e9-227">To do this, specify 6 time slices, or specify the starting point as time slice 1, and the ending point as time slice 7.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c69e9-228">與 `EXTEND_MODEL_CASES` 不同的是，您無法傳回與加入的輸入資料相同的值。</span><span class="sxs-lookup"><span data-stu-id="c69e9-228">Unlike `EXTEND_MODEL_CASES`, you cannot return the same values that you added as input data.</span></span> <span data-ttu-id="c69e9-229">傳回的所有六個值都是根據更新模型所做的預測，其中包含舊的和新的資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-229">All six values returned are predictions that are based on the updated model, which includes both old and new data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c69e9-230">從 REPLACE_MODEL_CASES 的時間戳記 1 開始，您會根據新的資料取得新的預測，新的資料會取代舊的訓練資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-230">With REPLACE_MODEL_CASES, starting at timestamp 1 you get new predictions based on the new data, which replaces the old training data.</span></span>  
  
 <span data-ttu-id="c69e9-231">如需查詢範例以及使用和之語法的詳細 `REPLACE_MODEL_CASES` 資訊 `EXTEND_MODEL_CASES` ，請參閱[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)。</span><span class="sxs-lookup"><span data-stu-id="c69e9-231">For query examples and more information about the syntax for using `REPLACE_MODEL_CASES` and `EXTEND_MODEL_CASES`, see [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx).</span></span>  
  
###  <a name="missing-value-substitution-in-time-series-models"></a><a name="bkmk_MissingValues"></a><span data-ttu-id="c69e9-232">時間序列模型中的遺漏值替代</span><span class="sxs-lookup"><span data-stu-id="c69e9-232">Missing Value Substitution in Time Series Models</span></span>  
 <span data-ttu-id="c69e9-233">當您使用 `PREDICTION JOIN` 陳述式將新的資料加入時間序列模型時，新的資料集不能有任何遺漏值。</span><span class="sxs-lookup"><span data-stu-id="c69e9-233">When you add new data to a time series model by using a `PREDICTION JOIN` statement, the new dataset cannot have any missing values.</span></span> <span data-ttu-id="c69e9-234">如果有任何數列不完整，此模型必須提供遺漏的值，其方式是使用 null、數值平均、特定的數值平均或預測值。</span><span class="sxs-lookup"><span data-stu-id="c69e9-234">If any series is incomplete, the model must supply the missing values by using either a null, a numeric means, a specific numeric mean, or a predicted value.</span></span> <span data-ttu-id="c69e9-235">如果您指定 `EXTEND_MODEL_CASES`，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會使用根據原始模型的預測來取代遺漏值。</span><span class="sxs-lookup"><span data-stu-id="c69e9-235">If you specify `EXTEND_MODEL_CASES`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] replaces the missing values with predictions based on the original model.</span></span> <span data-ttu-id="c69e9-236">如果您使用 `REPLACE_MODEL_CASES` ，會以 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 您在*MISSING_VALUE_SUBSTITUTION*參數中指定的值來取代遺漏值。</span><span class="sxs-lookup"><span data-stu-id="c69e9-236">If you use `REPLACE_MODEL_CASES`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] replaces the missing values with the value that you specify in the *MISSING_VALUE_SUBSTITUTION* parameter.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="c69e9-237">預測函數的清單</span><span class="sxs-lookup"><span data-stu-id="c69e9-237">List of Prediction Functions</span></span>  
 <span data-ttu-id="c69e9-238">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-238">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="c69e9-239">不過， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法支援下表所列出的其他函數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-239">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm supports the additional functions, listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c69e9-240">預測函數</span><span class="sxs-lookup"><span data-stu-id="c69e9-240">Prediction Function</span></span>|<span data-ttu-id="c69e9-241">使用量</span><span class="sxs-lookup"><span data-stu-id="c69e9-241">Usage</span></span>|  
|[<span data-ttu-id="c69e9-242">Lag &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c69e9-242">Lag &#40;DMX&#41;</span></span>](/sql/dmx/lag-dmx)|<span data-ttu-id="c69e9-243">傳回目前案例的日期與定型集的最後日期之間的時間配量數目。</span><span class="sxs-lookup"><span data-stu-id="c69e9-243">Returns a number of time slices between the date of the current case and the last date of the training set.</span></span><br /><br /> <span data-ttu-id="c69e9-244">這個函數的典型用法就是用來識別最近的定型案例，好讓您可以擷取有關案例的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-244">A typical use of this function is to identify recent training cases so that you can retrieve detailed data about the cases.</span></span>|  
|[<span data-ttu-id="c69e9-245">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c69e9-245">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="c69e9-246">傳回指定之可預測資料行的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="c69e9-246">Returns the node ID for the specified predictable column.</span></span><br /><br /> <span data-ttu-id="c69e9-247">這個函數的典型用法就是用來識別產生特定預測值的節點，好讓您可以檢閱與此節點有關的案例，或擷取方程式和其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c69e9-247">A typical use of this function is to identify the node that generated a particular predicted value so that you can review the cases associated with the node, or retrieve the equation and other details.</span></span>|  
|[<span data-ttu-id="c69e9-248">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c69e9-248">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="c69e9-249">傳回指定之可預測資料行中預測的標準差。</span><span class="sxs-lookup"><span data-stu-id="c69e9-249">Returns the standard deviation of the predictions in the specified predictable column.</span></span><br /><br /> <span data-ttu-id="c69e9-250">此函數會取代 INCLUDE_STATISTICS 引數，時間序列模型不支援這個引數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-250">This function replaces the INCLUDE_STATISTICS argument, which is not supported for time series models.</span></span>|  
|[<span data-ttu-id="c69e9-251">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c69e9-251">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="c69e9-252">傳回指定之可預測資料行中預測的變異數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-252">Returns the variance of the predictions for the specified predictable column.</span></span><br /><br /> <span data-ttu-id="c69e9-253">此函數會取代 INCLUDE_STATISTICS 引數，時間序列模型不支援這個引數。</span><span class="sxs-lookup"><span data-stu-id="c69e9-253">This function replaces the INCLUDE_STATISTICS argument, which is not supported for time series models.</span></span>|  
|[<span data-ttu-id="c69e9-254">PredictTimeSeries &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c69e9-254">PredictTimeSeries &#40;DMX&#41;</span></span>](/sql/dmx/predicttimeseries-dmx)|<span data-ttu-id="c69e9-255">傳回時間序列的預測記錄值或未來預測值。</span><span class="sxs-lookup"><span data-stu-id="c69e9-255">Returns predicted historical values or future predicted values for a time series.</span></span><br /><br /> <span data-ttu-id="c69e9-256">您也可以使用一般預測函數 [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) 來查詢時間序列模型。</span><span class="sxs-lookup"><span data-stu-id="c69e9-256">You can also query time series models by using the general prediction function, [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx).</span></span>|  
  
 <span data-ttu-id="c69e9-257">如需所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法通用函數的清單，請參閱[一般預測函數 &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="c69e9-257">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="c69e9-258">如需特定函數的語法，請參閱[資料採礦延伸模組 &#40;DMX&#41; 函數參考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="c69e9-258">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69e9-259">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c69e9-259">See Also</span></span>  
 <span data-ttu-id="c69e9-260">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="c69e9-260">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="c69e9-261">[Microsoft 時間序列演算法](microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c69e9-261">[Microsoft Time Series Algorithm](microsoft-time-series-algorithm.md) </span></span>  
 <span data-ttu-id="c69e9-262">[Microsoft 時間序列演算法技術參考](microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c69e9-262">[Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="c69e9-263">時間序列模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="c69e9-263">Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
