---
title: 管理 FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], security
- FileTables [SQL Server], managing access
ms.assetid: 93af982c-b4fe-4be0-8268-11f86dae27e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a15a914c243f1fafd3b913d98113e984bf533086
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699778"
---
# <a name="manage-filetables"></a><span data-ttu-id="b1eb7-102">管理 FileTable</span><span class="sxs-lookup"><span data-stu-id="b1eb7-102">Manage FileTables</span></span>
  <span data-ttu-id="b1eb7-103">描述用於管理 FileTable 的常見管理工作。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-103">Describes common administrative tasks for managing FileTables.</span></span>  
  
##  <a name="how-to-get-a-list-of-filetables-and-related-objects"></a><a name="HowToEnumerate"></a> <span data-ttu-id="b1eb7-104">如何：取得 FileTable 和相關物件的清單</span><span class="sxs-lookup"><span data-stu-id="b1eb7-104">How To: Get a List of FileTables and Related Objects</span></span>  
 <span data-ttu-id="b1eb7-105">若要取得 FileTable 的清單，請查詢下列其中一個目錄檢視：</span><span class="sxs-lookup"><span data-stu-id="b1eb7-105">To get a list of FileTables, query one of the following catalog views:</span></span>  
  
-   [<span data-ttu-id="b1eb7-106">sys.filetables &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1eb7-106">sys.filetables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)  
  
-   <span data-ttu-id="b1eb7-107">[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql) (檢查 **is_filetable** 資料行的值)。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-107">[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql) (Check the value of the **is_filetable** column.)</span></span>  
  
```sql  
SELECT * FROM sys.filetables;  
GO  
  
SELECT * FROM sys.tables WHERE is_filetable = 1;  
GO  
```  
  
 <span data-ttu-id="b1eb7-108">若要取得建立相關聯之 FileTable 時所建立的系統定義物件清單，請查詢 [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-108">To get a list of the system-defined objects that were created when the associated FileTables were created, query the catalog view [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).</span></span>  
  
```sql  
SELECT object_id, OBJECT_NAME(object_id) AS 'Object Name'  
    FROM sys.filetable_system_defined_objects  
    WHERE object_id = filetable_object_id;  
GO  
```  
  
##  <a name="disabling-and-re-enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsDisabling"></a> <span data-ttu-id="b1eb7-109">停用並重新啟用資料庫層級的非交易式存取</span><span class="sxs-lookup"><span data-stu-id="b1eb7-109">Disabling and Re-enabling Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="b1eb7-110">若要取得特定管理工作所需的獨佔存取，您可能必須暫時停用非交易式存取。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-110">To acquire the exclusive access that is required for certain administrative tasks, you may have to disable non-transactional access temporarily.</span></span>  
  
 <span data-ttu-id="b1eb7-111">**ALTER DATABASE 陳述式在變更非交易式存取層級時的行為**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-111">**Behavior of the ALTER DATABASE statement when changing the level of non-transactional access**</span></span>  
  
-   <span data-ttu-id="b1eb7-112">將非交易式存取設為 READ_ONLY 或 OFF 時，只要存在與所要求作業衝突的開啟檔案控制代碼，ALTER DATABASE 命令就不會將控制權傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-112">When you set non-transactional access to READ_ONLY or OFF, the ALTER DATABASE command does not return control to the user as long as there are open file handles that conflict with the requested operation.</span></span> <span data-ttu-id="b1eb7-113">與此作業衝突的檔案控制代碼包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="b1eb7-113">The file handles that conflict with this operation include the following:</span></span>  
  
    -   <span data-ttu-id="b1eb7-114">將存取權設為 **NONE**時，為所有開啟檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-114">When you are setting access to **NONE**, all open file handles.</span></span>  
  
    -   <span data-ttu-id="b1eb7-115">將存取權設為 **READ_ONLY**時，為所有針對寫入存取所開啟的檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-115">When you are setting access to **READ_ONLY**, all file handles opened for write access.</span></span>  
  
     <span data-ttu-id="b1eb7-116">如需有關終止開啟檔案控制代碼的詳細資訊，請參閱本主題中的＜ [終止與 FileTable 相關聯的開啟檔案控制代碼](#BasicsKilling) ＞。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-116">For information about killing open file handles, see [Killing Open File Handles Associated with a FileTable](#BasicsKilling) in this topic.</span></span>  
  
     <span data-ttu-id="b1eb7-117">如果 ALTER DATABASE 命令已取消或因逾時而結束，則交易式存取的層級不會變更。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-117">If the ALTER DATABASE command is canceled or ends with a timeout, then the level of transactional access is not changed.</span></span>  
  
-   <span data-ttu-id="b1eb7-118">如果使用 WITH \<termination> 子句 (ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT) 來呼叫 ALTER DATABASE 陳述式，則系統會終止所有開啟的非交易式檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-118">If you call the ALTER DATABASE statement with a WITH \<termination> clause (ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT), then all open non-transactional file handles are killed.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="b1eb7-119">終止開啟檔案控制代碼，可能會導致使用者遺失未儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-119">Killing open file handles may cause users to lose unsaved data.</span></span> <span data-ttu-id="b1eb7-120">此行為與檔案系統本身的行為一致。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-120">This behavior is consistent with the behavior of the file system itself.</span></span>  
  
 <span data-ttu-id="b1eb7-121">**停用非交易式存取的影響**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-121">**Effects of disabling non-transactional access**</span></span>  
  
 <span data-ttu-id="b1eb7-122">變更資料庫層級的非交易式存取層級，會對資料庫層級目錄底下的 FileTable 目錄造成下列影響：</span><span class="sxs-lookup"><span data-stu-id="b1eb7-122">Changing the level of non-transactional access at the database level has the following effects on the FileTable directories under the database-level directory:</span></span>  
  
-   <span data-ttu-id="b1eb7-123">將存取權設為 **NONE**時，就無法再存取或看到所有 FileTable 目錄及其內容。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-123">When you set access to **NONE**, then all the FileTable directories and their contents are no longer accessible or visible.</span></span>  
  
-   <span data-ttu-id="b1eb7-124">將存取權設為 **READ_ONLY**時，所有 FileTable 目錄和其內容也會是唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-124">When you set access to **READ_ONLY**, then all the FileTable directories and their contents are also read-only.</span></span>  
  
 <span data-ttu-id="b1eb7-125">停用執行個體層級的 FILESTREAM，會對該執行個體的資料庫層級目錄和其下的 FileTable 目錄造成下列影響：</span><span class="sxs-lookup"><span data-stu-id="b1eb7-125">Disabling FILESTREAM at the instance level has the following effects on the database-level directories on that instance, and the FileTable directories under them:</span></span>  
  
-   <span data-ttu-id="b1eb7-126">如果您在執行個體層級停用 FILESTREAM，就不會顯示執行個體上的資料庫層級目錄。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-126">None of the database-level directories on the instance are visible if FILESTREAM is disabled at the instance level.</span></span>  
  
###  <a name="how-to-disable-and-re-enable-non-transactional-access-at-the-database-level"></a><a name="HowToDisable"></a> <span data-ttu-id="b1eb7-127">如何：停用並重新啟用資料庫層級的非交易式存取</span><span class="sxs-lookup"><span data-stu-id="b1eb7-127">How To: Disable and Re-enable Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="b1eb7-128">如需詳細資訊，請參閱 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-128">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="b1eb7-129">**停用完整的非交易式存取**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-129">**To disable full non-transactional access**</span></span>  
 <span data-ttu-id="b1eb7-130">您可以呼叫 **ALTER DATABASE** 陳述式並將 **NON_TRANSACTED_ACCESS** 的值設定為 **READ_ONLY** 或 **OFF**。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-130">Call the **ALTER DATABASE** statement and SET the value of **NON_TRANSACTED_ACCESS** to **READ_ONLY** or **OFF**.</span></span>  
  
```sql  
-- Disable write access.  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = READ_ONLY );  
GO  
  
-- Disable non-transactional access.  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = OFF );  
GO  
```  
  
 <span data-ttu-id="b1eb7-131">**重新啟用完整的非交易式存取**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-131">**To re-enable full non-transactional access**</span></span>  
 <span data-ttu-id="b1eb7-132">您可以呼叫 **ALTER DATABASE** 陳述式並將 **NON_TRANSACTED_ACCESS** 的值設定為 **FULL**。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-132">Call the **ALTER DATABASE** statement and SET the value of **NON_TRANSACTED_ACCESS** to **FULL**.</span></span>  
  
```sql  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL );  
GO  
```  
  
###  <a name="how-to-ensure-the-visibility-of-the-filetables-in-a-database"></a><a name="visible"></a> <span data-ttu-id="b1eb7-133">如何：確保資料庫中 FileTable 的可見度</span><span class="sxs-lookup"><span data-stu-id="b1eb7-133">How to: Ensure the Visibility of the FileTables in a Database</span></span>  
 <span data-ttu-id="b1eb7-134">如果下列所有條件都成立，就會顯示資料庫層級目錄和其下的 FileTable 目錄 (如果有的話)：</span><span class="sxs-lookup"><span data-stu-id="b1eb7-134">A database-level directory and the FileTable directories under it are visible when all of these conditions are true:</span></span>  
  
1.  <span data-ttu-id="b1eb7-135">在執行個體層級啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-135">FILESTREAM is enabled at the instance level.</span></span>  
  
2.  <span data-ttu-id="b1eb7-136">在資料庫層級啟用非交易式存取。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-136">Non-transactional access is enabled at the database level.</span></span>  
  
3.  <span data-ttu-id="b1eb7-137">已在資料庫層級指定有效的目錄。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-137">A valid directory has been specified at the database level.</span></span>  
  
##  <a name="disabling-and-re-enabling-the-filetable-namespace-at-the-table-level"></a><a name="BasicsEnabling"></a> <span data-ttu-id="b1eb7-138">停用並重新啟用資料表層級的 FileTable 命名空間</span><span class="sxs-lookup"><span data-stu-id="b1eb7-138">Disabling and Re-enabling the FileTable Namespace at the Table Level</span></span>  
 <span data-ttu-id="b1eb7-139">停用 FileTable 命名空間，會停用所有使用 FileTable 所建立的系統定義條件約束和觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-139">Disabling the FileTable namespace disables all the system-defined constraints and triggers that were created with the FileTable.</span></span> <span data-ttu-id="b1eb7-140">如果您需要使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業來大規模重新組織 FileTable，但不想要產生 FileTable 語意強制執行的成本，這樣做就很有用。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-140">This is useful in cases where a FileTable has to be reorganized on a large scale by using [!INCLUDE[tsql](../../includes/tsql-md.md)] operations without incurring the expense of enforcing FileTable semantics.</span></span> <span data-ttu-id="b1eb7-141">不過，這些作業可能會讓 FileTable 處於不一致的狀態，而且可能會無法重新啟用 FileTable 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-141">However these operations can leave the FileTable in an inconsistent state, and can prevent the re-enabling of the FileTable namespace.</span></span>  
  
 <span data-ttu-id="b1eb7-142">停用 FileTable 命名空間會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="b1eb7-142">Disabling a FileTable namespace has the following results:</span></span>  
  
-   <span data-ttu-id="b1eb7-143">系統不會實際從資料表中卸除 FileTable 資料行和資料。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-143">FileTable columns and data are not physically dropped from the table.</span></span>  
  
-   <span data-ttu-id="b1eb7-144">FileTable 目錄及其所含的檔案和目錄會從檔案系統中消失，而且不適用於進行檔案 I/O 存取。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-144">The FileTable directory and the files and directories that it contains disappear from the file system and are not available for file i/o access.</span></span>  
  
-   <span data-ttu-id="b1eb7-145">您無法卸除和重新建立系統定義的 FileTable 資料行，但就 DML 作業而言，它們的行為與一般資料行一樣。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-145">System-defined FileTable columns cannot be dropped and recreated; otherwise, however, they behave like ordinary columns for DML operations.</span></span>  
  
-   <span data-ttu-id="b1eb7-146">開啟檔案控制代碼會讓 FileTable 條件約束無法停用，因為此作業在資料表上需要有結構描述鎖定。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-146">Open file handles prevent the FileTable constraints from being disabled, since this operation requires a schema lock on the table.</span></span>  
  
-   <span data-ttu-id="b1eb7-147">停用 FileTable 命名空間之後，系統會停止強制執行所有 FileTable 語意 (包含系統定義的條件約束和觸發程序)。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-147">Enforcement of all the FileTable semantics, including system-defined constraints and triggers, stops after the FileTable namespace is disabled.</span></span>  
  
 <span data-ttu-id="b1eb7-148">重新啟用 FileTable 命名空間會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="b1eb7-148">Re-enabling a FileTable namespace has the following results:</span></span>  
  
-   <span data-ttu-id="b1eb7-149">系統會檢查 FileTable 的一致性。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-149">The FileTable is checked for consistency.</span></span> <span data-ttu-id="b1eb7-150">如果發現不一致，則會引發錯誤，而 FileTable 會保持停用狀態，否則會重新啟用 FileTable。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-150">If inconsistencies are found, then an error is raised and the FileTable remains disabled; otherwise, the FileTable is re-enabled.</span></span>  
  
-   <span data-ttu-id="b1eb7-151">系統會還原強制執行 FileTable 語意 (包含系統定義的條件約束和觸發程序)。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-151">The enforcement of FileTable semantics, including system-defined constraints and triggers, is restored.</span></span>  
  
-   <span data-ttu-id="b1eb7-152">FileTable 目錄及其所含的檔案及目錄會在檔案系統中顯示，而且可用於進行檔案 I/O 存取。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-152">The FileTable directory and the files and directories that it contains become visible in the file system and become available for file i/o access.</span></span>  
  
###  <a name="how-to-disable-and-re-enable-the-filetable-namespace-at-the-table-level"></a><a name="HowToEnableNS"></a> <span data-ttu-id="b1eb7-153">如何：停用並重新啟用資料表層級的 FileTable 命名空間</span><span class="sxs-lookup"><span data-stu-id="b1eb7-153">How To: Disable and Re-enable the FileTable Namespace at the Table Level</span></span>  
 <span data-ttu-id="b1eb7-154">您可以使用 **{ ENABLE | DISABLE } FILETABLE_NAMESPACE** 選項來呼叫 ALTER TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-154">Call the ALTER TABLE statement with the **{ ENABLE | DISABLE } FILETABLE_NAMESPACE** option.</span></span>  
  
 <span data-ttu-id="b1eb7-155">**停用 FileTable 命名空間**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-155">**To disable the FileTable namespace**</span></span>  
 ```sql  
ALTER TABLE filetable_name  
    DISABLE FILETABLE_NAMESPACE;  
GO  
```  
  
 <span data-ttu-id="b1eb7-156">**重新啟用 FileTable 命名空間**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-156">**To re-enable the FileTable namespace**</span></span>  
 ```sql  
ALTER TABLE filetable_name  
    ENABLE FILETABLE_NAMESPACE;  
GO  
```  
  
##  <a name="killing-open-file-handles-associated-with-a-filetable"></a><a name="BasicsKilling"></a> <span data-ttu-id="b1eb7-157">終止與 FileTable 相關聯的開啟檔案控制代碼</span><span class="sxs-lookup"><span data-stu-id="b1eb7-157">Killing Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="b1eb7-158">儲存在 FileTable 中之檔案的開啟控制代碼可能會防止特定管理工作所需的獨佔存取。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-158">Open handles to the files stored in a FileTable can prevent the exclusive access that is required for certain administrative tasks.</span></span> <span data-ttu-id="b1eb7-159">若要啟用緊急工作，您可能必須終止與一個或多個 FileTable 相關聯的開啟檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-159">To enable urgent tasks, you may have to kill open file handles associated with one or more FileTables.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="b1eb7-160">終止開啟檔案控制代碼，可能會導致使用者遺失未儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-160">Killing open file handles may cause users to lose unsaved data.</span></span> <span data-ttu-id="b1eb7-161">此行為與檔案系統本身的行為一致。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-161">This behavior is consistent with the behavior of the file system itself.</span></span>  
  
###  <a name="how-to-get-a-list-of-open-file-handles-associated-with-a-filetable"></a><a name="HowToListOpen"></a> <span data-ttu-id="b1eb7-162">如何：取得與 FileTable 建立關聯的開啟檔案控制代碼清單</span><span class="sxs-lookup"><span data-stu-id="b1eb7-162">How To: Get a List of Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="b1eb7-163">查詢 [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-163">Query the catalog view [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql).</span></span>  
  
```sql  
SELECT * FROM sys.dm_filestream_non_transacted_handles;  
GO  
```  
  
###  <a name="how-to-kill-open-file-handles-associated-with-a-filetable"></a><a name="HowToKill"></a> <span data-ttu-id="b1eb7-164">如何：終止與 FileTable 建立關聯的開啟檔案控制代碼</span><span class="sxs-lookup"><span data-stu-id="b1eb7-164">How To: Kill Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="b1eb7-165">使用適當的引數來呼叫預存程序 [sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles)，可終止資料庫或 FileTable 中的所有開啟檔案控制代碼，或是終止特定控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-165">Call the stored procedure [sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles) with the appropriate arguments to kill all open file handles in the database or in the FileTable, or to kill a specific handle.</span></span>  
  
```  
USE database_name;  
  
-- Kill all open handles in all the filetables in the database.  
EXEC sp_kill_filestream_non_transacted_handles;  
GO  
  
-- Kill all open handles in a single filetable.  
EXEC sp_kill_filestream_non_transacted_handles @table_name = 'filetable_name';  
GO  
  
-- Kill a single handle.  
EXEC sp_kill_filestream_non_transacted_handles @handle_id = integer_handle_id;  
GO  
```  
  
###  <a name="how-to-identify-the-locks-held-by-filetables"></a><a name="HowToIdentifyLocks"></a> <span data-ttu-id="b1eb7-166">如何：識別 FileTable 所持有的鎖定</span><span class="sxs-lookup"><span data-stu-id="b1eb7-166">How to: Identify the Locks Held by FileTables</span></span>  
 <span data-ttu-id="b1eb7-167">FileTable 所採用的大部分鎖定都會對應至應用程式所開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-167">Most locks taken by FileTables correspond to files opened by applications.</span></span>  
  
 <span data-ttu-id="b1eb7-168">**識別開啟的檔案和相關聯的鎖定**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-168">**To identify open files and the associated locks**</span></span>  
 <span data-ttu-id="b1eb7-169">您可以將 [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) 動態管理檢視中的 **request_owner_id** 欄位與 [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql) 中的 **fcb_id** 欄位聯結。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-169">Join the **request_owner_id** field in the dynamic management view [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) with the **fcb_id** field in [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql).</span></span> <span data-ttu-id="b1eb7-170">在某些情況下，鎖定不會對應至單一開啟檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-170">In some cases, the lock does not correspond to a single open file handle.</span></span>  
  
```sql  
SELECT opened_file_name  
    FROM sys.dm_filestream_non_transacted_handles  
    WHERE fcb_id IN  
        ( SELECT request_owner_id FROM sys.dm_tran_locks );  
GO  
```  
  
##  <a name="filetable-security"></a><a name="BasicsSecurity"></a> <span data-ttu-id="b1eb7-171">FileTable 安全性</span><span class="sxs-lookup"><span data-stu-id="b1eb7-171">FileTable Security</span></span>  
 <span data-ttu-id="b1eb7-172">儲存在 FileTable 中的檔案和目錄都僅受 SQL Server 安全性保護。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-172">The files and directories stored in FileTables are secured by SQL Server security only.</span></span> <span data-ttu-id="b1eb7-173">會針對檔案系統存取和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存取，強制執行以資料表和資料行為基礎的安全性。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-173">Table and column-based security is enforced for file system access as well as [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="b1eb7-174">但是，不支援 Windows 檔案系統安全性 API 和 ACL 設定。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-174">Windows file system security APIs and ACL settings are not supported.</span></span>  
  
 <span data-ttu-id="b1eb7-175">適用於 FILESTREAM 檔案群組和容器的安全性及存取權限也適用於 FileTable，因為檔案資料會儲存成 FileTable 中的 FILESTREAM 資料行。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-175">The security and access permissions that are applicable to FILESTREAM filegroups and containers also apply to FileTables, since the file data is stored as a FILESTREAM column in the FileTable.</span></span>  
  
 <span data-ttu-id="b1eb7-176">**FileTable 安全性和 Transact-SQL 存取**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-176">**FileTable Security and Transact-SQL Access**</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="b1eb7-177">FileTable 中資料的存取是使用與任何其他資料表相同的方式進行保護。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-177">access to data in FileTables is secured in the same way as any other table.</span></span> <span data-ttu-id="b1eb7-178">系統會針對每個存取或變更資料的作業，進行適當的資料表和資料行層級安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-178">Appropriate table and column-level security checks are done for every operation that accesses or changes the data.</span></span>  
  
 <span data-ttu-id="b1eb7-179">**FileTable 安全性和檔案系統存取**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-179">**FileTable Security and File System Access**</span></span>  
 <span data-ttu-id="b1eb7-180">檔案系統 API 需要 FileTable 中整個資料列的適當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 權限 (即資料表層級權限)，才能開啟 FileTable 中所儲存之檔案或目錄的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-180">File system APIs require appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permissions on the entire row in the FileTable (that is, table-level permission) to open a handle to a file or directory stored in the FileTable.</span></span> <span data-ttu-id="b1eb7-181">如果使用者沒有 FileTable 中任何資料行的適當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 權限，則會拒絕檔案系統存取。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-181">If the user does not have the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permission on any column in the FileTable, then file system access is denied.</span></span>  
  
##  <a name="backup-and-filetables"></a><a name="OtherBackup"></a> <span data-ttu-id="b1eb7-182">備份和 FileTable</span><span class="sxs-lookup"><span data-stu-id="b1eb7-182">Backup and FileTables</span></span>  
 <span data-ttu-id="b1eb7-183">當您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來備份 FileTable 時，FILESTREAM 資料會與資料庫中的結構化資料一起備份。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-183">When you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to back up a FileTable, the FILESTREAM data is backed up with the structured data in the database.</span></span> <span data-ttu-id="b1eb7-184">如果您不想要將 FILESTREAM 資料與關聯式資料一起備份，您可以使用部分備份來排除 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-184">If you do not want to back up FILESTREAM data with relational data, you can use a partial backup to exclude FILESTREAM filegroups.</span></span>  
  
 <span data-ttu-id="b1eb7-185">**FileTable 備份的交易一致性**</span><span class="sxs-lookup"><span data-stu-id="b1eb7-185">**Transactional Consistency of FileTable Backups**</span></span>  
  
 <span data-ttu-id="b1eb7-186">許多管理工具和作業 (包括備份、記錄備份和異動複寫) 會透過讀取交易記錄來讀取交易上一致的資料。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-186">Many administrative tools and operations, (including backup, log backup, and transactional replication) read transactionally consistent data by reading the transaction logs.</span></span> <span data-ttu-id="b1eb7-187">此時，它們會讀取當做交易之一部分更新的任何 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-187">At this time, they read any FILESTREAM data updated as part of a transaction.</span></span> <span data-ttu-id="b1eb7-188">未在資料庫層級啟用非交易式存取時，這些工具和作業會以完整交易一致性的方式運作。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-188">When non-transactional access is not enabled at the database level, these tools and operations work with full transactional consistency.</span></span>  
  
 <span data-ttu-id="b1eb7-189">但是，當啟用完整的非交易式存取時，則 FileTable 包含的更新資料可以比工具或程序從交易記錄讀取的交易還要新 (透過非交易式更新)。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-189">However, when full non-transactional access is enabled, then a FileTable could contain data that was updated more recently (through a non-transactional update) than the transaction that the tool or process is reading from the transaction log.</span></span> <span data-ttu-id="b1eb7-190">這表示，特定交易的「時間點」還原作業可能會包含比該交易還新的 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-190">This means that a "point in time" restore operation to a specific transaction may contain FILESTREAM data that is more recent than that transaction.</span></span> <span data-ttu-id="b1eb7-191">當 FileTable 上允許非交易式更新時，這會是預期的行為。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-191">This is the expected behavior when non-transactional updates are allowed on FileTables.</span></span>  
  
##  <a name="sql-server-profiler-and-filetables"></a><a name="Monitor"></a> <span data-ttu-id="b1eb7-192">SQL Server Profiler 和 FileTable</span><span class="sxs-lookup"><span data-stu-id="b1eb7-192">SQL Server Profiler and FileTables</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b1eb7-193">Profiler 可以在儲存於 FileTable 之檔案的追蹤輸出中，擷取「Windows 檔案開啟」和「檔案關閉」作業。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-193">Profiler can capture the Windows File Open and File Close operations in trace output for files that are stored in a FileTable.</span></span>  
  
##  <a name="auditing-and-filetables"></a><a name="OtherAuditing"></a> <span data-ttu-id="b1eb7-194">稽核和 FileTable</span><span class="sxs-lookup"><span data-stu-id="b1eb7-194">Auditing and FileTables</span></span>  
 <span data-ttu-id="b1eb7-195">您可以稽核 FileTable，就像其他任何資料表一樣。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-195">FileTable can be audited just like any other table.</span></span> <span data-ttu-id="b1eb7-196">但是，不會根據作業來設定 Win32 存取模式。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-196">Howerver, Win32 access patterns are not set based operations.</span></span> <span data-ttu-id="b1eb7-197">檔案系統中的單一動作會轉譯成多個 Transact-SQL DML 作業。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-197">A single action in the file system translates into multiple Transact-SQL DML operations.</span></span> <span data-ttu-id="b1eb7-198">例如，在 Microsoft Word 中開啟檔案會轉譯成多個開啟/關閉/建立/重新命名/刪除作業及對應的 Transact-SQL DML 活動。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-198">For example, opening a file in Microsoft Word translates into multiple open/close/create/rename/delete operations and corresponding Transact-SQL DML activities.</span></span> <span data-ttu-id="b1eb7-199">這會產生詳細稽核記錄，這種記錄很難將檔案系統動作與對應 Transact-SQL DML 稽核記錄之間的記錄產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-199">This results in verbose audit records where it is hard to correlate records between file system actions and corresponding Transact-SQL DML audit records.</span></span>  
  
##  <a name="dbcc-and-filetables"></a><a name="OtherDBCC"></a> <span data-ttu-id="b1eb7-200">DBCC 和 FileTable</span><span class="sxs-lookup"><span data-stu-id="b1eb7-200">DBCC and FileTables</span></span>  
 <span data-ttu-id="b1eb7-201">您可以使用 DBCC CHECKCONSTRAINTS 來驗證 FileTable 上的條件約束，包括系統定義的條件約束。</span><span class="sxs-lookup"><span data-stu-id="b1eb7-201">You can use DBCC CHECKCONSTRAINTS to validate the constraints on a FileTable including system-defined constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1eb7-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1eb7-202">See Also</span></span>  
 <span data-ttu-id="b1eb7-203">[FileTable 與其他 SQL Server 功能的相容性](filetable-compatibility-with-other-sql-server-features.md) </span><span class="sxs-lookup"><span data-stu-id="b1eb7-203">[FileTable Compatibility with Other SQL Server Features](filetable-compatibility-with-other-sql-server-features.md) </span></span>  
 [<span data-ttu-id="b1eb7-204">FileTable DDL、函數、預存程序及檢視</span><span class="sxs-lookup"><span data-stu-id="b1eb7-204">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
  
  
