---
title: Multilookup 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1fec079e-33b3-4e4d-92b3-6b4d06a49a77
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f2aff7a2a39e1a072cf4b05f0a04e12ced529af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595709"
---
# <a name="multilookup-function-report-builder-and-ssrs"></a><span data-ttu-id="43443-102">Multilookup 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="43443-102">Multilookup Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="43443-103">從包含名稱/值組的資料集傳回第一組符合指定之名稱集合的值。</span><span class="sxs-lookup"><span data-stu-id="43443-103">Returns the set of first-match values for the specified set of names from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="43443-104">語法</span><span class="sxs-lookup"><span data-stu-id="43443-104">Syntax</span></span>  
  
```  
  
Multilookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43443-105">參數</span><span class="sxs-lookup"><span data-stu-id="43443-105">Parameters</span></span>  
 <span data-ttu-id="43443-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="43443-106">*source_expression*</span></span>  
 <span data-ttu-id="43443-107">(`VariantArray`) - 在目前範圍中評估並指定要查閱之名稱或索引鍵集合的運算式。</span><span class="sxs-lookup"><span data-stu-id="43443-107">(`VariantArray`) An expression that is evaluated in the current scope and that specifies the set of names or keys to look up.</span></span> <span data-ttu-id="43443-108">例如，如果是多值參數 `=Parameters!IDs.value`。</span><span class="sxs-lookup"><span data-stu-id="43443-108">For example, for a multivalue parameter, `=Parameters!IDs.value`.</span></span>  
  
 <span data-ttu-id="43443-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="43443-109">*destination_expression*</span></span>  
 <span data-ttu-id="43443-110">(`Variant`) - 針對資料集中的每個資料列評估並指定要比對之名稱或索引鍵的運算式。</span><span class="sxs-lookup"><span data-stu-id="43443-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="43443-111">例如： `=Fields!ID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="43443-111">For example, `=Fields!ID.Value`.</span></span>  
  
 <span data-ttu-id="43443-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="43443-112">*result_expression*</span></span>  
 <span data-ttu-id="43443-113"> (`Variant`) 在 dataset 中針對資料列評估的運算式，其中*source_expression*  =  *destination_expression*，並指定要取得的值。</span><span class="sxs-lookup"><span data-stu-id="43443-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="43443-114">例如： `=Fields!Name.Value` 。</span><span class="sxs-lookup"><span data-stu-id="43443-114">For example, `=Fields!Name.Value`.</span></span>  
  
 <span data-ttu-id="43443-115">*資料集 (dataset)*</span><span class="sxs-lookup"><span data-stu-id="43443-115">*dataset*</span></span>  
 <span data-ttu-id="43443-116">指定報表中資料集名稱的常數。</span><span class="sxs-lookup"><span data-stu-id="43443-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="43443-117">例如，"Colors"。</span><span class="sxs-lookup"><span data-stu-id="43443-117">For example, "Colors".</span></span>  
  
## <a name="return"></a><span data-ttu-id="43443-118">傳回</span><span class="sxs-lookup"><span data-stu-id="43443-118">Return</span></span>  
 <span data-ttu-id="43443-119">傳回 `VariantArray` 或在沒有相符項目時傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="43443-119">Returns a `VariantArray`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43443-120">備註</span><span class="sxs-lookup"><span data-stu-id="43443-120">Remarks</span></span>  
 <span data-ttu-id="43443-121">使用 `Multilookup` 可從具有一對一關係的每一組名稱/值組的資料集內擷取一組值。</span><span class="sxs-lookup"><span data-stu-id="43443-121">Use `Multilookup` to retrieve a set of values from a dataset for name-value pairs where each pair has a 1-to-1 relationship.</span></span> <span data-ttu-id="43443-122">`MultiLookup` 等於針對一組名稱或索引鍵呼叫 `Lookup`。</span><span class="sxs-lookup"><span data-stu-id="43443-122">`MultiLookup` is the equivalent of calling `Lookup` for a set of names or keys.</span></span> <span data-ttu-id="43443-123">例如，如果是根據主索引鍵識別碼的多值參數，您可以在資料表中的文字方塊內使用運算式中的 `Multilookup`，從未繫結至參數或資料表的資料集擷取關聯的值。</span><span class="sxs-lookup"><span data-stu-id="43443-123">For example, for a multivalue parameter that is based on primary key identifiers, you can use `Multilookup` in an expression in a text box in a table to retrieve associated values from a dataset that is not bound to the parameter or to the table.</span></span>  
  
 <span data-ttu-id="43443-124">`Multilookup` 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="43443-124">`Multilookup` does the following:</span></span>  
  
-   <span data-ttu-id="43443-125">評估目前範圍中的來源運算式，並產生變數物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="43443-125">Evaluates the source expression in the current scope and generates an array of variant objects.</span></span>  
  
-   <span data-ttu-id="43443-126">如果是陣列中的每一個物件，則呼叫 [Lookup 函式 &#40;報表產生器及 SSRS&#41;](report-builder-functions-lookup-function.md)，並將結果新增傳回陣列。</span><span class="sxs-lookup"><span data-stu-id="43443-126">For each object in the array, calls [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md) and adds the result to the return array.</span></span>  
  
-   <span data-ttu-id="43443-127">傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="43443-127">Returns the set of results.</span></span>  
  
 <span data-ttu-id="43443-128">若要從具有一對一關聯性之名稱/值組的資料集中，擷取指定名稱的單一值，請使用 [Lookup 函式 &#40;報表產生器及 SSRS&#41;](report-builder-functions-lookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="43443-128">To retrieve a single value from a dataset with name-value pairs for a specified name where there is a 1-to-1 relationship, use [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span> <span data-ttu-id="43443-129">若要從具有一對多關聯性之名稱/值組的資料集中，擷取某個名稱的多個值，請使用 [LookupSet 函式 &#40;報表產生器及 SSRS&#41;](report-builder-functions-lookupset-function.md)。</span><span class="sxs-lookup"><span data-stu-id="43443-129">To retrieve multiple values from a dataset with name-value pairs for a name where there is a 1-to-many relationship, use [LookupSet Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookupset-function.md).</span></span>  
  
 <span data-ttu-id="43443-130">適用以下限制：</span><span class="sxs-lookup"><span data-stu-id="43443-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="43443-131">當套用所有篩選運算式之後，便會評估 `Multilookup`。</span><span class="sxs-lookup"><span data-stu-id="43443-131">`Multilookup` is evaluated after all filter expressions are applied</span></span>  
  
-   <span data-ttu-id="43443-132">只支援一層的查閱。</span><span class="sxs-lookup"><span data-stu-id="43443-132">Only one level of look-up is supported.</span></span> <span data-ttu-id="43443-133">來源、目的地或結果運算式不能包含查閱函數的參考。</span><span class="sxs-lookup"><span data-stu-id="43443-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="43443-134">來源和目的地運算式必須評估為相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="43443-134">Source and destination expressions must evaluate to the same data type.</span></span>  
  
-   <span data-ttu-id="43443-135">來源、目的地和結果運算式無法包含報表或群組變數的參考。</span><span class="sxs-lookup"><span data-stu-id="43443-135">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="43443-136">`Multilookup` 不能當做下列報表項目的運算式使用：</span><span class="sxs-lookup"><span data-stu-id="43443-136">`Multilookup` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="43443-137">資料來源的動態連接字串。</span><span class="sxs-lookup"><span data-stu-id="43443-137">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="43443-138">資料集中的導出欄位。</span><span class="sxs-lookup"><span data-stu-id="43443-138">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="43443-139">資料集中的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="43443-139">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="43443-140">資料集中的篩選。</span><span class="sxs-lookup"><span data-stu-id="43443-140">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="43443-141">報表參數。</span><span class="sxs-lookup"><span data-stu-id="43443-141">Report parameters.</span></span>  
  
    -   <span data-ttu-id="43443-142">Report.Language 屬性。</span><span class="sxs-lookup"><span data-stu-id="43443-142">The Report.Language property.</span></span>  
  
 <span data-ttu-id="43443-143">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="43443-143">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43443-144">範例</span><span class="sxs-lookup"><span data-stu-id="43443-144">Example</span></span>  
 <span data-ttu-id="43443-145">假設資料集 "Category" 包含 CategoryList 欄位，這個欄位是包含以逗號分隔之類別目錄識別碼的清單，例如 "2, 4, 2, 1"。</span><span class="sxs-lookup"><span data-stu-id="43443-145">Assume a dataset called "Category" contains the field CategoryList, which is a field that contains a comma-separated list of category identifers, for example, "2, 4, 2, 1".</span></span>  
  
 <span data-ttu-id="43443-146">CategoryNames 資料集包含類別目錄識別碼和類別目錄名稱，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="43443-146">The dataset CategoryNames contains the category identifier and category name, as shown in the following table.</span></span>  
  
|<span data-ttu-id="43443-147">ID</span><span class="sxs-lookup"><span data-stu-id="43443-147">ID</span></span>|<span data-ttu-id="43443-148">名稱</span><span class="sxs-lookup"><span data-stu-id="43443-148">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="43443-149">1</span><span class="sxs-lookup"><span data-stu-id="43443-149">1</span></span>|<span data-ttu-id="43443-150">Accessories</span><span class="sxs-lookup"><span data-stu-id="43443-150">Accessories</span></span>|  
|<span data-ttu-id="43443-151">2</span><span class="sxs-lookup"><span data-stu-id="43443-151">2</span></span>|<span data-ttu-id="43443-152">Bikes</span><span class="sxs-lookup"><span data-stu-id="43443-152">Bikes</span></span>|  
|<span data-ttu-id="43443-153">3</span><span class="sxs-lookup"><span data-stu-id="43443-153">3</span></span>|<span data-ttu-id="43443-154">Clothing</span><span class="sxs-lookup"><span data-stu-id="43443-154">Clothing</span></span>|  
|<span data-ttu-id="43443-155">4</span><span class="sxs-lookup"><span data-stu-id="43443-155">4</span></span>|<span data-ttu-id="43443-156">元件</span><span class="sxs-lookup"><span data-stu-id="43443-156">Components</span></span>|  
  
 <span data-ttu-id="43443-157">若要查閱對應到識別碼清單的名稱，請使用 `Multilookup`。</span><span class="sxs-lookup"><span data-stu-id="43443-157">To look up the names that correspond to the list of  identifiers, use `Multilookup`.</span></span> <span data-ttu-id="43443-158">您必須先將此清單分割成字串陣列、呼叫 `Multilookup` 來擷取類別目錄名稱，並將結果串連成一個字串。</span><span class="sxs-lookup"><span data-stu-id="43443-158">You must first split the list into a string array, call `Multilookup` to retrieve the category names, and concatenate the results into a string.</span></span>  
  
 <span data-ttu-id="43443-159">當下列運算式置於繫結至 Category 資料集之資料區中的文字方塊內時，將會顯示 "Bikes, Components, Bikes, Accessories"：</span><span class="sxs-lookup"><span data-stu-id="43443-159">The following expression, when placed in a text box in a data region bound to the Category dataset, displays "Bikes, Components, Bikes, Accessories":</span></span>  
  
```  
=Join(MultiLookup(Split(Fields!CategoryList.Value,","),  
   Fields!CategoryID.Value,Fields!CategoryName.Value,"Category")),  
   ", ")  
```  
  
## <a name="example"></a><span data-ttu-id="43443-160">範例</span><span class="sxs-lookup"><span data-stu-id="43443-160">Example</span></span>  
 <span data-ttu-id="43443-161">假設 ProductColors 資料集包含色彩識別碼欄位 ColorID 及色彩值欄位 Color，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="43443-161">Assume a dataset ProductColors contains a color identifier field ColorID and a color value field Color, as shown in the following table.</span></span>  
  
|<span data-ttu-id="43443-162">ColorID</span><span class="sxs-lookup"><span data-stu-id="43443-162">ColorID</span></span>|<span data-ttu-id="43443-163">Color</span><span class="sxs-lookup"><span data-stu-id="43443-163">Color</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="43443-164">1</span><span class="sxs-lookup"><span data-stu-id="43443-164">1</span></span>|<span data-ttu-id="43443-165">紅色</span><span class="sxs-lookup"><span data-stu-id="43443-165">Red</span></span>|  
|<span data-ttu-id="43443-166">2</span><span class="sxs-lookup"><span data-stu-id="43443-166">2</span></span>|<span data-ttu-id="43443-167">藍色</span><span class="sxs-lookup"><span data-stu-id="43443-167">Blue</span></span>|  
|<span data-ttu-id="43443-168">3</span><span class="sxs-lookup"><span data-stu-id="43443-168">3</span></span>|<span data-ttu-id="43443-169">綠色</span><span class="sxs-lookup"><span data-stu-id="43443-169">Green</span></span>|  
  
 <span data-ttu-id="43443-170">假設多值參數 *MyColors* 沒有繫結至其可用值的資料集。</span><span class="sxs-lookup"><span data-stu-id="43443-170">Assume the multivalue parameter *MyColors* is not bound to a dataset for its available values.</span></span> <span data-ttu-id="43443-171">此參數的預設值為 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="43443-171">The default values for the parameter are set to 2 and 3.</span></span> <span data-ttu-id="43443-172">當下列運算式置於資料表的文字方塊中時，會將此參數的多個選定值串連成一個以逗號分隔的清單，並顯示 "Blue, Green"。</span><span class="sxs-lookup"><span data-stu-id="43443-172">The following expression, when placed in a text box in a table, concatenates the multiple selected values for the parameter into a comma-separated list and displays "Blue, Green".</span></span>  
  
```  
=Join(MultiLookup(Parameters!MyColors.Value,Fields!ColorID.Value,Fields!Color.Value,"ProductColors"),", ")  
```  
  
## <a name="see-also"></a><span data-ttu-id="43443-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43443-173">See Also</span></span>  
 <span data-ttu-id="43443-174">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="43443-174">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="43443-175">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="43443-175">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="43443-176">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="43443-176">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="43443-177">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="43443-177">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
