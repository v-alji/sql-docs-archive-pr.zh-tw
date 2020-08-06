---
title: 使用將複本新增至可用性群組精靈 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], wizards
ms.assetid: 60d962b6-2af4-4394-9190-61939a102bc0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4d75372cd2388e88fcb3d3ce95975bdefa54c5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593597"
---
# <a name="use-the-add-replica-to-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="69820-102">使用 [將複本加入至可用性群組] 精靈 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="69820-102">Use the Add Replica to Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="69820-103">使用 [將複本加入至可用性群組精靈]，可協助您將新次要複本加入至現有的 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="69820-103">Use the Add Replica to Availability Group Wizard to help you a add new secondary replica to an existing AlwaysOn availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69820-104">如需使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 將次要複本加入可用性群組的資訊，請參閱 [將次要複本加入至可用性群組 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="69820-104">For information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to add a secondary replica to an availability group, see [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="69820-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="69820-105">Before You Begin</span></span>  
 <span data-ttu-id="69820-106">如果您從未將任何可用性複本新增至可用性群組，請參閱[AlwaysOn 可用性群組 &#40;SQL Server&#41;的必要條件、限制和建議](prereqs-restrictions-recommendations-always-on-availability.md)中的「伺服器實例」和「可用性群組和複本」小節。</span><span class="sxs-lookup"><span data-stu-id="69820-106">If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="69820-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="69820-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="69820-108">您必須連接到裝載目前主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="69820-108">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="69820-109">加入次要複本之前，請確認 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 主機執行個體與現有複本位於相同 Windows Server 容錯移轉叢集 (WSFC) 叢集中，但位於不同的叢集節點上。</span><span class="sxs-lookup"><span data-stu-id="69820-109">Before adding a secondary replica, verify that the host instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is in the same Windows Server Failover Clustering (WSFC) cluster as the existing replicas but resides on a different cluster node.</span></span> <span data-ttu-id="69820-110">也請確認這個伺服器執行個體符合所有其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 必要條件。</span><span class="sxs-lookup"><span data-stu-id="69820-110">Also, verify that this server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="69820-111">如需詳細資訊，請參閱 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="69820-111">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="69820-112">如果您選取來裝載可用性複本的伺服器執行個體是以網域使用者帳戶執行，且還沒有資料庫鏡像端點，則此精靈可以建立端點，並授與伺服器執行個體服務帳戶的 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="69820-112">If a server instance that you select to host an availability replica is running under a domain user account and does not yet have a database mirroring endpoint, the wizard can create the endpoint and grant CONNECT permission to the server instance service account.</span></span> <span data-ttu-id="69820-113">但是，如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務是以內建帳戶 (例如本機系統、本機服務或網路服務) 或非網域帳戶的身分執行，您就必須將憑證用於端點驗證，而且精靈無法在此伺服器執行個體上建立資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="69820-113">However, if the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running as a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication, and the wizard will be unable to create a database mirroring endpoint on the server instance.</span></span> <span data-ttu-id="69820-114">在此情況下，我們建議您先手動建立資料庫鏡像端點，然後再啟動 [將複本加入至可用性群組] 精靈。</span><span class="sxs-lookup"><span data-stu-id="69820-114">In this case, we recommend that you create the database mirroring endpoints manually before you launch the Add Replica to Availability Group Wizard.</span></span>  
  
     `To use certificates for a database mirroring endpoint:`  
  
     [<span data-ttu-id="69820-115">CREATE ENDPOINT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69820-115">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
     [<span data-ttu-id="69820-116">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69820-116">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   <span data-ttu-id="69820-117">**使用完整初始資料同步處理的必要條件**</span><span class="sxs-lookup"><span data-stu-id="69820-117">**Prerequisites for using full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="69820-118">每個裝載可用性群組複本之伺服器執行個體上的所有資料庫檔案路徑均須相同。</span><span class="sxs-lookup"><span data-stu-id="69820-118">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="69820-119">任何裝載次要複本的伺服器執行個體上皆不應存在主要資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="69820-119">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="69820-120">這表示目前還不可有任何新次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="69820-120">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="69820-121">您必須指定網路共用，精靈才能建立及存取備份。</span><span class="sxs-lookup"><span data-stu-id="69820-121">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="69820-122">對於主要複本，用於啟動 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帳戶必須具有網路共用的讀取與寫入檔案系統權限。</span><span class="sxs-lookup"><span data-stu-id="69820-122">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="69820-123">如果是次要複本，此帳戶必須有網路共用的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="69820-123">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="69820-124">如果您無法使用精靈執行完整初始資料同步處理，則必須手動準備次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="69820-124">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="69820-125">您可以在執行精靈前後進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="69820-125">You can do this before or after running the wizard.</span></span> <span data-ttu-id="69820-126">如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="69820-126">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="69820-127">Security</span><span class="sxs-lookup"><span data-stu-id="69820-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="69820-128">權限</span><span class="sxs-lookup"><span data-stu-id="69820-128">Permissions</span></span>  
 <span data-ttu-id="69820-129">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="69820-129">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="69820-130">如果您想要允許 [將複本加入至可用性群組精靈] 管理資料庫鏡像端點，也需要 CONTROL ON ENDPOINT 權限。</span><span class="sxs-lookup"><span data-stu-id="69820-130">Also requires CONTROL ON ENDPOINT permission if you want to allow Add Replica to Availability Group Wizard to manage the database mirroring endpoint.</span></span>  
  

  
##  <a name="using-the-add-replica-to-availability-group-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="69820-131">使用將複本加入至可用性群組精靈 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="69820-131">Using the Add Replica to Availability Group Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="69820-132">**使用將複本加入至可用性群組精靈**</span><span class="sxs-lookup"><span data-stu-id="69820-132">**To Use the Add Replica to Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="69820-133">在 [物件總管] 中，連接到裝載可用性群組之主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="69820-133">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="69820-134">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="69820-134">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="69820-135">以滑鼠右鍵按一下您要加入次要複本的可用性群組，並選取 [加入複本] 命令。</span><span class="sxs-lookup"><span data-stu-id="69820-135">Right-click the availability group to which you are adding a secondary replica, and select the **Add Replica** command.</span></span> <span data-ttu-id="69820-136">這會啟動 [將複本加入至可用性群組] 精靈。</span><span class="sxs-lookup"><span data-stu-id="69820-136">This launches the Add Replica to Availability Group Wizard.</span></span>  
  
4.  <span data-ttu-id="69820-137">在 **[連接到現有次要複本]** 頁面上，連接到可用性群組中的每一個次要複本。</span><span class="sxs-lookup"><span data-stu-id="69820-137">On the **Connect to Existing Secondary Replicas** page, connect to every secondary replica in the availability group.</span></span> <span data-ttu-id="69820-138">如需詳細資訊，請參閱[連接到現有的次要複本頁面 &#40;新增複本嚮導和加入資料庫 wizard&#41;](connect-to-existing-secondary-replicas-page.md)。</span><span class="sxs-lookup"><span data-stu-id="69820-138">For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard and Add Databases Wizard&#41;](connect-to-existing-secondary-replicas-page.md).</span></span>  
  
5.  <span data-ttu-id="69820-139">在 **[指定複本]** 頁面上，針對可用性群組指定並設定一個或多個新次要複本。</span><span class="sxs-lookup"><span data-stu-id="69820-139">On the **Specify Replicas** page, specify and configure one or more new secondary replicas for the availability group.</span></span> <span data-ttu-id="69820-140">此頁面包含三個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="69820-140">This page contains three tabs.</span></span> <span data-ttu-id="69820-141">下表將介紹這些索引標籤。</span><span class="sxs-lookup"><span data-stu-id="69820-141">The following table introduces these tabs.</span></span> <span data-ttu-id="69820-142">如需詳細資訊，請參閱[指定複本頁面 &#40;新增可用性群組精靈：新增複本精靈 &#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="69820-142">For more information, see [Specify Replicas Page &#40;New Availability Group Wizard: Add Replica Wizard&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).</span></span>  
  
    |<span data-ttu-id="69820-143">索引標籤</span><span class="sxs-lookup"><span data-stu-id="69820-143">Tab</span></span>|<span data-ttu-id="69820-144">簡短描述</span><span class="sxs-lookup"><span data-stu-id="69820-144">Brief Description</span></span>|  
    |---------|-----------------------|  
    |<span data-ttu-id="69820-145">**複本**</span><span class="sxs-lookup"><span data-stu-id="69820-145">**Replicas**</span></span>|<span data-ttu-id="69820-146">使用此索引標籤可指定將裝載新次要複本的每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="69820-146">Use this tab to specify each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host a new secondary replica.</span></span>|  
    |<span data-ttu-id="69820-147">**端點**</span><span class="sxs-lookup"><span data-stu-id="69820-147">**Endpoints**</span></span>|<span data-ttu-id="69820-148">使用此索引標籤來驗證每個新次要複本的現有資料庫鏡像端點 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="69820-148">Use this tab to verify the existing database mirroring endpoint, if any, for each new secondary replica.</span></span> <span data-ttu-id="69820-149">如果在其服務帳戶使用 Windows 驗證的伺服器執行個體上缺少此端點，精靈會嘗試自動建立該端點。</span><span class="sxs-lookup"><span data-stu-id="69820-149">If this endpoint is lacking on a server instance whose service accounts use Windows Authentication, the wizard will attempt to create the endpoint automatically.</span></span> <span data-ttu-id="69820-150">**注意：** 如果有任何伺服器實例是在非網域使用者帳戶下執行，您必須先對伺服器實例進行手動變更，然後才能在嚮導中繼續進行。</span><span class="sxs-lookup"><span data-stu-id="69820-150">**Note:**  If any server instance is running under a non-domain user account, you need to do make a manual change to your server instance before you can proceed in the wizard.</span></span> <span data-ttu-id="69820-151">如需詳細資訊，請參閱本主題前面的＜ [必要條件](#Prerequisites)＞。</span><span class="sxs-lookup"><span data-stu-id="69820-151">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>|  
    |<span data-ttu-id="69820-152">**備份喜好設定**</span><span class="sxs-lookup"><span data-stu-id="69820-152">**Backup Preferences**</span></span>|<span data-ttu-id="69820-153">使用此索引標籤可指定整個可用性群組的備份喜好設定，如果您希望修改目前設定，可指定個別可用性複本的備份優先權。</span><span class="sxs-lookup"><span data-stu-id="69820-153">Use this tab to specify your backup preference for the availability group as a whole, if you wish to modify the current setting, and to specify your backup priorities for the individual availability replicas.</span></span>|  
  
6.  <span data-ttu-id="69820-154">在 **[選取初始資料同步處理]** 頁面上，選擇您要如何建立新的次要資料庫並將它聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="69820-154">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="69820-155">選擇下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="69820-155">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="69820-156">**完整**</span><span class="sxs-lookup"><span data-stu-id="69820-156">**Full**</span></span>  
  
         <span data-ttu-id="69820-157">只有在您的環境符合自動啟動初始資料同步處理的需求時，才選取此選項 (如需詳細資訊，請參閱本主題稍早的 [必要條件、限制和建議](#Prerequisites))。</span><span class="sxs-lookup"><span data-stu-id="69820-157">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic).</span></span>  
  
         <span data-ttu-id="69820-158">如果您選取 **[完整]** ，在建立可用性群組之後，精靈會將每個主要資料庫及其交易記錄備份至網路共用，並在裝載新次要複本的每個伺服器執行個體上還原這些備份。</span><span class="sxs-lookup"><span data-stu-id="69820-158">If you select **Full**, after creating the availability group, the wizard will back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts a new secondary replica.</span></span> <span data-ttu-id="69820-159">然後精靈會將每個新次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="69820-159">The wizard will then join every new secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="69820-160">在 **[指定所有複本可存取的共用網路位置:]** 欄位中，指定裝載複本的所有伺服器執行個體都有讀寫存取的備份共用。</span><span class="sxs-lookup"><span data-stu-id="69820-160">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="69820-161">記錄備份將是記錄備份鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="69820-161">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="69820-162">請適當地儲存記錄備份檔案。</span><span class="sxs-lookup"><span data-stu-id="69820-162">Store the log backup files appropriately.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="69820-163">如需檔案系統必要權限的資訊，請參閱本主題稍早的 [必要條件](#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="69820-163">For information about the required file-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="69820-164">**僅聯結**</span><span class="sxs-lookup"><span data-stu-id="69820-164">**Join only**</span></span>  
  
         <span data-ttu-id="69820-165">如果您已經在將裝載新次要複本的伺服器執行個體上手動備妥次要資料庫，就可以選取此選項。</span><span class="sxs-lookup"><span data-stu-id="69820-165">If you have manually prepared secondary databases on the server instances that will host the new secondary replicas, you can select this option.</span></span> <span data-ttu-id="69820-166">然後精靈會將這些新的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="69820-166">The wizard will join these new secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="69820-167">**略過初始資料同步處理**</span><span class="sxs-lookup"><span data-stu-id="69820-167">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="69820-168">如果要使用您自己的主要資料庫的資料庫和記錄備份，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="69820-168">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="69820-169">如需詳細資訊，請參閱[於 AlwaysOn 次要資料庫啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="69820-169">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
7.  <span data-ttu-id="69820-170">**[驗證]** 頁面會驗證您在此精靈中指定的值是否符合 [將複本加入至可用性群組] 精靈的需求。</span><span class="sxs-lookup"><span data-stu-id="69820-170">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the Add Replica to Availability Group Wizard.</span></span> <span data-ttu-id="69820-171">若要進行變更，您可以按 **[上一步]** 返回先前的精靈頁面，以變更一個或多個值。</span><span class="sxs-lookup"><span data-stu-id="69820-171">To make a change, click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="69820-172">然後按 **[下一步]** 返回 **[驗證]** 頁面，再按一下 **[重新執行驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="69820-172">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
8.  <span data-ttu-id="69820-173">在 **[摘要]** 頁面上，檢閱您為新的可用性群組的選擇。</span><span class="sxs-lookup"><span data-stu-id="69820-173">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="69820-174">若要進行變更，請按 **[上一步]** 返回相關頁面。</span><span class="sxs-lookup"><span data-stu-id="69820-174">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="69820-175">進行變更之後，請按 **[下一步]** 返回 **[摘要]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="69820-175">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
     <span data-ttu-id="69820-176">如果您對所做的選擇感到滿意時，可以選擇按一下 [指令碼]，建立精靈將執行之步驟的指令碼。</span><span class="sxs-lookup"><span data-stu-id="69820-176">If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="69820-177">然後，若要建立及設定新的可用性群組，請按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="69820-177">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
9. <span data-ttu-id="69820-178">**[進度]** 頁面會顯示建立可用性群組之步驟的進度 (設定端點、建立可用性群組，並將次要複本加入群組中)。</span><span class="sxs-lookup"><span data-stu-id="69820-178">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
10. <span data-ttu-id="69820-179">當這些步驟完成時， **[結果]** 頁面會顯示每個步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="69820-179">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="69820-180">如果所有這些步驟都成功，表示新的可用性群組已完成設定。</span><span class="sxs-lookup"><span data-stu-id="69820-180">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="69820-181">如果任何步驟導致錯誤，您可能需要手動完成設定。</span><span class="sxs-lookup"><span data-stu-id="69820-181">If any of the steps result in an error, you might need to manually complete the configuration.</span></span> <span data-ttu-id="69820-182">如需有關給定錯誤原因的詳細資訊，請按一下 **[結果]** 資料行中相關聯的 [錯誤] 連結。</span><span class="sxs-lookup"><span data-stu-id="69820-182">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="69820-183">當精靈完成時，按一下 **[關閉]** 以結束。</span><span class="sxs-lookup"><span data-stu-id="69820-183">When the wizard completes, click **Close** to exit.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="69820-184">新增複本之後，請參閱＜後續操作：新增複本之後＞一節，位於[將次要複本新增至可用性群組 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)中。</span><span class="sxs-lookup"><span data-stu-id="69820-184">After adding a replica, see the "Follow Up: After Adding a Replica" section in [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="69820-185">相關工作</span><span class="sxs-lookup"><span data-stu-id="69820-185">Related Tasks</span></span>  
  
-   [<span data-ttu-id="69820-186">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69820-186">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="69820-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69820-187">See Also</span></span>  
 <span data-ttu-id="69820-188">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="69820-188">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="69820-189">[AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="69820-189">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 [<span data-ttu-id="69820-190">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69820-190">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
