---
title: 資料採礦模型檢視器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- displaying data mining models
- mining models [Analysis Services], viewing
- data mining [Analysis Services], models
- viewing data mining models
- mining model content
- support [data mining]
- exploring data mining models [Analysis Services]
ms.assetid: 14c8e656-f63c-4e8a-a3af-1d580e823d28
author: minewiskan
ms.author: owend
ms.openlocfilehash: 70215231f8ed7c9c218a9c3bf15c06ce59949f69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585672"
---
# <a name="data-mining-model-viewers"></a><span data-ttu-id="d4442-102">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="d4442-102">Data Mining Model Viewers</span></span>
  <span data-ttu-id="d4442-103">在中定型資料採礦模型之後 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您可以流覽模型來尋找有趣的趨勢。</span><span class="sxs-lookup"><span data-stu-id="d4442-103">After you train a data mining model in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can explore the model to look for interesting trends.</span></span> <span data-ttu-id="d4442-104">因為採礦模型的結果很複雜，而且其原始格式不易了解，所以用視覺化方式調查資料通常是了解演算法在資料內探索的規則和關聯性的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="d4442-104">Because the results of mining models are complex and can be difficult to understand in a raw format, visually investigating the data is often the easiest way to understand the rules and relationships that algorithms discover within the data.</span></span>  
  
 <span data-ttu-id="d4442-105">您用來建立模型的每一個演算法都會傳回不同類型的結果。</span><span class="sxs-lookup"><span data-stu-id="d4442-105">Each algorithm that you use to build a model returns a different type of results.</span></span> <span data-ttu-id="d4442-106">因此， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會為每一個演算法提供個別的檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-106">Therefore, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides a separate viewer for each algorithm.</span></span> <span data-ttu-id="d4442-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中瀏覽採礦模型時，該模型會使用適合它的檢視器顯示在資料採礦設計師的 **[採礦模型檢視器]** 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="d4442-107">When you browse a mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer, using the appropriate viewer for the model.</span></span>  
  
## <a name="how-to-use-the-model-viewers"></a><span data-ttu-id="d4442-108">如何使用模型檢視器</span><span class="sxs-lookup"><span data-stu-id="d4442-108">How to Use the Model Viewers</span></span>  
 <span data-ttu-id="d4442-109">您要先選取採礦模型，然後再選取檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-109">First you select the mining model and then you select a viewer.</span></span> <span data-ttu-id="d4442-110">每一個模型一定都有兩個可用的檢視器：自訂檢視器 (可包含多個索引標籤) 和一般檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-110">Each model always has two viewers available: a custom viewer, which can include multiple tabs, and the generic viewer.</span></span>  
  
 <span data-ttu-id="d4442-111">根據您選取的模型類型而定，您會看到瀏覽模型的不同選項。</span><span class="sxs-lookup"><span data-stu-id="d4442-111">Depending on the type of the model that you selected, you will see very different options for exploring the model.</span></span> <span data-ttu-id="d4442-112">與每一個模型類型有關的自訂檢視器會依照您用來建立選定資料採礦模型的演算法而訂製。</span><span class="sxs-lookup"><span data-stu-id="d4442-112">The custom viewers associated with each model type are tailored to the algorithm that you used to create the selected data mining model.</span></span> <span data-ttu-id="d4442-113">每一個自訂檢視器都有各種工具和對話方塊，可幫助您瀏覽模型中的統計資料和模式、檢視圖表，或是以互動方式處理機率臨界值或依名稱篩選掉項目。</span><span class="sxs-lookup"><span data-stu-id="d4442-113">Each custom viewer has a variety of tools and dialog boxes for helping you explore the statistics and patterns in the model, view charts, or interactively work with probability thresholds or filter out items by name.</span></span>  
  
 <span data-ttu-id="d4442-114">下圖說明當您為相同的模型選擇自訂檢視器和一般檢視器時，兩者之間的差異。</span><span class="sxs-lookup"><span data-stu-id="d4442-114">The following diagram illustrates the difference when you choose a custom viewer and the generic viewer for the same model.</span></span>  
  
1.  <span data-ttu-id="d4442-115">首先，您會看到當您選取以 Microsoft 時間序列演算法為根據的採礦模型時，所顯示的自訂檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-115">First, you see the custom viewer that is displayed when you select a mining model based on the Microsoft Time Series algorithm.</span></span>  
  
     <span data-ttu-id="d4442-116">這個特定自訂檢視器會自動建立時間序列的圖形，並提供五個預測。</span><span class="sxs-lookup"><span data-stu-id="d4442-116">This particular custom viewer automatically creates a graph of the time series and provides five predictions.</span></span>  
  
2.  <span data-ttu-id="d4442-117">接下來，您會看到使用 **[Microsoft 一般內容樹狀檢視器]** 時所顯示的相同模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-117">Next, you see the same model, displayed using the **Microsoft Generic Content Tree Viewer**.</span></span>  
  
     <span data-ttu-id="d4442-118">一般檢視器會在左邊顯示模型中的節點清單。</span><span class="sxs-lookup"><span data-stu-id="d4442-118">On the left, the generic viewer displays a list of the nodes in the model.</span></span> <span data-ttu-id="d4442-119">您可以按一下節點，在右窗格中檢視其內容。</span><span class="sxs-lookup"><span data-stu-id="d4442-119">You can click a node to view its contents in the right-hand pane.</span></span>  
  
 <span data-ttu-id="d4442-120">![採礦模型設計工具的概觀](../media/generic-mining-model-tab1.gif "採礦模型設計工具的概觀")</span><span class="sxs-lookup"><span data-stu-id="d4442-120">![Overview of mining model designer](../media/generic-mining-model-tab1.gif "Overview of mining model designer")</span></span>  
  
## <a name="more-about-the-microsoft-generic-content-tree-viewer"></a><span data-ttu-id="d4442-121">Microsoft 一般內容樹狀檢視器詳細資料</span><span class="sxs-lookup"><span data-stu-id="d4442-121">More about the Microsoft Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="d4442-122">您也可以使用 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) 來檢視每個模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-122">Each model can also be viewed using the [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="d4442-123">此檢視器會根據標準 HTML 表格格式來呈現採礦模型的內容。</span><span class="sxs-lookup"><span data-stu-id="d4442-123">This viewer presents the contents of the mining model according to a standard HTML table format.</span></span> <span data-ttu-id="d4442-124">但是，節點的排列和每一個節點的內容將會因為用來產生結果的演算法而有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="d4442-124">However, the arrangement of the nodes and the content of each node will differ greatly depending on the algorithm used to generate the results.</span></span>  
  
 <span data-ttu-id="d4442-125">雖然自訂檢視器的設計目的是要了瀏覽及了解模型，但是當您已經了解此模型而且想要從特定節點擷取統計資料或規則時，一般檢視器會更為實用。</span><span class="sxs-lookup"><span data-stu-id="d4442-125">Whereas the custom viewers are designed for exploring and understanding the model, the generic viewer is more useful when you already understand the model and want to extract statistics or rules from a specific node.</span></span> <span data-ttu-id="d4442-126">例如，當您想要檢視 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在分析期間擷取之有關模式與統計資料的詳細資訊 (例如節點的機率或迴歸公式) 時，您會使用一般檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-126">For example, you would use the generic viewer when you want to view detailed information about the patterns and statistics that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] captured during analysis, such as the probability of a node, or a regression formula.</span></span>  
  
 <span data-ttu-id="d4442-127">您也可以使用 DMX 撰寫 *「內容查詢」* (Content Query)，以取得在此檢視器中呈現的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="d4442-127">You can also write *content queries* using DMX to get all of the information that is presented in this viewer.</span></span> <span data-ttu-id="d4442-128">如需詳細資訊，請參閱 [內容查詢 &#40;資料採礦&#41;](content-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d4442-128">For more information, see [Content Queries &#40;Data Mining&#41;](content-queries-data-mining.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4442-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="d4442-129">In This Section</span></span>  
 <span data-ttu-id="d4442-130">下列主題會更詳細描述每一個檢視器以及如何解譯其中的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4442-130">The following topics describe in more detail each of the viewers, and how to interpret the information in them.</span></span>  
  
 [<span data-ttu-id="d4442-131">使用 Microsoft 樹狀檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="d4442-131">Browse a Model Using the Microsoft Tree Viewer</span></span>](browse-a-model-using-the-microsoft-tree-viewer.md)  
 <span data-ttu-id="d4442-132">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-132">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer.</span></span> <span data-ttu-id="d4442-133">這個檢視器會顯示以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法及 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線性迴歸演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-133">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span>  
  
 [<span data-ttu-id="d4442-134">使用 Microsoft 叢集檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="d4442-134">Browse a Model Using the Microsoft Cluster Viewer</span></span>](browse-a-model-using-the-microsoft-cluster-viewer.md)  
 <span data-ttu-id="d4442-135">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-135">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer.</span></span> <span data-ttu-id="d4442-136">這個檢視器會顯示以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-136">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="d4442-137">使用 Microsoft 時間序列檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="d4442-137">Browse a Model Using the Microsoft Time Series Viewer</span></span>](browse-a-model-using-the-microsoft-time-series-viewer.md)  
 <span data-ttu-id="d4442-138">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-138">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series Viewer.</span></span> <span data-ttu-id="d4442-139">這個檢視器會顯示以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-139">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="d4442-140">使用 Microsoft 貝氏機率分類檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="d4442-140">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
 <span data-ttu-id="d4442-141">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-141">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes viewer.</span></span> <span data-ttu-id="d4442-142">這個檢視器會顯示以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-142">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="d4442-143">使用 Microsoft 時序叢集檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="d4442-143">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>](browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
 <span data-ttu-id="d4442-144">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-144">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer.</span></span> <span data-ttu-id="d4442-145">這個檢視器會顯示以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-145">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="d4442-146">使用 Microsoft 關聯規則檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="d4442-146">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](browse-a-model-using-the-microsoft-association-rules-viewer.md)  
 <span data-ttu-id="d4442-147">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-147">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer.</span></span> <span data-ttu-id="d4442-148">這個檢視器會顯示以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯分析演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-148">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm.</span></span>  
  
 [<span data-ttu-id="d4442-149">使用 Microsoft 類神經網路檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="d4442-149">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](browse-a-model-using-the-microsoft-neural-network-viewer.md)  
 <span data-ttu-id="d4442-150">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路檢視器。</span><span class="sxs-lookup"><span data-stu-id="d4442-150">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer.</span></span> <span data-ttu-id="d4442-151">這個檢視器會顯示以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法建立的採礦模型，包括使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 羅吉斯迴歸演算法的模型。</span><span class="sxs-lookup"><span data-stu-id="d4442-151">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm, including models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="d4442-152">使用 Microsoft 一般內容樹狀檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="d4442-152">Browse a Model Using the Microsoft Generic Content Tree Viewer</span></span>](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)  
 <span data-ttu-id="d4442-153">描述一般檢視器中可用於所有資料採礦模型的詳細資訊，並提供範例說明如何解譯每種演算法的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4442-153">Describes the detailed information that is available in the generic viewer for all data mining models and provides examples of how to interpret the information for each algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4442-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4442-154">See Also</span></span>  
 <span data-ttu-id="d4442-155">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d4442-155">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="d4442-156">資料採礦設計師</span><span class="sxs-lookup"><span data-stu-id="d4442-156">Data Mining Designer</span></span>](data-mining-designer.md)  
  
  
