---
title: 使用 [將資料庫加入至可用性組嚮導] (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], databases
ms.assetid: 81e5e36d-735d-4731-8017-2654673abb88
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a093bb23687d4e49d311b46a7bb0bd211016a0ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585621"
---
# <a name="use-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="18c1e-102">使用 [將資料庫加入至可用性群組] 精靈 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="18c1e-102">Use the Add Database to Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="18c1e-103">使用 [將資料庫加入至可用性群組精靈] 可將一個或多個資料庫加入現有的 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18c1e-103">Use the Add Database to Availability Group Wizard to help you add one or more databases to an existing AlwaysOn availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18c1e-104">如需使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 加入資料庫的相關資訊，請參閱 [將資料庫加入至可用性群組 &#40;SQL Server&#41;](availability-group-add-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-104">For information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to add a database, see [Add a Database to an Availability Group &#40;SQL Server&#41;](availability-group-add-a-database.md).</span></span>  
  
 <span data-ttu-id="18c1e-105">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="18c1e-105">**In This Topic:**</span></span>  
  
-   <span data-ttu-id="18c1e-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="18c1e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="18c1e-107">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="18c1e-107">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="18c1e-108">安全性</span><span class="sxs-lookup"><span data-stu-id="18c1e-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="18c1e-109">**若要加入資料庫，請使用：**  [將資料庫加入可用性群組精靈 (SQL Server Management Studio)](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="18c1e-109">**To add a database, using:**  [Add Database to Availability Group Wizard (SQL Server Management Studio)](#SSMSProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="18c1e-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="18c1e-110">Before You Begin</span></span>  
 <span data-ttu-id="18c1e-111">如果您從未將資料庫新增至可用性群組，請參閱[AlwaysOn 可用性群組 &#40;SQL Server&#41;的必要條件、限制和建議](prereqs-restrictions-recommendations-always-on-availability.md)中的「可用性資料庫」一節。</span><span class="sxs-lookup"><span data-stu-id="18c1e-111">If you have never added a database to an availability group, see the "Availability Databases" section in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="Prerequisites"></a><span data-ttu-id="18c1e-112">必要條件、限制和建議</span><span class="sxs-lookup"><span data-stu-id="18c1e-112">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="18c1e-113">您必須連接到裝載目前主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="18c1e-113">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="18c1e-114">如果資料庫已加密，甚至包含資料庫加密金鑰 (DEK)，您就無法使用 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 或 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] ，將資料庫加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18c1e-114">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="18c1e-115">即使加密的資料庫已經解密，其記錄備份可能包含加密資料。</span><span class="sxs-lookup"><span data-stu-id="18c1e-115">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="18c1e-116">在此情況中，資料庫的完整初始資料同步處理可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="18c1e-116">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="18c1e-117">這是因為還原記錄作業可能需要資料庫加密金鑰 (DEK) 所使用的憑證，而該憑證可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="18c1e-117">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="18c1e-118">**若要讓解密的資料庫能夠透過精靈加入至可用性群組：**</span><span class="sxs-lookup"><span data-stu-id="18c1e-118">**To make a decrypted database eligible to add to an availability group using the wizard:**</span></span>  
  
    1.  <span data-ttu-id="18c1e-119">建立主要資料庫的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="18c1e-119">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="18c1e-120">建立主要資料庫的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="18c1e-120">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="18c1e-121">在裝載次要複本的伺服器執行個體上還原資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="18c1e-121">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="18c1e-122">從主要資料庫建立新的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="18c1e-122">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="18c1e-123">在次要資料庫上還原這個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="18c1e-123">Restore this log backup on the secondary database.</span></span>  
  
-   <span data-ttu-id="18c1e-124">**使用完整初始資料同步處理的必要條件**</span><span class="sxs-lookup"><span data-stu-id="18c1e-124">**Prerequisites for using full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="18c1e-125">每個裝載可用性群組複本之伺服器執行個體上的所有資料庫檔案路徑均須相同。</span><span class="sxs-lookup"><span data-stu-id="18c1e-125">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="18c1e-126">任何裝載次要複本的伺服器執行個體上皆不應存在主要資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="18c1e-126">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="18c1e-127">這表示目前還不可有任何新次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="18c1e-127">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="18c1e-128">您必須指定網路共用，精靈才能建立及存取備份。</span><span class="sxs-lookup"><span data-stu-id="18c1e-128">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="18c1e-129">對於主要複本，用於啟動 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帳戶必須具有網路共用的讀取與寫入檔案系統權限。</span><span class="sxs-lookup"><span data-stu-id="18c1e-129">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="18c1e-130">如果是次要複本，此帳戶必須有網路共用的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="18c1e-130">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="18c1e-131">如果您無法使用精靈執行完整初始資料同步處理，則必須手動準備次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="18c1e-131">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="18c1e-132">您可以在執行精靈前後進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="18c1e-132">You can do this before or after running the wizard.</span></span> <span data-ttu-id="18c1e-133">如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18c1e-133">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="18c1e-134">Security</span><span class="sxs-lookup"><span data-stu-id="18c1e-134">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="18c1e-135">權限</span><span class="sxs-lookup"><span data-stu-id="18c1e-135">Permissions</span></span>  
 <span data-ttu-id="18c1e-136">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="18c1e-136">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a><span data-ttu-id="18c1e-137">使用 [將資料庫加入至可用性組嚮導] (SQL Server Management Studio) </span><span class="sxs-lookup"><span data-stu-id="18c1e-137">Using the Add Database to Availability Group Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="18c1e-138">**使用將資料庫加入至可用性群組精靈**</span><span class="sxs-lookup"><span data-stu-id="18c1e-138">**To Use the Add Database to Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="18c1e-139">在 [物件總管] 中，連接到裝載可用性群組之主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="18c1e-139">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="18c1e-140">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="18c1e-140">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="18c1e-141">以滑鼠右鍵按一下您要加入資料庫的可用性群組，並選取 [加入資料庫]\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="18c1e-141">Right-click the availability group to which you are adding a database, and select the **Add Database** command.</span></span> <span data-ttu-id="18c1e-142">這個命令會啟動 [將資料庫加入至可用性群組] 精靈。</span><span class="sxs-lookup"><span data-stu-id="18c1e-142">This command launches the Add Database to Availability Group Wizard.</span></span>  
  
4.  <span data-ttu-id="18c1e-143">在 **[選取資料庫]** 頁面上，選取一個或多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="18c1e-143">On the **Select Databases** page, select one or more databases.</span></span> <span data-ttu-id="18c1e-144">如需詳細資訊，請參閱 [[選取資料庫] 頁面 &#40;新增可用性組嚮導-加入資料庫 Wizard&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-144">For more information, see [Select Databases Page &#40;New Availability Group Wizard-Add Database Wizard&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md).</span></span>  
  
5.  <span data-ttu-id="18c1e-145">在 **[選取初始資料同步處理]** 頁面上，選擇您要如何建立新的次要資料庫並將它聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18c1e-145">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="18c1e-146">選擇下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="18c1e-146">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="18c1e-147">**完整**</span><span class="sxs-lookup"><span data-stu-id="18c1e-147">**Full**</span></span>  
  
         <span data-ttu-id="18c1e-148">只有在您的環境符合自動啟動初始資料同步處理的需求時，才選取此選項 (如需詳細資訊，請參閱本主題稍早的 [必要條件、限制和建議](#Prerequisites))。</span><span class="sxs-lookup"><span data-stu-id="18c1e-148">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic).</span></span>  
  
         <span data-ttu-id="18c1e-149">如果您選取 **[完整]**，在建立可用性群組之後，精靈會嘗試將每個主要資料庫及其交易記錄備份至網路共用，並在裝載次要複本的每個伺服器執行個體上還原這些備份。</span><span class="sxs-lookup"><span data-stu-id="18c1e-149">If you select **Full**, after creating the availability group, the wizard will attempt to back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts an secondary replica.</span></span> <span data-ttu-id="18c1e-150">然後精靈會將每個次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18c1e-150">The wizard will then join every secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="18c1e-151">在 **[指定所有複本可存取的共用網路位置:]** 欄位中，指定裝載複本的所有伺服器執行個體都有讀寫存取的備份共用。</span><span class="sxs-lookup"><span data-stu-id="18c1e-151">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="18c1e-152">記錄備份將是記錄備份鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="18c1e-152">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="18c1e-153">請適當地儲存記錄備份檔案。</span><span class="sxs-lookup"><span data-stu-id="18c1e-153">Store the log backup files appropriately.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="18c1e-154">如需檔案系統必要權限的資訊，請參閱本主題稍早的 [必要條件](#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-154">For information about the required file-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="18c1e-155">**僅聯結**</span><span class="sxs-lookup"><span data-stu-id="18c1e-155">**Join only**</span></span>  
  
         <span data-ttu-id="18c1e-156">如果您已經在將裝載次要複本的伺服器執行個體上手動備妥次要資料庫，就可以選取此選項。</span><span class="sxs-lookup"><span data-stu-id="18c1e-156">If you have manually prepared secondary databases on the server instances that will host the secondary replicas, you can select this option.</span></span> <span data-ttu-id="18c1e-157">然後精靈會將現有的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18c1e-157">The wizard will join the existing secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="18c1e-158">**略過初始資料同步處理**</span><span class="sxs-lookup"><span data-stu-id="18c1e-158">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="18c1e-159">如果要使用您自己的主要資料庫的資料庫和記錄備份，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="18c1e-159">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="18c1e-160">如需詳細資訊，請參閱[於 AlwaysOn 次要資料庫啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-160">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
     <span data-ttu-id="18c1e-161">如需詳細資訊，請參閱[&#40;AlwaysOn 可用性群組嚮導&#41;中選取初始資料同步處理頁面](select-initial-data-synchronization-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-161">For more information, see [Select Initial Data Synchronization Page &#40;AlwaysOn Availability Group Wizards&#41;](select-initial-data-synchronization-page-always-on-availability-group-wizards.md).</span></span>  
  
6.  <span data-ttu-id="18c1e-162">在 **[連接到現有次要複本]** 頁面上，如果裝載此可用性群組之可用性複本的所有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體都是在相同使用者帳戶下以服務方式執行，請按一下 **[全部連接]**。</span><span class="sxs-lookup"><span data-stu-id="18c1e-162">On the **Connect to Existing Secondary Replicas** page, if the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host the availability replicas for this availability group are all running as a service in the same user account, click **Connect all**.</span></span> <span data-ttu-id="18c1e-163">如果有任何伺服器執行個體是在不同的帳戶下以服務方式執行，請按一下每個伺服器執行個體名稱右邊的個別 **[連接]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="18c1e-163">If any of the server instances are running as a service under different accounts, click the individual **Connect** button to the right of each server instance name.</span></span>  
  
     <span data-ttu-id="18c1e-164">如需詳細資訊，請參閱[連接到現有的次要複本頁面 &#40;新增複本嚮導和加入資料庫 wizard&#41;](connect-to-existing-secondary-replicas-page.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-164">For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard and Add Databases Wizard&#41;](connect-to-existing-secondary-replicas-page.md).</span></span>  
  
7.  <span data-ttu-id="18c1e-165">**[驗證]** 頁面會驗證您在此精靈中指定的值是否符合 [新增可用性群組精靈] 的需求。</span><span class="sxs-lookup"><span data-stu-id="18c1e-165">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the New Availability Group Wizard.</span></span> <span data-ttu-id="18c1e-166">若要進行變更，您可以按 **[上一步]** 返回先前的精靈頁面，以變更一個或多個值。</span><span class="sxs-lookup"><span data-stu-id="18c1e-166">To make a change, you can click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="18c1e-167">然後按 **[下一步]** 返回 **[驗證]** 頁面，再按一下 **[重新執行驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="18c1e-167">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
     <span data-ttu-id="18c1e-168">如需詳細資訊，請參閱[&#40;AlwaysOn 可用性群組嚮導&#41;的驗證頁面](validation-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-168">For more information, see [Validation Page &#40;AlwaysOn Availability Group Wizards&#41;](validation-page-always-on-availability-group-wizards.md).</span></span>  
  
8.  <span data-ttu-id="18c1e-169">在 **[摘要]** 頁面上，檢閱您為新的可用性群組的選擇。</span><span class="sxs-lookup"><span data-stu-id="18c1e-169">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="18c1e-170">若要進行變更，請按 **[上一步]** 返回相關頁面。</span><span class="sxs-lookup"><span data-stu-id="18c1e-170">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="18c1e-171">進行變更之後，請按 **[下一步]** 返回 **[摘要]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="18c1e-171">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
     <span data-ttu-id="18c1e-172">如需詳細資訊，請參閱[&#40;AlwaysOn 可用性群組&#41;](summary-page-always-on-availability-group-wizards.md)的 [摘要] 頁面。</span><span class="sxs-lookup"><span data-stu-id="18c1e-172">For more information, see [Summary Page &#40;AlwaysOn Availability Group Wizards&#41;](summary-page-always-on-availability-group-wizards.md).</span></span>  
  
     <span data-ttu-id="18c1e-173">如果您對所做的選擇感到滿意時，可以選擇按一下 [指令碼]，建立精靈將執行之步驟的指令碼。</span><span class="sxs-lookup"><span data-stu-id="18c1e-173">If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="18c1e-174">然後，若要建立及設定新的可用性群組，請按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="18c1e-174">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
9. <span data-ttu-id="18c1e-175">**[進度]** 頁面會顯示建立可用性群組之步驟的進度 (設定端點、建立可用性群組，並將次要複本加入群組中)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-175">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
     <span data-ttu-id="18c1e-176">如需詳細資訊，請參閱[&#40;AlwaysOn 可用性群組嚮導&#41;的進度頁面](progress-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-176">For more information, see [Progress Page &#40;AlwaysOn Availability Group Wizards&#41;](progress-page-always-on-availability-group-wizards.md).</span></span>  
  
10. <span data-ttu-id="18c1e-177">當這些步驟完成時， **[結果]** 頁面會顯示每個步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="18c1e-177">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="18c1e-178">如果所有這些步驟都成功，表示新的可用性群組已完成設定。</span><span class="sxs-lookup"><span data-stu-id="18c1e-178">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="18c1e-179">如果任何步驟導致錯誤，您可能需要手動完成設定。</span><span class="sxs-lookup"><span data-stu-id="18c1e-179">If any of the steps result in an error, you might need to manually complete the configuration.</span></span> <span data-ttu-id="18c1e-180">如需有關給定錯誤原因的詳細資訊，請按一下 **[結果]** 資料行中相關聯的 [錯誤] 連結。</span><span class="sxs-lookup"><span data-stu-id="18c1e-180">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="18c1e-181">當精靈完成時，按一下 **[關閉]** 以結束。</span><span class="sxs-lookup"><span data-stu-id="18c1e-181">When the wizard completes, click **Close** to exit.</span></span>  
  
     <span data-ttu-id="18c1e-182">如需詳細資訊，請參閱[結果頁面 &#40;AlwaysOn 可用性群組精靈&#41;](results-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-182">For more information, see [Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md).</span></span>  
  
11. <span data-ttu-id="18c1e-183">如果初始資料同步處理並未在所有次要資料庫上自動啟動，您需要設定任何尚未聯結的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="18c1e-183">If initial data synchronization was not automatically started on all of you secondary database, you need to configure any not-yet-joined secondary databases.</span></span> <span data-ttu-id="18c1e-184">如需詳細資訊，請參閱[於 AlwaysOn 次要資料庫啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-184">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="18c1e-185">相關工作</span><span class="sxs-lookup"><span data-stu-id="18c1e-185">Related Tasks</span></span>  
  
-   [<span data-ttu-id="18c1e-186">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18c1e-186">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="18c1e-187">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18c1e-187">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="18c1e-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18c1e-188">See Also</span></span>  
 <span data-ttu-id="18c1e-189">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="18c1e-189">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="18c1e-190">[AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="18c1e-190">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="18c1e-191">[將資料庫新增至可用性群組 &#40;SQL Server&#41;](availability-group-add-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="18c1e-191">[Add a Database to an Availability Group &#40;SQL Server&#41;](availability-group-add-a-database.md) </span></span>  
 <span data-ttu-id="18c1e-192">[在 AlwaysOn 次要資料庫上啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="18c1e-192">[Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md) </span></span>  
 [<span data-ttu-id="18c1e-193">將資料庫加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18c1e-193">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
  
