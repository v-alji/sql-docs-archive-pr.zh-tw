---
title: 明確階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, about explicit hierarchies
- hierarchies [Master Data Services], explicit hierarchies
- explicit hierarchies
ms.assetid: e6f44e37-e1f0-4c38-a816-1935a856d5a4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f37f341dc2c003683e696f2767a6b644047d5a0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699940"
---
# <a name="explicit-hierarchies-master-data-services"></a><span data-ttu-id="eb922-102">明確階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="eb922-102">Explicit Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="eb922-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，明確階層可以您指定的任何方式組織來自單一實體的成員。</span><span class="sxs-lookup"><span data-stu-id="eb922-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], an explicit hierarchy organizes members from a single entity in any way you specify.</span></span> <span data-ttu-id="eb922-104">衍生階層可以是不完全的，而且明確階層不像衍生階層，前者不是以網域屬性關聯性為基礎。</span><span class="sxs-lookup"><span data-stu-id="eb922-104">The structure can be ragged and unlike derived hierarchies, explicit hierarchies are not based on domain-based attribute relationships.</span></span>

## <a name="consolidated-members-group-other-members"></a><span data-ttu-id="eb922-105">合併成員群組其他成員</span><span class="sxs-lookup"><span data-stu-id="eb922-105">Consolidated Members Group Other Members</span></span>
 <span data-ttu-id="eb922-106">明確階層會使用您為了分組其他成員所建立的合併成員。</span><span class="sxs-lookup"><span data-stu-id="eb922-106">An explicit hierarchy uses consolidated members that you create for the purpose of grouping other members.</span></span> <span data-ttu-id="eb922-107">這些合併成員一次只能屬於一個明確階層。</span><span class="sxs-lookup"><span data-stu-id="eb922-107">These consolidated members can belong to only one explicit hierarchy at a time.</span></span> <span data-ttu-id="eb922-108">明確階層也包含其關聯實體的所有分葉成員。</span><span class="sxs-lookup"><span data-stu-id="eb922-108">An explicit hierarchy also includes all of the leaf members from the associated entity.</span></span>

 <span data-ttu-id="eb922-109">明確階層可以是不完全的，這表示階層可以同時在不同層級結束。</span><span class="sxs-lookup"><span data-stu-id="eb922-109">An explicit hierarchy can be ragged, which means that the hierarchy can end at different levels simultaneously.</span></span> <span data-ttu-id="eb922-110">每個合併成員都可以有數量不受限制的合併成員及其底下的分葉成員，也可以沒有任何成員。</span><span class="sxs-lookup"><span data-stu-id="eb922-110">Each consolidated member can have an unlimited number of consolidated and leaf members underneath, or can have none.</span></span> <span data-ttu-id="eb922-111">分葉成員可以在單一彙總成員底下，或是在合併成員的多個層級底下。</span><span class="sxs-lookup"><span data-stu-id="eb922-111">The leaf members can be under a single consolidated member or under multiple levels of consolidated members.</span></span>

> [!NOTE]
>  <span data-ttu-id="eb922-112">在您可以建立明確階層之前，實體必須啟用明確階層。</span><span class="sxs-lookup"><span data-stu-id="eb922-112">Before you can create an explicit hierarchy, the entity must be enabled for explicit hierarchies.</span></span> <span data-ttu-id="eb922-113">如需詳細資訊，請參閱[啟用明確階層和集合的實體 &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="eb922-113">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>

## <a name="types-of-explicit-hierarchies"></a><span data-ttu-id="eb922-114">明確階層的類型</span><span class="sxs-lookup"><span data-stu-id="eb922-114">Types of Explicit Hierarchies</span></span>
 <span data-ttu-id="eb922-115">有兩種類型的明確階層：強制和非強制。</span><span class="sxs-lookup"><span data-stu-id="eb922-115">There are two types of explicit hierarchies: mandatory and non-mandatory.</span></span>

### <a name="mandatory-explicit-hierarchy"></a><span data-ttu-id="eb922-116">強制的明確階層</span><span class="sxs-lookup"><span data-stu-id="eb922-116">Mandatory Explicit Hierarchy</span></span>
 <span data-ttu-id="eb922-117">強制的明確階層是一種階層，其中的所有分葉成員都必須包括在階層樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="eb922-117">A mandatory explicit hierarchy is a hierarchy in which all leaf members must be included in the hierarchy tree.</span></span> <span data-ttu-id="eb922-118">根據預設，所有成員都會包含在樹狀結構的根。</span><span class="sxs-lookup"><span data-stu-id="eb922-118">By default, all members are included at the root of the tree.</span></span> <span data-ttu-id="eb922-119">您可以視需要重新排列成員。</span><span class="sxs-lookup"><span data-stu-id="eb922-119">You can rearrange the members as needed.</span></span>

### <a name="non-mandatory-explicit-hierarchy"></a><span data-ttu-id="eb922-120">非強制的明確階層</span><span class="sxs-lookup"><span data-stu-id="eb922-120">Non-Mandatory Explicit Hierarchy</span></span>
 <span data-ttu-id="eb922-121">非強制的明確階層是一種階層，其所有分葉成員都是位於系統建立的 [未使用]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="eb922-121">A non-mandatory explicit hierarchy is a hierarchy in which all leaf members are in a system-created **Unused** node.</span></span> <span data-ttu-id="eb922-122">您可以在需要時，將成員移出這個節點。</span><span class="sxs-lookup"><span data-stu-id="eb922-122">You can move members out of this node as you need them.</span></span> <span data-ttu-id="eb922-123">其餘的成員可以保留在 [未使用]\*\*\*\* 節點中。</span><span class="sxs-lookup"><span data-stu-id="eb922-123">The rest of the members can remain in the **Unused** node.</span></span>

 <span data-ttu-id="eb922-124">當您使用非強制的明確階層時，在此階層上所做的任何報告或分析可能不會符合強制的階層上所做的報告或分析。</span><span class="sxs-lookup"><span data-stu-id="eb922-124">When you use non-mandatory explicit hierarchies, any reporting or analysis done on the hierarchy may not match reporting or analysis done on mandatory hierarchies.</span></span>

## <a name="rules"></a><span data-ttu-id="eb922-125">規則</span><span class="sxs-lookup"><span data-stu-id="eb922-125">Rules</span></span>
 <span data-ttu-id="eb922-126">下列規則適用於明確階層 (強制和非強制)。</span><span class="sxs-lookup"><span data-stu-id="eb922-126">The following rules apply to explicit hierarchies (both mandatory and non-mandatory).</span></span>

-   <span data-ttu-id="eb922-127">每個分葉成員只能包含在階層中一次。</span><span class="sxs-lookup"><span data-stu-id="eb922-127">Each leaf member can be included in the hierarchy only once.</span></span>

-   <span data-ttu-id="eb922-128">所有的合併成員都必須包含在階層中。</span><span class="sxs-lookup"><span data-stu-id="eb922-128">All consolidated members must be included in a hierarchy.</span></span>

-   <span data-ttu-id="eb922-129">合併成員不能位於一個以上的明確階層中。</span><span class="sxs-lookup"><span data-stu-id="eb922-129">Consolidated members cannot be in more than one explicit hierarchy.</span></span>

-   <span data-ttu-id="eb922-130">階層樹狀結構中的合併成員不必包含底下的分葉成員。</span><span class="sxs-lookup"><span data-stu-id="eb922-130">Consolidated members in the hierarchy tree do not have to contain leaf members underneath them.</span></span>

-   <span data-ttu-id="eb922-131">如果您刪除明確階層，之前在此階層中使用的所有合併成員也會一併刪除。</span><span class="sxs-lookup"><span data-stu-id="eb922-131">If you delete an explicit hierarchy, all consolidated members that were used in the hierarchy are deleted.</span></span>

-   <span data-ttu-id="eb922-132">如果您刪除之前在明確階層中的合併成員，則之前依照該合併成員所分組的所有分葉成員都會移到根目錄。</span><span class="sxs-lookup"><span data-stu-id="eb922-132">If you delete a consolidated member that was in an explicit hierarchy, all leaf members that were grouped by that consolidated member are moved to the root.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="eb922-133">明確階層與衍生階層的比較</span><span class="sxs-lookup"><span data-stu-id="eb922-133">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="eb922-134">下表顯示明確階層與衍生階層之間的某些差異。</span><span class="sxs-lookup"><span data-stu-id="eb922-134">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="eb922-135">明確階層</span><span class="sxs-lookup"><span data-stu-id="eb922-135">Explicit Hierarchies</span></span>|<span data-ttu-id="eb922-136">衍生階層</span><span class="sxs-lookup"><span data-stu-id="eb922-136">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="eb922-137">結構是由使用者所定義</span><span class="sxs-lookup"><span data-stu-id="eb922-137">Structure is defined by the user</span></span>|<span data-ttu-id="eb922-138">結構衍生自網域屬性之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="eb922-138">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="eb922-139">包含來自單一實體的成員</span><span class="sxs-lookup"><span data-stu-id="eb922-139">Contains members from a single entity</span></span>|<span data-ttu-id="eb922-140">包含來自多個實體的成員</span><span class="sxs-lookup"><span data-stu-id="eb922-140">Contains members from multiple entities</span></span>|
|<span data-ttu-id="eb922-141">使用合併成員群組其他成員</span><span class="sxs-lookup"><span data-stu-id="eb922-141">Uses consolidated members to group other members</span></span>|<span data-ttu-id="eb922-142">使用某個實體的分葉成員群組另一個實體的分葉成員</span><span class="sxs-lookup"><span data-stu-id="eb922-142">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="eb922-143">可以是不完全的</span><span class="sxs-lookup"><span data-stu-id="eb922-143">Can be ragged</span></span>|<span data-ttu-id="eb922-144">永遠包含固定數目的層級</span><span class="sxs-lookup"><span data-stu-id="eb922-144">Always contains a consistent number of levels</span></span>|

## <a name="explicit-hierarchy-example"></a><span data-ttu-id="eb922-145">明確階層範例</span><span class="sxs-lookup"><span data-stu-id="eb922-145">Explicit Hierarchy Example</span></span>
 <span data-ttu-id="eb922-146">在下列範例中，Product 實體包含這些分葉成員：BK-M101 {Mountain-100}、BK-M201 {Mountain-200}、BK-M301 {Mountain-300}、BK-R150 {Road-150}、BK-R450 {Road-450} 和 BK-R650 {Road-650}。</span><span class="sxs-lookup"><span data-stu-id="eb922-146">In the following example, the Product entity contains these leaf members: BK-M101 {Mountain-100}, BK-M201 {Mountain-200}, BK-M301 {Mountain-300}, BK-R150 {Road-150}, BK-R450 {Road-450}, and BK-R650 {Road-650}.</span></span>

 <span data-ttu-id="eb922-147">若要摘要列出在特定合併點上的分葉成員，您可以在 Product 實體中建立合併成員。</span><span class="sxs-lookup"><span data-stu-id="eb922-147">To summarize these leaf members at specific consolidation points, you can create consolidated members in the Product entity.</span></span> <span data-ttu-id="eb922-148">在階層樹狀結構中，於您想要摘要列出分葉成員的層級上插入合併成員。</span><span class="sxs-lookup"><span data-stu-id="eb922-148">Insert the consolidated members at levels in the hierarchy tree where you want to summarize the leaf members.</span></span> <span data-ttu-id="eb922-149">您可以插入合併成員的位置並沒有任何限制，但是每一個成員 (分葉或合併成員) 只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="eb922-149">There is no limitation on where you insert your consolidated members; however, each member (leaf or consolidated) can be used only once.</span></span>

 <span data-ttu-id="eb922-150">![越野車明確階層範例](../../2014/master-data-services/media/mds-conc-explicit-hierarchy.gif "越野車明確階層範例")</span><span class="sxs-lookup"><span data-stu-id="eb922-150">![Mountain Bike Explicit Hierarchy Example](../../2014/master-data-services/media/mds-conc-explicit-hierarchy.gif "Mountain Bike Explicit Hierarchy Example")</span></span>

 <span data-ttu-id="eb922-151">合併成員可在任何層級用來分組成員，而且分葉成員和合併成員會依照您決定的順序來排序。</span><span class="sxs-lookup"><span data-stu-id="eb922-151">Consolidated members can be used to group members at any level, and leaf and consolidated members are sorted in the order you determine.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="eb922-152">相關工作</span><span class="sxs-lookup"><span data-stu-id="eb922-152">Related Tasks</span></span>

|<span data-ttu-id="eb922-153">工作描述</span><span class="sxs-lookup"><span data-stu-id="eb922-153">Task Description</span></span>|<span data-ttu-id="eb922-154">主題</span><span class="sxs-lookup"><span data-stu-id="eb922-154">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="eb922-155">啟用明確階層和集合的實體。</span><span class="sxs-lookup"><span data-stu-id="eb922-155">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="eb922-156">啟用明確階層和集合的實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb922-156">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|<span data-ttu-id="eb922-157">建立新的明確階層。</span><span class="sxs-lookup"><span data-stu-id="eb922-157">Create a new explicit hierarchy.</span></span>|[<span data-ttu-id="eb922-158">建立明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb922-158">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="eb922-159">變更現有明確階層的名稱。</span><span class="sxs-lookup"><span data-stu-id="eb922-159">Change the name of an existing explicity hierarchy.</span></span>|[<span data-ttu-id="eb922-160">變更明確階層名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb922-160">Change an Explicit Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="eb922-161">刪除現有明確階層。</span><span class="sxs-lookup"><span data-stu-id="eb922-161">Delete an existing explicit hierarchy.</span></span>|[<span data-ttu-id="eb922-162">刪除明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb922-162">Delete an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-explicit-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="eb922-163">相關內容</span><span class="sxs-lookup"><span data-stu-id="eb922-163">Related Content</span></span>

-   [<span data-ttu-id="eb922-164">衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb922-164">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="eb922-165">集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb922-165">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)


