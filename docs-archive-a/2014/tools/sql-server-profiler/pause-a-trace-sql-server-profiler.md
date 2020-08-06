---
title: 暫停追蹤 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
author: stevestein
ms.author: sstein
ms.openlocfilehash: cdc9dbbd01099b1d33787a72b0bd59b65cea722e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686590"
---
# <a name="pause-a-trace-sql-server-profiler"></a><span data-ttu-id="18711-102">暫停追蹤 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="18711-102">Pause a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="18711-103">暫停追蹤可避免進一步擷取事件資料，直到追蹤重新啟動為止。</span><span class="sxs-lookup"><span data-stu-id="18711-103">Pausing a trace prevents further event data from being captured until the trace is restarted.</span></span>  
  
 <span data-ttu-id="18711-104">暫停追蹤可防止事件資料被擷取，直到重新啟動追蹤為止。</span><span class="sxs-lookup"><span data-stu-id="18711-104">When you pause a trace, you prevent event data from being captured until the trace is restarted.</span></span> <span data-ttu-id="18711-105">重新啟動追蹤可讓追蹤作業繼續進行。</span><span class="sxs-lookup"><span data-stu-id="18711-105">Restarting a trace lets trace operations resume.</span></span> <span data-ttu-id="18711-106">重新啟動之後，先前擷取的資料並不會遺失。</span><span class="sxs-lookup"><span data-stu-id="18711-106">No previously captured data is lost after a restart.</span></span> <span data-ttu-id="18711-107">當追蹤重新啟動時，資料的擷取動作會從該暫停點繼續進行。</span><span class="sxs-lookup"><span data-stu-id="18711-107">When the trace is restarted, data capturing resumes from that point onward.</span></span> <span data-ttu-id="18711-108">當追蹤暫停時，您可以變更名稱、事件、資料行及篩選條件。</span><span class="sxs-lookup"><span data-stu-id="18711-108">While a trace is paused, you can change the name, events, columns, and filters.</span></span> <span data-ttu-id="18711-109">但是，您無法變更傳送追蹤資料的目的地，也不能變更伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="18711-109">However, you cannot change the destinations to which you are sending the trace data, nor change the server connection.</span></span>  
  
### <a name="to-pause-a-trace"></a><span data-ttu-id="18711-110">若要暫停追蹤</span><span class="sxs-lookup"><span data-stu-id="18711-110">To pause a trace</span></span>  
  
1.  <span data-ttu-id="18711-111">選取包含執行中追蹤的視窗。</span><span class="sxs-lookup"><span data-stu-id="18711-111">Select a window that contains a running trace.</span></span>  
  
2.  <span data-ttu-id="18711-112">在 **[檔案]** 功能表上，按一下 **[暫停追蹤]** 。</span><span class="sxs-lookup"><span data-stu-id="18711-112">On the **File** menu, click **Pause Trace**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18711-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18711-113">See Also</span></span>  
 [<span data-ttu-id="18711-114">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="18711-114">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
