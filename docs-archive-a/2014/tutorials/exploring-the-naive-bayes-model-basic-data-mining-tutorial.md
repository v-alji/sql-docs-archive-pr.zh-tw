---
title: 探索貝氏貝氏機率分類模型 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a26fa972e1ed50e2f4107026210a5935fcb86d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703549"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a><span data-ttu-id="70bc3-102">瀏覽貝氏機率分類模型 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="70bc3-102">Exploring the Naive Bayes Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="70bc3-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]貝氏貝氏機率分類演算法提供數種方法來顯示自行車購買與輸入屬性之間的互動。</span><span class="sxs-lookup"><span data-stu-id="70bc3-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm provides several methods for displaying the interaction between bike buying and the input attributes.</span></span>  
  
 <span data-ttu-id="70bc3-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]貝氏貝氏機率分類 Viewer 提供下列索引標籤，供您用來探索貝氏貝氏機率分類的採礦模型：</span><span class="sxs-lookup"><span data-stu-id="70bc3-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes Viewer provides the following tabs for use in exploring Naive Bayes mining models:</span></span>  
  
 
  
##  <a name="dependency-network"></a><a name="DependencyNetwork"></a><span data-ttu-id="70bc3-105">相依性網路</span><span class="sxs-lookup"><span data-stu-id="70bc3-105">Dependency Network</span></span>  
 <span data-ttu-id="70bc3-106">[相依性**網路**] 索引標籤的運作方式與樹狀檢視器的 [相依性**網路**] 索引標籤相同 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="70bc3-106">The **Dependency Network** tab works in the same way as the **Dependency Network** tab for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Tree Viewer.</span></span> <span data-ttu-id="70bc3-107">檢視器中的每一個節點各代表變數，節點之間的線條則代表關聯性。</span><span class="sxs-lookup"><span data-stu-id="70bc3-107">Each node in the viewer represents an attribute, and the lines between nodes represent relationships.</span></span> <span data-ttu-id="70bc3-108">在此檢視器中，您可以查看對於可預測屬性 Bike Buyer 的狀態具有影響力的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="70bc3-108">In the viewer, you can see all the attributes that affect the state of the predictable attribute, Bike Buyer.</span></span>  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a><span data-ttu-id="70bc3-109">若要在相依性網路索引標籤中瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="70bc3-109">To explore the model in the Dependency Network tab</span></span>  
  
1.  <span data-ttu-id="70bc3-110">使用 [**採礦模型檢視器**] 索引標籤頂端的 [**採礦模型**] 清單，切換到 `TM_NaiveBayes` 模型。</span><span class="sxs-lookup"><span data-stu-id="70bc3-110">Use the **Mining Model** list at the top of the **Mining Model Viewer** tab to switch to the `TM_NaiveBayes` model.</span></span>  
  
2.  <span data-ttu-id="70bc3-111">使用 [**檢視器]** 清單切換至 [ **Microsoft 貝氏貝氏機率分類檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="70bc3-111">Use the **Viewer** list to switch to **Microsoft Naive Bayes Viewer**.</span></span>  
  
3.  <span data-ttu-id="70bc3-112">按一下 `Bike Buyer` 節點以識別其相依性。</span><span class="sxs-lookup"><span data-stu-id="70bc3-112">Click the `Bike Buyer` node to identify its dependencies.</span></span>  
  
     <span data-ttu-id="70bc3-113">粉紅色的陰影表示所有屬性都會影響自行車的購買。</span><span class="sxs-lookup"><span data-stu-id="70bc3-113">The pink shading indicates that all of the attributes have an effect on bike buying.</span></span>  
  
4.  <span data-ttu-id="70bc3-114">調整滑動軸來識別最具影響力的屬性。</span><span class="sxs-lookup"><span data-stu-id="70bc3-114">Adjust the slider to identify the most influential attribute.</span></span>  
  
     <span data-ttu-id="70bc3-115">隨著您將滑動軸往下移，便只留下對 [Bike Buyer] 資料行影響最大的屬性。</span><span class="sxs-lookup"><span data-stu-id="70bc3-115">As you lower the slider, only the attributes that have the greatest effect on the [Bike Buyer] column remain.</span></span> <span data-ttu-id="70bc3-116">當您調整滑動軸時，您可以發現幾個最具影響力的屬性如下：擁有的汽車數量、通勤距離及小孩總數。</span><span class="sxs-lookup"><span data-stu-id="70bc3-116">By adjusting the slider, you can discover that a few of the most influential attributes are: number of cars owned, commute distance, and total number of children.</span></span>  
 
  
##  <a name="attribute-profiles"></a><a name="AttributeProfiles"></a> <span data-ttu-id="70bc3-117">屬性設定檔</span><span class="sxs-lookup"><span data-stu-id="70bc3-117">Attribute Profiles</span></span>  
 <span data-ttu-id="70bc3-118">[**屬性設定檔**] 索引標籤會描述輸入屬性的不同狀態如何影響可預測屬性的結果。</span><span class="sxs-lookup"><span data-stu-id="70bc3-118">The **Attribute Profiles** tab describes how different states of the input attributes affect the outcome of the predictable attribute.</span></span>  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a><span data-ttu-id="70bc3-119">若要在屬性設定檔索引標籤中瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="70bc3-119">To explore the model in the Attribute Profiles tab</span></span>  
  
1.  <span data-ttu-id="70bc3-120">在 [**可預測**] 方塊中，確認 `Bike Buyer` 已選取 []。</span><span class="sxs-lookup"><span data-stu-id="70bc3-120">In the **Predictable** box, verify that `Bike Buyer` is selected.</span></span>  
  
2.  <span data-ttu-id="70bc3-121">如果「**挖掘圖例**」封鎖了**屬性設定檔**的顯示，請將它移出。</span><span class="sxs-lookup"><span data-stu-id="70bc3-121">If the **Mining Legend** is blocking display of the **Attribute profiles**, move it out of the way.</span></span>  
  
3.  <span data-ttu-id="70bc3-122">在 [**長條圖**列] 方塊中，選取 [ **5**]。</span><span class="sxs-lookup"><span data-stu-id="70bc3-122">In the **Histogram** bars box, select **5**.</span></span>  
  
     <span data-ttu-id="70bc3-123">在我們的模型中，5 是任何一個變數的最大狀態數。</span><span class="sxs-lookup"><span data-stu-id="70bc3-123">In our model, 5 is the maximum number of states for any one variable.</span></span>  
  
     <span data-ttu-id="70bc3-124">能夠影響這個可預測屬性所處狀態的屬性，會與輸入屬性之每一個狀態的值及其在可預測屬性之每一個狀態中的分佈情況一同列出。</span><span class="sxs-lookup"><span data-stu-id="70bc3-124">The attributes that affect the state of this predictable attribute are listed together with the values of each state of the input attributes and their distributions in each state of the predictable attribute.</span></span>  
  
4.  <span data-ttu-id="70bc3-125">在 [**屬性**] 資料行中，尋找 [**擁有的汽車數目**]。</span><span class="sxs-lookup"><span data-stu-id="70bc3-125">In the **Attributes** column, find **Number Cars Owned**.</span></span>  <span data-ttu-id="70bc3-126">請注意自行車買主 (標記為 1 的資料行) 與非買主 (標記為 0 的資料行) 的長條圖差異。</span><span class="sxs-lookup"><span data-stu-id="70bc3-126">Notice the differences in the histograms for bike buyers (column labeled 1) and non-buyers (column labeled 0).</span></span> <span data-ttu-id="70bc3-127">沒有任何汽車或是擁有一輛汽車的人比較可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="70bc3-127">A person with zero or one car is much more likely to buy a bike.</span></span>  
  
5.  <span data-ttu-id="70bc3-128">在 [自行車購買者 (] 資料行中，按兩下標示為 1) 資料行的 [ **Cars 擁有**的資料格數目]。</span><span class="sxs-lookup"><span data-stu-id="70bc3-128">Double-click the **Number Cars Owned** cell in the bike buyer (column labeled 1) column.</span></span>  
  
     <span data-ttu-id="70bc3-129">[**挖掘圖例**] 會顯示更詳細的觀點。</span><span class="sxs-lookup"><span data-stu-id="70bc3-129">The **Mining Legend** displays a more detailed view.</span></span>  
  
  
##  <a name="attribute-characteristics"></a><a name="AttributeCharacteristics"></a><span data-ttu-id="70bc3-130">屬性特性</span><span class="sxs-lookup"><span data-stu-id="70bc3-130">Attribute Characteristics</span></span>  
 <span data-ttu-id="70bc3-131">使用 [**屬性特性**] 索引標籤，您可以選取屬性和值，以查看其他屬性的值在選取的值案例中出現的頻率。</span><span class="sxs-lookup"><span data-stu-id="70bc3-131">With the **Attribute Characteristics** tab, you can select an attribute and value to see how frequently values for other attributes appear in the selected value cases.</span></span>  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a><span data-ttu-id="70bc3-132">若要在屬性特性索引標籤中瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="70bc3-132">To explore the model in the Attribute Characteristics tab</span></span>  
  
1.  <span data-ttu-id="70bc3-133">在 [**屬性**] 清單中，確認 `Bike Buyer` 已選取 []。</span><span class="sxs-lookup"><span data-stu-id="70bc3-133">In the **Attribute** list, verify that `Bike Buyer` is selected.</span></span>  
  
2.  <span data-ttu-id="70bc3-134">將**值**設定為**1**。</span><span class="sxs-lookup"><span data-stu-id="70bc3-134">Set the **Value** to **1**.</span></span>  
  
     <span data-ttu-id="70bc3-135">在此檢視器中，您將會看到家裡沒有小孩、通勤距離很短而且住在北美地區的客戶比較可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="70bc3-135">In the viewer, you will see that customers who have no children at home, short commutes, and live in the North America region are more likely to buy a bike.</span></span>  
  
  
##  <a name="attribute-discrimination"></a><a name="AttributeDiscrimination"></a><span data-ttu-id="70bc3-136">屬性辨識</span><span class="sxs-lookup"><span data-stu-id="70bc3-136">Attribute Discrimination</span></span>  
 <span data-ttu-id="70bc3-137">使用 [**屬性**辨識] 索引標籤，您可以調查自行車購買和其他屬性值的兩個離散值之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="70bc3-137">With the **Attribute Discrimination** tab, you can investigate the relationship between two discrete values of bike buying and other attribute values.</span></span> <span data-ttu-id="70bc3-138">因為 `TM_NaiveBayes` 模型只有兩個狀態，1和0，所以您不需要對檢視器進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="70bc3-138">Because the `TM_NaiveBayes` model has only two states, 1 and 0, you do not have to make any changes to the viewer.</span></span>  
  
 <span data-ttu-id="70bc3-139">在此檢視器中，您可以看出沒有汽車的人傾向於購買自行車，而擁有兩輛汽車的人則傾向於不購買自行車。</span><span class="sxs-lookup"><span data-stu-id="70bc3-139">In the viewer, you can see that people who do not own cars tend to buy bicycles, and people who own two cars tend not to buy bicycles.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="70bc3-140">相關工作</span><span class="sxs-lookup"><span data-stu-id="70bc3-140">Related Tasks</span></span>  
 <span data-ttu-id="70bc3-141">請參閱下列主題，瀏覽其他採礦模型。</span><span class="sxs-lookup"><span data-stu-id="70bc3-141">See the following topics to explore the other mining models.</span></span>  
  
-   [<span data-ttu-id="70bc3-142">流覽決策樹模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="70bc3-142">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="70bc3-143">&#40;基本資料採礦教學課程中探索群集模型&#41;</span><span class="sxs-lookup"><span data-stu-id="70bc3-143">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="70bc3-144">下一課</span><span class="sxs-lookup"><span data-stu-id="70bc3-144">Next Lesson</span></span>  
 [<span data-ttu-id="70bc3-145">第5課： &#40;基本資料採礦教學課程來測試模型&#41;</span><span class="sxs-lookup"><span data-stu-id="70bc3-145">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="70bc3-146">本課程的前一項工作</span><span class="sxs-lookup"><span data-stu-id="70bc3-146">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="70bc3-147">&#40;基本資料採礦教學課程中探索群集模型&#41;</span><span class="sxs-lookup"><span data-stu-id="70bc3-147">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="70bc3-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70bc3-148">See Also</span></span>  
 <span data-ttu-id="70bc3-149">[使用 Microsoft 貝氏貝氏機率分類檢視器流覽模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="70bc3-149">[Browse a Model Using the Microsoft Naive Bayes Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md) </span></span>  
 <span data-ttu-id="70bc3-150">[[屬性辨識] 索引標籤 &#40;[採礦模型檢視器]&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="70bc3-150">[Attribute Discrimination Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="70bc3-151">[[屬性設定檔] 索引標籤 &#40;[採礦模型檢視器&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="70bc3-151">[Attribute Profiles Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="70bc3-152">[[屬性特性] 索引標籤 &#40;[採礦模型檢視器]&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="70bc3-152">[Attribute Characteristics Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="70bc3-153">[[相依性網路] 索引標籤 &#40;&#41;的採礦模型檢視器](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="70bc3-153">[Dependency Network Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)</span></span>  
  
  
