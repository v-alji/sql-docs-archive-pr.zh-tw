---
title: Previous 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3891deec3f152cdf46da77a7f2d11d38387c5c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595705"
---
# <a name="previous-function-report-builder-and-ssrs"></a><span data-ttu-id="7f91b-102">Previous 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7f91b-102">Previous Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7f91b-103">傳回某個項目在指定之範圍內上一個執行個體的值或指定的彙總值。</span><span class="sxs-lookup"><span data-stu-id="7f91b-103">Returns the value or the specified aggregate value for the previous instance of an item within the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="7f91b-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f91b-104">Syntax</span></span>  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f91b-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f91b-105">Parameters</span></span>  
 <span data-ttu-id="7f91b-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="7f91b-106">*expression*</span></span>  
 <span data-ttu-id="7f91b-107">(`Variant` 或 `Binary`) 用來識別資料及擷取資料上一個值的運算式，例如，`Fields!Fieldname.Value` 或 `Sum(Fields!Fieldname.Value)`。</span><span class="sxs-lookup"><span data-stu-id="7f91b-107">(`Variant` or `Binary`) The expression to use to identify the data and for which to retrieve the previous value, for example, `Fields!Fieldname.Value` or `Sum(Fields!Fieldname.Value)`.</span></span>  
  
 <span data-ttu-id="7f91b-108">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="7f91b-108">*scope*</span></span>  
 <span data-ttu-id="7f91b-109">(`String`) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="7f91b-109">(`String`) Optional.</span></span> <span data-ttu-id="7f91b-110">群組或資料區域的名稱，或) 中的 null `Nothing` ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ，指定要從中取出*expression*所指定之先前值的範圍。</span><span class="sxs-lookup"><span data-stu-id="7f91b-110">The name of a group or data region, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the scope from which to retrieve the previous value specified by *expression*.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="7f91b-111">傳回類型</span><span class="sxs-lookup"><span data-stu-id="7f91b-111">Return Type</span></span>  
 <span data-ttu-id="7f91b-112">傳回 `Variant` 或 `Binary`。</span><span class="sxs-lookup"><span data-stu-id="7f91b-112">Returns a `Variant` or `Binary`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f91b-113">備註</span><span class="sxs-lookup"><span data-stu-id="7f91b-113">Remarks</span></span>  
 <span data-ttu-id="7f91b-114">`Previous` 函數會在套用過所有的排序和篩選之後，針對在指定範圍內評估的運算式傳回上一個值。</span><span class="sxs-lookup"><span data-stu-id="7f91b-114">The `Previous` function returns the previous value for the expression evaluated in the specified scope after all sorting and filtering have been applied.</span></span>  
  
 <span data-ttu-id="7f91b-115">如果*expression*未包含匯總， `Previous` 函數會預設為報表專案的目前範圍。</span><span class="sxs-lookup"><span data-stu-id="7f91b-115">If *expression* does not contain an aggregate, the `Previous` function defaults to the current scope for the report item.</span></span>  
  
 <span data-ttu-id="7f91b-116">在詳細資料群組中，請使用 `Previous` 來指定上一個詳細資料列執行個體中欄位參考的值。</span><span class="sxs-lookup"><span data-stu-id="7f91b-116">In a details group, use `Previous` to specify the value of a field reference in the previous instance of the detail row.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f91b-117">`Previous`函數只支援詳細資料群組中的欄位參考。</span><span class="sxs-lookup"><span data-stu-id="7f91b-117">The `Previous` function only supports field references in the details group.</span></span> <span data-ttu-id="7f91b-118">例如，在詳細資料群組的文字方塊中， `=Previous(Fields!Quantity.Value)` 會從上一個資料列傳回 `Quantity` 欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="7f91b-118">For example, in a text box in the details group, `=Previous(Fields!Quantity.Value)` returns the data for the field `Quantity` from the previous row.</span></span> <span data-ttu-id="7f91b-119">在第一個資料列中，這個運算式會傳回 Null (在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="7f91b-119">In the first row, this expression returns a null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span>  
  
 <span data-ttu-id="7f91b-120">如果*expression*包含使用預設範圍的彙總函式，則會 `Previous` 匯總在彙總函式呼叫所指定之範圍的先前實例內的資料。</span><span class="sxs-lookup"><span data-stu-id="7f91b-120">If *expression* contains an aggregate function that uses a default scope, `Previous` aggregates the data within the previous instance of the scope specified in the aggregate function call.</span></span>  
  
 <span data-ttu-id="7f91b-121">如果*expression*包含的彙總函式指定的範圍不是預設值，則函數的*範圍*參數 `Previous` 必須是彙總函式調用中所指定範圍的包含範圍。</span><span class="sxs-lookup"><span data-stu-id="7f91b-121">If *expression* contains an aggregate function that specifies a scope other than the default, the *scope* parameter for the `Previous` function must be a containing scope for the scope specified in the aggregate function call.</span></span>  
  
 <span data-ttu-id="7f91b-122">函數 `Level` 、 `InScope` `Aggregate` 和 `Previous` 不能用在*expression*參數中。</span><span class="sxs-lookup"><span data-stu-id="7f91b-122">The functions `Level`, `InScope`, `Aggregate` and `Previous` cannot be used in the *expression*parameter.</span></span> <span data-ttu-id="7f91b-123">不支援為任何彙總函式指定 *recursive* 參數。</span><span class="sxs-lookup"><span data-stu-id="7f91b-123">Specifying the *recursive* parameter for any aggregate function is not supported.</span></span>  
  
 <span data-ttu-id="7f91b-124">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="7f91b-124">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7f91b-125">範例</span><span class="sxs-lookup"><span data-stu-id="7f91b-125">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="7f91b-126">描述</span><span class="sxs-lookup"><span data-stu-id="7f91b-126">Description</span></span>  
 <span data-ttu-id="7f91b-127">下列程式碼範例如果置於資料區域的預設資料列中，會為上一個資料列的 `LineTotal` 欄位提供值。</span><span class="sxs-lookup"><span data-stu-id="7f91b-127">The following code example, when placed in the default data row of a data region, provides the value for the field `LineTotal` in the previous row.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7f91b-128">程式碼</span><span class="sxs-lookup"><span data-stu-id="7f91b-128">Code</span></span>  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a><span data-ttu-id="7f91b-129">描述</span><span class="sxs-lookup"><span data-stu-id="7f91b-129">Description</span></span>  
 <span data-ttu-id="7f91b-130">下列程式碼範例顯示的運算式會計算月中特定日的銷售總和，以及該日在去年度的上一個值。</span><span class="sxs-lookup"><span data-stu-id="7f91b-130">The following example shows an expression that calculates the sum of sales on a specific day of the month and the previous value for that day of the month in a previous year.</span></span> <span data-ttu-id="7f91b-131">運算式會加到屬於子群組 `GroupbyDay`的資料列中的資料格。</span><span class="sxs-lookup"><span data-stu-id="7f91b-131">The expression is added to a cell in a row that belongs to the child group `GroupbyDay`.</span></span> <span data-ttu-id="7f91b-132">該群組的父群組為 `GroupbyMonth`，這個群組的父群組又為 `GroupbyYear`。</span><span class="sxs-lookup"><span data-stu-id="7f91b-132">Its parent group is `GroupbyMonth`, which has a parent group `GroupbyYear`.</span></span> <span data-ttu-id="7f91b-133">運算式會顯示 GroupbyDay (預設範圍) 的結果，然後再顯示 `GroupbyYear` (GroupbyDay 父群組 `GroupbyMonth`的父代) 的結果。</span><span class="sxs-lookup"><span data-stu-id="7f91b-133">The expression displays the results for GroupbyDay (the default scope) and then for `GroupbyYear` (the parent of the parent group `GroupbyMonth`).</span></span>  
  
 <span data-ttu-id="7f91b-134">例如，如果資料區域具有名為 `Year`的父群組，而其子群組名為 `Month`，該子群組的子群組又名為 `Day` (3 個巢狀層級)。</span><span class="sxs-lookup"><span data-stu-id="7f91b-134">For example, for a data region with a parent group named `Year`, its child group named `Month`, and its child group named `Day` (3 nested levels).</span></span> <span data-ttu-id="7f91b-135">與群組 `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` 相關資料列中的運算式 `Day` 會針對去年度的同一日期和月份傳回銷售值。</span><span class="sxs-lookup"><span data-stu-id="7f91b-135">The expression `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` in a row associated with the group `Day` returns the sales value for the same day and month for the previous year.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7f91b-136">程式碼</span><span class="sxs-lookup"><span data-stu-id="7f91b-136">Code</span></span>  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f91b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f91b-137">See Also</span></span>  
 <span data-ttu-id="7f91b-138">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7f91b-138">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7f91b-139">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7f91b-139">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7f91b-140">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7f91b-140">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7f91b-141">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7f91b-141">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
