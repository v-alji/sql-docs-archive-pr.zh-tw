---
title: 註冊 Kerberos 連接的服務主體名稱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SPNs
- network connections [SQL Server], SPNs
- registering SPNs
- Server Principal Names
- SPNs [SQL Server]
ms.assetid: e38d5ce4-e538-4ab9-be67-7046e0d9504e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4db1e8b86fca057acbce29491be9c2be91f0748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599179"
---
# <a name="register-a-service-principal-name-for-kerberos-connections"></a><span data-ttu-id="470d0-102">註冊 Kerberos 連接的服務主體名稱</span><span class="sxs-lookup"><span data-stu-id="470d0-102">Register a Service Principal Name for Kerberos Connections</span></span>
  <span data-ttu-id="470d0-103">若要搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 Kerberos 驗證，需要符合下列兩個條件：</span><span class="sxs-lookup"><span data-stu-id="470d0-103">To use Kerberos authentication with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires both the following conditions to be true:</span></span>  
  
-   <span data-ttu-id="470d0-104">用戶端和伺服器電腦必須屬於相同的 Windows 網域，或在受信任的網域中。</span><span class="sxs-lookup"><span data-stu-id="470d0-104">The client and server computers must be part of the same Windows domain, or in trusted domains.</span></span>  
  
-   <span data-ttu-id="470d0-105">必須向 Active Directory 登錄「服務主要名稱」(SPN)，而 Active Directory 的角色如同 Windows 網域中的「金鑰發佈中心」。</span><span class="sxs-lookup"><span data-stu-id="470d0-105">A Service Principal Name (SPN) must be registered with Active Directory, which assumes the role of the Key Distribution Center in a Windows domain.</span></span> <span data-ttu-id="470d0-106">登錄後的 SPN 會對應至啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體服務的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="470d0-106">The SPN, after it is registered, maps to the Windows account that started the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance service.</span></span> <span data-ttu-id="470d0-107">如果尚未執行 SPN 註冊或註冊作業失敗，則 Windows 安全層無法判斷與 SPN 相關聯的帳戶，因此不會使用 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="470d0-107">If the SPN registration has not been performed or fails, the Windows security layer cannot determine the account associated with the SPN, and Kerberos authentication will not be used.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="470d0-108">如果伺服器無法自動註冊 SPN，則必須手動註冊 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-108">If the server cannot automatically register the SPN, the SPN must be registered manually.</span></span> <span data-ttu-id="470d0-109">請參閱 [手動 SPN 註冊](#Manual)。</span><span class="sxs-lookup"><span data-stu-id="470d0-109">See [Manual SPN Registration](#Manual).</span></span>  
  
 <span data-ttu-id="470d0-110">您可以透過查詢 sys.dm_exec_connections 動態管理檢視，驗證連接是否使用 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="470d0-110">You can verify that a connection is using Kerberos by querying the sys.dm_exec_connections dynamic management view.</span></span> <span data-ttu-id="470d0-111">請執行下列查詢並檢查 auth_scheme column 的值 (如果有啟用 Kerberos，該值將為 "KERBEROS")。</span><span class="sxs-lookup"><span data-stu-id="470d0-111">Run the following query and check the value of the auth_scheme column, which will be "KERBEROS" if Kerberos is enabled.</span></span>  
  
```  
SELECT auth_scheme FROM sys.dm_exec_connections WHERE session_id = @@spid ;  
```  
  
> [!TIP]  
>  <span data-ttu-id="470d0-112">**[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** 是一種診斷工具，可幫助排除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發生的 Kerberos 相關連接問題。</span><span class="sxs-lookup"><span data-stu-id="470d0-112">**[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** is a diagnostic tool that helps troubleshoot Kerberos related connectivity issues with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="470d0-113">如需詳細資訊，請參閱 [Microsoft Kerberos Configuration Manager for SQL Server](https://www.microsoft.com/download/details.aspx?id=39046)。</span><span class="sxs-lookup"><span data-stu-id="470d0-113">For more information, see [Microsoft Kerberos Configuration Manager for SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).</span></span>  
  
##  <a name="the-role-of-the-spn-in-authentication"></a><a name="Role"></a> <span data-ttu-id="470d0-114">SPN 在驗證中的角色</span><span class="sxs-lookup"><span data-stu-id="470d0-114">The Role of the SPN in Authentication</span></span>  
 <span data-ttu-id="470d0-115">當應用程式開啟連接並使用 Windows 驗證時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 會傳遞 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 電腦名稱、執行個體名稱，並選擇性地傳遞 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-115">When an application opens a connection and uses Windows Authentication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client passes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer name, instance name and, optionally, an SPN.</span></span> <span data-ttu-id="470d0-116">如果連接傳遞 SPN，則會在不進行任何變更的情況下使用該 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-116">If the connection passes an SPN it is used without any changes.</span></span>  
  
 <span data-ttu-id="470d0-117">如果連接未通過 SPN，則會根據使用的通訊協定、伺服器名稱和執行個體名稱建構預設的 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-117">If the connection does not pass an SPN, a default SPN is constructed based on the protocol used, server name, and the instance name.</span></span>  
  
 <span data-ttu-id="470d0-118">在前述兩種狀況中，SPN 都會傳送到「金鑰散佈中心」，以取得安全性 Token 來驗證連接。</span><span class="sxs-lookup"><span data-stu-id="470d0-118">In both of the preceding scenarios, the SPN is sent to the Key Distribution Center to obtain a security token for authenticating the connection.</span></span> <span data-ttu-id="470d0-119">如果無法取得安全性 Token，則驗證會使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="470d0-119">If a security token cannot be obtained, authentication uses NTLM.</span></span>  
  
 <span data-ttu-id="470d0-120">服務主要名稱 (SPN) 是用戶端用以唯一識別服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="470d0-120">A service principal name (SPN) is the name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="470d0-121">Kerberos 驗證服務可以使用 SPN 來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="470d0-121">The Kerberos authentication service can use an SPN to authenticate a service.</span></span> <span data-ttu-id="470d0-122">當用戶端想要連接到服務時，它會尋找服務的執行個體、撰寫該執行個體的 SPN、連接到服務，然後呈現服務的 SPN 以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="470d0-122">When a client wants to connect to a service, it locates an instance of the service, composes an SPN for that instance, connects to the service, and presents the SPN for the service to authenticate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="470d0-123">本主題提供的資訊也適用於使用群集的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態。</span><span class="sxs-lookup"><span data-stu-id="470d0-123">The information that is provided in this topic also applies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurations that use clustering.</span></span>  
  
 <span data-ttu-id="470d0-124">Windows 驗證是 SQL Server 驗證使用者的慣用方法。</span><span class="sxs-lookup"><span data-stu-id="470d0-124">Windows Authentication is the preferred method for users to authenticate to SQL Server.</span></span> <span data-ttu-id="470d0-125">使用 Windows 驗證的用戶端是透過 NTLM 或 Kerberos 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="470d0-125">Clients that use Windows Authentication are authenticated by either using NTLM or Kerberos.</span></span> <span data-ttu-id="470d0-126">在 Active Directory 環境中，永遠會先嘗試 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="470d0-126">In an Active Directory environment, Kerberos authentication is always attempted first.</span></span> <span data-ttu-id="470d0-127">使用具名管道的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 使用者無法使用 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="470d0-127">Kerberos authentication is not available for [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] clients using named pipes.</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="470d0-128">權限</span><span class="sxs-lookup"><span data-stu-id="470d0-128">Permissions</span></span>  
 <span data-ttu-id="470d0-129">當 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務啟動時，它會嘗試註冊服務主體名稱 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="470d0-129">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service starts, it attempts to register the Service Principal Name (SPN).</span></span> <span data-ttu-id="470d0-130">如果啟動 SQL Server 的帳戶無權在 Active Directory 網域服務中註冊 SPN，這個呼叫就會失敗，而且在應用程式事件記錄檔與 SQL Server 錯誤記錄檔中會記錄警告訊息。</span><span class="sxs-lookup"><span data-stu-id="470d0-130">If the account starting SQL Server doesn't have permission to register a SPN in Active Directory Domain Services, this call will fail and a warning message will be logged in the Application event log as well as the SQL Server error log.</span></span> <span data-ttu-id="470d0-131">若要註冊 SPN， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 必須在內建帳戶下執行，例如 Local System (不建議) 或 NETWORK SERVICE，或是在具有註冊 SPN 之權限的帳戶下執行 (例如網域管理員帳戶)。</span><span class="sxs-lookup"><span data-stu-id="470d0-131">To register the SPN, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be running under a built-in account, such as Local System (not recommended), or NETWORK SERVICE, or an account that has permission to register an SPN, such as a domain administrator account.</span></span> <span data-ttu-id="470d0-132">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在  [!INCLUDE[win7](../../includes/win7-md.md)] 或  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 作業系統上執行時，您可以使用虛擬帳戶或受管理的服務帳戶 (MSA) 執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="470d0-132">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running on the  [!INCLUDE[win7](../../includes/win7-md.md)] or  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] operating system, you can run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a virtual account or a managed service account (MSA).</span></span> <span data-ttu-id="470d0-133">虛擬帳戶和 MSA 都可以註冊 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-133">Both virtual accounts and MSA's can register an SPN.</span></span> <span data-ttu-id="470d0-134">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並未在這些帳戶的其中一個之下執行，SPN 就不會在啟動時註冊，而且網域管理員必須手動註冊 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-134">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running under one of these accounts, the SPN is not registered at startup and the domain administrator must register the SPN manually.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="470d0-135">當 Windows 網域設定為在小於 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Windows Server 2008 R2 的功能層級上執行時，受管理的服務帳戶將沒有針對 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服務註冊 SPN 的必要權限。</span><span class="sxs-lookup"><span data-stu-id="470d0-135">When the Windows domain is configured to run at less than the [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Windows Server 2008 R2 functional level, then the Managed Service Account will not have the necessary permissions to register the SPNs for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span> <span data-ttu-id="470d0-136">如果需要 Kerberos 驗證，則網域管理員應該在受管理的服務帳戶上手動註冊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-136">If Kerberos authentication is required, the Domain Administrator should manually register the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SPNs on the Managed Service Account.</span></span>  
  
 <span data-ttu-id="470d0-137">KB 文件 [How to use Kerberos authentication in SQL Server](https://support.microsoft.com/kb/319723)(如何在 SQL Server 中使用 Kerberos 驗證) 包含如何將讀取或寫入權限授與非網域管理員帳戶之 SPN 的資訊。</span><span class="sxs-lookup"><span data-stu-id="470d0-137">The KB article, [How to use Kerberos authentication in SQL Server](https://support.microsoft.com/kb/319723), contains information about how to grant read or write permission to an SPN for an account that is not a Domain Administrator.</span></span>  
  
 <span data-ttu-id="470d0-138">[How to Implement Kerberos Constrained Delegation with SQL Server 2008](https://technet.microsoft.com/library/ee191523.aspx)(如何使用 SQL Server 2008 實作 Kerberos 受限委派) 提供額外資訊</span><span class="sxs-lookup"><span data-stu-id="470d0-138">Additional information is available at [How to Implement Kerberos Constrained Delegation with SQL Server 2008](https://technet.microsoft.com/library/ee191523.aspx)</span></span>  
  
##  <a name="spn-formats"></a><a name="Formats"></a> <span data-ttu-id="470d0-139">SPN 格式</span><span class="sxs-lookup"><span data-stu-id="470d0-139">SPN Formats</span></span>  
 <span data-ttu-id="470d0-140">從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]開始，SPN 格式就有了變動，以便能夠在 TCP/IP、具名管道和共用記憶體上支援 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="470d0-140">Beginning with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SPN format is changed in order to support Kerberos authentication on TCP/IP, named pipes, and shared memory.</span></span> <span data-ttu-id="470d0-141">具名和預設執行個體支援的 SPN 格式如下所示。</span><span class="sxs-lookup"><span data-stu-id="470d0-141">The supported SPN formats for named and default instances are as follows.</span></span>  
  
 <span data-ttu-id="470d0-142">**具名執行個體**</span><span class="sxs-lookup"><span data-stu-id="470d0-142">**Named instance**</span></span>  
  
-   <span data-ttu-id="470d0-143">*MSSQLSvc/FQDN*:[_port_**|**_instancename_]，其中：</span><span class="sxs-lookup"><span data-stu-id="470d0-143">*MSSQLSvc/FQDN*:[_port_**|**_instancename_], where:</span></span>  
  
    -   <span data-ttu-id="470d0-144">*MSSQLSvc* 是所註冊的服務。</span><span class="sxs-lookup"><span data-stu-id="470d0-144">*MSSQLSvc* is the service that is being registered.</span></span>  
  
    -   <span data-ttu-id="470d0-145">*FQDN*是伺服器的完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="470d0-145">*FQDN* is the fully qualified domain name of the server.</span></span>  
  
    -   <span data-ttu-id="470d0-146">*port*是 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="470d0-146">*port* is the TCP port number.</span></span>  
  
    -   <span data-ttu-id="470d0-147">*instancename*是實例的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="470d0-147">*instancename* is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="470d0-148">**預設執行個體**</span><span class="sxs-lookup"><span data-stu-id="470d0-148">**Default instance**</span></span>  
  
-   <span data-ttu-id="470d0-149">*MSSQLSvc/fqdn*：_port_ **|** _MSSQLSvc/fqdn_，其中：</span><span class="sxs-lookup"><span data-stu-id="470d0-149">*MSSQLSvc/FQDN*:_port_**|**_MSSQLSvc/FQDN_, where:</span></span>  
  
    -   <span data-ttu-id="470d0-150">*MSSQLSvc* 是所註冊的服務。</span><span class="sxs-lookup"><span data-stu-id="470d0-150">*MSSQLSvc* is the service that is being registered.</span></span>  
  
    -   <span data-ttu-id="470d0-151">*FQDN*是伺服器的完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="470d0-151">*FQDN* is the fully qualified domain name of the server.</span></span>  
  
    -   <span data-ttu-id="470d0-152">*port*是 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="470d0-152">*port* is the TCP port number.</span></span>  
  
 <span data-ttu-id="470d0-153">新的 SPN 格式不需要通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="470d0-153">The new SPN format does not require a port number.</span></span> <span data-ttu-id="470d0-154">這表示，不使用通訊埠編號的多重通訊埠伺服器或通訊協定可以使用 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="470d0-154">This means that a multiple-port server or a protocol that does not use port numbers can use Kerberos authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="470d0-155">在 TCP/IP 連接的情況下，由於 TCP 通訊埠包含於 SPN 中，因此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必須啟用 TCP 通訊協定，使用者才能使用 Kerberos 驗證進行連接。</span><span class="sxs-lookup"><span data-stu-id="470d0-155">In the case of a TCP/IP connection, where the TCP port is included in the SPN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must enable the TCP protocol for a user to connect by using Kerberos authentication.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="470d0-156">MSSQLSvc/*fqdn：埠*</span><span class="sxs-lookup"><span data-stu-id="470d0-156">MSSQLSvc/*fqdn:port*</span></span>|<span data-ttu-id="470d0-157">使用 TCP 時，此為提供者產生的預設 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-157">The provider-generated, default SPN when TCP is used.</span></span> <span data-ttu-id="470d0-158">*port* 是 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="470d0-158">*port* is a TCP port number.</span></span>|  
|<span data-ttu-id="470d0-159">MSSQLSvc/*fqdn*</span><span class="sxs-lookup"><span data-stu-id="470d0-159">MSSQLSvc/*fqdn*</span></span>|<span data-ttu-id="470d0-160">使用 TCP 以外的通訊協定時，此為提供者針對預設執行個體所產生的預設 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-160">The provider-generated, default SPN for a default instance when a protocol other than TCP is used.</span></span> <span data-ttu-id="470d0-161">*fqdn*是完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="470d0-161">*fqdn* is a fully-qualified domain name.</span></span>|  
|<span data-ttu-id="470d0-162">MSSQLSvc/*fqdn： InstanceName*</span><span class="sxs-lookup"><span data-stu-id="470d0-162">MSSQLSvc/*fqdn:InstanceName*</span></span>|<span data-ttu-id="470d0-163">使用 TCP 以外的通訊協定時，此為提供者針對具名執行個體所產生的預設 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-163">The provider-generated, default SPN for a named instance when a protocol other than TCP is used.</span></span> <span data-ttu-id="470d0-164">*InstanceName*是實例的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="470d0-164">*InstanceName* is the name of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
##  <a name="automatic-spn-registration"></a><a name="Auto"></a> <span data-ttu-id="470d0-165">自動 SPN 註冊</span><span class="sxs-lookup"><span data-stu-id="470d0-165">Automatic SPN Registration</span></span>  
 <span data-ttu-id="470d0-166">當 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體啟動時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會嘗試註冊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-166">When an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to register the SPN for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="470d0-167">當此執行個體停止時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會嘗試取消註冊 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-167">When the instance is stopped, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to unregister the SPN.</span></span> <span data-ttu-id="470d0-168">如果是 TCP/IP 連線，SPN 會以 *MSSQLSvc/\<FQDN>* : *\<tcpport>* 格式註冊。具名執行個體和預設執行個體都會註冊為 *MSSQLSvc*，依賴 *\<tcpport>* 值來區分執行個體。</span><span class="sxs-lookup"><span data-stu-id="470d0-168">For a TCP/IP connection the SPN is registered in the format *MSSQLSvc/\<FQDN>*:*\<tcpport>*.Both named instances and the default instance are registered as *MSSQLSvc*, relying on the *\<tcpport>* value to differentiate the instances.</span></span>  
  
 <span data-ttu-id="470d0-169">對於支援 Kerberos 的其他連接，SPN 會以\*MSSQLSvc/ \<FQDN> \*：的格式註冊， *\<instancename>* 以用於已命名的實例。</span><span class="sxs-lookup"><span data-stu-id="470d0-169">For other connections that support Kerberos the SPN is registered in the format *MSSQLSvc/\<FQDN>*:*\<instancename>* for a named instance.</span></span> <span data-ttu-id="470d0-170">用來註冊預設執行個體的格式為 *MSSQLSvc/\<FQDN>* 。</span><span class="sxs-lookup"><span data-stu-id="470d0-170">The format for registering the default instance is *MSSQLSvc/\<FQDN>*.</span></span>  
  
 <span data-ttu-id="470d0-171">如果服務帳戶缺少這些動作所需的權限，可能需要手動介入才能註冊或取消註冊 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-171">Manual intervention might be required to register or unregister the SPN if the service account lacks the permissions that are required for these actions.</span></span>  
  
##  <a name="manual-spn-registration"></a><a name="Manual"></a> <span data-ttu-id="470d0-172">手動 SPN 註冊</span><span class="sxs-lookup"><span data-stu-id="470d0-172">Manual SPN Registration</span></span>  
 <span data-ttu-id="470d0-173">若要手動註冊 SPN，管理員必須使用 Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 支援工具所隨附的 Setspn.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="470d0-173">To register the SPN manually, the administrator must use the Setspn.exe tool that is provided with the Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] Support Tools.</span></span> <span data-ttu-id="470d0-174">如需詳細資訊，請參閱 [Windows Server 2003 Service Pack 1 支援工具](https://support.microsoft.com/kb/892777) KB 文件。</span><span class="sxs-lookup"><span data-stu-id="470d0-174">For more information, see the [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777) KB article.</span></span>  
  
 <span data-ttu-id="470d0-175">Setspn.exe 是一個命令列工具，可讓您讀取、修改及刪除服務主要名稱 (SPN) 目錄屬性。</span><span class="sxs-lookup"><span data-stu-id="470d0-175">Setspn.exe is a command line tool that enables you to read, modify, and delete the Service Principal Names (SPN) directory property.</span></span> <span data-ttu-id="470d0-176">此工具也可讓您檢視目前的 SPN、重設此帳戶的預設 SPN，或是加入或刪除補充 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-176">This tool also enables you to view the current SPNs, reset the account's default SPNs, and add or delete supplemental SPNs.</span></span>  
  
 <span data-ttu-id="470d0-177">下列範例說明用來手動註冊 TCP/IP 連接之 SPN 的語法。</span><span class="sxs-lookup"><span data-stu-id="470d0-177">The following example illustrates the syntax used to register manually register an SPN for a TCP/IP connection.</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:1433 accountname  
```  
  
 <span data-ttu-id="470d0-178">**注意** 如果 SPN 已存在，必須先將它刪除以後才可以重新註冊。</span><span class="sxs-lookup"><span data-stu-id="470d0-178">**Note** If an SPN already exists, it must be deleted before it can be reregistered.</span></span> <span data-ttu-id="470d0-179">您可以搭配 `setspn` 參數使用 `-D` 命令來進行這項處理。</span><span class="sxs-lookup"><span data-stu-id="470d0-179">You do this by using the `setspn` command together with the `-D` switch.</span></span> <span data-ttu-id="470d0-180">下列範例說明如何手動註冊以新執行個體為基礎的 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-180">The following examples illustrate how to manually register a new instance-based SPN.</span></span> <span data-ttu-id="470d0-181">若為預設執行個體，請使用：</span><span class="sxs-lookup"><span data-stu-id="470d0-181">For a default instance, use:</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com accountname  
```  
  
 <span data-ttu-id="470d0-182">若為具名執行個體，請使用：</span><span class="sxs-lookup"><span data-stu-id="470d0-182">For a named instance, use:</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:instancename accountname  
```  
  
##  <a name="client-connections"></a><a name="Client"></a> <span data-ttu-id="470d0-183">用戶端連接</span><span class="sxs-lookup"><span data-stu-id="470d0-183">Client Connections</span></span>  
 <span data-ttu-id="470d0-184">用戶端驅動程式內可支援使用者指定的 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-184">User-specified SPNs are supported in client drivers.</span></span> <span data-ttu-id="470d0-185">但是，如果未提供 SPN，將會根據用戶端連接的類型來自動產生 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-185">However, if an SPN is not provided, it will be generated automatically based on the type of a client connection.</span></span> <span data-ttu-id="470d0-186">如果是 TCP 連接，將會針對具名和預設執行個體使用 *MSSQLSvc*/*FQDN*:[*port*] 格式的 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-186">For a TCP connection, an SPN in the format *MSSQLSvc*/*FQDN*:[*port*] is used for both the named and default instances.</span></span>  
  
 <span data-ttu-id="470d0-187">針對具名管道和共用記憶體連接，會將*MSSQLSvc* / *fqdn*：*instancename*格式的 SPN 用於已命名的實例，而*MSSQLSvc* / *FQDN*則用於預設實例。</span><span class="sxs-lookup"><span data-stu-id="470d0-187">For named pipes and shared memory connections, an SPN in the format *MSSQLSvc*/*FQDN*:*instancename* is used for a named instance and *MSSQLSvc*/*FQDN* is used for the default instance.</span></span>  
  
 <span data-ttu-id="470d0-188">**將服務帳戶當做 SPN 使用**</span><span class="sxs-lookup"><span data-stu-id="470d0-188">**Using a service account as an SPN**</span></span>  
  
 <span data-ttu-id="470d0-189">服務帳戶可以當做 SPN 使用，</span><span class="sxs-lookup"><span data-stu-id="470d0-189">Service accounts can be used as an SPN.</span></span> <span data-ttu-id="470d0-190">它們是透過 Kerberos 驗證的連接屬性所指定，而且會使用以下的格式：</span><span class="sxs-lookup"><span data-stu-id="470d0-190">They are specified through the connection attribute for the Kerberos authentication and take the following formats:</span></span>  
  
-   <span data-ttu-id="470d0-191">**username@domain**或網域使用者帳戶的網域\**\**使用者名稱</span><span class="sxs-lookup"><span data-stu-id="470d0-191">**username@domain** or **domain\username** for a domain user account</span></span>  
  
-   <span data-ttu-id="470d0-192">適用於電腦網域帳戶 (如本機系統或 NETWORK SERVICES) 的 **machine$@domain** 或 **host\FQDN**。</span><span class="sxs-lookup"><span data-stu-id="470d0-192">**machine$@domain** or **host\FQDN** for a computer domain account such as Local System or NETWORK SERVICES.</span></span>  
  
 <span data-ttu-id="470d0-193">若要判斷連接的驗證方法，請執行下列查詢。</span><span class="sxs-lookup"><span data-stu-id="470d0-193">To determine the authentication method of a connection, execute the following query.</span></span>  
  
```sql  
SELECT net_transport, auth_scheme   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
```  
  
##  <a name="authentication-defaults"></a><a name="Defaults"></a> <span data-ttu-id="470d0-194">驗證預設值</span><span class="sxs-lookup"><span data-stu-id="470d0-194">Authentication Defaults</span></span>  
 <span data-ttu-id="470d0-195">下表說明根據 SPN 註冊狀況所使用的驗證預設值。</span><span class="sxs-lookup"><span data-stu-id="470d0-195">The following table describes the authentication defaults that are used based on SPN registration scenarios.</span></span>  
  
|<span data-ttu-id="470d0-196">狀況</span><span class="sxs-lookup"><span data-stu-id="470d0-196">Scenario</span></span>|<span data-ttu-id="470d0-197">驗證方法</span><span class="sxs-lookup"><span data-stu-id="470d0-197">Authentication method</span></span>|  
|--------------|---------------------------|  
|<span data-ttu-id="470d0-198">SPN 會對應到正確的網域帳戶、虛擬帳戶、MSA 或內建帳戶。</span><span class="sxs-lookup"><span data-stu-id="470d0-198">The SPN maps to the correct domain account, virtual account, MSA, or built-in account.</span></span> <span data-ttu-id="470d0-199">例如，Local System 或 NETWORK SERVICE。</span><span class="sxs-lookup"><span data-stu-id="470d0-199">For example, Local System or NETWORK SERVICE.</span></span><br /><br /> <span data-ttu-id="470d0-200">注意：正確表示已註冊之 SPN 對應的帳戶就是執行 SQL Server 服務的帳戶。</span><span class="sxs-lookup"><span data-stu-id="470d0-200">Note: Correct means that the account mapped by the registered SPN is the account that the SQL Server service is running under.</span></span>|<span data-ttu-id="470d0-201">本機連接會使用 NTLM，遠端連接則使用 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="470d0-201">Local connections use NTLM, remote connections use Kerberos.</span></span>|  
|<span data-ttu-id="470d0-202">SPN 是正確的網域帳戶、虛擬帳戶、MSA 或內建帳戶。</span><span class="sxs-lookup"><span data-stu-id="470d0-202">The SPN is the correct domain account, virtual account, MSA, or built-in account.</span></span><br /><br /> <span data-ttu-id="470d0-203">注意：正確表示已註冊之 SPN 對應的帳戶就是執行 SQL Server 服務的帳戶。</span><span class="sxs-lookup"><span data-stu-id="470d0-203">Note: Correct means that the account mapped by the registered SPN is the account that the SQL Server service is running under.</span></span>|<span data-ttu-id="470d0-204">本機連接會使用 NTLM，遠端連接則使用 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="470d0-204">Local connections use NTLM, remote connections use Kerberos.</span></span>|  
|<span data-ttu-id="470d0-205">SPN 對應到不正確的網域帳戶、虛擬帳戶、MSA 或內建帳戶。</span><span class="sxs-lookup"><span data-stu-id="470d0-205">The SPN maps to an incorrect domain account, virtual account, MSA, or built-in account</span></span>|<span data-ttu-id="470d0-206">驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="470d0-206">Authentication fails.</span></span>|  
|<span data-ttu-id="470d0-207">SPN 查閱失敗或是未對應到正確的網域帳戶、虛擬帳戶、MSA 或內建帳戶，或者不是正確的網域帳戶、虛擬帳戶、MSA 或內建帳戶。</span><span class="sxs-lookup"><span data-stu-id="470d0-207">The SPN lookup fails or does not map to a correct domain account, virtual account, MSA, or built-in account, or is not a correct domain account, virtual account, MSA, or built-in account.</span></span>|<span data-ttu-id="470d0-208">本機和遠端連接都會使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="470d0-208">Local and remote connections use NTLM.</span></span>|  
  
##  <a name="comments"></a><a name="Comments"></a> <span data-ttu-id="470d0-209">註解</span><span class="sxs-lookup"><span data-stu-id="470d0-209">Comments</span></span>  
 <span data-ttu-id="470d0-210">專用管理員連接 (DAC) 使用以執行個體名稱為基礎的 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-210">The Dedicated Administrator Connection (DAC) uses an instance name based SPN.</span></span> <span data-ttu-id="470d0-211">如果該 SPN 註冊成功的話，Kerberos 驗證便可搭配 DAC 使用。</span><span class="sxs-lookup"><span data-stu-id="470d0-211">Kerberos authentication can be used with a DAC if that SPN is registered successfully.</span></span> <span data-ttu-id="470d0-212">另外，使用者也可將此帳戶名稱指定為 SPN。</span><span class="sxs-lookup"><span data-stu-id="470d0-212">As an alternative a user can specify the account name as an SPN.</span></span>  
  
 <span data-ttu-id="470d0-213">如果 SPN 註冊在啟動期間失敗，則此失敗會記錄在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中，而啟動會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="470d0-213">If SPN registration fails during startup, this failure is recorded in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, and startup continues.</span></span>  
  
 <span data-ttu-id="470d0-214">如果 SPN 取消註冊在關閉期間失敗，則此失敗會記錄在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中，而關閉作業會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="470d0-214">If SPN de-registration fails during shutdown, this failure is recorded in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, and shutdown continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="470d0-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="470d0-215">See Also</span></span>  
 <span data-ttu-id="470d0-216">[用戶端連接中的服務主要名稱 &#40;SPN&#41; 支援](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) </span><span class="sxs-lookup"><span data-stu-id="470d0-216">[Service Principal Name &#40;SPN&#41; Support in Client Connections](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) </span></span>  
 <span data-ttu-id="470d0-217">[用戶端連接 &#40;OLE DB&#41; 中的服務主體名稱 &#40;SPN&#41;](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="470d0-217">[Service Principal Names &#40;SPNs&#41; in Client Connections &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md) </span></span>  
 <span data-ttu-id="470d0-218">[用戶端連接 &#40;ODBC&#41; 中的服務主體名稱 &#40;SPN&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="470d0-218">[Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) </span></span>  
 <span data-ttu-id="470d0-219">[SQL Server Native Client 功能](../../relational-databases/native-client/features/sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="470d0-219">[SQL Server Native Client Features](../../relational-databases/native-client/features/sql-server-native-client-features.md) </span></span>  
 [<span data-ttu-id="470d0-220">管理 Reporting Services 環境中的 Kerberos 驗證問題</span><span class="sxs-lookup"><span data-stu-id="470d0-220">Manage Kerberos Authentication Issues in a Reporting Services Environment</span></span>](https://technet.microsoft.com/library/ff679930.aspx)  
  
  
