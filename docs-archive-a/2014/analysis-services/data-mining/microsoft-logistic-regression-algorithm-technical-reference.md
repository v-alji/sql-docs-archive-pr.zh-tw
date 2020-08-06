---
title: Microsoft 羅吉斯回歸演算法技術參考 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- MAXIMUM_INPUT_ATTRIBUTES parameter
- HOLDOUT_PERCENTAGE parameter
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
- SAMPLE_SIZE parameter
- regression algorithms [Analysis Services]
- HOLDOUT_SEED parameter
ms.assetid: cf32f1f3-153e-476f-91a4-bb834ec7c88d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72597453c9a52b890c822dd7c46aff46bc3ba44e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606502"
---
# <a name="microsoft-logistic-regression-algorithm-technical-reference"></a><span data-ttu-id="b0d9e-102">Microsoft 羅吉斯迴歸演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="b0d9e-102">Microsoft Logistic Regression Algorithm Technical Reference</span></span>
  <span data-ttu-id="b0d9e-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 羅吉斯迴歸演算法是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法的演變，其中 *HIDDEN_NODE_RATIO* 參數設為 0。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm is a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm, where the *HIDDEN_NODE_RATIO* parameter is set to 0.</span></span> <span data-ttu-id="b0d9e-104">此設定會建立不包含隱藏層的類神經網路模型，而這相等於羅吉斯迴歸。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-104">This setting will create a neural network model that does not contain a hidden layer, and that therefore is equivalent to logistic regression.</span></span>

## <a name="implementation-of-the-microsoft-logistic-regression-algorithm"></a><span data-ttu-id="b0d9e-105">Microsoft 羅吉斯迴歸演算法的實作</span><span class="sxs-lookup"><span data-stu-id="b0d9e-105">Implementation of the Microsoft Logistic Regression Algorithm</span></span>
 <span data-ttu-id="b0d9e-106">假設可預測資料行只包含兩個狀態，但您仍然想要執行迴歸分析，使輸入資料行與可預測資料行將包含特定狀態的機率相關。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-106">Suppose the predictable column contains only two states, yet you still want to perform a regression analysis, relating input columns to the probability that the predictable column will contain a specific state.</span></span> <span data-ttu-id="b0d9e-107">下列圖表說明如果您指定 1 和 0 給可預測資料行的狀態時將得到的結果，請計算資料行將包含特定狀態的機率，並對輸入屬性執行線性迴歸。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-107">The following diagram illustrates the results you will obtain if you assign 1 and 0 to the states of the predictable column, calculate the probability that the column will contain a specific state, and perform a linear regression against an input variable.</span></span>

 <span data-ttu-id="b0d9e-108">![使用線性迴歸的模式化不良資料](../media/logistic-linear-regression.gif "使用線性迴歸的模式化不良資料")</span><span class="sxs-lookup"><span data-stu-id="b0d9e-108">![Poorly modeled data using linear regression](../media/logistic-linear-regression.gif "Poorly modeled data using linear regression")</span></span>

 <span data-ttu-id="b0d9e-109">x 軸包含輸入資料行的值。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-109">The x-axis contains values of an input column.</span></span> <span data-ttu-id="b0d9e-110">y 軸包含可預測資料行成為一個狀態或另一個狀態的機率。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-110">The y-axis contains the probabilities that the predictable column will be one state or the other.</span></span> <span data-ttu-id="b0d9e-111">其問題在於，即使 0 和 1 是資料行的最大值和最小值，但線性迴歸並不限制資料行介於 0 和 1 之間。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-111">The problem with this is that the linear regression does not constrain the column to be between 0 and 1, even though those are the maximum and minimum values of the column.</span></span> <span data-ttu-id="b0d9e-112">解決此問題的方式之一是執行羅吉斯迴歸。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-112">A way to solve this problem is to perform logistic regression.</span></span> <span data-ttu-id="b0d9e-113">羅吉斯迴歸分析不建立直線，而是建立「S」形曲線來包含最大和最小條件約束。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-113">Instead of creating a straight line, logistic regression analysis creates an "S" shaped curve that contains maximum and minimum constraints.</span></span> <span data-ttu-id="b0d9e-114">例如，下列圖表說明您如果對先前範例所使用的相同資料執行羅吉斯迴歸會達到的結果。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-114">For example, the following diagram illustrates the results you will achieve if you perform a logistic regression against the same data as used for the previous example.</span></span>

 <span data-ttu-id="b0d9e-115">![使用羅吉斯迴歸模式化的資料](../media/logistic-regression.gif "使用羅吉斯迴歸模式化的資料")</span><span class="sxs-lookup"><span data-stu-id="b0d9e-115">![Data modeled by using logistic regression](../media/logistic-regression.gif "Data modeled by using logistic regression")</span></span>

 <span data-ttu-id="b0d9e-116">請注意，曲線絕不能高於 1 或低於 0。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-116">Notice how the curve never goes above 1 or below 0.</span></span> <span data-ttu-id="b0d9e-117">您可以使用羅吉斯迴歸來描述哪些輸入資料行在決定可預測資料行的狀態時很重要。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-117">You can use logistic regression to describe which input columns are important in determining the state of the predictable column.</span></span>

### <a name="feature-selection"></a><span data-ttu-id="b0d9e-118">特徵選取</span><span class="sxs-lookup"><span data-stu-id="b0d9e-118">Feature Selection</span></span>
 <span data-ttu-id="b0d9e-119">所有 Analysis Services 資料採礦演算法都會自動使用特徵選取來改善分析並減少處理的負載。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-119">Feature selection is used automatically by all Analysis Services data mining algorithms to improve analysis and reduce processing load.</span></span> <span data-ttu-id="b0d9e-120">在羅吉斯迴歸模型中，特徵選取所使用的方法取決於屬性的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-120">The method used for feature selection in a logistic regression model depends on the data type of the attribute.</span></span> <span data-ttu-id="b0d9e-121">羅吉斯迴歸是以 Microsoft 類神經網路演算法為基礎，因此，它會使用適用於類神經網路的特徵選取方法子集。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-121">Because logistic regression is based on the Microsoft Neural Network algorithm, it uses a subset of the feature selection methods that apply to neural networks.</span></span> <span data-ttu-id="b0d9e-122">如需詳細資訊，請參閱[特徵選取 &#40;資料採礦&#41;](feature-selection-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-122">For more information, see [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>

### <a name="scoring-inputs"></a><span data-ttu-id="b0d9e-123">計分輸入</span><span class="sxs-lookup"><span data-stu-id="b0d9e-123">Scoring Inputs</span></span>
 <span data-ttu-id="b0d9e-124">在類神經網路模型或羅吉斯迴歸模型的內容中，「計分」\*\* 表示一種程序，會將資料中出現的值轉換為使用相同小數位數的一組值，因此可以互相比較。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-124">*Scoring* in the context of a neural network model or logistic regression model means the process of converting the values that are present in the data into a set of values that use the same scale and therefore can be compared to each other.</span></span> <span data-ttu-id="b0d9e-125">例如，假設 Income 輸入的範圍是 0 到 100,000，而 [Number of Children] 輸入的範圍是 0 到 5。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-125">For example, suppose the inputs for Income range from 0 to 100,000 whereas the inputs for [Number of Children] range from 0 to 5.</span></span> <span data-ttu-id="b0d9e-126">此轉換程式可讓您對每個輸入的重要性進行*評分*或比較，而不論值的差異。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-126">This conversion process allows you to *score*, or compare, the importance of each input regardless of the difference in values.</span></span>

 <span data-ttu-id="b0d9e-127">對於出現在定型集中的每個狀態，模型都會產生一個輸入。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-127">For each state that appears in the training set, the model generates an input.</span></span> <span data-ttu-id="b0d9e-128">對於離散或離散化的輸入，如果在定型集中至少出現一次遺漏狀態，則會建立其他輸入來代表「遺漏」狀態。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-128">For discrete or discretized inputs, an additional input is created to represent the Missing state, if the missing state appears at least once in the training set.</span></span> <span data-ttu-id="b0d9e-129">至於連續輸入，最多會建立兩個輸入節點：一個用於「遺漏」值 (如果出現在定型資料中)，而另一個輸入則用於所有現有的值或非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-129">For continuous inputs, at most two input nodes are created: one for Missing values, if present in the training data, and one input for all existing, or non-null, values.</span></span> <span data-ttu-id="b0d9e-130">每個輸入都會使用 z 分數正規化方法來調整為數值格式， (x-μ) /StdDev。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-130">Each input is scaled to a numeric format using the z-score normalization method, (x - μ)/StdDev.</span></span>

 <span data-ttu-id="b0d9e-131">在 z-score 正規化期間，平均值 (μ) 和標準差會透過完整的定型集取得。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-131">During z-score normalization, the mean (μ) and standard deviation are obtained over the complete training set.</span></span>

 <span data-ttu-id="b0d9e-132">**連續值**</span><span class="sxs-lookup"><span data-stu-id="b0d9e-132">**Continuous values**</span></span>

 <span data-ttu-id="b0d9e-133">值存在： (X-μ) /σ//X 是要編碼的實際值) </span><span class="sxs-lookup"><span data-stu-id="b0d9e-133">Value is present:   (X - μ)/σ // X is the actual value being encoded)</span></span>

 <span data-ttu-id="b0d9e-134">值不存在：-μ/σ//負 mu 除以 sigma) </span><span class="sxs-lookup"><span data-stu-id="b0d9e-134">Value is absent:    -   μ/σ  // negative mu divided by sigma)</span></span>

 <span data-ttu-id="b0d9e-135">**離散值**</span><span class="sxs-lookup"><span data-stu-id="b0d9e-135">**Discrete values**</span></span>

 <span data-ttu-id="b0d9e-136">μ = p- (狀態的先前機率) </span><span class="sxs-lookup"><span data-stu-id="b0d9e-136">μ = p - (the prior probability of a state)</span></span>

 <span data-ttu-id="b0d9e-137">StdDev  = sqrt(p(1-p))</span><span class="sxs-lookup"><span data-stu-id="b0d9e-137">StdDev  = sqrt(p(1-p))</span></span>

 <span data-ttu-id="b0d9e-138">值存在： (1-μ) /σ// (一個減 mu) 除以 sigma) </span><span class="sxs-lookup"><span data-stu-id="b0d9e-138">Value is present:     (1 - μ)/σ// (One minus mu) divided by sigma)</span></span>

 <span data-ttu-id="b0d9e-139">值不存在： (-μ) /σ//負 mu 除以 sigma) </span><span class="sxs-lookup"><span data-stu-id="b0d9e-139">Value is absent:     (- μ)/σ// negative mu divided by sigma)</span></span>

### <a name="understanding-logistic-regression-coefficients"></a><span data-ttu-id="b0d9e-140">了解羅吉斯迴歸係數</span><span class="sxs-lookup"><span data-stu-id="b0d9e-140">Understanding Logistic Regression Coefficients</span></span>
 <span data-ttu-id="b0d9e-141">在統計文獻中，有各種方法可以執行羅吉斯迴歸，但是所有方法的重要部分都是評估模型的符合度。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-141">There are various methods in the statistical literature for performing logistic regression, but an important part of all methods is assessing the fit of the model.</span></span> <span data-ttu-id="b0d9e-142">在勝算比和共變模式之間，提出各種符合程度統計資料。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-142">A variety of goodness-to-fit statistics have been proposed, among them odds ratios and covariate patterns.</span></span> <span data-ttu-id="b0d9e-143">如何測量模型符合度的討論超出本主題的範圍，不過，您可以在模型中擷取係數的值，然後用於設計符合您自己的量值。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-143">A discussion of how to measure the fit of a model is beyond the scope of this topic; however, you can retrieve the value of the coefficients in the model and use them to design your own measures of fit.</span></span>

> [!NOTE]
>  <span data-ttu-id="b0d9e-144">當做羅吉斯迴歸模型一部分建立的係數不代表勝算比，而且不應該如此解譯。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-144">The coefficients that are created as part of a logistic regression model do not represent odds ratios and should not be interpreted as such.</span></span>

 <span data-ttu-id="b0d9e-145">模型圖形中每個節點的係數都代表該節點之輸入的加權總和。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-145">The coefficients for each node in the model graph represent a weighted sum of the inputs to that node.</span></span> <span data-ttu-id="b0d9e-146">在羅吉斯迴歸模型中，隱藏層是空的，因此只有輸出節點中儲存的一組係數。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-146">In a logistic regression model, the hidden layer is empty; therefore, there is only one set of coefficients, which is stored in the output nodes.</span></span> <span data-ttu-id="b0d9e-147">您可以使用下列查詢來擷取係數的值：</span><span class="sxs-lookup"><span data-stu-id="b0d9e-147">You can retrieve the values of the coefficients by using the following query:</span></span>

```
SELECT FLATTENED [NODE_UNIQUE NAME],
(SELECT ATTRIBUTE_NAME< ATTRIBUTE_VALUE
FROM NODE_DISTRIBUTION) AS t
FROM <model name>.CONTENT
WHERE NODE_TYPE = 23
```

 <span data-ttu-id="b0d9e-148">針對每個輸出值，此查詢會傳回係數以及指回相關輸入節點的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-148">For each output value, this query returns the coefficients and an ID that points back to the related input node.</span></span> <span data-ttu-id="b0d9e-149">它也會傳回包含輸出值與截距的資料列。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-149">It also returns a row that contains the value of the output and the intercept.</span></span> <span data-ttu-id="b0d9e-150">每個輸入 X 都有自己的係數 (Ci) ，但此嵌套資料表也會包含「自由」係數 (Co) ，並根據下列公式計算：</span><span class="sxs-lookup"><span data-stu-id="b0d9e-150">Each input X has its own coefficient (Ci), but the nested table also contains a "free" coefficient (Co), calculated according to the following formula:</span></span>

 <span data-ttu-id="b0d9e-151">F (X) = X1 \* C1 + X2 \* C2 + ... + Xn \* Cn + X0</span><span class="sxs-lookup"><span data-stu-id="b0d9e-151">F(X) = X1\*C1 + X2\*C2 + ... +Xn\*Cn + X0</span></span>

 <span data-ttu-id="b0d9e-152">Activation: exp(F(X)) / (1 + exp(F(X)) )</span><span class="sxs-lookup"><span data-stu-id="b0d9e-152">Activation: exp(F(X)) / (1 + exp(F(X)) )</span></span>

 <span data-ttu-id="b0d9e-153">如需詳細資訊，請參閱 [羅吉斯迴歸模型查詢範例](logistic-regression-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-153">For more information, see [Logistic Regression Model Query Examples](logistic-regression-model-query-examples.md).</span></span>

## <a name="customizing-the-logistic-regression-algorithm"></a><span data-ttu-id="b0d9e-154">自訂羅吉斯迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="b0d9e-154">Customizing the Logistic Regression Algorithm</span></span>
 <span data-ttu-id="b0d9e-155">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 羅吉斯迴歸演算法支援數個會影響所產生之採礦模型的行為、效能和精確度的參數。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-155">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] logistic regression algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="b0d9e-156">您也可以在用於輸入的資料行上設定模型旗標，藉以修改模型的行為。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-156">You can also modify the behavior of the model by setting modeling flags on the columns used as input.</span></span>

### <a name="setting-algorithm-parameters"></a><span data-ttu-id="b0d9e-157">設定演算法參數</span><span class="sxs-lookup"><span data-stu-id="b0d9e-157">Setting Algorithm Parameters</span></span>
 <span data-ttu-id="b0d9e-158">下表描述可搭配 Microsoft 羅吉斯迴歸演算法使用的參數。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-158">The following table describes the parameters that can be used with the Microsoft Logistic Regression algorithm.</span></span>

 <span data-ttu-id="b0d9e-159">HOLDOUT_PERCENTAGE 指定定型資料內用來計算維持錯誤的案例百分比。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-159">HOLDOUT_PERCENTAGE Specifies the percentage of cases within the training data used to calculate the holdout error.</span></span> <span data-ttu-id="b0d9e-160">HOLDOUT_PERCENTAGE 在培訓採礦模型時是做為停止準則的一部份。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-160">HOLDOUT_PERCENTAGE is used as part of the stopping criteria while training the mining model.</span></span>

 <span data-ttu-id="b0d9e-161">預設值是 30。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-161">The default is 30.</span></span>

 <span data-ttu-id="b0d9e-162">HOLDOUT_SEED 指定在隨機判斷維持的資料時，用來植入虛擬隨機產生器的數位。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-162">HOLDOUT_SEED Specifies a number to use to seed the pseudo-random generator when randomly determining the holdout data.</span></span> <span data-ttu-id="b0d9e-163">如果 HOLDOUT_SEED 是設定為 0，則此演算法會依據採礦模型的名稱產生種子，以保證在重新處理期間模型內容保持不變。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-163">If HOLDOUT_SEED is set to 0, the algorithm generates the seed based on the name of the mining model, to guarantee that the model content remains the same during reprocessing.</span></span>

 <span data-ttu-id="b0d9e-164">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-164">The default is 0.</span></span>

 <span data-ttu-id="b0d9e-165">MAXIMUM_INPUT_ATTRIBUTES 定義演算法在叫用特徵選取之前可處理的輸入屬性數目。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-165">MAXIMUM_INPUT_ATTRIBUTES Defines the number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="b0d9e-166">將此值設定為 0 可關閉特徵選取。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-166">Set this value to 0 to turn off feature selection.</span></span>

 <span data-ttu-id="b0d9e-167">預設值為 255。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-167">The default is 255.</span></span>

 <span data-ttu-id="b0d9e-168">MAXIMUM_OUTPUT_ATTRIBUTES 定義演算法在叫用特徵選取之前，可以處理的輸出屬性數目。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-168">MAXIMUM_OUTPUT_ATTRIBUTES Defines the number of output attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="b0d9e-169">將此值設定為 0 可關閉特徵選取。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-169">Set this value to 0 to turn off feature selection.</span></span>

 <span data-ttu-id="b0d9e-170">預設值為 255。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-170">The default is 255.</span></span>

 <span data-ttu-id="b0d9e-171">MAXIMUM_STATES 指定演算法支援之屬性狀態的最大數目。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-171">MAXIMUM_STATES Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="b0d9e-172">如果屬性擁有的狀態數目大於狀態的最大數目，演算法會使用屬性最常用的狀態，並忽略其餘的狀態。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-172">If the number of states that an attribute has is larger than the maximum number of states, the algorithm uses the most popular states of the attribute and ignores the remaining states.</span></span>

 <span data-ttu-id="b0d9e-173">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-173">The default is 100.</span></span>

 <span data-ttu-id="b0d9e-174">SAMPLE_SIZE 指定要用來定型模型的案例數目。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-174">SAMPLE_SIZE Specifies the number of cases to be used to train the model.</span></span> <span data-ttu-id="b0d9e-175">此演算法提供者會使用此數字或不包括在鑑效組百分比 (由 HOLDOUT_PERCENTAGE 參數指定) 中的總案例數百分比，以較小者為準。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-175">The algorithm provider uses either this number or the percentage of total of cases that are not included in the holdout percentage as specified by the HOLDOUT_PERCENTAGE parameter, whichever value is smaller.</span></span>

 <span data-ttu-id="b0d9e-176">換句話說，如果 HOLDOUT_PERCENTAGE 設定為 30，則演算法將使用此參數的值，或等於總案例數 70% 的值，以較小者為準。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-176">In other words, if HOLDOUT_PERCENTAGE is set to 30, the algorithm will use either the value of this parameter, or a value that is equal to 70 percent of the total number of cases, whichever is smaller.</span></span>

 <span data-ttu-id="b0d9e-177">預設值為 10000。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-177">The default is 10000.</span></span>

### <a name="modeling-flags"></a><span data-ttu-id="b0d9e-178">模型旗標</span><span class="sxs-lookup"><span data-stu-id="b0d9e-178">Modeling Flags</span></span>
 <span data-ttu-id="b0d9e-179">系統支援下列模型旗標，可搭配 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 羅吉斯迴歸演算法使用。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-179">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>

 <span data-ttu-id="b0d9e-180">NOT Null 表示資料行不能包含 Null。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-180">NOT NULL Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="b0d9e-181">如果 Analysis Services 在模型定型期間遇到 Null 值，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-181">An error will result if Analysis Services encounters a null during model training.</span></span>

 <span data-ttu-id="b0d9e-182">適用於採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-182">Applies to mining structure columns.</span></span>

 <span data-ttu-id="b0d9e-183">MODEL_EXISTENCE_ONLY 表示會將資料行視為具有兩種可能的狀態： `Missing` 和 `Existing` 。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-183">MODEL_EXISTENCE_ONLY Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="b0d9e-184">Null 為遺漏值。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-184">A null is a missing value.</span></span>

 <span data-ttu-id="b0d9e-185">適用於採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-185">Applies to mining model column.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0d9e-186">需求</span><span class="sxs-lookup"><span data-stu-id="b0d9e-186">Requirements</span></span>
 <span data-ttu-id="b0d9e-187">羅吉斯迴歸模型必須包含索引鍵資料行、輸入資料行和至少一個可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-187">A logistic regression model must contain a key column, input columns, and at least one predictable column.</span></span>

### <a name="input-and-predictable-columns"></a><span data-ttu-id="b0d9e-188">輸入和可預測資料行</span><span class="sxs-lookup"><span data-stu-id="b0d9e-188">Input and Predictable Columns</span></span>
 <span data-ttu-id="b0d9e-189">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 羅吉斯迴歸演算法支援特定輸入資料行內容類型、可預測資料行內容類型和模型旗標，這些都會在下表中列出。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-189">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm supports the specific input column content types, predictable column content types, and modeling flags that are listed in the following table.</span></span> <span data-ttu-id="b0d9e-190">如需內容類型用於採礦模型時所代表意義的詳細資訊，請參閱[內容類型 &#40;資料採礦&#41;](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d9e-190">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>

|<span data-ttu-id="b0d9e-191">資料行</span><span class="sxs-lookup"><span data-stu-id="b0d9e-191">Column</span></span>|<span data-ttu-id="b0d9e-192">內容類型</span><span class="sxs-lookup"><span data-stu-id="b0d9e-192">Content types</span></span>|
|------------|-------------------|
|<span data-ttu-id="b0d9e-193">輸入屬性</span><span class="sxs-lookup"><span data-stu-id="b0d9e-193">Input attribute</span></span>|<span data-ttu-id="b0d9e-194">Continuous、Discrete、Discretized、Key、Table</span><span class="sxs-lookup"><span data-stu-id="b0d9e-194">Continuous, Discrete, Discretized, Key, Table</span></span>|
|<span data-ttu-id="b0d9e-195">可預測屬性</span><span class="sxs-lookup"><span data-stu-id="b0d9e-195">Predictable attribute</span></span>|<span data-ttu-id="b0d9e-196">Continuous、Discrete、Discretized</span><span class="sxs-lookup"><span data-stu-id="b0d9e-196">Continuous, Discrete, Discretized</span></span>|

## <a name="see-also"></a><span data-ttu-id="b0d9e-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0d9e-197">See Also</span></span>
 <span data-ttu-id="b0d9e-198">[Microsoft 羅吉斯回歸演算法](microsoft-logistic-regression-algorithm.md)[線性回歸模型查詢範例](linear-regression-model-query-examples.md)[羅吉斯回歸模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](mining-model-content-for-logistic-regression-models.md) [Microsoft 類神經網路演算法](microsoft-neural-network-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="b0d9e-198">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) [Linear Regression Model Query Examples](linear-regression-model-query-examples.md) [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)</span></span>


