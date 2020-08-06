---
title: 保護發行者 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- Publishers [SQL Server replication], security
- publications [SQL Server replication], security
ms.assetid: 4513a18d-dd6e-407a-b009-49dc9432ec7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dca3f704c43a97c2c34921007341b9bd613676ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598275"
---
# <a name="secure-the-publisher"></a><span data-ttu-id="460f9-102">保護發行者</span><span class="sxs-lookup"><span data-stu-id="460f9-102">Secure the Publisher</span></span>
  <span data-ttu-id="460f9-103">下列複寫代理程式連接到發行者：</span><span class="sxs-lookup"><span data-stu-id="460f9-103">The following replication agents connect to the Publisher:</span></span>  
  
-   <span data-ttu-id="460f9-104">記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="460f9-104">Log Reader Agent</span></span>  
  
-   <span data-ttu-id="460f9-105">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="460f9-105">Snapshot Agent</span></span>  
  
-   <span data-ttu-id="460f9-106">佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="460f9-106">Queue Reader Agent</span></span>  
  
-   <span data-ttu-id="460f9-107">合併代理程式</span><span class="sxs-lookup"><span data-stu-id="460f9-107">Merge Agent</span></span>  
  
 <span data-ttu-id="460f9-108">我們建議您為這些代理程式提供適當的登入，遵循授與所需最小權限的原則，並保護所有密碼的儲存。</span><span class="sxs-lookup"><span data-stu-id="460f9-108">We recommend that you provide an appropriate login for these agents, follow the principle of granting the minimal rights that are required, and protect the storage of all passwords.</span></span> <span data-ttu-id="460f9-109">如需有關各代理程式需要的權限資訊，請參閱＜ [Replication Agent Security Model](replication-agent-security-model.md)＞。</span><span class="sxs-lookup"><span data-stu-id="460f9-109">For information about the permissions that are required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="460f9-110">除了適當地管理登入和密碼以外，您還必須了解發行集存取清單 (PAL) 的角色。</span><span class="sxs-lookup"><span data-stu-id="460f9-110">Besides appropriately managing logins and passwords, you should understand the role of the publication access list (PAL).</span></span> <span data-ttu-id="460f9-111">PAL 是用來啟用登入以存取發行集資料，並同時限制在發行者端進行的資料庫特定存取。</span><span class="sxs-lookup"><span data-stu-id="460f9-111">The PAL is used to enable logins to access to publication data while restricting ad hoc access to the database at the Publisher.</span></span>  
  
## <a name="publication-access-list"></a><span data-ttu-id="460f9-112">發行集存取清單</span><span class="sxs-lookup"><span data-stu-id="460f9-112">Publication Access List</span></span>  
 <span data-ttu-id="460f9-113">PAL 是在發行者端保護發行集安全的主要機制。</span><span class="sxs-lookup"><span data-stu-id="460f9-113">The PAL is the primary mechanism for securing publications at the Publisher.</span></span> <span data-ttu-id="460f9-114">PAL 功能類似於 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 存取控制清單。</span><span class="sxs-lookup"><span data-stu-id="460f9-114">The PAL functions similarly to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows access control list.</span></span> <span data-ttu-id="460f9-115">建立發行集之後，複寫便會建立此發行集的 PAL。</span><span class="sxs-lookup"><span data-stu-id="460f9-115">When you create a publication, replication creates a PAL for the publication.</span></span> <span data-ttu-id="460f9-116">PAL 可進行設定，使其包含已授與了對發行集存取權的登入與群組清單。</span><span class="sxs-lookup"><span data-stu-id="460f9-116">The PAL can be configured to contain a list of logins and groups that are granted access to the publication.</span></span> <span data-ttu-id="460f9-117">當代理程式連接到「發行者」或「散發者」並要求存取發行集時，便會將 PAL 上的驗證資訊與代理程式提供的「發行者」登入進行比較。</span><span class="sxs-lookup"><span data-stu-id="460f9-117">When an agent connects to the Publisher or Distributor and requests access to a publication, the authentication information in the PAL is compared to the Publisher login that the agent provides.</span></span> <span data-ttu-id="460f9-118">這項處理序藉由防止用戶端工具使用「發行者」與「散發者」登入在「發行者」上直接進行修改，為「發行者」提供了額外的安全性。</span><span class="sxs-lookup"><span data-stu-id="460f9-118">This process provides additional security for the Publisher by preventing the Publisher and Distributor login from being used by a client tool to perform modifications on the Publisher directly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="460f9-119">複寫會在「發行者」上為每個發行集建立角色，以強制賦予 PAL 成員資格。</span><span class="sxs-lookup"><span data-stu-id="460f9-119">Replication creates a role on the Publisher for each publication to enforce PAL membership.</span></span> <span data-ttu-id="460f9-120">該角色的名稱格式為 **Msmerge_** _\<PublicationID>_ (合併式複寫) 及 **MSReplPAL_** _\<PublicationDatabaseID>_ **_** _\<PublicationID>_ (異動複寫和快照式複寫)。</span><span class="sxs-lookup"><span data-stu-id="460f9-120">The role has a name in the form **Msmerge_**_\<PublicationID>_ for merge replication and **MSReplPAL_**_\<PublicationDatabaseID>_**_**_\<PublicationID>_ for transactional and snapshot replication.</span></span>  
  
 <span data-ttu-id="460f9-121">根據預設，下列登入包含在 PAL 內：建立發行集時的 **sysadmin** (系統管理員) 固定伺服器角色成員，以及用來建立發行集的登入。</span><span class="sxs-lookup"><span data-stu-id="460f9-121">By default, the following logins are included in the PAL: the members of the **sysadmin** fixed server role at the time the publication is created and the login that is used to create the publication.</span></span> <span data-ttu-id="460f9-122">依預設，對於發行集資料庫上所有 **系統管理員 (sysadmin)** 固定伺服器角色或 **db_owner** 固定資料庫角色的成員，其登入均可訂閱發行集而不需將其明確加入 PAL 中。</span><span class="sxs-lookup"><span data-stu-id="460f9-122">By default, all logins that are members of the **sysadmin** fixed server role or the **db_owner** fixed database role on the publication database can subscribe to a publication without being explicitly added to the PAL.</span></span>  
  
 <span data-ttu-id="460f9-123">使用 PAL 時，請考慮下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="460f9-123">When you are using the PAL, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="460f9-124">您必須先將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入關聯到發行集資料庫中的資料庫使用者，才能夠將該登入加入 PAL 中。</span><span class="sxs-lookup"><span data-stu-id="460f9-124">You must associate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login with a database user in the publication database before adding the login to the PAL.</span></span>  
  
-   <span data-ttu-id="460f9-125">遵循最小權限原則，僅授與 PAL 中登入執行複寫工作所需的權限。</span><span class="sxs-lookup"><span data-stu-id="460f9-125">Follow the principle of least privilege by allowing logins in the PAL only the permissions the logins must have to perform replication tasks.</span></span> <span data-ttu-id="460f9-126">請勿將登入加入任何不要求複寫的固定資料庫角色或伺服器角色中。</span><span class="sxs-lookup"><span data-stu-id="460f9-126">Do not add the logins to any fixed database roles or server roles that are not required for replication.</span></span> <span data-ttu-id="460f9-127">如需有關所需權限的詳細資訊，請參閱＜ [Replication Agent Security Model](replication-agent-security-model.md) ＞和＜ [Replication Security Best Practices](replication-security-best-practices.md)＞。</span><span class="sxs-lookup"><span data-stu-id="460f9-127">For more information about the permissions that are required, see [Replication Agent Security Model](replication-agent-security-model.md) and [Replication Security Best Practices](replication-security-best-practices.md).</span></span>  
  
-   <span data-ttu-id="460f9-128">如果使用遠端散發者，則 PAL 中的帳戶在發行者和散發者兩端都必須是可以使用的。</span><span class="sxs-lookup"><span data-stu-id="460f9-128">If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor.</span></span> <span data-ttu-id="460f9-129">該帳戶必須是在兩部伺服器都已定義的網域帳戶或本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="460f9-129">The account must be either a domain account or a local account that is defined at both servers.</span></span> <span data-ttu-id="460f9-130">與兩個登入相關聯的密碼必須是一樣的。</span><span class="sxs-lookup"><span data-stu-id="460f9-130">The passwords associated with both logins must be the same.</span></span>  
  
-   <span data-ttu-id="460f9-131">如果 PAL 包含 Windows 帳戶且網域使用 Active Directory，則執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的帳戶必須擁有從 Active Directory 進行讀取的權限。</span><span class="sxs-lookup"><span data-stu-id="460f9-131">If the PAL contains Windows accounts and the domain uses Active Directory, the account under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs must have permissions to read from Active Directory.</span></span> <span data-ttu-id="460f9-132">如果您遇到 Windows 帳戶問題，請確定執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的帳戶擁有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="460f9-132">If you experience issues with Windows accounts, make sure that the account under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs has sufficient permissions.</span></span> <span data-ttu-id="460f9-133">如需詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="460f9-133">For more information, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="460f9-134">若要管理 PAL，請參閱[管理發行集存取清單中的登入](manage-logins-in-the-publication-access-list.md)。</span><span class="sxs-lookup"><span data-stu-id="460f9-134">To manage the PAL, see [Manage Logins in the Publication Access List](manage-logins-in-the-publication-access-list.md).</span></span>  
  
## <a name="snapshot-agent"></a><span data-ttu-id="460f9-135">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="460f9-135">Snapshot Agent</span></span>  
 <span data-ttu-id="460f9-136">每個發行集都有一個「快照集代理程式」。</span><span class="sxs-lookup"><span data-stu-id="460f9-136">There is one Snapshot Agent for each publication.</span></span> <span data-ttu-id="460f9-137">如需詳細資訊，請參閱[建立發行集](../publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="460f9-137">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
## <a name="ftp-snapshot-delivery"></a><span data-ttu-id="460f9-138">FTP 快照集傳遞</span><span class="sxs-lookup"><span data-stu-id="460f9-138">FTP Snapshot Delivery</span></span>  
 <span data-ttu-id="460f9-139">如果您將快照集指定為應該透過 FTP 共用而不是 UNC 共用來使用，則在設定 FTP 存取時必須指定登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="460f9-139">If you specify that snapshots should be made available through an FTP share rather than a UNC share, you must specify a login and password when configuring FTP access.</span></span> <span data-ttu-id="460f9-140">如需詳細資訊，請參閱[透過 FTP 傳遞快照集](../publish/deliver-a-snapshot-through-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="460f9-140">For more information, see [Deliver a Snapshot Through FTP](../publish/deliver-a-snapshot-through-ftp.md).</span></span>  
  
## <a name="log-reader-agent"></a><span data-ttu-id="460f9-141">記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="460f9-141">Log Reader Agent</span></span>  
 <span data-ttu-id="460f9-142">每個為異動複寫發行的資料庫，都會有一個記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="460f9-142">There is one Log Reader Agent for each database published for transactional replication.</span></span> <span data-ttu-id="460f9-143">如需詳細資訊，請參閱[建立發行集](../publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="460f9-143">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
## <a name="queue-reader-agent"></a><span data-ttu-id="460f9-144">佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="460f9-144">Queue Reader Agent</span></span>  
 <span data-ttu-id="460f9-145">所有與給定「散發者」相關聯的「發行者」和發行集 (允許佇列更新訂閱) 都有一個「佇列讀取器代理程式」。</span><span class="sxs-lookup"><span data-stu-id="460f9-145">There is one Queue Reader Agent for all Publishers and publications (that allow queued updating subscriptions) associated with a given Distributor.</span></span> <span data-ttu-id="460f9-146">如需詳細資訊，請參閱[啟用交易式發行集的更新訂閱](../publish/enable-updating-subscriptions-for-transactional-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="460f9-146">For more information, see [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="460f9-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="460f9-147">See Also</span></span>  
 <span data-ttu-id="460f9-148">[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="460f9-148">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="460f9-149">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="460f9-149">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="460f9-150">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="460f9-150">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
