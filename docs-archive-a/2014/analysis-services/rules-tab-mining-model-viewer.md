---
title: '[規則] 索引標籤 (採礦模型檢視器) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.rules.f1
ms.assetid: 705d5492-b58f-45d9-94d7-ed57b7025823
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0d86931865fd9352074669de93b14dacfc84537
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592927"
---
# <a name="rules-tab-mining-model-viewer"></a><span data-ttu-id="c94a5-102">規則索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="c94a5-102">Rules Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="c94a5-103">在關聯模型中使用 [規則]\*\*\*\* 窗格，即可檢視演算法從資料擷取的規則。</span><span class="sxs-lookup"><span data-stu-id="c94a5-103">Use the **Rules** pane in an association model to view the rules that the algorithm extracted from the data.</span></span> <span data-ttu-id="c94a5-104">規則描述各項目之間相互關聯的方式，可用於建立建議。</span><span class="sxs-lookup"><span data-stu-id="c94a5-104">Rules describe how items are related to each other, and can be used to create recommendations.</span></span>  
  
 <span data-ttu-id="c94a5-105">您可以使用檢視器中的選項來篩選檢視器所顯示的規則數目。</span><span class="sxs-lookup"><span data-stu-id="c94a5-105">You can use the options in the viewer to filter the number of rules that are displayed in the viewer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c94a5-106">根據預設，檢視器只顯示高於 [最小機率]\*\*\*\* 中定義之機率臨界值的規則。</span><span class="sxs-lookup"><span data-stu-id="c94a5-106">By default, only the rules that are above the probability threshold defined in **Minimum probability** are displayed in the viewer.</span></span> <span data-ttu-id="c94a5-107">無法使用檢視器減小此值，因為規則輸出的機率臨界值是在建立模型時決定的。</span><span class="sxs-lookup"><span data-stu-id="c94a5-107">You cannot make this value any smaller by using the viewer, because the probability threshold for rule output is determined when the model is created.</span></span> <span data-ttu-id="c94a5-108">如需詳細資訊，請參閱 [Microsoft 關聯分析演算法技術參考](data-mining/microsoft-association-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="c94a5-108">For more information, see [Microsoft Association Algorithm Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="c94a5-109">**如需詳細資訊，請參閱** [Microsoft 關聯分析演算法](data-mining/microsoft-association-algorithm.md)、 [使用 Microsoft 關聯規則檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="c94a5-109">**For More Information:** [Microsoft Association Algorithm](data-mining/microsoft-association-algorithm.md), [Browse a Model Using the Microsoft Association Rules Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="c94a5-110">選項</span><span class="sxs-lookup"><span data-stu-id="c94a5-110">Options</span></span>  
 <span data-ttu-id="c94a5-111">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="c94a5-111">**Refresh viewer content**</span></span>  
 <span data-ttu-id="c94a5-112">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="c94a5-112">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="c94a5-113">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="c94a5-113">**Mining Model**</span></span>  
 <span data-ttu-id="c94a5-114">選擇包含在目前採礦結構中，您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="c94a5-114">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="c94a5-115">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="c94a5-115">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="c94a5-116">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="c94a5-116">**Viewer**</span></span>  
 <span data-ttu-id="c94a5-117">選擇用來檢視選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="c94a5-117">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="c94a5-118">可以使用每個採礦模型的自訂檢視器，或 [Microsoft 一般內容樹狀檢視器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c94a5-118">You can use the custom viewer for each mining model, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="c94a5-119">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="c94a5-119">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="c94a5-120">**最小機率**</span><span class="sxs-lookup"><span data-stu-id="c94a5-120">**Minimum probability**</span></span>  
 <span data-ttu-id="c94a5-121">變更此值可設定在檢視器中顯示規則所需的最小機率。</span><span class="sxs-lookup"><span data-stu-id="c94a5-121">Change this value to set the minimum probability required for a rule to be displayed in the viewer.</span></span> <span data-ttu-id="c94a5-122">增大機率值會減少顯示的規則數目。</span><span class="sxs-lookup"><span data-stu-id="c94a5-122">Increasing the value for probability will reduce the number of rules that are displayed.</span></span>  
  
 <span data-ttu-id="c94a5-123">**最低重要性**</span><span class="sxs-lookup"><span data-stu-id="c94a5-123">**Minimum importance**</span></span>  
 <span data-ttu-id="c94a5-124">變更此值可設定在檢視器中顯示規則所需的最低重要性。</span><span class="sxs-lookup"><span data-stu-id="c94a5-124">Change this value to set the minimum importance required for a rule to be displayed in the viewer.</span></span> <span data-ttu-id="c94a5-125">增大重要性值會減少顯示的規則數目。</span><span class="sxs-lookup"><span data-stu-id="c94a5-125">Increasing the value for importance will reduce the number of rules that are displayed.</span></span>  
  
 <span data-ttu-id="c94a5-126">**篩選規則**</span><span class="sxs-lookup"><span data-stu-id="c94a5-126">**Filter Rule**</span></span>  
 <span data-ttu-id="c94a5-127">輸入字串值，即可篩選在檢視器中出現的規則數目。</span><span class="sxs-lookup"><span data-stu-id="c94a5-127">Type a string value to filter the number of rules that appear in the viewer.</span></span>  
  
 <span data-ttu-id="c94a5-128">還可以輸入 .NET 規則運算式做為篩選準則。</span><span class="sxs-lookup"><span data-stu-id="c94a5-128">You can also type .NET regular expressions as filter criteria.</span></span> <span data-ttu-id="c94a5-129">例如，下列運算式會傳回規則左側包含 'Road Bottle Cage' 的所有規則：</span><span class="sxs-lookup"><span data-stu-id="c94a5-129">For example, the following expression returns all rules that contain 'Road Bottle Cage' on the left side of the rule:</span></span>  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*->.*`  
  
 <span data-ttu-id="c94a5-130">請注意，您可能需要重新整理檢視，才能查看篩選準則套用情況。</span><span class="sxs-lookup"><span data-stu-id="c94a5-130">Note that you might need to refresh the view to see the filter criteria apply.</span></span> <span data-ttu-id="c94a5-131">您也可以開啟和關閉 [顯示完整名稱]\*\*\*\* 選項以重新整理清單。</span><span class="sxs-lookup"><span data-stu-id="c94a5-131">You can also toggle the **Show long name** option on and off to refresh the list.</span></span>  
  
 <span data-ttu-id="c94a5-132">根據預設，篩選準則會套用至屬性/值組合的完整名稱；因此，如果您只檢視屬性名稱，則可能無法明確知道已正確套用篩選準則。</span><span class="sxs-lookup"><span data-stu-id="c94a5-132">By default the filter criteria applies to the full name of the attribute-value combination; therefore, if you are viewing the attribute name only, it might not be obvious that the filter criteria has applied correctly.</span></span> <span data-ttu-id="c94a5-133">使用 [顯示]\*\*\*\* 下拉式清單可選取 [顯示屬性名稱和值]\*\*\*\*，並驗證是否已正確篩選項目集的清單。</span><span class="sxs-lookup"><span data-stu-id="c94a5-133">Use the **Show** dropdown list to select **Show attribute name and value**, and verify that the list of itemsets is filtered correctly.</span></span>  
  
 <span data-ttu-id="c94a5-134">**顯示**</span><span class="sxs-lookup"><span data-stu-id="c94a5-134">**Show**</span></span>  
 <span data-ttu-id="c94a5-135">調整在檢視器中顯示規則的方式。</span><span class="sxs-lookup"><span data-stu-id="c94a5-135">Adjust the way that the rule is displayed in the viewer.</span></span> <span data-ttu-id="c94a5-136">您可以選取下列三個選項之一：</span><span class="sxs-lookup"><span data-stu-id="c94a5-136">You can select one of the three following options:</span></span>  
  
-   <span data-ttu-id="c94a5-137">顯示屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="c94a5-137">Show the attribute name and value</span></span>  
  
-   <span data-ttu-id="c94a5-138">只顯示屬性值</span><span class="sxs-lookup"><span data-stu-id="c94a5-138">Show the attribute value only</span></span>  
  
-   <span data-ttu-id="c94a5-139">只顯示屬性名稱</span><span class="sxs-lookup"><span data-stu-id="c94a5-139">Show the attribute name only</span></span>  
  
 <span data-ttu-id="c94a5-140">**顯示完整名稱**</span><span class="sxs-lookup"><span data-stu-id="c94a5-140">**Show long name**</span></span>  
 <span data-ttu-id="c94a5-141">按照規則出現在採礦模型內容的情形來顯示規則的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="c94a5-141">Show the full name of the rule as it appears in the mining model content.</span></span>  
  
 <span data-ttu-id="c94a5-142">**最大資料列數**</span><span class="sxs-lookup"><span data-stu-id="c94a5-142">**Maximum rows**</span></span>  
 <span data-ttu-id="c94a5-143">限制檢視器中顯示的規則數目。</span><span class="sxs-lookup"><span data-stu-id="c94a5-143">Limit the number of rules that are displayed in the viewer.</span></span>  
  
 <span data-ttu-id="c94a5-144">**機率**</span><span class="sxs-lookup"><span data-stu-id="c94a5-144">**Probability**</span></span>  
 <span data-ttu-id="c94a5-145">此資料行在圖表中顯示每個規則的機率。</span><span class="sxs-lookup"><span data-stu-id="c94a5-145">This column in the chart displays the probability for each rule.</span></span>  
  
 <span data-ttu-id="c94a5-146">您可以按一下資料行標題，依機率來排序。</span><span class="sxs-lookup"><span data-stu-id="c94a5-146">You can click the column heading to sort by probability.</span></span>  
  
 <span data-ttu-id="c94a5-147">**重要性**</span><span class="sxs-lookup"><span data-stu-id="c94a5-147">**Importance**</span></span>  
 <span data-ttu-id="c94a5-148">此資料行在圖表中顯示每個規則的重要性。</span><span class="sxs-lookup"><span data-stu-id="c94a5-148">This column in the chart displays the importance for each rule.</span></span>  
  
 <span data-ttu-id="c94a5-149">您可以按一下資料行標題，依重要性來排序。</span><span class="sxs-lookup"><span data-stu-id="c94a5-149">You can click the column heading to sort by importance.</span></span>  
  
 <span data-ttu-id="c94a5-150">**規則**</span><span class="sxs-lookup"><span data-stu-id="c94a5-150">**Rule**</span></span>  
 <span data-ttu-id="c94a5-151">依據使用 [顯示]\*\*\*\* 和 [顯示完整名稱]\*\*\*\* 選項指定的格式，此資料行在圖表中顯示每個規則的文字說明。</span><span class="sxs-lookup"><span data-stu-id="c94a5-151">This column in the chart displays the text description for each rule, according to the format specified by using the options, **Show** and **Show long name**.</span></span>  
  
 <span data-ttu-id="c94a5-152">您可以按一下資料行標題，依規則文字來排序。</span><span class="sxs-lookup"><span data-stu-id="c94a5-152">You can click the column heading to sort by the text of the rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94a5-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c94a5-153">See Also</span></span>  
 <span data-ttu-id="c94a5-154">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c94a5-154">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="c94a5-155">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="c94a5-155">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="c94a5-156">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="c94a5-156">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
