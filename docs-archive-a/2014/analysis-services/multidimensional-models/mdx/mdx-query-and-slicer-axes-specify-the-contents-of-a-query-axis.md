---
title: 指定查詢座標軸的內容 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cellsets [MDX]
- query axis [MDX]
ms.assetid: c745ade0-738e-4a98-a3f0-3eabfd3eeba2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 28fd867b8f8caaf74e4dd704753c354368da2e89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703322"
---
# <a name="specifying-the-contents-of-a-query-axis-mdx"></a><span data-ttu-id="e9da1-102">指定查詢座標軸的內容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="e9da1-102">Specifying the Contents of a Query Axis (MDX)</span></span>
  <span data-ttu-id="e9da1-103">查詢座標軸指定多維度運算式 (MDX) SELECT 陳述式傳回的資料格集邊緣。</span><span class="sxs-lookup"><span data-stu-id="e9da1-103">Query axes specify the edges of a cellset returned by a Multidimensional Expressions (MDX) SELECT statement.</span></span> <span data-ttu-id="e9da1-104">指定資料格集邊緣，您就可以限制用戶端能看見的傳回資料。</span><span class="sxs-lookup"><span data-stu-id="e9da1-104">Specifying the edges of a cellset lets you restrict the returned data that is visible to the client.</span></span>  
  
 <span data-ttu-id="e9da1-105">若要指定查詢座標軸，您可以使用 `<SELECT query axis clause>` ，將集合指派給特定查詢座標軸。</span><span class="sxs-lookup"><span data-stu-id="e9da1-105">To specify query axes, you use the `<SELECT query axis clause>` to assign a set to a particular query axis.</span></span> <span data-ttu-id="e9da1-106">每個 `<SELECT query axis clause>` 值定義一個查詢座標軸。</span><span class="sxs-lookup"><span data-stu-id="e9da1-106">Each `<SELECT query axis clause>` value defines one query axis.</span></span> <span data-ttu-id="e9da1-107">資料集中的座標軸數等於 SELECT 陳述式中的 `<SELECT query axis clause>` 值。</span><span class="sxs-lookup"><span data-stu-id="e9da1-107">The number of axes in the dataset is equal to the number of `<SELECT query axis clause>` values in the SELECT statement.</span></span>  
  
## <a name="query-axis-syntax"></a><span data-ttu-id="e9da1-108">查詢座標軸語法</span><span class="sxs-lookup"><span data-stu-id="e9da1-108">Query Axis Syntax</span></span>  
 <span data-ttu-id="e9da1-109">以下語法顯示 `<SELECT query axis clause>`的語法：</span><span class="sxs-lookup"><span data-stu-id="e9da1-109">The following syntax shows the syntax for the `<SELECT query axis clause>`:</span></span>  
  
```  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression [ <SELECT dimension property list clause> ] [<HAVING clause>]  
   ON {  
      Integer_Expression |   
      AXIS( Integer_Expression ) |   
      {COLUMNS | ROWS | PAGES | SECTIONS | CHAPTERS}     
      }  
  
```  
  
 <span data-ttu-id="e9da1-110">每一個查詢座標軸都有一個號碼：x-軸是零 (0)，y-軸是 1，z-軸是 2，依此類推。</span><span class="sxs-lookup"><span data-stu-id="e9da1-110">Each query axis has a number: zero (0) for the x-axis, 1 for the y-axis, 2 for the z-axis, and so on.</span></span> <span data-ttu-id="e9da1-111">在 `<SELECT query axis clause>`的語法中， `Integer_Expression` 值指定座標軸數目。</span><span class="sxs-lookup"><span data-stu-id="e9da1-111">In the syntax for the `<SELECT query axis clause>`, the `Integer_Expression` value specifies the axis number.</span></span> <span data-ttu-id="e9da1-112">MDX 查詢最多可以支援 128 個指定座標軸，但只有極少數的 MDX 查詢會使用 5 個以上的座標軸。</span><span class="sxs-lookup"><span data-stu-id="e9da1-112">An MDX query can support up to 128 specified axes, but very few MDX queries will use more than 5 axes.</span></span> <span data-ttu-id="e9da1-113">對於前 5 個座標軸，可改為使用別名 COLUMNS、ROWS、PAGES、SECTIONS 與 CHAPTERS。</span><span class="sxs-lookup"><span data-stu-id="e9da1-113">For the first 5 axes, the aliases COLUMNS, ROWS, PAGES, SECTIONS, and CHAPTERS can instead be used.</span></span>  
  
 <span data-ttu-id="e9da1-114">MDX 查詢無法略過查詢座標軸。</span><span class="sxs-lookup"><span data-stu-id="e9da1-114">An MDX query cannot skip query axes.</span></span> <span data-ttu-id="e9da1-115">也就是說，包含一個或多個查詢座標軸的查詢絕不能排除編號較低或中間的座標軸。</span><span class="sxs-lookup"><span data-stu-id="e9da1-115">That is, a query that includes one or more query axes must not exclude lower-numbered or intermediate axes.</span></span> <span data-ttu-id="e9da1-116">例如，查詢不可以只有 ROWS 座標軸，而沒有 COLUMNS 座標軸，或者有 COLUMNS 與 PAGES 座標軸，但沒有 ROWS 座標軸。</span><span class="sxs-lookup"><span data-stu-id="e9da1-116">For example, a query cannot have a ROWS axis without a COLUMNS axis, or have COLUMNS and PAGES axes without a ROWS axis.</span></span>  
  
 <span data-ttu-id="e9da1-117">但是，您可以指定沒有座標軸的 SELECT 子句 (也就是說，一個空的 SELECT 子句)。</span><span class="sxs-lookup"><span data-stu-id="e9da1-117">However, you can specify a SELECT clause without any axes (that is, an empty SELECT clause).</span></span> <span data-ttu-id="e9da1-118">在此狀況下，所有的維度都是切片維度，且 MDX 查詢選取一個資料格。</span><span class="sxs-lookup"><span data-stu-id="e9da1-118">In this case, all dimensions are slicer dimensions, and the MDX query selects one cell.</span></span>  
  
 <span data-ttu-id="e9da1-119">在先前顯示的查詢座標軸語法中， `Set_Expression` 值指定了定義查詢座標軸內容的集合。</span><span class="sxs-lookup"><span data-stu-id="e9da1-119">In the query axis syntax previously shown, each `Set_Expression` value specifies the set that defines the contents of the query axis.</span></span> <span data-ttu-id="e9da1-120">如需集合的詳細資訊，請參閱[使用成員、Tuple 和集合 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="e9da1-120">For more information about sets, see [Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e9da1-121">範例</span><span class="sxs-lookup"><span data-stu-id="e9da1-121">Examples</span></span>  
 <span data-ttu-id="e9da1-122">下列簡單的 SELECT 陳述式會傳回 Columns 軸上的量值 Internet Sales Amount，並且使用 MDX MEMBERS 函數傳回 Rows 軸的 Date 維度上，Calendar 階層的所有成員：</span><span class="sxs-lookup"><span data-stu-id="e9da1-122">The following simple SELECT statement returns the measure Internet Sales Amount on the Columns axis, and uses the MDX MEMBERS function to return all the members from the Calendar hierarchy on the Date dimension on the Rows axis:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="e9da1-123">後續兩個查詢會傳回完全相同的結果，但是會示範使用軸數，而非別名：</span><span class="sxs-lookup"><span data-stu-id="e9da1-123">The two following queries return exactly the same results but demonstrate the use of axis numbers rather than aliases:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON 0,  
{[Date].[Calendar].MEMBERS} ON 1  
FROM [Adventure Works]  
  
SELECT {[Measures].[Internet Sales Amount]} ON AXIS(0),  
{[Date].[Calendar].MEMBERS} ON AXIS(1)  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="e9da1-124">在設定定義之前使用的 NON EMPTY 關鍵字是從軸中移除所有空白 Tuple 的簡單方式。</span><span class="sxs-lookup"><span data-stu-id="e9da1-124">The NON EMPTY keyword, used before the set definition, is an easy way to remove all empty tuples from an axis.</span></span> <span data-ttu-id="e9da1-125">例如，在我們最近看到的範例中，自2004年8月起的 cube 中沒有任何資料。</span><span class="sxs-lookup"><span data-stu-id="e9da1-125">For example, in the examples we've seen so far there is no data in the cube from August 2004 onwards.</span></span> <span data-ttu-id="e9da1-126">若要從任何資料行都沒有資料的資料格集中移除所有資料列，只要在設定 Rows 軸定義之前加入 NON EMPTY 即可，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9da1-126">To remove all rows from the cellset that have no data in any column, simply add NON EMPTY before the set on the Rows axis definition as follows:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="e9da1-127">NON EMPTY 可以在查詢中的所有軸上使用。</span><span class="sxs-lookup"><span data-stu-id="e9da1-127">NON EMPTY can be used on all axes in a query.</span></span> <span data-ttu-id="e9da1-128">比較下面兩個查詢的結果，第一個未使用 NON EMPTY，第二個則在兩個軸上都使用：</span><span class="sxs-lookup"><span data-stu-id="e9da1-128">Compare the results of the following two queries, the first of which does not use NON EMPTY and the second of which does on both axes:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
SELECT NON EMPTY {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
```  
  
 <span data-ttu-id="e9da1-129">HAVING 子句可以依據特定準則篩選軸的內容；雖然它的彈性比其他可達成相同結果的方法小 (例如 FILTER 函數)，不過它比較容易使用。</span><span class="sxs-lookup"><span data-stu-id="e9da1-129">The HAVING clause can be used to filter the contents of an axis based on a specific criteria; it is less flexible than other methods that can achieve the same results, such as the FILTER function, but it is simpler to use.</span></span> <span data-ttu-id="e9da1-130">以下範例只會傳回 Internet Sales Amount 大於 $15,000 的日期：</span><span class="sxs-lookup"><span data-stu-id="e9da1-130">Here is an example that returns only those dates where Internet Sales Amount is greater than $15,000:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Date].MEMBERS}   
HAVING [Measures].[Internet Sales Amount]>15000  
ON ROWS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9da1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9da1-131">See Also</span></span>  
 [<span data-ttu-id="e9da1-132">指定 Slicer 軸的內容 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="e9da1-132">Specifying the Contents of a Slicer Axis &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
