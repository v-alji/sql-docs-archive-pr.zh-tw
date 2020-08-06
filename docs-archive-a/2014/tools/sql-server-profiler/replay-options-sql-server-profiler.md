---
title: SQL Server Profiler)  (重新執行選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
- health monitor [SQL Server]
- Replay Configuration dialog box
ms.assetid: 58761a25-a84f-4a90-9c61-97700bc5ad9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 695a1431145813f0a7829626a380e510d0e602e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705737"
---
# <a name="replay-options-sql-server-profiler"></a><span data-ttu-id="72c2f-102">重新執行選項 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="72c2f-102">Replay Options (SQL Server Profiler)</span></span>
  <span data-ttu-id="72c2f-103">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來重新執行擷取的追蹤之前，請在 [重新執行組態]  對話方塊中指定重新執行選項。</span><span class="sxs-lookup"><span data-stu-id="72c2f-103">Before replaying a captured trace with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], specify replay options in the **Replay Configuration** dialog box.</span></span> <span data-ttu-id="72c2f-104">若要啟動此對話方塊，請開啟 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 中的重新執行追蹤檔案或資料表，然後在 [重新執行]  功能表上按一下 [啟動]  。</span><span class="sxs-lookup"><span data-stu-id="72c2f-104">To launch this dialog box, open the replay trace file or table in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and on the **Replay** menu, click **Start**.</span></span> <span data-ttu-id="72c2f-105">如需有關重做追蹤時所需之權限的詳細資訊，請參閱＜ [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)＞。</span><span class="sxs-lookup"><span data-stu-id="72c2f-105">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="72c2f-106">本主題描述使用 [重新執行組態]  對話方塊所指定的選項。</span><span class="sxs-lookup"><span data-stu-id="72c2f-106">This topic describes the options specified with the **Replay Configuration** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72c2f-107">我們建議您使用分散式重新執行公用程式來重新執行密集的 OLTP 應用程式 (具有許多使用中並行連接或高輸送量)。</span><span class="sxs-lookup"><span data-stu-id="72c2f-107">We recommend using the Distributed Replay Utility for replaying an intensive OLTP application (with many active concurrent connections or high throughput).</span></span> <span data-ttu-id="72c2f-108">分散式重新執行公用程式可以從多部電腦重新執行追蹤資料，並有效模擬關鍵任務的工作負載。</span><span class="sxs-lookup"><span data-stu-id="72c2f-108">The Distributed Replay Utility can replay trace data from multiple computers, better simulating a mission-critical workload.</span></span> <span data-ttu-id="72c2f-109">如需詳細資訊，請參閱 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="72c2f-109">For more information, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
## <a name="basic-replay-options"></a><span data-ttu-id="72c2f-110">基本重新執行選項</span><span class="sxs-lookup"><span data-stu-id="72c2f-110">Basic Replay Options</span></span>  
 <span data-ttu-id="72c2f-111">**重新執行伺服器**</span><span class="sxs-lookup"><span data-stu-id="72c2f-111">**Replay server**</span></span>  
 <span data-ttu-id="72c2f-112">該伺服器是您要對其重新執行追蹤的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="72c2f-112">The server is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] against which you want to replay the trace.</span></span> <span data-ttu-id="72c2f-113">伺服器必須遵守 [重新執行需求](replay-requirements.md)中所描述的重新執行需求。</span><span class="sxs-lookup"><span data-stu-id="72c2f-113">The server must adhere to the replay requirements described in [Replay Requirements](replay-requirements.md)."</span></span>  
  
 <span data-ttu-id="72c2f-114">**儲存至檔案**</span><span class="sxs-lookup"><span data-stu-id="72c2f-114">**Save to file**</span></span>  
 <span data-ttu-id="72c2f-115">將重新執行追蹤的結果寫入輸出檔中，以供稍後檢視。</span><span class="sxs-lookup"><span data-stu-id="72c2f-115">The output file where the result of replaying the trace is written for later viewing.</span></span> <span data-ttu-id="72c2f-116">根據預設， [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 只會在螢幕上顯示重新執行追蹤的結果。</span><span class="sxs-lookup"><span data-stu-id="72c2f-116">By default, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] displays only the results of replaying the trace on the screen.</span></span>  
  
 <span data-ttu-id="72c2f-117">**儲存至資料表**</span><span class="sxs-lookup"><span data-stu-id="72c2f-117">**Save to table**</span></span>  
 <span data-ttu-id="72c2f-118">將重新執行追蹤的結果寫入資料庫資料表中，以供稍後檢視。</span><span class="sxs-lookup"><span data-stu-id="72c2f-118">The database table where the result of replaying the trace is written for later viewing.</span></span>  
  
 <span data-ttu-id="72c2f-119">**重新執行執行緒的數目**</span><span class="sxs-lookup"><span data-stu-id="72c2f-119">**Number of replay threads**</span></span>  
 <span data-ttu-id="72c2f-120">指定要同時使用的重新執行執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="72c2f-120">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="72c2f-121">數量愈大，在重新執行期間所耗用的資源就愈多，但重新執行的速度也愈快。</span><span class="sxs-lookup"><span data-stu-id="72c2f-121">A higher number consumes more resources during replay, but replay is faster.</span></span> <span data-ttu-id="72c2f-122">使用多執行緒時，就不會完整地維護事件順序。</span><span class="sxs-lookup"><span data-stu-id="72c2f-122">Event ordering is not fully maintained when multiple threads are used.</span></span>  
  
 <span data-ttu-id="72c2f-123">**依照追蹤的順序重新執行事件**</span><span class="sxs-lookup"><span data-stu-id="72c2f-123">**Replay events in the order they were traced**</span></span>  
 <span data-ttu-id="72c2f-124">可讓您使用偵錯方法，例如逐步執行每項追蹤。</span><span class="sxs-lookup"><span data-stu-id="72c2f-124">Allows you to use debugging methods such as stepping through each trace.</span></span> <span data-ttu-id="72c2f-125">如果沒有選取此選項，則重新執行作業不保證會以原先擷取事件的順序來重新執行事件。</span><span class="sxs-lookup"><span data-stu-id="72c2f-125">If this option is not selected, replay does not guarantee that events are replayed in an order that is consistent with the order in which events were originally captured.</span></span>  
  
 <span data-ttu-id="72c2f-126">**使用多執行緒重新執行事件**</span><span class="sxs-lookup"><span data-stu-id="72c2f-126">**Replay events using multiple threads**</span></span>  
 <span data-ttu-id="72c2f-127">最佳化效能，並停用偵錯。</span><span class="sxs-lookup"><span data-stu-id="72c2f-127">Optimizes performance and disables debugging.</span></span> <span data-ttu-id="72c2f-128">它會依照針對特定伺服器處理序識別碼 (SPID) 記錄的順序來重新執行事件，但不保證 SPID 的順序。</span><span class="sxs-lookup"><span data-stu-id="72c2f-128">Events are replayed in the order they were recorded for a particular server process ID (SPID), but ordering of SPIDs is not guaranteed.</span></span>  
  
 <span data-ttu-id="72c2f-129">**顯示重新執行結果**</span><span class="sxs-lookup"><span data-stu-id="72c2f-129">**Display replay results**</span></span>  
 <span data-ttu-id="72c2f-130">顯示重新執行的結果。</span><span class="sxs-lookup"><span data-stu-id="72c2f-130">Display the results of the replay.</span></span> <span data-ttu-id="72c2f-131">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="72c2f-131">This is the default option.</span></span> <span data-ttu-id="72c2f-132">若您重新執行的追蹤很大，您可能想要停用此選項來儲存磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="72c2f-132">If the trace you are replaying is very large, you may want to disable this to save disk space.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72c2f-133">為得到最佳的重新執行效能，建議您選擇使用多執行緒來重新執行事件，並且不要選擇顯示重新執行的結果。</span><span class="sxs-lookup"><span data-stu-id="72c2f-133">For best replay performance, we recommend that you select to replay events using multiple threads, and do not select to display the replay results.</span></span>  
  
## <a name="advanced-replay-options"></a><span data-ttu-id="72c2f-134">進階重新執行選項</span><span class="sxs-lookup"><span data-stu-id="72c2f-134">Advanced Replay Options</span></span>  
 <span data-ttu-id="72c2f-135">**重新執行系統 SPID**</span><span class="sxs-lookup"><span data-stu-id="72c2f-135">**Replay system SPIDs**</span></span>  
 <span data-ttu-id="72c2f-136">重新執行所有 SPID。</span><span class="sxs-lookup"><span data-stu-id="72c2f-136">Replay all SPIDs.</span></span> <span data-ttu-id="72c2f-137">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="72c2f-137">This is the default option.</span></span>  
  
 <span data-ttu-id="72c2f-138">**只重新執行一個 SPID**</span><span class="sxs-lookup"><span data-stu-id="72c2f-138">**Replay one SPID only**</span></span>  
 <span data-ttu-id="72c2f-139">重新執行您從清單中選擇的 SPID 號碼。</span><span class="sxs-lookup"><span data-stu-id="72c2f-139">Replays the SPID number you choose from the list.</span></span>  
  
 <span data-ttu-id="72c2f-140">**依日期和時間限制重新執行**</span><span class="sxs-lookup"><span data-stu-id="72c2f-140">**Limit replay by date and time**</span></span>  
 <span data-ttu-id="72c2f-141">針對所指定的 [開始時間]  及 [結束時間]  來重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="72c2f-141">Replays the trace for the specified **Start time** and **End time**.</span></span>  
  
 <span data-ttu-id="72c2f-142">**健全狀況監視器等候間隔**</span><span class="sxs-lookup"><span data-stu-id="72c2f-142">**Health monitor wait interval**</span></span>  
 <span data-ttu-id="72c2f-143">設定可允許處理序執行的時間量，時間一到，健全狀況監視器就會將其終止。</span><span class="sxs-lookup"><span data-stu-id="72c2f-143">Sets the amount of time a process is allowed to run before the health monitor terminates it.</span></span>  
  
 <span data-ttu-id="72c2f-144">**健全狀況監視器輪詢間隔**</span><span class="sxs-lookup"><span data-stu-id="72c2f-144">**Health monitor poll interval**</span></span>  
 <span data-ttu-id="72c2f-145">設定健全狀況監視器輪詢適用項目來加以終止的頻率。</span><span class="sxs-lookup"><span data-stu-id="72c2f-145">Sets how often the health monitor polls candidates for termination.</span></span>  
  
 <span data-ttu-id="72c2f-146">**啟用 SQL Server 封鎖處理序監視器**</span><span class="sxs-lookup"><span data-stu-id="72c2f-146">**Enable SQL Server blocked processes monitor**</span></span>  
 <span data-ttu-id="72c2f-147">設定已封鎖之處理序監視器搜尋已封鎖或封鎖中處理序的頻率。</span><span class="sxs-lookup"><span data-stu-id="72c2f-147">Sets how often the blocked processes monitor searches for blocked or blocking processes.</span></span>  
  
## <a name="about-the-health-monitor"></a><span data-ttu-id="72c2f-148">關於健全狀況監視器</span><span class="sxs-lookup"><span data-stu-id="72c2f-148">About the Health Monitor</span></span>  
 <span data-ttu-id="72c2f-149">健全狀況監視器是一個應用程式執行緒，可監視有關重新執行追蹤的模擬處理序，並結束重新執行作業中被封鎖的處理序。</span><span class="sxs-lookup"><span data-stu-id="72c2f-149">The health monitor is an application thread that monitors the simulated processes involved in replaying a trace, and ends those processes that are blocked within the replay.</span></span> <span data-ttu-id="72c2f-150">您可以在 [重新執行組態] 對話方塊的 [進階重新執行選項] 索引標籤中，指定健全狀況監視器要等候幾秒，再結束被封鎖的處理序 ([健全狀況監視器等候間隔])。</span><span class="sxs-lookup"><span data-stu-id="72c2f-150">In the **Advanced Replay Options** tab of the **Replay Configuration** dialog box, you can specify how long the health monitor should wait in seconds before ending a blocked process (**Health monitor wait interval**).</span></span> <span data-ttu-id="72c2f-151">如果您將此間隔設為 0，則健全狀況監視器就永遠都不會結束重新執行追蹤中的模擬封鎖處理序。</span><span class="sxs-lookup"><span data-stu-id="72c2f-151">If you set this interval to 0, the health monitor never ends simulated blocking processes in the replaying trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c2f-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72c2f-152">See Also</span></span>  
 <span data-ttu-id="72c2f-153">[重新執行追蹤](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="72c2f-153">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="72c2f-154">[重新執行需求](replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="72c2f-154">[Replay Requirements](replay-requirements.md) </span></span>  
 [<span data-ttu-id="72c2f-155">重新執行追蹤的考量 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="72c2f-155">Considerations for Replaying Traces &#40;SQL Server Profiler&#41;</span></span>](considerations-for-replaying-traces-sql-server-profiler.md)  
  
  
