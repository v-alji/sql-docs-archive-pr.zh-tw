---
title: 集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce49c57aad5da52dabba32a0f3fb9b6f4f45b209
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699997"
---
# <a name="collections-master-data-services"></a><span data-ttu-id="16aed-102">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="16aed-102">Collections (Master Data Services)</span></span>
  <span data-ttu-id="16aed-103">集合是一組來自單一實體的分葉成員和合併成員。</span><span class="sxs-lookup"><span data-stu-id="16aed-103">A collection is a group of leaf and consolidated members from a single entity.</span></span> <span data-ttu-id="16aed-104">當您不需要完整的階層，而且想要檢視成員的不同群組進行報告或分析時，或當您不需要建立分類時，請使用集合。</span><span class="sxs-lookup"><span data-stu-id="16aed-104">Use collections when you do not need a complete hierarchy and you want to view different groupings of members for reporting or analysis, or when you need to create a taxonomy.</span></span>  
  
## <a name="what-collections-contain"></a><span data-ttu-id="16aed-105">集合包含的內容</span><span class="sxs-lookup"><span data-stu-id="16aed-105">What Collections Contain</span></span>  
 <span data-ttu-id="16aed-106">集合不會限制您可以包含的成員數目或類型，前提是這些成員都在同一實體內。</span><span class="sxs-lookup"><span data-stu-id="16aed-106">Collections do not limit the number or type of members you can include, as long as the members are within the same entity.</span></span> <span data-ttu-id="16aed-107">集合可以包含多個強制和非強制明確階層中的分葉成員與合併成員。</span><span class="sxs-lookup"><span data-stu-id="16aed-107">A collection can contain leaf and consolidated members from multiple mandatory and non-mandatory explicit hierarchies.</span></span>  
  
 <span data-ttu-id="16aed-108">建立集合時，建立的不是階層結構，而是成員的一般清單。</span><span class="sxs-lookup"><span data-stu-id="16aed-108">When you create a collection, you are not creating a hierarchical structure; you are creating a flat list of members.</span></span> <span data-ttu-id="16aed-109">當您從某個階層中選取一個節點，並將其加入至集合時，您所選取的合併成員是加入至集合中的唯一成員。</span><span class="sxs-lookup"><span data-stu-id="16aed-109">When you select a node from a hierarchy and add it to the collection, the consolidated member you selected is the only member added to the collection.</span></span>  
  
 <span data-ttu-id="16aed-110">集合也可以包含其他集合。</span><span class="sxs-lookup"><span data-stu-id="16aed-110">A collection can also contain other collections.</span></span> <span data-ttu-id="16aed-111">您可以使用集合的集合來建立分類。</span><span class="sxs-lookup"><span data-stu-id="16aed-111">You can use collections of collections to create taxonomies.</span></span>  
  
 <span data-ttu-id="16aed-112">當您建立集合時，您會自動列為擁有者。</span><span class="sxs-lookup"><span data-stu-id="16aed-112">When you create a collection you are automatically listed as the owner.</span></span> <span data-ttu-id="16aed-113">如果您是管理員，可以視需要建立集合的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="16aed-113">If you are an administrator, you can create other attributes for your collection as needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16aed-114">在您可以建立集合之前，實體必須啟用明確階層。</span><span class="sxs-lookup"><span data-stu-id="16aed-114">Before you can create a collection, the entity must be enabled for explicit hierarchies.</span></span> <span data-ttu-id="16aed-115">如需詳細資訊，請參閱[啟用明確階層和集合的實體 &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="16aed-115">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
## <a name="subscription-views-for-collections"></a><span data-ttu-id="16aed-116">集合的訂閱檢視</span><span class="sxs-lookup"><span data-stu-id="16aed-116">Subscription Views for Collections</span></span>  
 <span data-ttu-id="16aed-117">顯示集合的訂閱檢視有兩種。</span><span class="sxs-lookup"><span data-stu-id="16aed-117">There are two types of subscription views that show collections.</span></span> <span data-ttu-id="16aed-118">[集合屬性]\*\*\*\* 格式會顯示集合的清單，以及與集合相關的任何屬性 (如描述或擁有者)。</span><span class="sxs-lookup"><span data-stu-id="16aed-118">The **Collection attributes** format shows a list of collections and any attributes related to the collections (like description or owner).</span></span> <span data-ttu-id="16aed-119">[集合]\*\*\*\* 格式會顯示所有集合中的所有成員，以及每個成員加權和排序次序。</span><span class="sxs-lookup"><span data-stu-id="16aed-119">The **Collections** format shows all members in all collections, as well as each members weight and sort order.</span></span> <span data-ttu-id="16aed-120">如需詳細資訊，請參閱[匯出資料 &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="16aed-120">For more information, see [Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md).</span></span>  
  
 <span data-ttu-id="16aed-121">如果您為某個集合中的特定成員設定加權值，這些值則可以在相關的訂閱檢視中使用。</span><span class="sxs-lookup"><span data-stu-id="16aed-121">If you set weight values for specific members in a collection, these values are available in related subscription views.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="16aed-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="16aed-122">Related Tasks</span></span>  
  
|<span data-ttu-id="16aed-123">工作描述</span><span class="sxs-lookup"><span data-stu-id="16aed-123">Task Description</span></span>|<span data-ttu-id="16aed-124">主題</span><span class="sxs-lookup"><span data-stu-id="16aed-124">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="16aed-125">啟用明確階層和集合的實體。</span><span class="sxs-lookup"><span data-stu-id="16aed-125">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="16aed-126">啟用明確階層和集合的實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="16aed-126">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|<span data-ttu-id="16aed-127">建立新集合。</span><span class="sxs-lookup"><span data-stu-id="16aed-127">Create a new collection.</span></span>|[<span data-ttu-id="16aed-128">建立集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="16aed-128">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)|  
|<span data-ttu-id="16aed-129">將成員加入至現有的集合。</span><span class="sxs-lookup"><span data-stu-id="16aed-129">Add members to an existing collection.</span></span>|[<span data-ttu-id="16aed-130">將成員加入至集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="16aed-130">Add Members to a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="16aed-131">相關內容</span><span class="sxs-lookup"><span data-stu-id="16aed-131">Related Content</span></span>  
  
-   [<span data-ttu-id="16aed-132">明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="16aed-132">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [<span data-ttu-id="16aed-133">將資料匯出 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="16aed-133">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)  
  
  
