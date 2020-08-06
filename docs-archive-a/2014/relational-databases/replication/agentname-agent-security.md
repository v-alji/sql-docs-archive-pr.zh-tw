---
title: '&lt;代理程式名稱&gt; 代理程式安全性 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc72d4380b4d1980da30b8445596e1919a859e31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606800"
---
# <a name="ltagentnamegt-agent-security"></a><span data-ttu-id="ee705-102">&lt;AgentName&gt; 代理程式安全性</span><span class="sxs-lookup"><span data-stu-id="ee705-102">&lt;AgentName&gt; Agent Security</span></span>
  <span data-ttu-id="ee705-103">[\<AgentName> 代理程式安全性] 頁面，可供指定散發代理程式 (適用於異動與快照式複寫) 或合併代理程式 (適用於合併式複寫) 用來執行並連線到複寫拓撲中電腦的帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee705-103">The **\<AgentName> Agent Security** page allows you to specify the accounts under which the Distribution Agent (for transactional and snapshot replication) or Merge Agent (for merge replication) run and make connections to the computers in a replication topology.</span></span> <span data-ttu-id="ee705-104">如需代理程式所需權限和複寫安全性最佳做法的資訊，請參閱[複寫代理程式安全性模型](security/replication-agent-security-model.md)和[複寫安全性最佳做法](security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="ee705-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ee705-105">選項。</span><span class="sxs-lookup"><span data-stu-id="ee705-105">Options</span></span>  
 <span data-ttu-id="ee705-106">按一下每個訂閱者之資料列中的屬性按鈕 ( **...** )，即可存取 **[散發代理程式安全性]** 或 **[合併代理程式安全性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ee705-106">Click the properties button (**...**) in the row for each Subscriber to access the **Distribution Agent Security** or **Merge Agent Security** dialog box.</span></span> <span data-ttu-id="ee705-107">如需有關代理程式所使用帳戶需要之權限的詳細資訊，請在所啟動之對話方塊上，按一下 **[說明]** 。</span><span class="sxs-lookup"><span data-stu-id="ee705-107">Click **Help** on the dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="ee705-108">在其中的一個對話方塊中輸入設定之後，訂閱者的連接資訊就會在方格中顯示。</span><span class="sxs-lookup"><span data-stu-id="ee705-108">After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="ee705-109">**訂閱者的代理程式**</span><span class="sxs-lookup"><span data-stu-id="ee705-109">**Agent for Subscriber**</span></span>  
 <span data-ttu-id="ee705-110">每個訂閱者的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee705-110">The name of each Subscriber.</span></span>  
  
 <span data-ttu-id="ee705-111">**散發者的連接**</span><span class="sxs-lookup"><span data-stu-id="ee705-111">**Connection to Distributor**</span></span>  
 <span data-ttu-id="ee705-112">這會針對交易式與快照式複寫顯示。</span><span class="sxs-lookup"><span data-stu-id="ee705-112">Displayed for transactional and snapshot replication.</span></span> <span data-ttu-id="ee705-113">用於連接到散發者的內容。</span><span class="sxs-lookup"><span data-stu-id="ee705-113">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="ee705-114">本機連接一律會使用執行代理程式之 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶的內容來進行：</span><span class="sxs-lookup"><span data-stu-id="ee705-114">Local connections are always made using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="ee705-115">就發送訂閱而言，本機連線會連線到「散發者」，因此這個欄位一律會顯示：[模擬 '\<Domain>\\<登入\>'] 或 [模擬 '\<Computer>\\<登入\>'] (針對發送訂閱)。</span><span class="sxs-lookup"><span data-stu-id="ee705-115">For push subscriptions, the local connection is the connection to the Distributor, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="ee705-116">針對提取訂閱，連線也可以用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的內容來進行。</span><span class="sxs-lookup"><span data-stu-id="ee705-116">For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="ee705-117">這個欄位會顯示下列其中一項資訊：[使用登入 '\<Login>']、[模擬 ' **\<Domain>\\<登入\>']** ，或 [模擬 '\<Computer>\\<登入\>']。</span><span class="sxs-lookup"><span data-stu-id="ee705-117">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ee705-118">建議使用 Windows 帳戶的內容進行所有連接。</span><span class="sxs-lookup"><span data-stu-id="ee705-118">recommends that all connections be made using the context of the Windows account.</span></span>  
  
 <span data-ttu-id="ee705-119">**發行者和散發者的連接**</span><span class="sxs-lookup"><span data-stu-id="ee705-119">**Connection to Publisher & Distributor**</span></span>  
 <span data-ttu-id="ee705-120">這會針對合併複寫顯示。</span><span class="sxs-lookup"><span data-stu-id="ee705-120">Displayed for merge replication.</span></span> <span data-ttu-id="ee705-121">連接到發行者與散發者所使用的內容。</span><span class="sxs-lookup"><span data-stu-id="ee705-121">The context under which the connections to the Publisher and Distributor are made.</span></span> <span data-ttu-id="ee705-122">本機連接一律會使用執行代理程式之 Windows 帳戶的內容進行連接：</span><span class="sxs-lookup"><span data-stu-id="ee705-122">Local connections are always made using the context of the Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="ee705-123">就發送訂閱而言，本機連線會連線到「發行者」和「散發者」，因此這個欄位一律會顯示：[模擬 '\<Domain>\\<登入\>'] 或 [模擬 '\<Computer>\\<登入\>'] (針對發送訂閱)。</span><span class="sxs-lookup"><span data-stu-id="ee705-123">For push subscriptions, the local connection is the connection to the Publisher and Distributor, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="ee705-124">對於提取訂閱，連接也可以用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的內容來進行。</span><span class="sxs-lookup"><span data-stu-id="ee705-124">For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="ee705-125">這個欄位會顯示下列其中一項資訊：[使用登入 '\<Login>']、[模擬 ' **\<Domain>\\<登入\>']** ，或 [模擬 '\<Computer>\\<登入\>']。</span><span class="sxs-lookup"><span data-stu-id="ee705-125">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ee705-126">建議使用 Windows 帳戶的內容進行所有連接。</span><span class="sxs-lookup"><span data-stu-id="ee705-126">recommends that all connections be made using the context of the Windows account.</span></span>  
  
 <span data-ttu-id="ee705-127">**訂閱者的連接**</span><span class="sxs-lookup"><span data-stu-id="ee705-127">**Connection to Subscriber**</span></span>  
 <span data-ttu-id="ee705-128">與訂閱者進行連接的內容。</span><span class="sxs-lookup"><span data-stu-id="ee705-128">The context under which the connection to the Subscriber is made.</span></span> <span data-ttu-id="ee705-129">本機連接一律會使用執行代理程式之 Windows 帳戶的內容進行連接：</span><span class="sxs-lookup"><span data-stu-id="ee705-129">Local connections are always made using the context of the Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="ee705-130">就發送訂閱而言，本機連線會連線到「訂閱者」，因此這個欄位一律會顯示：[模擬 '\<Domain>\\<登入\>'] 或 [模擬 '\<Computer>\\<登入\>'] (針對發送訂閱)。</span><span class="sxs-lookup"><span data-stu-id="ee705-130">For pull subscriptions, the local connection is the connection to the Subscriber, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="ee705-131">對於發送訂閱，連接也可以用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的內容來進行。</span><span class="sxs-lookup"><span data-stu-id="ee705-131">For push subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="ee705-132">這個欄位會顯示下列其中一項資訊：[使用登入 '\<Login>']、[模擬 ' **\<Domain>\\<登入\>']** ，或 [模擬 '\<Computer>\\<登入\>']。</span><span class="sxs-lookup"><span data-stu-id="ee705-132">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ee705-133">建議使用 Windows 帳戶的內容進行所有連接。</span><span class="sxs-lookup"><span data-stu-id="ee705-133">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee705-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee705-134">See Also</span></span>  
 <span data-ttu-id="ee705-135">[檢視及修改提取訂閱屬性](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ee705-135">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="ee705-136">[檢視及修改發送訂閱屬性](view-and-modify-push-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ee705-136">[View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) </span></span>  
 <span data-ttu-id="ee705-137">[管理複寫的登入與密碼](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="ee705-137">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="ee705-138">[複寫代理程式安全性模型](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="ee705-138">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 [<span data-ttu-id="ee705-139">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="ee705-139">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
