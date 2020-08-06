---
title: 分次還原 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- partial updates [SQL Server]
- staged restores [SQL Server]
- piecemeal restores [SQL Server]
- restoring [SQL Server], piecemeal restore scenario
ms.assetid: 208f55e0-0762-4cfb-85c4-d36a76ea0f5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ebc4ea11780908f847946a01338571211b57678a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699814"
---
# <a name="piecemeal-restores-sql-server"></a><span data-ttu-id="1663c-102">分次還原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1663c-102">Piecemeal Restores (SQL Server)</span></span>
  <span data-ttu-id="1663c-103">這個主題僅與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 版中包含多個檔案或檔案群組 (若是簡單模式，僅適用唯讀檔案群組) 的資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="1663c-103">This topic is relevant only for databases in the Enterprise edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.</span></span>  
  
 <span data-ttu-id="1663c-104">如需分次還原及記憶體最佳化資料表的詳細資訊，請參閱 [分次還原具有記憶體最佳化資料表的資料庫](../in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="1663c-104">For information about piecemeal restore and memory-optimized tables, see [Piecemeal Restore of Databases With Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="1663c-105">*「分次還原」* (Piecemeal Restore) 允許對含有多個檔案群組的資料庫分段進行還原與復原。</span><span class="sxs-lookup"><span data-stu-id="1663c-105">*Piecemeal restore* allows databases that contain multiple filegroups to be restored and recovered in stages.</span></span> <span data-ttu-id="1663c-106">分次還原涉及一連串的還原順序，這會從主要檔案群組開始，而在某些情況下，還會從其中一個或多個次要的檔案群組開始。</span><span class="sxs-lookup"><span data-stu-id="1663c-106">Piecemeal restore involves a series of restore sequences, starting with the primary filegroup and, in some cases, one or more secondary filegroups.</span></span> <span data-ttu-id="1663c-107">分次還原會維護各項檢查，以確保最後資料庫能維持一致。</span><span class="sxs-lookup"><span data-stu-id="1663c-107">Piecemeal restore maintains checks to ensure that the database will be consistent in the end.</span></span> <span data-ttu-id="1663c-108">還原順序完成後，就可以直接讓復原的檔案 (如果這些檔案有效，而且與資料庫一致) 上線。</span><span class="sxs-lookup"><span data-stu-id="1663c-108">After the restore sequence is completed, recovered files, if they are valid and consistent with the database, can be brought online directly.</span></span>  
  
 <span data-ttu-id="1663c-109">分次還原適用於所有恢復模式，但它對於完整模式和大量記錄模式，可以提供比簡單模式更大的彈性。</span><span class="sxs-lookup"><span data-stu-id="1663c-109">Piecemeal restore works with all recovery models, but is more flexible for the full and bulk-logged models than for the simple model.</span></span>  
  
 <span data-ttu-id="1663c-110">每個分次還原都會從稱為「部分還原順序」  (Partial-Restore Sequence) 的初始還原順序開始進行。</span><span class="sxs-lookup"><span data-stu-id="1663c-110">Every piecemeal restore starts with an initial restore sequence called the *partial-restore sequence*.</span></span> <span data-ttu-id="1663c-111">部分還原順序至少會還原並復原主要檔案群組，而在簡單復原模式下，則是所有的讀取/寫入檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-111">Minimally, the partial-restore sequence restores and recovers the primary filegroup and, under the simple recovery model, all read/write filegroups.</span></span> <span data-ttu-id="1663c-112">在分次還原順序期間，整個資料庫必須離線。</span><span class="sxs-lookup"><span data-stu-id="1663c-112">During the piecemeal-restore sequence, the whole database must go offline.</span></span> <span data-ttu-id="1663c-113">此後，資料庫便會在線上，而還原的檔案群組也可供使用。</span><span class="sxs-lookup"><span data-stu-id="1663c-113">Thereafter, the database is online and restored filegroups are available.</span></span> <span data-ttu-id="1663c-114">不過，任何未還原的檔案群組會維持離線且無法存取。</span><span class="sxs-lookup"><span data-stu-id="1663c-114">However, any unrestored filegroups remain offline and are not accessible.</span></span> <span data-ttu-id="1663c-115">但是，您可以稍後再利用檔案還原來還原離線檔案群組並讓它們回到線上。</span><span class="sxs-lookup"><span data-stu-id="1663c-115">Any offline filegroups, however, can be restored and brought online later by a file restore.</span></span>  
  
 <span data-ttu-id="1663c-116">不論資料庫使用的復原模式為何，部分還原順序從還原完整備份及指定 PARTIAL 選項的 RESTORE DATABASE 陳述式開始。</span><span class="sxs-lookup"><span data-stu-id="1663c-116">Regardless of the recovery model that is used by the database, the partial-restore sequence starts with a RESTORE DATABASE statement that restores a full backup and specifies the PARTIAL option.</span></span> <span data-ttu-id="1663c-117">PARTIAL 選項永遠會開始新的分次還原，因此您只能在部分還原順序的初始陳述式中指定 PARTIAL 一次。</span><span class="sxs-lookup"><span data-stu-id="1663c-117">The PARTIAL option always starts a new piecemeal restore; therefore, you must specify PARTIAL only one time in the initial statement of the partial-restore sequence.</span></span> <span data-ttu-id="1663c-118">完成部分還原順序並讓資料庫回到線上後，其餘的檔案狀態都會變成「復原暫止」，因為檔案的復原已經延後。</span><span class="sxs-lookup"><span data-stu-id="1663c-118">When the partial restore sequence finishes and the database is brought online, the state of the remaining files becomes "recovery pending" because their recovery has been postponed.</span></span>  
  
 <span data-ttu-id="1663c-119">其後，分次還原通常包含一或多個還原順序，這稱為「檔案群組還原順序」  。</span><span class="sxs-lookup"><span data-stu-id="1663c-119">Subsequently, a piecemeal restore typically includes one or more restore sequences, which are called *filegroup-restore sequences*.</span></span> <span data-ttu-id="1663c-120">只要您願意等，就可以等著執行特定的檔案群組還原順序。</span><span class="sxs-lookup"><span data-stu-id="1663c-120">You can wait to perform a specific filegroup-restore sequence for as long as you want.</span></span> <span data-ttu-id="1663c-121">每個檔案群組還原順序都會將一或多個離線檔案群組還原並復原到與資料庫一致的點上。</span><span class="sxs-lookup"><span data-stu-id="1663c-121">Each filegroup-restore sequence restores and recovers one or more offline filegroups to a point consistent with the database.</span></span> <span data-ttu-id="1663c-122">檔案群組還原順序的時間和次數取決於您的復原目標、您要還原的離線檔案群組數目，以及您在每一檔案群組還原順序當中還原的檔案群組數。</span><span class="sxs-lookup"><span data-stu-id="1663c-122">The timing and number of filegroup-restore sequences depends on your recovery goal, the number of offline filegroups you want to restore, and on how many of them you restore per filegroup-restore sequence.</span></span>  
  
 <span data-ttu-id="1663c-123">執行分次還原的實際需求視資料庫的復原模式而定。</span><span class="sxs-lookup"><span data-stu-id="1663c-123">The exact requirements for performing a piecemeal restore depend on the recovery model of the database.</span></span> <span data-ttu-id="1663c-124">如需詳細資訊，請參閱本主題稍後的「在簡單復原模式下分次還原」與「在完整復原模式下分次還原」。</span><span class="sxs-lookup"><span data-stu-id="1663c-124">For more information, see "Piecemeal Restore Under the Simple Recovery Model" and "Piecemeal Restore Under the Full Recovery Model," later in this topic.</span></span>  
  
## <a name="piecemeal-restore-scenarios"></a><span data-ttu-id="1663c-125">分次還原實例</span><span class="sxs-lookup"><span data-stu-id="1663c-125">Piecemeal Restore Scenarios</span></span>  
 <span data-ttu-id="1663c-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有版本都支援離線分次還原。</span><span class="sxs-lookup"><span data-stu-id="1663c-126">All editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support offline piecemeal restores.</span></span> <span data-ttu-id="1663c-127">在 Enterprise 版中，分次還原可以在線上或離線進行。</span><span class="sxs-lookup"><span data-stu-id="1663c-127">In the Enterprise edition, a piecemeal restore can be either online or offline.</span></span> <span data-ttu-id="1663c-128">離線與線上分次還原的含意如下：</span><span class="sxs-lookup"><span data-stu-id="1663c-128">The implications of offline and online piecemeal restores are as follows:</span></span>  
  
-   <span data-ttu-id="1663c-129">離線分次還原實例</span><span class="sxs-lookup"><span data-stu-id="1663c-129">Offline piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="1663c-130">在離線分次還原中，資料庫會在部分還原順序之後上線。</span><span class="sxs-lookup"><span data-stu-id="1663c-130">In an offline piecemeal restore, the database is online after the partial-restore sequence.</span></span> <span data-ttu-id="1663c-131">尚未還原的檔案群組會保持離線，但是有必要時，可以先將資料庫離線，再還原這些檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-131">Filegroups that have not yet been restored remain offline, but they can be restored as you need them after taking the database offline.</span></span>  
  
-   <span data-ttu-id="1663c-132">線上分次還原實例</span><span class="sxs-lookup"><span data-stu-id="1663c-132">Online piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="1663c-133">如果是在部分還原順序之後的線上分次還原中，資料庫會在線上運作，且可使用主要檔案群組和任何復原的次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-133">In an online piecemeal restore, after the partial-restore sequence, the database is online, and the primary filegroup and any recovered secondary filegroups are available.</span></span> <span data-ttu-id="1663c-134">尚未還原的檔案群組會保持離線，但資料庫持續在線上運作時可視需要予以還原。</span><span class="sxs-lookup"><span data-stu-id="1663c-134">Filegroups that have not yet been restored remain offline, but they can be restored as needed while the database remains online.</span></span>  
  
     <span data-ttu-id="1663c-135">線上分次還原可以包括延遲交易。</span><span class="sxs-lookup"><span data-stu-id="1663c-135">Online piecemeal restores can involve deferred transactions.</span></span> <span data-ttu-id="1663c-136">當只有還原檔案群組的子集時，可能會延遲相依於線上檔案群組之資料庫中的交易。</span><span class="sxs-lookup"><span data-stu-id="1663c-136">When only a subset of filegroups has been restored, transactions in the database that depend on online filegroups might become deferred.</span></span> <span data-ttu-id="1663c-137">這是正常狀況，因為整個資料庫必須維持一致。</span><span class="sxs-lookup"><span data-stu-id="1663c-137">This is typical, because the whole database must be consistent.</span></span> <span data-ttu-id="1663c-138">如需詳細資訊，請參閱 [延遲交易 &#40;SQL Server&#41;](deferred-transactions-sql-server.md)中無用的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-138">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
-   [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="1663c-139">分次還原狀況</span><span class="sxs-lookup"><span data-stu-id="1663c-139">piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="1663c-140">如需記憶體中 OLTP 資料庫之分次還原的相關資訊，請參閱 [使用記憶體最佳化資料表分次備份和還原資料庫](../in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="1663c-140">For information on Piecemeal Restores of In-Memory OLTP databases see [Piecemeal Backup and Restore of Databases With Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="1663c-141">限制</span><span class="sxs-lookup"><span data-stu-id="1663c-141">Restrictions</span></span>  
 <span data-ttu-id="1663c-142">如果部分還原順序排除任何 [FILESTREAM](../blob/filestream-sql-server.md) 檔案群組，則不支援時間點還原。</span><span class="sxs-lookup"><span data-stu-id="1663c-142">If a partial restore sequence excludes any [FILESTREAM](../blob/filestream-sql-server.md) filegroup, point-in-time restore is not supported.</span></span> <span data-ttu-id="1663c-143">您可以強制還原順序，以繼續進行。</span><span class="sxs-lookup"><span data-stu-id="1663c-143">You can force the restore sequence to continue.</span></span> <span data-ttu-id="1663c-144">但是，絕對無法還原 RESTORE 陳述式中省略的 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-144">However the FILESTREAM filegroups that are omitted from your RESTORE statement can never be restored.</span></span> <span data-ttu-id="1663c-145">若要強制時間點還原，請指定 CONTINUE_AFTER_ERROR 選項，連同 STOPAT、STOPATMARK 或 STOPBEFOREMARK 選項，而且您也必須在後續的 RESTORE LOG 陳述式中指定這些項目。</span><span class="sxs-lookup"><span data-stu-id="1663c-145">To force a point-in-time restore, specify the CONTINUE_AFTER_ERROR option together with the STOPAT, STOPATMARK, or STOPBEFOREMARK option, which you must also specify in your subsequent RESTORE LOG statements.</span></span> <span data-ttu-id="1663c-146">如果您指定 CONTINUE_AFTER_ERROR，則部分還原順序會成功，而 FILESTREAM 檔案群組則會變成無法復原。</span><span class="sxs-lookup"><span data-stu-id="1663c-146">If you specify CONTINUE_AFTER_ERROR, the partial restore sequence succeeds and the FILESTREAM filegroup becomes unrecoverable.</span></span>  
  
## <a name="piecemeal-restore-under-the-simple-recovery-model"></a><span data-ttu-id="1663c-147">在簡單復原模式下分次還原</span><span class="sxs-lookup"><span data-stu-id="1663c-147">Piecemeal Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="1663c-148">在簡單復原模式下，分次還原順序必須從完整資料庫或部分備份開始。</span><span class="sxs-lookup"><span data-stu-id="1663c-148">Under the simple recovery model, the piecemeal restore sequence must start with a full database or partial backup.</span></span> <span data-ttu-id="1663c-149">然後，如果還原備份是差異基底，請接著還原最近一次的差異備份。</span><span class="sxs-lookup"><span data-stu-id="1663c-149">Then, if the restored backup is a differential base, restore the latest differential backup next.</span></span>  
  
 <span data-ttu-id="1663c-150">在第一個部分還原順序期間，如果只還原讀取/寫入檔案群組的子集，則當您復原部分還原的資料庫時，任何未還原的檔案群組就會變得無用。</span><span class="sxs-lookup"><span data-stu-id="1663c-150">During the first partial restore sequence, if you restore only a subset of read/write filegroups, any unrestored filegroups become defunct when you recover the partially restored database.</span></span> <span data-ttu-id="1663c-151">只有下列情況才適合省略部分還原順序中的讀取/寫入檔案群組：</span><span class="sxs-lookup"><span data-stu-id="1663c-151">Omitting a read/write filegroup from the partial-restore sequence is appropriate only in the following cases:</span></span>  
  
-   <span data-ttu-id="1663c-152">想要讓未還原的檔案群組變得無用。</span><span class="sxs-lookup"><span data-stu-id="1663c-152">You intend for the unrestored filegroups to become defunct.</span></span>  
  
-   <span data-ttu-id="1663c-153">還原順序將到達每個未還原的檔案群組都變唯讀、被捨棄或解除功能 (於部分還原順序的前一個還原期間) 的復原點。</span><span class="sxs-lookup"><span data-stu-id="1663c-153">The restore sequence will arrive at a recovery point at which each unrestored filegroup has become read-only, dropped, or defunct (during a previous restore in the partial-restore sequence).</span></span>  
  
-   <span data-ttu-id="1663c-154">完整備份是在資料庫使用簡單復原模式當時所進行的，但是復原點則是在資料庫使用完整復原模式的時候。</span><span class="sxs-lookup"><span data-stu-id="1663c-154">The full backup was taken while the database was using the simple recovery model, but the recovery point is at a time when the database is using the full recovery model.</span></span> <span data-ttu-id="1663c-155">如需詳細資訊，請參閱本主題稍後的「針對已從簡單復原模式切換到完整復原模式的資料庫執行分次還原」。</span><span class="sxs-lookup"><span data-stu-id="1663c-155">For more information, see "Performing a Piecemeal Restore of a Database Whose Recovery Model Has Been Switched from Simple to Full," later in this topic.</span></span>  
  
### <a name="requirements-for-piecemeal-restore-under-the-simple-recovery-model"></a><span data-ttu-id="1663c-156">在簡單復原模式下分次還原的需求</span><span class="sxs-lookup"><span data-stu-id="1663c-156">Requirements for Piecemeal Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="1663c-157">在簡單復原模式下，初始階段會還原並復原主要檔案群組以及所有的讀取/寫入次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-157">Under the simple recovery model, the initial stage restores and recovers the primary filegroup and all read/write secondary filegroups.</span></span> <span data-ttu-id="1663c-158">初始階段完成後，就可以直接讓復原的檔案 (如果這些檔案有效，而且與資料庫一致) 上線。</span><span class="sxs-lookup"><span data-stu-id="1663c-158">After the initial stage is completed, recovered files, if they are valid and consistent with the database, can be brought online directly.</span></span>  
  
 <span data-ttu-id="1663c-159">此後，可以分一個或多個其他階段來還原唯讀檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-159">Thereafter, read-only filegroups can be restored in one or more additional stages.</span></span>  
  
 <span data-ttu-id="1663c-160">只有在下列情況成立時，才能對唯讀次要檔案群組進行分次還原：</span><span class="sxs-lookup"><span data-stu-id="1663c-160">Piecemeal restore is available for a read-only secondary filegroup only if the following are true:</span></span>  
  
-   <span data-ttu-id="1663c-161">備份時唯讀。</span><span class="sxs-lookup"><span data-stu-id="1663c-161">Was read-only when backed up.</span></span>  
  
-   <span data-ttu-id="1663c-162">保持唯讀 (與主要檔案群組保持邏輯上的一致)。</span><span class="sxs-lookup"><span data-stu-id="1663c-162">Has remained read-only (keeping it logically consistent with the primary filegroup).</span></span>  
  
 <span data-ttu-id="1663c-163">若要執行分次還原，必須遵守下列方針：</span><span class="sxs-lookup"><span data-stu-id="1663c-163">To perform a piecemeal restore, the following guidelines must be followed:</span></span>  
  
-   <span data-ttu-id="1663c-164">分次還原簡單復原模式資料庫的完整備份組必須包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="1663c-164">A complete set of backups for the piecemeal restore of a simple recovery model database must contain the following:</span></span>  
  
    -   <span data-ttu-id="1663c-165">包含主要檔案群組與所有檔案群組的部分或完整資料庫備份 (這些檔案群組在進行備份時都是可讀取/寫入的)。</span><span class="sxs-lookup"><span data-stu-id="1663c-165">A partial or full database backup that contains the primary filegroup and all filegroups that were read/write at the time of the backup.</span></span>  
  
    -   <span data-ttu-id="1663c-166">每個唯讀檔案的備份。</span><span class="sxs-lookup"><span data-stu-id="1663c-166">A backup of each read-only file.</span></span>  
  
-   <span data-ttu-id="1663c-167">若要唯讀檔案的備份與主要檔案群組一致，從備份次要檔案群組開始，到包含主要檔案群組的備份完成為止，次要檔案群組都必須是唯讀。</span><span class="sxs-lookup"><span data-stu-id="1663c-167">For the backup of a read-only file to be consistent with the primary filegroup, the secondary filegroup must have been read-only from when it was backed up until the backup that contains the primary filegroup was completed.</span></span> <span data-ttu-id="1663c-168">如果差異檔案備份是在檔案群組成為唯讀之後才建立，您可以使用這些差異檔案備份。</span><span class="sxs-lookup"><span data-stu-id="1663c-168">You can use differential file backups, if they were taken after the filegroup became read-only.</span></span>  
  
### <a name="piecemeal-restore-stages-simple-recovery-model"></a><span data-ttu-id="1663c-169">分次還原階段 (簡單復原模式)</span><span class="sxs-lookup"><span data-stu-id="1663c-169">Piecemeal Restore Stages (Simple Recovery Model)</span></span>  
 <span data-ttu-id="1663c-170">分次還原實例牽涉到下列階段：</span><span class="sxs-lookup"><span data-stu-id="1663c-170">The piecemeal restore scenario involves the following stages:</span></span>  
  
-   <span data-ttu-id="1663c-171">初始階段 (還原並復原主要檔案群組與所有讀取/寫入檔案群組)</span><span class="sxs-lookup"><span data-stu-id="1663c-171">Initial stage (restore and recover the primary filegroup and all read/write filegroups)</span></span>  
  
     <span data-ttu-id="1663c-172">初始階段會執行部分還原。</span><span class="sxs-lookup"><span data-stu-id="1663c-172">The initial stage performs a partial restore.</span></span> <span data-ttu-id="1663c-173">部分還原順序會還原主要檔案群組、所有讀取/寫入次要檔案群組，以及 (選擇性的) 某些唯讀檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-173">The partial restore sequence restores the primary filegroup, all read/write secondary filegroups, and (optionally) some of the read-only filegroups.</span></span> <span data-ttu-id="1663c-174">在初始階段，整個資料庫必須離線。</span><span class="sxs-lookup"><span data-stu-id="1663c-174">During the initial stage, the whole database must go offline.</span></span> <span data-ttu-id="1663c-175">在初始階段之後，資料庫會持續在線上運作，且可使用還原的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-175">After the initial stage, the database is online, and restored filegroups are available.</span></span> <span data-ttu-id="1663c-176">不過，所有尚未還原的唯讀檔案群組會保持離線。</span><span class="sxs-lookup"><span data-stu-id="1663c-176">However, any read-only filegroups that have not yet been restored, remain offline.</span></span>  
  
     <span data-ttu-id="1663c-177">初始階段中的第一個 RESTORE 陳述式必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1663c-177">The first RESTORE statement in the initial stage must do the following:</span></span>  
  
    -   <span data-ttu-id="1663c-178">使用包含主要檔案群組與所有檔案群組 (進行備份時都是讀取/寫入的) 的部分或完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="1663c-178">Use a partial or full database backup that contains the primary filegroup and all filegroups that were read/write at the time of the backup.</span></span> <span data-ttu-id="1663c-179">部分還原的順序，通常是從還原部分備份開始。</span><span class="sxs-lookup"><span data-stu-id="1663c-179">It is common to start a partial restore sequence by restoring a partial backup.</span></span>  
  
    -   <span data-ttu-id="1663c-180">指定 PARTIAL 選項，指出分次還原的開始。</span><span class="sxs-lookup"><span data-stu-id="1663c-180">Specify the PARTIAL option, which indicates the start of a piecemeal restore.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1663c-181">PARTIAL 選項會執行安全性檢查，確保產生的資料庫適合用來做為實際執行的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1663c-181">The PARTIAL option performs safety checks that ensure that the resulting database is suited for use as a production database.</span></span>  
  
    -   <span data-ttu-id="1663c-182">如果備份是完整資料庫備份，請指定 READ_WRITE_FILEGROUPS 選項。</span><span class="sxs-lookup"><span data-stu-id="1663c-182">Specify the READ_WRITE_FILEGROUPS option if the backup is a full database backup.</span></span>  
  
-   <span data-ttu-id="1663c-183">當資料庫在線上時，您可以使用一或多個線上檔案還原來還原並復原離線唯讀檔案 (在備份時是唯讀的)。</span><span class="sxs-lookup"><span data-stu-id="1663c-183">While the database is online, you can use one or more online file restores to restore and recover offline read-only files that were read-only at the time of backup.</span></span> <span data-ttu-id="1663c-184">線上檔案還原的時間視您何時需要讓資料上線而定。</span><span class="sxs-lookup"><span data-stu-id="1663c-184">The timing of the online file restores depends on when you want to have the data online.</span></span>  
  
     <span data-ttu-id="1663c-185">是否必須將資料還原到檔案，取決於下列條件：</span><span class="sxs-lookup"><span data-stu-id="1663c-185">Whether you must restore data to a file depends on the following:</span></span>  
  
    -   <span data-ttu-id="1663c-186">與資料庫一致的有效唯讀檔案加以復原之後，不需還原任何資料，即可直接上線。</span><span class="sxs-lookup"><span data-stu-id="1663c-186">Valid read-only files that are consistent with the database can be brought online directly by recovering them without restoring any data.</span></span>  
  
    -   <span data-ttu-id="1663c-187">損毀或與資料庫不一致的檔案必須在復原之前予以還原。</span><span class="sxs-lookup"><span data-stu-id="1663c-187">Files that are damaged or inconsistent with the database must be restored before they are recovered.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1663c-188">範例</span><span class="sxs-lookup"><span data-stu-id="1663c-188">Examples</span></span>  
  
-   [<span data-ttu-id="1663c-189">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="1663c-189">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="1663c-190">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="1663c-190">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="piecemeal-restore-under-the-full-recovery-model"></a><span data-ttu-id="1663c-191">在完整復原模式下分次還原</span><span class="sxs-lookup"><span data-stu-id="1663c-191">Piecemeal Restore Under the Full Recovery Model</span></span>  
 <span data-ttu-id="1663c-192">在完整復原模式或大量記錄復原模式下，分次還原適用於任何包含多個檔案群組的資料庫，而且您可以將資料庫還原到任何一個時間點。</span><span class="sxs-lookup"><span data-stu-id="1663c-192">Under the full recovery model or bulk-logged recovery model, piecemeal restore is available for any database that contains multiple filegroups and you can restore a database to any point in time.</span></span> <span data-ttu-id="1663c-193">分次還原的還原順序的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="1663c-193">The restore sequences of a piecemeal restore behave as follows:</span></span>  
  
-   <span data-ttu-id="1663c-194">部分還原順序</span><span class="sxs-lookup"><span data-stu-id="1663c-194">Partial-restore sequence</span></span>  
  
     <span data-ttu-id="1663c-195">部分還原順序會還原主要檔案群組，以及選擇性地還原某些次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-195">The partial restore sequence restores the primary filegroup and, optionally, some of the secondary filegroups.</span></span>  
  
     <span data-ttu-id="1663c-196">第一個 RESTORE DATABASE 陳述式必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1663c-196">The first RESTORE DATABASE statement must do the following:</span></span>  
  
    -   <span data-ttu-id="1663c-197">指定 PARTIAL 選項。</span><span class="sxs-lookup"><span data-stu-id="1663c-197">Specify the PARTIAL option.</span></span> <span data-ttu-id="1663c-198">這會指出分次還原的開始。</span><span class="sxs-lookup"><span data-stu-id="1663c-198">This indicates the start of a piecemeal restore.</span></span>  
  
    -   <span data-ttu-id="1663c-199">使用包含主要檔案群組的任何完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="1663c-199">Use any full database backup that contains the primary filegroup.</span></span> <span data-ttu-id="1663c-200">部分還原的順序，通常是從還原部分備份開始。</span><span class="sxs-lookup"><span data-stu-id="1663c-200">The common practice is to start a partial restore sequence by restoring a partial backup.</span></span>  
  
    -   <span data-ttu-id="1663c-201">若要還原到特定時間點，您必須在部分還原順序中指定時間。</span><span class="sxs-lookup"><span data-stu-id="1663c-201">To restore to a specific point in time, you must specify the time in the partial restore sequence.</span></span> <span data-ttu-id="1663c-202">還原順序的每個連續步驟都必須指定相同的時間點。</span><span class="sxs-lookup"><span data-stu-id="1663c-202">Every successive step of the restore sequence must specify the same point in time.</span></span>  
  
-   <span data-ttu-id="1663c-203">檔案群組還原順序會讓其他檔案群組在線上與資料庫保持一致。</span><span class="sxs-lookup"><span data-stu-id="1663c-203">Filegroup-restore sequences bring additional filegroups online to a point consistent with the database.</span></span>  
  
     <span data-ttu-id="1663c-204">在 Enterprise 版中，可以在資料庫仍在線上運作時還原並復原任何離線的次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1663c-204">In the Enterprise edition, any offline secondary filegroup can be restored and recovered while the database remains online.</span></span> <span data-ttu-id="1663c-205">如果特定唯讀檔案是未受損的，且與資料庫一致，就不需要還原檔案。</span><span class="sxs-lookup"><span data-stu-id="1663c-205">If a specific read-only file is undamaged and consistent with the database, the file does not have to be restored.</span></span> <span data-ttu-id="1663c-206">如需詳細資訊，請參閱[復原資料庫而不還原資料 &#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="1663c-206">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
### <a name="applying-log-backups"></a><span data-ttu-id="1663c-207">套用記錄備份</span><span class="sxs-lookup"><span data-stu-id="1663c-207">Applying Log Backups</span></span>  
 <span data-ttu-id="1663c-208">如果唯讀檔案群組從建立檔案備份以前已經是唯讀，就不需要將記錄備份套用到檔案群組，而且檔案還原會將它略過。</span><span class="sxs-lookup"><span data-stu-id="1663c-208">If a read-only filegroup has been read-only since before the file backup was created, applying log backups to the filegroup is unnecessary and is skipped by file restore.</span></span> <span data-ttu-id="1663c-209">如果檔案群組是可讀取/寫入，就必須套用無間斷記錄備份鏈結至最後一個完整或差異還原，才能將檔案群組向前復原到目前的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1663c-209">If the filegroup is read/write, an unbroken chain of log backups must be applied to the last full or differential restore to bring the filegroup forward to the current log file.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1663c-210">範例</span><span class="sxs-lookup"><span data-stu-id="1663c-210">Examples</span></span>  
  
-   [<span data-ttu-id="1663c-211">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="1663c-211">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="1663c-212">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="1663c-212">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
## <a name="performing-a-piecemeal-restore-of-a-database-whose-recovery-model-has-been-switched-from-simple-to-full"></a><span data-ttu-id="1663c-213">針對已從簡單復原模式切換到完整復原模式的資料庫執行分次還原</span><span class="sxs-lookup"><span data-stu-id="1663c-213">Performing a Piecemeal Restore of a Database Whose Recovery Model Has Been Switched from Simple to Full</span></span>  
 <span data-ttu-id="1663c-214">從完整的部分或資料庫備份起，您就可以開始針對已經從簡單復原模式切換到完整復原模式的資料庫執行分次還原。</span><span class="sxs-lookup"><span data-stu-id="1663c-214">You can perform a piecemeal restore of a database that has been switched from the simple recovery model to the full recovery model since the full partial or database backup.</span></span> <span data-ttu-id="1663c-215">例如，考慮有個資料庫採取了下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1663c-215">For example, consider a database for which you take the following steps:</span></span>  
  
1.  <span data-ttu-id="1663c-216">建立簡單模式資料庫的部分備份 (backup_1)。</span><span class="sxs-lookup"><span data-stu-id="1663c-216">Create a partial backup (backup_1) of a simple-model database.</span></span>  
  
2.  <span data-ttu-id="1663c-217">過一段時間以後，將復原模式變更為「完整」。</span><span class="sxs-lookup"><span data-stu-id="1663c-217">After some time, change the recovery model to full.</span></span>  
  
3.  <span data-ttu-id="1663c-218">建立差異備份。</span><span class="sxs-lookup"><span data-stu-id="1663c-218">Create a differential backup.</span></span>  
  
4.  <span data-ttu-id="1663c-219">開始進行記錄備份。</span><span class="sxs-lookup"><span data-stu-id="1663c-219">Start taking log backups.</span></span>  
  
 <span data-ttu-id="1663c-220">之後，以下的順序有效：</span><span class="sxs-lookup"><span data-stu-id="1663c-220">Thereafter, the following sequence is valid:</span></span>  
  
1.  <span data-ttu-id="1663c-221">忽略部分次要檔案群組的部分還原。</span><span class="sxs-lookup"><span data-stu-id="1663c-221">A partial restore that omits some secondary filegroups.</span></span>  
  
2.  <span data-ttu-id="1663c-222">差異還原後有其他必要的還原。</span><span class="sxs-lookup"><span data-stu-id="1663c-222">A differential restore followed by any other needed restores.</span></span>  
  
3.  <span data-ttu-id="1663c-223">稍後，從 backup_1 部分備份進行讀取/寫入次要檔案群組 WITH NORECOVERY 檔案還原</span><span class="sxs-lookup"><span data-stu-id="1663c-223">Later, a file restore of a read/write secondary filegroup WITH NORECOVERY from the backup_1 partial backup</span></span>  
  
4.  <span data-ttu-id="1663c-224">差異備份之後緊接著原始分次還原順序中所還原的任何其他備份，可還原資料直到原始的復原點為止。</span><span class="sxs-lookup"><span data-stu-id="1663c-224">The differential backup followed by any other backups that were restored in the original piecemeal restore sequence to restore the data up to the original recovery point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1663c-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1663c-225">See Also</span></span>  
 <span data-ttu-id="1663c-226">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1663c-226">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="1663c-227">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1663c-227">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="1663c-228">[將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="1663c-228">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="1663c-229">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1663c-229">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="1663c-230">規劃和執行還原順序 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="1663c-230">Plan and Perform Restore Sequences &#40;Full Recovery Model&#41;</span></span>](plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
