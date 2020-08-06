---
title: 記錄讀取器代理程式安全性 (點對點複寫) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dfef98adb622f9da922af0c1cdbb1cf8b7a07da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598294"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a><span data-ttu-id="e47a9-102">記錄讀取器代理程式安全性 (點對點複寫)</span><span class="sxs-lookup"><span data-stu-id="e47a9-102">Log Reader Agent Security (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="e47a9-103">**[記錄讀取器代理程式安全性]** 頁面，可讓您指定記錄讀取器代理程式在每個對等 (Peer) 端執行和連接的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e47a9-103">The **Log Reader Agent Security** page allows you to specify the accounts under which the Log Reader Agent at each peer runs and makes connections.</span></span> <span data-ttu-id="e47a9-104">如需代理程式所需權限和複寫安全性最佳做法的資訊，請參閱[複寫代理程式安全性模型](security/replication-agent-security-model.md)和[複寫安全性最佳做法](security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="e47a9-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e47a9-105">每一個使用異動複寫發行的資料庫都有一個記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="e47a9-105">There is one Log Reader Agent for each database that is published using transactional replication.</span></span> <span data-ttu-id="e47a9-106">如果資料庫的記錄讀取器代理程式已經完成設定 (此精靈前一次執行中的發行集，或相同資料庫中的其他交易式發行集)，則無法變更它在此精靈中使用的認證。</span><span class="sxs-lookup"><span data-stu-id="e47a9-106">If the Log Reader Agent for a database has already been configured (either for a publication in a previous run of this wizard or for another transactional publication in the same database), you cannot change the credentials it uses in this wizard.</span></span> <span data-ttu-id="e47a9-107">如果您指定新認證，將會忽略這些認證。</span><span class="sxs-lookup"><span data-stu-id="e47a9-107">If you specify new credentials, they are ignored.</span></span> <span data-ttu-id="e47a9-108">若要變更認證，請使用 **[發行集屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e47a9-108">To change credentials, use the **Publication Properties** dialog box.</span></span> <span data-ttu-id="e47a9-109">如需詳細資訊，請參閱 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e47a9-109">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e47a9-110">選項。</span><span class="sxs-lookup"><span data-stu-id="e47a9-110">Options</span></span>  
 <span data-ttu-id="e47a9-111">在每個對等 (Peer) 的資料列中按一下屬性按鈕 ( **...** )，即可存取 **[記錄讀取器代理程式安全性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e47a9-111">Click the properties button (**...**) in the row for each peer to access the **Log Reader Agent Security** dialog box.</span></span> <span data-ttu-id="e47a9-112">在啟動的 **[記錄讀取器代理程式安全性]** 對話方塊上按一下 **[說明]** ，以取得代理程式使用的帳戶所需之權限的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e47a9-112">Click **Help** on the **Log Reader Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="e47a9-113">在對話方塊中輸入設定之後，訂閱者的連接資訊會在方格中顯示。</span><span class="sxs-lookup"><span data-stu-id="e47a9-113">After settings have been entered in the dialog box, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="e47a9-114">**發行者的代理程式**</span><span class="sxs-lookup"><span data-stu-id="e47a9-114">**Agents for Publisher**</span></span>  
 <span data-ttu-id="e47a9-115">每個對等 (Peer) 伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="e47a9-115">The name of each peer server instance.</span></span>  
  
 <span data-ttu-id="e47a9-116">**對等 (Peer) 資料庫**</span><span class="sxs-lookup"><span data-stu-id="e47a9-116">**Peer Database**</span></span>  
 <span data-ttu-id="e47a9-117">在每個對等 (Peer) 端作為發行集資料庫和訂閱資料庫的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e47a9-117">The database that serves as the publication database and subscription database at each peer.</span></span>  
  
 <span data-ttu-id="e47a9-118">**散發者的連接**</span><span class="sxs-lookup"><span data-stu-id="e47a9-118">**Connection to Distributor**</span></span>  
 <span data-ttu-id="e47a9-119">用於連接到散發者的內容。</span><span class="sxs-lookup"><span data-stu-id="e47a9-119">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="e47a9-120">散發者的本機連接一律會使用代理程式所執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶的內容進行，所以這個欄位將一律顯示 [模擬 '\<Domain>\\<登入\>']，或 [模擬 '\<Computer>\\<登入\>']。</span><span class="sxs-lookup"><span data-stu-id="e47a9-120">The local connection to the Distributor is always made using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs, so this field will always display **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span>  
  
 <span data-ttu-id="e47a9-121">**發行者的連接**</span><span class="sxs-lookup"><span data-stu-id="e47a9-121">**Connection to Publisher**</span></span>  
 <span data-ttu-id="e47a9-122">用於連接到發行者的內容。</span><span class="sxs-lookup"><span data-stu-id="e47a9-122">The context under which the connection to the Publisher is made.</span></span> <span data-ttu-id="e47a9-123">發行者的連接可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，或使用執行代理程式之 Windows 帳戶的內容進行。</span><span class="sxs-lookup"><span data-stu-id="e47a9-123">The connection to the Publisher can be made using a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login or using the context of the Windows account under which the agent runs.</span></span> <span data-ttu-id="e47a9-124">這個欄位會顯示下列其中一項資訊：[使用登入 '\<Login>']、[模擬 '\<Domain>\\<登入\>']，或 [模擬 '\<Computer>\\<登入\>']。</span><span class="sxs-lookup"><span data-stu-id="e47a9-124">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="e47a9-125">建議使用 Windows 帳戶的內容進行所有連接。</span><span class="sxs-lookup"><span data-stu-id="e47a9-125">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e47a9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e47a9-126">See Also</span></span>  
 <span data-ttu-id="e47a9-127">[管理點對點拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="e47a9-127">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="e47a9-128">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="e47a9-128">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
