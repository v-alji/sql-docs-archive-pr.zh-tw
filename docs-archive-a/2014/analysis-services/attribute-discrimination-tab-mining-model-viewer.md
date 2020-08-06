---
title: '[屬性辨識] 索引標籤 ([採礦模型檢視器]) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.discrimination.f1
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: a8b0d4bc99b1c8f1c5de0269312f02eeb09df022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593173"
---
# <a name="attribute-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="54817-102">屬性辨識索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="54817-102">Attribute Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="54817-103">使用 [屬性辨識]\*\*\*\* 索引標籤，即可比較輸入屬性的狀態以及查看它們與結果屬性如何相關。</span><span class="sxs-lookup"><span data-stu-id="54817-103">Use the **Attribute Discrimination** tab to compare the states of the input attributes and see how they are related to the outcome attribute.</span></span> <span data-ttu-id="54817-104">先列出造成兩個選取的可預測屬性狀態之間最大差異的屬性值。</span><span class="sxs-lookup"><span data-stu-id="54817-104">The attribute values that make the most difference between the two selected predictable attribute states are listed first.</span></span>  
  
 <span data-ttu-id="54817-105">\*\*如需詳細資訊，請參閱 \*\* [Microsoft 貝氏機率分類演算法](data-mining/microsoft-naive-bayes-algorithm.md)、[使用 Microsoft 貝氏機率分類檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="54817-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="54817-106">選項</span><span class="sxs-lookup"><span data-stu-id="54817-106">Options</span></span>  
 <span data-ttu-id="54817-107">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="54817-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="54817-108">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="54817-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="54817-109">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="54817-109">**Mining Model**</span></span>  
 <span data-ttu-id="54817-110">在目前採礦結構中選擇採礦模型。</span><span class="sxs-lookup"><span data-stu-id="54817-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="54817-111">採礦模型會自動在正確的自訂檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="54817-111">The mining model automatically opens in the correct custom viewer.</span></span>  
  
 <span data-ttu-id="54817-112">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="54817-112">**Viewer**</span></span>  
 <span data-ttu-id="54817-113">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="54817-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="54817-114">可以為每個模型選擇自訂檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。</span><span class="sxs-lookup"><span data-stu-id="54817-114">For each model, you can choose either the custom viewer, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="54817-115">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="54817-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="54817-116">**屬性**</span><span class="sxs-lookup"><span data-stu-id="54817-116">**Attribute**</span></span>  
 <span data-ttu-id="54817-117">選擇可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="54817-117">Choose a predictable attribute.</span></span>  
  
 <span data-ttu-id="54817-118">**值 1**</span><span class="sxs-lookup"><span data-stu-id="54817-118">**Value 1**</span></span>  
 <span data-ttu-id="54817-119">選擇一種可預測屬性狀態，和 **[值 2]** 裡包含的狀態進行比較。</span><span class="sxs-lookup"><span data-stu-id="54817-119">Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.</span></span>  
  
 <span data-ttu-id="54817-120">**值2**</span><span class="sxs-lookup"><span data-stu-id="54817-120">**Value 2**</span></span>  
 <span data-ttu-id="54817-121">選取一種可預測屬性狀態，和 **[值 1]** 裡包含的狀態進行比較。</span><span class="sxs-lookup"><span data-stu-id="54817-121">Select a state of the predictable attribute to compare to the state that is contained in **Value 1**.</span></span> <span data-ttu-id="54817-122">您也可以選取**所有其他狀態**來比較**值 1**中的值與其補數（也就是值1以外的所有其他值）。</span><span class="sxs-lookup"><span data-stu-id="54817-122">You can also select **All Other States** to compare the value in **Value 1** with its complement-that is, all other values except Value 1.</span></span>  
  
 <span data-ttu-id="54817-123">**和的辨識分數 \<Value 1>\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="54817-123">**Discrimination scores for \<Value 1> and \<Value 2>**</span></span>  
 <span data-ttu-id="54817-124">圖形包含下列資料行，描述目標屬性與輸入屬性的特定狀態如何相關。</span><span class="sxs-lookup"><span data-stu-id="54817-124">The graph contains the following columns, which describe how the target attribute is related to specific states of the input attribute.</span></span>  
  
|<span data-ttu-id="54817-125">值</span><span class="sxs-lookup"><span data-stu-id="54817-125">Value</span></span>|<span data-ttu-id="54817-126">描述</span><span class="sxs-lookup"><span data-stu-id="54817-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54817-127">**屬性**</span><span class="sxs-lookup"><span data-stu-id="54817-127">**Attributes**</span></span>|<span data-ttu-id="54817-128">採礦模型中的輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="54817-128">An input attribute in the mining model.</span></span>|  
|<span data-ttu-id="54817-129">**值**</span><span class="sxs-lookup"><span data-stu-id="54817-129">**Values**</span></span>|<span data-ttu-id="54817-130">列在 [屬性]\*\*\*\* 中之屬性的狀態。</span><span class="sxs-lookup"><span data-stu-id="54817-130">A state of the attribute that is listed in **Attributes**.</span></span>|  
|<span data-ttu-id="54817-131">**照顧\<Value 1>**</span><span class="sxs-lookup"><span data-stu-id="54817-131">**Favors \<Value 1>**</span></span>|<span data-ttu-id="54817-132">長條表示目前屬性和值是否喜好 [值 1]\*\*\*\* 中所選的目標結果。</span><span class="sxs-lookup"><span data-stu-id="54817-132">The bar indicates whether the current attribute and value favor the target outcome selected in **Value 1**.</span></span>|  
|<span data-ttu-id="54817-133">**照顧\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="54817-133">**Favors \<Value 2>**</span></span>|<span data-ttu-id="54817-134">長條表示目前屬性和值是否喜好 [值 2]\*\*\*\* 中所選的目標結果。</span><span class="sxs-lookup"><span data-stu-id="54817-134">The bar indicates whether the current attribute and value favor the target outcome selected in **Value 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54817-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54817-135">See Also</span></span>  
 <span data-ttu-id="54817-136">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="54817-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="54817-137">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="54817-137">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="54817-138">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="54817-138">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
