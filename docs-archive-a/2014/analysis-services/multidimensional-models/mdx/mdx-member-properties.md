---
title: 使用 MDX) 的成員屬性 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b7fdf989fc23ea70be7d7863f5d4c6ac0b61d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698620"
---
# <a name="using-member-properties-mdx"></a><span data-ttu-id="40bc9-102">使用成員屬性 (MDX)</span><span class="sxs-lookup"><span data-stu-id="40bc9-102">Using Member Properties (MDX)</span></span>
  <span data-ttu-id="40bc9-103">成員屬性包含每個 Tuple 中每個成員的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="40bc9-103">Member properties cover the basic information about each member in each tuple.</span></span> <span data-ttu-id="40bc9-104">此基本資訊包括成員名稱、父層級、子系數目等等。</span><span class="sxs-lookup"><span data-stu-id="40bc9-104">This basic information includes the member name, parent level, the number of children, and so on.</span></span> <span data-ttu-id="40bc9-105">指定層級上的所有成員都能使用成員屬性。</span><span class="sxs-lookup"><span data-stu-id="40bc9-105">Member properties are available for all members at a given level.</span></span> <span data-ttu-id="40bc9-106">就組織而言，會將成員屬性視為儲存在單一維度上，且以維度方式組織的資料。</span><span class="sxs-lookup"><span data-stu-id="40bc9-106">In terms of organization, member properties are treated as dimensionally organized data, stored on a single dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40bc9-107">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，成員屬性稱為屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="40bc9-107">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], member properties are know as attribute relationships.</span></span> <span data-ttu-id="40bc9-108">如需詳細資訊，請參閱 [屬性關聯性](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="40bc9-108">For more information, see [Attribute Relationships](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
 <span data-ttu-id="40bc9-109">成員屬性不是 *「內建」* 就是 *「自訂」*：</span><span class="sxs-lookup"><span data-stu-id="40bc9-109">Member properties are either *intrinsic* or *custom*:</span></span>  
  
 <span data-ttu-id="40bc9-110">內建成員屬性</span><span class="sxs-lookup"><span data-stu-id="40bc9-110">Intrinsic member properties</span></span>  
 <span data-ttu-id="40bc9-111">當維度與層級提供其他內建維度與層級成員屬性 (如成員識別碼) 時，所有成員都會支援內建成員屬性 (例如，格式化的成員值)。</span><span class="sxs-lookup"><span data-stu-id="40bc9-111">All members support intrinsic member properties, such as the formatted value of a member, while dimensions and levels supply additional intrinsic dimension and level member properties, such as the ID of a member.</span></span>  
  
 <span data-ttu-id="40bc9-112">如需詳細資訊，請參閱[內建成員屬性 &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="40bc9-112">For more information, see [Intrinsic Member Properties &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).</span></span>  
  
 <span data-ttu-id="40bc9-113">使用者自訂成員屬性</span><span class="sxs-lookup"><span data-stu-id="40bc9-113">User-defined member properties</span></span>  
 <span data-ttu-id="40bc9-114">成員通常會擁有與之相關的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="40bc9-114">Members often have additional properties associated with them.</span></span> <span data-ttu-id="40bc9-115">例如，Products 層級可能會為每項產品提供 SKU、SRP、Weight 與 Volume 屬性。</span><span class="sxs-lookup"><span data-stu-id="40bc9-115">For example, the Products level may offer the SKU, SRP, Weight, and Volume properties for each product.</span></span> <span data-ttu-id="40bc9-116">這些屬性不是成員，但包含了有關 Products 層級上成員的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="40bc9-116">These properties are not members, but contain additional information about members at the Products level.</span></span>  
  
 <span data-ttu-id="40bc9-117">如需詳細資訊，請參閱[使用者自訂成員屬性 &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="40bc9-117">For more information, see [User-Defined Member Properties &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).</span></span>  
  
 <span data-ttu-id="40bc9-118">內建和使用者自訂成員屬性都可以透過使用 `PROPERTIES` 關鍵字或[properties](/sql/mdx/properties-mdx)函數來抓取。</span><span class="sxs-lookup"><span data-stu-id="40bc9-118">Both intrinsic and user-defined member properties can be retrieved through the use of the `PROPERTIES` keyword or the [Properties](/sql/mdx/properties-mdx) function.</span></span>  
  
## <a name="using-the-properties-keyword"></a><span data-ttu-id="40bc9-119">使用 PROPERTIES 關鍵字</span><span class="sxs-lookup"><span data-stu-id="40bc9-119">Using the PROPERTIES Keyword</span></span>  
 <span data-ttu-id="40bc9-120">`PROPERTIES` 關鍵字可以指定成員屬性，以供指定的座標軸維度使用。</span><span class="sxs-lookup"><span data-stu-id="40bc9-120">The `PROPERTIES` keyword specifies the member properties that are to be used for a given axis dimension.</span></span> <span data-ttu-id="40bc9-121">`PROPERTIES`關鍵字會內嵌在 `<axis specification>` MDX [SELECT](/sql/mdx/mdx-data-manipulation-select)語句的子句中：</span><span class="sxs-lookup"><span data-stu-id="40bc9-121">The `PROPERTIES` keyword is buried within the `<axis specification>` clause of the MDX [SELECT](/sql/mdx/mdx-data-manipulation-select) statement:</span></span>  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 <span data-ttu-id="40bc9-122">`<axis_specification>` 子句包含一個選擇性的 `<dim_props>` 子句，如以下語法所示：</span><span class="sxs-lookup"><span data-stu-id="40bc9-122">The `<axis_specification>` clause includes an optional `<dim_props>` clause, as shown in the following syntax:</span></span>  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="40bc9-123">如需 `<set>` 和 `<axis_name>` 值的詳細資訊，請參閱[指定查詢座標軸的內容 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="40bc9-123">For more information about the `<set>` and `<axis_name>` values, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
 <span data-ttu-id="40bc9-124">`<dim_props>` 子句可讓您使用 `PROPERTIES` 關鍵字，查詢維度、層級與成員屬性。</span><span class="sxs-lookup"><span data-stu-id="40bc9-124">The `<dim_props>` clause lets you query dimension, level, and member properties using the `PROPERTIES` keyword.</span></span> <span data-ttu-id="40bc9-125">以下語法顯示 `<dim_props>` 子句的格式：</span><span class="sxs-lookup"><span data-stu-id="40bc9-125">The following syntax shows the formatting of the `<dim_props>` clause:</span></span>  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 <span data-ttu-id="40bc9-126">`<property>` 語法的解析會依據您查詢的屬性而有所不同：</span><span class="sxs-lookup"><span data-stu-id="40bc9-126">The breakdown of the `<property>` syntax varies depending on the property that you are querying:</span></span>  
  
-   <span data-ttu-id="40bc9-127">可區分內容的內建成員屬性，必須在前面加上維度或層級的名稱。</span><span class="sxs-lookup"><span data-stu-id="40bc9-127">Context sensitive intrinsic member properties must be preceded with the name of the dimension or level.</span></span> <span data-ttu-id="40bc9-128">但是，不區分內容的內建成員屬性，就無法以維度或層級名稱來限定。</span><span class="sxs-lookup"><span data-stu-id="40bc9-128">However, non-context sensitive intrinsic member properties cannot be qualified by the dimension or level name.</span></span> <span data-ttu-id="40bc9-129">如需如何搭配使用關鍵字與內建成員屬性的詳細資訊 `PROPERTIES` ，請參閱[內部成員屬性 &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="40bc9-129">For more information about how to use the `PROPERTIES` keyword with intrinsic member properties, see [Intrinsic Member Properties &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).</span></span>  
  
-   <span data-ttu-id="40bc9-130">使用者自訂成員屬性應該在前面加上所屬層級的名稱。</span><span class="sxs-lookup"><span data-stu-id="40bc9-130">User-defined member properties should be preceded by the name of the level in which they reside.</span></span> <span data-ttu-id="40bc9-131">如需如何搭配使用 `PROPERTIES` 關鍵字與使用者定義成員屬性的詳細資訊，請參閱[&#40;MDX&#41;的使用者自訂成員屬性](mdx-member-properties-user-defined-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="40bc9-131">For more information about how to use the `PROPERTIES` keyword with user-defined member properties, see [User-Defined Member Properties &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40bc9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40bc9-132">See Also</span></span>  
 [<span data-ttu-id="40bc9-133">建立和使用屬性值 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="40bc9-133">Creating and Using Property Values &#40;MDX&#41;</span></span>](../../creating-and-using-property-values-mdx.md)  
  
  
