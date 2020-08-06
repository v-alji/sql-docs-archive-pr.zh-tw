---
title: 開啟 SharePoint 追蹤記錄檔的 Reporting Services 事件 (ULS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81110ef6-4289-405c-a931-e7e9f49e69ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d1b0a936c234035baf18ca947661de2663195a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595624"
---
# <a name="turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls"></a><span data-ttu-id="6c7e7-102">Turn on Reporting Services events for the SharePoint trace log (ULS)</span><span class="sxs-lookup"><span data-stu-id="6c7e7-102">Turn on Reporting Services events for the SharePoint trace log (ULS)</span></span>
  <span data-ttu-id="6c7e7-103">從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]開始，SharePoint 模式的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 伺服器可以將 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 事件寫入 SharePoint 統一記錄服務 (ULS) 追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-103">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] servers in SharePoint mode can write [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] events to the SharePoint Unified Logging Service (ULS) trace log.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="6c7e7-104">特定類別目錄。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-104">specific categories are available on the Monitoring page of SharePoint Central Administration.</span></span>

 <span data-ttu-id="6c7e7-105">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-105">In this Topic:</span></span>

-   [<span data-ttu-id="6c7e7-106">一般 ULS 記錄建議</span><span class="sxs-lookup"><span data-stu-id="6c7e7-106">General ULS Log Recommendations</span></span>](#bkmk_general)

-   [<span data-ttu-id="6c7e7-107">開啟和關閉 Reporting Services 類別目錄中的 Reporting Services 事件</span><span class="sxs-lookup"><span data-stu-id="6c7e7-107">To turn on and off Reporting Services events in the Reporting Services Category</span></span>](#bkmk_turnon)

-   [<span data-ttu-id="6c7e7-108">建議組態</span><span class="sxs-lookup"><span data-stu-id="6c7e7-108">Recommended Configuration</span></span>](#bkmk_recommended)

-   [<span data-ttu-id="6c7e7-109">讀取記錄項目</span><span class="sxs-lookup"><span data-stu-id="6c7e7-109">Reading the logs entries</span></span>](#bkmk_readentries)

-   [<span data-ttu-id="6c7e7-110">SQL Server Reporting Services 事件清單</span><span class="sxs-lookup"><span data-stu-id="6c7e7-110">List of SQL Server Reporting Services Events</span></span>](#bkmk_list)

-   [<span data-ttu-id="6c7e7-111">利用 PowerShell 檢視記錄檔</span><span class="sxs-lookup"><span data-stu-id="6c7e7-111">View a Log file with PowerShell</span></span>](#bkmk_powershell)

-   [<span data-ttu-id="6c7e7-112">追蹤記錄位置</span><span class="sxs-lookup"><span data-stu-id="6c7e7-112">Trace Log Location</span></span>](#bkmk_trace)

##  <a name="general-uls-log-recommendations"></a><a name="bkmk_general"></a> <span data-ttu-id="6c7e7-113">一般 ULS 記錄建議</span><span class="sxs-lookup"><span data-stu-id="6c7e7-113">General ULS Log Recommendations</span></span>
 <span data-ttu-id="6c7e7-114">下表將針對監視 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 環境，列出建議的事件類別目錄和層級。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-114">The following table lists event categories and levels that are recommended for monitoring a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] environment..</span></span> <span data-ttu-id="6c7e7-115">記錄事件時，每個項目都會包含記錄事件的時間、處理序名稱，以及執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-115">When an event is logged, each entry includes the time the event was logged, the process name, and the thread ID.</span></span>

|<span data-ttu-id="6c7e7-116">類別</span><span class="sxs-lookup"><span data-stu-id="6c7e7-116">Category</span></span>|<span data-ttu-id="6c7e7-117">層級</span><span class="sxs-lookup"><span data-stu-id="6c7e7-117">Level</span></span>|<span data-ttu-id="6c7e7-118">描述</span><span class="sxs-lookup"><span data-stu-id="6c7e7-118">Description</span></span>|
|--------------|-----------|-----------------|
|<span data-ttu-id="6c7e7-119">資料庫</span><span class="sxs-lookup"><span data-stu-id="6c7e7-119">Database</span></span>|<span data-ttu-id="6c7e7-120">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="6c7e7-120">Verbose</span></span>|<span data-ttu-id="6c7e7-121">記錄涉及資料庫存取權的事件。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-121">Logs events that involve database access.</span></span>|
|<span data-ttu-id="6c7e7-122">一般</span><span class="sxs-lookup"><span data-stu-id="6c7e7-122">General</span></span>|<span data-ttu-id="6c7e7-123">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="6c7e7-123">Verbose</span></span>|<span data-ttu-id="6c7e7-124">記錄涉及下列項目之存取權的事件：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-124">Logs events that involve access to the following items:</span></span><br /><br /> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="6c7e7-125">網頁</span><span class="sxs-lookup"><span data-stu-id="6c7e7-125">Web pages</span></span><br /><br /> <span data-ttu-id="6c7e7-126">報表檢視器 HTTP 處理常式</span><span class="sxs-lookup"><span data-stu-id="6c7e7-126">Report Viewer HTTP handler</span></span><br /><br /> <span data-ttu-id="6c7e7-127">報表存取 (.rdl 檔)</span><span class="sxs-lookup"><span data-stu-id="6c7e7-127">Report access (.rdl files)</span></span><br /><br /> <span data-ttu-id="6c7e7-128">資料來源 (.rsds 檔)</span><span class="sxs-lookup"><span data-stu-id="6c7e7-128">Data sources (.rsds files)</span></span><br /><br /> <span data-ttu-id="6c7e7-129">SharePoint 網站的 URL (.smdl 檔)</span><span class="sxs-lookup"><span data-stu-id="6c7e7-129">URLs on the SharePoint site (.smdl files)</span></span>|
|<span data-ttu-id="6c7e7-130">Office Server 一般</span><span class="sxs-lookup"><span data-stu-id="6c7e7-130">Office Server General</span></span>|<span data-ttu-id="6c7e7-131">例外狀況</span><span class="sxs-lookup"><span data-stu-id="6c7e7-131">Exception</span></span>|<span data-ttu-id="6c7e7-132">記錄登入失敗。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-132">Logs logon failures.</span></span>|
|<span data-ttu-id="6c7e7-133">拓撲</span><span class="sxs-lookup"><span data-stu-id="6c7e7-133">Topology</span></span>|<span data-ttu-id="6c7e7-134">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="6c7e7-134">Verbose</span></span>|<span data-ttu-id="6c7e7-135">記錄目前的使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-135">Logs current user information.</span></span>|
|<span data-ttu-id="6c7e7-136">Web 組件</span><span class="sxs-lookup"><span data-stu-id="6c7e7-136">Web Parts</span></span>|<span data-ttu-id="6c7e7-137">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="6c7e7-137">Verbose</span></span>|<span data-ttu-id="6c7e7-138">記錄涉及報表檢視器 Web 組件之存取權的事件。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-138">Logs events that involve access to the Report Viewer Web Part.</span></span>|

##  <a name="to-turn-on-and-off-reporting-services-events-in-the-reporting-services-category"></a><a name="bkmk_turnon"></a> <span data-ttu-id="6c7e7-139">開啟和關閉 Reporting Services 類別目錄中的 Reporting Services 事件</span><span class="sxs-lookup"><span data-stu-id="6c7e7-139">To turn on and off Reporting Services events in the Reporting Services Category</span></span>

1.  <span data-ttu-id="6c7e7-140">在 SharePoint 管理中心內</span><span class="sxs-lookup"><span data-stu-id="6c7e7-140">From SharePoint Central Administration</span></span>

2.  <span data-ttu-id="6c7e7-141">按一下 **[監視]** 。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-141">Click **Monitoring**.</span></span>

3.  <span data-ttu-id="6c7e7-142">按一下 **[報表]** 群組中的 **[設定診斷記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-142">Click **Configure Diagnostic Logging** in the **Reporting** group.</span></span>

4.  <span data-ttu-id="6c7e7-143">在類別目錄清單中找到 **[SQL Server Reporting Services]** 。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-143">Find **SQL Server Reporting Services** in the category list.</span></span>

5.  <span data-ttu-id="6c7e7-144">按一下加號 (+) 展開 **[SQL Server Reporting Services]** 之下的子類別目錄。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-144">Click the plus symbol (+) to expand the sub categories under **SQL Server Reporting Services**.</span></span>

6.  <span data-ttu-id="6c7e7-145">選取要加入至追蹤記錄的子類別目錄。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-145">Select the subcategories to be added to the trace log.</span></span>

7.  <span data-ttu-id="6c7e7-146">在類別目錄清單的底部，選取 **[回報至追蹤記錄的最低緊急事件]** 的事件等級。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-146">At the bottom of the categories list, select an event level for the **Least critical event to report to the trace log**.</span></span> <span data-ttu-id="6c7e7-147">選取 **[無]** 停用追蹤。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-147">Select **None** to disable tracing.</span></span>

> [!NOTE]
>  <span data-ttu-id="6c7e7-148">**不支援** [回報至追蹤記錄的最低緊急事件] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]選項。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-148">The option **Least critical event to report to the event log** is not supported by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="6c7e7-149">已忽略此選項。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-149">The option is ignored.</span></span>

##  <a name="recommended-configuration"></a><a name="bkmk_recommended"></a> <span data-ttu-id="6c7e7-150">建議組態</span><span class="sxs-lookup"><span data-stu-id="6c7e7-150">Recommended Configuration</span></span>
 <span data-ttu-id="6c7e7-151">建議您使用下列記錄選項做為標準組態：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-151">The following logging options are recommended as a standard configuration:</span></span>

-   <span data-ttu-id="6c7e7-152">**HTTP 重新導向程式**</span><span class="sxs-lookup"><span data-stu-id="6c7e7-152">**HTTP Redirector**</span></span>

-   <span data-ttu-id="6c7e7-153">**SOAP 用戶端 Proxy**</span><span class="sxs-lookup"><span data-stu-id="6c7e7-153">**SOAP Client Proxy**</span></span>

-   <span data-ttu-id="6c7e7-154">如果您遇到組態設定方面的問題，請加入 **[組態頁面]** 。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-154">If you are experiencing issues with configuration, add **Configuration Pages**.</span></span>

 <span data-ttu-id="6c7e7-155">您可以使用下列 PowerShell 指令程式來檢閱所有目前伺服器陣列診斷記錄設定：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-155">You can review all of the current farm diagnostic log settings with the following PowerShell cmdlet:</span></span>

```powershell
Get-SPDiagnosticConfig
```

##  <a name="reading-the-logs-entries"></a><a name="bkmk_readentries"></a> <span data-ttu-id="6c7e7-156">讀取記錄項目</span><span class="sxs-lookup"><span data-stu-id="6c7e7-156">Reading the logs entries</span></span>
 <span data-ttu-id="6c7e7-157">記錄中的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 項目會以下列方式格式化。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-157">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] entries in the log are formatted in the following way.</span></span>

1.  <span data-ttu-id="6c7e7-158">**產品：SQL Server Reporting Services**</span><span class="sxs-lookup"><span data-stu-id="6c7e7-158">**Product:SQL Server Reporting Services**</span></span>

2.  <span data-ttu-id="6c7e7-159">**類別目錄：** 與伺服器相關的事件其名稱開頭會有 "Report Server" 字元。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-159">**Category:** Events related to the server will have the characters "Report Server", at the beginning of the name.</span></span> <span data-ttu-id="6c7e7-160">例如 "Report Server Alerting Runtime"，這些事件會記錄到報表伺服器記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-160">For example "Report Server Alerting Runtime" These events are also logged to the report server log files.</span></span>

3.  <span data-ttu-id="6c7e7-161">**類別目錄：** 與 Web 前端元件相關或從中進行通訊的事件不會包含 "Report Server"。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-161">**Category:** Events related to or communicated from a web front-end component do not contain "Report Server".</span></span> <span data-ttu-id="6c7e7-162">例如 "Service Application Proxy"、"Report Server Alerting Runtime"。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-162">For example "Service Application Proxy" Report Server Alerting Runtime".</span></span> <span data-ttu-id="6c7e7-163">WFE 項目會包含 CorrelationID，但伺服器項目不會包含。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-163">The WFE entries do contain a CorrelationID but the server entries do not.</span></span>

##  <a name="list-of-sql-server-reporting-services-events"></a><a name="bkmk_list"></a> <span data-ttu-id="6c7e7-164">SQL Server Reporting Services 事件清單</span><span class="sxs-lookup"><span data-stu-id="6c7e7-164">List of SQL Server Reporting Services Events</span></span>
 <span data-ttu-id="6c7e7-165">下表為 SQL Server Reporting Services 類別目錄中事件的清單：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-165">The following table is a list of the events in the SQL Server Reporting Services Category:</span></span>

|<span data-ttu-id="6c7e7-166">區域名稱</span><span class="sxs-lookup"><span data-stu-id="6c7e7-166">Area Name</span></span>|<span data-ttu-id="6c7e7-167">描述或範例項目</span><span class="sxs-lookup"><span data-stu-id="6c7e7-167">Description or sample entries</span></span>|
|---------------|-----------------------------------|
|<span data-ttu-id="6c7e7-168">[組態頁面]</span><span class="sxs-lookup"><span data-stu-id="6c7e7-168">Configuration Pages</span></span>||
|<span data-ttu-id="6c7e7-169">HTTP 重新導向程式</span><span class="sxs-lookup"><span data-stu-id="6c7e7-169">HTTP Redirector</span></span>||
|<span data-ttu-id="6c7e7-170">本機模式處理</span><span class="sxs-lookup"><span data-stu-id="6c7e7-170">Local Mode Processing</span></span>||
|<span data-ttu-id="6c7e7-171">本機模式轉譯</span><span class="sxs-lookup"><span data-stu-id="6c7e7-171">Local Mode Rendering</span></span>||
|<span data-ttu-id="6c7e7-172">SOAP 用戶端 Proxy</span><span class="sxs-lookup"><span data-stu-id="6c7e7-172">SOAP Client Proxy</span></span>||
|<span data-ttu-id="6c7e7-173">UI 頁面</span><span class="sxs-lookup"><span data-stu-id="6c7e7-173">UI Pages</span></span>||
|<span data-ttu-id="6c7e7-174">Power View</span><span class="sxs-lookup"><span data-stu-id="6c7e7-174">Power View</span></span>|<span data-ttu-id="6c7e7-175">已寫入 **LogClientTraceEvents** API 中的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-175">Log entries that were written to the **LogClientTraceEvents** API.</span></span> <span data-ttu-id="6c7e7-176">這些專案來自于用戶端應用程式，包括 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 適用于 Enterprise Edition 之增益集的功能 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-176">These entries are sourced from client applications, including [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.</span></span><br /><br /> <span data-ttu-id="6c7e7-177">所有來自於 LogClientTraceEvents API 的記錄項目都會記錄在 "SQL Server Reporting Services" [類別目錄]  和 "Power View" [區域]  之下。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-177">All log entries from the LogClientTraceEvents API will be logged under the **Category** of "SQL Server Reporting Services" and the **Area** of "Power View".</span></span><br /><br /> <span data-ttu-id="6c7e7-178">使用 "Power View" 區域所記錄的項目內容是由用戶端應用程式所決定。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-178">The content of entries logged with the area of "Power View" is determined by the client application.</span></span>|
|<span data-ttu-id="6c7e7-179">報表伺服器警示執行階段</span><span class="sxs-lookup"><span data-stu-id="6c7e7-179">Report Server Alerting Runtime</span></span>||
|<span data-ttu-id="6c7e7-180">報表伺服器應用程式定義域管理員</span><span class="sxs-lookup"><span data-stu-id="6c7e7-180">Report Server App Domain Manager</span></span>||
|<span data-ttu-id="6c7e7-181">報表伺服器緩衝回應</span><span class="sxs-lookup"><span data-stu-id="6c7e7-181">Report Server Buffered Response</span></span>||
|<span data-ttu-id="6c7e7-182">報表伺服器快取</span><span class="sxs-lookup"><span data-stu-id="6c7e7-182">Report Server Cache</span></span>||
|<span data-ttu-id="6c7e7-183">報表伺服器目錄</span><span class="sxs-lookup"><span data-stu-id="6c7e7-183">Report Server Catalog</span></span>||
|<span data-ttu-id="6c7e7-184">報表伺服器區塊</span><span class="sxs-lookup"><span data-stu-id="6c7e7-184">Report Server Chunk</span></span>||
|<span data-ttu-id="6c7e7-185">報表伺服器清除</span><span class="sxs-lookup"><span data-stu-id="6c7e7-185">Report Server Cleanup</span></span>||
|<span data-ttu-id="6c7e7-186">報表伺服器組態管理員</span><span class="sxs-lookup"><span data-stu-id="6c7e7-186">Report Server Configuration Manager</span></span>|<span data-ttu-id="6c7e7-187">範例項目：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-187">Sample entries:</span></span><br /><br /> <span data-ttu-id="6c7e7-188">MediumUsing 報表伺服器內部 URL http://localhost:80/ReportServer。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-188">MediumUsing report server internal url http://localhost:80/ReportServer.</span></span><br /><br /> <span data-ttu-id="6c7e7-189">UnexpectedMissing 或是無效的 ExtendedProtectionLevel 設定</span><span class="sxs-lookup"><span data-stu-id="6c7e7-189">UnexpectedMissing or Invalid ExtendedProtectionLevel setting</span></span>|
|<span data-ttu-id="6c7e7-190">報表伺服器密碼編譯</span><span class="sxs-lookup"><span data-stu-id="6c7e7-190">Report Server Crypto</span></span>||
|<span data-ttu-id="6c7e7-191">報表伺服器資料延伸模組</span><span class="sxs-lookup"><span data-stu-id="6c7e7-191">Report Server Data Extension</span></span>||
|<span data-ttu-id="6c7e7-192">報表伺服器資料庫輪詢</span><span class="sxs-lookup"><span data-stu-id="6c7e7-192">Report Server DB Polling</span></span>||
|<span data-ttu-id="6c7e7-193">報表伺服器預設值</span><span class="sxs-lookup"><span data-stu-id="6c7e7-193">Report Server Default</span></span>||
|<span data-ttu-id="6c7e7-194">報表伺服器電子郵件延伸模組</span><span class="sxs-lookup"><span data-stu-id="6c7e7-194">Report Server Email Extension</span></span>||
|<span data-ttu-id="6c7e7-195">報表伺服器 Excel 轉譯器</span><span class="sxs-lookup"><span data-stu-id="6c7e7-195">Report Server Excel Renderer</span></span>||
|<span data-ttu-id="6c7e7-196">報表伺服器延伸模組 Factory</span><span class="sxs-lookup"><span data-stu-id="6c7e7-196">Report Server Extension Factory</span></span>||
|<span data-ttu-id="6c7e7-197">報表伺服器 HTTP 執行階段</span><span class="sxs-lookup"><span data-stu-id="6c7e7-197">Report Server HTTP Runtime</span></span>||
|<span data-ttu-id="6c7e7-198">報表伺服器影像轉譯器</span><span class="sxs-lookup"><span data-stu-id="6c7e7-198">Report Server Image Renderer</span></span>||
|<span data-ttu-id="6c7e7-199">報表伺服器記憶體監控</span><span class="sxs-lookup"><span data-stu-id="6c7e7-199">Report Server Memory Monitoring</span></span>||
|<span data-ttu-id="6c7e7-200">報表伺服器通知</span><span class="sxs-lookup"><span data-stu-id="6c7e7-200">Report Server Notification</span></span>||
|<span data-ttu-id="6c7e7-201">報表伺服器處理</span><span class="sxs-lookup"><span data-stu-id="6c7e7-201">Report Server Processing</span></span>||
|<span data-ttu-id="6c7e7-202">報表伺服器提供者</span><span class="sxs-lookup"><span data-stu-id="6c7e7-202">Report Server Provider</span></span>||
|<span data-ttu-id="6c7e7-203">報表伺服器轉譯</span><span class="sxs-lookup"><span data-stu-id="6c7e7-203">Report Server Rendering</span></span>||
|<span data-ttu-id="6c7e7-204">報表伺服器報表預覽</span><span class="sxs-lookup"><span data-stu-id="6c7e7-204">Report Server Report Preview</span></span>||
|<span data-ttu-id="6c7e7-205">報表伺服器資源公用程式</span><span class="sxs-lookup"><span data-stu-id="6c7e7-205">Report Server Resource Utility</span></span>|<span data-ttu-id="6c7e7-206">範例項目：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-206">Sample Entries:</span></span><br /><br /> <span data-ttu-id="6c7e7-207">MediumReporting Services 啟動 SKU：評估版</span><span class="sxs-lookup"><span data-stu-id="6c7e7-207">MediumReporting Services starting SKU: Evaluation</span></span><br /><br /> <span data-ttu-id="6c7e7-208">MediumEvaluation 複本：剩下 180 天</span><span class="sxs-lookup"><span data-stu-id="6c7e7-208">MediumEvaluation copy: 180 days left</span></span>|
|<span data-ttu-id="6c7e7-209">報表伺服器執行工作</span><span class="sxs-lookup"><span data-stu-id="6c7e7-209">Report Server Running Jobs</span></span>||
|<span data-ttu-id="6c7e7-210">報表伺服器執行要求</span><span class="sxs-lookup"><span data-stu-id="6c7e7-210">Report Server Running Requests</span></span>||
|<span data-ttu-id="6c7e7-211">報表伺服器排程</span><span class="sxs-lookup"><span data-stu-id="6c7e7-211">Report Server Schedule</span></span>||
|<span data-ttu-id="6c7e7-212">報表伺服器安全性</span><span class="sxs-lookup"><span data-stu-id="6c7e7-212">Report Server Security</span></span>||
|<span data-ttu-id="6c7e7-213">報表伺服器服務控制器</span><span class="sxs-lookup"><span data-stu-id="6c7e7-213">Report Server Service Controller</span></span>||
|<span data-ttu-id="6c7e7-214">報表伺服器工作階段</span><span class="sxs-lookup"><span data-stu-id="6c7e7-214">Report Server Session</span></span>||
|<span data-ttu-id="6c7e7-215">報表伺服器訂閱</span><span class="sxs-lookup"><span data-stu-id="6c7e7-215">Report Server Subscription</span></span>||
|<span data-ttu-id="6c7e7-216">報表伺服器 WCF 執行階段</span><span class="sxs-lookup"><span data-stu-id="6c7e7-216">Report Server WCF Runtime</span></span>||
|<span data-ttu-id="6c7e7-217">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="6c7e7-217">Report Server Web Server</span></span>||
|<span data-ttu-id="6c7e7-218">服務應用程式 Proxy</span><span class="sxs-lookup"><span data-stu-id="6c7e7-218">Service Application Proxy</span></span>||
|<span data-ttu-id="6c7e7-219">共用服務</span><span class="sxs-lookup"><span data-stu-id="6c7e7-219">Shared Service</span></span>|<span data-ttu-id="6c7e7-220">範例項目：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-220">Sample entries:</span></span><br /><br /> <span data-ttu-id="6c7e7-221">MediumUpdating ReportingWebServiceApplication</span><span class="sxs-lookup"><span data-stu-id="6c7e7-221">MediumUpdating ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="6c7e7-222">MediumGranting 對內容資料庫的存取。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-222">MediumGranting access to content databases.</span></span><br /><br /> <span data-ttu-id="6c7e7-223">ReportingWebServiceApplication 的 MediumProvisioning 執行個體</span><span class="sxs-lookup"><span data-stu-id="6c7e7-223">MediumProvisioning instances for ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="6c7e7-224">ReportingWebServiceApplication 的 MediumProcessing 服務帳戶變更</span><span class="sxs-lookup"><span data-stu-id="6c7e7-224">MediumProcessing service account change for ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="6c7e7-225">MediumSetting 資料庫權限。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-225">MediumSetting database permissions.</span></span>|

##  <a name="view-a-log-file-with-powershell"></a><a name="bkmk_powershell"></a> <span data-ttu-id="6c7e7-226">利用 PowerShell 檢視記錄檔</span><span class="sxs-lookup"><span data-stu-id="6c7e7-226">View a Log file with PowerShell</span></span>
 <span data-ttu-id="6c7e7-227">![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容")您可以使用 PowerShell 從 ULS 記錄檔傳回 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 相關事件的清單。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-227">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")You can use PowerShell to return a list of the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] related events from a ULS Log file.</span></span> <span data-ttu-id="6c7e7-228">從 SharePoint 2010 管理命令介面鍵入下列命令，從包含 "**sql server reporting services**" 的 ULS 記錄檔 UESQL11SPOINT-20110606-1530.log 傳回已篩選資料列清單：</span><span class="sxs-lookup"><span data-stu-id="6c7e7-228">Type the following command from the SharePoint 2010 Management Shell to return a filtered list of rows from the file a ULS log file UESQL11SPOINT-20110606-1530.log, that contain "**sql server reporting services**":</span></span>

```powershell
Get-Content -Path "C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS\UESQL11SPOINT-20110606-1530.log" | Select-String "sql server reporting services"
```

 <span data-ttu-id="6c7e7-229">您可以下載多種可用來讀取 ULS 記錄的工具。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-229">There are also many tools you can download which will allow you read ULS logs.</span></span> <span data-ttu-id="6c7e7-230">例如， [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) 或 [SharePoint ULS 記錄檢視器](http://ulsviewer.codeplex.com/workitem/list/basic)。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-230">For example, the [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) or [SharePoint ULS Log Viewer](http://ulsviewer.codeplex.com/workitem/list/basic).</span></span> <span data-ttu-id="6c7e7-231">兩者都在 CodePlex 上提供。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-231">Both are available on CodePlex.</span></span>

 <span data-ttu-id="6c7e7-232">如需有關如何使用 PowerShell 來檢視記錄資料的詳細資訊，請參閱 [檢視診斷記錄 (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx)</span><span class="sxs-lookup"><span data-stu-id="6c7e7-232">For more information on how to use PowerShell to view log data, see [View diagnostic logs (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx)</span></span>

##  <a name="trace-log-location"></a><a name="bkmk_trace"></a><span data-ttu-id="6c7e7-233">追蹤記錄檔位置</span><span class="sxs-lookup"><span data-stu-id="6c7e7-233">Trace Log Location</span></span>
 <span data-ttu-id="6c7e7-234">追蹤記錄檔通常位於 **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** 資料夾中，但是您可以從 SharePoint 管理中心的 **[診斷記錄]** 頁面中驗證或變更此路徑。</span><span class="sxs-lookup"><span data-stu-id="6c7e7-234">The Trace Log files are usually found in the folder **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** but you can verify or change the path from the **Diagnostic Logging** page in SharePoint Central Administration.</span></span>

