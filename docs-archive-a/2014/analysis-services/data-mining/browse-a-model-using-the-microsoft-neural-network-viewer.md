---
title: 使用 Microsoft 類神經網路檢視器流覽模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model content, viewing
- classification mining model [Analysis Services]
- Microsoft Neural Network Viewer
- regression algorithms [Analysis Services]
- Neural Network Viewer [Analysis Services]
- neural network model [Analysis Services]
ms.assetid: 2343d746-c4f4-499b-9d3c-17d63310a9a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 77e08955d09b7995e34ac94b75f809a303ca0d2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607184"
---
# <a name="browse-a-model-using-the-microsoft-neural-network-viewer"></a><span data-ttu-id="a9245-102">使用 Microsoft 類神經網路檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="a9245-102">Browse a Model Using the Microsoft Neural Network Viewer</span></span>
  <span data-ttu-id="a9245-103">中的類 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神經網路檢視器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會顯示以類神經網路演算法建立的採礦模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a9245-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="a9245-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法建立可分析多個輸入和輸出的分類和迴歸採礦模型，對於開放式分析和瀏覽十分有用。</span><span class="sxs-lookup"><span data-stu-id="a9245-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates classification and regression mining models that can analyze multiple inputs and outputs, and is very useful for open-ended analyses and exploration.</span></span> <span data-ttu-id="a9245-105">如需有關這個演算法的詳細資訊，請參閱＜ [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a9245-105">For more information about this algorithm, see [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md).</span></span>  
  
 <span data-ttu-id="a9245-106">在您使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路檢視器瀏覽模型時，通常會選擇某個目標屬性和狀態，然後使用該檢視器來查看輸入屬性是如何影響結果。</span><span class="sxs-lookup"><span data-stu-id="a9245-106">When you explore a model using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer, you typically pick some target attribute and state, and then use the viewer to see how input attributes affect the outcome</span></span>  
  
 <span data-ttu-id="a9245-107">例如，假設您知道有關某一類別潛在客戶的下列事實：</span><span class="sxs-lookup"><span data-stu-id="a9245-107">For example, suppose you know these facts about a class of potential customers:</span></span>  
  
-   <span data-ttu-id="a9245-108">中年人 (40 至 50 歲)。</span><span class="sxs-lookup"><span data-stu-id="a9245-108">Middle aged (40 to 50 years old).</span></span>  
  
-   <span data-ttu-id="a9245-109">擁有房子。</span><span class="sxs-lookup"><span data-stu-id="a9245-109">Owns a home.</span></span>  
  
-   <span data-ttu-id="a9245-110">有兩個仍住在家中的孩子。</span><span class="sxs-lookup"><span data-stu-id="a9245-110">Has two children who still live at home.</span></span>  
  
 <span data-ttu-id="a9245-111">如何將這些屬性與客戶將進行購買的可能性相互關聯？</span><span class="sxs-lookup"><span data-stu-id="a9245-111">How can you correlate these attributes with the likelihood that the customer will make a purchase?</span></span>  
  
 <span data-ttu-id="a9245-112">透過將購買行為做為目標結果來建立類神經網路模型，您可以瀏覽客戶屬性 (例如高收入) 的多個組合，並且發現哪個屬性組合最有可能影響購買行為。</span><span class="sxs-lookup"><span data-stu-id="a9245-112">By building a neural network model using purchasing behavior as the target outcome, you can explore multiple combinations on customer attributes, such as high income, and discover which combination of attributes is most likely to influence purchasing behavior.</span></span> <span data-ttu-id="a9245-113">例如，您可能會發現決定因素是上班通勤距離。</span><span class="sxs-lookup"><span data-stu-id="a9245-113">For example, you might discover that the determining factor is the distance that they commute to work.</span></span>  
  
 <span data-ttu-id="a9245-114">如果您需要更詳細的檢視資訊，例如表示已發現的每個模式的方程式，則可以切換檢視並且使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="a9245-114">If you need to more view detailed information, such as the equations that represent each pattern that was discovered, you can switch views and use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="a9245-115">如需詳細資訊，請參閱[使用 Microsoft 一般內容樹狀檢視器瀏覽模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a9245-115">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="a9245-116">檢視器索引標籤</span><span class="sxs-lookup"><span data-stu-id="a9245-116">Viewer Tabs</span></span>  
 <span data-ttu-id="a9245-117">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中瀏覽採礦模型時，該模型會在適合它的檢視器中，顯示於資料採礦設計師的 **[採礦模型檢視器]** 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="a9245-117">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="a9245-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路檢視器會提供下列索引標籤，用來瀏覽類神經網路採礦模型：</span><span class="sxs-lookup"><span data-stu-id="a9245-118">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer provides the following tabs for use in exploring neural network mining models:</span></span>  
  
-   [<span data-ttu-id="a9245-119">輸入</span><span class="sxs-lookup"><span data-stu-id="a9245-119">Inputs</span></span>](#BKMK_Inputs)  
  
-   [<span data-ttu-id="a9245-120">輸出</span><span class="sxs-lookup"><span data-stu-id="a9245-120">Outputs</span></span>](#BKMK_Outputs)  
  
-   [<span data-ttu-id="a9245-121">變數</span><span class="sxs-lookup"><span data-stu-id="a9245-121">Variables</span></span>](#BKMK_Characteristics)  
  
###  <a name="inputs"></a><a name="BKMK_Inputs"></a><span data-ttu-id="a9245-122">輸入</span><span class="sxs-lookup"><span data-stu-id="a9245-122">Inputs</span></span>  
 <span data-ttu-id="a9245-123">使用 **[輸入]** 索引標籤選擇模型用來做為輸入的屬性和值。</span><span class="sxs-lookup"><span data-stu-id="a9245-123">Use the **Inputs** tab to choose the attributes and values that the model used as inputs.</span></span> <span data-ttu-id="a9245-124">根據預設，當檢視器開啟時包含所有屬性。</span><span class="sxs-lookup"><span data-stu-id="a9245-124">By default, the viewer opens with all attributes included.</span></span> <span data-ttu-id="a9245-125">在此預設檢視中，模型會選擇哪些是要顯示的最重要的屬性值。</span><span class="sxs-lookup"><span data-stu-id="a9245-125">In this default view, the model chooses which attribute values are the most important to display.</span></span>  
  
 <span data-ttu-id="a9245-126">若要選取輸入屬性，請按一下 [輸入]\*\*\*\* 方格的 [屬性]\*\*\*\* 資料行內，然後從下拉式清單中選取屬性。</span><span class="sxs-lookup"><span data-stu-id="a9245-126">To select an input attribute, click inside the **Attribute** column of the **Input** grid, and select an attribute from the drop-down list.</span></span> <span data-ttu-id="a9245-127">(只有模型所包含的屬性才會包含在清單中)。</span><span class="sxs-lookup"><span data-stu-id="a9245-127">(Only attributes that are included in the model are included in the list.)</span></span>  
  
 <span data-ttu-id="a9245-128">第一個相異值出現在 **[值]** 資料行之下。</span><span class="sxs-lookup"><span data-stu-id="a9245-128">The first distinct value appears under the **Value** column.</span></span> <span data-ttu-id="a9245-129">按一下預設值會顯示一份清單，它包含相關聯屬性的所有可能狀態。</span><span class="sxs-lookup"><span data-stu-id="a9245-129">Clicking the default value reveals a list that contains all the possible states of the associated attribute.</span></span> <span data-ttu-id="a9245-130">您可以選取要調查的狀態。</span><span class="sxs-lookup"><span data-stu-id="a9245-130">You can select the state that you want to investigate.</span></span> <span data-ttu-id="a9245-131">您可以選取任何您想要的屬性，數目不限。</span><span class="sxs-lookup"><span data-stu-id="a9245-131">You can select as many attributes as you want.</span></span>  
  
 [<span data-ttu-id="a9245-132">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a9245-132">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="outputs"></a><a name="BKMK_Outputs"></a><span data-ttu-id="a9245-133">產出</span><span class="sxs-lookup"><span data-stu-id="a9245-133">Outputs</span></span>  
 <span data-ttu-id="a9245-134">使用 **[輸出]** 索引標籤選擇要調查的結果屬性。</span><span class="sxs-lookup"><span data-stu-id="a9245-134">Use the **Outputs** tab to choose the outcome attribute to investigate.</span></span> <span data-ttu-id="a9245-135">您可以選擇任何兩個結果狀態來進行比較，並且假設在建立模型時資料行已定義為可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="a9245-135">You can choose any two outcome states to compare, assuming the columns were defined as predictable attributes when the model was created.</span></span>  
  
 <span data-ttu-id="a9245-136">使用 **OutputAttribute** 清單來選取屬性。</span><span class="sxs-lookup"><span data-stu-id="a9245-136">Use the **OutputAttribute** list to select an attribute.</span></span> <span data-ttu-id="a9245-137">接著，您可以從 **[值 1]** 和 **[值 2]** 清單中，選取與屬性相關聯的兩個狀態。</span><span class="sxs-lookup"><span data-stu-id="a9245-137">You can then select two states that are associated with the attribute from the **Value 1** and **Value 2** lists.</span></span> <span data-ttu-id="a9245-138">輸出屬性的這兩個狀態將會在 **[變數]** 窗格中做比較。</span><span class="sxs-lookup"><span data-stu-id="a9245-138">These two states of the output attribute will be compared in the **Variables** pane.</span></span>  
  
 [<span data-ttu-id="a9245-139">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a9245-139">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="variables"></a><a name="BKMK_Characteristics"></a><span data-ttu-id="a9245-140">變數</span><span class="sxs-lookup"><span data-stu-id="a9245-140">Variables</span></span>  
 <span data-ttu-id="a9245-141">[變數]\*\*\*\* 索引標籤中的方格包含下列資料行：[屬性]\*\*\*\*、[值]\*\*\*\*、[喜好 [值 1]]\*\*\*\* 和 [喜好 [值 2]]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a9245-141">The grid in the **Variables** tab contains the following columns: **Attribute**, **Value**, **Favors [value 1]**, and **Favors [value 2]**.</span></span> <span data-ttu-id="a9245-142">依預設，資料行是依 [喜好 [值 1]]\*\*\*\* 的程度來排序。</span><span class="sxs-lookup"><span data-stu-id="a9245-142">By default, the columns are sorted by the strength of **Favors [value 1]**.</span></span> <span data-ttu-id="a9245-143">按一下資料行標題會將排序順序變更為選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="a9245-143">Clicking a column heading changes the sort order to the selected column.</span></span>  
  
 <span data-ttu-id="a9245-144">屬性右邊的列會顯示指定的輸入屬性狀態所喜好的輸出屬性狀態。</span><span class="sxs-lookup"><span data-stu-id="a9245-144">A bar to the right of the attribute shows which state of the output attribute the specified input attribute state favors.</span></span> <span data-ttu-id="a9245-145">此橫條的大小會顯示輸出狀態喜好輸入狀態的強烈程度。</span><span class="sxs-lookup"><span data-stu-id="a9245-145">The size of the bar shows how strongly the output state favors the input state.</span></span>  
  
 [<span data-ttu-id="a9245-146">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a9245-146">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="a9245-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9245-147">See Also</span></span>  
 <span data-ttu-id="a9245-148">[Microsoft 類神經網路演算法](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a9245-148">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="a9245-149">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="a9245-149">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="a9245-150">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="a9245-150">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="a9245-151">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a9245-151">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="a9245-152">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="a9245-152">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
