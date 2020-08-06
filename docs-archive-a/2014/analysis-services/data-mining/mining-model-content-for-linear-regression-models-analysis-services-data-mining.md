---
title: 線性回歸模型的採礦模型內容 (Analysis Services 資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- mining model content, linear regression models
- regression algorithms [Analysis Services]
ms.assetid: a6abcb75-524e-4e0a-a375-c10475ac0a9d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cb41cf0053f236b4bda8d4520030603a391d1c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702166"
---
# <a name="mining-model-content-for-linear-regression-models-analysis-services---data-mining"></a><span data-ttu-id="a9a86-102">線性迴歸模型的採礦模型內容 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="a9a86-102">Mining Model Content for Linear Regression Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="a9a86-103">本主題描述使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線性迴歸演算法的模型專用的採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="a9a86-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span> <span data-ttu-id="a9a86-104">如需適用於所有模型類型的一般採礦模型內容說明，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a86-104">For a general explanation of mining model content for all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-linear-regression-model"></a><span data-ttu-id="a9a86-105">了解線性迴歸模型的結構</span><span class="sxs-lookup"><span data-stu-id="a9a86-105">Understanding the Structure of a Linear Regression Model</span></span>  
 <span data-ttu-id="a9a86-106">線性迴歸模型的結構相當簡單。</span><span class="sxs-lookup"><span data-stu-id="a9a86-106">A linear regression model has an extremely simple structure.</span></span> <span data-ttu-id="a9a86-107">每個模型都有一個代表模型及其中繼資料的單一父節點，以及一個包含每個可預測屬性之回歸公式的迴歸樹狀結構節點 (NODE_TYPE = 25) 。</span><span class="sxs-lookup"><span data-stu-id="a9a86-107">Each model has a single parent node that represents the model and its metadata, and a regression tree node (NODE_TYPE = 25) that contains the regression formula for each predictable attribute.</span></span>  
  
 <span data-ttu-id="a9a86-108">![線性迴歸的模型結構](../media/modelcontentstructure-linreg.gif "線性迴歸的模型結構")</span><span class="sxs-lookup"><span data-stu-id="a9a86-108">![Structure of model for linear regression](../media/modelcontentstructure-linreg.gif "Structure of model for linear regression")</span></span>  
  
 <span data-ttu-id="a9a86-109">線性迴歸模型使用與 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹相同的演算法，但是使用不同的參數來限制樹狀結構，而且只有連續的屬性會當作輸入接受。</span><span class="sxs-lookup"><span data-stu-id="a9a86-109">Linear regression models use the same algorithm as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees, but different parameters are used to constrain the tree, and only continuous attributes are accepted as inputs.</span></span> <span data-ttu-id="a9a86-110">不過，線性迴歸模式是以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法為基礎；因此，線性迴歸模型會使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹檢視器顯示。</span><span class="sxs-lookup"><span data-stu-id="a9a86-110">However, because linear regression models are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm, linear regression models are displayed by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Tree Viewer.</span></span> <span data-ttu-id="a9a86-111">如需相關資訊，請參閱 [使用 Microsoft 樹狀檢視器瀏覽模型](browse-a-model-using-the-microsoft-tree-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a86-111">For information, see [Browse a Model Using the Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="a9a86-112">下節說明如何解譯迴歸公式節點中的資訊。</span><span class="sxs-lookup"><span data-stu-id="a9a86-112">The next section explains how to interpret information in the regression formula node.</span></span> <span data-ttu-id="a9a86-113">此資訊不僅適用於線性迴歸模型，也適用於部分樹狀結構中包含迴歸的決策樹模型。</span><span class="sxs-lookup"><span data-stu-id="a9a86-113">This information applies not only to linear regression models, but also to decision trees models that contain regressions in a portion of the tree.</span></span>  
  
## <a name="model-content-for-a-linear-regression-model"></a><span data-ttu-id="a9a86-114">線性迴歸模型的模型內容</span><span class="sxs-lookup"><span data-stu-id="a9a86-114">Model Content for a Linear Regression Model</span></span>  
 <span data-ttu-id="a9a86-115">本節僅針對採礦模型內容中與線性迴歸具有特定相關的資料行，提供詳細資料和範例。</span><span class="sxs-lookup"><span data-stu-id="a9a86-115">This section provides detail and examples only for those columns in the mining model content that have particular relevance for linear regression.</span></span>  
  
 <span data-ttu-id="a9a86-116">如需結構描述資料列集中一般用途資料行的資訊，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a86-116">For information about general-purpose columns in the schema rowset, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="a9a86-117">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a9a86-117">MODEL_CATALOG</span></span>  
 <span data-ttu-id="a9a86-118">模型儲存位置所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9a86-118">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="a9a86-119">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="a9a86-119">MODEL_NAME</span></span>  
 <span data-ttu-id="a9a86-120">模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9a86-120">Name of the model.</span></span>  
  
 <span data-ttu-id="a9a86-121">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a9a86-121">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="a9a86-122">**根節點** ：空白</span><span class="sxs-lookup"><span data-stu-id="a9a86-122">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="a9a86-123">**迴歸節點** ：可預測屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9a86-123">**Regression node:** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a9a86-124">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="a9a86-124">NODE_NAME</span></span>  
 <span data-ttu-id="a9a86-125">永遠與 NODE_UNIQUE_NAME 相同。</span><span class="sxs-lookup"><span data-stu-id="a9a86-125">Always same as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="a9a86-126">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a9a86-126">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="a9a86-127">節點在模型內的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="a9a86-127">A unique identifier for the node within the model.</span></span> <span data-ttu-id="a9a86-128">這項值不能被改變。</span><span class="sxs-lookup"><span data-stu-id="a9a86-128">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="a9a86-129">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a9a86-129">NODE_TYPE</span></span>  
 <span data-ttu-id="a9a86-130">線性迴歸模型會輸出下列節點類型：</span><span class="sxs-lookup"><span data-stu-id="a9a86-130">A linear regression model outputs the following node types:</span></span>  
  
|<span data-ttu-id="a9a86-131">節點類型識別碼</span><span class="sxs-lookup"><span data-stu-id="a9a86-131">Node Type ID</span></span>|<span data-ttu-id="a9a86-132">類型</span><span class="sxs-lookup"><span data-stu-id="a9a86-132">Type</span></span>|<span data-ttu-id="a9a86-133">描述</span><span class="sxs-lookup"><span data-stu-id="a9a86-133">Description</span></span>|  
|------------------|----------|-----------------|  
|<span data-ttu-id="a9a86-134">25</span><span class="sxs-lookup"><span data-stu-id="a9a86-134">25</span></span>|<span data-ttu-id="a9a86-135">迴歸樹根節點</span><span class="sxs-lookup"><span data-stu-id="a9a86-135">Regression tree root</span></span>|<span data-ttu-id="a9a86-136">包含描述輸入和輸出變數之間關聯性的公式。</span><span class="sxs-lookup"><span data-stu-id="a9a86-136">Contains the formula that describes the relationship between the input and output variable.</span></span>|  
  
 <span data-ttu-id="a9a86-137">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a9a86-137">NODE_CAPTION</span></span>  
 <span data-ttu-id="a9a86-138">與節點關聯的標籤或標題。</span><span class="sxs-lookup"><span data-stu-id="a9a86-138">A label or a caption associated with the node.</span></span> <span data-ttu-id="a9a86-139">這個屬性主要是供顯示之用。</span><span class="sxs-lookup"><span data-stu-id="a9a86-139">This property is primarily for display purposes.</span></span>  
  
 <span data-ttu-id="a9a86-140">**根節點** ：空白</span><span class="sxs-lookup"><span data-stu-id="a9a86-140">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="a9a86-141">**迴歸節點** ：全部。</span><span class="sxs-lookup"><span data-stu-id="a9a86-141">**Regression node:** All.</span></span>  
  
 <span data-ttu-id="a9a86-142">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="a9a86-142">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="a9a86-143">節點所擁有子系數目的估計。</span><span class="sxs-lookup"><span data-stu-id="a9a86-143">An estimate of the number of children that the node has.</span></span>  
  
 <span data-ttu-id="a9a86-144">**根節點** ：指出迴歸節點的數目。</span><span class="sxs-lookup"><span data-stu-id="a9a86-144">**Root node:** Indicates the number of regression nodes.</span></span> <span data-ttu-id="a9a86-145">在模型中，每個可預測的屬性都會建立一個迴歸節點。</span><span class="sxs-lookup"><span data-stu-id="a9a86-145">One regression node is created for each predictable attribute in the model.</span></span>  
  
 <span data-ttu-id="a9a86-146">**迴歸節點** ：一律為 0。</span><span class="sxs-lookup"><span data-stu-id="a9a86-146">**Regression node:** Always 0.</span></span>  
  
 <span data-ttu-id="a9a86-147">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a9a86-147">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="a9a86-148">節點之父系的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="a9a86-148">The unique name of the node's parent.</span></span> <span data-ttu-id="a9a86-149">任何根層級的節點都會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="a9a86-149">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="a9a86-150">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a9a86-150">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="a9a86-151">節點的描述。</span><span class="sxs-lookup"><span data-stu-id="a9a86-151">A description of the node.</span></span>  
  
 <span data-ttu-id="a9a86-152">**根節點** ：空白</span><span class="sxs-lookup"><span data-stu-id="a9a86-152">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="a9a86-153">**迴歸節點** ：全部。</span><span class="sxs-lookup"><span data-stu-id="a9a86-153">**Regression node:** All.</span></span>  
  
 <span data-ttu-id="a9a86-154">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="a9a86-154">NODE_RULE</span></span>  
 <span data-ttu-id="a9a86-155">未用於線性迴歸模型。</span><span class="sxs-lookup"><span data-stu-id="a9a86-155">Not used for linear regression models.</span></span>  
  
 <span data-ttu-id="a9a86-156">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="a9a86-156">MARGINAL_RULE</span></span>  
 <span data-ttu-id="a9a86-157">未用於線性迴歸模型。</span><span class="sxs-lookup"><span data-stu-id="a9a86-157">Not used for linear regression models.</span></span>  
  
 <span data-ttu-id="a9a86-158">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a9a86-158">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="a9a86-159">與此節點關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="a9a86-159">The probability associated with this node.</span></span>  
  
 <span data-ttu-id="a9a86-160">**根節點** ：0</span><span class="sxs-lookup"><span data-stu-id="a9a86-160">**Root node:** 0</span></span>  
  
 <span data-ttu-id="a9a86-161">**迴歸節點** ：1</span><span class="sxs-lookup"><span data-stu-id="a9a86-161">**Regression node:** 1</span></span>  
  
 <span data-ttu-id="a9a86-162">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a9a86-162">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="a9a86-163">從父節點到達節點的機率。</span><span class="sxs-lookup"><span data-stu-id="a9a86-163">The probability of reaching the node from the parent node.</span></span>  
  
 <span data-ttu-id="a9a86-164">**根節點** ：0</span><span class="sxs-lookup"><span data-stu-id="a9a86-164">**Root node:** 0</span></span>  
  
 <span data-ttu-id="a9a86-165">**迴歸節點** ：1</span><span class="sxs-lookup"><span data-stu-id="a9a86-165">**Regression node:** 1</span></span>  
  
 <span data-ttu-id="a9a86-166">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="a9a86-166">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="a9a86-167">提供節點中關於值之統計資料的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="a9a86-167">A nested table that provides statistics about the values in the node.</span></span>  
  
 <span data-ttu-id="a9a86-168">**根節點** ：0</span><span class="sxs-lookup"><span data-stu-id="a9a86-168">**Root node:** 0</span></span>  
  
 <span data-ttu-id="a9a86-169">**迴歸節點** ：包含建立迴歸公式所使用之元素的資料表。</span><span class="sxs-lookup"><span data-stu-id="a9a86-169">**Regression node:** A table that contains the elements used to build the regression formula.</span></span> <span data-ttu-id="a9a86-170">迴歸節點包含下列值類型：</span><span class="sxs-lookup"><span data-stu-id="a9a86-170">A regression node contains the following value types:</span></span>  
  
|<span data-ttu-id="a9a86-171">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a9a86-171">VALUETYPE</span></span>|  
|---------------|  
|<span data-ttu-id="a9a86-172">1 (遺漏)</span><span class="sxs-lookup"><span data-stu-id="a9a86-172">1 (Missing)</span></span>|  
|<span data-ttu-id="a9a86-173">3 (連續)</span><span class="sxs-lookup"><span data-stu-id="a9a86-173">3 (Continuous)</span></span>|  
|<span data-ttu-id="a9a86-174">7 (係數)</span><span class="sxs-lookup"><span data-stu-id="a9a86-174">7 (Coefficient)</span></span>|  
|<span data-ttu-id="a9a86-175">8 (得分)</span><span class="sxs-lookup"><span data-stu-id="a9a86-175">8 (Score Gain)</span></span>|  
|<span data-ttu-id="a9a86-176">9 (統計資料)</span><span class="sxs-lookup"><span data-stu-id="a9a86-176">9 (Statistics)</span></span>|  
|<span data-ttu-id="a9a86-177">11 (截距)</span><span class="sxs-lookup"><span data-stu-id="a9a86-177">11 (Intercept)</span></span>|  
  
 <span data-ttu-id="a9a86-178">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a9a86-178">NODE_SUPPORT</span></span>  
 <span data-ttu-id="a9a86-179">支援這個節點的案例數目。</span><span class="sxs-lookup"><span data-stu-id="a9a86-179">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="a9a86-180">**根節點** ：0</span><span class="sxs-lookup"><span data-stu-id="a9a86-180">**Root node:** 0</span></span>  
  
 <span data-ttu-id="a9a86-181">**迴歸節點** ：定型案例的計數。</span><span class="sxs-lookup"><span data-stu-id="a9a86-181">**Regression node:** Count of training cases.</span></span>  
  
 <span data-ttu-id="a9a86-182">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="a9a86-182">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="a9a86-183">可預測屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9a86-183">Name of predictable attribute.</span></span>  
  
 <span data-ttu-id="a9a86-184">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="a9a86-184">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="a9a86-185">與 NODE_PROBABILITY 相同</span><span class="sxs-lookup"><span data-stu-id="a9a86-185">Same as NODE_PROBABILITY</span></span>  
  
 <span data-ttu-id="a9a86-186">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a9a86-186">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="a9a86-187">用於顯示用途的標籤。</span><span class="sxs-lookup"><span data-stu-id="a9a86-187">Label used for display purposes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9a86-188">備註</span><span class="sxs-lookup"><span data-stu-id="a9a86-188">Remarks</span></span>  
 <span data-ttu-id="a9a86-189">當您使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線性迴歸演算法建立模型時，資料採礦引擎會建立一個特殊的決策樹模型執行個體，並提供包含樹狀結構的參數以便將所有定型資料包含在單一節點中。</span><span class="sxs-lookup"><span data-stu-id="a9a86-189">When you create a model by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, the data mining engine creates a special instance of a decision trees model and supplies parameters that constrain the tree to contain all the training data in a single node.</span></span> <span data-ttu-id="a9a86-190">所有連續輸入都會加上旗標，並評估為潛在的迴歸輸入變數，但只有符合資料的迴歸輸入變數會保留為最終模型中的迴歸輸入變數。</span><span class="sxs-lookup"><span data-stu-id="a9a86-190">All continuous inputs are flagged and evaluated as potential regressors, but only those regressors that fit the data are retained as regressors in the final model.</span></span> <span data-ttu-id="a9a86-191">此分析會針對每個迴歸輸入變數產生單一的迴歸公式，或不產生任何迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="a9a86-191">The analysis produces either a single regression formula for each regressor or no regression formula at all.</span></span>  
  
 <span data-ttu-id="a9a86-192">您可以按一下 [[Microsoft 樹狀檢視器]](browse-a-model-using-the-microsoft-tree-viewer.md) 中的 [(全部)]\*\*\*\* 節點，檢視 [採礦圖例]\*\*\*\* 中的完整迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="a9a86-192">You can view the complete regression formula in the **Mining Legend**, by clicking the **(All)** node in the [Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="a9a86-193">同時，當您建立包含連續可預測屬性的決策樹模型時，有時候樹狀結構所擁有的迴歸節點會共用迴歸樹根節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="a9a86-193">Also, when you create a decision trees model that includes a continuous predictable attribute, sometimes the tree has regression nodes that share the properties of regression tree nodes.</span></span>  
  
##  <a name="node-distribution-for-continuous-attributes"></a><a name="NodeDist_Regression"></a><span data-ttu-id="a9a86-194">連續屬性的節點分佈</span><span class="sxs-lookup"><span data-stu-id="a9a86-194">Node Distribution for Continuous Attributes</span></span>  
 <span data-ttu-id="a9a86-195">迴歸節點中大部分重要的資訊都包含在 NODE_DISTRIBUTION 資料表中。</span><span class="sxs-lookup"><span data-stu-id="a9a86-195">Most of the important information in a regression node is contained in the NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="a9a86-196">下列範例說明 NODE_DISTRIBUTION 資料表的配置。</span><span class="sxs-lookup"><span data-stu-id="a9a86-196">The following example illustrates the layout of the NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="a9a86-197">在此範例中，已使用目標郵寄採礦結構建立線性迴歸模型，根據年齡預測客戶收入。</span><span class="sxs-lookup"><span data-stu-id="a9a86-197">In this example, the Targeted Mailing mining structure has been used to create a linear regression model that predicts customer income based on age.</span></span> <span data-ttu-id="a9a86-198">此模型僅用於說明，因為該模型可以使用現有的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 範例資料和採礦結構輕鬆建立。</span><span class="sxs-lookup"><span data-stu-id="a9a86-198">The model is for the purpose of illustration only, because it can be built easily using the existing [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample data and mining structure.</span></span>  
  
|<span data-ttu-id="a9a86-199">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a9a86-199">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a9a86-200">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a9a86-200">ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a9a86-201">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a9a86-201">SUPPORT</span></span>|<span data-ttu-id="a9a86-202">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a9a86-202">PROBABILITY</span></span>|<span data-ttu-id="a9a86-203">variance</span><span class="sxs-lookup"><span data-stu-id="a9a86-203">VARIANCE</span></span>|<span data-ttu-id="a9a86-204">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a9a86-204">VALUETYPE</span></span>|  
|---------------------|----------------------|-------------|-----------------|--------------|---------------|  
|<span data-ttu-id="a9a86-205">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="a9a86-205">Yearly Income</span></span>|<span data-ttu-id="a9a86-206">Missing</span><span class="sxs-lookup"><span data-stu-id="a9a86-206">Missing</span></span>|<span data-ttu-id="a9a86-207">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-207">0</span></span>|<span data-ttu-id="a9a86-208">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="a9a86-208">0.000457142857142857</span></span>|<span data-ttu-id="a9a86-209">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-209">0</span></span>|<span data-ttu-id="a9a86-210">1</span><span class="sxs-lookup"><span data-stu-id="a9a86-210">1</span></span>|  
|<span data-ttu-id="a9a86-211">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="a9a86-211">Yearly Income</span></span>|<span data-ttu-id="a9a86-212">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="a9a86-212">57220.8876687257</span></span>|<span data-ttu-id="a9a86-213">17484</span><span class="sxs-lookup"><span data-stu-id="a9a86-213">17484</span></span>|<span data-ttu-id="a9a86-214">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="a9a86-214">0.999542857142857</span></span>|<span data-ttu-id="a9a86-215">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="a9a86-215">1041275619.52776</span></span>|<span data-ttu-id="a9a86-216">3</span><span class="sxs-lookup"><span data-stu-id="a9a86-216">3</span></span>|  
|<span data-ttu-id="a9a86-217">年齡</span><span class="sxs-lookup"><span data-stu-id="a9a86-217">Age</span></span>|<span data-ttu-id="a9a86-218">471.687717702463</span><span class="sxs-lookup"><span data-stu-id="a9a86-218">471.687717702463</span></span>|<span data-ttu-id="a9a86-219">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-219">0</span></span>|<span data-ttu-id="a9a86-220">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-220">0</span></span>|<span data-ttu-id="a9a86-221">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="a9a86-221">126.969442359327</span></span>|<span data-ttu-id="a9a86-222">7</span><span class="sxs-lookup"><span data-stu-id="a9a86-222">7</span></span>|  
|<span data-ttu-id="a9a86-223">年齡</span><span class="sxs-lookup"><span data-stu-id="a9a86-223">Age</span></span>|<span data-ttu-id="a9a86-224">234.680904692439</span><span class="sxs-lookup"><span data-stu-id="a9a86-224">234.680904692439</span></span>|<span data-ttu-id="a9a86-225">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-225">0</span></span>|<span data-ttu-id="a9a86-226">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-226">0</span></span>|<span data-ttu-id="a9a86-227">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-227">0</span></span>|<span data-ttu-id="a9a86-228">8</span><span class="sxs-lookup"><span data-stu-id="a9a86-228">8</span></span>|  
|<span data-ttu-id="a9a86-229">年齡</span><span class="sxs-lookup"><span data-stu-id="a9a86-229">Age</span></span>|<span data-ttu-id="a9a86-230">45.4269617936399</span><span class="sxs-lookup"><span data-stu-id="a9a86-230">45.4269617936399</span></span>|<span data-ttu-id="a9a86-231">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-231">0</span></span>|<span data-ttu-id="a9a86-232">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-232">0</span></span>|<span data-ttu-id="a9a86-233">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="a9a86-233">126.969442359327</span></span>|<span data-ttu-id="a9a86-234">9</span><span class="sxs-lookup"><span data-stu-id="a9a86-234">9</span></span>|  
||<span data-ttu-id="a9a86-235">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="a9a86-235">35793.5477381267</span></span>|<span data-ttu-id="a9a86-236">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-236">0</span></span>|<span data-ttu-id="a9a86-237">0</span><span class="sxs-lookup"><span data-stu-id="a9a86-237">0</span></span>|<span data-ttu-id="a9a86-238">1012968919.28372</span><span class="sxs-lookup"><span data-stu-id="a9a86-238">1012968919.28372</span></span>|<span data-ttu-id="a9a86-239">11</span><span class="sxs-lookup"><span data-stu-id="a9a86-239">11</span></span>|  
  
 <span data-ttu-id="a9a86-240">NODE_DISTRIBUTION 資料表包含多個資料列，每個資料列都會依照變數分組。</span><span class="sxs-lookup"><span data-stu-id="a9a86-240">The NODE_DISTRIBUTION table contains multiple rows, each grouped by a variable.</span></span> <span data-ttu-id="a9a86-241">前兩個資料列的值類型永遠是 1 和 3，而且會描述目標屬性。</span><span class="sxs-lookup"><span data-stu-id="a9a86-241">The first two rows are always value types 1 and 3, and describe the target attribute.</span></span> <span data-ttu-id="a9a86-242">之後的資料列會提供特定「迴歸輸入變數」\*\* 公式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a9a86-242">The succeeding rows provide details about the formula for a particular *regressor*.</span></span> <span data-ttu-id="a9a86-243">迴歸輸入變數是一種輸入變數，其中包含與輸出變數的線性關聯性。</span><span class="sxs-lookup"><span data-stu-id="a9a86-243">A regressor is an input variable that has a linear relationship with the output variable.</span></span> <span data-ttu-id="a9a86-244">您可以擁有多個迴歸輸入變數，而且每個迴歸輸入變數對於係數 (VALUETYPE = 7)、得分 (VALUETYPE = 8) 以及統計資料 (VALUETYPE = 9) 都有個別的資料列。</span><span class="sxs-lookup"><span data-stu-id="a9a86-244">You can have multiple regressors, and each regressor will have a separate row for the coefficient (VALUETYPE = 7), score gain (VALUETYPE = 8), and statistics (VALUETYPE = 9).</span></span> <span data-ttu-id="a9a86-245">最後，資料表所擁有的資料列包含方程式的截距 (VALUETYPE = 11)。</span><span class="sxs-lookup"><span data-stu-id="a9a86-245">Finally, the table has a row that contains the intercept of the equation (VALUETYPE = 11).</span></span>  
  
### <a name="elements-of-the-regression-formula"></a><span data-ttu-id="a9a86-246">迴歸公式的元素</span><span class="sxs-lookup"><span data-stu-id="a9a86-246">Elements of the Regression Formula</span></span>  
 <span data-ttu-id="a9a86-247">NODE_DISTRIBUTION 巢狀資料表在個別的資料列中，包含迴歸公式的每個元素。</span><span class="sxs-lookup"><span data-stu-id="a9a86-247">The nested NODE_DISTRIBUTION table contains each element of the regression formula in a separate row.</span></span> <span data-ttu-id="a9a86-248">範例結果中資料的前兩個資料列包含可預測屬性 [年收入]\*\*\*\* 的資訊，該屬性會製作相依變數的模型。</span><span class="sxs-lookup"><span data-stu-id="a9a86-248">The first two rows of data in the example results contain information about the predictable attribute, **Yearly Income**, which models the dependent variable.</span></span> <span data-ttu-id="a9a86-249">SUPPORT 資料行會顯示支援此屬性兩個狀態之案例的計數：提供 [年收入]\*\*\*\* 值，或遺漏 [年收入]\*\*\*\* 值。</span><span class="sxs-lookup"><span data-stu-id="a9a86-249">The SUPPORT column shows the count of cases in support of the two states of this attribute: either a **Yearly Income** value was available, or the **Yearly Income** value was missing.</span></span>  
  
 <span data-ttu-id="a9a86-250">VARIANCE 資料行會告訴您可預測屬性的計算變異數。</span><span class="sxs-lookup"><span data-stu-id="a9a86-250">The VARIANCE column tells you the computed variance of the predictable attribute.</span></span> <span data-ttu-id="a9a86-251">「變異數」\*\* 是在給定預期分佈的情況下，值如何在範例中散佈的量值。</span><span class="sxs-lookup"><span data-stu-id="a9a86-251">*Variance* is a measure of how scattered the values are in a sample, given an expected distribution.</span></span> <span data-ttu-id="a9a86-252">此處的變異數會透過從平均值取得平方差的平均值來計算。</span><span class="sxs-lookup"><span data-stu-id="a9a86-252">Variance here is calculated by taking the average of the squared deviation from the mean.</span></span> <span data-ttu-id="a9a86-253">變異數的平方根也就是所謂的標準差。</span><span class="sxs-lookup"><span data-stu-id="a9a86-253">The square root of the variance is also known as standard deviation.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a9a86-254">不提供標準差，但是您可以輕易地計算出來。</span><span class="sxs-lookup"><span data-stu-id="a9a86-254">does not provide the standard deviation but you can easily calculate it.</span></span>  
  
 <span data-ttu-id="a9a86-255">對於每個迴歸輸入變數，系統會輸出三個資料列。</span><span class="sxs-lookup"><span data-stu-id="a9a86-255">For each regressor, three rows are output.</span></span> <span data-ttu-id="a9a86-256">這些資料列包含係數、得分以及迴歸輸入變數統計資料。</span><span class="sxs-lookup"><span data-stu-id="a9a86-256">They contain the coefficient, score gain, and regressor statistics.</span></span>  
  
 <span data-ttu-id="a9a86-257">最後，資料表所包含的資料列會提供方程式的截距。</span><span class="sxs-lookup"><span data-stu-id="a9a86-257">Finally, the table contains a row that provides the intercept for the equation.</span></span>  
  
#### <a name="coefficient"></a><span data-ttu-id="a9a86-258">Coefficient</span><span class="sxs-lookup"><span data-stu-id="a9a86-258">Coefficient</span></span>  
 <span data-ttu-id="a9a86-259">每個迴歸輸入變數都會計算出一個係數 (VALUETYPE = 7)。</span><span class="sxs-lookup"><span data-stu-id="a9a86-259">For each regressor, a coefficient (VALUETYPE = 7) is calculated.</span></span> <span data-ttu-id="a9a86-260">係數本身會出現在 ATTRIBUTE_VALUE 資料行中，而 VARIANCE 資料行會告訴您係數的變異數。</span><span class="sxs-lookup"><span data-stu-id="a9a86-260">The coefficient itself appears in the ATTRIBUTE_VALUE column, whereas the VARIANCE column tells you the variance for the coefficient.</span></span> <span data-ttu-id="a9a86-261">系統會計算係數以便將線性最大化。</span><span class="sxs-lookup"><span data-stu-id="a9a86-261">The coefficients are calculated so as to maximize linearity.</span></span>  
  
#### <a name="score-gain"></a><span data-ttu-id="a9a86-262">得分</span><span class="sxs-lookup"><span data-stu-id="a9a86-262">Score Gain</span></span>  
 <span data-ttu-id="a9a86-263">每個迴歸輸入變數的得分 (VALUETYPE = 8) 都代表屬性的有趣性分數。</span><span class="sxs-lookup"><span data-stu-id="a9a86-263">The score gain (VALUETYPE = 8) for each regressor represents the interestingness score of the attribute.</span></span> <span data-ttu-id="a9a86-264">您可以使用這個值估計多個迴歸輸入變數的實用性。</span><span class="sxs-lookup"><span data-stu-id="a9a86-264">You can use this value to estimate the usefulness of multiple regressors.</span></span>  
  
#### <a name="statistics"></a><span data-ttu-id="a9a86-265">統計資料</span><span class="sxs-lookup"><span data-stu-id="a9a86-265">Statistics</span></span>  
 <span data-ttu-id="a9a86-266">迴歸輸入變數統計資料 (VALUETYPE = 9) 是擁有值之案例的屬性平均值。</span><span class="sxs-lookup"><span data-stu-id="a9a86-266">The regressor statistic (VALUETYPE = 9) is the mean for the attribute for cases that have a value.</span></span> <span data-ttu-id="a9a86-267">ATTRIBUTE_VALUE 資料行包含平均值本身，而 VARIANCE 資料行包含平均值偏差的總和。</span><span class="sxs-lookup"><span data-stu-id="a9a86-267">The ATTRIBUTE_VALUE column contains the mean itself, whereas the VARIANCE column contains the sum of deviations from the mean.</span></span>  
  
#### <a name="intercept"></a><span data-ttu-id="a9a86-268">Intercept</span><span class="sxs-lookup"><span data-stu-id="a9a86-268">Intercept</span></span>  
 <span data-ttu-id="a9a86-269">迴歸方程式中的「截距」**(VALUETYPE = 11) 或「剩餘」** 會在輸入屬性所在的點，告訴您可預測屬性的值為 0。</span><span class="sxs-lookup"><span data-stu-id="a9a86-269">Normally, the *intercept* (VALUETYPE = 11) or *residual* in a regression equation tells you the value of the predictable attribute, at the point where the input attribute, is 0.</span></span> <span data-ttu-id="a9a86-270">在許多情況下，這可能不會發生，但是可能會導致反直覺式的結果。</span><span class="sxs-lookup"><span data-stu-id="a9a86-270">In many cases, this might not happen, and could lead to counterintuitive results.</span></span>  
  
 <span data-ttu-id="a9a86-271">例如，在根據年齡預測收入的模型中得知年齡為 0 的收入是毫無用處的。</span><span class="sxs-lookup"><span data-stu-id="a9a86-271">For example, in a model that predicts income based on age, it is useless to learn the income at age 0.</span></span> <span data-ttu-id="a9a86-272">在實際生活中，了解關於平均值的線性行為通常比較實用。</span><span class="sxs-lookup"><span data-stu-id="a9a86-272">In real-life, it is typically more useful to know about the behavior of the line with respect to average values.</span></span> <span data-ttu-id="a9a86-273">因此，會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 修改截距，以表示與平均值關聯性中的每個回歸輸入變數。</span><span class="sxs-lookup"><span data-stu-id="a9a86-273">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] modifies the intercept to express each regressor in a relationship with the mean.</span></span>  
  
 <span data-ttu-id="a9a86-274">這種調整很難在採礦模型內容中看出來，但是如果您在 [Microsoft 樹狀檢視器]\*\*\*\* 的 [採礦圖例]\*\*\*\* 中檢視完整的方程式就很明顯。</span><span class="sxs-lookup"><span data-stu-id="a9a86-274">This adjustment is difficult to see in the mining model content, but is apparent if you view the completed equation in the **Mining Legend** of the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="a9a86-275">迴歸公式會從 0 點移位到代表平均值的點。</span><span class="sxs-lookup"><span data-stu-id="a9a86-275">The regression formula is shifted away from the 0 point to the point that represents the mean.</span></span> <span data-ttu-id="a9a86-276">這會讓目前的資料以更直覺的方式呈現。</span><span class="sxs-lookup"><span data-stu-id="a9a86-276">This presents a view that is more intuitive given the current data.</span></span>  
  
 <span data-ttu-id="a9a86-277">因此，假設平均年齡為 45 歲左右，迴歸公式的截距 (VALUETYPE = 11) 會告訴您平均收入。</span><span class="sxs-lookup"><span data-stu-id="a9a86-277">Therefore, assuming that the mean age is around 45, the intercept (VALUETYPE = 11) for the regression formula tells you the mean income.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a86-278">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9a86-278">See Also</span></span>  
 <span data-ttu-id="a9a86-279">[&#40;Analysis Services 的採礦模型內容-資料採礦&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a9a86-279">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a9a86-280">[Microsoft 線性回歸演算法](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a9a86-280">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="a9a86-281">[Microsoft 線性回歸演算法技術參考](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a9a86-281">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="a9a86-282">線性迴歸模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="a9a86-282">Linear Regression Model Query Examples</span></span>](linear-regression-model-query-examples.md)  
  
  
