---
title: 資料集 Fields 集合參考 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 006c6bd3-d776-4c20-9092-32e40688ac49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e4140c35f8035e3ac8fae37aefb9d7f2afcaecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599380"
---
# <a name="dataset-fields-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="18889-102">資料集欄位集合參考 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="18889-102">Dataset Fields Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="18889-103">報表中的每一個資料集都包含一個 Fields 集合。</span><span class="sxs-lookup"><span data-stu-id="18889-103">Each dataset in a report contains one Fields collection.</span></span> <span data-ttu-id="18889-104">Fields 集合是資料集查詢所指定的欄位加上您建立之任何其他導出欄位的集合。</span><span class="sxs-lookup"><span data-stu-id="18889-104">The Fields collection is the set of fields specified by the dataset query plus any additional calculated fields that you create.</span></span> <span data-ttu-id="18889-105">當您建立資料集之後，欄位集合會出現在 **[報表資料]** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="18889-105">After you create a dataset, the field collection appears in the **Report Data** pane.</span></span>  
  
 <span data-ttu-id="18889-106">運算式中的簡單欄位參考會在設計介面上顯示為簡單運算式。</span><span class="sxs-lookup"><span data-stu-id="18889-106">A simple field reference in an expression displays on the design surface as a simple expression.</span></span> <span data-ttu-id="18889-107">例如，當您將 `Sales` 欄位從 [報表資料] 窗格拖曳到設計介面上的資料表資料格時，就會顯示 `[Sales]` 。</span><span class="sxs-lookup"><span data-stu-id="18889-107">For example, when you drag the field `Sales` from the Report Data pane to a table cell on the design surface, `[Sales]` is displayed.</span></span> <span data-ttu-id="18889-108">這代表在文字方塊 Value 屬性上設定的基礎運算式 `=Fields!Sales.Value` 。</span><span class="sxs-lookup"><span data-stu-id="18889-108">This represents the underlying expression `=Fields!Sales.Value` that is set on the text box Value property.</span></span> <span data-ttu-id="18889-109">當報表執行時，報表處理器會評估此運算式，並將資料來源中的實際資料顯示在資料表資料格內的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="18889-109">When the report runs, the report processor evaluates this expression and displays the actual data from the data source in the text box in the table cell.</span></span> <span data-ttu-id="18889-110">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) 和[資料集 Fields 集合 &#40;報表產生器及 SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="18889-110">For more, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) and [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-the-field-collection-for-a-dataset"></a><span data-ttu-id="18889-111">顯示資料集的欄位集合</span><span class="sxs-lookup"><span data-stu-id="18889-111">Displaying the Field Collection for a Dataset</span></span>  
 <span data-ttu-id="18889-112">若要顯示欄位集合的個別值，請將每一個欄位拖曳到資料表詳細資料列，並執行報表。</span><span class="sxs-lookup"><span data-stu-id="18889-112">To display the individual values for a field collection, drag each field to a table detail row and run the report.</span></span> <span data-ttu-id="18889-113">資料表之詳細資料列或清單資料區中的參考會顯示資料集中每一個資料列的值。</span><span class="sxs-lookup"><span data-stu-id="18889-113">References from the detail row of a table or list data region display a value for each row in the dataset.</span></span>  
  
 <span data-ttu-id="18889-114">若要顯示欄位的摘要值，請將每一個數值欄位拖曳到矩陣的資料區。</span><span class="sxs-lookup"><span data-stu-id="18889-114">To display summarized values for a field, drag each numeric field to the data area of a matrix.</span></span> <span data-ttu-id="18889-115">總計資料列的預設彙總函式為 Sum，例如 `=Sum(Fields!Sales.Value)`。</span><span class="sxs-lookup"><span data-stu-id="18889-115">The default aggregate function for the total row is Sum, for example, `=Sum(Fields!Sales.Value)`.</span></span> <span data-ttu-id="18889-116">您可以變更預設函數，以便能夠計算不同的總計。</span><span class="sxs-lookup"><span data-stu-id="18889-116">You can change the default function in order to calculate different totals.</span></span> <span data-ttu-id="18889-117">如需詳細資訊，請參閱 [彙總函式參考 &#40;報表產生器和 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="18889-117">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
 <span data-ttu-id="18889-118">若要將欄位集合的摘要值直接顯示在設計介面上的文字方塊中 (不屬於資料區的一部分)，您必須將資料集名稱指定為彙總函式的範圍。</span><span class="sxs-lookup"><span data-stu-id="18889-118">To display summarized values for a field collection in a text box directly on the design surface (not part of a data region), you must specify the dataset name as a scope for the aggregate function.</span></span> <span data-ttu-id="18889-119">例如，如果是名為 `SalesData`的資料集，下列運算式會針對 `Sales`: `=Sum(Fields!Sales,"SalesData")`欄位指定所有值的總計。</span><span class="sxs-lookup"><span data-stu-id="18889-119">For example, for a dataset named `SalesData`, the following expression specifies the total of all values for the field `Sales`: `=Sum(Fields!Sales,"SalesData")`.</span></span>  
  
 <span data-ttu-id="18889-120">當您使用 [運算式]  對話方塊來定義簡單欄位參考時，可以在 [類別目錄] 窗格中選取 Fields 集合，並在 [欄位]  窗格中查看可用欄位的清單。</span><span class="sxs-lookup"><span data-stu-id="18889-120">When you use the **Expression** dialog box to define a simple field reference, you can select the Fields collection in the Category pane and see the list of available fields in the **Field** pane.</span></span> <span data-ttu-id="18889-121">每個欄位都有數個屬性，包括 Value 和 IsMissing。</span><span class="sxs-lookup"><span data-stu-id="18889-121">Each field has several properties, including Value and IsMissing.</span></span> <span data-ttu-id="18889-122">其餘的屬性會預先定義在擴充欄位屬性上，這些屬性可能可以提供給資料集使用 (視資料來源類型而定)。</span><span class="sxs-lookup"><span data-stu-id="18889-122">The remaining properties are predefined extended field properties that may be available to the dataset depending on the data source type.</span></span>  
  
### <a name="detecting-nulls-for-a-dataset-field"></a><span data-ttu-id="18889-123">偵測資料集欄位的 Null</span><span class="sxs-lookup"><span data-stu-id="18889-123">Detecting Nulls for a Dataset Field</span></span>  
 <span data-ttu-id="18889-124">若要偵測 Null 的欄位值 ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 `Nothing`)，您可以使用 `IsNothing` 函數。</span><span class="sxs-lookup"><span data-stu-id="18889-124">To detect a field value that is null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), you can use the function `IsNothing`.</span></span> <span data-ttu-id="18889-125">當下列運算式放置於資料表詳細資料列的文字方塊內時，運算式會測試 `MiddleName` 欄位，並在該值為 Null 時以 "No Middle Name" 文字替代，而當該值不是 Null 時則為欄位值本身：</span><span class="sxs-lookup"><span data-stu-id="18889-125">When placed in a text box in a table details row, the following expression tests the field `MiddleName` and substitutes the text "No Middle Name" when the value is null, and the field value itself when the value is not null:</span></span>  
  
 `=IIF(IsNothing(Fields!MiddleName.Value),"No Middle Name",Fields!MiddleName.Value)`  
  
### <a name="detecting-missing-fields-for-dynamic-queries-at-run-time"></a><span data-ttu-id="18889-126">在執行階段偵測動態查詢的遺漏欄位</span><span class="sxs-lookup"><span data-stu-id="18889-126">Detecting Missing Fields for Dynamic Queries at Run Time</span></span>  
 <span data-ttu-id="18889-127">Fields 集合內的項目預設會有兩個屬性：Value 和 IsMissing。</span><span class="sxs-lookup"><span data-stu-id="18889-127">By default, items in the Fields collection have two properties: Value and IsMissing.</span></span> <span data-ttu-id="18889-128">IsMissing p 屬性會指出在設計階段針對資料集所定義的欄位是否包含在執行階段擷取的欄位中。</span><span class="sxs-lookup"><span data-stu-id="18889-128">The IsMissing property indicates whether a field that is defined for a dataset at design time is contained in the fields retrieved at run time.</span></span> <span data-ttu-id="18889-129">例如，您的查詢可能會呼叫預存程式，其中的結果集與輸入參數不同，或者您的查詢可能是 `SELECT * FROM` *\<table>* 資料表定義變更的位置。</span><span class="sxs-lookup"><span data-stu-id="18889-129">For example, your query might call a stored procedure in which the result set varies with an input parameter, or your query might be `SELECT * FROM` *\<table>* where the table definition changed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18889-130">IsMissing 會偵測設計階段與執行階段之間對於任何資料來源類型的資料集結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="18889-130">IsMissing detects changes in the dataset schema between design time and run time for any type of data source.</span></span> <span data-ttu-id="18889-131">IsMissing 不能用來偵測多維度 cube 中的空白成員，而且與和的 MDX 查詢語言概念無關 `EMPTY` `NON EMPTY` 。</span><span class="sxs-lookup"><span data-stu-id="18889-131">IsMissing cannot be used to detect empty members in a multidimensional cube and is not related to the MDX query language concepts of `EMPTY` and `NON EMPTY`.</span></span>  
  
 <span data-ttu-id="18889-132">您可以在自訂程式碼中測試 IsMissing 屬性，以判斷結果集中是否有欄位存在。</span><span class="sxs-lookup"><span data-stu-id="18889-132">You can test the IsMissing property in custom code to determine if a field is present in the result set.</span></span> <span data-ttu-id="18889-133">您不能搭配 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數呼叫 (如 `IIF` 或 `SWITCH`) 使用運算式來測試欄位是否存在，因為 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 會評估此函數呼叫中的所有參數，而當評估遺漏項目的參考時，這樣的處理會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="18889-133">You cannot test for its presence using an expression with a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] function call such as `IIF` or `SWITCH`, because [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] evaluates all parameters in the call to the function, which results in an error when the reference to the missing is evaluated.</span></span>  
  
#### <a name="example-for-controlling-the-visibility-of-a-dynamic-column-for-a-missing-field"></a><span data-ttu-id="18889-134">控制遺漏欄位之動態資料行可見性的範例</span><span class="sxs-lookup"><span data-stu-id="18889-134">Example for Controlling the Visibility of a Dynamic Column for a Missing Field</span></span>  
 <span data-ttu-id="18889-135">若要設定一個運算式來控制在資料集中顯示欄位之資料行的可見性，您必須定義一個自訂程式碼函數，根據欄位是否遺漏來傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="18889-135">To set an expression that controls the visibility of a column that displays a field in a dataset, you must first define a custom code function that returns a Boolean value based on whether the field is missing.</span></span> <span data-ttu-id="18889-136">例如，如果此欄位遺漏，下列自訂程式碼函數會傳回 True，如果此欄位存在則傳回 False。</span><span class="sxs-lookup"><span data-stu-id="18889-136">For example, the following custom code function returns true if the field is missing and false if the field exists.</span></span>  
  
```  
Public Function IsFieldMissing(field as Field) as Boolean  
 If (field.IsMissing) Then  
 Return True  
  Else   
  Return False  
 End If  
End Function  
```  
  
 <span data-ttu-id="18889-137">若要使用此函數來控制資料行的可見性，請將此資料行的 Hidden 屬性設定為以下運算式：</span><span class="sxs-lookup"><span data-stu-id="18889-137">To use this function to control visibility of a column, set the Hidden property of the column to the following expression:</span></span>  
  
 `=Code.IsFieldMissing(Fields!FieldName)`  
  
 <span data-ttu-id="18889-138">當欄位不存在時，便會隱藏此資料行。</span><span class="sxs-lookup"><span data-stu-id="18889-138">The column is hidden when the field does not exist.</span></span>  
  
#### <a name="example-for-controlling-the-text-box-value-for-a-missing-field"></a><span data-ttu-id="18889-139">控制遺漏欄位之文字方塊值的範例</span><span class="sxs-lookup"><span data-stu-id="18889-139">Example for Controlling the Text Box Value for a Missing Field</span></span>  
 <span data-ttu-id="18889-140">若要使用您撰寫的文字來取代遺漏欄位的值，您必須撰寫自訂程式碼，使其在欄位遺漏時可傳回用來取代欄位值的文字。</span><span class="sxs-lookup"><span data-stu-id="18889-140">To substitute text that you write in place of the value of a missing field, you must write custom code that returns text you can use in place of a field value when the field is missing.</span></span> <span data-ttu-id="18889-141">例如，下列自訂程式碼函數會在欄位存在時傳回欄位的值，而當欄位不存在時，則傳回您指定為第二個參數的訊息：</span><span class="sxs-lookup"><span data-stu-id="18889-141">For example, the following custom code function returns the value of the field if the field exists, and the message that you specify as the second parameter if the field does not exist:</span></span>  
  
```  
Public Function IsFieldMissingThenString(field as Field, strMessage as String) as String  
 If (field.IsMissing) Then  
  Return strMessage  
 Else   
  Return field.Value  
  End If  
End Function  
```  
  
 <span data-ttu-id="18889-142">若要在文字方塊中使用這個函數，請將下列運算式加入到 Value 屬性：</span><span class="sxs-lookup"><span data-stu-id="18889-142">To use this function in a text box, add the following expression to the Value property:</span></span>  
  
 `=Code.IsFieldMissingThenString(Fields!FieldName,"Missing")`  
  
 <span data-ttu-id="18889-143">此文字方塊會顯示欄位值或是您指定的文字。</span><span class="sxs-lookup"><span data-stu-id="18889-143">The text box displays either the field value or the text that you specified.</span></span>  
  
### <a name="using-extended-field-properties"></a><span data-ttu-id="18889-144">使用擴充欄位屬性</span><span class="sxs-lookup"><span data-stu-id="18889-144">Using Extended Field Properties</span></span>  
 <span data-ttu-id="18889-145">擴充欄位屬性是資料處理延伸模組在欄位上所定義的其他屬性，此模組是由資料集的資料來源類型所決定。</span><span class="sxs-lookup"><span data-stu-id="18889-145">Extended field properties are additional properties defined on a field by the data processing extension, which is determined by the data source type for the dataset.</span></span> <span data-ttu-id="18889-146">擴充欄位屬性是預先定義的，或是資料來源類型所特有的。</span><span class="sxs-lookup"><span data-stu-id="18889-146">Extended field properties are predefined or specific to a data source type.</span></span> <span data-ttu-id="18889-147">如需詳細資訊，請參閱 [Analysis Services 資料庫的擴充欄位屬性 &#40;SSRS&#41;](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="18889-147">For more information, see [Extended Field Properties for an Analysis Services Database &#40;SSRS&#41;](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md).</span></span>  
  
 <span data-ttu-id="18889-148">如果您指定了該欄位不支援的屬性，則運算式會評估為 `null` ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="18889-148">If you specify a property that is not supported for that field, the expression evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="18889-149">如果資料提供者不支援擴充欄位屬性，或是執行查詢時找不到欄位，則當屬性類型為 `null` 和 `Nothing` 時，此屬性值會是 `String` ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中則為 `Object`)；當屬性類型為 `Integer` 時，此屬性值為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="18889-149">If a data provider does not support extended field properties, or if the field is not found when the query is executed, the value for the property is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) for properties of type `String` and `Object`, and zero (0) for properties of type `Integer`.</span></span> <span data-ttu-id="18889-150">資料處理延伸模組可藉由最佳化包含這個語法的查詢來利用預先定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="18889-150">A data processing extension may take advantage of predefined properties by optimizing queries that include this syntax.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18889-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18889-151">See Also</span></span>  
 <span data-ttu-id="18889-152">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="18889-152">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="18889-153">將資料加入報表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="18889-153">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](../report-data/report-datasets-ssrs.md)  
  
  
