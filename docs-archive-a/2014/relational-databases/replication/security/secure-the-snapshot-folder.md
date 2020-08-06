---
title: 保護快照集資料夾 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], security
ms.assetid: 3cd877d1-ffb8-48fd-a72b-98eb948aad27
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c977936ad2aca6e5a98ee685a15662a00b625494
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598272"
---
# <a name="secure-the-snapshot-folder"></a><span data-ttu-id="2a7b3-102">保護快照集資料夾</span><span class="sxs-lookup"><span data-stu-id="2a7b3-102">Secure the Snapshot Folder</span></span>
  <span data-ttu-id="2a7b3-103">快照集資料夾是儲存快照集檔案的目錄；建議您將此目錄專用於快照集儲存。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-103">The snapshot folder is a directory that stores snapshot files; it is recommended that you dedicate the directory for snapshot storage.</span></span> <span data-ttu-id="2a7b3-104">授與「快照集代理程式」對資料夾的寫入權限，並確定僅授與 Windows 帳戶讀取權限，「合併代理程式」或「散發代理程式」使用該帳戶來存取此資料夾。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-104">Grant the Snapshot Agent write permission to the folder, and ensure that read permission is granted only to the Windows account that the Merge Agent or Distribution agent uses when accessing the folder.</span></span> <span data-ttu-id="2a7b3-105">與代理程式相關聯的 Windows 帳戶必須為網域帳戶，這樣才能存取位於遠端電腦上的快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-105">The Windows account associated with the agent must be a domain account to access a snapshot folder that is located on a remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a7b3-106">使用者帳戶控制 (UAC) 可協助管理員管理其較高的使用者權限 (有時也稱為「權限」) 。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-106">User Account Control (UAC)  helps administrators manage their elevated user rights (sometimes called *privileges*).</span></span> <span data-ttu-id="2a7b3-107">在已啟用 UAC 的作業系統上執行時，管理員不會使用其管理權限。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-107">When running on operating systems that have UAC enabled, administrators do not use their administrative rights.</span></span> <span data-ttu-id="2a7b3-108">反而會以標準 (非管理員) 使用者的身分執行大部分的動作，只有在必要時才會採用其管理權限。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-108">Instead, they perform most actions as standard (non-administrative) users, temporarily assuming their administrative rights only when it is required.</span></span> <span data-ttu-id="2a7b3-109">UAC 可以防止以管理員權限存取快照共用。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-109">UAC can prevent administrative access to the snapshot share.</span></span> <span data-ttu-id="2a7b3-110">因此，您必須針對快照集代理程式、散發代理程式和合併代理程式所使用的 Windows 帳戶，明確地授與快照集共用權限。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-110">You must therefore explicitly grant snapshot share permissions to the Windows accounts that are used by the Snapshot Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="2a7b3-111">即使 Windows 帳戶是管理員群組的成員，也必須這麼做。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-111">You must do this even if the Windows accounts are members of the Administrators group.</span></span>  
  
 <span data-ttu-id="2a7b3-112">透過「設定散發精靈」或「新增發行集精靈」設定「散發者」時，快照集資料夾預設為本機路徑：X:\Program Files\Microsoft SQL Server\\ *\<instance>* \MSSQL\ReplData。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-112">When configuring a Distributor through the Configure Distribution Wizard or the New Publication Wizard, the snapshot folder defaults to a local path: X:\Program Files\Microsoft SQL Server\\*\<instance>* \MSSQL\ReplData.</span></span> <span data-ttu-id="2a7b3-113">如果您使用的是遠端「散發者」或提取訂閱，則必須指定 UNC 網路共用 (例如 \\\\<*電腦名稱>* \snapshot) 而不是本機路徑。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-113">If you are using a remote Distributor or pull subscriptions, you must specify a UNC network share (such as \\\\<*computername>* \snapshot) rather than a local path.</span></span>  
  
 <span data-ttu-id="2a7b3-114">授與快照集資料夾存取權限時，您必須依據存取資料夾的方式授與它們權限。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-114">When granting permissions to access the snapshot folder, you must grant them according to the way in which the folder is accessed.</span></span> <span data-ttu-id="2a7b3-115">下列對話方塊索引標籤用於 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003：</span><span class="sxs-lookup"><span data-stu-id="2a7b3-115">The following dialog box tabs are used in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003:</span></span>  
  
-   <span data-ttu-id="2a7b3-116">如果您指定的是本機路徑，則可透過 **[屬性]** 對話方塊的 **[安全性]** 索引標籤授與對該資料夾的存取權限。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-116">If you specify a local path, grant permissions through the **Security** tab of the **Properties** dialog box for the folder.</span></span>  
  
-   <span data-ttu-id="2a7b3-117">如果您指定的是網路共用，則可透過 **[屬性]** 對話方塊的 **[共用]** 索引標籤授與對該資料夾的存取權限。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-117">If you specify a network share, grant permissions through the **Sharing** tab of the **Properties** dialog box for the folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a7b3-118">如果複寫代理程式在「散發者」上執行，請使用 **[屬性]** 對話方塊的 **[安全性]** 索引標籤，此資料夾才能授與權限給用來執行此代理程式的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-118">If the replication agent runs on the Distributor, use the **Security** tab of the **Properties** dialog box for the folder to grant permissions to the Windows account used to run the agent.</span></span> <span data-ttu-id="2a7b3-119">即使在使用網路共用時，也要進行這項處理。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-119">Do this even when a network share is used.</span></span> <span data-ttu-id="2a7b3-120">當「發行者」和「散發者」位於相同電腦上時，這會套用到發送訂閱的「合併代理程式」和「散發代理程式」及套用到「快照集代理程式」。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-120">This applies to the Merge Agent and Distribution Agent for a push subscription and to the Snapshot Agent when the Publisher and Distributor are on the same computer.</span></span>  
  
 <span data-ttu-id="2a7b3-121">如需設定本機路徑和網路共用權限的詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-121">For more information about setting permissions for local paths and network shares, see the Windows documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a7b3-122">如果卸除發行集，則複寫會嘗試移除 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶之安全性內容下的快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-122">If a publication is dropped, replication attempts to remove the snapshot folder under the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account.</span></span> <span data-ttu-id="2a7b3-123">如果此帳戶沒有足夠的權限，則使用具有足夠權限的帳戶登入並手動移除該資料夾。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-123">If this account does not have sufficient privileges, log in with an account that does have sufficient privileges and remove the folder manually.</span></span> <span data-ttu-id="2a7b3-124">如果資料夾是本機路徑，移除資料夾需要有 **修改** 權限，如果資料夾是網路路徑，則需要有 **完全控制** 權限。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-124">Removing a folder requires the **Modify** privilege if the folder is a local path or the **Full Control** privilege if the folder is a network path.</span></span>  
  
## <a name="delivering-snapshots-through-ftp"></a><span data-ttu-id="2a7b3-125">透過 FTP 傳遞快照集</span><span class="sxs-lookup"><span data-stu-id="2a7b3-125">Delivering Snapshots Through FTP</span></span>  
 <span data-ttu-id="2a7b3-126">建議安全性最佳做法是將快照集儲存在 UNC 共用中，但是快照集也可以先儲存在 FTP 共用中，然後再透過 FTP 傳遞到「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-126">It is recommended as a security best practice that snapshots be stored in a UNC share, but snapshots can be stored in an FTP share and then delivered to a Subscriber through FTP.</span></span> <span data-ttu-id="2a7b3-127">設定 FTP 伺服器時，請確定虛擬目錄公開基礎 UNC 共用，該共用允許發行集之「快照集代理程式」的寫入存取權限。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-127">When configuring the FTP server, ensure that the virtual directory exposes an underlying UNC share that permits write access by the Snapshot Agent for the publication.</span></span>  
  
 <span data-ttu-id="2a7b3-128">若要設定「訂閱者」為透過 FTP 擷取「快照集」，首先要設定具有 FTP 登入與密碼的 FTP 伺服器 (允許「訂閱者」有讀取 (或「取得」) 存取權限)，以允許其下載快照集檔案。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-128">To configure a Subscriber to retrieve the Snapshot via FTP, first set up an FTP server with an FTP login and password that allows Subscribers read (or "get") access to allow the snapshot files to be downloaded.</span></span>  
  
 <span data-ttu-id="2a7b3-129">若要透過 FTP 傳遞快照集，請參閱[透過 FTP 傳遞快照集](../publish/deliver-a-snapshot-through-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-129">To deliver snapshots through FTP, see [Deliver a Snapshot Through FTP](../publish/deliver-a-snapshot-through-ftp.md).</span></span>  
  
 <span data-ttu-id="2a7b3-130">如需有關設定和變更透過 FTP 存取快照集之密碼的詳細資訊，請參閱＜ [Secure the Publisher](secure-the-publisher.md)＞主題中的＜FTP 快照集傳遞＞一節。</span><span class="sxs-lookup"><span data-stu-id="2a7b3-130">For information about setting and changing the password for access to snapshots through FTP, see the section "FTP Snapshot Delivery" in the topic [Secure the Publisher](secure-the-publisher.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7b3-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a7b3-131">See Also</span></span>  
 <span data-ttu-id="2a7b3-132">[替代快照集資料夾位置](../alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="2a7b3-132">[Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="2a7b3-133">[使用快照集初始化訂閱](../initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="2a7b3-133">[Initialize a Subscription with a Snapshot](../initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="2a7b3-134">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="2a7b3-134">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="2a7b3-135">[SQL Server 複寫安全性](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="2a7b3-135">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="2a7b3-136">透過 FTP 傳送快照集</span><span class="sxs-lookup"><span data-stu-id="2a7b3-136">Transfer Snapshots Through FTP</span></span>](../transfer-snapshots-through-ftp.md)  
  
  
