---
title: 類神經網路模型的採礦模型內容 (Analysis Services 資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- output neurons [Analysis Services]
- neural network algorithms [Analysis Services]
- output layer [Data Mining]
- hidden layer
- hidden neurons
- input layer [Data Mining]
- input neurons [Analysis Services]
- mining model content, neural network models
- neural network model [Analysis Services]
ms.assetid: ea21ff9d-857f-475c-bd3d-6d1405bad069
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f3dc1ff7badfae6c3dfcee9919f5879782764e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598664"
---
# <a name="mining-model-content-for-neural-network-models-analysis-services---data-mining"></a><span data-ttu-id="0a551-102">Mining Model Content for Neural Network Models (Analysis Services - Data Mining)</span><span class="sxs-lookup"><span data-stu-id="0a551-102">Mining Model Content for Neural Network Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="0a551-103">本主題描述使用 Microsoft 類神經網路演算法的模型專用的採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="0a551-103">This topic describes mining model content that is specific to models that use the Microsoft Neural Network algorithm.</span></span> <span data-ttu-id="0a551-104">如需如何解譯所有模型類型共用的統計資料與結構的說明，以及與採礦模型內容相關的一般詞彙說明，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="0a551-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-neural-network-model"></a><span data-ttu-id="0a551-105">了解類神經網路模型的結構</span><span class="sxs-lookup"><span data-stu-id="0a551-105">Understanding the Structure of a Neural Network Model</span></span>  
 <span data-ttu-id="0a551-106">每個類神經網路模型都有一個代表模型及其中繼資料的單一父節點，以及一個提供輸入屬性之相關描述性統計資料的臨界統計資料節點 (NODE_TYPE = 24)。</span><span class="sxs-lookup"><span data-stu-id="0a551-106">Each neural network model has a single parent node that represents the model and its metadata, and a marginal statistics node (NODE_TYPE = 24) that provides descriptive statistics about the input attributes.</span></span> <span data-ttu-id="0a551-107">臨界統計資料節點相當實用，因為該節點摘要輸入的相關資訊，您就不需要從個別節點查詢資料。</span><span class="sxs-lookup"><span data-stu-id="0a551-107">The marginal statistics node is useful because it summarizes information about inputs, so that you do not need to query data from the individual nodes.</span></span>  
  
 <span data-ttu-id="0a551-108">在這兩個節點下面，至少還有兩個節點，可能更多，取決於模型的可預測屬性數量。</span><span class="sxs-lookup"><span data-stu-id="0a551-108">Underneath these two nodes, there are at least two more nodes, and might be many more, depending on how many predictable attributes the model has.</span></span>  
  
-   <span data-ttu-id="0a551-109">第一個節點 (NODE_TYPE = 18) 永遠代表輸入層的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-109">The first node (NODE_TYPE = 18) always represents the top node of the input layer.</span></span> <span data-ttu-id="0a551-110">在這個最上層節點之下，您可以找到包含實際輸入屬性及其值的輸入節點 (NODE_TYPE = 21)。</span><span class="sxs-lookup"><span data-stu-id="0a551-110">Beneath this top node, you can find input nodes (NODE_TYPE = 21) that contain the actual input attributes and their values.</span></span>  
  
-   <span data-ttu-id="0a551-111">每個後續節點都包含不同的「子網路」\*\* (NODE_TYPE = 17)。</span><span class="sxs-lookup"><span data-stu-id="0a551-111">Successive nodes each contain a different *subnetwork* (NODE_TYPE = 17).</span></span> <span data-ttu-id="0a551-112">每個子網路永遠包含一個隱藏層 (NODE_TYPE = 19)，以及一個該子網路的輸出層 (NODE_TYPE = 20)。</span><span class="sxs-lookup"><span data-stu-id="0a551-112">Each subnetwork always contains a hidden layer (NODE_TYPE = 19), and an output layer (NODE_TYPE = 20) for that subnetwork.</span></span>  
  
 <span data-ttu-id="0a551-113">![類神經網路的模型內容結構](../media/modelcontentstructure-nn.gif "類神經網路的模型內容結構")</span><span class="sxs-lookup"><span data-stu-id="0a551-113">![structure of model content for neural networks](../media/modelcontentstructure-nn.gif "structure of model content for neural networks")</span></span>  
  
 <span data-ttu-id="0a551-114">輸入層中的資訊相當直接：每個輸入層 (NODE_TYPE = 18) 的最上層節點都當做一組輸入節點 (NODE_TYPE = 21) 的組合管理使用。</span><span class="sxs-lookup"><span data-stu-id="0a551-114">The information in the input layer is straightforward: the top node for each input layer (NODE_TYPE = 18) serves as an organizer for a collection of input nodes (NODE_TYPE = 21).</span></span> <span data-ttu-id="0a551-115">輸入節點的內容詳述於下表。</span><span class="sxs-lookup"><span data-stu-id="0a551-115">The content of the input nodes is described in the following table.</span></span>  
  
 <span data-ttu-id="0a551-116">每個子網路 (NODE_TYPE = 17) 都代表輸入層對於特定可預測屬性之影響的分析。</span><span class="sxs-lookup"><span data-stu-id="0a551-116">Each subnetwork (NODE_TYPE = 17) represents the analysis of the influence of the input layer on a particular predictable attribute.</span></span> <span data-ttu-id="0a551-117">如果有多個可預測輸出，則有多個子網路。</span><span class="sxs-lookup"><span data-stu-id="0a551-117">If there are multiple predictable outputs, there are multiple subnetworks.</span></span> <span data-ttu-id="0a551-118">每個子網路的隱藏層都包含多個隱藏節點 (NODE_TYPE = 22)，其中含有在該特定隱藏節點結束之每個轉換的加權詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0a551-118">The hidden layer for each subnetwork contains multiple hidden nodes (NODE_TYPE = 22) that contain details about the weights for each transition that ends in that particular hidden node.</span></span>  
  
 <span data-ttu-id="0a551-119">輸出層 (NODE_TYPE = 20) 包含輸出節點 (NODE_TYPE = 23)，其中每個節點都包含不同的可預測屬性值。</span><span class="sxs-lookup"><span data-stu-id="0a551-119">The output layer (NODE_TYPE = 20) contains output nodes (NODE_TYPE = 23) that each contain distinct values of the predictable attribute.</span></span> <span data-ttu-id="0a551-120">如果可預測屬性為連續的數值資料類型，則屬性只有一個輸出節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-120">If the predictable attribute is a continuous numeric data type, there is only one output node for the attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a551-121">羅吉斯迴歸演算法使用類神經網路的特殊案例，其中只有一個可預測結果，而且潛在有許多輸入。</span><span class="sxs-lookup"><span data-stu-id="0a551-121">The logistic regression algorithm uses a special case of a neural network that has only one predictable outcome and potentially many inputs.</span></span> <span data-ttu-id="0a551-122">羅吉斯迴歸不使用隱藏層。</span><span class="sxs-lookup"><span data-stu-id="0a551-122">Logistic regression does not use a hidden layer.</span></span>  
  
 <span data-ttu-id="0a551-123">瀏覽輸入和子網路結構最簡單的方式就是使用 **Microsoft 一般內容樹狀檢視器**。</span><span class="sxs-lookup"><span data-stu-id="0a551-123">The easiest way to explore the structure of the inputs and subnetworks is to use the **Microsoft Generic Content Tree viewer**.</span></span> <span data-ttu-id="0a551-124">您可以按一下任何節點將其展開並查看其子節點，或檢視包含在節點中的加權和其他統計資料。</span><span class="sxs-lookup"><span data-stu-id="0a551-124">You can click any node to expand it and see the child nodes, or view the weights and other statistics that is contained in the node.</span></span>  
  
 <span data-ttu-id="0a551-125">若要使用資料並查看模型讓輸入與輸出相互關聯的方式，請使用 **Microsoft 類神經網路檢視器**。</span><span class="sxs-lookup"><span data-stu-id="0a551-125">To work with the data and see how the model correlates inputs with outputs, use the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="0a551-126">您可以利用這個自訂的檢視器，篩選輸入屬性及其值，並以圖形方式查看這些屬性和值如何影響輸出。</span><span class="sxs-lookup"><span data-stu-id="0a551-126">By using this custom viewer, you can filter on input attributes and their values, and graphically see how they affect the outputs.</span></span> <span data-ttu-id="0a551-127">檢視器中的工具提示會顯示與每個成對輸入和輸出值相關聯的機率與增益。</span><span class="sxs-lookup"><span data-stu-id="0a551-127">The tooltips in the viewer show you the probability and lift associated with each pair of inputs and output values.</span></span> <span data-ttu-id="0a551-128">如需詳細資訊，請參閱 [使用 Microsoft 類神經網路檢視器瀏覽模型](browse-a-model-using-the-microsoft-neural-network-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="0a551-128">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
## <a name="model-content-for-a-neural-network-model"></a><span data-ttu-id="0a551-129">類神經網路模型的模型內容</span><span class="sxs-lookup"><span data-stu-id="0a551-129">Model Content for a Neural Network Model</span></span>  
 <span data-ttu-id="0a551-130">本節僅針對採礦模型內容中與類神經網路具有特定相關的資料行，提供詳細資料和範例。</span><span class="sxs-lookup"><span data-stu-id="0a551-130">This section provides detail and examples only for those columns in the mining model content that have particular relevance for neural networks.</span></span> <span data-ttu-id="0a551-131">如需結構描述資料列集 (例如 MODEL_CATALOG 和 MODEL_NAME) 中一般用途資料行的詳細資訊 (此處沒有說明)，或採礦模型術語的說明，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="0a551-131">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="0a551-132">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0a551-132">MODEL_CATALOG</span></span>  
 <span data-ttu-id="0a551-133">模型儲存位置所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-133">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="0a551-134">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="0a551-134">MODEL_NAME</span></span>  
 <span data-ttu-id="0a551-135">模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-135">Name of the model.</span></span>  
  
 <span data-ttu-id="0a551-136">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="0a551-136">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="0a551-137">對應至這個節點之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-137">The names of the attributes that correspond to this node.</span></span>  
  
|<span data-ttu-id="0a551-138">節點</span><span class="sxs-lookup"><span data-stu-id="0a551-138">Node</span></span>|<span data-ttu-id="0a551-139">內容</span><span class="sxs-lookup"><span data-stu-id="0a551-139">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0a551-140">模型根</span><span class="sxs-lookup"><span data-stu-id="0a551-140">Model root</span></span>|<span data-ttu-id="0a551-141">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-141">Blank</span></span>|  
|<span data-ttu-id="0a551-142">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="0a551-142">Marginal statistics</span></span>|<span data-ttu-id="0a551-143">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-143">Blank</span></span>|  
|<span data-ttu-id="0a551-144">輸入層</span><span class="sxs-lookup"><span data-stu-id="0a551-144">Input layer</span></span>|<span data-ttu-id="0a551-145">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-145">Blank</span></span>|  
|<span data-ttu-id="0a551-146">輸入節點</span><span class="sxs-lookup"><span data-stu-id="0a551-146">Input node</span></span>|<span data-ttu-id="0a551-147">輸入屬性名稱</span><span class="sxs-lookup"><span data-stu-id="0a551-147">Input attribute name</span></span>|  
|<span data-ttu-id="0a551-148">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0a551-148">Hidden layer</span></span>|<span data-ttu-id="0a551-149">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-149">Blank</span></span>|  
|<span data-ttu-id="0a551-150">隱藏節點</span><span class="sxs-lookup"><span data-stu-id="0a551-150">Hidden node</span></span>|<span data-ttu-id="0a551-151">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-151">Blank</span></span>|  
|<span data-ttu-id="0a551-152">輸出層</span><span class="sxs-lookup"><span data-stu-id="0a551-152">Output layer</span></span>|<span data-ttu-id="0a551-153">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-153">Blank</span></span>|  
|<span data-ttu-id="0a551-154">輸出節點</span><span class="sxs-lookup"><span data-stu-id="0a551-154">Output node</span></span>|<span data-ttu-id="0a551-155">輸出屬性名稱</span><span class="sxs-lookup"><span data-stu-id="0a551-155">Output attribute name</span></span>|  
  
 <span data-ttu-id="0a551-156">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="0a551-156">NODE_NAME</span></span>  
 <span data-ttu-id="0a551-157">節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-157">The name of the node.</span></span> <span data-ttu-id="0a551-158">此資料行包含與 NODE_UNIQUE_NAME 相同的值。</span><span class="sxs-lookup"><span data-stu-id="0a551-158">This column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="0a551-159">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="0a551-159">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="0a551-160">節點的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-160">The unique name of the node.</span></span>  
  
 <span data-ttu-id="0a551-161">如需有關名稱與識別碼如何提供模型之結構資訊的詳細資訊，請參閱＜ [使用節點名稱與識別碼](#bkmk_NodeIDs)＞一節。</span><span class="sxs-lookup"><span data-stu-id="0a551-161">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="0a551-162">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0a551-162">NODE_TYPE</span></span>  
 <span data-ttu-id="0a551-163">類神經網路模型會輸出下列節點類型：</span><span class="sxs-lookup"><span data-stu-id="0a551-163">A neural network model outputs the following node types:</span></span>  
  
|<span data-ttu-id="0a551-164">節點類型識別碼</span><span class="sxs-lookup"><span data-stu-id="0a551-164">Node Type ID</span></span>|<span data-ttu-id="0a551-165">描述</span><span class="sxs-lookup"><span data-stu-id="0a551-165">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="0a551-166">1</span><span class="sxs-lookup"><span data-stu-id="0a551-166">1</span></span>|<span data-ttu-id="0a551-167">模型。</span><span class="sxs-lookup"><span data-stu-id="0a551-167">Model.</span></span>|  
|<span data-ttu-id="0a551-168">17</span><span class="sxs-lookup"><span data-stu-id="0a551-168">17</span></span>|<span data-ttu-id="0a551-169">子網路的組合管理節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-169">Organizer node for the subnetwork.</span></span>|  
|<span data-ttu-id="0a551-170">18</span><span class="sxs-lookup"><span data-stu-id="0a551-170">18</span></span>|<span data-ttu-id="0a551-171">輸入層的組合管理節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-171">Organizer node for the input layer.</span></span>|  
|<span data-ttu-id="0a551-172">19</span><span class="sxs-lookup"><span data-stu-id="0a551-172">19</span></span>|<span data-ttu-id="0a551-173">隱藏層的組合管理節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-173">Organizer node for the hidden layer.</span></span>|  
|<span data-ttu-id="0a551-174">20</span><span class="sxs-lookup"><span data-stu-id="0a551-174">20</span></span>|<span data-ttu-id="0a551-175">輸出層的組合管理節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-175">Organizer node for the output layer.</span></span>|  
|<span data-ttu-id="0a551-176">21</span><span class="sxs-lookup"><span data-stu-id="0a551-176">21</span></span>|<span data-ttu-id="0a551-177">輸入屬性節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-177">Input attribute node.</span></span>|  
|<span data-ttu-id="0a551-178">22</span><span class="sxs-lookup"><span data-stu-id="0a551-178">22</span></span>|<span data-ttu-id="0a551-179">隱藏層節點</span><span class="sxs-lookup"><span data-stu-id="0a551-179">Hidden layer node</span></span>|  
|<span data-ttu-id="0a551-180">23</span><span class="sxs-lookup"><span data-stu-id="0a551-180">23</span></span>|<span data-ttu-id="0a551-181">輸出屬性節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-181">Output attribute node.</span></span>|  
|<span data-ttu-id="0a551-182">24</span><span class="sxs-lookup"><span data-stu-id="0a551-182">24</span></span>|<span data-ttu-id="0a551-183">臨界統計資料節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-183">Marginal statistics node.</span></span>|  
  
 <span data-ttu-id="0a551-184">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="0a551-184">NODE_CAPTION</span></span>  
 <span data-ttu-id="0a551-185">與節點關聯的標籤或標題。</span><span class="sxs-lookup"><span data-stu-id="0a551-185">A label or a caption associated with the node.</span></span> <span data-ttu-id="0a551-186">在類神經網路模型中，永遠為空白。</span><span class="sxs-lookup"><span data-stu-id="0a551-186">In neural network models, always blank.</span></span>  
  
 <span data-ttu-id="0a551-187">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0a551-187">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="0a551-188">節點所擁有子系數目的估計。</span><span class="sxs-lookup"><span data-stu-id="0a551-188">An estimate of the number of children that the node has.</span></span>  
  
|<span data-ttu-id="0a551-189">節點</span><span class="sxs-lookup"><span data-stu-id="0a551-189">Node</span></span>|<span data-ttu-id="0a551-190">內容</span><span class="sxs-lookup"><span data-stu-id="0a551-190">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0a551-191">模型根</span><span class="sxs-lookup"><span data-stu-id="0a551-191">Model root</span></span>|<span data-ttu-id="0a551-192">指出子節點的計數，其中至少包含 1 個網路、1 個必要的臨界節點，以及 1 個必要的輸入層。</span><span class="sxs-lookup"><span data-stu-id="0a551-192">Indicates the count of child nodes, which includes at least 1 network, 1 required marginal node, and 1 required input layer.</span></span> <span data-ttu-id="0a551-193">例如，如果值為 5，則有 3 個子網路。</span><span class="sxs-lookup"><span data-stu-id="0a551-193">For example, if the value is 5, there are 3 subnetworks.</span></span>|  
|<span data-ttu-id="0a551-194">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="0a551-194">Marginal statistics</span></span>|<span data-ttu-id="0a551-195">一律是 0。</span><span class="sxs-lookup"><span data-stu-id="0a551-195">Always 0.</span></span>|  
|<span data-ttu-id="0a551-196">輸入層</span><span class="sxs-lookup"><span data-stu-id="0a551-196">Input layer</span></span>|<span data-ttu-id="0a551-197">指出模型使用之輸入屬性和值配對的數目。</span><span class="sxs-lookup"><span data-stu-id="0a551-197">Indicates the number of input attribute-values pairs that were used by the model.</span></span>|  
|<span data-ttu-id="0a551-198">輸入節點</span><span class="sxs-lookup"><span data-stu-id="0a551-198">Input node</span></span>|<span data-ttu-id="0a551-199">一律是 0。</span><span class="sxs-lookup"><span data-stu-id="0a551-199">Always 0.</span></span>|  
|<span data-ttu-id="0a551-200">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0a551-200">Hidden layer</span></span>|<span data-ttu-id="0a551-201">指出模型建立之隱藏節點的數目。</span><span class="sxs-lookup"><span data-stu-id="0a551-201">Indicates the number of hidden nodes that were created by the model.</span></span>|  
|<span data-ttu-id="0a551-202">隱藏節點</span><span class="sxs-lookup"><span data-stu-id="0a551-202">Hidden node</span></span>|<span data-ttu-id="0a551-203">一律是 0。</span><span class="sxs-lookup"><span data-stu-id="0a551-203">Always 0.</span></span>|  
|<span data-ttu-id="0a551-204">輸出層</span><span class="sxs-lookup"><span data-stu-id="0a551-204">Output layer</span></span>|<span data-ttu-id="0a551-205">指出輸出值的數目。</span><span class="sxs-lookup"><span data-stu-id="0a551-205">Indicates the number of output values.</span></span>|  
|<span data-ttu-id="0a551-206">輸出節點</span><span class="sxs-lookup"><span data-stu-id="0a551-206">Output node</span></span>|<span data-ttu-id="0a551-207">一律是 0。</span><span class="sxs-lookup"><span data-stu-id="0a551-207">Always 0.</span></span>|  
  
 <span data-ttu-id="0a551-208">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="0a551-208">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="0a551-209">節點之父系的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-209">The unique name of the node's parent.</span></span> <span data-ttu-id="0a551-210">任何根層級的節點都會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="0a551-210">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="0a551-211">如需有關名稱與識別碼如何提供模型之結構資訊的詳細資訊，請參閱＜ [使用節點名稱與識別碼](#bkmk_NodeIDs)＞一節。</span><span class="sxs-lookup"><span data-stu-id="0a551-211">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="0a551-212">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0a551-212">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="0a551-213">使用者易記的節點描述。</span><span class="sxs-lookup"><span data-stu-id="0a551-213">A user-friendly description of the node.</span></span>  
  
|<span data-ttu-id="0a551-214">節點</span><span class="sxs-lookup"><span data-stu-id="0a551-214">Node</span></span>|<span data-ttu-id="0a551-215">內容</span><span class="sxs-lookup"><span data-stu-id="0a551-215">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0a551-216">模型根</span><span class="sxs-lookup"><span data-stu-id="0a551-216">Model root</span></span>|<span data-ttu-id="0a551-217">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-217">Blank</span></span>|  
|<span data-ttu-id="0a551-218">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="0a551-218">Marginal statistics</span></span>|<span data-ttu-id="0a551-219">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-219">Blank</span></span>|  
|<span data-ttu-id="0a551-220">輸入層</span><span class="sxs-lookup"><span data-stu-id="0a551-220">Input layer</span></span>|<span data-ttu-id="0a551-221">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-221">Blank</span></span>|  
|<span data-ttu-id="0a551-222">輸入節點</span><span class="sxs-lookup"><span data-stu-id="0a551-222">Input node</span></span>|<span data-ttu-id="0a551-223">輸入屬性名稱</span><span class="sxs-lookup"><span data-stu-id="0a551-223">Input attribute name</span></span>|  
|<span data-ttu-id="0a551-224">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0a551-224">Hidden layer</span></span>|<span data-ttu-id="0a551-225">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-225">Blank</span></span>|  
|<span data-ttu-id="0a551-226">隱藏節點</span><span class="sxs-lookup"><span data-stu-id="0a551-226">Hidden node</span></span>|<span data-ttu-id="0a551-227">指出隱藏節點清單中，隱藏節點順序的整數。</span><span class="sxs-lookup"><span data-stu-id="0a551-227">Integer that indicates the sequence of the hidden node in the list of hidden nodes.</span></span>|  
|<span data-ttu-id="0a551-228">輸出層</span><span class="sxs-lookup"><span data-stu-id="0a551-228">Output layer</span></span>|<span data-ttu-id="0a551-229">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-229">Blank</span></span>|  
|<span data-ttu-id="0a551-230">輸出節點</span><span class="sxs-lookup"><span data-stu-id="0a551-230">Output node</span></span>|<span data-ttu-id="0a551-231">如果輸出屬性是連續的，則包含輸出屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-231">If the output attribute is continuous, contains the name of the output attribute.</span></span><br /><br /> <span data-ttu-id="0a551-232">如果輸出屬性是離散或離散化的，則包含輸出屬性的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="0a551-232">If the output attribute is discrete or discretized, contains the name of the attribute and the value.</span></span>|  
  
 <span data-ttu-id="0a551-233">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="0a551-233">NODE_RULE</span></span>  
 <span data-ttu-id="0a551-234">節點中內嵌之規則的 XML 描述。</span><span class="sxs-lookup"><span data-stu-id="0a551-234">An XML description of the rule that is embedded in the node.</span></span>  
  
|<span data-ttu-id="0a551-235">節點</span><span class="sxs-lookup"><span data-stu-id="0a551-235">Node</span></span>|<span data-ttu-id="0a551-236">內容</span><span class="sxs-lookup"><span data-stu-id="0a551-236">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0a551-237">模型根</span><span class="sxs-lookup"><span data-stu-id="0a551-237">Model root</span></span>|<span data-ttu-id="0a551-238">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-238">Blank</span></span>|  
|<span data-ttu-id="0a551-239">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="0a551-239">Marginal statistics</span></span>|<span data-ttu-id="0a551-240">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-240">Blank</span></span>|  
|<span data-ttu-id="0a551-241">輸入層</span><span class="sxs-lookup"><span data-stu-id="0a551-241">Input layer</span></span>|<span data-ttu-id="0a551-242">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-242">Blank</span></span>|  
|<span data-ttu-id="0a551-243">輸入節點</span><span class="sxs-lookup"><span data-stu-id="0a551-243">Input node</span></span>|<span data-ttu-id="0a551-244">包含與 NODE_DESCRIPTION 資料行資訊相同的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="0a551-244">An XML fragment that contains the same information as the NODE_DESCRIPTION column.</span></span>|  
|<span data-ttu-id="0a551-245">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0a551-245">Hidden layer</span></span>|<span data-ttu-id="0a551-246">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-246">Blank</span></span>|  
|<span data-ttu-id="0a551-247">隱藏節點</span><span class="sxs-lookup"><span data-stu-id="0a551-247">Hidden node</span></span>|<span data-ttu-id="0a551-248">指出隱藏節點清單中，隱藏節點順序的整數。</span><span class="sxs-lookup"><span data-stu-id="0a551-248">Integer that indicates the sequence of the hidden node in the list of hidden nodes.</span></span>|  
|<span data-ttu-id="0a551-249">輸出層</span><span class="sxs-lookup"><span data-stu-id="0a551-249">Output layer</span></span>|<span data-ttu-id="0a551-250">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-250">Blank</span></span>|  
|<span data-ttu-id="0a551-251">輸出節點</span><span class="sxs-lookup"><span data-stu-id="0a551-251">Output node</span></span>|<span data-ttu-id="0a551-252">包含與 NODE_DESCRIPTION 資料行資訊相同的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="0a551-252">An XML fragment that contains the same information as the NODE_DESCRIPTION column.</span></span>|  
  
 <span data-ttu-id="0a551-253">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="0a551-253">MARGINAL_RULE</span></span>  
 <span data-ttu-id="0a551-254">若是類神經網路模型，永遠為空白。</span><span class="sxs-lookup"><span data-stu-id="0a551-254">For neural network models, always blank.</span></span>  
  
 <span data-ttu-id="0a551-255">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="0a551-255">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="0a551-256">與此節點關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="0a551-256">The probability associated with this node.</span></span> <span data-ttu-id="0a551-257">若是類神經網路模型，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="0a551-257">For neural network models, always 0.</span></span>  
  
 <span data-ttu-id="0a551-258">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="0a551-258">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="0a551-259">從父節點到達節點的機率。</span><span class="sxs-lookup"><span data-stu-id="0a551-259">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="0a551-260">若是類神經網路模型，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="0a551-260">For neural network models, always 0.</span></span>  
  
 <span data-ttu-id="0a551-261">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="0a551-261">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="0a551-262">包含節點之統計資訊的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="0a551-262">A nested table that contains statistical information for the node.</span></span> <span data-ttu-id="0a551-263">如需每個節點類型之這個資料表內容的詳細資訊，請參閱 [Understanding the NODE_DISTRIBUTION Table](#bkmk_NodeDistTable)(了解 NODE_DISTRIBUTION 資料表) 一節。</span><span class="sxs-lookup"><span data-stu-id="0a551-263">For detailed information about the contents of this table for each node type, see the section, [Understanding the NODE_DISTRIBUTION Table](#bkmk_NodeDistTable).</span></span>  
  
 <span data-ttu-id="0a551-264">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="0a551-264">NODE_SUPPORT</span></span>  
 <span data-ttu-id="0a551-265">若是類神經網路模型，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="0a551-265">For neural network models, always 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a551-266">支援機率永遠為 0，因為此模型類型的輸出不是機率。</span><span class="sxs-lookup"><span data-stu-id="0a551-266">Support probabilities are always 0 because the output of this model type is not probabilistic.</span></span> <span data-ttu-id="0a551-267">對於演算法唯一有意義的是加權，因此，此演算法不會計算機率、支援或變異數。</span><span class="sxs-lookup"><span data-stu-id="0a551-267">Only the weights are meaningful for the algorithm; therefore, the algorithm does not compute probability, support, or variance.</span></span>  
  
 <span data-ttu-id="0a551-268">若要在特定值的定型案例中取得支援的相關資訊，請查看臨界統計資料節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-268">To get information about the support in the training cases for specific values, see the marginal statistics node.</span></span>  
  
 <span data-ttu-id="0a551-269">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="0a551-269">MSOLAP_MODEL_COLUMN</span></span>  
 |<span data-ttu-id="0a551-270">節點</span><span class="sxs-lookup"><span data-stu-id="0a551-270">Node</span></span>|<span data-ttu-id="0a551-271">內容</span><span class="sxs-lookup"><span data-stu-id="0a551-271">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0a551-272">模型根</span><span class="sxs-lookup"><span data-stu-id="0a551-272">Model root</span></span>|<span data-ttu-id="0a551-273">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-273">Blank</span></span>|  
|<span data-ttu-id="0a551-274">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="0a551-274">Marginal statistics</span></span>|<span data-ttu-id="0a551-275">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-275">Blank</span></span>|  
|<span data-ttu-id="0a551-276">輸入層</span><span class="sxs-lookup"><span data-stu-id="0a551-276">Input layer</span></span>|<span data-ttu-id="0a551-277">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-277">Blank</span></span>|  
|<span data-ttu-id="0a551-278">輸入節點</span><span class="sxs-lookup"><span data-stu-id="0a551-278">Input node</span></span>|<span data-ttu-id="0a551-279">輸入屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-279">Input attribute name.</span></span>|  
|<span data-ttu-id="0a551-280">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0a551-280">Hidden layer</span></span>|<span data-ttu-id="0a551-281">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-281">Blank</span></span>|  
|<span data-ttu-id="0a551-282">隱藏節點</span><span class="sxs-lookup"><span data-stu-id="0a551-282">Hidden node</span></span>|<span data-ttu-id="0a551-283">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-283">Blank</span></span>|  
|<span data-ttu-id="0a551-284">輸出層</span><span class="sxs-lookup"><span data-stu-id="0a551-284">Output layer</span></span>|<span data-ttu-id="0a551-285">空白</span><span class="sxs-lookup"><span data-stu-id="0a551-285">Blank</span></span>|  
|<span data-ttu-id="0a551-286">輸出節點</span><span class="sxs-lookup"><span data-stu-id="0a551-286">Output node</span></span>|<span data-ttu-id="0a551-287">輸入屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="0a551-287">Input attribute name.</span></span>|  
  
 <span data-ttu-id="0a551-288">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="0a551-288">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="0a551-289">若是類神經網路模型，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="0a551-289">For a neural network model, always 0.</span></span>  
  
 <span data-ttu-id="0a551-290">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="0a551-290">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="0a551-291">若是類神經網路模型，永遠為空白。</span><span class="sxs-lookup"><span data-stu-id="0a551-291">For neural network models, always blank.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a551-292">備註</span><span class="sxs-lookup"><span data-stu-id="0a551-292">Remarks</span></span>  
 <span data-ttu-id="0a551-293">定型類神經網路模型的目的在於判斷與每個轉換關聯的加權 (從輸入到中點，以及從中點到端點)。</span><span class="sxs-lookup"><span data-stu-id="0a551-293">The purpose of training a neural network model is to determine the weights that are associated with each transition from an input to a midpoint, and from a midpoint to an endpoint.</span></span> <span data-ttu-id="0a551-294">因此，模型的輸入層主要存在目的為儲存建立模型所使用的實際值。</span><span class="sxs-lookup"><span data-stu-id="0a551-294">Therefore, the input layer of the model principally exists to store the actual values that were used to build the model.</span></span> <span data-ttu-id="0a551-295">隱藏層會儲存經過計算的加權，並提供回到輸入屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="0a551-295">The hidden layer stores the weights that were computed, and provides pointers back to the input attributes.</span></span> <span data-ttu-id="0a551-296">輸出層會儲存可預測的值，同時提供回到隱藏層中端點的指標。</span><span class="sxs-lookup"><span data-stu-id="0a551-296">The output layer stores the predictable values, and also provides pointers back to the midpoints in the hidden layer.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_NodeIDs"></a><span data-ttu-id="0a551-297">使用節點名稱和識別碼</span><span class="sxs-lookup"><span data-stu-id="0a551-297">Using Node Names and IDs</span></span>  
 <span data-ttu-id="0a551-298">類神經網路模型中節點的命名提供有關節點類型的其他資訊，讓隱藏層與輸入層更容易產生關聯，並讓輸出層與隱藏層產生關聯。</span><span class="sxs-lookup"><span data-stu-id="0a551-298">The naming of the nodes in a neural network model provides additional information about the type of node, to make it easier to relate the hidden layer to the input layer, and the output layer to the hidden layer.</span></span> <span data-ttu-id="0a551-299">下表顯示指派給每層節點之識別碼的慣例。</span><span class="sxs-lookup"><span data-stu-id="0a551-299">The following table shows the convention for the IDs that are assigned to nodes in each layer.</span></span>  
  
|<span data-ttu-id="0a551-300">節點類型</span><span class="sxs-lookup"><span data-stu-id="0a551-300">Node Type</span></span>|<span data-ttu-id="0a551-301">節點識別碼的慣例</span><span class="sxs-lookup"><span data-stu-id="0a551-301">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="0a551-302">模型根 (1)</span><span class="sxs-lookup"><span data-stu-id="0a551-302">Model root (1)</span></span>|<span data-ttu-id="0a551-303">00000000000000000.</span><span class="sxs-lookup"><span data-stu-id="0a551-303">00000000000000000.</span></span>|  
|<span data-ttu-id="0a551-304">臨界統計資料節點 (24)</span><span class="sxs-lookup"><span data-stu-id="0a551-304">Marginal statistics node (24)</span></span>|<span data-ttu-id="0a551-305">10000000000000000</span><span class="sxs-lookup"><span data-stu-id="0a551-305">10000000000000000</span></span>|  
|<span data-ttu-id="0a551-306">輸入層 (18)</span><span class="sxs-lookup"><span data-stu-id="0a551-306">Input layer (18)</span></span>|<span data-ttu-id="0a551-307">30000000000000000</span><span class="sxs-lookup"><span data-stu-id="0a551-307">30000000000000000</span></span>|  
|<span data-ttu-id="0a551-308">輸入節點 (21)</span><span class="sxs-lookup"><span data-stu-id="0a551-308">Input node (21)</span></span>|<span data-ttu-id="0a551-309">從 60000000000000000 開始</span><span class="sxs-lookup"><span data-stu-id="0a551-309">Starts at 60000000000000000</span></span>|  
|<span data-ttu-id="0a551-310">子網路 (17)</span><span class="sxs-lookup"><span data-stu-id="0a551-310">Subnetwork (17)</span></span>|<span data-ttu-id="0a551-311">20000000000000000</span><span class="sxs-lookup"><span data-stu-id="0a551-311">20000000000000000</span></span>|  
|<span data-ttu-id="0a551-312">隱藏層 (19)</span><span class="sxs-lookup"><span data-stu-id="0a551-312">Hidden layer (19)</span></span>|<span data-ttu-id="0a551-313">40000000000000000</span><span class="sxs-lookup"><span data-stu-id="0a551-313">40000000000000000</span></span>|  
|<span data-ttu-id="0a551-314">隱藏節點 (22)</span><span class="sxs-lookup"><span data-stu-id="0a551-314">Hidden node (22)</span></span>|<span data-ttu-id="0a551-315">從 70000000000000000 開始</span><span class="sxs-lookup"><span data-stu-id="0a551-315">Starts at 70000000000000000</span></span>|  
|<span data-ttu-id="0a551-316">輸出層 (20)</span><span class="sxs-lookup"><span data-stu-id="0a551-316">Output layer (20)</span></span>|<span data-ttu-id="0a551-317">50000000000000000</span><span class="sxs-lookup"><span data-stu-id="0a551-317">50000000000000000</span></span>|  
|<span data-ttu-id="0a551-318">輸出節點 (23)</span><span class="sxs-lookup"><span data-stu-id="0a551-318">Output node (23)</span></span>|<span data-ttu-id="0a551-319">從 80000000000000000 開始</span><span class="sxs-lookup"><span data-stu-id="0a551-319">Starts at 80000000000000000</span></span>|  
  
 <span data-ttu-id="0a551-320">您可以檢視隱藏節點 (NODE_TYPE = 22) 中的 NODE_DISTRIBUTION 資料表，來判斷與特定隱藏層節點關聯的輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="0a551-320">You can determine which input attributes are related to a specific hidden layer node by viewing the NODE_DISTRIBUTION table in the hidden node (NODE_TYPE = 22).</span></span> <span data-ttu-id="0a551-321">NODE_DISTRIBUTION 資料表的每個資料列都包含輸入屬性節點的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0a551-321">Each row of the NODE_DISTRIBUTION table contains the ID of an input attribute node.</span></span>  
  
 <span data-ttu-id="0a551-322">同樣地，您可以檢視輸出節點 (NODE_TYPE = 23) 中的 NODE_DISTRIBUTION 資料表，來判斷與輸出屬性關聯的隱藏層。</span><span class="sxs-lookup"><span data-stu-id="0a551-322">Similarly, you can determine which hidden layers are related to an output attribute by viewing the NODE_DISTRIBUTION table in the output node (NODE_TYPE = 23).</span></span> <span data-ttu-id="0a551-323">NODE_DISTRIBUTION 資料表的每個資料列都包含隱藏層的識別碼以及相關的係數。</span><span class="sxs-lookup"><span data-stu-id="0a551-323">Each row of the NODE_DISTRIBUTION table contains the ID of a hidden layer node, together with the related coefficient.</span></span>  
  
##  <a name="interpreting-the-information-in-the-node_distribution-table"></a><a name="bkmk_NodeDistTable"></a> <span data-ttu-id="0a551-324">解譯 NODE_DISTRIBUTION 資料表中的資訊</span><span class="sxs-lookup"><span data-stu-id="0a551-324">Interpreting the Information in the NODE_DISTRIBUTION Table</span></span>  
 <span data-ttu-id="0a551-325">NODE_DISTRIBUTION 資料表在某些節點中可以是空的。</span><span class="sxs-lookup"><span data-stu-id="0a551-325">The NODE_DISTRIBUTION table can be empty in some nodes.</span></span> <span data-ttu-id="0a551-326">不過，對於輸入節點、隱藏層節點，以及輸出節點，NODE_DISTRIBUTION 資料表會儲存關於模型的重要與感興趣的資訊。</span><span class="sxs-lookup"><span data-stu-id="0a551-326">However, for input nodes, hidden layer nodes, and output nodes, the NODE_DISTRIBUTION table stores important and interesting information about the model.</span></span> <span data-ttu-id="0a551-327">為協助您解譯這項資訊，NODE_DISTRIBUTION 資料表包含每個資料列的 VALUETYPE 資料行，這些資料列會告訴您 ATTRIBUTE_VALUE 資料行中的值是 [離散 (4)]、[離散化 (5)]，還是 [連續 (3)] 的。</span><span class="sxs-lookup"><span data-stu-id="0a551-327">To help you interpret this information, the NODE_DISTRIBUTION table contains a VALUETYPE column for each row that tells you whether the value in the ATTRIBUTE_VALUE column is Discrete (4), Discretized (5), or Continuous (3).</span></span>  
  
### <a name="input-nodes"></a><span data-ttu-id="0a551-328">輸入節點</span><span class="sxs-lookup"><span data-stu-id="0a551-328">Input Nodes</span></span>  
 <span data-ttu-id="0a551-329">輸入層包含模型中所使用之屬性每個值的節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-329">The input layer contains a node for each value of the attribute that was used in the model.</span></span>  
  
 <span data-ttu-id="0a551-330">**離散屬性** ：此輸入節點僅會將屬性的名稱及其值儲存在 ATTRIBUTE_NAME 和 ATTRIBUTE_VALUE 資料行中。</span><span class="sxs-lookup"><span data-stu-id="0a551-330">**Discrete attribute:** The input node stores only the name of the attribute and its value in the ATTRIBUTE_NAME and ATTRIBUTE_VALUE columns.</span></span> <span data-ttu-id="0a551-331">例如，如果 [Work Shift] 為資料行，系統就會針對模型中使用之資料行的每個值建立個別的節點，例如，AM 和 PM。</span><span class="sxs-lookup"><span data-stu-id="0a551-331">For example, if [Work Shift] is the column, a separate node is created for each value of that column that was used in the model, such as AM and PM.</span></span> <span data-ttu-id="0a551-332">每個節點的 NODE_DISTRIBUTION 資料表僅會列出屬性目前的值。</span><span class="sxs-lookup"><span data-stu-id="0a551-332">The NODE_DISTRIBUTION table for each node lists only the current value of the attribute.</span></span>  
  
 <span data-ttu-id="0a551-333">**離散化數值屬性** ：此輸入節點會儲存屬性的名稱及值，這可能是一個範圍或一個特定的值。</span><span class="sxs-lookup"><span data-stu-id="0a551-333">**Discretized numeric attribute:** The input node stores the name of the attribute, and the value, which can be a range or a specific value.</span></span> <span data-ttu-id="0a551-334">所有值都會以運算式表示，例如，'77.4 - 87.4' 或 ' < 64.0' 用於 [Time Per Issue] 的值。</span><span class="sxs-lookup"><span data-stu-id="0a551-334">All values are represented by expressions, such as '77.4 - 87.4' or ' < 64.0' for the value of the [Time Per Issue].</span></span> <span data-ttu-id="0a551-335">每個節點的 NODE_DISTRIBUTION 資料表僅會列出屬性目前的值。</span><span class="sxs-lookup"><span data-stu-id="0a551-335">The NODE_DISTRIBUTION table for each node lists only the current value of the attribute.</span></span>  
  
 <span data-ttu-id="0a551-336">**連續屬性** ：輸入節點會儲存屬性的平均值。</span><span class="sxs-lookup"><span data-stu-id="0a551-336">**Continuous attribute:** The input node stores the mean value of the attribute.</span></span> <span data-ttu-id="0a551-337">每個節點的 NODE_DISTRIBUTION 資料表僅會列出屬性目前的值。</span><span class="sxs-lookup"><span data-stu-id="0a551-337">The NODE_DISTRIBUTION table for each node lists only the current value of the attribute.</span></span>  
  
### <a name="hidden-layer-nodes"></a><span data-ttu-id="0a551-338">隱藏層節點</span><span class="sxs-lookup"><span data-stu-id="0a551-338">Hidden Layer Nodes</span></span>  
 <span data-ttu-id="0a551-339">隱藏層包含節點的變數數目。</span><span class="sxs-lookup"><span data-stu-id="0a551-339">The hidden layer contains a variable number of nodes.</span></span> <span data-ttu-id="0a551-340">在每個節點中，NODE_DISTRIBUTION 資料表在輸入層中都包含隱藏層到節點的對應。</span><span class="sxs-lookup"><span data-stu-id="0a551-340">In each node, the NODE_DISTRIBUTION table contains mappings from the hidden layer to the nodes in the input layer.</span></span> <span data-ttu-id="0a551-341">ATTRIBUTE_NAME 資料行包含對應到輸入層中之節點的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="0a551-341">The ATTRIBUTE_NAME column contains a node ID that corresponds to a node in the input layer.</span></span> <span data-ttu-id="0a551-342">ATTRIBUTE_VALUE 資料行包含與輸入節點和隱藏層節點組合關聯的加權。</span><span class="sxs-lookup"><span data-stu-id="0a551-342">The ATTRIBUTE_VALUE column contains the weight associated with that combination of input node and hidden layer node.</span></span> <span data-ttu-id="0a551-343">資料表中的最後一個資料列包含代表隱藏層中該隱藏節點之加權的係數。</span><span class="sxs-lookup"><span data-stu-id="0a551-343">The last row in the table contains a coefficient that represents the weight of that hidden node in the hidden layer.</span></span>  
  
### <a name="output-nodes"></a><span data-ttu-id="0a551-344">輸出節點</span><span class="sxs-lookup"><span data-stu-id="0a551-344">Output Nodes</span></span>  
 <span data-ttu-id="0a551-345">輸出層包含模型中所使用之每個輸出值的一個輸出節點。</span><span class="sxs-lookup"><span data-stu-id="0a551-345">The output layer contains one output node for each output value that was used in the model.</span></span> <span data-ttu-id="0a551-346">在每個節點中，NODE_DISTRIBUTION 資料表在隱藏層中都包含輸出層到節點的對應。</span><span class="sxs-lookup"><span data-stu-id="0a551-346">In each node, the NODE_DISTRIBUTION table contains mappings from the output layer to the nodes in the hidden layer.</span></span> <span data-ttu-id="0a551-347">ATTRIBUTE_NAME 資料行包含對應到隱藏層中之節點的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="0a551-347">The ATTRIBUTE_NAME column contains a node ID that corresponds to a node in the hidden layer.</span></span> <span data-ttu-id="0a551-348">ATTRIBUTE_VALUE 資料行包含與輸出節點和隱藏層節點組合關聯的加權。</span><span class="sxs-lookup"><span data-stu-id="0a551-348">The ATTRIBUTE_VALUE column contains the weight associated with that combination of output node and hidden layer node.</span></span>  
  
 <span data-ttu-id="0a551-349">NODE_DISTRIBUTION 資料表包含的下列額外資訊取決於屬性的類型為：</span><span class="sxs-lookup"><span data-stu-id="0a551-349">The NODE_DISTRIBUTION table has the following additional information, depending on whether the type of the attribute:</span></span>  
  
 <span data-ttu-id="0a551-350">**離散屬性** ：NODE_DISTRIBUTION 資料表的最後兩個資料列包含整個節點的係數，以及屬性目前的值。</span><span class="sxs-lookup"><span data-stu-id="0a551-350">**Discrete attribute:** The final two rows of the NODE_DISTRIBUTION table contain a coefficient for the node as a whole, and the current value of the attribute.</span></span>  
  
 <span data-ttu-id="0a551-351">**離散化數值屬性** ：除了屬性的值為一個範圍的值之外，與離散屬性相同。</span><span class="sxs-lookup"><span data-stu-id="0a551-351">**Discretized numeric attribute:** Identical to discrete attributes, except that the value of the attribute is a range of values.</span></span>  
  
 <span data-ttu-id="0a551-352">**連續屬性** ：NODE_DISTRIBUTION 資料表的最後兩個資料列包含屬性的平均值、整個節點的係數，以及係數的變異數。</span><span class="sxs-lookup"><span data-stu-id="0a551-352">**Continuous attribute:** The final two rows of the NODE_DISTRIBUTION table contain the mean of the attribute, the coefficient for the node as a whole, and the variance of the coefficient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a551-353">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a551-353">See Also</span></span>  
 <span data-ttu-id="0a551-354">[Microsoft 類神經網路演算法](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="0a551-354">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="0a551-355">[Microsoft 類神經網路演算法技術參考](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0a551-355">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="0a551-356">類神經網路模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="0a551-356">Neural Network Model Query Examples</span></span>](neural-network-model-query-examples.md)  
  
  
