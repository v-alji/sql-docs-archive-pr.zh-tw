---
title: 訂閱者 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c5281a53b755bc171cdf96e7856e38ee6a54a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593922"
---
# <a name="subscribers"></a><span data-ttu-id="0da28-102">訂閱者</span><span class="sxs-lookup"><span data-stu-id="0da28-102">Subscribers</span></span>
  <span data-ttu-id="0da28-103">指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將接收所選發行集之訂閱的或非訂閱者。</span><span class="sxs-lookup"><span data-stu-id="0da28-103">Specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers that will receive a subscription to the selected publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0da28-104">選項。</span><span class="sxs-lookup"><span data-stu-id="0da28-104">Options</span></span>  
 <span data-ttu-id="0da28-105">**[發行者屬性]**</span><span class="sxs-lookup"><span data-stu-id="0da28-105">**Subscribers**</span></span>  
 <span data-ttu-id="0da28-106">選取方格中的核取方塊以啟用對應的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源，作為 **[發行集]** 頁面上選擇之發行集的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="0da28-106">Select the check box in the grid to enable the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source as a Subscriber to the publication chosen on the **Publication** page.</span></span> <span data-ttu-id="0da28-107">如果未列出訂閱者，請按一下 **[加入訂閱者]** 或 **[加入 SQL Server 訂閱者]** 。</span><span class="sxs-lookup"><span data-stu-id="0da28-107">If the Subscriber is not listed, click **Add Subscriber** or **Add SQL Server Subscriber**.</span></span>  
  
 <span data-ttu-id="0da28-108">**訂閱資料庫**</span><span class="sxs-lookup"><span data-stu-id="0da28-108">**Subscription database**</span></span>  
 <span data-ttu-id="0da28-109">此資料行中顯示的資訊和可用的動作，會視 **[訂閱者]** 資料行中所列出的訂閱者類型而定：</span><span class="sxs-lookup"><span data-stu-id="0da28-109">The information displayed in and actions available from this column depend on the type of Subscriber listed in the **Subscribers** column:</span></span>  
  
-   <span data-ttu-id="0da28-110">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者，請從 **[訂閱資料庫]** 清單中選取訂閱資料庫，或從相同清單中選取 **[新增資料庫]** 命令來建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="0da28-110">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, select a subscription database from the **Subscription Database** list or create a new database by selecting the **New database** command from the same list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0da28-111">如果您啟用發行者作為訂閱者，則訂閱資料庫必須不同於發行集資料庫。</span><span class="sxs-lookup"><span data-stu-id="0da28-111">If you are enabling the Publisher as a Subscriber, the subscription database must be different from the publication database.</span></span>  
  
-   <span data-ttu-id="0da28-112">針對非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者，不會顯示訂閱資料庫。</span><span class="sxs-lookup"><span data-stu-id="0da28-112">For non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, the subscription database is not displayed.</span></span> <span data-ttu-id="0da28-113">在 **[加入非 SQL Server]** 對話方塊的 **[資料來源名稱]** 欄位中，指定資料庫以及其他連接資訊。</span><span class="sxs-lookup"><span data-stu-id="0da28-113">Specify the database, along with other connection information, in the **Data source name** field of the **Add Non-SQL Server** dialog box.</span></span> <span data-ttu-id="0da28-114">按一下 **[加入訂閱者]** 然後按一下 **[加入非 SQL Server 訂閱者]** ，即可使用此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0da28-114">This dialog box is available by clicking **Add Subscriber** and then clicking **Add Non-SQL Server Subscriber**.</span></span>  
  
 <span data-ttu-id="0da28-115">**[加入訂閱者]**</span><span class="sxs-lookup"><span data-stu-id="0da28-115">**Add Subscriber**</span></span>  
 <span data-ttu-id="0da28-116">將伺服器加入可以啟用為訂閱者的伺服器清單中。</span><span class="sxs-lookup"><span data-stu-id="0da28-116">Add a server to the list of servers that can be enabled as Subscribers.</span></span> <span data-ttu-id="0da28-117">當所有下列條件都為 True 時，會顯示此按鈕：</span><span class="sxs-lookup"><span data-stu-id="0da28-117">This button is displayed when all of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="0da28-118">選取的發行集是不支援更新訂閱的快照式發行集或交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="0da28-118">The publication you selected is a snapshot or transactional publication that does not support updating subscriptions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0da28-119">如果您所訂閱的發行集擁有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的訂閱，而發行集尚未啟用給非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者使用，則您無法新增非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的訂閱。</span><span class="sxs-lookup"><span data-stu-id="0da28-119">If the publication you are subscribing to has [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subscriptions and the publication is not already enabled for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, you cannot add a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subscription.</span></span>  
  
-   <span data-ttu-id="0da28-120">訂閱是發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="0da28-120">The subscription is a push subscription.</span></span>  
  
-   <span data-ttu-id="0da28-121">所選發行集的發行者是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0da28-121">The Publisher of the selected publication is [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later.</span></span>  
  
 <span data-ttu-id="0da28-122">按一下 **[加入訂閱者]** 會顯示包含下列兩個選項的功能表： **[加入 SQL Server 訂閱者]** 和 **[加入非 SQL Server 訂閱者]** 。</span><span class="sxs-lookup"><span data-stu-id="0da28-122">Clicking **Add Subscriber** shows a menu with two choices: **Add SQL Server Subscriber** and **Add Non-SQL Server Subscriber**.</span></span> <span data-ttu-id="0da28-123">按一下 **[加入非 SQL Server 訂閱者]** ，即可加入 Oracle 或 IBM DB2 訂閱者。</span><span class="sxs-lookup"><span data-stu-id="0da28-123">Click **Add Non-SQL Server Subscriber** to add an Oracle or IBM DB2 Subscriber.</span></span>  
  
 <span data-ttu-id="0da28-124">**[加入 SQL Server 訂閱者]**</span><span class="sxs-lookup"><span data-stu-id="0da28-124">**Add SQL Server Subscriber**</span></span>  
 <span data-ttu-id="0da28-125">將伺服器加入可以啟用為訂閱者的伺服器清單中。</span><span class="sxs-lookup"><span data-stu-id="0da28-125">Add a server to the list of servers that can be enabled as Subscribers.</span></span> <span data-ttu-id="0da28-126">當一或多個下列條件為 True 時，會顯示此按鈕：</span><span class="sxs-lookup"><span data-stu-id="0da28-126">This button is displayed when one or more of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="0da28-127">選取的發行集是合併式發行集，或支援更新訂閱的快照式發行集或交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="0da28-127">The publication you selected is a merge publication, or a snapshot or transactional publication that supports updating subscriptions.</span></span>  
  
-   <span data-ttu-id="0da28-128">訂閱是提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="0da28-128">The subscription is a pull subscription.</span></span>  
  
-   <span data-ttu-id="0da28-129">選取之發行集的發行者是 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]之前的版本。</span><span class="sxs-lookup"><span data-stu-id="0da28-129">The Publisher of the selected publication is earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="0da28-130">針對先前的版本，只有當一或多個下列條件為 True 時，才會顯示此按鈕：</span><span class="sxs-lookup"><span data-stu-id="0da28-130">For earlier versions, the button is displayed only if one or more of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="0da28-131">您是發行者端 **系統管理員** (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="0da28-131">You are a member of the **sysadmin** fixed server role at the Publisher.</span></span>  
  
    -   <span data-ttu-id="0da28-132">訂閱者已經加入 **[發行者屬性]** 對話方塊中的 **[訂閱者]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="0da28-132">The Subscriber has been added on the **Subscribers** page of the **Publisher Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="0da28-133">發行集允許匿名訂閱。</span><span class="sxs-lookup"><span data-stu-id="0da28-133">The publication allows anonymous subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da28-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0da28-134">See Also</span></span>  
 <span data-ttu-id="0da28-135">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="0da28-135">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="0da28-136">[Create a Push Subscription](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="0da28-136">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="0da28-137">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="0da28-137">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="0da28-138">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="0da28-138">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
