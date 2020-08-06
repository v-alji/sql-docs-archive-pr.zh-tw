---
title: 使用可用性群組精靈 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.f1
- sql12.swb.newavgroupwiz.f1
helpviewer_keywords:
- New Availability Group Wizard, availability replicas
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], creating
ms.assetid: e1f1dccc-9e65-471d-8fd1-b45085c9484a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c88bc60b4aeab12b3c55d23d1fe7b2b033a962f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593592"
---
# <a name="use-the-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="9bcc2-102">使用可用性群組精靈 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9bcc2-102">Use the Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9bcc2-103">本主題描述如何使用 [新增可用性群組精靈] (在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中)，在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中建立和設定 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-103">This topic describes how to use the New Availability Group Wizard (in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]) to create and configure an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9bcc2-104">*「可用性群組」* (Availability Group) 會定義當做單一單位容錯移轉的一組使用者資料庫，以及支援容錯移轉的一組容錯移轉夥伴 (也稱為 *「可用性複本」* (Availability Replica))。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9bcc2-105">如需可用性群組的簡介，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9bcc2-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9bcc2-107">必要條件、限制及建議</span><span class="sxs-lookup"><span data-stu-id="9bcc2-107">Prerequisites, Restrictions, and Recommendations</span></span>](#PrerequisitesRestrictions)  
  
     [<span data-ttu-id="9bcc2-108">安全性</span><span class="sxs-lookup"><span data-stu-id="9bcc2-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9bcc2-109">**使用下列項目建立和設定可用性群組：**  [新增可用性群組精靈 (SQL Server Management Studio)](#RunAGwiz)</span><span class="sxs-lookup"><span data-stu-id="9bcc2-109">**To create and configure an availability group, using:**  [New Availability Group Wizard (SQL Server Management Studio)](#RunAGwiz)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9bcc2-110">除了使用 [新增可用性群組精靈] 以外，您也可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-110">As an alternative to using the New Availability Group Wizard, you can use [!INCLUDE[tsql](../../../includes/tsql-md.md)] or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlets.</span></span> <span data-ttu-id="9bcc2-111">如需詳細資訊，請參閱 [建立可用性群組 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) 或 [建立可用性群組 &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)中建立和設定 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-111">For more information, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) or [Create an Availability Group &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9bcc2-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="9bcc2-112">Before You Begin</span></span>  
 <span data-ttu-id="9bcc2-113">我們強烈建議您先閱讀本節內容，然後再嘗試建立您的第一個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-113">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a><span data-ttu-id="9bcc2-114">必要條件、限制和建議</span><span class="sxs-lookup"><span data-stu-id="9bcc2-114">Prerequisites, Restrictions, and Recommendations</span></span>  
 <span data-ttu-id="9bcc2-115">在大多數情況下，您可以使用 [新增可用性群組精靈] 來完成建立和設定可用性群組所需的所有工作。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-115">In most cases, you can use the New Availability Group Wizard to complete all of the tasks require to create and configure an availability group.</span></span> <span data-ttu-id="9bcc2-116">不過，您可能需要手動完成一些工作。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-116">However, you might need to complete some of the tasks manually.</span></span>  
  
-   <span data-ttu-id="9bcc2-117">建立可用性群組之前，請確認裝載可用性複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體位於相同 Windows Server 容錯移轉叢集 (WSFC) 容錯移轉叢集的不同 WSFC 節點上。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-117">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="9bcc2-118">此外，請確認每個伺服器執行個體都符合所有其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 必要條件。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-118">Also, verify that each of the server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="9bcc2-119">如需詳細資訊，強烈建議您閱讀 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-119">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="9bcc2-120">如果您選取來裝載可用性複本的伺服器執行個體是以網域使用者帳戶執行，且還沒有資料庫鏡像端點，則此精靈可以建立端點，並授與伺服器執行個體服務帳戶的 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-120">If a server instance that you select to host an availability replica is running under a domain user account and does not yet have a database mirroring endpoint, the wizard can create the endpoint and grant CONNECT permission to the server instance service account.</span></span> <span data-ttu-id="9bcc2-121">但是，如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務是以內建帳戶 (例如本機系統、本機服務或網路服務) 或非網域帳戶的身分執行，您就必須將憑證用於端點驗證，而且精靈無法在此伺服器執行個體上建立資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-121">However, if the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running as a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication, and the wizard will be unable to create a database mirroring endpoint on the server instance.</span></span> <span data-ttu-id="9bcc2-122">在此情況下，我們建議您先手動建立資料庫鏡像端點，然後再啟動 [新增可用性群組精靈]。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-122">In this case, we recommend that you create the database mirroring endpoints manually before you launch the New Availability Group Wizard.</span></span>  
  
     `To use certificates for a database mirroring endpoint:`  
  
     [<span data-ttu-id="9bcc2-123">CREATE ENDPOINT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-123">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
     [<span data-ttu-id="9bcc2-124">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-124">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   <span data-ttu-id="9bcc2-125">SQL Server 容錯移轉叢集執行個體 (FCI) 不支援依照可用性群組進行自動容錯移轉，因此任何由 FCI 裝載的可用性複本只能設定為手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-125">SQL Server Failover Cluster Instances (FCIs) do not support automatic failover by availability groups, so any availability replica that is hosted by an FCI can only be configured for manual failover.</span></span>  
  
-   <span data-ttu-id="9bcc2-126">如果資料庫已加密，甚至包含資料庫加密金鑰 (DEK)，您就無法使用 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 或 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] ，將資料庫加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-126">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="9bcc2-127">即使加密的資料庫已經解密，其記錄備份可能包含加密資料。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-127">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="9bcc2-128">在此情況中，資料庫的完整初始資料同步處理可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-128">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="9bcc2-129">這是因為還原記錄作業可能需要資料庫加密金鑰 (DEK) 所使用的憑證，而該憑證可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-129">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="9bcc2-130">若要讓解密的資料庫能夠透過精靈加入至可用性群組：</span><span class="sxs-lookup"><span data-stu-id="9bcc2-130">To make a decrypted database eligible to add to an availability group using the wizard:</span></span>  
  
    1.  <span data-ttu-id="9bcc2-131">建立主要資料庫的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-131">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="9bcc2-132">建立主要資料庫的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-132">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="9bcc2-133">在裝載次要複本的伺服器執行個體上還原資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-133">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="9bcc2-134">從主要資料庫建立新的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-134">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="9bcc2-135">在次要資料庫上還原這個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-135">Restore this log backup on the secondary database.</span></span>  
  
-   <span data-ttu-id="9bcc2-136">**執行完整初始資料同步處理精靈的必要條件**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-136">**Prerequisites for the wizard to perform full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="9bcc2-137">每個裝載可用性群組複本之伺服器執行個體上的所有資料庫檔案路徑均須相同。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-137">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="9bcc2-138">任何裝載次要複本的伺服器執行個體上皆不應存在主要資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-138">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="9bcc2-139">這表示目前還不可有任何新次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-139">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="9bcc2-140">您必須指定網路共用，精靈才能建立及存取備份。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-140">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="9bcc2-141">對於主要複本，用於啟動 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帳戶必須具有網路共用的讀取與寫入檔案系統權限。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-141">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="9bcc2-142">如果是次要複本，此帳戶必須有網路共用的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-142">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="9bcc2-143">記錄備份將是記錄備份鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-143">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="9bcc2-144">請適當地儲存記錄備份檔案。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-144">Store the log backup files appropriately.</span></span>  
  
     <span data-ttu-id="9bcc2-145">如果您無法使用精靈執行完整初始資料同步處理，則必須手動準備次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-145">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="9bcc2-146">您可以在執行精靈前後進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-146">You can do this before or after running the wizard.</span></span> <span data-ttu-id="9bcc2-147">如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-147">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9bcc2-148">Security</span><span class="sxs-lookup"><span data-stu-id="9bcc2-148">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9bcc2-149">權限</span><span class="sxs-lookup"><span data-stu-id="9bcc2-149">Permissions</span></span>  
 <span data-ttu-id="9bcc2-150">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-150">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="9bcc2-151">如果您想要允許 [可用性群組精靈] 管理資料庫鏡像端點，也需要 CONTROL ON ENDPOINT 權限。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-151">Also requires CONTROL ON ENDPOINT permission if you want to allow Availability Group Wizard to manage the database mirroring endpoint.</span></span>  
  
##  <a name="using-the-new-availability-group-wizard"></a><a name="RunAGwiz"></a> <span data-ttu-id="9bcc2-152">使用新增可用性群組精靈</span><span class="sxs-lookup"><span data-stu-id="9bcc2-152">Using the New Availability Group Wizard</span></span>  
  
1.  <span data-ttu-id="9bcc2-153">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-153">In Object Explorer, connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="9bcc2-154">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-154">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="9bcc2-155">若要啟動 [新增可用性群組精靈]，請選取 **[新增可用性群組精靈]** 命令。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-155">To launch the New Availability Group Wizard, select the **New Availability Group Wizard** command.</span></span>  
  
4.  <span data-ttu-id="9bcc2-156">當您初次執行此精靈時，將會出現 **[簡介]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-156">The first time you run this wizard, an **Introduction** page appears.</span></span> <span data-ttu-id="9bcc2-157">如果將來要略過此頁面，您可以按一下 **[不要再顯示此頁面]**。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-157">To bypass this page in the future, you can click **Do not show this page again**.</span></span> <span data-ttu-id="9bcc2-158">閱讀這個頁面之後，請按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-158">After reading this page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="9bcc2-159">在 **[指定可用性群組名稱]** 頁面上，於 **[可用性群組名稱]** 欄位內輸入新的可用性群組名稱。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-159">On the **Specify Availability Group Name** page, enter the name of the new availability group in the **Availability group name** field.</span></span> <span data-ttu-id="9bcc2-160">此名稱必須是有效的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 識別碼，該識別碼在 WSFC 容錯移轉叢集及整體網域中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-160">This name must be a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifier that is unique on the WSFC failover cluster and in your domain as a whole.</span></span> <span data-ttu-id="9bcc2-161">可用性群組名稱的最大長度為 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-161">The maximum length for an availability group name is 128 characters.</span></span>  
  
6.  <span data-ttu-id="9bcc2-162">在 **[選取資料庫]** 頁面上，方格會列出連接之伺服器執行個體上有資格變成 *「可用性資料庫」*(Availability Database) 的使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-162">On the **Select Databases** page, the grid lists user databases on the connected server instance that are eligible to become the *availability databases*.</span></span> <span data-ttu-id="9bcc2-163">請選取一個或多個列出的資料庫，以便參與新的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-163">Select one or more of the listed databases to participate in the new availability group.</span></span> <span data-ttu-id="9bcc2-164">這些資料庫一開始將會成為初始 *「主要資料庫」*(Primary Database)。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-164">These databases will initially be the initial *primary databases*.</span></span>  
  
     <span data-ttu-id="9bcc2-165">針對每個列出的資料庫， **[大小]** 資料行會顯示資料庫大小 (如果已知的話)。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-165">For each listed database, the **Size** column displays the database size, if known.</span></span> <span data-ttu-id="9bcc2-166">[狀態]\*\*\*\* 資料行會指出給定的資料庫是否符合可用性資料庫的[必要條件](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-166">The **Status** column indicates whether a given database meets the [prerequisites](prereqs-restrictions-recommendations-always-on-availability.md)for availability databases.</span></span> <span data-ttu-id="9bcc2-167">如果不符合必要條件，簡短狀態描述會指出資料庫不合格的原因。例如，資料庫沒有使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-167">It the prerequisites are not met, a brief status description indicates the reason that the database is ineligible; for example, if it does not use the full recovery model.</span></span> <span data-ttu-id="9bcc2-168">如需詳細資訊，請按一下狀態描述。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-168">For more information, click the status description.</span></span>  
  
     <span data-ttu-id="9bcc2-169">如果您變更資料庫讓它符合資格，請按一下 **[重新整理]** 更新資料庫方格。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-169">If you change a database to make it eligible, click **Refresh** to update the databases grid.</span></span>  
  
7.  <span data-ttu-id="9bcc2-170">在 **[指定複本]** 頁面上，針對新的可用性群組指定並設定一個或多個複本。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-170">On the **Specify Replicas** page, specify and configure one or more replicas for the new availability group.</span></span> <span data-ttu-id="9bcc2-171">此頁面包含四個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-171">This page contains four tabs.</span></span> <span data-ttu-id="9bcc2-172">下表將介紹這些索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-172">The following table introduces these tabs.</span></span> <span data-ttu-id="9bcc2-173">如需詳細資訊，請參閱[指定複本頁面 &#40;新增可用性群組精靈：加入複本精靈&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-173">For more information, see the [Specify Replicas Page &#40;New Availability Group Wizard: Add Replica Wizard&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) topic.</span></span>  
  
    |<span data-ttu-id="9bcc2-174">索引標籤</span><span class="sxs-lookup"><span data-stu-id="9bcc2-174">Tab</span></span>|<span data-ttu-id="9bcc2-175">簡短描述</span><span class="sxs-lookup"><span data-stu-id="9bcc2-175">Brief Description</span></span>|  
    |---------|-----------------------|  
    |<span data-ttu-id="9bcc2-176">**複本**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-176">**Replicas**</span></span>|<span data-ttu-id="9bcc2-177">使用此索引標籤可指定將裝載次要複本的每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-177">Use this tab to specify each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host a secondary replica.</span></span> <span data-ttu-id="9bcc2-178">請注意，您目前所連接的伺服器執行個體必須裝載主要複本。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-178">Note that the server instance to which you are currently connected must host the primary replica.</span></span>|  
    |<span data-ttu-id="9bcc2-179">**端點**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-179">**Endpoints**</span></span>|<span data-ttu-id="9bcc2-180">使用此索引標籤可驗證任何現有的資料庫鏡像端點，此外，如果在其服務帳戶使用 Windows 驗證的伺服器執行個體上缺少此端點，則可自動建立該端點。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-180">Use this tab to verify any existing database mirroring endpoints and also, if this endpoint is lacking on a server instance whose service accounts use Windows Authentication, to create the endpoint automatically.</span></span> <span data-ttu-id="9bcc2-181">**注意：** 如果有任何伺服器實例是在非網域使用者帳戶下執行，您必須先對伺服器實例進行手動變更，然後才能在嚮導中繼續進行。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-181">**Note:**  If any server instance is running under a non-domain user account, you need to do make a manual change to your server instance before you can proceed in the wizard.</span></span> <span data-ttu-id="9bcc2-182">如需詳細資訊，請參閱本主題前面的＜ [必要條件](#PrerequisitesRestrictions)＞。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-182">For more information, see [Prerequisites](#PrerequisitesRestrictions), earlier in this topic.</span></span>|  
    |<span data-ttu-id="9bcc2-183">**備份喜好設定**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-183">**Backup Preferences**</span></span>|<span data-ttu-id="9bcc2-184">使用此索引標籤可指定整個可用性群組的備份喜好設定，以及個別可用性複本的備份優先權。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-184">Use this tab to specify your backup preference for the availability group as a whole and your backup priorities for the individual availability replicas.</span></span>|  
    |<span data-ttu-id="9bcc2-185">**接聽程式**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-185">**Listener**</span></span>|<span data-ttu-id="9bcc2-186">使用此索引標籤可建立可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-186">Use this tab to create an availability group listener.</span></span> <span data-ttu-id="9bcc2-187">根據預設，精靈不會建立接聽程式。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-187">By default, the wizard does not create a listener.</span></span>|  
  
8.  <span data-ttu-id="9bcc2-188">在 **[選取初始資料同步處理]** 頁面上，選擇您要如何建立新的次要資料庫並將它聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-188">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="9bcc2-189">選擇下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="9bcc2-189">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="9bcc2-190">**完整**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-190">**Full**</span></span>  
  
         <span data-ttu-id="9bcc2-191">只有在您的環境符合自動啟動初始資料同步處理的需求時，才選取此選項 (如需詳細資訊，請參閱本主題稍早的 [必要條件、限制和建議](#PrerequisitesRestrictions))。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-191">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#PrerequisitesRestrictions), earlier in this topic).</span></span>  
  
         <span data-ttu-id="9bcc2-192">如果您選取 **[完整]**，在建立可用性群組之後，精靈會將每個主要資料庫及其交易記錄備份至網路共用，並在裝載次要複本的每個伺服器執行個體上還原這些備份。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-192">If you select **Full**, after creating the availability group, the wizard will back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts an secondary replica.</span></span> <span data-ttu-id="9bcc2-193">然後精靈會將每個次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-193">The wizard will then join every secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="9bcc2-194">在 **[指定所有複本可存取的共用網路位置:]** 欄位中，指定裝載複本的所有伺服器執行個體都有讀寫存取的備份共用。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-194">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="9bcc2-195">如需詳細資訊，請參閱本主題前面的＜ [必要條件](#PrerequisitesRestrictions)＞。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-195">For more information, see [Prerequisites](#PrerequisitesRestrictions), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="9bcc2-196">**僅聯結**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-196">**Join only**</span></span>  
  
         <span data-ttu-id="9bcc2-197">如果您已經在將裝載次要複本的伺服器執行個體上手動備妥次要資料庫，就可以選取此選項。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-197">If you have manually prepared secondary databases on the server instances that will host the secondary replicas, you can select this option.</span></span> <span data-ttu-id="9bcc2-198">然後精靈會將現有的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-198">The wizard will join the existing secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="9bcc2-199">**略過初始資料同步處理**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-199">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="9bcc2-200">如果要使用您自己的主要資料庫的資料庫和記錄備份，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-200">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="9bcc2-201">如需詳細資訊，請參閱[於 AlwaysOn 次要資料庫啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-201">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
9. <span data-ttu-id="9bcc2-202">**[驗證]** 頁面會驗證您在此精靈中指定的值是否符合 [新增可用性群組精靈] 的需求。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-202">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the New Availability Group Wizard.</span></span> <span data-ttu-id="9bcc2-203">若要進行變更，您可以按 **[上一步]** 返回先前的精靈頁面，以變更一個或多個值。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-203">To make a change, click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="9bcc2-204">然後按 **[下一步]** 返回 **[驗證]** 頁面，再按一下 **[重新執行驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-204">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
10. <span data-ttu-id="9bcc2-205">在 **[摘要]** 頁面上，檢閱您為新的可用性群組的選擇。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-205">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="9bcc2-206">若要進行變更，請按 **[上一步]** 返回相關頁面。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-206">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="9bcc2-207">進行變更之後，請按 **[下一步]** 返回 **[摘要]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-207">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9bcc2-208">如果沒有將要裝載新可用性複本之伺服器執行個體的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶做為登入存在，[新增可用性群組精靈] 就需要建立登入。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-208">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account of a server instance that will host a new availability replica does not already exist as a login, the New Availability Group Wizard needs to create the login.</span></span> <span data-ttu-id="9bcc2-209">在 **[摘要]** 頁面上，精靈會顯示要建立之登入的資訊。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-209">On the **Summary** page, the wizard displays the information for the login that is to be created.</span></span> <span data-ttu-id="9bcc2-210">如果您按一下 **[完成]**，精靈就會為 SQL Server 服務帳戶建立此登入，並且授與登入 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-210">If you click **Finish**, the wizard creates this login for the SQL Server service account and grants the login CONNECT permission.</span></span>  
  
     <span data-ttu-id="9bcc2-211">如果您對所做的選擇感到滿意時，可以選擇按一下 **[指令碼]** ，建立精靈將執行之步驟的指令碼。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-211">If you are satisfied with your selections, optionally click **Script** to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="9bcc2-212">然後，若要建立及設定新的可用性群組，請按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-212">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
11. <span data-ttu-id="9bcc2-213">**[進度]** 頁面會顯示建立可用性群組之步驟的進度 (設定端點、建立可用性群組，並將次要複本加入群組中)。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-213">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
12. <span data-ttu-id="9bcc2-214">當這些步驟完成時， **[結果]** 頁面會顯示每個步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-214">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="9bcc2-215">如果所有這些步驟都成功，表示新的可用性群組已完成設定。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-215">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="9bcc2-216">如果任何步驟導致錯誤，您可能需要手動完成組態，或者針對失敗的步驟使用精靈。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-216">If any of the steps result in an error, you might need to manually complete the configuration or use a wizard for the failed step.</span></span> <span data-ttu-id="9bcc2-217">如需有關給定錯誤原因的詳細資訊，請按一下 **[結果]** 資料行中相關聯的 [錯誤] 連結。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-217">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="9bcc2-218">當精靈完成時，按一下 **[關閉]** 以結束。</span><span class="sxs-lookup"><span data-stu-id="9bcc2-218">When the wizard completes, click **Close** to exit.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9bcc2-219">相關工作</span><span class="sxs-lookup"><span data-stu-id="9bcc2-219">Related Tasks</span></span>  
 <span data-ttu-id="9bcc2-220">**若要完成可用性群組組態**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-220">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="9bcc2-221">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-221">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="9bcc2-222">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-222">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="9bcc2-223">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-223">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="9bcc2-224">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-224">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="9bcc2-225">**建立可用性群組的其他方法**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-225">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="9bcc2-226">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-226">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="9bcc2-227">建立可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-227">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="9bcc2-228">建立可用性群組 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-228">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="9bcc2-229">**若要啟用 AlwaysOn 可用性群組**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-229">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="9bcc2-230">啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-230">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="9bcc2-231">**若要設定資料庫鏡像端點**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-231">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="9bcc2-232">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-232">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="9bcc2-233">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-233">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="9bcc2-234">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-234">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="9bcc2-235">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-235">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="9bcc2-236">**若要疑難排解 AlwaysOn 可用性群組組態**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-236">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="9bcc2-237">針對 AlwaysOn 可用性群組 Configuration &#40;SQL Server&#41;已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="9bcc2-237">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="9bcc2-238">針對失敗的新增檔案作業進行疑難排解 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-238">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="9bcc2-239">相關內容</span><span class="sxs-lookup"><span data-stu-id="9bcc2-239">Related Content</span></span>  
  
-   <span data-ttu-id="9bcc2-240">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-240">**Blogs:**</span></span>  
  
     [<span data-ttu-id="9bcc2-241">AlwaysON - HADRON 學習系列：具備 HADRON 功能之資料庫的工作者集區使用方式</span><span class="sxs-lookup"><span data-stu-id="9bcc2-241">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="9bcc2-242">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="9bcc2-242">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="9bcc2-243">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="9bcc2-243">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="9bcc2-244">**影片：**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-244">**Videos:**</span></span>  
  
     [<span data-ttu-id="9bcc2-245">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 1 部：新一代高可用性解決方案簡介</span><span class="sxs-lookup"><span data-stu-id="9bcc2-245">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="9bcc2-246">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 2 部：使用 AlwaysOn 建立關鍵任務的高可用性方案</span><span class="sxs-lookup"><span data-stu-id="9bcc2-246">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="9bcc2-247">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="9bcc2-247">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="9bcc2-248">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="9bcc2-248">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="9bcc2-249">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="9bcc2-249">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="9bcc2-250">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="9bcc2-250">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="9bcc2-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bcc2-251">See Also</span></span>  
 <span data-ttu-id="9bcc2-252">[資料庫鏡像端點 &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9bcc2-252">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="9bcc2-253">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9bcc2-253">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="9bcc2-254">AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;</span><span class="sxs-lookup"><span data-stu-id="9bcc2-254">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
