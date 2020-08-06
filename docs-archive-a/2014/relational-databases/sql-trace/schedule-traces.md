---
title: 排程追蹤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a698d88db35c84f7611293cf45807203c883865a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597761"
---
# <a name="schedule-traces"></a><span data-ttu-id="1dc22-102">排程追蹤</span><span class="sxs-lookup"><span data-stu-id="1dc22-102">Schedule Traces</span></span>
  <span data-ttu-id="1dc22-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有兩個方法可以排程追蹤。</span><span class="sxs-lookup"><span data-stu-id="1dc22-103">There are two ways to schedule tracing in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1dc22-104">您可以：</span><span class="sxs-lookup"><span data-stu-id="1dc22-104">You can:</span></span>  
  
-   <span data-ttu-id="1dc22-105">啟用追蹤停止時間。</span><span class="sxs-lookup"><span data-stu-id="1dc22-105">Enable a trace stop time.</span></span>  
  
-   <span data-ttu-id="1dc22-106">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來排程追蹤。</span><span class="sxs-lookup"><span data-stu-id="1dc22-106">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to schedule a trace.</span></span>  
  
## <a name="specifying-a-stop-time"></a><span data-ttu-id="1dc22-107">指定停止時間</span><span class="sxs-lookup"><span data-stu-id="1dc22-107">Specifying a Stop Time</span></span>  
 <span data-ttu-id="1dc22-108">如果使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序或 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，您可以指定追蹤停止時間。</span><span class="sxs-lookup"><span data-stu-id="1dc22-108">You can specify a trace stop time if you use [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures or if you use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="1dc22-109">最初設定追蹤時，必須設定停止時間。</span><span class="sxs-lookup"><span data-stu-id="1dc22-109">The stop time must be set when the trace is originally configured.</span></span>  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a><span data-ttu-id="1dc22-110">使用 SQL Server Agent 來排程追蹤</span><span class="sxs-lookup"><span data-stu-id="1dc22-110">Scheduling Traces by Using SQL Server Agent</span></span>  
 <span data-ttu-id="1dc22-111">排程追蹤最好的方法是利用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 啟動追蹤，然後使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序 **sp_trace_setstatus**或 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]指定追蹤停止時間。</span><span class="sxs-lookup"><span data-stu-id="1dc22-111">The best way to schedule traces is to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to start the trace and then specify a trace stop time by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure **sp_trace_setstatus**, or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="1dc22-112">**若要設定追蹤的結束時間篩選**</span><span class="sxs-lookup"><span data-stu-id="1dc22-112">**To set an end time filter for a trace**</span></span>  
  
 [<span data-ttu-id="1dc22-113">根據事件結束時間篩選事件 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="1dc22-113">Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [<span data-ttu-id="1dc22-114">sp_trace_setstatus &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1dc22-114">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="1dc22-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dc22-115">See Also</span></span>  
 [<span data-ttu-id="1dc22-116">自動化管理工作 &#40;SQL Server Agent&#41;</span><span class="sxs-lookup"><span data-stu-id="1dc22-116">Automated Administration Tasks &#40;SQL Server Agent&#41;</span></span>](../../ssms/agent/sql-server-agent.md)  
  
  
