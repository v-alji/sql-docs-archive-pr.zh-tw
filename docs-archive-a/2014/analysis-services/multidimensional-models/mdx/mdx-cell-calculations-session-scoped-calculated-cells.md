---
title: 建立會話範圍匯出資料格 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 199de07778a153cd1bc40b5033d364e5e0055bd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594741"
---
# <a name="creating-session-scoped-calculated-cells"></a><span data-ttu-id="e53d1-102">建立工作階段範圍導出資料格</span><span class="sxs-lookup"><span data-stu-id="e53d1-102">Creating Session-Scoped Calculated Cells</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="e53d1-103">此語法已經被取代。</span><span class="sxs-lookup"><span data-stu-id="e53d1-103">This syntax has been deprecated.</span></span> <span data-ttu-id="e53d1-104">您應該改用 MDX 指派。</span><span class="sxs-lookup"><span data-stu-id="e53d1-104">You should use MDX assignments should instead.</span></span> <span data-ttu-id="e53d1-105">如需指派的詳細資訊，請參閱[基本 MDX 指令碼 &#40;MDX&#41;](the-basic-mdx-script-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="e53d1-105">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="e53d1-106">若要建立可供相同工作階段的所有查詢使用的導出資料格，您可以使用 [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) 陳述式或 [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e53d1-106">To create calculated cells that are available to all queries in the same session, you can use either the [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) statement or the [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) statement.</span></span> <span data-ttu-id="e53d1-107">兩個陳述式會有相同的結果。</span><span class="sxs-lookup"><span data-stu-id="e53d1-107">Both statements have the same result.</span></span>  
  
## <a name="create-cell-calculation-syntax"></a><span data-ttu-id="e53d1-108">CREATE CELL CALCULATION 語法</span><span class="sxs-lookup"><span data-stu-id="e53d1-108">CREATE CELL CALCULATION Syntax</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e53d1-109">此語法已經被取代。</span><span class="sxs-lookup"><span data-stu-id="e53d1-109">This syntax has been deprecated.</span></span> <span data-ttu-id="e53d1-110">您應該改用 MDX 指派。</span><span class="sxs-lookup"><span data-stu-id="e53d1-110">You should use MDX assignments should instead.</span></span> <span data-ttu-id="e53d1-111">如需指派的詳細資訊，請參閱[基本 MDX 指令碼 &#40;MDX&#41;](the-basic-mdx-script-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="e53d1-111">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="e53d1-112">請使用下列語法以使用 CREATE CELL CALCULATION 陳述式，定義工作階段範圍導出資料格：</span><span class="sxs-lookup"><span data-stu-id="e53d1-112">Use the following syntax to use the CREATE CELL CALCULATION statement to define a session-scoped calculated cell:</span></span>  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## <a name="alter-cube-syntax"></a><span data-ttu-id="e53d1-113">ALTER CUBE 語法</span><span class="sxs-lookup"><span data-stu-id="e53d1-113">ALTER CUBE Syntax</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e53d1-114">此語法已經被取代。</span><span class="sxs-lookup"><span data-stu-id="e53d1-114">This syntax has been deprecated.</span></span> <span data-ttu-id="e53d1-115">您應該改用 MDX 指派。</span><span class="sxs-lookup"><span data-stu-id="e53d1-115">You should use MDX assignments should instead.</span></span> <span data-ttu-id="e53d1-116">如需指派的詳細資訊，請參閱[基本 MDX 指令碼 &#40;MDX&#41;](the-basic-mdx-script-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="e53d1-116">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="e53d1-117">請使用下列語法以使用 ALTER CUBE 述式，定義工作階段範圍導出資料格：</span><span class="sxs-lookup"><span data-stu-id="e53d1-117">Use the following syntax to use the ALTER CUBE statement to define a session-scoped calculated cell:</span></span>  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 <span data-ttu-id="e53d1-118">`String_Expression` 值包含正交、一維的 MDX 集合運算式的清單，其中的每一項都必須解析成下表列出集合的其中一個類別目錄</span><span class="sxs-lookup"><span data-stu-id="e53d1-118">The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions, each of which must resolve to one of the categories of sets that are listed in the following table.</span></span>  
  
|<span data-ttu-id="e53d1-119">類別</span><span class="sxs-lookup"><span data-stu-id="e53d1-119">Category</span></span>|<span data-ttu-id="e53d1-120">描述</span><span class="sxs-lookup"><span data-stu-id="e53d1-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e53d1-121">空集合</span><span class="sxs-lookup"><span data-stu-id="e53d1-121">Empty set</span></span>|<span data-ttu-id="e53d1-122">解析成空集合的 MDX 命名集運算式。</span><span class="sxs-lookup"><span data-stu-id="e53d1-122">An MDX set expression that resolves into an empty set.</span></span> <span data-ttu-id="e53d1-123">在此情況下，導出資料格的範圍是整個 Cube。</span><span class="sxs-lookup"><span data-stu-id="e53d1-123">In this case, the scope of the calculated cell is the whole cube.</span></span>|  
|<span data-ttu-id="e53d1-124">單一成員集合</span><span class="sxs-lookup"><span data-stu-id="e53d1-124">Single member set</span></span>|<span data-ttu-id="e53d1-125">解析成單一成員集合的 MDX 命名集運算式。</span><span class="sxs-lookup"><span data-stu-id="e53d1-125">An MDX set expression that resolves into a single member.</span></span>|  
|<span data-ttu-id="e53d1-126">單一層級成員</span><span class="sxs-lookup"><span data-stu-id="e53d1-126">Set of level members</span></span>|<span data-ttu-id="e53d1-127">解析成單一層級成員的 MDX 命名集運算式。</span><span class="sxs-lookup"><span data-stu-id="e53d1-127">An MDX set expression that resolves into the members of a single level.</span></span> <span data-ttu-id="e53d1-128">*Level_Expression*是其中一個範例。`Members`</span><span class="sxs-lookup"><span data-stu-id="e53d1-128">An example of this is the *Level_Expression*.`Members`</span></span> <span data-ttu-id="e53d1-129">MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="e53d1-129">MDX function.</span></span> <span data-ttu-id="e53d1-130">若要包含匯出成員，請使用*Level_Expression*。`AllMembers`</span><span class="sxs-lookup"><span data-stu-id="e53d1-130">To include calculated members, use the *Level_Expression*.`AllMembers`</span></span> <span data-ttu-id="e53d1-131">MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="e53d1-131">MDX function.</span></span><br /><br /> <span data-ttu-id="e53d1-132">如需詳細資訊，請參閱 [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx)。</span><span class="sxs-lookup"><span data-stu-id="e53d1-132">For more information, see [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).</span></span>|  
|<span data-ttu-id="e53d1-133">下階集合</span><span class="sxs-lookup"><span data-stu-id="e53d1-133">Set of descendants</span></span>|<span data-ttu-id="e53d1-134">解析為指定成員之下階的 MDX 集合運算式。</span><span class="sxs-lookup"><span data-stu-id="e53d1-134">An MDX set expression that resolves into the descendants of a specified member.</span></span> <span data-ttu-id="e53d1-135">其中一個範例是 `Descendants` (*Member_Expression*、 *Level_Expression* *Desc_Flag*) MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="e53d1-135">An example of this is the `Descendants`(*Member_Expression*, *Level_Expression*, *Desc_Flag*) MDX function.</span></span><br /><br /> <span data-ttu-id="e53d1-136">如需詳細資訊，請參閱 [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx)。</span><span class="sxs-lookup"><span data-stu-id="e53d1-136">For more information, see [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e53d1-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e53d1-137">See Also</span></span>  
 [<span data-ttu-id="e53d1-138">在 MDX 中建立資料格計算 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="e53d1-138">Building Cell Calculations in MDX &#40;MDX&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
