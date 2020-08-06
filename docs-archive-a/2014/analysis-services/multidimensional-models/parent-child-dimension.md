---
title: 父子式階層 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], parent-child
- dimensions [Analysis Services], parent-child
- parent attributes [Analysis Services]
- data members [Analysis Services]
- hierarchies [Analysis Services], multilevel
- self-joins
- self-referencing relationships
- members [Analysis Services], data
- parent-child dimensions [Analysis Services]
ms.assetid: 4657f5dc-d88e-48d2-a448-08f79bc89546
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08641e9ba17e6ad2e2f4112e01073d448aa8564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709978"
---
# <a name="parent-child-hierarchy"></a><span data-ttu-id="10f50-102">父子式階層</span><span class="sxs-lookup"><span data-stu-id="10f50-102">Parent-Child Hierarchy</span></span>
  <span data-ttu-id="10f50-103">父子式階層是位於包含父屬性之標準維度中的階層。</span><span class="sxs-lookup"><span data-stu-id="10f50-103">A parent-child hierarchy is a hierarchy in a standard dimension that contains a parent attribute.</span></span> <span data-ttu-id="10f50-104">父屬性描述維度主資料表內的「自我參考關聯性」\*\* 或「自我聯結」\*\*。</span><span class="sxs-lookup"><span data-stu-id="10f50-104">A parent attribute describes a *self-referencing relationship*, or *self-join*, within a dimension main table.</span></span> <span data-ttu-id="10f50-105">父子式階層是由單一父屬性所建構的。</span><span class="sxs-lookup"><span data-stu-id="10f50-105">Parent-child hierarchies are constructed from a single parent attribute.</span></span> <span data-ttu-id="10f50-106">因為階層中的層級是從與父屬性相關之成員間的父子式關聯性衍生而來，所以只會將一個層級指派給父子式階層。</span><span class="sxs-lookup"><span data-stu-id="10f50-106">Only one level is assigned to a parent-child hierarchy, because the levels present in the hierarchy are drawn from the parent-child relationships between members associated with the parent attribute.</span></span> <span data-ttu-id="10f50-107">父子式階層中之成員的位置是由父屬性 (Attribute) 的 `KeyColumns` 和 `RootMemberIf` 屬性 (Property) 所決定，而層級中之成員的位置是由父屬性 (Attribute) 的 `OrderBy` 屬性 (Property) 所決定。</span><span class="sxs-lookup"><span data-stu-id="10f50-107">The position of a member in a parent-child hierarchy is determined by the `KeyColumns` and `RootMemberIf` properties of the parent attribute, whereas the position of a member in a level is determined by the `OrderBy` property of the parent attribute.</span></span> <span data-ttu-id="10f50-108">如需屬性 (attribute) 之屬性 (property) 的詳細資訊，請參閱 [屬性和屬性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="10f50-108">For more information about attribute properties, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
 <span data-ttu-id="10f50-109">因為在父子式階層內有層級之間的父子式關聯性，所以除了有彙總自子成員的資料以外，部分非分葉成員還可能會有衍生自基礎資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="10f50-109">Because of parent-child relationships between levels in a parent-child hierarchy, some nonleaf members can also have data derived from underlying data sources, in addition to data aggregated from child members.</span></span>  
  
## <a name="dimension-schema"></a><span data-ttu-id="10f50-110">維度結構描述</span><span class="sxs-lookup"><span data-stu-id="10f50-110">Dimension Schema</span></span>  
 <span data-ttu-id="10f50-111">父子式階層的維度結構描述，相依於維度主資料表上所顯示的自我參考關聯性。</span><span class="sxs-lookup"><span data-stu-id="10f50-111">The dimension schema of a parent-child hierarchy depends on a self-referencing relationship present on the dimension main table.</span></span> <span data-ttu-id="10f50-112">例如，下圖說明 **範例資料庫中的** DimOrganization [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] 維度主資料表。</span><span class="sxs-lookup"><span data-stu-id="10f50-112">For example, the following diagram illustrates the **DimOrganization** dimension main table in the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] sample database.</span></span>  
  
 <span data-ttu-id="10f50-113">![DimOrganization 資料表中的自我參考聯結](../dev-guide/media/dimorganization.gif "DimOrganization 資料表中的自我參考聯結")</span><span class="sxs-lookup"><span data-stu-id="10f50-113">![Self-referencing join in DimOrganization table](../dev-guide/media/dimorganization.gif "Self-referencing join in DimOrganization table")</span></span>  
  
 <span data-ttu-id="10f50-114">在這份維度資料表中， **ParentOrganizationKey** 資料行與 **OrganizationKey** 主索引鍵資料行具有外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="10f50-114">In this dimension table, the **ParentOrganizationKey** column has a foreign key relationship with the **OrganizationKey** primary key column.</span></span> <span data-ttu-id="10f50-115">換句話說，此資料表中的每一個記錄均可透過父子式關聯性與資料表中的另一個記錄相關。</span><span class="sxs-lookup"><span data-stu-id="10f50-115">In other words, each record in this table can be related through a parent-child relationship with another record in the table.</span></span> <span data-ttu-id="10f50-116">這種自我聯結通常用來呈現組織實體資料 (例如，部門內之員工的管理結構)。</span><span class="sxs-lookup"><span data-stu-id="10f50-116">This kind of self-join is generally used to represent organization entity data, such as the management structure of employees in a department.</span></span>  
  
## <a name="hierarchies-and-levels"></a><span data-ttu-id="10f50-117">階層和層級</span><span class="sxs-lookup"><span data-stu-id="10f50-117">Hierarchies and Levels</span></span>  
 <span data-ttu-id="10f50-118">沒有父子式關聯性的維度是藉由群組和排序屬性來建構階層。</span><span class="sxs-lookup"><span data-stu-id="10f50-118">Dimensions that do not have a parent-child relationship construct hierarchies by grouping and ordering attributes.</span></span> <span data-ttu-id="10f50-119">這些維度會從屬性名稱衍生其階層的層級名稱。</span><span class="sxs-lookup"><span data-stu-id="10f50-119">These dimensions derive the level names for their hierarchies from the attribute names.</span></span>  
  
 <span data-ttu-id="10f50-120">然而，父子式維度會檢查維度主資料表所含的資料，然後評估資料表中之記錄間的父子式關聯性，以建構父子式階層。</span><span class="sxs-lookup"><span data-stu-id="10f50-120">However, parent-child dimensions construct parent-child hierarchies by examining the data that the dimension main table contains, and then evaluating the parent-child relationships between the records in the table.</span></span> <span data-ttu-id="10f50-121">如需父子式階層的詳細資訊，請參閱 [使用者階層](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="10f50-121">For more information about parent-child hierarchies, see [User Hierarchies](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md).</span></span>  
  
 <span data-ttu-id="10f50-122">父子式階層並不會從用來建立階層的屬性中，衍生出父子式階層中的層級名稱。</span><span class="sxs-lookup"><span data-stu-id="10f50-122">Parent-child hierarchies do not derive the names for the levels in a parent-child hierarchy from the attributes that are used to create the hierarchy.</span></span> <span data-ttu-id="10f50-123">相反地，這些維度會使用命名範本自動建立層級名稱，也就是您可以在父屬性層級指定的字串運算式，以控制屬性如何產生屬性階層。</span><span class="sxs-lookup"><span data-stu-id="10f50-123">Instead, these dimensions create level names automatically by using a naming template-a string expression you can specify at the level of the parent attribute that controls how the attribute generates the attribute hierarchy.</span></span> <span data-ttu-id="10f50-124">如需如何設定父屬性之命名範本的詳細資訊，請參閱 [屬性和屬性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="10f50-124">For more information about how to set the naming template for a parent attribute, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="data-members"></a><span data-ttu-id="10f50-125">資料成員</span><span class="sxs-lookup"><span data-stu-id="10f50-125">Data Members</span></span>  
 <span data-ttu-id="10f50-126">通常，維度中的分葉成員會包含直接衍生自基礎資料來源的資料，而非分葉成員則會包含衍生自子成員上所執行之彙總的資料。</span><span class="sxs-lookup"><span data-stu-id="10f50-126">Typically, leaf members in a dimension contain data derived directly from underlying data sources, whereas nonleaf members contain data derived from aggregations performed on child members.</span></span>  
  
 <span data-ttu-id="10f50-127">但是父子式階層除了彙總自子成員的資料以外，也可能會有部分非分葉成員的資料是衍生自基礎資料來源。</span><span class="sxs-lookup"><span data-stu-id="10f50-127">However, parent-child hierarchies might have some nonleaf members whose data is derived from underlying data sources, in addition to data aggregated from child members.</span></span> <span data-ttu-id="10f50-128">針對父子式階層中的這些非分葉成員，可以建立特殊、由系統產生的子成員，其中包含基礎事實資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="10f50-128">For these nonleaf members in a parent-child hierarchy, special system-generated child members can be created that contain the underlying fact table data.</span></span> <span data-ttu-id="10f50-129">這些特殊子成員稱為 *資料成員*，包含與非分葉成員直接相關聯而且與非分葉成員的下階導出之摘要值無關的值。</span><span class="sxs-lookup"><span data-stu-id="10f50-129">Referred to as *data members*, these special child members contain a value that is directly associated with a nonleaf member and is independent of the summary value calculated from the descendants of the nonleaf member.</span></span> <span data-ttu-id="10f50-130">如需資料成員的詳細資訊，請參閱 [父子式階層中的屬性](parent-child-dimension-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="10f50-130">For more information about data members, see [Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f50-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10f50-131">See Also</span></span>  
 <span data-ttu-id="10f50-132">[父子式階層中的屬性](parent-child-dimension-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="10f50-132">[Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md) </span></span>  
 [<span data-ttu-id="10f50-133">資料庫維度屬性</span><span class="sxs-lookup"><span data-stu-id="10f50-133">Database Dimension Properties</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)  
  
  
