---
title: 使用 Microsoft 貝氏貝氏機率分類 Viewer 流覽模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discrimination [Analysis Services]
- naive bayes model [Analysis Services]
- Bayesian classifiers
- mining model content, viewing
- predictive modeling [Analysis Services]
- Naive Bayes Viewer [Analysis Services]
- data mining [Analysis Services], predictive modeling
- Microsoft Naive Bayes Viewer
- histograms [Analysis Services]
- mining models [Analysis Services], predictive modeling
- dependencies [Analysis Services]
ms.assetid: 19743095-63c1-4486-8c1d-2efc143243be
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03469e73d82a389426f91d8757630f50fe78fc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607187"
---
# <a name="browse-a-model-using-the-microsoft-naive-bayes-viewer"></a><span data-ttu-id="22bc2-102">使用 Microsoft 貝氏機率分類檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="22bc2-102">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>
  <span data-ttu-id="22bc2-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]中的貝氏貝氏機率分類檢視器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會顯示以貝氏貝氏機率分類演算法建立的採礦模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="22bc2-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span> <span data-ttu-id="22bc2-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法是可高度適應預測模型工作的分類演算法。</span><span class="sxs-lookup"><span data-stu-id="22bc2-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm that is highly adaptable to predictive modeling tasks.</span></span> <span data-ttu-id="22bc2-105">如需有關這個演算法的詳細資訊，請參閱＜ [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md)＞。</span><span class="sxs-lookup"><span data-stu-id="22bc2-105">For more information about this algorithm, see [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md).</span></span>  
  
 <span data-ttu-id="22bc2-106">由於貝氏機率分類模型的主要用途之一是要提供一個方式來快速瀏覽資料集內的資料，因此 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類檢視器會提供數個方法，來顯示可預測屬性和輸入屬性之間的互動。</span><span class="sxs-lookup"><span data-stu-id="22bc2-106">Because one of the main purposes of a naive Bayes model is to provide a way to quickly explore the data in a dataset, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer provides several methods for displaying the interaction between predictable attributes and input attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22bc2-107">如果您要檢視有關此模型中所用的方程式及所探索之模式的詳細資訊，可以切換至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="22bc2-107">If you want to view detailed information about the equations used in the model and the patterns that were discovered, you can switch to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="22bc2-108">如需詳細資訊，請參閱[使用 Microsoft 一般內容樹狀檢視器瀏覽模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="22bc2-108">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="22bc2-109">檢視器索引標籤</span><span class="sxs-lookup"><span data-stu-id="22bc2-109">Viewer Tabs</span></span>  
 <span data-ttu-id="22bc2-110">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中瀏覽採礦模型時，該模型會在適合它的檢視器中，顯示於資料採礦設計師的 **[採礦模型檢視器]** 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="22bc2-110">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="22bc2-111">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類檢視器會提供用來瀏覽資料的下列索引標籤：</span><span class="sxs-lookup"><span data-stu-id="22bc2-111">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer provides the following tabs for exploring data:</span></span>  
  
-   [<span data-ttu-id="22bc2-112">相依性網路</span><span class="sxs-lookup"><span data-stu-id="22bc2-112">Dependency Network</span></span>](#BKMK_Dependency)  
  
-   [<span data-ttu-id="22bc2-113">屬性設定檔</span><span class="sxs-lookup"><span data-stu-id="22bc2-113">Attribute Profiles</span></span>](#BKMK_Profiles)  
  
-   [<span data-ttu-id="22bc2-114">屬性特性</span><span class="sxs-lookup"><span data-stu-id="22bc2-114">Attribute Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="22bc2-115">屬性辨識</span><span class="sxs-lookup"><span data-stu-id="22bc2-115">Attribute Discrimination</span></span>](#BKMK_Discrimination)  
  
##  <a name="dependency-network"></a><a name="BKMK_Dependency"></a><span data-ttu-id="22bc2-116">相依性網路</span><span class="sxs-lookup"><span data-stu-id="22bc2-116">Dependency Network</span></span>  
 <span data-ttu-id="22bc2-117">**[相依性網路]** 索引標籤會顯示模型中的輸入屬性和可預測屬性之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="22bc2-117">The **Dependency Network** tab displays the dependencies between the input attributes and the predictable attributes in a model.</span></span> <span data-ttu-id="22bc2-118">檢視器左邊的滑桿會有篩選的作用，與相依性程度相關。</span><span class="sxs-lookup"><span data-stu-id="22bc2-118">The slider at the left of the viewer acts as a filter that is tied to the strengths of the dependencies.</span></span> <span data-ttu-id="22bc2-119">降低滑桿只顯示最強的連結。</span><span class="sxs-lookup"><span data-stu-id="22bc2-119">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="22bc2-120">當您選取節點時，檢視器會反白顯示該節點特定的相依性。</span><span class="sxs-lookup"><span data-stu-id="22bc2-120">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="22bc2-121">例如，若您選擇一個可預測的節點，檢視器也會反白顯示每一個可協助預測該可預測節點的節點。</span><span class="sxs-lookup"><span data-stu-id="22bc2-121">For example, if you choose a predictable node, the viewer also highlights each node that helps predict the predictable node.</span></span>  
  
 <span data-ttu-id="22bc2-122">檢視器底端的圖例會將色碼連結至圖表中的相依性類型。</span><span class="sxs-lookup"><span data-stu-id="22bc2-122">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="22bc2-123">例如，當您選取可預測的節點時，可預測節點會呈現淺粉藍色陰影，而預測所選取之節點的節點則會呈現橙色陰影。</span><span class="sxs-lookup"><span data-stu-id="22bc2-123">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="22bc2-124">回到頁首</span><span class="sxs-lookup"><span data-stu-id="22bc2-124">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-profiles"></a><a name="BKMK_Profiles"></a> <span data-ttu-id="22bc2-125">屬性設定檔</span><span class="sxs-lookup"><span data-stu-id="22bc2-125">Attribute Profiles</span></span>  
 <span data-ttu-id="22bc2-126">**[屬性設定檔]** 索引標籤會在方格中顯示長條圖。</span><span class="sxs-lookup"><span data-stu-id="22bc2-126">The **Attribute Profiles** tab displays histograms in a grid.</span></span> <span data-ttu-id="22bc2-127">您可以使用這個方格，來比較您在 **[可預測]** 方塊中選取的可預測屬性與模型中的所有其他屬性。</span><span class="sxs-lookup"><span data-stu-id="22bc2-127">You can use this grid to compare the predictable attribute that you select in the **Predictable** box to all other attributes that are in the model.</span></span> <span data-ttu-id="22bc2-128">索引標籤中的每一個資料行代表可預測屬性的狀態。</span><span class="sxs-lookup"><span data-stu-id="22bc2-128">Each column in the tab represents a state of the predictable attribute.</span></span> <span data-ttu-id="22bc2-129">如果可預測屬性有許多狀態，您可以調整 **[長條圖列]** 來變更會出現在長條圖中的狀態數目。</span><span class="sxs-lookup"><span data-stu-id="22bc2-129">If the predictable attribute has many states, you can change the number of states that appear in the histogram by adjusting the **Histogram bars**.</span></span> <span data-ttu-id="22bc2-130">如果您選擇的數目小於屬性中的狀態總數，狀態就會依支援的順序列出，剩餘狀態則收集到單一灰色值區內。</span><span class="sxs-lookup"><span data-stu-id="22bc2-130">If the number you choose is less than the total number of states in the attribute, the states are listed in order of support, with the remaining states collected into a single gray bucket.</span></span>  
  
 <span data-ttu-id="22bc2-131">若要顯示使長條圖色彩與屬性狀態相關的採礦圖例，請按一下 **[顯示圖例]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="22bc2-131">To display a Mining Legend that relates the colors of the histogram to the states of an attribute, click the **Show Legend** check box.</span></span> <span data-ttu-id="22bc2-132">採礦圖例也會針對您所選取的每個屬性值組顯示案例的分佈情況。</span><span class="sxs-lookup"><span data-stu-id="22bc2-132">The Mining Legend also displays the distribution of cases for each attribute-value pair that you select.</span></span>  
  
 <span data-ttu-id="22bc2-133">若要將方格的內容複製到 [剪貼簿] 作為一個 HTML 資料表，請以滑鼠右鍵按一下 [屬性設定檔]\*\*\*\* 索引標籤，然後選取 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22bc2-133">To copy the contents of the grid to the Clipboard as an HTML table, right-click the **Attribute Profiles** tab and select **Copy**.</span></span>  
  
 [<span data-ttu-id="22bc2-134">回到頁首</span><span class="sxs-lookup"><span data-stu-id="22bc2-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-characteristics"></a><a name="BKMK_Characteristics"></a><span data-ttu-id="22bc2-135">屬性特性</span><span class="sxs-lookup"><span data-stu-id="22bc2-135">Attribute Characteristics</span></span>  
 <span data-ttu-id="22bc2-136">若要使用 **[屬性特性]** 索引標籤，請從 **[屬性]** 清單中選取一個可預測屬性，並從 **[值]** 清單中選取所選屬性的狀態。</span><span class="sxs-lookup"><span data-stu-id="22bc2-136">To use the **Attribute Characteristics** tab, select a predictable attribute from the **Attribute** list and select a state of the selected attribute from the **Value** list.</span></span> <span data-ttu-id="22bc2-137">當您設定這些變數時， **[屬性特性]** 索引標籤會顯示與所選屬性的所選案例相關聯之屬性的狀態。</span><span class="sxs-lookup"><span data-stu-id="22bc2-137">When you set these variables, the **Attribute Characteristics** tab displays the states of the attributes that are associated with the selected case of the selected attribute.</span></span> <span data-ttu-id="22bc2-138">屬性是依重要性排序。</span><span class="sxs-lookup"><span data-stu-id="22bc2-138">The attributes are sorted by importance.</span></span>  
  
 [<span data-ttu-id="22bc2-139">回到頁首</span><span class="sxs-lookup"><span data-stu-id="22bc2-139">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-discrimination"></a><a name="BKMK_Discrimination"></a><span data-ttu-id="22bc2-140">屬性辨識</span><span class="sxs-lookup"><span data-stu-id="22bc2-140">Attribute Discrimination</span></span>  
 <span data-ttu-id="22bc2-141">若要使用 **[屬性辨識]** 索引標籤，請從 **[屬性]**、 **[值 1]** 和 **[值 2]** 清單中選取可預測屬性和它的兩個狀態。</span><span class="sxs-lookup"><span data-stu-id="22bc2-141">To use the **Attribute Discrimination** tab, select a predictable attribute and two of its states from the **Attribute**, **Value 1**, and **Value 2** lists.</span></span> <span data-ttu-id="22bc2-142">接著， **[屬性辨識]** 索引標籤上的方格會在資料行中顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="22bc2-142">The grid on the **Attribute Discrimination** tab then displays the following information in columns:</span></span>  
  
 <span data-ttu-id="22bc2-143">**屬性**</span><span class="sxs-lookup"><span data-stu-id="22bc2-143">**Attribute**</span></span>  
 <span data-ttu-id="22bc2-144">列出資料集內的其他屬性，這些屬性包含一個非常喜好可預測屬性之其中一個狀態的狀態。</span><span class="sxs-lookup"><span data-stu-id="22bc2-144">Lists other attributes in the dataset that contain a state that highly favors one state of the predictable attribute.</span></span>  
  
 <span data-ttu-id="22bc2-145">**值**</span><span class="sxs-lookup"><span data-stu-id="22bc2-145">**Values**</span></span>  
 <span data-ttu-id="22bc2-146">在 [屬性]\*\*\*\* 資料行中顯示屬性的值。</span><span class="sxs-lookup"><span data-stu-id="22bc2-146">Shows the value of the attribute in the **Attribute** column.</span></span>  
  
 <span data-ttu-id="22bc2-147">**照顧\<value 1>**</span><span class="sxs-lookup"><span data-stu-id="22bc2-147">**Favors \<value 1>**</span></span>  
 <span data-ttu-id="22bc2-148">顯示一個彩色列，它會指出屬性值喜好 [值 1]\*\*\*\* 中顯示之可預測屬性值的強烈程度。</span><span class="sxs-lookup"><span data-stu-id="22bc2-148">Shows a colored bar that indicates how strongly the attribute value favors the predictable attribute value shown in **Value 1**.</span></span>  
  
 <span data-ttu-id="22bc2-149">**照顧\<value 2>**</span><span class="sxs-lookup"><span data-stu-id="22bc2-149">**Favors \<value 2>**</span></span>  
 <span data-ttu-id="22bc2-150">顯示一個彩色列，它會指出屬性值喜好 [值 2]\*\*\*\* 中顯示之可預測屬性值的強烈程度。</span><span class="sxs-lookup"><span data-stu-id="22bc2-150">Shows a colored bar that indicates how strongly the attribute value favors the predictable attribute value shown in **Value 2**.</span></span>  
  
 [<span data-ttu-id="22bc2-151">回到頁首</span><span class="sxs-lookup"><span data-stu-id="22bc2-151">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="22bc2-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22bc2-152">See Also</span></span>  
 <span data-ttu-id="22bc2-153">[Microsoft 貝氏貝氏機率分類演算法](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="22bc2-153">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 <span data-ttu-id="22bc2-154">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="22bc2-154">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="22bc2-155">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="22bc2-155">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="22bc2-156">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="22bc2-156">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
