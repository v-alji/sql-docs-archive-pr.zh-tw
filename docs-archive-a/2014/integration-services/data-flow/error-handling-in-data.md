---
title: 處理資料中的錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data conversion errors [Integration Services]
- errors [Integration Services], data flow components
- lookups [Integration Services]
- errors [Integration Services]
- errors [Integration Services], data flow outputs
- error outputs [Integration Services]
- data flow [Integration Services], errors
- expressions [Integration Services], errors
ms.assetid: c61667b4-25cb-4d45-a52f-a733e32863f4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 442ecc68fc352d50955af9302fbcedf77ba36338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709817"
---
# <a name="error-handling-in-data"></a><span data-ttu-id="34073-102">處理資料中的錯誤</span><span class="sxs-lookup"><span data-stu-id="34073-102">Error Handling in Data</span></span>
  <span data-ttu-id="34073-103">當資料流程元件將轉換套用至資料行資料、從來源擷取資料或將資料載入目的地時，可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-103">When a data flow component applies a transformation to column data, extracts data from sources, or loads data into destinations, errors can occur.</span></span> <span data-ttu-id="34073-104">錯誤通常是因為非預期的資料值所產生的。</span><span class="sxs-lookup"><span data-stu-id="34073-104">Errors frequently occur because of unexpected data values.</span></span> <span data-ttu-id="34073-105">例如，資料轉換失敗的原因是資料行包含字串而非數字；向資料庫資料行插入失敗的原因是資料為日期，而資料行是數值資料類型；運算式評估失敗的原因是資料行值為零，導致數學運算無效。</span><span class="sxs-lookup"><span data-stu-id="34073-105">For example, a data conversion fails because a column contains a string instead of a number, an insertion into a database column fails because the data is a date and the column has a numeric data type, or an expression fails to evaluate because a column value is zero, resulting in a mathematical operation that is not valid.</span></span>  
  
 <span data-ttu-id="34073-106">通常，錯誤可歸類為下列類別之一：</span><span class="sxs-lookup"><span data-stu-id="34073-106">Errors typically fall into one the following categories:</span></span>  
  
-   <span data-ttu-id="34073-107">資料轉換錯誤，當轉換導致遺失有效數位、遺失無效位數以及字串截斷時，會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-107">Data conversion errors, which occur if a conversion results in loss of significant digits, the loss of insignificant digits, and the truncation of strings.</span></span> <span data-ttu-id="34073-108">如果所要求的轉換不受支援，也會發生資料轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-108">Data conversion errors also occur if the requested conversion is not supported.</span></span>  
  
-   <span data-ttu-id="34073-109">運算式評估錯誤，如果在執行階段評估的運算式執行無效作業，或者，由於遺失或錯誤的資料值而語法不正確，則會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-109">Expression evaluation errors, which occur if expressions that are evaluated at run time perform invalid operations or become syntactically incorrect because of missing or incorrect data values.</span></span>  
  
-   <span data-ttu-id="34073-110">查閱錯誤，如果查閱作業無法在查閱資料表中找到相符部分，則會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-110">Lookup errors, which occur if a lookup operation fails to locate a match in the lookup table.</span></span>  
  
 <span data-ttu-id="34073-111">許多資料流程元件都支援錯誤輸出，這可讓您控制元件處理內送資料與外送資料中資料列層級錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="34073-111">Many data flow components support error outputs, which let you control how the component handles row-level errors in both incoming and outgoing data.</span></span> <span data-ttu-id="34073-112">您可以藉由設定輸入或輸出中個別資料行的選項，來指定發生截斷或錯誤時元件的行為方式。</span><span class="sxs-lookup"><span data-stu-id="34073-112">You specify how the component behaves when truncation or an error occurs by setting options on individual columns in the input or output.</span></span> <span data-ttu-id="34073-113">例如，您可以指定，如果客戶名稱資料被截斷則元件應失敗，但忽略包含不重要資料之其他資料行的錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-113">For example, you can specify that the component should fail if customer name data is truncated, but ignore errors on another column that contains less important data.</span></span>  
  
 <span data-ttu-id="34073-114">錯誤輸出可以連接到其他轉換的輸入，或載入無錯誤輸出以外的其他目的地。</span><span class="sxs-lookup"><span data-stu-id="34073-114">The error output can be connected to the input of another transformation or loaded into a different destination than the non-error output.</span></span> <span data-ttu-id="34073-115">例如，錯誤輸出可以連接到為空白資料行提供字串之「衍生的資料行」轉換。</span><span class="sxs-lookup"><span data-stu-id="34073-115">For example, the error output can be a connected to a Derived Column transformation that provides a string for a column that is blank.</span></span>  
  
 <span data-ttu-id="34073-116">下圖顯示包含錯誤輸出的簡單資料流程。</span><span class="sxs-lookup"><span data-stu-id="34073-116">The following diagram shows a simple data flow including an error output.</span></span>  
  
 <span data-ttu-id="34073-117">![具有錯誤輸出的資料流程](../media/mw-dts-11.gif "具有錯誤輸出的資料流程")</span><span class="sxs-lookup"><span data-stu-id="34073-117">![Data flow with error output](../media/mw-dts-11.gif "Data flow with error output")</span></span>  
  
 <span data-ttu-id="34073-118">除資料行之外，錯誤輸出還包含 **ErrorCode** 和 **ErrorColumn** 資料行。</span><span class="sxs-lookup"><span data-stu-id="34073-118">In addition to the data columns, the error output includes the **ErrorCode** and **ErrorColumn** columns.</span></span> <span data-ttu-id="34073-119">**ErrorCode** 資料行可以識別錯誤， **ErrorColumn** 包含錯誤資料行的歷程識別碼。</span><span class="sxs-lookup"><span data-stu-id="34073-119">The **ErrorCode** column identifies the error and the **ErrorColumn** contains the lineage identifier of the error column.</span></span> <span data-ttu-id="34073-120">若要檢視這些資料行的中繼資料，請按一下將錯誤輸出連接到資料流程中之下一個元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="34073-120">To view the metadata of these columns, click the path that connects the error output to the next component in the data flow.</span></span> <span data-ttu-id="34073-121">在某些情況下， **ErrorColumn** 資料行的值會被設定為零。</span><span class="sxs-lookup"><span data-stu-id="34073-121">Under some circumstances, the value of the **ErrorColumn** column is set to zero.</span></span> <span data-ttu-id="34073-122">當錯誤狀況影響整個資料列而非單一資料行時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="34073-122">This occurs when the error condition affects the entire row instead of a single column.</span></span> <span data-ttu-id="34073-123">其中一個例子是查閱轉換中的查閱失敗時。</span><span class="sxs-lookup"><span data-stu-id="34073-123">An example is when a lookup fails in the Lookup transformation.</span></span>  
  
 <span data-ttu-id="34073-124">如需詳細資訊，請參閱 [資料流程](data-flow.md) 和 [Integration Services 路徑](integration-services-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="34073-124">For more information, see [Data Flow](data-flow.md) and [Integration Services Paths](integration-services-paths.md).</span></span>  
  
 <span data-ttu-id="34073-125">如需 Integration Services 錯誤、警告和其他訊息的清單，請參閱 [Integration Services 錯誤和訊息參考](../integration-services-error-and-message-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="34073-125">For a list of Integration Services errors, warnings, and other messages, see [Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md).</span></span>  
  
## <a name="error-and-truncation-options"></a><span data-ttu-id="34073-126">錯誤與截斷選項</span><span class="sxs-lookup"><span data-stu-id="34073-126">Error and Truncation Options</span></span>  
 <span data-ttu-id="34073-127">錯誤可以歸類為下列兩種類別之一：錯誤或截斷。</span><span class="sxs-lookup"><span data-stu-id="34073-127">Errors fall into one of two categories: errors or truncations.</span></span> <span data-ttu-id="34073-128">錯誤表示明確的失敗，並產生 NULL 結果。</span><span class="sxs-lookup"><span data-stu-id="34073-128">An error indicates an unequivocal failure, and generates a NULL result.</span></span> <span data-ttu-id="34073-129">此類錯誤可以包含資料轉換錯誤或運算式評估錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-129">Such errors can include data conversion errors or expression evaluation errors.</span></span> <span data-ttu-id="34073-130">例如，嘗試將包含字母字元的字串轉換為數值時，會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-130">For example, an attempt to convert a string that contains alphabetical characters to a number causes an error.</span></span> <span data-ttu-id="34073-131">資料轉換、運算式評估，以及運算式結果指派至變數、屬性和資料行可能會因為不合法的轉型和不相容的資料類型而失敗。</span><span class="sxs-lookup"><span data-stu-id="34073-131">Data conversions, expression evaluations, and assignments of expression results to variables, properties, and data columns may fail because of illegal casts and incompatible data types.</span></span> <span data-ttu-id="34073-132">如需詳細資訊，請參閱 [Cast &#40;SSIS 運算式&#41;](../expressions/cast-ssis-expression.md)、[運算式中的 Integration Services 資料類型](../expressions/integration-services-data-types-in-expressions.md)和 [Integration Services 資料類型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="34073-132">For more information see, [Cast &#40;SSIS Expression&#41;](../expressions/cast-ssis-expression.md), [Integration Services Data Types in Expressions](../expressions/integration-services-data-types-in-expressions.md), and [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="34073-133">截斷的嚴重性低於錯誤。</span><span class="sxs-lookup"><span data-stu-id="34073-133">A truncation is less serious than an error.</span></span> <span data-ttu-id="34073-134">截斷產生的結果可能是可使用的，甚至可能是想要的結果。</span><span class="sxs-lookup"><span data-stu-id="34073-134">A truncation generates results that might be usable or even desirable.</span></span> <span data-ttu-id="34073-135">您可以選擇將截斷視為錯誤或可接受的條件。</span><span class="sxs-lookup"><span data-stu-id="34073-135">You can elect to treat truncations as errors or as acceptable conditions.</span></span> <span data-ttu-id="34073-136">例如，如果您要將 15 個字元的字串插入寬度僅為一個字元的資料行中，則您可以選擇截斷字串。</span><span class="sxs-lookup"><span data-stu-id="34073-136">For example, if you are inserting a 15-character string into a column that is only one character wide, you can elect to truncate the string.</span></span>  
  
 <span data-ttu-id="34073-137">您可以設定來源、轉換及目的地處理錯誤和截斷的方式。</span><span class="sxs-lookup"><span data-stu-id="34073-137">You can configure how sources, transformations, and destinations handle errors and truncations.</span></span> <span data-ttu-id="34073-138">下表描述這些選項。</span><span class="sxs-lookup"><span data-stu-id="34073-138">The following table describes the options.</span></span>  
  
|<span data-ttu-id="34073-139">選項</span><span class="sxs-lookup"><span data-stu-id="34073-139">Option</span></span>|<span data-ttu-id="34073-140">描述</span><span class="sxs-lookup"><span data-stu-id="34073-140">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="34073-141">失敗元件</span><span class="sxs-lookup"><span data-stu-id="34073-141">Fail Component</span></span>|<span data-ttu-id="34073-142">當發生錯誤或截斷時，資料流程工作將失敗。</span><span class="sxs-lookup"><span data-stu-id="34073-142">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="34073-143">失敗是錯誤和截斷的預設選項。</span><span class="sxs-lookup"><span data-stu-id="34073-143">Failure is the default option for an error and a truncation.</span></span>|  
|<span data-ttu-id="34073-144">忽略失敗</span><span class="sxs-lookup"><span data-stu-id="34073-144">Ignore Failure</span></span>|<span data-ttu-id="34073-145">會忽略錯誤或截斷，並會將資料列導向轉換或來源的輸出。</span><span class="sxs-lookup"><span data-stu-id="34073-145">The error or the truncation is ignored and the data row is directed to the output of the transformation or source.</span></span>|  
|<span data-ttu-id="34073-146">重新導向資料列</span><span class="sxs-lookup"><span data-stu-id="34073-146">Redirect Row</span></span>|<span data-ttu-id="34073-147">會將錯誤或截斷資料列導向來源、轉換或目的地的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="34073-147">The error or the truncation data row is directed to the error output of the source, transformation, or destination.</span></span>|  
  
## <a name="adding-the-error-description"></a><span data-ttu-id="34073-148">新增錯誤描述</span><span class="sxs-lookup"><span data-stu-id="34073-148">Adding the Error Description</span></span>  
 <span data-ttu-id="34073-149">依預設，錯誤輸出會提供數值錯誤碼，且通常包含發生錯誤之資料行的識別碼。</span><span class="sxs-lookup"><span data-stu-id="34073-149">By default an error output provides the numeric error code and usually contains the identifier of the column in which the error occurred.</span></span> <span data-ttu-id="34073-150">您可以使用「指令碼」元件，利用單行指令碼來呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 介面的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 方法，以便將錯誤描述包含在其他的資料行中。</span><span class="sxs-lookup"><span data-stu-id="34073-150">You can use the Script component to include the error description in an additional column by using a single line of script to call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span>  
  
 <span data-ttu-id="34073-151">「指令碼」元件可以加入資料流程之錯誤區段的任何位置，但必須在您想擷取錯誤之資料流程元件的下游；不過這個元件通常是在將錯誤資料列寫入目的地之前才放入。</span><span class="sxs-lookup"><span data-stu-id="34073-151">The Script component can be added to the error segment of the data flow anywhere downstream from the data flow components whose errors that you want to capture, but is typically placed immediately before the error rows are written to a destination.</span></span> <span data-ttu-id="34073-152">如此一來指令碼就只會查閱寫入之錯誤資料列的描述。</span><span class="sxs-lookup"><span data-stu-id="34073-152">This way, the script looks up only descriptions for error rows that are written.</span></span> <span data-ttu-id="34073-153">例如，資料流程的錯誤區段可能會更新某些錯誤，而且不會將這些資料列寫入錯誤目的地。</span><span class="sxs-lookup"><span data-stu-id="34073-153">For example, the error segment of the data flow may correct some errors and not write those rows to an error destination.</span></span> <span data-ttu-id="34073-154">如需詳細資訊，請參閱[使用腳本元件增強錯誤輸出](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="34073-154">For more information, see [Enhancing an Error Output with the Script Component](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md).</span></span>  
  
### <a name="to-configure-an-error-output"></a><span data-ttu-id="34073-155">設定錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="34073-155">To configure an error output</span></span>  
  
-   [<span data-ttu-id="34073-156">在資料流程元件中設定錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="34073-156">Configure an Error Output in a Data Flow Component</span></span>](../configure-an-error-output-in-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="34073-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34073-157">See Also</span></span>  
 <span data-ttu-id="34073-158">[資料流程](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="34073-158">[Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="34073-159">[使用轉換來轉換資料](transformations/transform-data-with-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="34073-159">[Transform Data with Transformations](transformations/transform-data-with-transformations.md) </span></span>  
 <span data-ttu-id="34073-160">[以路徑連接元件](../connect-components-with-paths.md) </span><span class="sxs-lookup"><span data-stu-id="34073-160">[Connect Components with Paths](../connect-components-with-paths.md) </span></span>  
 <span data-ttu-id="34073-161">[資料流程工作](../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="34073-161">[Data Flow Task](../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="34073-162">資料流程</span><span class="sxs-lookup"><span data-stu-id="34073-162">Data Flow</span></span>](data-flow.md)  
  
  
