---
title: 將整個企業的管理自動化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8df3e34c2c70c81f9710ade0d6855446b930fb50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597552"
---
# <a name="automated-administration-across-an-enterprise"></a><span data-ttu-id="57828-102">將整個企業的管理自動化</span><span class="sxs-lookup"><span data-stu-id="57828-102">Automated Administration Across an Enterprise</span></span>
  <span data-ttu-id="57828-103">將多個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之間的管理自動化，稱為「多伺服器管理」\*\*(Multiserver Administration)。</span><span class="sxs-lookup"><span data-stu-id="57828-103">Automating administration across multiple instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is called *multiserver administration*.</span></span> <span data-ttu-id="57828-104">使用多伺服器管理，可進行以下工作：</span><span class="sxs-lookup"><span data-stu-id="57828-104">Use multiserver administration to do the following:</span></span>  
  
-   <span data-ttu-id="57828-105">管理二或多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="57828-105">Manage two or more servers.</span></span>  
  
-   <span data-ttu-id="57828-106">為企業伺服器之間的資訊流程進行排程以作為資料倉儲之用。</span><span class="sxs-lookup"><span data-stu-id="57828-106">Schedule information flows between enterprise servers for data warehousing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57828-107">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 持續努力減少整體擁有成本的過程中，[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 導入了兩項功能：稱為「原則式管理」的管理伺服器方法，以及使用組態伺服器和伺服器群組的多伺服器查詢。</span><span class="sxs-lookup"><span data-stu-id="57828-107">As part of [!INCLUDE[msCoName](../../includes/msconame-md.md)] ongoing efforts to reduce the total cost of ownership, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduced two features:  a method of managing servers that is called Policy-Based Management, and multiserver queries that use configuration servers and server groups.</span></span> <span data-ttu-id="57828-108">這些功能可以搭配本主題所描述的某些功能使用，也可以取代這些功能。</span><span class="sxs-lookup"><span data-stu-id="57828-108">These features can be used with, or instead of, some of the features that are described in this topic.</span></span> <span data-ttu-id="57828-109">如需詳細資訊，請參閱[使用以原則為基礎的管理來管理伺服器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)和[使用中央管理伺服器管理多部伺服器](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="57828-109">For more information, see [Administer Servers by Using Policy-Based Management](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) and [Administer Multiple Servers Using Central Management Servers](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).</span></span>  
  
 <span data-ttu-id="57828-110">若要利用多伺服器管理，您至少要有一部主要伺服器與一部目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="57828-110">To take advantage of multiserver administration, you must have at least one master server and at least one target server.</span></span> <span data-ttu-id="57828-111">主要伺服器會將作業散發到目標伺服器，並接收目標伺服器傳回的事件。</span><span class="sxs-lookup"><span data-stu-id="57828-111">A master server distributes jobs to, and receives events from, target servers.</span></span> <span data-ttu-id="57828-112">對於目標伺服器上執行的作業，主要伺服器也會儲存其作業定義的集中副本。</span><span class="sxs-lookup"><span data-stu-id="57828-112">A master server also stores the central copy of job definitions for jobs that are run on target servers.</span></span> <span data-ttu-id="57828-113">目標伺服器則會定期連接到主要伺服器，以更新其作業排程。</span><span class="sxs-lookup"><span data-stu-id="57828-113">Target servers connect periodically to the master server to update their schedule of jobs.</span></span> <span data-ttu-id="57828-114">如果主要伺服器上有新的作業，目標伺服器便會下載該作業。</span><span class="sxs-lookup"><span data-stu-id="57828-114">If a new job exists on the master server, the target server downloads the job.</span></span> <span data-ttu-id="57828-115">當目標伺服器完成作業後，它就會重新連接到主要伺服器並報告作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="57828-115">After the target server completes the job, it reconnects to the master server and reports the status of the job.</span></span>  
  
 <span data-ttu-id="57828-116">下圖顯示主要伺服器和目標伺服器之間的關係：</span><span class="sxs-lookup"><span data-stu-id="57828-116">The following illustration shows the relationship between master and target servers:</span></span>  
  
 <span data-ttu-id="57828-117">![多伺服器管理組態](../../database-engine/media/multisvr.gif "多伺服器管理組態")</span><span class="sxs-lookup"><span data-stu-id="57828-117">![Multiserver administration configuration](../../database-engine/media/multisvr.gif "Multiserver administration configuration")</span></span>  
  
 <span data-ttu-id="57828-118">如果您負責管理大型公司的部門伺服器，您可以定義下列項目：</span><span class="sxs-lookup"><span data-stu-id="57828-118">If you administer departmental servers across a large corporation, you can define the following:</span></span>  
  
-   <span data-ttu-id="57828-119">含多個作業步驟的備份作業。</span><span class="sxs-lookup"><span data-stu-id="57828-119">One backup job with job steps.</span></span>  
  
-   <span data-ttu-id="57828-120">發生備份失敗狀況時要通知的操作員。</span><span class="sxs-lookup"><span data-stu-id="57828-120">Operators to notify in case of backup failure.</span></span>  
  
-   <span data-ttu-id="57828-121">備份作業的執行排程。</span><span class="sxs-lookup"><span data-stu-id="57828-121">An execution schedule for the backup job.</span></span>  
  
 <span data-ttu-id="57828-122">請在主要伺服器上撰寫一次這個備份作業，然後將每個部門伺服器都編列為目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="57828-122">Write this backup job one time on the master server and then enlist each departmental server as a target server.</span></span> <span data-ttu-id="57828-123">一旦您將這些伺服器編列上去以後，所有的部門伺服器都會執行同一個備份作業，而您只需定義一次作業。</span><span class="sxs-lookup"><span data-stu-id="57828-123">From the time of their enlistment, all the departmental servers run the same backup job, yet you defined the job only once.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57828-124">多伺服器管理功能是提供給 sysadmin 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="57828-124">Multiserver administration features are intended for members of the sysadmin role.</span></span> <span data-ttu-id="57828-125">但是，目標伺服器上的 sysadmin 角色成員，不能編輯主要伺服器在目標伺服器上所執行的作業。</span><span class="sxs-lookup"><span data-stu-id="57828-125">However, a member of the sysadmin role on the target server cannot edit the operations that are performed on the target server by the master server.</span></span> <span data-ttu-id="57828-126">這個安全性措施避免意外刪除作業步驟，防止目標伺服器上的作業中斷。</span><span class="sxs-lookup"><span data-stu-id="57828-126">This security measure prevents job steps from being accidentally deleted and operations on the target server from being interrupted.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57828-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="57828-127">In This Section</span></span>  
 [<span data-ttu-id="57828-128">建立多伺服器環境</span><span class="sxs-lookup"><span data-stu-id="57828-128">Create a Multiserver Environment</span></span>](create-a-multiserver-environment.md)  
 <span data-ttu-id="57828-129">包含如何建立與管理主要伺服器及目標伺服器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="57828-129">Contains information about how to create and manage master and target servers.</span></span>  
  
 [<span data-ttu-id="57828-130">為多伺服器環境選擇適當的 SQL Server Agent 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="57828-130">Choose the Right SQL Server Agent Service Account for Multiserver Environments</span></span>](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 <span data-ttu-id="57828-131">包含針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服務使用非管理的 Windows 帳戶或「本機系統」帳戶，會如何影響多伺服器環境的資訊。</span><span class="sxs-lookup"><span data-stu-id="57828-131">Contains information about how using nonadministrative Windows accounts or the Local System account for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service can affect multiserver environments.</span></span>  
  
 [<span data-ttu-id="57828-132">在目標伺服器上設定加密選項</span><span class="sxs-lookup"><span data-stu-id="57828-132">Set Encryption Options on Target Servers</span></span>](set-encryption-options-on-target-servers.md)  
 <span data-ttu-id="57828-133">包含在目標伺服器上設定 MsxEncryptChannelOptions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 登錄子機碼的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="57828-133">Contains information about setting the MsxEncryptChannelOptions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent registry subkey on target servers.</span></span>  
  
 [<span data-ttu-id="57828-134">管理整個企業的作業</span><span class="sxs-lookup"><span data-stu-id="57828-134">Manage Jobs Across an Enterprise</span></span>](manage-jobs-across-an-enterprise.md)  
 <span data-ttu-id="57828-135">包含檢查作業狀態、變更作業的目標伺服器、同步處理目標伺服器時鐘，以及向主要伺服器輪詢其目前作業狀態等的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="57828-135">Contains information about checking job status, changing target servers for jobs, synchronizing target server clocks, and polling master servers for their current job status.</span></span>  
  
 [<span data-ttu-id="57828-136">為使用 Proxy 的多伺服器作業疑難排解</span><span class="sxs-lookup"><span data-stu-id="57828-136">Troubleshoot Multiserver Jobs That Use Proxies</span></span>](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 <span data-ttu-id="57828-137">包含失敗的使用 Proxy 之多伺服器作業的疑難排解資訊。</span><span class="sxs-lookup"><span data-stu-id="57828-137">Contains information about troubleshooting multiserver jobs that use proxies which fail.</span></span>  
  
 [<span data-ttu-id="57828-138">輪詢伺服器</span><span class="sxs-lookup"><span data-stu-id="57828-138">Poll Servers</span></span>](poll-servers.md)  
 <span data-ttu-id="57828-139">包含如何以隱含方式 (及明確方式) 讓目標伺服器輪詢主要伺服器，以同步處理作業資訊的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="57828-139">Contains information about how to implicitly and explicitly make target servers poll master servers to synchronize jobs information.</span></span>  
  
 [<span data-ttu-id="57828-140">管理事件</span><span class="sxs-lookup"><span data-stu-id="57828-140">Manage Events</span></span>](manage-events.md)  
 <span data-ttu-id="57828-141">包含如何將事件從目標伺服器轉送至主要伺服器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="57828-141">Contains information about event forwarding from target servers to master servers.</span></span>  
  
 [<span data-ttu-id="57828-142">微調企業整體的自動化管理</span><span class="sxs-lookup"><span data-stu-id="57828-142">Tune Automated Administration Across an Enterprise</span></span>](tune-automated-administration-across-an-enterprise.md)  
 <span data-ttu-id="57828-143">包含多伺服器環境中的自動化管理如何利用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]之自行微調功能的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="57828-143">Contains information about how automated administration in a multiserver environment takes advantage of the self-tuning features of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57828-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57828-144">See Also</span></span>  
 <span data-ttu-id="57828-145">[SQL Server Database Engine 回溯相容性](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="57828-145">[SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span></span>  
 <span data-ttu-id="57828-146">[註冊伺服器](../register-servers/register-servers.md) </span><span class="sxs-lookup"><span data-stu-id="57828-146">[Register Servers](../register-servers/register-servers.md) </span></span>  
 <span data-ttu-id="57828-147">[sp_add_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-147">[sp_add_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="57828-148">[sp_delete_targetserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-148">[sp_delete_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql) </span></span>  
 <span data-ttu-id="57828-149">[sp_delete_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-149">[sp_delete_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="57828-150">[sp_help_downloadlist &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-150">[sp_help_downloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql) </span></span>  
 <span data-ttu-id="57828-151">[sp_help_jobserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-151">[sp_help_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql) </span></span>  
 <span data-ttu-id="57828-152">[sp_help_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-152">[sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="57828-153">[sp_resync_targetserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-153">[sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql) </span></span>  
 <span data-ttu-id="57828-154">[sp_update_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-154">[sp_update_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="57828-155">[dbo.sysjobservers &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-155">[dbo.sysjobservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql) </span></span>  
 <span data-ttu-id="57828-156">[sys.sys登入 &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57828-156">[sys.syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql) </span></span>  
 [<span data-ttu-id="57828-157">dbo.systargetservers &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="57828-157">dbo.systargetservers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
