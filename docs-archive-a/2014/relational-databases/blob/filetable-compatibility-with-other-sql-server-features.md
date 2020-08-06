---
title: FileTable 與其他 SQL Server 功能的相容性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], using with other features
ms.assetid: f12a17e4-bd3d-42b0-b253-efc36876db37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a6ac6668ff362a986646c4e01b1f0e5e722611c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707629"
---
# <a name="filetable-compatibility-with-other-sql-server-features"></a><span data-ttu-id="784c2-102">FileTable 與其他 SQL Server 功能的相容性</span><span class="sxs-lookup"><span data-stu-id="784c2-102">FileTable Compatibility with Other SQL Server Features</span></span>
  <span data-ttu-id="784c2-103">描述 FileTable 如何搭配其他的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]功能一起運作。</span><span class="sxs-lookup"><span data-stu-id="784c2-103">Describes how FileTables work with other features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="alwayson-availability-groups-and-filetables"></a><a name="alwayson"></a> <span data-ttu-id="784c2-104">AlwaysOn 可用性群組和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-104">AlwaysOn Availability Groups and FileTables</span></span>  
 <span data-ttu-id="784c2-105">當包含 FILESTREAM 或 FileTable 資料的資料庫屬於 AlwaysOn 可用性群組時：</span><span class="sxs-lookup"><span data-stu-id="784c2-105">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="784c2-106">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]僅部分支援 FileTable 功能。</span><span class="sxs-lookup"><span data-stu-id="784c2-106">FileTable functionality is partially supported by [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="784c2-107">在容錯移轉之後，主要複本上的 FileTable 資料可供存取，但卻無法存取位在可讀取之次要複本上的 FileTable 資料。</span><span class="sxs-lookup"><span data-stu-id="784c2-107">After a failover, FileTable data is accessible on the primary replica, but FileTable data is not accessible on readable secondary replicas.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="784c2-108">請注意，容錯移轉後將支援所有 FILESTREAM 功能。</span><span class="sxs-lookup"><span data-stu-id="784c2-108">Notice that after a failover all FILESTREAM functionality is supported.</span></span> <span data-ttu-id="784c2-109">可讀取的次要複本以及新的主要複本上的 FILESTREAM 資料皆可供存取。</span><span class="sxs-lookup"><span data-stu-id="784c2-109">FILESTREAM data is accessible on both readable secondary replicas and on the new primary.</span></span>  
  
-   <span data-ttu-id="784c2-110">FILESTREAM 和 FileTable 函數會接受或傳回虛擬網路名稱 (VNN) 而非電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="784c2-110">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="784c2-111">如需有關這些函數的詳細資訊，請參閱 [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql) (Filestream 和 FileTable 函數 (Transact-SQL))。</span><span class="sxs-lookup"><span data-stu-id="784c2-111">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="784c2-112">透過檔案系統 API 對 FILESTREAM 或 FileTable 資料進行的所有存取都應該使用 VNN 而非電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="784c2-112">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span> <span data-ttu-id="784c2-113">如需詳細資訊，請參閱 [FILESTREAM 和 FileTable 與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="784c2-113">For more information, see [FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="partitioning-and-filetables"></a><a name="OtherPartitioning"></a> <span data-ttu-id="784c2-114">資料分割和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-114">Partitioning and FileTables</span></span>  
 <span data-ttu-id="784c2-115">FileTable 不支援資料分割。</span><span class="sxs-lookup"><span data-stu-id="784c2-115">Partitioning is not supported on FileTables.</span></span> <span data-ttu-id="784c2-116">有了多重 FILESTREAM 檔案群組的支援，在大多數情況下可以處理單純的向上擴充問題，而不必訴諸於資料分割 (不同於 SQL 2008 FILESTREAM)。</span><span class="sxs-lookup"><span data-stu-id="784c2-116">With the support for multiple FILESTREAM file groups, pure scale-up issues can be handled without having to resort to partitioning  in most scenarios (unlike SQL 2008 FILESTREAMs).</span></span>  
  
##  <a name="replication-and-filetables"></a><a name="OtherRepl"></a> <span data-ttu-id="784c2-117">複寫和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-117">Replication and FileTables</span></span>  
 <span data-ttu-id="784c2-118">FileTable 不支援複寫和相關功能 (包括異動複寫、合併式複寫、異動資料擷取和變更追蹤)。</span><span class="sxs-lookup"><span data-stu-id="784c2-118">Replication and related features (including transactional replication, merge replication, change data capture, and change tracking) are not supported with FileTables.</span></span>  
  
##  <a name="transaction-semantics-and-filetables"></a><a name="OtherIsolation"></a> <span data-ttu-id="784c2-119">交易語意和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-119">Transaction Semantics and FileTables</span></span>  
 <span data-ttu-id="784c2-120">**Windows 應用程式**</span><span class="sxs-lookup"><span data-stu-id="784c2-120">**Windows applications**</span></span>  
 <span data-ttu-id="784c2-121">Windows 應用程式不了解資料庫交易，所以 Windows 寫入作業不會提供資料庫交易的 ACID 屬性。</span><span class="sxs-lookup"><span data-stu-id="784c2-121">Windows applications do not understand database transactions, so Windows write operations do not provide the ACID properties of a database transaction.</span></span> <span data-ttu-id="784c2-122">因此，交易式回復和復原無法利用 Windows 更新作業來進行。</span><span class="sxs-lookup"><span data-stu-id="784c2-122">Therefore transactional rollbacks and recovery are not possible with Windows update operations.</span></span>  
  
 <span data-ttu-id="784c2-123">**Transact-SQL 應用程式**</span><span class="sxs-lookup"><span data-stu-id="784c2-123">**Transact-SQL applications**</span></span>  
 <span data-ttu-id="784c2-124">對於在 FileTable 的 FILESTREAM (file_stream) 資料行中工作的 TSQL 應用程式而言，隔離語意與一般使用者資料表內的 FILESTREAM 資料類型相同。</span><span class="sxs-lookup"><span data-stu-id="784c2-124">For TSQL applications working on the FILESTREAM (file_stream) column in a FileTable, the isolation semantics are the same as with FILESTREAM datatype in a regular user table.</span></span>  
  
##  <a name="query-notifications-and-filetables"></a><a name="OtherQueryNot"></a> <span data-ttu-id="784c2-125">查詢通知和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-125">Query Notifications and FileTables</span></span>  
 <span data-ttu-id="784c2-126">此查詢不得在 WHERE 子句或是查詢的任何其他部分中，包含 FileTable 中 FILESTREAM 資料行的參考。</span><span class="sxs-lookup"><span data-stu-id="784c2-126">The query cannot contain reference to the FILESTREAM column in the FileTable, in the WHERE clause or any other part of the query.</span></span>  
  
##  <a name="select-into-and-filetables"></a><a name="OtherSelectInto"></a> <span data-ttu-id="784c2-127">SELECT INTO 和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-127">SELECT INTO and FileTables</span></span>  
 <span data-ttu-id="784c2-128">FileTable 中的 SELECT INTO 陳述式將不會傳播目的地資料表上所建立的 FileTable 語意 (就像一般資料表中的 FILESTREAM 資料行一樣)。</span><span class="sxs-lookup"><span data-stu-id="784c2-128">SELECT INTO statements from a FileTable will not propagate the FileTable semantics on the created destination table (just like FILESTREAM columns in a regular table).</span></span> <span data-ttu-id="784c2-129">所有目的地資料表資料行的行為就像一般資料行一樣。</span><span class="sxs-lookup"><span data-stu-id="784c2-129">All the destination table columns will behave just like normal columns.</span></span> <span data-ttu-id="784c2-130">這些資料行不會有任何關聯的 FileTable 語意。</span><span class="sxs-lookup"><span data-stu-id="784c2-130">They will not have any FileTable semantics associated with them.</span></span>  
  
##  <a name="triggers-and-filetables"></a><a name="OtherTriggers"></a> <span data-ttu-id="784c2-131">觸發程序和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-131">Triggers and FileTables</span></span>  
 <span data-ttu-id="784c2-132">**DDL (資料定義語言) 觸發程序**</span><span class="sxs-lookup"><span data-stu-id="784c2-132">**DDL (Data Definition Language) Triggers**</span></span>  
 <span data-ttu-id="784c2-133">包含 FileTable 的 DDL 觸發程序並無特殊考量。</span><span class="sxs-lookup"><span data-stu-id="784c2-133">There are no special considerations for DDL triggers with FileTables.</span></span> <span data-ttu-id="784c2-134">一般 DDL 觸發程序將針對 Create/Alter DATABASE 作業以及 FileTable 的 CREATE/ALTER TABLE 作業引發。</span><span class="sxs-lookup"><span data-stu-id="784c2-134">Normal DDL triggers will fire for Create/Alter database operations as well as CREATE/ALTER TABLE operations for FileTables.</span></span> <span data-ttu-id="784c2-135">觸發程序可以透過呼叫 EVENTDATA() 函數，擷取實際事件資料，該資料包括 DDL 命令文字和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="784c2-135">Triggers can retrieve the actual event data that includes the DDL command text and other information by calling the EVENTDATA() function.</span></span> <span data-ttu-id="784c2-136">現有 Eventdata 結構描述沒有任何新的事件或變更。</span><span class="sxs-lookup"><span data-stu-id="784c2-136">There are no new events or changes to the existing Eventdata schema.</span></span>  
  
 <span data-ttu-id="784c2-137">**DML (資料操作語言) 觸發程序**</span><span class="sxs-lookup"><span data-stu-id="784c2-137">**DML (Data Manipulation Language) Triggers**</span></span>  
 <span data-ttu-id="784c2-138">在建立觸發程序的 DDL 作業期間將會強制施行這些限制。</span><span class="sxs-lookup"><span data-stu-id="784c2-138">These restrictions will be enforced during the DDL operation to create triggers.</span></span>  
  
-   <span data-ttu-id="784c2-139">FileTable 將不會支援 DML 作業的 INSTEAD OF 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="784c2-139">FileTables will NOT support INSTEAD OF triggers for DML operations.</span></span> <span data-ttu-id="784c2-140">包含 FILESTREAM 資料行的所有資料表都有現有的限制。</span><span class="sxs-lookup"><span data-stu-id="784c2-140">This is an existing restriction on all tables that contain FILESTREAM columns.</span></span>  
  
-   <span data-ttu-id="784c2-141">FileTable 將會支援 DML 作業的 AFTER 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="784c2-141">FileTables will support AFTER triggers for DML operations.</span></span>  
  
-   <span data-ttu-id="784c2-142">FileTable 上定義的觸發程序無法更新任何 FileTable (包括父系 FileTable)。</span><span class="sxs-lookup"><span data-stu-id="784c2-142">Triggers defined on a FileTable cannot update any FileTables (including the parent FileTable).</span></span> <span data-ttu-id="784c2-143">這項限制存在的目的主要是為了避免觸發程序與相同交易中檔案系統存取所持有的鎖定之間發生鎖定衝突。</span><span class="sxs-lookup"><span data-stu-id="784c2-143">This restriction exists mainly to prevent a trigger from getting into locking conflicts with the locks held by the file system access in the same transaction.</span></span>  
  
 <span data-ttu-id="784c2-144">**非交易式存取以及它對觸發程序的影響**</span><span class="sxs-lookup"><span data-stu-id="784c2-144">**Non-transactional access and its effects on triggers**</span></span>  
 -   <span data-ttu-id="784c2-145">當某個資料庫允許非交易式更新存取時，您就可以針對任何資料表中的 FILESTREAM 資料進行就地更新，包括該資料庫中的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="784c2-145">When non-transactional update access is allowed in a database, it is possible to do in-place update of the FILESTREAM data in any table, including FileTable in that database.</span></span> <span data-ttu-id="784c2-146">由於這種可能性，因此觸發程序可能無法使用 FILESTREAM 內容的前置資料影像。</span><span class="sxs-lookup"><span data-stu-id="784c2-146">Due to this possibility, the before image of the FILESTREAM contents may not be available for use by the trigger.</span></span>  
  
-   <span data-ttu-id="784c2-147">如果是透過檔案系統的非交易式更新作業，SQL Server 將會建立內部交易來擷取 CloseHandle 作業，而且任何已定義的 DML 觸發程序可能會當做該交易的一部分引發。</span><span class="sxs-lookup"><span data-stu-id="784c2-147">For non-transactional update operations through File system, SQL Server will create an internal transaction to capture the CloseHandle operation and the any defined DML triggers may be fired as part of that transaction.</span></span> <span data-ttu-id="784c2-148">雖然無法防止觸發程序主體內部之這類交易的回復，不過這項作業不會回復已對 FILESTREAM 所做的變更。</span><span class="sxs-lookup"><span data-stu-id="784c2-148">A rollback such a transaction inside the trigger body, while not prevented, does not roll back the changes done to the FILESTREAM.</span></span>  <span data-ttu-id="784c2-149">這類回復可能也會防止系統引發 Update 觸發程序，即使 FILESTREAM 內容可能已經變更也一樣。</span><span class="sxs-lookup"><span data-stu-id="784c2-149">Such a rollback may also prevent the Update triggers from being fired, even though the FILESTREAM contents may have been changed.</span></span>  
  
-   <span data-ttu-id="784c2-150">除了這些影響以外，FileTable 的觸發程序也需要處理其他幾個行為</span><span class="sxs-lookup"><span data-stu-id="784c2-150">In addition to these impacts, triggers on FileTables need to deal with couple of additional behaviors</span></span>  
  
    -   <span data-ttu-id="784c2-151">如果是透過檔案系統針對 FileTable 進行的非交易式更新作業，FILESTREAM 內容可能會由其他 Win32 作業獨佔鎖定，而且可能無法透過觸發程序主體進行讀取/寫入存取。</span><span class="sxs-lookup"><span data-stu-id="784c2-151">In case of non-transactional update operations on FileTable through the File system, it is possible that the FILESTREAM contents may be exclusively locked by other Win32 operations and may not be accessible for read/write through the trigger body.</span></span> <span data-ttu-id="784c2-152">在這類情況中，任何嘗試存取觸發程序主體中之 FILESTREAM 內容的行為都可能會產生「共用違規」錯誤。</span><span class="sxs-lookup"><span data-stu-id="784c2-152">In such cases, any attempt to access the FILESTREAM contents within the trigger body may give a "Sharing Violation" error.</span></span> <span data-ttu-id="784c2-153">因此，觸發程序應該設計成可正確處理這類錯誤。</span><span class="sxs-lookup"><span data-stu-id="784c2-153">Triggers should be designed to handle such errors appropriately.</span></span>  
  
    -   <span data-ttu-id="784c2-154">FILESTREAM 的 AFTER 影像可能不穩定，因為在某些情況下，其他非交易式更新可能基於檔案系統存取所允許的共用模式，同時主動寫入該影像。</span><span class="sxs-lookup"><span data-stu-id="784c2-154">AFTER image of the FILESTREAM may not be stable since in some cases it may be actively being written by other non-transactional updates at the same time (due to the sharing modes permitted in the File system access).</span></span>  
  
-   <span data-ttu-id="784c2-155">不正常終止 Win32 控制代碼 (例如管理員明確終止 Win32 控制代碼或是資料庫損毀) 將不會在復原作業期間執行使用者觸發程序，即使不正常終止的 Win32 應用程式可能已經變更 FILESTREAM 內容也是一樣。</span><span class="sxs-lookup"><span data-stu-id="784c2-155">Abnormal termination of Win32 handles, like explicit killing of Win32 handles by an admin OR a database crash, will not execute user triggers during the recovery operations, even though the FILESTREAM content may have been changed by the abnormally terminated Win32 application.</span></span>  
  
##  <a name="views-and-filetables"></a><a name="OtherViews"></a> <span data-ttu-id="784c2-156">檢視表和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-156">Views and FileTables</span></span>  
 <span data-ttu-id="784c2-157">**檢視**</span><span class="sxs-lookup"><span data-stu-id="784c2-157">**Views**</span></span>  
 <span data-ttu-id="784c2-158">可以在 FileTable 上建立檢視表，就像在任何其他資料表上建立一樣。</span><span class="sxs-lookup"><span data-stu-id="784c2-158">A view can be created on a FileTable as on any other table.</span></span> <span data-ttu-id="784c2-159">但是，在 FileTable 上建立的檢視表要考量以下事項：</span><span class="sxs-lookup"><span data-stu-id="784c2-159">However the following considerations apply to a view created on a FileTable:</span></span>  
  
-   <span data-ttu-id="784c2-160">檢視表將不會有任何 FileTable 語意。</span><span class="sxs-lookup"><span data-stu-id="784c2-160">View will not have any FileTable semantics.</span></span> <span data-ttu-id="784c2-161">例如，檢視表中的資料行 (包括 [檔案屬性] 資料行) 的行為就像一般檢視表資料行一樣，沒有任何特殊的語意，代表檔案/目錄的資料列也是相同情形。</span><span class="sxs-lookup"><span data-stu-id="784c2-161">i.e. the columns in the view (including File Attribute columns) behave just like normal view columns without any special semantics and same is true for rows representing Files/directories.</span></span>  
  
-   <span data-ttu-id="784c2-162">檢視表可能會依據「可更新的檢視表」語意來更新，但是基礎資料表條件約束可以拒絕更新，就像在資料表中一樣。</span><span class="sxs-lookup"><span data-stu-id="784c2-162">View may be updateable based on the "updateable view" semantics, but the underlying table constraints can reject the updates just like in the table.</span></span>  
  
-   <span data-ttu-id="784c2-163">檔案的檔案路徑可以在檢視表中視覺化，其方式是將它新增為檢視表中的明確資料行。</span><span class="sxs-lookup"><span data-stu-id="784c2-163">File path for a file can be visualized in the view by adding it as an explicit column in the view.</span></span> <span data-ttu-id="784c2-164">例如：</span><span class="sxs-lookup"><span data-stu-id="784c2-164">For example:</span></span>  
  
     `CREATE VIEW MP3FILES AS SELECT column1, column2, ..., GetFileNamespacePath() AS PATH, column3,...  FROM Documents`  
  
 <span data-ttu-id="784c2-165">**索引檢視表**</span><span class="sxs-lookup"><span data-stu-id="784c2-165">**Indexed Views**</span></span>  
 <span data-ttu-id="784c2-166">目前的索引檢視表不得包含 FILESTREAM 資料行，或是相依於 FILESTREAM 資料行的計算資料行/保存的計算資料行。</span><span class="sxs-lookup"><span data-stu-id="784c2-166">Currently Indexed views cannot include FILESTREAM columns or computed/persisted computed columns that depend on the FILESTREAM columns.</span></span> <span data-ttu-id="784c2-167">當 FileTable 上定義檢視表時，這個行為依然不會變更。</span><span class="sxs-lookup"><span data-stu-id="784c2-167">This behavior remains unchanged with views defined on the FileTable also.</span></span>  
  
##  <a name="snapshot-isolation-and-filetables"></a><a name="OtherSnapshots"></a> <span data-ttu-id="784c2-168">快照集隔離和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-168">Snapshot Isolation and FileTables</span></span>  
 <span data-ttu-id="784c2-169">Read Committed 快照集隔離 (RCSI) 和快照集隔離 (SI) 會依賴擁有資料快照集可供讀取者使用的能力，即使資料上發生更新作業也是一樣。</span><span class="sxs-lookup"><span data-stu-id="784c2-169">Read Committed Snapshot Isolation (RCSI) and Snapshot Isolation (SI) rely on the ability to have a snapshot of the data available for readers even when update operations are happening on the data.</span></span> <span data-ttu-id="784c2-170">但是，FileTables 允許對 Filestream 資料的非交易式寫入存取。</span><span class="sxs-lookup"><span data-stu-id="784c2-170">However FileTables allow non-transactional write access to Filestream data.</span></span> <span data-ttu-id="784c2-171">因此，以下限制適用於在包含 FileTable 的資料庫中使用這些功能：</span><span class="sxs-lookup"><span data-stu-id="784c2-171">As a result, the following restrictions apply to the use of these features in databases that contain FileTables:</span></span>  
  
-   <span data-ttu-id="784c2-172">可以更改包含 FileTable 的資料庫來啟用 RCSI/SI。</span><span class="sxs-lookup"><span data-stu-id="784c2-172">A database that contains FileTables can be altered to enable RCSI/SI.</span></span>  
  
-   <span data-ttu-id="784c2-173">當資料庫的非交易式存取設定為 FULL 時，在 RCSI 或 SI 之下執行的交易具有以下行為：</span><span class="sxs-lookup"><span data-stu-id="784c2-173">When non_transactional access is set to FULL for the database, then a transaction running under RCSI or SI has the following behavior:</span></span>  
  
    -   <span data-ttu-id="784c2-174">讀取到 FileTable file_stream 資料行的任何 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 都會失敗。</span><span class="sxs-lookup"><span data-stu-id="784c2-174">Any [!INCLUDE[tsql](../../../includes/tsql-md.md)] reads of the FileTable file_stream column fail.</span></span> <span data-ttu-id="784c2-175">資料行的 INSERT 和 UPDATE 依然會成功，只要不是從 file_stream 資料行讀取。</span><span class="sxs-lookup"><span data-stu-id="784c2-175">INSERT and UPDATE to the column still succeed, as long as they do not read from the file_stream column.</span></span>  
  
    -   <span data-ttu-id="784c2-176">如果 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式指定 READCOMMITTEDLOCK 資料表提示，讀取將會成功，而且將會取得資料列的鎖定，而不是使用資料列版本設定。</span><span class="sxs-lookup"><span data-stu-id="784c2-176">If the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement specifies READCOMMITTEDLOCK table hints, the reads succeed, and take locks on the rows, rather than use row versioning.</span></span>  
  
    -   <span data-ttu-id="784c2-177">交易 Win32 FileStream 開啟要求也會失敗。</span><span class="sxs-lookup"><span data-stu-id="784c2-177">Transacted Win32 FileStream open requests also fail.</span></span>  
  
    -   <span data-ttu-id="784c2-178">非交易 FileTable Win32 存取會成功。</span><span class="sxs-lookup"><span data-stu-id="784c2-178">Non-transacted FileTable Win32 access succeeds.</span></span> <span data-ttu-id="784c2-179">FileTable 執行的所有內部查詢都不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="784c2-179">All internal queries done by FileTable are not affected.</span></span>  
  
    -   <span data-ttu-id="784c2-180">全文檢索索引一定會成功，不論資料庫選項為何 (READ_COMMITTED_SNAPSHOT 或 ALLOW_SNAPSHOT_ISOLATION)。</span><span class="sxs-lookup"><span data-stu-id="784c2-180">Fulltext indexing always succeeds, no matter what the database options are (READ_COMMITTED_SNAPSHOT or ALLOW_SNAPSHOT_ISOLATION).</span></span>  
  
##  <a name="readable-secondary-databases"></a><a name="readsec"></a> <span data-ttu-id="784c2-181">可讀取次要資料庫</span><span class="sxs-lookup"><span data-stu-id="784c2-181">Readable Secondary Databases</span></span>  
 <span data-ttu-id="784c2-182">快照集的相同考量，如上節＜ [快照集隔離和 FileTable](#OtherSnapshots)＞所述，也適用於可讀取次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="784c2-182">The same considerations apply to readable secondary databases as to snapshots, as described in the preceding section, [Snapshot Isolation and FileTables](#OtherSnapshots).</span></span>  
  
##  <a name="contained-databases-and-filetables"></a><a name="CDB"></a> <span data-ttu-id="784c2-183">自主資料庫和 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-183">Contained Databases and FileTables</span></span>  
 <span data-ttu-id="784c2-184">FileTable 功能相依的 FILESTREAM 功能必須先在資料庫外部進行一些設定。</span><span class="sxs-lookup"><span data-stu-id="784c2-184">The FILESTREAM feature on which the FileTable feature depends requires some configuration outside of the database.</span></span> <span data-ttu-id="784c2-185">因此，使用 FILESTREAM 或 FileTable 的資料庫並非完全自主。</span><span class="sxs-lookup"><span data-stu-id="784c2-185">Therefore a database that uses FILESTREAM or FileTable is not fully contained.</span></span>  
  
 <span data-ttu-id="784c2-186">若要使用自主資料庫的特定功能 (例如包含的使用者)，可以將資料庫內含項目設定為 PARTIAL。</span><span class="sxs-lookup"><span data-stu-id="784c2-186">You can set database containment to PARTIAL if you want to use certain features of contained databases, such as contained users.</span></span> <span data-ttu-id="784c2-187">但在此情況下，必須注意某些資料庫設定不會包含在資料庫中，因此不會隨資料庫移動自動移動。</span><span class="sxs-lookup"><span data-stu-id="784c2-187">In this case, however, you must be aware that some of the database settings are not contained in the database and are not automatically moved when the database moves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="784c2-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="784c2-188">See Also</span></span>  
 [<span data-ttu-id="784c2-189">管理 FileTable</span><span class="sxs-lookup"><span data-stu-id="784c2-189">Manage FileTables</span></span>](manage-filetables.md)  
  
  
