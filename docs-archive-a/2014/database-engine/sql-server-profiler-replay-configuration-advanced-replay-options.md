---
title: SQL Server Profiler-重新執行設定 (Advanced Replay 選項) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.advanced.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: b4eb34f7-3af6-4a44-ba7e-2b8430ec3cd7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 95070d8defb5b7778859ce470aaa8cfc85955ba6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705370"
---
# <a name="sql-server-profiler---replay-configuration-advanced-replay-options"></a><span data-ttu-id="0f57f-102">SQL Server Profiler - 重新執行組態 (進階重新執行選項)</span><span class="sxs-lookup"><span data-stu-id="0f57f-102">SQL Server Profiler - Replay Configuration (Advanced Replay Options)</span></span>
  <span data-ttu-id="0f57f-103">在 [重新執行組態]\*\*\*\* 對話方塊中，使用 [進階重新執行選項]\*\*\*\* 索引標籤來指定如何重新執行追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="0f57f-103">In the **Replay Configuration** dialog box, use the **Advanced Replay Options** tab to specify how to replay a trace file.</span></span>  
  
 <span data-ttu-id="0f57f-104">若要檢視這個視窗，請使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 開啟包含用以重新執行的適當事件之追蹤檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="0f57f-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace file or table that contains the appropriate events for replay.</span></span> <span data-ttu-id="0f57f-105">如需詳細資訊，請參閱 [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f57f-105">For more information, see [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md).</span></span> <span data-ttu-id="0f57f-106">在追蹤檔案或資料表開啟期間，請在 [重新執行]\*\*\*\* 功能表上按一下 [啟動]\*\*\*\*，連接到想要重新執行追蹤之 SQL Server 的執行個體，然後按一下 [進階重新執行選項]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0f57f-106">While the trace file or table is open, on the **Replay** menu, click **Start**, connect to the instance of SQL Server where you want to replay the trace, and then click the **Advanced Replay Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0f57f-107">選項</span><span class="sxs-lookup"><span data-stu-id="0f57f-107">Options</span></span>  
 <span data-ttu-id="0f57f-108">**重新執行系統 SPID**</span><span class="sxs-lookup"><span data-stu-id="0f57f-108">**Replay system SPIDs**</span></span>  
 <span data-ttu-id="0f57f-109">指定 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 是否重新執行系統處理序識別碼 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="0f57f-109">Specifies whether [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] replays system process identifiers (SPIDs).</span></span>  
  
 <span data-ttu-id="0f57f-110">**只重新執行一個 SPID**</span><span class="sxs-lookup"><span data-stu-id="0f57f-110">**Replay one SPID only**</span></span>  
 <span data-ttu-id="0f57f-111">只重新執行與選取之 SPID 相關的來源追蹤檔案中的活動。</span><span class="sxs-lookup"><span data-stu-id="0f57f-111">Replays only the activity in the source trace file that is related to the selected SPID.</span></span>  
  
 <span data-ttu-id="0f57f-112">**要重新執行的 SPID**</span><span class="sxs-lookup"><span data-stu-id="0f57f-112">**SPID to replay**</span></span>  
 <span data-ttu-id="0f57f-113">指定要重新執行的 SPID。</span><span class="sxs-lookup"><span data-stu-id="0f57f-113">Specify which SPID to replay.</span></span>  
  
 <span data-ttu-id="0f57f-114">**依日期和時間限制重新執行**</span><span class="sxs-lookup"><span data-stu-id="0f57f-114">**Limit replay by date and time**</span></span>  
 <span data-ttu-id="0f57f-115">核取以只重新執行來源追蹤檔案的一部份。</span><span class="sxs-lookup"><span data-stu-id="0f57f-115">Check to replay only a portion of the source trace file.</span></span>  
  
 <span data-ttu-id="0f57f-116">**開始時間**</span><span class="sxs-lookup"><span data-stu-id="0f57f-116">**Start time**</span></span>  
 <span data-ttu-id="0f57f-117">來源追蹤檔案中應該啟動重新執行的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="0f57f-117">Date and time in the source trace file where the replay should start.</span></span>  
  
 <span data-ttu-id="0f57f-118">**結束時間**</span><span class="sxs-lookup"><span data-stu-id="0f57f-118">**End time**</span></span>  
 <span data-ttu-id="0f57f-119">來源追蹤檔案中應該停止重新執行的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="0f57f-119">Date and time in the source trace file where the replay should stop.</span></span>  
  
 <span data-ttu-id="0f57f-120">**健全狀況監視器等候間隔 (秒)**</span><span class="sxs-lookup"><span data-stu-id="0f57f-120">**Health monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="0f57f-121">指定重新執行的等候間隔秒數。</span><span class="sxs-lookup"><span data-stu-id="0f57f-121">Specify the wait interval to replay in seconds.</span></span> <span data-ttu-id="0f57f-122">預設值為 3600 秒 (1 小時)。</span><span class="sxs-lookup"><span data-stu-id="0f57f-122">Default is 3600 seconds (1 hour).</span></span> <span data-ttu-id="0f57f-123">此設定會影響健全狀況監視器結束處理序之前，處理序可以執行的時間量。</span><span class="sxs-lookup"><span data-stu-id="0f57f-123">This setting affects the amount of time a process is allowed to run before being terminated by the health monitor.</span></span>  
  
 <span data-ttu-id="0f57f-124">**健全狀況監視器輪詢間隔 (秒)**</span><span class="sxs-lookup"><span data-stu-id="0f57f-124">**Health monitor poll interval (sec)**</span></span>  
 <span data-ttu-id="0f57f-125">指定重新執行期間健全狀況監視器輪詢間隔秒數。</span><span class="sxs-lookup"><span data-stu-id="0f57f-125">Specify the health monitor poll interval during replay in seconds.</span></span> <span data-ttu-id="0f57f-126">預設值為 60 秒。</span><span class="sxs-lookup"><span data-stu-id="0f57f-126">Default is 60 seconds.</span></span> <span data-ttu-id="0f57f-127">此值可以讓使用者設定健全狀況監視器輪詢是否有應結束之候選者的頻率。</span><span class="sxs-lookup"><span data-stu-id="0f57f-127">This value allows the user to configure how often the health monitor polls for candidates for termination.</span></span>  
  
 <span data-ttu-id="0f57f-128">**啟用 SQL Server 封鎖處理序監視器**</span><span class="sxs-lookup"><span data-stu-id="0f57f-128">**Enable SQL Server blocked processes monitor**</span></span>  
 <span data-ttu-id="0f57f-129">啟用搜尋已封鎖或封鎖中處理序的處理序。</span><span class="sxs-lookup"><span data-stu-id="0f57f-129">Enables a process that searches for blocked or blocking processes.</span></span>  
  
 <span data-ttu-id="0f57f-130">**封鎖處理序監視器等候間隔 (秒)**</span><span class="sxs-lookup"><span data-stu-id="0f57f-130">**Blocked processes monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="0f57f-131">設定封鎖處理序監視器搜尋已封鎖或封鎖中處理序的頻率。</span><span class="sxs-lookup"><span data-stu-id="0f57f-131">Configures how often the blocked processes monitor searches for blocked or blocking processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f57f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f57f-132">See Also</span></span>  
 <span data-ttu-id="0f57f-133">[重新執行追蹤資料表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="0f57f-133">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="0f57f-134">[重新執行追蹤檔案 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="0f57f-134">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="0f57f-135">重新執行追蹤</span><span class="sxs-lookup"><span data-stu-id="0f57f-135">Replay Traces</span></span>](../tools/sql-server-profiler/replay-traces.md)  
  
  
