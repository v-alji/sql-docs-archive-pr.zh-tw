---
title: 實體 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], about entities
- entities [Master Data Services]
ms.assetid: 0af057d5-6b73-472b-99eb-9f5eb61a9b5b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 220dfd87622f2f976070279dd44bd0732917f952
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687001"
---
# <a name="entities-master-data-services"></a><span data-ttu-id="720df-102">實體 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="720df-102">Entities (Master Data Services)</span></span>
  <span data-ttu-id="720df-103">實體是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 模型中包含的物件。</span><span class="sxs-lookup"><span data-stu-id="720df-103">Entities are objects that are contained in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] models.</span></span> <span data-ttu-id="720df-104">每個實體都含有會員，也就是您所管理之主要資料的資料列。</span><span class="sxs-lookup"><span data-stu-id="720df-104">Each entity contains members, which are the rows of master data that you manage.</span></span>  
  
## <a name="how-many-entities-are-appropriate"></a><span data-ttu-id="720df-105">多少實體才合適？</span><span class="sxs-lookup"><span data-stu-id="720df-105">How Many Entities are Appropriate?</span></span>  
 <span data-ttu-id="720df-106">模型可以包含任何您想要管理的實體數量。</span><span class="sxs-lookup"><span data-stu-id="720df-106">Models can contain as many entities as you want to manage.</span></span> <span data-ttu-id="720df-107">每個實體都應該將類似的資料類型群組在一起。</span><span class="sxs-lookup"><span data-stu-id="720df-107">Each entity should group a similar kind of data.</span></span> <span data-ttu-id="720df-108">例如，您可能會想要將一個實體用於您所有的公司帳戶，或是將一個實體用於員工的主要清單。</span><span class="sxs-lookup"><span data-stu-id="720df-108">For example, you might want an entity for all of your corporate accounts, or an entity for your master list of employees.</span></span>  
  
 <span data-ttu-id="720df-109">一般來說，有一個或多個中央實體對您的公司很重要，而且模型中的其他物件也與這些實體有關。</span><span class="sxs-lookup"><span data-stu-id="720df-109">Typically, there are one or more central entities that are important to your business, and to which other objects in the model relate.</span></span> <span data-ttu-id="720df-110">例如，在 Product 模型中，您可以有一個名為 Product 的中央實體，以及與其他 Product 實體相關，名為 Subcategory 和 Category 的實體。</span><span class="sxs-lookup"><span data-stu-id="720df-110">For example, in a Product model, you could have a central entity called Product and entities called Subcategory and Category that relate to the Product entity.</span></span> <span data-ttu-id="720df-111">但是，您不需要有中央實體。</span><span class="sxs-lookup"><span data-stu-id="720df-111">However, you do not need to have a central entity.</span></span> <span data-ttu-id="720df-112">依據您的需求，您可能會有數個您認為同樣重要的實體。</span><span class="sxs-lookup"><span data-stu-id="720df-112">Depending on your needs, you might have several entities that you consider to be of equal importance.</span></span>  
  
## <a name="how-entities-relate-to-other-model-objects"></a><span data-ttu-id="720df-113">實體如何與其他的模型物件相關聯</span><span class="sxs-lookup"><span data-stu-id="720df-113">How Entities Relate to Other Model Objects</span></span>  
 <span data-ttu-id="720df-114">您可以將實體視為包含主要資料的資料表，其中資料列代表成員，而資料行代表屬性。</span><span class="sxs-lookup"><span data-stu-id="720df-114">You can think of an entity as a table that contains master data, where the rows represent members and the columns represent attributes.</span></span>  
  
 <span data-ttu-id="720df-115">![以資料表表示的 Master Data Services 實體](../../2014/master-data-services/media/mds-conc-entity-table.gif "以資料表表示的 Master Data Services 實體")</span><span class="sxs-lookup"><span data-stu-id="720df-115">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>  
  
 <span data-ttu-id="720df-116">以您要管理的主要資料清單來擴展實體。</span><span class="sxs-lookup"><span data-stu-id="720df-116">You populate the entity with a list of master data that you want to manage.</span></span>  
  
 <span data-ttu-id="720df-117">實體可用來建立衍生階層，也就是以多個實體為基礎的層級型階層。</span><span class="sxs-lookup"><span data-stu-id="720df-117">Entities can be used to build derived hierarchies, which are level-based hierarchies based on multiple entities.</span></span> <span data-ttu-id="720df-118">如需詳細資訊，請參閱 [衍生階層 &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="720df-118">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).</span></span>  
  
 <span data-ttu-id="720df-119">您也可以讓實體包含明確階層 (以單一實體為基礎的不完全結構) 和集合 (成員子集的 One-off 合併)。</span><span class="sxs-lookup"><span data-stu-id="720df-119">Entities can also be enabled to contain explicit hierarchies (ragged structures based on a single entity) and collections (one-off combinations of subsets of members).</span></span> <span data-ttu-id="720df-120">如需詳細資訊，請參閱[明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) 和[集合 &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="720df-120">For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) and [Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md).</span></span>  
  
## <a name="using-entities-as-constrained-lists"></a><span data-ttu-id="720df-121">使用實體做為條件約束清單</span><span class="sxs-lookup"><span data-stu-id="720df-121">Using Entities as Constrained Lists</span></span>  
 <span data-ttu-id="720df-122">當使用者要指派屬性給實體中的成員時，您可以讓他們從條件約束的值清單中選擇。</span><span class="sxs-lookup"><span data-stu-id="720df-122">When users are assigning attributes to the members in an entity, you can have them choose from a constrained list of values.</span></span> <span data-ttu-id="720df-123">若要這麼做，您可以使用實體來擴展屬性值的清單。</span><span class="sxs-lookup"><span data-stu-id="720df-123">To do this, you use an entity to populate the list of values for the attribute.</span></span> <span data-ttu-id="720df-124">這稱為網域屬性。</span><span class="sxs-lookup"><span data-stu-id="720df-124">This is called a domain-based attribute.</span></span> <span data-ttu-id="720df-125">如需詳細資訊，請參閱 [網域屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="720df-125">For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).</span></span>  
  
## <a name="base-entities"></a><span data-ttu-id="720df-126">基底實體</span><span class="sxs-lookup"><span data-stu-id="720df-126">Base Entities</span></span>  
 <span data-ttu-id="720df-127">在模型中導覽物件時，基底實體是使用者的起始點。</span><span class="sxs-lookup"><span data-stu-id="720df-127">A base entity is a starting point for users when navigating objects in the model.</span></span> <span data-ttu-id="720df-128">基底實體可決定當使用者開啟 **[總管]** 功能區域，並按一下功能表列上的 **[總管]** 時，所呈現的畫面配置。</span><span class="sxs-lookup"><span data-stu-id="720df-128">A base entity determines the layout of the screen when a user opens the **Explorer** functional area and clicks **Explorer** on the menu bar.</span></span> <span data-ttu-id="720df-129">若要指定實體做為基底實體，請導覽至 **[系統管理]** 功能區域。</span><span class="sxs-lookup"><span data-stu-id="720df-129">To specify an entity as a base entity, navigate to the **System Administration** functional area.</span></span> <span data-ttu-id="720df-130">在 **[模型檢視]** 頁面上，將實體從右邊的樹狀控制，拖曳至左邊樹狀控制中的模型名稱。</span><span class="sxs-lookup"><span data-stu-id="720df-130">On the **Model View** page, drag the entity from the tree control on the right to the name of the model in the tree control on the left.</span></span>  
  
## <a name="entity-security"></a><span data-ttu-id="720df-131">實體安全性</span><span class="sxs-lookup"><span data-stu-id="720df-131">Entity Security</span></span>  
 <span data-ttu-id="720df-132">您可以授予使用者實體的權限，包括相關的模型物件。</span><span class="sxs-lookup"><span data-stu-id="720df-132">You can give users permission to an entity, which includes related model objects.</span></span> <span data-ttu-id="720df-133">如需詳細資訊，請參閱[實體權限 &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="720df-133">For more information, see [Entity Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md).</span></span>  
  
## <a name="entity-examples"></a><span data-ttu-id="720df-134">實體範例</span><span class="sxs-lookup"><span data-stu-id="720df-134">Entity Examples</span></span>  
 <span data-ttu-id="720df-135">下列範例顯示具有下列屬性的實體：Name、Code、Subcategory、StandardCost、ListPrice 和 FilePhoto。</span><span class="sxs-lookup"><span data-stu-id="720df-135">The following example shows an entity that has these attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto.</span></span> <span data-ttu-id="720df-136">這些屬性描述成員。</span><span class="sxs-lookup"><span data-stu-id="720df-136">These attributes describe the members.</span></span> <span data-ttu-id="720df-137">每個成員都是由單一資料列的屬性值來表示。</span><span class="sxs-lookup"><span data-stu-id="720df-137">Each member is represented by a single row of attribute values.</span></span>  
  
 <span data-ttu-id="720df-138">![自行車產品實體資料表](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "自行車產品實體資料表")</span><span class="sxs-lookup"><span data-stu-id="720df-138">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>  
  
 <span data-ttu-id="720df-139">在下列範例中，Product 實體是中央實體。</span><span class="sxs-lookup"><span data-stu-id="720df-139">In the following example, the Product entity is the central entity.</span></span> <span data-ttu-id="720df-140">Subcategory 實體是 Product 實體的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="720df-140">The Subcategory entity is a domain-based attribute of the Product entity.</span></span> <span data-ttu-id="720df-141">Category 實體是 Subcategory 實體的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="720df-141">The Category entity is a domain-based attribute of the Subcategory entity.</span></span> <span data-ttu-id="720df-142">StandardCost 和 ListPrice 是 Product 實體的自由格式屬性，FilePhoto 則是 Product 實體的檔案屬性。</span><span class="sxs-lookup"><span data-stu-id="720df-142">StandardCost and ListPrice are free-form attributes of the Product entity, and FilePhoto is a file attribute of the Product entity.</span></span>  
  
 <span data-ttu-id="720df-143">![產品實體樹狀結構](../../2014/master-data-services/media/mds-conc-entity-ui.gif "產品實體樹狀結構")</span><span class="sxs-lookup"><span data-stu-id="720df-143">![Product Entity Tree Structure](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Product Entity Tree Structure")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="720df-144">這是以 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者介面 (UI) 為基礎的範例。</span><span class="sxs-lookup"><span data-stu-id="720df-144">This is an example based on the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI).</span></span> <span data-ttu-id="720df-145">階層樹狀結構會顯示實體與網域屬性之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="720df-145">The hierarchical tree structure shows relationships between entities and domain-based attributes.</span></span> <span data-ttu-id="720df-146">這是為了顯示關聯性，而不是為了表示重要性層級。</span><span class="sxs-lookup"><span data-stu-id="720df-146">It is intended to show relationships rather than represent levels of importance.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="720df-147">相關工作</span><span class="sxs-lookup"><span data-stu-id="720df-147">Related Tasks</span></span>  
  
|<span data-ttu-id="720df-148">工作描述</span><span class="sxs-lookup"><span data-stu-id="720df-148">Task Description</span></span>|<span data-ttu-id="720df-149">主題</span><span class="sxs-lookup"><span data-stu-id="720df-149">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="720df-150">建立新實體。</span><span class="sxs-lookup"><span data-stu-id="720df-150">Create a new entity.</span></span>|[<span data-ttu-id="720df-151">建立實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="720df-151">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)|  
|<span data-ttu-id="720df-152">指定實體可以包含明確階層和集合。</span><span class="sxs-lookup"><span data-stu-id="720df-152">Specify that an entity can contain explicit hierarchies and collections.</span></span>|[<span data-ttu-id="720df-153">啟用明確階層和集合的實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="720df-153">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|<span data-ttu-id="720df-154">變更現有實體的名稱。</span><span class="sxs-lookup"><span data-stu-id="720df-154">Change the name of an existing entity.</span></span>|[<span data-ttu-id="720df-155">變更機構名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="720df-155">Change an Entity Name &#40;Master Data Services&#41;</span></span>](edit-an-entity-master-data-services.md)|  
|<span data-ttu-id="720df-156">刪除現有實體。</span><span class="sxs-lookup"><span data-stu-id="720df-156">Delete an existing entity.</span></span>|[<span data-ttu-id="720df-157">刪除實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="720df-157">Delete an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-entity-master-data-services.md)|  
|<span data-ttu-id="720df-158">將權限指派給實體。</span><span class="sxs-lookup"><span data-stu-id="720df-158">Assign permission to entities.</span></span>|[<span data-ttu-id="720df-159">指派模型物件權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="720df-159">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="720df-160">相關內容</span><span class="sxs-lookup"><span data-stu-id="720df-160">Related Content</span></span>  
  
-   [<span data-ttu-id="720df-161">模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="720df-161">Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/models-master-data-services.md)  
  
-   [<span data-ttu-id="720df-162">成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="720df-162">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
-   [<span data-ttu-id="720df-163">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="720df-163">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
