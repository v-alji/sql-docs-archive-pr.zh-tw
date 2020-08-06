---
title: 將追蹤結果儲存至檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 644fc812bbb4863c336ff2f53f5b2d67ee0a4d5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585785"
---
# <a name="save-trace-results-to-a-file"></a><span data-ttu-id="3ff3d-102">將追蹤結果儲存至檔案</span><span class="sxs-lookup"><span data-stu-id="3ff3d-102">Save Trace Results to a File</span></span>
  <span data-ttu-id="3ff3d-103">您可以將追蹤結果儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-103">You can save trace results to a file.</span></span> <span data-ttu-id="3ff3d-104">追蹤檔案是用來寫入追蹤結果的檔案。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-104">A trace file is a file where the trace results are written.</span></span> <span data-ttu-id="3ff3d-105">追蹤檔案可以位於本機目錄 (例如 C:\\  \\檔案名稱.trc  ) 或網路目錄 (例如 \\\電腦名稱\共用名稱\檔案名稱.trc)。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-105">A trace file can be located either in a local directory (such as C:\\*foldername*\\*filename.trc*) or a network directory (such as \\\computername\sharename\filename.trc).</span></span>  
  
 <span data-ttu-id="3ff3d-106">您可以使用追蹤檔案來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3ff3d-106">You can use the trace files to do the following:</span></span>  
  
-   <span data-ttu-id="3ff3d-107">重新執行追蹤</span><span class="sxs-lookup"><span data-stu-id="3ff3d-107">Replay traces</span></span>  
  
-   <span data-ttu-id="3ff3d-108">稽核 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ff3d-108">Audit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="3ff3d-109">進行效能分析</span><span class="sxs-lookup"><span data-stu-id="3ff3d-109">Conduct performance analysis</span></span>  
  
-   <span data-ttu-id="3ff3d-110">使追蹤事件與效能計數器相互關聯，以加強問題偵測</span><span class="sxs-lookup"><span data-stu-id="3ff3d-110">Correlate trace events with performance counters to enhance problem detection</span></span>  
  
-   <span data-ttu-id="3ff3d-111">執行 Database Engine Tuning Advisor 分析</span><span class="sxs-lookup"><span data-stu-id="3ff3d-111">Perform Database Engine Tuning Advisor analysis</span></span>  
  
-   <span data-ttu-id="3ff3d-112">完成查詢最佳化。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-112">Carry out query optimization</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="3ff3d-113">當 **@tracefile** 預存程式**sp_trace_create**的引數指定路徑和檔案名時，會將追蹤結果儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-113">saves trace results to a file when a path and file name are specified for the **@tracefile** argument of the stored procedure **sp_trace_create**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ff3d-114">若要將路徑指定到 **sp_trace_create** 預存程序以儲存追蹤檔案，則其必須是伺服器可存取的目錄。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-114">If a path is specified to the **sp_trace_create** stored procedure for saving the trace file, the directory must be accessible to the server.</span></span> <span data-ttu-id="3ff3d-115">另請注意，若要在 **sp_trace_create**指定本機目錄，此目錄必須是伺服器電腦上的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-115">Also be aware that if a local directory is specified to **sp_trace_create**, it is a local directory on the server computer.</span></span>  
  
 <span data-ttu-id="3ff3d-116">如果使用了 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，您就可以將追蹤結果儲存到檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-116">If [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is used, it allows you to save trace results to a file or to a table.</span></span> <span data-ttu-id="3ff3d-117">將追蹤結果儲存到資料表與將追蹤儲存到檔案一樣，都允許稍後進行存取，但是儲存到資料表還有一項優點，就是可以透過查詢資料表來搜尋特定事件。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-117">Saving trace results to a table allows the same access as saving the trace to a file plus you can query the table to search for specific events.</span></span>  
  
 <span data-ttu-id="3ff3d-118">如需儲存追蹤結果的詳細資訊，請參閱[將追蹤結果儲存到資料表 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) 和[將追蹤結果儲存至檔案 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="3ff3d-118">For more information about saving trace results, see [Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) and [Save Trace Results to a File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff3d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ff3d-119">See Also</span></span>  
 <span data-ttu-id="3ff3d-120">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3ff3d-120">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="3ff3d-121">[建立追蹤 &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="3ff3d-121">[Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md) </span></span>  
 [<span data-ttu-id="3ff3d-122">建立追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="3ff3d-122">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
