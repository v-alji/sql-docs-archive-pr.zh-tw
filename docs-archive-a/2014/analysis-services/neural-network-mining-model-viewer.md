---
title: 類神經網路 (採礦模型檢視器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.neuralnet.f1
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 39ca8d3cd9f2a327abd8558b13a018ceda27968d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594726"
---
# <a name="neural-network-mining-model-viewer"></a><span data-ttu-id="027a9-102">類神經網路 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="027a9-102">Neural Network (Mining Model Viewer)</span></span>
  <span data-ttu-id="027a9-103">使用 **[類神經網路]** 檢視器，即可探索以 [!INCLUDE[msCoName](../includes/msconame-md.md)] 類神經網路演算法或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 羅吉斯迴歸演算法為基礎的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="027a9-103">Use the **Neural Net** viewer to explore mining models that are based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network algorithm or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="027a9-104">\*\*如需詳細資訊，請參閱 \*\* [Microsoft 類神經網路演算法](data-mining/microsoft-neural-network-algorithm.md)、[Microsoft 羅吉斯迴歸演算法](data-mining/microsoft-logistic-regression-algorithm.md)、[使用 Microsoft 類神經網路檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="027a9-104">**For More Information:** [Microsoft Neural Network Algorithm](data-mining/microsoft-neural-network-algorithm.md), [Microsoft Logistic Regression Algorithm](data-mining/microsoft-logistic-regression-algorithm.md),[Browse a Model Using the Microsoft Neural Network Viewer](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="027a9-105">選項</span><span class="sxs-lookup"><span data-stu-id="027a9-105">Options</span></span>  
 <span data-ttu-id="027a9-106">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="027a9-106">**Refresh viewer content**</span></span>  
 <span data-ttu-id="027a9-107">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="027a9-107">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="027a9-108">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="027a9-108">**Mining Model**</span></span>  
 <span data-ttu-id="027a9-109">在目前採礦結構中選擇要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="027a9-109">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="027a9-110">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="027a9-110">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="027a9-111">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="027a9-111">**Viewer**</span></span>  
 <span data-ttu-id="027a9-112">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="027a9-112">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="027a9-113">可以使用自訂檢視器，或 **[Microsoft 一般內容樹狀檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="027a9-113">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="027a9-114">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="027a9-114">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="027a9-115">**輸入**</span><span class="sxs-lookup"><span data-stu-id="027a9-115">**Input**</span></span>  
 <span data-ttu-id="027a9-116">使用此區域選擇輸入屬性和值，以便您稍後可以探索它們如何影響結果。</span><span class="sxs-lookup"><span data-stu-id="027a9-116">Use this area to choose input attributes and values, so that you can later explore how these affect the outcome.</span></span>  
  
|<span data-ttu-id="027a9-117">值</span><span class="sxs-lookup"><span data-stu-id="027a9-117">Value</span></span>|<span data-ttu-id="027a9-118">描述</span><span class="sxs-lookup"><span data-stu-id="027a9-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="027a9-119">**屬性**</span><span class="sxs-lookup"><span data-stu-id="027a9-119">**Attribute**</span></span>|<span data-ttu-id="027a9-120">從清單選擇輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="027a9-120">Choose an input attribute from the list.</span></span> <span data-ttu-id="027a9-121">如果您將選取專案保留為預設值， **\<All>** 則圖表會顯示所有輸入屬性的清單，並依其對可預測屬性的影響進行排序。</span><span class="sxs-lookup"><span data-stu-id="027a9-121">If you leave the selection as the default, **\<All>**, the chart shows a list of all input attributes, ranked by their impact on the predictable attribute.</span></span>|  
|<span data-ttu-id="027a9-122">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="027a9-122">**Value**</span></span>|<span data-ttu-id="027a9-123">選擇輸入屬性的值。</span><span class="sxs-lookup"><span data-stu-id="027a9-123">Choose a value for the input attribute.</span></span>|  
  
 <span data-ttu-id="027a9-124">**輸出**</span><span class="sxs-lookup"><span data-stu-id="027a9-124">**Output**</span></span>  
 <span data-ttu-id="027a9-125">使用這些控制項，選擇要在橫條圖中分析和比較的可預測屬性和值。</span><span class="sxs-lookup"><span data-stu-id="027a9-125">Use these controls to choose a predictable attribute and value to analyze and compare in the bar graph.</span></span> <span data-ttu-id="027a9-126">如果您未變更選取項目，則橫條圖會比較最上面的兩個結果狀態。</span><span class="sxs-lookup"><span data-stu-id="027a9-126">If you do not change the selections, the bar graph compares the top two outcome states.</span></span>  
  
|<span data-ttu-id="027a9-127">值</span><span class="sxs-lookup"><span data-stu-id="027a9-127">Value</span></span>|<span data-ttu-id="027a9-128">描述</span><span class="sxs-lookup"><span data-stu-id="027a9-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="027a9-129">**輸出屬性**</span><span class="sxs-lookup"><span data-stu-id="027a9-129">**Output Attribute**</span></span>|<span data-ttu-id="027a9-130">選擇可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="027a9-130">Choose a predictable attribute.</span></span> <span data-ttu-id="027a9-131">如果您在建立模型時未將資料行定義為可預測資料行，則無法在此處新增它。</span><span class="sxs-lookup"><span data-stu-id="027a9-131">If you did not define the column as a predictable one when you created the model, you cannot add it here.</span></span>|  
|<span data-ttu-id="027a9-132">**值 1**</span><span class="sxs-lookup"><span data-stu-id="027a9-132">**Value 1**</span></span>|<span data-ttu-id="027a9-133">選擇一種可預測屬性狀態，和 **[值 2]** 裡包含的狀態進行比較。</span><span class="sxs-lookup"><span data-stu-id="027a9-133">Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.</span></span><br /><br /> <span data-ttu-id="027a9-134">可以比較任兩個離散或離散化值；但無法像在其他檢視器中一樣，比較值與其補數。</span><span class="sxs-lookup"><span data-stu-id="027a9-134">You can compare any two discrete or discretized values; however, you cannot compare a value to its complement, as you can in other viewers.</span></span>|  
|<span data-ttu-id="027a9-135">**值2**</span><span class="sxs-lookup"><span data-stu-id="027a9-135">**Value 2**</span></span>|<span data-ttu-id="027a9-136">選取一種可預測屬性狀態，和 **[值 1]** 裡包含的狀態進行比較。</span><span class="sxs-lookup"><span data-stu-id="027a9-136">Select a state of the predictable attribute to compare to the state that is contained in **Value 1**.</span></span>|  
  
 <span data-ttu-id="027a9-137">**變數**</span><span class="sxs-lookup"><span data-stu-id="027a9-137">**Variables**</span></span>  
 <span data-ttu-id="027a9-138">[類神經網路]\*\*\*\* 索引標籤的此部分包含互動式橫條圖，該圖會對您選擇的輸入和結果屬性進行回應。</span><span class="sxs-lookup"><span data-stu-id="027a9-138">This part of the **Neural Network** tab contains an interactive bar graph, which responds to the selections that you made for input and outcome attributes.</span></span> <span data-ttu-id="027a9-139">因為類神經網路會計算某個特定值影響特定結果的可能性，所以您可以選擇任何輸入組合，橫條圖就會顯示該組合如何影響一組要比較的結果。</span><span class="sxs-lookup"><span data-stu-id="027a9-139">Because a neural network calculates the likelihood that a particular value influences a particular outcome, you can choose any combination of inputs, and the bar chart will display how that combination affects the pair of outcomes that you are comparing.</span></span>  
  
|<span data-ttu-id="027a9-140">值</span><span class="sxs-lookup"><span data-stu-id="027a9-140">Value</span></span>|<span data-ttu-id="027a9-141">描述</span><span class="sxs-lookup"><span data-stu-id="027a9-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="027a9-142">**屬性**</span><span class="sxs-lookup"><span data-stu-id="027a9-142">**Attribute**</span></span>|<span data-ttu-id="027a9-143">顯示您在 **[屬性]** 中所選取輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="027a9-143">Shows the name of the input attribute you selected in **Attribute**.</span></span>|  
|<span data-ttu-id="027a9-144">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="027a9-144">**Value**</span></span>|<span data-ttu-id="027a9-145">顯示所選取輸入屬性的值。</span><span class="sxs-lookup"><span data-stu-id="027a9-145">Shows the value for the selected input attribute.</span></span>|  
|<span data-ttu-id="027a9-146">**照顧\<Value 1>**</span><span class="sxs-lookup"><span data-stu-id="027a9-146">**Favors \<Value 1>**</span></span>|<span data-ttu-id="027a9-147">顯示長條，該圖表示此特定屬性/值組合對 [值 1]\*\*\*\* 中選擇的目標結果有多大影響。</span><span class="sxs-lookup"><span data-stu-id="027a9-147">Displays a bar that indicates how much this particular attribute-value combination affects the target outcome chosen in **Value 1**.</span></span>|  
|<span data-ttu-id="027a9-148">**照顧\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="027a9-148">**Favors \<Value 2>**</span></span>|<span data-ttu-id="027a9-149">顯示長條，該圖表示此特定屬性/值組合對 [值 2]\*\*\*\* 中選擇的目標結果有多大影響。</span><span class="sxs-lookup"><span data-stu-id="027a9-149">Displays a bar that indicates how much this particular attribute-value combination affects the target outcome chosen in **Value 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="027a9-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="027a9-150">See Also</span></span>  
 <span data-ttu-id="027a9-151">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="027a9-151">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="027a9-152">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="027a9-152">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="027a9-153">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="027a9-153">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
