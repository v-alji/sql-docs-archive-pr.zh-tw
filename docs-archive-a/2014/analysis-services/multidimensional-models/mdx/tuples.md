---
title: 元組 |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 35b629ae-b1ef-44b1-b556-96956aeb56e7
author: minewiskan
ms.author: owend
ms.openlocfilehash: c39d03d60cb66f3b2e26b2e660bd85f4e5e9d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705573"
---
# <a name="tuples"></a><span data-ttu-id="c8124-102">Tuple</span><span class="sxs-lookup"><span data-stu-id="c8124-102">Tuples</span></span>
  <span data-ttu-id="c8124-103">Tuple 可以唯一識別 Cube 中的資料配量。</span><span class="sxs-lookup"><span data-stu-id="c8124-103">A tuple uniquely identifies a slice of data from a cube.</span></span> <span data-ttu-id="c8124-104">Tuple 是由維度成員的組合所構成，只要沒有兩個以上的成員屬於相同階層即可。</span><span class="sxs-lookup"><span data-stu-id="c8124-104">The tuple is formed by a combination of dimension members, as long as there are no two or more members that belong to the same hierarchy.</span></span>  
  
## <a name="implicit-or-default-attribute-members-in-a-tuple"></a><span data-ttu-id="c8124-105">Tuple 中的隱含或預設屬性成員</span><span class="sxs-lookup"><span data-stu-id="c8124-105">Implicit or default attribute members in a tuple</span></span>  
 <span data-ttu-id="c8124-106">在 MDX 查詢或運算式中定義 Tuple 時，您不需明確包含每個屬性階層的屬性成員。</span><span class="sxs-lookup"><span data-stu-id="c8124-106">When defining a tuple in an MDX query or expression, you do not need to explicitly include the attribute member from every attribute hierarchy.</span></span> <span data-ttu-id="c8124-107">如果屬性階層的成員沒有明確包含在查詢或運算式中，該屬性階層的預設成員就是 Tuple 中隱含包含的屬性成員。</span><span class="sxs-lookup"><span data-stu-id="c8124-107">If a member from an attribute hierarchy is not explicitly included in a query or an expression, the default member for that attribute hierarchy is the attribute member implicitly included in the tuple.</span></span> <span data-ttu-id="c8124-108">除非 Cube 中另有明確定義，否則每個屬性階層的預設成員就是 (全部) 成員 (如果 (全部) 成員存在的話)。</span><span class="sxs-lookup"><span data-stu-id="c8124-108">Unless otherwise explicitly defined in a cube, the default member for every attribute hierarchy is the (All) member, if an (All) member exists.</span></span> <span data-ttu-id="c8124-109">如果 (全部) 成員不存在屬性階層中，預設成員就是屬性階層的最上層成員。</span><span class="sxs-lookup"><span data-stu-id="c8124-109">If an (All) member does not exist within an attribute hierarchy, the default member is a member of the attribute hierarchy's top level.</span></span> <span data-ttu-id="c8124-110">除非明確定義了預設量值，否則預設量值就是 Cube 中第一個指定的量值。</span><span class="sxs-lookup"><span data-stu-id="c8124-110">The default measure is the first measure specified in the cube, unless a default measure is explicitly defined.</span></span> <span data-ttu-id="c8124-111">如需詳細資訊，請參閱[定義預設成員](../attribute-properties-define-a-default-member.md)和 [DefaultMember &#40;MDX&#41;](/sql/mdx/defaultmember-mdx)。</span><span class="sxs-lookup"><span data-stu-id="c8124-111">For more information, see [Define a Default Member](../attribute-properties-define-a-default-member.md) and [DefaultMember &#40;MDX&#41;](/sql/mdx/defaultmember-mdx).</span></span>  
  
 <span data-ttu-id="c8124-112">例如，藉由明確定義 Measures 維度的單一成員，下列 Tuple 會識別 Adventure Works 資料庫中的單一資料格。</span><span class="sxs-lookup"><span data-stu-id="c8124-112">For example, the following tuple identifies a single cell in the Adventure Works database by explicitly defining only a single member of the Measures dimension.</span></span>  
  
```  
(Measures.[Reseller Sales Amount])  
```  
  
 <span data-ttu-id="c8124-113">上述範例唯一識別由 Measures 維度之 Reseller Sales Amount 成員及 Cube 中每個屬性階層之預設成員組成的資料格。</span><span class="sxs-lookup"><span data-stu-id="c8124-113">The previous example uniquely identifies the cell consisting of the Reseller Sales Amount member from the Measures dimension and the default member from every attribute hierarchy in the cube.</span></span> <span data-ttu-id="c8124-114">除了 Destination Currency 屬性階層，每個屬性階層的預設成員都是 (全部) 成員。</span><span class="sxs-lookup"><span data-stu-id="c8124-114">The default member is the (All) member for every attribute hierarchy other than the Destination Currency attribute hierarchy.</span></span> <span data-ttu-id="c8124-115">Destination Currency 階層的預設成員是 US Dollar 成員 (這個預設成員是在 Adventure Works Cube 的 MDX 指令碼中定義的)。</span><span class="sxs-lookup"><span data-stu-id="c8124-115">The default member for the Destination Currency hierarchy is the US Dollar member (this default member is defined in the MDX script for the Adventure Works cube).</span></span>  
  
 <span data-ttu-id="c8124-116">下列查詢會傳回上述範例中指定 Tuple 所參考之資料格的值：($80,450.596.98)。</span><span class="sxs-lookup"><span data-stu-id="c8124-116">The following query returns the value for the cell referenced by the tuple specified in the previous example, ($80,450.596.98).</span></span>  
  
```  
SELECT   
Measures.[Reseller Sales Amount] ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c8124-117">當您在查詢中指定集合 (此處由單一 Tuple 組成) 的座標軸時，必須先指定資料行軸的集合，然後指定資料列軸的集合。</span><span class="sxs-lookup"><span data-stu-id="c8124-117">When you specify an axis for a set (in this case composed of a single tuple) in a query, you must begin by specifying a set for the column axis before specifying a set for the row axis.</span></span> <span data-ttu-id="c8124-118">資料行軸也可以用 *axis(0)* 或僅僅 *0*的方式來代表。</span><span class="sxs-lookup"><span data-stu-id="c8124-118">The column axis can also be referred to as *axis(0)* or simply *0*.</span></span> <span data-ttu-id="c8124-119">如需 MDX 查詢的詳細資訊，請參閱[基本 MDX 查詢 &#40;MDX&#41;](mdx-query-the-basic-query.md)。</span><span class="sxs-lookup"><span data-stu-id="c8124-119">For more information about MDX queries, see [The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md).</span></span>  
  
### <a name="tuples-as-values-or-member-references"></a><span data-ttu-id="c8124-120">Tuple 做為值或成員參考</span><span class="sxs-lookup"><span data-stu-id="c8124-120">Tuples as values or member references</span></span>  
 <span data-ttu-id="c8124-121">您可以在查詢中使用 Tuple，來傳回 Tuple 所參考之資料格的值，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="c8124-121">You can use a tuple in a query to return the value in the cell that is referenced by the tuple, as in the previous example.</span></span> <span data-ttu-id="c8124-122">或者，您也可以在運算式中使用 Tuple，明確參考 Tuple 中指定的成員。</span><span class="sxs-lookup"><span data-stu-id="c8124-122">Or you can use a tuple in an expression to explicitly refer to the members specified in the tuple.</span></span> <span data-ttu-id="c8124-123">查詢或運算式可以利用會傳回或取用 Tuple 的函數。</span><span class="sxs-lookup"><span data-stu-id="c8124-123">The query or the expression can utilize functions that either return or consume tuples.</span></span> <span data-ttu-id="c8124-124">Tuple 可以用來參考 Tuple 所指定之資料格的值，或在函數中使用時用來指定成員組合。</span><span class="sxs-lookup"><span data-stu-id="c8124-124">A tuple can be used to either refer to the value of the cell that the tuple specifies, or to specify a combination of members when utilized in a function.</span></span>  
  
### <a name="tuple-dimensionality"></a><span data-ttu-id="c8124-125">Tuple 維度性</span><span class="sxs-lookup"><span data-stu-id="c8124-125">Tuple dimensionality</span></span>  
 <span data-ttu-id="c8124-126">Tuple 的 *「維度性」* 是指 Tuple 中的成員順序。</span><span class="sxs-lookup"><span data-stu-id="c8124-126">The *dimensionality* of a tuple refers to the sequence or order of the members in the tuple.</span></span> <span data-ttu-id="c8124-127">因為隱含成員一律以相同順序出現，所以就 Tuple 的明確定義成員方面最常考慮到維度性。</span><span class="sxs-lookup"><span data-stu-id="c8124-127">Since the implicit members always occur in the same order, dimensionality is most often thought of in terms of the explicitly defined members of the tuple.</span></span> <span data-ttu-id="c8124-128">當您定義一組 Tuple 時，Tuple 的成員順序很重要。</span><span class="sxs-lookup"><span data-stu-id="c8124-128">The ordering of the members of the tuple is important when you define a set of tuples.</span></span> <span data-ttu-id="c8124-129">下列範例包含資料行軸上 Tuple 的兩個成員。</span><span class="sxs-lookup"><span data-stu-id="c8124-129">The following example includes two members in a tuple on the column axis.</span></span>  
  
```  
SELECT   
([Measures].[Reseller Sales Amount],[Date].[Calendar Year].[CY 2004]) ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c8124-130">當您從一個以上的維度明確指定 Tuple 的成員時，必須用括號含括整個 Tuple。</span><span class="sxs-lookup"><span data-stu-id="c8124-130">When you explicitly specify a member in a tuple from more than one dimension, you must include the entire tuple in parentheses.</span></span> <span data-ttu-id="c8124-131">只指定 Tuple 中的單一成員時，括號是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c8124-131">When only specifying a single member in a tuple, parentheses are optional.</span></span>  
  
 <span data-ttu-id="c8124-132">在上述範例中，查詢中的 Tuple 指定傳回位於 Measures 維度之 Reseller Sales Amount 和 Date 維度中 Calendar Year 屬性階層之 CY 2004 成員交集處的 Cube 資料格。</span><span class="sxs-lookup"><span data-stu-id="c8124-132">The tuple in the query in the previous example specifies the return of the cube cell at the intersection of the Reseller Sales Amount Measure of the Measures dimension and the CY 2004 member of the Calendar Year attribute hierarchy in the Date dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8124-133">屬性成員可以其成員名稱或成員索引鍵代表。</span><span class="sxs-lookup"><span data-stu-id="c8124-133">An attribute member can be referred by either its member name or its member key.</span></span> <span data-ttu-id="c8124-134">在上述範例中，您可以將參考值從 [CY 2004] 取代成 &[2004]。</span><span class="sxs-lookup"><span data-stu-id="c8124-134">In the previous example, you could replace the reference to [CY 2004] with &[2004].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8124-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8124-135">See Also</span></span>  
 <span data-ttu-id="c8124-136">[MDX 中的重要概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c8124-136">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="c8124-137">[Cube 空間](cube-space.md) </span><span class="sxs-lookup"><span data-stu-id="c8124-137">[Cube Space](cube-space.md) </span></span>  
 <span data-ttu-id="c8124-138">[自動存在](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="c8124-138">[Autoexists](autoexists.md) </span></span>  
 [<span data-ttu-id="c8124-139">使用成員、Tuple 和集合 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="c8124-139">Working with Members, Tuples, and Sets &#40;MDX&#41;</span></span>](working-with-members-tuples-and-sets-mdx.md)  
  
  
