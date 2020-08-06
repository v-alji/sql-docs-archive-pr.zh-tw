---
title: 建立查詢範圍的資料格計算 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped cell calculations [MDX]
ms.assetid: 45987daa-4400-41e9-add7-2428fd75709b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a9c9d529bfeb26b959b2521e4ce3c3d7f10d082
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708753"
---
# <a name="creating-query-scoped-cell-calculations-mdx"></a><span data-ttu-id="3f732-102">建立查詢範圍資料格計算 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3f732-102">Creating Query-Scoped Cell Calculations (MDX)</span></span>
  <span data-ttu-id="3f732-103">您可以使用多維度運算式 (MDX) 的 `WITH` 關鍵字，描述查詢內容中的導出資料格。</span><span class="sxs-lookup"><span data-stu-id="3f732-103">You use the `WITH` keyword in Multidimensional Expressions (MDX) to describe calculated cells within the context of a query.</span></span> <span data-ttu-id="3f732-104">`WITH` 關鍵字有下列語法：</span><span class="sxs-lookup"><span data-stu-id="3f732-104">The `WITH` keyword has the following syntax:</span></span>  
  
```  
WITH CELL CALCULATION Cube_Name.CellCalc_Identifier  String_Expression  
```  
  
 <span data-ttu-id="3f732-105">`CellCalc_Identifier` 值是導出資料格的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f732-105">The `CellCalc_Identifier` value is the name of the calculated cells.</span></span> <span data-ttu-id="3f732-106">`String_Expression` 值包含正交、一維的 MDX 集合運算式。</span><span class="sxs-lookup"><span data-stu-id="3f732-106">The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions.</span></span> <span data-ttu-id="3f732-107">每個集合運算式都必須解析為下表列出的其中一種類別目錄。</span><span class="sxs-lookup"><span data-stu-id="3f732-107">Each of these set expressions must resolve to one of the categories listed in the following table.</span></span>  
  
|<span data-ttu-id="3f732-108">類別</span><span class="sxs-lookup"><span data-stu-id="3f732-108">Category</span></span>|<span data-ttu-id="3f732-109">描述</span><span class="sxs-lookup"><span data-stu-id="3f732-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3f732-110">空集合</span><span class="sxs-lookup"><span data-stu-id="3f732-110">Empty set</span></span>|<span data-ttu-id="3f732-111">解析成空集合的 MDX 命名集運算式。</span><span class="sxs-lookup"><span data-stu-id="3f732-111">An MDX set expression that resolves into an empty set.</span></span> <span data-ttu-id="3f732-112">在此情況下，導出資料格的範圍是整個 Cube。</span><span class="sxs-lookup"><span data-stu-id="3f732-112">In this case, the scope of the calculated cell is the whole cube.</span></span>|  
|<span data-ttu-id="3f732-113">單一成員集合</span><span class="sxs-lookup"><span data-stu-id="3f732-113">Single member set</span></span>|<span data-ttu-id="3f732-114">解析成單一成員集合的 MDX 命名集運算式。</span><span class="sxs-lookup"><span data-stu-id="3f732-114">An MDX set expression that resolves into a single member.</span></span>|  
|<span data-ttu-id="3f732-115">單一層級成員</span><span class="sxs-lookup"><span data-stu-id="3f732-115">Set of level members</span></span>|<span data-ttu-id="3f732-116">解析成單一層級成員的 MDX 命名集運算式。</span><span class="sxs-lookup"><span data-stu-id="3f732-116">An MDX set expression that resolves into the members of a single level.</span></span> <span data-ttu-id="3f732-117">*Level_Expression*是這類集合運算式的範例。`Members`</span><span class="sxs-lookup"><span data-stu-id="3f732-117">An example of such a set expression is the *Level_Expression*.`Members`</span></span> <span data-ttu-id="3f732-118">MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="3f732-118">MDX function.</span></span> <span data-ttu-id="3f732-119">若要包含匯出成員，請使用*Level_Expression*。`AllMembers`</span><span class="sxs-lookup"><span data-stu-id="3f732-119">To include calculated members, use the *Level_Expression*.`AllMembers`</span></span> <span data-ttu-id="3f732-120">MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="3f732-120">MDX function.</span></span> <span data-ttu-id="3f732-121">如需詳細資訊，請參閱 [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx)。</span><span class="sxs-lookup"><span data-stu-id="3f732-121">For more information, see [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).</span></span>|  
|<span data-ttu-id="3f732-122">下階集合</span><span class="sxs-lookup"><span data-stu-id="3f732-122">Set of descendants</span></span>|<span data-ttu-id="3f732-123">解析為指定成員之下階的 MDX 集合運算式。</span><span class="sxs-lookup"><span data-stu-id="3f732-123">An MDX set expression that resolves into the descendants of a specified member.</span></span> <span data-ttu-id="3f732-124">這類集合運算式的範例是 `Descendants` (*Member_Expression*、 *Level_Expresion* *Desc_Flag*) MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="3f732-124">An example of such a set expression is the `Descendants`(*Member_Expression*, *Level_Expresion*, *Desc_Flag*) MDX function.</span></span> <span data-ttu-id="3f732-125">如需詳細資訊，請參閱 [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx)。</span><span class="sxs-lookup"><span data-stu-id="3f732-125">For more information, see [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).</span></span>|  
  
 <span data-ttu-id="3f732-126">如果 `String_Expression` 引數未描述維度，MDX 會假設已包含所有成員以供建構計算 Subcube。</span><span class="sxs-lookup"><span data-stu-id="3f732-126">If the `String_Expression` argument does not describe a dimension, MDX assumes that all members are included for the purposes of constructing the calculation subcube.</span></span> <span data-ttu-id="3f732-127">因此，如果 `String_Expression` 引數是 NULL，導出資料格定義就會套用到整個 Cube。</span><span class="sxs-lookup"><span data-stu-id="3f732-127">Therefore, if the `String_Expression` argument is NULL, the calculated cells definition applies to the whole cube.</span></span>  
  
 <span data-ttu-id="3f732-128">`MDX_Expression` 引數包含一個 MDX 運算式，此運算式會將 `String_Expression` 引數中定義的所有資料格評估為資料格值。</span><span class="sxs-lookup"><span data-stu-id="3f732-128">The `MDX_Expression` argument contains an MDX expression that evaluates to a cell value for all the cells defined in the `String_Expression` argument.</span></span>  
  
## <a name="additional-considerations"></a><span data-ttu-id="3f732-129">其他考量</span><span class="sxs-lookup"><span data-stu-id="3f732-129">Additional Considerations</span></span>  
 <span data-ttu-id="3f732-130">`CONDITION` 屬性指定的計算條件，MDX 只會處理一次。</span><span class="sxs-lookup"><span data-stu-id="3f732-130">MDX processes the calculation condition, specified by the `CONDITION` property, only once.</span></span> <span data-ttu-id="3f732-131">這個單次處理特性提高了評估多重導出資料格定義時的效能，特別是在 Cube 傳遞之間有重疊的導出資料格時。</span><span class="sxs-lookup"><span data-stu-id="3f732-131">This single processing provides increased performance for the evaluation of multiple calculated cells definitions, especially with overlapping calculated cells across cube passes.</span></span>  
  
 <span data-ttu-id="3f732-132">發生單次處理的時機，視導出資料格定義的建立範圍而定：</span><span class="sxs-lookup"><span data-stu-id="3f732-132">When this single processing occurs depends on the creation scope of the calculated cells definition:</span></span>  
  
-   <span data-ttu-id="3f732-133">如果做為 Cube 的一部份建立在全域範圍，MDX 會在處理 Cube 時處理計算條件。</span><span class="sxs-lookup"><span data-stu-id="3f732-133">If created at global scope, as part of a cube, MDX process the calculation condition when the cube is processed.</span></span> <span data-ttu-id="3f732-134">如果您以任何方式修改 Cube 中的資料格，而且資料格包含在導出資料格定義的計算 Subcube 中，則在重新處理 Cube 之前，計算條件可能不正確。</span><span class="sxs-lookup"><span data-stu-id="3f732-134">If cells are modified in the cube in any way, and the cells are included in the calculation subcube of a calculated cells definition, the calculation condition may not be accurate until the cube is reprocessed.</span></span> <span data-ttu-id="3f732-135">例如，進行回寫可能會修改資料格。</span><span class="sxs-lookup"><span data-stu-id="3f732-135">Cell modification can occur from writebacks, for example.</span></span> <span data-ttu-id="3f732-136">重新處理 Cube 時就會重新處理計算條件。</span><span class="sxs-lookup"><span data-stu-id="3f732-136">The calculation condition is reprocessed when the cube is reprocessed.</span></span>  
  
-   <span data-ttu-id="3f732-137">如果建立在工作階段範圍，那麼在工作階段期間發出陳述式時，MDX 就會處理計算條件。</span><span class="sxs-lookup"><span data-stu-id="3f732-137">If created at session scope, MDX process the calculation condition when the statement is issued during the session.</span></span> <span data-ttu-id="3f732-138">與全域建立的導出資料格定義一樣，如果修改資料格的話，導出資料格定義的計算條件可能不正確。</span><span class="sxs-lookup"><span data-stu-id="3f732-138">As with calculated cells definitions created globally, if the cells are modified, the calculation condition may not be accurate for the calculated cells definition.</span></span>  
  
-   <span data-ttu-id="3f732-139">如果建立在查詢範圍，MDX 會在查詢執行時處理計算條件。</span><span class="sxs-lookup"><span data-stu-id="3f732-139">If created at query scope, MDX processes the calculation condition when the query runs.</span></span> <span data-ttu-id="3f732-140">資料格修改問題在這裏也適用，但是因為 MDX 查詢執行的處理時間很短，所以資料延遲問題會減到最少。</span><span class="sxs-lookup"><span data-stu-id="3f732-140">The cell modification issue applies here, also, although data latency issues are minimal because of the low processing time of MDX query execution.</span></span>  
  
 <span data-ttu-id="3f732-141">另一方面，每當對 Cube (涉及導出資料格定義中包含的資料格) 發出 MDX 查詢時，MDX 就會處理計算公式。</span><span class="sxs-lookup"><span data-stu-id="3f732-141">On the other hand, MDX processes the calculation formula whenever an MDX query is issued against the cube involving cells included in the calculated cells definition.</span></span> <span data-ttu-id="3f732-142">不管建立範圍為何，都會發生這個處理。</span><span class="sxs-lookup"><span data-stu-id="3f732-142">This processing occurs regardless of the creation scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f732-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f732-143">See Also</span></span>  
 [<span data-ttu-id="3f732-144">CREATE CELL CALCULATION 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="3f732-144">CREATE CELL CALCULATION Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
  
