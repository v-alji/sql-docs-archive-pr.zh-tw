---
title: 第 2 課：建立合併式發行集的訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
author: rothja
ms.author: jroth
ms.openlocfilehash: 2ca4f9cdf9c40d80b428d65b4201be61c2ea3eae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597073"
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a><span data-ttu-id="f4d3c-102">第 2 課：建立合併式發行集的訂閱</span><span class="sxs-lookup"><span data-stu-id="f4d3c-102">Lesson 2: Creating a Subscription to the Merge Publication</span></span>
  <span data-ttu-id="f4d3c-103">在這一課，您將使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-103">In this lesson, you will create the subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f4d3c-104">接著，您將在訂閱資料庫上設定權限，並手動為新訂閱產生已篩選資料快照集。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-104">You will then set permissions on the subscription database and manually generate the filtered data snapshot for the new subscription.</span></span> <span data-ttu-id="f4d3c-105">您必須先完成上一課 [第 1 課：使用合併式複寫發行資料](lesson-1-publishing-data-using-merge-replication.md)，才能進行這一課。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-105">This lesson requires that you have completed the previous lesson, [Lesson 1: Publishing Data Using Merge Replication](lesson-1-publishing-data-using-merge-replication.md).</span></span>  
  
### <a name="to-create-the-subscription"></a><span data-ttu-id="f4d3c-106">建立訂閱</span><span class="sxs-lookup"><span data-stu-id="f4d3c-106">To create the subscription</span></span>  
  
1.  <span data-ttu-id="f4d3c-107">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的「訂閱者」，依序展開伺服器節點和 [複寫]\*\*\*\* 資料夾，以滑鼠右鍵按一下 [本機訂閱]\*\*\*\* 資料夾，然後按一下 [新增訂閱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-107">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, expand the **Replication** folder, right-click the **Local Subscriptions** folder, and then click **New Subscriptions**.</span></span>  
  
     <span data-ttu-id="f4d3c-108">「新增訂閱精靈」隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-108">The New Subscription Wizard launches.</span></span>  
  
2.  <span data-ttu-id="f4d3c-109">在 [發行集]\*\*\*\* 頁面上，按一下 [發行者]\*\*\*\* 清單中的 [尋找 SQL Server 發行者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-109">On the **Publication** page, click **Find SQL Server Publisher** in the **Publisher** list.</span></span>  
  
3.  <span data-ttu-id="f4d3c-110">在 [連接到伺服器]\*\*\*\* 對話方塊的 [伺服器名稱]\*\*\*\* 方塊中，輸入「發行者」執行個體的名稱，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-110">In the **Connect to Server** dialog box, enter the name of the Publisher instance in the **Server name** box, and click **Connect**.</span></span>  
  
4.  <span data-ttu-id="f4d3c-111">按一下 [AdvWorksSalesOrdersMerge]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-111">Click **AdvWorksSalesOrdersMerge**, and click **Next**.</span></span>  
  
5.  <span data-ttu-id="f4d3c-112">在 [合併代理程式位置] 頁面上，按一下 [在訂閱者端執行每一個代理程式]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-112">On the Merge Agent Location page, click **Run each agent at its Subscriber**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="f4d3c-113">在 [訂閱者] 頁面上，選取「訂閱者」伺服器的執行個體名稱，然後在 [訂閱資料庫]\*\*\*\* 之下，從清單選取 [\<New Database>]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-113">On the Subscribers page, select the instance name of the Subscriber server, and under **Subscription Database**, select **\<New Database>** from the list.</span></span>  
  
7.  <span data-ttu-id="f4d3c-114">在 [新增資料庫]\*\*\*\* 對話方塊的 [資料庫名稱]\*\*\*\* 方塊中，輸入 **SalesOrdersReplica**，然後按一下 [確定]\*\*\*\*，再按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-114">In the **New Database** dialog box, enter **SalesOrdersReplica** in the **Database name** box, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="f4d3c-115">在 [合併代理程式安全性] 頁面上，按一下省略號 (**...**) ] 按鈕， \<_Machine_Name> 在 [**處理帳戶**] 方塊中輸入 _**\ repl_merge** ，提供此帳戶的密碼，按一下 **[確定**]，按 [**下**一步]，然後再按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-115">On the Merge Agent Security page, click the ellipsis (**...**) button, enter \<_Machine_Name>_**\repl_merge** in the **Process account** box, supply the password for this account, click **OK**, click **Next**, and then click **Next** again.</span></span>  
  
9. <span data-ttu-id="f4d3c-116">在 [初始化訂閱] 頁面上，從 [初始化時機]\*\*\*\* 清單中選取 [第一次同步處理時]\*\*\*\*，按一下 [下一步]\*\*\*\*，然後再按一次 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-116">On the Initialize Subscriptions page, select **At first synchronization** from the **Initialize When** list, click **Next**, and then click **Next** again.</span></span>  
  
10. <span data-ttu-id="f4d3c-117">在 [HOST_NAME 值] 頁面 `adventure-works\pamela0` 的 [ **HOST_NAME 值**] 方塊中，輸入的值，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-117">On the HOST_NAME Values page, enter a value of `adventure-works\pamela0` in the **HOST_NAME Value** box, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="f4d3c-118">再按一次 [完成]\*\*\*\*，建立訂閱之後，按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-118">Click **Finish** again, and after the subscription is created, click **Close**.</span></span>  
  
### <a name="setting-database-permissions-at-the-subscriber"></a><span data-ttu-id="f4d3c-119">在訂閱者端設定資料庫權限</span><span class="sxs-lookup"><span data-stu-id="f4d3c-119">Setting database permissions at the Subscriber</span></span>  
  
1.  <span data-ttu-id="f4d3c-120">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的「訂閱者」，依序展開 [資料庫]\*\*\*\*、[SalesOrdersReplica]\*\*\*\* 和 [安全性]\*\*\*\*，以滑鼠右鍵按一下 [使用者]\*\*\*\*，然後選取 [新增使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Databases**, **SalesOrdersReplica**, and **Security**, right-click **Users**, and then select **New User**.</span></span>  
  
2.  <span data-ttu-id="f4d3c-121">在 [**一般**] 頁面 \<_Machine_Name> _的 [**使用者名稱**] 方塊中輸入**\ repl_merge** ，按一下省略號\*\* (...**) ] 按鈕，按一下 **[流覽]**，選取 \<_Machine_Name> _ **\ repl_merge**，按一下 **[確定]**，按一下 [**檢查名稱\*\*]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-121">On the **General** page, enter \<_Machine_Name>_**\repl_merge** in the **User name** box, click the ellipsis (**...**) button, click **Browse**, select \<_Machine_Name>_**\repl_merge**, click **OK**, click **Check Names**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f4d3c-122">在 [資料庫角色成員資格]\*\*\*\* 中，選取 [db_owner]\*\*\*\*，然後按一下 [確定]\*\*\*\* 建立使用者。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-122">In **Database role membership**, select **db_owner**, and then click **OK** to create the user.</span></span>  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a><span data-ttu-id="f4d3c-123">為訂閱建立已篩選資料快照集</span><span class="sxs-lookup"><span data-stu-id="f4d3c-123">To create the filtered data snapshot for the subscription</span></span>  
  
1.  <span data-ttu-id="f4d3c-124">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「發行者」，展開伺服器節點，然後展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-124">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="f4d3c-125">在 [本機發行集]\*\*\*\* 資料夾中，以滑鼠右鍵按一下 [AdvWorksSalesOrdersMerge]\*\*\*\* 發行集，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-125">In the **Local Publications** folder, right-click the **AdvWorksSalesOrdersMerge** publication, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="f4d3c-126">[發行集屬性]\*\*\*\* 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-126">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="f4d3c-127">選取 [資料分割]\*\*\*\* 頁面，然後按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-127">Select the **Data Partitions** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="f4d3c-128">在 [**加入資料分割**] 對話方塊中，于 `adventure-works\pamela0` [ **HOST_NAME 值**] 方塊中輸入，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-128">In the **Add Data Partition** dialog box, type `adventure-works\pamela0` in the **HOST_NAME Value** box, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="f4d3c-129">選取新加入的資料分割，按一下 [立即產生選取的快照集]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-129">Select the newly added partition, click **Generate the selected snapshots now**, and then click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f4d3c-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f4d3c-130">Next Steps</span></span>  
 <span data-ttu-id="f4d3c-131">您已順利建立合併式發行集的訂閱，並為新訂閱的資料分割產生已篩選快照集，因此在訂閱初始化時，即可使用此快照集。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-131">You have successfully created a subscription to the merge publication and generated the filtered snapshot for the new subscription's data partition so that it will be available when the subscription is initialized.</span></span> <span data-ttu-id="f4d3c-132">下一步，您將授與權限給訂閱資料庫上的合併代理程式，並執行合併代理程式以啟動同步處理並初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-132">Next, you will grant rights to the Merge Agent on the subscription database and run the Merge Agent to start synchronization and initialize the subscription.</span></span> <span data-ttu-id="f4d3c-133">請參閱 [第 3 課：同步處理合併式發行集的訂閱](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="f4d3c-133">See [Lesson 3: Synchronizing the Subscription to the Merge Publication](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d3c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4d3c-134">See Also</span></span>  
 <span data-ttu-id="f4d3c-135">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="f4d3c-135">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="f4d3c-136">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="f4d3c-136">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="f4d3c-137">Snapshots for Merge Publications with Parameterized Filters</span><span class="sxs-lookup"><span data-stu-id="f4d3c-137">Snapshots for Merge Publications with Parameterized Filters</span></span>](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
