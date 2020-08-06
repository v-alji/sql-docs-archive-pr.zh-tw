---
title: 使用新增 Azure 複本精靈 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f7ee9e80f0511fe23aebb887b15b5e8b7e9cabf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687156"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a><span data-ttu-id="b037e-102">使用加入 Azure 複本精靈 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b037e-102">Use the Add Azure Replica Wizard (SQL Server)</span></span>
  <span data-ttu-id="b037e-103">使用 [加入 Azure 複本] 嚮導，協助您在混合式 IT 中建立新的 Azure VM，並將其設定為新的或現有 AlwaysOn 可用性群組的次要複本。</span><span class="sxs-lookup"><span data-stu-id="b037e-103">Use the Add Azure Replica Wizard to help you create a new Azure VM in hybrid IT and configure it as a secondary replica for a new or existing AlwaysOn availability group.</span></span>  
  
-   <span data-ttu-id="b037e-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="b037e-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b037e-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="b037e-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="b037e-106">安全性</span><span class="sxs-lookup"><span data-stu-id="b037e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b037e-107">**使用下列方法加入複本：**  [加入 Azure 複本精靈 (SQL Server Management Studio)](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="b037e-107">**To add a replica, using:**  [Add Azure Replica Wizard (SQL Server Management Studio)](#SSMSProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b037e-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="b037e-108">Before You Begin</span></span>  
 <span data-ttu-id="b037e-109">如果您從未將任何可用性複本新增至可用性群組，請參閱[AlwaysOn 可用性群組 &#40;SQL Server&#41;的必要條件、限制和建議](prereqs-restrictions-recommendations-always-on-availability.md)中的「伺服器實例」和「可用性群組和複本」小節。</span><span class="sxs-lookup"><span data-stu-id="b037e-109">If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="b037e-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="b037e-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="b037e-111">您必須連接到裝載目前主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b037e-111">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="b037e-112">您必須擁有混合式 IT 環境，其中的內部部署子網路具有 Azure 的站對站 VPN。</span><span class="sxs-lookup"><span data-stu-id="b037e-112">You must have a hybrid-IT environment where your on-premise subnet has a site-to-site VPN with Azure.</span></span> <span data-ttu-id="b037e-113">如需詳細資訊，請參閱 [使用 Azure 傳統入口網站建立具有站對站 VPN 連線的虛擬網路](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create)。</span><span class="sxs-lookup"><span data-stu-id="b037e-113">For more information, see [Configure a Site-to-Site VPN in the Management Portal](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).</span></span>  
  
-   <span data-ttu-id="b037e-114">您的可用性群組必須包含內部部署可用性複本。</span><span class="sxs-lookup"><span data-stu-id="b037e-114">Your availability group must contain on-premise availability replicas.</span></span>  
  
-   <span data-ttu-id="b037e-115">如果可用性群組接聽程式的用戶端想要在可用性群組容錯移轉至 Azure 複本時維持接聽程式的連線能力，它們就必須具有網際網路的連線能力。</span><span class="sxs-lookup"><span data-stu-id="b037e-115">Clients to the availability group listener must have connectivity to the Internet if they want to maintain connectivity with the listener when the availability group is failed over to an Azure replica.</span></span>  
  
-   <span data-ttu-id="b037e-116">**使用完整初始資料同步處理的必要條件** ：您需要指定網路共用，才能讓精靈建立及存取備份。</span><span class="sxs-lookup"><span data-stu-id="b037e-116">**Prerequisites for using full initial data synchronization** You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="b037e-117">對於主要複本，用於啟動 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帳戶必須具有網路共用的讀取與寫入檔案系統權限。</span><span class="sxs-lookup"><span data-stu-id="b037e-117">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="b037e-118">如果是次要複本，此帳戶必須有網路共用的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="b037e-118">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="b037e-119">如果您無法使用精靈執行完整初始資料同步處理，則必須手動準備次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="b037e-119">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="b037e-120">您可以在執行精靈前後進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="b037e-120">You can do this before or after running the wizard.</span></span> <span data-ttu-id="b037e-121">如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="b037e-121">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b037e-122">Security</span><span class="sxs-lookup"><span data-stu-id="b037e-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b037e-123">權限</span><span class="sxs-lookup"><span data-stu-id="b037e-123">Permissions</span></span>  
 <span data-ttu-id="b037e-124">請參閱 [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)</span><span class="sxs-lookup"><span data-stu-id="b037e-124">See [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)</span></span>  
  
##  <a name="using-the-add-azure-replica-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b037e-125">使用加入 Azure 複本精靈 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b037e-125">Using the Add Azure Replica Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="b037e-126">您可以從 [指定複本頁面](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)啟動 [加入 Azure 複本精靈]。</span><span class="sxs-lookup"><span data-stu-id="b037e-126">The Add Azure Replica Wizard can be launched from the [Specify Replicas Page](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).</span></span> <span data-ttu-id="b037e-127">存取這個頁面的方式有兩種：</span><span class="sxs-lookup"><span data-stu-id="b037e-127">There are two ways to reach this page:</span></span>  
  
-   [<span data-ttu-id="b037e-128">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b037e-128">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   <span data-ttu-id="b037e-129">[使用 [將複本加入可用性群組中精靈] &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="b037e-129">[Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span></span>  
  
 <span data-ttu-id="b037e-130">一旦您啟動 [加入 Azure 複本精靈] 之後，請遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="b037e-130">Once you have launched the Add Azure Replica Wizard, follow the steps below:</span></span>  
  
1.  <span data-ttu-id="b037e-131">首先，下載您的 Azure 訂用帳戶的管理憑證。</span><span class="sxs-lookup"><span data-stu-id="b037e-131">First, download a management certificate for your Azure subscription.</span></span> <span data-ttu-id="b037e-132">按一下 [下載] 開啟登入頁面。</span><span class="sxs-lookup"><span data-stu-id="b037e-132">Click **Download** to open the sign-in page.</span></span>  
  
2.  <span data-ttu-id="b037e-133">在登入頁面中，登入您的 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b037e-133">In the sign-in page, sign in to your Azure subscription.</span></span> <span data-ttu-id="b037e-134">一旦您登入之後，此精靈就會將管理憑證安裝到本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="b037e-134">Once you are signed in, the wizard installs a management certificate onto your local machine.</span></span> <span data-ttu-id="b037e-135">當您再次使用此精靈時，就會自動載入這個管理憑證。</span><span class="sxs-lookup"><span data-stu-id="b037e-135">This management certificate is automatically loaded when you use this wizard again.</span></span> <span data-ttu-id="b037e-136">如果您已下載多個管理憑證，可以按一下 **...** 按鈕選取您想要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="b037e-136">If you have downloaded multiple management certificates, you can click the **...** button to select the one you want to use.</span></span>  
  
3.  <span data-ttu-id="b037e-137">接著，按一下 **[連接]** ，連接到您的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b037e-137">Next, connect to your subscription by clicking **Connect**.</span></span> <span data-ttu-id="b037e-138">一旦您連線之後，下拉式清單就會填入您的 Azure 參數，例如 [虛擬網路] 和 [虛擬網路子網路]。</span><span class="sxs-lookup"><span data-stu-id="b037e-138">Once you are connected, the drop-down lists are populated with your Azure parameters, such as **Virtual Network** and **Virtual Network Subnet**.</span></span>  
  
4.  <span data-ttu-id="b037e-139">針對將裝載新次要複本的 Azure VM 指定設定：</span><span class="sxs-lookup"><span data-stu-id="b037e-139">Specify the settings for the Azure VM that will host the new secondary replica:</span></span>  
  
     <span data-ttu-id="b037e-140">映像</span><span class="sxs-lookup"><span data-stu-id="b037e-140">Image</span></span>  
     <span data-ttu-id="b037e-141">要用於 Azure VM 的 SQL Server 映像名稱</span><span class="sxs-lookup"><span data-stu-id="b037e-141">The name of the SQL Server image to use for the Azure VM</span></span>  
  
     <span data-ttu-id="b037e-142">VM 大小</span><span class="sxs-lookup"><span data-stu-id="b037e-142">VM Size</span></span>  
     <span data-ttu-id="b037e-143">Azure VM 的大小</span><span class="sxs-lookup"><span data-stu-id="b037e-143">The size of the Azure VM</span></span>  
  
     <span data-ttu-id="b037e-144">虛擬機器名稱</span><span class="sxs-lookup"><span data-stu-id="b037e-144">VM Name</span></span>  
     <span data-ttu-id="b037e-145">Azure VM 的 DNS 名稱</span><span class="sxs-lookup"><span data-stu-id="b037e-145">The DNS name of the Azure VM</span></span>  
  
     <span data-ttu-id="b037e-146">VM 使用者名稱</span><span class="sxs-lookup"><span data-stu-id="b037e-146">VM Username</span></span>  
     <span data-ttu-id="b037e-147">Azure VM 預設系統管理員的使用者名稱</span><span class="sxs-lookup"><span data-stu-id="b037e-147">The username of the default administrator for the Azure VM</span></span>  
  
     <span data-ttu-id="b037e-148">VM 系統管理員密碼 (和確認密碼)</span><span class="sxs-lookup"><span data-stu-id="b037e-148">VM Administrator Password (and Confirm Password)</span></span>  
     <span data-ttu-id="b037e-149">Azure VM 預設系統管理員的密碼</span><span class="sxs-lookup"><span data-stu-id="b037e-149">The password for the default administrator for the Azure VM</span></span>  
  
     <span data-ttu-id="b037e-150">虛擬網路</span><span class="sxs-lookup"><span data-stu-id="b037e-150">Virtual Network</span></span>  
     <span data-ttu-id="b037e-151">要放置 Azure VM 的虛擬網路</span><span class="sxs-lookup"><span data-stu-id="b037e-151">The virtual network in which to place the Azure VM</span></span>  
  
     <span data-ttu-id="b037e-152">虛擬網路子網路</span><span class="sxs-lookup"><span data-stu-id="b037e-152">Virtual Network Subnet</span></span>  
     <span data-ttu-id="b037e-153">要放置 Azure VM 的虛擬網路子網路</span><span class="sxs-lookup"><span data-stu-id="b037e-153">The virtual network subnet in which to place the Azure VM</span></span>  
  
     <span data-ttu-id="b037e-154">網域</span><span class="sxs-lookup"><span data-stu-id="b037e-154">Domain</span></span>  
     <span data-ttu-id="b037e-155">要加入 Azure VM 的 Active Directory (AD) 網域</span><span class="sxs-lookup"><span data-stu-id="b037e-155">The Active Directory (AD) domain to join the Azure VM</span></span>  
  
     <span data-ttu-id="b037e-156">網域使用者名稱</span><span class="sxs-lookup"><span data-stu-id="b037e-156">Domain Username</span></span>  
     <span data-ttu-id="b037e-157">用來將 Azure VM 加入至網域的 AD 使用者名稱</span><span class="sxs-lookup"><span data-stu-id="b037e-157">The AD username used to join the Azure VM to the domain</span></span>  
  
     <span data-ttu-id="b037e-158">密碼</span><span class="sxs-lookup"><span data-stu-id="b037e-158">Password</span></span>  
     <span data-ttu-id="b037e-159">用來將 Azure VM 加入至網域的密碼</span><span class="sxs-lookup"><span data-stu-id="b037e-159">The password used to join the Azure VM to the domain</span></span>  
  
5.  <span data-ttu-id="b037e-160">按一下 **[確定]** 認可您的設定並結束 [加入 Azure 複本精靈]。</span><span class="sxs-lookup"><span data-stu-id="b037e-160">Click **OK** to commit your settings and exit the Add Azure Replica Wizard.</span></span>  
  
6.  <span data-ttu-id="b037e-161">繼續針對 [指定複本頁面](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) 進行其餘組態設定步驟，就像設定任何新的複本一樣。</span><span class="sxs-lookup"><span data-stu-id="b037e-161">Continue with the rest of the configuration steps for [Specify Replicas Page](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) as you do for any new replica.</span></span>  
  
     <span data-ttu-id="b037e-162">當您完成 [可用性群組嚮導] 或 [將複本加入至可用性組嚮導] 之後，設定程式會執行 Azure 中的所有作業來建立新的 VM、將它加入 AD 網域、將它新增至 Windows 叢集、啟用 AlwaysOn 高可用性，並將新的複本加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="b037e-162">Once you are finished with the Availability Group Wizard or the Add Replica to Availability Group Wizard, the configuration process performs all operations in Azure to create the new VM, join it to the AD domain, add it to the Windows cluster, enable AlwaysOn High Availability, and add the new replica to the availability group.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b037e-163">相關工作</span><span class="sxs-lookup"><span data-stu-id="b037e-163">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b037e-164">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b037e-164">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b037e-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b037e-165">See Also</span></span>  
 <span data-ttu-id="b037e-166">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b037e-166">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="b037e-167">[AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="b037e-167">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 [<span data-ttu-id="b037e-168">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b037e-168">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
