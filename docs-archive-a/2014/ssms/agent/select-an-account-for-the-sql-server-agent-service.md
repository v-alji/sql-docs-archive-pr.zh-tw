---
title: 選取 SQL Server Agent 服務的帳戶 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, accounts
- startup accounts [SQL Server]
- SQL Server Agent service, accounts
- accounts [SQL Server], SQL Server Agent
- Windows groups [SQL Server Agent]
- SQL Server Agent, permissions
- members [SQL Server], SQL Server Agent service
- Windows domain accounts [SQL Server]
- security [SQL Server], SQL Server Agent
ms.assetid: fe658e32-9e6b-4147-a189-7adc3bd28fe7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 25e470bb8bde192d05a078a77fce71850c641854
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704666"
---
# <a name="select-an-account-for-the-sql-server-agent-service"></a><span data-ttu-id="cb026-102">選取 SQL Server Agent 服務的帳戶</span><span class="sxs-lookup"><span data-stu-id="cb026-102">Select an Account for the SQL Server Agent Service</span></span>
  <span data-ttu-id="cb026-103">服務啟動帳戶會定義 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Agent 用來執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 帳戶及其網路權限。</span><span class="sxs-lookup"><span data-stu-id="cb026-103">The service startup account defines the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account in which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs and its network permissions.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cb026-104">Agent 會以指定的使用者帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="cb026-104">Agent runs as a specified user account.</span></span> <span data-ttu-id="cb026-105">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員選擇下列選項，藉此選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務的帳戶：</span><span class="sxs-lookup"><span data-stu-id="cb026-105">You select an account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, where you can choose from the following options:</span></span>  
  
-   <span data-ttu-id="cb026-106">**內建帳戶**。</span><span class="sxs-lookup"><span data-stu-id="cb026-106">**Built-in account**.</span></span> <span data-ttu-id="cb026-107">您可從下列內建 Windows 服務帳戶的清單中進行選擇：</span><span class="sxs-lookup"><span data-stu-id="cb026-107">You can choose from a list of the following built-in Windows service accounts:</span></span>  
  
    -   <span data-ttu-id="cb026-108">**本機系統**帳戶。</span><span class="sxs-lookup"><span data-stu-id="cb026-108">**Local System** account.</span></span> <span data-ttu-id="cb026-109">這個帳戶的名稱是 NT AUTHORITY\System。</span><span class="sxs-lookup"><span data-stu-id="cb026-109">The name of this account is NT AUTHORITY\System.</span></span> <span data-ttu-id="cb026-110">它是功能強大的帳戶，可不受限制地存取所有本機系統資源。</span><span class="sxs-lookup"><span data-stu-id="cb026-110">It is a powerful account that has unrestricted access to all local system resources.</span></span> <span data-ttu-id="cb026-111">這個帳戶是本機電腦上的 Windows **Administrators** 群組成員，因此也是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="cb026-111">It is a member of the Windows **Administrators** group on the local computer, and is therefore a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin** fixed server role</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="cb026-112">[本機系統帳戶]\*\*\*\* 選項僅用於回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="cb026-112">The **Local System account** option is provided for backward compatibility only.</span></span> <span data-ttu-id="cb026-113">本機系統帳戶具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 不需要的權限。</span><span class="sxs-lookup"><span data-stu-id="cb026-113">The Local System account has permissions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not require.</span></span> <span data-ttu-id="cb026-114">避免以本機系統帳戶身分執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="cb026-114">Avoid running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent as the Local System account.</span></span> <span data-ttu-id="cb026-115">為了改善安全性，請搭配使用 Windows 網域帳戶與下節「Windows 網域帳戶權限」所列的權限。</span><span class="sxs-lookup"><span data-stu-id="cb026-115">For improved security, use a Windows domain account with the permissions listed in the following section, "Windows Domain Account Permissions."</span></span>  
  
-   <span data-ttu-id="cb026-116">**此帳戶**。</span><span class="sxs-lookup"><span data-stu-id="cb026-116">**This account**.</span></span> <span data-ttu-id="cb026-117">可讓您指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務用來執行的 Windows 網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="cb026-117">Lets you specify the Windows domain account in which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service runs.</span></span> <span data-ttu-id="cb026-118">我們建議您選擇非 Windows **Administrators** 群組成員的 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cb026-118">We recommend choosing a Windows user account that is not a member of the Windows **Administrators** group.</span></span> <span data-ttu-id="cb026-119">然而， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶不是本機 **Administrators** 群組的成員時，則會限制多伺服器管理的使用。</span><span class="sxs-lookup"><span data-stu-id="cb026-119">However, there are limitations for using multiserver administration when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account is not a member of the local **Administrators** group.</span></span> <span data-ttu-id="cb026-120">如需詳細資訊，請參閱本主題稍後的＜支援的服務帳戶類型＞。</span><span class="sxs-lookup"><span data-stu-id="cb026-120">For more information, see 'Supported Service Account Types' that follows in this topic.</span></span>  
  
## <a name="windows-domain-account-permissions"></a><span data-ttu-id="cb026-121">Windows 網域帳戶權限</span><span class="sxs-lookup"><span data-stu-id="cb026-121">Windows Domain Account Permissions</span></span>  
 <span data-ttu-id="cb026-122">為了改善安全性，請選取 [這個帳戶]\*\*\*\*，以指定 Windows 網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="cb026-122">For improved security, select **This account**, which specifies a Windows domain account.</span></span> <span data-ttu-id="cb026-123">您指定的 Windows 網域帳戶必須具有下列權限：</span><span class="sxs-lookup"><span data-stu-id="cb026-123">The Windows domain account that you specify must have the following permissions:</span></span>  
  
-   <span data-ttu-id="cb026-124">在所有 Windows 版本中，以服務方式登入的權限 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="cb026-124">In all Windows versions, permission to log on as a service (SeServiceLogonRight)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb026-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶必須是網域控制站上 Pre-Windows 2000 Compatible Access 群組的一部分，否則，非 Windows Administrators 群組成員之網域使用者所擁有的作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="cb026-125">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account must be part of the Pre-Windows 2000 Compatible Access group on the domain controller, or jobs that are owned by domain users who are not members of the Windows Administrators group will fail.</span></span>  
  
-   <span data-ttu-id="cb026-126">在 Windows 伺服器中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務用以執行的帳戶需要下列權限，才能支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy。</span><span class="sxs-lookup"><span data-stu-id="cb026-126">In Windows servers, the account that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service runs as requires the following permissions to be able to support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxies.</span></span>  
  
    -   <span data-ttu-id="cb026-127">略過周遊檢查的權限 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="cb026-127">Permission to bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
    -   <span data-ttu-id="cb026-128">取代處理序層級 Token 的權限 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="cb026-128">Permission to replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
    -   <span data-ttu-id="cb026-129">調整處理序之記憶體配額的權限 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="cb026-129">Permission to adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
    -   <span data-ttu-id="cb026-130">使用批次登入類型登入的權限 (SeBatchLogonRight)</span><span class="sxs-lookup"><span data-stu-id="cb026-130">Permission to log on using the batch logon type (SeBatchLogonRight)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb026-131">如果帳戶沒有支援 Proxy 所需的權限，則只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員可以建立作業。</span><span class="sxs-lookup"><span data-stu-id="cb026-131">If the account does not have the permissions required to support proxies, only members of the **sysadmin** fixed server role can create jobs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb026-132">若要接收 WMI 警示通知，必須授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的服務帳戶對於包含 WMI 事件之命名空間的權限，以及 ALTER ANY EVENT NOTIFICATION 的權限。</span><span class="sxs-lookup"><span data-stu-id="cb026-132">To receive WMI alert notification, the service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must have been granted permission to the namespace that contains the WMI events, and ALTER ANY EVENT NOTIFICATION.</span></span>  
  
## <a name="sql-server-role-membership"></a><span data-ttu-id="cb026-133">SQL Server 角色成員資格</span><span class="sxs-lookup"><span data-stu-id="cb026-133">SQL Server Role Membership</span></span>  
 <span data-ttu-id="cb026-134">用來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務的帳戶必須是下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 角色的成員：</span><span class="sxs-lookup"><span data-stu-id="cb026-134">The account that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service runs as must be a member of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] roles:</span></span>  
  
-   <span data-ttu-id="cb026-135">帳戶必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="cb026-135">The account must be a member of the **sysadmin** fixed server role.</span></span>  
  
-   <span data-ttu-id="cb026-136">若要使用多伺服器作業處理，帳戶必須是主要伺服器上 **msdb** 資料庫角色 **TargetServersRole** 的成員。</span><span class="sxs-lookup"><span data-stu-id="cb026-136">To use multiserver job processing, the account must be a member of the **msdb** database role **TargetServersRole** on the master server.</span></span>  
  
## <a name="supported-service-account-types"></a><span data-ttu-id="cb026-137">支援的服務帳戶類型</span><span class="sxs-lookup"><span data-stu-id="cb026-137">Supported Service Account Types</span></span>  
 <span data-ttu-id="cb026-138">下表列出可用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務的 Windows 帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="cb026-138">The following table lists the Windows account types that can be used for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
|<span data-ttu-id="cb026-139">服務帳戶類型</span><span class="sxs-lookup"><span data-stu-id="cb026-139">Service account type</span></span>|<span data-ttu-id="cb026-140">非叢集伺服器</span><span class="sxs-lookup"><span data-stu-id="cb026-140">Nonclustered Server</span></span>|<span data-ttu-id="cb026-141">叢集伺服器</span><span class="sxs-lookup"><span data-stu-id="cb026-141">Clustered server</span></span>|<span data-ttu-id="cb026-142">網域控制站 (非叢集)</span><span class="sxs-lookup"><span data-stu-id="cb026-142">Domain controller (nonclustered)</span></span>|  
|--------------------------|---------------------------|----------------------|------------------------------------------|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="cb026-143">Windows 網域帳戶 (Windows Administrators 群組的成員)</span><span class="sxs-lookup"><span data-stu-id="cb026-143">Windows domain account (member of Windows Administrators group)</span></span>|<span data-ttu-id="cb026-144">支援</span><span class="sxs-lookup"><span data-stu-id="cb026-144">Supported</span></span>|<span data-ttu-id="cb026-145">支援</span><span class="sxs-lookup"><span data-stu-id="cb026-145">Supported</span></span>|<span data-ttu-id="cb026-146">支援</span><span class="sxs-lookup"><span data-stu-id="cb026-146">Supported</span></span>|  
|<span data-ttu-id="cb026-147">Windows 網域帳戶 (非管理)</span><span class="sxs-lookup"><span data-stu-id="cb026-147">Windows domain account (non-administrative)</span></span>|<span data-ttu-id="cb026-148">支援<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cb026-148">Supported<sup>1</sup></span></span>|<span data-ttu-id="cb026-149">支援<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cb026-149">Supported<sup>1</sup></span></span>|<span data-ttu-id="cb026-150">支援<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cb026-150">Supported<sup>1</sup></span></span>|  
|<span data-ttu-id="cb026-151">網路服務帳戶 (NT AUTHORITY\NetworkService)</span><span class="sxs-lookup"><span data-stu-id="cb026-151">Network Service account (NT AUTHORITY\NetworkService)</span></span>|<span data-ttu-id="cb026-152">支援<sup>1、3、4</sup></span><span class="sxs-lookup"><span data-stu-id="cb026-152">Supported<sup>1, 3, 4</sup></span></span>|<span data-ttu-id="cb026-153">不支援</span><span class="sxs-lookup"><span data-stu-id="cb026-153">Not supported</span></span>|<span data-ttu-id="cb026-154">不支援</span><span class="sxs-lookup"><span data-stu-id="cb026-154">Not supported</span></span>|  
|<span data-ttu-id="cb026-155">本機使用者帳戶 (非管理)</span><span class="sxs-lookup"><span data-stu-id="cb026-155">Local user account (non-administrative)</span></span>|<span data-ttu-id="cb026-156">支援<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cb026-156">Supported<sup>1</sup></span></span>|<span data-ttu-id="cb026-157">不支援</span><span class="sxs-lookup"><span data-stu-id="cb026-157">Not supported</span></span>|<span data-ttu-id="cb026-158">不適用</span><span class="sxs-lookup"><span data-stu-id="cb026-158">Not applicable</span></span>|  
|<span data-ttu-id="cb026-159">本機系統帳戶 (NT AUTHORITY\System)</span><span class="sxs-lookup"><span data-stu-id="cb026-159">Local System account (NT AUTHORITY\System)</span></span>|<span data-ttu-id="cb026-160">支援<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cb026-160">Supported<sup>2</sup></span></span>|<span data-ttu-id="cb026-161">不支援</span><span class="sxs-lookup"><span data-stu-id="cb026-161">Not supported</span></span>|<span data-ttu-id="cb026-162">支援<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cb026-162">Supported<sup>2</sup></span></span>|  
|<span data-ttu-id="cb026-163">本機服務帳戶 (NT AUTHORITY\LocalService)</span><span class="sxs-lookup"><span data-stu-id="cb026-163">Local Service account (NT AUTHORITY\LocalService)</span></span>|<span data-ttu-id="cb026-164">不支援</span><span class="sxs-lookup"><span data-stu-id="cb026-164">Not supported</span></span>|<span data-ttu-id="cb026-165">不支援</span><span class="sxs-lookup"><span data-stu-id="cb026-165">Not supported</span></span>|<span data-ttu-id="cb026-166">不支援</span><span class="sxs-lookup"><span data-stu-id="cb026-166">Not supported</span></span>|  
  
 <span data-ttu-id="cb026-167"><sup>1</sup>請參閱下面的限制1。</span><span class="sxs-lookup"><span data-stu-id="cb026-167"><sup>1</sup> See Limitation 1 below.</span></span>  
  
 <span data-ttu-id="cb026-168"><sup>2</sup>請參閱下面的限制2。</span><span class="sxs-lookup"><span data-stu-id="cb026-168"><sup>2</sup> See Limitation 2 below.</span></span>  
  
 <span data-ttu-id="cb026-169"><sup>3</sup>請參閱下面的限制3。</span><span class="sxs-lookup"><span data-stu-id="cb026-169"><sup>3</sup> See Limitation 3 below.</span></span>  
  
 <span data-ttu-id="cb026-170"><sup>4</sup>請參閱下面的限制4。</span><span class="sxs-lookup"><span data-stu-id="cb026-170"><sup>4</sup> See Limitation 4 below.</span></span>  
  
### <a name="limitation-1-using-non-administrative-accounts-for-multiserver-administration"></a><span data-ttu-id="cb026-171">限制 1：對於多伺服器管理使用非管理帳戶</span><span class="sxs-lookup"><span data-stu-id="cb026-171">Limitation 1: Using Non-administrative Accounts for Multiserver Administration</span></span>  
 <span data-ttu-id="cb026-172">在主要伺服器上編列目標伺服器可能失敗，並出現下列錯誤訊息：「編列作業失敗」。</span><span class="sxs-lookup"><span data-stu-id="cb026-172">Enlisting target servers to a master server may fail with the following error message: "The enlist operation failed."</span></span>  
  
 <span data-ttu-id="cb026-173">若要解決此錯誤，請重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="cb026-173">To resolve this error, restart both the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="cb026-174">如需詳細資訊，請參閱 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cb026-174">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
### <a name="limitation-2-using-the-local-system-account-for-multiserver-administration"></a><span data-ttu-id="cb026-175">限制 2：對於多伺服器管理使用本機系統帳戶</span><span class="sxs-lookup"><span data-stu-id="cb026-175">Limitation 2: Using the Local System Account for Multiserver Administration</span></span>  
 <span data-ttu-id="cb026-176">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務在本機系統帳戶下執行時支援多伺服器管理，但前提是主要伺服器和目標伺服器都必須位於相同電腦上。</span><span class="sxs-lookup"><span data-stu-id="cb026-176">Multiserver administration is supported when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is run under the Local System account only when both the master server and the target server reside on the same computer.</span></span> <span data-ttu-id="cb026-177">如果您使用此組態，則當您在主要伺服器上編列目標伺服器時會傳回下列訊息：</span><span class="sxs-lookup"><span data-stu-id="cb026-177">If you use this configuration, the following message is returned when you enlist target servers to the master server:</span></span>  
  
 <span data-ttu-id="cb026-178">「請確定 <目標伺服器電腦名稱>\*\* 的代理程式啟動帳戶有權限以 targetServer 的身分登入」。</span><span class="sxs-lookup"><span data-stu-id="cb026-178">"Ensure the agent start-up account for *<target_server_computer_name>* has rights to log on as targetServer."</span></span>  
  
 <span data-ttu-id="cb026-179">您可以忽略此參考訊息。</span><span class="sxs-lookup"><span data-stu-id="cb026-179">You can ignore this informational message.</span></span> <span data-ttu-id="cb026-180">編列作業應該順利完成。</span><span class="sxs-lookup"><span data-stu-id="cb026-180">The enlistment operation should complete successfully.</span></span> <span data-ttu-id="cb026-181">如需詳細資訊，請參閱 [建立多伺服器環境](create-a-multiserver-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="cb026-181">For more information, see [Create a Multiserver Environment](create-a-multiserver-environment.md).</span></span>  
  
### <a name="limitation-3-using-the-network-service-account-when-it-is-a-sql-server-user"></a><span data-ttu-id="cb026-182">限制 3：若為 SQL Server 使用者，則使用網路服務帳戶</span><span class="sxs-lookup"><span data-stu-id="cb026-182">Limitation 3: Using the Network Service Account When It Is a SQL Server User</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cb026-183">如果您是在網路服務帳戶之下執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，而且已明確授與網路服務帳戶存取權限，以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者的身分登入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，則 Agent 可能無法啟動。</span><span class="sxs-lookup"><span data-stu-id="cb026-183">Agent may fail to start if you run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under the Network Service account, and the Network Service account has been explicitly granted access to log into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="cb026-184">若要解決此問題，請將執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="cb026-184">To resolve this, reboot the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="cb026-185">這個動作只需要做一次。</span><span class="sxs-lookup"><span data-stu-id="cb026-185">This only needs to be done once.</span></span>  
  
### <a name="limitation-4-using-the-network-service-account-when-sql-server-reporting-services-is-running-on-the-same-computer"></a><span data-ttu-id="cb026-186">限制 4：當 SQL Server Reporting Services 在相同電腦上執行時，則使用網路服務帳戶</span><span class="sxs-lookup"><span data-stu-id="cb026-186">Limitation 4: Using the Network Service Account When SQL Server Reporting Services Is Running on the Same Computer</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cb026-187">如果您是在網路服務帳戶之下執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，且 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 也在相同電腦上執行，則 Agent 可能無法啟動。</span><span class="sxs-lookup"><span data-stu-id="cb026-187">Agent may fail to start if you run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under the Network Service account and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is also running on the same computer.</span></span>  
  
 <span data-ttu-id="cb026-188">若要解決此問題，請將執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦重新開機，然後重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="cb026-188">To resolve this, reboot the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running, and then restart both the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="cb026-189">這個動作只需要做一次。</span><span class="sxs-lookup"><span data-stu-id="cb026-189">This only needs to be done once.</span></span>  
  
## <a name="common-tasks"></a><span data-ttu-id="cb026-190">一般工作</span><span class="sxs-lookup"><span data-stu-id="cb026-190">Common Tasks</span></span>  
 <span data-ttu-id="cb026-191">**若要指定 SQL Server Agent 服務的啟動帳戶**</span><span class="sxs-lookup"><span data-stu-id="cb026-191">**To specify the startup account for the SQL Server Agent service**</span></span>  
  
-   [<span data-ttu-id="cb026-192">設定 SQL Server Agent 的服務啟動帳戶 &#40;SQL Server 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="cb026-192">Set the Service Startup Account for SQL Server Agent &#40;SQL Server Configuration Manager&#41;</span></span>](set-service-startup-account-sql-server-agent-sql-server-configuration-manager.md)  
  
 <span data-ttu-id="cb026-193">**若要指定 SQL Server Agent 的郵件設定檔**</span><span class="sxs-lookup"><span data-stu-id="cb026-193">**To specify the mail profile for SQL Server Agent**</span></span>  
  
-   [<span data-ttu-id="cb026-194">設定 SQL Server Agent Mail 使用 Database Mail</span><span class="sxs-lookup"><span data-stu-id="cb026-194">Configure SQL Server Agent Mail to Use Database Mail</span></span>](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
> [!NOTE]  
>  <span data-ttu-id="cb026-195">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員，指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 必須在啟動作業系統時啟動。</span><span class="sxs-lookup"><span data-stu-id="cb026-195">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to specify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must start up when the operating system starts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb026-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb026-196">See Also</span></span>  
 <span data-ttu-id="cb026-197">[設定 Windows 服務帳戶和許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="cb026-197">[Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) </span></span>  
 <span data-ttu-id="cb026-198">[管理服務的如何主題 &#40;SQL Server 組態管理員&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="cb026-198">[Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md) </span></span>  
 [<span data-ttu-id="cb026-199">實作 SQL Server Agent 安全性</span><span class="sxs-lookup"><span data-stu-id="cb026-199">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
