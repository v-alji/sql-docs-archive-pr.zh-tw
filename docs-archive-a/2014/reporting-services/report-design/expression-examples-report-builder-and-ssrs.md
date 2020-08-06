---
title: 運算式範例 (報表產生器及 SSRS) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/08/2017
ms.openlocfilehash: c7ef06143dafdb5034d0f6202fdc16bc51f74ca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594409"
---
# <a name="expression-examples-report-builder-and-ssrs"></a><span data-ttu-id="3a324-102">運算式範例 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3a324-102">Expression Examples (Report Builder and SSRS)</span></span>

<span data-ttu-id="3a324-103">運算式常用於在報表中控制內容以及報表的外觀。</span><span class="sxs-lookup"><span data-stu-id="3a324-103">Expressions are used frequently in reports to control content and report appearance.</span></span> <span data-ttu-id="3a324-104">運算式是以撰寫 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ，而且可以使用內建函數自訂程式碼、報表與群組變數，以及使用者定義的變數。</span><span class="sxs-lookup"><span data-stu-id="3a324-104">Expressions are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], and can use built-in functions custom code, report and group variables, and user-defined variables.</span></span> <span data-ttu-id="3a324-105">運算式以等號 (=) 當做開頭。</span><span class="sxs-lookup"><span data-stu-id="3a324-105">Expressions begin with an equal sign (=).</span></span> <span data-ttu-id="3a324-106">如需運算式編輯器以及可包含之參考類型的詳細資訊，請參閱[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) 和[新增運算式 &#40;報表產生器及 SSRS&#41;](add-an-expression-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-106">For more information about the expression editor and the types of references that you can include, see [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md), and [Add an Expression &#40;Report Builder and SSRS&#41;](add-an-expression-report-builder-and-ssrs.md).</span></span>  

> [!IMPORTANT]  
>  <span data-ttu-id="3a324-107">若啟用 RDL 沙箱，當報表發行時，運算式文字中只能使用特定類型和成員。</span><span class="sxs-lookup"><span data-stu-id="3a324-107">When RDL Sandboxing is enabled, only certain types and members can be used in expression text at report publish time.</span></span> <span data-ttu-id="3a324-108">如需詳細資訊，請參閱 [啟用與停用 RDL 沙箱](../enable-and-disable-rdl-sandboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-108">For more information, see [Enable and Disable RDL Sandboxing](../enable-and-disable-rdl-sandboxing.md).</span></span>  

<span data-ttu-id="3a324-109">本主題提供可用於報表中一般工作的運算式範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-109">This topic provides examples of expressions that can be used for common tasks in a report.</span></span>  

-   <span data-ttu-id="3a324-110">[Visual Basic 函數](#VisualBasicFunctions) ：日期、字串、轉換和條件式 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數的範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-110">[Visual Basic Functions](#VisualBasicFunctions) Examples for date, string, conversion and conditional [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions.</span></span>  

-   <span data-ttu-id="3a324-111">[報表函數](#ReportFunctions) ：彙總和其他內建報表函數的範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-111">[Report Functions](#ReportFunctions) Examples for aggregates and other built-in report functions.</span></span>  

-   <span data-ttu-id="3a324-112">[報表資料的外觀](#AppearanceofReportData) ：變更報表外觀的範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-112">[Appearance of Report Data](#AppearanceofReportData) Examples for changing the appearance of a report.</span></span>  

-   <span data-ttu-id="3a324-113">[屬性](#Properties) ：設定報表項目屬性來控制格式或可見性的範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-113">[Properties](#Properties) Examples for setting report item properties to control format or visibility.</span></span>  

-   <span data-ttu-id="3a324-114">[參數](#Parameters) ：在運算式中使用參數的範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-114">[Parameters](#Parameters) Examples for using parameters in an expression.</span></span>  

-   <span data-ttu-id="3a324-115">[自訂程式碼](#CustomCode) ：內嵌自訂程式碼的範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-115">[Custom Code](#CustomCode) Examples of embedded custom code.</span></span>  

<span data-ttu-id="3a324-116">如需特定用法的運算式範例，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="3a324-116">For expression examples for specific uses, see the following topics:</span></span>  

-   [<span data-ttu-id="3a324-117">群組運算式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-117">Group Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="3a324-118">篩選方程式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-118">Filter Equation Examples &#40;Report Builder and SSRS&#41;</span></span>](filter-equation-examples-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="3a324-119">常用的篩選 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-119">Commonly Used Filters &#40;Report Builder and SSRS&#41;</span></span>](commonly-used-filters-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="3a324-120">報表和群組變數集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-120">Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-report-and-group-variables-references-report-builder.md)  

<span data-ttu-id="3a324-121">如需有關簡單和複雜運算式、使用運算式的地方，以及您可以包含在運算式中之參考類型的詳細資訊，請參閱 [運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-121">For more information about simple and complex expressions, where you can use expressions, and the types of references that you can include in an expression, see topics under [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="3a324-122">如需評估運算式以計算彙總所使用之內容的詳細資訊，請參閱[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-122">For more information about the context in which expressions are evaluated for calculating aggregates, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  

<span data-ttu-id="3a324-123">如需了解如何在撰寫報表的內容中，撰寫使用本主題中運算式範例所使用許多函式和運算子的運算式，請參閱[教學課程：運算式簡介](../tutorial-introducing-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-123">To learn how to write expressions that use many of the functions and operators also used by expression examples in this topic, but in the context of writing a report, see [Tutorial: Introducing Expressions](../tutorial-introducing-expressions.md).</span></span>  

<span data-ttu-id="3a324-124">運算式編輯器包含內建函數的階層式檢視。</span><span class="sxs-lookup"><span data-stu-id="3a324-124">The expression editor includes a hierarchical view of built-in functions.</span></span> <span data-ttu-id="3a324-125">當您選取函數時，程式碼範例會出現在 [值] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="3a324-125">When you select the function, a code example appears in the Values pane.</span></span> <span data-ttu-id="3a324-126">如需詳細資訊，請參閱 &#40;報表產生器&#41;中的 [[運算式] 對話方塊](../expression-dialog-box.md)或 [[運算式] 對話方塊](../expression-dialog-box-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-126">For more information, see the [Expression Dialog Box](../expression-dialog-box.md) or [Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md).</span></span>  

## <a name="functions"></a><span data-ttu-id="3a324-127">函數</span><span class="sxs-lookup"><span data-stu-id="3a324-127">Functions</span></span>  

<span data-ttu-id="3a324-128">報表中的許多運算式都有包含函數，</span><span class="sxs-lookup"><span data-stu-id="3a324-128">Many expressions in a report contain functions.</span></span> <span data-ttu-id="3a324-129">您可以使用這些函數來格式化資料、套用邏輯以及存取報表中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3a324-129">You can format data, apply logic, and access report metadata using these functions.</span></span> <span data-ttu-id="3a324-130">您可以撰寫運算式來使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 執行時間程式庫中的函式，以及來自 <xref:System.Convert> 和 <xref:System.Math> 命名空間的函數。</span><span class="sxs-lookup"><span data-stu-id="3a324-130">You can write expressions that use functions from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library, and from the <xref:System.Convert> and <xref:System.Math> namespaces.</span></span> <span data-ttu-id="3a324-131">您可以加入其他組件或自訂程式碼中函數的參考，</span><span class="sxs-lookup"><span data-stu-id="3a324-131">You can add references to functions from other assemblies or custom code.</span></span> <span data-ttu-id="3a324-132">您也可以使用中的類別 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ，包括 <xref:System.Text.RegularExpressions> 。</span><span class="sxs-lookup"><span data-stu-id="3a324-132">You can also use classes from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], including <xref:System.Text.RegularExpressions>.</span></span>  

###  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> <span data-ttu-id="3a324-133">Visual Basic 函數</span><span class="sxs-lookup"><span data-stu-id="3a324-133">Visual Basic Functions</span></span>  
<span data-ttu-id="3a324-134">您可以利用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數來操作文字方塊所顯示的資料，或參數、屬性或報表的其他區域所用的資料。</span><span class="sxs-lookup"><span data-stu-id="3a324-134">You can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to manipulate the data that is displayed in text boxes or that is used for parameters, properties, or other areas of the report.</span></span> <span data-ttu-id="3a324-135">此章節提供示範其中一些函數的範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-135">This section provides examples demonstrating some of these functions.</span></span> <span data-ttu-id="3a324-136">如需詳細資訊，請參閱 MSDN 上的 [Visual Basic 執行階段程式庫成員](https://go.microsoft.com/fwlink/?LinkId=198941) 。</span><span class="sxs-lookup"><span data-stu-id="3a324-136">For more information, see [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) on MSDN.</span></span>  

<span data-ttu-id="3a324-137">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 提供許多自訂格式選項，例如特定的日期格式。</span><span class="sxs-lookup"><span data-stu-id="3a324-137">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides many custom format options, for example, for specific date formats.</span></span> <span data-ttu-id="3a324-138">如需詳細資訊，請參閱 MSDN 上的 [格式化型別](https://go.microsoft.com/fwlink/?LinkId=112024) 。</span><span class="sxs-lookup"><span data-stu-id="3a324-138">For more information, see [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) on MSDN.</span></span>  

#### <a name="math-functions"></a><span data-ttu-id="3a324-139">數學函式</span><span class="sxs-lookup"><span data-stu-id="3a324-139">Math Functions</span></span>  

-   <span data-ttu-id="3a324-140">`Round` 函數可用來將數字四捨五入至最接近的整數。</span><span class="sxs-lookup"><span data-stu-id="3a324-140">The `Round` function is useful to round numbers to the nearest integer.</span></span> <span data-ttu-id="3a324-141">下列運算式會將 1.3 四捨五入成 1。</span><span class="sxs-lookup"><span data-stu-id="3a324-141">The following expression rounds a 1.3 to 1:</span></span>  

```  
= Round(1.3)  
```  

<span data-ttu-id="3a324-142">您也可以撰寫運算式來將值四捨五入至您所指定的倍數，類似於 Excel 中的 `MRound` 函數。</span><span class="sxs-lookup"><span data-stu-id="3a324-142">You can also write an expression to round a value to a multiple that you specify, similar to the `MRound` function in Excel.</span></span> <span data-ttu-id="3a324-143">您可將值乘以一個可產生整數的因數，將數字四捨五入，然後再除以同一個因數。</span><span class="sxs-lookup"><span data-stu-id="3a324-143">Multiply the value by a factor that creates an integer, round the number, and then divide by the same factor.</span></span> <span data-ttu-id="3a324-144">例如，若要將 1.3 四捨五入到最接近的 .2 的倍數 (1.4)，請使用下列運算式：</span><span class="sxs-lookup"><span data-stu-id="3a324-144">For example, to round 1.3 to the nearest multiple of .2 (1.4), use the following expression:</span></span>  

```  
= Round(1.3*5)/5  
```  

####  <a name="date-functions"></a><a name="DateFunctions"></a><span data-ttu-id="3a324-145">日期函數</span><span class="sxs-lookup"><span data-stu-id="3a324-145">Date Functions</span></span>  

-   <span data-ttu-id="3a324-146">`Today` 函數會提供目前的日期。</span><span class="sxs-lookup"><span data-stu-id="3a324-146">The `Today` function provides the current date.</span></span> <span data-ttu-id="3a324-147">此運算式可用於文字方塊，以顯示報表中的日期，或根據目前的日期在參數中篩選資料。</span><span class="sxs-lookup"><span data-stu-id="3a324-147">This expression can be used in a text box to display the date on the report, or in a parameter to filter data based on the current date.</span></span>  

```  
=Today()  
```  

-   <span data-ttu-id="3a324-148">`DateAdd` 函數在根據單一參數提供一個範圍的日期時很有用。</span><span class="sxs-lookup"><span data-stu-id="3a324-148">The `DateAdd` function is useful for supplying a range of dates based on a single parameter.</span></span> <span data-ttu-id="3a324-149">下列運算式提供在名為 *StartDate*參數的日期六個月之後的日期。</span><span class="sxs-lookup"><span data-stu-id="3a324-149">The following expression provides a date that is six months after the date from a parameter named *StartDate*.</span></span>  

```  
=DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
```  

-   <span data-ttu-id="3a324-150">`Year` 函數會顯示特定日期的年份。</span><span class="sxs-lookup"><span data-stu-id="3a324-150">The `Year` function displays the year for a particular date.</span></span> <span data-ttu-id="3a324-151">您可以使用這個來將日期群組在一起，或是將年顯示為一組日期的標籤。</span><span class="sxs-lookup"><span data-stu-id="3a324-151">You can use this to group dates together or to display the year as a label for a set of dates.</span></span> <span data-ttu-id="3a324-152">這個運算式會提供給定訂購日期群組的年份。</span><span class="sxs-lookup"><span data-stu-id="3a324-152">This expression provides the year for a given group of sales order dates.</span></span> <span data-ttu-id="3a324-153">`Month` 函數和其他函數也可用來操作日期。</span><span class="sxs-lookup"><span data-stu-id="3a324-153">The `Month` function and other functions can also be used to manipulate dates.</span></span> <span data-ttu-id="3a324-154">如需詳細資訊，請參閱 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 文件。</span><span class="sxs-lookup"><span data-stu-id="3a324-154">For more information, see the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] documentation.</span></span>  

```  
=Year(Fields!OrderDate.Value)  
```  

-   <span data-ttu-id="3a324-155">您可以在運算式中結合函數來自訂格式。</span><span class="sxs-lookup"><span data-stu-id="3a324-155">You can combine functions in an expression to customize the format.</span></span> <span data-ttu-id="3a324-156">下列運算式會將日期的格式從「月-日-年」改成「月-週-週數」，</span><span class="sxs-lookup"><span data-stu-id="3a324-156">The following expression changes the format of a date in the form month-day-year to month-week-week number.</span></span> <span data-ttu-id="3a324-157">例如從 12/23/2009 改成 December Week 3：</span><span class="sxs-lookup"><span data-stu-id="3a324-157">For example, 12/23/2009 to December Week 3:</span></span>  

```  
=Format(Fields!MyDate.Value, "MMMM") & " Week " &   
(Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
```  

<span data-ttu-id="3a324-158">當做為資料集中的導出欄位使用時，您可以在圖表中使用這個運算式，在每個月內逐週彙總值。</span><span class="sxs-lookup"><span data-stu-id="3a324-158">When used as a calculated field in a dataset, you can use this expression on a chart to aggregate values by week within each month.</span></span>  

-   <span data-ttu-id="3a324-159">下列運算式會將 SellStartDate 值格式化為 MMM-YY。</span><span class="sxs-lookup"><span data-stu-id="3a324-159">The following expression formats the SellStartDate value as MMM-YY.</span></span> <span data-ttu-id="3a324-160">SellStartDate 欄位是 datetime 資料類型。</span><span class="sxs-lookup"><span data-stu-id="3a324-160">SellStartDate field is a datetime data type.</span></span>  

```  
=FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
```  

-   <span data-ttu-id="3a324-161">下列運算式會將 SellStartDate 值格式化為 dd/MM/yyyy。</span><span class="sxs-lookup"><span data-stu-id="3a324-161">The following expression formats the SellStartDate value as dd/MM/yyyy.</span></span> <span data-ttu-id="3a324-162">SellStartDate 欄位是 datetime 資料類型。</span><span class="sxs-lookup"><span data-stu-id="3a324-162">The SellStartDate field is a datetime data type.</span></span>  

```  
=FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
```  

-   <span data-ttu-id="3a324-163">`CDate` 函數會將值轉換成日期。</span><span class="sxs-lookup"><span data-stu-id="3a324-163">The `CDate` function converts the value to a date.</span></span> <span data-ttu-id="3a324-164">`Now` 函數會根據您的系統傳回包含目前日期和時間的日期值。</span><span class="sxs-lookup"><span data-stu-id="3a324-164">The `Now` function returns a date value containing the current date and time according to your system.</span></span> <span data-ttu-id="3a324-165">`DateDiff` 會傳回長數值，指定兩個日期值之間的時間間隔數。</span><span class="sxs-lookup"><span data-stu-id="3a324-165">`DateDiff` returns a Long value specifying the number of time intervals between two Date values.</span></span>  

<span data-ttu-id="3a324-166">下列範例顯示目前年度的開始日期</span><span class="sxs-lookup"><span data-stu-id="3a324-166">The following example displays the start date of the current year</span></span>  

```  
=DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
```  

-   <span data-ttu-id="3a324-167">下列範例會根據目前月份顯示上個月的開始日期。</span><span class="sxs-lookup"><span data-stu-id="3a324-167">The following example displays the start date for the previous month based on the current month.</span></span>  

```  
=DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
```  

-   <span data-ttu-id="3a324-168">下列運算式會產生 SellStartDate 與 LastReceiptDate 之間的間隔年數。</span><span class="sxs-lookup"><span data-stu-id="3a324-168">The following expression generates the interval years between SellStartDate and LastReceiptDate.</span></span> <span data-ttu-id="3a324-169">這些欄位位於兩個不同的資料集：DataSet1 和 DataSet2 中。</span><span class="sxs-lookup"><span data-stu-id="3a324-169">These fields are in two different datasets, DataSet1 and DataSet2.</span></span> <span data-ttu-id="3a324-170">[First 函式 &#40;報表產生器及 SSRS&#41;](report-builder-functions-first-function.md) 為彙總函式，它會傳回 DataSet1 中 SellStartDate 的第一個值，以及 DataSet2 中 LastReceiptDate 的第一個值。</span><span class="sxs-lookup"><span data-stu-id="3a324-170">The [First Function &#40;Report Builder and SSRS&#41;](report-builder-functions-first-function.md), which is an aggregate function, returns the first value of SellStartDate in DataSet1 and the first value of LastReceiptDate in DataSet2.</span></span>  

```  
=DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
```  

-   <span data-ttu-id="3a324-171">`DatePart` 函數會傳回包含給定 Date 值之指定元件的整數值。下列運算式則會傳回 DataSet1 中 SellStartDate 第一個值的年份。</span><span class="sxs-lookup"><span data-stu-id="3a324-171">The `DatePart` function returns an Integer value containing the specified component of a given Date value.The following expression returns the year for the first value of the SellStartDate in DataSet1.</span></span> <span data-ttu-id="3a324-172">已指定資料集範圍，因為報表中有多個資料集。</span><span class="sxs-lookup"><span data-stu-id="3a324-172">The dataset scope is specified because there are multiple datasets in the report.</span></span>  

```  
=Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  

```  

-   <span data-ttu-id="3a324-173">`DateSerial` 函數會傳回代表指定年、月、日，並將時間資訊設為午夜的 Date 值。</span><span class="sxs-lookup"><span data-stu-id="3a324-173">The `DateSerial` function returns a Date value representing a specified year, month, and day, with the time information set to midnight.</span></span> <span data-ttu-id="3a324-174">下列範例會根據目前月份顯示上個月的結束日期。</span><span class="sxs-lookup"><span data-stu-id="3a324-174">The following example displays the ending date for the prior month, based on the current month.</span></span>  

```  
=DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
```  

-   <span data-ttu-id="3a324-175">下列運算式會根據使用者選取的日期參數值，顯示各種日期。</span><span class="sxs-lookup"><span data-stu-id="3a324-175">The following expressions display various dates based on a date parameter value selected by the user.</span></span>  

|<span data-ttu-id="3a324-176">範例描述</span><span class="sxs-lookup"><span data-stu-id="3a324-176">Example Description</span></span>|<span data-ttu-id="3a324-177">範例</span><span class="sxs-lookup"><span data-stu-id="3a324-177">Example</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="3a324-178">昨天</span><span class="sxs-lookup"><span data-stu-id="3a324-178">Yesterday</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|<span data-ttu-id="3a324-179">兩天前</span><span class="sxs-lookup"><span data-stu-id="3a324-179">Two Days Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|<span data-ttu-id="3a324-180">一個月前</span><span class="sxs-lookup"><span data-stu-id="3a324-180">One Month Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="3a324-181">兩個月前</span><span class="sxs-lookup"><span data-stu-id="3a324-181">Two Months Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="3a324-182">一年前</span><span class="sxs-lookup"><span data-stu-id="3a324-182">One Year Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="3a324-183">兩年前</span><span class="sxs-lookup"><span data-stu-id="3a324-183">Two Years Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  

####  <a name="string-functions"></a><a name="StringFunctions"></a><span data-ttu-id="3a324-184">字串函式</span><span class="sxs-lookup"><span data-stu-id="3a324-184">String Functions</span></span>  

-   <span data-ttu-id="3a324-185">您可以使用串連運算子和 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 常數，將一個以上的欄位結合在一起。</span><span class="sxs-lookup"><span data-stu-id="3a324-185">Combine more than one field by using concatenation operators and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] constants.</span></span> <span data-ttu-id="3a324-186">下列運算式會傳回兩個欄位，分別位於相同文字方塊中的不同行：</span><span class="sxs-lookup"><span data-stu-id="3a324-186">The following expression returns two fields, each on a separate line in the same text box:</span></span>  

```  
=Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
```  

-   <span data-ttu-id="3a324-187">您可以使用 `Format` 函數，將字串中的日期與數字格式化。</span><span class="sxs-lookup"><span data-stu-id="3a324-187">Format dates and numbers in a string with the `Format` function.</span></span> <span data-ttu-id="3a324-188">下列運算式會以完整日期格式來顯示 *StartDate* 和 *EndDate* 參數的值：</span><span class="sxs-lookup"><span data-stu-id="3a324-188">The following expression displays values of the *StartDate* and *EndDate* parameters in long date format:</span></span>  

```  
=Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
```  

<span data-ttu-id="3a324-189">如果文字方塊只包含日期或數位，您應該使用文字方塊的 Format 屬性來套用格式設定，而不是文字方塊內的函式 `Format` 。</span><span class="sxs-lookup"><span data-stu-id="3a324-189">If the text box contains only a date or number, you should use the Format property of the text box to apply formatting instead of the `Format` function within the text box.</span></span>  

-   <span data-ttu-id="3a324-190">`Right`、 `Len` 和函數在傳回 `InStr` 子字串時很有用，例如，將網域使用者*DOMAIN* \\ *username*名稱修剪成隻有使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="3a324-190">The `Right`, `Len`, and `InStr` functions are useful for returning a substring, for example, trimming *DOMAIN*\\*username* to just the user name.</span></span> <span data-ttu-id="3a324-191">下列運算式會從名為\\User *的參數傳回字串中反斜線 (*) 字元右邊的字串部分：</span><span class="sxs-lookup"><span data-stu-id="3a324-191">The following expression returns the part of the string to the right of a backslash (\\) character from a parameter named *User*:</span></span>  

```  
=Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
```  

<span data-ttu-id="3a324-192">下列運算式會產生與上一個運算式相同的值，使用類別的成員， [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.String> 而不是 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數：</span><span class="sxs-lookup"><span data-stu-id="3a324-192">The following expression results in the same value as the previous one, using members of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.String> class instead of [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions:</span></span>  

```  
=Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
```  

-   <span data-ttu-id="3a324-193">顯示多重數值參數中所選的值。</span><span class="sxs-lookup"><span data-stu-id="3a324-193">Display the selected values from a multivalue parameter.</span></span> <span data-ttu-id="3a324-194">下列範例會使用函式 `Join` ，將參數*MySelection*的選取值串連成單一字串，以便設定為報表專案中文字方塊值的運算式：</span><span class="sxs-lookup"><span data-stu-id="3a324-194">The following example uses the `Join` function to concatenate the selected values of the parameter *MySelection* into a single string that can be set as an expression for the value of a text box in a report item:</span></span>  

```  
= Join(Parameters!MySelection.Value)  
```  

<span data-ttu-id="3a324-195">下列範例的作用與上述範例相同，也會在選取值清單前面顯示文字字串。</span><span class="sxs-lookup"><span data-stu-id="3a324-195">The following example does the same as the above example, as well as displays a text string prior to the list of selected values.</span></span>  

```  
="Report for " & JOIN(Parameters!MySelection.Value, " & ")  

```  

-   <span data-ttu-id="3a324-196">中的函式適用 `Regex` [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> 于變更現有字串的格式，例如，格式化電話號碼。</span><span class="sxs-lookup"><span data-stu-id="3a324-196">The `Regex` functions from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> are useful for changing the format of existing strings, for example, formatting a telephone number.</span></span> <span data-ttu-id="3a324-197">下列運算式使用 `Replace` 函數，將欄位中十位數電話號碼的格式從 "*nnn* - *nnn* - *nnnn*" 變更為 " (*nnn*) *nnn* - *nnnn*"：</span><span class="sxs-lookup"><span data-stu-id="3a324-197">The following expression uses the `Replace` function to change the format of a ten-digit telephone number in a field from "*nnn*-*nnn*-*nnnn*" to "(*nnn*) *nnn*-*nnnn*":</span></span>  

```  
=System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
```  

> [!NOTE]  
>  <span data-ttu-id="3a324-198">確認 Fields!Phone.Value 的值沒有額外的空格，而且為 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="3a324-198">Verify that the value for Fields!Phone.Value has no extra spaces and is of type <xref:System.String>.</span></span>  

#### <a name="lookup"></a><span data-ttu-id="3a324-199">查閱</span><span class="sxs-lookup"><span data-stu-id="3a324-199">Lookup</span></span>  

-   <span data-ttu-id="3a324-200">您可以藉由指定索引鍵欄位，使用 `Lookup` 函數來從一對一關係的資料集 (如索引鍵-值組) 中擷取值。</span><span class="sxs-lookup"><span data-stu-id="3a324-200">By specifying a key field, you can use the `Lookup` function to retrieve a value from a dataset for a one-to-one relationship, for example, a key-value pair.</span></span> <span data-ttu-id="3a324-201">下列運算式會顯示提供要比對的產品識別碼時，資料集 ("Product") 中的產品名稱：</span><span class="sxs-lookup"><span data-stu-id="3a324-201">The following expression displays the product name from a dataset ("Product"), given the product identifier to match on:</span></span>  

```  
=Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields!ProductName.Value, "Product")  
```  

#### <a name="lookupset"></a><span data-ttu-id="3a324-202">LookupSet</span><span class="sxs-lookup"><span data-stu-id="3a324-202">LookupSet</span></span>  

-   <span data-ttu-id="3a324-203">您可以藉由指定索引鍵欄位，使用 `LookupSet` 函數來從一對多關係的資料集中擷取一組值。</span><span class="sxs-lookup"><span data-stu-id="3a324-203">By specifying a key field, you can use the `LookupSet` function to retrieve a set of values from a dataset for a one-to-many relationship.</span></span> <span data-ttu-id="3a324-204">例如，人員可以擁有多個電話號碼。</span><span class="sxs-lookup"><span data-stu-id="3a324-204">For example, a person can have multiple telephone numbers.</span></span> <span data-ttu-id="3a324-205">在下列範例中，假設 PhoneList 資料集在每一個資料列中包含人員識別碼和電話號碼。</span><span class="sxs-lookup"><span data-stu-id="3a324-205">In the following example, assume the dataset PhoneList contains a person identifier and a telephone number in each row.</span></span> <span data-ttu-id="3a324-206">`LookupSet` 會傳回值的陣列。</span><span class="sxs-lookup"><span data-stu-id="3a324-206">`LookupSet` returns an array of values.</span></span> <span data-ttu-id="3a324-207">下列運算式會將傳回值結合成單一字串，並顯示 ContactID 指定之人員的電話號碼清單：</span><span class="sxs-lookup"><span data-stu-id="3a324-207">The following expression combines the return values into a single string and displays the list of telephone numbers for the person specified by ContactID:</span></span>  

```  
=Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
```  

####  <a name="conversion-functions"></a><a name="ConversionFunctions"></a><span data-ttu-id="3a324-208">轉換函式</span><span class="sxs-lookup"><span data-stu-id="3a324-208">Conversion Functions</span></span>  
<span data-ttu-id="3a324-209">您可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數，將欄位從一種資料類型轉換成不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3a324-209">You can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to convert a field from the one data type to a different data type.</span></span> <span data-ttu-id="3a324-210">轉換函數可用來將欄位的預設資料類型轉換為計算或結合文字時所需的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3a324-210">Conversion functions can be used to convert the default data type for a field to the data type needed for calculations or to combine text.</span></span>  

-   <span data-ttu-id="3a324-211">下列運算式會將常數 500 轉換為 Decimal 類型，以便與篩選運算式之值欄位中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] money 資料類型相比較。</span><span class="sxs-lookup"><span data-stu-id="3a324-211">The following expression converts the constant 500 to type Decimal in order to compare it to a [!INCLUDE[tsql](../../includes/tsql-md.md)] money data type in the Value field for a filter expression.</span></span>  

```  
=CDec(500)  
```  

-   <span data-ttu-id="3a324-212">下列運算式會顯示針對多重數值參數 *MySelection*所選的值數目。</span><span class="sxs-lookup"><span data-stu-id="3a324-212">The following expression displays the number of values selected for the multivalue parameter *MySelection*.</span></span>  

```  
=CStr(Parameters!MySelection.Count)  
```  

####  <a name="decision-functions"></a><a name="DecisionFunctions"></a> <span data-ttu-id="3a324-213">決策函數</span><span class="sxs-lookup"><span data-stu-id="3a324-213">Decision Functions</span></span>  

-   <span data-ttu-id="3a324-214">`Iif` 函數會根據運算式是否評估為 true 而傳回兩個值之一。</span><span class="sxs-lookup"><span data-stu-id="3a324-214">The `Iif` function returns one of two values depending on whether the expression is true or not.</span></span> <span data-ttu-id="3a324-215">當 `LineTotal` 超過 100 時，下列運算式會使用 `Iif` 函數來傳回布林值 `True`，</span><span class="sxs-lookup"><span data-stu-id="3a324-215">The following expression uses the `Iif` function to return a Boolean value of `True` if the value of `LineTotal` exceeds 100.</span></span> <span data-ttu-id="3a324-216">否則會傳回 `False`：</span><span class="sxs-lookup"><span data-stu-id="3a324-216">Otherwise it returns `False`:</span></span>  

```  
=IIF(Fields!LineTotal.Value > 100, True, False)  
```  

-   <span data-ttu-id="3a324-217">使用多個 `IIF` 函數 (也稱為「巢狀 IIF」) 可以根據 `PctComplete` 值傳回三個值之一。</span><span class="sxs-lookup"><span data-stu-id="3a324-217">Use multiple `IIF` functions (also known as "nested IIFs") to return one of three values depending on the value of `PctComplete`.</span></span> <span data-ttu-id="3a324-218">您可以將下列運算式置入文字方塊的填滿色彩，依照文字方塊中的值而變更背景色彩。</span><span class="sxs-lookup"><span data-stu-id="3a324-218">The following expression can be placed in the fill color of a text box to change the background color depending on the value in the text box.</span></span>  

```  
=IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
```  

<span data-ttu-id="3a324-219">大於或等於 10 的值會以綠色背景顯示、介於 1 和 9 之間的值以藍色背景顯示，小於 1 的值則以紅色背景顯示。</span><span class="sxs-lookup"><span data-stu-id="3a324-219">Values greater than or equal to 10 display with a green background, between 1 and 9 display with a blue background, and less than 1 display with a red background.</span></span>  

-   <span data-ttu-id="3a324-220">另一種取得相同功能的方法，是使用 `Switch` 函數。</span><span class="sxs-lookup"><span data-stu-id="3a324-220">A different way to get the same functionality uses the `Switch` function.</span></span> <span data-ttu-id="3a324-221">當測試的條件有三個或三個以上時，`Switch` 函數就很有用。</span><span class="sxs-lookup"><span data-stu-id="3a324-221">The `Switch` function is useful when you have three or more conditions to test.</span></span> <span data-ttu-id="3a324-222">`Switch` 函數會傳回與數列中評估為 true 的第一個運算式相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="3a324-222">The `Switch` function returns the value associated with the first expression in a series that evaluates to true:</span></span>  

```  
=Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red",)  
```  

<span data-ttu-id="3a324-223">大於或等於 10 的值會以綠色背景顯示、介於 1 和 9 之間的值以藍色背景顯示、等於 1 的值以黃色背景顯示，0 或小於 0 的值則以紅色背景顯示。</span><span class="sxs-lookup"><span data-stu-id="3a324-223">Values greater than or equal to 10 display with a green background, between 1 and 9 display with a blue background, equal to 1 display with a yellow background, and 0 or less display with a red background.</span></span>  

-   <span data-ttu-id="3a324-224">測試 `ImportantDate` 欄位的值，如果超過一週會傳回 "Red"，否則傳回 "Blue"。</span><span class="sxs-lookup"><span data-stu-id="3a324-224">Test the value of the `ImportantDate` field and return "Red" if it is more than a week old, and "Blue" otherwise.</span></span> <span data-ttu-id="3a324-225">這個運算式可用來控制報表項目中文字方塊的色彩屬性：</span><span class="sxs-lookup"><span data-stu-id="3a324-225">This expression can be used to control the Color property of a text box in a report item:</span></span>  

```  
=IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
```  

-   <span data-ttu-id="3a324-226">測試 `PhoneNumber` 欄位的值，如果為 `null` (在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 `Nothing`) 傳回 "No Value"，否則傳回電話號碼值。</span><span class="sxs-lookup"><span data-stu-id="3a324-226">Test the value of the `PhoneNumber` field and return "No Value" if it is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]); otherwise return the phone number value.</span></span> <span data-ttu-id="3a324-227">這個運算式可用來控制報表項目中文字方塊的值。</span><span class="sxs-lookup"><span data-stu-id="3a324-227">This expression can be used to control the value of a text box in a report item.</span></span>  

```  
=IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
```  

-   <span data-ttu-id="3a324-228">測試 `Department` 欄位的值，並傳回子報表名稱或`null` (在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="3a324-228">Test the value of the `Department` field and return either a subreport name or a `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="3a324-229">此運算式可用於條件式鑽研子報表。</span><span class="sxs-lookup"><span data-stu-id="3a324-229">This expression can be used for conditional drillthrough subreports.</span></span>  

```  
=IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
```  

-   <span data-ttu-id="3a324-230">測試欄位值是否為 Null。</span><span class="sxs-lookup"><span data-stu-id="3a324-230">Test if a field value is null.</span></span> <span data-ttu-id="3a324-231">此運算式可用來控制影像報表項目的 `Hidden` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3a324-231">This expression can be used to control the `Hidden` property of an image report item.</span></span> <span data-ttu-id="3a324-232">在下列範例中，只有當欄位 [LargePhoto] 的值不是 Null 時，才會顯示該欄位所指定的影像。</span><span class="sxs-lookup"><span data-stu-id="3a324-232">In the following example, the image specified by the field [LargePhoto] is displayed only if the value of the field is not null.</span></span>  

```  
=IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
```  

-   <span data-ttu-id="3a324-233">`MonthName` 函數會傳回字串值，包含指定之月份的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a324-233">The `MonthName` function returns a string value containing the name of the specified month.</span></span> <span data-ttu-id="3a324-234">下列範例會在欄位包含 0 的值時，於月份欄位中顯示 NA。</span><span class="sxs-lookup"><span data-stu-id="3a324-234">The following example displays NA in the Month field when the field contains the value of 0.</span></span>  

```  
IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  

```  

###  <a name="report-functions"></a><a name="ReportFunctions"></a> <span data-ttu-id="3a324-235">報表函數</span><span class="sxs-lookup"><span data-stu-id="3a324-235">Report Functions</span></span>  
<span data-ttu-id="3a324-236">在運算式中，您可以加入在報表中操作資料之其他報表函數的參考。</span><span class="sxs-lookup"><span data-stu-id="3a324-236">In an expression, you can add a reference to additional report functions that manipulate data in a report.</span></span> <span data-ttu-id="3a324-237">此章節提供這些函數的其中兩個範例。</span><span class="sxs-lookup"><span data-stu-id="3a324-237">This section provides examples for two of these functions.</span></span> <span data-ttu-id="3a324-238">如需報表函數和範例的詳細資訊，請參閱[彙總函數參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-238">For more information about report functions and examples, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  

#####  <a name="sum"></a><a name="Sum"></a><span data-ttu-id="3a324-239">要求</span><span class="sxs-lookup"><span data-stu-id="3a324-239">Sum</span></span>  

-   <span data-ttu-id="3a324-240">`Sum` 函數可以將群組或資料區域中的值加總。</span><span class="sxs-lookup"><span data-stu-id="3a324-240">The `Sum` function can total the values in a group or data region.</span></span> <span data-ttu-id="3a324-241">群組的頁首或頁尾可以使用這個函數。</span><span class="sxs-lookup"><span data-stu-id="3a324-241">This function can be useful in the header or footer of a group.</span></span> <span data-ttu-id="3a324-242">下列運算式會顯示 Order 群組或資料區域中資料的總和：</span><span class="sxs-lookup"><span data-stu-id="3a324-242">The following expression displays the sum of data in the Order group or data region:</span></span>  

```  
=Sum(Fields!LineTotal.Value, "Order")  
```  

-   <span data-ttu-id="3a324-243">您也可以使用 `Sum` 函數進行條件式彙總計算。</span><span class="sxs-lookup"><span data-stu-id="3a324-243">You can also use the `Sum` function for conditional aggregate calculations.</span></span> <span data-ttu-id="3a324-244">例如，如果資料集有稱為 State 的欄位，而該欄位具有 Not Started、Started、Finished 等可能值，則下列運算式在置入群組頁首時，只會計算 Finished 值的彙總總和：</span><span class="sxs-lookup"><span data-stu-id="3a324-244">For example, if a dataset has a field that is named State with possible values Not Started, Started, Finished, the following expression, when placed in a group header, calculates the aggregate sum for only the value Finished:</span></span>  

```  
=Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
```  

#####  <a name="rownumber"></a><a name="RowNumber"></a><span data-ttu-id="3a324-245">RowNumber</span><span class="sxs-lookup"><span data-stu-id="3a324-245">RowNumber</span></span>  

-   <span data-ttu-id="3a324-246">`RowNumber` 函數在用於資料區域內的文字方塊時，會為其中顯示此運算式的每個文字方塊執行個體顯示資料列號碼。</span><span class="sxs-lookup"><span data-stu-id="3a324-246">The `RowNumber` function, when used in a text box within a data region, displays the row number for each instance of the text box in which the expression appears.</span></span> <span data-ttu-id="3a324-247">此函數對於計算資料表中的資料列數目非常有用。</span><span class="sxs-lookup"><span data-stu-id="3a324-247">This function can be useful to number rows in a table.</span></span> <span data-ttu-id="3a324-248">它對於更複雜的工作也非常實用，例如，根據資料列數目提供分頁符號。</span><span class="sxs-lookup"><span data-stu-id="3a324-248">It can also be useful for more complex tasks, such as providing page breaks based on number of rows.</span></span> <span data-ttu-id="3a324-249">如需詳細資訊，請參閱這個主題中的 [分頁符號](#PageBreaks) 。</span><span class="sxs-lookup"><span data-stu-id="3a324-249">For more information, see [Page Breaks](#PageBreaks) in this topic.</span></span>  

<span data-ttu-id="3a324-250">您所指定的 `RowNumber` 範圍會控制何時開始重新編號。</span><span class="sxs-lookup"><span data-stu-id="3a324-250">The scope you specify for `RowNumber` controls when renumbering begins.</span></span> <span data-ttu-id="3a324-251">`Nothing` 關鍵字指出函數將從最外層資料區域中的第一個資料列開始計數；</span><span class="sxs-lookup"><span data-stu-id="3a324-251">The `Nothing` keyword indicates that the function will start counting at the first row in the outermost data region.</span></span> <span data-ttu-id="3a324-252">若要在巢狀資料區域內開始計數，請使用資料區域的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a324-252">To start counting within nested data regions, use the name of the data region.</span></span> <span data-ttu-id="3a324-253">若要在群組內開始計數，請使用群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a324-253">To start counting within a group, use the name of the group.</span></span>  

```  
=RowNumber(Nothing)  
```  

##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> <span data-ttu-id="3a324-254">報表資料的外觀</span><span class="sxs-lookup"><span data-stu-id="3a324-254">Appearance of Report Data</span></span>  
<span data-ttu-id="3a324-255">您可以使用運算式來操作報表中資料顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="3a324-255">You can use expressions to manipulate how data appears on a report.</span></span> <span data-ttu-id="3a324-256">例如，可以在單一文字方塊中顯示兩個欄位的值、顯示有關報表的資訊，或影響報表中插入分頁符號的方式。</span><span class="sxs-lookup"><span data-stu-id="3a324-256">For example, you can display the values of two fields in a single text box, display information about the report, or affect how page breaks are inserted in the report.</span></span>  

###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> <span data-ttu-id="3a324-257">頁首和頁尾</span><span class="sxs-lookup"><span data-stu-id="3a324-257">Page Headers and Footers</span></span>  
<span data-ttu-id="3a324-258">設計報表時，您需要顯示報表的名稱以及報表尾的頁碼。</span><span class="sxs-lookup"><span data-stu-id="3a324-258">When designing a report, you may want to display the name of the report and page number in the report footer.</span></span> <span data-ttu-id="3a324-259">若要這麼做，您可以使用下列運算式：</span><span class="sxs-lookup"><span data-stu-id="3a324-259">To do this, you can use the following expressions:</span></span>  

-   <span data-ttu-id="3a324-260">下列運算式提供報表的名稱和執行報表的時間。</span><span class="sxs-lookup"><span data-stu-id="3a324-260">The following expression provides the name of the report and the time it was run.</span></span> <span data-ttu-id="3a324-261">它可以放置在報表尾的文字方塊中或是報表的主體中。</span><span class="sxs-lookup"><span data-stu-id="3a324-261">It can be placed in a text box in the report footer or in the body of the report.</span></span> <span data-ttu-id="3a324-262">時間格式採用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的簡短日期格式字串：</span><span class="sxs-lookup"><span data-stu-id="3a324-262">The time is formatted with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] formatting string for short date:</span></span>  

```  
=Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
```  

-   <span data-ttu-id="3a324-263">下列放在報表尾文字方塊中的運算式，提供報表的頁碼與總頁數。</span><span class="sxs-lookup"><span data-stu-id="3a324-263">The following expression, placed in a text box in the footer of a report, provides page number and total pages in the report:</span></span>  

```  
=Globals.PageNumber & " of " & Globals.TotalPages  
```  

<span data-ttu-id="3a324-264">下列範例描述如何顯示一頁中頁首的第一個和最後一個值，與目錄清單中所找到的類似。</span><span class="sxs-lookup"><span data-stu-id="3a324-264">The following examples describe how to display the first and last values from a page in the page header, similar to what you might find in a directory listing.</span></span> <span data-ttu-id="3a324-265">這個範例假設包含名稱為 `LastName`之文字方塊的資料區域。</span><span class="sxs-lookup"><span data-stu-id="3a324-265">The example assumes a data region that contains a text box named `LastName`.</span></span>  

-   <span data-ttu-id="3a324-266">下列運算式放在頁首左側文字方塊中，用來提供頁面 `LastName` 文字方塊的第一個值：</span><span class="sxs-lookup"><span data-stu-id="3a324-266">The following expression, placed in a text box on the left side of the page header, provides the first value of the `LastName` text box on the page:</span></span>  

```  
=First(ReportItems("LastName").Value)  
```  

-   <span data-ttu-id="3a324-267">下列運算式放在頁首右邊的文字方塊中時，會提供此頁上 `LastName` 文字方塊的最後一個值：</span><span class="sxs-lookup"><span data-stu-id="3a324-267">The following expression, placed in a text box on the right side of the page header, provides the last value of the `LastName` text box on the page:</span></span>  

```  
=Last(ReportItems("LastName").Value)  
```  

<span data-ttu-id="3a324-268">下列範例描述如何顯示總頁數。</span><span class="sxs-lookup"><span data-stu-id="3a324-268">The following example describes how to display a page total.</span></span> <span data-ttu-id="3a324-269">這個範例假設包含名稱為 `Cost`之文字方塊的資料區域。</span><span class="sxs-lookup"><span data-stu-id="3a324-269">The example assumes a data region that contains a text box named `Cost`.</span></span>  

-   <span data-ttu-id="3a324-270">下列運算式放在頁首或頁尾中，用來提供頁面 `Cost` 文字方塊中各個值的總和：</span><span class="sxs-lookup"><span data-stu-id="3a324-270">The following expression, placed in the page header or footer, provides the sum of the values in the `Cost` text box for the page:</span></span>  

```  
=Sum(ReportItems("Cost").Value)  
```  

> [!NOTE]  
>  <span data-ttu-id="3a324-271">在頁首或頁尾中，每個運算式只能參考一個報表項目。</span><span class="sxs-lookup"><span data-stu-id="3a324-271">You can refer to only one report item per expression in a page header or footer.</span></span> <span data-ttu-id="3a324-272">此外，您也可以在頁首或頁尾的運算式中參考文字方塊名稱，但不能參考文字方塊內實際的資料運算式。</span><span class="sxs-lookup"><span data-stu-id="3a324-272">Also, you can refer to the text box name, but not the actual data expression within the text box, in page header and footer expressions.</span></span>  

###  <a name="page-breaks"></a><a name="PageBreaks"></a> <span data-ttu-id="3a324-273">分頁符號</span><span class="sxs-lookup"><span data-stu-id="3a324-273">Page Breaks</span></span>  
<span data-ttu-id="3a324-274">在某些報表中，除了在群組或報表項目上放置分頁符號以外，您也可能會需要在指定資料列數目的結尾處放置分頁符號。</span><span class="sxs-lookup"><span data-stu-id="3a324-274">In some reports, you may want to place a page break at the end of a specified number of rows instead of, or in addition to, on groups or report items.</span></span> <span data-ttu-id="3a324-275">若要執行這個動作，請建立包含所要群組或細節記錄的群組，將分頁符號加入群組中，再依指定的資料列數，將群組運算式加入群組中。</span><span class="sxs-lookup"><span data-stu-id="3a324-275">To do this, create a group that contains the groups or detail records you want, add a page break to the group, and then add a group expression to group by a specified number of rows.</span></span>  

-   <span data-ttu-id="3a324-276">下列運算式放在群組運算式中，每 25 個資料列即指派一個數字。</span><span class="sxs-lookup"><span data-stu-id="3a324-276">The following expression, when placed in the group expression, assigns a number to each set of 25 rows.</span></span> <span data-ttu-id="3a324-277">為群組定義分頁符號時，這個運算式每隔 25 個資料列就會產生一個分頁符號。</span><span class="sxs-lookup"><span data-stu-id="3a324-277">When a page break is defined for the group, this expression results in a page break every 25 rows.</span></span>  

```  
=Ceiling(RowNumber(Nothing)/25)  
```  

<span data-ttu-id="3a324-278">若要讓使用者設定每頁資料列數的值，請建立名為 `RowsPerPage` 的參數，然後以該參數做為群組運算式的基礎，如下列運算式所示：</span><span class="sxs-lookup"><span data-stu-id="3a324-278">To allow the user to set a value for the number of rows per page, create a parameter named `RowsPerPage` and base the group expression on the parameter, as shown in the following expression:</span></span>  

```  
=Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
```  

<span data-ttu-id="3a324-279">如需有關為群組設定分頁符號的詳細資訊，請參閱[加入分頁符號 &#40;報表產生器及 SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-279">For more information about setting page breaks for a group, see [Add a Page Break &#40;Report Builder and SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md).</span></span>  

##  <a name="properties"></a><a name="Properties"></a> <span data-ttu-id="3a324-280">屬性</span><span class="sxs-lookup"><span data-stu-id="3a324-280">Properties</span></span>  
<span data-ttu-id="3a324-281">運算式不只用來顯示文字方塊中的資料。</span><span class="sxs-lookup"><span data-stu-id="3a324-281">Expressions are not only used to display data in text boxes.</span></span> <span data-ttu-id="3a324-282">運算式也可以用來變更將屬性套用至報表項目的方式。</span><span class="sxs-lookup"><span data-stu-id="3a324-282">They can also be used to change how properties are applied to report items.</span></span> <span data-ttu-id="3a324-283">您可以變更報表項目的樣式資訊，或是變更其可見性。</span><span class="sxs-lookup"><span data-stu-id="3a324-283">You can change style information for a report item, or change its visibility.</span></span>  

###  <a name="formatting"></a><a name="Formatting"></a><span data-ttu-id="3a324-284">樣式</span><span class="sxs-lookup"><span data-stu-id="3a324-284">Formatting</span></span>  

-   <span data-ttu-id="3a324-285">當用在文字方塊的 Color 屬性時，下列運算式會依 `Profit` 欄位值而變更文字的色彩：</span><span class="sxs-lookup"><span data-stu-id="3a324-285">The following expression, when used in the Color property of a text box, changes the color of the text depending on the value of the `Profit` field:</span></span>  

```  
=Iif(Fields!Profit.Value < 0, "Red", "Black")  
```  

<span data-ttu-id="3a324-286">您也可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 物件變數 `Me`。</span><span class="sxs-lookup"><span data-stu-id="3a324-286">You can also use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] object variable `Me`.</span></span> <span data-ttu-id="3a324-287">這個變數是另一種參考文字方塊值的方式。</span><span class="sxs-lookup"><span data-stu-id="3a324-287">This variable is another way of referring to the value of a text box.</span></span>  

`=Iif(Me.Value < 0, "Red", "Black")`  

-   <span data-ttu-id="3a324-288">當用在資料區域中之報表項目的 BackgroundColor 屬性中，下列運算式會替代淡綠色和白色之間每個資料列的背景色彩：</span><span class="sxs-lookup"><span data-stu-id="3a324-288">The following expression, when used in the BackgroundColor property of a report item in a data region, alternates the background color of each row between pale green and white:</span></span>  

```  
=Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
```  

<span data-ttu-id="3a324-289">如果您使用指定之範圍的運算式，可能必須指出彙總函式的資料集：</span><span class="sxs-lookup"><span data-stu-id="3a324-289">If you are using an expression for a specified scope, you may have to indicate the dataset for the aggregate function:</span></span>  

```  
=Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
```  

> [!NOTE]  
>  <span data-ttu-id="3a324-290">可用的色彩是來自 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] KnownColor 列舉。</span><span class="sxs-lookup"><span data-stu-id="3a324-290">Available colors come from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] KnownColor enumeration.</span></span>  

### <a name="chart-colors"></a><span data-ttu-id="3a324-291">圖表色彩</span><span class="sxs-lookup"><span data-stu-id="3a324-291">Chart Colors</span></span>  
<span data-ttu-id="3a324-292">若要指定形狀圖的色彩，您可以使用自訂程式碼控制色彩對應到資料點值的順序。</span><span class="sxs-lookup"><span data-stu-id="3a324-292">To specify colors for a Shape chart, you can use custom code to control the order that colors are mapped to data point values.</span></span> <span data-ttu-id="3a324-293">這有助於針對擁有相同類別目錄群組的多個圖表，使用一致的色彩。</span><span class="sxs-lookup"><span data-stu-id="3a324-293">This helps you use consistent colors for multiple charts that have the same category groups.</span></span> <span data-ttu-id="3a324-294">如需詳細資訊，請參閱[跨多個形狀圖指定一致的色彩 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-294">For more information, see [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  

###  <a name="visibility"></a><a name="Visibility"></a><span data-ttu-id="3a324-295">可視</span><span class="sxs-lookup"><span data-stu-id="3a324-295">Visibility</span></span>  
<span data-ttu-id="3a324-296">您可以使用報表項目的可見性屬性，來顯示和隱藏報表中的項目。</span><span class="sxs-lookup"><span data-stu-id="3a324-296">You can show and hide items in a report using the visibility properties for the report item.</span></span> <span data-ttu-id="3a324-297">在如資料表的資料區域中，您可以根據運算式中的值一開始便隱藏詳細資料列。</span><span class="sxs-lookup"><span data-stu-id="3a324-297">In a data region such as a table, you can initially hide detail rows based on the value in an expression.</span></span>  

-   <span data-ttu-id="3a324-298">當用於群組詳細資料列的初始可見性時，下列運算式會顯示 `PctQuota` 欄位超出 90% 之所有銷售的詳細資料列：</span><span class="sxs-lookup"><span data-stu-id="3a324-298">The following expression, when used for initial visibility of detail rows in a group, shows the detail rows for all sales exceeding 90 percent in the `PctQuota` field:</span></span>  

```  
=Iif(Fields!PctQuota.Value>.9, False, True)  
```  

-   <span data-ttu-id="3a324-299">下列運算式設定在資料表的 Hidden 屬性中時，只有當資料表有 12 個以上的資料列時，才會顯示該資料表：</span><span class="sxs-lookup"><span data-stu-id="3a324-299">The following expression, when set in the Hidden property of a table, shows the table only if it has more than 12 rows:</span></span>  

```  
=IIF(CountRows()>12,false,true)  
```  

-   <span data-ttu-id="3a324-300">下列運算式是在資料行的屬性中設定時 `Hidden` ，只有在從資料來源中取出資料之後，才會顯示該欄位存在於報表資料集中的資料行：</span><span class="sxs-lookup"><span data-stu-id="3a324-300">The following expression, when set in the `Hidden` property of a column, shows the column only if the field exists in the report dataset after the data is retrieved from the data source:</span></span>  

```  
=IIF(Fields!Column_1.IsMissing, true, false)  
```  

###  <a name="urls"></a><a name="Hyperlinks"></a><span data-ttu-id="3a324-301">Url</span><span class="sxs-lookup"><span data-stu-id="3a324-301">URLs</span></span>  
<span data-ttu-id="3a324-302">您可以使用報表資料來自訂 URL，也可以條件式地控制是否要加入 URL 做為文字方塊的動作。</span><span class="sxs-lookup"><span data-stu-id="3a324-302">You can customize URLs by using report data and also conditionally control whether URLs are added as an action for a text box.</span></span>  

-   <span data-ttu-id="3a324-303">當下列運算式做為文字方塊的動作時，會產生自訂的 URL，將 `EmployeeID` 資料集欄位指定為 URL 參數。</span><span class="sxs-lookup"><span data-stu-id="3a324-303">The following expression, when used as an action on a text box, generates a customized URL that specifies the dataset field `EmployeeID` as a URL parameter.</span></span>  

```  
="http://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
```  

<span data-ttu-id="3a324-304">如需詳細資訊，請參閱[將超連結新增至 URL &#40;報表產生器及 SSRS&#41;](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-304">For more information, see [Add a Hyperlink to a URL &#40;Report Builder and SSRS&#41;](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md).</span></span>  

-   <span data-ttu-id="3a324-305">下列運算式會條件式地控制是否要在文字方塊中加入 URL。</span><span class="sxs-lookup"><span data-stu-id="3a324-305">The following expression conditionally controls whether to add a URL in a text box.</span></span> <span data-ttu-id="3a324-306">這個運算式會根據名為 `IncludeURLs` 的參數，讓使用者決定是否要在報表中包含作用中的 URL。</span><span class="sxs-lookup"><span data-stu-id="3a324-306">This expression depends on a parameter named `IncludeURLs` that allows a user to decide whether to include active URLs in a report.</span></span> <span data-ttu-id="3a324-307">這個運算式會設定為文字方塊的動作。</span><span class="sxs-lookup"><span data-stu-id="3a324-307">This expression is set as an action on a text box.</span></span> <span data-ttu-id="3a324-308">透過將參數設定為 False，然後再檢視報表，您可以將報表匯出為沒有超連結的 Microsoft Excel 格式。</span><span class="sxs-lookup"><span data-stu-id="3a324-308">By setting the parameter to False and then viewing the report, you can export the report Microsoft Excel without hyperlinks.</span></span>  

```  
=IIF(Parameters!IncludeURLs.Value,"http://adventure-works.com/productcatalog",Nothing)  
```  

##  <a name="report-data"></a><a name="ReportData"></a><span data-ttu-id="3a324-309">報表資料</span><span class="sxs-lookup"><span data-stu-id="3a324-309">Report Data</span></span>  
<span data-ttu-id="3a324-310">您可以使用運算式來操作用於報表中的資料。</span><span class="sxs-lookup"><span data-stu-id="3a324-310">Expressions can be used to manipulate the data that is used in the report.</span></span> <span data-ttu-id="3a324-311">您可以參考參數和其他的報表資訊。</span><span class="sxs-lookup"><span data-stu-id="3a324-311">You can refer to parameters and other report information.</span></span> <span data-ttu-id="3a324-312">您甚至可以變更用來擷取報表資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="3a324-312">You can even change the query that is used to retrieve data for the report.</span></span>  

###  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="3a324-313">參數</span><span class="sxs-lookup"><span data-stu-id="3a324-313">Parameters</span></span>  
<span data-ttu-id="3a324-314">您可以在參數中使用運算式，以更改參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="3a324-314">You can use expressions in a parameter to vary the default value for the parameter.</span></span> <span data-ttu-id="3a324-315">例如，您可以利用參數，根據用來執行報表的使用者識別碼來篩選特定使用者的資料。</span><span class="sxs-lookup"><span data-stu-id="3a324-315">For example, you can use a parameter to filter data to a particular user based on the user ID that is used to run the report.</span></span>  

-   <span data-ttu-id="3a324-316">使用下列運算式做為參數的預設值時，收集執行報表之人員的使用者識別碼：</span><span class="sxs-lookup"><span data-stu-id="3a324-316">The following expression, when used as the default value for a parameter, collects the user ID of the person running the report:</span></span>  

```  
=User!UserID  
```  

-   <span data-ttu-id="3a324-317">若要在報表的查詢參數、篩選運算式、文字方塊或其他區域中參考參數，請使用 `Parameters` 全域集合。</span><span class="sxs-lookup"><span data-stu-id="3a324-317">To refer to a parameter in a query parameter, filter expression, text box, or other area of the report, use the `Parameters` global collection.</span></span> <span data-ttu-id="3a324-318">這個範例假設參數的名稱是 *Department*：</span><span class="sxs-lookup"><span data-stu-id="3a324-318">This example assumes that the parameter is named *Department*:</span></span>  

```  
=Parameters!Department.Value  
```  

-   <span data-ttu-id="3a324-319">您可以在報表中建立參數，但將其設為隱藏。</span><span class="sxs-lookup"><span data-stu-id="3a324-319">Parameters can be created in a report but set to hidden.</span></span> <span data-ttu-id="3a324-320">當報表在報表伺服器上執行時，工具列中不會顯示參數，而報表讀取器也無法變更其預設值。</span><span class="sxs-lookup"><span data-stu-id="3a324-320">When the report runs on the report server, the parameter does not appear in the toolbar and the report reader cannot change the default value.</span></span> <span data-ttu-id="3a324-321">您可以使用設為預設值的隱藏參數做為自訂常數。</span><span class="sxs-lookup"><span data-stu-id="3a324-321">You can use a hidden parameter set to a default value as custom constant.</span></span> <span data-ttu-id="3a324-322">您可以在任何運算式中使用此值，欄位運算式也在內。</span><span class="sxs-lookup"><span data-stu-id="3a324-322">You can use this value in any expression, including a field expression.</span></span> <span data-ttu-id="3a324-323">下列運算式會識別由名為 *ParameterField*之參數的預設參數值所指定的欄位：</span><span class="sxs-lookup"><span data-stu-id="3a324-323">The following expression identifies the field specified by the default parameter value for the parameter named *ParameterField*:</span></span>  

```  
=Fields(Parameters!ParameterField.Value).Value  
```  

## <a name="custom-code"></a><a name="CustomCode"></a><span data-ttu-id="3a324-324">自訂程式碼</span><span class="sxs-lookup"><span data-stu-id="3a324-324">Custom Code</span></span>

<span data-ttu-id="3a324-325">您可以在報表中使用自訂程式碼，</span><span class="sxs-lookup"><span data-stu-id="3a324-325">You can use custom code in a report.</span></span> <span data-ttu-id="3a324-326">自訂程式碼會內嵌在報表中，或是儲存在用於報表的自訂組件中。</span><span class="sxs-lookup"><span data-stu-id="3a324-326">Custom code is either embedded in a report or stored in a custom assembly which is used in the report.</span></span> <span data-ttu-id="3a324-327">如需自訂程式碼的詳細資訊，請參閱[報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-327">For more information about custom code, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  

### <a name="using-group-variables-for-custom-aggregation"></a><span data-ttu-id="3a324-328">使用群組變數進行自訂彙總</span><span class="sxs-lookup"><span data-stu-id="3a324-328">Using Group Variables for Custom Aggregation</span></span>

<span data-ttu-id="3a324-329">您可以初始化特定群組範圍本機之群組變數的值，然後在運算式中加入該變數的參考。</span><span class="sxs-lookup"><span data-stu-id="3a324-329">You can initialize the value for a group variable that is local to a particular group scope and then include a reference to that variable in expressions.</span></span> <span data-ttu-id="3a324-330">搭配自訂程式碼使用群組變數的其中一種方式是實作自訂彙總。</span><span class="sxs-lookup"><span data-stu-id="3a324-330">One of the ways that you can use a group variable with custom code is to implement a custom aggregate.</span></span> <span data-ttu-id="3a324-331">如需詳細資訊，請參閱 [在 Reporting Services 2008 中使用群組變數進行自訂彙總](https://go.microsoft.com/fwlink/?LinkId=128714)。</span><span class="sxs-lookup"><span data-stu-id="3a324-331">For more information, see [Using Group Variables in Reporting Services 2008 for Custom Aggregation](https://go.microsoft.com/fwlink/?LinkId=128714).</span></span>  

<span data-ttu-id="3a324-332">如需變數的詳細資訊，請參閱 [報表和群組變數集合參考 &#40;報表產生器及 SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="3a324-332">For more information about variables, see [Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md).</span></span>  

## <a name="suppressing-null-or-zero-values-at-run-time"></a><span data-ttu-id="3a324-333">在執行階段隱藏 Null 或零值</span><span class="sxs-lookup"><span data-stu-id="3a324-333">Suppressing Null or Zero Values at Run Time</span></span>

<span data-ttu-id="3a324-334">運算式中有些值可能會在報表處理時評估為 Null 或未定義。</span><span class="sxs-lookup"><span data-stu-id="3a324-334">Some values in an expression can evaluate to null or undefined at report processing time.</span></span> <span data-ttu-id="3a324-335">這樣可能會造成執行階段錯誤，導致文字方塊中顯示 **#Error** ，而不是評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="3a324-335">This can create run-time errors that result in **#Error** displaying in the text box instead of the evaluated expression.</span></span> <span data-ttu-id="3a324-336">`IIF` 函數對於這種行為特別敏感，因為不像 If-Then-Else 陳述式，`IIF` 陳述式的每部分都會先進行評估 (包括函數呼叫)，才會傳遞至測試 `true` 或 `false` 的常式。</span><span class="sxs-lookup"><span data-stu-id="3a324-336">The `IIF` function is particularly sensitive to this behavior because, unlike an If-Then-Else statement, each part of the `IIF` statement is evaluated (including function calls) before being passed to the routine that tests for `true` or `false`.</span></span> <span data-ttu-id="3a324-337">如果 `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` 為 NOTHING， **陳述式會在轉譯的報表中產生** #Error `Fields!Sales.Value` 。</span><span class="sxs-lookup"><span data-stu-id="3a324-337">The statement `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` generates **#Error** in the rendered report if `Fields!Sales.Value` is NOTHING.</span></span>  

<span data-ttu-id="3a324-338">若要避免此種狀況，請使用下列其中一種策略：</span><span class="sxs-lookup"><span data-stu-id="3a324-338">To avoid this condition, use one of the following strategies:</span></span>  

-   <span data-ttu-id="3a324-339">如果欄位 B 的值為 0 或未定義，則將分子設為 0，分母設為 1；否則將分子設為欄位 A 的值，分母設為欄位 B 的值。</span><span class="sxs-lookup"><span data-stu-id="3a324-339">Set the numerator to 0 and the denominator to 1 if the value for field B is 0 or undefined; otherwise, set the numerator to the value for field A and the denominator to the value for field B.</span></span>  

```  
=IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
```  

-   <span data-ttu-id="3a324-340">使用自訂程式碼函數來傳回運算式的值。</span><span class="sxs-lookup"><span data-stu-id="3a324-340">Use a custom code function to return the value for the expression.</span></span> <span data-ttu-id="3a324-341">下列範例會傳回目前值和上一個值之間的百分比差異。</span><span class="sxs-lookup"><span data-stu-id="3a324-341">The following example returns the percentage difference between a current value and a previous value.</span></span> <span data-ttu-id="3a324-342">這可以用來計算任兩個連續值之間的差異，也可以處理第一個比較 (沒有上一個值) 的邊緣案例，以及上一個或目前的值為 `null` (在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 `Nothing`) 的案例。</span><span class="sxs-lookup"><span data-stu-id="3a324-342">This can be used to calculate the difference between any two successive values and it handles the edge case of the first comparison (when there is no previous value) and cases whether either the previous value or the current value is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span>  

```  
Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
     If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
          Return Nothing  
     Else if PreviousValue = 0 OR CurrentValue = 0 Then  
          Return Nothing  
     Else
          Return (CurrentValue - PreviousValue) / CurrentValue  
     End If  
End Function  
```  

<span data-ttu-id="3a324-343">下列運算式顯示如何針對 "ColumnGroupByYear" 容器 (群組或資料區域)，從文字方塊呼叫此自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="3a324-343">The following expression shows how to call this custom code from a text box, for the "ColumnGroupByYear" container (group or data region).</span></span>  

```  
=Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
```  

<span data-ttu-id="3a324-344">這有助於避免執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3a324-344">This helps to avoid run-time exceptions.</span></span> <span data-ttu-id="3a324-345">您現在可以在文字方塊的 `Color` 屬性中使用類似 `=IIF(Me.Value < 0, "red", "black")` 的運算式，以便根據值大於或小於 0，有條件地顯示文字。</span><span class="sxs-lookup"><span data-stu-id="3a324-345">You can now use an expression like `=IIF(Me.Value < 0, "red", "black")` in the `Color` property of the text box to conditionally the display text based on whether the values are greater than or less than 0.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3a324-346">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a324-346">See Also</span></span>

- [<span data-ttu-id="3a324-347">篩選方程式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-347">Filter Equation Examples &#40;Report Builder and SSRS&#41;</span></span>](filter-equation-examples-report-builder-and-ssrs.md)
- [<span data-ttu-id="3a324-348">群組運算式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-348">Group Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)
- [<span data-ttu-id="3a324-349">報表中的運算式用法 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-349">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](expression-uses-in-reports-report-builder-and-ssrs.md)
- [<span data-ttu-id="3a324-350">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-350">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)
- [<span data-ttu-id="3a324-351">常用的篩選 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3a324-351">Commonly Used Filters &#40;Report Builder and SSRS&#41;</span></span>](commonly-used-filters-report-builder-and-ssrs.md)