---
title: 重新執行至資料指標 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfc5ba06b60100bf8ecc8d04909371021a5b00e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705730"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a><span data-ttu-id="3c925-102">重新執行至資料指標處 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="3c925-102">Replay to a Cursor (SQL Server Profiler)</span></span>
  <span data-ttu-id="3c925-103">此主題描述如何利用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，來重新執行已在到達資料指標時暫停的追蹤檔或資料表。</span><span class="sxs-lookup"><span data-stu-id="3c925-103">This topic describes how to replay trace files or tables that pause when a cursor is reached by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="3c925-104">在資料指標暫停追蹤可以支援偵錯，因為您可以將較長追蹤指令碼的重新執行過程分解為可累加分析的較短片段。</span><span class="sxs-lookup"><span data-stu-id="3c925-104">Pausing traces at cursors supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.</span></span>  
  
### <a name="to-replay-to-the-cursor"></a><span data-ttu-id="3c925-105">若要重新執行至資料指標處</span><span class="sxs-lookup"><span data-stu-id="3c925-105">To replay to the cursor</span></span>  
  
1.  <span data-ttu-id="3c925-106">開啟您要重新執行的追蹤檔案或追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="3c925-106">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="3c925-107">如需詳細資訊，請參閱 [開啟追蹤檔案 &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 或 [開啟追蹤資料表 &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)隨附的預先定義「微調」範本。</span><span class="sxs-lookup"><span data-stu-id="3c925-107">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="3c925-108">確定您開啟的追蹤檔案或資料表包含重新執行所需的事件類別。</span><span class="sxs-lookup"><span data-stu-id="3c925-108">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="3c925-109">如需詳細資訊，請參閱 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c925-109">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="3c925-110">在追蹤視窗中按一下事件。</span><span class="sxs-lookup"><span data-stu-id="3c925-110">In the trace window, click an event.</span></span>  
  
3.  <span data-ttu-id="3c925-111">在 [重新執行]  功能表上，按一下 [執行至資料指標處]  ，然後連接您要重新執行追蹤的伺服器。</span><span class="sxs-lookup"><span data-stu-id="3c925-111">On the **Replay** menu, click **Run to Cursor**, and then connect to the server where you want to replay the trace.</span></span>  
  
4.  <span data-ttu-id="3c925-112">在 **[重新執行組態]** 對話方塊中確認設定，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="3c925-112">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3c925-113">開始重新執行，並在到達第一個資料指標時暫停。</span><span class="sxs-lookup"><span data-stu-id="3c925-113">The replay starts, pausing when the first cursor is reached.</span></span>  
  
5.  <span data-ttu-id="3c925-114">按 F5 可繼續追蹤。</span><span class="sxs-lookup"><span data-stu-id="3c925-114">Press F5 to resume the trace.</span></span>  
  
6.  <span data-ttu-id="3c925-115">重複步驟 5 至追蹤結束。</span><span class="sxs-lookup"><span data-stu-id="3c925-115">Repeat Step 5 through the end of the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c925-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c925-116">See Also</span></span>  
 <span data-ttu-id="3c925-117">[重新執行至中斷點 &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="3c925-117">[Replay to a Breakpoint &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="3c925-118">[重新執行追蹤](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="3c925-118">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="3c925-119">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="3c925-119">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
