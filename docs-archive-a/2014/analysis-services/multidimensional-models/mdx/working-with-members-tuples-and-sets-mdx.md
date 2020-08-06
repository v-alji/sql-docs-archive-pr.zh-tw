---
title: 使用成員、元組和集合 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], tuples
- member keys [MDX]
- MDX [Analysis Services], sets
- calculated members [MDX]
- members [MDX]
- Multidimensional Expressions [Analysis Services], members
- named sets [MDX]
- Multidimensional Expressions [Analysis Services], tuples
- member functions [MDX]
- sets [MDX]
- MDX [Analysis Services], members
- member names [MDX]
- Multidimensional Expressions [Analysis Services], sets
- tuple functions
- tuples
- set functions [MDX]
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ce3bf2d5ad7df2b1cd74897b3b49c7cef97e8ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585628"
---
# <a name="working-with-members-tuples-and-sets-mdx"></a><span data-ttu-id="1921e-102">使用成員、Tuple 和集合 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1921e-102">Working with Members, Tuples, and Sets (MDX)</span></span>
  <span data-ttu-id="1921e-103">MDX 提供許多會傳回一或多個成員、Tuple 或集合的函數，或作用於成員、Tuple 或集合的函數。</span><span class="sxs-lookup"><span data-stu-id="1921e-103">MDX provides numerous functions that return one or more members, tuples, or sets; or that act upon a member, tuple, or set.</span></span>  
  
## <a name="member-functions"></a><span data-ttu-id="1921e-104">成員函數</span><span class="sxs-lookup"><span data-stu-id="1921e-104">Member Functions</span></span>  
 <span data-ttu-id="1921e-105">MDX 提供數個函數，用來從其他 MDX 實體 (例如維度、層級、集合或 Tuple) 擷取成員。</span><span class="sxs-lookup"><span data-stu-id="1921e-105">MDX provides several functions for retrieving members from other MDX entities, such as from dimensions, levels, sets, or tuples.</span></span> <span data-ttu-id="1921e-106">例如， [FirstChild](/sql/mdx/firstchild-mdx) 函數會在成員上作用並且會傳回成員。</span><span class="sxs-lookup"><span data-stu-id="1921e-106">For example, the [FirstChild](/sql/mdx/firstchild-mdx) function is a function that acts upon a member and returns a member.</span></span>  
  
 <span data-ttu-id="1921e-107">若要取得 Time 維度的第一個子成員，您可以明確陳述該成員，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1921e-107">To obtain the first child member of the Time dimension, you can explicitly state the member, as in the following example.</span></span>  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="1921e-108">您也可以使用 `FirstChild` 函數來傳回相同的成員，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1921e-108">You can also use the `FirstChild` function to return the same member, as in the following example.</span></span>  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="1921e-109">如需 MDX 成員函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-109">For more information about MDX member functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="tuple-functions"></a><span data-ttu-id="1921e-110">Tuple 函數</span><span class="sxs-lookup"><span data-stu-id="1921e-110">Tuple Functions</span></span>  
 <span data-ttu-id="1921e-111">MDX 提供數個會傳回 Tuple 的函數，在接受 Tuple 的任何地方都可以使用這些函數。</span><span class="sxs-lookup"><span data-stu-id="1921e-111">MDX provides several functions that return tuples, and they can be used anywhere that a tuple is accepted.</span></span> <span data-ttu-id="1921e-112">例如，[Item &#40;Tuple&#41; &#40;MDX&#41;](/sql/mdx/item-tuple-mdx) 函數可以用來擷取集合中的第一個 Tuple，當您知道集合由單一 Tuple 組成，並且您要提供該 Tuple 給需要 Tuple 的函數時，此函數會非常有用。</span><span class="sxs-lookup"><span data-stu-id="1921e-112">For example, the [Item &#40;Tuple&#41; &#40;MDX&#41;](/sql/mdx/item-tuple-mdx) function can be used to extract the first tuple from set, which is very useful when you know that a set is composed of a single tuple and you want to supply that tuple to a function that requires a tuple.</span></span>  
  
 <span data-ttu-id="1921e-113">下列範例會從資料行軸上的 Tuple 集合傳回第一個 Tuple。</span><span class="sxs-lookup"><span data-stu-id="1921e-113">The following example returns the first tuple from within the set of tuples on the column axis.</span></span>  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="1921e-114">如需 Tuple 函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-114">For more information about tuple functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="set-functions"></a><span data-ttu-id="1921e-115">集合函數</span><span class="sxs-lookup"><span data-stu-id="1921e-115">Set Functions</span></span>  
 <span data-ttu-id="1921e-116">MDX 提供數個會傳回集合的函數。</span><span class="sxs-lookup"><span data-stu-id="1921e-116">MDX provides several functions that return sets.</span></span> <span data-ttu-id="1921e-117">明顯的輸入 Tuple 並將它們以大括號括起來並不是擷取集合的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="1921e-117">Explicitly typing tuples and enclosing them in braces is not the only way to retrieve a set.</span></span> <span data-ttu-id="1921e-118">如需傳回集合之成員函數的詳細資訊，請參閱 [MDX 的關鍵概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1921e-118">For more information about the members function to return a set, see [Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md).</span></span> <span data-ttu-id="1921e-119">還有許多其他集合函數。</span><span class="sxs-lookup"><span data-stu-id="1921e-119">There are many additional set functions.</span></span>  
  
 <span data-ttu-id="1921e-120">您可以使用冒號運算子以成員的自然順序來建立集合。</span><span class="sxs-lookup"><span data-stu-id="1921e-120">The colon operator lets you use the natural order of members to create a set.</span></span> <span data-ttu-id="1921e-121">例如，下列範例中顯示的集合包含 2002 日曆年度第一季到第四季的 Tuple：</span><span class="sxs-lookup"><span data-stu-id="1921e-121">For example, the set shown in the following example contains tuples for the 1st through the 4th quarter of calendar year 2002.</span></span>  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="1921e-122">如果不要使用冒號運算子來建立集合，您也可以指定 Tuple 來建立相同的成員集合，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1921e-122">If you do not use the colon operator to create the set, you can create the same set of members by specifying the tuples in the following example.</span></span>  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="1921e-123">冒號運算式是一個包含函數。</span><span class="sxs-lookup"><span data-stu-id="1921e-123">The colon operator is an inclusive function.</span></span> <span data-ttu-id="1921e-124">冒號運算子兩旁的成員都會包含在結果集中。</span><span class="sxs-lookup"><span data-stu-id="1921e-124">The members on both sides of the colon operator are included in the resulting set.</span></span>  
  
 <span data-ttu-id="1921e-125">如需集合函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-125">For more information about set functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="array-functions"></a><span data-ttu-id="1921e-126">陣列函式</span><span class="sxs-lookup"><span data-stu-id="1921e-126">Array Functions</span></span>  
 <span data-ttu-id="1921e-127">陣列函數會作用於集合並且會傳回陣列。</span><span class="sxs-lookup"><span data-stu-id="1921e-127">An array function acts upon a set and returns an array.</span></span> <span data-ttu-id="1921e-128">如需陣列函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-128">For more information about array functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="hierarchy-functions"></a><span data-ttu-id="1921e-129">階層函數</span><span class="sxs-lookup"><span data-stu-id="1921e-129">Hierarchy Functions</span></span>  
 <span data-ttu-id="1921e-130">階層函數會作用於成員、層級、階層或字串，然後傳回階層。</span><span class="sxs-lookup"><span data-stu-id="1921e-130">A hierarchy function returns a hierarchy by acting upon a member, level, hierarchy, or string.</span></span> <span data-ttu-id="1921e-131">如需階層函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-131">For more information about hierarchy functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="level-functions"></a><span data-ttu-id="1921e-132">層級函數</span><span class="sxs-lookup"><span data-stu-id="1921e-132">Level Functions</span></span>  
 <span data-ttu-id="1921e-133">層級函數會作用在成員、層級或字串，然後傳回層級。</span><span class="sxs-lookup"><span data-stu-id="1921e-133">A level function returns a level by acting upon a member, level, or string.</span></span> <span data-ttu-id="1921e-134">如需層級函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-134">For more information about level functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="logical-functions"></a><span data-ttu-id="1921e-135">邏輯函數</span><span class="sxs-lookup"><span data-stu-id="1921e-135">Logical Functions</span></span>  
 <span data-ttu-id="1921e-136">邏輯函數會作用在 MDX 運算式，以傳回運算式中 Tuple、成員或集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1921e-136">A logical function acts upon a MDX expression to return information about the tuples, members, or sets in the expression.</span></span> <span data-ttu-id="1921e-137">例如，[IsEmpty &#40;MDX&#41;](/sql/mdx/isempty-mdx) 函數會評估運算式傳回的是否為空資料格值。</span><span class="sxs-lookup"><span data-stu-id="1921e-137">For example, the [IsEmpty &#40;MDX&#41;](/sql/mdx/isempty-mdx) function evaluates whether an expression has returned an empty cell value.</span></span> <span data-ttu-id="1921e-138">如需邏輯函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-138">For more information about logical functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="numeric-functions"></a><span data-ttu-id="1921e-139">數值函數</span><span class="sxs-lookup"><span data-stu-id="1921e-139">Numeric Functions</span></span>  
 <span data-ttu-id="1921e-140">數值函數會作用在 MDX 運算式以傳回純量值。</span><span class="sxs-lookup"><span data-stu-id="1921e-140">A numeric function acts upon a MDX expression to return a scalar value.</span></span> <span data-ttu-id="1921e-141">例如，[Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) 函數會彙總指定集合中 Tuple 的量值後，傳回導出的純量值。</span><span class="sxs-lookup"><span data-stu-id="1921e-141">For example, the [Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) function returns a scalar value calculated by aggregating measures over the tuples in a specified set.</span></span> <span data-ttu-id="1921e-142">如需數值函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-142">For more information about numeric functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="string-functions"></a><span data-ttu-id="1921e-143">字串函式</span><span class="sxs-lookup"><span data-stu-id="1921e-143">String Functions</span></span>  
 <span data-ttu-id="1921e-144">字串函數會作用在 MDX 運算式以傳回字串。</span><span class="sxs-lookup"><span data-stu-id="1921e-144">A string function acts upon a MDX expression to return a string.</span></span> <span data-ttu-id="1921e-145">例如，[UniqueName &#40;MDX&#41;](/sql/mdx/uniquename-mdx) 函數會傳回包含維度、階層、層級或成員唯一名稱的字串值。</span><span class="sxs-lookup"><span data-stu-id="1921e-145">For example, the [UniqueName &#40;MDX&#41;](/sql/mdx/uniquename-mdx) function returns a string value containing the unique name of a dimension, hierarchy, level, or member.</span></span> <span data-ttu-id="1921e-146">如需字串函數的詳細資訊，請參閱 [MDX 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="1921e-146">For more information about string functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1921e-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1921e-147">See Also</span></span>  
 <span data-ttu-id="1921e-148">[MDX 中的重要概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1921e-148">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="1921e-149">[MDX 查詢基本概念 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1921e-149">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="1921e-150">MDX 函數參考 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="1921e-150">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
