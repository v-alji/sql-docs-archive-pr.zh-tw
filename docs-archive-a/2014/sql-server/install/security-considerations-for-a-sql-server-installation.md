---
title: SQL Server 安裝的安全性考量 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [SQL Server]
- server message blocks [SQL Server]
- disabling protocols
- security [SQL Server], installations
- protocols [SQL Server], disabling
- NetBIOS [SQL Server]
- services [SQL Server], security
- SMB [SQL Server]
- isolating services [SQL Server]
- Setup [SQL Server], security
- low SQL Server installation privileges
- NTFS [SQL Server]
- physical security [SQL Server]
- file system security [SQL Server]
- installing SQL Server, security
ms.assetid: cf96155f-30a8-48b7-8d6b-24ce90dafdc7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed0cd42d51c2b4db96778182c60f1ad3d13a098c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598138"
---
# <a name="security-considerations-for-a-sql-server-installation"></a><span data-ttu-id="13250-102">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="13250-102">Security Considerations for a SQL Server Installation</span></span>
  <span data-ttu-id="13250-103">安全性對於每一個產品和每一項業務都很重要。</span><span class="sxs-lookup"><span data-stu-id="13250-103">Security is important for every product and every business.</span></span> <span data-ttu-id="13250-104">只要遵循簡單的最佳做法，就可以避免許多安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="13250-104">By following simple best practices, you can avoid many security vulnerabilities.</span></span> <span data-ttu-id="13250-105">本主題會討論一些您在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前和安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之後應該考慮的安全性最佳做法。</span><span class="sxs-lookup"><span data-stu-id="13250-105">This topic discusses some security best practices that you should consider both before you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="13250-106">特定功能的參考主題中會包括那些功能的安全性指南。</span><span class="sxs-lookup"><span data-stu-id="13250-106">Security guidance for specific features is included in the reference topics for those features.</span></span>  
  
## <a name="before-installing-ssnoversion"></a><span data-ttu-id="13250-107">安裝之前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13250-107">Before Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="13250-108">設定伺服器環境時，請遵循這些最佳做法：</span><span class="sxs-lookup"><span data-stu-id="13250-108">Follow these best practices when you set up the server environment:</span></span>  
  
-   [<span data-ttu-id="13250-109">加強實體安全性</span><span class="sxs-lookup"><span data-stu-id="13250-109">Enhance physical security</span></span>](#physical_security)  
  
-   [<span data-ttu-id="13250-110">使用防火牆</span><span class="sxs-lookup"><span data-stu-id="13250-110">Use firewalls</span></span>](#firewalls)  
  
-   [<span data-ttu-id="13250-111">隔離服務</span><span class="sxs-lookup"><span data-stu-id="13250-111">Isolate services</span></span>](#isolated_services)  
  
-   [<span data-ttu-id="13250-112">設定安全檔案系統</span><span class="sxs-lookup"><span data-stu-id="13250-112">Configure a secure file system</span></span>](#sa_with_least_privileges)  
  
-   [<span data-ttu-id="13250-113">停用 NetBIOS 和伺服器訊息區塊</span><span class="sxs-lookup"><span data-stu-id="13250-113">Disable NetBIOS and server message block</span></span>](#disabled_protocols)  
  
-   [<span data-ttu-id="13250-114">在網域控制站上安裝 SQL Server</span><span class="sxs-lookup"><span data-stu-id="13250-114">Installing SQL Server on a domain controller</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md#Install_DC)  
  
###  <a name="enhance-physical-security"></a><a name="physical_security"></a> <span data-ttu-id="13250-115">Enhance Physical Security</span><span class="sxs-lookup"><span data-stu-id="13250-115">Enhance Physical Security</span></span>  
 <span data-ttu-id="13250-116">實體和邏輯隔離，構成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性的基礎。</span><span class="sxs-lookup"><span data-stu-id="13250-116">Physical and logical isolation make up the foundation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security.</span></span> <span data-ttu-id="13250-117">若要加強 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝的實體安全性，請執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="13250-117">To enhance the physical security of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, do the following tasks:</span></span>  
  
-   <span data-ttu-id="13250-118">將伺服器放在只有獲得授權的人員能夠存取的地點。</span><span class="sxs-lookup"><span data-stu-id="13250-118">Place the server in a room accessible only to authorized persons.</span></span>  
  
-   <span data-ttu-id="13250-119">將主控資料庫的電腦放在實體保護位置中，最好是有上鎖的電腦機房，裡面有水災偵測和火災偵測或控制系統的監視功能。</span><span class="sxs-lookup"><span data-stu-id="13250-119">Place computers that host a database in a physically protected location, ideally a locked computer room with monitored flood detection and fire detection or suppression systems.</span></span>  
  
-   <span data-ttu-id="13250-120">在公司內部網路的安全區域中安裝資料庫，而且請勿將 SQL Server 直接連接到網際網路。</span><span class="sxs-lookup"><span data-stu-id="13250-120">Install databases in the secure zone of the corporate intranet and do not connect your SQL Servers directly to the Internet.</span></span>  
  
-   <span data-ttu-id="13250-121">定期備份所有資料，並在遠端位置保護備份安全。</span><span class="sxs-lookup"><span data-stu-id="13250-121">Back up all data regularly and secure the backups in an off-site location.</span></span>  
  
###  <a name="use-firewalls"></a><a name="firewalls"></a> <span data-ttu-id="13250-122">Use Firewalls</span><span class="sxs-lookup"><span data-stu-id="13250-122">Use Firewalls</span></span>  
 <span data-ttu-id="13250-123">防火牆對於保護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝的安全非常重要。</span><span class="sxs-lookup"><span data-stu-id="13250-123">Firewalls are important to help secure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="13250-124">如果您遵照這些方針，防火牆將是最有效的：</span><span class="sxs-lookup"><span data-stu-id="13250-124">Firewalls will be most effective if you follow these guidelines:</span></span>  
  
-   <span data-ttu-id="13250-125">將防火牆放在伺服器和網際網路之間。</span><span class="sxs-lookup"><span data-stu-id="13250-125">Put a firewall between the server and the Internet.</span></span> <span data-ttu-id="13250-126">啟用您的防火牆。</span><span class="sxs-lookup"><span data-stu-id="13250-126">Enable your firewall.</span></span> <span data-ttu-id="13250-127">如果防火牆已關閉，請將它開啟。</span><span class="sxs-lookup"><span data-stu-id="13250-127">If your firewall is turned off, turn it on.</span></span> <span data-ttu-id="13250-128">如果防火牆已開啟，請勿將它關閉。</span><span class="sxs-lookup"><span data-stu-id="13250-128">If your firewall is turned on, do not turn it off.</span></span>  
  
-   <span data-ttu-id="13250-129">將網路分割成防火牆所隔開的安全區域。</span><span class="sxs-lookup"><span data-stu-id="13250-129">Divide the network into security zones separated by firewalls.</span></span> <span data-ttu-id="13250-130">封鎖所有傳輸，然後選擇性地只准許必要的傳輸。</span><span class="sxs-lookup"><span data-stu-id="13250-130">Block all traffic, and then selectively admit only what is required.</span></span>  
  
-   <span data-ttu-id="13250-131">在多層環境中，請使用多個防火牆來建立篩選的子網路。</span><span class="sxs-lookup"><span data-stu-id="13250-131">In a multi-tier environment, use multiple firewalls to create screened subnets.</span></span>  
  
-   <span data-ttu-id="13250-132">當您在 Windows 網域內安裝伺服器時，請設定內部防火牆允許 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="13250-132">When you are installing the server inside a Windows domain, configure interior firewalls to allow Windows Authentication.</span></span>  
  
-   <span data-ttu-id="13250-133">如果應用程式使用分散式交易，您可能必須設定防火牆，好讓 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 傳輸可以在個別 MS DTC 執行個體之間流動。</span><span class="sxs-lookup"><span data-stu-id="13250-133">If your application uses distributed transactions, you might have to configure the firewall to allow [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) traffic to flow between separate MS DTC instances.</span></span> <span data-ttu-id="13250-134">您也必須設定防火牆，好讓 MS DTC 與資源管理員 (如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 之間的傳輸可以流動。</span><span class="sxs-lookup"><span data-stu-id="13250-134">You will also have to configure the firewall to allow traffic to flow between the MS DTC and resource managers such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="13250-135">如需預設 Windows 防火牆設定的詳細資訊以及影響 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]之 TCP 通訊埠的描述，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="13250-135">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
###  <a name="isolate-services"></a><a name="isolated_services"></a> <span data-ttu-id="13250-136">Isolate Services</span><span class="sxs-lookup"><span data-stu-id="13250-136">Isolate Services</span></span>  
 <span data-ttu-id="13250-137">隔離服務減少一個遭到破壞的服務被用來破壤其他服務的風險。</span><span class="sxs-lookup"><span data-stu-id="13250-137">Isolating services reduces the risk that one compromised service could be used to compromise others.</span></span> <span data-ttu-id="13250-138">若要隔離服務，請考慮下列方針：</span><span class="sxs-lookup"><span data-stu-id="13250-138">To isolate services, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="13250-139">在個別 Windows 帳戶下執行個別的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="13250-139">Run separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services under separate Windows accounts.</span></span> <span data-ttu-id="13250-140">請盡可能針對每一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務使用低權限的個別 Windows 或本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="13250-140">Whenever possible, use separate, low-rights Windows or Local user accounts for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="13250-141">如需詳細資訊，請參閱 [設定 Windows 服務帳戶與權限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)預覽版本升級問題的解答。</span><span class="sxs-lookup"><span data-stu-id="13250-141">For more information, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
###  <a name="configure-a-secure-file-system"></a><a name="sa_with_least_privileges"></a> <span data-ttu-id="13250-142">Configure a Secure File System</span><span class="sxs-lookup"><span data-stu-id="13250-142">Configure a Secure File System</span></span>  
 <span data-ttu-id="13250-143">使用正確的檔案系統會增加安全性。</span><span class="sxs-lookup"><span data-stu-id="13250-143">Using the correct file system increases security.</span></span> <span data-ttu-id="13250-144">如果是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝，您應該執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="13250-144">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations, you should do the following tasks:</span></span>  
  
-   <span data-ttu-id="13250-145">使用 NTFS 檔案系統 (NTFS)。</span><span class="sxs-lookup"><span data-stu-id="13250-145">Use the NTFS file system (NTFS).</span></span> <span data-ttu-id="13250-146">NTFS 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝的慣用檔案系統，因為它比 FAT 檔案系統更穩定，而且具有更高的可復原性。</span><span class="sxs-lookup"><span data-stu-id="13250-146">NTFS is the preferred file system for installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because it is more stable and recoverable than FAT file systems.</span></span> <span data-ttu-id="13250-147">NTFS 也會啟用一些安全性選項，例如檔案和目錄存取控制清單 (ACL) 及加密檔案系統 (EFS) 檔案加密。</span><span class="sxs-lookup"><span data-stu-id="13250-147">NTFS also enables security options like file and directory access control lists (ACLs) and Encrypting File System (EFS) file encryption.</span></span> <span data-ttu-id="13250-148">在安裝期間， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將會在偵測到 NTFS 時，對登錄機碼和檔案設定適當的 ACL。</span><span class="sxs-lookup"><span data-stu-id="13250-148">During installation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will set appropriate ACLs on registry keys and files if it detects NTFS.</span></span> <span data-ttu-id="13250-149">這些權限不應該變更。</span><span class="sxs-lookup"><span data-stu-id="13250-149">These permissions should not be changed.</span></span> <span data-ttu-id="13250-150">未來的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本可能不支援在含有 FAT 檔案系統的電腦上安裝。</span><span class="sxs-lookup"><span data-stu-id="13250-150">Future releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not support installation on computers with FAT file systems.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13250-151">如果您使用 EFS，資料庫檔案將會在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的帳戶識別下加密。</span><span class="sxs-lookup"><span data-stu-id="13250-151">If you use EFS, database files will be encrypted under the identity of the account running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="13250-152">只有這個帳戶才能夠解密該檔案。</span><span class="sxs-lookup"><span data-stu-id="13250-152">Only this account will be able to decrypt the files.</span></span> <span data-ttu-id="13250-153">如果您必須變更執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的帳戶，您應該先在舊的帳戶下解密檔案，然後在新的帳戶下重新加密檔案。</span><span class="sxs-lookup"><span data-stu-id="13250-153">If you must change the account that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should first decrypt the files under the old account and then re-encrypt them under the new account.</span></span>  
  
-   <span data-ttu-id="13250-154">針對重要資料檔使用獨立磁碟容錯陣列 (RAID)。</span><span class="sxs-lookup"><span data-stu-id="13250-154">Use a redundant array of independent disks (RAID) for critical data files.</span></span>  
  
###  <a name="disable-netbios-and-server-message-block"></a><a name="disabled_protocols"></a> <span data-ttu-id="13250-155">Disable NetBIOS and Server Message Block</span><span class="sxs-lookup"><span data-stu-id="13250-155">Disable NetBIOS and Server Message Block</span></span>  
 <span data-ttu-id="13250-156">周邊網路中的伺服器應該停用所有非必要的通訊協定，包括 NetBIOS 和伺服器訊息區塊 (SMB) 在內。</span><span class="sxs-lookup"><span data-stu-id="13250-156">Servers in the perimeter network should have all unnecessary protocols disabled, including NetBIOS and server message block (SMB).</span></span>  
  
 <span data-ttu-id="13250-157">NetBIOS 使用下列通訊埠：</span><span class="sxs-lookup"><span data-stu-id="13250-157">NetBIOS uses the following ports:</span></span>  
  
-   <span data-ttu-id="13250-158">UDP/137 (NetBIOS 名稱服務)</span><span class="sxs-lookup"><span data-stu-id="13250-158">UDP/137 (NetBIOS name service)</span></span>  
  
-   <span data-ttu-id="13250-159">UDP/138 (NetBIOS 資料包服務)</span><span class="sxs-lookup"><span data-stu-id="13250-159">UDP/138 (NetBIOS datagram service)</span></span>  
  
-   <span data-ttu-id="13250-160">TCP/139 (NetBIOS 工作階段服務)</span><span class="sxs-lookup"><span data-stu-id="13250-160">TCP/139 (NetBIOS session service)</span></span>  
  
 <span data-ttu-id="13250-161">SMB 使用下列通訊埠：</span><span class="sxs-lookup"><span data-stu-id="13250-161">SMB uses the following ports:</span></span>  
  
-   <span data-ttu-id="13250-162">TCP/139</span><span class="sxs-lookup"><span data-stu-id="13250-162">TCP/139</span></span>  
  
-   <span data-ttu-id="13250-163">TCP/445</span><span class="sxs-lookup"><span data-stu-id="13250-163">TCP/445</span></span>  
  
 <span data-ttu-id="13250-164">Web 伺服器和網域名稱系統 (DNS) 伺服器不需要 NetBIOS 或 SMB。</span><span class="sxs-lookup"><span data-stu-id="13250-164">Web servers and Domain Name System (DNS) servers do not require NetBIOS or SMB.</span></span> <span data-ttu-id="13250-165">在這些伺服器上，請停用這兩種通訊協定以減少使用者列舉的威脅。</span><span class="sxs-lookup"><span data-stu-id="13250-165">On these servers, disable both protocols to reduce the threat of user enumeration.</span></span>  
  
###  <a name="installing-ssnoversion-on-a-domain-controller"></a><a name="Install_DC"></a> <span data-ttu-id="13250-166">在網域控制站上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13250-166">Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a domain controller</span></span>  
 <span data-ttu-id="13250-167">基於安全性理由，不建議您在網域控制站上安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="13250-167">For security reasons, we recommend that you do not install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a domain controller.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="13250-168">安裝程式將不會封鎖當做網域控制站之電腦上的安裝，但適用以下限制：</span><span class="sxs-lookup"><span data-stu-id="13250-168">Setup will not block installation on a computer that is a domain controller, but the following limitations apply:</span></span>  
  
-   <span data-ttu-id="13250-169">您無法以本機服務帳戶在網域控制站上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="13250-169">You cannot run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services on a domain controller under a local service account.</span></span>  
  
-   <span data-ttu-id="13250-170">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝到電腦上以後，您無法將電腦從網域成員變成網域控制站。</span><span class="sxs-lookup"><span data-stu-id="13250-170">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, you cannot change the computer from a domain member to a domain controller.</span></span> <span data-ttu-id="13250-171">在您將主機電腦變更為網域控制站之前，必須先解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="13250-171">You must uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you change the host computer to a domain controller.</span></span>  
  
-   <span data-ttu-id="13250-172">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝到電腦上以後，您無法將電腦從網域控制站變成網域成員。</span><span class="sxs-lookup"><span data-stu-id="13250-172">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, you cannot change the computer from a domain controller to a domain member.</span></span> <span data-ttu-id="13250-173">在您將主機電腦變更為網域成員之前，必須先解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="13250-173">You must uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you change the host computer to a domain member.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="13250-174">容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="13250-174">failover cluster instances are not supported where cluster nodes are domain controllers.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="13250-175">安裝程式無法在唯讀的網域控制站上建立安全性群組或提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="13250-175">Setup cannot create security groups or provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts on a read-only domain controller.</span></span> <span data-ttu-id="13250-176">在此狀況中，安裝程式將會失敗。</span><span class="sxs-lookup"><span data-stu-id="13250-176">In this scenario, Setup will fail.</span></span>  
  
## <a name="during-or-after-installation-of-ssnoversion"></a><span data-ttu-id="13250-177">安裝時或安裝後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13250-177">During or After Installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="13250-178">安裝之後，您可以遵照關於帳戶和驗證模式的這些最佳做法，來加強 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝的安全性：</span><span class="sxs-lookup"><span data-stu-id="13250-178">After installation, you can enhance the security of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation by following these best practices regarding accounts and authentication modes:</span></span>  
  
 <span data-ttu-id="13250-179">**服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="13250-179">**Service accounts**</span></span>  
  
-   <span data-ttu-id="13250-180">使用可能的最低權限來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="13250-180">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services by using the lowest possible permissions.</span></span>  
  
-   <span data-ttu-id="13250-181">將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務與低權限的 Windows 本機使用者帳戶或網域使用者帳戶產生關聯。</span><span class="sxs-lookup"><span data-stu-id="13250-181">Associate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services with low privileged Windows local user accounts, or domain user accounts.</span></span>  
  
-   <span data-ttu-id="13250-182">如需詳細資訊，請參閱 [設定 Windows 服務帳戶與權限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)預覽版本升級問題的解答。</span><span class="sxs-lookup"><span data-stu-id="13250-182">For more information, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
 <span data-ttu-id="13250-183">**驗證模式**</span><span class="sxs-lookup"><span data-stu-id="13250-183">**Authentication mode**</span></span>  
  
-   <span data-ttu-id="13250-184">需要 Windows 驗證才能連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="13250-184">Require Windows Authentication for connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="13250-185">使用 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="13250-185">Use Kerberos authentication.</span></span> <span data-ttu-id="13250-186">如需詳細資訊，請參閱 [註冊 Kerberos 連接的服務主體名稱](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="13250-186">For more information, see [Register a Service Principal Name for Kerberos Connections](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).</span></span>  
  
 <span data-ttu-id="13250-187">**增強式密碼**</span><span class="sxs-lookup"><span data-stu-id="13250-187">**Strong passwords**</span></span>  
  
-   <span data-ttu-id="13250-188">一律指派增強式密碼給 `sa` 帳戶。</span><span class="sxs-lookup"><span data-stu-id="13250-188">Always assign a strong password to the `sa` account.</span></span>  
  
-   <span data-ttu-id="13250-189">一律啟用檢查密碼強度和逾期的密碼原則。</span><span class="sxs-lookup"><span data-stu-id="13250-189">Always enable password policy checking for password strength and expiration.</span></span>  
  
-   <span data-ttu-id="13250-190">對所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入一律使用增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="13250-190">Always use strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13250-191">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 安裝期間會在 BUILTIN\Users 群組中加入一個登入。</span><span class="sxs-lookup"><span data-stu-id="13250-191">During setup of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] a login is added for the BUILTIN\Users group.</span></span> <span data-ttu-id="13250-192">這個登入可讓電腦上所有經過驗證的使用者以 public 角色成員的身分存取 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="13250-192">This allows all authenticated users of the computer to access the instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as a member of the public role.</span></span> <span data-ttu-id="13250-193">BUILTIN\Users 登入可以安全地移除，藉此限制擁有個別登入或為其他擁有登入之 Windows 群組成員的電腦使用者對 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的存取。</span><span class="sxs-lookup"><span data-stu-id="13250-193">The BUILTIN\Users login can be safely removed to restrict [!INCLUDE[ssDE](../../includes/ssde-md.md)] access to computer users who have individual logins or are members of other Windows groups with logins.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13250-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13250-194">See Also</span></span>  
 <span data-ttu-id="13250-195">[安裝 SQL Server 2014 的硬體和軟體需求](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="13250-195">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 <span data-ttu-id="13250-196">[網路通訊協定和網路程式庫](../../../2014/sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="13250-196">[Network Protocols and Network Libraries](../../../2014/sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 [<span data-ttu-id="13250-197">註冊 Kerberos 連接的服務主體名稱</span><span class="sxs-lookup"><span data-stu-id="13250-197">Register a Service Principal Name for Kerberos Connections</span></span>](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)  
  
  
