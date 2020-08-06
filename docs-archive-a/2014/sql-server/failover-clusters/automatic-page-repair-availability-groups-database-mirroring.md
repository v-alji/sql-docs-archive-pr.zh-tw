---
title: 可用性群組和資料庫鏡像的自動修復頁面 () |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- automatic page repair
- Availability Groups [SQL Server], automatic page repair
- database mirroring [SQL Server], automatic page repair
- suspect pages [SQL Server]
ms.assetid: cf2e3650-5fac-4f34-b50e-d17765578a8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 09b5a5069d019dc452a49179e1c83d78a50e0566
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595602"
---
# <a name="automatic-page-repair-for-availability-groups-and-database-mirroring"></a><span data-ttu-id="c29dc-102">自動修復頁面 (適用於可用性群組和資料庫鏡像)</span><span class="sxs-lookup"><span data-stu-id="c29dc-102">Automatic Page Repair (For Availability Groups and Database Mirroring)</span></span>
  <span data-ttu-id="c29dc-103">資料庫鏡像與 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]都支援自動修復頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-103">Automatic page repair is supported by database mirroring and by [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="c29dc-104">在頁面因為某些錯誤類型而損毀、無法讀取之後，資料庫鏡像夥伴 (主體或鏡像) 或可用性複本 (主要或次要) 會嘗試自動復原頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-104">After certain types of errors corrupt a page, making it unreadable, a database mirroring partner (principal or mirror) or an availability replica (primary or secondary) attempts to automatically recover the page.</span></span> <span data-ttu-id="c29dc-105">無法讀取頁面的夥伴/複本會向其夥伴或另一個複本要求一個全新頁面副本。</span><span class="sxs-lookup"><span data-stu-id="c29dc-105">The partner/replica that cannot read the page requests a fresh copy of the page from its partner or from another replica.</span></span> <span data-ttu-id="c29dc-106">如果這個要求成功，無法讀取的頁面就會被可讀取的副本取代，而這通常會解決錯誤。</span><span class="sxs-lookup"><span data-stu-id="c29dc-106">If this request succeeds, the unreadable page is replaced by the readable copy, and this usually resolves the error.</span></span>  
  
 <span data-ttu-id="c29dc-107">一般來說，資料庫鏡像和 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 會以相等方式處理 I/O 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c29dc-107">Generally speaking, database mirroring and [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] handle I/O errors in equivalent ways.</span></span> <span data-ttu-id="c29dc-108">幾個差異會在這裡明確標註。</span><span class="sxs-lookup"><span data-stu-id="c29dc-108">The few differences are explicitly called out here.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c29dc-109">自動修復頁面不同於 DBCC 修復。</span><span class="sxs-lookup"><span data-stu-id="c29dc-109">Automatic page repair differs from DBCC repair.</span></span> <span data-ttu-id="c29dc-110">自動修復頁面會保留所有資料。</span><span class="sxs-lookup"><span data-stu-id="c29dc-110">All of the data is preserved by an automatic page repair.</span></span> <span data-ttu-id="c29dc-111">相反地，利用 DBCC REPAIR_ALLOW_DATA_LOSS 選項來更正錯誤，可能需要刪除某些頁面，因而也需要刪除某些資料。</span><span class="sxs-lookup"><span data-stu-id="c29dc-111">In contrast, correcting errors by using the DBCC REPAIR_ALLOW_DATA_LOSS option might require that some pages, and therefore data, be deleted.</span></span>  
  
  
  
##  <a name="error-types-that-cause-an-automatic-page-repair-attempt"></a><a name="ErrorTypes"></a><span data-ttu-id="c29dc-112">導致嘗試自動修復頁面的錯誤類型</span><span class="sxs-lookup"><span data-stu-id="c29dc-112">Error Types That Cause an Automatic Page-Repair Attempt</span></span>  
 <span data-ttu-id="c29dc-113">資料庫鏡像的自動修復頁面僅會嘗試修復在操作資料檔案時，因為下表列出的其中一個錯誤而失敗的頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-113">Database mirroring automatic page repair tries to repair only pages in a data file on which an operation has failed for one of the errors listed in the following table.</span></span>  
  
|<span data-ttu-id="c29dc-114">錯誤號碼</span><span class="sxs-lookup"><span data-stu-id="c29dc-114">Error number</span></span>|<span data-ttu-id="c29dc-115">描述</span><span class="sxs-lookup"><span data-stu-id="c29dc-115">Description</span></span>|<span data-ttu-id="c29dc-116">造成嘗試自動修復頁面的執行個體</span><span class="sxs-lookup"><span data-stu-id="c29dc-116">Instances that cause automatic page-repair attempt</span></span>|  
|------------------|-----------------|---------------------------------------------------------|  
|[<span data-ttu-id="c29dc-117">823</span><span class="sxs-lookup"><span data-stu-id="c29dc-117">823</span></span>](../../relational-databases/errors-events/mssqlserver-823-database-engine-error.md)|<span data-ttu-id="c29dc-118">只有當作業系統在資料上執行循環冗餘檢查 (CRC) 失敗時，才會採取動作。</span><span class="sxs-lookup"><span data-stu-id="c29dc-118">Action is taken only if the operating system performed a cyclic redundancy check (CRC) that failed on the data.</span></span>|<span data-ttu-id="c29dc-119">ERROR_CRC。</span><span class="sxs-lookup"><span data-stu-id="c29dc-119">ERROR_CRC.</span></span> <span data-ttu-id="c29dc-120">這項錯誤的作業系統值為 23。</span><span class="sxs-lookup"><span data-stu-id="c29dc-120">The operating-system value for this error is 23.</span></span>|  
|[<span data-ttu-id="c29dc-121">824</span><span class="sxs-lookup"><span data-stu-id="c29dc-121">824</span></span>](../../relational-databases/errors-events/mssqlserver-824-database-engine-error.md)|<span data-ttu-id="c29dc-122">邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="c29dc-122">Logical errors.</span></span>|<span data-ttu-id="c29dc-123">邏輯資料錯誤，例如，分次寫入或頁面總和檢查碼錯誤。</span><span class="sxs-lookup"><span data-stu-id="c29dc-123">Logical data errors, such as torn write or bad page checksum.</span></span>|  
|<span data-ttu-id="c29dc-124">829</span><span class="sxs-lookup"><span data-stu-id="c29dc-124">829</span></span>|<span data-ttu-id="c29dc-125">頁面已標示為還原暫止。</span><span class="sxs-lookup"><span data-stu-id="c29dc-125">A page has been marked as restore pending.</span></span>|<span data-ttu-id="c29dc-126">All：</span><span class="sxs-lookup"><span data-stu-id="c29dc-126">All.</span></span>|  
  
 <span data-ttu-id="c29dc-127">若要檢視最近的 823 CRC 錯誤和 824 錯誤，請參閱 [msdb](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 資料庫中的 [suspect_pages](../../relational-databases/databases/msdb-database.md) 資料表。</span><span class="sxs-lookup"><span data-stu-id="c29dc-127">To view recent 823 CRC errors and 824 errors, see the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table in the [msdb](../../relational-databases/databases/msdb-database.md) database.</span></span>  
  
  
  
##  <a name="page-types-that-cannot-be-automatically-repaired"></a><a name="UnrepairablePageTypes"></a><span data-ttu-id="c29dc-128">無法自動修復的頁面類型</span><span class="sxs-lookup"><span data-stu-id="c29dc-128">Page Types That Cannot Be Automatically Repaired</span></span>  
 <span data-ttu-id="c29dc-129">自動修復頁面無法修復下列控制頁類型：</span><span class="sxs-lookup"><span data-stu-id="c29dc-129">Automatic page repair cannot repair the following control page types:</span></span>  
  
-   <span data-ttu-id="c29dc-130">檔案標頭頁面 (頁面識別碼 0)。</span><span class="sxs-lookup"><span data-stu-id="c29dc-130">File header page (page ID 0).</span></span>  
  
-   <span data-ttu-id="c29dc-131">第 9 頁 (資料庫啟動頁面)。</span><span class="sxs-lookup"><span data-stu-id="c29dc-131">Page 9 (the database boot page).</span></span>  
  
-   <span data-ttu-id="c29dc-132">配置頁面：全域配置對應 (Global Allocation Map，GAM) 頁面、共用全域配置對應 (Shared Global Allocation Map，SGAM) 頁面，以及頁面可用空間 (Page Free Space，PFS) 頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-132">Allocation pages: Global Allocation Map (GAM) pages, Shared Global Allocation Map (SGAM) pages, and Page Free Space (PFS) pages.</span></span>  
  

  
##  <a name="handling-io-errors-on-the-principalprimary-database"></a><a name="PrimaryIOErrors"></a><span data-ttu-id="c29dc-133">處理主體/主資料庫上的 i/o 錯誤</span><span class="sxs-lookup"><span data-stu-id="c29dc-133">Handling I/O Errors on the Principal/Primary Database</span></span>  
 <span data-ttu-id="c29dc-134">在主體/主要資料庫上，只有當資料庫處於 SYNCHRONIZED 狀態，而且主體/主要資料庫仍在將資料庫的記錄檔記錄傳送到鏡像/次要資料庫時，才會嘗試自動修復頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-134">On the principal/primary database, automatic page repair is tried only when the database is in the SYNCHRONIZED state and the principal/primary is still sending log records for the database to the mirror/secondary.</span></span> <span data-ttu-id="c29dc-135">自動修復頁面的基本動作順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="c29dc-135">The basic sequence of actions in an automatic page-repair attempt are as follows:</span></span>  
  
1.  <span data-ttu-id="c29dc-136">在主體/主要資料庫的資料頁面上發生讀取錯誤時，主體/主要資料庫會在 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 資料表中插入一個資料列，列出適當的錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="c29dc-136">When a read error occurs on a data page in the principal/primary database, the principal/primary inserts a row in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table with the appropriate error status.</span></span> <span data-ttu-id="c29dc-137">如果是資料庫鏡像，主體資料庫接著就會向鏡像資料庫要求頁面的副本。</span><span class="sxs-lookup"><span data-stu-id="c29dc-137">For database mirroring, the principal then requests a copy of the page from the mirror.</span></span> <span data-ttu-id="c29dc-138">如果是 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，主要資料庫會向所有次要資料庫廣播要求，並從第一個回應的次要資料庫取得頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-138">For [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], the primary broadcasts the request to all the secondaries and gets the page from the first to respond.</span></span> <span data-ttu-id="c29dc-139">此要求會指定目前在已排清記錄檔結尾的頁面識別碼和 LSN。</span><span class="sxs-lookup"><span data-stu-id="c29dc-139">The request specifies the page ID and the LSN that is currently at the end of the flushed log.</span></span> <span data-ttu-id="c29dc-140">該頁面會標示為 *還原暫止*。</span><span class="sxs-lookup"><span data-stu-id="c29dc-140">The page is marked as *restore pending*.</span></span> <span data-ttu-id="c29dc-141">這樣就無法在嘗試進行自動修復頁面期間存取該頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-141">This makes it inaccessible during the automatic page-repair attempt.</span></span> <span data-ttu-id="c29dc-142">在嘗試修復期間存取此頁面的嘗試將會失敗，其錯誤為 829 (還原暫止)。</span><span class="sxs-lookup"><span data-stu-id="c29dc-142">Attempts to access this page during the repair attempt will fail with error 829 (restore pending).</span></span>  
  
2.  <span data-ttu-id="c29dc-143">收到頁面要求後，鏡像/次要資料庫會等到已經將記錄重做到要求中指定的 LSN 為止。</span><span class="sxs-lookup"><span data-stu-id="c29dc-143">After receiving the page request, the mirror/secondary waits until it has redone the log up to the LSN specified in the request.</span></span> <span data-ttu-id="c29dc-144">然後，鏡像/次要資料庫就會嘗試存取其資料庫副本中的頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-144">Then, the mirror/secondary tries to access the page in its copy of the database.</span></span> <span data-ttu-id="c29dc-145">如果可以存取頁面，鏡像/次要資料庫就會將該頁面的副本傳送到主體/主要資料庫。</span><span class="sxs-lookup"><span data-stu-id="c29dc-145">If the page can be accessed, the mirror/secondary sends the copy of the page to the principal/primary.</span></span> <span data-ttu-id="c29dc-146">否則，鏡像/次要資料庫會將錯誤傳回主體/主要資料庫，而且自動修復頁面嘗試會失敗。</span><span class="sxs-lookup"><span data-stu-id="c29dc-146">Otherwise, the mirror/secondary returns an error to the principal/primary, and the automatic page-repair attempt fails.</span></span>  
  
3.  <span data-ttu-id="c29dc-147">主體/主要資料庫會處理包含全新頁面副本的回應。</span><span class="sxs-lookup"><span data-stu-id="c29dc-147">The principal/primary processes the response that contains the fresh copy of the page.</span></span>  
  
4.  <span data-ttu-id="c29dc-148">自動修復頁面修復可疑頁面之後，該頁面在 **suspect_pages** 資料表中會標示為已還原 (**event_type** = 5)。</span><span class="sxs-lookup"><span data-stu-id="c29dc-148">After the automatic page-repair attempt fixes a suspect page, the page is marked in the **suspect_pages** table as restored (**event_type** = 5).</span></span>  
  
5.  <span data-ttu-id="c29dc-149">如果頁面 I/O 錯誤造成任何 [延遲的交易](../../relational-databases/backup-restore/deferred-transactions-sql-server.md)，修復該頁面後，主體/主要資料庫會嘗試解決那些交易。</span><span class="sxs-lookup"><span data-stu-id="c29dc-149">If the page I/O error caused any [deferred transactions](../../relational-databases/backup-restore/deferred-transactions-sql-server.md), after you repair the page, the principal/primary tries to resolve those transactions.</span></span>  
  

  
##  <a name="handling-io-errors-on-the-mirrorsecondary-database"></a><a name="SecondaryIOErrors"></a><span data-ttu-id="c29dc-150">處理鏡像/次要資料庫上的 i/o 錯誤</span><span class="sxs-lookup"><span data-stu-id="c29dc-150">Handling I/O Errors on the Mirror/Secondary Database</span></span>  
 <span data-ttu-id="c29dc-151">資料庫鏡像與 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]通常會以相同方式處理鏡像/次要資料庫上發生的資料頁面 I/O 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c29dc-151">I/O errors on data pages that occur on the mirror/secondary database are handled in generally the same way by database mirroring and by [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
1.  <span data-ttu-id="c29dc-152">對於資料庫鏡像，如果鏡像資料庫在重做記錄檔記錄時遇到一個或多個頁面 I/O 錯誤，鏡像工作階段會進入 SUSPENDED 狀態。</span><span class="sxs-lookup"><span data-stu-id="c29dc-152">With database mirroring, if the mirror encounters one or more page I/O errors when it redoes a log record, the mirroring session enters the SUSPENDED state.</span></span> <span data-ttu-id="c29dc-153">對於 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，如果次要複本在重做記錄檔記錄時遇到一個或多個頁面 I/O 錯誤，次要資料庫會進入 SUSPENDED 狀態。</span><span class="sxs-lookup"><span data-stu-id="c29dc-153">With [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], if a secondary replica encounters one or more page I/O errors when it redoes a log record, the secondary database enters the SUSPENDED state.</span></span> <span data-ttu-id="c29dc-154">此時，鏡像/次要資料庫會在 **suspect_pages** 資料表中插入一個資料列，列出適當的錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="c29dc-154">At that point, the mirror/secondary inserts a row in the **suspect_pages** table with the appropriate error status.</span></span> <span data-ttu-id="c29dc-155">鏡像/次要資料庫接著就會向主體/主要資料庫要求頁面的副本。</span><span class="sxs-lookup"><span data-stu-id="c29dc-155">The mirror/secondary then requests a copy of the page from the principal/primary.</span></span>  
  
2.  <span data-ttu-id="c29dc-156">主體/主要資料庫會嘗試存取其資料庫副本中的頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-156">The principal/primary tries to access the page in its copy of the database.</span></span> <span data-ttu-id="c29dc-157">如果可以存取頁面，主體/主要資料庫就會將該頁面的副本傳送到鏡像/次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="c29dc-157">If the page can be accessed, the principal/primary sends the copy of page to the mirror/secondary.</span></span>  
  
3.  <span data-ttu-id="c29dc-158">如果鏡像/次要資料庫收到所要求之每個頁面的副本，鏡像/次要資料庫會嘗試繼續鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="c29dc-158">If the mirror/secondary receives copies of every page it has requested, the mirror/secondary tries to resume the mirroring session.</span></span> <span data-ttu-id="c29dc-159">如果自動修復頁面修復可疑頁面，該頁面在 **suspect_pages** 資料表中會標示為已還原 (**event_type** = 4)。</span><span class="sxs-lookup"><span data-stu-id="c29dc-159">If an automatic page-repair attempt fixes a suspect page, the page is marked in the **suspect_pages** table as restored (**event_type** = 4).</span></span>  
  
     <span data-ttu-id="c29dc-160">如果鏡像/次要資料庫沒有收到向主體/主要資料庫要求的頁面，自動修復頁面嘗試會失敗。</span><span class="sxs-lookup"><span data-stu-id="c29dc-160">If a mirror/secondary does not receive a page that it requested from the principal/primary, the automatic page-repair attempt fails.</span></span> <span data-ttu-id="c29dc-161">對於資料庫鏡像，鏡像工作階段保持暫停。</span><span class="sxs-lookup"><span data-stu-id="c29dc-161">With database mirroring, the mirroring session remains suspended.</span></span> <span data-ttu-id="c29dc-162">對於 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，次要資料庫也會保持暫停。</span><span class="sxs-lookup"><span data-stu-id="c29dc-162">With [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], the secondary database remains suspended.</span></span> <span data-ttu-id="c29dc-163">如果手動繼續鏡像工作階段或次要資料庫，在同步處理階段期間，將會再次叫用損毀的頁面。</span><span class="sxs-lookup"><span data-stu-id="c29dc-163">If the mirroring session or secondary database is resumed manually, the corrupted pages will be hit again during the synchronization phase.</span></span>  

  
##  <a name="developer-best-practice"></a><a name="DevBP"></a><span data-ttu-id="c29dc-164">開發人員最佳做法</span><span class="sxs-lookup"><span data-stu-id="c29dc-164">Developer Best Practice</span></span>  
 <span data-ttu-id="c29dc-165">自動修復頁面是在背景中執行的非同步程序。</span><span class="sxs-lookup"><span data-stu-id="c29dc-165">An automatic page repair is an asynchronous process that runs in the background.</span></span> <span data-ttu-id="c29dc-166">因此，要求無法讀取之頁面的資料庫作業也會失敗，而且會針對造成失敗的情況，傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c29dc-166">Therefore, a database operation that requests an unreadable page fails and returns the error code for whatever condition caused the failure.</span></span> <span data-ttu-id="c29dc-167">開發鏡像資料庫或可用性資料庫的應用程式時，您應該攔截失敗作業的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c29dc-167">When developing an application for a mirrored database or an availability database, you should intercept exceptions for failed operations.</span></span> <span data-ttu-id="c29dc-168">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤碼為 823、824 或 829，您應該稍後重試該作業。</span><span class="sxs-lookup"><span data-stu-id="c29dc-168">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error code is 823, 824, or 829, you should retry the operation later.</span></span>  
  

  
##  <a name="how-to-view-automatic-page-repair-attempts"></a><a name="ViewAPRattempts"></a><span data-ttu-id="c29dc-169">如何：查看自動修復頁面嘗試</span><span class="sxs-lookup"><span data-stu-id="c29dc-169">How To: View Automatic Page-Repair Attempts</span></span>  
 <span data-ttu-id="c29dc-170">下列動態管理檢視會針對給定可用性資料庫或鏡像資料庫上進行的最新自動修復頁面嘗試行為傳回資料列，每個資料庫最多 100 個資料列。</span><span class="sxs-lookup"><span data-stu-id="c29dc-170">The following dynamic management views return rows for the latest automatic page-repair attempts on a given availability database or mirrored database, with a maximum of 100 rows per database.</span></span>  
  
-   <span data-ttu-id="c29dc-171">**AlwaysOn 可用性群組：**</span><span class="sxs-lookup"><span data-stu-id="c29dc-171">**AlwaysOn Availability Groups:**</span></span>  
  
     [<span data-ttu-id="c29dc-172">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c29dc-172">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
  
     <span data-ttu-id="c29dc-173">針對可用性複本上的任何可用性資料庫進行的每個自動修復頁面嘗試行為，各傳回一個資料列，該可用性複本是針對伺服器執行個體的任何可用性群組所裝載。</span><span class="sxs-lookup"><span data-stu-id="c29dc-173">Returns a row for every automatic page-repair attempt on any availability database on an availability replica that is hosted for any availability group by the server instance.</span></span>  
  
-   <span data-ttu-id="c29dc-174">**資料庫鏡像：**</span><span class="sxs-lookup"><span data-stu-id="c29dc-174">**Database mirroring:**</span></span>  
  
     [<span data-ttu-id="c29dc-175">sys.dm_db_mirroring_auto_page_repair &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c29dc-175">sys.dm_db_mirroring_auto_page_repair &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-auto-page-repair)  
  
     <span data-ttu-id="c29dc-176">針對在伺服器執行個體之任何鏡像資料庫上進行的每個自動修復頁面嘗試行為，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="c29dc-176">Returns a row for every automatic page-repair attempt on any mirrored database on the server instance.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="c29dc-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c29dc-177">See Also</span></span>  
 <span data-ttu-id="c29dc-178">[管理 suspect_pages 資料表 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c29dc-178">[Manage the suspect_pages Table &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md) </span></span>  
 <span data-ttu-id="c29dc-179">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c29dc-179">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="c29dc-180">資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c29dc-180">Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
