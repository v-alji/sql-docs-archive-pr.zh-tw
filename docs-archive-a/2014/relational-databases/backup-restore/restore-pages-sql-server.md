---
title: 還原頁面 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restorepage.general.f1
helpviewer_keywords:
- restoring pages [SQL Server]
- pages [SQL Server], restoring
- databases [SQL Server], damaged
- page restores [SQL Server]
- pages [SQL Server], damaged
- restoring [SQL Server], pages
ms.assetid: 07e40950-384e-4d84-9ac5-84da6dd27a91
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6fb008314b9cb156f1cc575bda71b6364eca6e3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698320"
---
# <a name="restore-pages-sql-server"></a><span data-ttu-id="43f65-102">還原頁面 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="43f65-102">Restore Pages (SQL Server)</span></span>
  <span data-ttu-id="43f65-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]，在  中還原頁面。</span><span class="sxs-lookup"><span data-stu-id="43f65-103">This topic describes how to restore pages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="43f65-104">分頁還原的目標是還原一個或多個受損頁面而毋需還原整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="43f65-104">The goal of a page restore is to restore one or more damaged pages without restoring the whole database.</span></span> <span data-ttu-id="43f65-105">一般而言，選定要還原的頁面會標示為「有疑問」，因為存取該頁面時發生問題。</span><span class="sxs-lookup"><span data-stu-id="43f65-105">Typically, pages that are candidates for restore have been marked as "suspect" because of an error that is encountered when accessing the page.</span></span> <span data-ttu-id="43f65-106">有疑問的頁面是在 [msdb](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 資料庫的 **suspect_pages** 資料表中識別。</span><span class="sxs-lookup"><span data-stu-id="43f65-106">Suspect pages are identified in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="43f65-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="43f65-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="43f65-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="43f65-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="43f65-109">頁面還原何時有用？</span><span class="sxs-lookup"><span data-stu-id="43f65-109">When is a Page Restore Useful?</span></span>](#WhenUseful)  
  
     [<span data-ttu-id="43f65-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="43f65-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="43f65-111">建議</span><span class="sxs-lookup"><span data-stu-id="43f65-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="43f65-112">安全性</span><span class="sxs-lookup"><span data-stu-id="43f65-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="43f65-113">**若要使用下列項目還原頁面：**</span><span class="sxs-lookup"><span data-stu-id="43f65-113">**To restore pages, using:**</span></span>  
  
     [<span data-ttu-id="43f65-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="43f65-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="43f65-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="43f65-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="43f65-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="43f65-116">Before You Begin</span></span>  
  
###  <a name="when-is-a-page-restore-useful"></a><a name="WhenUseful"></a> <span data-ttu-id="43f65-117">頁面還原何時有用？</span><span class="sxs-lookup"><span data-stu-id="43f65-117">When is a Page Restore Useful?</span></span>  
 <span data-ttu-id="43f65-118">頁面還原主要是用來修復隔離的損毀頁面。</span><span class="sxs-lookup"><span data-stu-id="43f65-118">A page restore is intended for repairing isolated damaged pages.</span></span> <span data-ttu-id="43f65-119">還原和復原少數個別頁面可能比檔案還原更快，可以減少還原作業期間離線的資料量。</span><span class="sxs-lookup"><span data-stu-id="43f65-119">Restoring and recovering a few individual pages might be faster than a file restore, reducing the amount of data that is offline during a restore operation.</span></span> <span data-ttu-id="43f65-120">不過，如果不只是要還原一個檔案中的幾個頁面，則還原整個檔案，通常更有效率。</span><span class="sxs-lookup"><span data-stu-id="43f65-120">However, if you have to restore more than a few pages in a file, it is generally more efficient to restore the whole file.</span></span> <span data-ttu-id="43f65-121">例如，如果在裝置上有很多頁面指出有暫止的裝置失敗，請考慮還原檔案，可能要還原至另一個位置，然後修復該裝置。</span><span class="sxs-lookup"><span data-stu-id="43f65-121">For example, if lots of pages on a device indicate a pending device failure, consider restoring the file, possibly to another location, and repairing the device.</span></span>  
  
 <span data-ttu-id="43f65-122">此外，並非所有頁面錯誤都需要還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-122">Furthermore, not all page errors require a restore.</span></span> <span data-ttu-id="43f65-123">快取資料 (如次要索引) 可能會發生問題，只要重新計算資料就可解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="43f65-123">A problem can occur in cached data, such as a secondary index, that can be resolved by recalculating the data.</span></span> <span data-ttu-id="43f65-124">例如，如果資料庫管理員卸除並重建次要索引，則儘管已修正損毀資料，也不會在 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 資料表中指明為已修正。</span><span class="sxs-lookup"><span data-stu-id="43f65-124">For example, if the database administrator drops a secondary index and rebuilds it, the corrupted data, although fixed, is not indicated as such in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="43f65-125">限制事項</span><span class="sxs-lookup"><span data-stu-id="43f65-125">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="43f65-126">頁面還原適用於使用完整或大量記錄復原模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="43f65-126">Page restore applies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span> <span data-ttu-id="43f65-127">分頁還原只支援讀取/寫入檔案群組。</span><span class="sxs-lookup"><span data-stu-id="43f65-127">Page restore is supported only for read/write filegroups.</span></span>  
  
-   <span data-ttu-id="43f65-128">只能還原資料庫頁面。</span><span class="sxs-lookup"><span data-stu-id="43f65-128">Only database pages can be restored.</span></span> <span data-ttu-id="43f65-129">您無法使用分頁還原來還原下列項目：</span><span class="sxs-lookup"><span data-stu-id="43f65-129">Page restore cannot be used to restore the following:</span></span>  
  
    -   <span data-ttu-id="43f65-130">交易記錄</span><span class="sxs-lookup"><span data-stu-id="43f65-130">Transaction log</span></span>  
  
    -   <span data-ttu-id="43f65-131">配置頁面：全域配置對應 (Global Allocation Map，GAM) 頁面、共用全域配置對應 (Shared Global Allocation Map，SGAM) 頁面，以及頁面可用空間 (Page Free Space，PFS) 頁面。</span><span class="sxs-lookup"><span data-stu-id="43f65-131">Allocation pages: Global Allocation Map (GAM) pages, Shared Global Allocation Map (SGAM) pages, and Page Free Space (PFS) pages.</span></span>  
  
    -   <span data-ttu-id="43f65-132">所有資料檔案的頁面 0 (檔案啟動頁面)</span><span class="sxs-lookup"><span data-stu-id="43f65-132">Page 0 of all data files (the file boot page)</span></span>  
  
    -   <span data-ttu-id="43f65-133">頁面 1:9 (資料庫啟動頁面)</span><span class="sxs-lookup"><span data-stu-id="43f65-133">Page 1:9 (the database boot page)</span></span>  
  
    -   <span data-ttu-id="43f65-134">全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="43f65-134">Full-text catalog</span></span>  
  
-   <span data-ttu-id="43f65-135">對於使用大量記錄復原模式的資料庫，分頁還原具有下列其他條件：</span><span class="sxs-lookup"><span data-stu-id="43f65-135">For a database that uses the bulk-logged recovery model, page restore has the following additional conditions:</span></span>  
  
    -   <span data-ttu-id="43f65-136">對於大量記錄資料而言，在檔案群組或分頁資料離線時進行備份會有問題，因為離線的資料並未記錄在記錄中。</span><span class="sxs-lookup"><span data-stu-id="43f65-136">Backing up while filegroup or page data is offline is problematic for bulk-logged data, because the offline data is not recorded in the log.</span></span> <span data-ttu-id="43f65-137">任何離線頁面都可以阻止備份記錄。</span><span class="sxs-lookup"><span data-stu-id="43f65-137">Any offline page can prevent backing up the log.</span></span> <span data-ttu-id="43f65-138">在此情況下，請考慮使用 DBCC REPAIR，因為這可能會讓資料損失比還原最近備份還少。</span><span class="sxs-lookup"><span data-stu-id="43f65-138">In this cases, consider using DBCC REPAIR, because this might cause less data loss than restoring to the most recent backup.</span></span>  
  
    -   <span data-ttu-id="43f65-139">除非指定 WITH CONTINUE_AFTER_ERROR，否則大量記錄資料庫的記錄備份遇到損壞的分頁時會失敗。</span><span class="sxs-lookup"><span data-stu-id="43f65-139">If a log backup of a bulk-logged database encounters a bad page, it fails unless WITH CONTINUE_AFTER_ERROR is specified.</span></span>  
  
    -   <span data-ttu-id="43f65-140">一般來說，分頁還原不適合用於大量記錄復原。</span><span class="sxs-lookup"><span data-stu-id="43f65-140">Page restore generally does not work with bulk-logged recovery.</span></span>  
  
         <span data-ttu-id="43f65-141">執行分頁還原的最佳作法是將資料庫設定為完整復原模式，並嘗試記錄備份。</span><span class="sxs-lookup"><span data-stu-id="43f65-141">A best practice for performing page restore is to set the database to the full recovery model, and try a log backup.</span></span> <span data-ttu-id="43f65-142">如果記錄備份有效，您就可以進行分頁還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-142">If the log backup works, you can continue with the page restore.</span></span> <span data-ttu-id="43f65-143">如果記錄備份失敗，您會失去自從前次記錄備份之後的工作，或必須試著執行 DBCC，且必須搭配 REPAIR_ALLOW_DATA_LOSS 選項來執行。</span><span class="sxs-lookup"><span data-stu-id="43f65-143">If the log backup fails, you either have to lose work since the previous log backup or you have to try running DBCC must be run with the REPAIR_ALLOW_DATA_LOSS option.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="43f65-144">建議</span><span class="sxs-lookup"><span data-stu-id="43f65-144">Recommendations</span></span>  
  
-   <span data-ttu-id="43f65-145">頁面還原案例：</span><span class="sxs-lookup"><span data-stu-id="43f65-145">Page restore scenarios:</span></span>  
  
     <span data-ttu-id="43f65-146">離線分頁還原</span><span class="sxs-lookup"><span data-stu-id="43f65-146">Offline page restore</span></span>  
     <span data-ttu-id="43f65-147">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本都支援在資料庫離線時還原頁面。</span><span class="sxs-lookup"><span data-stu-id="43f65-147">All editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support restoring pages when the database is offline.</span></span> <span data-ttu-id="43f65-148">在離線頁面還原中，還原受損的頁面時資料庫是離線狀態。</span><span class="sxs-lookup"><span data-stu-id="43f65-148">In an offline page restore, the database is offline while damaged pages are restored.</span></span> <span data-ttu-id="43f65-149">在還原順序結束後，資料庫會恢復上線。</span><span class="sxs-lookup"><span data-stu-id="43f65-149">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="43f65-150">線上頁面還原</span><span class="sxs-lookup"><span data-stu-id="43f65-150">Online page restore</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="43f65-151">Enterprise Edition 支援線上頁面還原，但是當資料庫目前離線時，該版本會使用離線還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-151">Enterprise edition supports online page restores, though they use offline restore if the database is currently offline.</span></span> <span data-ttu-id="43f65-152">在大部分情況下，損毀的頁面可以在資料庫保持上線時還原，包括正進行還原頁面的檔案群組在內。</span><span class="sxs-lookup"><span data-stu-id="43f65-152">In most cases, a damaged page can be restored while the database remains online, including the filegroup to which a page is being restored.</span></span> <span data-ttu-id="43f65-153">即使有一個或多個次要檔案群組離線，只要主要檔案群組還在線上，通常就會在線上執行頁面還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-153">When the primary filegroup is online, even if one or more of its secondary filegroups are offline, page restores are usually performed online.</span></span> <span data-ttu-id="43f65-154">但是，偶爾損毀的頁面可能需要進行離線還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-154">Occasionally, however, a damaged page can require an offline restore.</span></span> <span data-ttu-id="43f65-155">例如，一些重要頁面損毀可能會讓資料庫無法啟動。</span><span class="sxs-lookup"><span data-stu-id="43f65-155">For example, damage to certain critical pages might prevent the database from starting.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="43f65-156">若受損的頁面正在儲存重要資料庫中繼資料，則在嘗試線上頁面還原時，中繼資料的必要更新可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="43f65-156">If damaged pages are storing critical database metadata, required updates to metadata might fail during an online page restore attempt.</span></span> <span data-ttu-id="43f65-157">在此情況下，您可以執行離線頁面還原，但是您必須先建立 [結尾記錄備份](tail-log-backups-sql-server.md) (使用 RESTORE WITH NORECOVERY 來備份交易記錄)。</span><span class="sxs-lookup"><span data-stu-id="43f65-157">In this case, you can perform an offline page restore, but first you must create a [tail log backup](tail-log-backups-sql-server.md) (by backing up the transaction log using RESTORE WITH NORECOVERY).</span></span>  
  
-   <span data-ttu-id="43f65-158">線上分頁還原會利用改良的頁面層級錯誤報告 (包括頁面總和檢查碼) 和追蹤。</span><span class="sxs-lookup"><span data-stu-id="43f65-158">Page restore takes advantage of the improved page-level error reporting (including page checksums) and tracking.</span></span> <span data-ttu-id="43f65-159">因總和檢查碼或寫入損壞偵測為損毀的頁面 (「損毀頁面」 ) 可由頁面還原作業加以還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-159">Pages that are detected as corrupted by check-summing or a torn write, *damaged pages*, can be restored by a page restore operation.</span></span> <span data-ttu-id="43f65-160">只有明確指定的頁面才會還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-160">Only explicitly specified pages are restored.</span></span> <span data-ttu-id="43f65-161">每一個指定的頁面都是由指定之資料備份中該頁面的複本所取代。</span><span class="sxs-lookup"><span data-stu-id="43f65-161">Each specified page is replaced by the copy of that page from the specified data backup.</span></span>  
  
     <span data-ttu-id="43f65-162">當您還原後續的記錄備份時，這些備份只會套用到至少包含一個正在復原之頁面的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="43f65-162">When you restore the subsequent log backups, they are applied only to database files that contain at least one page that is being recovered.</span></span> <span data-ttu-id="43f65-163">必須套用未中斷的記錄備份鏈結至最後一個完整或差異還原，將包含該頁面的檔案群組向前帶到目前的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="43f65-163">An unbroken chain of log backups must be applied to the last full or differential restore to bring the filegroup that contains the page forward to the current log file.</span></span> <span data-ttu-id="43f65-164">在檔案還原中，向前復原集會以單一記錄重做行程向前進行。</span><span class="sxs-lookup"><span data-stu-id="43f65-164">As in a file restore, the roll forward set is advanced with a single log redo pass.</span></span> <span data-ttu-id="43f65-165">頁面還原若要成功，還原的頁面必須復原到與資料庫一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="43f65-165">For a page restore to succeed, the restored pages must be recovered to a state consistent with the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="43f65-166">Security</span><span class="sxs-lookup"><span data-stu-id="43f65-166">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="43f65-167">權限</span><span class="sxs-lookup"><span data-stu-id="43f65-167">Permissions</span></span>  
 <span data-ttu-id="43f65-168">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="43f65-168">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="43f65-169">如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。</span><span class="sxs-lookup"><span data-stu-id="43f65-169">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="43f65-170">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="43f65-170">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="43f65-171">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="43f65-171">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="43f65-172">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="43f65-172">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="43f65-173">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 開始， 就會支援頁面還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-173">Starting in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports page restores.</span></span>  
  
#### <a name="to-restore-pages"></a><span data-ttu-id="43f65-174">若要還原頁面</span><span class="sxs-lookup"><span data-stu-id="43f65-174">To restore pages</span></span>  
  
1.  <span data-ttu-id="43f65-175">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]連接到適當的  執行個體，然後在 [物件總管] 中，按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="43f65-175">Connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="43f65-176">展開 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="43f65-176">Expand **Databases**.</span></span> <span data-ttu-id="43f65-177">視資料庫而定，選取使用者資料庫，或者展開 [系統資料庫] ，再選取系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="43f65-177">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="43f65-178">以滑鼠右鍵按一下資料庫，指向 [工作] ，再指向 [還原] ，然後按一下 [頁面] ，這樣會開啟 [還原頁面]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="43f65-178">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Page**, which opens the **Restore Page** dialog box.</span></span>  
  
     <span data-ttu-id="43f65-179">**Restore**</span><span class="sxs-lookup"><span data-stu-id="43f65-179">**Restore**</span></span>  
     <span data-ttu-id="43f65-180">此區段與 [還原資料庫 (一般頁面)](../../integration-services/general-page-of-integration-services-designers-options.md) 上的 **[還原至]** 執行相同功能。</span><span class="sxs-lookup"><span data-stu-id="43f65-180">This section performs the same function as that of **Restore to** on the [Restore Database (General Page)](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
     <span data-ttu-id="43f65-181">**Database**</span><span class="sxs-lookup"><span data-stu-id="43f65-181">**Database**</span></span>  
     <span data-ttu-id="43f65-182">指定要還原的資料庫。</span><span class="sxs-lookup"><span data-stu-id="43f65-182">Specifies the database to restore.</span></span> <span data-ttu-id="43f65-183">您可以輸入新的資料庫，或者從下拉式清單中選取現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="43f65-183">You can enter a new database or select an existing database from the drop-down list.</span></span> <span data-ttu-id="43f65-184"> 清單包含伺服器上的所有資料庫，但不含系統資料庫 **master**和 tempdb。</span><span class="sxs-lookup"><span data-stu-id="43f65-184">The list includes all databases on the server, except the system databases **master** and **tempdb**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="43f65-185">若要還原受密碼保護的備份，必須使用 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="43f65-185">To restore a password-protected backup, you must use the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="43f65-186">**結尾記錄備份**</span><span class="sxs-lookup"><span data-stu-id="43f65-186">**Tail-Log backup**</span></span>  
     <span data-ttu-id="43f65-187">在 [備份裝置]  中輸入或選取檔案名稱，在這個檔案中將會儲存資料庫的結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="43f65-187">Enter or select a file name in **Backup device** where there tail-log backup will be stored for the database.</span></span>  
  
     <span data-ttu-id="43f65-188">**備份組**</span><span class="sxs-lookup"><span data-stu-id="43f65-188">**Backup Sets**</span></span>  
     <span data-ttu-id="43f65-189">此區段顯示參與還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="43f65-189">This section displays the backup sets involved in the restoration.</span></span>  
  
    |<span data-ttu-id="43f65-190">頁首</span><span class="sxs-lookup"><span data-stu-id="43f65-190">Header</span></span>|<span data-ttu-id="43f65-191">值</span><span class="sxs-lookup"><span data-stu-id="43f65-191">Values</span></span>|  
    |------------|------------|  
    |<span data-ttu-id="43f65-192">**名稱**</span><span class="sxs-lookup"><span data-stu-id="43f65-192">**Name**</span></span>|<span data-ttu-id="43f65-193">備份組的名稱。</span><span class="sxs-lookup"><span data-stu-id="43f65-193">The name of the backup set.</span></span>|  
    |<span data-ttu-id="43f65-194">**元件**</span><span class="sxs-lookup"><span data-stu-id="43f65-194">**Component**</span></span>|<span data-ttu-id="43f65-195">備份的元件：**資料庫**、**檔案**或 **\<blank>** (適用於交易記錄)。</span><span class="sxs-lookup"><span data-stu-id="43f65-195">The backed-up component: **Database**, **File**, or **\<blank>** (for transaction logs).</span></span>|  
    |<span data-ttu-id="43f65-196">**型別**</span><span class="sxs-lookup"><span data-stu-id="43f65-196">**Type**</span></span>|<span data-ttu-id="43f65-197">執行的備份類型：[完整]、[差異] 或 [交易記錄]。</span><span class="sxs-lookup"><span data-stu-id="43f65-197">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="43f65-198">**Server**</span><span class="sxs-lookup"><span data-stu-id="43f65-198">**Server**</span></span>|<span data-ttu-id="43f65-199">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行備份作業的  執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="43f65-199">The name of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="43f65-200">**Database**</span><span class="sxs-lookup"><span data-stu-id="43f65-200">**Database**</span></span>|<span data-ttu-id="43f65-201">備份作業中所含的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="43f65-201">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="43f65-202">**位置**</span><span class="sxs-lookup"><span data-stu-id="43f65-202">**Position**</span></span>|<span data-ttu-id="43f65-203">備份組在磁碟區中的位置。</span><span class="sxs-lookup"><span data-stu-id="43f65-203">The position of the backup set in the volume.</span></span>|  
    |<span data-ttu-id="43f65-204">**第一個 LSN**</span><span class="sxs-lookup"><span data-stu-id="43f65-204">**First LSN**</span></span>|<span data-ttu-id="43f65-205">在備份組中第一個交易的記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="43f65-205">The log sequence number (LSN) of the first transaction in the backup set.</span></span> <span data-ttu-id="43f65-206">針對檔案備份為空白。</span><span class="sxs-lookup"><span data-stu-id="43f65-206">Blank for file backups.</span></span>|  
    |<span data-ttu-id="43f65-207">**最後一個 LSN**</span><span class="sxs-lookup"><span data-stu-id="43f65-207">**Last LSN**</span></span>|<span data-ttu-id="43f65-208">在備份組中最後一個交易的記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="43f65-208">The log sequence number (LSN) of the last transaction in the backup set.</span></span> <span data-ttu-id="43f65-209">針對檔案備份為空白。</span><span class="sxs-lookup"><span data-stu-id="43f65-209">Blank for file backups.</span></span>|  
    |<span data-ttu-id="43f65-210">**檢查點 LSN**</span><span class="sxs-lookup"><span data-stu-id="43f65-210">**Checkpoint LSN**</span></span>|<span data-ttu-id="43f65-211">建立備份時最近檢查點的記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="43f65-211">The log sequence number (LSN) of the most recent checkpoint at the time the backup was created.</span></span>|  
    |<span data-ttu-id="43f65-212">**完整 LSN**</span><span class="sxs-lookup"><span data-stu-id="43f65-212">**Full LSN**</span></span>|<span data-ttu-id="43f65-213">最新完整資料庫備份的記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="43f65-213">The log sequence number (LSN) of the most recent full database backup.</span></span>|  
    |<span data-ttu-id="43f65-214">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="43f65-214">**Start Date**</span></span>|<span data-ttu-id="43f65-215">備份作業開始時的日期和時間，會出現在用戶端的地區設定中。</span><span class="sxs-lookup"><span data-stu-id="43f65-215">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="43f65-216">**完成日期**</span><span class="sxs-lookup"><span data-stu-id="43f65-216">**Finish Date**</span></span>|<span data-ttu-id="43f65-217">備份作業完成時的日期和時間，會出現在用戶端的地區設定中。</span><span class="sxs-lookup"><span data-stu-id="43f65-217">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="43f65-218">**大小**</span><span class="sxs-lookup"><span data-stu-id="43f65-218">**Size**</span></span>|<span data-ttu-id="43f65-219">備份組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="43f65-219">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="43f65-220">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="43f65-220">**User Name**</span></span>|<span data-ttu-id="43f65-221">執行備份作業的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="43f65-221">The name of the user who performed the backup operation.</span></span>|  
    |<span data-ttu-id="43f65-222">**到期**</span><span class="sxs-lookup"><span data-stu-id="43f65-222">**Expiration**</span></span>|<span data-ttu-id="43f65-223">備份組過期的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="43f65-223">The date and time the backup set expires.</span></span>|  
  
     <span data-ttu-id="43f65-224"> 按一下 [驗證] 來檢查執行頁面還原作業所需之備份檔案的完整性。</span><span class="sxs-lookup"><span data-stu-id="43f65-224">Click **Verify** to check the integrity of the backup files needed to perform the page restore operation.</span></span>  
  
4.  <span data-ttu-id="43f65-225"> 若要識別損毀頁面，在 **[資料庫]** 方塊中已選取正確的資料庫時，按一下 [檢查資料庫頁面]。</span><span class="sxs-lookup"><span data-stu-id="43f65-225">To identify corrupted pages, with the correct database selected in the **Database** box, click **Check Database Pages**.</span></span> <span data-ttu-id="43f65-226">這是長時間執行的作業。</span><span class="sxs-lookup"><span data-stu-id="43f65-226">This is a long running operation.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="43f65-227">若要還原未損毀的特定頁面，請按一下 [加入]  ，然後輸入要還原之頁面的 [檔案識別碼]  和 [頁面識別碼]  。</span><span class="sxs-lookup"><span data-stu-id="43f65-227">To restore specific pages that are not corrupted, click **Add** and enter the **File ID** and **Page ID** of the pages to be restored.</span></span>  
  
5.  <span data-ttu-id="43f65-228">頁面方格會用來識別要還原的頁面。</span><span class="sxs-lookup"><span data-stu-id="43f65-228">The pages grid is used to identify the pages to be restored.</span></span> <span data-ttu-id="43f65-229">一開始是從 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 系統資料表填入這個方格。</span><span class="sxs-lookup"><span data-stu-id="43f65-229">Initially, this grid is populated from the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) system table.</span></span> <span data-ttu-id="43f65-230"> 若要從方格中加入或移除頁面，請按一下 **[加入]** 或 [移除]。</span><span class="sxs-lookup"><span data-stu-id="43f65-230">To add or remove pages from the grid, click **Add** or **Remove**.</span></span> <span data-ttu-id="43f65-231">如需詳細資訊，請參閱 [管理 suspect_pages 資料表 &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md)，在  中還原頁面。</span><span class="sxs-lookup"><span data-stu-id="43f65-231">For more information, see [Manage the suspect_pages Table &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md).</span></span>  
  
6.  <span data-ttu-id="43f65-232">**[備份組]** 方格會列出預設還原計畫中的備份組。</span><span class="sxs-lookup"><span data-stu-id="43f65-232">The **Backup sets** grid lists the backup sets in the default restore plan.</span></span> <span data-ttu-id="43f65-233">您可以選擇按一下 [確認]，確認備份可讀取而且備份組是完整的，而不需加以還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-233">Optionally, click **Verify** to verify that the backups are readable and that the backup sets are complete, without restoring them.</span></span> <span data-ttu-id="43f65-234">如需詳細資訊，請參閱 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="43f65-234">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
     <span data-ttu-id="43f65-235">**頁面**</span><span class="sxs-lookup"><span data-stu-id="43f65-235">**Pages**</span></span>  
  
7.  <span data-ttu-id="43f65-236">若要還原頁面方格中所列的頁面，請按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="43f65-236">To restore the pages listed in the pages grid, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="43f65-237">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="43f65-237">Using Transact-SQL</span></span>  
 <span data-ttu-id="43f65-238">若要在 RESTORE DATABASE 陳述式中指定頁面，您需要包含該頁面之檔案的檔案識別碼和頁面的頁面識別碼。</span><span class="sxs-lookup"><span data-stu-id="43f65-238">To specify a page in a RESTORE DATABASE statement, you need the file ID of the file containing the page and the page ID of the page.</span></span> <span data-ttu-id="43f65-239">所需語法如下：</span><span class="sxs-lookup"><span data-stu-id="43f65-239">The required syntax is as follows:</span></span>  
  
 `RESTORE DATABASE <database_name>`  
  
 `PAGE = '<file: page> [ ,... n ] ' [ ,... n ]`  
  
 `FROM <backup_device> [ ,... n ]`  
  
 `WITH NORECOVERY`  
  
 <span data-ttu-id="43f65-240">如需 PAGE 選項之參數的詳細資訊，請參閱 [RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="43f65-240">For more information about the parameters of the PAGE option, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span> <span data-ttu-id="43f65-241">如需 RESTORE DATABASE 語法的詳細資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="43f65-241">For more information about the RESTORE DATABASE syntax, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
#### <a name="to-restore-pages"></a><span data-ttu-id="43f65-242">若要還原頁面</span><span class="sxs-lookup"><span data-stu-id="43f65-242">To restore pages</span></span>  
  
1.  <span data-ttu-id="43f65-243">取得要還原之已損壞頁面的頁面識別碼。</span><span class="sxs-lookup"><span data-stu-id="43f65-243">Obtain the page IDs of the damaged pages to be restored.</span></span> <span data-ttu-id="43f65-244">總和檢查碼或分次寫入錯誤會傳回頁面識別碼，提供指定頁面所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="43f65-244">A checksum or torn write error returns page ID, providing the information required for specifying the pages.</span></span> <span data-ttu-id="43f65-245">若要查閱已損壞頁面的頁面識別碼，請使用下列來源：</span><span class="sxs-lookup"><span data-stu-id="43f65-245">To look up page ID of a damaged page, use any of the following sources.</span></span>  
  
    |<span data-ttu-id="43f65-246">頁面識別碼來源</span><span class="sxs-lookup"><span data-stu-id="43f65-246">Source of page ID</span></span>|<span data-ttu-id="43f65-247">主題</span><span class="sxs-lookup"><span data-stu-id="43f65-247">Topic</span></span>|  
    |-----------------------|-----------|  
    |<span data-ttu-id="43f65-248">**msdb..suspect_pages**</span><span class="sxs-lookup"><span data-stu-id="43f65-248">**msdb..suspect_pages**</span></span>|[<span data-ttu-id="43f65-249">管理 suspect_pages 資料表 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="43f65-249">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](manage-the-suspect-pages-table-sql-server.md)|  
    |<span data-ttu-id="43f65-250">錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="43f65-250">Error log</span></span>|[<span data-ttu-id="43f65-251">檢視 SQL Server 錯誤記錄檔 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="43f65-251">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)|  
    |<span data-ttu-id="43f65-252">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="43f65-252">Event traces</span></span>|[<span data-ttu-id="43f65-253">監視及回應事件</span><span class="sxs-lookup"><span data-stu-id="43f65-253">Monitor and Respond to Events</span></span>](../../ssms/agent/monitor-and-respond-to-events.md)|  
    |<span data-ttu-id="43f65-254">DBCC</span><span class="sxs-lookup"><span data-stu-id="43f65-254">DBCC</span></span>|[<span data-ttu-id="43f65-255">DBCC &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43f65-255">DBCC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-transact-sql)|  
    |<span data-ttu-id="43f65-256">WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="43f65-256">WMI provider</span></span>|[<span data-ttu-id="43f65-257">伺服器事件的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="43f65-257">WMI Provider for Server Events Concepts</span></span>](../wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)|  
  
2.  <span data-ttu-id="43f65-258">使用包含該頁面之完整資料庫、檔案或檔案群組備份，開始進行分頁還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-258">Start a page restore with a full database, file, or filegroup backup that contains the page.</span></span> <span data-ttu-id="43f65-259">在 RESTORE DATABASE 陳述式中，使用 PAGE 子句來列出要還原之所有分頁的頁面識別碼。</span><span class="sxs-lookup"><span data-stu-id="43f65-259">In the RESTORE DATABASE statement, use the PAGE clause to list the page IDs of all of the pages to be restored.</span></span>  
  
3.  <span data-ttu-id="43f65-260">套用最新差異</span><span class="sxs-lookup"><span data-stu-id="43f65-260">Apply the most recent differentials .</span></span>  
  
4.  <span data-ttu-id="43f65-261">套用後續的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="43f65-261">Apply the subsequent log backups.</span></span>  
  
5.  <span data-ttu-id="43f65-262">為包含還原頁面之最後一個 LSN 的資料庫建立新的記錄備份，亦即上次進行離線分頁還原的時點。</span><span class="sxs-lookup"><span data-stu-id="43f65-262">Create a new log backup of the database that includes the final LSN of the restored pages, that is, the point at which the last restored page is taken offline.</span></span> <span data-ttu-id="43f65-263">最後一個 LSN (設定為順序中的第一個還原的一部分) 是重做目標 LSN。</span><span class="sxs-lookup"><span data-stu-id="43f65-263">The final LSN, which is set as part of the first restore in the sequence, is the redo target LSN.</span></span> <span data-ttu-id="43f65-264">針對包含頁面的檔案進行線上向前復原可在重做目標 LSN 停止。</span><span class="sxs-lookup"><span data-stu-id="43f65-264">Online roll forward of the file containing the page is able to stop at the redo target LSN.</span></span> <span data-ttu-id="43f65-265">若要了解檔案目前的重做目標 LSN，請參閱 **sys.master_files** 的 **redo_target_lsn** 資料行。</span><span class="sxs-lookup"><span data-stu-id="43f65-265">To learn the current redo target LSN of a file, see the **redo_target_lsn** column of **sys.master_files**.</span></span> <span data-ttu-id="43f65-266">如需詳細資訊，請參閱 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="43f65-266">For more information, see [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql).</span></span>  
  
6.  <span data-ttu-id="43f65-267">還原新的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="43f65-267">Restore the new log backup.</span></span> <span data-ttu-id="43f65-268">套用此新的記錄備份後，就可完成分頁還原，頁面現在可以使用。</span><span class="sxs-lookup"><span data-stu-id="43f65-268">After this new log backup is applied, the page restore is completed and the pages are now usable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="43f65-269">這個順序與檔案還原順序類似。</span><span class="sxs-lookup"><span data-stu-id="43f65-269">This sequence is analogous to a file restore sequence.</span></span> <span data-ttu-id="43f65-270">事實上，分頁還原和檔案還原都可以做為相同順序的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="43f65-270">In fact, page restore and file restores can both be performed as part of the same sequence.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="43f65-271">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43f65-271">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="43f65-272">下列範例會以 `B` 還原檔案 `NORECOVERY`的四個損毀頁面。</span><span class="sxs-lookup"><span data-stu-id="43f65-272">The following example restores four damaged pages of file `B` with `NORECOVERY`.</span></span> <span data-ttu-id="43f65-273">接著，兩個記錄備份會套用 `NORECOVERY`，後面接著以 `RECOVERY`還原的結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="43f65-273">Next, two log backups are applied with `NORECOVERY`, followed with the tail-log backup, which is restored with `RECOVERY`.</span></span> <span data-ttu-id="43f65-274">這個範例會執行線上還原。</span><span class="sxs-lookup"><span data-stu-id="43f65-274">This example performs an online restore.</span></span> <span data-ttu-id="43f65-275">在範例中，檔案 `B` 的檔案識別碼是 `1`，而損毀頁面的頁面識別碼是 `57`、 `202`、 `916`和 `1016`。</span><span class="sxs-lookup"><span data-stu-id="43f65-275">In the example, the file ID of file `B` is `1`, and the page IDs of the damaged pages are `57`, `202`, `916`, and `1016`.</span></span>  
  
```sql  
RESTORE DATABASE <database> PAGE='1:57, 1:202, 1:916, 1:1016'  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
RESTORE LOG <database> FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG <database> FROM <log_backup>   
   WITH NORECOVERY;   
BACKUP LOG <database> TO <new_log_backup>;   
RESTORE LOG <database> FROM <new_log_backup> WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="43f65-276">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43f65-276">See Also</span></span>  
 <span data-ttu-id="43f65-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43f65-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="43f65-278">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="43f65-278">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="43f65-279">[管理 suspect_pages 資料表 &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="43f65-279">[Manage the suspect_pages Table &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md) </span></span>  
 [<span data-ttu-id="43f65-280">SQL Server 資料庫的備份與還原</span><span class="sxs-lookup"><span data-stu-id="43f65-280">Back Up and Restore of SQL Server Databases</span></span>](back-up-and-restore-of-sql-server-databases.md)  
  
  
