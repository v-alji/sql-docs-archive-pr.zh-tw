---
title: 具有明確頂層的衍生階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d2460ddf098f0547c2876dd9689f5d2bf9b461a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592725"
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a><span data-ttu-id="e8adf-102">具有明確頂層的衍生階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e8adf-102">Derived Hierarchies with Explicit Caps (Master Data Services)</span></span>
  <span data-ttu-id="e8adf-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當明確階層的層級當做衍生階層的最上層使用時，稱為具有明確頂層的衍生階層。</span><span class="sxs-lookup"><span data-stu-id="e8adf-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when the levels from an explicit hierarchy are used as the top levels of a derived hierarchy, this is called a derived hierarchy with an explicit cap.</span></span>

 <span data-ttu-id="e8adf-104">明確階層必須是以衍生階層最上方之實體的相同實體為基礎。</span><span class="sxs-lookup"><span data-stu-id="e8adf-104">The explicit hierarchy must be based on the same entity as the entity at the top of the derived hierarchy.</span></span>

 <span data-ttu-id="e8adf-105">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者介面 (UI) 中，您可以將明確階層拖曳至衍生階層最上方，以建立此階層類型。</span><span class="sxs-lookup"><span data-stu-id="e8adf-105">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), you create this type of hierarchy by dragging an explicit hierarchy to the top of a derived hierarchy.</span></span>

 <span data-ttu-id="e8adf-106">![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")</span><span class="sxs-lookup"><span data-stu-id="e8adf-106">![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")</span></span>

## <a name="derived-hierarchy-with-explicit-cap-example"></a><span data-ttu-id="e8adf-107">具有明確頂層的衍生階層範例</span><span class="sxs-lookup"><span data-stu-id="e8adf-107">Derived Hierarchy with Explicit Cap Example</span></span>
 <span data-ttu-id="e8adf-108">在這個範例中，明確階層中的成員是來自 Subcategory 實體。</span><span class="sxs-lookup"><span data-stu-id="e8adf-108">In this example, the members in the explicit hierarchy are from the Subcategory entity.</span></span> <span data-ttu-id="e8adf-109">在衍生階層中，最上層成員也是來自 Subcategory 實體。</span><span class="sxs-lookup"><span data-stu-id="e8adf-109">In the derived hierarchy, the top-level members are also from the Subcategory entity.</span></span>

 <span data-ttu-id="e8adf-110">![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")</span><span class="sxs-lookup"><span data-stu-id="e8adf-110">![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")</span></span>

 <span data-ttu-id="e8adf-111">透過在衍生階層最上方使用明確階層，衍生階層會變得不完全。</span><span class="sxs-lookup"><span data-stu-id="e8adf-111">By using the explicit hierarchy at the top of a derived hierarchy, the derived hierarchy becomes ragged.</span></span>

## <a name="rules"></a><span data-ttu-id="e8adf-112">規則</span><span class="sxs-lookup"><span data-stu-id="e8adf-112">Rules</span></span>

-   <span data-ttu-id="e8adf-113">具有明確頂層的衍生階層中不能有一個以上的明確階層。</span><span class="sxs-lookup"><span data-stu-id="e8adf-113">You cannot have more than one explicit hierarchy in a derived hierarchy with explicit cap.</span></span>

-   <span data-ttu-id="e8adf-114">同一個明確階層可以做為多個衍生階層的端點。</span><span class="sxs-lookup"><span data-stu-id="e8adf-114">You can use the same explicit hierarchy as a cap for multiple derived hierarchies.</span></span>

-   <span data-ttu-id="e8adf-115">不能指派階層成員權限給具有明確頂層的衍生階層。</span><span class="sxs-lookup"><span data-stu-id="e8adf-115">You cannot assign hierarchy member permissions to derived hierarchies with explicit caps.</span></span> <span data-ttu-id="e8adf-116">如果您個別指派權限給明確階層或衍生階層，此權限會同時影響這兩個階層。</span><span class="sxs-lookup"><span data-stu-id="e8adf-116">If you assign permissions to either the explicit hierarchy or the derived hierarchy individually, the permissions affect both hierarchies.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="e8adf-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="e8adf-117">Related Tasks</span></span>

|<span data-ttu-id="e8adf-118">工作描述</span><span class="sxs-lookup"><span data-stu-id="e8adf-118">Task Description</span></span>|<span data-ttu-id="e8adf-119">主題</span><span class="sxs-lookup"><span data-stu-id="e8adf-119">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="e8adf-120">建立衍生階層。</span><span class="sxs-lookup"><span data-stu-id="e8adf-120">Create a derived hierarchy.</span></span>|[<span data-ttu-id="e8adf-121">建立衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e8adf-121">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="e8adf-122">建立明確階層。</span><span class="sxs-lookup"><span data-stu-id="e8adf-122">Create an explicit hierarchy.</span></span>|[<span data-ttu-id="e8adf-123">建立明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e8adf-123">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="e8adf-124">刪除現有衍生階層。</span><span class="sxs-lookup"><span data-stu-id="e8adf-124">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="e8adf-125">刪除衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e8adf-125">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="e8adf-126">相關內容</span><span class="sxs-lookup"><span data-stu-id="e8adf-126">Related Content</span></span>

-   [<span data-ttu-id="e8adf-127">衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e8adf-127">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="e8adf-128">明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e8adf-128">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)


