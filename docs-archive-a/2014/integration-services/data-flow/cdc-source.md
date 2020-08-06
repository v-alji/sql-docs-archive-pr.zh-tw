---
title: CDC 來源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.f1
ms.assetid: 99775608-e177-44ed-bb44-aaccb0f4f327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 064c25b129364dfcd813d71a462586303dd4ff60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599624"
---
# <a name="cdc-source"></a><span data-ttu-id="e9925-102">CDC 來源</span><span class="sxs-lookup"><span data-stu-id="e9925-102">CDC Source</span></span>
  <span data-ttu-id="e9925-103">CDC 來源會從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 變更資料表中讀取變更資料的範圍，並將這些變更向下游傳遞至其他 SSIS 元件。</span><span class="sxs-lookup"><span data-stu-id="e9925-103">The CDC source reads a range of change data from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] change tables and delivers the changes downstream to other SSIS components.</span></span>  
  
 <span data-ttu-id="e9925-104">CDC 來源所讀取的變數資料範圍稱為 CDC 處理範圍，並且由目前資料流程啟動之前執行的 CDC 控制工作所決定。</span><span class="sxs-lookup"><span data-stu-id="e9925-104">The range of change data read by the CDC source is called the CDC Processing Range and is determine by the CDC Control task that is executed before the current data flow starts.</span></span> <span data-ttu-id="e9925-105">CDC 處理範圍衍生自維護資料表群組之 CDC 處理狀態的封裝變數值。</span><span class="sxs-lookup"><span data-stu-id="e9925-105">The CDC Processing Range is derived from the value of a package variable that maintains the state of the CDC processing for a group of tables.</span></span>  
  
 <span data-ttu-id="e9925-106">CDC 來源會使用資料庫資料表、檢視或 SQL 陳述式，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e9925-106">The CDC source extracts data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using a database table, a view, or an SQL statement.</span></span>  
  
 <span data-ttu-id="e9925-107">CDC 來源使用下列組態：</span><span class="sxs-lookup"><span data-stu-id="e9925-107">The CDC source uses the following configurations:</span></span>  
  
-   <span data-ttu-id="e9925-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ADO.NET 連接管理員，用以存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e9925-108">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ADO.NET connection manager to access the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database.</span></span> <span data-ttu-id="e9925-109">如需設定 CDC 來源連接的詳細資訊，請參閱 [CDC 來源編輯器 &#40;連線管理員頁面&#41;](../cdc-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="e9925-109">For more information about configuring the CDC source connection, see [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).</span></span>  
  
-   <span data-ttu-id="e9925-110">啟用 CDC 的資料表。</span><span class="sxs-lookup"><span data-stu-id="e9925-110">A table enabled for CDC.</span></span>  
  
-   <span data-ttu-id="e9925-111">所選資料表的擷取執行個體名稱 (如果 more-than-one 存在)。</span><span class="sxs-lookup"><span data-stu-id="e9925-111">The name of the capture instance of the selected table (if more-than-one exists).</span></span>  
  
-   <span data-ttu-id="e9925-112">變更處理模式。</span><span class="sxs-lookup"><span data-stu-id="e9925-112">The change processing mode.</span></span>  
  
-   <span data-ttu-id="e9925-113">做為決定 CDC 處理範圍之依據的 CDC 狀態封裝變數名稱。</span><span class="sxs-lookup"><span data-stu-id="e9925-113">The name of the CDC state package variable based on which the CDC Processing range is determined.</span></span> <span data-ttu-id="e9925-114">CDC 來源不會修改該變數。</span><span class="sxs-lookup"><span data-stu-id="e9925-114">The CDC source does not modify that variable.</span></span>  
  
 <span data-ttu-id="e9925-115">CDC 來源傳回的資料與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 函式 **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** 或 **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (如果有) 傳回的資料相同。</span><span class="sxs-lookup"><span data-stu-id="e9925-115">The data returned by the CDC Source is the same as that returned by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC functions **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** or **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (when available).</span></span> <span data-ttu-id="e9925-116">唯一的選擇性附加資料行是 **__$initial_processing** ，表示目前處理範圍是否可與資料表的初始載入重疊。</span><span class="sxs-lookup"><span data-stu-id="e9925-116">The only optional addition is the column, **__$initial_processing** that indicates whether the current processing range can overlap with an initial load of the table.</span></span> <span data-ttu-id="e9925-117">如需初始處理的詳細資訊，請參閱 [CDC 控制工作](../control-flow/cdc-control-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e9925-117">For more information about initial processing, see [CDC Control Task](../control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="e9925-118">CDC 來源有一個一般輸出和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="e9925-118">The CDC source has one regular output and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="e9925-119">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="e9925-119">Error Handling</span></span>  
 <span data-ttu-id="e9925-120">CDC 來源有錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="e9925-120">The CDC source has an error output.</span></span> <span data-ttu-id="e9925-121">此元件的錯誤輸出包含下列輸出資料行：</span><span class="sxs-lookup"><span data-stu-id="e9925-121">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="e9925-122">**錯誤碼**：此值一律為 -1。</span><span class="sxs-lookup"><span data-stu-id="e9925-122">**Error Code**: The value is always -1.</span></span>  
  
-   <span data-ttu-id="e9925-123">**錯誤資料行**：造成錯誤 (用於轉換錯誤) 的來源資料行。</span><span class="sxs-lookup"><span data-stu-id="e9925-123">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="e9925-124">**錯誤資料列資料行**：造成錯誤的記錄資料。</span><span class="sxs-lookup"><span data-stu-id="e9925-124">**Error Row Columns**: The record data that causes the error.</span></span>  
  
 <span data-ttu-id="e9925-125">根據錯誤行為設定，CDC 來源支援在錯誤輸出中傳回擷取程序期間發生的錯誤 (資料轉換、截斷)。</span><span class="sxs-lookup"><span data-stu-id="e9925-125">Depending on the error behavior setting, the CDC source supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="e9925-126">如需詳細資訊，請參閱 [CDC 來源編輯器 &#40;錯誤輸出頁面&#41;](../cdc-source-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="e9925-126">For more information, see [CDC Source Editor &#40;Error Output Page&#41;](../cdc-source-editor-error-output-page.md).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="e9925-127">資料類型支援</span><span class="sxs-lookup"><span data-stu-id="e9925-127">Data Type Support</span></span>  
 <span data-ttu-id="e9925-128">Microsoft 的 CDC 來源元件支援所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，這些資料類型都會對應至正確的 SSIS 資料類型。</span><span class="sxs-lookup"><span data-stu-id="e9925-128">The CDC source component for Microsoft supports all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, which are mapped to the correct SSIS data types.</span></span>  
  
## <a name="troubleshooting-the-cdc-source"></a><span data-ttu-id="e9925-129">CDC 來源的疑難排解</span><span class="sxs-lookup"><span data-stu-id="e9925-129">Troubleshooting the CDC Source</span></span>  
 <span data-ttu-id="e9925-130">以下包含 CDC 來源的疑難排解資訊。</span><span class="sxs-lookup"><span data-stu-id="e9925-130">The following contains information on troubleshooting the CDC source.</span></span>  
  
### <a name="use-this-script-to-isolate-problems-and-reproduce-them-in-sql-server-management-studio"></a><span data-ttu-id="e9925-131">使用此指令碼來隔離問題，並在 SQL Server Management Studio 中重現問題。</span><span class="sxs-lookup"><span data-stu-id="e9925-131">Use this script to isolate problems and reproduce them in SQL Server Management Studio</span></span>  
 <span data-ttu-id="e9925-132">CDC 來源作業是由叫用 CDC 來源之前執行的 CDC 控制工作作業所控制。</span><span class="sxs-lookup"><span data-stu-id="e9925-132">The CDC source operation is governed by the operation of the CDC Control task executed before invoking the CDC source.</span></span> <span data-ttu-id="e9925-133">CDC 控制工作會準備 CDC 狀態封裝變數的值，以包含開始和結束 LSN。</span><span class="sxs-lookup"><span data-stu-id="e9925-133">The CDC Control task prepares the value of the CDC state package variable to contain the start and end LSNs.</span></span> <span data-ttu-id="e9925-134">它所執行的功能相當於下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="e9925-134">It performs function equivalent to the following script:</span></span>  
  
```  
use <cdc-enabled-database-name>  
               declare @start_lsn binary(10), @end_lsn binary(10)  
               set @start_lsn = sys.fn_cdc_increment_lsn(  
                       convert(binary(10),'0x' + '<value-from-state-cs>', 1))  
               set @end_lsn =   
                       convert(binary(10),'0x' + '<value-from-state-ce>', 1)  
               select * from cdc.fn_cdc_get_net_changes_dbo_Table1(@start_lsn,  
@end_lsn, '<mode>')  
```  
  
 <span data-ttu-id="e9925-135">其中：</span><span class="sxs-lookup"><span data-stu-id="e9925-135">where:</span></span>  
  
-   <span data-ttu-id="e9925-136">\<cdc-enabled-database-name> 是包含變更資料表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="e9925-136">\<cdc-enabled-database-name> is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database containing the change tables.</span></span>  
  
-   <span data-ttu-id="e9925-137">\<value-from-state-cs> 是在 CDC 狀態變數中顯示為 CS/\<value-from-state-cs>/ 的值 (CS 代表 Current-processing-range-Start)。</span><span class="sxs-lookup"><span data-stu-id="e9925-137">\<value-from-state-cs> is the value that appears in the CDC state variable as CS/\<value-from-state-cs>/ (CS stands for Current-processing-range-Start).</span></span>  
  
-   <span data-ttu-id="e9925-138">\<value-from-state-ce> 是在 CDC 狀態變數中顯示為 CE/\<value-from-state-cs>/ 的值 (CE 代表 Current-processing-range-End)。</span><span class="sxs-lookup"><span data-stu-id="e9925-138">\<value-from-state-ce> is the value that appears in the CDC state variable as CE/\<value-from-state-cs>/ (CE stands for Current-processing-range-End).</span></span>  
  
-   <span data-ttu-id="e9925-139">\<mode> 是 CDC 處理模式。</span><span class="sxs-lookup"><span data-stu-id="e9925-139">\<mode> are the CDC processing modes.</span></span> <span data-ttu-id="e9925-140">處理模式有下列其中一個值：[全部]  、[全部 (含舊值)]  、[淨]  、[淨 (含更新遮罩)]  、[淨 (含合併)]  。</span><span class="sxs-lookup"><span data-stu-id="e9925-140">The processing modes have one of the following values **All**, **All with Old Values**, **Net**, **Net with Update Mask**, **Net with Merge**.</span></span>  
  
 <span data-ttu-id="e9925-141">此指令碼會在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中重現問題，協助您輕鬆重現及識別錯誤以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="e9925-141">This script helps isolate problems by reproducing them in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], where it is easy to reproduce and identify errors.</span></span>  
  
#### <a name="sql-server-error-message"></a><span data-ttu-id="e9925-142">SQL Server 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="e9925-142">SQL Server Error Message</span></span>  
 <span data-ttu-id="e9925-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可能會傳回下列訊息：</span><span class="sxs-lookup"><span data-stu-id="e9925-143">The following message may be returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="e9925-144">**提供給程序或函式 cdc.fn_cdc_get_net_changes_\<..> 的引數數量不足。**</span><span class="sxs-lookup"><span data-stu-id="e9925-144">**An insufficient number of arguments were supplied for the procedure or function cdc.fn_cdc_get_net_changes_\<..>.**</span></span>  
  
 <span data-ttu-id="e9925-145">此錯誤並不表示缺少引數。</span><span class="sxs-lookup"><span data-stu-id="e9925-145">This error does not indicate that an argument is missing.</span></span> <span data-ttu-id="e9925-146">它表示 CDC 狀態變數中的開始或結束 LSN 值無效。</span><span class="sxs-lookup"><span data-stu-id="e9925-146">It means that the start or end LSN values in the CDC state variable are invalid.</span></span>  
  
## <a name="configuring-the-cdc-source"></a><span data-ttu-id="e9925-147">設定 CDC 來源</span><span class="sxs-lookup"><span data-stu-id="e9925-147">Configuring the CDC Source</span></span>  
 <span data-ttu-id="e9925-148">您可以透過程式設計方式或 SSIS 設計師來設定 CDC 來源。</span><span class="sxs-lookup"><span data-stu-id="e9925-148">You can configure the CDC source programmatically or through the SSIS Designer.</span></span>  
  
 <span data-ttu-id="e9925-149">如需詳細資訊，請參閱下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="e9925-149">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e9925-150">CDC 來源編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e9925-150">CDC Source Editor &#40;Connection Manager Page&#41;</span></span>](../cdc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="e9925-151">CDC 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e9925-151">CDC Source Editor &#40;Columns Page&#41;</span></span>](../cdc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="e9925-152">CDC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e9925-152">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
 <span data-ttu-id="e9925-153">**[進階編輯器]** 對話方塊包含可以程式設計方式設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9925-153">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="e9925-154">若要開啟 **[進階編輯器]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="e9925-154">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="e9925-155">在 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 專案的 [資料流程]  畫面中，以滑鼠右鍵按一下 CDC 來源，然後選取 [顯示進階編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="e9925-155">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC source and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="e9925-156">如需可在 [進階編輯器]  對話方塊中設定之屬性的詳細資訊，請參閱 [CDC 來源自訂屬性](cdc-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e9925-156">For more information about the properties that you can set in the **Advanced Editor** dialog box, see [CDC Source Custom Properties](cdc-source-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9925-157">本節內容</span><span class="sxs-lookup"><span data-stu-id="e9925-157">In This Section</span></span>  
  
-   [<span data-ttu-id="e9925-158">CDC 來源編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e9925-158">CDC Source Editor &#40;Connection Manager Page&#41;</span></span>](../cdc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="e9925-159">CDC 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e9925-159">CDC Source Editor &#40;Columns Page&#41;</span></span>](../cdc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="e9925-160">CDC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e9925-160">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="e9925-161">CDC 來源自訂屬性</span><span class="sxs-lookup"><span data-stu-id="e9925-161">CDC Source Custom Properties</span></span>](cdc-source-custom-properties.md)  
  
-   [<span data-ttu-id="e9925-162">使用 CDC 來源擷取變更資料</span><span class="sxs-lookup"><span data-stu-id="e9925-162">Extract Change Data Using the CDC Source</span></span>](cdc-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="e9925-163">相關內容</span><span class="sxs-lookup"><span data-stu-id="e9925-163">Related Content</span></span>  
  
-   <span data-ttu-id="e9925-164">mattmasson.com 上的部落格文章： [Processing Modes for the CDC Source](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/)。</span><span class="sxs-lookup"><span data-stu-id="e9925-164">Blog entry, [Processing Modes for the CDC Source](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/), on mattmasson.com.</span></span>  
  
  
