---
title: 指定交叉分析篩選器軸的內容 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- filtering data [MDX]
ms.assetid: c56b0a70-cdec-427f-990e-425290344e7d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8620c54970ea14a2ac01c85262a372d2b3db0d68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687281"
---
# <a name="specifying-the-contents-of-a-slicer-axis-mdx"></a><span data-ttu-id="6a6d0-102">指定 Slicer 軸的內容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="6a6d0-102">Specifying the Contents of a Slicer Axis (MDX)</span></span>
  <span data-ttu-id="6a6d0-103">Slicer 軸會篩選多維度運算式 (MDX) SELECT 陳述式傳回的資料，限制傳回的資料，以便只傳回與指定成員交集的資料。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-103">The slicer axis filters the data returned by the Multidimensional Expressions (MDX) SELECT statement, restricting the returned data so that only data intersecting with the specified members will be returned.</span></span> <span data-ttu-id="6a6d0-104">它可以視為查詢中隱藏的額外軸。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-104">It can be thought of as an invisible extra axis in a query.</span></span> <span data-ttu-id="6a6d0-105">Slicer 軸定義在 MDX SELECT 陳述式的 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-105">The slicer axis is defined in the WHERE clause of the SELECT statement in MDX.</span></span>  
  
## <a name="slicer-axis-syntax"></a><span data-ttu-id="6a6d0-106">Slicer 軸語法</span><span class="sxs-lookup"><span data-stu-id="6a6d0-106">Slicer Axis Syntax</span></span>  
 <span data-ttu-id="6a6d0-107">若要明確指定 Slicer 軸，您可以在 MDX 中使用 `<SELECT slicer axis clause>` ，如以下語法所述：</span><span class="sxs-lookup"><span data-stu-id="6a6d0-107">To explicitly specify a slicer axis, you  using the `<SELECT slicer axis clause>` in MDX, as described in the following syntax:</span></span>  
  
```  
<SELECT slicer axis clause> ::=  WHERE Set_Expression  
```  
  
 <span data-ttu-id="6a6d0-108">在顯示的 Slicer 軸語法中， `Set_Expression` 可以取得 Tuple 運算式或集合運算式，而 Tuple 運算式會視為一個集合，用於評估子句。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-108">In the slicer axis syntax shown, `Set_Expression` can take either a tuple expression, which is treated as a set for the purposes of evaluating the clause, or a set expression.</span></span> <span data-ttu-id="6a6d0-109">如果已指定集合運算式，MDX 將嘗試評估此集合，彙總集合中每一個 Tuple 的結果資料格。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-109">If a set expression is specified, MDX will try to evaluate the set, aggregating the result cells in every tuple along the set.</span></span> <span data-ttu-id="6a6d0-110">換句話說，MDX 將會在此集合嘗試使用 [Aggregate](/sql/mdx/aggregate-mdx) 函數，利用與其相關的彙總函式來彙總每個量值。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-110">In other words, MDX will try to use the [Aggregate](/sql/mdx/aggregate-mdx) function on the set, aggregating each measure by its associated aggregation function.</span></span> <span data-ttu-id="6a6d0-111">此外，如果無法將集合運算式表示為屬性階層成員的交叉聯集，MDX 會將 Slicer 落在集合運算式之外的資料格，評估為 Null。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-111">Also, if the set expression cannot be expressed as a crossjoin of attribute hierarchy members, MDX treats cells that fall outside of the set expression for the slicer as null for evaluation purposes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6a6d0-112">MDX SELECT 陳述式的 WHERE 子句不像 SQL 中的 WHERE 子句，前者絕不會直接篩選查詢的 Rows 軸上傳回的內容。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-112">Unlike the WHERE clause in SQL, the WHERE clause of an MDX SELECT statement never directly filters what is returned on the Rows axis of a query.</span></span> <span data-ttu-id="6a6d0-113">若要篩選查詢的 Rows 或 Columns 軸上顯示的內容，您可以使用各種不同的 MDX 函數，例如 FILTER、NONEMPTY 和 TOPCOUNT。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-113">To filter what appears on the Rows or Columns axis of a query, you can use a variety of MDX functions, for example FILTER, NONEMPTY and TOPCOUNT.</span></span>  
  
### <a name="implicit-slicer-axis"></a><span data-ttu-id="6a6d0-114">隱含 Slicer 軸</span><span class="sxs-lookup"><span data-stu-id="6a6d0-114">Implicit Slicer Axis</span></span>  
 <span data-ttu-id="6a6d0-115">如果 Cube 內階層的成員未明確地包含在查詢座標軸中，階層的預設成員就會隱含地包含在 Slicer 軸中。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-115">If a member from a hierarchy within the cube is not explicitly included in a query axis, the default member from that hierarchy is implicitly included in the slicer axis.</span></span> <span data-ttu-id="6a6d0-116">如需預設成員的詳細資訊，請參閱 [定義預設成員](../attribute-properties-define-a-default-member.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-116">For more information about default members, see [Define a Default Member](../attribute-properties-define-a-default-member.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6a6d0-117">範例</span><span class="sxs-lookup"><span data-stu-id="6a6d0-117">Examples</span></span>  
 <span data-ttu-id="6a6d0-118">下列查詢不包含 WHERE 子句，並且會傳回所有 Calendar Year 之 Internet Sales Amount 的量值。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-118">The following query does not include a WHERE clause, and returns the value of the Internet Sales Amount measure for all Calendar Years:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="6a6d0-119">加入 WHERE 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6a6d0-119">Adding a WHERE clause, as follows:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States])  
  
```  
  
 <span data-ttu-id="6a6d0-120">不會改變查詢中 Rows 或 Columns 上傳回的內容；它會改變針對每一個資料格傳回的值。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-120">does not change what is returned on Rows or Columns in the query; it changes the values returned for each cell.</span></span> <span data-ttu-id="6a6d0-121">這個範例會分割查詢，以便傳回所有 Calendar Year 的 Internet Sales Amount 值，不過只包括住在 United States 的 Customer。不同階層的成員可以加入 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-121">In this example, the query is sliced so that it returns the value of Internet Sales Amount for all Calendar Years but only for Customers who live in the United States.Multiple members from different hierarchies can be added to the WHERE clause.</span></span> <span data-ttu-id="6a6d0-122">下列查詢會針對住在美國 (United States) 並且購買過自行車類別 (Bikes Category) 產品 (Product) 的客戶 Customer)，顯示所有日曆年度 (Calendar Year) 的網際網路銷售量 (Internet Sales Amount) 值。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-122">The following query shows the value of Internet Sales Amount for all Calendar Years for Customers who live in the United States and who bought Products in the Category Bikes:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States], [Product].[Category].&[1])  
```  
  
 <span data-ttu-id="6a6d0-123">如果您要使用相同階層的多個成員，則需要在 WHERE 子句中包含一個集合。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-123">If you want to use multiple members from the same hierarchy, you need to include a set in the WHERE clause.</span></span> <span data-ttu-id="6a6d0-124">例如，下列查詢會針對購買過自行車類別 (Category Bikes) 產品 (Product)，並且住在美國 (United States) 或英國 (United Kingdom) 的客戶 Customer)，顯示所有日曆年度 (Calendar Year) 的網際網路銷售量 (Internet Sales Amount) 值：</span><span class="sxs-lookup"><span data-stu-id="6a6d0-124">For example, the following query shows the value of Internet Sales Amount for all Calendar Years for Customers who bought Products in the Category Bikes and live in either the United States or the United Kingdom:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE(  
{[Customer].[Customer Geography].[Country].&[United States]  
, [Customer].[Customer Geography].[Country].&[United Kingdom]}  
, [Product].[Category].&[1])  
  
```  
  
 <span data-ttu-id="6a6d0-125">如上面所述，在 WHERE 子句中使用集合將隱含地彙總集合中所有成員的值。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-125">As mentioned above, using a set in the WHERE clause will implicitly aggregate values for all members in the set.</span></span> <span data-ttu-id="6a6d0-126">在這種情況下，查詢會在每一個資料格中顯示美國和英國的彙總值。</span><span class="sxs-lookup"><span data-stu-id="6a6d0-126">In this case, the query shows aggregated values for the United States and the United Kingdom in each cell.</span></span>  
  
  
