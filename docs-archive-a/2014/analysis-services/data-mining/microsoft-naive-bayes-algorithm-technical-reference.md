---
title: Microsoft 貝氏貝氏機率分類演算法技術參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_DEPENDENCY_PROBABILITY parameter
- MAXIMUM_INPUT_ATTRIBUTES parameter
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
ms.assetid: a4cd47fe-2127-4930-b18f-3edd17ee9a65
author: minewiskan
ms.author: owend
ms.openlocfilehash: b03f77f1e7299ef073f0e01775d879ee0ce57f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606500"
---
# <a name="microsoft-naive-bayes-algorithm-technical-reference"></a><span data-ttu-id="40148-102">Microsoft 貝氏機率分類演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="40148-102">Microsoft Naive Bayes Algorithm Technical Reference</span></span>
  <span data-ttu-id="40148-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]貝氏貝氏機率分類演算法是提供的分類演算法，可 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用於預測模型。</span><span class="sxs-lookup"><span data-stu-id="40148-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm provided by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for use in predictive modeling.</span></span> <span data-ttu-id="40148-104">此演算法會計算輸入資料行和可預測資料行之間的條件式機率，並假設資料行是獨立的。</span><span class="sxs-lookup"><span data-stu-id="40148-104">The algorithm calculates the conditional probability between input and predictable columns, and assumes that the columns are independent.</span></span> <span data-ttu-id="40148-105">這種獨立性假設產生了貝氏機率分類這個名稱。</span><span class="sxs-lookup"><span data-stu-id="40148-105">This assumption of independence leads to the name Naive Bayes.</span></span>  
  
## <a name="implementation-of-the-microsoft-naive-bayes-algorithm"></a><span data-ttu-id="40148-106">Microsoft 貝氏機率分類演算法的實作</span><span class="sxs-lookup"><span data-stu-id="40148-106">Implementation of the Microsoft Naive Bayes Algorithm</span></span>  
 <span data-ttu-id="40148-107">此演算法比其他 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法更少計算，因此對於快速產生採礦模型來探索輸入資料行和可預測資料行之間的關聯性很有用。</span><span class="sxs-lookup"><span data-stu-id="40148-107">This algorithm is less computationally intense than other [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, and therefore is useful for quickly generating mining models to discover relationships between input columns and predictable columns.</span></span> <span data-ttu-id="40148-108">此演算法會考量輸入屬性值與輸出屬性值的每個配對。</span><span class="sxs-lookup"><span data-stu-id="40148-108">The algorithm considers each pair of input attribute values and output attribute values.</span></span>  
  
 <span data-ttu-id="40148-109">貝氏理論的數學屬性描述超出本文件集的範圍；如需詳細資訊，請參閱 Microsoft Research 報告中的 [學習貝氏網路：知識與統計資料的組合](https://go.microsoft.com/fwlink/?LinkId=207029)。</span><span class="sxs-lookup"><span data-stu-id="40148-109">A description of the mathematical properties of Bayes Theorem is beyond the scope of this documentation; for more information, see the paper by Microsoft Research titled [Learning Bayesian Networks: The Combination of Knowledge and Statistical Data](https://go.microsoft.com/fwlink/?LinkId=207029).</span></span>  
  
 <span data-ttu-id="40148-110">如需調整所有模型中的機率來表示可能遺漏值的描述，請參閱[遺漏值 &#40;Analysis Services - 資料採礦&#41;](missing-values-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="40148-110">For a description of how probabilities in all models are adjusted to account for potential missing values, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
### <a name="feature-selection"></a><span data-ttu-id="40148-111">特徵選取</span><span class="sxs-lookup"><span data-stu-id="40148-111">Feature Selection</span></span>  
 <span data-ttu-id="40148-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法會執行自動特徵選取，藉以限制建立模型時所考量的值數目。</span><span class="sxs-lookup"><span data-stu-id="40148-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm performs automatic feature selection to limit the number of values that are considered when building the model.</span></span> <span data-ttu-id="40148-113">如需詳細資訊，請參閱[特徵選取 &#40;資料採礦&#41;](feature-selection-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="40148-113">For more information, see [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>  
  
|<span data-ttu-id="40148-114">演算法</span><span class="sxs-lookup"><span data-stu-id="40148-114">Algorithm</span></span>|<span data-ttu-id="40148-115">分析的方法</span><span class="sxs-lookup"><span data-stu-id="40148-115">Method of analysis</span></span>|<span data-ttu-id="40148-116">註解</span><span class="sxs-lookup"><span data-stu-id="40148-116">Comments</span></span>|  
|---------------|------------------------|--------------|  
|<span data-ttu-id="40148-117">貝氏機率分類</span><span class="sxs-lookup"><span data-stu-id="40148-117">Naive Bayes</span></span>|<span data-ttu-id="40148-118">Shannon 熵</span><span class="sxs-lookup"><span data-stu-id="40148-118">Shannon's Entropy</span></span><br /><br /> <span data-ttu-id="40148-119">使用 K2 優先的貝氏</span><span class="sxs-lookup"><span data-stu-id="40148-119">Bayesian with K2 Prior</span></span><br /><br /> <span data-ttu-id="40148-120">使用優先統一狄氏分配的貝氏 (預設值)</span><span class="sxs-lookup"><span data-stu-id="40148-120">Bayesian Dirichlet with uniform prior (default)</span></span>|<span data-ttu-id="40148-121">貝氏機率分類只接受離散或離散化的屬性，因此無法使用有趣性分數。</span><span class="sxs-lookup"><span data-stu-id="40148-121">Naive Bayes only accepts discrete or discretized attributes; therefore, it cannot use the interestingness score.</span></span>|  
  
 <span data-ttu-id="40148-122">此演算法的設計會將處理時間降至最低，並可有效地選取重要性最高的屬性，不過，您可以設定參數來控制此演算法所使用的資料，如下所示：</span><span class="sxs-lookup"><span data-stu-id="40148-122">The algorithm is designed to minimize processing time and efficiently select the attributes that have the greatest importance; however, you can control the data that is used by the algorithm by setting parameters as follows:</span></span>  
  
-   <span data-ttu-id="40148-123">若要限制當做輸入使用的值，減少 MAXIMUM_INPUT_ATTRIBUTES 的值。</span><span class="sxs-lookup"><span data-stu-id="40148-123">To limit the values that are used as inputs, decrease the value of MAXIMUM_INPUT_ATTRIBUTES.</span></span>  
  
-   <span data-ttu-id="40148-124">若要限制模型分析的屬性數目，減少 MAXIMUM_OUTPUT_ATTRIBUTES 的值。</span><span class="sxs-lookup"><span data-stu-id="40148-124">To limit the number of attributes analyzed by the model, decrease the value of MAXIMUM_OUTPUT_ATTRIBUTES.</span></span>  
  
-   <span data-ttu-id="40148-125">若要限制可以針對任何一個屬性考量的值數目，減少 MINIMUM_STATES 的值。</span><span class="sxs-lookup"><span data-stu-id="40148-125">To limit the number of values that can be considered for any one attribute, decrease the value of MINIMUM_STATES.</span></span>  
  
## <a name="customizing-the-naive-bayes-algorithm"></a><span data-ttu-id="40148-126">自訂貝氏機率分類演算法</span><span class="sxs-lookup"><span data-stu-id="40148-126">Customizing the Naive Bayes Algorithm</span></span>  
 <span data-ttu-id="40148-127">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法支援數個會影響所產生之採礦模型的行為、效能和精確度的參數。</span><span class="sxs-lookup"><span data-stu-id="40148-127">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="40148-128">您也可以設定模型資料行上的模型旗標來控制處理資料的方式，或設定採礦結構上的旗標來指定處理遺漏值或 Null 值的方式。</span><span class="sxs-lookup"><span data-stu-id="40148-128">You can also set modeling flags on the model columns to control how data is processed, or set flags on the mining structure to specify how missing values or nulls should be handled.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="40148-129">設定演算法參數</span><span class="sxs-lookup"><span data-stu-id="40148-129">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="40148-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法支援數個會影響所產生之採礦模型的效能和精確度的參數。</span><span class="sxs-lookup"><span data-stu-id="40148-130">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports several parameters that affect the performance and accuracy of the resulting mining model.</span></span> <span data-ttu-id="40148-131">下表描述每一個參數。</span><span class="sxs-lookup"><span data-stu-id="40148-131">The following table describes each parameter.</span></span>  
  
 <span data-ttu-id="40148-132">*MAXIMUM_INPUT_ATTRIBUTES*</span><span class="sxs-lookup"><span data-stu-id="40148-132">*MAXIMUM_INPUT_ATTRIBUTES*</span></span>  
 <span data-ttu-id="40148-133">指定在叫用特徵選取之前，演算法可以處理輸入屬性的最大數目。</span><span class="sxs-lookup"><span data-stu-id="40148-133">Specifies the maximum number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="40148-134">將此值設定為 0，會停用輸入屬性的特徵選取。</span><span class="sxs-lookup"><span data-stu-id="40148-134">Setting this value to 0 disables feature selection for input attributes.</span></span>  
  
 <span data-ttu-id="40148-135">預設值為 255。</span><span class="sxs-lookup"><span data-stu-id="40148-135">The default is 255.</span></span>  
  
 <span data-ttu-id="40148-136">*MAXIMUM_OUTPUT_ATTRIBUTES*</span><span class="sxs-lookup"><span data-stu-id="40148-136">*MAXIMUM_OUTPUT_ATTRIBUTES*</span></span>  
 <span data-ttu-id="40148-137">指定在叫用特徵選取之前，演算法可以處理輸出屬性的最大數目。</span><span class="sxs-lookup"><span data-stu-id="40148-137">Specifies the maximum number of output attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="40148-138">將此值設定為 0，會停用輸出屬性的特徵選取。</span><span class="sxs-lookup"><span data-stu-id="40148-138">Setting this value to 0 disables feature selection for output attributes.</span></span>  
  
 <span data-ttu-id="40148-139">預設值為 255。</span><span class="sxs-lookup"><span data-stu-id="40148-139">The default is 255.</span></span>  
  
 <span data-ttu-id="40148-140">*MINIMUM_DEPENDENCY_PROBABILITY*</span><span class="sxs-lookup"><span data-stu-id="40148-140">*MINIMUM_DEPENDENCY_PROBABILITY*</span></span>  
 <span data-ttu-id="40148-141">指定介於輸入和輸出屬性之間的最小相依機率。</span><span class="sxs-lookup"><span data-stu-id="40148-141">Specifies the minimum dependency probability between input and output attributes.</span></span> <span data-ttu-id="40148-142">這個值會用來限制演算法所產生之內容的大小。</span><span class="sxs-lookup"><span data-stu-id="40148-142">This value is used to limit the size of the content that is generated by the algorithm.</span></span> <span data-ttu-id="40148-143">此屬性可設定為 0 到 1。</span><span class="sxs-lookup"><span data-stu-id="40148-143">This property can be set from 0 to 1.</span></span> <span data-ttu-id="40148-144">越大的值會減少模型內容中的屬性數目。</span><span class="sxs-lookup"><span data-stu-id="40148-144">Larger values reduce the number of attributes in the content of the model.</span></span>  
  
 <span data-ttu-id="40148-145">預設值是 0.5。</span><span class="sxs-lookup"><span data-stu-id="40148-145">The default is 0.5.</span></span>  
  
 <span data-ttu-id="40148-146">*MAXIMUM_STATES*</span><span class="sxs-lookup"><span data-stu-id="40148-146">*MAXIMUM_STATES*</span></span>  
 <span data-ttu-id="40148-147">指定演算法所支援之屬性狀態的最大數目。</span><span class="sxs-lookup"><span data-stu-id="40148-147">Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="40148-148">如果屬性具有的狀態數目大於狀態的最大數目，則演算法會使用屬性最常用的狀態，並將其餘的狀態視為遺漏。</span><span class="sxs-lookup"><span data-stu-id="40148-148">If the number of states that an attribute has is greater than the maximum number of states, the algorithm uses the attribute's most popular states and treats the remaining states as missing.</span></span>  
  
 <span data-ttu-id="40148-149">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="40148-149">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="40148-150">模型旗標</span><span class="sxs-lookup"><span data-stu-id="40148-150">Modeling Flags</span></span>  
 <span data-ttu-id="40148-151">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法支援下列模型旗標。</span><span class="sxs-lookup"><span data-stu-id="40148-151">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm supports the following modeling flags.</span></span> <span data-ttu-id="40148-152">當您建立採礦結構或採礦模型時，您會定義模型旗標來指定分析期間要如何處理每個資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="40148-152">When you create the mining structure or mining model, you define modeling flags to specify how values in each column are handled during analysis.</span></span> <span data-ttu-id="40148-153">如需詳細資訊，請參閱[模型旗標 &#40;資料採礦&#41;](modeling-flags-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="40148-153">For more information, see [Modeling Flags &#40;Data Mining&#41;](modeling-flags-data-mining.md).</span></span>  
  
|<span data-ttu-id="40148-154">模型旗標</span><span class="sxs-lookup"><span data-stu-id="40148-154">Modeling Flag</span></span>|<span data-ttu-id="40148-155">描述</span><span class="sxs-lookup"><span data-stu-id="40148-155">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="40148-156">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="40148-156">MODEL_EXISTENCE_ONLY</span></span>|<span data-ttu-id="40148-157">表示資料行將被視為擁有兩個可能狀態：「遺漏」和「現有」。</span><span class="sxs-lookup"><span data-stu-id="40148-157">Means that the column will be treated as having two possible states: Missing and Existing.</span></span> <span data-ttu-id="40148-158">Null 為遺漏值。</span><span class="sxs-lookup"><span data-stu-id="40148-158">A null is a missing value.</span></span><br /><br /> <span data-ttu-id="40148-159">適用於採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="40148-159">Applies to mining model column.</span></span>|  
|<span data-ttu-id="40148-160">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="40148-160">NOT NULL</span></span>|<span data-ttu-id="40148-161">表示資料行不能包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="40148-161">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="40148-162">如果 Analysis Services 在模型定型期間遇到 Null 值，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="40148-162">An error will result if Analysis Services encounters a null during model training.</span></span><br /><br /> <span data-ttu-id="40148-163">適用於採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="40148-163">Applies to mining structure column.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40148-164">需求</span><span class="sxs-lookup"><span data-stu-id="40148-164">Requirements</span></span>  
 <span data-ttu-id="40148-165">貝氏機率分類樹狀模型必須包含索引鍵資料行、至少一個可預測屬性，以及至少一個輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="40148-165">A Naive Bayes tree model must contain a key column, at least one predictable attribute, and at least one input attribute.</span></span> <span data-ttu-id="40148-166">任何屬性都不得為連續的；如果您的資料包含連續數值資料，將會忽略或離散化該資料。</span><span class="sxs-lookup"><span data-stu-id="40148-166">No attribute can be continuous; if your data contains continuous numeric data, it will be ignored or discretized.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="40148-167">輸入和可預測資料行</span><span class="sxs-lookup"><span data-stu-id="40148-167">Input and Predictable Columns</span></span>  
 <span data-ttu-id="40148-168">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法支援下表所列的特定輸入資料行和可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="40148-168">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="40148-169">如需內容類型用於採礦模型時所代表意義的詳細資訊，請參閱[內容類型 &#40;資料採礦&#41;](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="40148-169">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="40148-170">資料行</span><span class="sxs-lookup"><span data-stu-id="40148-170">Column</span></span>|<span data-ttu-id="40148-171">內容類型</span><span class="sxs-lookup"><span data-stu-id="40148-171">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="40148-172">輸入屬性</span><span class="sxs-lookup"><span data-stu-id="40148-172">Input attribute</span></span>|<span data-ttu-id="40148-173">Cyclical、Discrete、Discretized、Key、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="40148-173">Cyclical, Discrete, Discretized, Key, Table, and Ordered</span></span>|  
|<span data-ttu-id="40148-174">可預測屬性</span><span class="sxs-lookup"><span data-stu-id="40148-174">Predictable attribute</span></span>|<span data-ttu-id="40148-175">Cyclical、Discrete、Discretized、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="40148-175">Cyclical, Discrete, Discretized, Table, and Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="40148-176">系統支援 Cyclical 和 Ordered 內容類型，但是演算法將它們視為離散值，因此不會執行特殊處理。</span><span class="sxs-lookup"><span data-stu-id="40148-176">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40148-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40148-177">See Also</span></span>  
 <span data-ttu-id="40148-178">[Microsoft 貝氏貝氏機率分類演算法](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="40148-178">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 <span data-ttu-id="40148-179">[貝氏貝氏機率分類模型查詢範例](naive-bayes-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="40148-179">[Naive Bayes Model Query Examples](naive-bayes-model-query-examples.md) </span></span>  
 [<span data-ttu-id="40148-180">貝氏機率分類模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="40148-180">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
