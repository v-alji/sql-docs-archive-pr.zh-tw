---
title: Microsoft 關聯分析演算法技術參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_ITEMSET_SIZE parameter
- MAXIMUM_SUPPORT parameter
- association algorithms [Analysis Services]
- MINIMUM_SUPPORT parameter
- OPTIMIZED_PREDICTION_COUNT parameter
- associations [Analysis Services]
- MAXIMUM_ITEMSET_COUNT parameter
- MAXIMUM_ITEMSET_SIZE parameter
- MINIMUM_PROBABILITY parameter
ms.assetid: 50a22202-e936-4995-ae1d-4ff974002e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: eac813711aafc714edef6acc98cda612dd879549
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593668"
---
# <a name="microsoft-association-algorithm-technical-reference"></a><span data-ttu-id="fd8c2-102">Microsoft 關聯分析演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="fd8c2-102">Microsoft Association Algorithm Technical Reference</span></span>
  <span data-ttu-id="fd8c2-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則演算法是有名的 Apriori 演算法的簡單實作。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm is a straightforward implementation of the well-known Apriori algorithm.</span></span>  
  
 <span data-ttu-id="fd8c2-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則演算法都可用來分析關聯，但每個演算法所找到的規則都可能不同。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-104">Both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm can be used to analyze associations, but the rules that are found by each algorithm can differ.</span></span> <span data-ttu-id="fd8c2-105">在決策樹模型中，導致特定規則的分岔是根據資訊改善而定，在關聯模型中，規則則是完全根據信心而定。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-105">In a decision trees model, the splits that lead to specific rules are based on information gain, whereas in an association model, rules are based completely on confidence.</span></span> <span data-ttu-id="fd8c2-106">因此，在關聯模型中，強大的規則或具有高信心指數的規則可能因為沒有提供新資訊而不具有高「有趣性」。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-106">Therefore, in an association model, a strong rule, or one that has high confidence, might not necessarily be interesting because it does not provide new information.</span></span>  
  
## <a name="implementation-of-the-microsoft-association-algorithm"></a><span data-ttu-id="fd8c2-107">Microsoft 關聯分析演算法的實作</span><span class="sxs-lookup"><span data-stu-id="fd8c2-107">Implementation of the Microsoft Association Algorithm</span></span>  
 <span data-ttu-id="fd8c2-108">Apriori 演算法並不會分析模式，而是產生「候選項目集」\*\* 並接著加以計算。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-108">The Apriori algorithm does not analyze patterns, but rather generates and then counts *candidate itemsets*.</span></span> <span data-ttu-id="fd8c2-109">項目可能代表事件、產品或屬性的值，根據分析的資料類型而定。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-109">An item can represent an event, a product, or the value of an attribute, depending on the type of data that is being analyzed.</span></span>  
  
 <span data-ttu-id="fd8c2-110">在常見類型的關聯模型中，代表「是/否」或「遺漏/現有」值的布林值變數會指派給每個屬性，例如產品或事件名稱。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-110">In the most common type of association model Boolean variables, representing a Yes/No or Missing/Existing value, are assigned to each attribute, such as a product or event name.</span></span> <span data-ttu-id="fd8c2-111">購物籃分析是關聯規則模型的其中一個範例，該模型使用布林值變數代表客戶購物籃中的特定產品是否存在。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-111">A market basket analysis is an example of an association rules model that uses Boolean variables to represent the presence or absence of particular products in a customer's shopping basket.</span></span>  
  
 <span data-ttu-id="fd8c2-112">接著，演算法會針對每個項目集建立代表支援及信心的分數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-112">For each itemset, the algorithm then creates scores that represent support and confidence.</span></span> <span data-ttu-id="fd8c2-113">這些分數可用來從項目集衍生有趣性規則並排列其次序。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-113">These scores can be used to rank and derive interesting rules from the itemsets.</span></span>  
  
 <span data-ttu-id="fd8c2-114">您也可以針對數值屬性建立關聯模型。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-114">Association models can also be created for numerical attributes.</span></span> <span data-ttu-id="fd8c2-115">如果是連續屬性，可以將數字「分隔」\*\* 或群組到值區中。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-115">If the attributes are continuous, the numbers can be *discretized, or* grouped in buckets.</span></span> <span data-ttu-id="fd8c2-116">接著就可以將離散化的值當做布林值或屬性值配對處理。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-116">The discretized values can then be handled either as Booleans or as attribute-value pairs.</span></span>  
  
### <a name="support-probability-and-importance"></a><span data-ttu-id="fd8c2-117">支援、機率和重要性</span><span class="sxs-lookup"><span data-stu-id="fd8c2-117">Support, Probability, and Importance</span></span>  
 <span data-ttu-id="fd8c2-118">「支援」**(有時也稱為「頻率」**) 代表包含目標項目或項目組合的案例數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-118">*Support*, which issometimes referred to as *frequency*, means the number of cases that contain the targeted item or combination of items.</span></span> <span data-ttu-id="fd8c2-119">只有至少具有指定支援量的項目才能包含在模型中。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-119">Only items that have at least the specified amount of support can be included in the model.</span></span>  
  
 <span data-ttu-id="fd8c2-120">「常見項目集」\*\* 代表項目的集合，其中的項目組合也具有 MINIMUM_SUPPORT 參數所定義臨界值以上的支援。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-120">A *frequent itemset* refers to a collection of items where the combination of items also has support above the threshold defined by the MINIMUM_SUPPORT parameter.</span></span> <span data-ttu-id="fd8c2-121">例如，如果項目集為 {A,B,C} 而 MINIMUM_SUPPORT 值為 10，則每個個別的 A、B 及 C 項目都必須至少存在於模型所含的 10 個案例中，且項目組合 {A,B,C} 也必須存在於至少 10 個案例中。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-121">For example, if the itemset is {A,B,C} and the MINIMUM_SUPPORT value is 10, each individual item A, B, and C must be found in at least 10 cases to be included in the model, and the combination of items {A,B,C} must also be found in at least 10 cases.</span></span>  
  
 <span data-ttu-id="fd8c2-122">**注意** ：您也可以指定項目集的最大長度 (長度代表項目數) 來控制採礦模型中的項目集數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-122">**Note** You can also control the number of itemsets in a mining model by specifying the maximum length of an itemset, where length means the number of items.</span></span>  
  
 <span data-ttu-id="fd8c2-123">根據預設，任何特定項目或項目集的支援都代表包含該項目或項目集的案例計數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-123">By default, the support for any particular item or itemset represents a count of the cases that contain that item or items.</span></span> <span data-ttu-id="fd8c2-124">不過，您也可以將數字輸入為小於 1 的小數值，將 MINIMUM_SUPPORT 表示為資料集總案例數的百分比。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-124">However, you can also express MINIMUM_SUPPORT as a percentage of the total cases in the data set, by typing the number as a decimal value less than 1.</span></span> <span data-ttu-id="fd8c2-125">例如，如果將 MINIMUM_SUPPORT 值指定為 0.03，該值代表資料集中至少有 3% 的總案例數必須包含此項目或項目集，才能加入模型。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-125">For example, if you specify a MINIMUM_SUPPORT value of 0.03, it means that at least 3% of the total cases in the data set must contain this item or itemset for inclusion in the model.</span></span> <span data-ttu-id="fd8c2-126">您應該試用模型，以判斷是計數或是百分比比較適用。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-126">You should experiment with your model to determine whether using a count or percentage makes more sense.</span></span>  
  
 <span data-ttu-id="fd8c2-127">相反地，規則的臨界值不會表示為計數或百分比，而是以機率表示，這有時也稱為「信心」\*\*。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-127">In contrast, the threshold for rules is expressed not as a count or percentage, but as a probability, sometimes referred to as *confidence*.</span></span> <span data-ttu-id="fd8c2-128">例如，如果項目集 {A,B,C} 出現在 50 個案例中，但項目 {A,B,D} 也出現在 50 個案例中，而項目集 {A,B} 則出現在另外 50 個案例中，則很明顯地 {A,B} 並不能準確地預測 {C}。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-128">For example, if the itemset {A,B,C} occurs in 50 cases, but the itemset {A,B,D} also occurs in 50 cases, and the itemset {A,B} in another 50 cases, it is obvious that {A,B} is not a strong predictor of {C}.</span></span> <span data-ttu-id="fd8c2-129">因此，為了針對所有已知結果來計算特定結果的加權， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會使用項目集 {A,B,C} 的支援除以所有相關項目集的支援來計算個別規則的機率 (例如 If {A,B} Then {C})。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-129">Therefore, to weight a particular outcomes against all known outcomes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calculates the probability of the individual rule (such as If {A,B} Then {C}) by dividing the support for the itemset {A,B,C} by the support for all related itemsets.</span></span>  
  
 <span data-ttu-id="fd8c2-130">您也可以藉由設定 MINIMUM_PROBABILITY 的值來限制模型所產生的規則數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-130">You can restrict the number of rules that a model produces by setting a value for MINIMUM_PROBABILITY.</span></span>  
  
 <span data-ttu-id="fd8c2-131">對於每個建立的規則，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 都會輸出分數指出其「重要性」**，也稱為「增益」**。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-131">For each rule that is created, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] outputs a score that indicates its *importance*, which is alsoreferred to as *lift*.</span></span> <span data-ttu-id="fd8c2-132">項目集和規則的增益重要性計算方式不同。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-132">Lift Importance is calculated differently for itemsets and rules.</span></span>  
  
 <span data-ttu-id="fd8c2-133">項目集的重要性計算方式是用項目集的機率除以項目集中個別項目的複合機率。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-133">The importance of an itemset is calculated as the probability of the itemset divided by the compound probability of the individual items in the itemset.</span></span> <span data-ttu-id="fd8c2-134">例如，如果項目集包含 {A,B}，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會先計算所有包含此 A 和 B 組合的案例數，並將該值除以總案例數，然後再正規化為機率。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-134">For example, if an itemset contains {A,B}, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] first counts all the cases that contain this combination A and B, and divides that by the total number of cases, and then normalizes the probability.</span></span>  
  
 <span data-ttu-id="fd8c2-135">規則的重要性則是在已知規則左側的情況下，用規則右側的對數可能性來計算。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-135">The importance of a rule is calculated by the log likelihood of the right-hand side of the rule, given the left-hand side of the rule.</span></span> <span data-ttu-id="fd8c2-136">例如，在規則 `If {A} Then {B}`中， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會計算具有 A 和 B 的案例對於具有 B 但沒有 A 的案例的比率，然後再使用對數刻度將該比率正規化。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-136">For example, in the rule `If {A} Then {B}`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calculates the ratio of cases with A and B over cases with B but without A, and then normalizes that ratio by using a logarithmic scale.</span></span>  
  
### <a name="feature-selection"></a><span data-ttu-id="fd8c2-137">特徵選取</span><span class="sxs-lookup"><span data-stu-id="fd8c2-137">Feature Selection</span></span>  
 <span data-ttu-id="fd8c2-138">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則演算法不會執行任何類型的自動特徵選取，</span><span class="sxs-lookup"><span data-stu-id="fd8c2-138">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm does not perform any kind of automatic feature selection.</span></span> <span data-ttu-id="fd8c2-139">而是提供參數來控制演算法所使用的資料。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-139">Instead, the algorithm provides parameters that control the data that is used by the algorithm.</span></span> <span data-ttu-id="fd8c2-140">這可能包含每個項目集大小的限制，或者將項目集加入至模型時所需最大及最小支援的設定。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-140">This might include limits on the size of each itemset, or setting the maximum and minimum support required to add an itemset to the model.</span></span>  
  
-   <span data-ttu-id="fd8c2-141">若要篩選出太平常以致於不有趣的項目集事件，請減少 MAXIMUM_SUPPORT 的值，以從模型中移除太常出現的項目集。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-141">To filter out items and events that are too common and therefore uninteresting, decrease the value of MAXIMUM_SUPPORT to remove very frequent itemsets from the model.</span></span>  
  
-   <span data-ttu-id="fd8c2-142">若要篩選出很少見的項目和項目集，請增加 MINIMUM_SUPPORT 的值。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-142">To filter out items and itemsets that are rare, increase the value of MINIMUM_SUPPORT.</span></span>  
  
-   <span data-ttu-id="fd8c2-143">若要篩選出規則，請增加 MINIMUM_PROBABILITY 的值。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-143">To filter out rules, increase the value of MINIMUM_PROBABILITY.</span></span>  
  
## <a name="customizing-the-microsoft-association-rules-algorithm"></a><span data-ttu-id="fd8c2-144">自訂 Microsoft 關聯規則演算法</span><span class="sxs-lookup"><span data-stu-id="fd8c2-144">Customizing the Microsoft Association Rules Algorithm</span></span>  
 <span data-ttu-id="fd8c2-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則演算法支援數個會影響所產生之採礦模型的行為、效能和精確度的參數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-145">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="fd8c2-146">設定演算法參數</span><span class="sxs-lookup"><span data-stu-id="fd8c2-146">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="fd8c2-147">您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的資料採礦設計師，隨時變更採礦模型的參數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-147">You can change the parameters for a mining model at any time by using the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="fd8c2-148">您也可以使用 AMO 中的集合以程式設計方式變更參數 <xref:Microsoft.AnalysisServices.MiningModel.AlgorithmParameters%2A> ，或在 XMLA 中使用[MiningModels 元素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/collections/miningmodels-element-assl) 。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-148">You can also change parameters programmatically by using the <xref:Microsoft.AnalysisServices.MiningModel.AlgorithmParameters%2A> collection in AMO, or by using the [MiningModels Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/collections/miningmodels-element-assl) in XMLA.</span></span> <span data-ttu-id="fd8c2-149">下表描述每一個參數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-149">The following table describes each parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd8c2-150">您不能使用 DMX 語句變更現有模型中的參數;您必須在 DMX CREATE MODEL 或 ALTER STRUCTURE 中指定參數 .。。當您建立模型時，加入模型。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-150">You cannot change the parameters in an existing model by using a DMX statement; you must specify the parameters in the DMX CREATE MODEL or ALTER STRUCTURE... ADD MODEL when you create the model.</span></span>  
  
 <span data-ttu-id="fd8c2-151">*MAXIMUM_ITEMSET_COUNT*</span><span class="sxs-lookup"><span data-stu-id="fd8c2-151">*MAXIMUM_ITEMSET_COUNT*</span></span>  
 <span data-ttu-id="fd8c2-152">指定要產生的最大項目集數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-152">Specifies the maximum number of itemsets to produce.</span></span> <span data-ttu-id="fd8c2-153">如果沒有指定任何數目，則會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-153">If no number is specified, the default value is used.</span></span>  
  
 <span data-ttu-id="fd8c2-154">預設值是 200000。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-154">The default is 200000.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd8c2-155">項目集是由支援排序。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-155">Itemsets are ranked by support.</span></span> <span data-ttu-id="fd8c2-156">在擁有相同支援的項目集中具有任意的排序。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-156">Among itemsets that have the same support, ordering is arbitrary.</span></span>  
  
 <span data-ttu-id="fd8c2-157">*MAXIMUM_ITEMSET_SIZE*</span><span class="sxs-lookup"><span data-stu-id="fd8c2-157">*MAXIMUM_ITEMSET_SIZE*</span></span>  
 <span data-ttu-id="fd8c2-158">指定項目集內所允許的最大項目數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-158">Specifies the maximum number of items that are allowed in an itemset.</span></span> <span data-ttu-id="fd8c2-159">將此值設定為 0，即代表項目集沒有大小限制。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-159">Setting this value to 0 specifies that there is no limit to the size of the itemset.</span></span>  
  
 <span data-ttu-id="fd8c2-160">預設值為 3。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-160">The default is 3.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd8c2-161">減少這個值可能會縮短建立模型所需的時間，因為在達到限制時，模型的處理就會停止。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-161">Decreasing this value can potentially reduce the time that is required for creating the model, because processing of the model stops when the limit is reached.</span></span>  
  
 <span data-ttu-id="fd8c2-162">*MAXIMUM_SUPPORT*</span><span class="sxs-lookup"><span data-stu-id="fd8c2-162">*MAXIMUM_SUPPORT*</span></span>  
 <span data-ttu-id="fd8c2-163">指定項目集可支援的最大案例數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-163">Specifies the maximum number of cases that an itemset has for support.</span></span> <span data-ttu-id="fd8c2-164">這個參數可用來排除經常出現的項目，因此可能沒有什麼意義。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-164">This parameter can be used to eliminate items that appear frequently and therefore potentially have little meaning.</span></span>  
  
 <span data-ttu-id="fd8c2-165">如果此值小於 1，則此值代表總案例數的百分比。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-165">If this value is less than 1, the value represents a percentage of the total cases.</span></span> <span data-ttu-id="fd8c2-166">大於 1 的值代表可包含項目集的絕對案例數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-166">Values greater than 1 represent the absolute number of cases that can contain the itemset.</span></span>  
  
 <span data-ttu-id="fd8c2-167">預設值是 1。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-167">The default is 1.</span></span>  
  
 <span data-ttu-id="fd8c2-168">*MINIMUM_ITEMSET_SIZE*</span><span class="sxs-lookup"><span data-stu-id="fd8c2-168">*MINIMUM_ITEMSET_SIZE*</span></span>  
 <span data-ttu-id="fd8c2-169">指定項目集內所允許的最小項目數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-169">Specifies the minimum number of items that are allowed in an itemset.</span></span> <span data-ttu-id="fd8c2-170">如果增加此數目，模型可能會包含較少的項目集。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-170">If you increase this number, the model might contain fewer itemsets.</span></span> <span data-ttu-id="fd8c2-171">如果您要忽略單一項目的項目集，舉例來說，則這會很有用。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-171">This can be useful if you want to ignore single-item itemsets, for example.</span></span>  
  
 <span data-ttu-id="fd8c2-172">預設值是 1。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-172">The default is 1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd8c2-173">您不能藉由增加最小值來縮短模型處理時間，因為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在處理中仍需計算單一項目的機率。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-173">You cannot reduce model processing time by increasing the minimum value, because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] must calculate probabilities for single items anyway as part of processing.</span></span> <span data-ttu-id="fd8c2-174">不過，將此值設定為較高的值可讓您篩選出較小的項目集。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-174">However, by setting this value higher you can filter out smaller itemsets.</span></span>  
  
 <span data-ttu-id="fd8c2-175">*MINIMUM_PROBABILITY*</span><span class="sxs-lookup"><span data-stu-id="fd8c2-175">*MINIMUM_PROBABILITY*</span></span>  
 <span data-ttu-id="fd8c2-176">指定規則成立的最小機率。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-176">Specifies the minimum probability that a rule is true.</span></span>  
  
 <span data-ttu-id="fd8c2-177">例如，如果將此值設定為 0.5，則代表不能產生任何機率小於 50% 的規則。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-177">For example, if you set this value to 0.5, it means that no rule with less than fifty percent probability can be generated.</span></span>  
  
 <span data-ttu-id="fd8c2-178">預設值是 0.4。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-178">The default is 0.4.</span></span>  
  
 <span data-ttu-id="fd8c2-179">*MINIMUM_SUPPORT*</span><span class="sxs-lookup"><span data-stu-id="fd8c2-179">*MINIMUM_SUPPORT*</span></span>  
 <span data-ttu-id="fd8c2-180">指定演算法產生規則之前必須包含項目集的最小案例數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-180">Specifies the minimum number of cases that must contain the itemset before the algorithm generates a rule.</span></span>  
  
 <span data-ttu-id="fd8c2-181">如果將此值設定為小於 1，則會以總案例數的百分比來計算最小案例數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-181">If you set this value to less than 1, the minimum number of cases is calculated as a percentage of the total cases.</span></span>  
  
 <span data-ttu-id="fd8c2-182">如果將此值設定為大於 1 的整數，則會以必須包含項目集的案例計數來計算最小案例數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-182">If you set this value to a whole number greater than 1, specifies the minimum number of cases is calculated as a count of cases that must contain the itemset.</span></span> <span data-ttu-id="fd8c2-183">如果記憶體有限，演算法可自動增加此參數的值。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-183">The algorithm might automatically increase the value of this parameter if memory is limited.</span></span>  
  
 <span data-ttu-id="fd8c2-184">預設值是 0.03。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-184">The default is 0.03.</span></span> <span data-ttu-id="fd8c2-185">也就是說只有至少具有 3% 案例的項目集才能包含在模型中。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-185">This means that to be included in the model, an itemset must be found in at least 3% of cases.</span></span>  
  
 <span data-ttu-id="fd8c2-186">*OPTIMIZED_PREDICTION_COUNT*</span><span class="sxs-lookup"><span data-stu-id="fd8c2-186">*OPTIMIZED_PREDICTION_COUNT*</span></span>  
 <span data-ttu-id="fd8c2-187">定義要達成最佳化預測所進行快取的項目數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-187">Defines the number of items to be cached for optimizing prediction.</span></span>  
  
 <span data-ttu-id="fd8c2-188">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-188">The default value is 0.</span></span> <span data-ttu-id="fd8c2-189">使用預設值時，演算法將會在查詢中產生所要求的預測數目。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-189">When the default is used, the algorithm will produce as many predictions as requested in the query.</span></span>  
  
 <span data-ttu-id="fd8c2-190">如果您為 *OPTIMIZED_PREDICTION_COUNT,* 指定非零值，即使您要求更多的預測，預測查詢最多也只能傳回指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-190">If you specify a nonzero value for *OPTIMIZED_PREDICTION_COUNT,* prediction queries can return at most the specified number of items, even if you request additional predictions.</span></span> <span data-ttu-id="fd8c2-191">不過，設定一個值可以增強預測效能。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-191">However, setting a value can improve prediction performance.</span></span>  
  
 <span data-ttu-id="fd8c2-192">例如，如果值設定為 3，則演算法只會快取 3 個項目進行預測。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-192">For example, if the value is set to 3, the algorithm caches only 3 items for prediction.</span></span> <span data-ttu-id="fd8c2-193">您將不會看到其他可能等同所傳回之 3 個項目的預測。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-193">You cannot see additional predictions that might be equally probable to the 3 items that are returned.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="fd8c2-194">模型旗標</span><span class="sxs-lookup"><span data-stu-id="fd8c2-194">Modeling Flags</span></span>  
 <span data-ttu-id="fd8c2-195">下列模型旗標受到支援，可用於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則演算法。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-195">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span>  
  
 <span data-ttu-id="fd8c2-196">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="fd8c2-196">NOT NULL</span></span>  
 <span data-ttu-id="fd8c2-197">表示資料行不能包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-197">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="fd8c2-198">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在模型定型期間遇到 Null 值，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-198">An error will result if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a null during model training.</span></span>  
  
 <span data-ttu-id="fd8c2-199">適用於採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-199">Applies to the mining structure column.</span></span>  
  
 <span data-ttu-id="fd8c2-200">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="fd8c2-200">MODEL_EXISTENCE_ONLY</span></span>  
 <span data-ttu-id="fd8c2-201">表示資料行將被視為擁有兩個可能狀態：`Missing` 和 `Existing`。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-201">Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="fd8c2-202">Null 為遺漏值。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-202">A null is a missing value.</span></span>  
  
 <span data-ttu-id="fd8c2-203">適用於採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-203">Applies to the mining model column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd8c2-204">需求</span><span class="sxs-lookup"><span data-stu-id="fd8c2-204">Requirements</span></span>  
 <span data-ttu-id="fd8c2-205">關聯模型必須包含索引鍵資料行、輸入資料行和單一的可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-205">An association model must contain a key column, input columns, and a single predictable column.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="fd8c2-206">輸入和可預測資料行</span><span class="sxs-lookup"><span data-stu-id="fd8c2-206">Input and Predictable Columns</span></span>  
 <span data-ttu-id="fd8c2-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則演算法支援下表所列的特定輸入資料行和可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-207">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="fd8c2-208">如需採礦模型中內容類型意義的詳細資訊，請參閱[內容類型 &#40;資料採礦&#41;](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-208">For more information about the meaning of content types in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="fd8c2-209">資料行</span><span class="sxs-lookup"><span data-stu-id="fd8c2-209">Column</span></span>|<span data-ttu-id="fd8c2-210">內容類型</span><span class="sxs-lookup"><span data-stu-id="fd8c2-210">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="fd8c2-211">輸入屬性</span><span class="sxs-lookup"><span data-stu-id="fd8c2-211">Input attribute</span></span>|<span data-ttu-id="fd8c2-212">Cyclical、Discrete、Discretized、Key、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="fd8c2-212">Cyclical, Discrete, Discretized, Key, Table, Ordered</span></span>|  
|<span data-ttu-id="fd8c2-213">可預測屬性</span><span class="sxs-lookup"><span data-stu-id="fd8c2-213">Predictable attribute</span></span>|<span data-ttu-id="fd8c2-214">Cyclical、Discrete、Discretized、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="fd8c2-214">Cyclical, Discrete, Discretized, Table, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="fd8c2-215">系統支援 Cyclical 和 Ordered 內容類型，但是演算法將它們視為離散值，因此不會執行特殊處理。</span><span class="sxs-lookup"><span data-stu-id="fd8c2-215">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8c2-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd8c2-216">See Also</span></span>  
 <span data-ttu-id="fd8c2-217">[Microsoft 關聯分析演算法](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="fd8c2-217">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="fd8c2-218">[關聯模型查詢範例](association-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="fd8c2-218">[Association Model Query Examples](association-model-query-examples.md) </span></span>  
 [<span data-ttu-id="fd8c2-219">關聯模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fd8c2-219">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
