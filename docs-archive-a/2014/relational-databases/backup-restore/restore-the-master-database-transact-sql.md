---
title: 還原 master 資料庫 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], restoring
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c9cb078b7af60fc5e060bcb144fc9cbaee8ecf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598458"
---
# <a name="restore-the-master-database-transact-sql"></a><span data-ttu-id="a31f4-102">還原 master 資料庫 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a31f4-102">Restore the master Database (Transact-SQL)</span></span>
  <span data-ttu-id="a31f4-103">本主題說明如何從完整資料庫備份中還原 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a31f4-103">This topic explains how to restore the **master** database from a full database backup.</span></span>  
  
### <a name="to-restore-the-master-database"></a><span data-ttu-id="a31f4-104">還原 master 資料庫</span><span class="sxs-lookup"><span data-stu-id="a31f4-104">To restore the master database</span></span>  
  
1.  <span data-ttu-id="a31f4-105">以單一使用者模式啟動伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a31f4-105">Start the server instance in single-user mode.</span></span>  
  
     <span data-ttu-id="a31f4-106">如需如何指定單一使用者啟動參數資訊 ( **-m**) 的相關資訊，請參閱[設定伺服器啟動選項 &#40;SQL Server 組態管理員&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="a31f4-106">For information about how to specify the single-user startup parameter (**-m**), see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).</span></span>  
  
2.  <span data-ttu-id="a31f4-107">若要還原 **master**的完整資料庫備份，請使用下列 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a31f4-107">To restore a full database backup of **master**, use the following [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
     <span data-ttu-id="a31f4-108">`RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`</span><span class="sxs-lookup"><span data-stu-id="a31f4-108">`RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`</span></span>  
  
     <span data-ttu-id="a31f4-109">即使有同名的資料庫，REPLACE 選項還是會指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 還原指定的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a31f4-109">The REPLACE option instructs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to restore the specified database even when a database of the same name already exists.</span></span> <span data-ttu-id="a31f4-110">現有的資料庫 (如果有的話) 會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="a31f4-110">The existing database, if any, is deleted.</span></span> <span data-ttu-id="a31f4-111">在單一使用者模式中，我們建議您在 [sqlcmd 公用程式](../../tools/sqlcmd-utility.md)中輸入 RESTORE DATABASE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a31f4-111">In single-user mode, we recommend that you enter the RESTORE DATABASE statement in the [sqlcmd utility](../../tools/sqlcmd-utility.md).</span></span> <span data-ttu-id="a31f4-112">如需詳細資訊，請參閱 [使用 sqlcmd 公用程式](../scripting/sqlcmd-use-the-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="a31f4-112">For more information, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a31f4-113">在還原 **master** 之後， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體會關閉，並終止 **sqlcmd** 處理序。</span><span class="sxs-lookup"><span data-stu-id="a31f4-113">After **master** is restored, the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] shuts down and terminates the **sqlcmd** process.</span></span> <span data-ttu-id="a31f4-114">在重新啟動伺服器執行個體之前，請移除單一使用者啟動參數。</span><span class="sxs-lookup"><span data-stu-id="a31f4-114">Before you restart the server instance, remove the single-user startup parameter.</span></span> <span data-ttu-id="a31f4-115">如需詳細資訊，請參閱[設定伺服器啟動選項 &#40;SQL Server 組態管理員&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="a31f4-115">For more information, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).</span></span>  
  
3.  <span data-ttu-id="a31f4-116">重新啟動伺服器執行個體，然後繼續其他復原步驟，例如還原其他資料庫、附加資料庫，以及更正使用者不符的項目。</span><span class="sxs-lookup"><span data-stu-id="a31f4-116">Restart the server instance and continue other recovery steps such as restoring other databases, attaching databases, and correcting user mismatches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a31f4-117">範例</span><span class="sxs-lookup"><span data-stu-id="a31f4-117">Example</span></span>  
 <span data-ttu-id="a31f4-118">下列範例會在預設伺服器執行個體上還原 `master` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a31f4-118">The following example restores the `master` database on the default server instance.</span></span> <span data-ttu-id="a31f4-119">此範例假設伺服器執行個體已經在單一使用者模式中執行。</span><span class="sxs-lookup"><span data-stu-id="a31f4-119">The example assumes that the server instance is already running in single-user mode.</span></span> <span data-ttu-id="a31f4-120">此範例會啟動 `sqlcmd` ，並執行 `RESTORE DATABASE` 陳述式，從磁碟裝置還原 `master` 的完整資料庫備份： `Z:\SQLServerBackups\master.bak`。</span><span class="sxs-lookup"><span data-stu-id="a31f4-120">The example starts `sqlcmd` and executes a `RESTORE DATABASE` statement that restores a full database backup of `master` from a disk device: `Z:\SQLServerBackups\master.bak`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a31f4-121">針對具名執行個體，**sqlcmd** 命令必須指定 **-S** _\<ComputerName>_ \\ *\<InstanceName>* 選項。</span><span class="sxs-lookup"><span data-stu-id="a31f4-121">For a named instance, the **sqlcmd** command must specify the **-S**_\<ComputerName>_\\*\<InstanceName>* option.</span></span>  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a31f4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a31f4-122">See Also</span></span>  
 <span data-ttu-id="a31f4-123">[完整資料庫還原 &#40;簡單復原模式&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="a31f4-123">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="a31f4-124">[完整資料庫還原 &#40;完整復原模式&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="a31f4-124">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="a31f4-125">[孤立的使用者疑難排解 &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a31f4-125">[Troubleshoot Orphaned Users &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span></span>  
 <span data-ttu-id="a31f4-126">[資料庫卸離和附加 &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a31f4-126">[Database Detach and Attach &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="a31f4-127">[重建系統資料庫](../databases/system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="a31f4-127">[Rebuild System Databases](../databases/system-databases.md) </span></span>  
 <span data-ttu-id="a31f4-128">[Database Engine 服務啟動選項](../../database-engine/configure-windows/database-engine-service-startup-options.md) </span><span class="sxs-lookup"><span data-stu-id="a31f4-128">[Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md) </span></span>  
 <span data-ttu-id="a31f4-129">[SQL Server 組態管理員](../sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a31f4-129">[SQL Server Configuration Manager](../sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="a31f4-130">[系統資料庫的備份與還原 &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a31f4-130">[Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span></span>  
 <span data-ttu-id="a31f4-131">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a31f4-131">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="a31f4-132">以單一使用者模式啟動 SQL Server</span><span class="sxs-lookup"><span data-stu-id="a31f4-132">Start SQL Server in Single-User Mode</span></span>](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
