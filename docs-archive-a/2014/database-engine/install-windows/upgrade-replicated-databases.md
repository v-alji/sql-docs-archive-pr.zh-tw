---
title: 升級複寫的資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- merge replication database upgrades [SQL Server replication]
- replication [SQL Server], upgrading
- transactional replication, upgrading databases
- snapshot replication [SQL Server], upgrading databases
- upgrading replicated databases
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 326a94820876b40128428aac58e47c650ce122b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594147"
---
# <a name="upgrade-replicated-databases"></a><span data-ttu-id="0b48f-102">升級複寫的資料庫</span><span class="sxs-lookup"><span data-stu-id="0b48f-102">Upgrade Replicated Databases</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="0b48f-103">支援從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級複寫資料庫。升級節點時，不需要停止其他節點上的活動。</span><span class="sxs-lookup"><span data-stu-id="0b48f-103">supports upgrading replicated databases from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; it is not required to stop activity at other nodes while a node is being upgraded.</span></span> <span data-ttu-id="0b48f-104">請確定您遵守有關拓撲中支援之版本的規則：</span><span class="sxs-lookup"><span data-stu-id="0b48f-104">Ensure that you adhere to the rules regarding which versions are supported in a topology:</span></span>  
  
-   <span data-ttu-id="0b48f-105">散發者可以是任何版本，只要其高於或等於發行者版本 (在許多情況下，散發者與發行者為同一執行個體)。</span><span class="sxs-lookup"><span data-stu-id="0b48f-105">A Distributor can be any version as long as it is greater than or equal to the Publisher version (in many cases the Distributor is the same instance as the Publisher).</span></span>  
  
-   <span data-ttu-id="0b48f-106">發行者可以是任何版本，只要它小於或等於散發者版本即可。</span><span class="sxs-lookup"><span data-stu-id="0b48f-106">A Publisher can be any version as long as it less than or equal to the Distributor version.</span></span>  
  
-   <span data-ttu-id="0b48f-107">訂閱者版本視發行集的類型而定：</span><span class="sxs-lookup"><span data-stu-id="0b48f-107">Subscriber version depends on the type of publication:</span></span>  
  
    -   <span data-ttu-id="0b48f-108">交易式發行集的訂閱者可以是兩個發行者版本內的任何版本。</span><span class="sxs-lookup"><span data-stu-id="0b48f-108">A Subscriber to a transactional publication can be any version within two versions of the Publisher version.</span></span> <span data-ttu-id="0b48f-109">例如：執行中的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 發行者可以有 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 訂閱者，而 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 發行者可以有 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 訂閱者。</span><span class="sxs-lookup"><span data-stu-id="0b48f-109">For example: a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Publisher running can have [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Subscribers; and a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Publisher can have [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Subscribers.</span></span>  
  
    -   <span data-ttu-id="0b48f-110">合併式發行集的訂閱者可以是小於或等於發行者版本的任何版本。</span><span class="sxs-lookup"><span data-stu-id="0b48f-110">A Subscriber to a merge publication can be any version less than or equal to the Publisher version.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b48f-111">有關這個主題，請參閱「安裝說明」文件集和《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="0b48f-111">This topic is available in the Setup Help documentation and in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="0b48f-112">在「安裝說明」文件集中，以粗體文字表示的主題連結只會參考線上叢書中的主題。</span><span class="sxs-lookup"><span data-stu-id="0b48f-112">Topic links that appear as bold text in the Setup Help documentation refer to topics that are only available in Books Online.</span></span>  
  
## <a name="run-the-log-reader-agent-for-transactional-replication-before-upgrade"></a><span data-ttu-id="0b48f-113">在升級之前執行異動複寫的記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="0b48f-113">Run the Log Reader Agent for Transactional Replication Before Upgrade</span></span>  
 <span data-ttu-id="0b48f-114">在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之前，您必須確定所有來自已發行資料表的認可交易都已經由記錄讀取器代理程式進行過處理。</span><span class="sxs-lookup"><span data-stu-id="0b48f-114">Before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must make sure that all committed transactions from published tables have been processed by the Log Reader Agent.</span></span> <span data-ttu-id="0b48f-115">若要確定已經處理過所有交易，請針對每個包含交易式發行集的資料庫執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0b48f-115">To make sure that all transactions have been processed, perform the following steps for each database that contains transactional publications:</span></span>  
  
1.  <span data-ttu-id="0b48f-116">確定已在針對資料庫執行記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="0b48f-116">Make sure that the Log Reader Agent is running for the database.</span></span> <span data-ttu-id="0b48f-117">依預設，代理程式會持續執行。</span><span class="sxs-lookup"><span data-stu-id="0b48f-117">By default, the agent runs continuously.</span></span>  
  
2.  <span data-ttu-id="0b48f-118">停止在已發行資料表上的使用者活動。</span><span class="sxs-lookup"><span data-stu-id="0b48f-118">Stop user activity on published tables.</span></span>  
  
3.  <span data-ttu-id="0b48f-119">提供時間讓記錄讀取器代理程式將交易複製到散發資料庫，然後再停止代理程式。</span><span class="sxs-lookup"><span data-stu-id="0b48f-119">Allow time for the Log Reader Agent to copy transactions to the distribution database, and then stop the agent.</span></span>  
  
4.  <span data-ttu-id="0b48f-120">執行 [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) 以確認已處理所有的交易。</span><span class="sxs-lookup"><span data-stu-id="0b48f-120">Execute [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) to verify that all transactions have been processed.</span></span> <span data-ttu-id="0b48f-121">這個程序中所產生的結果集應該是空的。</span><span class="sxs-lookup"><span data-stu-id="0b48f-121">The result set from this procedure should be empty.</span></span>  
  
5.  <span data-ttu-id="0b48f-122">執行 [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) 以關閉 sp_replcmds 的連接。</span><span class="sxs-lookup"><span data-stu-id="0b48f-122">Execute [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) to close the connection from sp_replcmds.</span></span>  
  
6.  <span data-ttu-id="0b48f-123">將伺服器升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b48f-123">Perform the server upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
7.  <span data-ttu-id="0b48f-124">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 和記錄讀取器代理程式在升級之後沒有自動啟動，則將其重新啟動。</span><span class="sxs-lookup"><span data-stu-id="0b48f-124">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and the Log Reader Agent if they do not start automatically after the upgrade.</span></span>  
  
## <a name="run-agents-for-merge-replication-after-upgrade"></a><span data-ttu-id="0b48f-125">升級之後為合併式複寫執行代理程式</span><span class="sxs-lookup"><span data-stu-id="0b48f-125">Run Agents for Merge Replication After Upgrade</span></span>  
 <span data-ttu-id="0b48f-126">升級之後，請為每一個合併式發行集執行快照集代理程式，並為每一個訂閱執行合併代理程式來更新複寫中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0b48f-126">After upgrade, run the Snapshot Agent for each merge publication and the Merge Agent for each subscription to update replication metadata.</span></span> <span data-ttu-id="0b48f-127">您不必套用新的快照集，因為不需要重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="0b48f-127">You do not have to apply the new snapshot, because it is not necessary to reinitialize subscriptions.</span></span> <span data-ttu-id="0b48f-128">升級之後，第一次執行合併代理程式時會更新訂閱中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0b48f-128">Subscription metadata is updated the first time the Merge Agent is run after upgrade.</span></span> <span data-ttu-id="0b48f-129">這表示在發行者升級時，訂閱資料庫可以持續在線上運作並保持使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="0b48f-129">This means that the subscription database can remain online and active during the Publisher upgrade.</span></span>  
  
 <span data-ttu-id="0b48f-130">合併式複寫會將發行集與訂閱中繼資料儲存在發行集與訂閱資料庫中的許多系統資料表內。</span><span class="sxs-lookup"><span data-stu-id="0b48f-130">Merge replication stores publication and subscription metadata in a number of system tables in the publication and subscription databases.</span></span> <span data-ttu-id="0b48f-131">執行快照集代理程式會更發行集中繼資料，而執行合併代理程式會更新訂閱中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0b48f-131">Running the Snapshot Agent updates publication metadata and running the Merge Agent updates subscription metadata.</span></span> <span data-ttu-id="0b48f-132">只有要產生發行集快照集時才需要它。</span><span class="sxs-lookup"><span data-stu-id="0b48f-132">It is only required to generate a publication snapshot.</span></span> <span data-ttu-id="0b48f-133">如果合併式發行集使用參數化篩選，則每個資料分割也會有快照集。</span><span class="sxs-lookup"><span data-stu-id="0b48f-133">If a merge publication uses parameterized filters, each partition also has a snapshot.</span></span> <span data-ttu-id="0b48f-134">您不需要更新這些分割快照集</span><span class="sxs-lookup"><span data-stu-id="0b48f-134">It is not necessary to update these partitioned snapshots.</span></span>  
  
 <span data-ttu-id="0b48f-135">您可以從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、複寫監視器或命令列執行代理程式。</span><span class="sxs-lookup"><span data-stu-id="0b48f-135">Run the agents from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Replication Monitor, or from the command line.</span></span> <span data-ttu-id="0b48f-136">如需有關執行快照集代理程式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="0b48f-136">For more information about running the Snapshot Agent, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0b48f-137">建立和套用初始快照集</span><span class="sxs-lookup"><span data-stu-id="0b48f-137">Create and Apply the Initial Snapshot</span></span>](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [<span data-ttu-id="0b48f-138">啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0b48f-138">Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="0b48f-139">建立和套用初始快照集</span><span class="sxs-lookup"><span data-stu-id="0b48f-139">Create and Apply the Initial Snapshot</span></span>](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [<span data-ttu-id="0b48f-140">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="0b48f-140">Replication Agent Executables Concepts</span></span>](../../../2014/relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 <span data-ttu-id="0b48f-141">如需有關執行合併代理程式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="0b48f-141">For more information about running the Merge Agent, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0b48f-142">同步處理提取訂閱</span><span class="sxs-lookup"><span data-stu-id="0b48f-142">Synchronize a Pull Subscription</span></span>](../../../2014/relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [<span data-ttu-id="0b48f-143">同步處理發送訂閱</span><span class="sxs-lookup"><span data-stu-id="0b48f-143">Synchronize a Push Subscription</span></span>](../../../2014/relational-databases/replication/synchronize-a-push-subscription.md)  
  
 <span data-ttu-id="0b48f-144">在使用合併式複寫的拓撲中升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後，如果您想要使用新功能，請變更任何發行集的發行集相容性層級。</span><span class="sxs-lookup"><span data-stu-id="0b48f-144">After upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a topology that uses merge replication, change the publication compatibility level of any publications if you want to use new features.</span></span>  
  
## <a name="upgrading-to-standard-workgroup-or-express-editions"></a><span data-ttu-id="0b48f-145">升級至 Standard、Workgroup 或 Express Edition</span><span class="sxs-lookup"><span data-stu-id="0b48f-145">Upgrading to Standard, Workgroup, or Express Editions</span></span>  
 <span data-ttu-id="0b48f-146">從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的一個版本升級到另一個版本之前，請確認您目前使用的功能在您想要升級後的版本中受到支援。</span><span class="sxs-lookup"><span data-stu-id="0b48f-146">Before upgrading from one edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to another, verify that the functionality you are currently using is supported in the edition to which you are upgrading.</span></span> <span data-ttu-id="0b48f-147">如需詳細資訊，請參閱[SQL Server 2014 版本支援的功能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)中的複寫一節。</span><span class="sxs-lookup"><span data-stu-id="0b48f-147">For more information, see the section on Replication in [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="web-synchronization-for-merge-replication"></a><span data-ttu-id="0b48f-148">合併式複寫的 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="0b48f-148">Web Synchronization for Merge Replication</span></span>  
 <span data-ttu-id="0b48f-149">合併式複寫的 Web 同步處理選項要求，必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (replisapi.dll) 複製到用於同步處理之 Internet Information Services (IIS) 伺服器上的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="0b48f-149">The Web synchronization option for merge replication requires that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (replisapi.dll) be copied to the virtual directory on the Internet Information Services (IIS) server used for synchronization.</span></span> <span data-ttu-id="0b48f-150">當您設定 Web 同步處理時，「設定 Web 同步處理精靈」會將檔案複製到虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="0b48f-150">When you configure Web synchronization, the file is copied to the virtual directory by the Configure Web Synchronization Wizard.</span></span> <span data-ttu-id="0b48f-151">如果您升級安裝在 IIS 伺服器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件，就必須將 replisapi.dll 從 COM 目錄手動複製到 IIS 伺服器上的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="0b48f-151">If you upgrade the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components installed on the IIS server, you must manually copy replisapi.dll from the COM directory to the virtual directory on the IIS server.</span></span> <span data-ttu-id="0b48f-152">如需設定 Web 同步處理的詳細資訊，請參閱 [設定 Web 同步處理](../../../2014/relational-databases/replication/configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="0b48f-152">For more information about configuring Web synchronization, see [Configure Web Synchronization](../../../2014/relational-databases/replication/configure-web-synchronization.md).</span></span>  
  
## <a name="restoring-a-replicated-database-from-an-earlier-version"></a><span data-ttu-id="0b48f-153">從舊版還原複寫的資料庫</span><span class="sxs-lookup"><span data-stu-id="0b48f-153">Restoring a Replicated Database from an Earlier Version</span></span>  
 <span data-ttu-id="0b48f-154">若要確定從舊版還原複寫資料庫的備份時有保留複寫設定：還原到與建立備份的伺服器和資料庫同名的伺服器和資料庫。</span><span class="sxs-lookup"><span data-stu-id="0b48f-154">To ensure replication settings are retained when restoring a backup of a replicated database from a previous version: restore to a server and database with the same names as the server and database at which the backup was taken.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b48f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b48f-155">See Also</span></span>  
 <span data-ttu-id="0b48f-156">[複寫管理常見問題集](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="0b48f-156">[Replication Administration FAQ](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="0b48f-157">[複寫回溯相容性](../../../2014/relational-databases/replication/replication-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="0b48f-157">[Replication Backward Compatibility](../../../2014/relational-databases/replication/replication-backward-compatibility.md) </span></span>  
 <span data-ttu-id="0b48f-158">[支援的版本與版本升級](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="0b48f-158">[Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 [<span data-ttu-id="0b48f-159">升級為 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="0b48f-159">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
  
  
