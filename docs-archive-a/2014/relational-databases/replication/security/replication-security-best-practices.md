---
title: 複寫安全性最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], best practices
- security [SQL Server replication], between domains
- authentication [SQL Server replication]
- Internet [SQL Server replication], security
ms.assetid: 1ab2635d-0992-4c99-b17d-041d02ec9a7c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e5918bfed52a6ed1befd81d2fdb7910062060e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584379"
---
# <a name="replication-security-best-practices"></a><span data-ttu-id="4fce6-102">複寫安全性最佳做法</span><span class="sxs-lookup"><span data-stu-id="4fce6-102">Replication Security Best Practices</span></span>
  <span data-ttu-id="4fce6-103">複寫會移動分散式環境中的資料，範圍從單一網域上的企業內部網路，乃至於存取未受信任網域之間以及網際網路上資料的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4fce6-103">Replication moves data in distributed environments ranging from intranets on a single domain to applications that access data between untrusted domains and over the Internet.</span></span> <span data-ttu-id="4fce6-104">因此，了解在這些不同環境下保護複寫連接安全的最佳方法相當重要。</span><span class="sxs-lookup"><span data-stu-id="4fce6-104">It is important to understand the best approach for securing replication connections under these different circumstances.</span></span>  
  
 <span data-ttu-id="4fce6-105">下列資訊與所有環境中的複寫相關：</span><span class="sxs-lookup"><span data-stu-id="4fce6-105">The following information is relevant to replication in all environments:</span></span>  
  
-   <span data-ttu-id="4fce6-106">使用業界標準方法加密複寫拓撲中各電腦之間的連接，例如虛擬私人網路 (Virtual Private Networks，VPN)、安全通訊端層 (Secure Sockets Layer，SSL) 或 IP 安全性 (IPSEC)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-106">Encrypt the connections between computers in a replication topology using an industry standard method, such as Virtual Private Networks (VPN), Secure Sockets Layer (SSL), or IP Security (IPSEC).</span></span> <span data-ttu-id="4fce6-107">如需詳細資訊，請參閱[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-107">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span> <span data-ttu-id="4fce6-108">如需有關透過網際網路使用 VPN 與 SSL 複寫資料的資訊，請參閱＜ [Securing Replication Over the Internet](securing-replication-over-the-internet.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4fce6-108">For information about using VPN and SSL for replicating data over the Internet, see [Securing Replication Over the Internet](securing-replication-over-the-internet.md).</span></span>  
  
     <span data-ttu-id="4fce6-109">如果使用 SSL 保護複寫拓撲中電腦之間的連接，請將每個複寫代理程式的 **-EncryptionLevel** 參數值指定為 **1** 或 **2** (建議使用 **2** 值)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-109">If you use SSL to secure the connections between computers in a replication topology, specify a value of **1** or **2** for the **-EncryptionLevel** parameter of each replication agent (a value of **2** is recommended).</span></span> <span data-ttu-id="4fce6-110">值 **1** 會指定使用加密，但代理程式不會確認 SSL 伺服器憑證是否由受信任簽發者簽署；值 **2** 則會指定對憑證進行確認。</span><span class="sxs-lookup"><span data-stu-id="4fce6-110">A value of **1** specifies that encryption is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer; a value of **2** specifies that the certificate is verified.</span></span> <span data-ttu-id="4fce6-111">可於代理程式設定檔和命令列中指定代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="4fce6-111">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="4fce6-112">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="4fce6-112">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="4fce6-113">處理複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="4fce6-113">Work with Replication Agent Profiles</span></span>](../agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="4fce6-114">檢視並修改複寫代理程式命令提示字元參數 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4fce6-114">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [<span data-ttu-id="4fce6-115">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="4fce6-115">Replication Agent Executables Concepts</span></span>](../concepts/replication-agent-executables-concepts.md)  
  
-   <span data-ttu-id="4fce6-116">以不同的 Windows 帳戶執行各複寫代理程式，並針對所有複寫代理程式連接使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4fce6-116">Run each replication agent under a different Windows account, and use Windows Authentication for all replication agent connections.</span></span> <span data-ttu-id="4fce6-117">如需指定帳戶的詳細資訊，請參閱[管理複寫的登入與密碼](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-117">For more information about specifying accounts, see [Manage Logins and Passwords in Replication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).</span></span>  
  
-   <span data-ttu-id="4fce6-118">僅對各代理程式授與必要的權限。</span><span class="sxs-lookup"><span data-stu-id="4fce6-118">Grant only the required permissions to each agent.</span></span> <span data-ttu-id="4fce6-119">如需詳細資訊，請參閱＜ [Replication Agent Security Model](replication-agent-security-model.md)＞的「代理程式所需的權限」一節。</span><span class="sxs-lookup"><span data-stu-id="4fce6-119">For more information, see the "Permissions Required by Agents" section of [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="4fce6-120">確定發行集存取清單 (PAL) 中包含所有「合併代理程式」及「散發代理程式」。</span><span class="sxs-lookup"><span data-stu-id="4fce6-120">Ensure all Merge Agent and Distribution Agent accounts are in the publication access list (PAL).</span></span> <span data-ttu-id="4fce6-121">如需詳細資訊，請參閱[保護發行者](secure-the-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-121">For more information, see [Secure the Publisher](secure-the-publisher.md).</span></span>  
  
-   <span data-ttu-id="4fce6-122">僅允許 PAL 中的帳戶擁有執行複寫工作所需的權限，以遵守最低權限原則。</span><span class="sxs-lookup"><span data-stu-id="4fce6-122">Follow the principle of least privilege by allowing accounts in the PAL only the permissions they need to perform replication tasks.</span></span> <span data-ttu-id="4fce6-123">切勿將登入加入至複寫不需要的任何固定伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="4fce6-123">Do not add the logins to any fixed server roles that are not required for replication.</span></span>  
  
-   <span data-ttu-id="4fce6-124">設定快照集共用，以允許所有「合併代理程式」和「散發代理程式」擁有讀取權限。</span><span class="sxs-lookup"><span data-stu-id="4fce6-124">Configure the snapshot share to allow read access by all Merge Agents and Distribution Agents.</span></span> <span data-ttu-id="4fce6-125">在發行集的快照集擁有參數化篩選的情況下，務必確認各資料夾已設定為僅允許存取適當的「合併代理程式」帳戶。</span><span class="sxs-lookup"><span data-stu-id="4fce6-125">In the case of snapshots for publications with parameterized filters, ensure that each folder is configured to allow access only to the appropriate Merge Agent accounts.</span></span>  
  
-   <span data-ttu-id="4fce6-126">設定快照集共用，以允許「快照集代理程式」擁有寫入權限。</span><span class="sxs-lookup"><span data-stu-id="4fce6-126">Configure the snapshot share to allow write access by the Snapshot Agent.</span></span>  
  
-   <span data-ttu-id="4fce6-127">如果您使用提取訂閱，請使用網路共用，而非使用快照集資料夾的本機路徑。</span><span class="sxs-lookup"><span data-stu-id="4fce6-127">If you use pull subscriptions, use a network share rather than a local path for the snapshot folder.</span></span>  
  
 <span data-ttu-id="4fce6-128">如果您的複寫拓撲包含不是位於相同網域中的電腦，或包含位於彼此之間沒有信任關係之網域中的電腦，可針對代理程式建立的連接使用 Windows 驗證或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證 (如需網域的詳細資訊，請參閱 Windows 說明文件)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-128">If your replication topology includes computers that are not in the same domain or are in domains that do not have trust relationships with each other, you can use Windows Authentication or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication for the connections made by agents (For more information about domains, see the Windows documentation).</span></span> <span data-ttu-id="4fce6-129">基於安全性最佳做法，建議您使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4fce6-129">It is recommended as a security best practice that you use Windows Authentication.</span></span>  
  
-   <span data-ttu-id="4fce6-130">使用 Windows 驗證：</span><span class="sxs-lookup"><span data-stu-id="4fce6-130">To use Windows Authentication:</span></span>  
  
    -   <span data-ttu-id="4fce6-131">在適當的節點 (在各節點使用相同名稱和密碼) 為各代理程式加入本機 Windows 帳戶 (並非網域帳戶)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-131">Add a local Windows account (not a domain account) for each agent at the appropriate nodes (use the same name and password at each node).</span></span> <span data-ttu-id="4fce6-132">例如，發送訂閱的散發代理程式在散發者端執行，並且建立至散發者與訂閱者的連接。</span><span class="sxs-lookup"><span data-stu-id="4fce6-132">For example, the Distribution Agent for a push subscription runs at the Distributor and makes connections to the Distributor and Subscriber.</span></span> <span data-ttu-id="4fce6-133">「散發代理程式」的 Windows 帳戶應加入至「散發者」和「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="4fce6-133">The Windows account for the Distribution Agent should be added to the Distributor and Subscriber.</span></span>  
  
    -   <span data-ttu-id="4fce6-134">確認指定的代理程式 (例如，訂閱的「散發代理程式」) 會在每部電腦上以相同的帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="4fce6-134">Ensure that a given agent (for example the Distribution Agent for a subscription) runs under the same account at each computer.</span></span>  
  
-   <span data-ttu-id="4fce6-135">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證：</span><span class="sxs-lookup"><span data-stu-id="4fce6-135">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication:</span></span>  
  
    -   <span data-ttu-id="4fce6-136">在適當的節點 (在各節點使用相同帳戶名稱和密碼) 為各代理程式加入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4fce6-136">Add a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account for each agent at the appropriate nodes (use the same account name and password at each node).</span></span> <span data-ttu-id="4fce6-137">例如，發送訂閱的散發代理程式在散發者端執行，並且建立至散發者與訂閱者的連接。</span><span class="sxs-lookup"><span data-stu-id="4fce6-137">For example, the Distribution Agent for a push subscription runs at the Distributor and makes connections to the Distributor and Subscriber.</span></span> <span data-ttu-id="4fce6-138">「散發代理程式」的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帳戶應加入至「散發者」和「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="4fce6-138">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account for the Distribution Agent should be added to the Distributor and Subscriber.</span></span>  
  
    -   <span data-ttu-id="4fce6-139">確認指定的代理程式 (例如，訂閱的「散發代理程式」) 會在每部電腦上以相同的帳戶建立連接。</span><span class="sxs-lookup"><span data-stu-id="4fce6-139">Ensure that a given agent (for example the Distribution Agent for a subscription) makes connections under the same account at each computer.</span></span>  
  
    -   <span data-ttu-id="4fce6-140">在需要 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證的情況下，通常無法存取 UNC 快照集共用 (例如，存取可能遭到防火牆封鎖)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-140">In situations that require [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, access to UNC snapshot shares is often not available (for example access might be blocked by a firewall).</span></span> <span data-ttu-id="4fce6-141">在這種情況下，您可以透過檔案傳輸通訊協定 (FTP) 將快照集傳送至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="4fce6-141">In this case, you can transfer the snapshot to Subscribers through file transfer protocol (FTP).</span></span> <span data-ttu-id="4fce6-142">如需詳細資訊，請參閱[透過 FTP 傳送快照集](../transfer-snapshots-through-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="4fce6-142">For more information, see [Transfer Snapshots Through FTP](../transfer-snapshots-through-ftp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fce6-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fce6-143">See Also</span></span>  
 <span data-ttu-id="4fce6-144">[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="4fce6-144">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="4fce6-145">[透過網際網路的複寫](../replication-over-the-internet.md) </span><span class="sxs-lookup"><span data-stu-id="4fce6-145">[Replication over the Internet](../replication-over-the-internet.md) </span></span>  
 <span data-ttu-id="4fce6-146">[保護訂閱者](secure-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="4fce6-146">[Secure the Subscriber](secure-the-subscriber.md) </span></span>  
 <span data-ttu-id="4fce6-147">[保護散發者](secure-the-distributor.md) </span><span class="sxs-lookup"><span data-stu-id="4fce6-147">[Secure the Distributor](secure-the-distributor.md) </span></span>  
 <span data-ttu-id="4fce6-148">[保護發行者](secure-the-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="4fce6-148">[Secure the Publisher](secure-the-publisher.md) </span></span>  
 [<span data-ttu-id="4fce6-149">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="4fce6-149">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
