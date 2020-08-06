---
title: 壓縮檔案 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkfile.f1
helpviewer_keywords:
- shrinking files
- decreasing file size
- databases [SQL Server], shrinking
- reducing file size
- size [SQL Server], files
- file size [SQL Server]
ms.assetid: ce5c8798-c039-4ab2-81e7-90a8d688b893
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac69e4bd2db3ef7fe0815d235dd1de7d3396b302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686970"
---
# <a name="shrink-a-file"></a><span data-ttu-id="433cc-102">壓縮檔案</span><span class="sxs-lookup"><span data-stu-id="433cc-102">Shrink a File</span></span>
  <span data-ttu-id="433cc-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中壓縮資料或記錄檔。</span><span class="sxs-lookup"><span data-stu-id="433cc-103">This topic describes how to shrink a data or log file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="433cc-104">將資料頁面從檔案結尾移到靠近檔案前端的未使用空間，以壓縮資料並復原儲存空間。</span><span class="sxs-lookup"><span data-stu-id="433cc-104">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="433cc-105">當檔案結尾建立了足夠的可用空間後，檔案結尾的資料頁面便可取消配置並返回檔案系統。</span><span class="sxs-lookup"><span data-stu-id="433cc-105">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
 <span data-ttu-id="433cc-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="433cc-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="433cc-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="433cc-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="433cc-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="433cc-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="433cc-109">建議</span><span class="sxs-lookup"><span data-stu-id="433cc-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="433cc-110">安全性</span><span class="sxs-lookup"><span data-stu-id="433cc-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="433cc-111">**使用下列方法壓縮資料或記錄檔：**</span><span class="sxs-lookup"><span data-stu-id="433cc-111">**To shrink a data or log file, using:**</span></span>  
  
     [<span data-ttu-id="433cc-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="433cc-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="433cc-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="433cc-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="433cc-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="433cc-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="433cc-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="433cc-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="433cc-116">主要資料檔無法縮到小於 model 資料庫中主要資料檔的大小。</span><span class="sxs-lookup"><span data-stu-id="433cc-116">The primary data file cannot be made smaller than the size of the primary file in the model database.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="433cc-117">建議</span><span class="sxs-lookup"><span data-stu-id="433cc-117">Recommendations</span></span>  
  
-   <span data-ttu-id="433cc-118">為壓縮檔案所移動的資料可散佈至檔案中的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="433cc-118">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="433cc-119">如此會造成索引片段，並可能導致大範圍之索引搜尋的查詢效能變慢。</span><span class="sxs-lookup"><span data-stu-id="433cc-119">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="433cc-120">若要消除資料片段，可考慮在壓縮之後重建該檔案的索引。</span><span class="sxs-lookup"><span data-stu-id="433cc-120">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="433cc-121">Security</span><span class="sxs-lookup"><span data-stu-id="433cc-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="433cc-122">權限</span><span class="sxs-lookup"><span data-stu-id="433cc-122">Permissions</span></span>  
 <span data-ttu-id="433cc-123">需要 **系統管理員** 固定伺服器角色或 **db_owner** 固定資料庫角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="433cc-123">Requires membership in the **sysadmin** fixed server role or the **db_owner** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="433cc-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="433cc-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-shrink-a-data-or-log-file"></a><span data-ttu-id="433cc-125">若要壓縮資料檔或記錄檔</span><span class="sxs-lookup"><span data-stu-id="433cc-125">To shrink a data or log file</span></span>  
  
1.  <span data-ttu-id="433cc-126">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="433cc-126">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="433cc-127">展開 **[資料庫]** ，然後以滑鼠右鍵按一下您要壓縮的資料庫。</span><span class="sxs-lookup"><span data-stu-id="433cc-127">Expand **Databases** and then right-click the database that you want to shrink.</span></span>  
  
3.  <span data-ttu-id="433cc-128">指向 **[工作]** ，指向 **[壓縮]** ，然後按一下 **[檔案]** 。</span><span class="sxs-lookup"><span data-stu-id="433cc-128">Point to **Tasks**, point to **Shrink**, and then click **Files**.</span></span>  
  
     <span data-ttu-id="433cc-129">**Database**</span><span class="sxs-lookup"><span data-stu-id="433cc-129">**Database**</span></span>  
     <span data-ttu-id="433cc-130">顯示選取之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="433cc-130">Displays the name of the selected database.</span></span>  
  
     <span data-ttu-id="433cc-131">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="433cc-131">**File type**</span></span>  
     <span data-ttu-id="433cc-132">選取檔案的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="433cc-132">Select the file type for the file.</span></span> <span data-ttu-id="433cc-133">可用的選擇為 **[資料]** 與 **[記錄]** 檔案。</span><span class="sxs-lookup"><span data-stu-id="433cc-133">The available choices are **Data** and **Log** files.</span></span> <span data-ttu-id="433cc-134">預設的選取項目為 **[資料]** 。</span><span class="sxs-lookup"><span data-stu-id="433cc-134">The default selection is **Data**.</span></span> <span data-ttu-id="433cc-135">若選取不同的檔案群組類型，就會變更其他欄位中的選取項目。</span><span class="sxs-lookup"><span data-stu-id="433cc-135">Selecting a different filegroup type changes the selections in the other fields accordingly.</span></span>  
  
     <span data-ttu-id="433cc-136">**檔案群組**</span><span class="sxs-lookup"><span data-stu-id="433cc-136">**Filegroup**</span></span>  
     <span data-ttu-id="433cc-137">從與上面選取之 **[檔案類型]** 相關聯的檔案群組清單中選取檔案群組。</span><span class="sxs-lookup"><span data-stu-id="433cc-137">Select a filegroup from the list of Filegroups associated with the selected **File type** above.</span></span> <span data-ttu-id="433cc-138">若選取不同的檔案群組，就會變更其他欄位中的選取項目。</span><span class="sxs-lookup"><span data-stu-id="433cc-138">Selecting a different filegroup changes the selections in the other fields accordingly.</span></span>  
  
     <span data-ttu-id="433cc-139">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="433cc-139">**File name**</span></span>  
     <span data-ttu-id="433cc-140">從選取的檔案群組與檔案類型的可用檔案清單中選取檔案。</span><span class="sxs-lookup"><span data-stu-id="433cc-140">Select a file from the list of available files of the selected filegroup and file type.</span></span>  
  
     <span data-ttu-id="433cc-141">**位置**</span><span class="sxs-lookup"><span data-stu-id="433cc-141">**Location**</span></span>  
     <span data-ttu-id="433cc-142">顯示目前選取之檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="433cc-142">Displays the full path to the currently selected file.</span></span> <span data-ttu-id="433cc-143">無法編輯路徑，但是可以將它複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="433cc-143">The path is not editable, but it can be copied to the clipboard.</span></span>  
  
     <span data-ttu-id="433cc-144">**目前配置的空間**</span><span class="sxs-lookup"><span data-stu-id="433cc-144">**Currently allocated space**</span></span>  
     <span data-ttu-id="433cc-145">若要資料檔，則顯示目前配置的空間。</span><span class="sxs-lookup"><span data-stu-id="433cc-145">For data files, displays the current allocated space.</span></span> <span data-ttu-id="433cc-146">針對記錄檔，顯示從 DBCC SQLPERF(LOGSPACE) 的輸出計算而來的目前配置空間。</span><span class="sxs-lookup"><span data-stu-id="433cc-146">For log files, displays the current allocated space computed from the output of DBCC SQLPERF(LOGSPACE).</span></span>  
  
     <span data-ttu-id="433cc-147">**可用空間**</span><span class="sxs-lookup"><span data-stu-id="433cc-147">**Available free space**</span></span>  
     <span data-ttu-id="433cc-148">針對資料檔，顯示從 DBCC SHOWFILESTATS(fileid) 的輸出計算而來的目前可用空間。</span><span class="sxs-lookup"><span data-stu-id="433cc-148">For data files, displays the current available free space computed from the output of DBCC SHOWFILESTATS(fileid).</span></span> <span data-ttu-id="433cc-149">針對記錄檔，顯示從 DBCC SQLPERF(LOGSPACE) 的輸出計算而來的目前可用空間。</span><span class="sxs-lookup"><span data-stu-id="433cc-149">For log files, displays the current available free space computed from the output of DBCC SQLPERF(LOGSPACE).</span></span>  
  
     <span data-ttu-id="433cc-150">**釋放未使用的空間**</span><span class="sxs-lookup"><span data-stu-id="433cc-150">**Release unused space**</span></span>  
     <span data-ttu-id="433cc-151">使檔案中未使用的空間釋出至作業系統，並壓縮檔案至最後配置的範圍，縮減檔案大小而不移動任何資料。</span><span class="sxs-lookup"><span data-stu-id="433cc-151">Cause any unused space in the files to be released to the operating system and shrink the file to the last allocated extent, reducing the file size without moving any data.</span></span> <span data-ttu-id="433cc-152">未嘗試重新放置資料列給未配置的頁面。</span><span class="sxs-lookup"><span data-stu-id="433cc-152">No attempt is made to relocate rows to unallocated pages.</span></span>  
  
     <span data-ttu-id="433cc-153">**釋放未使用的空間之前，先重新組織頁面**</span><span class="sxs-lookup"><span data-stu-id="433cc-153">**Reorganize pages before releasing unused space**</span></span>  
     <span data-ttu-id="433cc-154">相當於執行指定目標檔案大小的 DBCC SHRINKFILE。</span><span class="sxs-lookup"><span data-stu-id="433cc-154">Equivalent to executing DBCC SHRINKFILE specifying the target file size.</span></span> <span data-ttu-id="433cc-155">選取此選項時，使用者必須在 **[將檔案壓縮為]** 方塊中指定目標檔案大小。</span><span class="sxs-lookup"><span data-stu-id="433cc-155">When this option is selected, the user must specify a target file size in the **Shrink file to** box.</span></span>  
  
     <span data-ttu-id="433cc-156">**[將檔案壓縮為]**</span><span class="sxs-lookup"><span data-stu-id="433cc-156">**Shrink file to**</span></span>  
     <span data-ttu-id="433cc-157">指定壓縮作業的目標檔案大小。</span><span class="sxs-lookup"><span data-stu-id="433cc-157">Specifies the target file size for the shrink operation.</span></span> <span data-ttu-id="433cc-158">此大小不可小於目前配置的空間或大於配置給檔案的總範圍。</span><span class="sxs-lookup"><span data-stu-id="433cc-158">The size cannot be less than the current allocated space or more than the total extents allocated to the file.</span></span> <span data-ttu-id="433cc-159">一旦變更焦點或按一下工具列上的任何按鈕時，輸入超過下限或上限的值將還原為下限或上限。</span><span class="sxs-lookup"><span data-stu-id="433cc-159">Entering a value beyond the minimum or the maximum will revert to the min or the max once the focus is changed or when any of the buttons on the toolbar are clicked.</span></span>  
  
     <span data-ttu-id="433cc-160">**將資料移轉至同一檔案群組中的其他檔案，以清空檔案**</span><span class="sxs-lookup"><span data-stu-id="433cc-160">**Empty file by migrating the data to other files in the same filegroup**</span></span>  
     <span data-ttu-id="433cc-161">移轉來自指定之檔案的所有資料。</span><span class="sxs-lookup"><span data-stu-id="433cc-161">Migrate all data from the specified file.</span></span> <span data-ttu-id="433cc-162">這個選項允許檔案使用 ALTER DATABASE 陳述式卸除。</span><span class="sxs-lookup"><span data-stu-id="433cc-162">This option allows the file to be dropped using the ALTER DATABASE statement.</span></span> <span data-ttu-id="433cc-163">此選項相當於執行具有 EMPTYFILE 選項的 DBCC SHRINKFILE。</span><span class="sxs-lookup"><span data-stu-id="433cc-163">This option is equivalent to executing DBCC SHRINKFILE with the EMPTYFILE option.</span></span>  
  
4.  <span data-ttu-id="433cc-164">選取檔案類型與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="433cc-164">Select the file type and file name.</span></span>  
  
5.  <span data-ttu-id="433cc-165">(選擇性) 選取 **[釋放未使用的空間]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="433cc-165">Optionally, select the **Release unused space** check box.</span></span>  
  
     <span data-ttu-id="433cc-166">選取此選項，會讓檔案中任何未使用的空間釋出到作業系統，並壓縮文件到最後的配置範圍。</span><span class="sxs-lookup"><span data-stu-id="433cc-166">Selecting this option causes any unused space in the file to be released to the operating system and shrinks the file to the last allocated extent.</span></span> <span data-ttu-id="433cc-167">如此一來無需移動任何資料即可縮減檔案大小。</span><span class="sxs-lookup"><span data-stu-id="433cc-167">This reduces the file size without moving any data.</span></span>  
  
6.  <span data-ttu-id="433cc-168">(選擇性) 選取 **[釋放未使用空間之前重新組織檔案]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="433cc-168">Optionally, select the **Reorganize files before releasing unused space** check box.</span></span> <span data-ttu-id="433cc-169">若選取此選項，則必須在 **[將檔案壓縮為]** 中指定一個值。</span><span class="sxs-lookup"><span data-stu-id="433cc-169">If this is selected, the **Shrink file to** value must be specified.</span></span> <span data-ttu-id="433cc-170">根據預設，會清除此選項。</span><span class="sxs-lookup"><span data-stu-id="433cc-170">By default, the option is cleared.</span></span>  
  
     <span data-ttu-id="433cc-171">選取此選項，會讓檔案中任何未使用的空間釋出到作業系統，並嘗試將資料列重新放置到未配置的資料頁。</span><span class="sxs-lookup"><span data-stu-id="433cc-171">Selecting this option causes any unused space in the file to be released to the operating system and tries to relocate rows to unallocated pages.</span></span>  
  
7.  <span data-ttu-id="433cc-172">(選擇性) 輸入資料庫壓縮後資料庫檔案中最大的可用剩餘空間百分比。</span><span class="sxs-lookup"><span data-stu-id="433cc-172">Optionally, enter the maximum percentage of free space to be left in the database file after the database has been shrunk.</span></span> <span data-ttu-id="433cc-173">允許值介於 0 和 99 之間。</span><span class="sxs-lookup"><span data-stu-id="433cc-173">Permissible values are between 0 and 99.</span></span> <span data-ttu-id="433cc-174">只有當啟用 **[釋放未使用空間之前重新組織檔案]** 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="433cc-174">This option is only available when **Reorganize files before releasing unused space** is enabled.</span></span>  
  
8.  <span data-ttu-id="433cc-175">(選擇性) 選取 **[將資料移轉至同一檔案群組中的其他檔案，以清空檔案]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="433cc-175">Optionally, select the **Empty file by migrating the data to other files in the same filegroup** check box.</span></span>  
  
     <span data-ttu-id="433cc-176">選取此選項，使檔案群組中指定檔案內的所有資料都移到其他檔案內。</span><span class="sxs-lookup"><span data-stu-id="433cc-176">Selecting this option moves all data from the specified file to other files in the filegroup.</span></span> <span data-ttu-id="433cc-177">然後即可刪除空白檔案。</span><span class="sxs-lookup"><span data-stu-id="433cc-177">The empty file can then be deleted.</span></span> <span data-ttu-id="433cc-178">這個選項的作用與使用 EMPTYFILE 選項執行 DBCC SHRINKFILE 的作用相同。</span><span class="sxs-lookup"><span data-stu-id="433cc-178">This option is the same as executing DBCC SHRINKFILE with the EMPTYFILE option.</span></span>  
  
9. <span data-ttu-id="433cc-179">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="433cc-179">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="433cc-180">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="433cc-180">Using Transact-SQL</span></span>  
  
#### <a name="to-shrink-a-data-or-log-file"></a><span data-ttu-id="433cc-181">若要壓縮資料檔或記錄檔</span><span class="sxs-lookup"><span data-stu-id="433cc-181">To shrink a data or log file</span></span>  
  
1.  <span data-ttu-id="433cc-182">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="433cc-182">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="433cc-183">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="433cc-183">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="433cc-184">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="433cc-184">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="433cc-185">下列範例會使用 [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) ，將 `UserDB` 資料庫中名為 `DataFile1` 之資料檔大小壓縮成 7 MB。</span><span class="sxs-lookup"><span data-stu-id="433cc-185">This example uses [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) to shrink the size of a data file named `DataFile1` in the `UserDB` database to 7 MB.</span></span>  
  
 [!code-sql[DBCC#DBCC_SHRINKFILE1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkfile1)]  
  
## <a name="see-also"></a><span data-ttu-id="433cc-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="433cc-186">See Also</span></span>  
 <span data-ttu-id="433cc-187">[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="433cc-187">[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) </span></span>  
 <span data-ttu-id="433cc-188">[壓縮資料庫](shrink-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="433cc-188">[Shrink a Database](shrink-a-database.md) </span></span>  
 <span data-ttu-id="433cc-189">[刪除資料庫的資料或記錄檔](delete-data-or-log-files-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="433cc-189">[Delete Data or Log Files from a Database](delete-data-or-log-files-from-a-database.md) </span></span>  
 <span data-ttu-id="433cc-190">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="433cc-190">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="433cc-191">sys.database_files &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="433cc-191">sys.database_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)  
  
  
