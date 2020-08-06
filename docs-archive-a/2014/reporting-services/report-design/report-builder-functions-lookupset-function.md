---
title: LookupSet 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7685acfd-1c8d-420c-993c-903236fbe1ff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4edc7a17f2aa3813e8aa73e538594b5df3aeabc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595714"
---
# <a name="lookupset-function-report-builder-and-ssrs"></a><span data-ttu-id="c75e1-102">LookupSet 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c75e1-102">LookupSet Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c75e1-103">從包含名稱/值組的資料集傳回符合指定之名稱的值組。</span><span class="sxs-lookup"><span data-stu-id="c75e1-103">Returns the set of matching values for the specified name from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="c75e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c75e1-104">Syntax</span></span>  
  
```  
  
LookupSet(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c75e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="c75e1-105">Parameters</span></span>  
 <span data-ttu-id="c75e1-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="c75e1-106">*source_expression*</span></span>  
 <span data-ttu-id="c75e1-107">(`Variant`) - 在目前範圍中評估並指定要查閱之名稱或索引鍵的運算式。</span><span class="sxs-lookup"><span data-stu-id="c75e1-107">(`Variant`) An expression that is evaluated in the current scope and that specifies the name or key to look up.</span></span> <span data-ttu-id="c75e1-108">例如： `=Fields!ID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="c75e1-108">For example, `=Fields!ID.Value`.</span></span>  
  
 <span data-ttu-id="c75e1-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="c75e1-109">*destination_expression*</span></span>  
 <span data-ttu-id="c75e1-110">(`Variant`) - 針對資料集中的每個資料列評估並指定要比對之名稱或索引鍵的運算式。</span><span class="sxs-lookup"><span data-stu-id="c75e1-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="c75e1-111">例如： `=Fields!CustomerID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="c75e1-111">For example, `=Fields!CustomerID.Value`.</span></span>  
  
 <span data-ttu-id="c75e1-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="c75e1-112">*result_expression*</span></span>  
 <span data-ttu-id="c75e1-113"> (`Variant`) 在 dataset 中針對資料列評估的運算式，其中*source_expression*  =  *destination_expression*，並指定要取得的值。</span><span class="sxs-lookup"><span data-stu-id="c75e1-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="c75e1-114">例如： `=Fields!PhoneNumber.Value` 。</span><span class="sxs-lookup"><span data-stu-id="c75e1-114">For example, `=Fields!PhoneNumber.Value`.</span></span>  
  
 <span data-ttu-id="c75e1-115">*資料集 (dataset)*</span><span class="sxs-lookup"><span data-stu-id="c75e1-115">*dataset*</span></span>  
 <span data-ttu-id="c75e1-116">指定報表中資料集名稱的常數。</span><span class="sxs-lookup"><span data-stu-id="c75e1-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="c75e1-117">例如，"ContactInformation"。</span><span class="sxs-lookup"><span data-stu-id="c75e1-117">For example, "ContactInformation".</span></span>  
  
## <a name="return"></a><span data-ttu-id="c75e1-118">傳回</span><span class="sxs-lookup"><span data-stu-id="c75e1-118">Return</span></span>  
 <span data-ttu-id="c75e1-119">傳回 `VariantArray` 或在沒有相符項目時傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="c75e1-119">Returns a `VariantArray`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c75e1-120">備註</span><span class="sxs-lookup"><span data-stu-id="c75e1-120">Remarks</span></span>  
 <span data-ttu-id="c75e1-121">使用 `LookupSet` 可從具有一對多關係之名稱/值組的指定資料集中擷取一組值。</span><span class="sxs-lookup"><span data-stu-id="c75e1-121">Use `LookupSet` to retrieve a set of values from the specified dataset for a name/value pair where there is a 1-to-many relationship.</span></span> <span data-ttu-id="c75e1-122">例如，如果是資料表中的客戶識別碼，您可以使用 `LookupSet` 從未繫結至資料區的資料集中，擷取該客戶的所有相關電話號碼。</span><span class="sxs-lookup"><span data-stu-id="c75e1-122">For example, for a customer identifier in a table, you can use `LookupSet` to retrieve all the associated phone numbers for that customer from a dataset that is not bound to the data region.</span></span>  
  
 <span data-ttu-id="c75e1-123">`LookupSet` 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c75e1-123">`LookupSet` does the following:</span></span>  
  
-   <span data-ttu-id="c75e1-124">評估目前範圍中的來源運算式。</span><span class="sxs-lookup"><span data-stu-id="c75e1-124">Evaluates the source expression in the current scope.</span></span>  
  
-   <span data-ttu-id="c75e1-125">根據指定之資料集的定序，在已經套用篩選之後針對指定之資料集的每一個資料列評估目的地運算式。</span><span class="sxs-lookup"><span data-stu-id="c75e1-125">Evaluates the destination expression for each row of the specified dataset after filters have been applied, based on the collation of the specified dataset.</span></span>  
  
-   <span data-ttu-id="c75e1-126">在每一個符合來源運算式和目的地運算式的項目上，針對資料集中的該資料列評估結果運算式。</span><span class="sxs-lookup"><span data-stu-id="c75e1-126">For each match of source expression and destination expression, evaluates the result expression for that row in the dataset.</span></span>  
  
-   <span data-ttu-id="c75e1-127">傳回結果運算式值的集合。</span><span class="sxs-lookup"><span data-stu-id="c75e1-127">Returns the set of result expression values.</span></span>  
  
 <span data-ttu-id="c75e1-128">若要從具有一對一關聯性之名稱/值組的資料集中，擷取指定名稱的單一值，請使用 [Lookup 函式 &#40;報表產生器及 SSRS&#41;](report-builder-functions-lookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="c75e1-128">To retrieve a single value from a dataset with name/value pairs for a specified name where there is a 1-to-1 relationship, use [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span> <span data-ttu-id="c75e1-129">若要呼叫 `Lookup` 一組值，請使用[Multilookup 函數 &#40;報表產生器和 SSRS&#41;](report-builder-functions-multilookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="c75e1-129">To call `Lookup` for a set of values, use [Multilookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-multilookup-function.md).</span></span>  
  
 <span data-ttu-id="c75e1-130">適用以下限制：</span><span class="sxs-lookup"><span data-stu-id="c75e1-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="c75e1-131">當套用所有篩選運算式之後，便會評估 `LookupSet`。</span><span class="sxs-lookup"><span data-stu-id="c75e1-131">`LookupSet` is evaluated after all filter expressions are applied.</span></span>  
  
-   <span data-ttu-id="c75e1-132">只支援一層的查閱。</span><span class="sxs-lookup"><span data-stu-id="c75e1-132">Only one level of lookup is supported.</span></span> <span data-ttu-id="c75e1-133">來源、目的地或結果運算式不能包含查閱函數的參考。</span><span class="sxs-lookup"><span data-stu-id="c75e1-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="c75e1-134">來源和目的地運算式必須評估為相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c75e1-134">Source and destination expressions must evaluate to the same data type.</span></span>  
  
-   <span data-ttu-id="c75e1-135">來源、目的地和結果運算式無法包含報表或群組變數的參考。</span><span class="sxs-lookup"><span data-stu-id="c75e1-135">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="c75e1-136">`LookupSet` 不能當做下列報表項目的運算式使用：</span><span class="sxs-lookup"><span data-stu-id="c75e1-136">`LookupSet` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="c75e1-137">資料來源的動態連接字串。</span><span class="sxs-lookup"><span data-stu-id="c75e1-137">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="c75e1-138">資料集中的導出欄位。</span><span class="sxs-lookup"><span data-stu-id="c75e1-138">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="c75e1-139">資料集中的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="c75e1-139">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="c75e1-140">資料集中的篩選。</span><span class="sxs-lookup"><span data-stu-id="c75e1-140">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="c75e1-141">報表參數。</span><span class="sxs-lookup"><span data-stu-id="c75e1-141">Report parameters.</span></span>  
  
    -   <span data-ttu-id="c75e1-142">Report.Language 屬性。</span><span class="sxs-lookup"><span data-stu-id="c75e1-142">The Report.Language property.</span></span>  
  
 <span data-ttu-id="c75e1-143">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="c75e1-143">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c75e1-144">範例</span><span class="sxs-lookup"><span data-stu-id="c75e1-144">Example</span></span>  
 <span data-ttu-id="c75e1-145">在下列範例中，假設資料表繫結至一個資料集，此資料集包含銷售領域識別碼 TerritoryGroupID。</span><span class="sxs-lookup"><span data-stu-id="c75e1-145">In the following example, assume the table is bound to a dataset that includes a sales territory identifier TerritoryGroupID.</span></span> <span data-ttu-id="c75e1-146">另一個資料集 "Stores" 包含領域中所有商店的清單，並包含領域識別碼 ID 和 StoreName 商店的名稱。</span><span class="sxs-lookup"><span data-stu-id="c75e1-146">A separate dataset called "Stores" contains the list of all stores in a territory and includes the territory identifier ID and the name of the store StoreName.</span></span>  
  
 <span data-ttu-id="c75e1-147">在下列運算式中，`LookupSet` 會比較 "Stores" 資料集中每一個資料列的 TerritoryGroupID 值與 ID。</span><span class="sxs-lookup"><span data-stu-id="c75e1-147">In the following expression, `LookupSet` compares the value TerritoryGroupID to ID for each row in the dataset called "Stores".</span></span> <span data-ttu-id="c75e1-148">在每次比對中，該資料列的 StoreName 欄位值都會加入至結果集。</span><span class="sxs-lookup"><span data-stu-id="c75e1-148">For each match, the value of the StoreName field for that row is added to the result set.</span></span>  
  
```  
=LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores")  
```  
  
## <a name="example"></a><span data-ttu-id="c75e1-149">範例</span><span class="sxs-lookup"><span data-stu-id="c75e1-149">Example</span></span>  
 <span data-ttu-id="c75e1-150">因為 `LookupSet` 會傳回物件的集合，所以您無法直接在文字方塊中顯示結果運算式。</span><span class="sxs-lookup"><span data-stu-id="c75e1-150">Because `LookupSet` returns a collection of objects, you cannot display the result expression directly in a text box.</span></span> <span data-ttu-id="c75e1-151">您可以將集合中每一個物件的值串連起來當做一個字串。</span><span class="sxs-lookup"><span data-stu-id="c75e1-151">You can concatenate the value of each object in the collection as a string.</span></span>  
  
 <span data-ttu-id="c75e1-152">使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數 `Join` 從一組物件建立分隔的字串。</span><span class="sxs-lookup"><span data-stu-id="c75e1-152">Use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] function `Join` create a delimited string from a set of objects.</span></span> <span data-ttu-id="c75e1-153">使用逗號當做分隔符號，在單一行中結合這些物件。</span><span class="sxs-lookup"><span data-stu-id="c75e1-153">Use a comma as a separator to combine the objects in a single line.</span></span> <span data-ttu-id="c75e1-154">在某些轉譯器中，您可能會使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 換行字元 (`vbCrLF`) 當作分隔符號，在新行中列出每一個值。</span><span class="sxs-lookup"><span data-stu-id="c75e1-154">In some renderers, you might use a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] line feed (`vbCrLF`) as a separator to list each value on a new line.</span></span>  
  
 <span data-ttu-id="c75e1-155">當下列運算式當做文字方塊的 Value 屬性使用時，會使用 `Join` 來建立清單。</span><span class="sxs-lookup"><span data-stu-id="c75e1-155">The following expression, when it is used as the Value property for a text box, uses `Join` to create a list.</span></span>  
  
```  
=Join(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"),",")  
```  
  
## <a name="example"></a><span data-ttu-id="c75e1-156">範例</span><span class="sxs-lookup"><span data-stu-id="c75e1-156">Example</span></span>  
 <span data-ttu-id="c75e1-157">如果是只轉譯幾次的文字方塊，您可能會選擇加入自訂程式碼產生 HTML，以便在文字方塊中顯示值。</span><span class="sxs-lookup"><span data-stu-id="c75e1-157">For text boxes that only render a few times, you might choose to add custom code to generate HTML to display values in a text box.</span></span> <span data-ttu-id="c75e1-158">文字方塊中的 HTML 需要額外的處理，所以如果是轉譯好幾千次的文字方塊，這並不是一個好的選擇。</span><span class="sxs-lookup"><span data-stu-id="c75e1-158">HTML in a text box requires extra processing, so this would not be a good choice for a text box that is rendered thousands of times.</span></span>  
  
 <span data-ttu-id="c75e1-159">將下列 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數複製到報表定義中的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="c75e1-159">Copy the following [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to a Code block in a report definition.</span></span> <span data-ttu-id="c75e1-160">**MakeList** 會採用 *result_expression* 中所傳回的物件陣列，並使用 HTML 標記建立未排序的清單。</span><span class="sxs-lookup"><span data-stu-id="c75e1-160">**MakeList** takes the object array that is returned in *result_expression* and builds an unordered list by using HTML tags.</span></span> <span data-ttu-id="c75e1-161">**Length** 會傳回此物件陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="c75e1-161">**Length** returns the number of items in the object array.</span></span>  
  
```  
Function MakeList(ByVal items As Object()) As String  
   If items Is Nothing Then  
      Return Nothing  
   End If  
  
   Dim builder As System.Text.StringBuilder =   
      New System.Text.StringBuilder()  
   builder.Append("<ul>")  
  
   For Each item As Object In items  
      builder.Append("<li>")  
      builder.Append(item)  
   Next  
   builder.Append("</ul>")  
  
   Return builder.ToString()  
End Function  
  
Function Length(ByVal items as Object()) as Integer  
   If items is Nothing Then  
      Return 0  
   End If  
   Return items.Length  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="c75e1-162">範例</span><span class="sxs-lookup"><span data-stu-id="c75e1-162">Example</span></span>  
 <span data-ttu-id="c75e1-163">若要產生 HTML，您必須呼叫此函數。</span><span class="sxs-lookup"><span data-stu-id="c75e1-163">To generate the HTML, you must call the function.</span></span> <span data-ttu-id="c75e1-164">將下列運算式貼到文字方塊的 Value 屬性中，並將文字的標記類型設定為 HTML。</span><span class="sxs-lookup"><span data-stu-id="c75e1-164">Paste the following expression in the Value property for the text box and set the markup type for text to HTML.</span></span> <span data-ttu-id="c75e1-165">如需詳細資訊，請參閱[將 HTML 新增至報表 &#40;報表產生器及 SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c75e1-165">For more information, see [Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
```  
=Code.MakeList(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"))  
```  
  
## <a name="see-also"></a><span data-ttu-id="c75e1-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c75e1-166">See Also</span></span>  
 <span data-ttu-id="c75e1-167">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c75e1-167">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c75e1-168">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c75e1-168">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c75e1-169">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c75e1-169">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c75e1-170">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c75e1-170">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
