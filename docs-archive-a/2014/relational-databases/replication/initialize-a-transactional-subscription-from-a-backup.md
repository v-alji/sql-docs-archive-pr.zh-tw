---
title: 從備份初始化交易式訂閱 (複寫 Transact-sql 程式設計) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1563d58f2d54f77680781e22a162112ade1658e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585824"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a><span data-ttu-id="11a07-102">從備份初始化交易式訂閱 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="11a07-102">Initialize a Transactional Subscription from a Backup (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="11a07-103">雖然通常會使用快照集初始化交易式發行集的訂閱，但是可以使用複寫預存程序從備份初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="11a07-103">Although a subscription to a transactional publication is typically initialized with a snapshot, a subscription can be initialized from a backup using replication stored procedures.</span></span> <span data-ttu-id="11a07-104">如需詳細資訊，請參閱 [不使用快照集初始化交易式訂閱](initialize-a-transactional-subscription-without-a-snapshot.md)中手動初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="11a07-104">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a><span data-ttu-id="11a07-105">從備份初始化交易式訂閱者</span><span class="sxs-lookup"><span data-stu-id="11a07-105">To initialize a transactional subscriber from a backup</span></span>  
  
1.  <span data-ttu-id="11a07-106">如果是現有的發行集，請在發行集資料庫的發行者端執行 [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)，以確定此發行集可支援從備份初始化的功能。</span><span class="sxs-lookup"><span data-stu-id="11a07-106">For an existing publication, ensure that the publication supports the ability to initialize from backup by executing [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="11a07-107">請記下結果集中 **allow_initialize_from_backup** 的值。</span><span class="sxs-lookup"><span data-stu-id="11a07-107">Note the value of **allow_initialize_from_backup** in the result set.</span></span>  
  
    -   <span data-ttu-id="11a07-108">如果此值是 **1**，表示發行集支援此功能。</span><span class="sxs-lookup"><span data-stu-id="11a07-108">If the value is **1**, the publication supports this functionality.</span></span>  
  
    -   <span data-ttu-id="11a07-109">如果這個值是 **0**，請在發行集資料庫的發行者端執行 [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="11a07-109">If the value is **0**, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="11a07-110">針對 [ \*\* \@ 屬性**] 指定 [ **allow_initialize_from_backup** ] 的值，並 `true` 針對 [ \*\* \@ 值**] 指定值。</span><span class="sxs-lookup"><span data-stu-id="11a07-110">Specify a value of **allow_initialize_from_backup** for **\@property** and a value of `true` for **\@value**.</span></span>  
  
2.  <span data-ttu-id="11a07-111">如果是新的發行集，請在發行集資料庫的發行者端執行 [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="11a07-111">For a new publication, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="11a07-112">針對 [allow_initialize_from_backup] 指定的值 `true` 。 **allow_initialize_from_backup**</span><span class="sxs-lookup"><span data-stu-id="11a07-112">Specify a value of `true` for **allow_initialize_from_backup**.</span></span> <span data-ttu-id="11a07-113">如需詳細資訊，請參閱[建立發行集](publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="11a07-113">For more information, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="11a07-114">為了避免遺漏訂閱者資料，當您使用 **sp_addpublication** 搭配 `@allow_initialize_from_backup = N'true'`時，請一律使用 `@immediate_sync = N'true'`。</span><span class="sxs-lookup"><span data-stu-id="11a07-114">To avoid missing subscriber data, when using **sp_addpublication** with `@allow_initialize_from_backup = N'true'`, always use `@immediate_sync = N'true'`.</span></span>  
  
3.  <span data-ttu-id="11a07-115">使用 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) 陳述式建立發行集資料庫的備份。</span><span class="sxs-lookup"><span data-stu-id="11a07-115">Create a backup of the publication database using the [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
4.  <span data-ttu-id="11a07-116">使用 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式還原訂閱者上的備份。</span><span class="sxs-lookup"><span data-stu-id="11a07-116">Restore the backup on the Subscriber using the [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
5.  <span data-ttu-id="11a07-117">在發行集資料庫的發行者端，執行預存程序 [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="11a07-117">At the Publisher on the publication database, execute the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="11a07-118">指定下列參數：</span><span class="sxs-lookup"><span data-stu-id="11a07-118">Specify the following parameters:</span></span>  
  
    -   <span data-ttu-id="11a07-119">\*\* \@ sync_type\*\* - **initialize with backup**的值。</span><span class="sxs-lookup"><span data-stu-id="11a07-119">**\@sync_type** - a value of **initialize with backup**.</span></span>  
  
    -   <span data-ttu-id="11a07-120">\*\* \@ backupdevicetype\*\* -備份裝置的類型： [**邏輯** (預設) ]、[**磁片**] 或 [**磁帶**]。</span><span class="sxs-lookup"><span data-stu-id="11a07-120">**\@backupdevicetype** - the type of backup device: **logical** (default), **disk**, or **tape**.</span></span>  
  
    -   <span data-ttu-id="11a07-121">\*\* \@ backupdevicename\*\* -要用於還原的邏輯或實體備份裝置。</span><span class="sxs-lookup"><span data-stu-id="11a07-121">**\@backupdevicename** - the logical or physical backup device to use for the restore.</span></span>  
  
         <span data-ttu-id="11a07-122">如果是邏輯裝置，請指定使用 **sp_addumpdevice** 來建立裝置時所指定的備份裝置名稱。</span><span class="sxs-lookup"><span data-stu-id="11a07-122">For a logical device, specify the name of the backup device specified when **sp_addumpdevice** was used to create the device.</span></span>  
  
         <span data-ttu-id="11a07-123">如果是實體裝置，請指定完整路徑和檔案名稱，例如 `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` 或 `TAPE = '\\.\TAPE0'`。</span><span class="sxs-lookup"><span data-stu-id="11a07-123">For a physical device, specify a complete path and file name, such as `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` or `TAPE = '\\.\TAPE0'`.</span></span>  
  
    -   <span data-ttu-id="11a07-124"> (選擇性的)\ \** \@ 密\碼\**]-建立備份組時所提供的密碼。</span><span class="sxs-lookup"><span data-stu-id="11a07-124">(Optional) **\@password** - a password that was provided when the backup set was created.</span></span>  
  
    -   <span data-ttu-id="11a07-125"> (選擇性)\ \** \@ mediapasswor\d\** -格式化媒體集時所提供的密碼。</span><span class="sxs-lookup"><span data-stu-id="11a07-125">(Optional) **\@mediapassword** - a password that was provided when the media set was formatted.</span></span>  
  
    -   <span data-ttu-id="11a07-126"> (選擇性的)\ \** \@ fileidhin\t\** -要還原之備份組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="11a07-126">(Optional) **\@fileidhint** - identifier for the backup set to be restored.</span></span> <span data-ttu-id="11a07-127">例如，指定 **1** 表示備份媒體上的第一個備份組，指定 **2** 則表示第二個備份組。</span><span class="sxs-lookup"><span data-stu-id="11a07-127">For example, specifying **1** indicates the first backup set on the backup medium and **2** indicates the second backup set.</span></span>  
  
    -   <span data-ttu-id="11a07-128"> (適用于磁帶裝置\的\** \@ 選擇性) 卸載**-指定**1**的值 (預設) 如果在完成還原之後應該從磁片磁碟機卸載磁帶，則為**\0\** （如果不應卸載）。</span><span class="sxs-lookup"><span data-stu-id="11a07-128">(Optional for tape devices) **\@unload** - specify a value of **1** (default) if the tape should be unloaded from the drive after the restore is complete and **0** if it should not be unloaded.</span></span>  
  
6.  <span data-ttu-id="11a07-129">(選擇性) 針對提取訂閱，在訂閱資料庫的訂閱者端執行 [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) 和 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="11a07-129">(Optional) For a pull subscription, execute [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) and [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) at the Subscriber on the subscription database.</span></span> <span data-ttu-id="11a07-130">如需詳細資訊，請參閱 [建立提取訂閱](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="11a07-130">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
7.  <span data-ttu-id="11a07-131">(選擇性) 啟動散發代理程式。</span><span class="sxs-lookup"><span data-stu-id="11a07-131">(Optional) Start the Distribution Agent.</span></span> <span data-ttu-id="11a07-132">如需相關資訊，請參閱 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) 或 [Synchronize a Push Subscription](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="11a07-132">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) or [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a07-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11a07-133">See Also</span></span>  
 <span data-ttu-id="11a07-134">[使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="11a07-134">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="11a07-135">SQL Server 資料庫的備份與還原</span><span class="sxs-lookup"><span data-stu-id="11a07-135">Back Up and Restore of SQL Server Databases</span></span>](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
