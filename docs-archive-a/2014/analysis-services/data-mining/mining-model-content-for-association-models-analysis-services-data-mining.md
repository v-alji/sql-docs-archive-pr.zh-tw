---
title: 關聯模型的採礦模型內容 (Analysis Services 資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- mining model content, association models
- rules [Data Mining]
- associations [Analysis Services]
ms.assetid: d5849bcb-4b8f-4f71-9761-7dc5bb465224
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8904ce155526aee595db19094fd2bad48770e83e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594836"
---
# <a name="mining-model-content-for-association-models-analysis-services---data-mining"></a><span data-ttu-id="be7b1-102">關聯模型的採礦模型內容 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="be7b1-102">Mining Model Content for Association Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="be7b1-103">本主題說明使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則演算法的模型專用的採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="be7b1-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span> <span data-ttu-id="be7b1-104">如需與適用於所有模型類型採礦模型內容相關的一般及統計詞彙說明，請參閱 [採礦模型內容 &amp;#40;Analysis Services - 資料採礦&amp;#41;](mining-model-content-analysis-services-data-mining.md)(採礦模型內容 &#40;Analysis Services - 資料採礦&#41;)。</span><span class="sxs-lookup"><span data-stu-id="be7b1-104">For an explanation of general and statistical terminology related to mining model content that applies to all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-an-association-model"></a><span data-ttu-id="be7b1-105">了解關聯模型的結構</span><span class="sxs-lookup"><span data-stu-id="be7b1-105">Understanding the Structure of an Association Model</span></span>  
 <span data-ttu-id="be7b1-106">關聯模型有簡單的結構。</span><span class="sxs-lookup"><span data-stu-id="be7b1-106">An association model has a simple structure.</span></span> <span data-ttu-id="be7b1-107">每個模型都擁有代表模型及其中繼資料的單一父節點，而每個父節點則擁有項目集和規則的一般清單。</span><span class="sxs-lookup"><span data-stu-id="be7b1-107">Each model has a single parent node that represents the model and its metadata, and each parent node has a flat list of itemsets and rules.</span></span> <span data-ttu-id="be7b1-108">項目集和規則並非組織成樹狀結構，而是先以項目集排列，再以規則排列，如下列圖表所示。</span><span class="sxs-lookup"><span data-stu-id="be7b1-108">The itemsets and rules are not organized in trees, they are ordered with itemsets first and rules next as shown in the following diagram.</span></span>  
  
 <span data-ttu-id="be7b1-109">![關聯模型的模型內容結構](../media/modelcontentstructure-assoc.gif "關聯模型的模型內容結構")</span><span class="sxs-lookup"><span data-stu-id="be7b1-109">![structure of model content for association models](../media/modelcontentstructure-assoc.gif "structure of model content for association models")</span></span>  
  
 <span data-ttu-id="be7b1-110">每個項目集都是包含在其本身的節點中 (NODE_TYPE = 7)。</span><span class="sxs-lookup"><span data-stu-id="be7b1-110">Each itemset is contained in its own node (NODE_TYPE = 7).</span></span> <span data-ttu-id="be7b1-111">「節點」\*\* 包含項目集的定義、包含此項目集的案例數以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="be7b1-111">The *node* includes the definition of the itemset, the number of cases that contain this itemset, and other information.</span></span>  
  
 <span data-ttu-id="be7b1-112">每個規則也會包含在其本身的節點中 (NODE_TYPE = 8)。</span><span class="sxs-lookup"><span data-stu-id="be7b1-112">Each rule is also contained in its own node (NODE_TYPE = 8).</span></span> <span data-ttu-id="be7b1-113">「規則」\*\* 描述項目關聯方式的一般模式。</span><span class="sxs-lookup"><span data-stu-id="be7b1-113">A *rule* describes a general pattern for how items are associated.</span></span> <span data-ttu-id="be7b1-114">規則與 IF - THEN 陳述式類似。</span><span class="sxs-lookup"><span data-stu-id="be7b1-114">A rule is like an IF-THEN statement.</span></span> <span data-ttu-id="be7b1-115">規則的左側顯示現有的條件或條件集；</span><span class="sxs-lookup"><span data-stu-id="be7b1-115">The left-hand side of the rule shows an existing condition or set of conditions.</span></span> <span data-ttu-id="be7b1-116">規則的右側則顯示資料集中通常與左側的條件相關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="be7b1-116">The right-hand side of the rule shows the item in your data set that is usually associated with the conditions on the left side.</span></span>  
  
 <span data-ttu-id="be7b1-117">**注意** 如果想要擷取規則或項目集，您可以使用查詢僅傳回所要的節點類型。</span><span class="sxs-lookup"><span data-stu-id="be7b1-117">**Note** If you want to extract either the rules or the itemsets, you can use a query to return only the node types that you want.</span></span> <span data-ttu-id="be7b1-118">如需詳細資訊，請參閱 [關聯模型查詢範例](association-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="be7b1-118">For more information, see [Association Model Query Examples](association-model-query-examples.md).</span></span>  
  
## <a name="model-content-for-an-association-model"></a><span data-ttu-id="be7b1-119">關聯模型的模型內容</span><span class="sxs-lookup"><span data-stu-id="be7b1-119">Model Content for an Association Model</span></span>  
 <span data-ttu-id="be7b1-120">本章節僅針對採礦模型內容中與關聯模型相關的資料行，提供詳細資料和範例。</span><span class="sxs-lookup"><span data-stu-id="be7b1-120">This section provides detail and examples only for those columns in the mining model content that are relevant for association models.</span></span>  
  
 <span data-ttu-id="be7b1-121">如需結構描述資料列集 (例如，MODEL_CATALOG 和 MODEL_NAME) 中之一般用途資料行的詳細資訊，請參閱 [採礦模型內容 &amp;#40;Analysis Services - 資料採礦&amp;#41;](mining-model-content-analysis-services-data-mining.md)(採礦模型內容 &#40;Analysis Services - 資料採礦&#41;)。</span><span class="sxs-lookup"><span data-stu-id="be7b1-121">For information about the general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="be7b1-122">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="be7b1-122">MODEL_CATALOG</span></span>  
 <span data-ttu-id="be7b1-123">模型儲存位置所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="be7b1-123">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="be7b1-124">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="be7b1-124">MODEL_NAME</span></span>  
 <span data-ttu-id="be7b1-125">模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="be7b1-125">Name of the model.</span></span>  
  
 <span data-ttu-id="be7b1-126">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="be7b1-126">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="be7b1-127">對應至這個節點之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="be7b1-127">The names of the attributes that correspond to this node.</span></span>  
  
 <span data-ttu-id="be7b1-128">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="be7b1-128">NODE_NAME</span></span>  
 <span data-ttu-id="be7b1-129">節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="be7b1-129">The name of the node.</span></span> <span data-ttu-id="be7b1-130">對於關聯模型而言，此資料行包含與 NODE_UNIQUE_NAME 相同的值。</span><span class="sxs-lookup"><span data-stu-id="be7b1-130">For an association model, this column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="be7b1-131">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="be7b1-131">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="be7b1-132">節點的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="be7b1-132">The unique name of the node.</span></span>  
  
 <span data-ttu-id="be7b1-133">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="be7b1-133">NODE_TYPE</span></span>  
 <span data-ttu-id="be7b1-134">關聯模型僅輸出下列節點類型：</span><span class="sxs-lookup"><span data-stu-id="be7b1-134">A association model outputs only the following node types:</span></span>  
  
|<span data-ttu-id="be7b1-135">節點類型識別碼</span><span class="sxs-lookup"><span data-stu-id="be7b1-135">Node Type ID</span></span>|<span data-ttu-id="be7b1-136">類型</span><span class="sxs-lookup"><span data-stu-id="be7b1-136">Type</span></span>|  
|------------------|----------|  
|<span data-ttu-id="be7b1-137">1 (模型)</span><span class="sxs-lookup"><span data-stu-id="be7b1-137">1 (Model)</span></span>|<span data-ttu-id="be7b1-138">根目錄或父節點。</span><span class="sxs-lookup"><span data-stu-id="be7b1-138">Root or parent node.</span></span>|  
|<span data-ttu-id="be7b1-139">7 (項目集)</span><span class="sxs-lookup"><span data-stu-id="be7b1-139">7 (Itemset)</span></span>|<span data-ttu-id="be7b1-140">項目集或屬性值組的集合。</span><span class="sxs-lookup"><span data-stu-id="be7b1-140">An itemset, or collection of attribute-value pairs.</span></span> <span data-ttu-id="be7b1-141">範例：</span><span class="sxs-lookup"><span data-stu-id="be7b1-141">Examples:</span></span><br /><br /> `Product 1 = Existing, Product 2 = Existing`<br /><br /> <span data-ttu-id="be7b1-142">或</span><span class="sxs-lookup"><span data-stu-id="be7b1-142">or</span></span><br /><br /> <span data-ttu-id="be7b1-143">`Gender = Male`.</span><span class="sxs-lookup"><span data-stu-id="be7b1-143">`Gender = Male`.</span></span>|  
|<span data-ttu-id="be7b1-144">8 (規則)</span><span class="sxs-lookup"><span data-stu-id="be7b1-144">8 (Rule)</span></span>|<span data-ttu-id="be7b1-145">定義項目之間關聯方式的規則。</span><span class="sxs-lookup"><span data-stu-id="be7b1-145">A rule defining how items relate to each other.</span></span><br /><br /> <span data-ttu-id="be7b1-146">範例：</span><span class="sxs-lookup"><span data-stu-id="be7b1-146">Example:</span></span><br /><br /> <span data-ttu-id="be7b1-147">`Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.</span><span class="sxs-lookup"><span data-stu-id="be7b1-147">`Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.</span></span>|  
  
 <span data-ttu-id="be7b1-148">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="be7b1-148">NODE_CAPTION</span></span>  
 <span data-ttu-id="be7b1-149">與節點關聯的標籤或標題。</span><span class="sxs-lookup"><span data-stu-id="be7b1-149">A label or a caption associated with the node.</span></span>  
  
 <span data-ttu-id="be7b1-150">**項目集節點** 逗號分隔的項目清單。</span><span class="sxs-lookup"><span data-stu-id="be7b1-150">**Itemset node** A comma-separated list of items.</span></span>  
  
 <span data-ttu-id="be7b1-151">**規則節點** 包含規則的左側和右側。</span><span class="sxs-lookup"><span data-stu-id="be7b1-151">**Rule node** Contains the left and right-hand sides of the rule.</span></span>  
  
 <span data-ttu-id="be7b1-152">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="be7b1-152">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="be7b1-153">指出目前節點的子系數目。</span><span class="sxs-lookup"><span data-stu-id="be7b1-153">Indicates the number of children of the current node.</span></span>  
  
 <span data-ttu-id="be7b1-154">**父節點** 指出項目集加規則的總數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-154">**Parent node** Indicates the total number of itemsets plus rules.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be7b1-155">若要取得項目集和規則計數的細目，請參閱模型根節點的 NODE_DESCRIPTION。</span><span class="sxs-lookup"><span data-stu-id="be7b1-155">To get a breakdown of the count for itemsets and rules, see the NODE_DESCRIPTION for the root node of the model.</span></span>  
  
 <span data-ttu-id="be7b1-156">**項目集或規則節點** 永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="be7b1-156">**Itemset or rule node** Always 0.</span></span>  
  
 <span data-ttu-id="be7b1-157">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="be7b1-157">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="be7b1-158">節點之父系的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="be7b1-158">The unique name of the node's parent.</span></span>  
  
 <span data-ttu-id="be7b1-159">**父節點**一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="be7b1-159">**Parent node** Always NULL.</span></span>  
  
 <span data-ttu-id="be7b1-160">**項目集或規則節點** 永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="be7b1-160">**Itemset or rule node** Always 0.</span></span>  
  
 <span data-ttu-id="be7b1-161">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="be7b1-161">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="be7b1-162">節點內容的易記描述。</span><span class="sxs-lookup"><span data-stu-id="be7b1-162">A user-friendly description of the contents of the node.</span></span>  
  
 <span data-ttu-id="be7b1-163">**父節點** 包含下列模型相關資訊的逗號分隔清單：</span><span class="sxs-lookup"><span data-stu-id="be7b1-163">**Parent node** Includes a comma-separated list of the following information about the model:</span></span>  
  
|<span data-ttu-id="be7b1-164">項目</span><span class="sxs-lookup"><span data-stu-id="be7b1-164">Item</span></span>|<span data-ttu-id="be7b1-165">描述</span><span class="sxs-lookup"><span data-stu-id="be7b1-165">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="be7b1-166">ITEMSET_COUNT</span><span class="sxs-lookup"><span data-stu-id="be7b1-166">ITEMSET_COUNT</span></span>|<span data-ttu-id="be7b1-167">模型中所有項目集的計數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-167">Count of all itemsets in model.</span></span>|  
|<span data-ttu-id="be7b1-168">RULE_COUNT</span><span class="sxs-lookup"><span data-stu-id="be7b1-168">RULE_COUNT</span></span>|<span data-ttu-id="be7b1-169">模型中所有規則的計數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-169">Count of all rules in model.</span></span>|  
|<span data-ttu-id="be7b1-170">MIN_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="be7b1-170">MIN_SUPPORT</span></span>|<span data-ttu-id="be7b1-171">任何單一項目集可用的最小支援。</span><span class="sxs-lookup"><span data-stu-id="be7b1-171">The minimum support found for any single itemset.</span></span><br /><br /> <span data-ttu-id="be7b1-172">**注意** 此值可能與您為 *MINIMUM _SUPPORT* 參數設定的值不同。</span><span class="sxs-lookup"><span data-stu-id="be7b1-172">**Note** This value might differ from the value that you set for the *MINIMUM _SUPPORT* parameter.</span></span>|  
|<span data-ttu-id="be7b1-173">MAX_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="be7b1-173">MAX_SUPPORT</span></span>|<span data-ttu-id="be7b1-174">任何單一項目集可用的最大支援。</span><span class="sxs-lookup"><span data-stu-id="be7b1-174">The maximum support found for any single itemset.</span></span><br /><br /> <span data-ttu-id="be7b1-175">**注意** 此值可能與您為 *MAXIMUM_SUPPORT* 參數設定的值不同。</span><span class="sxs-lookup"><span data-stu-id="be7b1-175">**Note** This value might differ from the value that you set for the *MAXIMUM_SUPPORT* parameter.</span></span>|  
|<span data-ttu-id="be7b1-176">MIN_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="be7b1-176">MIN_ITEMSET_SIZE</span></span>|<span data-ttu-id="be7b1-177">最小項目集的大小，由項目計數表示。</span><span class="sxs-lookup"><span data-stu-id="be7b1-177">The size of the smallest itemset, represented as a count of items.</span></span><br /><br /> <span data-ttu-id="be7b1-178">0 值表示會將 `Missing` 狀態視為獨立項目。</span><span class="sxs-lookup"><span data-stu-id="be7b1-178">A value of 0 indicates that the `Missing` state was treated as an independent item.</span></span><br /><br /> <span data-ttu-id="be7b1-179">\**注意\*\*\*MINIMUM_ITEMSET_SIZE* 參數的預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="be7b1-179">**Note** The default value of the *MINIMUM_ITEMSET_SIZE* parameter is 1.</span></span>|  
|<span data-ttu-id="be7b1-180">MAX_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="be7b1-180">MAX_ITEMSET_SIZE</span></span>|<span data-ttu-id="be7b1-181">指出找到的最大項目集大小。</span><span class="sxs-lookup"><span data-stu-id="be7b1-181">Indicates the size of the largest itemset that was found.</span></span><br /><br /> <span data-ttu-id="be7b1-182">**注意** 此值受限於您在建立模型時所設定的 *MAX_ITEMSET_SIZE* 參數值。</span><span class="sxs-lookup"><span data-stu-id="be7b1-182">**Note** This value is constrained by the value that you set for the *MAX_ITEMSET_SIZE* parameter when you created the model.</span></span> <span data-ttu-id="be7b1-183">此值絕不能超出該值，但可以比該值小。</span><span class="sxs-lookup"><span data-stu-id="be7b1-183">This value can never exceed that value; however, it can be less.</span></span> <span data-ttu-id="be7b1-184">預設值是 3。</span><span class="sxs-lookup"><span data-stu-id="be7b1-184">The default value is 3.</span></span>|  
|<span data-ttu-id="be7b1-185">MIN_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="be7b1-185">MIN_PROBABILITY</span></span>|<span data-ttu-id="be7b1-186">針對模型中任何單一項目集或規則所偵測到的最小機率。</span><span class="sxs-lookup"><span data-stu-id="be7b1-186">The minimum probability detected for any single itemset or rule in the model.</span></span><br /><br /> <span data-ttu-id="be7b1-187">範例：0.400390625</span><span class="sxs-lookup"><span data-stu-id="be7b1-187">Example: 0.400390625</span></span><br /><br /> <span data-ttu-id="be7b1-188">**注意** 對項目集而言，此值一定會比您在建立模型時所設定的 *MINIMUM_PROBABILITY* 參數值大。</span><span class="sxs-lookup"><span data-stu-id="be7b1-188">**Note** For itemsets, this value is always greater than the value that you set for the *MINIMUM_PROBABILITY* parameter when you created the model.</span></span>|  
|<span data-ttu-id="be7b1-189">MAX_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="be7b1-189">MAX_PROBABILITY</span></span>|<span data-ttu-id="be7b1-190">針對模型中任何單一項目集或規則所偵測到的最大機率。</span><span class="sxs-lookup"><span data-stu-id="be7b1-190">The maximum probability detected for any single itemset or rule in the model.</span></span><br /><br /> <span data-ttu-id="be7b1-191">範例：1</span><span class="sxs-lookup"><span data-stu-id="be7b1-191">Example: 1</span></span><br /><br /> <span data-ttu-id="be7b1-192">**注意** 沒有參數可以限制項目集的最大機率。</span><span class="sxs-lookup"><span data-stu-id="be7b1-192">**Note** There is no parameter to constrain maximum probability of itemsets.</span></span> <span data-ttu-id="be7b1-193">如果想要排除太常出現的項目，請改用 *MAXIMUM_SUPPORT* 參數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-193">If you want to eliminate items that are too frequent, use the *MAXIMUM_SUPPORT* parameter instead.</span></span>|  
|<span data-ttu-id="be7b1-194">MIN_LIFT</span><span class="sxs-lookup"><span data-stu-id="be7b1-194">MIN_LIFT</span></span>|<span data-ttu-id="be7b1-195">模型針對任何項目集所提供的最小增益量。</span><span class="sxs-lookup"><span data-stu-id="be7b1-195">The minimum amount of lift that is provided by the model for any itemset.</span></span><br /><br /> <span data-ttu-id="be7b1-196">範例：0.14309369632511</span><span class="sxs-lookup"><span data-stu-id="be7b1-196">Example: 0.14309369632511</span></span><br /><br /> <span data-ttu-id="be7b1-197">注意：了解最小增益量有助於判斷任何項目集的增益是否重要。</span><span class="sxs-lookup"><span data-stu-id="be7b1-197">Note: Knowing the minimum lift can help you determine whether the lift for any one itemset is significant.</span></span>|  
|<span data-ttu-id="be7b1-198">MAX_LIFT</span><span class="sxs-lookup"><span data-stu-id="be7b1-198">MAX_LIFT</span></span>|<span data-ttu-id="be7b1-199">模型針對任何項目集所提供的最大增益量。</span><span class="sxs-lookup"><span data-stu-id="be7b1-199">The maximum amount of lift that is provided by the model for any itemset.</span></span><br /><br /> <span data-ttu-id="be7b1-200">範例：1.95758227647523 **注意** 了解最大增益量有助於判斷任何項目集的增益是否重要。</span><span class="sxs-lookup"><span data-stu-id="be7b1-200">Example: 1.95758227647523 **Note** Knowing the maximum lift can help you determine whether the lift for any one itemset is significant.</span></span>|  
  
 <span data-ttu-id="be7b1-201">**項目集節點** 項目集節點包含顯示為逗號分隔文字字串的項目清單。</span><span class="sxs-lookup"><span data-stu-id="be7b1-201">**Itemset node** Itemset nodes contain a list of the items, displayed as a comma-separated text string.</span></span>  
  
 <span data-ttu-id="be7b1-202">範例：</span><span class="sxs-lookup"><span data-stu-id="be7b1-202">Example:</span></span>  
  
 `Touring Tire = Existing, Water Bottle = Existing`  
  
 <span data-ttu-id="be7b1-203">這表示休閒車輪胎和水壺是一起購買的。</span><span class="sxs-lookup"><span data-stu-id="be7b1-203">This means touring tires and water bottles were purchased together.</span></span>  
  
 <span data-ttu-id="be7b1-204">**規則節點** 規則節點包含規則的左側和右側，並以箭頭分隔。</span><span class="sxs-lookup"><span data-stu-id="be7b1-204">**Rule node** Rule nodes contains a left-hand and right-hand side of the rule, separated by an arrow.</span></span>  
  
 <span data-ttu-id="be7b1-205">範例： `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`</span><span class="sxs-lookup"><span data-stu-id="be7b1-205">Example: `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`</span></span>  
  
 <span data-ttu-id="be7b1-206">這代表如果有人購買了休閒車輪胎和水壺，則可能也會購買腳踏車帽。</span><span class="sxs-lookup"><span data-stu-id="be7b1-206">This means that if someone bought a touring tire and a water bottle, they were also likely to buy a cycling cap.</span></span>  
  
 <span data-ttu-id="be7b1-207">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="be7b1-207">NODE_RULE</span></span>  
 <span data-ttu-id="be7b1-208">XML 片段，描述內嵌於節點中的規則或項目集。</span><span class="sxs-lookup"><span data-stu-id="be7b1-208">An XML fragment that describes the rule or itemset that is embedded in the node.</span></span>  
  
 <span data-ttu-id="be7b1-209">**父節點** 空白。</span><span class="sxs-lookup"><span data-stu-id="be7b1-209">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="be7b1-210">**項目集節點** 空白。</span><span class="sxs-lookup"><span data-stu-id="be7b1-210">**Itemset node** Blank.</span></span>  
  
 <span data-ttu-id="be7b1-211">**規則節點** XML 片段包含有關規則的其他有用資訊，例如支援、信心和項目數，以及代表規則左側之節點的識別碼。</span><span class="sxs-lookup"><span data-stu-id="be7b1-211">**Rule node** The XML fragment includes additional useful information about the rule, such as support, confidence, and the number of items, and the ID of the node that represents the left-hand side of the rule.</span></span>  
  
 <span data-ttu-id="be7b1-212">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="be7b1-212">MARGINAL_RULE</span></span>  
 <span data-ttu-id="be7b1-213">空白。</span><span class="sxs-lookup"><span data-stu-id="be7b1-213">Blank.</span></span>  
  
 <span data-ttu-id="be7b1-214">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="be7b1-214">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="be7b1-215">與項目集或規則相關聯的機率或信心分數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-215">A probability or confidence score associated with the itemset or rule.</span></span>  
  
 <span data-ttu-id="be7b1-216">**父節點** 永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="be7b1-216">**Parent node** Always 0.</span></span>  
  
 <span data-ttu-id="be7b1-217">**項目集節點** 項目集的機率。</span><span class="sxs-lookup"><span data-stu-id="be7b1-217">**Itemset node** Probability of the itemset.</span></span>  
  
 <span data-ttu-id="be7b1-218">**規則節點** 規則的信心值。</span><span class="sxs-lookup"><span data-stu-id="be7b1-218">**Rule node** Confidence value for the rule.</span></span>  
  
 <span data-ttu-id="be7b1-219">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="be7b1-219">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="be7b1-220">與 NODE_PROBABILITY 相同。</span><span class="sxs-lookup"><span data-stu-id="be7b1-220">Same as NODE_PROBABILITY.</span></span>  
  
 <span data-ttu-id="be7b1-221">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="be7b1-221">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="be7b1-222">根據節點是項目集或規則，資料表會包含非常不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="be7b1-222">The table contains very different information, depending on whether the node is an itemset or a rule.</span></span>  
  
 <span data-ttu-id="be7b1-223">**父節點** 空白。</span><span class="sxs-lookup"><span data-stu-id="be7b1-223">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="be7b1-224">**項目集節點** 列出項目集中的每個項目，並提供機率和支援值。</span><span class="sxs-lookup"><span data-stu-id="be7b1-224">**Itemset node** Lists each item in the itemset together with a probability and support value.</span></span> <span data-ttu-id="be7b1-225">例如，如果項目集包含兩個產品，則會列出每個產品的名稱以及包含每個產品之案例的計數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-225">For example, if the itemset contains two products, the name of each product is listed, together with the count of cases that include each product.</span></span>  
  
 <span data-ttu-id="be7b1-226">**規則節點** 包含兩個資料列。</span><span class="sxs-lookup"><span data-stu-id="be7b1-226">**Rule node** Contains two rows.</span></span> <span data-ttu-id="be7b1-227">第一個資料列顯示規則右側的屬性 (也就是預測的項目) 以及信心分數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-227">The first row shows the attribute from the right-hand side of the rule, which is the predicted item, together with a confidence score.</span></span>  
  
 <span data-ttu-id="be7b1-228">第二個資料列是關聯模型所特有；它包含規則右側項目集的指標。</span><span class="sxs-lookup"><span data-stu-id="be7b1-228">The second row is unique to association models; it contains a pointer to the itemset on the right-hand side of the rule.</span></span> <span data-ttu-id="be7b1-229">在 ATTRIBUTE_VALUE 資料行中，該指標是表示為僅包含右側項目之項目集的識別碼。</span><span class="sxs-lookup"><span data-stu-id="be7b1-229">The pointer is represented in the ATTRIBUTE_VALUE column as the ID of the itemset that contains only the right-hand item.</span></span>  
  
 <span data-ttu-id="be7b1-230">例如，如果規則為 `If {A,B} Then {C}`，則資料表包含項目 `{C}`的名稱以及項目 C 之項目集的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="be7b1-230">For example, if the rule is `If {A,B} Then {C}`, the table contains the name of the item `{C}`, and the ID of the node that contains the itemset for item C.</span></span>  
  
 <span data-ttu-id="be7b1-231">此指標很有用，因為您可以從項目集節點判斷出所有項目中有多少案例包含右側產品。</span><span class="sxs-lookup"><span data-stu-id="be7b1-231">This pointer is useful because you can determine from the itemset node how many cases in all include the right-hand side product.</span></span> <span data-ttu-id="be7b1-232">受規則 `If {A,B} Then {C}` 影響的案例是 `{C}`的項目集中所列案例的子集。</span><span class="sxs-lookup"><span data-stu-id="be7b1-232">The cases that are subject to the rule `If {A,B} Then {C}` are a subset of the cases listed in the itemset for `{C}`.</span></span>  
  
 <span data-ttu-id="be7b1-233">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="be7b1-233">NODE_SUPPORT</span></span>  
 <span data-ttu-id="be7b1-234">支援這個節點的案例數目。</span><span class="sxs-lookup"><span data-stu-id="be7b1-234">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="be7b1-235">**父節點** 模型中的案例數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-235">**Parent node** Number of cases in the model.</span></span>  
  
 <span data-ttu-id="be7b1-236">**項目集節點** 包含項目集中所有項目之案例的數目。</span><span class="sxs-lookup"><span data-stu-id="be7b1-236">**Itemset node** Number of cases that contains all items in the itemset.</span></span>  
  
 <span data-ttu-id="be7b1-237">**規則節點** 包含規則中所含全部項目之案例的數目。</span><span class="sxs-lookup"><span data-stu-id="be7b1-237">**Rule node** The number of cases that contain all items included in the rule.</span></span>  
  
 <span data-ttu-id="be7b1-238">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="be7b1-238">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="be7b1-239">根據節點是項目集或規則會包含非常不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="be7b1-239">Contains different information depending on whether the node is an itemset or rule.</span></span>  
  
 <span data-ttu-id="be7b1-240">**父節點** 空白。</span><span class="sxs-lookup"><span data-stu-id="be7b1-240">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="be7b1-241">**項目集節點** 空白。</span><span class="sxs-lookup"><span data-stu-id="be7b1-241">**Itemset node** Blank.</span></span>  
  
 <span data-ttu-id="be7b1-242">**規則節點** 包含規則左側項目之項目集的識別碼。</span><span class="sxs-lookup"><span data-stu-id="be7b1-242">**Rule node** The ID of the itemset that contains the items in the left-hand side of the rule.</span></span> <span data-ttu-id="be7b1-243">例如，如果規則是 `If {A,B} Then {C}`，則此資料行會包含僅包含 `{A,B}`之項目集的識別碼。</span><span class="sxs-lookup"><span data-stu-id="be7b1-243">For example, if the rule is `If {A,B} Then {C}`, this column contains the ID of the itemset that contains only `{A,B}`.</span></span>  
  
 <span data-ttu-id="be7b1-244">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="be7b1-244">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="be7b1-245">**父節點** 空白。</span><span class="sxs-lookup"><span data-stu-id="be7b1-245">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="be7b1-246">**項目集節點** 項目集的重要性分數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-246">**Itemset node** Importance score for the itemset.</span></span>  
  
 <span data-ttu-id="be7b1-247">**規則節點** 規則的重要性分數。</span><span class="sxs-lookup"><span data-stu-id="be7b1-247">**Rule node** Importance score for the rule.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be7b1-248">項目集和規則的重要性計算方式不同。</span><span class="sxs-lookup"><span data-stu-id="be7b1-248">Importance is calculated differently for itemsets and rules.</span></span> <span data-ttu-id="be7b1-249">如需詳細資訊，請參閱 [Microsoft 關聯分析演算法技術參考](microsoft-association-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="be7b1-249">For more information, see [Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="be7b1-250">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="be7b1-250">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="be7b1-251">空白。</span><span class="sxs-lookup"><span data-stu-id="be7b1-251">Blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7b1-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be7b1-252">See Also</span></span>  
 <span data-ttu-id="be7b1-253">[&#40;Analysis Services 的採礦模型內容-資料採礦&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="be7b1-253">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="be7b1-254">[Microsoft 關聯分析演算法](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="be7b1-254">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="be7b1-255">關聯模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="be7b1-255">Association Model Query Examples</span></span>](association-model-query-examples.md)  
  
  
