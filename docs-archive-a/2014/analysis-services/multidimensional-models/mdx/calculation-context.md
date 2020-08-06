---
title: 計算內容 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aec8aa98-b77d-4f8f-9684-2618b1d8e970
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6d14df51c6ec37fb96520af7acf207227ae4ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702007"
---
# <a name="calculation-context"></a><span data-ttu-id="87e41-102">計算內容</span><span class="sxs-lookup"><span data-stu-id="87e41-102">Calculation Context</span></span>
  <span data-ttu-id="87e41-103">計算內容是 Cube 中評估運算式以及所有座標為明確已知或可衍生自運算式的已知子空間。</span><span class="sxs-lookup"><span data-stu-id="87e41-103">The calculation context is the known subspace of the cube where an expression is evaluated and all coordinates are either explicitly known or can be derived from the expression.</span></span>  
  
## <a name="determining-the-calculation-context"></a><span data-ttu-id="87e41-104">決定計算內容</span><span class="sxs-lookup"><span data-stu-id="87e41-104">Determining the calculation context</span></span>  
 <span data-ttu-id="87e41-105">每個集合、成員、Tuple 或數值函數都是在整個 MDX 運算式或陳述式的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="87e41-105">Every set, member, tuple, or numeric function executes in the context of the entire MDX expression or statement.</span></span> <span data-ttu-id="87e41-106">傳遞引數 (例如 Tuple) 至函數時，只會明確提供 Cube 空間中的部分座標。</span><span class="sxs-lookup"><span data-stu-id="87e41-106">When an argument, such as a tuple, is passed to a function, only some of the coordinates in the cube space are explicitly provided.</span></span> <span data-ttu-id="87e41-107">其他座標是根據目前的計算內容取得。</span><span class="sxs-lookup"><span data-stu-id="87e41-107">The other coordinates are obtained based on the current calculation context.</span></span>  
  
 <span data-ttu-id="87e41-108">未指定之資料格座標和屬性成員的計算內容是依下列順序決定：</span><span class="sxs-lookup"><span data-stu-id="87e41-108">The calculation context for unspecified cell coordinates and attribute members is determined in the following order:</span></span>  
  
1.  <span data-ttu-id="87e41-109">FROM 子句 (如果有的話) - 採用 SELECT 陳述式的格式，這個子句可以指定整個 Cube，也可以指定 Subcube。</span><span class="sxs-lookup"><span data-stu-id="87e41-109">The FROM clause (if applicable) - this clause can either specify an entire cube or can specify a subcube in the form of a SELECT statement.</span></span>  
  
2.  <span data-ttu-id="87e41-110">WHERE 子句 (如果有的話) - 這個子句也稱為「slicer 軸」\*\*，用來指定集合、Tuple 或成員，可限制查詢所傳回之欄軸和列軸上的成員。</span><span class="sxs-lookup"><span data-stu-id="87e41-110">The WHERE clause (if applicable) - this clause, which is also known as the *slicer axis*, on which you specify a set, tuple, or member that restricts the members returned on the column and row axis by a query.</span></span> <span data-ttu-id="87e41-111">概念上，資料行或資料列軸上沒有明確指定之每個屬性階層的預設成員都是 slicer 座標軸的一部分。</span><span class="sxs-lookup"><span data-stu-id="87e41-111">Conceptually, the default member of every attribute hierarchy that is not explicitly specified on column or row axis is part of the slicer axis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="87e41-112">當 slicer 座標軸和另一個座標軸上指定了特定屬性的資料格座標時，函數中指定的座標會優先使用來決定座標軸上的成員集合。</span><span class="sxs-lookup"><span data-stu-id="87e41-112">When cell coordinates for a particular attribute are specified on both the slicer axis and on another axis, the coordinates specified in the function may take precedence in determining the members of the set on the axis.</span></span> <span data-ttu-id="87e41-113">[Filter (MDX)](/sql/mdx/filter-mdx) 和 [Order (MDX)](/sql/mdx/order-mdx) 函數是這類函數的範例 - 您可以使用 WHERE 子句，或 FROM 子句的 SELECT 陳述式，依據從計算內容排除的屬性成員來篩選或排序結果。</span><span class="sxs-lookup"><span data-stu-id="87e41-113">The [Filter (MDX)](/sql/mdx/filter-mdx) and [Order (MDX)](/sql/mdx/order-mdx) functions are examples of such functions - you can filter or order a result by attribute members that are excluded from the calculation context by the WHERE clause, or by a SELECT statement in the FROM clause.</span></span>  
  
3.  <span data-ttu-id="87e41-114">在查詢或運算式中定義的命名集和導出成員。</span><span class="sxs-lookup"><span data-stu-id="87e41-114">The named sets and calculated members defined in the query or expression.</span></span>  
  
4.  <span data-ttu-id="87e41-115">資料列和資料行軸上指定的 Tuple 和集合，利用資料列、資料行或 slicer 座標軸上沒有出現之屬性的預設成員。</span><span class="sxs-lookup"><span data-stu-id="87e41-115">The tuples and sets specified on the row and column axes, utilizing the default member for attributes that do not appear on the row, column, or slicer axis.</span></span>  
  
5.  <span data-ttu-id="87e41-116">每個座標軸上的 Cube 或 Subcube 資料格，刪除座標軸上的空 Tuple 並且套用 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="87e41-116">The cube or subcube cells on each axis, eliminating empty tuples on the axis and applying the HAVING clause.</span></span>  
  
6.  <span data-ttu-id="87e41-117">如需詳細資訊，請參閱 [建立查詢中的 Cube 內容 &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="87e41-117">For more information, see [Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md).</span></span>  
  
 <span data-ttu-id="87e41-118">在下列查詢中，資料列軸的計算內容受到 WHERE 子句中指定之 Country 屬性成員和 Calendar Year 屬性成員限制。</span><span class="sxs-lookup"><span data-stu-id="87e41-118">In the following query, the calculation context for the row axis is restricted by the Country attribute member and the Calendar Year attribute member that are specified in the WHERE clause.</span></span>  
  
```  
SELECT Customer.City.City.Members ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France, [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 <span data-ttu-id="87e41-119">然而，如果您透過指定資料列軸上之 `FILTER` 函數的方式修改這個查詢，並且利用 `FILTER` 函數中的 Calendar Year 屬性階層成員，就可以修改 Calendar Year 屬性階層的屬性成員，這是用來提供資料行軸上集合成員的計算內容。</span><span class="sxs-lookup"><span data-stu-id="87e41-119">However, if you modify this query by specifying the `FILTER` function on the row axis, and utilize a Calendar Year attribute hierarchy member in the `FILTER` function, then the attribute member from the Calendar Year attribute hierarchy that is used to provide the calculation context for the members of the set on the column axis can be modified.</span></span>  
  
```  
SELECT FILTER  
   (  
      Customer.City.City.Members,   
         ([Date].[Calendar].[Calendar Year].[CY 2003],  
            Measures.[Internet Order Quantity]) > 75   
   ) ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France,  
   [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 <span data-ttu-id="87e41-120">在上述查詢中，資料行軸上所出現之 Tuple 內資料格的計算內容是依 Calendar Year 屬性階層的 CY 2003 成員篩選，可是 Calendar Year 屬性階層的名義計算內容則是 CY 2004。</span><span class="sxs-lookup"><span data-stu-id="87e41-120">In the previous query, the calculation context for the cells in the tuples that appear on the column axis is filtered by the CY 2003 member of the Calendar Year attribute hierarchy, even though the nominal calculation context for the Calendar Year attribute hierarchy is CY 2004.</span></span> <span data-ttu-id="87e41-121">此外，它是依 Internet Order Quantity 量值篩選。</span><span class="sxs-lookup"><span data-stu-id="87e41-121">Furthermore, it is filtered by the Internet Order Quantity measure.</span></span> <span data-ttu-id="87e41-122">然而，一旦設定資料行軸上的集合成員，座標軸上所出現成員之值的計算內容會再度由 WHERE 子句決定。</span><span class="sxs-lookup"><span data-stu-id="87e41-122">However, once the members of the set on the column axis is set, the calculation context for the values for the members that appear on the axis is again determined by the WHERE clause.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="87e41-123">為了提高查詢效能，您應在解析程序中盡早刪除成員和 Tuple。</span><span class="sxs-lookup"><span data-stu-id="87e41-123">To increase query performance, you should eliminate members and tuples as early in the resolution process as possible.</span></span> <span data-ttu-id="87e41-124">如此一來，最終一個成員集合上的複雜查詢階段計算便會在最少資料格上運作。</span><span class="sxs-lookup"><span data-stu-id="87e41-124">In this manner, complex query time calculations on the final set of members operate on the fewest cells possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e41-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87e41-125">See Also</span></span>  
 <span data-ttu-id="87e41-126">[在查詢中建立 Cube 內容 &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="87e41-126">[Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span></span>  
 <span data-ttu-id="87e41-127">[MDX 查詢基本概念 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="87e41-127">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="87e41-128">MDX 的關鍵概念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="87e41-128">Key Concepts in MDX &#40;Analysis Services&#41;</span></span>](../key-concepts-in-mdx-analysis-services.md)  
  
  
