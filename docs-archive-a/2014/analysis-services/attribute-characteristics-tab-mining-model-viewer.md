---
title: 屬性特性索引標籤 () 的採礦模型檢視器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
ms.openlocfilehash: b29ba482c21bb674a10bc4c9e6c6eccdf30905dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593178"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="c0c07-102">屬性特性索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="c0c07-102">Attribute Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="c0c07-103">可以使用 [屬性特性]\*\*\*\* 窗格，瀏覽貝氏機率分類模型中結果和輸入屬性之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="c0c07-103">Use the **Attribute Characteristics** pane to explore the relationships between outcomes and input attributes in a Naïve Bayes model.</span></span> <span data-ttu-id="c0c07-104">可以選擇目標屬性的值，然後查看對結果造成最大影響的輸入屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="c0c07-104">You can choose the value of the target attribute, and then see a list of the input attributes that have the strongest effect on the outcomes.</span></span>  
  
 <span data-ttu-id="c0c07-105">\*\*如需詳細資訊，請參閱 \*\* [Microsoft 貝氏機率分類演算法](data-mining/microsoft-naive-bayes-algorithm.md)、[使用 Microsoft 貝氏機率分類檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="c0c07-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0c07-106">選項</span><span class="sxs-lookup"><span data-stu-id="c0c07-106">Options</span></span>  
 <span data-ttu-id="c0c07-107">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="c0c07-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="c0c07-108">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="c0c07-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="c0c07-109">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="c0c07-109">**Mining Model**</span></span>  
 <span data-ttu-id="c0c07-110">在目前採礦結構中選擇要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="c0c07-110">Choose a mining model to view, from the models in the current mining structure.</span></span> <span data-ttu-id="c0c07-111">採礦模型會自動在最適合所選特定模型類型的自訂檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="c0c07-111">The mining model will automatically open in a custom viewer that is best for the particular type of model you chose.</span></span>  
  
 <span data-ttu-id="c0c07-112">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="c0c07-112">**Viewer**</span></span>  
 <span data-ttu-id="c0c07-113">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="c0c07-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="c0c07-114">可以為每個模型選擇自訂檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。</span><span class="sxs-lookup"><span data-stu-id="c0c07-114">For each model, you have the choice of a custom viewer, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="c0c07-115">此清單中也會出現外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="c0c07-115">Plug-in viewers also appear in this list if available.</span></span>  
  
 <span data-ttu-id="c0c07-116">**屬性**</span><span class="sxs-lookup"><span data-stu-id="c0c07-116">**Attribute**</span></span>  
 <span data-ttu-id="c0c07-117">選擇要分析的可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="c0c07-117">Choose the predictable attribute that you want to analyze.</span></span>  
  
 <span data-ttu-id="c0c07-118">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="c0c07-118">**Value**</span></span>  
 <span data-ttu-id="c0c07-119">選擇 [屬性]\*\*\*\* 中設定之可預測屬性的狀態。</span><span class="sxs-lookup"><span data-stu-id="c0c07-119">Choose a state for the predictable attribute that you set in **Attribute**.</span></span> <span data-ttu-id="c0c07-120">因為貝氏機率分類模型不支援連續變數，所以所有目標屬性都有離散或離散化結果。</span><span class="sxs-lookup"><span data-stu-id="c0c07-120">Because Naïve Bayes models do not support continuous variables, all target attributes have discrete or discretized outcomes.</span></span> <span data-ttu-id="c0c07-121">永遠會自動將遺漏屬性新增至清單。</span><span class="sxs-lookup"><span data-stu-id="c0c07-121">The Missing attribute is always automatically added to the list.</span></span>  
  
 <span data-ttu-id="c0c07-122">**的特性\<predictable state>**</span><span class="sxs-lookup"><span data-stu-id="c0c07-122">**Characteristics for \<predictable state>**</span></span>  
 <span data-ttu-id="c0c07-123">圖形包含下列資料行，其中描述輸入屬性的狀態與選取之可預測屬性狀態如何相關。</span><span class="sxs-lookup"><span data-stu-id="c0c07-123">The graph contains the following columns, which describe how states of the input attributes are related to the selected predictable attribute state.</span></span>  
  
|<span data-ttu-id="c0c07-124">值</span><span class="sxs-lookup"><span data-stu-id="c0c07-124">Value</span></span>|<span data-ttu-id="c0c07-125">描述</span><span class="sxs-lookup"><span data-stu-id="c0c07-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0c07-126">**變數**</span><span class="sxs-lookup"><span data-stu-id="c0c07-126">**Variable**</span></span>|<span data-ttu-id="c0c07-127">列出採礦模型中的輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="c0c07-127">Lists the input attributes in the mining model.</span></span>|  
|<span data-ttu-id="c0c07-128">**值**</span><span class="sxs-lookup"><span data-stu-id="c0c07-128">**Values**</span></span>|<span data-ttu-id="c0c07-129">列出 [變數]\*\*\*\* 中輸入屬性的每個狀態。</span><span class="sxs-lookup"><span data-stu-id="c0c07-129">Lists each state of the input attribute in **Variable**.</span></span>|  
|<span data-ttu-id="c0c07-130">**機率**</span><span class="sxs-lookup"><span data-stu-id="c0c07-130">**Probability**</span></span>|<span data-ttu-id="c0c07-131">長條表示該資料列中的屬性和值與可預測屬性之選取狀態相關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="c0c07-131">The bar represents the probability that the attribute and value in that row are associated with the selected state of the predictable attribute.</span></span> <span data-ttu-id="c0c07-132">將滑鼠停留在長條上方，可查看以百分比表示的機率。</span><span class="sxs-lookup"><span data-stu-id="c0c07-132">Hover the mouse over the bar to view the probability as a percentage.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0c07-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0c07-133">See Also</span></span>  
 <span data-ttu-id="c0c07-134">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c0c07-134">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="c0c07-135">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="c0c07-135">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="c0c07-136">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="c0c07-136">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
