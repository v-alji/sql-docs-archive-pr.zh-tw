---
title: 建立 Transact-SQL 指令碼以執行追蹤 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3d4b4bebb2a3e05e3de12e59c53ccca9c980afd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686594"
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a><span data-ttu-id="0e543-102">建立 Transact-SQL 指令碼以執行追蹤 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="0e543-102">Create a Transact-SQL Script for Running a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="0e543-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，從現有的追蹤檔或資料表建立 Transact-SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="0e543-103">This topic describes how to create a Transact-SQL script from an existing trace file or table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a><span data-ttu-id="0e543-104">若要建立 Transact-SQL 指令碼以執行追蹤</span><span class="sxs-lookup"><span data-stu-id="0e543-104">To create a Transact-SQL script to run a trace</span></span>  
  
1.  <span data-ttu-id="0e543-105">開啟追蹤檔或資料表。</span><span class="sxs-lookup"><span data-stu-id="0e543-105">Open a trace file or table.</span></span> <span data-ttu-id="0e543-106">如需詳細資訊，請參閱 [開啟追蹤檔案 &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 或 [開啟追蹤資料表 &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)隨附的預先定義「微調」範本。</span><span class="sxs-lookup"><span data-stu-id="0e543-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="0e543-107">在 [檔案]  功能表上，依序指向 [匯出]  和 [指令碼追蹤定義]  ，然後按一下對應至您想要追蹤之伺服器的版本。</span><span class="sxs-lookup"><span data-stu-id="0e543-107">On the**File**menu, point to **Export**, point to **Script Trace Definition**, and then click the version that corresponds to the server you want to trace.</span></span>  
  
3.  <span data-ttu-id="0e543-108">在 [另存新檔]  對話方塊中，輸入指令碼檔案的名稱，然後按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="0e543-108">In the **Save As** dialog box, enter a name for the script file, and then click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e543-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e543-109">See Also</span></span>  
 <span data-ttu-id="0e543-110">[SQL Server Profiler 範本和權限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="0e543-110">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="0e543-111">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="0e543-111">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
