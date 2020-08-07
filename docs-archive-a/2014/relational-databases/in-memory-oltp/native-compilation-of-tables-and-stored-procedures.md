---
title: 資料表和預存程序的原生編譯 | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5880fbd9-a23e-464a-8b44-09750eeb2dad
author: rothja
ms.author: jroth
ms.openlocfilehash: 32c5b04610d894e06278fbeecdaf3bbebe850d60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597121"
---
# <a name="native-compilation-of-tables-and-stored-procedures"></a><span data-ttu-id="d1e52-102">資料表和預存程序的原生編譯</span><span class="sxs-lookup"><span data-stu-id="d1e52-102">Native Compilation of Tables and Stored Procedures</span></span>
  <span data-ttu-id="d1e52-103">記憶體中 OLTP 導入了原生編譯的概念。</span><span class="sxs-lookup"><span data-stu-id="d1e52-103">In-Memory OLTP introduces the concept of native compilation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1e52-104">可原生編譯用來存取記憶體最佳化資料表的預存程序。</span><span class="sxs-lookup"><span data-stu-id="d1e52-104">can natively compile stored procedures that access memory-optimized tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1e52-105">也可以透過原生方式編譯記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="d1e52-105">is also able to natively compile memory-optimized tables.</span></span> <span data-ttu-id="d1e52-106">與解譯的 (傳統) [!INCLUDE[tsql](../../includes/tsql-md.md)]相較之下，原生編譯可提供更快速的資料存取並且更有效率地執行查詢。</span><span class="sxs-lookup"><span data-stu-id="d1e52-106">Native compilation allows faster data access and more efficient query execution than interpreted (traditional) [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d1e52-107">資料表和預存程序的原生編譯會產生 DLL。</span><span class="sxs-lookup"><span data-stu-id="d1e52-107">Native compilation of tables and stored procedures produce DLLs.</span></span>  
  
 <span data-ttu-id="d1e52-108">另外也支援記憶體最佳化資料表類型的原生編譯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-108">Native compilation of memory optimized table types is also supported.</span></span> <span data-ttu-id="d1e52-109">如需詳細資訊，請參閱 [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e52-109">For more information, see [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md).</span></span>  
  
 <span data-ttu-id="d1e52-110">原生編譯是指將程式設計結構轉換成原生程式碼的程序，包含處理器指令，而不需再進一步編譯或解譯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-110">Native compilation refers to the process of converting programming constructs to native code, consisting of processor instructions without the need for further compilation or interpretation.</span></span>  
  
 <span data-ttu-id="d1e52-111">記憶體內 OLTP 會在建立記憶體最佳化資料表時，以及原生編譯預存程序載入原生 DLL 時，對兩者編譯記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="d1e52-111">In-Memory OLTP compiles memory-optimized tables when they are created, and natively compiled stored procedures when they are loaded to native DLLs.</span></span> <span data-ttu-id="d1e52-112">此外，DLL 會在資料庫或伺服器重新啟動之後重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-112">In addition, the DLLs are recompiled after a database or server restart.</span></span> <span data-ttu-id="d1e52-113">重新建立 DLL 所需的資訊儲存在資料庫中繼資料內。</span><span class="sxs-lookup"><span data-stu-id="d1e52-113">The information necessary to recreate the DLLs is stored in the database metadata.</span></span> <span data-ttu-id="d1e52-114">DLL 不是資料庫的一部分，不過它們與資料庫相關聯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-114">The DLLs are not part of the database, though they are associated with the database.</span></span> <span data-ttu-id="d1e52-115">例如，DLL 不包含在資料庫備份中。</span><span class="sxs-lookup"><span data-stu-id="d1e52-115">For example, the DLLs are not included in database backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1e52-116">記憶體最佳化資料表會在重新啟動伺服器期間重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-116">Memory-optimized tables are recompiled during a server restart.</span></span> <span data-ttu-id="d1e52-117">為了加速資料庫的復原，不會在啟動伺服器期間重新編譯原生編譯預存程序，而是會在第一次執行時進行編譯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-117">To speed up database recovery, natively compiled stored procedures are not recompiled during a server restart, they are compiled at the time of first execution.</span></span> <span data-ttu-id="d1e52-118">因為此延遲編譯，原生編譯預存程序只會在第一次執行後，呼叫 [sys.dm_os_loaded_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql) 時出現。</span><span class="sxs-lookup"><span data-stu-id="d1e52-118">As a result of this deferred compilation, natively compiled stored procedures only appear when calling [sys.dm_os_loaded_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql) after first execution.</span></span>  
  
## <a name="maintenance-of-in-memory-oltp-dlls"></a><span data-ttu-id="d1e52-119">維護記憶體中 OLTP DLL</span><span class="sxs-lookup"><span data-stu-id="d1e52-119">Maintenance of In-Memory OLTP DLLs</span></span>  
 <span data-ttu-id="d1e52-120">下列查詢顯示目前載入伺服器記憶體中的所有資料表和預存程序 DLL：</span><span class="sxs-lookup"><span data-stu-id="d1e52-120">The following query shows all table and stored procedure DLLs currently loaded in memory on the server:</span></span>  
  
```sql  
SELECT name, description FROM sys.dm_os_loaded_modules  
where description = 'XTP Native DLL'  
```  
  
 <span data-ttu-id="d1e52-121">資料庫管理員不需要維護原生編譯所產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="d1e52-121">Database administrators do not need to maintain files that are generated by a native compilation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1e52-122">會在不再需要時自動移除產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="d1e52-122">automatically removes generated files that are no longer needed.</span></span> <span data-ttu-id="d1e52-123">例如，產生的檔案會在資料表和預存程序已刪除，或資料庫卸載時移除。</span><span class="sxs-lookup"><span data-stu-id="d1e52-123">For example, generated files will be deleted when a table and stored procedure is deleted, or if a database is dropped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1e52-124">編譯失敗或中斷時，某些產生的檔案並不會刪除。</span><span class="sxs-lookup"><span data-stu-id="d1e52-124">If compilation fails or is interrupted, some generated files are not removed.</span></span> <span data-ttu-id="d1e52-125">刻意留下這些檔案是為了提供支援，而這些檔案會在資料庫卸除時移除。</span><span class="sxs-lookup"><span data-stu-id="d1e52-125">These files are intentionally left behind for supportability and are removed when the database is dropped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1e52-126">資料庫在啟動期間，SQL Server 會為資料庫復原所需的所有資料表編譯 Dll。</span><span class="sxs-lookup"><span data-stu-id="d1e52-126">During database startup, SQL Server compiles DLLs for all tables needed for database recovery.</span></span> <span data-ttu-id="d1e52-127">如果資料表在資料庫重新啟動之前已卸除，則檢查點檔案或交易記錄檔中可能仍有剩餘的資料表，讓資料表 DLL 可能會在資料庫啟動期間重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-127">If a table was dropped just prior to a database restart there can still be remnants of the table in the checkpoint files or the transaction log so the DLL for the table might be recompiled during database startup.</span></span> <span data-ttu-id="d1e52-128">重新啟動之後 DLL 將會被卸載，一般的清理程序就會移除檔案。</span><span class="sxs-lookup"><span data-stu-id="d1e52-128">After restart the DLL will be unloaded and the files will be removed by the normal cleanup process.</span></span>  
  
## <a name="native-compilation-of-tables"></a><span data-ttu-id="d1e52-129">資料表的原生編譯</span><span class="sxs-lookup"><span data-stu-id="d1e52-129">Native Compilation of Tables</span></span>  
 <span data-ttu-id="d1e52-130">使用 `CREATE TABLE` 陳述式建立記憶體最佳化資料表會導致將資料表資訊寫入資料庫中繼資料，並且在記憶體中建立資料表和索引結構。</span><span class="sxs-lookup"><span data-stu-id="d1e52-130">Creating a memory-optimized table using the `CREATE TABLE` statement results in the table information being written to the database metadata and the table and index structures created in memory.</span></span> <span data-ttu-id="d1e52-131">資料表也會編譯為 DLL。</span><span class="sxs-lookup"><span data-stu-id="d1e52-131">The table will also be compiled to a DLL.</span></span>  
  
 <span data-ttu-id="d1e52-132">請考慮下列範例指令碼，該指令碼會建立資料庫和記憶體最佳化資料表：</span><span class="sxs-lookup"><span data-stu-id="d1e52-132">Consider the following sample script, which creates a database and a memory-optimized table:</span></span>  
  
```sql  
use master  
go  
create database db1  
go  
alter database db1 add filegroup db1_mod contains memory_optimized_data  
go  
-- adapt filename as needed  
alter database db1 add file (name='db1_mod', filename='c:\data\db1_mod') to filegroup db1_mod  
go  
use db1  
go  
create table dbo.t1  
   (c1 int not null primary key nonclustered,  
    c2 INT)  
with (memory_optimized=on)  
go  
-- retrieve the path of the DLL for table t1  
select name, description FROM sys.dm_os_loaded_modules  
where name like '%xtp_t_' + cast(db_id() as varchar(10)) + '_' + cast(object_id('dbo.t1') as varchar(10)) + '.dll'  
go  
```  
  
 <span data-ttu-id="d1e52-133">建立資料表也會建立資料表 DLL 並將 DLL 載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="d1e52-133">Creating the table also creates the table DLL and loads the DLL in memory.</span></span> <span data-ttu-id="d1e52-134">CREATE TABLE 陳述式後面緊接著的 DMV 查詢會擷取資料表 DLL 的路徑。</span><span class="sxs-lookup"><span data-stu-id="d1e52-134">The DMV query immediately after the CREATE TABLE statement retrieves the path of the table DLL.</span></span>  
  
 <span data-ttu-id="d1e52-135">資料表 DLL 可理解資料表的索引結構和資料列格式。</span><span class="sxs-lookup"><span data-stu-id="d1e52-135">The table DLL understands the index structures and row format of the table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1e52-136">會使用 DLL 周遊索引、擷取資料列，以及儲存資料列內容。</span><span class="sxs-lookup"><span data-stu-id="d1e52-136">uses the DLL for traversing indexes, retrieving rows, as well as storing the contents of the rows.</span></span>  
  
## <a name="native-compilation-of-stored-procedures"></a><span data-ttu-id="d1e52-137">預存程序的原生編譯</span><span class="sxs-lookup"><span data-stu-id="d1e52-137">Native Compilation of Stored Procedures</span></span>  
 <span data-ttu-id="d1e52-138">標示為 NATIVE_COMPILATION 的預存程序為原生編譯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-138">Stored procedures that are marked with NATIVE_COMPILATION are natively compiled.</span></span> <span data-ttu-id="d1e52-139">這表示，程序中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式全都編譯為原生程式碼，能夠有效率地執行效能具有決定性的商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-139">This means the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the procedure are all compiled to native code for efficient execution of performance-critical business logic.</span></span>  
  
 <span data-ttu-id="d1e52-140">如需原生編譯的預存程序的詳細資訊，請參閱 [原生編譯的預存程序](natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e52-140">For more information about natively compiled stored procedures, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="d1e52-141">請考慮下列範例預存程序，它會在上一個範例的資料表 t1 中插入資料列：</span><span class="sxs-lookup"><span data-stu-id="d1e52-141">Consider the following sample stored procedure, which inserts rows in the table t1 from the previous example:</span></span>  
  
```sql  
create procedure dbo.native_sp  
with native_compilation, schemabinding, execute as owner  
as  
begin atomic  
with (transaction isolation level=snapshot, language=N'us_english')  
  
  declare @i int = 1000000  
  while @i > 0  
  begin  
    insert dbo.t1 values (@i, @i+1)  
    set @i -= 1  
  end  
  
end  
go  
exec dbo.native_sp  
go  
-- reset  
delete from dbo.t1  
go  
```  
  
 <span data-ttu-id="d1e52-142">native_sp 的 DLL 可直接與 t1 的 DLL 以及記憶體中 OLTP 儲存引擎互動，以盡快將資料列插入。</span><span class="sxs-lookup"><span data-stu-id="d1e52-142">The DLL for native_sp can interact directly with the DLL for t1, as well as the In-Memory OLTP storage engine, to insert the rows as fast as possible.</span></span>  
  
 <span data-ttu-id="d1e52-143">記憶體中 OLTP 編譯器會利用查詢最佳化工具，為預存程序中的每個查詢建立有效率的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="d1e52-143">The In-Memory OLTP compiler leverages the query optimizer to create an efficient execution plan for each of the queries in the stored procedure.</span></span> <span data-ttu-id="d1e52-144">請注意，原生編譯的預存程序不會在資料表中的資料變更時自動重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d1e52-144">Note that natively compiled stored procedures are not automatically recompiled if the data in the table changes.</span></span> <span data-ttu-id="d1e52-145">如需維護記憶體內部 OLTP 中的統計資料和預存程序的詳細資訊，請參閱 [記憶體最佳化資料表的統計資料](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e52-145">For more information on maintaining statistics and stored procedures with In-Memory OLTP see [Statistics for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="security-considerations-for-native-compilation"></a><span data-ttu-id="d1e52-146">原生編譯的安全性考量</span><span class="sxs-lookup"><span data-stu-id="d1e52-146">Security Considerations for Native Compilation</span></span>  
 <span data-ttu-id="d1e52-147">資料表和預存程序的原生編譯使用記憶體中 OLTP 編譯器。</span><span class="sxs-lookup"><span data-stu-id="d1e52-147">Native compilation of tables and stored procedures uses the In-Memory OLTP compiler.</span></span> <span data-ttu-id="d1e52-148">此編譯器會產生寫入磁碟並載入記憶體中的檔案。</span><span class="sxs-lookup"><span data-stu-id="d1e52-148">This compiler produces files that are written to disk and loaded into memory.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1e52-149">使用下列機制限制這些檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="d1e52-149">uses the following mechanisms to limit access to these files.</span></span>  
  
### <a name="native-compiler"></a><span data-ttu-id="d1e52-150">原生編譯器</span><span class="sxs-lookup"><span data-stu-id="d1e52-150">Native Compiler</span></span>  
 <span data-ttu-id="d1e52-151">原生編譯所需的編譯器可執行檔以及二進位和標頭檔案已在 MSSQL\Binn\Xtp 資料夾之下，安裝為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的一部分。</span><span class="sxs-lookup"><span data-stu-id="d1e52-151">The compiler executable, as well as binaries and header files required for native compilation are installed as part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance under the folder MSSQL\Binn\Xtp.</span></span> <span data-ttu-id="d1e52-152">因此，如果預設實例安裝在 C:\Program files 底下，編譯器檔案就會安裝在 C:\Program Files \\ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12。MSSQLSERVER\MSSQL\Binn\Xtp.</span><span class="sxs-lookup"><span data-stu-id="d1e52-152">So, if the default instance is installed under C:\Program Files, the compiler files are installed in C:\Program Files\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn\Xtp.</span></span>  
  
 <span data-ttu-id="d1e52-153">若要限制編譯器的存取權， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用存取控制清單 (ACL) 限制二進位檔案的存取。</span><span class="sxs-lookup"><span data-stu-id="d1e52-153">To limit access to the compiler, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses access control lists (ACLs) to restrict access to binary files.</span></span> <span data-ttu-id="d1e52-154">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 二進位皆受到保護，以防止其遭到修改或透過 ACL 竄改。</span><span class="sxs-lookup"><span data-stu-id="d1e52-154">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries are protected against modification or tampering through ACLs.</span></span> <span data-ttu-id="d1e52-155">原生編譯器的 ACL 也限制編譯器的使用權，僅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶和系統管理員擁有原生編譯器檔案的讀取和執行權限。</span><span class="sxs-lookup"><span data-stu-id="d1e52-155">The native compiler's ACLs also limit use of the compiler; only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and system administrators have read and execute permissions for native compiler files.</span></span>  
  
### <a name="files-generated-by-a-native-compilation"></a><span data-ttu-id="d1e52-156">原生編譯產生的檔案</span><span class="sxs-lookup"><span data-stu-id="d1e52-156">Files Generated by a Native Compilation</span></span>  
 <span data-ttu-id="d1e52-157">當資料表或預存程序進行編譯時，所產生的檔案會包含 DLL 以及中繼檔案，而中繼檔案含有下列附檔名：.c、.obj、.xml 和 .pdb。</span><span class="sxs-lookup"><span data-stu-id="d1e52-157">The files produced when a table or stored procedure is compiled include the DLL and intermediate files including files with the following extensions: .c, .obj, .xml, and .pdb.</span></span> <span data-ttu-id="d1e52-158">產生的檔案會儲存在預設資料夾的子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d1e52-158">The generated files are saved in a subfolder of the default data folder.</span></span> <span data-ttu-id="d1e52-159">這個子資料夾名為 Xtp。</span><span class="sxs-lookup"><span data-stu-id="d1e52-159">The subfolder is called Xtp.</span></span> <span data-ttu-id="d1e52-160">使用預設資料夾安裝預設實例時，產生的檔案會放在 C:\Program files \\ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12。MSSQLSERVER\MSSQL\DATA\Xtp.</span><span class="sxs-lookup"><span data-stu-id="d1e52-160">When installing the default instance with the default data folder, the generated files are placed in C:\Program Files\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\DATA\Xtp.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1e52-161">使用三種方式防止產生的 DLL 遭竄改：</span><span class="sxs-lookup"><span data-stu-id="d1e52-161">prevents tampering with the generated DLLs in three ways:</span></span>  
  
-   <span data-ttu-id="d1e52-162">當資料表或預存程序編譯為 DLL 時，此 DLL 會立即載入記憶體並連結到 sqlserver.exe 處理序。</span><span class="sxs-lookup"><span data-stu-id="d1e52-162">When a table or stored procedure is compiled to a DLL, this DLL is immediately loaded into memory and linked to the sqlserver.exe process.</span></span> <span data-ttu-id="d1e52-163">DLL 連結到處理序時無法修改。</span><span class="sxs-lookup"><span data-stu-id="d1e52-163">A DLL cannot be modified while it is linked to a process.</span></span>  
  
-   <span data-ttu-id="d1e52-164">當資料庫重新啟動時，所有資料表和預存程序將會依據資料庫中繼資料重新編譯 (移除並重新建立)。</span><span class="sxs-lookup"><span data-stu-id="d1e52-164">When a database is restarted, all tables and stored procedures are recompiled (removed and recreated) based on the database metadata.</span></span> <span data-ttu-id="d1e52-165">這將會移除惡意代理程式對產生之檔案所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="d1e52-165">This will remove any changes made to a generated file by a malicious agent.</span></span>  
  
-   <span data-ttu-id="d1e52-166">產生的資料會視為使用者資料的一部分，並和資料庫檔案擁有相同的安全性限制 (透過 ACL)：僅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶和系統管理員能夠存取這些檔案。</span><span class="sxs-lookup"><span data-stu-id="d1e52-166">The generated files are considered part of user data, and have the same security restrictions, via ACLs, as database files: only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and system administrators can access these files.</span></span>  
  
 <span data-ttu-id="d1e52-167">管理這些檔案不需要使用者互動。</span><span class="sxs-lookup"><span data-stu-id="d1e52-167">No user interaction is needed to manage these files.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1e52-168">會在必要時建立和移除檔案。</span><span class="sxs-lookup"><span data-stu-id="d1e52-168">will create and remove the files as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e52-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1e52-169">See Also</span></span>  
 <span data-ttu-id="d1e52-170">[記憶體優化資料表](memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="d1e52-170">[Memory-Optimized Tables](memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="d1e52-171">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="d1e52-171">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
