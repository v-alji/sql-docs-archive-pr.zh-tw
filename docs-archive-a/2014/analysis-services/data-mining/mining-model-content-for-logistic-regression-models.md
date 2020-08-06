---
title: 羅吉斯回歸模型的採礦模型內容 (Analysis Services 資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- mining model content, logistic regression models
- regression algorithms [Analysis Services]
ms.assetid: 69cc0b86-e8bc-4d6c-903e-85724f5c0396
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84964c59a63d41f0985001a2ae384fa298096927
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598671"
---
# <a name="mining-model-content-for-logistic-regression-models-analysis-services---data-mining"></a><span data-ttu-id="dd244-102">羅吉斯迴歸模型的採礦模型內容 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="dd244-102">Mining Model Content for Logistic Regression Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="dd244-103">本主題描述使用 Microsoft 羅吉斯迴歸演算法的模型專用的採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="dd244-103">This topic describes mining model content that is specific to models that use the Microsoft Logistic Regression algorithm.</span></span> <span data-ttu-id="dd244-104">如需如何解譯所有模型類型共用的統計資料與結構的說明，以及與採礦模型內容相關的一般詞彙說明，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="dd244-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-logistic-regression-model"></a><span data-ttu-id="dd244-105">了解羅吉斯迴歸模型的結構</span><span class="sxs-lookup"><span data-stu-id="dd244-105">Understanding the Structure of a Logistic Regression Model</span></span>  
 <span data-ttu-id="dd244-106">羅吉斯迴歸模型是使用 Microsoft 類神經網路演算法建立的，其參數會強迫模型刪除隱藏的節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-106">A logistic regression model is created by using the Microsoft Neural Network algorithm with parameters that constrain the model to eliminate the hidden node.</span></span> <span data-ttu-id="dd244-107">因此，羅吉斯迴歸模型的完整結構幾乎與類神經網路的結構相同：每個模型都有代表模型及其中繼資料的單一父節點，以及一個特殊的臨界統計資料節點 (NODE_TYPE = 24)，提供模型中所使用之輸入的名數性統計資料。</span><span class="sxs-lookup"><span data-stu-id="dd244-107">Therefore, the overall structure of a logistic regression model is almost identical to that of a neural network: each model has a single parent node that represents the model and its metadata, and a special marginal statistics node (NODE_TYPE = 24) that provides descriptive statistics about the inputs used in the model.</span></span>  
  
 <span data-ttu-id="dd244-108">此外，每個可預測屬性的模型都包含一個子網路 (NODE_TYPE = 17)。</span><span class="sxs-lookup"><span data-stu-id="dd244-108">Additionally, the model contains a subnetwork (NODE_TYPE = 17) for each predictable attribute.</span></span> <span data-ttu-id="dd244-109">如同在類神經網路模型中，每個子網路永遠都包含兩個分支：其中一個用於輸入層，而另一個包含隱藏層 (NODE_TYPE = 19) 和輸出層 (NODE_TYPE = 20) 的分支則用於網路。</span><span class="sxs-lookup"><span data-stu-id="dd244-109">Just like in a neural network model, each subnetwork always contains two branches: one for the input layer, and another branch that contains the hidden layer (NODE_TYPE = 19) and the output layer (NODE_TYPE = 20) for the network.</span></span> <span data-ttu-id="dd244-110">如果屬性指定為僅預測，相同的子網路則可用於多個屬性。</span><span class="sxs-lookup"><span data-stu-id="dd244-110">The same subnetwork may be used for multiple attributes if they are specified as predict-only.</span></span> <span data-ttu-id="dd244-111">同時為輸入的可預測屬性可能不會出現在相同的子網路中。</span><span class="sxs-lookup"><span data-stu-id="dd244-111">Predictable attributes that are also inputs may not appear in the same subnetwork.</span></span>  
  
 <span data-ttu-id="dd244-112">不過，在羅吉斯迴歸模型中，代表隱藏層的節點是空的，而且沒有子系。</span><span class="sxs-lookup"><span data-stu-id="dd244-112">However, in a logistic regression model, the node that represents the hidden layer is empty, and has no children.</span></span> <span data-ttu-id="dd244-113">因此，此模型包含代表個別輸出 (NODE_TYPE = 23) 與個別輸入 (NODE_TYPE = 21) 的節點，但是不包含個別的隱藏節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-113">Therefore the model contains nodes that represent individual outputs (NODE_TYPE = 23) and individual inputs (NODE_TYPE = 21) but no individual hidden nodes.</span></span>  
  
 <span data-ttu-id="dd244-114">![羅吉斯迴歸模型的模型內容結構](../media/skt-modelcontentstructure-logregc.gif "羅吉斯迴歸模型的模型內容結構")</span><span class="sxs-lookup"><span data-stu-id="dd244-114">![structure of content for logisitc regression model](../media/skt-modelcontentstructure-logregc.gif "structure of content for logisitc regression model")</span></span>  
  
 <span data-ttu-id="dd244-115">根據預設，羅吉斯迴歸模型顯示在 **[Microsoft 類神經網路檢視器]** 中。</span><span class="sxs-lookup"><span data-stu-id="dd244-115">By default, a logistic regression model is displayed in the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="dd244-116">您可以利用這個自訂的檢視器，篩選輸入屬性及其值，並以圖形方式查看這些屬性和值如何影響輸出。</span><span class="sxs-lookup"><span data-stu-id="dd244-116">With this custom viewer, you can filter on input attributes and their values, and graphically see how they affect the outputs.</span></span> <span data-ttu-id="dd244-117">檢視器中的工具提示會顯示與每個成對輸入和輸出值相關聯的機率與增益。</span><span class="sxs-lookup"><span data-stu-id="dd244-117">The tooltips in the viewer show you the probability and lift associated with each pair of inputs and output values.</span></span> <span data-ttu-id="dd244-118">如需詳細資訊，請參閱 [使用 Microsoft 類神經網路檢視器瀏覽模型](browse-a-model-using-the-microsoft-neural-network-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="dd244-118">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="dd244-119">若要探討輸入和子網路的結構以及查看詳細的統計資料，您可以使用 Microsoft 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="dd244-119">To explore the structure of the inputs and subnetworks, and to see detailed statistics, you can use the Microsoft Generic Content Tree viewer.</span></span> <span data-ttu-id="dd244-120">您可以按一下任何節點將其展開並查看其子節點，或檢視包含在節點中的加權和其他統計資料。</span><span class="sxs-lookup"><span data-stu-id="dd244-120">You can click on any node to expand it and see the child nodes, or view the weights and other statistics contained in the node.</span></span>  
  
## <a name="model-content-for-a-logistic-regression-model"></a><span data-ttu-id="dd244-121">羅吉斯迴歸模型的模型內容</span><span class="sxs-lookup"><span data-stu-id="dd244-121">Model Content for a Logistic Regression Model</span></span>  
 <span data-ttu-id="dd244-122">本節僅針對採礦模型內容中與羅吉斯迴歸具有特定相關的資料行，提供詳細資料和範例。</span><span class="sxs-lookup"><span data-stu-id="dd244-122">This section provides detail and examples only for those columns in the mining model content that have particular relevance for logistic regression.</span></span> <span data-ttu-id="dd244-123">此模型內容與類神經網路模型的內容幾乎相同，但是為了方便，適用於類神經網路模型的描述在此資料表中可能會重複。</span><span class="sxs-lookup"><span data-stu-id="dd244-123">The model content is almost identical to that of a neural network model, but descriptions that apply to neural network models may be repeated in this table for convenience.</span></span>  
  
 <span data-ttu-id="dd244-124">如需結構描述資料列集 (例如 MODEL_CATALOG 和 MODEL_NAME) 中一般用途資料行的詳細資訊 (此處沒有說明)，或採礦模型術語的說明，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="dd244-124">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="dd244-125">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dd244-125">MODEL_CATALOG</span></span>  
 <span data-ttu-id="dd244-126">模型儲存位置所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-126">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="dd244-127">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="dd244-127">MODEL_NAME</span></span>  
 <span data-ttu-id="dd244-128">模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-128">Name of the model.</span></span>  
  
 <span data-ttu-id="dd244-129">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd244-129">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="dd244-130">對應至這個節點之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-130">The names of the attribute that corresponds to this node.</span></span>  
  
|<span data-ttu-id="dd244-131">節點</span><span class="sxs-lookup"><span data-stu-id="dd244-131">Node</span></span>|<span data-ttu-id="dd244-132">內容</span><span class="sxs-lookup"><span data-stu-id="dd244-132">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="dd244-133">模型根</span><span class="sxs-lookup"><span data-stu-id="dd244-133">Model root</span></span>|<span data-ttu-id="dd244-134">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-134">Blank</span></span>|  
|<span data-ttu-id="dd244-135">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="dd244-135">Marginal statistics</span></span>|<span data-ttu-id="dd244-136">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-136">Blank</span></span>|  
|<span data-ttu-id="dd244-137">輸入層</span><span class="sxs-lookup"><span data-stu-id="dd244-137">Input layer</span></span>|<span data-ttu-id="dd244-138">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-138">Blank</span></span>|  
|<span data-ttu-id="dd244-139">輸入節點</span><span class="sxs-lookup"><span data-stu-id="dd244-139">Input node</span></span>|<span data-ttu-id="dd244-140">輸入屬性名稱</span><span class="sxs-lookup"><span data-stu-id="dd244-140">Input attribute name</span></span>|  
|<span data-ttu-id="dd244-141">hidden layer</span><span class="sxs-lookup"><span data-stu-id="dd244-141">Hidden layer</span></span>|<span data-ttu-id="dd244-142">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-142">Blank</span></span>|  
|<span data-ttu-id="dd244-143">輸出層</span><span class="sxs-lookup"><span data-stu-id="dd244-143">Output layer</span></span>|<span data-ttu-id="dd244-144">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-144">Blank</span></span>|  
|<span data-ttu-id="dd244-145">輸出節點</span><span class="sxs-lookup"><span data-stu-id="dd244-145">Output node</span></span>|<span data-ttu-id="dd244-146">輸出屬性名稱</span><span class="sxs-lookup"><span data-stu-id="dd244-146">Output attribute name</span></span>|  
  
 <span data-ttu-id="dd244-147">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd244-147">NODE_NAME</span></span>  
 <span data-ttu-id="dd244-148">節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-148">The name of the node.</span></span> <span data-ttu-id="dd244-149">目前，此資料行與 NODE_UNIQUE_NAME 包含相同的值，但是未來的版本可能會變更。</span><span class="sxs-lookup"><span data-stu-id="dd244-149">Currently, this column contains the same value as NODE_UNIQUE_NAME, though this may change in future releases.</span></span>  
  
 <span data-ttu-id="dd244-150">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd244-150">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="dd244-151">節點的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-151">The unique name of the node.</span></span>  
  
 <span data-ttu-id="dd244-152">如需有關名稱與識別碼如何提供模型之結構資訊的詳細資訊，請參閱＜ [使用節點名稱與識別碼](#bkmk_NodeIDs)＞一節。</span><span class="sxs-lookup"><span data-stu-id="dd244-152">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="dd244-153">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd244-153">NODE_TYPE</span></span>  
 <span data-ttu-id="dd244-154">羅吉斯迴歸模型會輸出下列節點類型：</span><span class="sxs-lookup"><span data-stu-id="dd244-154">A logistic regression model outputs the following node types:</span></span>  
  
|<span data-ttu-id="dd244-155">節點類型識別碼</span><span class="sxs-lookup"><span data-stu-id="dd244-155">Node Type ID</span></span>|<span data-ttu-id="dd244-156">描述</span><span class="sxs-lookup"><span data-stu-id="dd244-156">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="dd244-157">1</span><span class="sxs-lookup"><span data-stu-id="dd244-157">1</span></span>|<span data-ttu-id="dd244-158">模型。</span><span class="sxs-lookup"><span data-stu-id="dd244-158">Model.</span></span>|  
|<span data-ttu-id="dd244-159">17</span><span class="sxs-lookup"><span data-stu-id="dd244-159">17</span></span>|<span data-ttu-id="dd244-160">子網路的組合管理節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-160">Organizer node for the subnetwork.</span></span>|  
|<span data-ttu-id="dd244-161">18</span><span class="sxs-lookup"><span data-stu-id="dd244-161">18</span></span>|<span data-ttu-id="dd244-162">輸入層的組合管理節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-162">Organizer node for the input layer.</span></span>|  
|<span data-ttu-id="dd244-163">19</span><span class="sxs-lookup"><span data-stu-id="dd244-163">19</span></span>|<span data-ttu-id="dd244-164">隱藏層的組合管理節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-164">Organizer node for the hidden layer.</span></span> <span data-ttu-id="dd244-165">隱藏層是空的。</span><span class="sxs-lookup"><span data-stu-id="dd244-165">The hidden layer is empty.</span></span>|  
|<span data-ttu-id="dd244-166">20</span><span class="sxs-lookup"><span data-stu-id="dd244-166">20</span></span>|<span data-ttu-id="dd244-167">輸出層的組合管理節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-167">Organizer node for the output layer.</span></span>|  
|<span data-ttu-id="dd244-168">21</span><span class="sxs-lookup"><span data-stu-id="dd244-168">21</span></span>|<span data-ttu-id="dd244-169">輸入屬性節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-169">Input attribute node.</span></span>|  
|<span data-ttu-id="dd244-170">23</span><span class="sxs-lookup"><span data-stu-id="dd244-170">23</span></span>|<span data-ttu-id="dd244-171">輸出屬性節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-171">Output attribute node.</span></span>|  
|<span data-ttu-id="dd244-172">24</span><span class="sxs-lookup"><span data-stu-id="dd244-172">24</span></span>|<span data-ttu-id="dd244-173">臨界統計資料節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-173">Marginal statistics node.</span></span>|  
  
 <span data-ttu-id="dd244-174">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="dd244-174">NODE_CAPTION</span></span>  
 <span data-ttu-id="dd244-175">與節點關聯的標籤或標題。</span><span class="sxs-lookup"><span data-stu-id="dd244-175">A label or a caption associated with the node.</span></span> <span data-ttu-id="dd244-176">在羅吉斯迴歸模型中，永遠為空白。</span><span class="sxs-lookup"><span data-stu-id="dd244-176">In logistic regression models, always blank.</span></span>  
  
 <span data-ttu-id="dd244-177">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="dd244-177">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="dd244-178">節點所擁有子系數目的估計。</span><span class="sxs-lookup"><span data-stu-id="dd244-178">An estimate of the number of children that the node has.</span></span>  
  
|<span data-ttu-id="dd244-179">節點</span><span class="sxs-lookup"><span data-stu-id="dd244-179">Node</span></span>|<span data-ttu-id="dd244-180">內容</span><span class="sxs-lookup"><span data-stu-id="dd244-180">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="dd244-181">模型根</span><span class="sxs-lookup"><span data-stu-id="dd244-181">Model root</span></span>|<span data-ttu-id="dd244-182">指出子節點的計數，其中至少包含 1 個網路、1 個必要的臨界節點，以及 1 個必要的輸入層。</span><span class="sxs-lookup"><span data-stu-id="dd244-182">Indicates the count of child nodes, which includes at least 1 network, 1 required marginal node, and 1 required input layer.</span></span> <span data-ttu-id="dd244-183">例如，如果值為 5，則有 3 個子網路。</span><span class="sxs-lookup"><span data-stu-id="dd244-183">For example, if the value is 5, there are 3 subnetworks.</span></span>|  
|<span data-ttu-id="dd244-184">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="dd244-184">Marginal statistics</span></span>|<span data-ttu-id="dd244-185">一律是 0。</span><span class="sxs-lookup"><span data-stu-id="dd244-185">Always 0.</span></span>|  
|<span data-ttu-id="dd244-186">輸入層</span><span class="sxs-lookup"><span data-stu-id="dd244-186">Input layer</span></span>|<span data-ttu-id="dd244-187">指出模型使用之輸入屬性和值配對的數目。</span><span class="sxs-lookup"><span data-stu-id="dd244-187">Indicates the number of input attribute-values pairs that were used by the model.</span></span>|  
|<span data-ttu-id="dd244-188">輸入節點</span><span class="sxs-lookup"><span data-stu-id="dd244-188">Input node</span></span>|<span data-ttu-id="dd244-189">一律是 0。</span><span class="sxs-lookup"><span data-stu-id="dd244-189">Always 0.</span></span>|  
|<span data-ttu-id="dd244-190">hidden layer</span><span class="sxs-lookup"><span data-stu-id="dd244-190">Hidden layer</span></span>|<span data-ttu-id="dd244-191">在羅吉斯迴歸模型中，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="dd244-191">In a logistic regression model, always 0.</span></span>|  
|<span data-ttu-id="dd244-192">輸出層</span><span class="sxs-lookup"><span data-stu-id="dd244-192">Output layer</span></span>|<span data-ttu-id="dd244-193">指出輸出值的數目。</span><span class="sxs-lookup"><span data-stu-id="dd244-193">Indicates the number of output values.</span></span>|  
|<span data-ttu-id="dd244-194">輸出節點</span><span class="sxs-lookup"><span data-stu-id="dd244-194">Output node</span></span>|<span data-ttu-id="dd244-195">一律是 0。</span><span class="sxs-lookup"><span data-stu-id="dd244-195">Always 0.</span></span>|  
  
 <span data-ttu-id="dd244-196">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd244-196">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="dd244-197">節點之父系的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-197">The unique name of the node's parent.</span></span> <span data-ttu-id="dd244-198">任何根層級的節點都會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="dd244-198">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="dd244-199">如需有關名稱與識別碼如何提供模型之結構資訊的詳細資訊，請參閱＜ [使用節點名稱與識別碼](#bkmk_NodeIDs)＞一節。</span><span class="sxs-lookup"><span data-stu-id="dd244-199">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="dd244-200">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dd244-200">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="dd244-201">使用者易記的節點描述。</span><span class="sxs-lookup"><span data-stu-id="dd244-201">A user-friendly description of the node.</span></span>  
  
|<span data-ttu-id="dd244-202">節點</span><span class="sxs-lookup"><span data-stu-id="dd244-202">Node</span></span>|<span data-ttu-id="dd244-203">內容</span><span class="sxs-lookup"><span data-stu-id="dd244-203">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="dd244-204">模型根</span><span class="sxs-lookup"><span data-stu-id="dd244-204">Model root</span></span>|<span data-ttu-id="dd244-205">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-205">Blank</span></span>|  
|<span data-ttu-id="dd244-206">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="dd244-206">Marginal statistics</span></span>|<span data-ttu-id="dd244-207">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-207">Blank</span></span>|  
|<span data-ttu-id="dd244-208">輸入層</span><span class="sxs-lookup"><span data-stu-id="dd244-208">Input layer</span></span>|<span data-ttu-id="dd244-209">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-209">Blank</span></span>|  
|<span data-ttu-id="dd244-210">輸入節點</span><span class="sxs-lookup"><span data-stu-id="dd244-210">Input node</span></span>|<span data-ttu-id="dd244-211">輸入屬性名稱</span><span class="sxs-lookup"><span data-stu-id="dd244-211">Input attribute name</span></span>|  
|<span data-ttu-id="dd244-212">hidden layer</span><span class="sxs-lookup"><span data-stu-id="dd244-212">Hidden layer</span></span>|<span data-ttu-id="dd244-213">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-213">Blank</span></span>|  
|<span data-ttu-id="dd244-214">輸出層</span><span class="sxs-lookup"><span data-stu-id="dd244-214">Output layer</span></span>|<span data-ttu-id="dd244-215">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-215">Blank</span></span>|  
|<span data-ttu-id="dd244-216">輸出節點</span><span class="sxs-lookup"><span data-stu-id="dd244-216">Output node</span></span>|<span data-ttu-id="dd244-217">如果輸出屬性是連續的，則包含輸出屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-217">If the output attribute is continuous, contains the name of the output attribute.</span></span><br /><br /> <span data-ttu-id="dd244-218">如果輸出屬性是離散或離散化的，則包含輸出屬性的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="dd244-218">If the output attribute is discrete or discretized, contains the name of the attribute and the value.</span></span>|  
  
 <span data-ttu-id="dd244-219">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="dd244-219">NODE_RULE</span></span>  
 <span data-ttu-id="dd244-220">節點中內嵌之規則的 XML 描述。</span><span class="sxs-lookup"><span data-stu-id="dd244-220">An XML description of the rule that is embedded in the node.</span></span>  
  
|<span data-ttu-id="dd244-221">節點</span><span class="sxs-lookup"><span data-stu-id="dd244-221">Node</span></span>|<span data-ttu-id="dd244-222">內容</span><span class="sxs-lookup"><span data-stu-id="dd244-222">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="dd244-223">模型根</span><span class="sxs-lookup"><span data-stu-id="dd244-223">Model root</span></span>|<span data-ttu-id="dd244-224">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-224">Blank</span></span>|  
|<span data-ttu-id="dd244-225">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="dd244-225">Marginal statistics</span></span>|<span data-ttu-id="dd244-226">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-226">Blank</span></span>|  
|<span data-ttu-id="dd244-227">輸入層</span><span class="sxs-lookup"><span data-stu-id="dd244-227">Input layer</span></span>|<span data-ttu-id="dd244-228">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-228">Blank</span></span>|  
|<span data-ttu-id="dd244-229">輸入節點</span><span class="sxs-lookup"><span data-stu-id="dd244-229">Input node</span></span>|<span data-ttu-id="dd244-230">包含與 NODE_DESCRIPTION 資料行資訊相同的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="dd244-230">An XML fragment containing the same information as the NODE_DESCRIPTION column.</span></span>|  
|<span data-ttu-id="dd244-231">hidden layer</span><span class="sxs-lookup"><span data-stu-id="dd244-231">Hidden layer</span></span>|<span data-ttu-id="dd244-232">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-232">Blank</span></span>|  
|<span data-ttu-id="dd244-233">輸出層</span><span class="sxs-lookup"><span data-stu-id="dd244-233">Output layer</span></span>|<span data-ttu-id="dd244-234">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-234">Blank</span></span>|  
|<span data-ttu-id="dd244-235">輸出節點</span><span class="sxs-lookup"><span data-stu-id="dd244-235">Output node</span></span>|<span data-ttu-id="dd244-236">包含與 NODE_DESCRIPTION 資料行資訊相同的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="dd244-236">An XML fragment containing the same information as the NODE_DESCRIPTION column.</span></span>|  
  
 <span data-ttu-id="dd244-237">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="dd244-237">MARGINAL_RULE</span></span>  
 <span data-ttu-id="dd244-238">若是羅吉斯迴歸模型，永遠為空白。</span><span class="sxs-lookup"><span data-stu-id="dd244-238">For logistic regression models, always blank.</span></span>  
  
 <span data-ttu-id="dd244-239">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="dd244-239">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="dd244-240">與此節點關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="dd244-240">The probability associated with this node.</span></span> <span data-ttu-id="dd244-241">若是羅吉斯迴歸模型，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="dd244-241">For logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="dd244-242">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="dd244-242">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="dd244-243">從父節點到達節點的機率。</span><span class="sxs-lookup"><span data-stu-id="dd244-243">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="dd244-244">若是羅吉斯迴歸模型，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="dd244-244">For logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="dd244-245">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="dd244-245">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="dd244-246">包含節點之統計資訊的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="dd244-246">A nested table that contains statistical information for the node.</span></span> <span data-ttu-id="dd244-247">如需每個節點類型之這個資料表內容的詳細資訊，請參閱 [類神經網路模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="dd244-247">For detailed information about the contents of this table for each node type, see the section, Understanding the NODE_DISTRIBUTION Table, in [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="dd244-248">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="dd244-248">NODE_SUPPORT</span></span>  
 <span data-ttu-id="dd244-249">若是羅吉斯迴歸模型，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="dd244-249">For logistic regression models, always 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd244-250">支援機率永遠為 0，因為此模型類型的輸出不是機率。</span><span class="sxs-lookup"><span data-stu-id="dd244-250">Support probabilities are always 0 because the output of this model type is not probabilistic.</span></span> <span data-ttu-id="dd244-251">對於演算法唯一有意義的事情是加權，因此，此演算法不會計算機率、支援或變異數。</span><span class="sxs-lookup"><span data-stu-id="dd244-251">The only thing that is meaningful for the algorithm is the weights; therefore, the algorithm does not compute probability, support, or variance.</span></span>  
  
 <span data-ttu-id="dd244-252">若要在特定值的定型案例中取得支援的相關資訊，請查看臨界統計資料節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-252">To get information about the support in the training cases for specific values, see the marginal statistics node.</span></span>  
  
 <span data-ttu-id="dd244-253">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="dd244-253">MSOLAP_MODEL_COLUMN</span></span>  
 |<span data-ttu-id="dd244-254">節點</span><span class="sxs-lookup"><span data-stu-id="dd244-254">Node</span></span>|<span data-ttu-id="dd244-255">內容</span><span class="sxs-lookup"><span data-stu-id="dd244-255">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="dd244-256">模型根</span><span class="sxs-lookup"><span data-stu-id="dd244-256">Model root</span></span>|<span data-ttu-id="dd244-257">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-257">Blank</span></span>|  
|<span data-ttu-id="dd244-258">臨界統計資料</span><span class="sxs-lookup"><span data-stu-id="dd244-258">Marginal statistics</span></span>|<span data-ttu-id="dd244-259">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-259">Blank</span></span>|  
|<span data-ttu-id="dd244-260">輸入層</span><span class="sxs-lookup"><span data-stu-id="dd244-260">Input layer</span></span>|<span data-ttu-id="dd244-261">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-261">Blank</span></span>|  
|<span data-ttu-id="dd244-262">輸入節點</span><span class="sxs-lookup"><span data-stu-id="dd244-262">Input node</span></span>|<span data-ttu-id="dd244-263">輸入屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-263">Input attribute name.</span></span>|  
|<span data-ttu-id="dd244-264">hidden layer</span><span class="sxs-lookup"><span data-stu-id="dd244-264">Hidden layer</span></span>|<span data-ttu-id="dd244-265">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-265">Blank</span></span>|  
|<span data-ttu-id="dd244-266">輸出層</span><span class="sxs-lookup"><span data-stu-id="dd244-266">Output layer</span></span>|<span data-ttu-id="dd244-267">空白</span><span class="sxs-lookup"><span data-stu-id="dd244-267">Blank</span></span>|  
|<span data-ttu-id="dd244-268">輸出節點</span><span class="sxs-lookup"><span data-stu-id="dd244-268">Output node</span></span>|<span data-ttu-id="dd244-269">輸入屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="dd244-269">Input attribute name.</span></span>|  
  
 <span data-ttu-id="dd244-270">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="dd244-270">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="dd244-271">在羅吉斯迴歸模型中，永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="dd244-271">In logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="dd244-272">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="dd244-272">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="dd244-273">在羅吉斯迴歸模型中，永遠為空白。</span><span class="sxs-lookup"><span data-stu-id="dd244-273">In logistic regression models, always blank.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_NodeIDs"></a><span data-ttu-id="dd244-274">使用節點名稱和識別碼</span><span class="sxs-lookup"><span data-stu-id="dd244-274">Using Node Names and IDs</span></span>  
 <span data-ttu-id="dd244-275">在羅吉斯迴歸模型中之節點的命名，可提供模型中節點間之關聯性的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="dd244-275">The naming of the nodes in a logistic regression model provides additional information about the relationships between nodes in the model.</span></span> <span data-ttu-id="dd244-276">下表顯示指派給每層節點之識別碼的慣例。</span><span class="sxs-lookup"><span data-stu-id="dd244-276">The following table shows the conventions for the IDs that are assigned to nodes in each layer.</span></span>  
  
|<span data-ttu-id="dd244-277">節點類型</span><span class="sxs-lookup"><span data-stu-id="dd244-277">Node Type</span></span>|<span data-ttu-id="dd244-278">節點識別碼的慣例</span><span class="sxs-lookup"><span data-stu-id="dd244-278">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="dd244-279">模型根 (1)</span><span class="sxs-lookup"><span data-stu-id="dd244-279">Model root (1)</span></span>|<span data-ttu-id="dd244-280">00000000000000000.</span><span class="sxs-lookup"><span data-stu-id="dd244-280">00000000000000000.</span></span>|  
|<span data-ttu-id="dd244-281">臨界統計資料節點 (24)</span><span class="sxs-lookup"><span data-stu-id="dd244-281">Marginal statistics node (24)</span></span>|<span data-ttu-id="dd244-282">10000000000000000</span><span class="sxs-lookup"><span data-stu-id="dd244-282">10000000000000000</span></span>|  
|<span data-ttu-id="dd244-283">輸入層 (18)</span><span class="sxs-lookup"><span data-stu-id="dd244-283">Input layer (18)</span></span>|<span data-ttu-id="dd244-284">30000000000000000</span><span class="sxs-lookup"><span data-stu-id="dd244-284">30000000000000000</span></span>|  
|<span data-ttu-id="dd244-285">輸入節點 (21)</span><span class="sxs-lookup"><span data-stu-id="dd244-285">Input node (21)</span></span>|<span data-ttu-id="dd244-286">從 60000000000000000 開始</span><span class="sxs-lookup"><span data-stu-id="dd244-286">Starts at 60000000000000000</span></span>|  
|<span data-ttu-id="dd244-287">子網路 (17)</span><span class="sxs-lookup"><span data-stu-id="dd244-287">Subnetwork (17)</span></span>|<span data-ttu-id="dd244-288">20000000000000000</span><span class="sxs-lookup"><span data-stu-id="dd244-288">20000000000000000</span></span>|  
|<span data-ttu-id="dd244-289">隱藏層 (19)</span><span class="sxs-lookup"><span data-stu-id="dd244-289">Hidden layer (19)</span></span>|<span data-ttu-id="dd244-290">40000000000000000</span><span class="sxs-lookup"><span data-stu-id="dd244-290">40000000000000000</span></span>|  
|<span data-ttu-id="dd244-291">輸出層 (20)</span><span class="sxs-lookup"><span data-stu-id="dd244-291">Output layer (20)</span></span>|<span data-ttu-id="dd244-292">50000000000000000</span><span class="sxs-lookup"><span data-stu-id="dd244-292">50000000000000000</span></span>|  
|<span data-ttu-id="dd244-293">輸出節點 (23)</span><span class="sxs-lookup"><span data-stu-id="dd244-293">Output node (23)</span></span>|<span data-ttu-id="dd244-294">從 80000000000000000 開始</span><span class="sxs-lookup"><span data-stu-id="dd244-294">Starts at 80000000000000000</span></span>|  
  
 <span data-ttu-id="dd244-295">您可以使用這些識別碼，透過檢視輸出節點的 NODE_DISTRIBUTION 資料表，來判斷輸出屬性如何與特定輸入層屬性產生關聯。</span><span class="sxs-lookup"><span data-stu-id="dd244-295">You can use these IDs to determine how output attributes are related to specific input layer attributes, by viewing the NODE_DISTRIBUTION table of the output node.</span></span> <span data-ttu-id="dd244-296">該資料表中的每個資料列都包含一個識別碼，可指回特定的輸入屬性節點。</span><span class="sxs-lookup"><span data-stu-id="dd244-296">Each row in that table contains an ID that points back to a specific input attribute node.</span></span> <span data-ttu-id="dd244-297">NODE_DISTRIBUTION 資料表也包含該輸入和輸出配對的係數。</span><span class="sxs-lookup"><span data-stu-id="dd244-297">The NODE_DISTRIBUTION table also contains the coefficient for that input-output pair.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd244-298">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd244-298">See Also</span></span>  
 <span data-ttu-id="dd244-299">[Microsoft 羅吉斯回歸演算法](microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="dd244-299">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="dd244-300">[類神經網路模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="dd244-300">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="dd244-301">[羅吉斯回歸模型查詢範例](logistic-regression-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="dd244-301">[Logistic Regression Model Query Examples](logistic-regression-model-query-examples.md) </span></span>  
 [<span data-ttu-id="dd244-302">Microsoft 羅吉斯迴歸演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="dd244-302">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)  
  
  
