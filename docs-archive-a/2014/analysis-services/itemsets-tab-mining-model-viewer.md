---
title: 專案集索引標籤 () 的 [採礦模型檢視器] |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.itemsets.f1
ms.assetid: 95b2b805-b142-4064-9c80-4b1b3fe2fe63
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b99b62b01b196fd62e1ef264e530487018f6a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592961"
---
# <a name="itemsets-tab-mining-model-viewer"></a><span data-ttu-id="bb423-102">項目集索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="bb423-102">Itemsets Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="bb423-103">您可以使用 [項目集]\*\*\*\* 窗格，檢視關聯規則採礦模型所包含的常見項目集。</span><span class="sxs-lookup"><span data-stu-id="bb423-103">You can use the **Itemsets** pane to view the frequent itemsets that an association rules mining model contains.</span></span> <span data-ttu-id="bb423-104">因為關聯模型可包含許多項目集，所以檢視器中提供了一些控制項，協助您篩選在檢視器中顯示的項目集。</span><span class="sxs-lookup"><span data-stu-id="bb423-104">Because an association model can contain many itemsets, controls are provided in the viewer to help you filter the itemsets that are displayed in the viewer.</span></span>  
  
 <span data-ttu-id="bb423-105">**如需詳細資訊，請參閱** [Microsoft 關聯分析演算法](data-mining/microsoft-association-algorithm.md)、 [使用 Microsoft 關聯規則檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="bb423-105">**For More Information:** [Microsoft Association Algorithm](data-mining/microsoft-association-algorithm.md), [Browse a Model Using the Microsoft Association Rules Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="bb423-106">選項</span><span class="sxs-lookup"><span data-stu-id="bb423-106">Options</span></span>  
 <span data-ttu-id="bb423-107">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="bb423-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="bb423-108">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="bb423-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="bb423-109">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="bb423-109">**Mining Model**</span></span>  
 <span data-ttu-id="bb423-110">選擇包含在目前採礦結構中，您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="bb423-110">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="bb423-111">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="bb423-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="bb423-112">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="bb423-112">**Viewer**</span></span>  
 <span data-ttu-id="bb423-113">選擇用來檢視選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="bb423-113">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="bb423-114">可以使用自訂的關聯模型檢視器，或 [ [!INCLUDE[msCoName](../includes/msconame-md.md)] 一般內容樹狀檢視器]。</span><span class="sxs-lookup"><span data-stu-id="bb423-114">You can use either the custom viewer for association models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="bb423-115">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="bb423-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="bb423-116">**最小支援**</span><span class="sxs-lookup"><span data-stu-id="bb423-116">**Minimum support**</span></span>  
 <span data-ttu-id="bb423-117">變更此值以設定項目集必須包含的最小支援，才能出現在檢視器中。</span><span class="sxs-lookup"><span data-stu-id="bb423-117">Change this value to set the minimum support that an itemset must contain to appear in the viewer.</span></span> <span data-ttu-id="bb423-118">首次開啟模型時顯示的預設值是由模型所計算，但您可以變更此值以查看更多或更少項目集。</span><span class="sxs-lookup"><span data-stu-id="bb423-118">The default value that is displayed when you first open the model is calculated by the model, but you can change it to see more or fewer itemsets.</span></span>  
  
 <span data-ttu-id="bb423-119">**項目集大小下限**</span><span class="sxs-lookup"><span data-stu-id="bb423-119">**Minimum itemset size**</span></span>  
 <span data-ttu-id="bb423-120">變更此值可設定項目集必須包含的最小項目數目，才能出現在檢視器中。</span><span class="sxs-lookup"><span data-stu-id="bb423-120">Change this value to set the minimum number of items that must be included in an itemset before the itemset can be displayed in the viewer.</span></span>  
  
 <span data-ttu-id="bb423-121">**篩選項目集**</span><span class="sxs-lookup"><span data-stu-id="bb423-121">**Filter Itemset**</span></span>  
 <span data-ttu-id="bb423-122">輸入字串值，即可篩選在檢視器中出現的項目集數目。</span><span class="sxs-lookup"><span data-stu-id="bb423-122">Type a string value to filter the number of itemsets that appear in the viewer.</span></span>  
  
 <span data-ttu-id="bb423-123">還可以輸入 .NET 規則運算式做為篩選準則。</span><span class="sxs-lookup"><span data-stu-id="bb423-123">You can also type .NET regular expressions as filter criteria.</span></span> <span data-ttu-id="bb423-124">例如，下列運算式會傳回包含 'Road Bottle Cage' 的所有項目集：</span><span class="sxs-lookup"><span data-stu-id="bb423-124">For example, the following expression returns all itemsets that contain 'Road Bottle Cage':</span></span>  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*`  
  
 <span data-ttu-id="bb423-125">請注意，您可能需要重新整理檢視，才能查看篩選準則套用情況。</span><span class="sxs-lookup"><span data-stu-id="bb423-125">Note that you might need to refresh the view to see the filter criteria apply.</span></span> <span data-ttu-id="bb423-126">您也可以開啟和關閉 [顯示完整名稱]\*\*\*\* 選項以重新整理清單。</span><span class="sxs-lookup"><span data-stu-id="bb423-126">You can also toggle the **Show long name** option on and off to refresh the list.</span></span>  
  
 <span data-ttu-id="bb423-127">根據預設，篩選準則會套用至屬性/值組合的完整名稱；因此，如果您只檢視屬性名稱，則可能無法明確知道已正確套用篩選準則。</span><span class="sxs-lookup"><span data-stu-id="bb423-127">By default the filter criteria applies to the full name of the attribute-value combination; therefore, if you are viewing the attribute name only, it might not be obvious that the filter criteria has applied correctly.</span></span> <span data-ttu-id="bb423-128">使用 [顯示]\*\*\*\* 下拉式清單可選取 [顯示屬性名稱和值]\*\*\*\*，並驗證是否已正確篩選項目集的清單。</span><span class="sxs-lookup"><span data-stu-id="bb423-128">Use the **Show** dropdown list to select **Show attribute name and value**, and verify that the list of itemsets is filtered correctly.</span></span>  
  
 <span data-ttu-id="bb423-129">**顯示**</span><span class="sxs-lookup"><span data-stu-id="bb423-129">**Show**</span></span>  
 <span data-ttu-id="bb423-130">調整在檢視器中顯示項目集的方式。</span><span class="sxs-lookup"><span data-stu-id="bb423-130">Adjust how the itemset is displayed in the viewer.</span></span> <span data-ttu-id="bb423-131">您可以選取下列三個選項之一：</span><span class="sxs-lookup"><span data-stu-id="bb423-131">You can select one of the three following options:</span></span>  
  
-   <span data-ttu-id="bb423-132">顯示屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="bb423-132">Show attribute name and value</span></span>  
  
-   <span data-ttu-id="bb423-133">只顯示屬性值</span><span class="sxs-lookup"><span data-stu-id="bb423-133">Show attribute value only</span></span>  
  
-   <span data-ttu-id="bb423-134">只顯示屬性名稱</span><span class="sxs-lookup"><span data-stu-id="bb423-134">Show attribute name only</span></span>  
  
 <span data-ttu-id="bb423-135">請注意，此選項不會重新查詢模型；它只篩選所顯示的屬性或值。</span><span class="sxs-lookup"><span data-stu-id="bb423-135">Note that this option does not requery the model; it only filters the attributes or values that are displayed.</span></span>  
  
 <span data-ttu-id="bb423-136">**顯示完整名稱**</span><span class="sxs-lookup"><span data-stu-id="bb423-136">**Show long name**</span></span>  
 <span data-ttu-id="bb423-137">選取此選項可顯示項目集在採礦模型內容中的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="bb423-137">Select this option to display the full name of the itemset as it appears in the mining model content.</span></span>  
  
 <span data-ttu-id="bb423-138">**最大資料列數**</span><span class="sxs-lookup"><span data-stu-id="bb423-138">**Maximum rows**</span></span>  
 <span data-ttu-id="bb423-139">限制在檢視器中顯示的項目集數目。</span><span class="sxs-lookup"><span data-stu-id="bb423-139">Limit the number of itemsets that are displayed in the viewer.</span></span> <span data-ttu-id="bb423-140">根據預設，項目集是依支援的遞減順序排序，因此，減小此值會限制清單，只列出最常用的項目集。</span><span class="sxs-lookup"><span data-stu-id="bb423-140">By default, itemsets are ordered by support in descending order, so lowering this value restricts the list to the most common itemsets.</span></span>  
  
 <span data-ttu-id="bb423-141">**支援**</span><span class="sxs-lookup"><span data-stu-id="bb423-141">**Support**</span></span>  
 <span data-ttu-id="bb423-142">顯示對每個項目集的支援。</span><span class="sxs-lookup"><span data-stu-id="bb423-142">Displays the support for each itemset.</span></span>  
  
 <span data-ttu-id="bb423-143">**大小**</span><span class="sxs-lookup"><span data-stu-id="bb423-143">**Size**</span></span>  
 <span data-ttu-id="bb423-144">顯示存在於每個項目集內的項目數目。</span><span class="sxs-lookup"><span data-stu-id="bb423-144">Displays the number of items that exist in each itemset.</span></span>  
  
 <span data-ttu-id="bb423-145">**項目集**</span><span class="sxs-lookup"><span data-stu-id="bb423-145">**Itemset**</span></span>  
 <span data-ttu-id="bb423-146">顯示每個項目集的描述。</span><span class="sxs-lookup"><span data-stu-id="bb423-146">Displays the description of each itemset.</span></span> <span data-ttu-id="bb423-147">根據預設，項目集表示為以逗號分隔的屬性及其值清單。</span><span class="sxs-lookup"><span data-stu-id="bb423-147">By default, itemsets are presented as a comma-delimited list of attributes and their values.</span></span> <span data-ttu-id="bb423-148">您可以使用 [顯示]\*\*\*\* 選項來變更其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="bb423-148">You can change the way they are displayed by using the **Show** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb423-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb423-149">See Also</span></span>  
 <span data-ttu-id="bb423-150">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="bb423-150">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="bb423-151">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="bb423-151">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="bb423-152">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="bb423-152">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
