---
title: 在完整復原模式下，將資料庫還原至失敗點 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- point of failure [SQL Server]
- restoring databases [SQL Server], point of failure
- database restores [SQL Server], point of failure
ms.assetid: 04106e18-bbf7-4a5e-a2e1-3d65319814d5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95b73660ebb44f4daffe6eaefd873699cfbbd8ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595126"
---
# <a name="restore-a-database-to-the-point-of-failure-under-the-full-recovery-model-transact-sql"></a><span data-ttu-id="c5b4d-102">在完整復原模式下將資料庫還原至失敗點 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c5b4d-102">Restore a Database to the Point of Failure Under the Full Recovery Model (Transact-SQL)</span></span>
  <span data-ttu-id="c5b4d-103">此主題說明如何還原到失敗點。</span><span class="sxs-lookup"><span data-stu-id="c5b4d-103">This topic explains how to restore to the point of failure.</span></span> <span data-ttu-id="c5b4d-104">此主題只與使用完整或大量記錄復原模式的資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="c5b4d-104">The topic is relevant only for databases that are using the full or bulk-logged recovery models.</span></span>  
  
### <a name="to-restore-to-the-point-of-failure"></a><span data-ttu-id="c5b4d-105">還原到失敗點</span><span class="sxs-lookup"><span data-stu-id="c5b4d-105">To restore to the point of failure</span></span>  
  
1.  <span data-ttu-id="c5b4d-106">執行下列基本的 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式，備份記錄的結尾：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-106">Back up the tail of the log by running the following basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement:</span></span>  
  
    ```  
    BACKUP LOG <database_name> TO <backup_device>   
       WITH NORECOVERY, NO_TRUNCATE;  
    ```  
  
2.  <span data-ttu-id="c5b4d-107">執行下列基本的 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式，還原完整的資料庫備份：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-107">Restore a full database backup by running the following basic [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
3.  <span data-ttu-id="c5b4d-108">也可以選擇，執行下列基本的 RESTORE DATABASE 陳述式，還原差異資料庫備份：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-108">Optionally, restore a differential database backup by running the following basic RESTORE DATABASE statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
4.  <span data-ttu-id="c5b4d-109">套用每個交易記錄，包括您在步驟 1，透過在 RESTORE LOG 陳述式中指定 WITH NORECOVERY 所建立的結尾記錄備份：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-109">Apply each transaction log, including the tail-log backup you created in step 1, by specifying WITH NORECOVERY in the RESTORE LOG statement:</span></span>  
  
    ```  
    RESTORE LOG <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
5.  <span data-ttu-id="c5b4d-110">執行下列 RESTORE DATABASE 陳述式，復原資料庫：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-110">Recover the database by running the following RESTORE DATABASE statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name>   
       WITH RECOVERY;  
    ```  
  
## <a name="example"></a><span data-ttu-id="c5b4d-111">範例</span><span class="sxs-lookup"><span data-stu-id="c5b4d-111">Example</span></span>  
 <span data-ttu-id="c5b4d-112">在執行範例之前，必須先完成下列準備工作：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-112">Before you can run the example, you must complete the following preparations:</span></span>  
  
1.  <span data-ttu-id="c5b4d-113">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的預設復原模式是簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="c5b4d-113">The default recovery model of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is the simple recovery model.</span></span> <span data-ttu-id="c5b4d-114">由於此復原模式不支援還原至失敗點，請執行下列 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ALTER DATABASE [陳述式，設定](/sql/t-sql/statements/alter-database-transact-sql) 使用完整復原模式：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-114">Because this recovery model does not support restoring to the point of a failure, set [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] to use the full recovery model by running the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
    ```  
  
2.  <span data-ttu-id="c5b4d-115">使用下列 BACKUP 陳述式，建立資料庫的完整資料庫備份：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-115">Create a full database back of the database by using the following BACKUP statement:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Data.bck';  
    ```  
  
3.  <span data-ttu-id="c5b4d-116">建立例行的記錄備份：</span><span class="sxs-lookup"><span data-stu-id="c5b4d-116">Create a routine log backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Log.bck';  
    ```  
  
 <span data-ttu-id="c5b4d-117">下列範例會在建立 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的結尾記錄備份之後，還原先前建立的備份</span><span class="sxs-lookup"><span data-stu-id="c5b4d-117">The following example restores the backups that are created previously, after creating a tail-log backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="c5b4d-118">(此步驟假定可以取得記錄磁碟)。</span><span class="sxs-lookup"><span data-stu-id="c5b4d-118">(This step assumes that the log disk can be accessed.)</span></span>  
  
 <span data-ttu-id="c5b4d-119">首先，範例建立資料庫的結尾記錄備份，擷取使用中的記錄，並讓資料庫保留為「還原」狀態。</span><span class="sxs-lookup"><span data-stu-id="c5b4d-119">First, the example creates a tail-log backup of the database that captures the active log and leaves the database in the Restoring state.</span></span> <span data-ttu-id="c5b4d-120">然後，範例還原資料庫備份，套用先前建立的例行記錄備份，然後套用結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="c5b4d-120">Then, the example restores the database backup, applies the routine log backup created previously, and applies the tail-log backup.</span></span> <span data-ttu-id="c5b4d-121">最後，範例用另外一個步驟復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5b4d-121">Finally, the example recovers the database in a separate step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5b4d-122">預設行為是復原資料庫，作為還原最後備份的陳述式一部分。</span><span class="sxs-lookup"><span data-stu-id="c5b4d-122">The default behavior is to recover a database as part of the statement that restores the final backup.</span></span>  
  
```  
/* Example of restoring a to the point of failure */  
-- Step 1: Create a tail-log backup by using WITH NORECOVERY.  
BACKUP LOG AdventureWorks2012  
   TO DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 2: Restore the full database backup.  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Data.bck'  
   WITH NORECOVERY;  
GO  
-- Step 3: Restore the first transaction log backup.  
RESTORE LOG AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 4: Restore the tail-log backup.  
RESTORE LOG AdventureWorks2012  
   FROM  DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 5: Recover the database.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5b4d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5b4d-123">See Also</span></span>  
 <span data-ttu-id="c5b4d-124">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5b4d-124">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="c5b4d-125">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c5b4d-125">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
