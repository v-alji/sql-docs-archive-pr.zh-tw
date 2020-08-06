---
title: Lookup 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e60e5bab-b286-4897-9685-9ff12703517d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 053fefff51e4b4e338e262664bd7570280c92540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595711"
---
# <a name="lookup-function-report-builder-and-ssrs"></a><span data-ttu-id="1bae5-102">Lookup 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1bae5-102">Lookup Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1bae5-103">從包含名稱/值組的資料集傳回第一個符合指定之名稱的值。</span><span class="sxs-lookup"><span data-stu-id="1bae5-103">Returns the first matching value for the specified name from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="1bae5-104">語法</span><span class="sxs-lookup"><span data-stu-id="1bae5-104">Syntax</span></span>  
  
```  
  
Lookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bae5-105">參數</span><span class="sxs-lookup"><span data-stu-id="1bae5-105">Parameters</span></span>  
 <span data-ttu-id="1bae5-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="1bae5-106">*source_expression*</span></span>  
 <span data-ttu-id="1bae5-107">(`Variant`) - 在目前範圍中評估並指定要查閱之名稱或索引鍵的運算式。</span><span class="sxs-lookup"><span data-stu-id="1bae5-107">(`Variant`) An expression that is evaluated in the current scope and that specifies the name or key to look up.</span></span> <span data-ttu-id="1bae5-108">例如： `=Fields!ProdID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="1bae5-108">For example, `=Fields!ProdID.Value`.</span></span>  
  
 <span data-ttu-id="1bae5-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="1bae5-109">*destination_expression*</span></span>  
 <span data-ttu-id="1bae5-110">(`Variant`) - 針對資料集中的每個資料列評估並指定要比對之名稱或索引鍵的運算式。</span><span class="sxs-lookup"><span data-stu-id="1bae5-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="1bae5-111">例如： `=Fields!ProductID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="1bae5-111">For example, `=Fields!ProductID.Value`.</span></span>  
  
 <span data-ttu-id="1bae5-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="1bae5-112">*result_expression*</span></span>  
 <span data-ttu-id="1bae5-113"> (`Variant`) 在 dataset 中針對資料列評估的運算式，其中*source_expression*  =  *destination_expression*，並指定要取得的值。</span><span class="sxs-lookup"><span data-stu-id="1bae5-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="1bae5-114">例如： `=Fields!ProductName.Value` 。</span><span class="sxs-lookup"><span data-stu-id="1bae5-114">For example, `=Fields!ProductName.Value`.</span></span>  
  
 <span data-ttu-id="1bae5-115">*資料集 (dataset)*</span><span class="sxs-lookup"><span data-stu-id="1bae5-115">*dataset*</span></span>  
 <span data-ttu-id="1bae5-116">指定報表中資料集名稱的常數。</span><span class="sxs-lookup"><span data-stu-id="1bae5-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="1bae5-117">例如，"Products"。</span><span class="sxs-lookup"><span data-stu-id="1bae5-117">For example, "Products".</span></span>  
  
## <a name="return"></a><span data-ttu-id="1bae5-118">傳回</span><span class="sxs-lookup"><span data-stu-id="1bae5-118">Return</span></span>  
 <span data-ttu-id="1bae5-119">傳回 `Variant` 或在沒有相符項目時傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="1bae5-119">Returns a `Variant`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bae5-120">備註</span><span class="sxs-lookup"><span data-stu-id="1bae5-120">Remarks</span></span>  
 <span data-ttu-id="1bae5-121">使用 `Lookup` 可從具有一對一關係之名稱/值組的指定資料集中擷取值。</span><span class="sxs-lookup"><span data-stu-id="1bae5-121">Use `Lookup` to retrieve the value from the specified dataset for a name/value pair where there is a 1-to-1 relationship.</span></span> <span data-ttu-id="1bae5-122">例如，如果是資料表中的識別碼欄位，您可以使用 `Lookup` 從未繫結至資料區的資料集中，擷取對應的名稱欄位。</span><span class="sxs-lookup"><span data-stu-id="1bae5-122">For example, for an ID field in a table, you can use `Lookup` to retrieve the corresponding Name field from a dataset that is not bound to the data region.</span></span>  
  
 <span data-ttu-id="1bae5-123">`Lookup` 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1bae5-123">`Lookup` does the following:</span></span>  
  
-   <span data-ttu-id="1bae5-124">評估目前範圍中的來源運算式。</span><span class="sxs-lookup"><span data-stu-id="1bae5-124">Evaluates the source expression in the current scope.</span></span>  
  
-   <span data-ttu-id="1bae5-125">根據指定之資料集的定序，在已經套用篩選之後針對指定之資料集的每一個資料列評估目的地運算式。</span><span class="sxs-lookup"><span data-stu-id="1bae5-125">Evaluates the destination expression for each row of the specified dataset after filters have been applied, based on the collation of the specified dataset.</span></span>  
  
-   <span data-ttu-id="1bae5-126">在第一個符合來源運算式和目的地運算式的項目上，針對資料集中的該資料列評估結果運算式。</span><span class="sxs-lookup"><span data-stu-id="1bae5-126">On the first match of source expression and destination expression, evaluates the result expression for that row in the dataset.</span></span>  
  
-   <span data-ttu-id="1bae5-127">傳回結果運算式值。</span><span class="sxs-lookup"><span data-stu-id="1bae5-127">Returns the result expression value.</span></span>  
  
 <span data-ttu-id="1bae5-128">若要針對具有一對多關係的單一名稱或索引鍵欄位擷取多個值，請使用 [LookupSet 函式 &#40;報表產生器及 SSRS&#41;](report-builder-functions-lookupset-function.md)。</span><span class="sxs-lookup"><span data-stu-id="1bae5-128">To retrieve multiple values for a single name or key field where there is a 1-to-many relationship, use [LookupSet Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookupset-function.md).</span></span> <span data-ttu-id="1bae5-129">若要呼叫 `Lookup` 一組值，請使用[Multilookup 函數 &#40;報表產生器和 SSRS&#41;](report-builder-functions-lookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="1bae5-129">To call `Lookup` for a set of values, use [Multilookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span>  
  
 <span data-ttu-id="1bae5-130">適用以下限制：</span><span class="sxs-lookup"><span data-stu-id="1bae5-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="1bae5-131">當套用所有篩選運算式之後，便會評估 `Lookup`。</span><span class="sxs-lookup"><span data-stu-id="1bae5-131">`Lookup` is evaluated after all filter expressions are applied.</span></span>  
  
-   <span data-ttu-id="1bae5-132">只支援一層的查閱。</span><span class="sxs-lookup"><span data-stu-id="1bae5-132">Only one level of lookup is supported.</span></span> <span data-ttu-id="1bae5-133">來源、目的地或結果運算式不能包含查閱函數的參考。</span><span class="sxs-lookup"><span data-stu-id="1bae5-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="1bae5-134">來源和目的地運算式必須評估為相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1bae5-134">Source and destination expressions must evaluate to the same data type.</span></span> <span data-ttu-id="1bae5-135">傳回類型與評估之結果運算式的資料類型相同。</span><span class="sxs-lookup"><span data-stu-id="1bae5-135">The return type is the same as the data type of the evaluated result expression.</span></span>  
  
-   <span data-ttu-id="1bae5-136">來源、目的地和結果運算式無法包含報表或群組變數的參考。</span><span class="sxs-lookup"><span data-stu-id="1bae5-136">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="1bae5-137">`Lookup` 不能當做下列報表項目的運算式使用：</span><span class="sxs-lookup"><span data-stu-id="1bae5-137">`Lookup` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="1bae5-138">資料來源的動態連接字串。</span><span class="sxs-lookup"><span data-stu-id="1bae5-138">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="1bae5-139">資料集中的導出欄位。</span><span class="sxs-lookup"><span data-stu-id="1bae5-139">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="1bae5-140">資料集中的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="1bae5-140">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="1bae5-141">資料集中的篩選。</span><span class="sxs-lookup"><span data-stu-id="1bae5-141">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="1bae5-142">報表參數。</span><span class="sxs-lookup"><span data-stu-id="1bae5-142">Report parameters.</span></span>  
  
    -   <span data-ttu-id="1bae5-143">Report.Language 屬性。</span><span class="sxs-lookup"><span data-stu-id="1bae5-143">The Report.Language property.</span></span>  
  
 <span data-ttu-id="1bae5-144">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="1bae5-144">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bae5-145">範例</span><span class="sxs-lookup"><span data-stu-id="1bae5-145">Example</span></span>  
 <span data-ttu-id="1bae5-146">在下列範例中，假設資料表繫結至一個資料集，此資料集包含產品識別碼 ProductID 的欄位。</span><span class="sxs-lookup"><span data-stu-id="1bae5-146">In the following example, assume that a table is bound to a dataset that includes a field for the product identifier ProductID.</span></span> <span data-ttu-id="1bae5-147">另一個資料集 "Product" 包含對應的產品識別碼 ID 和產品名稱 Name。</span><span class="sxs-lookup"><span data-stu-id="1bae5-147">A separate dataset called "Product" contains the corresponding product identifier ID and the product name Name.</span></span>  
  
 <span data-ttu-id="1bae5-148">在下列運算式中，`Lookup` 會比較 "Product" 資料集之每一個資料列中 ProductID 與 ID 的值，而且當找到符合的項目時，就會傳回該資料列的 Name 欄位值。</span><span class="sxs-lookup"><span data-stu-id="1bae5-148">In the following expression, `Lookup` compares the value of ProductID to ID in each row of the dataset called "Product" and, when a match is found, returns the value of the Name field for that row.</span></span>  
  
```  
=Lookup(Fields!ProductID.Value, Fields!ID.Value, Fields!Name.Value, "Product")  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bae5-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bae5-149">See Also</span></span>  
 <span data-ttu-id="1bae5-150">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bae5-150">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1bae5-151">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bae5-151">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1bae5-152">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bae5-152">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1bae5-153">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1bae5-153">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
