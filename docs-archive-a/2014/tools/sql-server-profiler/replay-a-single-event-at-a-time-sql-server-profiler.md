---
title: 一次重新執行一個事件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 457bc94d9d8eae470fb60b450d30441c07e676df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705750"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a><span data-ttu-id="139c3-102">一次重新執行一個事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="139c3-102">Replay a Single Event at a Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="139c3-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，在重新執行追蹤檔案或資料表中，一次重新執行一個事件。</span><span class="sxs-lookup"><span data-stu-id="139c3-103">This topic describes how to replay one event at a time in a replay trace file or table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-replay-a-single-event-at-a-time"></a><span data-ttu-id="139c3-104">若要一次只重新執行一個事件</span><span class="sxs-lookup"><span data-stu-id="139c3-104">To replay a single event at a time</span></span>  
  
1.  <span data-ttu-id="139c3-105">開啟您要重新執行的追蹤檔案或追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="139c3-105">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="139c3-106">如需詳細資訊，請參閱 [開啟追蹤檔案 &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 或 [開啟追蹤資料表 &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)隨附的預先定義「微調」範本。</span><span class="sxs-lookup"><span data-stu-id="139c3-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="139c3-107">確定您開啟的追蹤檔案或資料表包含重新執行所需的事件類別。</span><span class="sxs-lookup"><span data-stu-id="139c3-107">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="139c3-108">如需詳細資訊，請參閱 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="139c3-108">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="139c3-109">在 **[重新執行]** 功能表上，按一下 **[步驟]** ，然後連接到要重新執行追蹤的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="139c3-109">On the **Replay** menu, click **Step**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="139c3-110">在 **[重新執行組態]** 對話方塊中確認設定，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="139c3-110">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span> <span data-ttu-id="139c3-111">如需在 [重新執行組態]  對話方塊中指定設定的詳細資訊，請參閱[重新執行追蹤檔案 &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) 或[重新執行追蹤資料表 &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="139c3-111">For more information about specifying settings on the **Replay Configuration** dialog box, see [Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) or [Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md).</span></span>  
  
4.  <span data-ttu-id="139c3-112">若要重新執行第一個事件，請在 **[重新執行組態]** 對話方塊上，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="139c3-112">To replay the first event, click **OK** in the **Replay Configuration** dialog box.</span></span>  
  
5.  <span data-ttu-id="139c3-113">若要重新執行後續事件，請在 **[重新執行]** 功能表上，按一下 **[步驟]** 或按 F10。</span><span class="sxs-lookup"><span data-stu-id="139c3-113">To replay subsequent events, on the **Replay** menu, click **Step**, or press F10.</span></span> <span data-ttu-id="139c3-114">每個事件都重複按一下 **[步驟]** 或按 F10。</span><span class="sxs-lookup"><span data-stu-id="139c3-114">Repeat clicking **Step** or pressing F10 for each event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="139c3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="139c3-115">See Also</span></span>  
 <span data-ttu-id="139c3-116">[重新執行追蹤](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="139c3-116">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="139c3-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="139c3-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
