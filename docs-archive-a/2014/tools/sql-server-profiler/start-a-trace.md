---
title: 啟動追蹤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2b75519631269a1213077a4e295ac73fca1b950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703582"
---
# <a name="start-a-trace"></a><span data-ttu-id="665dd-102">啟動追蹤</span><span class="sxs-lookup"><span data-stu-id="665dd-102">Start a Trace</span></span>
  <span data-ttu-id="665dd-103">在您使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來定義新追蹤或建立範本之後，即可使用新的追蹤定義或範本來啟動、暫停或停止擷取資料。</span><span class="sxs-lookup"><span data-stu-id="665dd-103">After you have defined a new trace or created a template by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can start, pause, or stop capturing data by using the new trace definition or template.</span></span>  
  
## <a name="starting-a-trace"></a><span data-ttu-id="665dd-104">啟動追蹤</span><span class="sxs-lookup"><span data-stu-id="665dd-104">Starting a Trace</span></span>  
 <span data-ttu-id="665dd-105">當您啟動追蹤，而且所定義的來源是 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 便會建立一個佇列，以提供暫存空間來放置所擷取的伺服器事件。</span><span class="sxs-lookup"><span data-stu-id="665dd-105">When you start a trace and the defined source is an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates a queue that provides a temporary holding place for captured server events.</span></span>  
  
 <span data-ttu-id="665dd-106">當您使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來存取 SQL 追蹤時，啟動追蹤時就會開啟新的追蹤視窗 (如果尚未開啟)，並立即擷取資料。</span><span class="sxs-lookup"><span data-stu-id="665dd-106">When you use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to access SQL Trace, a new trace window opens (if one is not already open) when a trace is started, and data is immediately captured.</span></span>  
  
 <span data-ttu-id="665dd-107">當您使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系統預存程序來存取 SQL 追蹤時，您必須在每次啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時啟動追蹤，以便擷取資料。</span><span class="sxs-lookup"><span data-stu-id="665dd-107">When you use [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to access SQL Trace, you must start a trace every time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts for data to be captured.</span></span> <span data-ttu-id="665dd-108">啟動追蹤後，您只能修改追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="665dd-108">When a trace has been started, you can modify only the name of the trace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="665dd-109">使用現有的追蹤時，您可以檢視屬性，但是不能修改屬性。</span><span class="sxs-lookup"><span data-stu-id="665dd-109">When working with existing traces, you can view the properties, but you cannot modify the properties.</span></span> <span data-ttu-id="665dd-110">若要修改屬性，請停止或暫停追蹤。</span><span class="sxs-lookup"><span data-stu-id="665dd-110">To modify the properties, stop or pause the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665dd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="665dd-111">See Also</span></span>  
 <span data-ttu-id="665dd-112">[連接到伺服器 &#40;SQL Server Profiler 後，自動啟動追蹤&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="665dd-112">[Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="665dd-113">[暫停追蹤 &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="665dd-113">[Pause a Trace &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="665dd-114">[停止追蹤 &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="665dd-114">[Stop a Trace &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="665dd-115">[清除追蹤視窗 &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="665dd-115">[Clear a Trace Window &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="665dd-116">在追蹤暫停或停止之後執行追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="665dd-116">Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;</span></span>](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  
