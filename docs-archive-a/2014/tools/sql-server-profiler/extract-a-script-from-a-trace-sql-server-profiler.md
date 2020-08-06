---
title: 從追蹤中擷取指令碼 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6633fafb8a39b189093044ef39694afa601af7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686589"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a><span data-ttu-id="f9ac9-102">從追蹤中擷取指令碼 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="f9ac9-102">Extract a Script from a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="f9ac9-103">此主題描述如何從追蹤檔案或資料表中擷取 [!INCLUDE[tsql](../../includes/tsql-md.md)] 事件，並利用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 將它們儲存為 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="f9ac9-103">This topic describes how to extract [!INCLUDE[tsql](../../includes/tsql-md.md)] events from a trace file or table and save them as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a><span data-ttu-id="f9ac9-104">若要從追蹤檔案或資料表中擷取 Transact-SQL 指令碼</span><span class="sxs-lookup"><span data-stu-id="f9ac9-104">To extract a Transact-SQL script from a trace file or table</span></span>  
  
1.  <span data-ttu-id="f9ac9-105">開啟包含您要儲存到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 事件的追蹤檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="f9ac9-105">Open a trace file or table that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] events that you want to save to a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="f9ac9-106">如需詳細資訊，請參閱 [開啟追蹤檔案 &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 或 [開啟追蹤資料表 &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)隨附的預先定義「微調」範本。</span><span class="sxs-lookup"><span data-stu-id="f9ac9-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="f9ac9-107">在 [檔案]  功能表上，依序指向 [匯出]  和 [擷取 SQL Server 事件]  ，然後按一下 [擷取 Transact-SQL 事件]  。</span><span class="sxs-lookup"><span data-stu-id="f9ac9-107">On the **File** menu, point to **Export**, point to **Extract SQL Server Events**, and then click **Extract Transact-SQL Events**.</span></span>  
  
3.  <span data-ttu-id="f9ac9-108">在 **[另存新檔]** 對話方塊中，輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 檔案的名稱，然後按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="f9ac9-108">In the **Save As** dialog box, type a name for the [!INCLUDE[tsql](../../includes/tsql-md.md)] file, and click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ac9-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9ac9-109">See Also</span></span>  
 [<span data-ttu-id="f9ac9-110">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="f9ac9-110">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
