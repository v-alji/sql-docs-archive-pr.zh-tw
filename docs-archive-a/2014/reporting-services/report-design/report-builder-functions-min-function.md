---
title: Min 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aa1ee96f-9fc4-4775-b9d4-c6187dc37e27
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 82bb852eeb334a0c7bde3e157f0035db766039da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595712"
---
# <a name="min-function-report-builder-and-ssrs"></a><span data-ttu-id="dbde7-102">Min 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="dbde7-102">Min Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dbde7-103">傳回運算式指定的所有非 Null 數值的最小值 (在給定範圍的內容中)。</span><span class="sxs-lookup"><span data-stu-id="dbde7-103">Returns the minimum value of all non-null numeric values specified by the expression, in the context of the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="dbde7-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbde7-104">Syntax</span></span>  
  
```  
  
Min(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbde7-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbde7-105">Parameters</span></span>  
 <span data-ttu-id="dbde7-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="dbde7-106">*expression*</span></span>  
 <span data-ttu-id="dbde7-107">(`Variant`) 要在其上執行彙總的運算式。</span><span class="sxs-lookup"><span data-stu-id="dbde7-107">(`Variant`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="dbde7-108">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="dbde7-108">*scope*</span></span>  
 <span data-ttu-id="dbde7-109">(`String`) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="dbde7-109">(`String`) Optional.</span></span> <span data-ttu-id="dbde7-110">包含要套用彙總函式之報表項目的資料集、群組或資料區的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbde7-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="dbde7-111">如果未指定 *scope* ，則使用目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="dbde7-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="dbde7-112">*遞迴*</span><span class="sxs-lookup"><span data-stu-id="dbde7-112">*recursive*</span></span>  
 <span data-ttu-id="dbde7-113">(**列舉型別**) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="dbde7-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="dbde7-114">`Simple` (預設值) 或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="dbde7-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="dbde7-115">指定是否要以遞迴方式執行彙總。</span><span class="sxs-lookup"><span data-stu-id="dbde7-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="dbde7-116">傳回類型</span><span class="sxs-lookup"><span data-stu-id="dbde7-116">Return Type</span></span>  
 <span data-ttu-id="dbde7-117">取決於運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="dbde7-117">Determined by the type of the expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbde7-118">備註</span><span class="sxs-lookup"><span data-stu-id="dbde7-118">Remarks</span></span>  
 <span data-ttu-id="dbde7-119">運算式中指定的資料集必須具有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="dbde7-119">The set of data specified in the expression must have the same data type.</span></span> <span data-ttu-id="dbde7-120">若要將具有多個數值資料類型的資料轉換成相同的資料類型，請使用 `CInt`、`CDbl` 或 `CDec` 等轉換函數。</span><span class="sxs-lookup"><span data-stu-id="dbde7-120">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="dbde7-121">如需詳細資訊，請參閱 [類型轉換函數](https://go.microsoft.com/fwlink/?LinkId=96142)。</span><span class="sxs-lookup"><span data-stu-id="dbde7-121">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="dbde7-122">*scope* 的值必須是字串常數，而且不得為運算式。</span><span class="sxs-lookup"><span data-stu-id="dbde7-122">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="dbde7-123">如果是未指定其他彙總的外部彙總， *scope* 必須參考目前的範圍或是包含的範圍。</span><span class="sxs-lookup"><span data-stu-id="dbde7-123">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="dbde7-124">如果是彙總的彙總，巢狀彙總可以指定子範圍。</span><span class="sxs-lookup"><span data-stu-id="dbde7-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="dbde7-125">*Expression* 可以包含巢狀彙總函式的呼叫，其中包含下列例外和條件：</span><span class="sxs-lookup"><span data-stu-id="dbde7-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="dbde7-126">巢狀彙總的*Scope* 必須與外部彙總的範圍相同或是由外部彙總的範圍所限制。</span><span class="sxs-lookup"><span data-stu-id="dbde7-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="dbde7-127">如果是運算式中的所有相異範圍，一個範圍必須與所有其他範圍之間具有子關聯性。</span><span class="sxs-lookup"><span data-stu-id="dbde7-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="dbde7-128">巢狀彙總的*Scope* 不得為資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbde7-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="dbde7-129">*運算式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函數。</span><span class="sxs-lookup"><span data-stu-id="dbde7-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="dbde7-130">*Expression* 不得包含指定 *recursive*的巢狀彙總。</span><span class="sxs-lookup"><span data-stu-id="dbde7-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="dbde7-131">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="dbde7-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="dbde7-132">如需遞迴彙總的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dbde7-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbde7-133">範例</span><span class="sxs-lookup"><span data-stu-id="dbde7-133">Example</span></span>  
 <span data-ttu-id="dbde7-134">下列程式碼範例提供目前範圍中的最低總計。</span><span class="sxs-lookup"><span data-stu-id="dbde7-134">The following code example provides the lowest total in the current scope.</span></span>  
  
```  
=Min(Fields!OrderTotal.Value)  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbde7-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbde7-135">See Also</span></span>  
 <span data-ttu-id="dbde7-136">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dbde7-136">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dbde7-137">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dbde7-137">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dbde7-138">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dbde7-138">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dbde7-139">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dbde7-139">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
