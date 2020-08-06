---
title: Last 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 123b78a0-d6c9-4f78-b0e7-73b21854a250
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c343e72e476d4a717ca551eedeb0f02650479ca4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595716"
---
# <a name="last-function-report-builder-and-ssrs"></a><span data-ttu-id="2f805-102">Last 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2f805-102">Last Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2f805-103">傳回所指定運算式給定範圍中的最後一個值。</span><span class="sxs-lookup"><span data-stu-id="2f805-103">Returns the last value in the given scope of the specified expression.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="2f805-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f805-104">Syntax</span></span>  
  
```  
  
Last(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f805-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f805-105">Parameters</span></span>  
 <span data-ttu-id="2f805-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="2f805-106">*expression*</span></span>  
 <span data-ttu-id="2f805-107">(`Variant` 或 `Binary`) 要執行彙總的運算式，例如 `=Fields!Fieldname.Value`。</span><span class="sxs-lookup"><span data-stu-id="2f805-107">(`Variant` or `Binary`) The expression on which to perform the aggregation, for example, `=Fields!Fieldname.Value`.</span></span>  
  
 <span data-ttu-id="2f805-108">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="2f805-108">*scope*</span></span>  
 <span data-ttu-id="2f805-109">(`String`) (選擇性) 包含要套用此函數之報表項目的資料集、資料區域或群組名稱。</span><span class="sxs-lookup"><span data-stu-id="2f805-109">(`String`) (Optional) The name of a dataset, data region, or group that contains the report items to which to apply the function.</span></span> <span data-ttu-id="2f805-110">如果未指定 *scope* ，則使用目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="2f805-110">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="2f805-111">傳回類型</span><span class="sxs-lookup"><span data-stu-id="2f805-111">Return Type</span></span>  
 <span data-ttu-id="2f805-112">由運算式的類型決定。</span><span class="sxs-lookup"><span data-stu-id="2f805-112">Determined by the type of expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f805-113">備註</span><span class="sxs-lookup"><span data-stu-id="2f805-113">Remarks</span></span>  
 <span data-ttu-id="2f805-114">`Last` 函數會在指定的範圍已套用所有排序和篩選之後，以一組資料傳回最後的值。</span><span class="sxs-lookup"><span data-stu-id="2f805-114">The `Last` function returns the final value in a set of data after all sorting and filtering have been applied at the specified scope.</span></span>  
  
 <span data-ttu-id="2f805-115">`Last` 函數無法在群組篩選運算式中使用目前 (預設) 範圍以外的範圍。</span><span class="sxs-lookup"><span data-stu-id="2f805-115">The `Last` function cannot be used in group filter expressions with anything except the current (default) scope.</span></span>  
  
 <span data-ttu-id="2f805-116">您也可以在頁首中使用 `Last`，從頁面的 `ReportItems` 集合傳回最後一個值，以產生會顯示頁面上第一個及最後一個項目的字典樣式標題。</span><span class="sxs-lookup"><span data-stu-id="2f805-116">You can also use `Last` in a page header to return the last value from the `ReportItems` collection for a page in order to produce dictionary-style headings that display the first and last entries on a page.</span></span>  
  
 <span data-ttu-id="2f805-117">*scope* 的值必須是字串常數，而且不得為運算式。</span><span class="sxs-lookup"><span data-stu-id="2f805-117">The value of *scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="2f805-118">如果是未指定其他彙總的外部彙總， *scope* 必須參考目前的範圍或是包含的範圍。</span><span class="sxs-lookup"><span data-stu-id="2f805-118">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="2f805-119">如果是彙總的彙總，巢狀彙總可以指定子範圍。</span><span class="sxs-lookup"><span data-stu-id="2f805-119">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="2f805-120">*Expression* 可以包含巢狀彙總函式的呼叫，其中包含下列例外和條件：</span><span class="sxs-lookup"><span data-stu-id="2f805-120">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="2f805-121">巢狀彙總的*Scope* 必須與外部彙總的範圍相同或是由外部彙總的範圍所限制。</span><span class="sxs-lookup"><span data-stu-id="2f805-121">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="2f805-122">如果是運算式中的所有相異範圍，一個範圍必須與所有其他範圍之間具有子關聯性。</span><span class="sxs-lookup"><span data-stu-id="2f805-122">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="2f805-123">巢狀彙總的*Scope* 不得為資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f805-123">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="2f805-124">*運算式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函數。</span><span class="sxs-lookup"><span data-stu-id="2f805-124">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="2f805-125">*Expression* 不得包含指定 *recursive*的巢狀彙總。</span><span class="sxs-lookup"><span data-stu-id="2f805-125">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="2f805-126">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="2f805-126">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="2f805-127">如需遞迴彙總的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2f805-127">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f805-128">範例</span><span class="sxs-lookup"><span data-stu-id="2f805-128">Example</span></span>  
 <span data-ttu-id="2f805-129">下列程式碼範例會傳回資料區的 `Category` 群組中的最後一個產品號碼。</span><span class="sxs-lookup"><span data-stu-id="2f805-129">The following code example returns the last product number in the `Category` group of a data region.</span></span>  
  
```  
=Last(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f805-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f805-130">See Also</span></span>  
 <span data-ttu-id="2f805-131">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2f805-131">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2f805-132">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2f805-132">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2f805-133">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2f805-133">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2f805-134">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2f805-134">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
