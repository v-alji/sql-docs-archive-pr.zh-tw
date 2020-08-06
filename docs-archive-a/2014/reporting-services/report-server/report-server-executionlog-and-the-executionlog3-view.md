---
title: 報表伺服器執行記錄和 ExecutionLog3 視圖 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- logs [Reporting Services], execution
- execution logs [Reporting Services]
ms.assetid: a7ead67d-1404-4e67-97e7-4c7b0d942070
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 868f8497e61c17662cb621850cdb8aee74c82706
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593304"
---
# <a name="report-server-execution-log-and-the-executionlog3-view"></a><span data-ttu-id="3bac4-102">報表伺服器執行記錄和 ExecutionLog3 檢視</span><span class="sxs-lookup"><span data-stu-id="3bac4-102">Report Server Execution Log and the ExecutionLog3 View</span></span>
  <span data-ttu-id="3bac4-103">報表伺服器執行記錄包含有關在伺服器上執行，或在原生模式向外延展部署或 SharePoint 伺服器陣列中多個伺服器上執行之報表的資訊。</span><span class="sxs-lookup"><span data-stu-id="3bac4-103">The report server execution log contains information about the reports that execute on the server or on multiple servers in a native mode scale-out deployment or a SharePoint farm.</span></span> <span data-ttu-id="3bac4-104">您可以使用報表執行記錄來了解要求報表的頻率、最常使用的輸出格式，以及每一個處理階段所花費處理時間的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="3bac4-104">You can use the report execution log to find out how often a report is requested, what output formats are used the most, and how many milliseconds of processing time is spent on each processing phase.</span></span> <span data-ttu-id="3bac4-105">此記錄會包含執行報表之資料集查詢所花費時間長度的資訊，以及處理資料所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="3bac4-105">The log contains information on the length of time spent executing a report's dataset query and the time spent processing the data.</span></span> <span data-ttu-id="3bac4-106">如果您是報表伺服器管理員，可以檢閱記錄資訊、識別長時間執行工作，並且向報表作者提出有關他們能夠改善之報表區域 (資料集或處理) 的建議。</span><span class="sxs-lookup"><span data-stu-id="3bac4-106">If you are a report server administrator, you can review the log information and identify long running tasks and make suggestions to the report authors on the areas of the report (dataset or processing) they may be able to improve.</span></span>  
  
 <span data-ttu-id="3bac4-107">設定為 SharePoint 模式的報表伺服器也可以利用 SharePoint ULS 記錄。</span><span class="sxs-lookup"><span data-stu-id="3bac4-107">Report servers configured for SharePoint mode, can also utilize the SharePoint ULS logs.</span></span> <span data-ttu-id="3bac4-108">如需詳細資訊，請參閱 [開啟 SharePoint 追蹤記錄的 Reporting Services 事件 &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)</span><span class="sxs-lookup"><span data-stu-id="3bac4-108">For more information, see [Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)</span></span>  
  
##  <a name="viewing-log-information"></a><a name="bkmk_top"></a> <span data-ttu-id="3bac4-109">檢視記錄資訊</span><span class="sxs-lookup"><span data-stu-id="3bac4-109">Viewing Log Information</span></span>  
 <span data-ttu-id="3bac4-110">報表伺服器執行會將有關報表執行的資料記錄到內部資料庫資料表中。</span><span class="sxs-lookup"><span data-stu-id="3bac4-110">The report server execution logs data about report execution into an internal database table.</span></span> <span data-ttu-id="3bac4-111">您可以從 SQL Server 檢視取得此資料表的資訊。</span><span class="sxs-lookup"><span data-stu-id="3bac4-111">The information from the table is available from SQL Server views.</span></span>  
  
 <span data-ttu-id="3bac4-112">報表執行記錄會儲存在預設名為 **ReportServer**的報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="3bac4-112">The report execution log is stored in the report server database that by default is named **ReportServer**.</span></span> <span data-ttu-id="3bac4-113">SQL 檢視會提供執行記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="3bac4-113">The SQL views provide the execution log information.</span></span> <span data-ttu-id="3bac4-114">"2" 和 "3" 檢視是在較新版本中新增，而且包含新欄位或是名稱比舊版更易記的欄位。</span><span class="sxs-lookup"><span data-stu-id="3bac4-114">The "2" and "3" views were added in more recent releases and contain new fields or they contain fields with friendlier names than the previous releases.</span></span> <span data-ttu-id="3bac4-115">舊版檢視仍然保留在產品中，因此相依於這些檢視的自訂應用程式不受影響。</span><span class="sxs-lookup"><span data-stu-id="3bac4-115">The older views remain in the product so custom applications that depend on them are not impacted.</span></span> <span data-ttu-id="3bac4-116">如果您沒有舊版檢視 (例如 ExecutionLog) 的相依性，建議您使用最新檢視 ExecutionLog**3**。</span><span class="sxs-lookup"><span data-stu-id="3bac4-116">If you do not have a dependence on an older view, for example ExecutionLog, it is recommended you use the most recent view, ExecutionLog**3**.</span></span>  
  
 <span data-ttu-id="3bac4-117">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="3bac4-117">In this topic:</span></span>  
  
-   [<span data-ttu-id="3bac4-118">SharePoint 模式報表伺服器的組態設定</span><span class="sxs-lookup"><span data-stu-id="3bac4-118">Configuration Settings for a SharePoint mode Report Server</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="3bac4-119">原生模式報表伺服器的組態設定</span><span class="sxs-lookup"><span data-stu-id="3bac4-119">Configuration Settings for a Native Mode Report Server</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="3bac4-120">記錄欄位 (ExecutionLog3)</span><span class="sxs-lookup"><span data-stu-id="3bac4-120">Log Fields (ExecutionLog3)</span></span>](#bkmk_executionlog3)  
  
-   [<span data-ttu-id="3bac4-121">AdditionalInfo 欄位</span><span class="sxs-lookup"><span data-stu-id="3bac4-121">The AdditionalInfo Field</span></span>](#bkmk_additionalinfo)  
  
-   [<span data-ttu-id="3bac4-122">記錄欄位 (ExecutionLog2)</span><span class="sxs-lookup"><span data-stu-id="3bac4-122">Log Fields (ExecutionLog2)</span></span>](#bkmk_executionlog2)  
  
-   [<span data-ttu-id="3bac4-123">記錄欄位 (ExecutionLog)</span><span class="sxs-lookup"><span data-stu-id="3bac4-123">Log Fields (ExecutionLog)</span></span>](#bkmk_executionlog)  
  
##  <a name="configuration-settings-for-a-sharepoint-mode-report-server"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="3bac4-124">SharePoint 模式報表伺服器的組態設定</span><span class="sxs-lookup"><span data-stu-id="3bac4-124">Configuration Settings for a SharePoint mode Report Server</span></span>  
 <span data-ttu-id="3bac4-125">您可以從 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的 [系統設定] 開啟或關閉報表執行記錄。</span><span class="sxs-lookup"><span data-stu-id="3bac4-125">You can turn report execution logging on or off from the system settings of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
 <span data-ttu-id="3bac4-126">根據預設，記錄項目會保留 60 天。</span><span class="sxs-lookup"><span data-stu-id="3bac4-126">By default, log entries are kept 60 days.</span></span> <span data-ttu-id="3bac4-127">超過此日期的項目會在每天上午 2:00 移除</span><span class="sxs-lookup"><span data-stu-id="3bac4-127">Entries that exceed this date are removed at 2:00 A.M.</span></span> <span data-ttu-id="3bac4-128">。</span><span class="sxs-lookup"><span data-stu-id="3bac4-128">every day.</span></span> <span data-ttu-id="3bac4-129">在到期的安裝上，不論何時都只能取得 60 天的資訊。</span><span class="sxs-lookup"><span data-stu-id="3bac4-129">On a mature installation, only 60 days of information will be available at any given time.</span></span>  
  
 <span data-ttu-id="3bac4-130">您無法針對資料列數目或記錄的項目類型設定限制。</span><span class="sxs-lookup"><span data-stu-id="3bac4-130">You cannot set limits on the number of rows or on the type of entries that are logged.</span></span>  
  
 <span data-ttu-id="3bac4-131">**若要啟用執行記錄：**</span><span class="sxs-lookup"><span data-stu-id="3bac4-131">**To enable execution logging:**</span></span>  
  
1.  <span data-ttu-id="3bac4-132">從 SharePoint 管理中心，按一下 [應用程式管理]  群組中的 [管理服務應用程式]  。</span><span class="sxs-lookup"><span data-stu-id="3bac4-132">From SharePoint Central Administration, click **Manage service applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="3bac4-133">按一下您想要設定之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="3bac4-133">Click the name of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application you want to configure.</span></span>  
  
3.  <span data-ttu-id="3bac4-134">按一下 **[系統設定]** 。</span><span class="sxs-lookup"><span data-stu-id="3bac4-134">Click **System Settings**.</span></span>  
  
4.  <span data-ttu-id="3bac4-135">選取 [記錄] 區段中的 [啟用執行記錄]。</span><span class="sxs-lookup"><span data-stu-id="3bac4-135">Select **Enable Execution Logging** in the **Logging** section.</span></span>  
  
5.  <span data-ttu-id="3bac4-136">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="3bac4-136">Click **OK**.</span></span>  
  
 <span data-ttu-id="3bac4-137">**若要啟用詳細資訊記錄：**</span><span class="sxs-lookup"><span data-stu-id="3bac4-137">**To enable verbose logging:**</span></span>  
  
 <span data-ttu-id="3bac4-138">您必須依照先前步驟的說明啟用記錄，然後完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3bac4-138">You need to enable logging as described in the previous steps and then complete the following:</span></span>  
  
1.  <span data-ttu-id="3bac4-139">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的 [系統設定] 頁面中，尋找 [使用者定義] 區段。</span><span class="sxs-lookup"><span data-stu-id="3bac4-139">From the **System Settings** page of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] services application, find the **User-defined** section.</span></span>  
  
2.  <span data-ttu-id="3bac4-140">將 [ExecutionLogLevel]  變更為 [verbose]  。</span><span class="sxs-lookup"><span data-stu-id="3bac4-140">Change the **ExecutionLogLevel** to **verbose**.</span></span> <span data-ttu-id="3bac4-141">這個欄位是文字輸入欄位，而且兩個可能的值為 [verbose]  和 [normal]  。</span><span class="sxs-lookup"><span data-stu-id="3bac4-141">This field is a text entry field and the two possible values are **verbose** and **normal**.</span></span>  
  
##  <a name="configuration-settings-for-a-native-mode-report-server"></a><a name="bkmk_native"></a> <span data-ttu-id="3bac4-142">原生模式報表伺服器的組態設定</span><span class="sxs-lookup"><span data-stu-id="3bac4-142">Configuration Settings for a Native Mode Report Server</span></span>  
 <span data-ttu-id="3bac4-143">您可以從 SQL Server Management Studio 的 [伺服器屬性] 頁面開啟或關閉報表執行記錄。</span><span class="sxs-lookup"><span data-stu-id="3bac4-143">You can turn report execution logging on or off from the Server Properties page in SQL Server Management Studio.</span></span> <span data-ttu-id="3bac4-144">**EnableExecutionLogging** 是進階屬性。</span><span class="sxs-lookup"><span data-stu-id="3bac4-144">The **EnableExecutionLogging** is and Advanced property.</span></span>  
  
 <span data-ttu-id="3bac4-145">根據預設，記錄項目會保留 60 天。</span><span class="sxs-lookup"><span data-stu-id="3bac4-145">By default, log entries are kept 60 days.</span></span> <span data-ttu-id="3bac4-146">超過此日期的項目會在每天上午 2:00 移除</span><span class="sxs-lookup"><span data-stu-id="3bac4-146">Entries that exceed this date are removed at 2:00 A.M.</span></span> <span data-ttu-id="3bac4-147">。</span><span class="sxs-lookup"><span data-stu-id="3bac4-147">every day.</span></span> <span data-ttu-id="3bac4-148">在到期的安裝上，不論何時都只能取得 60 天的資訊。</span><span class="sxs-lookup"><span data-stu-id="3bac4-148">On a mature installation, only 60 days of information will be available at any given time.</span></span>  
  
 <span data-ttu-id="3bac4-149">您無法針對資料列數目或記錄的項目類型設定限制。</span><span class="sxs-lookup"><span data-stu-id="3bac4-149">You cannot set limits on the number of rows or on the type of entries that are logged.</span></span>  
  
 <span data-ttu-id="3bac4-150">**若要啟用執行記錄：**</span><span class="sxs-lookup"><span data-stu-id="3bac4-150">**To enable execution logging:**</span></span>  
  
1.  <span data-ttu-id="3bac4-151">使用系統管理權限來啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="3bac4-151">Start SQL Server Management Studio with administrative privileges.</span></span> <span data-ttu-id="3bac4-152">例如，以滑鼠右鍵按一下 Management Studio 圖示，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="3bac4-152">For example right-click the Management Studio icon and click 'Run as administrator'.</span></span>  
  
2.  <span data-ttu-id="3bac4-153">連接到所需的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="3bac4-153">Connect to the desired report server.</span></span>  
  
3.  <span data-ttu-id="3bac4-154">以滑鼠右鍵按一下伺服器名稱，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="3bac4-154">Right-click the server name and click **Properties**.</span></span> <span data-ttu-id="3bac4-155">如果 [屬性] 選項已停用，請確認您已使用系統管理權限來啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="3bac4-155">If the Properties option is disabled, verify you ran SQL Server Management Studio with administrative privileges.</span></span>  
  
4.  <span data-ttu-id="3bac4-156">按一下 [記錄]  頁面。</span><span class="sxs-lookup"><span data-stu-id="3bac4-156">Click the **Logging** page.</span></span>  
  
5.  <span data-ttu-id="3bac4-157">選取 [啟用報表執行記錄]  。</span><span class="sxs-lookup"><span data-stu-id="3bac4-157">Select **Enable report execution Logging**.</span></span>  
  
 <span data-ttu-id="3bac4-158">**若要啟用詳細資訊記錄：**</span><span class="sxs-lookup"><span data-stu-id="3bac4-158">**To enable verbose logging:**</span></span>  
  
 <span data-ttu-id="3bac4-159">您必須依照先前步驟的說明啟用記錄，然後完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3bac4-159">You need to enable logging as described in the previous steps and then complete the following:</span></span>  
  
1.  <span data-ttu-id="3bac4-160">在 [伺服器屬性]  對話方塊中，按一下 [進階]  頁面。</span><span class="sxs-lookup"><span data-stu-id="3bac4-160">From the **Server Properties** dialog, click the **Advanced** page.</span></span>  
  
2.  <span data-ttu-id="3bac4-161">在 [使用者定義]  區段中，將 [ExecutionLogLevel]  變更為 [verbose]  。</span><span class="sxs-lookup"><span data-stu-id="3bac4-161">In the **User-defined** section, change the **ExecutionLogLevel** to **verbose**.</span></span> <span data-ttu-id="3bac4-162">這個欄位是文字輸入欄位，而且兩個可能的值為 [verbose]  和 [normal]  。</span><span class="sxs-lookup"><span data-stu-id="3bac4-162">This field is a text entry field and the two possible values are **verbose** and **normal**.</span></span>  
  
##  <a name="log-fields-executionlog3"></a><a name="bkmk_executionlog3"></a> <span data-ttu-id="3bac4-163">記錄欄位 (ExecutionLog3)</span><span class="sxs-lookup"><span data-stu-id="3bac4-163">Log Fields (ExecutionLog3)</span></span>  
 <span data-ttu-id="3bac4-164">這個檢視已在 XML 架構的 **AdditionalInfo** 資料行內加入其他效能診斷節點。</span><span class="sxs-lookup"><span data-stu-id="3bac4-164">This view added additional performance diagnostics node inside the XML based **AdditionalInfo** column.</span></span> <span data-ttu-id="3bac4-165">AdditionalInfo 資料行包含的 XML 結構是由 1 至多個其他資訊欄位所組成。</span><span class="sxs-lookup"><span data-stu-id="3bac4-165">The AdditionalInfo column contains an XML structure of 1 to many additional fields of information.</span></span> <span data-ttu-id="3bac4-166">下面是可從 ExecutionLog3 檢視中擷取資料列的範例 Transact SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3bac4-166">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog3.</span></span> <span data-ttu-id="3bac4-167">此範例會假設報表伺服器資料庫名為 **ReportServer**：</span><span class="sxs-lookup"><span data-stu-id="3bac4-167">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog3 order by TimeStart DESC  
```  
  
 <span data-ttu-id="3bac4-168">下表描述在報表執行記錄中擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="3bac4-168">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="3bac4-169">資料行</span><span class="sxs-lookup"><span data-stu-id="3bac4-169">Column</span></span>|<span data-ttu-id="3bac4-170">描述</span><span class="sxs-lookup"><span data-stu-id="3bac4-170">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3bac4-171">InstanceName</span><span class="sxs-lookup"><span data-stu-id="3bac4-171">InstanceName</span></span>|<span data-ttu-id="3bac4-172">處理要求的報表伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="3bac4-172">Name of the report server instance that handled the request.</span></span> <span data-ttu-id="3bac4-173">如果您的環境具有多個報表伺服器，您可以分析 InstanceName 散發以監視並判斷網路負載平衡器是否依照預期方式在報表伺服器之間散發要求。</span><span class="sxs-lookup"><span data-stu-id="3bac4-173">If your environment has more than one report server, you can analyze the InstanceName distribution to monitor and determine if your network-load balancer distributes requests across report servers as expected.</span></span>|  
|<span data-ttu-id="3bac4-174">ItemPath</span><span class="sxs-lookup"><span data-stu-id="3bac4-174">ItemPath</span></span>|<span data-ttu-id="3bac4-175">儲存報表或報表項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="3bac4-175">Path of where a report or report item is stored.</span></span>|  
|<span data-ttu-id="3bac4-176">UserName</span><span class="sxs-lookup"><span data-stu-id="3bac4-176">UserName</span></span>|<span data-ttu-id="3bac4-177">使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="3bac4-177">User identifier.</span></span>|  
|<span data-ttu-id="3bac4-178">ExecutionID</span><span class="sxs-lookup"><span data-stu-id="3bac4-178">ExecutionID</span></span>|<span data-ttu-id="3bac4-179">與要求相關聯的內部識別碼。</span><span class="sxs-lookup"><span data-stu-id="3bac4-179">The internal identifier associated with a request.</span></span> <span data-ttu-id="3bac4-180">相同使用者工作階段上的要求會共用相同的執行識別碼。</span><span class="sxs-lookup"><span data-stu-id="3bac4-180">Requests on the same user sessions share the same execution id.</span></span>|  
|<span data-ttu-id="3bac4-181">RequestType</span><span class="sxs-lookup"><span data-stu-id="3bac4-181">RequestType</span></span>|<span data-ttu-id="3bac4-182">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="3bac4-182">Possible Values:</span></span><br /><span data-ttu-id="3bac4-183">**互動式**</span><span class="sxs-lookup"><span data-stu-id="3bac4-183">**Interactive**</span></span><br /><span data-ttu-id="3bac4-184">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="3bac4-184">**Subscription**</span></span><br /><br /> <br /><br /> <span data-ttu-id="3bac4-185">分析依 RequestType=Subscription 所篩選並且依 TimeStart 所排序的記錄資料可能會顯現訂閱使用量龐大的週期，而且您可能會想要將某些報表訂閱修改成不同的時間。</span><span class="sxs-lookup"><span data-stu-id="3bac4-185">Analyzing log data filtered by RequestType=Subscription and sorted by TimeStart may reveal periods of heavy subscription usage and you may want to modify some of the report subscriptions to a different time.</span></span>|  
|<span data-ttu-id="3bac4-186">[格式]</span><span class="sxs-lookup"><span data-stu-id="3bac4-186">Format</span></span>|<span data-ttu-id="3bac4-187">轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="3bac4-187">Rendering format.</span></span>|  
|<span data-ttu-id="3bac4-188">參數</span><span class="sxs-lookup"><span data-stu-id="3bac4-188">Parameters</span></span>|<span data-ttu-id="3bac4-189">報表執行所使用的參數值。</span><span class="sxs-lookup"><span data-stu-id="3bac4-189">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="3bac4-190">ItemAction</span><span class="sxs-lookup"><span data-stu-id="3bac4-190">ItemAction</span></span>|<span data-ttu-id="3bac4-191">可能的值：</span><span class="sxs-lookup"><span data-stu-id="3bac4-191">Possible values:</span></span><br /><br /> <span data-ttu-id="3bac4-192">**轉譯**</span><span class="sxs-lookup"><span data-stu-id="3bac4-192">**Render**</span></span><br /><br /> <span data-ttu-id="3bac4-193">**排序**</span><span class="sxs-lookup"><span data-stu-id="3bac4-193">**Sort**</span></span><br /><br /> <span data-ttu-id="3bac4-194">**BookMarkNavigation**</span><span class="sxs-lookup"><span data-stu-id="3bac4-194">**BookMarkNavigation**</span></span><br /><br /> <span data-ttu-id="3bac4-195">**DocumentNavigation**</span><span class="sxs-lookup"><span data-stu-id="3bac4-195">**DocumentNavigation**</span></span><br /><br /> <span data-ttu-id="3bac4-196">**GetDocumentMap**</span><span class="sxs-lookup"><span data-stu-id="3bac4-196">**GetDocumentMap**</span></span><br /><br /> <span data-ttu-id="3bac4-197">**Findstring**</span><span class="sxs-lookup"><span data-stu-id="3bac4-197">**Findstring**</span></span><br /><br /> <span data-ttu-id="3bac4-198">**執行**</span><span class="sxs-lookup"><span data-stu-id="3bac4-198">**Execute**</span></span><br /><br /> <span data-ttu-id="3bac4-199">**RenderEdit**</span><span class="sxs-lookup"><span data-stu-id="3bac4-199">**RenderEdit**</span></span>|  
|<span data-ttu-id="3bac4-200">TimeStart</span><span class="sxs-lookup"><span data-stu-id="3bac4-200">TimeStart</span></span>|<span data-ttu-id="3bac4-201">指出報表處理持續期間的開始與結束時間。</span><span class="sxs-lookup"><span data-stu-id="3bac4-201">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="3bac4-202">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="3bac4-202">TimeEnd</span></span>||  
|<span data-ttu-id="3bac4-203">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="3bac4-203">TimeDataRetrieval</span></span>|<span data-ttu-id="3bac4-204">擷取資料所花費的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="3bac4-204">Number of milliseconds spent retrieving the data.</span></span>|  
|<span data-ttu-id="3bac4-205">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="3bac4-205">TimeProcessing</span></span>|<span data-ttu-id="3bac4-206">處理報表所花費的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="3bac4-206">Number of milliseconds spent processing the report.</span></span>|  
|<span data-ttu-id="3bac4-207">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="3bac4-207">TimeRendering</span></span>|<span data-ttu-id="3bac4-208">轉譯報表所花費的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="3bac4-208">Number of milliseconds spent rendering the report.</span></span>|  
|<span data-ttu-id="3bac4-209">來源</span><span class="sxs-lookup"><span data-stu-id="3bac4-209">Source</span></span>|<span data-ttu-id="3bac4-210">報表執行的來源。</span><span class="sxs-lookup"><span data-stu-id="3bac4-210">Source of the report execution.</span></span> <span data-ttu-id="3bac4-211">可能的值：</span><span class="sxs-lookup"><span data-stu-id="3bac4-211">Possible values:</span></span><br /><br /> <span data-ttu-id="3bac4-212">**直播**</span><span class="sxs-lookup"><span data-stu-id="3bac4-212">**Live**</span></span><br /><br /> <span data-ttu-id="3bac4-213">**Cache**：表示快取的執行，例如，資料集查詢不會即時執行。</span><span class="sxs-lookup"><span data-stu-id="3bac4-213">**Cache**: Indicates a cached execution, for example, dataset queries are not executed live.</span></span><br /><br /> <span data-ttu-id="3bac4-214">**快照式**</span><span class="sxs-lookup"><span data-stu-id="3bac4-214">**Snapshot**</span></span><br /><br /> <span data-ttu-id="3bac4-215">**History**</span><span class="sxs-lookup"><span data-stu-id="3bac4-215">**History**</span></span><br /><br /> <span data-ttu-id="3bac4-216">臨**機操作：** 表示動態產生的報表模型型切入報表，或在使用報表伺服器進行處理和轉譯的用戶端上預覽的報表產生器報表。</span><span class="sxs-lookup"><span data-stu-id="3bac4-216">**AdHoc** : Indicates either a dynamically generated report model based drill through report, or a Report Builder report that is previewed on a client utilizing the report server for processing and rendering.</span></span><br /><br /> <span data-ttu-id="3bac4-217">**Session**：表示已經建立之會話內的後續要求。</span><span class="sxs-lookup"><span data-stu-id="3bac4-217">**Session**: Indicates a follow up request within an already established session.</span></span>  <span data-ttu-id="3bac4-218">例如，初始要求是檢視頁面 1，而後續要求則是匯出到 Excel (包含目前的工作階段狀態)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-218">For example the initial request is to view page 1, and the follow up request is to export to Excel with the current session state.</span></span><br /><br /> <span data-ttu-id="3bac4-219">**Rdce**：表示報表定義自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="3bac4-219">**Rdce**:  Indicates a Report Definition Customization Extension.</span></span> <span data-ttu-id="3bac4-220">RDCE 自訂延伸模組可以動態地自訂報表定義，然後在執行報表時將其傳遞至處理引擎。</span><span class="sxs-lookup"><span data-stu-id="3bac4-220">An RDCE custom extension can dynamically customize a report definition before it is passed to the processing engine upon report execution.</span></span>|  
|<span data-ttu-id="3bac4-221">狀態</span><span class="sxs-lookup"><span data-stu-id="3bac4-221">Status</span></span>|<span data-ttu-id="3bac4-222">狀態 (不是 rsSuccess 就是錯誤碼；如果發生多個錯誤，就只會記錄第一個錯誤)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-222">Status (either rsSuccess or an error code; if multiple errors occur, only the first error is recorded).</span></span>|  
|<span data-ttu-id="3bac4-223">ByteCount</span><span class="sxs-lookup"><span data-stu-id="3bac4-223">ByteCount</span></span>|<span data-ttu-id="3bac4-224">轉譯報表的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-224">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="3bac4-225">RowCount</span><span class="sxs-lookup"><span data-stu-id="3bac4-225">RowCount</span></span>|<span data-ttu-id="3bac4-226">從查詢傳回的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3bac4-226">Number of rows returned from queries.</span></span>|  
|<span data-ttu-id="3bac4-227">AdditionalInfo</span><span class="sxs-lookup"><span data-stu-id="3bac4-227">AdditionalInfo</span></span>|<span data-ttu-id="3bac4-228">XML 屬性包，其中包含有關執行的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3bac4-228">An XML property bag containing additional information about the execution.</span></span> <span data-ttu-id="3bac4-229">每個資料列的內容可能都不同。</span><span class="sxs-lookup"><span data-stu-id="3bac4-229">The contents can be different for each row.</span></span>|  
  
##  <a name="the-additionalinfo-field"></a><a name="bkmk_additionalinfo"></a> <span data-ttu-id="3bac4-230">AdditionalInfo 欄位</span><span class="sxs-lookup"><span data-stu-id="3bac4-230">The AdditionalInfo Field</span></span>  
 <span data-ttu-id="3bac4-231">AdditionalInfo 欄位是一種 XML 屬性包或結構，其中包含有關執行的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3bac4-231">The AdditionalInfo field is an XML property bag or structure containing additional information about the execution.</span></span> <span data-ttu-id="3bac4-232">記錄中每個資料列的內容可能都不同。</span><span class="sxs-lookup"><span data-stu-id="3bac4-232">The contents can be different for each row in the log.</span></span>  
  
 <span data-ttu-id="3bac4-233">下表是標準和詳細資訊記錄中，AddtionalInfo 欄位內容的範例：</span><span class="sxs-lookup"><span data-stu-id="3bac4-233">The following tables are examples  of the contents of the AddtionalInfo field for both standard and verbose logging:</span></span>  
  
 <span data-ttu-id="3bac4-234">**AddtionalInfo 的標準記錄範例**</span><span class="sxs-lookup"><span data-stu-id="3bac4-234">**Standard logging example of AddtionalInfo**</span></span>  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>147</ConnectionOpenTime>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>642</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>63</ExecuteReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>157</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>60</ExecuteReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 <span data-ttu-id="3bac4-235">**AdditionalInfo 的詳細資訊記錄範例**</span><span class="sxs-lookup"><span data-stu-id="3bac4-235">**Verbose logging example of AdditionalInfo**</span></span>  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>127</ConnectionOpenTime>  
      <DataSource>  
        <Name>DataSource1</Name>  
        <DataExtension>SQL</DataExtension>  
      </DataSource>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>33</ExecuteReaderTime>  
          <DataReaderMappingTime>30</DataReaderMappingTime>  
          <DisposeDataReaderTime>1</DisposeDataReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>1</ExecuteReaderTime>  
          <DataReaderMappingTime>0</DataReaderMappingTime>  
          <DisposeDataReaderTime>0</DisposeDataReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 <span data-ttu-id="3bac4-236">以下說明您會在 [AdditionalInfo] 欄位中看到的一些屬性：</span><span class="sxs-lookup"><span data-stu-id="3bac4-236">The following describes some of the properties you will see in the AdditionalInfo field:</span></span>  
  
-   <span data-ttu-id="3bac4-237">**ProcessingEngine**： 1 = SQL Server 2005，2 = 新的隨選處理引擎。</span><span class="sxs-lookup"><span data-stu-id="3bac4-237">**ProcessingEngine**: 1=SQL Server 2005, 2=The new On-demand Processing Engine.</span></span> <span data-ttu-id="3bac4-238">如果大部分報表仍然顯示 1 值，可以調查重新設計報表的方式，讓它們都利用較新且更有效率的視需要處理引擎。</span><span class="sxs-lookup"><span data-stu-id="3bac4-238">If a majority of your reports are still showing the value of 1, you may investigate how to redesign them so they utilize the newer and more efficient on-demand processing engine.</span></span>  
  
     `<ProcessingEngine>2</ProcessingEngine>`  
  
-   <span data-ttu-id="3bac4-239">**ScalabilityTime**：在處理引擎中執行調整相關作業所花費的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="3bac4-239">**ScalabilityTime**: The number of milliseconds spent performing scale related operations in the processing engine.</span></span> <span data-ttu-id="3bac4-240">0 值表示沒有針對延展作業花費任何額外時間，而且 0 也表示要求沒有承受記憶體不足的壓力。</span><span class="sxs-lookup"><span data-stu-id="3bac4-240">A value of 0 indicates that no additional time was spent on scale operations and a 0 also indicates the request was not under memory pressure.</span></span>  
  
    ```  
    <ScalabilityTime>  
        <Processing>0</Processing>  
    </ScalabilityTime>  
    ```  
  
-   <span data-ttu-id="3bac4-241">**EstimatedMemoryUsageKB**：每個元件在特定要求期間所耗用的尖峰記憶體數量估計（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="3bac4-241">**EstimatedMemoryUsageKB**: An estimate of the peak amount of memory, in kilobytes, consumed by each component during a particular request.</span></span>  
  
    ```  
    <EstimatedMemoryUsageKB>  
        <Processing>38</Processing>  
    </EstimatedMemoryUsageKB>  
    ```  
  
-   <span data-ttu-id="3bac4-242">**DataExtension**：報表中使用的資料延伸模組或資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="3bac4-242">**DataExtension**: The types of data extensions or data sources used in the report.</span></span> <span data-ttu-id="3bac4-243">其數字為特定資料來源的出現次數。</span><span class="sxs-lookup"><span data-stu-id="3bac4-243">The number is a count of the number of occurrences of the particular data source.</span></span>  
  
    ```  
    <DataExtension>  
       <DAX>2</DAX>  
    </DataExtension>  
    ```  
  
-   <span data-ttu-id="3bac4-244">**ExternalImages**值為毫秒。</span><span class="sxs-lookup"><span data-stu-id="3bac4-244">**ExternalImages**The value is in miliseconds.</span></span> <span data-ttu-id="3bac4-245">此資料可用來診斷效能問題。</span><span class="sxs-lookup"><span data-stu-id="3bac4-245">This data can be used to diagnose performance issues.</span></span> <span data-ttu-id="3bac4-246">從外部 Web 伺服器擷取影像所需的時間可能會讓整體報表執行變慢。</span><span class="sxs-lookup"><span data-stu-id="3bac4-246">The time needed to retrieve images from an external webserver may slow the overall report execution.</span></span> <span data-ttu-id="3bac4-247">已在中新增 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3bac4-247">Added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
    ```  
    <ExternalImages>  
        <Count>3</Count>  
        <ByteCount>9268</ByteCount>  
        <ResourceFetchTime>9</ResourceFetchTime>  
    </ExternalImages>  
    ```  
  
-   <span data-ttu-id="3bac4-248">**連接**：多層式結構。</span><span class="sxs-lookup"><span data-stu-id="3bac4-248">**Connections**: A multi-leveled structure.</span></span> <span data-ttu-id="3bac4-249">已在中新增 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3bac4-249">Added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
    ```  
    <Connections>  
        <Connection>  
          <ConnectionOpenTime>127</ConnectionOpenTime>  
          <DataSource>  
            <Name>DataSource1</Name>  
            <DataExtension>SQL</DataExtension>  
          </DataSource>  
          <DataSets>  
            <DataSet>  
              <Name>DataSet1</Name>  
              <RowsRead>16</RowsRead>  
              <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>33</ExecuteReaderTime>  
              <DataReaderMappingTime>30</DataReaderMappingTime>  
              <DisposeDataReaderTime>1</DisposeDataReaderTime>  
            </DataSet>  
            <DataSet>  
              <Name>DataSet2</Name>  
              <RowsRead>3</RowsRead>  
              <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>1</ExecuteReaderTime>  
              <DataReaderMappingTime>0</DataReaderMappingTime>  
              <DisposeDataReaderTime>0</DisposeDataReaderTime>  
            </DataSet>  
          </DataSets>  
        </Connection>  
    </Connections>  
  
    ```  
  
##  <a name="log-fields-executionlog2"></a><a name="bkmk_executionlog2"></a><span data-ttu-id="3bac4-250">記錄欄位 (ExecutionLog2) </span><span class="sxs-lookup"><span data-stu-id="3bac4-250">Log Fields (ExecutionLog2)</span></span>  
 <span data-ttu-id="3bac4-251">這個檢視加入了一些新欄位並且重新命名了一些其他欄位。</span><span class="sxs-lookup"><span data-stu-id="3bac4-251">This view added a few new fields and renamed a few others.</span></span> <span data-ttu-id="3bac4-252">下面是可從 ExecutionLog2 檢視中擷取資料列的範例 Transact SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3bac4-252">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog2.</span></span> <span data-ttu-id="3bac4-253">此範例會假設報表伺服器資料庫名為 **ReportServer**：</span><span class="sxs-lookup"><span data-stu-id="3bac4-253">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog2 order by TimeStart DESC  
```  
  
 <span data-ttu-id="3bac4-254">下表描述在報表執行記錄中擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="3bac4-254">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="3bac4-255">資料行</span><span class="sxs-lookup"><span data-stu-id="3bac4-255">Column</span></span>|<span data-ttu-id="3bac4-256">描述</span><span class="sxs-lookup"><span data-stu-id="3bac4-256">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3bac4-257">InstanceName</span><span class="sxs-lookup"><span data-stu-id="3bac4-257">InstanceName</span></span>|<span data-ttu-id="3bac4-258">處理要求的報表伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="3bac4-258">Name of the report server instance that handled the request.</span></span>|  
|<span data-ttu-id="3bac4-259">ReportPath</span><span class="sxs-lookup"><span data-stu-id="3bac4-259">ReportPath</span></span>|<span data-ttu-id="3bac4-260">報表的路徑結構。</span><span class="sxs-lookup"><span data-stu-id="3bac4-260">The path structure to the report.</span></span>  <span data-ttu-id="3bac4-261">例如，名為 "test" 且位於報表管理員根資料夾中報表會具有 "/test" 的 ReportPath。</span><span class="sxs-lookup"><span data-stu-id="3bac4-261">For example a report named "test" which is the in root folder in Report Manager, would have a ReportPath of "/test".</span></span><br /><br /> <span data-ttu-id="3bac4-262">名為 "test" 且儲存在報表管理員 "samples" 資料夾中報表會具有 "/Samples/test/" 的 ReportPath</span><span class="sxs-lookup"><span data-stu-id="3bac4-262">A report named "test" that is saved in the folder "samples" on Report Manager , will have a ReportPath of "/Samples/test/"</span></span>|  
|<span data-ttu-id="3bac4-263">UserName</span><span class="sxs-lookup"><span data-stu-id="3bac4-263">UserName</span></span>|<span data-ttu-id="3bac4-264">使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="3bac4-264">User identifier.</span></span>|  
|<span data-ttu-id="3bac4-265">ExecutionID</span><span class="sxs-lookup"><span data-stu-id="3bac4-265">ExecutionID</span></span>||  
|<span data-ttu-id="3bac4-266">RequestType</span><span class="sxs-lookup"><span data-stu-id="3bac4-266">RequestType</span></span>|<span data-ttu-id="3bac4-267">要求類型 (使用者或系統)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-267">Request type (either user or system).</span></span>|  
|<span data-ttu-id="3bac4-268">格式</span><span class="sxs-lookup"><span data-stu-id="3bac4-268">Format</span></span>|<span data-ttu-id="3bac4-269">轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="3bac4-269">Rendering format.</span></span>|  
|<span data-ttu-id="3bac4-270">參數</span><span class="sxs-lookup"><span data-stu-id="3bac4-270">Parameters</span></span>|<span data-ttu-id="3bac4-271">報表執行所使用的參數值。</span><span class="sxs-lookup"><span data-stu-id="3bac4-271">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="3bac4-272">ReportAction</span><span class="sxs-lookup"><span data-stu-id="3bac4-272">ReportAction</span></span>|<span data-ttu-id="3bac4-273">可能的值如下：Render、Sort、BookMarkNavigation、DocumentNavigation、GetDocumentMap、Findstring</span><span class="sxs-lookup"><span data-stu-id="3bac4-273">Possible values: Render, Sort, BookMarkNavigation, DocumentNavigation, GetDocumentMap, Findstring</span></span>|  
|<span data-ttu-id="3bac4-274">TimeStart</span><span class="sxs-lookup"><span data-stu-id="3bac4-274">TimeStart</span></span>|<span data-ttu-id="3bac4-275">指出報表處理持續期間的開始與結束時間。</span><span class="sxs-lookup"><span data-stu-id="3bac4-275">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="3bac4-276">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="3bac4-276">TimeEnd</span></span>||  
|<span data-ttu-id="3bac4-277">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="3bac4-277">TimeDataRetrieval</span></span>|<span data-ttu-id="3bac4-278">擷取資料、處理報表和轉譯報表所花費的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="3bac4-278">Number of milliseconds spent retrieving the data, processing the report, and rendering the report.</span></span>|  
|<span data-ttu-id="3bac4-279">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="3bac4-279">TimeProcessing</span></span>||  
|<span data-ttu-id="3bac4-280">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="3bac4-280">TimeRendering</span></span>||  
|<span data-ttu-id="3bac4-281">來源</span><span class="sxs-lookup"><span data-stu-id="3bac4-281">Source</span></span>|<span data-ttu-id="3bac4-282">報表執行的來源 (1= 即時、2= 快取、3= 快照集、4= 記錄)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-282">Source of the report execution (1=Live, 2=Cache, 3=Snapshot, 4=History).</span></span>|  
|<span data-ttu-id="3bac4-283">狀態</span><span class="sxs-lookup"><span data-stu-id="3bac4-283">Status</span></span>|<span data-ttu-id="3bac4-284">狀態 (不是 rsSuccess 就是錯誤碼；如果發生多個錯誤，就只會記錄第一個錯誤)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-284">Status (either rsSuccess or an error code; if multiple errors occur, only the first error is recorded).</span></span>|  
|<span data-ttu-id="3bac4-285">ByteCount</span><span class="sxs-lookup"><span data-stu-id="3bac4-285">ByteCount</span></span>|<span data-ttu-id="3bac4-286">轉譯報表的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-286">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="3bac4-287">RowCount</span><span class="sxs-lookup"><span data-stu-id="3bac4-287">RowCount</span></span>|<span data-ttu-id="3bac4-288">從查詢傳回的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3bac4-288">Number of rows returned from queries.</span></span>|  
|<span data-ttu-id="3bac4-289">AdditionalInfo</span><span class="sxs-lookup"><span data-stu-id="3bac4-289">AdditionalInfo</span></span>|<span data-ttu-id="3bac4-290">XML 屬性包，其中包含有關執行的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3bac4-290">An XML property bag containing additional information about the execution.</span></span>|  
  
##  <a name="log-fields-executionlog"></a><a name="bkmk_executionlog"></a><span data-ttu-id="3bac4-291">記錄欄位 (ExecutionLog) </span><span class="sxs-lookup"><span data-stu-id="3bac4-291">Log Fields (ExecutionLog)</span></span>  
 <span data-ttu-id="3bac4-292">下面是可從 ExecutionLog 檢視中擷取資料列的範例 Transact SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3bac4-292">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog.</span></span> <span data-ttu-id="3bac4-293">此範例會假設報表伺服器資料庫名為 **ReportServer**：</span><span class="sxs-lookup"><span data-stu-id="3bac4-293">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog order by TimeStart DESC  
  
```  
  
 <span data-ttu-id="3bac4-294">下表描述在報表執行記錄中擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="3bac4-294">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="3bac4-295">資料行</span><span class="sxs-lookup"><span data-stu-id="3bac4-295">Column</span></span>|<span data-ttu-id="3bac4-296">描述</span><span class="sxs-lookup"><span data-stu-id="3bac4-296">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3bac4-297">InstanceName</span><span class="sxs-lookup"><span data-stu-id="3bac4-297">InstanceName</span></span>|<span data-ttu-id="3bac4-298">處理要求的報表伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="3bac4-298">Name of the report server instance that handled the request.</span></span>|  
|<span data-ttu-id="3bac4-299">ReportID</span><span class="sxs-lookup"><span data-stu-id="3bac4-299">ReportID</span></span>|<span data-ttu-id="3bac4-300">報表識別碼。</span><span class="sxs-lookup"><span data-stu-id="3bac4-300">Report identifier.</span></span>|  
|<span data-ttu-id="3bac4-301">UserName</span><span class="sxs-lookup"><span data-stu-id="3bac4-301">UserName</span></span>|<span data-ttu-id="3bac4-302">使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="3bac4-302">User identifier.</span></span>|  
|<span data-ttu-id="3bac4-303">RequestType</span><span class="sxs-lookup"><span data-stu-id="3bac4-303">RequestType</span></span>|<span data-ttu-id="3bac4-304">可能的值：</span><span class="sxs-lookup"><span data-stu-id="3bac4-304">Possible values:</span></span><br /><br /> <span data-ttu-id="3bac4-305">True= 訂閱要求</span><span class="sxs-lookup"><span data-stu-id="3bac4-305">True = A Subscription request</span></span><br /><br /> <span data-ttu-id="3bac4-306">False= 互動式要求</span><span class="sxs-lookup"><span data-stu-id="3bac4-306">False= An Interactive request</span></span>|  
|<span data-ttu-id="3bac4-307">格式</span><span class="sxs-lookup"><span data-stu-id="3bac4-307">Format</span></span>|<span data-ttu-id="3bac4-308">轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="3bac4-308">Rendering format.</span></span>|  
|<span data-ttu-id="3bac4-309">參數</span><span class="sxs-lookup"><span data-stu-id="3bac4-309">Parameters</span></span>|<span data-ttu-id="3bac4-310">報表執行所使用的參數值。</span><span class="sxs-lookup"><span data-stu-id="3bac4-310">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="3bac4-311">TimeStart</span><span class="sxs-lookup"><span data-stu-id="3bac4-311">TimeStart</span></span>|<span data-ttu-id="3bac4-312">指出報表處理持續期間的開始與結束時間。</span><span class="sxs-lookup"><span data-stu-id="3bac4-312">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="3bac4-313">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="3bac4-313">TimeEnd</span></span>||  
|<span data-ttu-id="3bac4-314">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="3bac4-314">TimeDataRetrieval</span></span>|<span data-ttu-id="3bac4-315">擷取資料、處理報表和轉譯報表所花費的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="3bac4-315">Number of milliseconds spent retrieving the data, processing the report, and rendering the report.</span></span>|  
|<span data-ttu-id="3bac4-316">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="3bac4-316">TimeProcessing</span></span>||  
|<span data-ttu-id="3bac4-317">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="3bac4-317">TimeRendering</span></span>||  
|<span data-ttu-id="3bac4-318">來源</span><span class="sxs-lookup"><span data-stu-id="3bac4-318">Source</span></span>|<span data-ttu-id="3bac4-319">報表執行的來源。</span><span class="sxs-lookup"><span data-stu-id="3bac4-319">Source of the report execution.</span></span> <span data-ttu-id="3bac4-320">可能的值如下：(1= 即時、2= 快取、3= 快照集、4= 記錄、5= 特定、6= 工作階段、7= RDCE)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-320">Possible values: (1=Live, 2=Cache, 3=Snapshot, 4=History, 5=Adhoc, 6=Session, 7=RDCE).</span></span>|  
|<span data-ttu-id="3bac4-321">狀態</span><span class="sxs-lookup"><span data-stu-id="3bac4-321">Status</span></span>|<span data-ttu-id="3bac4-322">可能的值如下：rsSuccess、rsProcessingAborted 或錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3bac4-322">Possible values: rsSuccess, rsProcessingAborted, or an error code.</span></span> <span data-ttu-id="3bac4-323">如果發生多個錯誤，只會記錄第一個錯誤。</span><span class="sxs-lookup"><span data-stu-id="3bac4-323">If multiple errors occur, only the first error is recorded.</span></span>|  
|<span data-ttu-id="3bac4-324">ByteCount</span><span class="sxs-lookup"><span data-stu-id="3bac4-324">ByteCount</span></span>|<span data-ttu-id="3bac4-325">轉譯報表的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="3bac4-325">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="3bac4-326">RowCount</span><span class="sxs-lookup"><span data-stu-id="3bac4-326">RowCount</span></span>|<span data-ttu-id="3bac4-327">從查詢傳回的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3bac4-327">Number of rows returned from queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bac4-328">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bac4-328">See Also</span></span>  
 <span data-ttu-id="3bac4-329">[開啟 SharePoint 追蹤記錄 &#40;ULS 的 Reporting Services 事件&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md) </span><span class="sxs-lookup"><span data-stu-id="3bac4-329">[Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md) </span></span>  
 <span data-ttu-id="3bac4-330">[Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="3bac4-330">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="3bac4-331">錯誤和事件參考 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3bac4-331">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
