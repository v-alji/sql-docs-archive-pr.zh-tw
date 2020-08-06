---
title: 刪除追蹤 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b3551cff36ef6e2c2e9cc6a4d9b7056ae44cb950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596607"
---
# <a name="delete-a-trace-transact-sql"></a><span data-ttu-id="4fce6-102">刪除追蹤 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4fce6-102">Delete a Trace (Transact-SQL)</span></span>
  <span data-ttu-id="4fce6-103">本主題說明如何使用預存程序來刪除追蹤。</span><span class="sxs-lookup"><span data-stu-id="4fce6-103">This topic describes how to use stored procedures to delete a trace.</span></span>  
  
 <span data-ttu-id="4fce6-104">如需使用追蹤預存程序的範例，請參閱[建立追蹤 &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-104">For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md).</span></span>  
  
### <a name="to-delete-a-trace"></a><span data-ttu-id="4fce6-105">若要刪除追蹤</span><span class="sxs-lookup"><span data-stu-id="4fce6-105">To delete a trace</span></span>  
  
1.  <span data-ttu-id="4fce6-106">指定 **@status = 0**，執行 **sp_trace_setstatus** 以停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="4fce6-106">Execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="4fce6-107">指定 **@status = 2**，執行 **sp_trace_setstatus** 以關閉追蹤，並將其資訊從伺服器中刪除。</span><span class="sxs-lookup"><span data-stu-id="4fce6-107">Execute **sp_trace_setstatus** by specifying **@status = 2** to close the trace and delete its information from the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fce6-108">您必須先關閉追蹤，才能將它刪除。</span><span class="sxs-lookup"><span data-stu-id="4fce6-108">A trace must be stopped first before it can be closed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fce6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fce6-109">See Also</span></span>  
 <span data-ttu-id="4fce6-110">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4fce6-110">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="4fce6-111">[系統預存程序 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4fce6-111">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="4fce6-112">SQL Server Profiler 預存程序 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4fce6-112">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
