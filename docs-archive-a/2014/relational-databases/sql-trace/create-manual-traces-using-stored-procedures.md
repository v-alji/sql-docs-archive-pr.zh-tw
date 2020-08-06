---
title: 使用預存程序建立手動追蹤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e2840dced22ccdba8fe71cc87c05d7fd6fb4be58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597050"
---
# <a name="create-manual-traces-using-stored-procedures"></a><span data-ttu-id="486d7-102">使用預存程序建立手動追蹤</span><span class="sxs-lookup"><span data-stu-id="486d7-102">Create Manual Traces using Stored Procedures</span></span>
  <span data-ttu-id="486d7-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所提供的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系統預存程序可建立 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體的追蹤。</span><span class="sxs-lookup"><span data-stu-id="486d7-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to create traces on an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="486d7-104">您可以從自己的應用程式中使用這些系統預存程序以手動建立追蹤，而不是使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]建立追蹤。</span><span class="sxs-lookup"><span data-stu-id="486d7-104">These system stored procedures can be used from within your own applications to create traces manually, instead of using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="486d7-105">如此一來，就可以依照您的企業需求撰寫自訂的應用程式。</span><span class="sxs-lookup"><span data-stu-id="486d7-105">This allows you to write custom applications specific to the needs of your enterprise.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="486d7-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="486d7-106">In This Section</span></span>  
 <span data-ttu-id="486d7-107">下表列出用於追蹤 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]之執行個體的系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="486d7-107">The following table lists the system stored procedures for tracing an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
|<span data-ttu-id="486d7-108">預存程序</span><span class="sxs-lookup"><span data-stu-id="486d7-108">Stored procedure</span></span>|<span data-ttu-id="486d7-109">已執行的工作</span><span class="sxs-lookup"><span data-stu-id="486d7-109">Task performed</span></span>|  
|----------------------|--------------------|  
|[<span data-ttu-id="486d7-110">sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="486d7-110">sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql)|<span data-ttu-id="486d7-111">傳回追蹤中所含事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="486d7-111">Returns information about events included in a trace.</span></span>|  
|[<span data-ttu-id="486d7-112">sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="486d7-112">sys.fn_trace_getinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)|<span data-ttu-id="486d7-113">傳回所指定追蹤或所有現有追蹤的資訊。</span><span class="sxs-lookup"><span data-stu-id="486d7-113">Returns information about a specified trace or all existing traces.</span></span>|  
|[<span data-ttu-id="486d7-114">sp_trace_create &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="486d7-114">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)|<span data-ttu-id="486d7-115">建立追蹤定義。</span><span class="sxs-lookup"><span data-stu-id="486d7-115">Creates a trace definition.</span></span> <span data-ttu-id="486d7-116">新追蹤會處於已停止狀態。</span><span class="sxs-lookup"><span data-stu-id="486d7-116">The new trace will be in a stopped state.</span></span>|  
|[<span data-ttu-id="486d7-117">sp_trace_generateevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="486d7-117">sp_trace_generateevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)|<span data-ttu-id="486d7-118">建立使用者定義事件。</span><span class="sxs-lookup"><span data-stu-id="486d7-118">Creates a user-defined event.</span></span>|  
|[<span data-ttu-id="486d7-119">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="486d7-119">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)|<span data-ttu-id="486d7-120">在追蹤中新增或移除事件類別或資料行。</span><span class="sxs-lookup"><span data-stu-id="486d7-120">Adds an event class or data column to a trace, or removes one from it.</span></span>|  
|[<span data-ttu-id="486d7-121">sp_trace_setstatus &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="486d7-121">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|<span data-ttu-id="486d7-122">啟動、停止或關閉追蹤。</span><span class="sxs-lookup"><span data-stu-id="486d7-122">Starts, stops, or closes a trace.</span></span>|  
|[<span data-ttu-id="486d7-123">sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="486d7-123">sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)|<span data-ttu-id="486d7-124">傳回追蹤所套用之篩選的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="486d7-124">Returns information about filters applied to a trace.</span></span>|  
|[<span data-ttu-id="486d7-125">sp_trace_setfilter &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="486d7-125">sp_trace_setfilter &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|<span data-ttu-id="486d7-126">將新的或修改過的篩選套用至追蹤。</span><span class="sxs-lookup"><span data-stu-id="486d7-126">Applies a new or modified filter to a trace.</span></span>|  
  
 <span data-ttu-id="486d7-127">**若要使用預存程序來定義自己的追蹤**</span><span class="sxs-lookup"><span data-stu-id="486d7-127">**To define your own trace using stored procedures**</span></span>  
  
1.  <span data-ttu-id="486d7-128">使用 **sp_trace_setevent**指定要擷取的事件。</span><span class="sxs-lookup"><span data-stu-id="486d7-128">Specify the events to capture using **sp_trace_setevent**.</span></span>  
  
2.  <span data-ttu-id="486d7-129">指定事件篩選條件。</span><span class="sxs-lookup"><span data-stu-id="486d7-129">Specify any event filters.</span></span> <span data-ttu-id="486d7-130">如需詳細資訊，請參閱[設定追蹤篩選 &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="486d7-130">For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md).</span></span>  
  
3.  <span data-ttu-id="486d7-131">使用 **sp_trace_create** 指定擷取事件資料的目的地。</span><span class="sxs-lookup"><span data-stu-id="486d7-131">Specify the destination for the captured event data using **sp_trace_create**.</span></span>  
  
 <span data-ttu-id="486d7-132">如需使用追蹤預存程序的範例，請參閱[建立追蹤 &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="486d7-132">For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).</span></span>  
  
 <span data-ttu-id="486d7-133">**若要設定追蹤定義預設值**</span><span class="sxs-lookup"><span data-stu-id="486d7-133">**To set trace definition defaults**</span></span>  
  
 [<span data-ttu-id="486d7-134">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="486d7-134">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
 <span data-ttu-id="486d7-135">**若要設定追蹤顯示預設值**</span><span class="sxs-lookup"><span data-stu-id="486d7-135">**To set trace display defaults**</span></span>  
  
 [<span data-ttu-id="486d7-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="486d7-136">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 <span data-ttu-id="486d7-137">**若要建立追蹤**</span><span class="sxs-lookup"><span data-stu-id="486d7-137">**To create a trace**</span></span>  
  
 [<span data-ttu-id="486d7-138">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="486d7-138">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [<span data-ttu-id="486d7-139">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="486d7-139">Transact-SQL</span></span>](../sql-trace/create-a-trace-transact-sql.md)  
  
 <span data-ttu-id="486d7-140">**若要從追蹤範本中移除事件**</span><span class="sxs-lookup"><span data-stu-id="486d7-140">**To add or remove events from a trace template**</span></span>  
  
 [<span data-ttu-id="486d7-141">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="486d7-141">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="486d7-142">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="486d7-142">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
