---
title: 修改現有的追蹤 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 55b8172ef8e6188059c484ab41f1a719e0e9f8c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585787"
---
# <a name="modify-an-existing-trace-transact-sql"></a><span data-ttu-id="e8eaf-102">修改現有的追蹤 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e8eaf-102">Modify an Existing Trace (Transact-SQL)</span></span>
  <span data-ttu-id="e8eaf-103">此主題描述如何使用預存程序來修改現有的追蹤。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-103">This topic describes how to use stored procedures to modify an existing trace.</span></span>  
  
### <a name="to-modify-an-existing-trace"></a><span data-ttu-id="e8eaf-104">若要修改現有的追蹤</span><span class="sxs-lookup"><span data-stu-id="e8eaf-104">To modify an existing trace</span></span>  
  
1.  <span data-ttu-id="e8eaf-105">如果追蹤已在執行，請執行 **sp_trace_setstatus** 並指定 **@status = 0**，以停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-105">If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="e8eaf-106">若要修改追蹤事件，請執行 **sp_trace_setevent** 並利用參數指定要做的變更。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-106">To modify trace events, execute **sp_trace_setevent** by specifying the changes through the parameters.</span></span> <span data-ttu-id="e8eaf-107">這些參數依序排列如下：</span><span class="sxs-lookup"><span data-stu-id="e8eaf-107">Listed in order, the parameters are:</span></span>  
  
    -   <span data-ttu-id="e8eaf-108">**@traceid** (追蹤識別碼) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-108">**@traceid** (Trace ID)</span></span>  
  
    -   <span data-ttu-id="e8eaf-109">**@eventid** (事件識別碼) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-109">**@eventid** (Event ID)</span></span>  
  
    -   <span data-ttu-id="e8eaf-110">**@columnid** (資料行識別碼) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-110">**@columnid** (Column ID)</span></span>  
  
    -   <span data-ttu-id="e8eaf-111">**@on**) 上的 (</span><span class="sxs-lookup"><span data-stu-id="e8eaf-111">**@on** (ON)</span></span>  
  
     <span data-ttu-id="e8eaf-112">當您修改 **@on** 參數時，請記住其與參數的互動 **@columnid** ：</span><span class="sxs-lookup"><span data-stu-id="e8eaf-112">When you modify the **@on** parameter, keep in mind its interaction with the **@columnid** parameter:</span></span>  
  
    |<span data-ttu-id="e8eaf-113">開啟</span><span class="sxs-lookup"><span data-stu-id="e8eaf-113">ON</span></span>|<span data-ttu-id="e8eaf-114">資料行識別碼</span><span class="sxs-lookup"><span data-stu-id="e8eaf-114">Column ID</span></span>|<span data-ttu-id="e8eaf-115">結果</span><span class="sxs-lookup"><span data-stu-id="e8eaf-115">Result</span></span>|  
    |--------|---------------|------------|  
    |<span data-ttu-id="e8eaf-116">ON (**1**)</span><span class="sxs-lookup"><span data-stu-id="e8eaf-116">ON (**1**)</span></span>|<span data-ttu-id="e8eaf-117">NULL</span><span class="sxs-lookup"><span data-stu-id="e8eaf-117">NULL</span></span>|<span data-ttu-id="e8eaf-118">會開啟事件。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-118">Event is turned on.</span></span> <span data-ttu-id="e8eaf-119">會清除所有資料行。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-119">All columns are cleared.</span></span>|  
    ||<span data-ttu-id="e8eaf-120">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="e8eaf-120">NOT NULL</span></span>|<span data-ttu-id="e8eaf-121">資料行會針對特定的事件開啟。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-121">Column is turned on for the specified event.</span></span>|  
    |<span data-ttu-id="e8eaf-122">OFF (**0**)</span><span class="sxs-lookup"><span data-stu-id="e8eaf-122">OFF (**0**)</span></span>|<span data-ttu-id="e8eaf-123">NULL</span><span class="sxs-lookup"><span data-stu-id="e8eaf-123">NULL</span></span>|<span data-ttu-id="e8eaf-124">會關閉事件。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-124">Event is turned off.</span></span> <span data-ttu-id="e8eaf-125">會清除所有資料行。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-125">All columns are cleared.</span></span>|  
    ||<span data-ttu-id="e8eaf-126">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="e8eaf-126">NOT NULL</span></span>|<span data-ttu-id="e8eaf-127">會針對特定的事件關閉資料行。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-127">Column is turned off for the specified event.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8eaf-128">與一般的預存程序不同，所有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 預存程序 (<strong>sp_trace_*xx*</strong>) 的參數均嚴格區分類型，且不支援自動資料類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-128">Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="e8eaf-129">如果沒有依照引數描述所指定，以正確的輸入參數資料類型來呼叫這些參數，預存程序會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-129">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e8eaf-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8eaf-130">See Also</span></span>  
 <span data-ttu-id="e8eaf-131">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-131">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="e8eaf-132">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-132">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="e8eaf-133">[系統預存程序 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-133">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="e8eaf-134">SQL Server Profiler 預存程序 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8eaf-134">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
