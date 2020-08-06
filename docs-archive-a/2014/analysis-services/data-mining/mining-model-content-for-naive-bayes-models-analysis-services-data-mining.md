---
title: 貝氏貝氏機率分類模型 (Analysis Services 資料採礦) 的模型內容 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- mining model content, naive bayes models
ms.assetid: 63fa15b0-e00c-4aa3-aa49-335f5572ff7e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 52e5da80e109828722d56fada19b019d1cfa51f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598666"
---
# <a name="mining-model-content-for-naive-bayes-models-analysis-services---data-mining"></a><span data-ttu-id="a3a16-102">貝氏機率分類模型的採礦模型內容 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="a3a16-102">Mining Model Content for Naive Bayes Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="a3a16-103">本主題描述使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝式機率分類演算法之模型專用的採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="a3a16-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span> <span data-ttu-id="a3a16-104">如需如何解譯所有模型類型共用的統計資料與結構的說明，以及與採礦模型內容相關的一般詞彙說明，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-naive-bayes-model"></a><span data-ttu-id="a3a16-105">了解貝式機率分類模型的結構</span><span class="sxs-lookup"><span data-stu-id="a3a16-105">Understanding the Structure of a Naive Bayes Model</span></span>  
 <span data-ttu-id="a3a16-106">貝式機率分類模型擁有代表模型及其中繼資料的單一父節點，而且在該父節點下，則擁有代表所選取之可預測屬性的所有獨立樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="a3a16-106">A Naive Bayes model has a single parent node that represents the model and its metadata, and underneath that parent node, any number of independent trees that represent the predictable attributes that you selected.</span></span> <span data-ttu-id="a3a16-107">除了屬性的樹狀結構，每個模型都包含一個臨界統計資料節點 (NODE_TYPE = 26)，該節點會提供該組定型案例的描述性統計資料。</span><span class="sxs-lookup"><span data-stu-id="a3a16-107">In addition to trees for the attributes, each model contains one marginal statistics node (NODE_TYPE = 26) that provides descriptive statistics about the set of training cases.</span></span> <span data-ttu-id="a3a16-108">如需詳細資訊，請參閱 [臨界統計資料節點中的資訊](#bkmk_margstats)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-108">For more information, see [Information in the Marginal Statistics Node](#bkmk_margstats).</span></span>  
  
 <span data-ttu-id="a3a16-109">對於每個可預測的屬性和值，此模型都會輸出一個樹狀結構，其中包含描述各種輸入資料行如何影響該特定可預測屬性和值之結果的資訊。</span><span class="sxs-lookup"><span data-stu-id="a3a16-109">For each predictable attribute and value, the model outputs a tree that contains information describing how the various input columns affected the outcome of that particular predictable.</span></span> <span data-ttu-id="a3a16-110">每個樹狀結構都包含可預測的屬性及其值 (NODE_TYPE = 9)，接著是一系列代表輸入屬性 (NODE_TYPE = 10) 的節點。</span><span class="sxs-lookup"><span data-stu-id="a3a16-110">Each tree contains the predictable attribute and its value (NODE_TYPE = 9), and then a series of nodes that represent the input attributes (NODE_TYPE = 10).</span></span> <span data-ttu-id="a3a16-111">輸入屬性通常擁有多個值，因此每個輸入屬性 (NODE_TYPE = 10) 都可能擁有多個子節點 (NODE_TYPE = 11)，每個子節點都可用於屬性的特定狀態。</span><span class="sxs-lookup"><span data-stu-id="a3a16-111">Because the input attributes typically have multiple values, each input attribute (NODE_TYPE = 10) may have multiple child nodes (NODE_TYPE = 11), each for a specific state of the attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3a16-112">由於貝式機率分類模型不允許使用連續資料類型，因此會將輸入資料行的所有值都視為離散或離散化的值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-112">Because a Naive Bayes model does not permit continuous data types, all the values of the input columns are treated as discrete or discretized.</span></span> <span data-ttu-id="a3a16-113">您可以指定將值離散化的方式。</span><span class="sxs-lookup"><span data-stu-id="a3a16-113">You can specify how a value is discretized.</span></span> <span data-ttu-id="a3a16-114">如需詳細資訊，請參閱 [變更採礦模型中的資料行離散化](change-the-discretization-of-a-column-in-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-114">For more information, [Change the Discretization of a Column in a Mining Model](change-the-discretization-of-a-column-in-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="a3a16-115">![貝氏機率分類的模型內容結構](../media/modelcontentstructure-nb.gif "貝氏機率分類的模型內容結構")</span><span class="sxs-lookup"><span data-stu-id="a3a16-115">![structure of model content for naive bayes](../media/modelcontentstructure-nb.gif "structure of model content for naive bayes")</span></span>  
  
## <a name="model-content-for-a-naive-bayes-model"></a><span data-ttu-id="a3a16-116">貝式機率分類模型的模型內容</span><span class="sxs-lookup"><span data-stu-id="a3a16-116">Model Content for a Naive Bayes Model</span></span>  
 <span data-ttu-id="a3a16-117">本節僅針對採礦模型內容中與貝式機率分類模型具有特定相關的資料行，提供詳細資料和範例。</span><span class="sxs-lookup"><span data-stu-id="a3a16-117">This section provides detail and examples only for those columns in the mining model content that have particular relevance for Naive Bayes models.</span></span>  
  
 <span data-ttu-id="a3a16-118">如需結構描述資料列集 (例如 MODEL_CATALOG 和 MODEL_NAME) 中一般用途資料行的詳細資訊 (此處沒有說明)，或採礦模型術語的說明，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-118">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="a3a16-119">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3a16-119">MODEL_CATALOG</span></span>  
 <span data-ttu-id="a3a16-120">模型儲存位置所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-120">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="a3a16-121">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-121">MODEL_NAME</span></span>  
 <span data-ttu-id="a3a16-122">模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-122">Name of the model.</span></span>  
  
 <span data-ttu-id="a3a16-123">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-123">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="a3a16-124">對應至這個節點之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-124">The names of the attributes that correspond to this node.</span></span>  
  
 <span data-ttu-id="a3a16-125">**模型根** ：可預測屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-125">**Model root** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a3a16-126">**臨界統計資料** ：不適用</span><span class="sxs-lookup"><span data-stu-id="a3a16-126">**Marginal statistics** Not applicable</span></span>  
  
 <span data-ttu-id="a3a16-127">**可預測的屬性** ：可預測屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-127">**Predictable attribute** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a3a16-128">**輸入屬性** ：輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-128">**Input attribute** The name of the input attribute.</span></span>  
  
 <span data-ttu-id="a3a16-129">**輸入屬性狀態** ：僅限輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-129">**Input attribute state** The name of the input attribute only.</span></span> <span data-ttu-id="a3a16-130">若要取得狀態，使用 MSOLAP_NODE_SHORT_CAPTION。</span><span class="sxs-lookup"><span data-stu-id="a3a16-130">To get the state, use MSOLAP_NODE_SHORT_CAPTION.</span></span>  
  
 <span data-ttu-id="a3a16-131">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-131">NODE_NAME</span></span>  
 <span data-ttu-id="a3a16-132">節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-132">The name of the node.</span></span>  
  
 <span data-ttu-id="a3a16-133">此資料行包含與 NODE_UNIQUE_NAME 相同的值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-133">This column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="a3a16-134">如需節點命名慣例的詳細資訊，請參閱 [使用節點名稱與識別碼](#bkmk_nodenames)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-134">For more information about node naming conventions, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="a3a16-135">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-135">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="a3a16-136">節點的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-136">The unique name of the node.</span></span> <span data-ttu-id="a3a16-137">系統會根據提供節點間關聯性之資訊的慣例指派唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-137">The unique names are assigned according to a convention that provides information about the relationships among the nodes.</span></span> <span data-ttu-id="a3a16-138">如需節點命名慣例的詳細資訊，請參閱 [使用節點名稱與識別碼](#bkmk_nodenames)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-138">For more information about node naming conventions, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="a3a16-139">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a3a16-139">NODE_TYPE</span></span>  
 <span data-ttu-id="a3a16-140">貝式機率分類模型會輸出下列節點類型：</span><span class="sxs-lookup"><span data-stu-id="a3a16-140">A Naive Bayes model outputs the following node types:</span></span>  
  
|<span data-ttu-id="a3a16-141">節點類型識別碼</span><span class="sxs-lookup"><span data-stu-id="a3a16-141">Node Type ID</span></span>|<span data-ttu-id="a3a16-142">描述</span><span class="sxs-lookup"><span data-stu-id="a3a16-142">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="a3a16-143">26 (NaiveBayesMarginalStatNode)</span><span class="sxs-lookup"><span data-stu-id="a3a16-143">26 (NaiveBayesMarginalStatNode)</span></span>|<span data-ttu-id="a3a16-144">包含描述模型整組定型案例的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a3a16-144">Contains statistics that describes the entire set of training cases for the model.</span></span>|  
|<span data-ttu-id="a3a16-145">9 (可預測的屬性)</span><span class="sxs-lookup"><span data-stu-id="a3a16-145">9 (Predictable attribute)</span></span>|<span data-ttu-id="a3a16-146">包含可預測屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-146">Contains the name of the predictable-attribute.</span></span>|  
|<span data-ttu-id="a3a16-147">10 (輸入屬性)</span><span class="sxs-lookup"><span data-stu-id="a3a16-147">10 (Input attribute)</span></span>|<span data-ttu-id="a3a16-148">包含輸入屬性資料行的名稱，以及含有屬性值之子節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-148">Contains the name of an input attribute column, and child nodes that contains the values for the attribute.</span></span>|  
|<span data-ttu-id="a3a16-149">11 (輸入屬性狀態)</span><span class="sxs-lookup"><span data-stu-id="a3a16-149">11 (Input attribute state)</span></span>|<span data-ttu-id="a3a16-150">包含與特定輸出屬性配對之所有輸入屬性的值或離散化的值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-150">Contains the values or discretized values of all input attributes that were paired with a particular output attribute.</span></span>|  
  
 <span data-ttu-id="a3a16-151">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a3a16-151">NODE_CAPTION</span></span>  
 <span data-ttu-id="a3a16-152">與節點關聯的標籤或標題。</span><span class="sxs-lookup"><span data-stu-id="a3a16-152">The label or a caption associated with the node.</span></span> <span data-ttu-id="a3a16-153">這個屬性主要是供顯示之用。</span><span class="sxs-lookup"><span data-stu-id="a3a16-153">This property is primarily for display purposes.</span></span>  
  
 <span data-ttu-id="a3a16-154">**模型根** ：空白</span><span class="sxs-lookup"><span data-stu-id="a3a16-154">**Model root** blank</span></span>  
  
 <span data-ttu-id="a3a16-155">臨界**統計資料**空白</span><span class="sxs-lookup"><span data-stu-id="a3a16-155">**Marginal statistics** blank</span></span>  
  
 <span data-ttu-id="a3a16-156">**可預測的屬性** ：可預測屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-156">**Predictable attribute** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a3a16-157">**輸入屬性** ：可預測屬性與目前輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-157">**Input attribute** The name of the predictable attribute and the current input attribute.</span></span> <span data-ttu-id="a3a16-158">例如：</span><span class="sxs-lookup"><span data-stu-id="a3a16-158">Ex:</span></span>  
  
 <span data-ttu-id="a3a16-159">Bike Buyer -> Age</span><span class="sxs-lookup"><span data-stu-id="a3a16-159">Bike Buyer -> Age</span></span>  
  
 <span data-ttu-id="a3a16-160">**輸入屬性狀態** ：可預測屬性與目前輸入屬性的名稱，加上輸入的值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-160">**Input attribute state** The name of the predictable attribute and the current input attribute, plus the value of the input.</span></span> <span data-ttu-id="a3a16-161">例如：</span><span class="sxs-lookup"><span data-stu-id="a3a16-161">Ex:</span></span>  
  
 <span data-ttu-id="a3a16-162">Bike Buyer -> Age = Missing</span><span class="sxs-lookup"><span data-stu-id="a3a16-162">Bike Buyer -> Age = Missing</span></span>  
  
 <span data-ttu-id="a3a16-163">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="a3a16-163">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="a3a16-164">節點擁有的子系數目。</span><span class="sxs-lookup"><span data-stu-id="a3a16-164">The number of children that the node has.</span></span>  
  
 <span data-ttu-id="a3a16-165">**模型根** ：模型中的可預測屬性計數針對臨界統計資料節點加 1。</span><span class="sxs-lookup"><span data-stu-id="a3a16-165">**Model root** Count of predictable attributes in the model plus 1 for the marginal statistics node.</span></span>  
  
 <span data-ttu-id="a3a16-166">**臨界統計資料** ：依定義，沒有子系。</span><span class="sxs-lookup"><span data-stu-id="a3a16-166">**Marginal statistics** By definition has no children.</span></span>  
  
 <span data-ttu-id="a3a16-167">**可預測的屬性**  ：與目前可預測屬性相關之輸入屬性的計數。</span><span class="sxs-lookup"><span data-stu-id="a3a16-167">**Predictable attribute**  Count of the input attributes that were related to the current predictable attribute.</span></span>  
  
 <span data-ttu-id="a3a16-168">**輸入屬性** ：目前輸入屬性之離散值或離散化之值的計數。</span><span class="sxs-lookup"><span data-stu-id="a3a16-168">**Input attribute** Count of the discrete or discretized values for the current input attribute.</span></span>  
  
 <span data-ttu-id="a3a16-169">**輸入屬性狀態** ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-169">**Input attribute state** Always 0.</span></span>  
  
 <span data-ttu-id="a3a16-170">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-170">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="a3a16-171">父節點的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-171">The unique name of the parent node.</span></span> <span data-ttu-id="a3a16-172">如需父節點與子節點關聯的詳細資訊，請參閱 [使用節點名稱與識別碼](#bkmk_nodenames)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-172">For more information about relating parent and child nodes, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="a3a16-173">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a3a16-173">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="a3a16-174">與節點標題相同。</span><span class="sxs-lookup"><span data-stu-id="a3a16-174">The same as the node caption.</span></span>  
  
 <span data-ttu-id="a3a16-175">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="a3a16-175">NODE_RULE</span></span>  
 <span data-ttu-id="a3a16-176">節點標題的 XML 表示。</span><span class="sxs-lookup"><span data-stu-id="a3a16-176">An XML representation of the node caption.</span></span>  
  
 <span data-ttu-id="a3a16-177">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="a3a16-177">MARGINAL_RULE</span></span>  
 <span data-ttu-id="a3a16-178">與節點規則相同。</span><span class="sxs-lookup"><span data-stu-id="a3a16-178">The same as the node rule.</span></span>  
  
 <span data-ttu-id="a3a16-179">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a3a16-179">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="a3a16-180">與此節點關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="a3a16-180">The probability associated with this node.</span></span>  
  
 <span data-ttu-id="a3a16-181">**模型根** ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-181">**Model root** Always 0.</span></span>  
  
 <span data-ttu-id="a3a16-182">**臨界統計資料** ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-182">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="a3a16-183">**可預測的屬性**  ：一律為 1。</span><span class="sxs-lookup"><span data-stu-id="a3a16-183">**Predictable attribute**  Always 1.</span></span>  
  
 <span data-ttu-id="a3a16-184">**輸入屬性** ：一律為 1。</span><span class="sxs-lookup"><span data-stu-id="a3a16-184">**Input attribute** Always 1.</span></span>  
  
 <span data-ttu-id="a3a16-185">**輸入屬性狀態** ：代表目前值機率的十進位數字。</span><span class="sxs-lookup"><span data-stu-id="a3a16-185">**Input attribute state** A decimal number that represents the probability of the current value.</span></span> <span data-ttu-id="a3a16-186">父系輸入屬性節點下，所有輸入屬性狀態的值總和為 1。</span><span class="sxs-lookup"><span data-stu-id="a3a16-186">Values for all input attribute states under the parent input attribute node sum to 1.</span></span>  
  
 <span data-ttu-id="a3a16-187">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a3a16-187">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="a3a16-188">與節點機率相同。</span><span class="sxs-lookup"><span data-stu-id="a3a16-188">The same as the node probability.</span></span>  
  
 <span data-ttu-id="a3a16-189">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="a3a16-189">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="a3a16-190">包含節點之機率長條圖的資料表。</span><span class="sxs-lookup"><span data-stu-id="a3a16-190">A table that contains the probability histogram for the node.</span></span> <span data-ttu-id="a3a16-191">如需詳細資訊，請參閱 [NODE_DISTRIBUTION 資料表](#bkmk_nodedist)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-191">For more information, see [NODE_DISTRIBUTION Table](#bkmk_nodedist).</span></span>  
  
 <span data-ttu-id="a3a16-192">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a3a16-192">NODE_SUPPORT</span></span>  
 <span data-ttu-id="a3a16-193">支援這個節點的案例數目。</span><span class="sxs-lookup"><span data-stu-id="a3a16-193">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="a3a16-194">**模型根** ：定型資料中所有案例的計數。</span><span class="sxs-lookup"><span data-stu-id="a3a16-194">**Model root** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="a3a16-195">**臨界統計資料** ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-195">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="a3a16-196">**可預測的屬性** ：定型資料中所有案例的計數。</span><span class="sxs-lookup"><span data-stu-id="a3a16-196">**Predictable attribute** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="a3a16-197">**輸入屬性** ：定型資料中所有案例的計數。</span><span class="sxs-lookup"><span data-stu-id="a3a16-197">**Input attribute** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="a3a16-198">**輸入屬性狀態** ：定型資料中，僅包含此特定值之案例的計數。</span><span class="sxs-lookup"><span data-stu-id="a3a16-198">**Input attribute state** Count of cases in training data that contain only this particular value.</span></span>  
  
 <span data-ttu-id="a3a16-199">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="a3a16-199">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="a3a16-200">主要用於顯示用途。</span><span class="sxs-lookup"><span data-stu-id="a3a16-200">A label used for display purposes.</span></span> <span data-ttu-id="a3a16-201">通常和 ATTRIBUTE_NAME 相同。</span><span class="sxs-lookup"><span data-stu-id="a3a16-201">Usually the same as ATTRIBUTE_NAME.</span></span>  
  
 <span data-ttu-id="a3a16-202">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="a3a16-202">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="a3a16-203">代表模型中屬性或值的重要性。</span><span class="sxs-lookup"><span data-stu-id="a3a16-203">Represents the importance of the attribute or value within the model.</span></span>  
  
 <span data-ttu-id="a3a16-204">**模型根** ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-204">**Model root** Always 0.</span></span>  
  
 <span data-ttu-id="a3a16-205">**臨界統計資料** ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-205">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="a3a16-206">**可預測的屬性**  ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-206">**Predictable attribute**  Always 0.</span></span>  
  
 <span data-ttu-id="a3a16-207">**輸入屬性** ：目前輸入屬性相對於目前可預測屬性的有趣性分數。</span><span class="sxs-lookup"><span data-stu-id="a3a16-207">**Input attribute** Interestingness score for the current input attribute in relation to the current predictable attribute.</span></span>  
  
 <span data-ttu-id="a3a16-208">**輸入屬性狀態** ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-208">**Input attribute state** Always 0.</span></span>  
  
 <span data-ttu-id="a3a16-209">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a3a16-209">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="a3a16-210">文字字串，表示資料行的名稱或值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-210">A text string that represents the name or the value of a column.</span></span>  
  
 <span data-ttu-id="a3a16-211">**模型根**著</span><span class="sxs-lookup"><span data-stu-id="a3a16-211">**Model root** Blank</span></span>  
  
 <span data-ttu-id="a3a16-212">**臨界統計資料** ：空白</span><span class="sxs-lookup"><span data-stu-id="a3a16-212">**Marginal statistics** Blank</span></span>  
  
 <span data-ttu-id="a3a16-213">**可預測屬性** 可預測屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-213">**Predictable attribute**  The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a3a16-214">**輸入屬性** ：輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a16-214">**Input attribute** The name of the input attribute.</span></span>  
  
 <span data-ttu-id="a3a16-215">**輸入屬性狀態** ：輸入屬性的值或離散化的值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-215">**Input attribute state** The value or discretized value of the input attribute.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_nodenames"></a><span data-ttu-id="a3a16-216">使用節點名稱和識別碼</span><span class="sxs-lookup"><span data-stu-id="a3a16-216">Using Node Names and IDs</span></span>  
 <span data-ttu-id="a3a16-217">在貝式機率分類中之節點的命名，可提供節點類型的其他資訊，讓您更容易了解模型中資訊間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a3a16-217">The naming of the nodes in a Naive Bayes model provides additional information about the type of node, to make it easier to understand the relationships among the information in the model.</span></span> <span data-ttu-id="a3a16-218">下表顯示指派給不同節點類型之識別碼的慣例。</span><span class="sxs-lookup"><span data-stu-id="a3a16-218">The following table shows the convention for the IDs that are assigned to different node types.</span></span>  
  
|<span data-ttu-id="a3a16-219">節點類型</span><span class="sxs-lookup"><span data-stu-id="a3a16-219">Node Type</span></span>|<span data-ttu-id="a3a16-220">節點識別碼的慣例</span><span class="sxs-lookup"><span data-stu-id="a3a16-220">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="a3a16-221">模型根 (1)</span><span class="sxs-lookup"><span data-stu-id="a3a16-221">Model root (1)</span></span>|<span data-ttu-id="a3a16-222">一律是 0。</span><span class="sxs-lookup"><span data-stu-id="a3a16-222">Always 0.</span></span>|  
|<span data-ttu-id="a3a16-223">臨界統計資料節點 (26)</span><span class="sxs-lookup"><span data-stu-id="a3a16-223">Marginal statistics node (26)</span></span>|<span data-ttu-id="a3a16-224">任意的識別碼值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-224">An arbitrary ID value.</span></span>|  
|<span data-ttu-id="a3a16-225">可預測的屬性 (9)</span><span class="sxs-lookup"><span data-stu-id="a3a16-225">Predictable attribute (9)</span></span>|<span data-ttu-id="a3a16-226">開頭為 10000000 的十六進位數字</span><span class="sxs-lookup"><span data-stu-id="a3a16-226">Hexadecimal number beginning with 10000000</span></span><br /><br /> <span data-ttu-id="a3a16-227">例如，100000001、10000000b</span><span class="sxs-lookup"><span data-stu-id="a3a16-227">Example: 100000001, 10000000b</span></span>|  
|<span data-ttu-id="a3a16-228">輸入屬性 (10)</span><span class="sxs-lookup"><span data-stu-id="a3a16-228">Input attribute (10)</span></span>|<span data-ttu-id="a3a16-229">兩部分的十六進位數字，其中第一部分永遠為 20000000，而第二部分開頭為相關可預測屬性的十六進位識別碼。</span><span class="sxs-lookup"><span data-stu-id="a3a16-229">A two-part hexadecimal number where the first part is always 20000000, and the second part starts with the hexadecimal identifier of the related predictable attribute.</span></span><br /><br /> <span data-ttu-id="a3a16-230">例如：20000000b00000000</span><span class="sxs-lookup"><span data-stu-id="a3a16-230">Example: 20000000b00000000</span></span><br /><br /> <span data-ttu-id="a3a16-231">在此情況下，相關的可預測屬性為 10000000b。</span><span class="sxs-lookup"><span data-stu-id="a3a16-231">In this case, the related predictable attribute is 10000000b.</span></span>|  
|<span data-ttu-id="a3a16-232">輸入屬性狀態 (11)</span><span class="sxs-lookup"><span data-stu-id="a3a16-232">Input attribute state (11)</span></span>|<span data-ttu-id="a3a16-233">三部分的十六進位數字，其中第一部分永遠為 30000000，第二部分開頭為相關可預測屬性的十六進位識別碼，而第三部分代表值的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a3a16-233">A three-part hexadecimal number where the first part is always 30000000, the second part starts with the hexadecimal identifier of the related predictable attribute, and the third part represents the identifier of the value.</span></span><br /><br /> <span data-ttu-id="a3a16-234">例如：30000000b00000000200000000</span><span class="sxs-lookup"><span data-stu-id="a3a16-234">Example: 30000000b00000000200000000</span></span><br /><br /> <span data-ttu-id="a3a16-235">在此情況下，相關的可預測屬性為 10000000b。</span><span class="sxs-lookup"><span data-stu-id="a3a16-235">In this case, the related predictable attribute is 10000000b.</span></span>|  
  
 <span data-ttu-id="a3a16-236">您可以使用識別碼將輸入屬性和狀態與可預測的屬性產生關聯。</span><span class="sxs-lookup"><span data-stu-id="a3a16-236">You can use the IDs to relate input attributes and states to a predictable attribute.</span></span> <span data-ttu-id="a3a16-237">例如，下列查詢會針對代表模型 `TM_NaiveBayes`之輸入屬性與可預測屬性可能組合的節點，傳回名稱和標題。</span><span class="sxs-lookup"><span data-stu-id="a3a16-237">For example, the following query returns the names and captions for nodes that represent the possible combinations of input and predictable attributes for the model, `TM_NaiveBayes`.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
```  
  
 <span data-ttu-id="a3a16-238">預期的結果：</span><span class="sxs-lookup"><span data-stu-id="a3a16-238">Expected results:</span></span>  
  
|<span data-ttu-id="a3a16-239">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-239">NODE_NAME</span></span>|<span data-ttu-id="a3a16-240">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a3a16-240">NODE_CAPTION</span></span>|  
|----------------|-------------------|  
|<span data-ttu-id="a3a16-241">20000000000000001</span><span class="sxs-lookup"><span data-stu-id="a3a16-241">20000000000000001</span></span>|<span data-ttu-id="a3a16-242">Bike Buyer -> Commute Distance</span><span class="sxs-lookup"><span data-stu-id="a3a16-242">Bike Buyer -> Commute Distance</span></span>|  
|<span data-ttu-id="a3a16-243">20000000000000002</span><span class="sxs-lookup"><span data-stu-id="a3a16-243">20000000000000002</span></span>|<span data-ttu-id="a3a16-244">Bike Buyer -> English Education</span><span class="sxs-lookup"><span data-stu-id="a3a16-244">Bike Buyer -> English Education</span></span>|  
|<span data-ttu-id="a3a16-245">20000000000000003</span><span class="sxs-lookup"><span data-stu-id="a3a16-245">20000000000000003</span></span>|<span data-ttu-id="a3a16-246">Bike Buyer -> English Occupation</span><span class="sxs-lookup"><span data-stu-id="a3a16-246">Bike Buyer -> English Occupation</span></span>|  
|<span data-ttu-id="a3a16-247">20000000000000009</span><span class="sxs-lookup"><span data-stu-id="a3a16-247">20000000000000009</span></span>|<span data-ttu-id="a3a16-248">Bike Buyer -> Marital Status</span><span class="sxs-lookup"><span data-stu-id="a3a16-248">Bike Buyer -> Marital Status</span></span>|  
|<span data-ttu-id="a3a16-249">2000000000000000a</span><span class="sxs-lookup"><span data-stu-id="a3a16-249">2000000000000000a</span></span>|<span data-ttu-id="a3a16-250">Bike Buyer -> Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="a3a16-250">Bike Buyer -> Number Children At Home</span></span>|  
|<span data-ttu-id="a3a16-251">2000000000000000b</span><span class="sxs-lookup"><span data-stu-id="a3a16-251">2000000000000000b</span></span>|<span data-ttu-id="a3a16-252">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="a3a16-252">Bike Buyer -> Region</span></span>|  
|<span data-ttu-id="a3a16-253">2000000000000000c</span><span class="sxs-lookup"><span data-stu-id="a3a16-253">2000000000000000c</span></span>|<span data-ttu-id="a3a16-254">Bike Buyer -> Total Children</span><span class="sxs-lookup"><span data-stu-id="a3a16-254">Bike Buyer -> Total Children</span></span>|  
  
 <span data-ttu-id="a3a16-255">接著，您可以使用父節點的識別碼來擷取子節點。</span><span class="sxs-lookup"><span data-stu-id="a3a16-255">You can then use the IDs of the parent nodes to retrieve the child nodes.</span></span> <span data-ttu-id="a3a16-256">下列查詢會擷取包含 `Marital Status` 屬性值的節點，以及每個節點的機率。</span><span class="sxs-lookup"><span data-stu-id="a3a16-256">The following query retrieves the nodes that contain values for the `Marital Status` attribute, together with the probability of each node.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION, NODE_PROBABILITY  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 11  
AND [PARENT_UNIQUE_NAME] = '20000000000000009'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a3a16-257">資料行 PARENT_UNIQUE_NAME 的名稱必須括在括號內，以便與同名的保留關鍵字區別。</span><span class="sxs-lookup"><span data-stu-id="a3a16-257">The name of the column, PARENT_UNIQUE_NAME, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="a3a16-258">預期的結果：</span><span class="sxs-lookup"><span data-stu-id="a3a16-258">Expected results:</span></span>  
  
|<span data-ttu-id="a3a16-259">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-259">NODE_NAME</span></span>|<span data-ttu-id="a3a16-260">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a3a16-260">NODE_CAPTION</span></span>|<span data-ttu-id="a3a16-261">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a3a16-261">NODE_PROBABILITY</span></span>|  
|----------------|-------------------|-----------------------|  
|<span data-ttu-id="a3a16-262">3000000000000000900000000</span><span class="sxs-lookup"><span data-stu-id="a3a16-262">3000000000000000900000000</span></span>|<span data-ttu-id="a3a16-263">Bike Buyer -> Marital Status = Missing</span><span class="sxs-lookup"><span data-stu-id="a3a16-263">Bike Buyer -> Marital Status = Missing</span></span>|<span data-ttu-id="a3a16-264">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-264">0</span></span>|  
|<span data-ttu-id="a3a16-265">3000000000000000900000001</span><span class="sxs-lookup"><span data-stu-id="a3a16-265">3000000000000000900000001</span></span>|<span data-ttu-id="a3a16-266">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="a3a16-266">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="a3a16-267">0.457504004</span><span class="sxs-lookup"><span data-stu-id="a3a16-267">0.457504004</span></span>|  
|<span data-ttu-id="a3a16-268">3000000000000000900000002</span><span class="sxs-lookup"><span data-stu-id="a3a16-268">3000000000000000900000002</span></span>|<span data-ttu-id="a3a16-269">Bike Buyer -> Marital Status = M</span><span class="sxs-lookup"><span data-stu-id="a3a16-269">Bike Buyer -> Marital Status = M</span></span>|<span data-ttu-id="a3a16-270">0.542495996</span><span class="sxs-lookup"><span data-stu-id="a3a16-270">0.542495996</span></span>|  
  
##  <a name="node_distribution-table"></a><a name="bkmk_nodedist"></a><span data-ttu-id="a3a16-271">NODE_DISTRIBUTION 資料表</span><span class="sxs-lookup"><span data-stu-id="a3a16-271">NODE_DISTRIBUTION Table</span></span>  
 <span data-ttu-id="a3a16-272">巢狀資料表資料行 NODE_DISTRIBUTION 通常包含節點中值分佈的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a3a16-272">The nested table column, NODE_DISTRIBUTION, typically contains statistics about the distribution of values in the node.</span></span> <span data-ttu-id="a3a16-273">在貝式機率分類模型中，僅會針對下列節點填入此資料表：</span><span class="sxs-lookup"><span data-stu-id="a3a16-273">In a Naive Bayes model, this table is populated only for the following nodes:</span></span>  
  
|<span data-ttu-id="a3a16-274">節點類型</span><span class="sxs-lookup"><span data-stu-id="a3a16-274">Node Type</span></span>|<span data-ttu-id="a3a16-275">巢狀資料表的內容</span><span class="sxs-lookup"><span data-stu-id="a3a16-275">Content of nested table</span></span>|  
|---------------|-----------------------------|  
|<span data-ttu-id="a3a16-276">模型根 (1)</span><span class="sxs-lookup"><span data-stu-id="a3a16-276">Model root (1)</span></span>|<span data-ttu-id="a3a16-277">空白。</span><span class="sxs-lookup"><span data-stu-id="a3a16-277">Blank.</span></span>|  
|<span data-ttu-id="a3a16-278">臨界統計資料節點 (24)</span><span class="sxs-lookup"><span data-stu-id="a3a16-278">Marginal statistics node (24)</span></span>|<span data-ttu-id="a3a16-279">對於整組定型資料，包含所有可預測屬性和輸入屬性的摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="a3a16-279">Contains summary information for all predictable attributes and input attributes, for entire set of training data.</span></span>|  
|<span data-ttu-id="a3a16-280">可預測的屬性 (9)</span><span class="sxs-lookup"><span data-stu-id="a3a16-280">Predictable attribute (9)</span></span>|<span data-ttu-id="a3a16-281">空白。</span><span class="sxs-lookup"><span data-stu-id="a3a16-281">Blank.</span></span>|  
|<span data-ttu-id="a3a16-282">輸入屬性 (10)</span><span class="sxs-lookup"><span data-stu-id="a3a16-282">Input attribute (10)</span></span>|<span data-ttu-id="a3a16-283">空白。</span><span class="sxs-lookup"><span data-stu-id="a3a16-283">Blank.</span></span>|  
|<span data-ttu-id="a3a16-284">輸入屬性狀態 (11)</span><span class="sxs-lookup"><span data-stu-id="a3a16-284">Input attribute state (11)</span></span>|<span data-ttu-id="a3a16-285">針對可預測值與輸入屬性值的這個特定組合，包含描述定型資料中值分佈的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a3a16-285">Contains statistics that describe the distribution of values in the training data for this particular combination of a predictable value and input attribute value.</span></span>|  
  
 <span data-ttu-id="a3a16-286">您可以使用節點識別碼或節點標題來擷取詳細資料的遞增層級。</span><span class="sxs-lookup"><span data-stu-id="a3a16-286">You can use the node IDs or node captions to retrieve increasing levels of detail.</span></span> <span data-ttu-id="a3a16-287">例如，下列查詢僅針對與值 `'Marital Status = S'`相關的輸入屬性節點，從 NODE_DISTRIBUTION 資料表擷取特定的資料行。</span><span class="sxs-lookup"><span data-stu-id="a3a16-287">For example, the following query retrieves specific columns from the NODE_DISTRIBUTION table for only those input attribute nodes that are related to the value, `'Marital Status = S'`.</span></span>  
  
```  
SELECT FLATTENED NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM TM_NaiveBayes.content  
WHERE NODE_TYPE = 11  
AND NODE_CAPTION = 'Bike Buyer -> Marital Status = S'  
```  
  
 <span data-ttu-id="a3a16-288">預期的結果：</span><span class="sxs-lookup"><span data-stu-id="a3a16-288">Expected results:</span></span>  
  
|<span data-ttu-id="a3a16-289">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a3a16-289">NODE_CAPTION</span></span>|<span data-ttu-id="a3a16-290">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-290">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a3a16-291">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a3a16-291">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a3a16-292">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a3a16-292">t.SUPPORT</span></span>|<span data-ttu-id="a3a16-293">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a3a16-293">t.PROBABILITY</span></span>|<span data-ttu-id="a3a16-294">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a3a16-294">t.VALUETYPE</span></span>|  
|-------------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="a3a16-295">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="a3a16-295">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="a3a16-296">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a3a16-296">Bike Buyer</span></span>|<span data-ttu-id="a3a16-297">Missing</span><span class="sxs-lookup"><span data-stu-id="a3a16-297">Missing</span></span>|<span data-ttu-id="a3a16-298">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-298">0</span></span>|<span data-ttu-id="a3a16-299">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-299">0</span></span>|<span data-ttu-id="a3a16-300">1</span><span class="sxs-lookup"><span data-stu-id="a3a16-300">1</span></span>|  
|<span data-ttu-id="a3a16-301">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="a3a16-301">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="a3a16-302">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a3a16-302">Bike Buyer</span></span>|<span data-ttu-id="a3a16-303">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-303">0</span></span>|<span data-ttu-id="a3a16-304">3783</span><span class="sxs-lookup"><span data-stu-id="a3a16-304">3783</span></span>|<span data-ttu-id="a3a16-305">0.472934117</span><span class="sxs-lookup"><span data-stu-id="a3a16-305">0.472934117</span></span>|<span data-ttu-id="a3a16-306">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-306">4</span></span>|  
|<span data-ttu-id="a3a16-307">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="a3a16-307">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="a3a16-308">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a3a16-308">Bike Buyer</span></span>|<span data-ttu-id="a3a16-309">1</span><span class="sxs-lookup"><span data-stu-id="a3a16-309">1</span></span>|<span data-ttu-id="a3a16-310">4216</span><span class="sxs-lookup"><span data-stu-id="a3a16-310">4216</span></span>|<span data-ttu-id="a3a16-311">0.527065883</span><span class="sxs-lookup"><span data-stu-id="a3a16-311">0.527065883</span></span>|<span data-ttu-id="a3a16-312">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-312">4</span></span>|  
  
 <span data-ttu-id="a3a16-313">在這些結果中，SUPPORT 資料行的值會顯示購買自行車之客戶的計數，以及指定的婚姻狀況。</span><span class="sxs-lookup"><span data-stu-id="a3a16-313">In these results, the value of the SUPPORT column tells you the count of customers with the specified marital status who purchased a bike.</span></span> <span data-ttu-id="a3a16-314">PROBABILITY 資料行包含每個屬性值的機率 (僅針對此節點計算)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-314">The PROBABILITY column contains the probability of each attribute value, as calculated for this node only.</span></span> <span data-ttu-id="a3a16-315">如需 NODE_DISTRIBUTION 資料表所用詞彙的一般定義，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a3a16-315">For general definitions of terms used in the NODE_DISTRIBUTION table, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
###  <a name="information-in-the-marginal-statistics-node"></a><a name="bkmk_margstats"></a> <span data-ttu-id="a3a16-316">臨界統計資料節點中的資訊</span><span class="sxs-lookup"><span data-stu-id="a3a16-316">Information in the Marginal Statistics Node</span></span>  
 <span data-ttu-id="a3a16-317">在貝式機率分類模型中，臨界統計資料節點的巢狀資料表包含整組定型資料的值分佈。</span><span class="sxs-lookup"><span data-stu-id="a3a16-317">In a Naive Bayes model, the nested table for the marginal statistics node contains the distribution of values for the entire set of training data.</span></span> <span data-ttu-id="a3a16-318">例如，下表包含模型 `TM_NaiveBayes`的巢狀 NODE_DISTRIBUTION 資料表中，統計資料的部分清單：</span><span class="sxs-lookup"><span data-stu-id="a3a16-318">For example, the following table contains a partial list of the statistics in the nested NODE_DISTRIBUTION table for the model, `TM_NaiveBayes`:</span></span>  
  
|<span data-ttu-id="a3a16-319">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3a16-319">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a3a16-320">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a3a16-320">ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a3a16-321">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a3a16-321">SUPPORT</span></span>|<span data-ttu-id="a3a16-322">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a3a16-322">PROBABILITY</span></span>|<span data-ttu-id="a3a16-323">variance</span><span class="sxs-lookup"><span data-stu-id="a3a16-323">VARIANCE</span></span>|<span data-ttu-id="a3a16-324">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a3a16-324">VALUETYPE</span></span>|  
|---------------------|----------------------|-------------|-----------------|--------------|---------------|  
|<span data-ttu-id="a3a16-325">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a3a16-325">Bike Buyer</span></span>|<span data-ttu-id="a3a16-326">Missing</span><span class="sxs-lookup"><span data-stu-id="a3a16-326">Missing</span></span>|<span data-ttu-id="a3a16-327">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-327">0</span></span>|<span data-ttu-id="a3a16-328">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-328">0</span></span>|<span data-ttu-id="a3a16-329">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-329">0</span></span>|<span data-ttu-id="a3a16-330">1</span><span class="sxs-lookup"><span data-stu-id="a3a16-330">1</span></span>|  
|<span data-ttu-id="a3a16-331">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a3a16-331">Bike Buyer</span></span>|<span data-ttu-id="a3a16-332">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-332">0</span></span>|<span data-ttu-id="a3a16-333">8869</span><span class="sxs-lookup"><span data-stu-id="a3a16-333">8869</span></span>|<span data-ttu-id="a3a16-334">0.507263784</span><span class="sxs-lookup"><span data-stu-id="a3a16-334">0.507263784</span></span>|<span data-ttu-id="a3a16-335">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-335">0</span></span>|<span data-ttu-id="a3a16-336">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-336">4</span></span>|  
|<span data-ttu-id="a3a16-337">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a3a16-337">Bike Buyer</span></span>|<span data-ttu-id="a3a16-338">1</span><span class="sxs-lookup"><span data-stu-id="a3a16-338">1</span></span>|<span data-ttu-id="a3a16-339">8615</span><span class="sxs-lookup"><span data-stu-id="a3a16-339">8615</span></span>|<span data-ttu-id="a3a16-340">0.492736216</span><span class="sxs-lookup"><span data-stu-id="a3a16-340">0.492736216</span></span>|<span data-ttu-id="a3a16-341">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-341">0</span></span>|<span data-ttu-id="a3a16-342">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-342">4</span></span>|  
|<span data-ttu-id="a3a16-343">Marital Status</span><span class="sxs-lookup"><span data-stu-id="a3a16-343">Marital Status</span></span>|<span data-ttu-id="a3a16-344">Missing</span><span class="sxs-lookup"><span data-stu-id="a3a16-344">Missing</span></span>|<span data-ttu-id="a3a16-345">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-345">0</span></span>|<span data-ttu-id="a3a16-346">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-346">0</span></span>|<span data-ttu-id="a3a16-347">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-347">0</span></span>|<span data-ttu-id="a3a16-348">1</span><span class="sxs-lookup"><span data-stu-id="a3a16-348">1</span></span>|  
|<span data-ttu-id="a3a16-349">Marital Status</span><span class="sxs-lookup"><span data-stu-id="a3a16-349">Marital Status</span></span>|<span data-ttu-id="a3a16-350">S</span><span class="sxs-lookup"><span data-stu-id="a3a16-350">S</span></span>|<span data-ttu-id="a3a16-351">7999</span><span class="sxs-lookup"><span data-stu-id="a3a16-351">7999</span></span>|<span data-ttu-id="a3a16-352">0.457504004</span><span class="sxs-lookup"><span data-stu-id="a3a16-352">0.457504004</span></span>|<span data-ttu-id="a3a16-353">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-353">0</span></span>|<span data-ttu-id="a3a16-354">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-354">4</span></span>|  
|<span data-ttu-id="a3a16-355">Marital Status</span><span class="sxs-lookup"><span data-stu-id="a3a16-355">Marital Status</span></span>|<span data-ttu-id="a3a16-356">M</span><span class="sxs-lookup"><span data-stu-id="a3a16-356">M</span></span>|<span data-ttu-id="a3a16-357">9485</span><span class="sxs-lookup"><span data-stu-id="a3a16-357">9485</span></span>|<span data-ttu-id="a3a16-358">0.542495996</span><span class="sxs-lookup"><span data-stu-id="a3a16-358">0.542495996</span></span>|<span data-ttu-id="a3a16-359">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-359">0</span></span>|<span data-ttu-id="a3a16-360">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-360">4</span></span>|  
|<span data-ttu-id="a3a16-361">Total Children</span><span class="sxs-lookup"><span data-stu-id="a3a16-361">Total Children</span></span>|<span data-ttu-id="a3a16-362">Missing</span><span class="sxs-lookup"><span data-stu-id="a3a16-362">Missing</span></span>|<span data-ttu-id="a3a16-363">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-363">0</span></span>|<span data-ttu-id="a3a16-364">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-364">0</span></span>|<span data-ttu-id="a3a16-365">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-365">0</span></span>|<span data-ttu-id="a3a16-366">1</span><span class="sxs-lookup"><span data-stu-id="a3a16-366">1</span></span>|  
|<span data-ttu-id="a3a16-367">Total Children</span><span class="sxs-lookup"><span data-stu-id="a3a16-367">Total Children</span></span>|<span data-ttu-id="a3a16-368">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-368">0</span></span>|<span data-ttu-id="a3a16-369">4865</span><span class="sxs-lookup"><span data-stu-id="a3a16-369">4865</span></span>|<span data-ttu-id="a3a16-370">0.278254404</span><span class="sxs-lookup"><span data-stu-id="a3a16-370">0.278254404</span></span>|<span data-ttu-id="a3a16-371">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-371">0</span></span>|<span data-ttu-id="a3a16-372">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-372">4</span></span>|  
|<span data-ttu-id="a3a16-373">Total Children</span><span class="sxs-lookup"><span data-stu-id="a3a16-373">Total Children</span></span>|<span data-ttu-id="a3a16-374">3</span><span class="sxs-lookup"><span data-stu-id="a3a16-374">3</span></span>|<span data-ttu-id="a3a16-375">2093</span><span class="sxs-lookup"><span data-stu-id="a3a16-375">2093</span></span>|<span data-ttu-id="a3a16-376">0.119709449</span><span class="sxs-lookup"><span data-stu-id="a3a16-376">0.119709449</span></span>|<span data-ttu-id="a3a16-377">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-377">0</span></span>|<span data-ttu-id="a3a16-378">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-378">4</span></span>|  
|<span data-ttu-id="a3a16-379">Total Children</span><span class="sxs-lookup"><span data-stu-id="a3a16-379">Total Children</span></span>|<span data-ttu-id="a3a16-380">1</span><span class="sxs-lookup"><span data-stu-id="a3a16-380">1</span></span>|<span data-ttu-id="a3a16-381">3406</span><span class="sxs-lookup"><span data-stu-id="a3a16-381">3406</span></span>|<span data-ttu-id="a3a16-382">0.19480668</span><span class="sxs-lookup"><span data-stu-id="a3a16-382">0.19480668</span></span>|<span data-ttu-id="a3a16-383">0</span><span class="sxs-lookup"><span data-stu-id="a3a16-383">0</span></span>|<span data-ttu-id="a3a16-384">4</span><span class="sxs-lookup"><span data-stu-id="a3a16-384">4</span></span>|  
  
 <span data-ttu-id="a3a16-385">包含 `Bike Buyer` 資料行，因為臨界統計資料節點永遠包含可預測屬性及其可能值的描述。</span><span class="sxs-lookup"><span data-stu-id="a3a16-385">The `Bike Buyer` column is included because the marginal statistics node always contains a description of the predictable attribute and its possible values.</span></span> <span data-ttu-id="a3a16-386">列出的其他所有資料行代表輸入屬性，以及模型中所使用的值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-386">All other columns that are listed represent input attributes, together with the values that were used in the model.</span></span> <span data-ttu-id="a3a16-387">值只能是遺失、離散或離散化。</span><span class="sxs-lookup"><span data-stu-id="a3a16-387">Values can only be missing, discrete or discretized.</span></span>  
  
 <span data-ttu-id="a3a16-388">在貝式機率分類模型中，可能沒有連續屬性，因此，所有數值資料都會以離散 (VALUE_TYPE = 4) 或離散化 (VALUE_TYPE = 5) 代表。</span><span class="sxs-lookup"><span data-stu-id="a3a16-388">In a Naive Bayes model, there can be no continuous attributes; therefore, all numeric data is represented as either discrete (VALUE_TYPE = 4) or discretized (VALUE_TYPE = 5).</span></span>  
  
 <span data-ttu-id="a3a16-389"> 值 (VALUE_TYPE = 1) 會加入到每個輸入和輸出屬性，以代表不在定型資料中的可能值。</span><span class="sxs-lookup"><span data-stu-id="a3a16-389">A `Missing` value (VALUE_TYPE = 1) is added to every input and output attribute to represent potential values that were not present in the training data.</span></span> <span data-ttu-id="a3a16-390">您必須仔細區別字串「遺失」和預設 `Missing` 值「遺失」。</span><span class="sxs-lookup"><span data-stu-id="a3a16-390">You must be careful to distinguish between "missing" as a string and the default `Missing` value.</span></span> <span data-ttu-id="a3a16-391">如需詳細資訊，請參閱 [遺漏值 &#40;Analysis Services - 資料採礦&#41;](missing-values-analysis-services-data-mining.md)預先定義的模型旗標外，協力廠商外掛程式也可能擁有其他的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="a3a16-391">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a16-392">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3a16-392">See Also</span></span>  
 <span data-ttu-id="a3a16-393">[&#40;Analysis Services 的採礦模型內容-資料採礦&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a3a16-393">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a3a16-394">[資料採礦模型檢視器](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="a3a16-394">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 <span data-ttu-id="a3a16-395">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="a3a16-395">[Data Mining Queries](data-mining-queries.md) </span></span>  
 [<span data-ttu-id="a3a16-396">Microsoft 貝氏機率分類演算法</span><span class="sxs-lookup"><span data-stu-id="a3a16-396">Microsoft Naive Bayes Algorithm</span></span>](microsoft-naive-bayes-algorithm.md)  
  
  
