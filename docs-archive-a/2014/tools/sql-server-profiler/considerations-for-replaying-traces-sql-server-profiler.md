---
title: 重新執行追蹤的考量 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c2f030a0191596e40ef1ee9e2b0b2d4da34c773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686607"
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a><span data-ttu-id="f38bd-102">重新執行追蹤的考量 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="f38bd-102">Considerations for Replaying Traces (SQL Server Profiler)</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f38bd-103">無法重新執行下列種類的追蹤：</span><span class="sxs-lookup"><span data-stu-id="f38bd-103">cannot replay the following kinds of traces:</span></span>  
  
-   <span data-ttu-id="f38bd-104">包含異動複寫與其他交易記錄活動的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f38bd-104">Traces that contain transactional replication and other transaction log activity.</span></span> <span data-ttu-id="f38bd-105">略過這些事件。</span><span class="sxs-lookup"><span data-stu-id="f38bd-105">These events are skipped.</span></span> <span data-ttu-id="f38bd-106">其他類型的複寫不會標示交易記錄，因此不受影響。</span><span class="sxs-lookup"><span data-stu-id="f38bd-106">Other types of replication do not mark the transaction log so they are not affected.</span></span>  
  
-   <span data-ttu-id="f38bd-107">包含了涉及全域唯一識別碼 (GUID) 作業的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f38bd-107">Traces that contain operations that involve globally unique identifiers (GUID).</span></span> <span data-ttu-id="f38bd-108">將略過這些事件。</span><span class="sxs-lookup"><span data-stu-id="f38bd-108">These events will be skipped.</span></span>  
  
-   <span data-ttu-id="f38bd-109">包含涉及 **bcp**公用程式、BULK INSERT、READTEXT、WRITETEXT 和 UPDATETEXT 陳述式之 **text**、 **ntext** 和 **image** 資料行上作業的追蹤，以及包含全文檢索作業的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f38bd-109">Traces that contain operations on **text**, **ntext**, and **image** columns involving the **bcp** utility, the BULK INSERT, READTEXT, WRITETEXT, and UPDATETEXT statements, and full-text operations.</span></span> <span data-ttu-id="f38bd-110">略過這些事件。</span><span class="sxs-lookup"><span data-stu-id="f38bd-110">These events are skipped.</span></span>  
  
-   <span data-ttu-id="f38bd-111">包含工作階段繫結： **sp_getbindtoken** 和 **sp_bindsession** 系統預存程序的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f38bd-111">Traces that contain session binding: **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span> <span data-ttu-id="f38bd-112">略過這些事件。</span><span class="sxs-lookup"><span data-stu-id="f38bd-112">These events are skipped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f38bd-113">如果您沒有使用預先設定的重新執行範本 (**TSQL_Replay**)，也沒有擷取所有必要的資料，則 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 不會重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="f38bd-113">If you do not use the preconfigured replay template (**TSQL_Replay**), and do not capture all required data, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] does not replay the trace.</span></span> <span data-ttu-id="f38bd-114">如需詳細資訊，請參閱 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f38bd-114">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
 <span data-ttu-id="f38bd-115">如需有關重做追蹤時所需之權限的詳細資訊，請參閱＜ [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f38bd-115">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38bd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f38bd-116">See Also</span></span>  
 <span data-ttu-id="f38bd-117">[bcp 公用程式](../bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f38bd-117">[bcp Utility](../bcp-utility.md) </span></span>  
 <span data-ttu-id="f38bd-118">[SQL Server 事件類別參考](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f38bd-118">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="f38bd-119">[sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f38bd-119">[sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span></span>  
 <span data-ttu-id="f38bd-120">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f38bd-120">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 <span data-ttu-id="f38bd-121">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f38bd-121">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="f38bd-122">[READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f38bd-122">[READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span></span>  
 <span data-ttu-id="f38bd-123">[WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f38bd-123">[WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span></span>  
 [<span data-ttu-id="f38bd-124">UPDATETEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f38bd-124">UPDATETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/updatetext-transact-sql)  
  
  
