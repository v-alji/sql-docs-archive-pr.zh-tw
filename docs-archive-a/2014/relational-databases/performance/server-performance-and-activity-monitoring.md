---
title: 伺服器效能與活動監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- activity monitoring [SQL Server]
- traces [SQL Server], how-to topics
- monitoring server performance [SQL Server], activity monitoring
- stored procedures [SQL Server], traces
- performance [SQL Server], servers
- servers [SQL Server], performance
- SQL Server Profiler, how-to topics
- SQL Server Management Studio [SQL Server], monitoring system
- Profiler [SQL Server Profiler], how-to topics
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a0fa7902d68c587a7733f07ceb8daccd3a6a98fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606809"
---
# <a name="server-performance-and-activity-monitoring"></a><span data-ttu-id="8b130-102">伺服器效能與活動監視</span><span class="sxs-lookup"><span data-stu-id="8b130-102">Server Performance and Activity Monitoring</span></span>
  <span data-ttu-id="8b130-103">監視資料庫的目標在於評估伺服器的執行效能。</span><span class="sxs-lookup"><span data-stu-id="8b130-103">The goal of monitoring databases is to assess how a server is performing.</span></span> <span data-ttu-id="8b130-104">有效的監視包括定期建立目前效能的快照集以隔離造成問題的處理序，以及持續蒐集資料來追蹤效能趨勢。</span><span class="sxs-lookup"><span data-stu-id="8b130-104">Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="8b130-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 作業系統提供公用程式，可讓您檢視資料庫的目前狀況並隨著狀況變更來追蹤效能。</span><span class="sxs-lookup"><span data-stu-id="8b130-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows operating system provide utilities that let you view the current condition of the database and to track performance as conditions change.</span></span>  
  
 <span data-ttu-id="8b130-106">下節包含說明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 的效能與活動監視工具的主題。</span><span class="sxs-lookup"><span data-stu-id="8b130-106">The following section contains topics that describe how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows performance and activity monitoring tools.</span></span> <span data-ttu-id="8b130-107">它包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="8b130-107">It contains the following topics:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b130-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="8b130-108">In This Section</span></span>  
 <span data-ttu-id="8b130-109">**若要使用 Windows 工具執行監視工作**</span><span class="sxs-lookup"><span data-stu-id="8b130-109">**To perform monitoring tasks with Windows tools**</span></span>  
  
-   [<span data-ttu-id="8b130-110">啟動系統監視器 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-110">Start System Monitor &#40;Windows&#41;</span></span>](start-system-monitor-windows.md)  
  
-   [<span data-ttu-id="8b130-111">檢視 Windows 應用程式記錄檔 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-111">View the Windows Application Log &#40;Windows&#41;</span></span>](view-the-windows-application-log-windows-10.md)  
  
 <span data-ttu-id="8b130-112">**若要使用 Windows 工具建立 SQL Server 資料庫警示**</span><span class="sxs-lookup"><span data-stu-id="8b130-112">**To create SQL Server database alerts with Windows tools**</span></span>  
  
-   [<span data-ttu-id="8b130-113">設定 SQL Server 資料庫警示 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-113">Set Up a SQL Server Database Alert &#40;Windows&#41;</span></span>](set-up-a-sql-server-database-alert-windows.md)  
  
 <span data-ttu-id="8b130-114">**若要使用 SQL Server Management Studio 執行監視工作**</span><span class="sxs-lookup"><span data-stu-id="8b130-114">**To perform monitoring tasks with SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="8b130-115">檢視 SQL Server 錯誤記錄檔 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-115">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="8b130-116">開啟活動監視器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-116">Open Activity Monitor &#40;SQL Server Management Studio&#41;</span></span>](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)  
  
 <span data-ttu-id="8b130-117">**若要使用 Transact-SQL 預存程序透過 SQL 追蹤執行監視工作**</span><span class="sxs-lookup"><span data-stu-id="8b130-117">**To perform monitoring tasks with SQL Trace by using Transact-SQL stored procedures**</span></span>  
  
-   [<span data-ttu-id="8b130-118">建立追蹤 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-118">Create a Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/create-a-trace-transact-sql.md)  
  
-   [<span data-ttu-id="8b130-119">設定追蹤篩選 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-119">Set a Trace Filter &#40;Transact-SQL&#41;</span></span>](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)  
  
-   [<span data-ttu-id="8b130-120">修改現有的追蹤 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-120">Modify an Existing Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/modify-an-existing-trace-transact-sql.md)  
  
-   [<span data-ttu-id="8b130-121">檢視已儲存的追蹤 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-121">View a Saved Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/view-a-saved-trace-transact-sql.md)  
  
-   [<span data-ttu-id="8b130-122">檢視篩選資訊 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-122">View Filter Information &#40;Transact-SQL&#41;</span></span>](../sql-trace/view-filter-information-transact-sql.md)  
  
-   [<span data-ttu-id="8b130-123">刪除追蹤 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-123">Delete a Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/delete-a-trace-transact-sql.md)  
  
 <span data-ttu-id="8b130-124">**若要使用 SQL Server Profiler 建立和修改追蹤**</span><span class="sxs-lookup"><span data-stu-id="8b130-124">**To create and modify traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="8b130-125">建立追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-125">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-126">設定全域追蹤選項 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-126">Set Global Trace Options &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-127">指定追蹤檔案的事件及資料行 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-127">Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-128">建立 Transact-SQL 指令碼以執行追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-128">Create a Transact-SQL Script for Running a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-129">將追蹤結果儲存至檔案 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-129">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-130">設定追蹤檔案的檔案大小上限 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-130">Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-131">將追蹤結果儲存到資料表 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-131">Save Trace Results to a Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-132">設定追蹤資料表的資料表大小上限 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-132">Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-133">篩選追蹤中的事件 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-133">Filter Events in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-134">檢視篩選資訊 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-134">View Filter Information &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-135">修改篩選 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-135">Modify a Filter &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-136">根據事件開始時間篩選事件 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-136">Filter Events Based on the Event Start Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-137">根據事件結束時間篩選事件 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-137">Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-138">篩選追蹤中的伺服器處理序識別碼 &#40;SPIDs&#41; &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-138">Filter Server Process IDs &#40;SPIDs&#41; in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-139">組織追蹤內顯示的資料行 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-139">Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)  
  
 <span data-ttu-id="8b130-140">**若要使用 SQL Server Profiler 啟動、暫停和停止追蹤**</span><span class="sxs-lookup"><span data-stu-id="8b130-140">**To start, pause, and stop traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="8b130-141">在連接伺服器之後自動啟動追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-141">Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-142">暫停追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-142">Pause a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-143">停止追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-143">Stop a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-144">在追蹤暫停或停止之後執行追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-144">Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
 <span data-ttu-id="8b130-145">**使用 SQL Server Profiler 開啟追蹤並設定顯示追蹤的方式**</span><span class="sxs-lookup"><span data-stu-id="8b130-145">**To open traces and configure how traces are displayed by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="8b130-146">開啟追蹤檔案 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-146">Open a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-147">開啟追蹤資料表 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-147">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-148">清除追蹤視窗 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-148">Clear a Trace Window &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-149">關閉追蹤視窗 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-149">Close a Trace Window &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-150">設定追蹤定義預設值 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-150">Set Trace Definition Defaults &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-151">設定追蹤顯示預設值 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-151">Set Trace Display Defaults &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 <span data-ttu-id="8b130-152">**若要使用 SQL Server Profiler 重新執行追蹤**</span><span class="sxs-lookup"><span data-stu-id="8b130-152">**To replay traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="8b130-153">重新執行追蹤檔案 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-153">Replay a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-154">重新執行追蹤資料表 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-154">Replay a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-155">一次重新執行一個事件 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-155">Replay a Single Event at a Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-156">重新執行至中斷點 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-156">Replay to a Breakpoint &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-157">重新執行至資料指標處 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-157">Replay to a Cursor &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-158">重新執行 Transact-SQL 指令碼 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-158">Replay a Transact-SQL Script &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)  
  
 <span data-ttu-id="8b130-159">**使用 SQL Server Profiler 建立、修改和使用追蹤範本**</span><span class="sxs-lookup"><span data-stu-id="8b130-159">**To create, modify, and use trace templates by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="8b130-160">建立追蹤範本 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-160">Create a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-161">修改追蹤範本 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-161">Modify a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-162">從執行中的追蹤衍生範本 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-162">Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-163">從追蹤檔案或追蹤資料表衍生範本 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-163">Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-164">匯出追蹤範本 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-164">Export a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-165">匯入追蹤範本 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-165">Import a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)  
  
 <span data-ttu-id="8b130-166">**若要使用 SQL Server Profiler 追蹤來收集和監視伺服器效能**</span><span class="sxs-lookup"><span data-stu-id="8b130-166">**To use SQL Server Profiler traces to collect and monitor server performance**</span></span>  
  
-   [<span data-ttu-id="8b130-167">在追蹤時尋找值或資料行 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-167">Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-168">儲存死結圖形 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-168">Save Deadlock Graphs &#40;SQL Server Profiler&#41;</span></span>](save-deadlock-graphs-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-169">個別儲存執行程序表 XML 事件 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-169">Save Showplan XML Events Separately &#40;SQL Server Profiler&#41;</span></span>](save-showplan-xml-events-separately-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-170">個別儲存執行程序表 XML 統計資料設定檔事件 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-170">Save Showplan XML Statistics Profile Events Separately &#40;SQL Server Profiler&#41;</span></span>](save-showplan-xml-statistics-profile-events-separately-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-171">從追蹤中擷取指令碼 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-171">Extract a Script from a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="8b130-172">使追蹤與 Windows 效能記錄資料產生相互關聯 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8b130-172">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
