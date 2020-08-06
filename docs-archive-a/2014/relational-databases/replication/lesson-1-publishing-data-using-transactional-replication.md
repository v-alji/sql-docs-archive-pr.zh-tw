---
title: 第 1 課：使用異動複寫發行資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce20f4ed8863ede34c8709d2b77bf032e7d14a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687754"
---
# <a name="lesson-1-publishing-data-using-transactional-replication"></a><span data-ttu-id="2a05c-102">第 1 課：使用異動複寫發行資料</span><span class="sxs-lookup"><span data-stu-id="2a05c-102">Lesson 1: Publishing Data Using Transactional Replication</span></span>
  <span data-ttu-id="2a05c-103"> 在這一課，您將使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 建立交易式發行集，以發行 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫中 **Product** 資料表的篩選子集。</span><span class="sxs-lookup"><span data-stu-id="2a05c-103">In this lesson, you will create a transactional publication using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to publish a filtered subset of the **Product** table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="2a05c-104">此外，您也會將散發代理程式所使用的 SQL Server 登入加入至發行集存取清單 (PAL)。</span><span class="sxs-lookup"><span data-stu-id="2a05c-104">You will also add the SQL Server login used by the Distribution Agent to the publication access list (PAL).</span></span> <span data-ttu-id="2a05c-105">開始進行此教學課程之前，必須先完成上一個教學課程 [準備伺服器進行複寫](tutorial-preparing-the-server-for-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="2a05c-105">Before starting this tutorial, you should have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="2a05c-106">建立發行集並定義發行項</span><span class="sxs-lookup"><span data-stu-id="2a05c-106">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="2a05c-107">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="2a05c-107">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2a05c-108">展開 [複寫]\*\*\*\* 資料夾，然後以滑鼠右鍵按一下 [本機發行集]\*\*\*\* 資料夾，再按一下 [新增發行集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-108">Expand the **Replication** folder, right-click the **Local Publications** folder, and click **New Publication**.</span></span>  
  
     <span data-ttu-id="2a05c-109">[發行集設定精靈] 隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="2a05c-109">The Publication Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="2a05c-110">在 [發行集資料庫] 頁面上，選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-110">On the Publication Database page, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="2a05c-111">在 [發行集類型] 頁面上，選取 [交易式發行集]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-111">On the Publication Type page, select **Transactional publication**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="2a05c-112">在 [發行項] 頁面上，展開 [Tables]\*\*\*\* 節點，選取 [Product]\*\*\*\* 核取方塊，然後展開 [Product]\*\*\*\*，再清除 [ListPrice]\*\*\*\* 和 [StandardCost]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2a05c-112">On the Articles page, expand the **Tables** node, select the **Product** check box, then expand **Product** and clear the **ListPrice** and **StandardCost** check boxes.</span></span> <span data-ttu-id="2a05c-113">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a05c-113">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="2a05c-114">在 [篩選資料表的資料列] 頁面上，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-114">On the Filter Table Rows page, click **Add**.</span></span>  
  
7.  <span data-ttu-id="2a05c-115">在 [新增篩選]\*\*\*\* 對話方塊中，按一下 [SafetyStockLevel]\*\*\*\* 資料行，再按一下向右鍵，將資料行新增至篩選查詢的篩選陳述式 WHERE 子句中，並依照下列方式修改 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="2a05c-115">In the **Add Filter** dialog box, click the **SafetyStockLevel** column, click the right arrow to add the column to the Filter statement WHERE clause of the filter query, and modify the WHERE clause as follows:</span></span>  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  <span data-ttu-id="2a05c-116">按一下 [確定]\*\*\*\*，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-116">Click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="2a05c-117">選取 [立即建立快照集，並保留快照集為可使用狀態，以初始化訂閱]\*\*\*\* 核取方塊，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-117">Select the **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** check box, and click **Next**.</span></span>  
  
10. <span data-ttu-id="2a05c-118">在 [代理程式安全性] 頁面上，清除 [使用快照集代理程式的安全性設定]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2a05c-118">On the Agent Security page, clear **Use the security settings from the Snapshot Agent** check box.</span></span>  
  
11. <span data-ttu-id="2a05c-119">按一下 [快照集代理程式的 [**安全性設定**]， \<_Machine_Name> 在 [**處理帳戶**] 方塊中輸入 _**\ repl_snapshot** ，提供此帳戶的密碼，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2a05c-119">Click **Security Settings** for the Snapshot Agent, enter \<_Machine_Name>_**\repl_snapshot** in the **Process account** box, supply the password for this account, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="2a05c-120">重複執行先前的步驟，將 repl_logreader 設定為記錄讀取器代理程式的處理帳戶，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-120">Repeat the previous step to set repl_logreader as the process account for the Log Reader Agent, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="2a05c-121">在 [完成精靈] 頁面的 [發行集名稱]\*\*\*\* 方塊中輸入 [AdvWorksProductTrans]\*\*\*\*，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-121">On the Complete the Wizard page, type **AdvWorksProductTrans** in the **Publication name** box, and click **Finish**.</span></span>  
  
14. <span data-ttu-id="2a05c-122">建立發行集之後，按一下 [關閉]\*\*\*\* 以完成精靈。</span><span class="sxs-lookup"><span data-stu-id="2a05c-122">After the publication is created, click **Close** to complete the wizard.</span></span>  
  
### <a name="to-view-the-status-of-snapshot-generation"></a><span data-ttu-id="2a05c-123">檢視快照集產生的狀態</span><span class="sxs-lookup"><span data-stu-id="2a05c-123">To view the status of snapshot generation</span></span>  
  
1.  <span data-ttu-id="2a05c-124">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「發行者」，展開伺服器節點，然後展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2a05c-124">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="2a05c-125">在 [本機發行集]\*\*\*\* 資料夾中，以滑鼠右鍵按一下 [AdvWorksProductTrans]\*\*\*\*，然後按一下 [檢視快照集代理程式狀態]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-125">In the **Local Publications** folder, right-click **AdvWorksProductTrans**, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="2a05c-126">發行集之快照集代理程式作業的目前狀態隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="2a05c-126">The current status of the Snapshot Agent job for the publication is displayed.</span></span> <span data-ttu-id="2a05c-127">確認快照集作業已成功，再繼續進行下一課。</span><span class="sxs-lookup"><span data-stu-id="2a05c-127">Verify that the snapshot job has succeeded before you continue to the next lesson.</span></span>  
  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a><span data-ttu-id="2a05c-128">將散發代理程式登入加入 PAL</span><span class="sxs-lookup"><span data-stu-id="2a05c-128">To add the Distribution Agent login to the PAL</span></span>  
  
1.  <span data-ttu-id="2a05c-129">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「發行者」，展開伺服器節點，然後展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2a05c-129">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="2a05c-130">在 [本機發行集]\*\*\*\* 資料夾中，以滑鼠右鍵按一下 [AdvWorksProductTrans]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-130">In the **Local Publications** folder, right-click **AdvWorksProductTrans**, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="2a05c-131">[發行集屬性]\*\*\*\* 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="2a05c-131">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="2a05c-132">選取 [發行集存取清單]\*\*\*\* 頁面，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-132">Select the **Publication Access List** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="2a05c-133">在 [新增發行集存取]\*\*\*\* 對話方塊中，選取 [<電腦名稱>__ \repl_distribution]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a05c-133">\In the **Add Publication Access** dialog box, select _<Machine_Name>_**\repl_distribution** and click **OK**.</span></span> <span data-ttu-id="2a05c-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2a05c-134">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2a05c-135">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2a05c-135">Next Steps</span></span>  
 <span data-ttu-id="2a05c-136">您已順利建立交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="2a05c-136">You have successfully created the transactional publication.</span></span> <span data-ttu-id="2a05c-137">下一步，您將訂閱此發行集。</span><span class="sxs-lookup"><span data-stu-id="2a05c-137">Next, you will subscribe to this publication.</span></span> <span data-ttu-id="2a05c-138">請參閱 [第 2 課：建立交易式發行集的訂閱](lesson-2-creating-a-subscription-to-the-transactional-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="2a05c-138">See [Lesson 2: Creating a Subscription to the Transactional Publication](lesson-2-creating-a-subscription-to-the-transactional-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a05c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a05c-139">See Also</span></span>  
 <span data-ttu-id="2a05c-140">[篩選發行的資料](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="2a05c-140">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="2a05c-141">[Define an Article](publish/define-an-article.md) </span><span class="sxs-lookup"><span data-stu-id="2a05c-141">[Define an Article](publish/define-an-article.md) </span></span>  
 [<span data-ttu-id="2a05c-142">建立並套用快照集</span><span class="sxs-lookup"><span data-stu-id="2a05c-142">Create and Apply the Snapshot</span></span>](create-and-apply-the-snapshot.md)  
  
  
