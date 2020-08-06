---
title: 屬性關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- member properties [Analysis Services], attribute relationships
- security [Analysis Services], properties
- PROPERTIES keyword
- storage [Analysis Services], attribute relationships
- natural hierarchies [Analysis Services]
- dimensions [Analysis Services], member properties
- queries [MDX], attribute relationships
- user-defined hierarchies [Analysis Services]
- attributes [Analysis Services], relationships
- member properties [Analysis Services]
- members [Analysis Services], attribute relationships
- storing data [Analysis Services], attribute relationships
- relationships [Analysis Services], attributes
ms.assetid: 2491422a-4cf5-4b23-b6ab-289222b22ce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 122638a2728a8a85ee58661196797383da20eef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702028"
---
# <a name="attribute-relationships"></a><span data-ttu-id="c2880-102">屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="c2880-102">Attribute Relationships</span></span>
  <span data-ttu-id="c2880-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，維度內的屬性永遠都是直接或間接與索引鍵屬性相關。</span><span class="sxs-lookup"><span data-stu-id="c2880-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes within a dimension are always related either directly or indirectly to the key attribute.</span></span> <span data-ttu-id="c2880-104">當您根據所有維度屬性都是衍生自相同關聯式資料表的星狀結構描述來定義維度時，便會在索引鍵屬性和維度的每個非索引鍵屬性之間，自動定義屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2880-104">When you define a dimension based on a star schema, which is where all dimension attributes are derived from the same relational table, an attribute relationship is automatically defined between the key attribute and each non-key attribute of the dimension.</span></span> <span data-ttu-id="c2880-105">而根據維度屬性是衍生自多個相關資料表的雪花式結構描述來定義維度時，便會自動定義下列的屬性關聯性：</span><span class="sxs-lookup"><span data-stu-id="c2880-105">When you define a dimension based on a snowflake schema, which is where dimension attributes are derived from multiple related tables, an attribute relationship is automatically defined as follows:</span></span>  
  
-   <span data-ttu-id="c2880-106">索引鍵屬性和繫結到主維度資料表之資料行的每個非索引鍵屬性之間。</span><span class="sxs-lookup"><span data-stu-id="c2880-106">Between the key attribute and each non-key attribute bound to columns in the main dimension table.</span></span>  
  
-   <span data-ttu-id="c2880-107">索引鍵屬性和繫結到連結基礎維度資料表之次要資料表的外部索引鍵屬性之間。</span><span class="sxs-lookup"><span data-stu-id="c2880-107">Between the key attribute and the attribute bound to the foreign key in the secondary table that links the underlying dimension tables.</span></span>  
  
-   <span data-ttu-id="c2880-108">在繫結到次要資料表之外部索引鍵的屬性和繫結到次要資料表中之資料行的非索引鍵屬性之間。</span><span class="sxs-lookup"><span data-stu-id="c2880-108">Between the attribute bound to foreign key in the secondary table and each non-key attribute bound to columns from the secondary table.</span></span>  
  
 <span data-ttu-id="c2880-109">然而，您可能會需要變更這些預設的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2880-109">However, there are a number of reasons why you might want to change these default attribute relationships.</span></span> <span data-ttu-id="c2880-110">例如，您可能會想要定義自然階層、自訂排序順序或依據非索引鍵屬性的維度資料粒度。</span><span class="sxs-lookup"><span data-stu-id="c2880-110">For example, you might want to define a natural hierarchy, a custom sort order, or dimension granularity based on a non-key attribute.</span></span> <span data-ttu-id="c2880-111">如需詳細資訊，請參閱[維度屬性屬性參考](../multidimensional-models/dimension-attribute-properties-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="c2880-111">For more information, see [Dimension Attribute Properties Reference](../multidimensional-models/dimension-attribute-properties-reference.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2880-112">在多維度運算式 (MDX) 中，屬性關聯性就是所謂的成員屬性。</span><span class="sxs-lookup"><span data-stu-id="c2880-112">Attribute relationships are known in Multidimensional Expressions (MDX) as member properties.</span></span>  
  
## <a name="natural-hierarchy-relationships"></a><span data-ttu-id="c2880-113">自然階層關聯性</span><span class="sxs-lookup"><span data-stu-id="c2880-113">Natural Hierarchy Relationships</span></span>  
 <span data-ttu-id="c2880-114">當使用者自訂階層中所含的每一個屬性有一對多的關聯性，而且底下緊接著該屬性時，此階層就是自然階層。</span><span class="sxs-lookup"><span data-stu-id="c2880-114">A hierarchy is a natural hierarchy when each attribute included in the user-defined hierarchy has a one to many relationship with the attribute immediately below it.</span></span> <span data-ttu-id="c2880-115">例如，假設客戶維度所依據的關聯式來源資料表中有八個資料行：</span><span class="sxs-lookup"><span data-stu-id="c2880-115">For example, consider a Customer dimension based on a relational source table with eight columns:</span></span>  
  
-   <span data-ttu-id="c2880-116">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="c2880-116">CustomerKey</span></span>  
  
-   <span data-ttu-id="c2880-117">CustomerName</span><span class="sxs-lookup"><span data-stu-id="c2880-117">CustomerName</span></span>  
  
-   <span data-ttu-id="c2880-118">年齡</span><span class="sxs-lookup"><span data-stu-id="c2880-118">Age</span></span>  
  
-   <span data-ttu-id="c2880-119">性別</span><span class="sxs-lookup"><span data-stu-id="c2880-119">Gender</span></span>  
  
-   <span data-ttu-id="c2880-120">電子郵件</span><span class="sxs-lookup"><span data-stu-id="c2880-120">Email</span></span>  
  
-   <span data-ttu-id="c2880-121">城市</span><span class="sxs-lookup"><span data-stu-id="c2880-121">City</span></span>  
  
-   <span data-ttu-id="c2880-122">Country</span><span class="sxs-lookup"><span data-stu-id="c2880-122">Country</span></span>  
  
-   <span data-ttu-id="c2880-123">區域</span><span class="sxs-lookup"><span data-stu-id="c2880-123">Region</span></span>  
  
 <span data-ttu-id="c2880-124">對應的 Analysis Services 維度有七個屬性：</span><span class="sxs-lookup"><span data-stu-id="c2880-124">The corresponding Analysis Services dimension has seven attributes:</span></span>  
  
-   <span data-ttu-id="c2880-125">客戶 (根據 CustomerKey，使用 CustomerName 提供成員名稱)</span><span class="sxs-lookup"><span data-stu-id="c2880-125">Customer (based on CustomerKey, with CustomerName supplying member names)</span></span>  
  
-   <span data-ttu-id="c2880-126">年齡、性別、電子郵件、城市、區域、國家 (地區)</span><span class="sxs-lookup"><span data-stu-id="c2880-126">Age, Gender, Email, City, Region, Country</span></span>  
  
 <span data-ttu-id="c2880-127">代表自然階層之關聯性的強制執行方式，是在某層級的屬性以及該層級底下之層級的屬性之間建立屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2880-127">Relationships representing natural hierarchies are enforced by creating an attribute relationship between the attribute for a level and the attribute for the level below it.</span></span> <span data-ttu-id="c2880-128">若是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，這樣會指定自然關聯性與潛在彙總。</span><span class="sxs-lookup"><span data-stu-id="c2880-128">For [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], this specifies a natural relationship and potential aggregation.</span></span> <span data-ttu-id="c2880-129">在客戶維度中，國家 (地區)、區域、城市和客戶等屬性都存在著自然階層。</span><span class="sxs-lookup"><span data-stu-id="c2880-129">In the Customer dimension, a natural hierarchy exists for the Country, Region, City, and Customer attributes.</span></span> <span data-ttu-id="c2880-130">`{Country, Region, City, Customer}` 的自然階層，會藉由加入下列屬性關聯性來描述：</span><span class="sxs-lookup"><span data-stu-id="c2880-130">The natural hierarchy for `{Country, Region, City, Customer}` is described by adding the following attribute relationships:</span></span>  
  
-   <span data-ttu-id="c2880-131">國家 (地區) 屬性與區域屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2880-131">The Country attribute as an attribute relationship to the Region attribute.</span></span>  
  
-   <span data-ttu-id="c2880-132">區域屬性與城市屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2880-132">The Region attribute as an attribute relationship to the City attribute.</span></span>  
  
-   <span data-ttu-id="c2880-133">城市屬性與客戶屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="c2880-133">The City attribute as an attribute relationship to the Customer attribute.</span></span>  
  
 <span data-ttu-id="c2880-134">若要導覽 cube 中的資料，您也可以建立使用者定義階層，此階層不代表資料 (中的自然階層，稱為臨機操作*或\*\*報表*階層) 。</span><span class="sxs-lookup"><span data-stu-id="c2880-134">For navigating data in the cube, you can also create a user-defined hierarchy that does not represent a natural hierarchy in the data (which is called an *ad hoc* or *reporting* hierarchy).</span></span> <span data-ttu-id="c2880-135">例如，您可以根據 `{Age, Gender}` 建立使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="c2880-135">For example, you could create a user-defined hierarchy based on `{Age, Gender}`.</span></span> <span data-ttu-id="c2880-136">使用者不會看到這兩個階層的行為有何差異，雖然自然階層會受益于匯總和編制索引結構，也就是在來源資料中的自然關聯性的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c2880-136">Users do not see any difference in how the two hierarchies behave, although the natural hierarchy benefits from aggregating and indexing structures - hidden from the user - that account for the natural relationships in the source data.</span></span>  
  
 <span data-ttu-id="c2880-137">層級的 `SourceAttribute` 屬性 (Property) 會決定該使用哪個屬性 (Attribute) 來描述層級。</span><span class="sxs-lookup"><span data-stu-id="c2880-137">The `SourceAttribute` property of a level determines which attribute is used to describe the level.</span></span> <span data-ttu-id="c2880-138">屬性 (Attribute) 上的 `KeyColumns` 屬性 (Property) 會指定資料來源檢視中，提供成員的資料行。</span><span class="sxs-lookup"><span data-stu-id="c2880-138">The `KeyColumns` property on the attribute specifies the column in the data source view that supplies the members.</span></span> <span data-ttu-id="c2880-139">屬性 (Attribute) 上的 `NameColumn` 屬性 (Property) 可為成員指定不同的名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="c2880-139">The `NameColumn` property on the attribute can specify a different name column for the members.</span></span>  
  
 <span data-ttu-id="c2880-140">若要使用定義使用者自訂階層中的層級 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，**維度設計師**可讓您選取維度屬性、維度資料表中的資料行，或從 cube 的資料來源視圖中所包含的相關資料表中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="c2880-140">To define a level in a user-defined hierarchy using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the **Dimension Designer** allows you to select a dimension attribute, a column in a dimension table, or a column from a related table included in the data source view for the cube.</span></span> <span data-ttu-id="c2880-141">如需建立使用者定義階層的詳細資訊，請參閱[建立使用者定義](../multidimensional-models/user-defined-hierarchies-create.md)階層。</span><span class="sxs-lookup"><span data-stu-id="c2880-141">For more information about creating user-defined hierarchies, see [Create User-Defined Hierarchies](../multidimensional-models/user-defined-hierarchies-create.md).</span></span>  
  
 <span data-ttu-id="c2880-142">在 Analysis Services 中，通常會對成員的內容進行假設。</span><span class="sxs-lookup"><span data-stu-id="c2880-142">In Analysis Services, an assumption is usually made about the content of members.</span></span> <span data-ttu-id="c2880-143">分葉成員並沒有下階，且包含衍生自基礎資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="c2880-143">Leaf members have no descendents and contain data derived from underlying data sources.</span></span> <span data-ttu-id="c2880-144">非分葉成員具有下階，且包含衍生自在子成員上執行之彙總的資料。</span><span class="sxs-lookup"><span data-stu-id="c2880-144">Nonleaf members have descendents and contain data derived from aggregations performed on child members.</span></span> <span data-ttu-id="c2880-145">在彙總層級中，成員是以從屬層級的彙總為基礎。</span><span class="sxs-lookup"><span data-stu-id="c2880-145">In aggregated levels, members are based on aggregations of subordinate levels.</span></span> <span data-ttu-id="c2880-146">因此，若在層級的來源屬性 (Attribute) 上，將 `IsAggregatable` 屬性 (Property) 設定為 `False` 時，就不應加入可彙總的屬性 (Attribute) 作為其上層級。</span><span class="sxs-lookup"><span data-stu-id="c2880-146">Therefore, when the `IsAggregatable` property is set to `False` on a source attribute for a level, no aggregatable attributes should be added as levels above it.</span></span>  
  
## <a name="defining-an-attribute-relationship"></a><span data-ttu-id="c2880-147">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="c2880-147">Defining an Attribute Relationship</span></span>  
 <span data-ttu-id="c2880-148">當您建立屬性關聯性時，其主要條件約束是要確定屬性關聯性所參考的屬性，在屬性關聯性所屬的屬性中，任何成員只有一個值。</span><span class="sxs-lookup"><span data-stu-id="c2880-148">The main constraint when you create an attribute relationship is to make sure that the attribute referred to by the attribute relationship has no more than one value for any member in the attribute to which the attribute relationship belongs.</span></span> <span data-ttu-id="c2880-149">例如，如果您在城市屬性與省份屬性間定義關聯性，每個城市就只能和單一省份相關。</span><span class="sxs-lookup"><span data-stu-id="c2880-149">For example, if you define a relationship between a City attribute and a State attribute, each city can only relate to a single state.</span></span>  
  
## <a name="attribute-relationship-queries"></a><span data-ttu-id="c2880-150">屬性關聯性查詢</span><span class="sxs-lookup"><span data-stu-id="c2880-150">Attribute Relationship Queries</span></span>  
 <span data-ttu-id="c2880-151">您可以使用 MDX 查詢，利用 MDX `PROPERTIES` 陳述式的 `SELECT` 關鍵字，從屬性關聯性中擷取成員屬性形式的資料。</span><span class="sxs-lookup"><span data-stu-id="c2880-151">You can use MDX queries to retrieve data from attribute relationships, in the form of member properties, with the `PROPERTIES` keyword of the MDX `SELECT` statement.</span></span> <span data-ttu-id="c2880-152">如需如何使用 MDX 來取得成員屬性的詳細資訊，請參閱[使用成員屬性 &#40;MDX&#41;](../multidimensional-models/mdx/mdx-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c2880-152">For more information about how to use MDX to retrieve member properties, see [Using Member Properties &#40;MDX&#41;](../multidimensional-models/mdx/mdx-member-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2880-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2880-153">See Also</span></span>  
 <span data-ttu-id="c2880-154">[屬性和屬性階層](attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="c2880-154">[Attributes and Attribute Hierarchies](attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="c2880-155">[維度屬性屬性參考](../multidimensional-models/dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c2880-155">[Dimension Attribute Properties Reference](../multidimensional-models/dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="c2880-156">[使用者階層](user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="c2880-156">[User Hierarchies](user-hierarchies.md) </span></span>  
 [<span data-ttu-id="c2880-157">使用者階層屬性</span><span class="sxs-lookup"><span data-stu-id="c2880-157">User Hierarchy Properties</span></span>](user-hierarchies-properties.md)  
  
  
