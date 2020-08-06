---
title: 建立追蹤與 Windows 效能記錄資料的關聯 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 879441c948f0ad04b971159a37ec0dcec90e3ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686606"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a><span data-ttu-id="77b18-102">使追蹤與 Windows 效能記錄資料相互關聯</span><span class="sxs-lookup"><span data-stu-id="77b18-102">Correlate a Trace with Windows Performance Log Data</span></span>
  <span data-ttu-id="77b18-103">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，您可以開啟 Microsoft Windows 效能記錄，選擇要與追蹤相互關連的計數器，而且在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 圖形化使用者介面中，讓選取的效能計數器顯示在追蹤的旁邊。</span><span class="sxs-lookup"><span data-stu-id="77b18-103">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can open a Microsoft Windows performance log, choose the counters you want to correlate with a trace, and display the selected performance counters alongside the trace in the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] graphical user interface.</span></span> <span data-ttu-id="77b18-104">選取追蹤視窗中的事件後， [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的 [系統監視器] 資料窗格中的紅色直條，表示與選取的追蹤事件相互關聯的效能記錄資料。</span><span class="sxs-lookup"><span data-stu-id="77b18-104">When you select an event in the trace window, a vertical red bar in the System Monitor data window pane of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indicates the performance log data that correlates with the selected trace event.</span></span>  
  
 <span data-ttu-id="77b18-105">若要使追蹤與效能計數器相互關聯，請開啟包含 [StartTime]  與 [EndTime]  資料行的追蹤檔案或資料表，然後在  **[檔案]** [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 功能表上，按一下 [匯入效能資料]  。</span><span class="sxs-lookup"><span data-stu-id="77b18-105">To correlate a trace with performance counters, open a trace file or table that contains the **StartTime** and **EndTime** data columns, and then click **Import Performance Data** on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File** menu.</span></span> <span data-ttu-id="77b18-106">接著可以開啟效能記錄，然後選取要與追蹤相互關聯的「系統監視器」物件與計數器。</span><span class="sxs-lookup"><span data-stu-id="77b18-106">You can then open a performance log, and select the System Monitor objects and counters that you want to correlate with the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b18-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77b18-107">See Also</span></span>  
 [<span data-ttu-id="77b18-108">使追蹤與 Windows 效能記錄資料產生相互關聯 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="77b18-108">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
