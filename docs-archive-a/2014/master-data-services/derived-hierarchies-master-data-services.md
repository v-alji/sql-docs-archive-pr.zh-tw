---
title: 衍生階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies
- hierarchies [Master Data Services], derived hierarchies
- derived hierarchies, about derived hierarchies
ms.assetid: a0fbd519-a10e-4cbd-92e6-5de9b8d3e3f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92867f225a8f14e59cb9a519f174902d0739773a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607433"
---
# <a name="derived-hierarchies-master-data-services"></a><span data-ttu-id="c3cb7-102">衍生階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c3cb7-102">Derived Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="c3cb7-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 衍生階層衍生自已存在於模型中實體之間的網域屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-103">A [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] derived hierarchy is derived from the domain-based attribute relationships that already exist between entities in a model.</span></span>

 <span data-ttu-id="c3cb7-104">您可以建立衍生階層，以反白顯示模型中任何現有的網域屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-104">You can create a derived hierarchy to highlight any of the existing domain-based attribute relationships in the model.</span></span>

## <a name="leaf-members-group-other-leaf-members"></a><span data-ttu-id="c3cb7-105">分頁成員群組其他分頁成員</span><span class="sxs-lookup"><span data-stu-id="c3cb7-105">Leaf Members Group Other Leaf Members</span></span>
 <span data-ttu-id="c3cb7-106">在衍生階層中，會使用來自某個實體的分頁成員為另一個實體的分頁成員分組。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-106">In a derived hierarchy, the leaf members from one entity are used to group the leaf members of another entity.</span></span> <span data-ttu-id="c3cb7-107">衍生階層是以這些實體間的關聯性為基礎。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-107">A derived hierarchy is based on the relationship between these entities.</span></span> <span data-ttu-id="c3cb7-108">相反地，明確階層是僅以單一實體的成員為基礎，並以您指定的任何方式予以結構化。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-108">An explicit hierarchy, in contrast, is based on members from a single entity only and is structured in any way you specify.</span></span>

 <span data-ttu-id="c3cb7-109">您可以變更衍生階層的結構，而不影響基礎資料。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-109">You can change the structure of a derived hierarchy without affecting the underlying data.</span></span> <span data-ttu-id="c3cb7-110">只要關聯性仍然存在於模型中，刪除衍生階層就不會影響主要資料。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-110">As long as the relationships still exist in the model, deleting a derived hierarchy has no effect on your master data.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="c3cb7-111">明確階層與衍生階層的比較</span><span class="sxs-lookup"><span data-stu-id="c3cb7-111">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="c3cb7-112">下表顯示明確階層與衍生階層之間的某些差異。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-112">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="c3cb7-113">明確階層</span><span class="sxs-lookup"><span data-stu-id="c3cb7-113">Explicit Hierarchies</span></span>|<span data-ttu-id="c3cb7-114">衍生階層</span><span class="sxs-lookup"><span data-stu-id="c3cb7-114">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="c3cb7-115">結構是由使用者所定義</span><span class="sxs-lookup"><span data-stu-id="c3cb7-115">Structure is defined by the user</span></span>|<span data-ttu-id="c3cb7-116">結構衍生自網域屬性之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="c3cb7-116">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="c3cb7-117">包含來自單一實體的成員</span><span class="sxs-lookup"><span data-stu-id="c3cb7-117">Contains members from a single entity</span></span>|<span data-ttu-id="c3cb7-118">包含來自多個實體的成員</span><span class="sxs-lookup"><span data-stu-id="c3cb7-118">Contains members from multiple entities</span></span>|
|<span data-ttu-id="c3cb7-119">使用合併成員群組其他成員</span><span class="sxs-lookup"><span data-stu-id="c3cb7-119">Uses consolidated members to group other members</span></span>|<span data-ttu-id="c3cb7-120">使用某個實體的分葉成員群組另一個實體的分葉成員</span><span class="sxs-lookup"><span data-stu-id="c3cb7-120">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="c3cb7-121">可以是不完全的</span><span class="sxs-lookup"><span data-stu-id="c3cb7-121">Can be ragged</span></span>|<span data-ttu-id="c3cb7-122">永遠包含固定數目的層級</span><span class="sxs-lookup"><span data-stu-id="c3cb7-122">Always contains a consistent number of levels</span></span>|

## <a name="creating-a-variable-depth-hierarchy"></a><span data-ttu-id="c3cb7-123">建立可變深度的階層</span><span class="sxs-lookup"><span data-stu-id="c3cb7-123">Creating a Variable-Depth Hierarchy</span></span>
 <span data-ttu-id="c3cb7-124">有兩種建議的方式可建立可變深度的階層：</span><span class="sxs-lookup"><span data-stu-id="c3cb7-124">There are two recommended ways to create a variable-depth hierarchy:</span></span>

-   <span data-ttu-id="c3cb7-125">如果您需要所有層級擁有相同的屬性，則建立單一實體，然後使用以實體為基礎的網域屬性在這個實體上建立遞迴階層。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-125">If you need all levels to have the same attributes, create a single entity, and then create a recursive hierarchy on this entity, using a domain-based attribute that is based on the entity.</span></span>

-   <span data-ttu-id="c3cb7-126">如果您需要一組屬性用於分葉成員，以及另一組屬性用於上層，請為衍生階層建立兩個實體。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-126">If you need one set of attributes for the leaf members and another set of attributes in the upper levels, create two entities for a derived hierarchy.</span></span> <span data-ttu-id="c3cb7-127">若是分葉實體，請使用以父實體為基礎的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-127">For the leaf entity, use a domain-based attribute that is based upon the parent entity.</span></span> <span data-ttu-id="c3cb7-128">若是父實體，請使用以本身為基礎的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-128">For the parent entity, use a domain-based attribute that is based upon itself.</span></span>

## <a name="derived-hierarchy-example"></a><span data-ttu-id="c3cb7-129">衍生階層範例</span><span class="sxs-lookup"><span data-stu-id="c3cb7-129">Derived Hierarchy Example</span></span>
 <span data-ttu-id="c3cb7-130">在下列範例中，Product 實體的分葉成員依 Subcategory 實體的分葉成員分組，後者則依 Category 實體的分葉成員分組。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-130">In the following example, leaf members of the Product entity are grouped by leaf members of the Subcategory entity, which are then grouped by leaf members of the Category entity.</span></span> <span data-ttu-id="c3cb7-131">此階層是可能的，因為 Product 實體有名稱為 Subcategory 的網域屬性，而 Subcategory 實體有名稱為 Category 的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-131">This hierarchy is possible because the Product entity has a domain-based attribute named Subcategory, and the Subcategory entity has a domain-based attribute named Category.</span></span>

 <span data-ttu-id="c3cb7-132">階層結構顯示成員分組方式。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-132">The hierarchy structure shows how the members are grouped.</span></span> <span data-ttu-id="c3cb7-133">有最多成員的實體位於底部。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-133">The entity with the most members is at the bottom.</span></span>

 <span data-ttu-id="c3cb7-134">![衍生自模型結構的階層](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "衍生自模型結構的階層")</span><span class="sxs-lookup"><span data-stu-id="c3cb7-134">![Hierarchy Derived from Model Structure](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "Hierarchy Derived from Model Structure")</span></span>

 <span data-ttu-id="c3cb7-135">在衍生階層中，您可以反白顯示 Product 與 Subcategory 之間的關聯性，然後反白顯示 Subcategory 與 Category 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-135">In a derived hierarchy, you can highlight the relationship between Product and Subcategory, and then between Subcategory and Category.</span></span> <span data-ttu-id="c3cb7-136">當您在此階層中檢視成員時，樹狀結構中的每個層級都包含相同實體中的成員。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-136">When you view the members in this hierarchy, each level in the tree contains members from the same entity.</span></span>

 <span data-ttu-id="c3cb7-137">![越野車衍生的階層範例](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "越野車衍生的階層範例")</span><span class="sxs-lookup"><span data-stu-id="c3cb7-137">![Mountain Bike Derived Hierarchy Example](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "Mountain Bike Derived Hierarchy Example")</span></span>

 <span data-ttu-id="c3cb7-138">這種類型的階層可防止您將成員移到無效的層級。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-138">This type of hierarchy prevents you from moving a member to a level that is not valid.</span></span> <span data-ttu-id="c3cb7-139">例如，您可以將某個子類別目錄 Road Bikes 中的 Road-650 自行車移到另一個子類別目錄 Mountain Bikes。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-139">For example, you can move the Road-650 bike from one subcategory, Road Bikes, to another, Mountain Bikes.</span></span> <span data-ttu-id="c3cb7-140">您無法像 1 {Bikes} 一樣直接移動類別目錄底下的 Road-650。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-140">You cannot move Road-650 directly under a category, like 1 {Bikes}.</span></span> <span data-ttu-id="c3cb7-141">每當您在階層樹狀結構中移動成員時，該成員的網域屬性值都會隨之變更，以反映這個移動作業。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-141">Each time you move a member in the hierarchy tree, the member's domain-based attribute value changes to reflect the move.</span></span>

## <a name="notes"></a><span data-ttu-id="c3cb7-142">注意</span><span class="sxs-lookup"><span data-stu-id="c3cb7-142">Notes</span></span>
 <span data-ttu-id="c3cb7-143">衍生階層樹狀結構中的所有成員都會依照代碼來排序。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-143">All members in a derived hierarchy tree are sorted by code.</span></span> <span data-ttu-id="c3cb7-144">您無法變更排序次序。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-144">You cannot change the sort order.</span></span>

 <span data-ttu-id="c3cb7-145">如果成員的網域屬性為空白，而且此屬性用於衍生階層，則該成員不會顯示在階層中。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-145">If a member's domain-based attribute is blank and the attribute is used for a derived hierarchy, the member is not displayed in the hierarchy.</span></span> <span data-ttu-id="c3cb7-146">建立商務規則來要求填入屬性。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-146">Create business rules to require attributes to be populated.</span></span> <span data-ttu-id="c3cb7-147">如需詳細資訊，請參閱[要求屬性值 &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-147">For more information, see [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="c3cb7-148">相關工作</span><span class="sxs-lookup"><span data-stu-id="c3cb7-148">Related Tasks</span></span>

|<span data-ttu-id="c3cb7-149">工作描述</span><span class="sxs-lookup"><span data-stu-id="c3cb7-149">Task Description</span></span>|<span data-ttu-id="c3cb7-150">主題</span><span class="sxs-lookup"><span data-stu-id="c3cb7-150">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="c3cb7-151">建立新的衍生階層。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-151">Create a new derived hierarchy.</span></span>|[<span data-ttu-id="c3cb7-152">建立衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-152">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="c3cb7-153">隱藏或刪除現有衍生階層中的層級。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-153">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="c3cb7-154">隱藏或刪除衍生階層中的層級 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-154">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="c3cb7-155">變更現有衍生階層的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-155">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="c3cb7-156">變更衍生階層名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-156">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="c3cb7-157">刪除現有衍生階層。</span><span class="sxs-lookup"><span data-stu-id="c3cb7-157">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="c3cb7-158">刪除衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-158">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="c3cb7-159">相關內容</span><span class="sxs-lookup"><span data-stu-id="c3cb7-159">Related Content</span></span>

-   [<span data-ttu-id="c3cb7-160">網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-160">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="c3cb7-161">明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-161">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="c3cb7-162">遞迴階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-162">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="c3cb7-163">具有明確頂層的衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-163">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="c3cb7-164">集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c3cb7-164">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)


