---
title: 報表產生器中運算式的自訂程式碼及組件參考 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- items [Reporting Services], expressions
- data [Reporting Services], expressions
- expressions [Reporting Services], about expressions
- expressions [Reporting Services]
- SSRS, expressions
- formulas [Reporting Services]
- data manipulation [Reporting Services]
- SQL Server Reporting Services, expressions
ms.assetid: ae8a0166-2ccc-45f4-8d28-c150da7b73de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0f895d1ecc569092dfbae22b514d3470e020b94d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704953"
---
# <a name="custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs"></a><span data-ttu-id="1e85e-102">報表產生器中運算式的自訂程式碼及組件參考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="1e85e-102">Custom Code and Assembly References in Expressions in Report Designer (SSRS)</span></span>
  <span data-ttu-id="1e85e-103">您可以加入內嵌於報表之自訂程式碼的參考，或是建置並儲存至電腦以及部署至報表伺服器之自訂組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1e85e-103">You can add references to custom code embedded in a report or to custom assemblies that you build and save to your computer and deploy to the report server.</span></span> <span data-ttu-id="1e85e-104">請將內嵌程式碼用在自訂常數、複雜函數或在單一報表內重複使用的函數上。</span><span class="sxs-lookup"><span data-stu-id="1e85e-104">Use embedded code for custom constants, complex functions or functions that are used multiple times in a single report.</span></span> <span data-ttu-id="1e85e-105">請使用自訂程式碼組件，將程式碼維護在單一位置並共用程式碼，讓多份報表使用。</span><span class="sxs-lookup"><span data-stu-id="1e85e-105">Use custom code assemblies to maintain code in a single place and share it for use by multiple reports.</span></span> <span data-ttu-id="1e85e-106">自訂程式碼可能會包含新的自訂常數、變數、函數或副程式。</span><span class="sxs-lookup"><span data-stu-id="1e85e-106">Custom code can include new custom constants, variables, functions, or subroutines.</span></span> <span data-ttu-id="1e85e-107">您可以包含內建集合 (例如 Parameters 集合) 的唯讀參考，</span><span class="sxs-lookup"><span data-stu-id="1e85e-107">You can include read-only references to built-in collections such as the Parameters collection.</span></span> <span data-ttu-id="1e85e-108">但是不能將報表資料值集傳遞至自訂函數 (尤其是不支援自訂彙總)。</span><span class="sxs-lookup"><span data-stu-id="1e85e-108">However, you cannot pass sets of report data values to custom functions; specifically, custom aggregates are not supported.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1e85e-109">對於時間緊迫的計算 (在執行階段時會評估一次，而您想在整個報表處理期間維持相同的值)，則請考慮是否要使用報表變數或群組變數。</span><span class="sxs-lookup"><span data-stu-id="1e85e-109">For time-sensitive calculations that are evaluated once at run-time and that you want to remain the same value throughout report processing, consider whether to use a report variable or group variable.</span></span> <span data-ttu-id="1e85e-110">如需詳細資訊，請參閱[報表和群組變數集合參考 &#40;報表產生器及 SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="1e85e-110">For more information, see [Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md).</span></span>  
  
 <span data-ttu-id="1e85e-111">報表設計師是將自訂程式碼加入至報表的慣用撰寫環境。</span><span class="sxs-lookup"><span data-stu-id="1e85e-111">Report Designer is the preferred authoring environment to use to add custom code to a report.</span></span> <span data-ttu-id="1e85e-112">報表產生器支援處理具有有效運算式的報表，或是包含報表伺服器上自訂組件之參考的報表。</span><span class="sxs-lookup"><span data-stu-id="1e85e-112">Report Builder supports processing reports that have valid expressions, or that include references to custom assemblies on a report server.</span></span> <span data-ttu-id="1e85e-113">報表產生器不會提供加入自訂組件之參考的方式。</span><span class="sxs-lookup"><span data-stu-id="1e85e-113">Report Builder does not provide a way to add a reference to a custom assembly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e85e-114">請注意，在升級報表伺服器期間，相依於自訂組件的報表可能需要進行其他步驟，才能完成升級。</span><span class="sxs-lookup"><span data-stu-id="1e85e-114">Be aware that during an upgrade of a report server, reports that depend on custom assemblies might require additional steps to complete the upgrade.</span></span> <span data-ttu-id="1e85e-115">如需詳細資訊，請參閱＜ [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1e85e-115">For more information, see [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="working-with-custom-code-in-report-builder"></a><a name="RB3"></a> <span data-ttu-id="1e85e-116">在報表產生器中使用自訂程式碼</span><span class="sxs-lookup"><span data-stu-id="1e85e-116">Working with Custom Code in Report Builder</span></span>  
 <span data-ttu-id="1e85e-117">在報表產生器中，您可以從報表伺服器開啟包含自訂組件之參考的報表。</span><span class="sxs-lookup"><span data-stu-id="1e85e-117">In Report Builder, you can open a report from a report server that includes references to custom assemblies.</span></span> <span data-ttu-id="1e85e-118">例如，您可以編輯在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中使用報表設計師所建立和部署的報表。</span><span class="sxs-lookup"><span data-stu-id="1e85e-118">For example, you can edit reports that are created and deployed by using Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="1e85e-119">自訂組件必須部署至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="1e85e-119">The custom assemblies must be deployed to the report server.</span></span>  
  
 <span data-ttu-id="1e85e-120">您無法執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1e85e-120">You cannot do the following:</span></span>  
  
1.  <span data-ttu-id="1e85e-121">將參考或類別成員執行個體加入至報表。</span><span class="sxs-lookup"><span data-stu-id="1e85e-121">Add references or class member instances to a report.</span></span>  
  
2.  <span data-ttu-id="1e85e-122">在本機模式中預覽含有自訂組件之參考的報表。</span><span class="sxs-lookup"><span data-stu-id="1e85e-122">Preview a report with references to custom assemblies in local mode.</span></span>  
  
##  <a name="including-references-to-commonly-used-functions"></a><a name="Common"></a><span data-ttu-id="1e85e-123">包含常用函數的參考</span><span class="sxs-lookup"><span data-stu-id="1e85e-123">Including References to Commonly Used Functions</span></span>  
 <span data-ttu-id="1e85e-124">**[運算式]** 對話方塊可用來檢視 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]一般內建函數的分類清單。</span><span class="sxs-lookup"><span data-stu-id="1e85e-124">Use the **Expression** dialog box to view a categorized list of common functions built-in to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="1e85e-125">當您展開 **[一般函數]** 並按一下類別目錄時， **[項目]** 窗格就會顯示您包含在運算式中的函數清單。</span><span class="sxs-lookup"><span data-stu-id="1e85e-125">When you expand **Common Functions** and click a category, the **Item** pane displays the list of functions that you include in an expression.</span></span> <span data-ttu-id="1e85e-126">一般函數包含 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Math> 和命名空間中的類別 <xref:System.Convert> 以及 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 執行時間程式庫函數。</span><span class="sxs-lookup"><span data-stu-id="1e85e-126">The common functions include classes from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Math> and <xref:System.Convert> namespaces and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library functions.</span></span> <span data-ttu-id="1e85e-127">為了方便起見，您可以在 **[運算式]** 對話方塊中檢視最常用的函數，這些函數會依類別目錄列出：文字、日期和時間、數學、檢閱、程式流程、彙總、財務、轉換和其他。</span><span class="sxs-lookup"><span data-stu-id="1e85e-127">For convenience, you can view the most commonly used functions in the **Expression** dialog box, where they are listed by category: Text, Date and Time, Math, Inspection, Program Flow, Aggregate, Financial, Conversion, and Miscellaneous.</span></span> <span data-ttu-id="1e85e-128">較不常用的函數則不會顯示在清單中，但仍可用於運算式。</span><span class="sxs-lookup"><span data-stu-id="1e85e-128">Less commonly used functions do not appear in the list but can still be used in an expression.</span></span>  
  
 <span data-ttu-id="1e85e-129">若要使用內建函數，請在 [項目] 窗格中的函數名稱上按兩下。</span><span class="sxs-lookup"><span data-stu-id="1e85e-129">To use a built-in function, double-click the function name in the Item pane.</span></span> <span data-ttu-id="1e85e-130">函數的描述會顯示在 [描述] 窗格中，函數呼叫的範例則顯示在 [範例] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="1e85e-130">A description of the function appears in the Description pane and an example of the function call appears in the Example pane.</span></span> <span data-ttu-id="1e85e-131">在 [程式碼] 窗格中，當您輸入函式名稱，並在後面加上左括弧\*\* (\*\* 時，IntelliSense 會協助顯示函數呼叫的每個有效語法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-131">In the code pane, when you type the function name followed by a left parenthesis **(**, the IntelliSense help displays each valid syntax for the function call.</span></span> <span data-ttu-id="1e85e-132">例如，若要計算資料表中名為 `Quantity` 欄位的最大值，請將簡單運算式 `=Max(` 加入至 [程式碼] 窗格，然後使用智慧標籤來檢視該函數呼叫的所有有效語法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-132">For example, to calculate the maximum value for a field named `Quantity` in a table, add the simple expression `=Max(` to the Code pane, and then use the smart tags to view all possible valid syntaxes for the function call.</span></span> <span data-ttu-id="1e85e-133">若要完成此範例，請輸入 `=Max(Fields!Quantity.Value)`。</span><span class="sxs-lookup"><span data-stu-id="1e85e-133">To complete this example, type `=Max(Fields!Quantity.Value)`.</span></span>  
  
 <span data-ttu-id="1e85e-134">如需每個函數的詳細資訊，請參閱 <xref:System.Math>、 <xref:System.Convert>以及 MSDN 上的 [Visual Basic 執行階段程式庫成員](https://go.microsoft.com/fwlink/?LinkId=198941) 。</span><span class="sxs-lookup"><span data-stu-id="1e85e-134">For more information about each function, see <xref:System.Math>, <xref:System.Convert>, and [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) on MSDN.</span></span>  
  
##  <a name="including-references-to-less-commonly-used-functions"></a><a name="NotCommon"></a><span data-ttu-id="1e85e-135">包含較少使用函數的參考</span><span class="sxs-lookup"><span data-stu-id="1e85e-135">Including References to Less Commonly Used Functions</span></span>  
 <span data-ttu-id="1e85e-136">若要包含其他較少使用之 CLR 命名空間的參考，您必須使用完整的參考，例如， <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="1e85e-136">To include a reference to other less commonly used CLR namespaces, you must use a fully qualified reference, for example, <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="1e85e-137">在這些較少使用函數的 **[運算式]** 對話方塊的程式碼窗格中，不支援 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="1e85e-137">IntelliSense is not supported in the code pane of the **Expression** dialog box for these less commonly used functions.</span></span>  
  
 <span data-ttu-id="1e85e-138">如需詳細資訊，請參閱 MSDN 上的 [Visual Basic 執行階段程式庫成員](https://go.microsoft.com/fwlink/?LinkId=198941) 。</span><span class="sxs-lookup"><span data-stu-id="1e85e-138">For more information, see [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) on MSDN.</span></span>  
  
##  <a name="including-references-to-external-assemblies"></a><a name="External"></a> <span data-ttu-id="1e85e-139">包含外部組件的參考</span><span class="sxs-lookup"><span data-stu-id="1e85e-139">Including References to External Assemblies</span></span>  
 <span data-ttu-id="1e85e-140">若要包含外部組件中類別的參考，您必須為報表處理器識別組件。</span><span class="sxs-lookup"><span data-stu-id="1e85e-140">To include a reference to a class in an external assembly, you must identify the assembly for the report processor.</span></span> <span data-ttu-id="1e85e-141">請使用 **[報表屬性]** 對話方塊的 **[參考]** 頁面來指定報表中要加入之組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="1e85e-141">Use the **References** page of the **Report Properties** dialog box to specify the fully qualified name of the assembly to add to the report.</span></span> <span data-ttu-id="1e85e-142">您必須在運算式中使用組件中類別的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="1e85e-142">In your expression, you must use the fully qualified name for the class in the assembly.</span></span> <span data-ttu-id="1e85e-143">外部組件中的類別並不會顯示在 **[運算式]** 對話方塊中，您必須提供正確的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="1e85e-143">Classes in an external assembly do not appear in the **Expression** dialog box; you must provide the correct name for the class.</span></span> <span data-ttu-id="1e85e-144">完整名稱包含命名空間、類別名稱和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="1e85e-144">A fully qualified name includes the namespace, the class name, and the member name.</span></span>  
  
##  <a name="including-embedded-code"></a><a name="Embedded"></a> <span data-ttu-id="1e85e-145">加入內嵌程式碼</span><span class="sxs-lookup"><span data-stu-id="1e85e-145">Including Embedded Code</span></span>  
 <span data-ttu-id="1e85e-146">若要將內嵌程式碼加入至報表，請使用 **[報表屬性]** 對話方塊的 [程式碼] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1e85e-146">To add embedded code to a report, use the Code tab of the **Report Properties** dialog box.</span></span> <span data-ttu-id="1e85e-147">您建立的程式碼區塊可以包含多個方法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-147">The code block you create can contain multiple methods.</span></span> <span data-ttu-id="1e85e-148">內嵌程式碼中的方法必須以撰寫 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ，而且必須以實例為基礎。</span><span class="sxs-lookup"><span data-stu-id="1e85e-148">Methods in embedded code must be written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] and must be instance-based.</span></span> <span data-ttu-id="1e85e-149">報表處理器會自動加入 System.Convert 和 System.Math 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="1e85e-149">The report processor automatically adds references for the System.Convert and System.Math namespaces.</span></span> <span data-ttu-id="1e85e-150">請使用 **[報表屬性]** 對話方塊的 **[參考]** 頁面來加入其他的組件參考。</span><span class="sxs-lookup"><span data-stu-id="1e85e-150">Use the **References** page of the **Report Properties** dialog box to add additional assembly references.</span></span> <span data-ttu-id="1e85e-151">如需詳細資訊，請參閱 [將組件參考加入至報表 &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1e85e-151">For more information, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md).</span></span>  
  
 <span data-ttu-id="1e85e-152">內嵌程式碼裡的方法，可透過全域定義的 `Code` 成員使用。</span><span class="sxs-lookup"><span data-stu-id="1e85e-152">Methods in embedded code are available through a globally defined `Code` member.</span></span> <span data-ttu-id="1e85e-153">您可藉由參考 `Code` 成員與方法名稱，來存取這些方法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-153">You access these by referring to the `Code` member and the method name.</span></span> <span data-ttu-id="1e85e-154">下列範例會呼叫 `ToUSD` 方法，這個方法會將 `StandardCost` 欄位的值轉換成美金值：</span><span class="sxs-lookup"><span data-stu-id="1e85e-154">The following example calls the method `ToUSD`, which converts the value in the `StandardCost` field to a dollar value:</span></span>  
  
```  
=Code.ToUSD(Fields!StandardCost.Value)  
```  
  
 <span data-ttu-id="1e85e-155">若要參考自訂程式碼中的內建集合，請加入內建 `Report` 物件的參考：</span><span class="sxs-lookup"><span data-stu-id="1e85e-155">To reference built-in collections in your custom code, include a reference to the built-in `Report` object:</span></span>  
  
```  
=Report.Parameters!Param1.Value  
```  
  
 <span data-ttu-id="1e85e-156">下列範例顯示定義部分自訂常數及變數的方法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-156">The following examples show how to define some custom constants and variables.</span></span>  
  
```  
Public Const MyNote = "Authored by Bob"  
Public Const NCopies As Int32 = 2  
Public Dim  MyVersion As String = "123.456"  
Public Dim MyDoubleVersion As Double = 123.456  
```  
  
 <span data-ttu-id="1e85e-157">雖然自訂常數不會出現在 **[運算式]** 對話方塊的 **[常數]** 類別目錄中 (這個類別目錄只會顯示內建常數)，但是您可以從任何運算式加入自訂常數的參考，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1e85e-157">Although custom constants do not appear in the **Constants** category in the **Expression** dialog box (which only displays built-in constants), you can add references to them from any expression, as shown in the following examples.</span></span> <span data-ttu-id="1e85e-158">在運算式中，會將自訂常數視為 `Variant`。</span><span class="sxs-lookup"><span data-stu-id="1e85e-158">In an expression, a custom constant is treated as a `Variant`.</span></span>  
  
```  
=Code.MyNote  
=Code.NCopies  
=Code.MyVersion  
=Code.MyDoubleVersion  
```  
  
 <span data-ttu-id="1e85e-159">下列範例包含 `FixSpelling` 函數的程式碼參考和程式碼實作，這個函數會將 `"Bicycle"` 欄位中所有出現的 "Bike" 文字取代成 `SubCategory` 文字。</span><span class="sxs-lookup"><span data-stu-id="1e85e-159">The following example includes both the code reference and the code implementation of the function `FixSpelling`, which substitutes the text `"Bicycle"` for all occurrences of the text "Bike" in the `SubCategory` field.</span></span>  
  
 `=Code.FixSpelling(Fields!SubCategory.Value)`  
  
 <span data-ttu-id="1e85e-160">將下列程式碼內嵌在定義程式碼區塊後，會顯示 `FixSpelling` 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="1e85e-160">The following code, when embedded in a report definition code block, shows an implementation of the `FixSpelling` method.</span></span> <span data-ttu-id="1e85e-161">這個範例會示範如何使用類別的完整參考 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] `StringBuilder` 。</span><span class="sxs-lookup"><span data-stu-id="1e85e-161">This example shows you how to use a fully qualified reference to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] `StringBuilder` class.</span></span>  
  
```vb  
Public Function FixSpelling(ByVal s As String) As String  
   Dim strBuilder As New System.Text.StringBuilder(s)  
   If s.Contains("Bike") Then  
      strBuilder.Replace("Bike", "Bicycle")  
      Return strBuilder.ToString()  
      Else : Return s  
   End If  
End Function  
```  
  
 <span data-ttu-id="1e85e-162">如需內建物件集合和初始化的詳細資訊，請參閱[內建的全域和使用者參考 &#40;報表產生器及 SSRS&#41;](built-in-collections-built-in-globals-and-users-references-report-builder.md) 和[初始化自訂組件物件](../custom-assemblies/initializing-custom-assembly-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="1e85e-162">For more information about built-in object collections and initialization, see [Built-in Globals and Users References &#40;Report Builder and SSRS&#41;](built-in-collections-built-in-globals-and-users-references-report-builder.md) and [Initializing Custom Assembly Objects](../custom-assemblies/initializing-custom-assembly-objects.md).</span></span>  
  
##  <a name="including-references-to-parameters-from-code"></a><a name="Parameters"></a> <span data-ttu-id="1e85e-163">加入程式碼中參數的參考</span><span class="sxs-lookup"><span data-stu-id="1e85e-163">Including References to Parameters from Code</span></span>  
 <span data-ttu-id="1e85e-164">您可以透過報表定義之程式碼區塊內或您所提供之自訂組件內的自訂程式碼，參考全域參數集合。</span><span class="sxs-lookup"><span data-stu-id="1e85e-164">You can reference the global parameters collection via custom code in a Code block of the report definition or in a custom assembly that you provide.</span></span> <span data-ttu-id="1e85e-165">此參數集合是唯讀的，而且沒有任何公用 Iterator。</span><span class="sxs-lookup"><span data-stu-id="1e85e-165">The parameters collection is read-only and has no public iterators.</span></span> <span data-ttu-id="1e85e-166">您不能使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `For Each` 結構來逐步執行集合。</span><span class="sxs-lookup"><span data-stu-id="1e85e-166">You cannot use a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `For Each` construct to step through the collection.</span></span> <span data-ttu-id="1e85e-167">您必須先知道報表定義中所定義的參數名稱，才可以在程式碼中參考它。</span><span class="sxs-lookup"><span data-stu-id="1e85e-167">You need to know the name of the parameter defined in the report definition before you can reference it in your code.</span></span> <span data-ttu-id="1e85e-168">但是，您可以逐一查看多重值參數的所有值。</span><span class="sxs-lookup"><span data-stu-id="1e85e-168">You can, however, iterate through all the values of a multivalue parameter.</span></span>  
  
 <span data-ttu-id="1e85e-169">下表包含從自訂程式碼參考內建 `Parameters` 集合的範例：</span><span class="sxs-lookup"><span data-stu-id="1e85e-169">The following table includes examples of referencing the built-in collection `Parameters` from custom code:</span></span>  
  
|<span data-ttu-id="1e85e-170">描述</span><span class="sxs-lookup"><span data-stu-id="1e85e-170">Description</span></span>|<span data-ttu-id="1e85e-171">運算式中的參考</span><span class="sxs-lookup"><span data-stu-id="1e85e-171">Reference in Expression</span></span>|<span data-ttu-id="1e85e-172">自訂程式碼定義</span><span class="sxs-lookup"><span data-stu-id="1e85e-172">Custom Code definition</span></span>|  
|-----------------|-----------------------------|----------------------------|  
|<span data-ttu-id="1e85e-173">將整個全域參數集合傳遞給自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e85e-173">Passing an entire global parameter collection to custom code.</span></span><br /><br /> <span data-ttu-id="1e85e-174">這個函數會傳回特定報表參數 *MyParameter*的值。</span><span class="sxs-lookup"><span data-stu-id="1e85e-174">This function returns the value of a specific report parameter *MyParameter*.</span></span>|`=Code.DisplayAParameterValue(Parameters)`|`Public Function DisplayAParameterValue(`<br /><br /> `ByVal parameters as Parameters) as Object`<br /><br /> `Return parameters("MyParameter").Value`<br /><br /> `End Function`|  
|<span data-ttu-id="1e85e-175">將個別參數傳遞給自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e85e-175">Passing an individual parameter to custom code.</span></span><br /><br /> <span data-ttu-id="1e85e-176">這個範例會傳回所傳入的參數值。</span><span class="sxs-lookup"><span data-stu-id="1e85e-176">This example returns the value of the parameter passed in.</span></span> <span data-ttu-id="1e85e-177">如果該參數為多重值參數，則傳回字串會是所有值的串連。</span><span class="sxs-lookup"><span data-stu-id="1e85e-177">If the parameter is a multivalue parameter, the return string is a concatenation of all the values.</span></span>|`=Code.ShowParametersValues(Parameters!DayOfTheWeek)`|`Public Function ShowParameterValues(ByVal parameter as Parameter)` <br />  `as String` <br /> `Dim s as String`  <br />  `If parameter.IsMultiValue then` <br />  `s = "Multivalue: "`  <br /> `For i as integer = 0 to parameter.Count-1` <br />  `s = s + CStr(parameter.Value(i)) + " "`  <br />  `Next` <br /> `Else` <br /> `s = "Single value: " + CStr(parameter.Value)` <br /> `End If` <br />  `Return s` <br /> `End Function`|  
  
##  <a name="including-references-to-code-from-custom-assemblies"></a><a name="Custom"></a><span data-ttu-id="1e85e-178">包含自訂群組件之程式碼的參考</span><span class="sxs-lookup"><span data-stu-id="1e85e-178">Including References to Code from Custom Assemblies</span></span>  
 <span data-ttu-id="1e85e-179">若要在報表中使用自訂組件，您必須先建立組件，並設定報表設計師可以使用該組件，在報表中加入對該組件的參考，然後在報表中使用運算式來參考該組件內含的方法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-179">To use custom assemblies in a report, you must first create the assembly, make it available to Report Designer, add a reference to the assembly in the report, and then use an expression in the report to refer to the methods contained in that assembly.</span></span> <span data-ttu-id="1e85e-180">報表部署至報表伺服器時，您也必須將自訂組件部署至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="1e85e-180">When the report is deployed to the report server, you must also deploy the custom assembly to the report server.</span></span>  
  
 <span data-ttu-id="1e85e-181">如需建立自訂組件，並讓 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]可以使用組件的資訊，請參閱 [將自訂組件與報表搭配使用](../custom-assemblies/using-custom-assemblies-with-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="1e85e-181">For information about creating a custom assembly and making it available to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md).</span></span>  
  
 <span data-ttu-id="1e85e-182">若要在運算式中參考自訂程式碼，您必須在組件中呼叫類別的成員。</span><span class="sxs-lookup"><span data-stu-id="1e85e-182">To refer to custom code in an expression, you must call the member of a class within the assembly.</span></span> <span data-ttu-id="1e85e-183">該如何完成，取決於此方法為靜態或以執行個體為基礎。</span><span class="sxs-lookup"><span data-stu-id="1e85e-183">How you do this depends on whether the method is static or instance-based.</span></span> <span data-ttu-id="1e85e-184">報表內的全域都可以使用自訂組件內的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-184">Static methods within a custom assembly are available globally within the report.</span></span> <span data-ttu-id="1e85e-185">您可以藉著指定命名空間、類別和方法名稱，來存取運算式中的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-185">You can access static methods in expressions by specifying the namespace, class, and method name.</span></span> <span data-ttu-id="1e85e-186">下列範例會呼叫方法 `ToGBP` ，將**StandardCost**值的值從美元轉換為英鎊：</span><span class="sxs-lookup"><span data-stu-id="1e85e-186">The following example calls the method `ToGBP`, which converts the value of the **StandardCost** value from dollar to pounds sterling:</span></span>  
  
```  
=CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
```  
  
 <span data-ttu-id="1e85e-187">以執行個體為基礎的方法，可透過全域定義的 `Code` 成員來使用。</span><span class="sxs-lookup"><span data-stu-id="1e85e-187">Instance-based methods are available through a globally defined `Code` member.</span></span> <span data-ttu-id="1e85e-188">您可以藉由參考 `Code` 成員，然後參考執行個體與方法名稱，來存取這些方法。</span><span class="sxs-lookup"><span data-stu-id="1e85e-188">You access these by referring to the `Code` member, followed by the instance and method name.</span></span> <span data-ttu-id="1e85e-189">下列範例會呼叫實例方法 `ToEUR` ，將**StandardCost**的值從美元轉換為歐元：</span><span class="sxs-lookup"><span data-stu-id="1e85e-189">The following example calls the instance method `ToEUR`, which converts the value of **StandardCost** from dollar to euro:</span></span>  
  
```  
=Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="1e85e-190">在 [報表設計師] 中，自訂組件會載入一次，然後在關閉 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]之前，都不會卸載。</span><span class="sxs-lookup"><span data-stu-id="1e85e-190">In Report Designer, a custom assembly is loaded once and is not unloaded until you close [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="1e85e-191">如果您要預覽報表，請變更報表中使用的自訂組件，然後再次預覽報表，在第二次預覽中將不會顯示變更。</span><span class="sxs-lookup"><span data-stu-id="1e85e-191">If you preview a report, make changes to a custom assembly used in the report, and then preview the report again, the changes will not appear in the second preview.</span></span> <span data-ttu-id="1e85e-192">若要重新載入組件，請關閉再重新開啟 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，再預覽報表。</span><span class="sxs-lookup"><span data-stu-id="1e85e-192">To reload the assembly, close and reopen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and then preview the report.</span></span>  
  
 <span data-ttu-id="1e85e-193">如需有關存取程式碼的詳細資訊，請參閱＜ [Accessing Custom Assemblies Through Expressions](../custom-assemblies/accessing-custom-assemblies-through-expressions.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1e85e-193">For more information about accessing your code, see [Accessing Custom Assemblies Through Expressions](../custom-assemblies/accessing-custom-assemblies-through-expressions.md).</span></span>  
  
##  <a name="passing-built-in-collections-into-custom-assemblies"></a><a name="collections"></a> <span data-ttu-id="1e85e-194">將內建集合傳給自訂組件</span><span class="sxs-lookup"><span data-stu-id="1e85e-194">Passing Built-in Collections into Custom Assemblies</span></span>  
 <span data-ttu-id="1e85e-195">若要將內建集合 (例如 *Globals* 或 *Parameters* 集合) 傳給自訂組件處理，必須將程式碼專案中的組件參考加入定義內建集合的組件，並且存取正確的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1e85e-195">If you want to pass built-in collections, such as the *Globals* or *Parameters* collection, into a custom assembly for processing, you must add an assembly reference in your code project to the assembly that defines the built-in collections and access the correct namespace.</span></span> <span data-ttu-id="1e85e-196">根據您是針對在報表伺服器上執行的報表 (伺服器報表) 還是以本機方式在 .NET 應用程式中執行的報表 (本機報表) 開發自訂組件，您需要參考的組件會有所不同。</span><span class="sxs-lookup"><span data-stu-id="1e85e-196">Depending on whether you are developing the custom assembly for a report that is run on a report server (server report) or a report that is run locally in a .NET application (local report), the assembly you need to reference is different.</span></span> <span data-ttu-id="1e85e-197">如需詳細資訊，請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="1e85e-197">See below for details.</span></span>  
  
-   <span data-ttu-id="1e85e-198">**命名空間** ：Microsoft.ReportingServices.ReportProcessing.ReportObjectModel</span><span class="sxs-lookup"><span data-stu-id="1e85e-198">**Namespace:** Microsoft.ReportingServices.ReportProcessing.ReportObjectModel</span></span>  
  
-   <span data-ttu-id="1e85e-199">**組件 (本機報表)** ：Microsoft.ReportingServices.ProcessingObjectModel.dll</span><span class="sxs-lookup"><span data-stu-id="1e85e-199">**Assembly (local report):** Microsoft.ReportingServices.ProcessingObjectModel.dll</span></span>  
  
-   <span data-ttu-id="1e85e-200">**組件 (伺服器報表)** ：Microsoft.ReportViewer.ProcessingObjectModel.dll</span><span class="sxs-lookup"><span data-stu-id="1e85e-200">**Assembly (server report):** Microsoft.ReportViewer.ProcessingObjectModel.dll</span></span>  
  
 <span data-ttu-id="1e85e-201">由於 *Fields* 和 *ReportItems* 集合的內容可能會在執行階段動態變更，因此您不應將這些不同的呼叫內容保留在自訂組件之中 (例如保留在成員變數中)。</span><span class="sxs-lookup"><span data-stu-id="1e85e-201">Since the content of the *Fields* and *ReportItems* collections can change dynamically at runtime, you should not hold onto them across calls into the custom assembly (for example, in a member variable).</span></span> <span data-ttu-id="1e85e-202">此項建議適用於所有的內建集合。</span><span class="sxs-lookup"><span data-stu-id="1e85e-202">The same recommendation applies generally to all built-in collections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e85e-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e85e-203">See Also</span></span>  
 <span data-ttu-id="1e85e-204">[將程式碼新增至 &#40;SSRS&#41;的報表](add-code-to-a-report-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1e85e-204">[Add Code to a Report &#40;SSRS&#41;](add-code-to-a-report-ssrs.md) </span></span>  
 <span data-ttu-id="1e85e-205">[將自訂群組件與報表搭配使用](../custom-assemblies/using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="1e85e-205">[Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) </span></span>  
 <span data-ttu-id="1e85e-206">[將元件參考加入至報表 &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1e85e-206">[Add an Assembly Reference to a Report &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md) </span></span>  
 <span data-ttu-id="1e85e-207">[Reporting Services SSRS &#40;的教學課程&#41;](../reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1e85e-207">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md) </span></span>  
 <span data-ttu-id="1e85e-208">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1e85e-208">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1e85e-209">報表範例 (報表產生器和 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1e85e-209">Report Samples (Report Builder and SSRS)</span></span>](https://go.microsoft.com/fwlink/?LinkId=198283)  
  
  
