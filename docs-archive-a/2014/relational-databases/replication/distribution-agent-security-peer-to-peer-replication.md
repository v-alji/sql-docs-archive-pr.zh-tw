---
title: 散發代理程式安全性 (點對點複寫) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72b5a52fbb3ddc11d0ea6f2c0b26786463e08eaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585871"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a><span data-ttu-id="e8858-102">散發代理程式安全性 (點對點複寫)</span><span class="sxs-lookup"><span data-stu-id="e8858-102">Distribution Agent Security (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="e8858-103">**[散發代理程式安全性]** 頁面，可以讓您指定執行散發代理程式的帳戶，並以點對點拓墣的方式連接到電腦。</span><span class="sxs-lookup"><span data-stu-id="e8858-103">The **Distribution Agent Security** page allows you to specify the accounts under which the Distribution Agent runs and makes connections to the computers in a peer-to-peer topology.</span></span> <span data-ttu-id="e8858-104">如需代理程式所需權限和複寫安全性最佳做法的資訊，請參閱[複寫代理程式安全性模型](security/replication-agent-security-model.md)和[複寫安全性最佳做法](security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="e8858-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8858-105">如果在上一回執行此精靈時，已為訂閱設定散發代理程式，您就無法變更其在此精靈中使用的認證。</span><span class="sxs-lookup"><span data-stu-id="e8858-105">If the Distribution Agent for a subscription has already been configured in a previous run of this wizard, you cannot change the credentials it uses in this wizard.</span></span> <span data-ttu-id="e8858-106">如果您指定新認證，將會忽略這些認證。</span><span class="sxs-lookup"><span data-stu-id="e8858-106">If you specify new credentials, they are ignored.</span></span> <span data-ttu-id="e8858-107">若要變更認證，請使用 **[訂閱屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e8858-107">To change credentials, use the **Subscription Properties** dialog box.</span></span> <span data-ttu-id="e8858-108">如需詳細資訊，請參閱 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e8858-108">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e8858-109">選項。</span><span class="sxs-lookup"><span data-stu-id="e8858-109">Options</span></span>  
 <span data-ttu-id="e8858-110">按一下每個訂閱者之資料列中的屬性按鈕 ( **...** )，即可存取 **[散發代理程式安全性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e8858-110">Click the properties button (**...**) in the row for each Subscriber to access the **Distribution Agent Security** dialog box.</span></span> <span data-ttu-id="e8858-111">如需有關代理程式使用之帳戶所需權限的詳細資訊，請按一下 **[散發代理程式安全性]** 對話方塊上的 **[說明]** 。</span><span class="sxs-lookup"><span data-stu-id="e8858-111">Click **Help** on the **Distribution Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="e8858-112">在其中的一個對話方塊中輸入設定之後，訂閱者的連接資訊就會在方格中顯示。</span><span class="sxs-lookup"><span data-stu-id="e8858-112">After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="e8858-113">**訂閱者的代理程式**</span><span class="sxs-lookup"><span data-stu-id="e8858-113">**Agent for Subscriber**</span></span>  
 <span data-ttu-id="e8858-114">每個對等 (Peer) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8858-114">The name of each peer.</span></span>  
  
 <span data-ttu-id="e8858-115">**對等 (Peer) 資料庫**</span><span class="sxs-lookup"><span data-stu-id="e8858-115">**Peer Database**</span></span>  
 <span data-ttu-id="e8858-116">對等 (Peer) 端的資料庫，會同時作為發行集資料庫與訂閱資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8858-116">The database at the peer that will serve as both a publication database and subscription database.</span></span>  
  
 <span data-ttu-id="e8858-117">**散發者的連接**</span><span class="sxs-lookup"><span data-stu-id="e8858-117">**Connection to Distributor**</span></span>  
 <span data-ttu-id="e8858-118">用於連接到散發者的內容。</span><span class="sxs-lookup"><span data-stu-id="e8858-118">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="e8858-119">本機連接一律會使用執行代理程式之 Windows 帳戶的內容來進行。</span><span class="sxs-lookup"><span data-stu-id="e8858-119">Local connections are always made using the context of the Windows account under which the agent runs.</span></span> <span data-ttu-id="e8858-120">此精靈會建立發送訂閱 (本機連線會連線到散發者)，所以此欄位一律會顯示：[模擬 '\<Domain>\\<登入\>'] 或 [模擬 '\<Computer>\\<登入\>']。</span><span class="sxs-lookup"><span data-stu-id="e8858-120">This wizard creates push subscriptions (the local connection is the connection to the Distributor), so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span>  
  
 <span data-ttu-id="e8858-121">**訂閱者的連接**</span><span class="sxs-lookup"><span data-stu-id="e8858-121">**Connection to Subscriber**</span></span>  
 <span data-ttu-id="e8858-122">與訂閱者進行連接的內容。</span><span class="sxs-lookup"><span data-stu-id="e8858-122">The context under which the connection to the Subscriber is made.</span></span> <span data-ttu-id="e8858-123">連接可以使用執行代理程式之 Windows 帳戶的內容，或使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的內容來進行。</span><span class="sxs-lookup"><span data-stu-id="e8858-123">The connection can be made using the context of the Windows account under which the agent runs or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="e8858-124">這個欄位會顯示下列其中一項資訊：[使用登入 '\<Login>']、[模擬 ' **\<Domain>\\<登入\>']** ，或 [模擬 '\<Computer>\\<登入\>']。</span><span class="sxs-lookup"><span data-stu-id="e8858-124">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="e8858-125">建議使用 Windows 帳戶的內容進行所有連接。</span><span class="sxs-lookup"><span data-stu-id="e8858-125">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8858-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8858-126">See Also</span></span>  
 <span data-ttu-id="e8858-127">[管理點對點拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="e8858-127">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="e8858-128">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="e8858-128">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
