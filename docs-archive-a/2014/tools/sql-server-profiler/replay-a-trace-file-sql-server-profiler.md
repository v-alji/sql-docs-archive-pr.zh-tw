---
title: 重新執行追蹤檔案 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 9e361275-c8fd-4499-8389-242cf8e27415
author: stevestein
ms.author: sstein
ms.openlocfilehash: d3a9f007b9b6d2b46be43abdb10db286a75c33fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705738"
---
# <a name="replay-a-trace-file-sql-server-profiler"></a><span data-ttu-id="c1c8c-102">重新執行追蹤檔案 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="c1c8c-102">Replay a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="c1c8c-103">重新執行是開啟儲存的追蹤並重新執行該追蹤的能力。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-103">Replay is the ability to open a saved trace and replay it again.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="c1c8c-104">具有多執行緒播放引擎的功能，可以模擬使用者連線及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-104">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c1c8c-105">重新執行在排解應用程式或處理序的疑難問題時很有用。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-105">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="c1c8c-106">您識別問題並實作更正時，針對更正的應用程式或處理序執行發現可能問題的追蹤。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-106">When you identify the problem and implement corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="c1c8c-107">然後，重新執行原始追蹤並比較結果。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-107">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="c1c8c-108">除了您要監視的其他任何事件類別以外，還必須擷取特定的事件類別以便重新執行。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-108">In addition to any other event classes you want to monitor, specific event classes must be captured to enable replay.</span></span> <span data-ttu-id="c1c8c-109">依預設，如果您使用 **TSQL_Replay** 追蹤範本，就會擷取這些事件。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-109">These events are captured by default if you use the **TSQL_Replay** trace template.</span></span> <span data-ttu-id="c1c8c-110">如需詳細資訊，請參閱 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
### <a name="to-replay-a-trace-file"></a><span data-ttu-id="c1c8c-111">若要重新執行追蹤檔案</span><span class="sxs-lookup"><span data-stu-id="c1c8c-111">To replay a trace file</span></span>  
  
1.  <span data-ttu-id="c1c8c-112">在 [檔案]  功能表上，指向 [開啟]  ，然後按一下 [追蹤檔案]  。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-112">On the **File** menu, point to **Open**, and then click **Trace File**.</span></span> <span data-ttu-id="c1c8c-113">選取追蹤檔案，其中包含重新執行所需的事件類別。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-113">Select a trace file that contains the event classes necessary for replay.</span></span>  
  
2.  <span data-ttu-id="c1c8c-114">在 [重新執行]  功能表上按一下 [開始]  ，然後連接到您要重新執行追蹤的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-114">On the **Replay** menu, click **Start**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="c1c8c-115">在 [重新執行組態]  對話方塊的 [基本重新執行選項]  索引標籤上，指定 [重新執行伺服器]  。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-115">In the **Replay Configuration** dialog box, on the **Basic Replay Options** tab, specify the **Replay server**.</span></span> <span data-ttu-id="c1c8c-116">按一下 [變更]  ，變更 [重新執行伺服器]  方塊上所顯示的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-116">Click **Change** to change the server displayed in the **Replay server** box.</span></span>  
  
4.  <span data-ttu-id="c1c8c-117">選擇性，選取下列要儲存重新執行之目的地的其中之一：</span><span class="sxs-lookup"><span data-stu-id="c1c8c-117">Optionally, select one of the following destinations in which to save the replay:</span></span>  
  
    -   <span data-ttu-id="c1c8c-118">[儲存至檔案]  ，指定用來儲存重新執行的檔案。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-118">**Save to file**, which specifies a file in which to save the replay.</span></span>  
  
    -   <span data-ttu-id="c1c8c-119">[儲存至資料表]  ，指定用來儲存重新執行的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-119">**Save to table**, which specifies a database table in which to save the replay.</span></span>  
  
5.  <span data-ttu-id="c1c8c-120">選擇 [以追蹤事件的順序重新執行事件]  或 [使用多執行緒重新執行事件]  。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-120">Choose either **Replay the events in the order they were traced**or **Replay events using multiple threads**.</span></span> <span data-ttu-id="c1c8c-121">下列資料表說明這些設定之間的差異。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-121">The following table explains the difference between these settings.</span></span>  
  
    |<span data-ttu-id="c1c8c-122">選項</span><span class="sxs-lookup"><span data-stu-id="c1c8c-122">Option</span></span>|<span data-ttu-id="c1c8c-123">描述</span><span class="sxs-lookup"><span data-stu-id="c1c8c-123">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="c1c8c-124">**依照追蹤的順序重新執行事件**</span><span class="sxs-lookup"><span data-stu-id="c1c8c-124">**Replay events in the order they were traced**</span></span>|<span data-ttu-id="c1c8c-125">以記錄事件的順序重新執行事件。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-125">Replays events in the order they were recorded.</span></span> <span data-ttu-id="c1c8c-126">此選項會啟動偵錯。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-126">This option enables debugging.</span></span>|  
    |<span data-ttu-id="c1c8c-127">**使用多執行緒重新執行事件**</span><span class="sxs-lookup"><span data-stu-id="c1c8c-127">**Replay events using multiple threads**</span></span>|<span data-ttu-id="c1c8c-128">這個選項使用多個執行緒重新執行每個事件，不受順序的限制。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-128">This option uses multiple threads to replay each event regardless of the sequence.</span></span> <span data-ttu-id="c1c8c-129">這個選項會將效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-129">This option optimizes performance.</span></span>|  
  
6.  <span data-ttu-id="c1c8c-130">選取 [顯示重新執行結果]  ，在重新執行時檢視其過程。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-130">Select **Display replay results** to view the replay as it occurs.</span></span>  
  
7.  <span data-ttu-id="c1c8c-131">(選擇性) 按一下 [進階重新執行選項]  索引標籤，設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="c1c8c-131">Optionally click the **Advanced Replay Options**tab to configure the following options:</span></span>  
  
    -   <span data-ttu-id="c1c8c-132">若要重新執行所有伺服器處理序識別碼 (SPID)，請選取 [重新執行系統 SPID]  。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-132">To replay all server process IDs (SPIDs), select **Replay system SPIDs**.</span></span>  
  
    -   <span data-ttu-id="c1c8c-133">若要限制只重新執行屬於特定 SPID 的處理序，請選取 [只重新執行一個 SPID]  。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-133">To limit the replay to processes belonging to a specific SPID, select **Replay one SPID only**.</span></span> <span data-ttu-id="c1c8c-134">在 [要重新執行的 SPID]  方塊中，輸入 SPID。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-134">In the **SPID to replay** box, type the SPID.</span></span>  
  
    -   <span data-ttu-id="c1c8c-135">若要重新執行特定時間週期發生的事件，請選取 [依日期與時間限制重新執行]  。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-135">To replay events that occurred during a specific time period, select **Limit the replay by date and time**.</span></span> <span data-ttu-id="c1c8c-136">選取 [開始時間]  與 [結束時間]  的日期和時間，指定重新執行中包含的時間週期。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-136">Select a date and time for the **Start time**and **End time**to specify the time period to include in the replay.</span></span>  
  
    -   <span data-ttu-id="c1c8c-137">若要控制 SQL Server 在重新執行期間管理處理序的方式，請設定 [健全狀況監視器選項]  。</span><span class="sxs-lookup"><span data-stu-id="c1c8c-137">To control how SQL Server manages processes during replay, configure **Health Monitor Options**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c8c-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1c8c-138">See Also</span></span>  
 <span data-ttu-id="c1c8c-139">[執行 SQL Server Profiler 所需的權限](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="c1c8c-139">[Permissions Required to Run SQL Server Profiler](sql-server-profiler.md) </span></span>  
 <span data-ttu-id="c1c8c-140">[重新執行追蹤](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="c1c8c-140">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="c1c8c-141">[開啟追蹤檔案 &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="c1c8c-141">[Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="c1c8c-142">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="c1c8c-142">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
