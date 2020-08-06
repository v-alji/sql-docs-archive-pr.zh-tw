---
title: 線性回歸模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- content queries [DMX]
ms.assetid: fd3cf312-57a1-44b6-b772-fce6fc1c26d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02d4b7309d7b5ea3d6295089f0fb2e778b1c9b4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606511"
---
# <a name="linear-regression-model-query-examples"></a><span data-ttu-id="28f7d-102">線性迴歸模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="28f7d-102">Linear Regression Model Query Examples</span></span>
  <span data-ttu-id="28f7d-103">當您針對資料採礦模型建立查詢時，可以建立內容查詢來提供有關分析期間所發現之模式的詳細資料，或是建立預測查詢來使用模型中的模式，為新的資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="28f7d-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="28f7d-104">例如，內容查詢可能會提供有關迴歸公式的其他詳細資料，而預測查詢則會告訴您新資料點是否符合模型。</span><span class="sxs-lookup"><span data-stu-id="28f7d-104">For example, a content query might provide additional details about the regression formula, while a prediction query might tell you if a new data point fits the model.</span></span> <span data-ttu-id="28f7d-105">您也可以使用查詢來擷取有關模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="28f7d-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="28f7d-106">本節說明如何針對以 Microsoft 線性迴歸演算法為基礎的模型來建立查詢。</span><span class="sxs-lookup"><span data-stu-id="28f7d-106">This section explains how to create queries for models that are based on the Microsoft Linear Regression algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="28f7d-107">線性迴歸是以 Microsoft 決策樹演算法的特殊案例為基礎，因此有許多相似處，而且使用連續可預測屬性的某些決策樹模型可以包含迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="28f7d-107">Because linear regression is based on a special case of the Microsoft Decision Trees algorithm, there are many similarities, and some decision tree models that use continuous predictable attributes can contain regression formulas.</span></span> <span data-ttu-id="28f7d-108">如需詳細資訊，請參閱 [Microsoft 決策樹演算法技術參考](microsoft-decision-trees-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="28f7d-108">For more information, see [Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="28f7d-109">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="28f7d-109">**Content queries**</span></span>  
  
 [<span data-ttu-id="28f7d-110">使用資料採礦結構描述資料列集來判斷用於模型的參數</span><span class="sxs-lookup"><span data-stu-id="28f7d-110">Using the Data Mining Schema Rowset to determine parameters used for a model</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="28f7d-111">使用 DMX 傳回模型的迴歸公式</span><span class="sxs-lookup"><span data-stu-id="28f7d-111">Using DMX to return the regression formula for the model</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="28f7d-112">僅傳回模型的係數</span><span class="sxs-lookup"><span data-stu-id="28f7d-112">Returning only the coefficient for the model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="28f7d-113">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="28f7d-113">**Prediction queries**</span></span>  
  
 [<span data-ttu-id="28f7d-114">使用單一查詢預測成果</span><span class="sxs-lookup"><span data-stu-id="28f7d-114">Predicting income using a singleton query</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="28f7d-115">搭配迴歸模型使用預測函數</span><span class="sxs-lookup"><span data-stu-id="28f7d-115">Using prediction functions with a regression model</span></span>](#bkmk_Query5)  
  
##  <a name="finding-information-about-the-linear-regression-model"></a><a name="bkmk_top"></a> <span data-ttu-id="28f7d-116">尋找有關線性迴歸模型的資訊</span><span class="sxs-lookup"><span data-stu-id="28f7d-116">Finding Information about the Linear Regression Model</span></span>  
 <span data-ttu-id="28f7d-117">線性迴歸模型的結構相當簡單：採礦模型將資料表示為定義迴歸公式的單一節點。</span><span class="sxs-lookup"><span data-stu-id="28f7d-117">The structure of a linear regression model is extremely simple: the mining model represents the data as a single node, which defines the regression formula.</span></span> <span data-ttu-id="28f7d-118">如需詳細資訊，請參閱 [羅吉斯迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="28f7d-118">For more information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
 [<span data-ttu-id="28f7d-119">回到頁首</span><span class="sxs-lookup"><span data-stu-id="28f7d-119">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-determine-parameters-used-for-a-model"></a><a name="bkmk_Query1"></a> <span data-ttu-id="28f7d-120">範例查詢 1：使用資料採礦結構描述資料列集來判斷用於模型的參數</span><span class="sxs-lookup"><span data-stu-id="28f7d-120">Sample Query 1: Using the Data Mining Schema Rowset to Determine Parameters Used for a Model</span></span>  
 <span data-ttu-id="28f7d-121">您可以查詢資料採礦結構描述資料列集來尋找有關模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="28f7d-121">By querying the data mining schema rowset, you can find metadata about the model.</span></span> <span data-ttu-id="28f7d-122">這可能包括建立模型的時間、上次處理模型的時間、模型所依據之採礦結構的名稱，以及指定為可預測屬性之資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="28f7d-122">This might include when the model was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column designated as the predictable attribute.</span></span> <span data-ttu-id="28f7d-123">您也可以傳回初次建立此模型時所使用的參數。</span><span class="sxs-lookup"><span data-stu-id="28f7d-123">You can also return the parameters that were used when the model was first created.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_PredictIncome'  
```  
  
 <span data-ttu-id="28f7d-124">範例結果：</span><span class="sxs-lookup"><span data-stu-id="28f7d-124">Sample results:</span></span>  
  
|<span data-ttu-id="28f7d-125">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="28f7d-125">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="28f7d-126">COMPLEXITY_PENALTY=0.9,</span><span class="sxs-lookup"><span data-stu-id="28f7d-126">COMPLEXITY_PENALTY=0.9,</span></span><br /><br /> <span data-ttu-id="28f7d-127">MAXIMUM_INPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="28f7d-127">MAXIMUM_INPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="28f7d-128">MAXIMUM_OUTPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="28f7d-128">MAXIMUM_OUTPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="28f7d-129">MINIMUM_SUPPORT=10,</span><span class="sxs-lookup"><span data-stu-id="28f7d-129">MINIMUM_SUPPORT=10,</span></span><br /><br /> <span data-ttu-id="28f7d-130">SCORE_METHOD=4,</span><span class="sxs-lookup"><span data-stu-id="28f7d-130">SCORE_METHOD=4,</span></span><br /><br /> <span data-ttu-id="28f7d-131">SPLIT_METHOD=3,</span><span class="sxs-lookup"><span data-stu-id="28f7d-131">SPLIT_METHOD=3,</span></span><br /><br /> <span data-ttu-id="28f7d-132">FORCE_REGRESSOR=</span><span class="sxs-lookup"><span data-stu-id="28f7d-132">FORCE_REGRESSOR=</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="28f7d-133">參數設定「`FORCE_REGRESSOR =` 」表示目前用於 FORCE_REGRESSOR 參數的值為 Null 值。</span><span class="sxs-lookup"><span data-stu-id="28f7d-133">The parameter setting, "`FORCE_REGRESSOR =` ", indicates that the current value for the FORCE_REGRESSOR parameter is null.</span></span>  
  
 [<span data-ttu-id="28f7d-134">回到頁首</span><span class="sxs-lookup"><span data-stu-id="28f7d-134">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-2-retrieving-the-regression-formula-for-the-model"></a><a name="bkmk_Query2"></a> <span data-ttu-id="28f7d-135">範例查詢 2：擷取模型的迴歸公式</span><span class="sxs-lookup"><span data-stu-id="28f7d-135">Sample Query 2: Retrieving the Regression Formula for the Model</span></span>  
 <span data-ttu-id="28f7d-136">下列查詢會針對利用＜ [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)＞中所使用之相同目標郵寄資料來源所建立的線性迴歸模型，傳回採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="28f7d-136">The following query returns the mining model content for a linear regression model that was built by using the same Targeted Mailing data source that was used in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="28f7d-137">此模型會根據年齡預測客戶收入。</span><span class="sxs-lookup"><span data-stu-id="28f7d-137">This model predicts customer income based on age.</span></span>  
  
 <span data-ttu-id="28f7d-138">查詢會傳回包含迴歸公式之節點的內容。</span><span class="sxs-lookup"><span data-stu-id="28f7d-138">The query returns the contents of the node that contains the regression formula.</span></span> <span data-ttu-id="28f7d-139">每個變數和係數都儲存在 NODE_DISTRIBUTION 資料表的個別資料列中。</span><span class="sxs-lookup"><span data-stu-id="28f7d-139">Each variable and coefficient is stored in a separate row of the nested NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="28f7d-140">如果您要檢視完整的迴歸公式，使用 [Microsoft 樹狀檢視器](browse-a-model-using-the-microsoft-tree-viewer.md)，按一下 **(All)** 節點，然後開啟 **[採礦圖例]**。</span><span class="sxs-lookup"><span data-stu-id="28f7d-140">If you want to view the complete regression formula, use the [Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md), click the **(All)** node, and open the **Mining Legend**.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION as t  
FROM LR_PredictIncome.CONTENT  
```  
  
> [!NOTE]  
>  <span data-ttu-id="28f7d-141">如果您使用 `SELECT <column name> from NODE_DISTRIBUTION`這類的查詢來參考巢狀資料表的個別資料行，某些資料行 (例如， **SUPPORT** 或 **PROBABILITY**) 必須括在括號內，以便與同名的保留關鍵字區別。</span><span class="sxs-lookup"><span data-stu-id="28f7d-141">If you reference individual columns of the nested table by using a query such as `SELECT <column name> from NODE_DISTRIBUTION`, some columns, such as **SUPPORT** or **PROBABILITY**, must be enclosed in brackets to distinguish them from reserved keywords of the same name.</span></span>  
  
 <span data-ttu-id="28f7d-142">預期的結果：</span><span class="sxs-lookup"><span data-stu-id="28f7d-142">Expected results:</span></span>  
  
|<span data-ttu-id="28f7d-143">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="28f7d-143">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="28f7d-144">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="28f7d-144">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="28f7d-145">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="28f7d-145">t.SUPPORT</span></span>|<span data-ttu-id="28f7d-146">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="28f7d-146">t.PROBABILITY</span></span>|<span data-ttu-id="28f7d-147">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="28f7d-147">t.VARIANCE</span></span>|<span data-ttu-id="28f7d-148">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="28f7d-148">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="28f7d-149">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="28f7d-149">Yearly Income</span></span>|<span data-ttu-id="28f7d-150">Missing</span><span class="sxs-lookup"><span data-stu-id="28f7d-150">Missing</span></span>|<span data-ttu-id="28f7d-151">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-151">0</span></span>|<span data-ttu-id="28f7d-152">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="28f7d-152">0.000457142857142857</span></span>|<span data-ttu-id="28f7d-153">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-153">0</span></span>|<span data-ttu-id="28f7d-154">1</span><span class="sxs-lookup"><span data-stu-id="28f7d-154">1</span></span>|  
|<span data-ttu-id="28f7d-155">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="28f7d-155">Yearly Income</span></span>|<span data-ttu-id="28f7d-156">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="28f7d-156">57220.8876687257</span></span>|<span data-ttu-id="28f7d-157">17484</span><span class="sxs-lookup"><span data-stu-id="28f7d-157">17484</span></span>|<span data-ttu-id="28f7d-158">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="28f7d-158">0.999542857142857</span></span>|<span data-ttu-id="28f7d-159">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="28f7d-159">1041275619.52776</span></span>|<span data-ttu-id="28f7d-160">3</span><span class="sxs-lookup"><span data-stu-id="28f7d-160">3</span></span>|  
|<span data-ttu-id="28f7d-161">年齡</span><span class="sxs-lookup"><span data-stu-id="28f7d-161">Age</span></span>|<span data-ttu-id="28f7d-162">471.687717702463</span><span class="sxs-lookup"><span data-stu-id="28f7d-162">471.687717702463</span></span>|<span data-ttu-id="28f7d-163">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-163">0</span></span>|<span data-ttu-id="28f7d-164">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-164">0</span></span>|<span data-ttu-id="28f7d-165">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="28f7d-165">126.969442359327</span></span>|<span data-ttu-id="28f7d-166">7</span><span class="sxs-lookup"><span data-stu-id="28f7d-166">7</span></span>|  
|<span data-ttu-id="28f7d-167">年齡</span><span class="sxs-lookup"><span data-stu-id="28f7d-167">Age</span></span>|<span data-ttu-id="28f7d-168">234.680904692439</span><span class="sxs-lookup"><span data-stu-id="28f7d-168">234.680904692439</span></span>|<span data-ttu-id="28f7d-169">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-169">0</span></span>|<span data-ttu-id="28f7d-170">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-170">0</span></span>|<span data-ttu-id="28f7d-171">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-171">0</span></span>|<span data-ttu-id="28f7d-172">8</span><span class="sxs-lookup"><span data-stu-id="28f7d-172">8</span></span>|  
|<span data-ttu-id="28f7d-173">年齡</span><span class="sxs-lookup"><span data-stu-id="28f7d-173">Age</span></span>|<span data-ttu-id="28f7d-174">45.4269617936399</span><span class="sxs-lookup"><span data-stu-id="28f7d-174">45.4269617936399</span></span>|<span data-ttu-id="28f7d-175">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-175">0</span></span>|<span data-ttu-id="28f7d-176">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-176">0</span></span>|<span data-ttu-id="28f7d-177">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="28f7d-177">126.969442359327</span></span>|<span data-ttu-id="28f7d-178">9</span><span class="sxs-lookup"><span data-stu-id="28f7d-178">9</span></span>|  
||<span data-ttu-id="28f7d-179">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="28f7d-179">35793.5477381267</span></span>|<span data-ttu-id="28f7d-180">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-180">0</span></span>|<span data-ttu-id="28f7d-181">0</span><span class="sxs-lookup"><span data-stu-id="28f7d-181">0</span></span>|<span data-ttu-id="28f7d-182">1012968919.28372</span><span class="sxs-lookup"><span data-stu-id="28f7d-182">1012968919.28372</span></span>|<span data-ttu-id="28f7d-183">11</span><span class="sxs-lookup"><span data-stu-id="28f7d-183">11</span></span>|  
  
 <span data-ttu-id="28f7d-184">相較之下，在 **[採礦圖例]** 中，迴歸公式顯示如下：</span><span class="sxs-lookup"><span data-stu-id="28f7d-184">In comparison, in the **Mining Legend**, the regression formula appears as follows:</span></span>  
  
 <span data-ttu-id="28f7d-185">Yearly Income = 57,220.919 + 471.688 \* (Age - 45.427)</span><span class="sxs-lookup"><span data-stu-id="28f7d-185">Yearly Income = 57,220.919 + 471.688 \* (Age - 45.427)</span></span>  
  
 <span data-ttu-id="28f7d-186">您可以發現，在 **[採礦圖例]** 中，有些數字會被捨入，不過，NODE_DISTRIBUTION 資料表和 **[採礦圖例]** 基本上包含相同的值。</span><span class="sxs-lookup"><span data-stu-id="28f7d-186">You can see that in the **Mining Legend**, some numbers are rounded; however, the NODE_DISTRIBUTION table and the **Mining Legend** essentially contain the same values.</span></span>  
  
 <span data-ttu-id="28f7d-187">VALUETYPE 資料行中的值會告訴您每個資料列中包含哪種資訊；如果您要以程式設計方式處理結果，哪個比較實用。</span><span class="sxs-lookup"><span data-stu-id="28f7d-187">The values in the VALUETYPE column tell you what kind of information is contained in each row, which is useful if you are processing the results programmatically.</span></span> <span data-ttu-id="28f7d-188">下表顯示針對線性迴歸公式輸出的值類型。</span><span class="sxs-lookup"><span data-stu-id="28f7d-188">The following table shows the value types that are output for a linear regression formula.</span></span>  
  
|<span data-ttu-id="28f7d-189">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="28f7d-189">VALUETYPE</span></span>|  
|---------------|  
|<span data-ttu-id="28f7d-190">1 (遺漏)</span><span class="sxs-lookup"><span data-stu-id="28f7d-190">1 (Missing)</span></span>|  
|<span data-ttu-id="28f7d-191">3 (連續)</span><span class="sxs-lookup"><span data-stu-id="28f7d-191">3 (Continuous)</span></span>|  
|<span data-ttu-id="28f7d-192">7 (係數)</span><span class="sxs-lookup"><span data-stu-id="28f7d-192">7 (Coefficient)</span></span>|  
|<span data-ttu-id="28f7d-193">8 (得分)</span><span class="sxs-lookup"><span data-stu-id="28f7d-193">8 (Score Gain)</span></span>|  
|<span data-ttu-id="28f7d-194">9 (統計資料)</span><span class="sxs-lookup"><span data-stu-id="28f7d-194">9 (Statistics)</span></span>|  
|<span data-ttu-id="28f7d-195">7 (係數)</span><span class="sxs-lookup"><span data-stu-id="28f7d-195">7 (Coefficient)</span></span>|  
|<span data-ttu-id="28f7d-196">8 (得分)</span><span class="sxs-lookup"><span data-stu-id="28f7d-196">8 (Score Gain)</span></span>|  
|<span data-ttu-id="28f7d-197">9 (統計資料)</span><span class="sxs-lookup"><span data-stu-id="28f7d-197">9 (Statistics)</span></span>|  
|<span data-ttu-id="28f7d-198">11 (截距)</span><span class="sxs-lookup"><span data-stu-id="28f7d-198">11 (Intercept)</span></span>|  
  
 <span data-ttu-id="28f7d-199">如需迴歸模型每個值類型之意義的詳細資訊，請參閱 [線性迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="28f7d-199">For more information about the meaning of each value type for regression models, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="28f7d-200">回到頁首</span><span class="sxs-lookup"><span data-stu-id="28f7d-200">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-3-returning-only-the-coefficient-for-the-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="28f7d-201">範例查詢 3：僅傳回模型的係數</span><span class="sxs-lookup"><span data-stu-id="28f7d-201">Sample Query 3: Returning Only the Coefficient for the Model</span></span>  
 <span data-ttu-id="28f7d-202">您可以使用 VALUETYPE 列舉，僅傳回迴歸方程式的係數，如以下查詢所示：</span><span class="sxs-lookup"><span data-stu-id="28f7d-202">By using the VALUETYPE enumeration, you can return only the coefficient for the regression equation, as shown in the following query:</span></span>  
  
```  
SELECT FLATTENED MODEL_NAME,  
    (SELECT ATTRIBUTE_VALUE, VALUETYPE  
     FROM NODE_DISTRIBUTION  
     WHERE VALUETYPE = 11)   
AS t  
FROM LR_PredictIncome.CONTENT  
```  
  
 <span data-ttu-id="28f7d-203">此查詢會傳回兩個資料列，其中一個資料列來自採礦模型內容，而另一個資料列則來自包含係數的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="28f7d-203">This query returns two rows, one from the mining model content, and the row from the nested table that contains the coefficient.</span></span> <span data-ttu-id="28f7d-204">ATTRIBUTE_NAME 資料行不包含在此處，因為該資料行對係數來說，永遠是空白的。</span><span class="sxs-lookup"><span data-stu-id="28f7d-204">The ATTRIBUTE_NAME column is not included here because it is always blank for the coefficient.</span></span>  
  
|<span data-ttu-id="28f7d-205">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="28f7d-205">MODEL_NAME</span></span>|<span data-ttu-id="28f7d-206">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="28f7d-206">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="28f7d-207">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="28f7d-207">t.VALUETYPE</span></span>|  
|-----------------|------------------------|-----------------|  
|<span data-ttu-id="28f7d-208">LR_PredictIncome</span><span class="sxs-lookup"><span data-stu-id="28f7d-208">LR_PredictIncome</span></span>|||  
|<span data-ttu-id="28f7d-209">LR_PredictIncome</span><span class="sxs-lookup"><span data-stu-id="28f7d-209">LR_PredictIncome</span></span>|<span data-ttu-id="28f7d-210">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="28f7d-210">35793.5477381267</span></span>|<span data-ttu-id="28f7d-211">11</span><span class="sxs-lookup"><span data-stu-id="28f7d-211">11</span></span>|  
  
 [<span data-ttu-id="28f7d-212">回到頁首</span><span class="sxs-lookup"><span data-stu-id="28f7d-212">Return to Top</span></span>](#bkmk_top)  
  
## <a name="making-predictions-from-a-linear-regression-model"></a><span data-ttu-id="28f7d-213">從線性迴歸模型進行預測</span><span class="sxs-lookup"><span data-stu-id="28f7d-213">Making Predictions from a Linear Regression Model</span></span>  
 <span data-ttu-id="28f7d-214">您可以使用資料採礦設計師中的 [採礦模型預測] 索引標籤，在線性迴歸模型上建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="28f7d-214">You can build prediction queries on linear regression models by using the Mining Model Prediction tab in Data Mining Designer.</span></span> <span data-ttu-id="28f7d-215">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中都提供預測查詢產生器。</span><span class="sxs-lookup"><span data-stu-id="28f7d-215">The prediction query builder is available in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="28f7d-216">您也可以使用適用於 Excel 的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 資料採礦增益集或適用於 Excel 的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 資料採礦增益集，在迴歸模型上建立查詢。</span><span class="sxs-lookup"><span data-stu-id="28f7d-216">You can also create queries on regression models by using the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Data Mining Add-ins for Excel or the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Data Mining Add-ins for Excel.</span></span> <span data-ttu-id="28f7d-217">即使適用於 Excel 的資料採礦增益集沒有建立迴歸模型，您也可以瀏覽並查詢儲存在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體上的任何採礦模型。</span><span class="sxs-lookup"><span data-stu-id="28f7d-217">Even though the Data Mining Add-ins for Excel do not create regression models, you can browse and query any mining model that is stored on an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="28f7d-218">回到頁首</span><span class="sxs-lookup"><span data-stu-id="28f7d-218">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-4-predicting-income-using-a-singleton-query"></a><a name="bkmk_Query4"></a><span data-ttu-id="28f7d-219">範例查詢4：使用單一查詢預測收入</span><span class="sxs-lookup"><span data-stu-id="28f7d-219">Sample Query 4: Predicting Income using a Singleton Query</span></span>  
 <span data-ttu-id="28f7d-220">在迴歸模型上建立單一查詢最簡單的方式是使用 **[單一查詢輸入]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="28f7d-220">The easiest way to create a single query on a regression model is by using the **Singleton Query Input** dialog box.</span></span> <span data-ttu-id="28f7d-221">例如，您可以建立下列 DMX 查詢，方法是選取適當的回歸模型、選擇 [**單一查詢**]，然後輸入 `20` 作為 [**年齡**] 的值。</span><span class="sxs-lookup"><span data-stu-id="28f7d-221">For example, you can build the following DMX query by selecting the appropriate regression model, choosing **Singleton Query**, and then typing `20` as the value for **Age**.</span></span>  
  
```  
SELECT [LR_PredictIncome].[Yearly Income]  
From   [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 <span data-ttu-id="28f7d-222">範例結果：</span><span class="sxs-lookup"><span data-stu-id="28f7d-222">Sample results:</span></span>  
  
|<span data-ttu-id="28f7d-223">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="28f7d-223">Yearly Income</span></span>|  
|-------------------|  
|<span data-ttu-id="28f7d-224">45227.302092176</span><span class="sxs-lookup"><span data-stu-id="28f7d-224">45227.302092176</span></span>|  
  
 [<span data-ttu-id="28f7d-225">回到頁首</span><span class="sxs-lookup"><span data-stu-id="28f7d-225">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-5-using-prediction-functions-with-a-regression-model"></a><a name="bkmk_Query5"></a> <span data-ttu-id="28f7d-226">範例查詢 5：搭配迴歸模型使用預測函數</span><span class="sxs-lookup"><span data-stu-id="28f7d-226">Sample Query 5: Using Prediction Functions with a Regression Model</span></span>  
 <span data-ttu-id="28f7d-227">您可以搭配線性迴歸模型使用多個標準的預測函數。</span><span class="sxs-lookup"><span data-stu-id="28f7d-227">You can use many of the standard prediction functions with linear regression models.</span></span> <span data-ttu-id="28f7d-228">下列範例說明如何將一些敘述性的統計資料加入到預測查詢結果中。</span><span class="sxs-lookup"><span data-stu-id="28f7d-228">The following example illustrates how to add some descriptive statistics to the prediction query results.</span></span> <span data-ttu-id="28f7d-229">從這些結果中您可以發現，這與此模型的平均值有相當大的偏差。</span><span class="sxs-lookup"><span data-stu-id="28f7d-229">From these results, you can see that there is considerable deviation from the mean for this model.</span></span>  
  
```  
SELECT  
  ([LR_PredictIncome].[Yearly Income]) as [PredIncome],  
  (PredictStdev([LR_PredictIncome].[Yearly Income])) as [StDev1]  
From  
  [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 <span data-ttu-id="28f7d-230">範例結果：</span><span class="sxs-lookup"><span data-stu-id="28f7d-230">Sample results:</span></span>  
  
|<span data-ttu-id="28f7d-231">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="28f7d-231">Yearly Income</span></span>|<span data-ttu-id="28f7d-232">StDev1</span><span class="sxs-lookup"><span data-stu-id="28f7d-232">StDev1</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="28f7d-233">45227.302092176</span><span class="sxs-lookup"><span data-stu-id="28f7d-233">45227.302092176</span></span>|<span data-ttu-id="28f7d-234">31827.1726561396</span><span class="sxs-lookup"><span data-stu-id="28f7d-234">31827.1726561396</span></span>|  
  
 [<span data-ttu-id="28f7d-235">回到頁首</span><span class="sxs-lookup"><span data-stu-id="28f7d-235">Return to Top</span></span>](#bkmk_top)  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="28f7d-236">預測函數的清單</span><span class="sxs-lookup"><span data-stu-id="28f7d-236">List of Prediction Functions</span></span>  
 <span data-ttu-id="28f7d-237">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="28f7d-237">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="28f7d-238">不過， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線性迴歸演算法支援下表所列出的其他函數。</span><span class="sxs-lookup"><span data-stu-id="28f7d-238">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28f7d-239">預測函數</span><span class="sxs-lookup"><span data-stu-id="28f7d-239">Prediction Function</span></span>|<span data-ttu-id="28f7d-240">使用量</span><span class="sxs-lookup"><span data-stu-id="28f7d-240">Usage</span></span>|  
|[<span data-ttu-id="28f7d-241">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="28f7d-241">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="28f7d-242">確定某個節點是否為模型中另一個節點的子系。</span><span class="sxs-lookup"><span data-stu-id="28f7d-242">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="28f7d-243">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="28f7d-243">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="28f7d-244">指示指定的節點是否包含目前案例。</span><span class="sxs-lookup"><span data-stu-id="28f7d-244">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="28f7d-245">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="28f7d-245">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="28f7d-246">傳回指定之資料行的一個或一組預測值。</span><span class="sxs-lookup"><span data-stu-id="28f7d-246">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="28f7d-247">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="28f7d-247">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="28f7d-248">傳回每個案例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="28f7d-248">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="28f7d-249">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="28f7d-249">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="28f7d-250">傳回預測值的標準差。</span><span class="sxs-lookup"><span data-stu-id="28f7d-250">Returns standard deviation for the predicted value.</span></span>|  
|[<span data-ttu-id="28f7d-251">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="28f7d-251">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="28f7d-252">傳回指定狀態的支援值。</span><span class="sxs-lookup"><span data-stu-id="28f7d-252">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="28f7d-253">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="28f7d-253">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="28f7d-254">傳回指定之資料行的變異數。</span><span class="sxs-lookup"><span data-stu-id="28f7d-254">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="28f7d-255">如需所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法共用之函數的清單，請參閱[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="28f7d-255">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span> <span data-ttu-id="28f7d-256">如需如何使用這些函數的詳細資訊，請參閱[資料採礦延伸模組 &#40;DMX&#41; 函數參考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="28f7d-256">For more information about how to use these functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f7d-257">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28f7d-257">See Also</span></span>  
 <span data-ttu-id="28f7d-258">[Microsoft 線性回歸演算法](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="28f7d-258">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="28f7d-259">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="28f7d-259">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="28f7d-260">[Microsoft 線性回歸演算法技術參考](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="28f7d-260">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="28f7d-261">線性迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="28f7d-261">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
