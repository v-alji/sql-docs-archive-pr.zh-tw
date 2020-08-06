---
title: 壓縮資料庫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkdatabase.f1
helpviewer_keywords:
- shrinking databases
- databases [SQL Server], shrinking
- decreasing database size
- database shrinking [SQL Server]
- reducing database size
ms.assetid: 83afbf74-fd50-4c39-831c-b1f473a50620
author: stevestein
ms.author: sstein
ms.openlocfilehash: 246036bfea6dc8431f878165330f7f0571949897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686971"
---
# <a name="shrink-a-database"></a><span data-ttu-id="eb114-102">壓縮資料庫</span><span class="sxs-lookup"><span data-stu-id="eb114-102">Shrink a Database</span></span>
  <span data-ttu-id="eb114-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ， [!INCLUDE[tsql](../../includes/tsql-md.md)]中壓縮資料庫。</span><span class="sxs-lookup"><span data-stu-id="eb114-103">This topic describes how to shrink a database by using Object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="eb114-104">將資料頁面從檔案結尾移到靠近檔案前端的未使用空間，以壓縮資料並復原儲存空間。</span><span class="sxs-lookup"><span data-stu-id="eb114-104">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="eb114-105">當檔案結尾建立了足夠的可用空間後，檔案結尾的資料頁面便可取消配置並返回檔案系統。</span><span class="sxs-lookup"><span data-stu-id="eb114-105">When enough free space is created at the end of the file, data pages at end of the file can be deallocated and returned to the file system.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb114-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="eb114-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eb114-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="eb114-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="eb114-108">資料庫的大小不得小於資料庫的大小下限。</span><span class="sxs-lookup"><span data-stu-id="eb114-108">The database cannot be made smaller than the minimum size of the database.</span></span> <span data-ttu-id="eb114-109">大小下限是最初建立資料庫時所指定的大小，或利用檔案大小變更作業 (如 DBCC SHRINKFILE) 來設定的最後一個明確大小。</span><span class="sxs-lookup"><span data-stu-id="eb114-109">The minimum size is the size specified when the database was originally created, or the last explicit size set by using a file-size-changing operation, such as DBCC SHRINKFILE.</span></span> <span data-ttu-id="eb114-110">例如，如果資料庫最初建立時為 10 MB 的大小，而後擴充到 100 MB，則該資料庫最多只能縮小到 10 MB，即使該資料庫中的所有資料都已刪除，也是如此。</span><span class="sxs-lookup"><span data-stu-id="eb114-110">For example, if a database was originally created with a size of 10 MB and grew to 100 MB, the smallest size the database could be reduced to is 10 MB, even if all the data in the database has been deleted.</span></span>  
  
-   <span data-ttu-id="eb114-111">資料庫在備份時不能進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="eb114-111">You cannot shrink a database while the database is being backed up.</span></span> <span data-ttu-id="eb114-112">相反地，當資料庫上正在進行壓縮作業時，也不能對其進行備份。</span><span class="sxs-lookup"><span data-stu-id="eb114-112">Conversely, you cannot backup a database while a shrink operation on the database is in process.</span></span>  
  
-   <span data-ttu-id="eb114-113">遇到 xVelocity 記憶體最佳化的資料行存放區索引時，DBCC SHRINKDATABASE 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="eb114-113">DBCC SHRINKDATABASE will fail when it encounters an xVelocity memory optimized columnstore index.</span></span> <span data-ttu-id="eb114-114">遇到資料行存放區索引之前完成的工作將會成功，因此資料庫可能會較小。</span><span class="sxs-lookup"><span data-stu-id="eb114-114">Work completed before encountering the columnstore index will succeed so the database might be smaller.</span></span> <span data-ttu-id="eb114-115">若要完成 DBCC SHRINKDATABASE，請在執行 DBCC SHRINKDATABASE 前停用所有資料行存放區索引，然後重建資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="eb114-115">To complete DBCC SHRINKDATABASE, disable all columnstore indexes before executing DBCC SHRINKDATABASE, and then rebuild the columnstore indexes.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="eb114-116">建議</span><span class="sxs-lookup"><span data-stu-id="eb114-116">Recommendations</span></span>  
  
-   <span data-ttu-id="eb114-117">檢視資料庫中目前的可用 (未配置) 空間量。</span><span class="sxs-lookup"><span data-stu-id="eb114-117">To view the current amount of free (unallocated) space in the database.</span></span> <span data-ttu-id="eb114-118">如需相關資訊，請參閱 [顯示資料庫的資料和記錄空間資訊](display-data-and-log-space-information-for-a-database.md)</span><span class="sxs-lookup"><span data-stu-id="eb114-118">For more information, see [Display Data and Log Space Information for a Database](display-data-and-log-space-information-for-a-database.md)</span></span>  
  
-   <span data-ttu-id="eb114-119">當您計畫壓縮資料庫時，請考量下列資訊：</span><span class="sxs-lookup"><span data-stu-id="eb114-119">Consider the following information when you plan to shrink a database:</span></span>  
  
    -   <span data-ttu-id="eb114-120">壓縮作業在截斷資料表或卸除資料表等產生大量未用空間的作業之後最有效。</span><span class="sxs-lookup"><span data-stu-id="eb114-120">A shrink operation is most effective after an operation that creates lots of unused space, such as a truncate table or a drop table operation.</span></span>  
  
    -   <span data-ttu-id="eb114-121">大部分資料庫都需要一些可用空間來執行每天的例行作業。</span><span class="sxs-lookup"><span data-stu-id="eb114-121">Most databases require some free space to be available for regular day-to-day operations.</span></span> <span data-ttu-id="eb114-122">如果您反覆壓縮資料庫，發現資料庫再次增長，就表示例行作業需要被壓縮的空間。</span><span class="sxs-lookup"><span data-stu-id="eb114-122">If you shrink a database repeatedly and notice that the database size grows again, this indicates that the space that was shrunk is required for regular operations.</span></span> <span data-ttu-id="eb114-123">在這些情況之下，反覆壓縮資料庫是一項會造成浪費的作業。</span><span class="sxs-lookup"><span data-stu-id="eb114-123">In these cases, repeatedly shrinking the database is a wasted operation.</span></span>  
  
    -   <span data-ttu-id="eb114-124">壓縮作業不會保留資料庫中索引的片段狀態，它通常會使片段增加到某個程度。</span><span class="sxs-lookup"><span data-stu-id="eb114-124">A shrink operation does not preserve the fragmentation state of indexes in the database, and generally increases fragmentation to a degree.</span></span> <span data-ttu-id="eb114-125">這就是不要反覆壓縮資料庫的另一個原因。</span><span class="sxs-lookup"><span data-stu-id="eb114-125">This is another reason not to repeatedly shrink the database.</span></span>  
  
    -   <span data-ttu-id="eb114-126">除非您有特定的需求，否則請不要將 AUTO_SHRINK 資料庫選項設定為 ON。</span><span class="sxs-lookup"><span data-stu-id="eb114-126">Unless you have a specific requirement, do not set the AUTO_SHRINK database option to ON.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb114-127">Security</span><span class="sxs-lookup"><span data-stu-id="eb114-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eb114-128">權限</span><span class="sxs-lookup"><span data-stu-id="eb114-128">Permissions</span></span>  
 <span data-ttu-id="eb114-129">需要 **系統管理員** 固定伺服器角色或 **db_owner** 固定資料庫角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="eb114-129">Requires membership in the **sysadmin** fixed server role or the **db_owner** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eb114-130">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb114-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-shrink-a-database"></a><span data-ttu-id="eb114-131">若要壓縮資料庫</span><span class="sxs-lookup"><span data-stu-id="eb114-131">To shrink a database</span></span>  
  
1.  <span data-ttu-id="eb114-132">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="eb114-132">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="eb114-133">展開 [資料庫]，然後以滑鼠右鍵按一下您要壓縮的資料庫。</span><span class="sxs-lookup"><span data-stu-id="eb114-133">Expand **Databases**, and then right-click the database that you want to shrink.</span></span>  
  
3.  <span data-ttu-id="eb114-134">指向 **[工作]** 的 **[壓縮]** ，然後按一下 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="eb114-134">Point to **Tasks**, point to **Shrink**, and then click **Database**.</span></span>  
  
     <span data-ttu-id="eb114-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="eb114-135">**Database**</span></span>  
     <span data-ttu-id="eb114-136">顯示選取之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="eb114-136">Displays the name of the selected database.</span></span>  
  
     <span data-ttu-id="eb114-137">**目前配置的空間**</span><span class="sxs-lookup"><span data-stu-id="eb114-137">**Current allocated space**</span></span>  
     <span data-ttu-id="eb114-138">顯示選取之資料庫的總計已使用和未使用的空間。</span><span class="sxs-lookup"><span data-stu-id="eb114-138">Displays the total used and unused space for the selected database.</span></span>  
  
     <span data-ttu-id="eb114-139">**可用空間**</span><span class="sxs-lookup"><span data-stu-id="eb114-139">**Available free space**</span></span>  
     <span data-ttu-id="eb114-140">顯示選取之資料庫的記錄檔和資料檔中可用空間的總和。</span><span class="sxs-lookup"><span data-stu-id="eb114-140">Displays the sum of free space in the log and data files of the selected database.</span></span>  
  
     <span data-ttu-id="eb114-141">**釋放未使用的空間之前，先重新組織檔案**</span><span class="sxs-lookup"><span data-stu-id="eb114-141">**Reorganize files before releasing unused space**</span></span>  
     <span data-ttu-id="eb114-142">選取這個選項相當於執行 DBCC SHRINKDATABASE 指定目標百分比選項。</span><span class="sxs-lookup"><span data-stu-id="eb114-142">Selecting this option is equivalent to executing DBCC SHRINKDATABASE specifying a target percent option.</span></span> <span data-ttu-id="eb114-143">清除此選項相當於搭配 TRUNCATEONLY 選項執行 DBCC SHRINKDATABASE。</span><span class="sxs-lookup"><span data-stu-id="eb114-143">Clearing this option is equivalent to executing DBCC SHRINKDATABASE with TRUNCATEONLY option.</span></span> <span data-ttu-id="eb114-144">依預設，開啟對話方塊時並不會選取此選項。</span><span class="sxs-lookup"><span data-stu-id="eb114-144">By default, this option is not selected when the dialog is opened.</span></span> <span data-ttu-id="eb114-145">如果選取此選項，使用者必須指定目標百分比選項。</span><span class="sxs-lookup"><span data-stu-id="eb114-145">If this option is selected, the user must specify a target percent option.</span></span>  
  
     <span data-ttu-id="eb114-146">**壓縮後檔案的最大可用空間**</span><span class="sxs-lookup"><span data-stu-id="eb114-146">**Maximum free space in files after shrinking**</span></span>  
     <span data-ttu-id="eb114-147">輸入在資料庫壓縮後，資料庫檔案中剩餘可用空間的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="eb114-147">Enter the maximum percentage of free space to be left in the database files after the database has been shrunk.</span></span> <span data-ttu-id="eb114-148">允許值介於 0 和 99 之間。</span><span class="sxs-lookup"><span data-stu-id="eb114-148">Permissible values are between 0 and 99.</span></span>  
  
4.  <span data-ttu-id="eb114-149">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="eb114-149">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eb114-150">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb114-150">Using Transact-SQL</span></span>  
  
#### <a name="to-shrink-a-database"></a><span data-ttu-id="eb114-151">若要壓縮資料庫</span><span class="sxs-lookup"><span data-stu-id="eb114-151">To shrink a database</span></span>  
  
1.  <span data-ttu-id="eb114-152">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eb114-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb114-153">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="eb114-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb114-154">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="eb114-154">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="eb114-155">這個範例會使用 [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) 縮小 `UserDB` 資料庫中的資料和記錄檔大小，使資料庫中能有 `10` % 的可用空間。</span><span class="sxs-lookup"><span data-stu-id="eb114-155">This example uses [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) to decreases the size of the data and log files in the `UserDB` database and to allow for `10` percent free space in the database.</span></span>  
  
 [!code-sql[DBCC#DBCC_SHRINKDB1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkdb1)]  
  
##  <a name="follow-up-after-you-shrink-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="eb114-156">後續操作：壓縮資料庫之後</span><span class="sxs-lookup"><span data-stu-id="eb114-156">Follow Up: After you shrink a database</span></span>  
 <span data-ttu-id="eb114-157">為壓縮檔案所移動的資料可散佈至檔案中的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="eb114-157">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="eb114-158">如此會造成索引片段，並可能導致大範圍之索引搜尋的查詢效能變慢。</span><span class="sxs-lookup"><span data-stu-id="eb114-158">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="eb114-159">若要消除資料片段，可考慮在壓縮之後重建該檔案的索引。</span><span class="sxs-lookup"><span data-stu-id="eb114-159">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb114-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb114-160">See Also</span></span>  
 <span data-ttu-id="eb114-161">[壓縮檔案](shrink-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="eb114-161">[Shrink a File](shrink-a-file.md) </span></span>  
 <span data-ttu-id="eb114-162">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb114-162">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="eb114-163">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb114-163">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="eb114-164">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb114-164">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span></span>  
 <span data-ttu-id="eb114-165">[DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb114-165">[DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) </span></span>  
 [<span data-ttu-id="eb114-166">資料庫檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="eb114-166">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
