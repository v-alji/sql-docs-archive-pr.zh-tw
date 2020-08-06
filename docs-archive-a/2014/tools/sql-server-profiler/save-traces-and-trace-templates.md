---
title: 儲存追蹤和追蹤範本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- exporting trace templates
- importing trace templates
- SQL Server Profiler, templates
ms.assetid: 957e6bf8-e7a3-4a59-a1cd-0a41538a8158
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36db7ccfd8b185d60eb39c20a58842f469e7878d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704550"
---
# <a name="save-traces-and-trace-templates"></a><span data-ttu-id="25a27-102">儲存追蹤及追蹤範本</span><span class="sxs-lookup"><span data-stu-id="25a27-102">Save Traces and Trace Templates</span></span>
  <span data-ttu-id="25a27-103">區分儲存追蹤檔案與儲存追蹤範本是很重要的。</span><span class="sxs-lookup"><span data-stu-id="25a27-103">It is important to distinguish saving trace files from saving trace templates.</span></span> <span data-ttu-id="25a27-104">儲存追蹤檔案牽涉到將擷取的事件資料儲存到指定的位置上。</span><span class="sxs-lookup"><span data-stu-id="25a27-104">Saving a trace file involves saving the captured event data to a specified place.</span></span> <span data-ttu-id="25a27-105">儲存追蹤範本則牽涉到儲存追蹤的定義，例如指定的資料行、事件類別或篩選等。</span><span class="sxs-lookup"><span data-stu-id="25a27-105">Saving a trace template involves saving the definition of the trace, such as specified data columns, event classes, or filters.</span></span>  
  
## <a name="saving-traces"></a><span data-ttu-id="25a27-106">儲存追蹤</span><span class="sxs-lookup"><span data-stu-id="25a27-106">Saving Traces</span></span>  
 <span data-ttu-id="25a27-107">若您必須於稍後分析或重新執行擷取的資料，請將擷取的事件資料儲存到檔案或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中。</span><span class="sxs-lookup"><span data-stu-id="25a27-107">Save captured event data to a file or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table when you need to analyze or replay the captured data at a later time.</span></span> <span data-ttu-id="25a27-108">使用追蹤檔案可執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="25a27-108">Use a trace file to do the following:</span></span>  
  
-   <span data-ttu-id="25a27-109">使用追蹤檔案或追蹤資料表來建立工作負載，以作為 Database Engine Tuning Advisor 的輸入項目。</span><span class="sxs-lookup"><span data-stu-id="25a27-109">Use a trace file or trace table to create a workload that is used as input for Database Engine Tuning Advisor.</span></span>  
  
-   <span data-ttu-id="25a27-110">使用追蹤檔可以擷取事件，並將追蹤檔傳給支援提供者以進行分析。</span><span class="sxs-lookup"><span data-stu-id="25a27-110">Use a trace file to capture events and send the trace file to the support provider for analysis.</span></span>  
  
-   <span data-ttu-id="25a27-111">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的查詢處理工具以存取資料，或檢視 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中的資料。</span><span class="sxs-lookup"><span data-stu-id="25a27-111">Use the query processing tools in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to access the data or to view the data in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="25a27-112">只有 **系統管理員** 固定伺服器角色的成員或資料表建立者，才能直接存取追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="25a27-112">Only members of the **sysadmin** fixed server role or the table creator can access the trace table directly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25a27-113">將追蹤資料擷取到資料表，比擷取到檔案還慢。</span><span class="sxs-lookup"><span data-stu-id="25a27-113">Capturing trace data to a table is a slower operation than capturing trace data to a file.</span></span> <span data-ttu-id="25a27-114">替代方式是將追蹤資料擷取到檔案中，開啟追蹤檔案，然後再將追蹤另存成追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="25a27-114">An alternative is to capture trace data to a file, open the trace file, and then save the trace as a trace table.</span></span>  
  
 <span data-ttu-id="25a27-115">使用追蹤檔案時， [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 會將擷取的事件資料 (不是追蹤定義) 儲存到 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace (\*.trc) 檔案中。</span><span class="sxs-lookup"><span data-stu-id="25a27-115">When you use a trace file, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] saves captured event data (not trace definitions) to a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace (\*.trc) file.</span></span> <span data-ttu-id="25a27-116">儲存追蹤檔案時副檔名會自動加到檔案結尾，而不論其他指定的副檔名為何。</span><span class="sxs-lookup"><span data-stu-id="25a27-116">The extension is added to the end of the file automatically when the trace file is saved, regardless of any other specified extension.</span></span> <span data-ttu-id="25a27-117">例如，若您指定名為 **Trace.dat**的追蹤檔案時，建立的檔案便稱為 **Trace.dat.trc**。</span><span class="sxs-lookup"><span data-stu-id="25a27-117">For example, if you specify a trace file called **Trace.dat**, the file created is called **Trace.dat.trc**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="25a27-118">具有 SHOWPLAN、ALTER TRACE 或 VIEW SERVER STATE 權限的使用者可以檢視執行程序表輸出中所擷取的查詢。</span><span class="sxs-lookup"><span data-stu-id="25a27-118">Users who have the SHOWPLAN, the ALTER TRACE, or the VIEW SERVER STATE permission can view queries that are captured in Showplan output.</span></span> <span data-ttu-id="25a27-119">這些查詢可能會包含類似密碼的敏感資訊。</span><span class="sxs-lookup"><span data-stu-id="25a27-119">These queries may contain sensitive information such as passwords.</span></span> <span data-ttu-id="25a27-120">因此，我們建議您只能將這些權限授與給有權檢視敏感資訊的使用者，例如 **db_owner** 固定資料庫角色的成員或是 **系統管理員** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="25a27-120">Therefore, we recommend that you only grant these permissions to users who are authorized to view sensitive information, such as members of the **db_owner** fixed database role, or members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="25a27-121">此外，我們也建議您只將執行程序表檔案或是包含與執行程序表相關之事件的追蹤檔案儲存到使用 NTFS 檔案系統的位置，並建議您將存取權限制為有權檢視敏感資訊的使用者。</span><span class="sxs-lookup"><span data-stu-id="25a27-121">Additionally, we recommend that you only save Showplan files or trace files that contain Showplan-related events to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view sensitive information.</span></span>  
  
## <a name="saving-templates"></a><span data-ttu-id="25a27-122">儲存範本</span><span class="sxs-lookup"><span data-stu-id="25a27-122">Saving Templates</span></span>  
 <span data-ttu-id="25a27-123">追蹤的範本定義包含事件類別、資料行、篩選和用於建立追蹤的所有其他屬性 (擷取的事件資料除外)。</span><span class="sxs-lookup"><span data-stu-id="25a27-123">The template definition of a trace includes the event classes, data columns, filters, and all other properties (except the captured event data) that are used to create a trace.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="25a27-124">針對一般追蹤工作和特定工作，例如建立可供 Database Engine Tuning Advisor 用來微調實體資料庫設計的工作負載，提供了預先定義的系統範本。</span><span class="sxs-lookup"><span data-stu-id="25a27-124">provides predefined system templates for common tracing tasks and for specific tasks, such as creating a workload that Database Engine Tuning Advisor can use to tune the physical database design.</span></span> <span data-ttu-id="25a27-125">您也可以建立與儲存使用者自訂的範本。</span><span class="sxs-lookup"><span data-stu-id="25a27-125">You can also create and save user-defined templates.</span></span>  
  
### <a name="importing-and-exporting-templates"></a><span data-ttu-id="25a27-126">匯入和匯出範本</span><span class="sxs-lookup"><span data-stu-id="25a27-126">Importing and Exporting Templates</span></span>  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="25a27-127">可讓您在不同的伺服器之間匯入和匯出範本。</span><span class="sxs-lookup"><span data-stu-id="25a27-127">allows you to import and export templates from one server to another.</span></span> <span data-ttu-id="25a27-128">匯出範本時，會將現有範本的副本移至您所指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="25a27-128">Exporting a template moves a copy of an existing template to a directory that you specify.</span></span> <span data-ttu-id="25a27-129">匯入範本時，則會複製您所指定的範本。</span><span class="sxs-lookup"><span data-stu-id="25a27-129">Importing a template makes a copy of a template that you specify.</span></span> <span data-ttu-id="25a27-130">在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中檢視這些範本時，您可以藉由範本名稱後的 "(user)" 這個詞彙來與系統範本作區別。</span><span class="sxs-lookup"><span data-stu-id="25a27-130">When these templates are viewed in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can distinguish them from system templates by the term "(user)" that follows the template name.</span></span> <span data-ttu-id="25a27-131">您無法覆寫或直接修改預先定義的系統範本。</span><span class="sxs-lookup"><span data-stu-id="25a27-131">You cannot overwrite or directly modify a predefined system template.</span></span>  
  
### <a name="analyzing-performance-with-templates"></a><span data-ttu-id="25a27-132">以範本分析效能</span><span class="sxs-lookup"><span data-stu-id="25a27-132">Analyzing Performance with Templates</span></span>  
 <span data-ttu-id="25a27-133">若您經常監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請使用範本來分析效能。</span><span class="sxs-lookup"><span data-stu-id="25a27-133">If you frequently monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use templates to analyze performance.</span></span> <span data-ttu-id="25a27-134">範本每次都會擷取相同的事件資料，並使用相同的追蹤定義來監視相同的事件。</span><span class="sxs-lookup"><span data-stu-id="25a27-134">The templates capture the same event data each time and use the same trace definition to monitor the same events.</span></span> <span data-ttu-id="25a27-135">您不需在每次建立追蹤時都定義事件類別與資料行。</span><span class="sxs-lookup"><span data-stu-id="25a27-135">You do not need to define the event classes and data columns every time you create a trace.</span></span> <span data-ttu-id="25a27-136">此外，範本可以提供給另一位使用者，用來監視特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="25a27-136">Also, a template can be given to another user to monitor specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="25a27-137">例如，支援提供者可以為使用者提供範本。</span><span class="sxs-lookup"><span data-stu-id="25a27-137">For example, a support provider can supply a customer with a template.</span></span> <span data-ttu-id="25a27-138">客戶可使用範本來擷取所需的事件資料，再將事件資料傳送給支援提供者以進行分析。</span><span class="sxs-lookup"><span data-stu-id="25a27-138">The customer uses the template to capture the required event data, which is then sent to the support provider for analysis.</span></span>  
  
 <span data-ttu-id="25a27-139">**若要將追蹤儲存至檔案**</span><span class="sxs-lookup"><span data-stu-id="25a27-139">**To save a trace to a file**</span></span>  
  
 [<span data-ttu-id="25a27-140">將追蹤結果儲存至檔案 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="25a27-140">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](save-trace-results-to-a-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="25a27-141">sp_trace_create &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="25a27-141">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="25a27-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25a27-142">See Also</span></span>  
 <span data-ttu-id="25a27-143">[將追蹤結果儲存到資料表 &#40;SQL Server Profiler&#41;](save-trace-results-to-a-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="25a27-143">[Save Trace Results to a Table &#40;SQL Server Profiler&#41;](save-trace-results-to-a-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="25a27-144">[建立追蹤範本 &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="25a27-144">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="25a27-145">[從執行中的追蹤衍生範本 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="25a27-145">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="25a27-146">[從追蹤檔案或追蹤資料表衍生範本 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="25a27-146">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="25a27-147">[匯出追蹤範本 &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="25a27-147">[Export a Trace Template &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="25a27-148">匯入追蹤範本 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="25a27-148">Import a Trace Template &#40;SQL Server Profiler&#41;</span></span>](import-a-trace-template-sql-server-profiler.md)  
  
  
