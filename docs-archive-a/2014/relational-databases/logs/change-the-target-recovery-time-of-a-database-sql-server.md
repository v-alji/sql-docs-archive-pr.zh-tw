---
title: 變更資料庫的目標復原時間 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c4331d2ade2819d172189a0de9daddecf3d9f6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594548"
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a><span data-ttu-id="2dcbe-102">變更資料庫的目標復原時間 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dcbe-102">Change the Target Recovery Time of a Database (SQL Server)</span></span>
  <span data-ttu-id="2dcbe-103">本主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中設定或變更 [!INCLUDE[tsql](../../includes/tsql-md.md)]資料庫的目標復原時間。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-103">This topic describes how to set the change the target recovery time of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2dcbe-104">根據預設，目標復原時間為 0，而且資料庫會使用 *「自動檢查點」* (Automatic Checkpoint) (由 **recovery interval** 伺服器選項控制)。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-104">By default, the target recovery time is 0, and the database uses *automatic checkpoints* (which are controlled by the **recovery interval** server option).</span></span> <span data-ttu-id="2dcbe-105">如果將目標復原時間設定為大於 0，就會導致資料庫使用 *「間接檢查點」* (Indirect-Checkpoint) 並且建立這個資料庫的復原時間上限。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-105">Setting the target recovery time to greater than 0 causes the database to use the *indirect-checkpoints* and establishes an upper-bound on recovery time for this database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2dcbe-106">如果長時間執行的交易造成過多的復原次數，可能會超過目標復原時間設定針對給定資料庫所指定的上限。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-106">The upper-bound that is specified for a given database by its target recovery time setting could be exceeded if a long-running transaction causes excessive UNDO times.</span></span>  
  
-   <span data-ttu-id="2dcbe-107">**開始之前：** [限制事項](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="2dcbe-107">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="2dcbe-108">**使用以下方式變更目標復原時間：** [SQL Server Management Studio](#SSMSProcedure) 或 [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="2dcbe-108">**To change the target recovery time, using:**  [SQL Server Management Studio](#SSMSProcedure) or [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2dcbe-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="2dcbe-109">Before You Begin</span></span>  
  
###  <a name="Restrictions"></a>  
  
> [!CAUTION]  
>  <span data-ttu-id="2dcbe-110">設定間接檢查點的資料庫線上交易式工作負載可能會導致效能降低。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-110">An online transactional workload on a database that is configured for indirect checkpoints could experience performance degradation.</span></span> <span data-ttu-id="2dcbe-111">間接檢查點可確定中途分頁的數目，低於特定臨界值，如此即可在目標復原時間內完成資料庫的復原。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-111">Indirect checkpoints make sure that the number of dirty pages are below a certain threshold so that the database recovery completes within the target recovery time.</span></span> <span data-ttu-id="2dcbe-112">復原間隔組態選項會使用異動數目來判斷復原時間，而間接檢查點則是會利用中途分頁數目來判斷復原時間。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-112">The recovery interval configuration option uses the number of transactions to determine the recovery time as opposed to indirect checkpoints which makes use of number of dirty pages.</span></span> <span data-ttu-id="2dcbe-113">在收到大量 DML 作業的資料庫上啟用間接檢查點時，背景寫入器可開始積極排清磁碟的中途緩衝區，以確保執行復原所需的時間，落在資料庫所設的目標復原時間內。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-113">When indirect checkpoints are enabled on a database receiving a large number of DML operations, the background writer can start aggressively flushing dirty buffers to disk to ensure that the time required to perform recovery is within the target recovery time set of the database.</span></span> <span data-ttu-id="2dcbe-114">如此會在某些系統上造成額外的 I/O 活動，而若磁碟子系統的運作超過或接近 I/O 臨界值，就會形成效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-114">This can cause additional I/O activity on certain systems which can contribute to a performance bottleneck if the disk subsystem is operating above or nearing the I/O threshold.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2dcbe-115">Security</span><span class="sxs-lookup"><span data-stu-id="2dcbe-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2dcbe-116">權限</span><span class="sxs-lookup"><span data-stu-id="2dcbe-116">Permissions</span></span>  
 <span data-ttu-id="2dcbe-117">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2dcbe-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2dcbe-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2dcbe-119">**若要變更目標復原時間**</span><span class="sxs-lookup"><span data-stu-id="2dcbe-119">**To change the target recovery time**</span></span>  
  
1.  <span data-ttu-id="2dcbe-120">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and expand that instance.</span></span>  
  
2.  <span data-ttu-id="2dcbe-121">以滑鼠右鍵按一下您想要變更的資料庫，然後按一下 [屬性] \*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-121">Right-click the database you want to change, and click the **Properties** command.</span></span>  
  
3.  <span data-ttu-id="2dcbe-122">在 [資料庫屬性]  對話方塊中按一下 [選項]  頁面。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-122">In the **Database Properties** dialog box, click the **Options** page.</span></span>  
  
4.  <span data-ttu-id="2dcbe-123">在 [復原] \*\*\*\* 面板的 [目標復原時間 (秒)] \*\*\*\* 欄位中，指定您想要設定為這個資料庫之復原時間上限的秒數。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-123">In the **Recovery** panel, in the **Target Recovery Time (Seconds)** field, specify the number of seconds that you want as the upper-bound on the recovery time for this database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2dcbe-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2dcbe-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="2dcbe-125">**若要變更目標復原時間**</span><span class="sxs-lookup"><span data-stu-id="2dcbe-125">**To change the target recovery time**</span></span>  
  
1.  <span data-ttu-id="2dcbe-126">連接到資料庫所在的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-126">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the database resides.</span></span>  
  
2.  <span data-ttu-id="2dcbe-127">使用下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2dcbe-127">Use the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)statement, as follows:</span></span>  
  
     <span data-ttu-id="2dcbe-128">TARGET_RECOVERY_TIME **=** _target_recovery_time_ { SECONDS | MINUTES }</span><span class="sxs-lookup"><span data-stu-id="2dcbe-128">TARGET_RECOVERY_TIME **=**_target_recovery_time_ { SECONDS | MINUTES }</span></span>  
  
     <span data-ttu-id="2dcbe-129">*目標復原時間*</span><span class="sxs-lookup"><span data-stu-id="2dcbe-129">*target_recovery_time*</span></span>  
     <span data-ttu-id="2dcbe-130">如果大於 0 (預設值)，便指定發生損毀時，指定之資料庫的復原時間上限。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-130">When greater than 0 (the default), specifies the upper-bound on the recovery time for the specified database in the event of a crash.</span></span>  
  
     <span data-ttu-id="2dcbe-131">SECONDS</span><span class="sxs-lookup"><span data-stu-id="2dcbe-131">SECONDS</span></span>  
     <span data-ttu-id="2dcbe-132">指出 *target_recovery_time* 應以秒數表示。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-132">Indicates that *target_recovery_time* is expressed as the number of seconds.</span></span>  
  
     <span data-ttu-id="2dcbe-133">MINUTES</span><span class="sxs-lookup"><span data-stu-id="2dcbe-133">MINUTES</span></span>  
     <span data-ttu-id="2dcbe-134">指出 *target_recovery_time* 應以分鐘數表示。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-134">Indicates that *target_recovery_time* is expressed as the number of minutes.</span></span>  
  
     <span data-ttu-id="2dcbe-135">下列範例會將 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的目標復原時間設定為 `60` 秒。</span><span class="sxs-lookup"><span data-stu-id="2dcbe-135">The following example sets the target recovery time of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to `60` seconds.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2dcbe-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dcbe-136">See Also</span></span>  
 <span data-ttu-id="2dcbe-137">[資料庫檢查點 &#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2dcbe-137">[Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span></span>  
 [<span data-ttu-id="2dcbe-138">ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcbe-138">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
