---
title: 重新執行至中斷點 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f33b6862847b042a2613d8c2aa035dd5805493ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705733"
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a><span data-ttu-id="2f5d0-102">重新執行至中斷點 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="2f5d0-102">Replay to a Breakpoint (SQL Server Profiler)</span></span>
  <span data-ttu-id="2f5d0-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，在您要重新執行的追蹤檔案或資料表中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-103">This topic describes how to set breakpoints in a trace file or table that you want to replay by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="2f5d0-104">開始重新執行追蹤之前，在追蹤檔案或資料表中設定中斷點，可以讓您在特定事件上暫停重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-104">Setting breakpoints in a trace file or table before you start to replay the trace, enables you to pause replay of the trace at specific events.</span></span> <span data-ttu-id="2f5d0-105">在重新執行追蹤時使用中斷點可以支援偵錯，因為您可以將很長的追蹤指令碼的重新執行過程，分解為可累加分析的短片段。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-105">Using breakpoints while replaying a trace supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.</span></span>  
  
### <a name="to-replay-to-a-breakpoint"></a><span data-ttu-id="2f5d0-106">若要重新執行至中斷點</span><span class="sxs-lookup"><span data-stu-id="2f5d0-106">To replay to a breakpoint</span></span>  
  
1.  <span data-ttu-id="2f5d0-107">開啟您要重新執行的追蹤檔案或追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-107">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="2f5d0-108">如需詳細資訊，請參閱 [開啟追蹤檔案 &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 或 [開啟追蹤資料表 &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)隨附的預先定義「微調」範本。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-108">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="2f5d0-109">確定您開啟的追蹤檔案或資料表包含重新執行所需的事件類別。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-109">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="2f5d0-110">如需詳細資訊，請參閱 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="2f5d0-111">在追蹤視窗中，按一下您要做為中斷點的事件。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-111">In the trace window, click an event that you want to use as a breakpoint.</span></span> <span data-ttu-id="2f5d0-112">使用下列三種方式之一來設定中斷點：</span><span class="sxs-lookup"><span data-stu-id="2f5d0-112">Use one of the following three methods to set a breakpoint:</span></span>  
  
    -   <span data-ttu-id="2f5d0-113">按 F9 鍵。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-113">Press F9.</span></span>  
  
    -   <span data-ttu-id="2f5d0-114">在 **[重新執行]** 功能表上，按一下 **[切換中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-114">On the **Replay** menu, click **Toggle Breakpoint**.</span></span>  
  
    -   <span data-ttu-id="2f5d0-115">以滑鼠右鍵按一下事件，然後按一下 [切換中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-115">Right-click the event, and then click **Toggle Breakpoint**.</span></span>  
  
     <span data-ttu-id="2f5d0-116">選取的追蹤事件旁邊會出現紅色項目符號，表示此為追蹤中斷點。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-116">A red bullet appears next to the selected trace event, indicating that it is the trace breakpoint.</span></span>  
  
     <span data-ttu-id="2f5d0-117">重複這個步驟來設定多個中斷點。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-117">Repeat this step to set several breakpoints.</span></span>  
  
3.  <span data-ttu-id="2f5d0-118">在 **[重新執行]** 功能表，按一下 **[開始]** ，連接到您要重新執行追蹤的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-118">On the **Replay** menu, click **Start**, and connect to the server where you want to replay the trace.</span></span>  
  
4.  <span data-ttu-id="2f5d0-119">在 **[重新執行組態]** 對話方塊中確認設定，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-119">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
     <span data-ttu-id="2f5d0-120">開始重新執行，到達中斷點時會暫停。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-120">The replay starts, pausing when the breakpoint is reached.</span></span>  
  
5.  <span data-ttu-id="2f5d0-121">按 F5 繼續重新執行，繼續到下一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-121">Press F5 to resume the replay and proceed to the next breakpoint.</span></span>  
  
6.  <span data-ttu-id="2f5d0-122">重複步驟 5 至追蹤結束。</span><span class="sxs-lookup"><span data-stu-id="2f5d0-122">Repeat Step 5 through the end of the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5d0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f5d0-123">See Also</span></span>  
 <span data-ttu-id="2f5d0-124">[重新執行至資料指標處 &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="2f5d0-124">[Replay to a Cursor &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="2f5d0-125">[重新執行追蹤](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="2f5d0-125">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="2f5d0-126">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="2f5d0-126">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
