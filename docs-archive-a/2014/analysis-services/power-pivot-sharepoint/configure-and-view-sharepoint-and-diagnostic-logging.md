---
title: 設定及查看 SharePoint 記錄檔和診斷記錄 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 85f62d29-cdc6-45b3-be1f-ff1182939858
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c031614b0b55560c5b03b7235a6cc0a73023807
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599216"
---
# <a name="configure-and-view-sharepoint-log-files--and-diagnostic-logging-powerpivot-for-sharepoint"></a><span data-ttu-id="68733-102">設定及檢視 SharePoint 記錄檔與診斷記錄 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="68733-102">Configure and View SharePoint Log Files  and Diagnostic Logging (PowerPivot for SharePoint)</span></span>
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="68733-103">伺服器作業、事件與訊息都會記錄在 SharePoint 記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="68733-103">server operations, events, and messages are recorded in SharePoint log files.</span></span> <span data-ttu-id="68733-104">使用本主題的資訊來設定記錄層級及檢視記錄檔資訊。</span><span class="sxs-lookup"><span data-stu-id="68733-104">Use the information in this topic to configure logging levels and view log file information.</span></span> <span data-ttu-id="68733-105">您可以控制要記錄到檔案中的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 伺服器事件。</span><span class="sxs-lookup"><span data-stu-id="68733-105">You can control which [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server events are logged to the file.</span></span> <span data-ttu-id="68733-106">您也可以控制所記錄之訊息的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="68733-106">You can also control the severity of messages that are logged.</span></span> <span data-ttu-id="68733-107">如需詳細資訊，請參閱[設定 &#40;PowerPivot for SharePoint 的使用量資料收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="68733-107">For more information, see [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="68733-108">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="68733-108">In this topic:</span></span>  
  
-   [<span data-ttu-id="68733-109">記錄檔位置</span><span class="sxs-lookup"><span data-stu-id="68733-109">Log File Location</span></span>](#bkmk_filelocation)  
  
-   [<span data-ttu-id="68733-110">為個別的事件類別目錄修改診斷記錄層次</span><span class="sxs-lookup"><span data-stu-id="68733-110">Modify diagnostic logging levels for individual event categories</span></span>](#bkmk_modifyloglevels)  
  
-   [<span data-ttu-id="68733-111">如何檢視 SharePoint 記錄檔</span><span class="sxs-lookup"><span data-stu-id="68733-111">How to View SharePoint Log Files</span></span>](#bkmk_how2viewlogfiles)  
  
##  <a name="log-file-location"></a><a name="bkmk_filelocation"></a><span data-ttu-id="68733-112">記錄檔位置</span><span class="sxs-lookup"><span data-stu-id="68733-112">Log File Location</span></span>  
 <span data-ttu-id="68733-113">根據預設，SharePoint 記錄檔會儲存到下列位置：</span><span class="sxs-lookup"><span data-stu-id="68733-113">By default, SharePoint log files are saved to the following location:</span></span>  
  
 `C:\Program files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS`  
  
 <span data-ttu-id="68733-114">LOGS 資料夾中包含記錄檔 (`.log`)、資料檔 (`.txt`) 與使用方式檔案 (`.usage`)。</span><span class="sxs-lookup"><span data-stu-id="68733-114">The LOGS folder contains log files (`.log`), data files (`.txt`), and usage files (`.usage`).</span></span> <span data-ttu-id="68733-115">SharePoint 追蹤記錄的檔案命名慣例為伺服器名稱後面緊接著日期和時間戳記。</span><span class="sxs-lookup"><span data-stu-id="68733-115">The file naming convention for a SharePoint trace log is the server name followed by a date and time stamp.</span></span> <span data-ttu-id="68733-116">SharePoint 追蹤記錄會定期以及有 IISRESET 時建立。</span><span class="sxs-lookup"><span data-stu-id="68733-116">SharePoint trace logs are created at regular intervals and whenever there is an IISRESET.</span></span> <span data-ttu-id="68733-117">通常在 24 小時的週期內會有許多追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="68733-117">It is common to have many trace logs within a 24 hour period.</span></span>  
  
##  <a name="modify-diagnostic-logging-levels-for-individual-event-categories"></a><a name="bkmk_modifyloglevels"></a><span data-ttu-id="68733-118">修改個別事件類別目錄的診斷記錄層級</span><span class="sxs-lookup"><span data-stu-id="68733-118">Modify diagnostic logging levels for individual event categories</span></span>  
 <span data-ttu-id="68733-119">根據預設，PowerPivot 事件的 ULS 記錄是設為 *「中」*。</span><span class="sxs-lookup"><span data-stu-id="68733-119">By default, ULS logging of PowerPivot events is set at *Medium*.</span></span> <span data-ttu-id="68733-120">這是 SQL Server 2012 的新設定。</span><span class="sxs-lookup"><span data-stu-id="68733-120">This setting is new for SQL Server 2012.</span></span> <span data-ttu-id="68733-121">如果您從舊版升級伺服器，記錄層次可能仍然設為 *「詳細資訊」*(SQL Server 2008 R2 的預設層次)。</span><span class="sxs-lookup"><span data-stu-id="68733-121">If you upgraded a server from the prior release, the logging level might still be set at *Verbose*, the default level in SQL Server 2008 R2.</span></span> <span data-ttu-id="68733-122">如果您習慣檢閱 ULS 記錄檔中的 PowerPivot 伺服器使用資訊，會注意到因為此變更，PowerPivot 伺服器作業相關資訊變少了。</span><span class="sxs-lookup"><span data-stu-id="68733-122">If you are accustomed to reviewing the ULS logs for PowerPivot server usage information, you will notice that as a result of this change, there is less information about PowerPivot server operations.</span></span>  
  
 <span data-ttu-id="68733-123">除了例外狀況 (類型為 *「高」*) 以外，所有的 PowerPivot 訊息都會歸類為「詳細資訊」類別目錄。</span><span class="sxs-lookup"><span data-stu-id="68733-123">Except for exceptions, which are of type *High*, all PowerPivot messages fall into the Verbose category.</span></span> <span data-ttu-id="68733-124">如果您想要例行伺服器作業 (例如連接、要求或查詢報告) 的記錄項目，必須將記錄層次變更為「詳細資訊」。</span><span class="sxs-lookup"><span data-stu-id="68733-124">If you want log entries for routine server operations such as connections, requests, or query reporting, you must change the logging level to Verbose.</span></span>  
  
 <span data-ttu-id="68733-125">若要為個別的事件類別修改診斷記錄層次：</span><span class="sxs-lookup"><span data-stu-id="68733-125">To modify diagnostic logging levels for individual event categories:</span></span>  
  
1.  <span data-ttu-id="68733-126">在 SharePoint 管理中心，按一下 **[監視]**。</span><span class="sxs-lookup"><span data-stu-id="68733-126">In SharePoint Central Administration, click **Monitoring**.</span></span>  
  
2.  <span data-ttu-id="68733-127">按一下 **[設定診斷記錄]**。</span><span class="sxs-lookup"><span data-stu-id="68733-127">Click **Configure diagnostic logging**.</span></span>  
  
3.  <span data-ttu-id="68733-128">捲動到 **[PowerPivot 服務]**。</span><span class="sxs-lookup"><span data-stu-id="68733-128">Scroll to **PowerPivot Service**.</span></span>  
  
4.  <span data-ttu-id="68733-129">展開類別目錄，然後選取個別的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="68733-129">Expand the category and select individual categories.</span></span>  
  
     <span data-ttu-id="68733-130">**[應用程式頁面要求]** 會指定尋找 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 以載入 PowerPivot 資料來源以及和伺服陣列中的其他伺服器通訊時，由服務應用程式所觸發的事件。</span><span class="sxs-lookup"><span data-stu-id="68733-130">**Application Page Request** specifies events triggered by the service application when locating a [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] for loading a PowerPivot data source and communicating with other servers in the farm.</span></span>  
  
     <span data-ttu-id="68733-131">**[要求處理]** 會指定針對位於伺服器陣列中伺服器上所載入的 PowerPivot 資料庫，由查詢要求所觸發的事件。</span><span class="sxs-lookup"><span data-stu-id="68733-131">**Request Processing** specifies events triggered by query requests against a PowerPivot database that is loaded on a server in the farm.</span></span>  
  
     <span data-ttu-id="68733-132">**[使用量]** 指定與 PowerPivot 使用量資料收集相關的事件。</span><span class="sxs-lookup"><span data-stu-id="68733-132">**Usage** specifies an event related to PowerPivot usage data collection.</span></span>  
  
5.  <span data-ttu-id="68733-133">在 [回報至事件記錄的最低緊急事件] 中，選取 **[無]** 以停用類別目錄的事件記錄，或是選取 **[錯誤]** 以限制僅針對錯誤進行記錄。</span><span class="sxs-lookup"><span data-stu-id="68733-133">In Least critical event to report to the event log, select **None** to disable event logging for the category, or **Error** to limit logging for just errors.</span></span>  
  
6.  <span data-ttu-id="68733-134">選取 **[詳細資訊]** ，將所有事件記錄到事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="68733-134">Select **Verbose** to log all events to the event log.</span></span>  
  
7.  <span data-ttu-id="68733-135">在 [回報至追蹤記錄的最低緊急事件] 中，選取 **[無]** 以停用類別目錄的追蹤，或是選取 **[錯誤]** 以限制僅為錯誤進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="68733-135">In Least critical event to report to the trace log, select **None** to disable tracing for the category, or **Error** to limit tracing for just errors.</span></span>  
  
8.  <span data-ttu-id="68733-136">選取 **[詳細資訊]** ，將所有事件記錄到追蹤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="68733-136">Select **Verbose** to log all events to the trace log.</span></span>  
  
9. <span data-ttu-id="68733-137">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="68733-137">Click **OK**.</span></span>  
  
##  <a name="how-to-view-sharepoint-log-files"></a><a name="bkmk_how2viewlogfiles"></a><span data-ttu-id="68733-138">如何查看 SharePoint 記錄檔</span><span class="sxs-lookup"><span data-stu-id="68733-138">How to View SharePoint Log Files</span></span>  
 <span data-ttu-id="68733-139">記錄檔是文字檔。</span><span class="sxs-lookup"><span data-stu-id="68733-139">Log files are text files.</span></span> <span data-ttu-id="68733-140">您可以使用任何文字編輯器來開啟它們。</span><span class="sxs-lookup"><span data-stu-id="68733-140">You can open them in any text editor.</span></span> <span data-ttu-id="68733-141">您也可以使用協力廠商的記錄檢視器應用程式。</span><span class="sxs-lookup"><span data-stu-id="68733-141">You can also use third-party log viewer applications.</span></span>  
  
#### <a name="use-a-text-editor"></a><span data-ttu-id="68733-142">使用文字編輯器</span><span class="sxs-lookup"><span data-stu-id="68733-142">Use a Text Editor</span></span>  
 <span data-ttu-id="68733-143">如果您要使用文字編輯器疑難排解 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 伺服器錯誤，下列秘訣可以協助您找出檔案中相關的資訊：</span><span class="sxs-lookup"><span data-stu-id="68733-143">If you are using a text editor to troubleshoot a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server error, the following tips can help you locate relevant information in the file:</span></span>  
  
-   <span data-ttu-id="68733-144">若是與發行、檢視或重新整理 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿相關的錯誤，請搜尋記錄檔中的活頁簿名稱。</span><span class="sxs-lookup"><span data-stu-id="68733-144">For errors related to publishing, viewing, or refreshing a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbook, search the log file for the name of the workbook.</span></span>  
  
-   <span data-ttu-id="68733-145">若是提供相互關聯識別碼的錯誤，請複製該識別碼，並將其當做記錄檔中的搜尋詞彙使用。</span><span class="sxs-lookup"><span data-stu-id="68733-145">For errors that provide a correlation ID, copy the ID and use it as a search term in the log file.</span></span>  
  
-   <span data-ttu-id="68733-146">搜尋錯誤狀態「高」或「例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="68733-146">Search for error status "High" or "Exception".</span></span> <span data-ttu-id="68733-147">搜尋 "PowerPivot Service"。</span><span class="sxs-lookup"><span data-stu-id="68733-147">Search for "PowerPivot Service".</span></span>  
  
-   <span data-ttu-id="68733-148">如果您知道錯誤發生的時間，請使用日期和時間資訊縮小您必須捲動之項目的範圍。</span><span class="sxs-lookup"><span data-stu-id="68733-148">If you know when the error occurred, use the date and time information to narrow the scope of entries you must scroll through.</span></span>  
  
#### <a name="use-a-log-viewer-application"></a><span data-ttu-id="68733-149">使用記錄檢視器應用程式</span><span class="sxs-lookup"><span data-stu-id="68733-149">Use a Log Viewer Application</span></span>  
 <span data-ttu-id="68733-150">您可以使用文字編輯器個別檢視追蹤記錄，但是可讓您同時檢視數個記錄檔的記錄檢視器應用程式可能更實用。</span><span class="sxs-lookup"><span data-stu-id="68733-150">Although you can use a text editor to view the trace logs individually, a log viewer application that enables you to view several log files together can be far more useful.</span></span> <span data-ttu-id="68733-151">慶幸的是，有一些協力廠商記錄檢視器應用程式可以從 Codeplex 網站下載，協助您在單一工作空間檢視多個追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="68733-151">Fortunately, there are several third-party log viewer applications available for download on the Codeplex site that can help you view multiple trace logs in a single workspace.</span></span>  
  
 <span data-ttu-id="68733-152">下列指示包含可從 Codeplex 下載的常用 SharePoint ULS 記錄檢視器的連結。</span><span class="sxs-lookup"><span data-stu-id="68733-152">The following instructions include links to popular SharePoint ULS Log Viewers that you can download from Codeplex.</span></span>  
  
1.  <span data-ttu-id="68733-153">移至 Codeplex 網站上的 [SharePoint 記錄檢視器](http://sharepointlogviewer.codeplex.com) 或 [SharePoint ULS 記錄檢視器](https://go.microsoft.com/fwlink/?LinkId=150052) 。</span><span class="sxs-lookup"><span data-stu-id="68733-153">Go to [SharePoint LogViewer](http://sharepointlogviewer.codeplex.com) or [SharePoint ULS Log Viewer](https://go.microsoft.com/fwlink/?LinkId=150052) on the Codeplex site.</span></span>  
  
2.  <span data-ttu-id="68733-154">按一下 **[Downloads]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="68733-154">Click the **Downloads** tab.</span></span>  
  
3.  <span data-ttu-id="68733-155">按一下可執行檔。</span><span class="sxs-lookup"><span data-stu-id="68733-155">Click the executable file.</span></span> <span data-ttu-id="68733-156">此可執行檔是 **SharePointLogViewer.exe** 或 **ULS Viewer 2.0 Binary**。</span><span class="sxs-lookup"><span data-stu-id="68733-156">It will either be **SharePointLogViewer.exe** or **ULS Viewer 2.0 Binary**.</span></span>  
  
4.  <span data-ttu-id="68733-157">閱讀並接受授權條款。</span><span class="sxs-lookup"><span data-stu-id="68733-157">Read and accept the licensing terms.</span></span>  
  
5.  <span data-ttu-id="68733-158">按一下 **[Save]** ，將軟體下載到您的本機系統。</span><span class="sxs-lookup"><span data-stu-id="68733-158">Click **Save** to download the software to your local system.</span></span>  
  
     <span data-ttu-id="68733-159">如果您正在下載 SharePoint ULS 記錄檢視器，請將 ULSViewer.zip 儲存至 Downloads 資料夾。</span><span class="sxs-lookup"><span data-stu-id="68733-159">If you are downloading SharePoint ULS Log Viewer, save ULSViewer.zip to the Downloads folder.</span></span>  
  
6.  <span data-ttu-id="68733-160">在 [Downloads] 資料夾中，以滑鼠右鍵按一下 ULSViewer.zip，然後選取 **[解壓縮全部]**。</span><span class="sxs-lookup"><span data-stu-id="68733-160">In the Downloads folder, right-click ULSViewer.zip and select **Extract All**.</span></span>  
  
7.  <span data-ttu-id="68733-161">指定目的地資料夾，然後按一下 **[解壓縮]**。</span><span class="sxs-lookup"><span data-stu-id="68733-161">Specify a destination folder, and then click **Extract**.</span></span>  
  
8.  <span data-ttu-id="68733-162">在包含已解壓縮之程式檔的資料夾中，按兩下 **[ULSViewer]** 並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="68733-162">In the folder that contains the extracted program files, double-click **ULSViewer** and run the application.</span></span>  
  
9. <span data-ttu-id="68733-163">按一下應用程式視窗左上角的資料夾圖示。</span><span class="sxs-lookup"><span data-stu-id="68733-163">Click the folder icon at the top left corner of the application window.</span></span>  
  
10. <span data-ttu-id="68733-164">瀏覽至 \Program files\Common Files\Microsoft Shared\Web Server Extensions\14\Logs。</span><span class="sxs-lookup"><span data-stu-id="68733-164">Browse to \Program files\Common Files\Microsoft Shared\Web Server Extensions\14\Logs.</span></span>  
  
11. <span data-ttu-id="68733-165">選取一個或多個追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="68733-165">Select one or more trace logs.</span></span> <span data-ttu-id="68733-166">根據預設，記錄檔名稱由電腦名稱加上日期和時間資訊所組成。</span><span class="sxs-lookup"><span data-stu-id="68733-166">By default, trace log file names consist of the computer name plus date and time information.</span></span> <span data-ttu-id="68733-167">檔案類型為 [純文字文件]。</span><span class="sxs-lookup"><span data-stu-id="68733-167">The file type is Text Document.</span></span>  
  
12. <span data-ttu-id="68733-168">按一下 **[開啟]** ，然後等待檔案載入。</span><span class="sxs-lookup"><span data-stu-id="68733-168">Click **Open** and wait for the files to load.</span></span>  
  
13. <span data-ttu-id="68733-169">根據嚴重性、處理序、類別目錄或使用者定義的文字檔，使用內建的篩選選取記錄。</span><span class="sxs-lookup"><span data-stu-id="68733-169">Use the built-in filters to select records based on severity, process, category, or a user-defined text file.</span></span> <span data-ttu-id="68733-170">您也可以按一下欄標題來變更排序次序。</span><span class="sxs-lookup"><span data-stu-id="68733-170">You can also click column headings to change the sort order.</span></span>  
  
#### <a name="entries-for-powerpivot-services"></a><span data-ttu-id="68733-171">PowerPivot 服務的項目</span><span class="sxs-lookup"><span data-stu-id="68733-171">Entries for PowerPivot Services</span></span>  
 <span data-ttu-id="68733-172">下表描述很可能在 SharePoint 記錄檔中找到之 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 伺服器作業的項目。</span><span class="sxs-lookup"><span data-stu-id="68733-172">The following table describes entries for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server operations most likely to be found in a SharePoint log file.</span></span>  
  
|<span data-ttu-id="68733-173">Process</span><span class="sxs-lookup"><span data-stu-id="68733-173">Process</span></span>|<span data-ttu-id="68733-174">區域</span><span class="sxs-lookup"><span data-stu-id="68733-174">Area</span></span>|<span data-ttu-id="68733-175">類別</span><span class="sxs-lookup"><span data-stu-id="68733-175">Category</span></span>|<span data-ttu-id="68733-176">層級</span><span class="sxs-lookup"><span data-stu-id="68733-176">Level</span></span>|<span data-ttu-id="68733-177">訊息</span><span class="sxs-lookup"><span data-stu-id="68733-177">Message</span></span>|<span data-ttu-id="68733-178">詳細資料</span><span class="sxs-lookup"><span data-stu-id="68733-178">Details</span></span>|  
|-------------|----------|--------------|-----------|-------------|-------------|  
|<span data-ttu-id="68733-179">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="68733-179">w3wp.exe</span></span>|<span data-ttu-id="68733-180">[PowerPivot 服務]</span><span class="sxs-lookup"><span data-stu-id="68733-180">PowerPivot Service</span></span>|<span data-ttu-id="68733-181">使用量</span><span class="sxs-lookup"><span data-stu-id="68733-181">Usage</span></span>|<span data-ttu-id="68733-182">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="68733-182">Verbose</span></span>|<span data-ttu-id="68733-183">目前沒有要求統計資料，沒有要記錄的項目。</span><span class="sxs-lookup"><span data-stu-id="68733-183">There are no current request statistics, nothing to log.</span></span>|<span data-ttu-id="68733-184">服務報表會在預先定義的間隔查詢回應統計資料，做為使用量資料集合系統的使用量事件。</span><span class="sxs-lookup"><span data-stu-id="68733-184">At predefined intervals, the service reports query response statistics as a usage event to the usage data collection system.</span></span> <span data-ttu-id="68733-185">此訊息表示沒有要報告的查詢統計資料。</span><span class="sxs-lookup"><span data-stu-id="68733-185">This message indicates there were no query statistics to report.</span></span>|  
|<span data-ttu-id="68733-186">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="68733-186">w3wp.exe</span></span>|<span data-ttu-id="68733-187">[PowerPivot 服務]</span><span class="sxs-lookup"><span data-stu-id="68733-187">PowerPivot Service</span></span>|<span data-ttu-id="68733-188">Web 前端</span><span class="sxs-lookup"><span data-stu-id="68733-188">Web front end</span></span>|<span data-ttu-id="68733-189">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="68733-189">Verbose</span></span>|<span data-ttu-id="68733-190">開始尋找資料來源的應用程式伺服器 =\<*path*></span><span class="sxs-lookup"><span data-stu-id="68733-190">Starting to locate an application server for data source=\<*path*></span></span>|<span data-ttu-id="68733-191">當它收到連接要求時， [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務會識別可用的 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 來處理要求。</span><span class="sxs-lookup"><span data-stu-id="68733-191">When it receives a connection request, the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] service identifies an available [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] to handle the request.</span></span> <span data-ttu-id="68733-192">如果伺服陣列中只有一個伺服器，在所有情況下本機伺服器都會接受要求。</span><span class="sxs-lookup"><span data-stu-id="68733-192">If there is only one server in the farm, the local server accepts the request in all cases.</span></span>|  
|<span data-ttu-id="68733-193">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="68733-193">w3wp.exe</span></span>|<span data-ttu-id="68733-194">[PowerPivot 服務]</span><span class="sxs-lookup"><span data-stu-id="68733-194">PowerPivot Service</span></span>|<span data-ttu-id="68733-195">Web 前端</span><span class="sxs-lookup"><span data-stu-id="68733-195">Web front end</span></span>|<span data-ttu-id="68733-196">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="68733-196">Verbose</span></span>|<span data-ttu-id="68733-197">尋找應用程式伺服器成功。</span><span class="sxs-lookup"><span data-stu-id="68733-197">Locating the application server succeeded.</span></span>|<span data-ttu-id="68733-198">此要求會配置到 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="68733-198">The request was allocated to a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] service application.</span></span>|  
|<span data-ttu-id="68733-199">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="68733-199">w3wp.exe</span></span>|<span data-ttu-id="68733-200">[PowerPivot 服務]</span><span class="sxs-lookup"><span data-stu-id="68733-200">PowerPivot Service</span></span>|<span data-ttu-id="68733-201">Web 前端</span><span class="sxs-lookup"><span data-stu-id="68733-201">Web front end</span></span>|<span data-ttu-id="68733-202">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="68733-202">Verbose</span></span>|<span data-ttu-id="68733-203">將的要求重新導向 \<*PowerPivotdata source*> 至 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="68733-203">Redirecting request for the \<*PowerPivotdata source*> to the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)].</span></span>|<span data-ttu-id="68733-204">此要求會轉送至 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="68733-204">The request was forwarded to the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)].</span></span>|  
|<span data-ttu-id="68733-205">w3wp.exe</span><span class="sxs-lookup"><span data-stu-id="68733-205">w3wp.exe</span></span>|<span data-ttu-id="68733-206">[PowerPivot 服務]</span><span class="sxs-lookup"><span data-stu-id="68733-206">PowerPivot Service</span></span>|<span data-ttu-id="68733-207">[要求處理]</span><span class="sxs-lookup"><span data-stu-id="68733-207">Request Processing</span></span>|<span data-ttu-id="68733-208">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="68733-208">Verbose</span></span>|<span data-ttu-id="68733-209">將使用者名稱的要求重新導向 \<*SharePoint user*> 至資料庫</span><span class="sxs-lookup"><span data-stu-id="68733-209">Redirecting request for UserName\<*SharePoint user*> to the database</span></span>|<span data-ttu-id="68733-210">系統會代表 SharePoint 使用者建立模擬的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="68733-210">An impersonated connection to the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data source was created on behalf of the SharePoint user.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68733-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68733-211">See Also</span></span>  
 <span data-ttu-id="68733-212">[PowerPivot 使用量資料收集](power-pivot-usage-data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="68733-212">[PowerPivot Usage Data Collection](power-pivot-usage-data-collection.md) </span></span>  
 <span data-ttu-id="68733-213">[檢視與讀取 SQL Server 安裝程式記錄檔](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) </span><span class="sxs-lookup"><span data-stu-id="68733-213">[View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) </span></span>  
 [<span data-ttu-id="68733-214">設定 &#40;PowerPivot for SharePoint 的使用量資料收集</span><span class="sxs-lookup"><span data-stu-id="68733-214">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
