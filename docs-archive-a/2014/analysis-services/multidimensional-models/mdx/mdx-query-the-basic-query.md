---
title: " (MDX) 的基本 MDX 查詢 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], SELECT statement
- queries [MDX], about queries
- cellsets [MDX]
- SELECT statement [MDX]
- cubes [Analysis Services], SELECT statement
ms.assetid: 4fa5a95a-fec9-4584-875c-dbf030c53e82
author: minewiskan
ms.author: owend
ms.openlocfilehash: b6b1a70753abe8e477bd1e522a37f4513cc12a52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598615"
---
# <a name="the-basic-mdx-query-mdx"></a><span data-ttu-id="dadc0-102">基本 MDX 查詢 (MDX)</span><span class="sxs-lookup"><span data-stu-id="dadc0-102">The Basic MDX Query (MDX)</span></span>
  <span data-ttu-id="dadc0-103"> (MDX) 查詢的基本多維度運算式是 SELECT 語句，也就是 MDX 中最常使用的查詢。</span><span class="sxs-lookup"><span data-stu-id="dadc0-103">The basic Multidimensional Expressions (MDX) query is the SELECT statement-the most frequently used query in MDX.</span></span> <span data-ttu-id="dadc0-104">了解 MDX SELECT 陳述式必須指定結果集的方式、SELECT 陳述式的語法為何，以及如何使用 SELECT 陳述式建立簡單查詢之後，您將完全了解如何使用 MDX 來查詢多維度資料。</span><span class="sxs-lookup"><span data-stu-id="dadc0-104">By understanding how an MDX SELECT statement must specify a result set, what the syntax of the SELECT statement is, and how to create a simple query using the SELECT statement, you will have a solid understanding of how to use MDX to query multidimensional data.</span></span>  
  
## <a name="specifying-a-result-set"></a><span data-ttu-id="dadc0-105">指定結果集</span><span class="sxs-lookup"><span data-stu-id="dadc0-105">Specifying a Result Set</span></span>  
 <span data-ttu-id="dadc0-106">在 MDX 中，SELECT 陳述式會指定一個結果集，內含從 Cube 傳回的多維度資料子集。</span><span class="sxs-lookup"><span data-stu-id="dadc0-106">In MDX, the SELECT statement specifies a result set that contains a subset of multidimensional data that has been returned from a cube.</span></span> <span data-ttu-id="dadc0-107">若要指定結果集，MDX 查詢必須包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="dadc0-107">To specify a result set, an MDX query must contain the following information:</span></span>  
  
-   <span data-ttu-id="dadc0-108">您要在結果集中包含的軸數目。</span><span class="sxs-lookup"><span data-stu-id="dadc0-108">The number of axes that you want the result set to contain.</span></span> <span data-ttu-id="dadc0-109">在一個 MDX 查詢中，您最多可指定 128 個座標軸。</span><span class="sxs-lookup"><span data-stu-id="dadc0-109">You can specify up to 128 axes in an MDX query.</span></span>  
  
-   <span data-ttu-id="dadc0-110">要在 MDX 查詢的每一個軸上包含的成員或 Tuple 集合。</span><span class="sxs-lookup"><span data-stu-id="dadc0-110">The set of members or tuples to include on each axis of the MDX query.</span></span>  
  
-   <span data-ttu-id="dadc0-111">設定 MDX 查詢內容的 Cube 的名稱。</span><span class="sxs-lookup"><span data-stu-id="dadc0-111">The name of the cube that sets the context of the MDX query.</span></span>  
  
-   <span data-ttu-id="dadc0-112">要在 slicer 軸上包含的成員或 Tuple 集合。</span><span class="sxs-lookup"><span data-stu-id="dadc0-112">The set of members or tuples to include on the slicer axis.</span></span> <span data-ttu-id="dadc0-113">如需 slicer 與查詢軸的詳細資訊，請參閱[利用查詢與 Slicer 軸限制查詢 &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md)。</span><span class="sxs-lookup"><span data-stu-id="dadc0-113">For more information about slicer and query axes, see[Restricting the Query with Query and Slicer Axes &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md).</span></span>  
  
 <span data-ttu-id="dadc0-114">為了識別查詢軸、要查詢的 Cube 以及 slicer 軸，MDX SELECT 陳述式會使用以下子句：</span><span class="sxs-lookup"><span data-stu-id="dadc0-114">To identify the query axes, the cube that will be queried, and the slicer axis, the MDX SELECT statement uses the following clauses:</span></span>  
  
-   <span data-ttu-id="dadc0-115">SELECT 子句，決定 MDX SELECT 陳述式的查詢座標軸。</span><span class="sxs-lookup"><span data-stu-id="dadc0-115">A SELECT clause that determines the query axes of an MDX SELECT statement.</span></span> <span data-ttu-id="dadc0-116">如需在 SELECT 子句內建構查詢軸的詳細資訊，請參閱[指定查詢軸的內容 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="dadc0-116">For more information about the construction of query axes in a SELECT clause, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
-   <span data-ttu-id="dadc0-117">決定要查詢之 Cube 的 FROM 子句。</span><span class="sxs-lookup"><span data-stu-id="dadc0-117">A FROM clause that determines which cube will be queried.</span></span> <span data-ttu-id="dadc0-118">如需 FROM 子句的詳細資訊，請參閱 [SELECT 陳述式 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)。</span><span class="sxs-lookup"><span data-stu-id="dadc0-118">For more information about the FROM clause, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
-   <span data-ttu-id="dadc0-119">選擇性的 WHERE 子句，這個子句會決定要在 slicer 軸上用來限制所傳回資料的成員或 Tuple。</span><span class="sxs-lookup"><span data-stu-id="dadc0-119">An optional WHERE clause that determines which members or tuples to use on the slicer axis to restrict the data returned.</span></span> <span data-ttu-id="dadc0-120">如需在 WHERE 子句內建構 slicer 軸的詳細資訊，請參閱[指定 Slicer 軸的內容 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="dadc0-120">For more information about the construction of a slicer axis in a WHERE clause, see [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dadc0-121">如需 SELECT 陳述式不同子句的詳細資訊，請參閱 [SELECT 陳述式 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)。</span><span class="sxs-lookup"><span data-stu-id="dadc0-121">For more detailed information about the various clauses of the SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
## <a name="select-statement-syntax"></a><span data-ttu-id="dadc0-122">SELECT 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="dadc0-122">SELECT Statement Syntax</span></span>  
 <span data-ttu-id="dadc0-123">以下語法顯示基本 SELECT 陳述式，包括 SELECT、FROM 與 WHERE 子句的用法：</span><span class="sxs-lookup"><span data-stu-id="dadc0-123">The following syntax shows a basic SELECT statement that includes the use of the SELECT, FROM, and WHERE clauses:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause>   
    [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
```  
  
 <span data-ttu-id="dadc0-124">MDX SELECT 陳述式支援選擇性語法，例如 WITH 關鍵字、使用 MDX 函數建立計算的成員以納入軸或 slicer 軸，以及做為查詢的一部分傳回特定資料格屬性值的能力。</span><span class="sxs-lookup"><span data-stu-id="dadc0-124">The MDX SELECT statement supports optional syntax, such as the WITH keyword, the use of MDX functions to create calculated members for inclusion in an axis or slicer axis, and the ability to return the values of specific cell properties as part of the query.</span></span> <span data-ttu-id="dadc0-125">如需 MDX SELECT 陳述式的詳細資訊，請參閱 [SELECT 陳述式 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)。</span><span class="sxs-lookup"><span data-stu-id="dadc0-125">For more information about the MDX SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
### <a name="comparing-the-syntax-of-the-mdx-select-statement-to-sql"></a><span data-ttu-id="dadc0-126">比較 MDX SELECT 陳述式與 SQL 的語法</span><span class="sxs-lookup"><span data-stu-id="dadc0-126">Comparing the Syntax of the MDX SELECT Statement to SQL</span></span>  
 <span data-ttu-id="dadc0-127">MDX SELECT 陳述式的語法格式跟 SQL 的語法格式相似。</span><span class="sxs-lookup"><span data-stu-id="dadc0-127">The syntax format for the MDX SELECT statement is similar to that of SQL syntax.</span></span> <span data-ttu-id="dadc0-128">但是，有幾個基本的相異之處：</span><span class="sxs-lookup"><span data-stu-id="dadc0-128">However, there are several fundamental differences:</span></span>  
  
-   <span data-ttu-id="dadc0-129">MDX 語法會利用以大括弧括住的元組或成員來區分集合 ({和} 字元 ) 。如需有關成員、元組和 set 語法的詳細資訊，請參閱[使用成員、元組和集合 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="dadc0-129">MDX syntax distinguishes sets by surrounding tuples or members with braces (the { and } characters.) For more information about member, tuple, and set syntax, see [Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).</span></span>  
  
-   <span data-ttu-id="dadc0-130">在 SELECT 陳述式中，MDX 查詢可以有 0、1、2 或最多 128 個查詢軸。</span><span class="sxs-lookup"><span data-stu-id="dadc0-130">MDX queries can have 0, 1, 2 or up to 128 query axes in the SELECT statement.</span></span> <span data-ttu-id="dadc0-131">每一個軸都會以完全相同的方式執行，不像 SQL 中查詢的資料列和資料行的行為模式大相逕庭。</span><span class="sxs-lookup"><span data-stu-id="dadc0-131">Each axis behaves in exactly the same way, unlike SQL where there are significant differences between how the rows and the columns of a query behave.</span></span>  
  
-   <span data-ttu-id="dadc0-132">如同 SQL 查詢，FROM 子句為 MDX 查詢的資料來源命名。</span><span class="sxs-lookup"><span data-stu-id="dadc0-132">As with an SQL query, the FROM clause names the source of the data for the MDX query.</span></span> <span data-ttu-id="dadc0-133">但是，MDX FROM 子句僅限於單一 Cube。</span><span class="sxs-lookup"><span data-stu-id="dadc0-133">However, the MDX FROM clause is restricted to a single cube.</span></span> <span data-ttu-id="dadc0-134">使用 LookupCube 函數，就能按值逐一擷取其他 Cube 的資訊。</span><span class="sxs-lookup"><span data-stu-id="dadc0-134">Information from other cubes can be retrieved on a value-by-value basis by using the LookupCube function.</span></span>  
  
-   <span data-ttu-id="dadc0-135">WHERE 子句會描述 MDX 查詢中的 slicer 軸。</span><span class="sxs-lookup"><span data-stu-id="dadc0-135">The WHERE clause describes the slicer axis in an MDX query.</span></span> <span data-ttu-id="dadc0-136">它的行為像是隱藏在查詢中的額外軸，會切割結果集的資料格中出現的值；不過它不像 SQL 的 WHERE 子句，不會直接影響查詢之資料列軸的結果。</span><span class="sxs-lookup"><span data-stu-id="dadc0-136">It acts as something like an invisible, extra axis in the query, slicing the values that appear in the cells in the result set; unlike the SQL WHERE clause it does not directly affect what appears on the rows axis of the query.</span></span> <span data-ttu-id="dadc0-137">SQL WHERE 子句的功能可透過其他 MDX 函數 (例如 FILTER 函數) 提供。</span><span class="sxs-lookup"><span data-stu-id="dadc0-137">The functionality of the SQL WHERE clause is available through other MDX functions such as the FILTER function.</span></span>  
  
## <a name="select-statement-example"></a><span data-ttu-id="dadc0-138">SELECT 陳述式範例</span><span class="sxs-lookup"><span data-stu-id="dadc0-138">SELECT Statement Example</span></span>  
 <span data-ttu-id="dadc0-139">以下範例顯示使用 SELECT 陳述式的基本 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="dadc0-139">The following example shows a basic MDX query that uses the SELECT statement.</span></span> <span data-ttu-id="dadc0-140">此查詢會傳回一個結果集，其中包含 Southwest 銷售區域在 2002 與 2003 年的銷售與稅額。</span><span class="sxs-lookup"><span data-stu-id="dadc0-140">This query returns a result set that contains the 2002 and 2003 sales and tax amounts for the Southwest sales territories.</span></span>  
  
```  
SELECT  
    { [Measures].[Sales Amount],   
        [Measures].[Tax Amount] } ON COLUMNS,  
    { [Date].[Fiscal].[Fiscal Year].&[2002],   
        [Date].[Fiscal].[Fiscal Year].&[2003] } ON ROWS  
FROM [Adventure Works]  
WHERE ( [Sales Territory].[Southwest] )  
```  
  
 <span data-ttu-id="dadc0-141">在此範例中，查詢定義了下列結果集資訊：</span><span class="sxs-lookup"><span data-stu-id="dadc0-141">In this example, the query defines the following result set information:</span></span>  
  
-   <span data-ttu-id="dadc0-142">SELECT 子句將查詢座標軸設為 Measures 維度的 Sales Amount 與 Tax Amount 成員，以及 Date 維度的 2002 與 2003 成員。</span><span class="sxs-lookup"><span data-stu-id="dadc0-142">The SELECT clause sets the query axes as the Sales Amount and Tax Amount members of the Measures dimension, and the 2002 and 2003 members of the Date dimension.</span></span>  
  
-   <span data-ttu-id="dadc0-143">FROM 子句指出資料來源是 Adventure Works Cube。</span><span class="sxs-lookup"><span data-stu-id="dadc0-143">The FROM clause indicates that the data source is the Adventure Works cube.</span></span>  
  
-   <span data-ttu-id="dadc0-144">WHERE 子句將 slicer 座標軸定義為 Sales Territory 維度的 Southwest 成員。</span><span class="sxs-lookup"><span data-stu-id="dadc0-144">The WHERE clause defines the slicer axis as the Southwest member of the Sales Territory dimension.</span></span>  
  
 <span data-ttu-id="dadc0-145">請注意，查詢範例也會使用 COLUMNS 與 ROWS 座標軸別名。</span><span class="sxs-lookup"><span data-stu-id="dadc0-145">Notice that the query example also uses the COLUMNS and ROWS axis aliases.</span></span> <span data-ttu-id="dadc0-146">而這些座標軸的序數位置已經被使用。</span><span class="sxs-lookup"><span data-stu-id="dadc0-146">The ordinal positions for these axes could also have been used.</span></span> <span data-ttu-id="dadc0-147">以下範例顯示要如何撰寫 MDX 查詢，以使用每個座標軸的序數位置：</span><span class="sxs-lookup"><span data-stu-id="dadc0-147">The following example shows how the MDX query could have been written to use the ordinal position of each axis:</span></span>  
  
```  
SELECT  
    { [Measures].[Sales Amount],   
        [Measures].[Tax Amount] } ON 0,  
    { [Date].[Fiscal].[Fiscal Year].&[2002],   
        [Date].[Fiscal].[Fiscal Year].&[2003] } ON 1  
FROM [Adventure Works]  
WHERE ( [Sales Territory].[Southwest] )  
```  
  
 <span data-ttu-id="dadc0-148">如需詳細範例，請參閱[指定查詢軸的內容 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) 和[指定 Slicer 軸的內容 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="dadc0-148">For more detailed examples, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)and [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dadc0-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dadc0-149">See Also</span></span>  
 <span data-ttu-id="dadc0-150">[MDX 中的重要概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="dadc0-150">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 [<span data-ttu-id="dadc0-151">SELECT 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="dadc0-151">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
