---
title: 檢視篩選資訊 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d94a7b4a73c264c1fb3a950aa1c9615a73db956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710498"
---
# <a name="view-filter-information-transact-sql"></a><span data-ttu-id="b9201-102">檢視篩選資訊 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b9201-102">View Filter Information (Transact-SQL)</span></span>
  <span data-ttu-id="b9201-103">此主題描述如何使用內建函數來檢視追蹤篩選資訊。</span><span class="sxs-lookup"><span data-stu-id="b9201-103">This topic describes how to use built-in functions to view trace filter information.</span></span>  
  
### <a name="to-view-filter-information"></a><span data-ttu-id="b9201-104">若要檢視篩選資訊</span><span class="sxs-lookup"><span data-stu-id="b9201-104">To view filter information</span></span>  
  
1.  <span data-ttu-id="b9201-105">藉由指定需要篩選資訊的追蹤識別碼，執行 **fn_trace_getfilterinfo** 。</span><span class="sxs-lookup"><span data-stu-id="b9201-105">Execute **fn_trace_getfilterinfo** by specifying the ID of the trace about which filter information is needed.</span></span> <span data-ttu-id="b9201-106">此函數會傳回資料表，其中列出篩選、篩選套用的資料行及篩選套用的值。</span><span class="sxs-lookup"><span data-stu-id="b9201-106">This function returns a table that lists the filters, the columns on which the filters are applied, and the values on which the filter is applied.</span></span>  
  
     <span data-ttu-id="b9201-107">以下列方式叫用函數：</span><span class="sxs-lookup"><span data-stu-id="b9201-107">Invoke the function this way:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b9201-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9201-108">See Also</span></span>  
 <span data-ttu-id="b9201-109">[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b9201-109">[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql) </span></span>  
 <span data-ttu-id="b9201-110">[系統預存程序 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b9201-110">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="b9201-111">SQL Server Profiler 預存程序 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b9201-111">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
