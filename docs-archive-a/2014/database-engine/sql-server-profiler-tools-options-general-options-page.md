---
title: SQL Server Profiler-[工具]-[選項] ([一般選項] 頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.generaloptions.f1
helpviewer_keywords:
- General Options dialog box
ms.assetid: a888246d-ccfe-415f-bbdc-d6adafac250a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fad4d3529482835367898276a973bd7c8827b553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597986"
---
# <a name="sql-server-profiler---tools-options-general-options-page"></a><span data-ttu-id="4e338-102">SQL Server Profiler-[工具]-[選項] ([一般選項] 頁面) </span><span class="sxs-lookup"><span data-stu-id="4e338-102">SQL Server Profiler - Tools-Options (General Options Page)</span></span>
  <span data-ttu-id="4e338-103">使用 [一般選項]\*\*\*\* 對話方塊來檢視或指定下列選項。</span><span class="sxs-lookup"><span data-stu-id="4e338-103">Use the **General Options** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4e338-104">選項</span><span class="sxs-lookup"><span data-stu-id="4e338-104">Options</span></span>  
  
### <a name="display-options"></a><span data-ttu-id="4e338-105">顯示選項</span><span class="sxs-lookup"><span data-stu-id="4e338-105">Display Options</span></span>  
 <span data-ttu-id="4e338-106">**字型名稱**</span><span class="sxs-lookup"><span data-stu-id="4e338-106">**Font name**</span></span>  
 <span data-ttu-id="4e338-107">顯示追蹤期間在追蹤結果方格中所使用的字型名稱。</span><span class="sxs-lookup"><span data-stu-id="4e338-107">Displays the name of the font used in the trace results grid during traces.</span></span>  
  
 <span data-ttu-id="4e338-108">**字型大小**</span><span class="sxs-lookup"><span data-stu-id="4e338-108">**Font size**</span></span>  
 <span data-ttu-id="4e338-109">顯示追蹤期間在追蹤結果方格中所使用的字型大小。</span><span class="sxs-lookup"><span data-stu-id="4e338-109">Displays the size of the font used in the trace results grid during traces.</span></span>  
  
 <span data-ttu-id="4e338-110">**選擇字型**</span><span class="sxs-lookup"><span data-stu-id="4e338-110">**Choose Font**</span></span>  
 <span data-ttu-id="4e338-111">開啟變更字型設定值的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4e338-111">Opens a dialog to change the font settings.</span></span>  
  
 <span data-ttu-id="4e338-112">**使用地區設定顯示日期和時間值**</span><span class="sxs-lookup"><span data-stu-id="4e338-112">**Use regional settings to display date and time values**</span></span>  
 <span data-ttu-id="4e338-113">顯示此電腦之地區設定中所設定的日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="4e338-113">Displays date and time values in regional settings configured for your computer.</span></span> <span data-ttu-id="4e338-114">如果未選取此選項，就會以 Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]所用的固定格式來顯示日期和時間值，其中包含毫秒。</span><span class="sxs-lookup"><span data-stu-id="4e338-114">If you do not select this option, the date and time values are displayed in the fixed format used by Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], which includes milliseconds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e338-115">切換此核取方塊可變更時間資料行的顯示格式，例如 **StartTime** 和 **EndTime**。</span><span class="sxs-lookup"><span data-stu-id="4e338-115">Toggling this checkbox changes the time columns display format such as **StartTime** and **EndTime**.</span></span> <span data-ttu-id="4e338-116">但是，此操作不會變更語言事件或遠端程序呼叫 (RPC) 中的 **DateTime** 值參數。</span><span class="sxs-lookup"><span data-stu-id="4e338-116">However, it does not change the **DateTime** value parameters inside the language events or remote procedure calls (RPCs).</span></span>  
  
 <span data-ttu-id="4e338-117">**顯示 [持續時間] 資料行中的值 (以百萬分之一秒為單位)。**</span><span class="sxs-lookup"><span data-stu-id="4e338-117">**Show values in Duration column in microseconds**</span></span>  
 <span data-ttu-id="4e338-118">以百萬分之一秒顯示追蹤的 [持續時間]\*\*\*\* 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="4e338-118">Displays the values in microseconds in the **Duration** data column of traces.</span></span> <span data-ttu-id="4e338-119">依預設，[持續時間]\*\*\*\* 資料行會以毫秒為單位顯示值。</span><span class="sxs-lookup"><span data-stu-id="4e338-119">By default, the **Duration** column displays values in milliseconds.</span></span>  
  
### <a name="tracing-options"></a><span data-ttu-id="4e338-120">追蹤選項</span><span class="sxs-lookup"><span data-stu-id="4e338-120">Tracing Options</span></span>  
 <span data-ttu-id="4e338-121">**進行連接後立即啟動追蹤**</span><span class="sxs-lookup"><span data-stu-id="4e338-121">**Start tracing immediately after making connection**</span></span>  
 <span data-ttu-id="4e338-122">建立連接後立即使用預設範本開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="4e338-122">Begin a trace using the default template as soon as a connection is made.</span></span>  
  
 <span data-ttu-id="4e338-123">**提供者版本變更時，更新追蹤定義**</span><span class="sxs-lookup"><span data-stu-id="4e338-123">**Update trace definition when provider version changes**</span></span>  
 <span data-ttu-id="4e338-124">更新提供者時，將最新追蹤定義套用至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4e338-124">Apply the most current trace definition to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] when the provider is updated.</span></span> <span data-ttu-id="4e338-125">依預設，不會核取此項目。</span><span class="sxs-lookup"><span data-stu-id="4e338-125">This item is not checked by default.</span></span> <span data-ttu-id="4e338-126">這會強制 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 查詢伺服器的追蹤定義並在磁碟上重新建立 (如果已存在) 檔案。</span><span class="sxs-lookup"><span data-stu-id="4e338-126">This forces [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to query the server for the trace definition and re-create, if one exists, the file on disk.</span></span>  
  
### <a name="file-rollover-options"></a><span data-ttu-id="4e338-127">檔案換用選項</span><span class="sxs-lookup"><span data-stu-id="4e338-127">File Rollover Options</span></span>  
 <span data-ttu-id="4e338-128">**依序載入所有換用檔案，不另外提示**</span><span class="sxs-lookup"><span data-stu-id="4e338-128">**Load all rollover files in sequence without prompting**</span></span>  
 <span data-ttu-id="4e338-129">開啟追蹤檔案時自動載入換用檔案。</span><span class="sxs-lookup"><span data-stu-id="4e338-129">Load rollover files automatically when a trace file is opened.</span></span> <span data-ttu-id="4e338-130">如果在追蹤時建立多個檔案，則選取此選項會自動載入所有的換用檔案。</span><span class="sxs-lookup"><span data-stu-id="4e338-130">If more than one file was created while tracing, selecting this option automatically loads all rollover files.</span></span>  
  
 <span data-ttu-id="4e338-131">**載入換用檔案之前先提示**</span><span class="sxs-lookup"><span data-stu-id="4e338-131">**Prompt before loading rollover files**</span></span>  
 <span data-ttu-id="4e338-132">在開啟追蹤檔案時，讓 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 在加入換用檔案之前給您提示。</span><span class="sxs-lookup"><span data-stu-id="4e338-132">Have [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] prompt you before adding a rollover file when a trace file is opened.</span></span>  
  
 <span data-ttu-id="4e338-133">**永不載入後續的換用檔案**</span><span class="sxs-lookup"><span data-stu-id="4e338-133">**Never load subsequent rollover files**</span></span>  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="4e338-134">開啟追蹤檔案時，永不載入後續的換用檔案。</span><span class="sxs-lookup"><span data-stu-id="4e338-134">never loads subsequent rollover files when a trace file is opened.</span></span>  
  
### <a name="replay-options"></a><span data-ttu-id="4e338-135">重新執行選項</span><span class="sxs-lookup"><span data-stu-id="4e338-135">Replay Options</span></span>  
 <span data-ttu-id="4e338-136">**預設重新執行執行緒數目**</span><span class="sxs-lookup"><span data-stu-id="4e338-136">**Default number of replay threads**</span></span>  
 <span data-ttu-id="4e338-137">指定要同時使用的重新執行執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="4e338-137">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="4e338-138">數字愈高會在重新執行時使用愈多資源，但是會增加重新執行並行。</span><span class="sxs-lookup"><span data-stu-id="4e338-138">A higher number consumes more resources during replay, but increases replay concurrency.</span></span>  
  
 <span data-ttu-id="4e338-139">**預設健全狀況監視器等候間隔 (秒)**</span><span class="sxs-lookup"><span data-stu-id="4e338-139">**Default health monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="4e338-140">指定重新執行的等候間隔秒數。</span><span class="sxs-lookup"><span data-stu-id="4e338-140">Specify the wait interval to replay in seconds.</span></span> <span data-ttu-id="4e338-141">預設值為 3600 秒 (1 小時)。</span><span class="sxs-lookup"><span data-stu-id="4e338-141">Default is 3600 seconds (1 hour).</span></span> <span data-ttu-id="4e338-142">此設定會影響允許執行緒執行的時間量，超過之後會被健全狀況監視器結束。</span><span class="sxs-lookup"><span data-stu-id="4e338-142">This setting affects the amount of time a thread is allowed to run before being terminated by the health monitor.</span></span>  
  
 <span data-ttu-id="4e338-143">**預設健全狀況監視器輪詢間隔 (秒)**</span><span class="sxs-lookup"><span data-stu-id="4e338-143">**Default health monitor poll interval (sec)**</span></span>  
 <span data-ttu-id="4e338-144">指定重新執行期間健全狀況監視器輪詢間隔秒數。</span><span class="sxs-lookup"><span data-stu-id="4e338-144">Specify the health monitor poll interval during replay in seconds.</span></span> <span data-ttu-id="4e338-145">預設值為 60 秒。</span><span class="sxs-lookup"><span data-stu-id="4e338-145">Default is 60 seconds.</span></span> <span data-ttu-id="4e338-146">此值可以讓使用者設定健全狀況監視器輪詢是否有應結束之候選者的頻率。</span><span class="sxs-lookup"><span data-stu-id="4e338-146">This value allows the user to configure how often the health monitor polls for candidates for termination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e338-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e338-147">See Also</span></span>  
 <span data-ttu-id="4e338-148">[連接到伺服器 &#40;SQL Server Profiler 後，自動啟動追蹤&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4e338-148">[Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4e338-149">[設定追蹤顯示預設值 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4e338-149">[Set Trace Display Defaults &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4e338-150">[重新執行追蹤資料表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4e338-150">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4e338-151">[重新執行追蹤檔案 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4e338-151">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4e338-152">[重新執行追蹤](../tools/sql-server-profiler/replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="4e338-152">[Replay Traces](../tools/sql-server-profiler/replay-traces.md) </span></span>  
 <span data-ttu-id="4e338-153">[&#40;SQL Server Profiler 設定全域追蹤選項&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4e338-153">[Set Global Trace Options &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4e338-154">[SQL Server Profiler 範本和權限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="4e338-154">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="4e338-155">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="4e338-155">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
