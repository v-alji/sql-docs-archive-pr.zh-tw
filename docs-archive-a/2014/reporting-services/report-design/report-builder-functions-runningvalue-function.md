---
title: RunningValue 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 168073a0409455041f4ebe3aa4c5dcfc8fa129a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595697"
---
# <a name="runningvalue-function-report-builder-and-ssrs"></a><span data-ttu-id="34272-102">RunningValue 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="34272-102">RunningValue Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="34272-103">傳回運算式指定的所有非 Null 數值的執行彙總 (在給定範圍中評估)。</span><span class="sxs-lookup"><span data-stu-id="34272-103">Returns a running aggregate of all non-null numeric values specified by the expression, evaluated for the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="34272-104">語法</span><span class="sxs-lookup"><span data-stu-id="34272-104">Syntax</span></span>  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34272-105">參數</span><span class="sxs-lookup"><span data-stu-id="34272-105">Parameters</span></span>  
 <span data-ttu-id="34272-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="34272-106">*expression*</span></span>  
 <span data-ttu-id="34272-107">要執行彙總的運算式，例如 `[Quantity]`。</span><span class="sxs-lookup"><span data-stu-id="34272-107">The expression on which to perform the aggregation, for example, `[Quantity]`.</span></span>  
  
 <span data-ttu-id="34272-108">*函數*</span><span class="sxs-lookup"><span data-stu-id="34272-108">*function*</span></span>  
 <span data-ttu-id="34272-109">(`Enum`) 運算式所要套用的彙總函式名稱，例如 `Sum`。</span><span class="sxs-lookup"><span data-stu-id="34272-109">(`Enum`) The name of the aggregate function to apply to the expression, for example, `Sum`.</span></span> <span data-ttu-id="34272-110">此函數可以是 `RunningValue`、`RowNumber` 或 `Aggregate`。</span><span class="sxs-lookup"><span data-stu-id="34272-110">This function cannot be `RunningValue`, `RowNumber`, or `Aggregate`.</span></span>  
  
 <span data-ttu-id="34272-111">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="34272-111">*scope*</span></span>  
 <span data-ttu-id="34272-112">(`String`) 字串常數，它是資料集、資料區域或群組的名稱，或為 Null (在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 `Nothing`)，可指定要在其中評估彙總的內容。</span><span class="sxs-lookup"><span data-stu-id="34272-112">(`String`) A string constant that is the name of a dataset, data region, or group, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the context in which to evaluate the aggregation.</span></span> <span data-ttu-id="34272-113">`Nothing` 指定最外層的內容，這通常為報表資料集。</span><span class="sxs-lookup"><span data-stu-id="34272-113">`Nothing` specifies the outermost context, usually the report dataset.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="34272-114">傳回類型</span><span class="sxs-lookup"><span data-stu-id="34272-114">Return Type</span></span>  
 <span data-ttu-id="34272-115">取決於 *function* 參數所指定的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="34272-115">Determined by the aggregate function that is specified in the *function* parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34272-116">備註</span><span class="sxs-lookup"><span data-stu-id="34272-116">Remarks</span></span>  
 <span data-ttu-id="34272-117">`RunningValue` 的值會針對範圍的每個新執行個體重設為 0。</span><span class="sxs-lookup"><span data-stu-id="34272-117">The value for `RunningValue` resets to 0 for each new instance of the scope.</span></span> <span data-ttu-id="34272-118">如果已指定群組，當群組運算式變更時，執行中的值也會重設。</span><span class="sxs-lookup"><span data-stu-id="34272-118">If a group is specified, the running value is reset when the group expression changes.</span></span> <span data-ttu-id="34272-119">如果已指定資料區域，就會為每個資料區域的新執行個體重設執行中的值。</span><span class="sxs-lookup"><span data-stu-id="34272-119">If a data region is specified, the running value is reset for each new instance of the data region.</span></span> <span data-ttu-id="34272-120">如果已指定資料集，則整個資料集不會重設執行中的值。</span><span class="sxs-lookup"><span data-stu-id="34272-120">If a dataset is specified, the running value is not reset throughout the entire dataset.</span></span>  
  
 <span data-ttu-id="34272-121">`RunningValue` 不能用於篩選或排序運算式。</span><span class="sxs-lookup"><span data-stu-id="34272-121">`RunningValue` cannot be used in a filter or sort expression.</span></span>  
  
 <span data-ttu-id="34272-122">評估執行值的資料集合必須具有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="34272-122">The set of data for which the running value is calculated must have the same data type.</span></span> <span data-ttu-id="34272-123">若要將具有多個數值資料類型的資料轉換成相同的資料類型，請使用 `CInt`、`CDbl` 或 `CDec` 等轉換函數。</span><span class="sxs-lookup"><span data-stu-id="34272-123">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="34272-124">如需詳細資訊，請參閱 [類型轉換函數](https://go.microsoft.com/fwlink/?LinkId=96142)。</span><span class="sxs-lookup"><span data-stu-id="34272-124">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="34272-125">*Scope* 不能是運算式。</span><span class="sxs-lookup"><span data-stu-id="34272-125">*Scope* cannot be an expression.</span></span>  
  
 <span data-ttu-id="34272-126">*Expression* 可以包含巢狀彙總函式的呼叫，其中包含下列例外和條件：</span><span class="sxs-lookup"><span data-stu-id="34272-126">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="34272-127">巢狀彙總的範圍必須與外部彙總的範圍相同或是由外部彙總的範圍所限制。</span><span class="sxs-lookup"><span data-stu-id="34272-127">Scope for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="34272-128">如果是運算式中的所有相異範圍，一個範圍必須與所有其他範圍之間具有子關聯性。</span><span class="sxs-lookup"><span data-stu-id="34272-128">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="34272-129">巢狀彙總的範圍不得為資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="34272-129">Scope for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="34272-130">*運算式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函數。</span><span class="sxs-lookup"><span data-stu-id="34272-130">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="34272-131">*Expression* 不得包含指定 *recursive*的巢狀彙總。</span><span class="sxs-lookup"><span data-stu-id="34272-131">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="34272-132">若要計算資料列數的執行值，請使用 `RowNumber`。</span><span class="sxs-lookup"><span data-stu-id="34272-132">To calculate the running value of the number of rows, use `RowNumber`.</span></span> <span data-ttu-id="34272-133">如需詳細資訊，請參閱 [RowNumber 函式 &#40;報表產生器及 SSRS&#41;](report-builder-functions-rownumber-function.md)。</span><span class="sxs-lookup"><span data-stu-id="34272-133">For more information, see [RowNumber Function &#40;Report Builder and SSRS&#41;](report-builder-functions-rownumber-function.md).</span></span>  
  
 <span data-ttu-id="34272-134">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="34272-134">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="34272-135">如需遞迴彙總的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="34272-135">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="34272-136">範例</span><span class="sxs-lookup"><span data-stu-id="34272-136">Examples</span></span>  
 <span data-ttu-id="34272-137">下列程式碼範例提供最外層範圍中 (也就是資料集) 名為 `Cost` 的欄位之執行總和。</span><span class="sxs-lookup"><span data-stu-id="34272-137">The following code example provides a running sum of the field named `Cost` in the outermost scope, which is the dataset.</span></span>  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 <span data-ttu-id="34272-138">下列程式碼範例提供名為 `Score` 的資料集中名為 `DataSet1`的欄位之累計總和。</span><span class="sxs-lookup"><span data-stu-id="34272-138">The following code example provides a running sum of the field named `Score` in the dataset named `DataSet1`.</span></span>  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 <span data-ttu-id="34272-139">下列程式碼範例提供最大範圍中名為 `Traffic Charges` 的欄位之累計總和。</span><span class="sxs-lookup"><span data-stu-id="34272-139">The following code example provides a running sum of the field named `Traffic Charges` in the outermost scope.</span></span>  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## <a name="see-also"></a><span data-ttu-id="34272-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34272-140">See Also</span></span>  
 <span data-ttu-id="34272-141">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34272-141">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="34272-142">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34272-142">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="34272-143">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34272-143">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="34272-144">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="34272-144">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
