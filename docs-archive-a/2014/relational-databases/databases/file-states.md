---
title: 檔案狀態 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- restoring file state [SQL Server]
- verifying file states
- current file states
- verifying filegroup states
- file states [SQL Server]
- online file state
- offline file state [SQL Server]
- viewing filegroup states
- viewing file states
- suspect file state
- recovering file state [SQL Server]
- current filegroup state
- recovery pending file state [SQL Server]
- displaying file states
- states [SQL Server], files
- displaying filegroup states
- defunct file state
ms.assetid: b426474d-8954-4df0-b78b-887becfbe8d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7cad94527d9191609a6920b5dfa200a98cd8bbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598987"
---
# <a name="file-states"></a><span data-ttu-id="498a7-102">檔案狀態</span><span class="sxs-lookup"><span data-stu-id="498a7-102">File States</span></span>
  <span data-ttu-id="498a7-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，資料庫檔案的狀態是與資料庫的狀態分開維護。</span><span class="sxs-lookup"><span data-stu-id="498a7-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the state of a database file is maintained independently from the state of the database.</span></span> <span data-ttu-id="498a7-104">檔案永遠處於特定狀態，例如 ONLINE 或 OFFLINE。</span><span class="sxs-lookup"><span data-stu-id="498a7-104">A file is always in one specific state, such as ONLINE or OFFLINE.</span></span> <span data-ttu-id="498a7-105">若要檢視檔案目前的狀態，請使用 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 或 [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="498a7-105">To view the current state of a file, use the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) or [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) catalog view.</span></span> <span data-ttu-id="498a7-106">如果資料庫是離線的，就可以從 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 目錄檢視來檢視檔案的狀態。</span><span class="sxs-lookup"><span data-stu-id="498a7-106">If the database is offline, the state of the files can be viewed from the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="498a7-107">檔案群組中的檔案狀態將決定整個檔案群組的可用性。</span><span class="sxs-lookup"><span data-stu-id="498a7-107">The state of the files in a filegroup determines the availability of the whole filegroup.</span></span> <span data-ttu-id="498a7-108">若要使某個檔案群組為可用的，則在檔案群組中的所有檔案必須都在線上。</span><span class="sxs-lookup"><span data-stu-id="498a7-108">For a filegroup to be available, all files within the filegroup must be online.</span></span> <span data-ttu-id="498a7-109">若要檢視檔案群組目前的狀態，請使用 [sys.filegroups](/sql/relational-databases/system-catalog-views/sys-filegroups-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="498a7-109">To view the current state of a filegroup, use the [sys.filegroups](/sql/relational-databases/system-catalog-views/sys-filegroups-transact-sql) catalog view.</span></span> <span data-ttu-id="498a7-110">如果檔案群組離線而您嘗試透過 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式存取檔案群組，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="498a7-110">If a filegroup is offline and you try to access the filegroup by a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, it will fail with an error.</span></span> <span data-ttu-id="498a7-111">當查詢最佳化工具建立 SELECT 陳述式的查詢計畫時，它可避免使用離線檔案群組中所存在的非叢集索引和叢集檢視，以利陳述式成功。</span><span class="sxs-lookup"><span data-stu-id="498a7-111">When the query optimizer builds query plans for SELECT statements, it avoids nonclustered indexes and indexed views that reside in offline filegroups, letting these statements to succeed.</span></span> <span data-ttu-id="498a7-112">不過，如果離線檔案群組包含目標資料表的堆積或叢集索引，SELECT 陳述式將會失敗。</span><span class="sxs-lookup"><span data-stu-id="498a7-112">However, if the offline filegroup contains the heap or clustered index of the target table, the SELECT statements fail.</span></span> <span data-ttu-id="498a7-113">除此之外，在離線檔案群組中，以 INSERT、UPDATE 或 DELETE 陳述式修改含有索引的資料表將會失敗。</span><span class="sxs-lookup"><span data-stu-id="498a7-113">Additionally, any INSERT, UPDATE, or DELETE statement that modifies a table with any index in an offline filegroup will fail.</span></span>  
  
## <a name="file-state-definitions"></a><span data-ttu-id="498a7-114">檔案狀態定義</span><span class="sxs-lookup"><span data-stu-id="498a7-114">File State Definitions</span></span>  
 <span data-ttu-id="498a7-115">下表定義檔案狀態。</span><span class="sxs-lookup"><span data-stu-id="498a7-115">The following table defines the file states.</span></span>  
  
|<span data-ttu-id="498a7-116">State</span><span class="sxs-lookup"><span data-stu-id="498a7-116">State</span></span>|<span data-ttu-id="498a7-117">定義</span><span class="sxs-lookup"><span data-stu-id="498a7-117">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="498a7-118">ONLINE</span><span class="sxs-lookup"><span data-stu-id="498a7-118">ONLINE</span></span>|<span data-ttu-id="498a7-119">檔案可供所有的作業使用。</span><span class="sxs-lookup"><span data-stu-id="498a7-119">The file is available for all operations.</span></span> <span data-ttu-id="498a7-120">如果資料庫本身是在線上，則主要檔案群組中的檔案將永遠在線上。</span><span class="sxs-lookup"><span data-stu-id="498a7-120">Files in the primary filegroup are always online if the database itself is online.</span></span> <span data-ttu-id="498a7-121">如果在主要檔案群組中的檔案不在線上，則資料庫也不會在線上且次要檔案的狀態是未定義的。</span><span class="sxs-lookup"><span data-stu-id="498a7-121">If a file in the primary filegroup is not online, the database is not online and the states of the secondary files are undefined.</span></span>|  
|<span data-ttu-id="498a7-122">OFFLINE</span><span class="sxs-lookup"><span data-stu-id="498a7-122">OFFLINE</span></span>|<span data-ttu-id="498a7-123">檔案無法存取且可能不在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="498a7-123">The file is not available for access and may not be present on the disk.</span></span> <span data-ttu-id="498a7-124">明確的使用者動作會使檔案變成離線，而且在採取其他使用者動作之前都是離線狀態。</span><span class="sxs-lookup"><span data-stu-id="498a7-124">Files become offline by explicit user action and remain offline until additional user action is taken.</span></span><br /><br /> <span data-ttu-id="498a7-125">注意當檔案損毀時，應該只能將檔案設為離線狀態，但是可以還原。 \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="498a7-125">**\*\* Caution \*\*** A file should only be set offline when the file is corrupted, but it can be restored.</span></span> <span data-ttu-id="498a7-126">設為離線的檔案只能透過從備份還原檔案來將它設為線上。</span><span class="sxs-lookup"><span data-stu-id="498a7-126">A file set to offline can only be set online by restoring the file from backup.</span></span> <span data-ttu-id="498a7-127">如需有關還原單一檔案的詳細資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="498a7-127">For more information about restoring a single file, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>|  
|<span data-ttu-id="498a7-128">RESTORING</span><span class="sxs-lookup"><span data-stu-id="498a7-128">RESTORING</span></span>|<span data-ttu-id="498a7-129">正在還原檔案。</span><span class="sxs-lookup"><span data-stu-id="498a7-129">The file is being restored.</span></span> <span data-ttu-id="498a7-130">檔案會輸入還原狀態，因為還原命令會影響整個檔案，而不是只有頁面還原，而且會一直保留此狀態，直到完成還原並復原檔案為止。</span><span class="sxs-lookup"><span data-stu-id="498a7-130">Files enter the restoring state because of a restore command affecting the whole file, not just a page restore, and remain in this state until the restore is completed and the file is recovered.</span></span>|  
|<span data-ttu-id="498a7-131">RECOVERY PENDING</span><span class="sxs-lookup"><span data-stu-id="498a7-131">RECOVERY PENDING</span></span>|<span data-ttu-id="498a7-132">已延遲檔案復原。</span><span class="sxs-lookup"><span data-stu-id="498a7-132">The recovery of the file has been postponed.</span></span> <span data-ttu-id="498a7-133">檔案會自動輸入此狀態，因為在分次還原處理序中，有未還原和未復原的檔案。</span><span class="sxs-lookup"><span data-stu-id="498a7-133">A file enters this state automatically because of a piecemeal restore process in which the file is not restored and recovered.</span></span> <span data-ttu-id="498a7-134">需要使用者執行其他動作以解決錯誤並允許完成復原處理。</span><span class="sxs-lookup"><span data-stu-id="498a7-134">Additional action by the user is required to resolve the error and allow for the recovery process to be completed.</span></span> <span data-ttu-id="498a7-135">如需詳細資訊，請參閱[分次還原 &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="498a7-135">For more information, see [Piecemeal Restores &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).</span></span>|  
|<span data-ttu-id="498a7-136">SUSPECT</span><span class="sxs-lookup"><span data-stu-id="498a7-136">SUSPECT</span></span>|<span data-ttu-id="498a7-137">在線上還原處理期間檔案復原失敗。</span><span class="sxs-lookup"><span data-stu-id="498a7-137">Recovery of the file failed during an online restore process.</span></span> <span data-ttu-id="498a7-138">如果檔案是在主要檔案群組中，資料庫也會標示為有疑問。</span><span class="sxs-lookup"><span data-stu-id="498a7-138">If the file is in the primary filegroup, the database is also marked as suspect.</span></span> <span data-ttu-id="498a7-139">否則，只有檔案是有疑問的，資料庫仍會在線上。</span><span class="sxs-lookup"><span data-stu-id="498a7-139">Otherwise, only the file is suspect and the database is still online.</span></span><br /><br /> <span data-ttu-id="498a7-140">檔案仍然會在有疑問的狀態下，直到可以使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="498a7-140">The file will remain in the suspect state until it is made available by one of the following methods:</span></span><br /><br /> <span data-ttu-id="498a7-141">還原和復原</span><span class="sxs-lookup"><span data-stu-id="498a7-141">Restore and recovery</span></span><br /><br /> <span data-ttu-id="498a7-142">DBCC CHECKDB with REPAIR_ALLOW_DATA_LOSS</span><span class="sxs-lookup"><span data-stu-id="498a7-142">DBCC CHECKDB with REPAIR_ALLOW_DATA_LOSS</span></span>|  
|<span data-ttu-id="498a7-143">DEFUNCT</span><span class="sxs-lookup"><span data-stu-id="498a7-143">DEFUNCT</span></span>|<span data-ttu-id="498a7-144">當它在線上時，就會卸除檔案。</span><span class="sxs-lookup"><span data-stu-id="498a7-144">The file was dropped when it was not online.</span></span> <span data-ttu-id="498a7-145">當移除了離線檔案群組，在檔案群組中的所有檔案就會變成無用。</span><span class="sxs-lookup"><span data-stu-id="498a7-145">All files in a filegroup become defunct when an offline filegroup is removed.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="498a7-146">相關內容</span><span class="sxs-lookup"><span data-stu-id="498a7-146">Related Content</span></span>  
 [<span data-ttu-id="498a7-147">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="498a7-147">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="498a7-148">資料庫狀態</span><span class="sxs-lookup"><span data-stu-id="498a7-148">Database States</span></span>](database-states.md)  
  
 [<span data-ttu-id="498a7-149">鏡像狀態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="498a7-149">Mirroring States &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [<span data-ttu-id="498a7-150">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="498a7-150">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [<span data-ttu-id="498a7-151">資料庫檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="498a7-151">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
