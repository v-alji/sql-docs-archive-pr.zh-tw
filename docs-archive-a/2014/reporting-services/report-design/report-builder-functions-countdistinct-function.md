---
title: CountDistinct 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 902c251e-e1e8-41d2-ac20-5bb6138ac410
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62fab53d4f26a874ac40e0a915c4242a41c72ce0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595728"
---
# <a name="countdistinct-function-report-builder-and-ssrs"></a><span data-ttu-id="2d0c0-102">CountDistinct 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2d0c0-102">CountDistinct Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2d0c0-103">傳回運算式指定的所有非 Null 相異值的計數 (在給定範圍的內容中評估)。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-103">Returns a count of all distinct non-null values specified by the expression, evaluated in the context of the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="2d0c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d0c0-104">Syntax</span></span>  
  
```  
  
CountDistinct(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d0c0-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d0c0-105">Parameters</span></span>  
 <span data-ttu-id="2d0c0-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="2d0c0-106">*expression*</span></span>  
 <span data-ttu-id="2d0c0-107">(`Variant`) 要在其上執行彙總的運算式。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-107">(`Variant`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="2d0c0-108">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="2d0c0-108">*scope*</span></span>  
 <span data-ttu-id="2d0c0-109">(`String`) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-109">(`String`) Optional.</span></span> <span data-ttu-id="2d0c0-110">包含要套用彙總函式之報表項目的資料集、群組或資料區的名稱。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="2d0c0-111">如果未指定 *scope* ，則使用目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="2d0c0-112">*遞迴*</span><span class="sxs-lookup"><span data-stu-id="2d0c0-112">*recursive*</span></span>  
 <span data-ttu-id="2d0c0-113">(**列舉型別**) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="2d0c0-114">`Simple` (預設值) 或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="2d0c0-115">指定是否要以遞迴方式執行彙總。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="2d0c0-116">傳回類型</span><span class="sxs-lookup"><span data-stu-id="2d0c0-116">Return Type</span></span>  
 <span data-ttu-id="2d0c0-117">傳回 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-117">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d0c0-118">備註</span><span class="sxs-lookup"><span data-stu-id="2d0c0-118">Remarks</span></span>  
 <span data-ttu-id="2d0c0-119">*scope* 的值必須是字串常數，而且不得為運算式。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-119">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="2d0c0-120">如果是未指定其他彙總的外部彙總， *scope* 必須參考目前的範圍或是包含的範圍。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-120">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="2d0c0-121">如果是彙總的彙總，巢狀彙總可以指定子範圍。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-121">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="2d0c0-122">*Expression* 可以包含巢狀彙總函式的呼叫，其中包含下列例外和條件：</span><span class="sxs-lookup"><span data-stu-id="2d0c0-122">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="2d0c0-123">巢狀彙總的*Scope* 必須與外部彙總的範圍相同或是由外部彙總的範圍所限制。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-123">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="2d0c0-124">如果是運算式中的所有相異範圍，一個範圍必須與所有其他範圍之間具有子關聯性。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-124">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="2d0c0-125">巢狀彙總的*Scope* 不得為資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-125">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="2d0c0-126">*運算式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函數。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-126">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="2d0c0-127">*Expression* 不得包含指定 *recursive*的巢狀彙總。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-127">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="2d0c0-128">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-128">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="2d0c0-129">如需遞迴彙總的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-129">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d0c0-130">範例</span><span class="sxs-lookup"><span data-stu-id="2d0c0-130">Example</span></span>  
 <span data-ttu-id="2d0c0-131">下列程式碼範例顯示的運算式會針對預設範圍及父群組範圍，計算 `Size` 的非 Null 唯一值數目。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-131">The following code example shows an expression that calculates the number of unique non-null values of `Size` for the default scope and for a parent group scope.</span></span> <span data-ttu-id="2d0c0-132">運算式會加到屬於子群組 `GroupbySubcategory`的資料列中的資料格。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-132">The expression is added to a cell in a row that belongs to the child group `GroupbySubcategory`.</span></span> <span data-ttu-id="2d0c0-133">父群組是 `GroupbyCategory`。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-133">The parent group is `GroupbyCategory`.</span></span> <span data-ttu-id="2d0c0-134">運算式會先顯示 `GroupbySubcategory` (預設範圍) 的結果，再顯示 `GroupbyCategory` (父群組範圍) 的結果。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-134">The expression displays the results for `GroupbySubcategory` (the default scope) and then for `GroupbyCategory` (the parent group scope).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d0c0-135">運算式不會真的包含歸位字元和分行符號；範例程式碼是為了支援文件轉譯器而包含這些字元及符號。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-135">Expressions should not contain actual carriage returns and line breaks; these are included in the example code to support documentation renderers.</span></span> <span data-ttu-id="2d0c0-136">如果要複製下列範例，請移除每一行的歸位字元。</span><span class="sxs-lookup"><span data-stu-id="2d0c0-136">If you copy the following example, remove carriage returns from each line.</span></span>  
  
```  
="Distinct count (Subcategory): " & CountDistinct(Fields!Size.Value) &   
"Distinct count (Category): " & CountDistinct(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d0c0-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d0c0-137">See Also</span></span>  
 <span data-ttu-id="2d0c0-138">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2d0c0-138">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2d0c0-139">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2d0c0-139">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2d0c0-140">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2d0c0-140">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2d0c0-141">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2d0c0-141">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
