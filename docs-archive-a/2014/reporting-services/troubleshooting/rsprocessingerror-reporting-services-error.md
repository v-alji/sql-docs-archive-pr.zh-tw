---
title: rsProcessingError - Reporting Services 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsProcessingError
ms.assetid: 414ee58a-8251-4367-9a8e-10c068d17280
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ca98c5532db080ab1e146e2aaa81e24fcb25579b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598210"
---
# <a name="rsprocessingerror---reporting-services-error"></a><span data-ttu-id="f190a-102">rsProcessingError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="f190a-102">rsProcessingError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="f190a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f190a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f190a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f190a-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="f190a-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f190a-105">Event ID</span></span>|<span data-ttu-id="f190a-106">rsProcessingError</span><span class="sxs-lookup"><span data-stu-id="f190a-106">rsProcessingError</span></span>|  
|<span data-ttu-id="f190a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f190a-107">Event Source</span></span>|<span data-ttu-id="f190a-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources</span><span class="sxs-lookup"><span data-stu-id="f190a-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources</span></span>|  
|<span data-ttu-id="f190a-109">元件</span><span class="sxs-lookup"><span data-stu-id="f190a-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="f190a-110">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f190a-110">Message Text</span></span>|<span data-ttu-id="f190a-111">報表處理時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f190a-111">Errors have occurred in report processing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f190a-112">說明</span><span class="sxs-lookup"><span data-stu-id="f190a-112">Explanation</span></span>  
 <span data-ttu-id="f190a-113">發行、處理、本機預覽、從報表伺服器檢視或建立報表的訂閱時，發生一個或多個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f190a-113">One or more errors were encountered while publishing, processing, previewing locally, viewing from the report server, or creating a subscription for a report.</span></span> <span data-ttu-id="f190a-114">這個錯誤訊息表示偵測到至少一個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f190a-114">This error message indicates at least one error was detected.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="f190a-115">可能的原因</span><span class="sxs-lookup"><span data-stu-id="f190a-115">Possible Causes</span></span>  
 <span data-ttu-id="f190a-116">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="f190a-116">Possible causes include:</span></span>  
  
-   <span data-ttu-id="f190a-117">報表伺服器上發生處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="f190a-117">A processing error occurred on the report server.</span></span>  
  
-   <span data-ttu-id="f190a-118">在預覽報表時，於處理本機報表期間發生處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="f190a-118">A processing error occurred during local report processing when previewing a report.</span></span>  
  
-   <span data-ttu-id="f190a-119">群組運算式經判斷為不正確的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f190a-119">A group expression evaluated to an incorrect data type.</span></span>  
  
-   <span data-ttu-id="f190a-120">篩選定義指定了兩個運算式，而這兩個運算式判斷為無法比較的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f190a-120">A filter definition specified two expressions that evaluated to data types that could not be compared.</span></span>  
  
-   <span data-ttu-id="f190a-121">運算式參考了欄位集合中不存在的欄位。</span><span class="sxs-lookup"><span data-stu-id="f190a-121">An expression referenced a non-existing field in the Fields collection.</span></span>  
  
-   <span data-ttu-id="f190a-122">運算式包含具有無效或衝突範圍的彙總函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f190a-122">An expression included an aggregate function call with an invalid or conflicting scope.</span></span>  
  
-   <span data-ttu-id="f190a-123">運算式參考了報表參數集合中不存在的參數。</span><span class="sxs-lookup"><span data-stu-id="f190a-123">An expression referenced a non-existing parameter in the Report Parameters collection.</span></span>  
  
-   <span data-ttu-id="f190a-124">無法載入不正確部署的自訂組件或 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組件。</span><span class="sxs-lookup"><span data-stu-id="f190a-124">A custom assembly or a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] assembly that was incorrectly deployed failed to load.</span></span>  
  
-   <span data-ttu-id="f190a-125">具有可為 Null 屬性設定為的參數， `False` 在參數中偵測到 null 值。</span><span class="sxs-lookup"><span data-stu-id="f190a-125">A parameter that has the Nullable property set to `False` has detected a null value in the parameter.</span></span>  
  
-   <span data-ttu-id="f190a-126">資料區域之 Hidden 屬性的運算式含有錯誤：物件參考未設定為物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f190a-126">An expression for the Hidden property of a data region contains an error: Object reference not set to an instance of an object.</span></span>  
  
-   <span data-ttu-id="f190a-127">運算式包含無效的函數呼叫或語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="f190a-127">An expression included an invalid function call or syntax error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f190a-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f190a-128">User Action</span></span>  
  
### <a name="finding-more-information"></a><span data-ttu-id="f190a-129">尋找詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f190a-129">Finding More Information</span></span>  
 <span data-ttu-id="f190a-130">執行下列其中一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="f190a-130">Do one or more of the following actions:</span></span>  
  
-   <span data-ttu-id="f190a-131">如果要從報表伺服器檢視報表，或是將報表當做訂閱檢視，請查看錯誤訊息的全文。</span><span class="sxs-lookup"><span data-stu-id="f190a-131">If you are viewing the report from the report server or if you are viewing the report as a subscription, look at the entire text of the error message.</span></span> <span data-ttu-id="f190a-132">全文中會提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="f190a-132">Additional information is provided in the expanded text.</span></span>  
  
-   <span data-ttu-id="f190a-133">如果您正在報表設計師中撰寫報表，並且在預覽或發行報表時看到這個錯誤，[錯誤清單] 視窗中會提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="f190a-133">If you are authoring a report in Report Designer and see this error when you preview or publish the report, additional information is provided in the Error List window.</span></span>  
  
-   <span data-ttu-id="f190a-134">如果您正在「報表設計師預覽」中撰寫報表，請查看錯誤訊息的全文。</span><span class="sxs-lookup"><span data-stu-id="f190a-134">If you are authoring a report in Report Designer Preview, look at the entire text of the error message.</span></span> <span data-ttu-id="f190a-135">全文中會提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="f190a-135">Additional information is provided in the expanded text.</span></span>  
  
-   <span data-ttu-id="f190a-136">如果您在報表伺服器上檢視報表，並以本機管理員身分在報表伺服器上執行，只要以滑鼠右鍵按一下頁面，然後選取 [檢視來源]  ，即可檢視呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="f190a-136">If you are viewing a report on the report server, and if you are running as local administrator on the report server, you can view the call stack if you right-click the page and select **View Source**.</span></span> <span data-ttu-id="f190a-137">呼叫堆疊中會提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="f190a-137">Additional information is provided in the call stack.</span></span>  
  
-   <span data-ttu-id="f190a-138">如果您正以本機管理員的身分在報表伺服器上執行，請搜尋 `ReportProcessingException`的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f190a-138">If you are running as local administrator on the report server, search the log file for `ReportProcessingException`.</span></span> <span data-ttu-id="f190a-139">記錄項目會包含更多資訊。</span><span class="sxs-lookup"><span data-stu-id="f190a-139">Log entries contain more information.</span></span> <span data-ttu-id="f190a-140">報表伺服器記錄檔通常位於 \<*drive*> ： \Program FILES\MICROSOFT SQL Server\MSRS12。MSSQLSERVER\Reporting Services\LogFiles\ ReportServerService__*datetimestamp*記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f190a-140">The report server log file is typically located at \<*drive*>:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__*datetimestamp*.log.</span></span> <span data-ttu-id="f190a-141">如需詳細資訊，請參閱 [Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="f190a-141">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
### <a name="failed-to-load-expression-host-assembly"></a><span data-ttu-id="f190a-142">無法載入運算式主機組件</span><span class="sxs-lookup"><span data-stu-id="f190a-142">Failed to Load Expression Host Assembly</span></span>  
 <span data-ttu-id="f190a-143">自訂組件必須以強式名稱簽署，並設定 AllowPartiallyTrustedCallers 屬性。</span><span class="sxs-lookup"><span data-stu-id="f190a-143">Custom assemblies must have strong name signing and the attribute AllowPartiallyTrustedCallers set.</span></span> <span data-ttu-id="f190a-144">如需相關資訊，請參閱 [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) 及 [Understanding Security Policies](../extensions/secure-development/understanding-security-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="f190a-144">For more information, see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) and [Understanding Security Policies](../extensions/secure-development/understanding-security-policies.md).</span></span>  
  
### <a name="a-built-in-global-name-does-not-exist"></a><span data-ttu-id="f190a-145">內建的全域名稱不存在</span><span class="sxs-lookup"><span data-stu-id="f190a-145">A Built-in Global Name Does Not Exist</span></span>  
 <span data-ttu-id="f190a-146">請檢查運算式中的拼字。</span><span class="sxs-lookup"><span data-stu-id="f190a-146">Check the spelling in expressions.</span></span> <span data-ttu-id="f190a-147">內建的全域、參數和欄位名稱都會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f190a-147">Built-in globals, parameters, and field names are case-sensitive.</span></span> <span data-ttu-id="f190a-148">在導致錯誤發生的運算式中，檢查此名稱是否確實存在報表中，而且它的拼字是否正確。</span><span class="sxs-lookup"><span data-stu-id="f190a-148">In the expression causing the error, check that the name actually exists in the report and that it is spelled correctly.</span></span> <span data-ttu-id="f190a-149">如需詳細資訊，請參閱[運算式中的內建集合 &#40;報表產生器及 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="f190a-149">For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
### <a name="parameter-properties-and-null"></a><span data-ttu-id="f190a-150">參數屬性和 Null</span><span class="sxs-lookup"><span data-stu-id="f190a-150">Parameter Properties and Null</span></span>  
 <span data-ttu-id="f190a-151">多重值參數不可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="f190a-151">A multivalue parameter cannot be Null.</span></span> <span data-ttu-id="f190a-152">如需詳細資訊，請參閱 MSDN 上的 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="f190a-152">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
### <a name="main-report-with-subreport-could-not-be-processed"></a><span data-ttu-id="f190a-153">無法處理含有子報表的主報表</span><span class="sxs-lookup"><span data-stu-id="f190a-153">Main Report with Subreport Could Not Be Processed</span></span>  
 <span data-ttu-id="f190a-154">含有子報表的主報表必須由相同的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表處理器版本處理。</span><span class="sxs-lookup"><span data-stu-id="f190a-154">A report with subreports must be processed by the same version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report processor.</span></span> <span data-ttu-id="f190a-155">將報表升級至目前版本的報表定義結構描述時，主報表和子報表不一定會同時更新。</span><span class="sxs-lookup"><span data-stu-id="f190a-155">When upgrading reports to the current version of the report definition schema, the main report and the subreports may or may not be updated at the same time.</span></span> <span data-ttu-id="f190a-156">如果報表與其子報表之間的版本不相容，就會顯示下列訊息：「無法處理子報表」。</span><span class="sxs-lookup"><span data-stu-id="f190a-156">If the version is not compatible between a report and its subreports, the following message is displayed: "Subreport could not be processed."</span></span>  
  
 <span data-ttu-id="f190a-157">您必須變更主報表或子報表，如此所有報表才能由相同的報表處理器版本處理。</span><span class="sxs-lookup"><span data-stu-id="f190a-157">You must change either the main report or the subreports so that all the reports can be processed by the same version of the report processor.</span></span> <span data-ttu-id="f190a-158">如需為何報表無法升級的資訊，請參閱 [升級報表](../install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="f190a-158">For information about why a report fails to upgrade, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
### <a name="verify-function-calls-are-visual-basic-and-not-sql"></a><span data-ttu-id="f190a-159">確認函數呼叫是 Visual Basic 而不是 SQL</span><span class="sxs-lookup"><span data-stu-id="f190a-159">Verify Function Calls are Visual Basic and Not SQL</span></span>  
 <span data-ttu-id="f190a-160">在關聯式資料庫上，您可以在查詢文字中使用 SQL 函數。</span><span class="sxs-lookup"><span data-stu-id="f190a-160">You can use SQL functions in query text on a relational database.</span></span> <span data-ttu-id="f190a-161">您無法在查詢文字中使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數。</span><span class="sxs-lookup"><span data-stu-id="f190a-161">You cannot use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions in query text.</span></span>  
  
 <span data-ttu-id="f190a-162">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，運算式可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函數、System.Math 或 System.String 函數、完整 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 函數，或是自訂程式碼或自訂組件中提供的自訂函數。</span><span class="sxs-lookup"><span data-stu-id="f190a-162">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], expressions can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions, System.Math or System.String functions, fully qualified [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] functions, or custom functions that you provide in custom code or a custom assembly.</span></span> <span data-ttu-id="f190a-163">您不能在運算式中使用 SQL 函數。</span><span class="sxs-lookup"><span data-stu-id="f190a-163">You cannot use SQL functions in an expression.</span></span>  
  
 <span data-ttu-id="f190a-164">請確認查詢和運算式中的函數呼叫有效。</span><span class="sxs-lookup"><span data-stu-id="f190a-164">Verify that the function calls made in the query and in the expressions are valid.</span></span>  
  
### <a name="cannot-compare-data-types-for-a-filter"></a><span data-ttu-id="f190a-165">無法比較篩選的資料類型</span><span class="sxs-lookup"><span data-stu-id="f190a-165">Cannot Compare Data Types for a Filter</span></span>  
 <span data-ttu-id="f190a-166">在篩選方程式中，定義篩選項目的篩選運算式與篩選值必須屬於相同的資料類型，才能進行比較。</span><span class="sxs-lookup"><span data-stu-id="f190a-166">In a filter equation, the filter expression that defines what to filter on and the filter value must be the same data type in order to be compared.</span></span> <span data-ttu-id="f190a-167">如果您看見下列其中一個錯誤，請修改欄位運算式或篩選值，讓資料類型相符：</span><span class="sxs-lookup"><span data-stu-id="f190a-167">If you see one of the following errors, modify the field expression or the filter value so that the data types match:</span></span>  
  
-   <span data-ttu-id="f190a-168">*\<report item type>* *\<report item name>* 無法執行的處理。</span><span class="sxs-lookup"><span data-stu-id="f190a-168">The processing of *\<report item type>* for the *\<report item name>* cannot be performed.</span></span> <span data-ttu-id="f190a-169">無法比較類型與的 *\<type>* 資料 *\<type>* 。</span><span class="sxs-lookup"><span data-stu-id="f190a-169">Cannot compare data of types *\<type>* and *\<type>*.</span></span> <span data-ttu-id="f190a-170">請檢查所傳回的資料類型 *\<report item name>* 。</span><span class="sxs-lookup"><span data-stu-id="f190a-170">Please check the data type returned by the *\<report item name>*.</span></span>  
  
-   <span data-ttu-id="f190a-171">無法評估 *\<property name>* 。</span><span class="sxs-lookup"><span data-stu-id="f190a-171">Failed to evaluate the *\<property name>*.</span></span>  
  
-   <span data-ttu-id="f190a-172">無法評估 *\<property name>* 。</span><span class="sxs-lookup"><span data-stu-id="f190a-172">Failed to evaluate the *\<property name>*.</span></span> <span data-ttu-id="f190a-173">它會參考具有錯誤的資料集欄位： *\<error string>* 。</span><span class="sxs-lookup"><span data-stu-id="f190a-173">It references a dataset field which has an error: *\<error string>*.</span></span>  
  
 <span data-ttu-id="f190a-174">如需詳細資訊，請參閱 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="f190a-174">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
### <a name="invalid-or-conflicting-scope-specification-in-an-aggregate-function-call"></a><span data-ttu-id="f190a-175">彙總函式呼叫中的無效或衝突範圍規格</span><span class="sxs-lookup"><span data-stu-id="f190a-175">Invalid or Conflicting Scope Specification in an Aggregate Function Call</span></span>  
 <span data-ttu-id="f190a-176">當您在 Tablix 資料格中加入運算式的彙總函式呼叫時，報表處理器就會在該資料格所屬之最內部群組的範圍中評估運算式。</span><span class="sxs-lookup"><span data-stu-id="f190a-176">When you include aggregate function calls to an expression in a Tablix cell, the report processor evaluates the expression in the scope of the innermost groups to which the cell belongs.</span></span>  
  
 <span data-ttu-id="f190a-177">您也可以將特定範圍的名稱傳遞給彙總函式。</span><span class="sxs-lookup"><span data-stu-id="f190a-177">You can also pass the name of a specific scope to an aggregate function.</span></span> <span data-ttu-id="f190a-178">範圍可以參考資料集的名稱、資料區域或在資料階層中較高範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="f190a-178">Scope can refer to the name of a dataset, a data region, or the name of a scope higher on the data hierarchy.</span></span> <span data-ttu-id="f190a-179">這點適用於下列訊息：</span><span class="sxs-lookup"><span data-stu-id="f190a-179">This applies to the following messages:</span></span>  
  
-   <span data-ttu-id="f190a-180">*\<report item type>*' *\<report item name>* ' 有不正確範圍 " *\<scope name>* "。</span><span class="sxs-lookup"><span data-stu-id="f190a-180">The *\<report item type>* '*\<report item name>*' has an invalid scope "*\<scope name>*".</span></span> <span data-ttu-id="f190a-181">範圍必須是目前的範圍，或包含在目前的範圍之內。</span><span class="sxs-lookup"><span data-stu-id="f190a-181">The scope must be the current scope, or contained within the current scope.</span></span>  
  
-   <span data-ttu-id="f190a-182">*\<property name>*' ' 的運算式 *\<report item type>* *\<report item name>* 含有對彙總函式不正確範圍參數。</span><span class="sxs-lookup"><span data-stu-id="f190a-182">The *\<property name>* expression for the *\<report item type>* '*\<report item name>*' has a scope parameter that is not valid for an aggregate function.</span></span> <span data-ttu-id="f190a-183">範圍參數必須設定為字串常數，此字串常數要和所包含的群組名稱、所包含的資料區域名稱或資料集名稱相同。</span><span class="sxs-lookup"><span data-stu-id="f190a-183">The scope parameter must be set to a string constant that is equal to either the name of a containing group, the name of a containing data region, or the name of a dataset.</span></span>  
  
 <span data-ttu-id="f190a-184">若為計算累加值的彙總函式 (`Previous`、`RunningValue` 或 `RowNumber`)，您可以指定屬於資料列群組名稱或資料行群組名稱的範圍參數，但不可同時屬於這兩者。</span><span class="sxs-lookup"><span data-stu-id="f190a-184">For aggregate functions that calculate running totals (`Previous`, `RunningValue`, or `RowNumber`), you can specify a scope parameter that is either a row group name or a column group name, but not both.</span></span> <span data-ttu-id="f190a-185">這點適用於下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="f190a-185">This applies to the following error message:</span></span>  
  
-   <span data-ttu-id="f190a-186">`Previous`， `RunningValue` 或在 `RowNumber` ' ' 資料格中使用的彙總函式，會參考的資料 *\<report item type>* *\<report item name>* 行和資料列中的群組範圍 *\<report item type>* 。</span><span class="sxs-lookup"><span data-stu-id="f190a-186">`Previous`, `RunningValue` or `RowNumber` aggregate functions used in the data cells of the *\<report item type>* '*\<report item name>*' refer to grouping scopes in both the columns and rows of the *\<report item type>*.</span></span> <span data-ttu-id="f190a-187">在 `Previous` 中，所有、和彙總函式的範圍參數， `RunningValue` `RowNumber` *\<report item type>* 都可以參考資料列群組或資料行群組，但不可同時參考兩者。</span><span class="sxs-lookup"><span data-stu-id="f190a-187">The scope parameters of all `Previous`, `RunningValue` and `RowNumber` aggregate functions within a *\<report item type>* can refer to row groupings or data column groupings, but not both.</span></span>  
  
 <span data-ttu-id="f190a-188">如需詳細資訊，請參閱[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](../report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md) 和[運算式中的內建集合 &#40;報表產生器及 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="f190a-188">For more information, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md) and [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
### <a name="default-dataset-scope-for-a-top-level-text-box"></a><span data-ttu-id="f190a-189">最上層文字方塊的預設資料集範圍</span><span class="sxs-lookup"><span data-stu-id="f190a-189">Default Dataset Scope for a Top Level Text Box</span></span>  
 <span data-ttu-id="f190a-190">當報表具有多個資料集時，請勿針對加入至報表設計介面的文字方塊使用預設範圍。</span><span class="sxs-lookup"><span data-stu-id="f190a-190">Do not use a default scope for a text box added to the report design surface when the report has more than one dataset.</span></span> <span data-ttu-id="f190a-191">請使用包含資料集名稱當做範圍的運算式，以及彙總函式。</span><span class="sxs-lookup"><span data-stu-id="f190a-191">Use an expression that includes the name of the dataset as the scope, and an aggregate function.</span></span> <span data-ttu-id="f190a-192">例如： `=First(Fields!FieldName.Value, "DataSet2")` 。</span><span class="sxs-lookup"><span data-stu-id="f190a-192">For example, `=First(Fields!FieldName.Value, "DataSet2")`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f190a-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f190a-193">See Also</span></span>  
 <span data-ttu-id="f190a-194">[運算式 &#40;報表產生器及 SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f190a-194">[Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f190a-195">[彙總函式參考 &#40;報表產生器及 SSRS&#41;](../report-design/report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f190a-195">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../report-design/report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="f190a-196">[運算式範例 &#40;報表產生器及 SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f190a-196">[Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f190a-197">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f190a-197">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="f190a-198">[常用的篩選 &#40;報表產生器及 SSRS&#41;](../report-design/commonly-used-filters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f190a-198">[Commonly Used Filters &#40;Report Builder and SSRS&#41;](../report-design/commonly-used-filters-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f190a-199">[資料集欄位集合 &#40;報表產生器及 SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f190a-199">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f190a-200">[報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f190a-200">[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span></span>  
 [<span data-ttu-id="f190a-201">參數集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f190a-201">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](../report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
