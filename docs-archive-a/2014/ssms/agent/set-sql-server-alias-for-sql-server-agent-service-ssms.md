---
title: 設定追蹤篩選 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 47d797c84a05f50da026280f6e197f965d804426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597537"
---
# <a name="set-a-trace-filter-transact-sql"></a><span data-ttu-id="a5c26-102">設定追蹤篩選 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5c26-102">Set a Trace Filter (Transact-SQL)</span></span>
  <span data-ttu-id="a5c26-103">本主題描述如何使用預存程序來建立篩選，針對所追蹤的事件，只擷取您需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="a5c26-103">This topic describes how to use stored procedures to create a filter that retrieves only the information you need on an event being traced.</span></span>  
  
### <a name="to-set-a-trace-filter"></a><span data-ttu-id="a5c26-104">若要設定追蹤篩選</span><span class="sxs-lookup"><span data-stu-id="a5c26-104">To set a trace filter</span></span>  
  
1.  <span data-ttu-id="a5c26-105">如果追蹤已在執行，請執行 **sp_trace_setstatus** 並指定 **@status = 0**，以停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="a5c26-105">If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="a5c26-106">執行 **sp_trace_setfilter** 以設定要從追蹤的事件中擷取的相關資訊類型。</span><span class="sxs-lookup"><span data-stu-id="a5c26-106">Execute **sp_trace_setfilter** to configure the type of information to retrieve for the event being traced.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a5c26-107">與一般的預存程序不同，所有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 預存程序 (<strong>sp_trace_*xx*</strong>) 的參數均嚴格區分類型，且不支援自動資料類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="a5c26-107">Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="a5c26-108">如果沒有依照引數描述所指定，以正確的輸入參數資料類型來呼叫這些參數，預存程序會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="a5c26-108">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure will return an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c26-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5c26-109">See Also</span></span>  
 <span data-ttu-id="a5c26-110">[篩選追蹤](../../relational-databases/sql-trace/filter-a-trace.md) </span><span class="sxs-lookup"><span data-stu-id="a5c26-110">[Filter a Trace](../../relational-databases/sql-trace/filter-a-trace.md) </span></span>  
 <span data-ttu-id="a5c26-111">[sp_trace_setfilter &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5c26-111">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span></span>  
 <span data-ttu-id="a5c26-112">[sp_trace_setstatus &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5c26-112">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="a5c26-113">[&#40;Transact-sql&#41;的系統預存程式](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5c26-113">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="a5c26-114">SQL Server Profiler 預存程序 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a5c26-114">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
