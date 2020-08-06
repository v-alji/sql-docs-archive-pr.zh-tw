---
title: 建立或設定可用性群組接聽程式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.newaglistener.general.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], client connectivity
ms.assetid: 2bc294f6-2312-4b6b-9478-2fb8a656e645
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2c74e92286eab4bc1be8f3f538d83d86f056cf01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710810"
---
# <a name="create-or-configure-an-availability-group-listener-sql-server"></a><span data-ttu-id="5828d-102">建立或設定可用性群組接聽程式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5828d-102">Create or Configure an Availability Group Listener (SQL Server)</span></span>
  <span data-ttu-id="5828d-103">本主題描述如何使用、或中的 PowerShell，針對 AlwaysOn 可用性群組建立或設定單一*可用性群組*接聽程式 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5828d-103">This topic describes how to create or configure a single *availability group listener* for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5828d-104">若要建立可用性群組的第一個可用性群組接聽程式，強烈建議您使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5828d-104">To create the first availability group listener of an availability group, we strongly recommend that you [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell.</span></span> <span data-ttu-id="5828d-105">除非必要 (例如建立其他接聽程式)，否則避免在 WSFC 叢集中直接建立接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-105">Avoid creating a listener directly in the WSFC cluster except when necessary, for example, to create an additional listener.</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5828d-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="5828d-106">Before You Begin</span></span>  
  
###  <a name="does-a-listener-exist-for-this-availability-group-already"></a><a name="DoesListenerExist"></a> <span data-ttu-id="5828d-107">這個可用性群組已經有接聽程式？</span><span class="sxs-lookup"><span data-stu-id="5828d-107">Does a Listener Exist for this Availability Group Already?</span></span>  
 <span data-ttu-id="5828d-108">**若要判斷可用性群組的接聽程式是否已經存在**</span><span class="sxs-lookup"><span data-stu-id="5828d-108">**To determine whether a listener already exists for the availability group**</span></span>  
  
-   [<span data-ttu-id="5828d-109">檢視可用性群組接聽程式屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5828d-109">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="5828d-110">如果接聽程式已存在，而且您想要建立其他接聽程式，請參閱本主題稍後的 [為可用性群組建立其他接聽程式 (選擇性)](#CreateAdditionalListener)。</span><span class="sxs-lookup"><span data-stu-id="5828d-110">If a listener already exists and you want to create an additional listener, see [To Create An Additional Listener for an Availability Group (Optional)](#CreateAdditionalListener), later in this topic.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5828d-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="5828d-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5828d-112">透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，您只可以為每個可用性群組建立一個接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-112">You can create only one listener per availability group through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5828d-113">通常每個可用性群組只需要一個接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-113">Typically, each availability group requires only one listener.</span></span> <span data-ttu-id="5828d-114">但是，某些客戶情況下一個可用性群組需要多個接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-114">However, some customer scenarios require multiple listeners for one availability group.</span></span>   <span data-ttu-id="5828d-115">透過 SQL Server 建立接聽程式之後，您可以使用適用容錯移轉叢集的 Windows PowerShell 或 WSFC 容錯移轉叢集管理員建立額外的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-115">After creating a listener through SQL Server, you can use Windows PowerShell for failover clusters or the WSFC Failover Cluster Manager to create additional listeners.</span></span> <span data-ttu-id="5828d-116">如需詳細資訊，請參閱本主題稍後的 [為可用性群組建立其他接聽程式 (選擇性)](#CreateAdditionalListener)。</span><span class="sxs-lookup"><span data-stu-id="5828d-116">For more information, see [To Create An Additional Listener for an Availability Group (Optional)](#CreateAdditionalListener), later in this topic.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="5828d-117">建議</span><span class="sxs-lookup"><span data-stu-id="5828d-117">Recommendations</span></span>  
 <span data-ttu-id="5828d-118">建議為多重子網路組態使用靜態 IP 位址，但並不是必要的。</span><span class="sxs-lookup"><span data-stu-id="5828d-118">Using a static IP address is recommended, although not required, for multiple subnet configurations.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="5828d-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="5828d-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="5828d-120">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="5828d-120">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="5828d-121">如果您要跨多個子網路設定可用性群組接聽程式，而且打算使用靜態 IP 位址，必須取得每個子網路的靜態 IP 位址，而且這些子網路要裝載您要建立其接聽程式之可用性群組的可用性複本。</span><span class="sxs-lookup"><span data-stu-id="5828d-121">If you are setting up an availability group listener across multiple subnets and plan to use static IP addresses, you need to get the static IP address of every subnet that hosts an availability replica for the availability group for which you are creating the listener.</span></span> <span data-ttu-id="5828d-122">您通常需要向網路管理員取得靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-122">Usually, you will need to ask your network administrators for the static IP addresses.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5828d-123">在建立第一個接聽程式之前，強烈建議您閱讀 [AlwaysOn 用戶端連接性 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5828d-123">Before you create your first listener, we strongly recommend that you read [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
###  <a name="requirements-for-the-dns-name-of-an-availability-group-listener"></a><a name="DNSnameReqs"></a> <span data-ttu-id="5828d-124">可用性群組接聽程式之 DNS 名稱的需求</span><span class="sxs-lookup"><span data-stu-id="5828d-124">Requirements for the DNS Name of an Availability Group Listener</span></span>  
 <span data-ttu-id="5828d-125">每個可用性群組接聽程式都需要一個 DNS 主機名稱，該名稱在網域中和 NetBIOS 中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="5828d-125">Each availability group listener requires a DNS host name that is unique in the domain and in NetBIOS.</span></span> <span data-ttu-id="5828d-126">DNS 名稱是字串值。</span><span class="sxs-lookup"><span data-stu-id="5828d-126">The DNS name is a string value.</span></span> <span data-ttu-id="5828d-127">此名稱只能包含英數字元、虛線 (-) 和連字號 (_) (順序不拘)。</span><span class="sxs-lookup"><span data-stu-id="5828d-127">This name can contain only alphanumeric characters, dashes (-), and hyphens (_), in any order.</span></span> <span data-ttu-id="5828d-128">DNS 主機名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5828d-128">DNS host names are case insensitive.</span></span> <span data-ttu-id="5828d-129">長度上限是 63 個字元，但是在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，您可以將長度上限指定為 15 個字元。</span><span class="sxs-lookup"><span data-stu-id="5828d-129">The maximum length is 63 characters, however, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the maximum length you can specify is 15 characters.</span></span>  
  
 <span data-ttu-id="5828d-130">我們建議您指定一個有意義的字串。</span><span class="sxs-lookup"><span data-stu-id="5828d-130">We recommend that you specify a meaningful string.</span></span> <span data-ttu-id="5828d-131">例如，如果是名為 `AG1`的可用性群組，有意義的 DNS 主機名稱會是 `ag1-listener`。</span><span class="sxs-lookup"><span data-stu-id="5828d-131">For example, for an availability group named `AG1`, a meaningful DNS host name would be `ag1-listener`.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5828d-132">NetBIOS 只會辨識 DNS 名稱中的前 15 個字元。</span><span class="sxs-lookup"><span data-stu-id="5828d-132">NetBIOS recognizes only the first 15 chars in the dns_name.</span></span> <span data-ttu-id="5828d-133">如果您有兩個由相同 Active Directory 所控制的 WSFC 叢集，而且嘗試使用超過 15 個字元的名稱以及完全相同的 15 個字元前置詞，在這兩個叢集中建立可用性群組接聽程式，就會收到一則錯誤，指出系統無法讓虛擬網路名稱資源上線。</span><span class="sxs-lookup"><span data-stu-id="5828d-133">If you have two WSFC clusters that are controlled by the same Active Directory and you try to create availability group listeners in both of clusters using names with more than 15 characters and an identical 15 character prefix, you will get an error reporting that the Virtual Network Name resource could not be brought online.</span></span> <span data-ttu-id="5828d-134">如需有關 DNS 名稱之前置詞命名規則的詳細資訊，請參閱＜ [指派網域名稱](https://technet.microsoft.com/library/cc731265\(WS.10\).aspx)＞。</span><span class="sxs-lookup"><span data-stu-id="5828d-134">For information about prefix naming rules for DNS names, see [Assigning Domain Names](https://technet.microsoft.com/library/cc731265\(WS.10\).aspx).</span></span>  
  
###  <a name="windows-permissions"></a><a name="WinPermissions"></a> <span data-ttu-id="5828d-135">Windows 權限</span><span class="sxs-lookup"><span data-stu-id="5828d-135">Windows Permissions</span></span>  
  
|<span data-ttu-id="5828d-136">權限</span><span class="sxs-lookup"><span data-stu-id="5828d-136">Permissions</span></span>|<span data-ttu-id="5828d-137">連結</span><span class="sxs-lookup"><span data-stu-id="5828d-137">Link</span></span>|  
|-----------------|----------|  
|<span data-ttu-id="5828d-138">裝載可用性群組之 WSFC 叢集的叢集物件名稱 (CNO) 必須具有「建立電腦物件」  權限。</span><span class="sxs-lookup"><span data-stu-id="5828d-138">The cluster object name (CNO) of WSFC cluster that is hosting the availability group must have **Create Computer objects** permission.</span></span><br /><br /> <span data-ttu-id="5828d-139">在 Active Directory 中，CNO 預設不會明確具有「建立電腦物件」  權限，而且可以建立 10 個虛擬電腦物件 (VCO)。</span><span class="sxs-lookup"><span data-stu-id="5828d-139">In Active Directory, a CNO by default does not have **Create Computer objects** permission explicitly and can create 10 virtual computer objects (VCOs).</span></span> <span data-ttu-id="5828d-140">在建立 10 個 VCO 之後，其他 VCO 的建立作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5828d-140">After 10 VCOs are created, the creation of additional VCOs will fail.</span></span> <span data-ttu-id="5828d-141">您可以明確授與權限給 WSFC 叢集的 CNO，以避免這個狀況。</span><span class="sxs-lookup"><span data-stu-id="5828d-141">You can avoid this by granting the permission explicitly to the WSFC cluster's CNO.</span></span> <span data-ttu-id="5828d-142">請注意，您已刪除之可用性群組的 VCO 不會自動在 Active Directory 中刪除及算為 10 個 VCO 預設限制，除非您手動加以刪除。</span><span class="sxs-lookup"><span data-stu-id="5828d-142">Note that VCOs for availability groups that you have deleted are not automatically deleted in Active Directory and count against your 10 VCO default limit unless they are manually deleted.</span></span><br /><br /> <span data-ttu-id="5828d-143">注意:在某些組織中，安全性原則會禁止將 [建立電腦物件]  權限授與個別使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5828d-143">Note: In some organizations, the security policy prohibits granting **Create Computer objects** permission to individual user accounts.</span></span>|<span data-ttu-id="5828d-144">＜Steps for configuring the account for the person who installs the cluster＞(為叢集安裝人員設定帳戶的步驟)  ，位於 [Failover Cluster Step-by-Step Guide:Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_installer) (容錯移轉叢集逐步指南：設定 Active Directory 中的帳戶)</span><span class="sxs-lookup"><span data-stu-id="5828d-144">*Steps for configuring the account for the person who installs the cluster* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_installer)</span></span><br /><br /> <span data-ttu-id="5828d-145">＜Steps for prestaging the cluster name account＞(預先設置叢集名稱帳戶的步驟)  ，位於 [Failover Cluster Step-by-Step Guide:Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating) (容錯移轉叢集逐步指南：設定 Active Directory 中的帳戶)</span><span class="sxs-lookup"><span data-stu-id="5828d-145">*Steps for prestaging the cluster name account* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating)</span></span>|  
|<span data-ttu-id="5828d-146">如果您的組織要求您為接聽程式虛擬網路名稱預先設置電腦帳戶，將需要 **Account Operator** 群組中的成員資格或網域管理員的協助。</span><span class="sxs-lookup"><span data-stu-id="5828d-146">If your organization requires that you prestage the computer account for a listener virtual network name, you will need membership in the **Account Operator** group or your domain administrator's assistance.</span></span><br /><br /> <span data-ttu-id="5828d-147">提示︰一般而言，不要為接聽程式虛擬網路名稱預先設置電腦帳戶是最簡單的。</span><span class="sxs-lookup"><span data-stu-id="5828d-147">Tip: Generally, it is simplest not to prestage the computer account for a listener virtual network name.</span></span> <span data-ttu-id="5828d-148">如果可以，讓帳戶在您執行「WSFC 高可用性精靈」時自動建立並設定。</span><span class="sxs-lookup"><span data-stu-id="5828d-148">If you can, let the account to be created and configured automatically when you run the WSFC High Availability wizard.</span></span>|<span data-ttu-id="5828d-149">*容錯移轉叢集逐步指南：設定 Active Directory 中的帳戶* 中的 [為叢集服務或應用程式預先設置帳戶的步驟](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating2)。</span><span class="sxs-lookup"><span data-stu-id="5828d-149">*Steps for prestaging an account for a clustered service or application* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating2).</span></span>|  
  
###  <a name="sql-server-permissions"></a><a name="SqlPermissions"></a> <span data-ttu-id="5828d-150">SQL Server 權限</span><span class="sxs-lookup"><span data-stu-id="5828d-150">SQL Server Permissions</span></span>  
  
|<span data-ttu-id="5828d-151">Task</span><span class="sxs-lookup"><span data-stu-id="5828d-151">Task</span></span>|<span data-ttu-id="5828d-152">權限</span><span class="sxs-lookup"><span data-stu-id="5828d-152">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5828d-153">建立可用性群組接聽程式</span><span class="sxs-lookup"><span data-stu-id="5828d-153">To create an availability group listener</span></span>|<span data-ttu-id="5828d-154">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="5828d-154">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="5828d-155">修改現有的可用性群組接聽程式</span><span class="sxs-lookup"><span data-stu-id="5828d-155">To modify an existing availability group listener</span></span>|<span data-ttu-id="5828d-156">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="5828d-156">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5828d-157">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5828d-157">Using SQL Server Management Studio</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="5828d-158">[新增可用性群組精靈](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 支援建立新可用性群組的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-158">The [New Availability Group wizard](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) supports creation of the listener for a new availability group.</span></span>  
  
 <span data-ttu-id="5828d-159">**建立或設定可用性群組接聽程式**</span><span class="sxs-lookup"><span data-stu-id="5828d-159">**To create or configure an availability group listener**</span></span>  
  
1.  <span data-ttu-id="5828d-160">在 [物件總管] 中，連接到裝載可用性群組之主要複本的伺服器執行個體，然後按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="5828d-160">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="5828d-161">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="5828d-161">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="5828d-162">按一下您要設定其接聽程式的可用性群組，然後選擇下列其中一個替代方式：</span><span class="sxs-lookup"><span data-stu-id="5828d-162">Click the availability group whose listener you want to configure, and choose one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="5828d-163">若要建立接聽程式，以滑鼠右鍵按一下 [可用性群組接聽程式]  節點，然後選取 [新增接聽程式]  命令。</span><span class="sxs-lookup"><span data-stu-id="5828d-163">To create a listener, right-click the **Availability group Listeners** node, and select the **New Listener** command.</span></span> <span data-ttu-id="5828d-164">這會開啟 **[新增可用性群組接聽程式]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5828d-164">This opens the **New Availability Group Listener** dialog box.</span></span> <span data-ttu-id="5828d-165">如需詳細資訊，請參閱本主題稍後的[加入可用性群組接聽程式 (對話方塊)](#AddAgListenerDialog)。</span><span class="sxs-lookup"><span data-stu-id="5828d-165">For more information, see [Add Availability Group Listener (Dialog Box)](#AddAgListenerDialog), later in this topic.</span></span>  
  
    -   <span data-ttu-id="5828d-166">若要變更現有接聽程式的通訊埠編號，展開 [可用性群組接聽程式]  節點、以滑鼠右鍵按一下接聽程式，然後選取 [屬性]  命令。</span><span class="sxs-lookup"><span data-stu-id="5828d-166">To change the port number of an existing listener, expand the **Availability group Listeners** node, right-click the listener, and select the **Properties** command.</span></span> <span data-ttu-id="5828d-167">在 **[通訊埠]** 欄位中輸入新的通訊埠編號，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="5828d-167">Enter the new port number into the **Port** field, and click **OK**.</span></span>  
  
###  <a name="new-availability-group-listener-dialog-box"></a><a name="AddAgListenerDialog"></a> <span data-ttu-id="5828d-168">新增可用性群組接聽程式 (對話方塊)</span><span class="sxs-lookup"><span data-stu-id="5828d-168">New Availability Group Listener (Dialog Box)</span></span>  
 <span data-ttu-id="5828d-169">**接聽程式 DNS 名稱**</span><span class="sxs-lookup"><span data-stu-id="5828d-169">**Listener DNS Name**</span></span>  
 <span data-ttu-id="5828d-170">指定可用性群組接聽程式的 DNS 主機名稱。</span><span class="sxs-lookup"><span data-stu-id="5828d-170">Specifies the DNS host name of the availability group listener.</span></span> <span data-ttu-id="5828d-171">DNS 名稱是一個字串，在網域和 NetBIOS 中都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="5828d-171">The DNS name is a string  must be unique in the domain and in NetBIOS.</span></span> <span data-ttu-id="5828d-172">此名稱只能包含英數字元、虛線 (-) 和連字號 (_) (順序不拘)。</span><span class="sxs-lookup"><span data-stu-id="5828d-172">This name can contain only alphanumeric characters, dashes (-), and hyphens (_), in any order.</span></span> <span data-ttu-id="5828d-173">DNS 主機名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5828d-173">DNS host names are case insensitive.</span></span> <span data-ttu-id="5828d-174">最大長度是 15 個字元。</span><span class="sxs-lookup"><span data-stu-id="5828d-174">The maximum length is 15 characters.</span></span>  
  
 <span data-ttu-id="5828d-175">如需詳細資訊，請參閱本主題前文中的＜ [可用性群組接聽程式之 DNS 名稱的需求](#DNSnameReqs)＞。</span><span class="sxs-lookup"><span data-stu-id="5828d-175">For more information, see [Requirements for the DNS Name of an Availability Group Listener](#DNSnameReqs), earlier in this topic.</span></span>  
  
 <span data-ttu-id="5828d-176">**通訊埠**</span><span class="sxs-lookup"><span data-stu-id="5828d-176">**Port**</span></span>  
 <span data-ttu-id="5828d-177">此接聽程式所使用的 TPC 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="5828d-177">The TPC port used by this listener.</span></span>  
  
 <span data-ttu-id="5828d-178">**網路模式**</span><span class="sxs-lookup"><span data-stu-id="5828d-178">**Network Mode**</span></span>  
 <span data-ttu-id="5828d-179">指出接聽程式所使用的 TCP 通訊協定，其中一個：</span><span class="sxs-lookup"><span data-stu-id="5828d-179">Indicates the TCP protocol used by the listener, one of:</span></span>  
  
 <span data-ttu-id="5828d-180">**DHCP**</span><span class="sxs-lookup"><span data-stu-id="5828d-180">**DHCP**</span></span>  
 <span data-ttu-id="5828d-181">接聽程式將使用執行動態主機設定通訊協定 (DHCP) 之伺服器所指派的動態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-181">The listener will us a dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).</span></span> <span data-ttu-id="5828d-182">DHCP 僅限於單一子網路。</span><span class="sxs-lookup"><span data-stu-id="5828d-182">DHCP is limited to a single subnet.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5828d-183">不建議在實際執行環境中使用 DHCP。</span><span class="sxs-lookup"><span data-stu-id="5828d-183">We do not recommend DHCP in production environment.</span></span> <span data-ttu-id="5828d-184">如果有停機時間且 DHCP IP 租用到期，則需要額外的時間來註冊與接聽程式 DNS 名稱相關聯的新 DHCP 網路 IP 位址，而影響用戶端連接。</span><span class="sxs-lookup"><span data-stu-id="5828d-184">If there is a down time and the DHCP IP lease expires, extra time is required to register the new DHCP network IP address that is associated with the listener DNS name and impact the client connectivity.</span></span> <span data-ttu-id="5828d-185">但是，DHCP 適合用於設定開發和測試環境，以驗證可用性群組的基本功能，也適合與應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="5828d-185">However, DHCP is good for setting up your development and testing environment to verify basic functions of availability groups and for integration with your applications.</span></span>  
  
 <span data-ttu-id="5828d-186">**靜態 IP**</span><span class="sxs-lookup"><span data-stu-id="5828d-186">**Static IP**</span></span>  
 <span data-ttu-id="5828d-187">接聽程式將使用一個或多個靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-187">The listener will use one or more static IP addresses.</span></span> <span data-ttu-id="5828d-188">其他 IP 位址為選擇性。</span><span class="sxs-lookup"><span data-stu-id="5828d-188">Additional IP addresses are optional.</span></span> <span data-ttu-id="5828d-189">若要建立跨多個子網路的可用性群組接聽程式，您必須在接聽程式組態中，針對每個子網路指定一個靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-189">To create an availability group listener across multiple subnets, for each subnet you must specify a static IP address in the listener configuration.</span></span> <span data-ttu-id="5828d-190">請連絡您的網路系統管理員以取得這些靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-190">Contact your network administrator to get these static IP addresses.</span></span>  
  
 <span data-ttu-id="5828d-191">如果您選取 **[靜態 IP]** ，就會在 **[網路模式]** 欄位底下出現一個子網路方格。</span><span class="sxs-lookup"><span data-stu-id="5828d-191">If you select **Static IP** a subnet grid appears below the **Network Mode** field.</span></span> <span data-ttu-id="5828d-192">此方格會顯示這個可用性群組接聽程式可存取之每個子網路的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5828d-192">This grid displays information about each subnet that can be accessed by this availability group listener.</span></span> <span data-ttu-id="5828d-193">在您按一下 **[加入]** 來加入靜態 IP 位址之前，此方格是空的。</span><span class="sxs-lookup"><span data-stu-id="5828d-193">This grid is empty until you add a static IP address by clicking **Add**.</span></span>  
  
 <span data-ttu-id="5828d-194">資料行如下：</span><span class="sxs-lookup"><span data-stu-id="5828d-194">The columns are as follows:</span></span>  
  
 <span data-ttu-id="5828d-195">**子網路**</span><span class="sxs-lookup"><span data-stu-id="5828d-195">**Subnet**</span></span>  
 <span data-ttu-id="5828d-196">顯示您加入至可用性群組接聽程式之每個子網路的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5828d-196">Displays the identifier of each subnet that you add to the availability group listener.</span></span>  
  
 <span data-ttu-id="5828d-197">**IP 位址**</span><span class="sxs-lookup"><span data-stu-id="5828d-197">**IP Address**</span></span>  
 <span data-ttu-id="5828d-198">顯示給定子網路的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-198">Displays the IP address of a given subnet.</span></span>  <span data-ttu-id="5828d-199">對於給定的子網路，IP 位址是 IPv4 位址或 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-199">For a given subnet, the IP address is either an IPv4 address or an IPv6 address.</span></span>  
  
 <span data-ttu-id="5828d-200">**加入**</span><span class="sxs-lookup"><span data-stu-id="5828d-200">**Add**</span></span>  
 <span data-ttu-id="5828d-201">按一下可將靜態 IP 位址加入至選取的子網路或此接聽程式的其他子網路。</span><span class="sxs-lookup"><span data-stu-id="5828d-201">Click to add to add a static IP address to a selected subnet or to another subnet for this listener.</span></span> <span data-ttu-id="5828d-202">這會開啟 **[加入 IP 位址]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5828d-202">This opens the **Add IP Address** dialog box.</span></span> <span data-ttu-id="5828d-203">如需詳細資訊，請參閱[加入 IP 位址對話方塊 &#40;SQL Server Management Studio&#41;](add-ip-address-dialog-box-sql-server-management-studio.md) 說明主題。</span><span class="sxs-lookup"><span data-stu-id="5828d-203">For more information, see the [Add IP Address Dialog Box &#40;SQL Server Management Studio&#41;](add-ip-address-dialog-box-sql-server-management-studio.md) help topic.</span></span>  
  
 <span data-ttu-id="5828d-204">**移除**</span><span class="sxs-lookup"><span data-stu-id="5828d-204">**Remove**</span></span>  
 <span data-ttu-id="5828d-205">按一下可從此接聽程式中移除選取的子網路。</span><span class="sxs-lookup"><span data-stu-id="5828d-205">Click to remove the selected subnet from this listener.</span></span>  
  
 <span data-ttu-id="5828d-206">**確定**</span><span class="sxs-lookup"><span data-stu-id="5828d-206">**OK**</span></span>  
 <span data-ttu-id="5828d-207">按一下可建立指定的可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-207">Click to create the specified availability group listener.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5828d-208">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5828d-208">Using Transact-SQL</span></span>  

### <a name="to-create-or-configure-an-availability-group-listener"></a><span data-ttu-id="5828d-209">建立或設定可用性群組接聽程式</span><span class="sxs-lookup"><span data-stu-id="5828d-209">To create or configure an availability group listener</span></span>
  
1.  <span data-ttu-id="5828d-210">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="5828d-210">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="5828d-211">使用 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) 陳述式的 LISTENER 選項或 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式的 ADD LISTENER 選項。</span><span class="sxs-lookup"><span data-stu-id="5828d-211">Use the LISTENER option of the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) statement or the ADD LISTENER option of the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="5828d-212">下列範例會將可用性群組接聽程式加入至名為 `MyAg2`的現有可用性群組。</span><span class="sxs-lookup"><span data-stu-id="5828d-212">The following example adds an availability group listener to an existing availability group named `MyAg2`.</span></span> <span data-ttu-id="5828d-213">系統會針對此接聽程式指定唯一的 DNS 名稱 `MyAg2ListenerIvP6`。</span><span class="sxs-lookup"><span data-stu-id="5828d-213">A unique DNS name, `MyAg2ListenerIvP6`, is specified for this listener.</span></span> <span data-ttu-id="5828d-214">兩個複本位於不同的子網路上，因此接聽程式使用靜態 IP 位址 (建議方法)。</span><span class="sxs-lookup"><span data-stu-id="5828d-214">The two replicas are on different subnets, so , as recommended, the listener uses static IP addresses.</span></span> <span data-ttu-id="5828d-215">針對這兩個可用性複本，WITH IP 子句都會指定使用 IPv6 格式的靜態 IP 位址： `2001:4898:f0:f00f::cf3c and 2001:4898:e0:f213::4ce2`。</span><span class="sxs-lookup"><span data-stu-id="5828d-215">For each of the two availability replicas, the WITH IP clause specifies a static IP address, `2001:4898:f0:f00f::cf3c and 2001:4898:e0:f213::4ce2`, which use the IPv6 format.</span></span> <span data-ttu-id="5828d-216">此範例也會指定使用選用的 PORT 引數指定通訊埠 `60173` 做為接聽程式通訊埠。</span><span class="sxs-lookup"><span data-stu-id="5828d-216">This example also specifies uses the optional PORT argument to specify port `60173` as the listener port.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg2   
          ADD LISTENER 'MyAg2ListenerIvP6' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173 );   
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="5828d-217">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5828d-217">Using PowerShell</span></span>  

### <a name="to-create-or-configure-an-availability-group-listener"></a><span data-ttu-id="5828d-218">建立或設定可用性群組接聽程式</span><span class="sxs-lookup"><span data-stu-id="5828d-218">To create or configure an availability group listener</span></span> 
  
1.  <span data-ttu-id="5828d-219">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="5828d-219">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="5828d-220">若要建立或修改可用性群組接聽程式，請使用下列其中一個指令程式：</span><span class="sxs-lookup"><span data-stu-id="5828d-220">To create or modify an availability group listener use one of the following cmdlets:</span></span>  
  
     `New-SqlAvailabilityGroupListener`  
     <span data-ttu-id="5828d-221">建立新的可用性群組接聽程式，並將其附加至現有的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="5828d-221">Creates a new availability group listener and attaches it to an existing availability group.</span></span>  
  
     <span data-ttu-id="5828d-222">例如，下列 `New-SqlAvailabilityGroupListener` 命令會針對可用性群組 `MyListener` 建立名為 `MyAg` 的可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-222">For example, the following `New-SqlAvailabilityGroupListener` command creates an availability group listener named `MyListener` for the availability group `MyAg`.</span></span> <span data-ttu-id="5828d-223">這個接聽程式將使用傳遞給 `-StaticIp` 參數的 IPv4 位址做為其虛擬 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-223">This listener will use the IPv4 address passed to the `-StaticIp` parameter as its virtual IP address.</span></span>  
  
    ```powershell
    New-SqlAvailabilityGroupListener -Name MyListener `
    -StaticIp '192.168.3.1/255.255.252.0' `
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg
    ```  
  
     `Set-SqlAvailabilityGroupListener`  
     <span data-ttu-id="5828d-224">修改現有可用性群組接聽程式上的通訊埠設定。</span><span class="sxs-lookup"><span data-stu-id="5828d-224">Modifies the port setting on an existing availability group listener.</span></span>  
  
     <span data-ttu-id="5828d-225">例如，下列 `Set-SqlAvailabilityGroupListener` 命令會將名為 `MyListener` 之可用性群組接聽程式的通訊埠編號設定為 `1535`。</span><span class="sxs-lookup"><span data-stu-id="5828d-225">For example, the following `Set-SqlAvailabilityGroupListener` command sets the port number for the availability group listener named `MyListener` to `1535`.</span></span> <span data-ttu-id="5828d-226">這個通訊埠是用來接聽接聽程式的連接。</span><span class="sxs-lookup"><span data-stu-id="5828d-226">This port is used to listen for connections to the listener.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityGroupListener -Port 1535 `
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
     `Add-SqlAGListenerstaticIp`  
     <span data-ttu-id="5828d-227">將靜態 IP 位址加入至現有的可用性群組接聽程式組態。</span><span class="sxs-lookup"><span data-stu-id="5828d-227">Adds a static IP address to an existing availability group listener configuration.</span></span> <span data-ttu-id="5828d-228">IP 位址可以是包含子網路的 IPv4 位址或 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-228">The IP address can be an IPv4 address with subnet, or an IPv6 address.</span></span>  
  
     <span data-ttu-id="5828d-229">例如，下列 `Add-SqlAGListenerstaticIp` 命令會將靜態 IPv4 位址加入至可用性群組 `MyListener` 的可用性群組接聽程式 `MyAg`。</span><span class="sxs-lookup"><span data-stu-id="5828d-229">For example, the following `Add-SqlAGListenerstaticIp` command adds a static IPv4 address to the availability group listener `MyListener` on the availability group `MyAg`.</span></span> <span data-ttu-id="5828d-230">這個 IPv6 位址會做為子網路 `255.255.252.0`之接聽程式的虛擬 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-230">This IPv6 address serves as the virtual IP address of the listener on the subnet `255.255.252.0`.</span></span> <span data-ttu-id="5828d-231">如果可用性群組跨越多個子網路，您就應該將每個子網路的靜態 IP 位址加入至接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-231">If the availability group spans multiple subnets, you should add a static IP address for each subnet to the listener.</span></span>  
  
    ```powershell
    $path = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\ MyListener" `
    Add-SqlAGListenerstaticIp -Path $path `
    -StaticIp "2001:0db8:85a3:0000:0000:8a2e:0370:7334"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="5828d-232">若要查看 Cmdlet 的語法，請在 PowerShell 環境中使用**get-help** Cmdlet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5828d-232">To view the syntax of a cmdlet, use the **Get-Help**  cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="5828d-233">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="5828d-233">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="5828d-234">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="5828d-234">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="troubleshooting"></a><span data-ttu-id="5828d-235">疑難排解</span><span class="sxs-lookup"><span data-stu-id="5828d-235">Troubleshooting</span></span>  
  
###  <a name="failure-to-create-an-availability-group-listener-because-of-active-directory-quotas"></a><a name="ADQuotas"></a><span data-ttu-id="5828d-236">因為 Active Directory 配額而無法建立可用性群組接聽程式</span><span class="sxs-lookup"><span data-stu-id="5828d-236">Failure to Create An Availability Group Listener Because of Active Directory Quotas</span></span>  
 <span data-ttu-id="5828d-237">新可用性群組接聽程式的建立作業可能會在建立時失敗，因為您已達到參與叢集節點電腦帳戶的 Active Directory 配額。</span><span class="sxs-lookup"><span data-stu-id="5828d-237">The creation of a new availability group listener may fail upon creation because you have reached an Active Directory quota for the participating cluster node machine account.</span></span>  <span data-ttu-id="5828d-238">如需詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="5828d-238">For more information, see the following articles:</span></span>  
  
-   [<span data-ttu-id="5828d-239">超連結 " https://support.microsoft.com/kb/307532 " 如何在修改電腦物件時疑難排解叢集服務帳戶</span><span class="sxs-lookup"><span data-stu-id="5828d-239">HYPERLINK "https://support.microsoft.com/kb/307532" How to Troubleshoot the Cluster Service Account When It Modifies Computer Objects</span></span>](https://support.microsoft.com/kb/307532)  
  
-   <span data-ttu-id="5828d-240">[HYPERLINK " https://technet.microsoft.com/library/cc904295(WS.10).aspx " Active Directory 配額](https://technet.microsoft.com/library/cc904295\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="5828d-240">[HYPERLINK "https://technet.microsoft.com/library/cc904295(WS.10).aspx" Active Directory Quotas](https://technet.microsoft.com/library/cc904295\(WS.10\).aspx)</span></span>  
  
##  <a name="follow-up-after-creating-an-availability-group-listener"></a><a name="FollowUp"></a><span data-ttu-id="5828d-241">後續操作：建立可用性群組接聽程式之後</span><span class="sxs-lookup"><span data-stu-id="5828d-241">Follow-up: After Creating an Availability Group Listener</span></span>  
  
###  <a name="multisubnetfailover-keyword-and-associated-features"></a><a name="MultiSubnetFailover"></a><span data-ttu-id="5828d-242">MultiSubnetFailover 關鍵字和相關聯的功能</span><span class="sxs-lookup"><span data-stu-id="5828d-242">MultiSubnetFailover Keyword and Associated Features</span></span>  
 <span data-ttu-id="5828d-243">`MultiSubnetFailover` 是新的連接字串關鍵字，可用來加快 SQL Server 2012 中 AlwaysOn 可用性群組和 AlwaysOn 容錯移轉叢集執行個體的容錯移轉速度。</span><span class="sxs-lookup"><span data-stu-id="5828d-243">`MultiSubnetFailover` is a new connection string keyword used to enable faster failover with AlwaysOn Availability Groups and AlwaysOn Failover Cluster Instances in SQL Server 2012.</span></span> <span data-ttu-id="5828d-244">當您在連接字串中設定 `MultiSubnetFailover=True` 時，就會啟用下列三項子功能：</span><span class="sxs-lookup"><span data-stu-id="5828d-244">The following three sub-features are enabled when `MultiSubnetFailover=True` is set in connection string:</span></span>  
  
-   <span data-ttu-id="5828d-245">將多重子網路快速容錯移轉至 AlwaysOn 可用性群組或容錯移轉叢集執行個體的多重子網路接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-245">Faster multi-subnet failover to a multi-subnet listener for an AlwaysOn Availability Group or Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="5828d-246">將單一子網路快速容錯移轉至 AlwaysOn 可用性群組或容錯移轉叢集執行個體的單一子網路接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-246">Faster single subnet failover to a single subnet listener for an AlwaysOn Availability Group or Failover Cluster Instances.</span></span>  
  
    -   <span data-ttu-id="5828d-247">這項功能是在連接至具有單一子網路中單一 IP 的接聽程式時使用。</span><span class="sxs-lookup"><span data-stu-id="5828d-247">This feature is used when connecting to a listener that has a single IP in a single subnet.</span></span> <span data-ttu-id="5828d-248">它會執行更積極的 TCP 連接重試，加快單一子網路容錯移轉的速度。</span><span class="sxs-lookup"><span data-stu-id="5828d-248">This performs more aggressive TCP connection retries to speed up single subnet failovers.</span></span>  
  
-   <span data-ttu-id="5828d-249">將具名執行個體解析為多重子網路 AlwaysOn 容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="5828d-249">Named instance resolution to a multi-subnet AlwaysOn Failover Cluster Instance.</span></span>  
  
    -   <span data-ttu-id="5828d-250">這項功能可針對具有多個子網路端點的 AlwaysOn 容錯移轉叢集執行個體加入具名執行個體解析支援。</span><span class="sxs-lookup"><span data-stu-id="5828d-250">This is to add named instance resolution support for an AlwaysOn Failover Cluster Instances with multiple subnet endpoints.</span></span>  
  
 <span data-ttu-id="5828d-251">**NET Framework 3.5 或 OLEDB 不支援 MultiSubnetFailover=True**</span><span class="sxs-lookup"><span data-stu-id="5828d-251">**MultiSubnetFailover=True Not Supported by NET Framework 3.5 or OLEDB**</span></span>  
  
 <span data-ttu-id="5828d-252">**問題：** 如果您的可用性群組或容錯移轉叢集實例的接聽程式名稱 (稱為 WSFC 叢集管理員中的網路名稱或用戶端存取點，) 取決於不同子網的多個 IP 位址，而且您使用 ADO.NET 搭配 .NET Framework 3.5 SP1 或 SQL Native Client 11.0 OLEDB，可用性群組接聽程式的用戶端連接要求50可能會達到連接逾時。</span><span class="sxs-lookup"><span data-stu-id="5828d-252">**Issue:** If your Availability Group or Failover Cluster Instance has a listener name (known as the network name or Client Access Point in the WSFC Cluster Manager) depending on multiple IP addresses from different subnets, and you are using either ADO.NET with .NET Framework 3.5SP1 or SQL Native Client 11.0 OLEDB, potentially 50% of your client-connection requests to the availability group listener will hit a connection timeout.</span></span>  
  
 <span data-ttu-id="5828d-253">**因應措施：** 建議您執行下列任一項工作。</span><span class="sxs-lookup"><span data-stu-id="5828d-253">**Workarounds:** We recommend that you do one of the following tasks.</span></span>  
  
-   <span data-ttu-id="5828d-254">如果您沒有操作叢集資源的權限，請將連接逾時變更為 30 秒 (此值會產生 20 秒 TCP 逾時期間加上 10 秒緩衝時間)。</span><span class="sxs-lookup"><span data-stu-id="5828d-254">If do not have the permission to manipulate cluster resources, change your connection timeout to 30 seconds (this value results in a 20-second TCP timeout period plus a 10-second buffer).</span></span>  
  
     <span data-ttu-id="5828d-255">**優點**：如果發生跨子網路的容錯移轉，用戶端復原時間很短。</span><span class="sxs-lookup"><span data-stu-id="5828d-255">**Pros**: If a cross-subnet failover occurs, client recovery time is short.</span></span>  
  
     <span data-ttu-id="5828d-256">**缺點**：半數的用戶端連線需要 20 秒以上</span><span class="sxs-lookup"><span data-stu-id="5828d-256">**Cons**: Half of the client connections will take more than 20 seconds</span></span>  
  
-   <span data-ttu-id="5828d-257">如果您有操作叢集資源的權限，比較建議的作法是將可用性群組接聽程式的網路名稱設定為 `RegisterAllProvidersIP=0`。</span><span class="sxs-lookup"><span data-stu-id="5828d-257">If you have the permission to manipulate cluster resources, the more recommended approach is to set the network name of your availability group listener to `RegisterAllProvidersIP=0`.</span></span> <span data-ttu-id="5828d-258">如需詳細資訊，請參閱本節稍後的＜RegisterAllProvidersIP 設定＞。</span><span class="sxs-lookup"><span data-stu-id="5828d-258">For more information, see "RegisterAllProvidersIP Setting" later in this section.</span></span>  
  
     <span data-ttu-id="5828d-259">**優點：** 您不需要增加用戶端連線逾時值。</span><span class="sxs-lookup"><span data-stu-id="5828d-259">**Pros:** You do not need to increase your client-connection timeout value.</span></span>  
  
     <span data-ttu-id="5828d-260">**缺點：** 如果發生跨子網容錯移轉，用戶端復原時間可能是15分鐘或更長，視您的 `HostRecordTTL` 設定和跨網站 DNS/AD 複寫排程的設定而定。</span><span class="sxs-lookup"><span data-stu-id="5828d-260">**Cons:** If a cross-subnet failover occurs, the client recovery time could be 15 minutes or longer, depending on your `HostRecordTTL` setting and the setting of your cross-site DNS/AD replication schedule.</span></span>  
  
###  <a name="registerallprovidersip-setting"></a><a name="RegisterAllProvidersIP"></a><span data-ttu-id="5828d-261">RegisterAllProvidersIP 設定</span><span class="sxs-lookup"><span data-stu-id="5828d-261">RegisterAllProvidersIP Setting</span></span>  
 <span data-ttu-id="5828d-262">當您使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 建立可用性群組接聽程式時，會在 WSFC 中建立用戶端存取點，且 `RegisterAllProvidersIP` 屬性會設定為 1 (true)。</span><span class="sxs-lookup"><span data-stu-id="5828d-262">When you use [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell to create an availability group listener, the Client Access Point is created in WSFC with the `RegisterAllProvidersIP` property set to 1 (true).</span></span> <span data-ttu-id="5828d-263">這個屬性值的影響取決於用戶端連接字串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5828d-263">The effect of this property value depends on the client connection string, as follows:</span></span>  
  
-   <span data-ttu-id="5828d-264">將 `MultiSubnetFailover` 設為 true 的連接字串</span><span class="sxs-lookup"><span data-stu-id="5828d-264">Connection strings that set `MultiSubnetFailover` to true</span></span>  
  
     [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="5828d-265">會將 `RegisterAllProvidersIP` 屬性設定為 1，以便在用戶端連接字串依建議指定 `MultiSubnetFailover = True` 的用戶端容錯移轉之後，縮短重新連接的時間。</span><span class="sxs-lookup"><span data-stu-id="5828d-265">sets the  `RegisterAllProvidersIP` property to 1 in order to reduce re-connection time after a failover for clients whose client connection strings specify `MultiSubnetFailover = True`, as recommended.</span></span> <span data-ttu-id="5828d-266">請注意，若要利用接聽程式多重子網路功能，用戶端可能需要支援 `MultiSubnetFailover` 關鍵字的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="5828d-266">Note that to take advantage of the listener multi-subnet feature, your clients might require a data provider that supports the `MultiSubnetFailover` keyword.</span></span> <span data-ttu-id="5828d-267">如需多重子網路容錯移轉之驅動程式支援的相關資訊，請參閱 [AlwaysOn 用戶端連接性 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5828d-267">For information about driver support for multi-subnet failover, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
     <span data-ttu-id="5828d-268">如需多重子網路叢集的相關資訊，請參閱 [SQL Server 多重子網路叢集 &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)，您只可以為每個可用性群組建立一個接聽程式。</span><span class="sxs-lookup"><span data-stu-id="5828d-268">For information about multi-subnet clustering, see [SQL Server Multi-Subnet Clustering &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="5828d-269">`RegisterAllProvidersIP = 1`時，如果您在 WSFC 叢集上執行 WSFC 驗證設定精靈，這個精靈會產生下列警告訊息：</span><span class="sxs-lookup"><span data-stu-id="5828d-269">When `RegisterAllProvidersIP = 1`, if you run the WSFC Validate a Configuration Wizard on the WSFC cluster, the wizard generates the following warning message:</span></span>  
    >   
    >  <span data-ttu-id="5828d-270">「網路名稱 'Name:<network_name>' 的 RegisterAllProviderIP 屬性設定為 1。在目前的叢集設定中，這個值應該設定為 0。」</span><span class="sxs-lookup"><span data-stu-id="5828d-270">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="5828d-271">請忽略這個訊息。</span><span class="sxs-lookup"><span data-stu-id="5828d-271">Please ignore this message.</span></span>  
  
-   <span data-ttu-id="5828d-272">未將 `MultiSubnetFailover` 設為 true 的連接字串</span><span class="sxs-lookup"><span data-stu-id="5828d-272">Connection strings that do not set `MultiSubnetFailover` to true</span></span>  
  
     <span data-ttu-id="5828d-273">`RegisterAllProvidersIP = 1`時，連接字串未使用 `MultiSubnetFailover = True`的任何用戶端將經歷嚴重的連線延遲。</span><span class="sxs-lookup"><span data-stu-id="5828d-273">When `RegisterAllProvidersIP = 1`, any clients whose connection strings do not use `MultiSubnetFailover = True`, will experience high latency connections.</span></span> <span data-ttu-id="5828d-274">這是因為這些用戶端嘗試循序連接到所有 IP。</span><span class="sxs-lookup"><span data-stu-id="5828d-274">This occurs because these clients attempt connections to all IPs sequentially.</span></span> <span data-ttu-id="5828d-275">相反地，如果 `RegisterAllProvidersIP` 變更為 0，則使用中 IP 位址會在 WSFC 叢集的用戶端存取點中註冊，因而減少舊版用戶端的延遲。</span><span class="sxs-lookup"><span data-stu-id="5828d-275">In contrast, if `RegisterAllProvidersIP` is changed to 0, the active IP address is registered in the Client Access Point in the WSFC cluster, reducing latency for legacy clients.</span></span> <span data-ttu-id="5828d-276">因此，如果您有需要連接到可用性群組接聽程式的舊版用戶端，而且無法使用 `MultiSubnetFailover` 屬性，我們建議您將變更 `RegisterAllProvidersIP` 為0。</span><span class="sxs-lookup"><span data-stu-id="5828d-276">Therefore, if you have legacy clients that need to connect to an availability group listener and cannot use the `MultiSubnetFailover` property, we recommend that you change `RegisterAllProvidersIP` to 0.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5828d-277">當您透過 WSFC 叢集 (容錯移轉叢集管理員 GUI) 建立可用性群組接聽程式時，`RegisterAllProvidersIP` 會預設為 0 (false)。</span><span class="sxs-lookup"><span data-stu-id="5828d-277">When you create an availability group listener through the WSFC cluster (Failover Cluster Manager GUI), `RegisterAllProvidersIP` will be 0 (false) by default.</span></span>  
  
###  <a name="hostrecordttl-setting"></a><a name="HostRecordTTL"></a><span data-ttu-id="5828d-278">HostRecordTTL 設定</span><span class="sxs-lookup"><span data-stu-id="5828d-278">HostRecordTTL Setting</span></span>  
 <span data-ttu-id="5828d-279">根據預設，用戶端會快取叢集 DNS 記錄 20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="5828d-279">By default, clients cache cluster DNS records for 20 minutes.</span></span>  <span data-ttu-id="5828d-280">透過縮短快取記錄的 `HostRecordTTL` 存留時間 (TTL)，舊版用戶端就可以更快速地重新連接。</span><span class="sxs-lookup"><span data-stu-id="5828d-280">By reducing `HostRecordTTL`, the Time to Live (TTL), for the cached record, legacy clients may reconnect more quickly.</span></span>  <span data-ttu-id="5828d-281">不過，縮短 `HostRecordTTL` 設定也可能導致傳輸至 DN 伺服器的流量增加。</span><span class="sxs-lookup"><span data-stu-id="5828d-281">However, reducing the `HostRecordTTL` setting may also result in increased traffic to the DN servers.</span></span>  
  
###  <a name="sample-powershell-script-to-disable-registerallprovidersip-and-reduce-ttl"></a><a name="SampleScript"></a><span data-ttu-id="5828d-282">用來停用 RegisterAllProvidersIP 和減少 TTL 的範例 PowerShell 腳本</span><span class="sxs-lookup"><span data-stu-id="5828d-282">Sample PowerShell Script to Disable RegisterAllProvidersIP and Reduce TTL</span></span>  
 <span data-ttu-id="5828d-283">下列 PowerShell 範例將示範如何設定接聽程式資源的 `RegisterAllProvidersIP` 和 `HostRecordTTL` 這兩個叢集參數。</span><span class="sxs-lookup"><span data-stu-id="5828d-283">The following PowerShell example demonstrates how to configure both the `RegisterAllProvidersIP` and `HostRecordTTL` cluster parameters for the listener resource.</span></span>  <span data-ttu-id="5828d-284">系統將會快取 DNS 記錄 5 分鐘，而不是預設的 20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="5828d-284">The DNS record will be cached for 5 minutes rather than the default 20 minutes.</span></span>  <span data-ttu-id="5828d-285">修改這兩個叢集參數可能會縮短無法使用 `MultiSubnetFailover` 參數的舊版用戶端在容錯移轉後連接到正確 IP 位址的時間。</span><span class="sxs-lookup"><span data-stu-id="5828d-285">Modifying both cluster parameters may reduce the time to connect to the correct IP address after a failover for legacy clients that cannot use the `MultiSubnetFailover` parameter.</span></span>  <span data-ttu-id="5828d-286">將 `yourListenerName` 取代為您要變更的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="5828d-286">Replace `yourListenerName` with the name of the listener that you are changing.</span></span>  
  
```powershell
Import-Module FailoverClusters  
Get-ClusterResource yourListenerName | Set-ClusterParameter RegisterAllProvidersIP 0
Get-ClusterResource yourListenerName|Set-ClusterParameter HostRecordTTL 300  
Stop-ClusterResource yourListenerName  
Start-ClusterResource yourAGResource  
```  
  
 <span data-ttu-id="5828d-287">如需容錯移轉期間復原次數的詳細資訊，請參閱 [Client Recovery Latency During Failover](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md#DNS)。</span><span class="sxs-lookup"><span data-stu-id="5828d-287">For more information about recovery times during failover, see [Client Recovery Latency During Failover](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md#DNS).</span></span>  
  
###  <a name="follow-up-recommendations"></a><a name="FollowUpRecommendations"></a><span data-ttu-id="5828d-288">後續建議</span><span class="sxs-lookup"><span data-stu-id="5828d-288">Follow-up Recommendations</span></span>  
 <span data-ttu-id="5828d-289">建立可用性群組接聽程式之後：</span><span class="sxs-lookup"><span data-stu-id="5828d-289">After you create an availability group listener:</span></span>  
  
-   <span data-ttu-id="5828d-290">要求網路管理員將接聽程式的 IP 位址保留為專用。</span><span class="sxs-lookup"><span data-stu-id="5828d-290">Ask your network administrator to reserve the listener's IP address for its exclusive use.</span></span>  
  
-   <span data-ttu-id="5828d-291">將接聽程式的 DNS 主機名稱提供給應用程式開發人員，以便在要求與這個可用性群組進行用戶端連接時，用於連接字串中。</span><span class="sxs-lookup"><span data-stu-id="5828d-291">Give the listener's DNS host name to application developers to use in connection strings when requesting client connections to this availability group.</span></span>  
  
-   <span data-ttu-id="5828d-292">鼓勵開發人員將用戶端連接字串更新為指定 `MultiSubnetFailover = True`(可能的話)。</span><span class="sxs-lookup"><span data-stu-id="5828d-292">Encourage developers to update client connection strings to specify `MultiSubnetFailover = True`, if possible.</span></span> <span data-ttu-id="5828d-293">如需多重子網路容錯移轉之驅動程式支援的相關資訊，請參閱 [AlwaysOn 用戶端連接性 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5828d-293">For information about driver support for multi-subnet failover, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
###  <a name="create-an-additional-listener-for-an-availability-group-optional"></a><a name="CreateAdditionalListener"></a><span data-ttu-id="5828d-294">為可用性群組建立額外的接聽程式 (選擇性) </span><span class="sxs-lookup"><span data-stu-id="5828d-294">Create an Additional Listener for an Availability Group (Optional)</span></span>  
 <span data-ttu-id="5828d-295">您透過 SQL Server 建立一個接聽程式之後，可以加入另一個接聽程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5828d-295">After you create one listener through SQL Server, you can add an additional listener, as follows:</span></span>  
  
1.  <span data-ttu-id="5828d-296">使用下列其中一種工具建立接聽程式：</span><span class="sxs-lookup"><span data-stu-id="5828d-296">Create the listener using either of the following tools:</span></span>  
  
    -   <span data-ttu-id="5828d-297">**使用 WSFC 容錯移轉叢集管理員：**</span><span class="sxs-lookup"><span data-stu-id="5828d-297">**Using WSFC Failover Cluster Manager:**</span></span>  
  
        1.  <span data-ttu-id="5828d-298">加入用戶端存取點並設定 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5828d-298">Add a client access point and configure the IP address.</span></span>  
  
        2.  <span data-ttu-id="5828d-299">使接聽程式連線。</span><span class="sxs-lookup"><span data-stu-id="5828d-299">Bring the listener online.</span></span>  
  
        3.  <span data-ttu-id="5828d-300">將相依性加入至 WSFC 可用性群組資源。</span><span class="sxs-lookup"><span data-stu-id="5828d-300">Add a dependency to the WSFC availability group resource.</span></span>  
  
         <span data-ttu-id="5828d-301">如需容錯移轉叢集管理員之對話方塊和索引標籤的相關資訊，請參閱 [使用者介面：容錯移轉叢集管理員嵌入式管理單元](https://technet.microsoft.com/library/cc772502.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5828d-301">For information about the dialog boxes and tabs of the Failover Cluster Manager, see [User Interface: The Failover Cluster Manager Snap-In](https://technet.microsoft.com/library/cc772502.aspx).</span></span>  
  
    -   <span data-ttu-id="5828d-302">**使用適用容錯移轉叢集的 Windows PowerShell：**</span><span class="sxs-lookup"><span data-stu-id="5828d-302">**Using Windows PowerShell for failover clusters:**</span></span>  
  
        1.  <span data-ttu-id="5828d-303">使用 [Add-ClusterResource](https://technet.microsoft.com/library/ee460983.aspx) 建立網路名稱和 IP 位址資源。</span><span class="sxs-lookup"><span data-stu-id="5828d-303">Use [Add-ClusterResource](https://technet.microsoft.com/library/ee460983.aspx) to create a network name and the IP address resources.</span></span>  
  
        2.  <span data-ttu-id="5828d-304">使用 [Start-ClusterResource](https://technet.microsoft.com/library/ee461056.aspx) 啟動網路名稱資源。</span><span class="sxs-lookup"><span data-stu-id="5828d-304">Use [Start-ClusterResource](https://technet.microsoft.com/library/ee461056.aspx) to start the network name resource.</span></span>  
  
        3.  <span data-ttu-id="5828d-305">使用 [Add-ClusterResourceDependency](https://technet.microsoft.com/library/ee461014.aspx) 設定網路名稱和現有 SQL Server 可用性群組資源之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="5828d-305">Use [Add-ClusterResourceDependency](https://technet.microsoft.com/library/ee461014.aspx) to set the dependency between the network name and the existing SQL Server Availability Group resource.</span></span>  
  
         <span data-ttu-id="5828d-306">如需有關使用適用容錯移轉叢集的 Windows PowerShell 之詳細資訊，請參閱 [伺服器管理員命令概觀](https://technet.microsoft.com/library/cc732757.aspx#BKMK_wps)。</span><span class="sxs-lookup"><span data-stu-id="5828d-306">For information about using Windows PowerShell for failover clusters, see [Overview of Server Manager Commands](https://technet.microsoft.com/library/cc732757.aspx#BKMK_wps).</span></span>  
  
2.  <span data-ttu-id="5828d-307">在新的接聽程式上啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 接聽。</span><span class="sxs-lookup"><span data-stu-id="5828d-307">Start [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] listening on the new listener.</span></span> <span data-ttu-id="5828d-308">建立額外的接聽程式之後，連接到裝載主要可用性群組複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體，然後使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 PowerShell 修改接聽程式通訊埠。</span><span class="sxs-lookup"><span data-stu-id="5828d-308">After creating the additional listener, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the primary replica of the availability group and use [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell to modify the listener port.</span></span>  
  
 <span data-ttu-id="5828d-309">如需詳細資訊，請參閱 [How to create multiple listeners for same availability group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx) (如何為相同可用性群組建立多個接聽程式) (SQL Server AlwaysOn 團隊部落格)。</span><span class="sxs-lookup"><span data-stu-id="5828d-309">For more information, see [How to create multiple listeners for same availability group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx) (a SQL Server AlwaysOn team blog).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5828d-310">相關工作</span><span class="sxs-lookup"><span data-stu-id="5828d-310">Related Tasks</span></span>  
  
-   [<span data-ttu-id="5828d-311">檢視可用性群組接聽程式屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5828d-311">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="5828d-312">移除可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5828d-312">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="5828d-313">相關內容</span><span class="sxs-lookup"><span data-stu-id="5828d-313">Related Content</span></span>  
  
-   [<span data-ttu-id="5828d-314">如何為相同可用性群組建立多個接聽程式</span><span class="sxs-lookup"><span data-stu-id="5828d-314">How to create multiple listeners for same availability group</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx)  
  
-   [<span data-ttu-id="5828d-315">SQL Server AlwaysOn 小組 Blog：官方 SQL Server AlwaysOn 小組的 blog</span><span class="sxs-lookup"><span data-stu-id="5828d-315">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn team blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="5828d-316">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5828d-316">See Also</span></span>  
 <span data-ttu-id="5828d-317">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5828d-317">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="5828d-318">[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="5828d-318">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="5828d-319">SQL Server 多重子網路叢集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5828d-319">SQL Server Multi-Subnet Clustering &#40;SQL Server&#41;</span></span>](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)  
