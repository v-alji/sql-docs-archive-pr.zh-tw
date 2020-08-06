---
title: 作用中次要資料庫： (Always On 可用性群組的次要複本上備份) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0cf899cdbeb1ae4ede6c9196b8eb93a9d9e54f05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701941"
---
# <a name="active-secondaries-backup-on-secondary-replicas-always-on-availability-groups"></a><span data-ttu-id="bce63-102">使用中次要：在次要複本上備份 (AlwaysOn 可用性群組)</span><span class="sxs-lookup"><span data-stu-id="bce63-102">Active Secondaries: Backup on Secondary Replicas (Always On Availability Groups)</span></span>
  <span data-ttu-id="bce63-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 使用中次要功能包含對次要複本執行備份作業的支援。</span><span class="sxs-lookup"><span data-stu-id="bce63-103">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] active secondary capabilities include support for performing backup operations on secondary replicas.</span></span> <span data-ttu-id="bce63-104">備份作業可能會對 I/O 和 CPU 造成相當大的壓力 (備份壓縮已啟用時)。</span><span class="sxs-lookup"><span data-stu-id="bce63-104">Backup operations can put significant strain on I/O and CPU (with backup compression).</span></span> <span data-ttu-id="bce63-105">將備份卸載至已同步處理或正在同步處理的次要複本，可讓裝載主要複本的伺服器執行個體上的資源用於第 1 層工作負載。</span><span class="sxs-lookup"><span data-stu-id="bce63-105">Offloading backups to a synchronized or synchronizing secondary replica allows you to use the resources on server instance that hosts the primary replica for your tier-1 workloads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bce63-106">不可對可用性群組的主要或次要資料庫執行 RESTORE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bce63-106">RESTORE statements are not allowed on either the primary or secondary databases of an availability group.</span></span>  
  
  
  
##  <a name="backup-types-supported-on-secondary-replicas"></a><a name="SupportedBuTypes"></a> <span data-ttu-id="bce63-107">次要複本支援的備份類型</span><span class="sxs-lookup"><span data-stu-id="bce63-107">Backup Types Supported on Secondary Replicas</span></span>  
  
-   <span data-ttu-id="bce63-108">`BACKUP DATABASE` 只有在次要複本上執行時，才支援資料庫、檔案或檔案群組的只複製完整備份。</span><span class="sxs-lookup"><span data-stu-id="bce63-108">`BACKUP DATABASE` supports only copy-only full backups of databases, files, or filegroups when it is executed on secondary replicas.</span></span> <span data-ttu-id="bce63-109">請注意，只複製備份不會影響記錄檔鏈結或清除差異式點陣圖。</span><span class="sxs-lookup"><span data-stu-id="bce63-109">Note that copy-only backups do not impact the log chain or clear the differential bitmap.</span></span>  
  
-   <span data-ttu-id="bce63-110">次要複本不支援差異備份。</span><span class="sxs-lookup"><span data-stu-id="bce63-110">Differential backups are not supported on secondary replicas.</span></span>  
  
-   <span data-ttu-id="bce63-111">**BACKUP LOG** 只支援一般記錄備份 (次要複本的記錄備份不支援 COPY_ONLY 選項)。</span><span class="sxs-lookup"><span data-stu-id="bce63-111">**BACKUP LOG** supports only regular log backups (the COPY_ONLY option is not supported for log backups on secondary replicas).</span></span>  
  
     <span data-ttu-id="bce63-112">跨任何複本 (主要或次要) 上所做的記錄檔備份可確保記錄檔鏈結一致，無論其可用性模式為何 (同步認可或非同步認可)。</span><span class="sxs-lookup"><span data-stu-id="bce63-112">A consistent log chain is ensured across log backups taken on any of the replicas (primary or secondary), irrespective of their availability mode (synchronous-commit or asynchronous-commit).</span></span>  
  
-   <span data-ttu-id="bce63-113">若要備份次要資料庫，次要複本必須能夠與主要複本通訊，而且必須處於 `SYNCHRONIZED` 或 `SYNCHRONIZING` 狀態。</span><span class="sxs-lookup"><span data-stu-id="bce63-113">To back up a secondary database, a secondary replica must be able to communicate with the primary replica and must be `SYNCHRONIZED` or `SYNCHRONIZING`.</span></span>  
  
##  <a name="configuring-where-backup-jobs-run"></a><a name="WhereBuJobsRun"></a><span data-ttu-id="bce63-114">設定執行備份作業的位置</span><span class="sxs-lookup"><span data-stu-id="bce63-114">Configuring Where Backup Jobs Run</span></span>  
 <span data-ttu-id="bce63-115">在次要複本執行備份，以便從主要實際執行伺服器卸載備份工作負載，是一極大的好處。</span><span class="sxs-lookup"><span data-stu-id="bce63-115">Performing backups on a secondary replica to offload the backup workload from the primary production server is a great benefit.</span></span> <span data-ttu-id="bce63-116">不過，在次要複本上執行備份會讓決定是否應該執行備份作業的程序複雜許多。</span><span class="sxs-lookup"><span data-stu-id="bce63-116">However, performing backups on secondary replicas introduce significant complexity to the process of determining where backup jobs should run.</span></span> <span data-ttu-id="bce63-117">若要解決這個問題，請依照以下方式設定執行備份作業的位置：</span><span class="sxs-lookup"><span data-stu-id="bce63-117">To address this, configure where backup jobs run as follows:</span></span>  
  
1.  <span data-ttu-id="bce63-118">設定可用性群組來指定您想要在哪些可用性複本執行備份。</span><span class="sxs-lookup"><span data-stu-id="bce63-118">Configure the availability group to specify which availability replicas where you would prefer backups to be performed.</span></span> <span data-ttu-id="bce63-119">如需詳細資訊，請參閱 *CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;* 或 *ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;* 的 [CREATE AVAILABILITY GROUP &amp;#40;Transact-SQL&amp;#41;](/sql/t-sql/statements/create-availability-group-transact-sql) 或 [ALTER AVAILABILITY GROUP &amp;#40;Transact-SQL&amp;#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)狀態。</span><span class="sxs-lookup"><span data-stu-id="bce63-119">For more information, see *AUTOMATED_BACKUP_PREFERENCE* and *BACKUP_PRIORITY* parameters in [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) or [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
2.  <span data-ttu-id="bce63-120">在裝載可用性複本的每個伺服器執行個體，而此可用性複本是執行備份的候選複本，為每個可用性資料庫建立已編寫指令碼的備份作業。</span><span class="sxs-lookup"><span data-stu-id="bce63-120">Create scripted backup jobs for every availability database on every server instance that hosts an availability replica that is a candidate for performing backups.</span></span> <span data-ttu-id="bce63-121">如需詳細資訊，請參閱 [設定可用性複本的備份 &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)狀態。</span><span class="sxs-lookup"><span data-stu-id="bce63-121">For more information, see the "Follow Up: After Configuring Backup on Secondary Replicas" section of [Configure Backup on Availability Replicas &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="bce63-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="bce63-122">Related Tasks</span></span>  
 <span data-ttu-id="bce63-123">**若要設定次要複本的備份**</span><span class="sxs-lookup"><span data-stu-id="bce63-123">**To configure backup on secondary replicas**</span></span>  
  
-   [<span data-ttu-id="bce63-124">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bce63-124">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
 <span data-ttu-id="bce63-125">**若要判斷目前的複本是否為慣用的備份複本**</span><span class="sxs-lookup"><span data-stu-id="bce63-125">**To determine whether the current replica is the preferred backup replica**</span></span>  
  
-   [<span data-ttu-id="bce63-126">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="bce63-126">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 <span data-ttu-id="bce63-127">**若要建立備份作業**</span><span class="sxs-lookup"><span data-stu-id="bce63-127">**To create a backup job**</span></span>  
  
-   [<span data-ttu-id="bce63-128">使用維護計畫精靈</span><span class="sxs-lookup"><span data-stu-id="bce63-128">Use the Maintenance Plan Wizard</span></span>](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [<span data-ttu-id="bce63-129">實作作業</span><span class="sxs-lookup"><span data-stu-id="bce63-129">Implement Jobs</span></span>](../../../ssms/agent/implement-jobs.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="bce63-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bce63-130">See Also</span></span>  
 <span data-ttu-id="bce63-131">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bce63-131">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="bce63-132">[只複製備份 &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bce63-132">[Copy-Only Backups &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md) </span></span>  
 <span data-ttu-id="bce63-133">[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bce63-133">[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) </span></span>  
 [<span data-ttu-id="bce63-134">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bce63-134">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
