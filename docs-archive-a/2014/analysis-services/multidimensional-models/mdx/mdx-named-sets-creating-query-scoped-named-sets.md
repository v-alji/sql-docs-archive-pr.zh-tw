---
title: " (MDX) 建立查詢範圍命名集 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6eccb4e20fca03079a04a0219b07f6411b80a433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698626"
---
# <a name="creating-query-scoped-named-sets-mdx"></a><span data-ttu-id="59bbd-102">建立查詢範圍命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="59bbd-102">Creating Query-Scoped Named Sets (MDX)</span></span>
  <span data-ttu-id="59bbd-103">如果單一多維度運算式 (MDX) 查詢只需要有命名集，您可以使用 WITH 關鍵字來定義命名集。</span><span class="sxs-lookup"><span data-stu-id="59bbd-103">If a named set is only required for a single Multidimensional Expressions (MDX) query, you can define that named set by using the WITH keyword.</span></span> <span data-ttu-id="59bbd-104">查詢完成執行之後，使用 WITH 關鍵字建立的命名集就不再存在。</span><span class="sxs-lookup"><span data-stu-id="59bbd-104">A named set that is created by using the WITH keyword no longer exists after the query has finished running.</span></span>  
  
 <span data-ttu-id="59bbd-105">如同本主題所討論，WITH 關鍵字的語法很有彈性，甚至可以使用函數來定義命名集。</span><span class="sxs-lookup"><span data-stu-id="59bbd-105">As discussed in this topic, the syntax of the WITH keyword is quite flexible, even accommodating the use of functions to define the named set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59bbd-106">如需命名集的詳細資訊，請參閱[在 MDX 中建立命名集 &#40;MDX&#41;](mdx-named-sets-building-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="59bbd-106">For more information about named sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
## <a name="with-keyword-syntax"></a><span data-ttu-id="59bbd-107">WITH 關鍵字語法</span><span class="sxs-lookup"><span data-stu-id="59bbd-107">WITH Keyword Syntax</span></span>  
 <span data-ttu-id="59bbd-108">使用以下語法將 WITH 關鍵字加入 MDX SELECT 陳述式：</span><span class="sxs-lookup"><span data-stu-id="59bbd-108">Use the following syntax to add the WITH keyword to a MDX SELECT statement:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
   ( SET Set_Identifier AS 'Set_Expression')  
  
```  
  
 <span data-ttu-id="59bbd-109">在 WITH 關鍵字的語法中， `Set_Identifier` 參數包含命名集的別名。</span><span class="sxs-lookup"><span data-stu-id="59bbd-109">In the syntax for the WITH keyword, the `Set_Identifier` parameter contains the alias for the named set.</span></span> <span data-ttu-id="59bbd-110">`Set_Expression` 參數包含了命名集別名所參考的集合運算式。</span><span class="sxs-lookup"><span data-stu-id="59bbd-110">The `Set_Expression` parameter contains the set expression to which the named set alias refers.</span></span>  
  
## <a name="with-keyword-example"></a><span data-ttu-id="59bbd-111">WITH 關鍵字範例</span><span class="sxs-lookup"><span data-stu-id="59bbd-111">WITH Keyword Example</span></span>  
 <span data-ttu-id="59bbd-112">下列 MDX 查詢會檢查 `FoodMart 2000` (Microsoft SQL Server 2000 Analysis Services 的範例資料庫) 中，各種 Chardonnay 和 Chablis 葡萄酒的單位銷售量。</span><span class="sxs-lookup"><span data-stu-id="59bbd-112">The following MDX query examines the unit sales of the various Chardonnay and Chablis wines in `FoodMart 2000`, the sample database for Microsoft SQL Server 2000 Analysis Services.</span></span> <span data-ttu-id="59bbd-113">此查詢就結果集而言雖然相當簡單，但當您必須維護這樣的查詢時卻是冗長而不便的。</span><span class="sxs-lookup"><span data-stu-id="59bbd-113">This query, although fairly simple in terms of the result set, is lengthy and unwieldy when you have to maintenance such a query.</span></span>  
  
```  
SELECT  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]} ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
 <span data-ttu-id="59bbd-114">若要使先前的 MDX 查詢易於維護，您可以使用 WITH 關鍵字來為查詢建立命名集。</span><span class="sxs-lookup"><span data-stu-id="59bbd-114">To make the previous MDX query easier to maintain, you can create a named set for the query by using the WITH keyword.</span></span> <span data-ttu-id="59bbd-115">以下程式碼顯示如何使用 WITH 關鍵字建立命名集 `[ChardonnayChablis]`，以及命名集如何使 SELECT 陳述式變得更短也更容易維護。</span><span class="sxs-lookup"><span data-stu-id="59bbd-115">The following code shows how to use the WITH keyword to create a named set, `[ChardonnayChablis]`, and how the named set makes the SELECT statement shorter and easier to maintain.</span></span>  
  
```  
WITH SET [ChardonnayChablis] AS  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]}  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
### <a name="using-functions-together-with-the-with-keyword"></a><span data-ttu-id="59bbd-116">函數搭配 WITH 關鍵字一起使用</span><span class="sxs-lookup"><span data-stu-id="59bbd-116">Using Functions Together with the WITH Keyword</span></span>  
 <span data-ttu-id="59bbd-117">雖然您可以明確定義命名集的每個成員，但這種方式會產生一個冗長的陳述式。</span><span class="sxs-lookup"><span data-stu-id="59bbd-117">Although you can explicitly define each member of a named set, this approach can produce a lengthy statement.</span></span> <span data-ttu-id="59bbd-118">若要讓建立和維護命名集更容易，您可以使用 MDX 函數來定義成員。</span><span class="sxs-lookup"><span data-stu-id="59bbd-118">To make the creation and maintenance of a named set easier, you can use MDX functions to define the members.</span></span>  
  
 <span data-ttu-id="59bbd-119">例如，下列 MDX 查詢範例使用 [Filter](/sql/mdx/filter-mdx)、 [CurrentMember](/sql/mdx/current-mdx)、 [Name](/sql/mdx/members-string-mdx) MDX 函數以及 InStr VBA 函數，來建立 `[ChardonnayChablis]` 命名集。</span><span class="sxs-lookup"><span data-stu-id="59bbd-119">For example, the following MDX query example uses the [Filter](/sql/mdx/filter-mdx), [CurrentMember](/sql/mdx/current-mdx), and [Name](/sql/mdx/members-string-mdx) MDX functions and the InStr VBA function to create the `[ChardonnayChablis]` named set.</span></span> <span data-ttu-id="59bbd-120">這個 `[ChardonnayChablis]` 命名集版本和先前在本主題中顯示的明確定義版本相同。</span><span class="sxs-lookup"><span data-stu-id="59bbd-120">This version of the `[ChardonnayChablis]` named set is the same as the explicitly defined version shown previously in this topic.</span></span>  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="59bbd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59bbd-121">See Also</span></span>  
 <span data-ttu-id="59bbd-122">[SELECT 語句 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="59bbd-122">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 [<span data-ttu-id="59bbd-123">建立工作階段範圍命名集 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="59bbd-123">Creating Session-Scoped Named Sets &#40;MDX&#41;</span></span>](mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  
