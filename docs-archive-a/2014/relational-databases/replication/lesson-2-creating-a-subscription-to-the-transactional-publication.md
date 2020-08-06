---
title: 第 2 課：建立交易式發行集的訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
author: rothja
ms.author: jroth
ms.openlocfilehash: dbf40fa259302dffdd6c0b8e8717b7c35b0cf92d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585811"
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a><span data-ttu-id="eef98-102">第 2 課：建立交易式發行集的訂閱</span><span class="sxs-lookup"><span data-stu-id="eef98-102">Lesson 2: Creating a Subscription to the Transactional Publication</span></span>
  <span data-ttu-id="eef98-103">在這一課，您將使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="eef98-103">In this lesson, you will create a subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="eef98-104">您必須先完成上一課 [第 1 課：使用異動複寫發行資料](lesson-1-publishing-data-using-transactional-replication.md)，才能進行這一課。</span><span class="sxs-lookup"><span data-stu-id="eef98-104">This lesson requires that you have completed the previous lesson, [Lesson 1: Publishing Data Using Transactional Replication](lesson-1-publishing-data-using-transactional-replication.md).</span></span>  
  
### <a name="to-create-the-subscription"></a><span data-ttu-id="eef98-105">建立訂閱</span><span class="sxs-lookup"><span data-stu-id="eef98-105">To create the subscription</span></span>  
  
1.  <span data-ttu-id="eef98-106">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「發行者」，展開伺服器節點，然後展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="eef98-106">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="eef98-107">在 **[本機發行集]** 資料夾中，以滑鼠右鍵按一下 **[AdvWorksProductTrans]** 發行集，然後按一下 **[新增訂閱]**。</span><span class="sxs-lookup"><span data-stu-id="eef98-107">In the **Local Publications** folder, right-click the **AdvWorksProductTrans** publication, and then click **New Subscriptions**.</span></span>  
  
     <span data-ttu-id="eef98-108">「新增訂閱精靈」隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="eef98-108">The New Subscription Wizard launches.</span></span>  
  
3.  <span data-ttu-id="eef98-109">在 [發行集] 頁面上，選取 **[AdvWorksProductTrans]**，然後按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="eef98-109">On the Publication page, select **AdvWorksProductTrans**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="eef98-110">在 [散發代理程式位置] 頁面上，選取 **[在散發者端執行所有代理程式]**，然後按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="eef98-110">On the Distribution Agent Location page, select **Run all agents at the Distributor**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="eef98-111">在 [訂閱者] 頁面上，如果未顯示訂閱者執行個體的名稱，請按一下 **[加入訂閱者]**，再按 **[加入 SQL Server 訂閱者]**，在 **[連接到伺服器]** 對話方塊中輸入訂閱者執行個體名稱，然後按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="eef98-111">On the Subscribers page, if the name of the Subscriber instance is not displayed, click **Add Subscriber**, click **Add SQL Server Subscriber**, enter the Subscriber instance name in the **Connect to Server** dialog box, and then click **Connect**.</span></span>  
  
6.  <span data-ttu-id="eef98-112">在 [訂閱者] 頁面上，選取訂閱者伺服器的實例名稱，然後選取 [ **\<New Database>** **訂閱資料庫**] 底下的 []。</span><span class="sxs-lookup"><span data-stu-id="eef98-112">On the Subscribers page, select the instance name of the Subscriber server, and select **\<New Database>** under **Subscription Database**.</span></span>  
  
7.  <span data-ttu-id="eef98-113">在 **[新增資料庫]** 對話方塊的 **[資料庫名稱]** 方塊中，輸入 **ProductReplica** ，然後按一下 **[確定]**，再按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="eef98-113">On the **New Database** dialog box, enter **ProductReplica** in the **Database name** box, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="eef98-114">在 [**散發代理程式安全性**] 對話方塊中，按一下省略號 (**...**) ] 按鈕， \<_Machine_Name> 在 [**處理帳戶**] 方塊中輸入 _**\ repl_distribution** ，輸入此帳戶的密碼，按一下 **[確定]**，然後按 **[下一步**]。</span><span class="sxs-lookup"><span data-stu-id="eef98-114">In the **Distribution Agent Security** dialog box, click the ellipsis (**...**) button, enter \<_Machine_Name>_**\repl_distribution** in the **Process account** box, enter the password for this account, click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="eef98-115">按一下 **[完成]** 接受其餘頁面上的預設值，並完成精靈。</span><span class="sxs-lookup"><span data-stu-id="eef98-115">Click **Finish** to accept the default values on the remaining pages and complete the wizard.</span></span>  
  
### <a name="setting-database-permissions-at-the-subscriber"></a><span data-ttu-id="eef98-116">在訂閱者端設定資料庫權限</span><span class="sxs-lookup"><span data-stu-id="eef98-116">Setting database permissions at the Subscriber</span></span>  
  
1.  <span data-ttu-id="eef98-117">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的「訂閱者」，依序展開 [資料庫]\*\*\*\*、[ProductReplica]\*\*\*\* 和 [安全性]\*\*\*\*，以滑鼠右鍵按一下 [使用者]\*\*\*\*，然後選取 [新增使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="eef98-117">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Databases**, **ProductReplica**, and **Security**, right-click **Users**, and then select **New User**.</span></span>  
  
2.  <span data-ttu-id="eef98-118">在 **[一般]** 頁面的 **[使用者類型]** 清單中，選取 **[Windows 使用者]**。</span><span class="sxs-lookup"><span data-stu-id="eef98-118">On the **General** page, in the **User type** list, select **Windows user**.</span></span>  
  
3.  <span data-ttu-id="eef98-119">選取 [**使用者名稱**] 方塊，然後按一下省略號 ( ... ) ] 按鈕，在 [**輸入物件名稱來選取**] 方塊輸入 <Machine_Name>**\ Repl_distribution**，按一下 [**檢查名稱**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="eef98-119">Select the **User name** box and click the ellipsis (...) button, in the **Enter the object name to select** box type <Machine_Name>**\repl_distribution**, click **Check Names**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="eef98-120">在 [成員資格]\*\*\*\* 頁面的 [資料庫角色成員資格]\*\*\*\* 區域中，選取 [db_owner]\*\*\*\*，然後按一下 [確定]\*\*\*\* 建立使用者。</span><span class="sxs-lookup"><span data-stu-id="eef98-120">On the **Membership** page, in **Database role membership** area, select **db_owner**, and then click **OK** to create the user.</span></span>  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a><span data-ttu-id="eef98-121">檢視訂閱的同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="eef98-121">To view the synchronization status of the subscription</span></span>  
  
1.  <span data-ttu-id="eef98-122">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「發行者」，展開伺服器節點，然後展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="eef98-122">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="eef98-123">在 **[本機訂閱]** 資料夾中，展開 **[AdvWorksProductTrans]** 發行集，以滑鼠右鍵按一下 **ProductReplica** 資料庫中的訂閱，然後按一下 **[檢視同步處理狀態]**。</span><span class="sxs-lookup"><span data-stu-id="eef98-123">In the **Local Publications** folder, expand the **AdvWorksProductTrans** publication, right-click the subscription in the **ProductReplica** database, and then click **View Synchronization Status**.</span></span>  
  
     <span data-ttu-id="eef98-124">訂閱的目前訂閱狀態隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="eef98-124">The current synchronization status of the subscription is displayed.</span></span>  
  
3.  <span data-ttu-id="eef98-125">如果 **[AdvWorksProductTrans]** 之下看不到訂閱，請按 F5 重新整理清單。</span><span class="sxs-lookup"><span data-stu-id="eef98-125">If the subscription is not visible under **AdvWorksProductTrans**, press F5 to refresh the list.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eef98-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eef98-126">Next Steps</span></span>  
 <span data-ttu-id="eef98-127">您已順利建立交易式發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="eef98-127">You have successfully created a subscription to the transactional publication.</span></span> <span data-ttu-id="eef98-128">由於此訂閱的散發代理程式會持續執行，因此，訂閱會在建立時初始化。</span><span class="sxs-lookup"><span data-stu-id="eef98-128">Because the Distribution Agent for this subscription runs continuously, the subscription is initialized when it is created.</span></span> <span data-ttu-id="eef98-129">下一步，您將使用追蹤 Token，確認變更正複寫至「訂閱者」並決定延遲。</span><span class="sxs-lookup"><span data-stu-id="eef98-129">Next, you will use tracer tokens to verify that changes are being replicated to the Subscriber and to determine latency.</span></span> <span data-ttu-id="eef98-130">請參閱＜ [Lesson 3: Validating the Subscription and Measuring Latency](lesson-3-validating-the-subscription-and-measuring-latency.md)＞。</span><span class="sxs-lookup"><span data-stu-id="eef98-130">See [Lesson 3: Validating the Subscription and Measuring Latency](lesson-3-validating-the-subscription-and-measuring-latency.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef98-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eef98-131">See Also</span></span>  
 <span data-ttu-id="eef98-132">[使用快照集初始化訂閱](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="eef98-132">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="eef98-133">[Create a Push Subscription](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="eef98-133">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="eef98-134">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="eef98-134">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
