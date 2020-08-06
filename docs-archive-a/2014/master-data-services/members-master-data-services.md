---
title: 成員 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services]
- consolidated members [Master Data Services]
- consolidated members [Master Data Services], about consolidated members
- members [Master Data Services], about members
- leaf members [Master Data Services], about leaf members
- members [Master Data Services]
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 89d2edb21b58575dffc21d9a6470171251889cc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698413"
---
# <a name="members-master-data-services"></a><span data-ttu-id="a517c-102">成員 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a517c-102">Members (Master Data Services)</span></span>
  <span data-ttu-id="a517c-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，成員是指實體主要資料。</span><span class="sxs-lookup"><span data-stu-id="a517c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], members are the physical master data.</span></span> <span data-ttu-id="a517c-104">例如，成員可以是 Product 實體中的 Road-150 bike，或是 Customer 實體中的特定客戶。</span><span class="sxs-lookup"><span data-stu-id="a517c-104">For example, a member can be a Road-150 bike in a Product entity or a specific customer in a Customer entity.</span></span>

## <a name="how-members-relate-to-other-model-objects"></a><span data-ttu-id="a517c-105">成員如何與其他的模型物件相關聯</span><span class="sxs-lookup"><span data-stu-id="a517c-105">How Members Relate to Other Model Objects</span></span>
 <span data-ttu-id="a517c-106">您可以將成員視為資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="a517c-106">You can think of members as rows in a table.</span></span> <span data-ttu-id="a517c-107">相關成員包含在一個實體中，而且每個成員都由屬性值定義。</span><span class="sxs-lookup"><span data-stu-id="a517c-107">Related members are contained in an entity, and each member is defined by attribute values.</span></span>

 <span data-ttu-id="a517c-108">在此範例中，資料表代表實體、資料表中的資料列代表成員，而資料表中的資料行則代表屬性。</span><span class="sxs-lookup"><span data-stu-id="a517c-108">In this example, the table represents an entity, the rows in the table represent members, and the columns in the table represent attributes.</span></span> <span data-ttu-id="a517c-109">每個資料格代表特定成員的屬性值。</span><span class="sxs-lookup"><span data-stu-id="a517c-109">Each cell represents an attribute value for a specific member.</span></span>

 <span data-ttu-id="a517c-110">![以資料表表示的 Master Data Services 實體](../../2014/master-data-services/media/mds-conc-entity-table.gif "以資料表表示的 Master Data Services 實體")</span><span class="sxs-lookup"><span data-stu-id="a517c-110">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>

## <a name="member-types"></a><span data-ttu-id="a517c-111">成員類型</span><span class="sxs-lookup"><span data-stu-id="a517c-111">Member Types</span></span>
 <span data-ttu-id="a517c-112">有三種類型的成員：分葉成員、合併成員和集合成員。</span><span class="sxs-lookup"><span data-stu-id="a517c-112">There are three types of members: leaf members, consolidated members, and collection members.</span></span>

 <span data-ttu-id="a517c-113">分葉成員是實體中的預設成員。</span><span class="sxs-lookup"><span data-stu-id="a517c-113">Leaf members are the default members in an entity.</span></span>

-   <span data-ttu-id="a517c-114">在衍生階層中，分葉成員是唯一的成員類型。</span><span class="sxs-lookup"><span data-stu-id="a517c-114">In derived hierarchies, leaf members are the only type of member.</span></span> <span data-ttu-id="a517c-115">某個實體的分葉成員會做為另一個實體之分葉成員的父系。</span><span class="sxs-lookup"><span data-stu-id="a517c-115">Leaf members from one entity are used as parents of leaf members from another entity.</span></span>

-   <span data-ttu-id="a517c-116">在明確階層中，分葉成員是最低層級，沒有子系。</span><span class="sxs-lookup"><span data-stu-id="a517c-116">In explicit hierarchies, leaf members are the lowest level and cannot have children.</span></span>

 <span data-ttu-id="a517c-117">只有在啟用實體的明確階層和集合時，合併成員才會存在。</span><span class="sxs-lookup"><span data-stu-id="a517c-117">Consolidated members exist only when explicit hierarchies and collections are enabled for the entity.</span></span>

-   <span data-ttu-id="a517c-118">衍生階層不包含合併成員。</span><span class="sxs-lookup"><span data-stu-id="a517c-118">Derived hierarchies do not contain consolidated members.</span></span>

-   <span data-ttu-id="a517c-119">在明確階層中，合併成員可以是階層中其他成員的父系，也可以是子系。</span><span class="sxs-lookup"><span data-stu-id="a517c-119">In explicit hierarchies, consolidated members can be parents of other members within the hierarchy, or they can be children.</span></span>

## <a name="use-hierarchies-and-collections-to-organize-members"></a><span data-ttu-id="a517c-120">使用階層與集合來組織成員</span><span class="sxs-lookup"><span data-stu-id="a517c-120">Use Hierarchies and Collections to Organize Members</span></span>
 <span data-ttu-id="a517c-121">階層和集合可以用來為成員分組，以進行報告或分析。</span><span class="sxs-lookup"><span data-stu-id="a517c-121">Hierarchies and collections can be used to group members for reporting or analysis.</span></span> <span data-ttu-id="a517c-122">如需詳細資訊，請參閱 [階層 &#40;Master Data Services&#41;](hierarchies-master-data-services.md) 和 [集合 &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a517c-122">For more information, see [Hierarchies &#40;Master Data Services&#41;](hierarchies-master-data-services.md) and [Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md).</span></span>

## <a name="member-example"></a><span data-ttu-id="a517c-123">成員範例</span><span class="sxs-lookup"><span data-stu-id="a517c-123">Member Example</span></span>
 <span data-ttu-id="a517c-124">在下列範例中，每個成員是由 Name、Code、Subcategory、StandardCost、ListPrice 和 FilePhoto 屬性值所組成。</span><span class="sxs-lookup"><span data-stu-id="a517c-124">In the following example, each member is made up of a Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto attribute value.</span></span>

 <span data-ttu-id="a517c-125">![自行車產品實體資料表](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "自行車產品實體資料表")</span><span class="sxs-lookup"><span data-stu-id="a517c-125">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="a517c-126">相關工作</span><span class="sxs-lookup"><span data-stu-id="a517c-126">Related Tasks</span></span>

|<span data-ttu-id="a517c-127">工作描述</span><span class="sxs-lookup"><span data-stu-id="a517c-127">Task Description</span></span>|<span data-ttu-id="a517c-128">主題</span><span class="sxs-lookup"><span data-stu-id="a517c-128">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="a517c-129">建立新分葉成員。</span><span class="sxs-lookup"><span data-stu-id="a517c-129">Create a new leaf member.</span></span>|[<span data-ttu-id="a517c-130">建立分葉成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-130">Create a Leaf Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)|
|<span data-ttu-id="a517c-131">建立新合併成員。</span><span class="sxs-lookup"><span data-stu-id="a517c-131">Create a new consolidated member.</span></span>|[<span data-ttu-id="a517c-132">建立合併成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-132">Create a Consolidated Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)|
|<span data-ttu-id="a517c-133">刪除現有的成員或集合。</span><span class="sxs-lookup"><span data-stu-id="a517c-133">Delete an existing member or collection.</span></span>|[<span data-ttu-id="a517c-134">刪除成員或集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-134">Delete a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)|
|<span data-ttu-id="a517c-135">重新啟用刪除的成員或集合。</span><span class="sxs-lookup"><span data-stu-id="a517c-135">Reactivate a deleted member or collection.</span></span>|[<span data-ttu-id="a517c-136">重新啟用成員或集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-136">Reactivate a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)|
|<span data-ttu-id="a517c-137">更新成員的屬性值。</span><span class="sxs-lookup"><span data-stu-id="a517c-137">Update the attribute values of a member.</span></span>|[<span data-ttu-id="a517c-138">變更屬性類型 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-138">Change the Attribute Type &#40;MDS Add-in for Excel&#41;</span></span>](microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|
|<span data-ttu-id="a517c-139">在階層中移動成員。</span><span class="sxs-lookup"><span data-stu-id="a517c-139">Move members within a hierarchy.</span></span>|[<span data-ttu-id="a517c-140">在階層中移動成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-140">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="a517c-141">相關內容</span><span class="sxs-lookup"><span data-stu-id="a517c-141">Related Content</span></span>

-   [<span data-ttu-id="a517c-142">Master Data Services 概觀</span><span class="sxs-lookup"><span data-stu-id="a517c-142">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)

-   [<span data-ttu-id="a517c-143">實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-143">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)

-   [<span data-ttu-id="a517c-144">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-144">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)

-   [<span data-ttu-id="a517c-145">階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-145">Hierarchies &#40;Master Data Services&#41;</span></span>](hierarchies-master-data-services.md)

-   [<span data-ttu-id="a517c-146">集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-146">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)

-   [<span data-ttu-id="a517c-147">分葉權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-147">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)

-   [<span data-ttu-id="a517c-148">合併的許可權 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-148">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)

-   [<span data-ttu-id="a517c-149">篩選運算子 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a517c-149">Filter Operators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/filter-operators-master-data-services.md)


