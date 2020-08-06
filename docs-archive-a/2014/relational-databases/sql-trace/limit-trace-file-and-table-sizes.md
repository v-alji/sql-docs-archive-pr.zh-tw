---
title: 限制追蹤檔案和資料表的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- traces [SQL Server], file size
- size [SQL Server], tables
- file rollover option [SQL Server]
- size [SQL Server], files
ms.assetid: 88c31b02-f44c-4a14-be8b-437f2097de12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7795dfdadb8fb3bbaa1b55dcd5c962d24a7ba29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597763"
---
# <a name="limit-trace-file-and-table-sizes"></a><span data-ttu-id="f2b97-102">限制追蹤檔案和資料表的大小</span><span class="sxs-lookup"><span data-stu-id="f2b97-102">Limit Trace File and Table Sizes</span></span>
  <span data-ttu-id="f2b97-103">「SQL 追蹤」結果的大小視追蹤所包含的事件類別和 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的使用方式而定。</span><span class="sxs-lookup"><span data-stu-id="f2b97-103">SQL Trace results vary in size depending on the event classes that are included in the trace and the way in which the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is used.</span></span> <span data-ttu-id="f2b97-104">如果您追蹤經常發生的事件類別，可設定檔案大小上限或最大資料列數目，將追蹤收集的資料量降到最低。</span><span class="sxs-lookup"><span data-stu-id="f2b97-104">If you trace event classes that occur frequently, you can minimize the amount of data that the trace collects by setting the maximum file size or the maximum number of rows.</span></span> <span data-ttu-id="f2b97-105">透過指定檔案大小上限或最大資料列數目，您就可以確保追蹤檔或資料表不會擴展超過指定的限制。</span><span class="sxs-lookup"><span data-stu-id="f2b97-105">By specifying the maximum file size or rows, you ensure that the trace file or table will not grow beyond the specified limit.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2b97-106">如果您將追蹤資料儲存到已存在的檔案，就可以將資料附加到檔案或覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="f2b97-106">If you save trace data to a file that already exists, you can append data to the file or overwrite the file.</span></span> <span data-ttu-id="f2b97-107">如果您選擇將資料附加到檔案，而追蹤檔已經達到或超過指定的檔案大小上限時，將會提醒您選擇增加檔案大小上限或指定新的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2b97-107">If you choose to append data to the file, and the trace file already meets or exceeds the specified maximum file size, you are notified and given the opportunity either to increase the maximum file size or specify a new file.</span></span> <span data-ttu-id="f2b97-108">追蹤資料表也是如此。</span><span class="sxs-lookup"><span data-stu-id="f2b97-108">The same is true for trace tables.</span></span>  
  
## <a name="maximum-file-size"></a><span data-ttu-id="f2b97-109">檔案大小上限</span><span class="sxs-lookup"><span data-stu-id="f2b97-109">Maximum File Size</span></span>  
 <span data-ttu-id="f2b97-110">已設定檔案大小上限的追蹤，在達到檔案大小上限之後，將會停止儲存追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="f2b97-110">A trace that has a maximum file size stops saving trace information to the file after the maximum file size has been reached.</span></span> <span data-ttu-id="f2b97-111">此選項可讓您將事件分組為更小、更易於管理的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2b97-111">This option allows you to group events into smaller, more manageable files.</span></span> <span data-ttu-id="f2b97-112">此外，限制檔案大小也可讓自動追蹤執行起來較為安全，因為在達到檔案大小上限時追蹤就會停止。</span><span class="sxs-lookup"><span data-stu-id="f2b97-112">In addition, limiting file size makes it safer to run unattended traces, because the trace stops when the maximum file size is reached.</span></span> <span data-ttu-id="f2b97-113">對於透過 Transact-SQL 預存程序或使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]建立的追蹤，您可以設定檔案大小上限。</span><span class="sxs-lookup"><span data-stu-id="f2b97-113">You can set the maximum file size for traces created by means of Transact-SQL stored procedures or by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="f2b97-114">檔案大小上限選項的上限是 1 GB。</span><span class="sxs-lookup"><span data-stu-id="f2b97-114">There is an upper limit of 1 gigabyte (GB) for the maximum file size option.</span></span> <span data-ttu-id="f2b97-115">預設的檔案大小上限是 5 MB。</span><span class="sxs-lookup"><span data-stu-id="f2b97-115">The default maximum file size is 5 megabytes (MB).</span></span>  
  
### <a name="enabling-file-rollover"></a><span data-ttu-id="f2b97-116">啟用檔案換用</span><span class="sxs-lookup"><span data-stu-id="f2b97-116">Enabling File Rollover</span></span>  
 <span data-ttu-id="f2b97-117">檔案換用選項會使得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在達到最大檔案大小時，關閉目前的檔案並建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2b97-117">The file rollover option causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to close the current file and create a new file when the maximum file size is reached.</span></span> <span data-ttu-id="f2b97-118">新檔案與舊檔案的名稱一樣，但名稱會附加一個整數來代表其順序。</span><span class="sxs-lookup"><span data-stu-id="f2b97-118">The new file has the same name as the previous file, but an integer is appended to the name to indicate its sequence.</span></span> <span data-ttu-id="f2b97-119">例如，若原始追蹤檔的名稱為 filename_1.trc，則下一個追蹤檔的名稱為 filename_2.trc，依此類推。</span><span class="sxs-lookup"><span data-stu-id="f2b97-119">For example, if the original trace file is named filename_1.trc, the next trace file is filename_2.trc, and so on.</span></span> <span data-ttu-id="f2b97-120">如果指派給新換用檔案的名稱已由現有的檔案使用，則會覆寫現有的檔案 (除非是唯讀)。</span><span class="sxs-lookup"><span data-stu-id="f2b97-120">If the name assigned to a new rollover file is already used by an existing file, the existing file is overwritten unless it is read only.</span></span> <span data-ttu-id="f2b97-121">將追蹤資料儲存至檔案時，會預設啟用檔案復原選項。</span><span class="sxs-lookup"><span data-stu-id="f2b97-121">The file rollover option is enabled by default when you are saving trace data to a file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2b97-122">檔案換用選項開啟時，追蹤會一直繼續，直到被其他方法停止為止。</span><span class="sxs-lookup"><span data-stu-id="f2b97-122">With the file rollover option on, the trace continues until it is stopped by some other means.</span></span> <span data-ttu-id="f2b97-123">若要在您達到檔案大小限制後停止追蹤，請停用檔案換用選項。</span><span class="sxs-lookup"><span data-stu-id="f2b97-123">To stop the trace after you have reached the file size limit, disable the file rollover option.</span></span>  
  
 <span data-ttu-id="f2b97-124">**若要設定追蹤檔的大小上限**</span><span class="sxs-lookup"><span data-stu-id="f2b97-124">**To set a maximum file size for a trace file**</span></span>  
  
 [<span data-ttu-id="f2b97-125">設定追蹤檔案的檔案大小上限 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="f2b97-125">Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
## <a name="maximum-number-of-rows"></a><span data-ttu-id="f2b97-126">最大資料列數目</span><span class="sxs-lookup"><span data-stu-id="f2b97-126">Maximum Number of Rows</span></span>  
 <span data-ttu-id="f2b97-127">已指定最大資料列數目的追蹤，在達到最大資料列數目之後，將會停止將追蹤資訊儲存到資料表。</span><span class="sxs-lookup"><span data-stu-id="f2b97-127">A trace with a maximum number of rows stops saving trace information to a table after the maximum number of rows has been reached.</span></span> <span data-ttu-id="f2b97-128">每個事件佔有一個資料列，所以此參數會在蒐集的事件數目上設定限制。</span><span class="sxs-lookup"><span data-stu-id="f2b97-128">Each event constitutes one row, so this parameter sets a limit on the number of events that are gathered.</span></span> <span data-ttu-id="f2b97-129">設定最大資料列數目可以更容易執行自動追蹤。</span><span class="sxs-lookup"><span data-stu-id="f2b97-129">Setting the maximum number of rows makes it easier to run unattended traces.</span></span> <span data-ttu-id="f2b97-130">例如，若您必須啟動追蹤，此追蹤會將追蹤資料儲存到資料表，但在資料表變得過大時必須停止追蹤，您可以自動執行這個動作。</span><span class="sxs-lookup"><span data-stu-id="f2b97-130">For example, if you need to start a trace that saves trace data to a table, but you want to stop the trace if the table becomes too large, you can do so automatically.</span></span>  
  
 <span data-ttu-id="f2b97-131">若已指定最大資料列數目且已達到最大資料列數目時， [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 執行時追蹤也會繼續執行，但不會再記錄追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="f2b97-131">When the maximum number of rows is specified and the maximum number of rows has been reached, the trace continues to run while [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is running, but the trace information is no longer recorded.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f2b97-132">會繼續顯示追蹤結果，直到追蹤停止為止。</span><span class="sxs-lookup"><span data-stu-id="f2b97-132">continues to display the trace results until the trace stops.</span></span>  
  
 <span data-ttu-id="f2b97-133">**若要設定追蹤的最大資料列數目**</span><span class="sxs-lookup"><span data-stu-id="f2b97-133">**To set a maximum number of rows for a trace**</span></span>  
  
 [<span data-ttu-id="f2b97-134">設定追蹤資料表的資料表大小上限 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="f2b97-134">Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
## <a name="see-also"></a><span data-ttu-id="f2b97-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2b97-135">See Also</span></span>  
 [<span data-ttu-id="f2b97-136">sp_trace_create &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f2b97-136">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)  
  
  
