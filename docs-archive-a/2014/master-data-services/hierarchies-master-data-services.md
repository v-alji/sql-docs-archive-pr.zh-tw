---
title: 階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services]
- hierarchies [Master Data Services], about hierarchies
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 126a01c03134c6859426c09fda398408694795f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597184"
---
# <a name="hierarchies-master-data-services"></a><span data-ttu-id="bc0c9-102">階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bc0c9-102">Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="bc0c9-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，階層是一個樹狀目錄，您可以用它來執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="bc0c9-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a hierarchy is a tree structure that you can use to:</span></span>

-   <span data-ttu-id="bc0c9-104">分組類似的成員供組織使用。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-104">Group similar members for organizational purposes.</span></span>

-   <span data-ttu-id="bc0c9-105">合併及摘要成員來進行報告和分析。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-105">Consolidate and summarize members for reporting and analysis.</span></span>

## <a name="what-hierarchies-contain"></a><span data-ttu-id="bc0c9-106">階層包含的內容</span><span class="sxs-lookup"><span data-stu-id="bc0c9-106">What Hierarchies Contain</span></span>
 <span data-ttu-id="bc0c9-107">每個階層都包含一個或多個實體中的成員。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-107">Each hierarchy contains members from one or more entities.</span></span> <span data-ttu-id="bc0c9-108">當您加入、變更或刪除成員時，所有的階層都會更新。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-108">When a member is added, changed, or deleted, all hierarchies are updated.</span></span> <span data-ttu-id="bc0c9-109">如此可確保資料在所有階層中都是正確的。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-109">This ensures that the data is accurate in all hierarchies.</span></span> <span data-ttu-id="bc0c9-110">階層也有助於確保每個成員只計算一次。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-110">Hierarchies also help ensure that each member is counted once and only once.</span></span>

 <span data-ttu-id="bc0c9-111">如果您要建立成員子集的群組，請考慮使用集合。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-111">If you want to create a grouping of a subset of members, consider using a collection.</span></span> <span data-ttu-id="bc0c9-112">如需詳細資訊，請參閱 [集合 &#40;Master Data Services&#41;](collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-112">For more information, see [Collections &#40;Master Data Services&#41;](collections-master-data-services.md).</span></span>

## <a name="kinds-of-hierarchies"></a><span data-ttu-id="bc0c9-113">階層類型</span><span class="sxs-lookup"><span data-stu-id="bc0c9-113">Kinds of Hierarchies</span></span>
 <span data-ttu-id="bc0c9-114">您可以建立多個階層，以不同的方式來檢視及組織成員。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-114">You can create multiple hierarchies to view and organize your members in different ways.</span></span> <span data-ttu-id="bc0c9-115">您可以建立：</span><span class="sxs-lookup"><span data-stu-id="bc0c9-115">You can create:</span></span>

-   <span data-ttu-id="bc0c9-116">來自單一實體的不完全階層，這些階層稱為明確階層。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-116">Ragged hierarchies from a single entity, which are called explicit hierarchies.</span></span> <span data-ttu-id="bc0c9-117">如需詳細資訊，請參閱 [明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-117">For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).</span></span>

-   <span data-ttu-id="bc0c9-118">來自根據實體與及其屬性之間現有關聯性之多個實體的層級型階層，這些階層稱為衍生階層。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-118">Level-based hierarchies from multiple entities, based on the existing relationships between entities and their attributes, which are called derived hierarchies.</span></span> <span data-ttu-id="bc0c9-119">如需詳細資訊，請參閱 [衍生階層 &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-119">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="bc0c9-120">階層中的所有成員都必須在相同的模型中。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-120">All members in a hierarchy must be within the same model.</span></span>

## <a name="hierarchies-are-not-taxonomies"></a><span data-ttu-id="bc0c9-121">層次不是分類</span><span class="sxs-lookup"><span data-stu-id="bc0c9-121">Hierarchies Are Not Taxonomies</span></span>
 <span data-ttu-id="bc0c9-122">階層與分類不同。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-122">A hierarchy is different from a taxonomy.</span></span> <span data-ttu-id="bc0c9-123">分類會同時根據多個屬性來組織成員，而階層則一次根據一個屬性來組織成員。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-123">A taxonomy organizes members by multiple attributes at the same time, while a hierarchy organizes members by one attribute at a time.</span></span> <span data-ttu-id="bc0c9-124">分類可以包含相同成員多次，而階層只能包含成員一次。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-124">A taxonomy can include the same member multiple times, while a hierarchy includes a member only once.</span></span>

 <span data-ttu-id="bc0c9-125">例如，相同的自行車可以包含在某個分類中兩次：一次是因為它是紅色，另一次是因為它的尺寸為 38。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-125">For example, the same bike can be included in a taxonomy twice: once because it's red, and once because it's a size 38.</span></span> <span data-ttu-id="bc0c9-126">在階層中，自行車只能包含一次，所以您必須決定是要根據它的顏色還是尺寸來顯示。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-126">In a hierarchy, the bike is included only once, so you must decide whether to show it in relation to its color or its size.</span></span>

## <a name="hierarchy-example"></a><span data-ttu-id="bc0c9-127">階層範例</span><span class="sxs-lookup"><span data-stu-id="bc0c9-127">Hierarchy Example</span></span>
 <span data-ttu-id="bc0c9-128">在下列範例中，產品成員是依子類別目錄成員分組。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-128">In the following example, product members are grouped by subcategory members.</span></span>

 <span data-ttu-id="bc0c9-129">![依子類別目錄分組之階層的範例](../../2014/master-data-services/media/mds-conc-hierarchy.gif "依子類別目錄分組之階層的範例")</span><span class="sxs-lookup"><span data-stu-id="bc0c9-129">![Hierarchy Grouped by Subcategory Example](../../2014/master-data-services/media/mds-conc-hierarchy.gif "Hierarchy Grouped by Subcategory Example")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="bc0c9-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="bc0c9-130">Related Tasks</span></span>

|<span data-ttu-id="bc0c9-131">工作描述</span><span class="sxs-lookup"><span data-stu-id="bc0c9-131">Task Description</span></span>|<span data-ttu-id="bc0c9-132">主題</span><span class="sxs-lookup"><span data-stu-id="bc0c9-132">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="bc0c9-133">啟用明確階層和集合的實體。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-133">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="bc0c9-134">啟用明確階層和集合的實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-134">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|<span data-ttu-id="bc0c9-135">建立明確階層。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-135">Create a explicit hierarchy.</span></span>|[<span data-ttu-id="bc0c9-136">建立明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-136">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="bc0c9-137">建立衍生階層。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-137">Create a derived hierarchy.</span></span>|[<span data-ttu-id="bc0c9-138">建立衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-138">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="bc0c9-139">隱藏或刪除現有衍生階層中的層級。</span><span class="sxs-lookup"><span data-stu-id="bc0c9-139">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="bc0c9-140">隱藏或刪除衍生階層中的層級 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-140">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="bc0c9-141">相關內容</span><span class="sxs-lookup"><span data-stu-id="bc0c9-141">Related Content</span></span>

-   [<span data-ttu-id="bc0c9-142">明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-142">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="bc0c9-143">衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-143">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="bc0c9-144">遞迴階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-144">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="bc0c9-145">具有明確頂層的衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-145">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="bc0c9-146">集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bc0c9-146">Collections &#40;Master Data Services&#41;</span></span>](collections-master-data-services.md)


