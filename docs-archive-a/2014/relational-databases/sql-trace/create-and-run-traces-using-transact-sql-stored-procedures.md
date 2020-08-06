---
title: 使用 Transact-SQL 預存程序來建立和執行追蹤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2905ce2822598502ef6337d1a083fb6fde001c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597052"
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a><span data-ttu-id="e4321-102">使用 Transact-SQL 預存程序來建立和執行追蹤</span><span class="sxs-lookup"><span data-stu-id="e4321-102">Create and Run Traces Using Transact-SQL Stored Procedures</span></span>
  <span data-ttu-id="e4321-103">SQL 追蹤的追蹤處理，會因您使用 Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或使用系統預存程序來建立和執行追蹤，而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e4321-103">The process of tracing with SQL Trace varies depending on whether you create and run your trace by using Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or by using system stored procedures.</span></span>  
  
 <span data-ttu-id="e4321-104">您可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]系統預存程序代替 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，來建立和執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="e4321-104">As an alternative to [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can use [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to create and run traces.</span></span> <span data-ttu-id="e4321-105">使用系統預存程序的追蹤處理如下：</span><span class="sxs-lookup"><span data-stu-id="e4321-105">The process of tracing by using system stored procedures is as follows:</span></span>  
  
1.  <span data-ttu-id="e4321-106">使用 **sp_trace_create**建立追蹤。</span><span class="sxs-lookup"><span data-stu-id="e4321-106">Create a trace by using **sp_trace_create**.</span></span>  
  
2.  <span data-ttu-id="e4321-107">使用 **sp_trace_setevent**加入事件。</span><span class="sxs-lookup"><span data-stu-id="e4321-107">Add events with **sp_trace_setevent**.</span></span>  
  
3.  <span data-ttu-id="e4321-108">(選擇性) 使用 **sp_trace_setfilter**設定篩選。</span><span class="sxs-lookup"><span data-stu-id="e4321-108">(Optional) Set a filter with **sp_trace_setfilter**.</span></span>  
  
4.  <span data-ttu-id="e4321-109">使用 **sp_trace_setstatus**啟動追蹤。</span><span class="sxs-lookup"><span data-stu-id="e4321-109">Start the trace with **sp_trace_setstatus**.</span></span>  
  
5.  <span data-ttu-id="e4321-110">使用 **sp_trace_setstatus**停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="e4321-110">Stop the trace with **sp_trace_setstatus**.</span></span>  
  
6.  <span data-ttu-id="e4321-111">使用 **sp_trace_setstatus**關閉追蹤。</span><span class="sxs-lookup"><span data-stu-id="e4321-111">Close the trace with **sp_trace_setstatus**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4321-112">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系統預存程序會建立伺服器端的追蹤，其保證只要磁碟上有空間且未發生寫入錯誤，就不會遺失事件。</span><span class="sxs-lookup"><span data-stu-id="e4321-112">Using [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures creates a server-side trace, which guarantees that no events will be lost as long as there is space on the disk and no write errors occur.</span></span> <span data-ttu-id="e4321-113">如果磁碟已滿或磁碟錯誤，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體會繼續執行，但追蹤會停止。</span><span class="sxs-lookup"><span data-stu-id="e4321-113">If the disk becomes full or the disk fails, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance continues to run, but tracing stops.</span></span> <span data-ttu-id="e4321-114">如果已設定 **c2 audit mode** ，並且發生寫入失敗，則追蹤會停止且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體會關閉。</span><span class="sxs-lookup"><span data-stu-id="e4321-114">If the **c2 audit mode** is set, and there is a write failure, tracing stops and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span> <span data-ttu-id="e4321-115">如需 **c2 稽核模式** 設定的詳細資訊，請參閱 [c2 稽核模式伺服器組態選項](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="e4321-115">For more information about the **c2 audit mode** setting, see [c2 audit mode Server Configuration Option](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4321-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="e4321-116">In This Section</span></span>  
  
|<span data-ttu-id="e4321-117">主題</span><span class="sxs-lookup"><span data-stu-id="e4321-117">Topic</span></span>|<span data-ttu-id="e4321-118">描述</span><span class="sxs-lookup"><span data-stu-id="e4321-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e4321-119">最佳化 SQL 追蹤</span><span class="sxs-lookup"><span data-stu-id="e4321-119">Optimize SQL Trace</span></span>](sql-trace.md)|<span data-ttu-id="e4321-120">包含如何降低追蹤對於系統效能之影響的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4321-120">Contains information about ways you can reduce the effects of tracing on system performance.</span></span>|  
|[<span data-ttu-id="e4321-121">篩選追蹤</span><span class="sxs-lookup"><span data-stu-id="e4321-121">Filter a Trace</span></span>](filter-a-trace.md)|<span data-ttu-id="e4321-122">包含使用篩選進行追蹤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4321-122">Contains information about using filters for tracing.</span></span>|  
|[<span data-ttu-id="e4321-123">限制追蹤檔案和資料表的大小</span><span class="sxs-lookup"><span data-stu-id="e4321-123">Limit Trace File and Table Sizes</span></span>](limit-trace-file-and-table-sizes.md)|<span data-ttu-id="e4321-124">包含如何限制追蹤資料所寫入之檔案和資料表大小的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4321-124">Contains information about how to limit the size of files and tables where trace data is written.</span></span> <span data-ttu-id="e4321-125">請注意，只有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 可以將追蹤資訊寫入資料表。</span><span class="sxs-lookup"><span data-stu-id="e4321-125">Note that only [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can write trace information to tables.</span></span>|  
|[<span data-ttu-id="e4321-126">排程追蹤</span><span class="sxs-lookup"><span data-stu-id="e4321-126">Schedule Traces</span></span>](schedule-traces.md)|<span data-ttu-id="e4321-127">包含如何設定追蹤的開始時間和結束時間之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4321-127">Contains information about how to set the start time and the end time for tracing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4321-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4321-128">See Also</span></span>  
 <span data-ttu-id="e4321-129">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e4321-129">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="e4321-130">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e4321-130">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="e4321-131">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e4321-131">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span></span>  
 [<span data-ttu-id="e4321-132">sp_trace_setstatus &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4321-132">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
  
