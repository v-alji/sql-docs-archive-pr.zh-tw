---
title: Union 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c87e16fe-c12a-4c9d-a9df-7a94e229fd04
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c80926be53254ec512b2189c4b67e8cd5885733f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595692"
---
# <a name="union-function-report-builder-and-ssrs"></a><span data-ttu-id="091ed-102">Union 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="091ed-102">Union Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="091ed-103">傳回運算式所指定之所有非 Null 數值的聯集 (在給定範圍中評估)。</span><span class="sxs-lookup"><span data-stu-id="091ed-103">Returns the union of all the non-null numeric values specified by the expression, evaluated in the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="091ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="091ed-104">Syntax</span></span>  
  
```  
  
Union(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="091ed-105">參數</span><span class="sxs-lookup"><span data-stu-id="091ed-105">Parameters</span></span>  
 <span data-ttu-id="091ed-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="091ed-106">*expression*</span></span>  
 <span data-ttu-id="091ed-107">(`SqlGeometry` 或 `SqlGeography`) - 要在其上執行彙總的運算式。</span><span class="sxs-lookup"><span data-stu-id="091ed-107">(`SqlGeometry` or `SqlGeography`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="091ed-108">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="091ed-108">*scope*</span></span>  
 <span data-ttu-id="091ed-109">(`String`) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="091ed-109">(`String`) Optional.</span></span> <span data-ttu-id="091ed-110">包含要套用彙總函式之報表項目的資料集、群組或資料區的名稱。</span><span class="sxs-lookup"><span data-stu-id="091ed-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="091ed-111">如果未指定 *scope* ，則使用目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="091ed-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="091ed-112">*遞迴*</span><span class="sxs-lookup"><span data-stu-id="091ed-112">*recursive*</span></span>  
 <span data-ttu-id="091ed-113">(**列舉型別**) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="091ed-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="091ed-114">`Simple` (預設值) 或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="091ed-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="091ed-115">指定是否要以遞迴方式執行彙總。</span><span class="sxs-lookup"><span data-stu-id="091ed-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return"></a><span data-ttu-id="091ed-116">傳回</span><span class="sxs-lookup"><span data-stu-id="091ed-116">Return</span></span>  
 <span data-ttu-id="091ed-117">根據運算式類型傳回空間物件 (`SqlGeometry` 或 `SqlGeography`)。</span><span class="sxs-lookup"><span data-stu-id="091ed-117">Returns a spatial object, either `SqlGeometry` or `SqlGeography`, based on the expression type.</span></span> <span data-ttu-id="091ed-118">如需 `SqlGeometry` 和 `SqlGeography` 空間資料類型的詳細資訊，請參閱[空間資料類型總覽](../../relational-databases/spatial/spatial-data-types-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="091ed-118">For more information about `SqlGeometry` and `SqlGeography` spatial data types, see [Spatial Data Types Overview](../../relational-databases/spatial/spatial-data-types-overview.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="091ed-119">備註</span><span class="sxs-lookup"><span data-stu-id="091ed-119">Remarks</span></span>  
 <span data-ttu-id="091ed-120">運算式中指定的資料集必須具有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="091ed-120">The set of data specified in the expression must have the same data type.</span></span>  
  
 <span data-ttu-id="091ed-121">*scope* 的值必須是字串常數，而且不得為運算式。</span><span class="sxs-lookup"><span data-stu-id="091ed-121">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="091ed-122">如果是未指定其他彙總的外部彙總， *scope* 必須參考目前的範圍或是包含的範圍。</span><span class="sxs-lookup"><span data-stu-id="091ed-122">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="091ed-123">不支援資料集範圍。</span><span class="sxs-lookup"><span data-stu-id="091ed-123">Dataset scopes are not supported.</span></span> <span data-ttu-id="091ed-124">如果是彙總的彙總，巢狀彙總可以指定子範圍。</span><span class="sxs-lookup"><span data-stu-id="091ed-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="091ed-125">*Expression* 可以包含巢狀彙總函式的呼叫，其中包含下列例外和條件：</span><span class="sxs-lookup"><span data-stu-id="091ed-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="091ed-126">巢狀彙總的*Scope* 必須與外部彙總的範圍相同或是由外部彙總的範圍所限制。</span><span class="sxs-lookup"><span data-stu-id="091ed-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="091ed-127">如果是運算式中的所有相異範圍，一個範圍必須與所有其他範圍之間具有子關聯性。</span><span class="sxs-lookup"><span data-stu-id="091ed-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="091ed-128">巢狀彙總的*Scope* 不得為資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="091ed-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="091ed-129">*運算式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函數。</span><span class="sxs-lookup"><span data-stu-id="091ed-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="091ed-130">*Expression* 不得包含指定 *recursive*的巢狀彙總。</span><span class="sxs-lookup"><span data-stu-id="091ed-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="091ed-131">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="091ed-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="091ed-132">如需遞迴彙總的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="091ed-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="091ed-133">範例</span><span class="sxs-lookup"><span data-stu-id="091ed-133">Example</span></span>  
 <span data-ttu-id="091ed-134">下表顯示 `SqlGeometry` 運算式和 `Union` 結果運算式的範例，使用適用於空間資料的 WKT (已知文字) 格式顯示。</span><span class="sxs-lookup"><span data-stu-id="091ed-134">The following table shows examples of `SqlGeometry` expressions and `Union` result expression, shown in WKT (Well Known Text) format for spatial data.</span></span>  
  
|<span data-ttu-id="091ed-135">具有空間資料的欄位</span><span class="sxs-lookup"><span data-stu-id="091ed-135">Field with spatial data</span></span>|<span data-ttu-id="091ed-136">範例</span><span class="sxs-lookup"><span data-stu-id="091ed-136">Example</span></span>|<span data-ttu-id="091ed-137">聯集結果</span><span class="sxs-lookup"><span data-stu-id="091ed-137">Union result</span></span>|  
|-----------------------------|-------------|------------------|  
|<span data-ttu-id="091ed-138">[PointLocation]</span><span class="sxs-lookup"><span data-stu-id="091ed-138">[PointLocation]</span></span>|<span data-ttu-id="091ed-139">POINT(1 2)</span><span class="sxs-lookup"><span data-stu-id="091ed-139">POINT(1 2)</span></span><br /><br /> <span data-ttu-id="091ed-140">POINT(3 4)</span><span class="sxs-lookup"><span data-stu-id="091ed-140">POINT(3 4)</span></span>|<span data-ttu-id="091ed-141">MULTIPOINT((1 2), (3 4))</span><span class="sxs-lookup"><span data-stu-id="091ed-141">MULTIPOINT((1 2), (3 4))</span></span>|  
|<span data-ttu-id="091ed-142">[PathDefinition]</span><span class="sxs-lookup"><span data-stu-id="091ed-142">[PathDefinition]</span></span>|<span data-ttu-id="091ed-143">LINESTRING(1 2, 3 4)</span><span class="sxs-lookup"><span data-stu-id="091ed-143">LINESTRING(1 2, 3 4)</span></span><br /><br /> <span data-ttu-id="091ed-144">LINESTRING(5 6, 7 8)</span><span class="sxs-lookup"><span data-stu-id="091ed-144">LINESTRING(5 6, 7 8)</span></span>|<span data-ttu-id="091ed-145">MULTILINESTRING((7 8, 5 6), (3 4, 1 2))</span><span class="sxs-lookup"><span data-stu-id="091ed-145">MULTILINESTRING((7 8, 5 6), (3 4, 1 2))</span></span>|  
|<span data-ttu-id="091ed-146">[PolygonDefinition]</span><span class="sxs-lookup"><span data-stu-id="091ed-146">[PolygonDefinition]</span></span>|<span data-ttu-id="091ed-147">POLYGON((1 2, 3 4, 5 2, 1 2))</span><span class="sxs-lookup"><span data-stu-id="091ed-147">POLYGON((1 2, 3 4, 5 2, 1 2))</span></span><br /><br /> <span data-ttu-id="091ed-148">POLYGON((-1 2, -3 4, -5 2, -1 2))</span><span class="sxs-lookup"><span data-stu-id="091ed-148">POLYGON((-1 2, -3 4, -5 2, -1 2))</span></span>|<span data-ttu-id="091ed-149">MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))</span><span class="sxs-lookup"><span data-stu-id="091ed-149">MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))</span></span>|  
  
```  
=Union(Fields!PointLocation.Value)  
=Union(Fields!PathDefinition.Value)  
=Union(Fields!PolygonDefinition.Value, "Group1")  
```  
  
## <a name="see-also"></a><span data-ttu-id="091ed-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="091ed-150">See Also</span></span>  
 <span data-ttu-id="091ed-151">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="091ed-151">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="091ed-152">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="091ed-152">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="091ed-153">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="091ed-153">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="091ed-154">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="091ed-154">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
