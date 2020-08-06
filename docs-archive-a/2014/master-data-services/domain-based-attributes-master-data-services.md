---
title: 網域屬性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9182974923848d49ed3e9ecfb58a14949784a2c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607418"
---
# <a name="domain-based-attributes-master-data-services"></a><span data-ttu-id="10b32-102">網域屬性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="10b32-102">Domain-Based Attributes (Master Data Services)</span></span>
  <span data-ttu-id="10b32-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，網域屬性是由其他實體成員擴展其值的屬性。</span><span class="sxs-lookup"><span data-stu-id="10b32-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a domain-based attribute is an attribute with values that are populated by members from another entity.</span></span> <span data-ttu-id="10b32-104">您可以將網域屬性視為受條件約束的清單，網域屬性會讓使用者無法輸入無效的屬性值。</span><span class="sxs-lookup"><span data-stu-id="10b32-104">You can think of a domain-based attribute as a constrained list; domain-based attributes prevent users from entering attribute values that are not valid.</span></span> <span data-ttu-id="10b32-105">若要選取屬性值，使用者必須從清單中挑選。</span><span class="sxs-lookup"><span data-stu-id="10b32-105">To select an attribute value, the user must pick from a list.</span></span>

## <a name="domain-based-attribute-example"></a><span data-ttu-id="10b32-106">網域屬性範例</span><span class="sxs-lookup"><span data-stu-id="10b32-106">Domain-Based Attribute Example</span></span>
 <span data-ttu-id="10b32-107">在下圖中，Product 實體有稱為 Subcategory 的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="10b32-107">In the following image, the Product entity has a domain-based attribute called Subcategory.</span></span> <span data-ttu-id="10b32-108">Subcategory 屬性是由 Subcategory 實體的值擴展。</span><span class="sxs-lookup"><span data-stu-id="10b32-108">The Subcategory attribute is populated by values from the Subcategory entity.</span></span>

 <span data-ttu-id="10b32-109">Subcategory 實體有稱為 Category 的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="10b32-109">The Subcategory entity has a domain-based attribute called Category.</span></span> <span data-ttu-id="10b32-110">Category 屬性是由 Category 實體的值擴展。</span><span class="sxs-lookup"><span data-stu-id="10b32-110">The Category attribute is populated by values from the Category entity.</span></span>

 <span data-ttu-id="10b32-111">![實體中的網域屬性](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "實體中的網域屬性")</span><span class="sxs-lookup"><span data-stu-id="10b32-111">![Domain-Based Attributes in an Entity](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Domain-Based Attributes in an Entity")</span></span>

## <a name="use-same-entity-for-multiple-domain-based-attributes"></a><span data-ttu-id="10b32-112">將相同的實體用於多個網域屬性</span><span class="sxs-lookup"><span data-stu-id="10b32-112">Use Same Entity for Multiple Domain-Based Attributes</span></span>
 <span data-ttu-id="10b32-113">同一個實體可以當做多個實體的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="10b32-113">You can use the same entity as a domain-based attribute of multiple entities.</span></span> <span data-ttu-id="10b32-114">例如，您可以建立稱為 YesNoIndicator 的實體，其具有成員：Yes、No 和 Maybe。</span><span class="sxs-lookup"><span data-stu-id="10b32-114">For example, you can create an entity called YesNoIndicator with the members: Yes, No, and Maybe.</span></span> <span data-ttu-id="10b32-115">您可以建立名稱為 InStock 的網域屬性，並且使用 YesNoIndicator 實體做為來源。</span><span class="sxs-lookup"><span data-stu-id="10b32-115">You can create a domain-based attribute named InStock and use the YesNoIndicator entity as the source.</span></span> <span data-ttu-id="10b32-116">您也可以建立名稱為 Approved 的其他網域屬性，並且使用 YesNoIndicator 實體做為來源。</span><span class="sxs-lookup"><span data-stu-id="10b32-116">You can also create another domain-based attribute named Approved and use the YesNoIndicator entity as a source.</span></span> <span data-ttu-id="10b32-117">每次您要使用者從 YesNoIndicator 實體成員清單中選擇時，都可以將此實體當做網域屬性使用。</span><span class="sxs-lookup"><span data-stu-id="10b32-117">Any time you want users to choose from a list of the YesNoIndicator entity's members, you can use the entity as a domain-based attribute.</span></span>

## <a name="domain-based-attributes-form-derived-hierarchies"></a><span data-ttu-id="10b32-118">網域屬性可形成衍生階層</span><span class="sxs-lookup"><span data-stu-id="10b32-118">Domain-Based Attributes Form Derived Hierarchies</span></span>
 <span data-ttu-id="10b32-119">網域屬性關聯性是衍生階層的基礎。</span><span class="sxs-lookup"><span data-stu-id="10b32-119">Domain-based attribute relationships are the basis for derived hierarchies.</span></span> <span data-ttu-id="10b32-120">如需詳細資訊，請參閱 [衍生階層 &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="10b32-120">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="10b32-121">相關工作</span><span class="sxs-lookup"><span data-stu-id="10b32-121">Related Tasks</span></span>

|<span data-ttu-id="10b32-122">工作描述</span><span class="sxs-lookup"><span data-stu-id="10b32-122">Task Description</span></span>|<span data-ttu-id="10b32-123">主題</span><span class="sxs-lookup"><span data-stu-id="10b32-123">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="10b32-124">從現有實體來源中建立新的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="10b32-124">Create a new domain-based attribute that is sourced from an existing entity.</span></span>|[<span data-ttu-id="10b32-125">建立網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="10b32-125">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|
|<span data-ttu-id="10b32-126">建立新實體。</span><span class="sxs-lookup"><span data-stu-id="10b32-126">Create a new entity.</span></span>|[<span data-ttu-id="10b32-127">建立實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="10b32-127">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="10b32-128">相關內容</span><span class="sxs-lookup"><span data-stu-id="10b32-128">Related Content</span></span>

-   [<span data-ttu-id="10b32-129">衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="10b32-129">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="10b32-130">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="10b32-130">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)

-   [<span data-ttu-id="10b32-131">實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="10b32-131">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)


