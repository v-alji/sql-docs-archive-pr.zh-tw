---
title: 使用 Microsoft 關聯規則檢視器流覽模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- mining models [Analysis Services], associations
- mining model content, viewing
- rules [Data Mining]
- Association Rules Viewer [Analysis Services]
- market basket analysis [Analysis Services]
- associations [Analysis Services]
- Microsoft Association Rules Viewer
- dependencies [Analysis Services]
ms.assetid: 538fc01b-8eb1-467a-9b66-3cd57cf7489f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75bcefde30cb81cc00d8ad971756c68dedf670ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606529"
---
# <a name="browse-a-model-using-the-microsoft-association-rules-viewer"></a><span data-ttu-id="03bd2-102">使用 Microsoft 關聯規則檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="03bd2-102">Browse a Model Using the Microsoft Association Rules Viewer</span></span>
  <span data-ttu-id="03bd2-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]中的關聯規則檢視器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會顯示以關聯分析演算法建立的採礦模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="03bd2-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm.</span></span> <span data-ttu-id="03bd2-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯演算法是用於建立資料採礦模型的關聯演算法，這些模型可用於購物籃分析。</span><span class="sxs-lookup"><span data-stu-id="03bd2-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm is an association algorithm for use in creating data mining models that you can use for market basket analysis.</span></span> <span data-ttu-id="03bd2-105">如需有關這個演算法的詳細資訊，請參閱＜ [Microsoft Association Algorithm](microsoft-association-algorithm.md)＞。</span><span class="sxs-lookup"><span data-stu-id="03bd2-105">For more information about this algorithm, see [Microsoft Association Algorithm](microsoft-association-algorithm.md).</span></span>  
  
 <span data-ttu-id="03bd2-106">以下是使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯演算法的主要原因：</span><span class="sxs-lookup"><span data-stu-id="03bd2-106">Following are the primary reasons for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm:</span></span>  
  
-   <span data-ttu-id="03bd2-107">若要尋找描述交易中通常出現在一起之項目的項目集。</span><span class="sxs-lookup"><span data-stu-id="03bd2-107">To find itemsets that describe items that are typically found together in a transaction.</span></span>  
  
-   <span data-ttu-id="03bd2-108">若要探索依據現有的項目預測交易中其他項目存在與否的規則。</span><span class="sxs-lookup"><span data-stu-id="03bd2-108">To discover rules that predict the presence of other items in a transaction based on existing items.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03bd2-109">若要檢視有關此模型中所用的方程式及所探索之模式的詳細資訊，請使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="03bd2-109">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="03bd2-110">如需詳細資訊，請參閱[使用 Microsoft 一般內容樹狀檢視器瀏覽模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="03bd2-110">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
 <span data-ttu-id="03bd2-111">如需如何建立、瀏覽，以及使用關聯採礦模型的逐步解說，請參閱[第 3 課︰建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="03bd2-111">For a walkthrough of how to create, explore, and use an association mining model, see [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="03bd2-112">檢視器索引標籤</span><span class="sxs-lookup"><span data-stu-id="03bd2-112">Viewer Tabs</span></span>  
 <span data-ttu-id="03bd2-113">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中瀏覽採礦模型時，該模型會在適合它的檢視器中，顯示於資料採礦設計師的 **[採礦模型檢視器]** 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="03bd2-113">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="03bd2-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則檢視器包括下列索引標籤：</span><span class="sxs-lookup"><span data-stu-id="03bd2-114">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer includes the following tabs:</span></span>  
  
-   [<span data-ttu-id="03bd2-115">項目集</span><span class="sxs-lookup"><span data-stu-id="03bd2-115">Itemsets</span></span>](#BKMK_Itemsets)  
  
-   [<span data-ttu-id="03bd2-116">規則</span><span class="sxs-lookup"><span data-stu-id="03bd2-116">Rules</span></span>](#BKMK_Rules)  
  
-   [<span data-ttu-id="03bd2-117">相依性網路</span><span class="sxs-lookup"><span data-stu-id="03bd2-117">Dependency Net</span></span>](#BKMK_Dependency)  
  
 <span data-ttu-id="03bd2-118">每一個索引標籤會包含 **[顯示完整名稱]** 核取方塊，您可以使用它在規則或項目集內顯示或隱藏從中產生項目集的資料表。</span><span class="sxs-lookup"><span data-stu-id="03bd2-118">Each tab contains the **Show long name** check box, which you can use to show or hide the table from which the itemset originates in the rule or itemset.</span></span>  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a><span data-ttu-id="03bd2-119">專案集</span><span class="sxs-lookup"><span data-stu-id="03bd2-119">Itemsets</span></span>  
 <span data-ttu-id="03bd2-120">**[項目集]** 索引標籤會顯示被模型識別為經常湊在一起的項目集清單。</span><span class="sxs-lookup"><span data-stu-id="03bd2-120">The **Itemsets** tab displays the list of itemsets that the model identified as frequently found together.</span></span> <span data-ttu-id="03bd2-121">索引標籤會顯示具有下列資料行的方格： **[案例數]**、 **[大小]** 和 **[項目集]**。</span><span class="sxs-lookup"><span data-stu-id="03bd2-121">The tab displays a grid with the following columns: **Support**, **Size**, and **Itemset**.</span></span> <span data-ttu-id="03bd2-122">如需有關案例數的詳細資訊，請參閱＜ [Microsoft Association Algorithm](microsoft-association-algorithm.md)＞。</span><span class="sxs-lookup"><span data-stu-id="03bd2-122">For more information about support, see [Microsoft Association Algorithm](microsoft-association-algorithm.md).</span></span> <span data-ttu-id="03bd2-123">**[大小]** 資料行會顯示項目集內的項目數目。</span><span class="sxs-lookup"><span data-stu-id="03bd2-123">The **Size** column displays the number of items in the itemset.</span></span> <span data-ttu-id="03bd2-124">**[項目集]** 資料行會顯示模型探索的實際項目集。</span><span class="sxs-lookup"><span data-stu-id="03bd2-124">The **Itemset** column displays the actual itemset that the model discovered.</span></span> <span data-ttu-id="03bd2-125">您可以使用 **[顯示]** 清單來控制項目集的格式，您可以將它設定為下列選項：</span><span class="sxs-lookup"><span data-stu-id="03bd2-125">You can control the format of the itemset by using the **Show** list, which you can set to the following options:</span></span>  
  
-   <span data-ttu-id="03bd2-126">**顯示屬性名稱和值**</span><span class="sxs-lookup"><span data-stu-id="03bd2-126">**Show attribute name and value**</span></span>  
  
-   <span data-ttu-id="03bd2-127">**只顯示屬性值**</span><span class="sxs-lookup"><span data-stu-id="03bd2-127">**Show attribute value only**</span></span>  
  
-   <span data-ttu-id="03bd2-128">**只顯示屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="03bd2-128">**Show attribute name only**</span></span>  
  
 <span data-ttu-id="03bd2-129">您可以使用 **[最小案例數]** 和 **[項目集大小下限]**，來篩選索引標籤中所顯示的項目集數目。</span><span class="sxs-lookup"><span data-stu-id="03bd2-129">You can filter the number of itemsets that are displayed in the tab by using **Minimum support** and **Minimum itemset size**.</span></span> <span data-ttu-id="03bd2-130">您可以使用 **[篩選項目集]** 和輸入必須存在的項目集特性，來進一步限制所顯示的項目集數目。</span><span class="sxs-lookup"><span data-stu-id="03bd2-130">You can limit the number of displayed itemsets even more by using **Filter Itemset** and entering an itemset characteristic that must exist.</span></span> <span data-ttu-id="03bd2-131">例如，若您輸入「Water Bottle = existing」，您就可以將項目集限制為僅包含水壺的那些項目集。</span><span class="sxs-lookup"><span data-stu-id="03bd2-131">For example, if you type "Water Bottle = existing", you can limit the itemsets to only those that contain a water bottle.</span></span> <span data-ttu-id="03bd2-132">**[篩選項目集]** 選項也會顯示您先前已用過的篩選清單。</span><span class="sxs-lookup"><span data-stu-id="03bd2-132">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
 <span data-ttu-id="03bd2-133">您可以按一下資料行標題來排序方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="03bd2-133">You can sort the rows in the grid by clicking a column heading.</span></span>  
  
 [<span data-ttu-id="03bd2-134">回到頁首</span><span class="sxs-lookup"><span data-stu-id="03bd2-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a><span data-ttu-id="03bd2-135">條</span><span class="sxs-lookup"><span data-stu-id="03bd2-135">Rules</span></span>  
 <span data-ttu-id="03bd2-136">**[規則]** 索引標籤會顯示關聯演算法探索的規則。</span><span class="sxs-lookup"><span data-stu-id="03bd2-136">The **Rules** tab displays the rules that the association algorithm discovered.</span></span> <span data-ttu-id="03bd2-137">**[規則]** 索引標籤有一個方格包含下列資料行： **[機率]**、 **[重要性]** 和 **[規則]**。</span><span class="sxs-lookup"><span data-stu-id="03bd2-137">The **Rules** tab includes a grid that contains the following columns: **Probability**, **Importance**, and **Rule**.</span></span> <span data-ttu-id="03bd2-138">機率是描述發生規則之結果的可能性。</span><span class="sxs-lookup"><span data-stu-id="03bd2-138">The probability describes how likely the result of a rule is to occur.</span></span> <span data-ttu-id="03bd2-139">重要性是設計來測量規則的效益。</span><span class="sxs-lookup"><span data-stu-id="03bd2-139">The importance is designed to measure the usefulness of a rule.</span></span> <span data-ttu-id="03bd2-140">雖然規則發生的機率很高，但規則的效益本身可能不重要。</span><span class="sxs-lookup"><span data-stu-id="03bd2-140">Although the probability that a rule will occur may be high, the usefulness of the rule may in itself be unimportant.</span></span> <span data-ttu-id="03bd2-141">重要性資料行會描述這方面。</span><span class="sxs-lookup"><span data-stu-id="03bd2-141">The importance column addresses this.</span></span> <span data-ttu-id="03bd2-142">例如，若每一個項目集包含屬性的特定狀態，則預測狀態的規則只是一般規則，即使機率很高也一樣。</span><span class="sxs-lookup"><span data-stu-id="03bd2-142">For example, if every itemset contains a specific state of an attribute, a rule that predicts state is trivial, even though the probability is very high.</span></span> <span data-ttu-id="03bd2-143">重要性愈高，規則就愈重要。</span><span class="sxs-lookup"><span data-stu-id="03bd2-143">The greater the importance, the more important the rule is.</span></span>  
  
 <span data-ttu-id="03bd2-144">您可以使用 [**最小**機率] 和 [**最低重要性**] 來篩選規則，類似于您可以在 [**專案集**] 索引標籤上執行的篩選。您也可以使用 [**篩選規則**]，根據其包含的屬性狀態來篩選規則。</span><span class="sxs-lookup"><span data-stu-id="03bd2-144">You can use **Minimum probability** and **Minimum importance** to filter the rules, similar to the filtering you can do on the **Itemsets** tab. You can also use **Filter Rule** to filter a rule based on the states of the attributes that it contains.</span></span>  
  
 <span data-ttu-id="03bd2-145">您可以按一下資料行標題來排序方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="03bd2-145">You can sort the rows in the grid by clicking a column heading.</span></span>  
  
 [<span data-ttu-id="03bd2-146">回到頁首</span><span class="sxs-lookup"><span data-stu-id="03bd2-146">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="dependency-net"></a><a name="BKMK_Dependency"></a><span data-ttu-id="03bd2-147">相依性網路</span><span class="sxs-lookup"><span data-stu-id="03bd2-147">Dependency Net</span></span>  
 <span data-ttu-id="03bd2-148">**[相依性網路]** 索引標籤包含相依性網路檢視器。</span><span class="sxs-lookup"><span data-stu-id="03bd2-148">The **Dependency Net** tab includes a dependency network viewer.</span></span> <span data-ttu-id="03bd2-149">檢視器中的每一個節點代表一個項目，例如「state = WA」。</span><span class="sxs-lookup"><span data-stu-id="03bd2-149">Each node in the viewer represents an item, such as "state = WA".</span></span> <span data-ttu-id="03bd2-150">節點之間的箭頭代表項目之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="03bd2-150">The arrow between nodes represents the association between items.</span></span> <span data-ttu-id="03bd2-151">根據演算法探索的規則，箭頭的方向會指出項目之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="03bd2-151">The direction of the arrow dictates the association between the items according to the rules that the algorithm discovered.</span></span> <span data-ttu-id="03bd2-152">例如，如果檢視器包含三個專案： A、B 和 C，而 C 是由 A 和 B 預測，則如果您選取節點 C，則兩個箭頭會指向節點 C-A 到 C，B 到 C。</span><span class="sxs-lookup"><span data-stu-id="03bd2-152">For example, if the viewer contains three items, A, B, and C, and C is predicted by A and B, if you select node C, two arrows point toward node C - A to C and B to C.</span></span>  
  
 <span data-ttu-id="03bd2-153">檢視器左邊的滑桿會有篩選的作用，與規則的機率相關。</span><span class="sxs-lookup"><span data-stu-id="03bd2-153">The slider at the left of the viewer acts as a filter that is tied to the probability of the rules.</span></span> <span data-ttu-id="03bd2-154">降低滑桿只顯示最強的連結。</span><span class="sxs-lookup"><span data-stu-id="03bd2-154">Lowering the slider shows only the strongest links.</span></span>  
  
 [<span data-ttu-id="03bd2-155">回到頁首</span><span class="sxs-lookup"><span data-stu-id="03bd2-155">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="03bd2-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03bd2-156">See Also</span></span>  
 <span data-ttu-id="03bd2-157">[Microsoft 關聯分析演算法](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="03bd2-157">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="03bd2-158">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="03bd2-158">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="03bd2-159">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="03bd2-159">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="03bd2-160">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="03bd2-160">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="03bd2-161">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="03bd2-161">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
