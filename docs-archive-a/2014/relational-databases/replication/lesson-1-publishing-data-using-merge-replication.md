---
title: 第 1 課：使用合併式複寫發行資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: c3c6e0b6-54cd-4b7d-8efb-2cefe14fcd7f
author: rothja
ms.author: jroth
ms.openlocfilehash: ba1d8829d84c02d1436013af80de4bf0979049e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705054"
---
# <a name="lesson-1-publishing-data-using-merge-replication"></a><span data-ttu-id="f8fbb-102">第 1 課：使用合併式複寫發行資料</span><span class="sxs-lookup"><span data-stu-id="f8fbb-102">Lesson 1: Publishing Data Using Merge Replication</span></span>
  <span data-ttu-id="f8fbb-103">在這一課，您將使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，建立合併式發行集，以發行 **範例資料庫中**Employee **、** SalesOrderHeader **和** SalesOrderDetail [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料表的子集。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-103">In this lesson, you will create a merge publication using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to publish a subset of the **Employee**, **SalesOrderHeader**, and **SalesOrderDetail** tables in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="f8fbb-104">這些資料表是以參數化資料列篩選器加以篩選，讓每一個訂閱包含唯一的資料分割。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-104">These tables are filtered with parameterized row filters so that each subscription contains a unique partition of the data.</span></span> <span data-ttu-id="f8fbb-105">此外，您也會將合併代理程式所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入加入至發行集存取清單 (PAL)。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-105">You will also add the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Merge Agent to the publication access list (PAL).</span></span> <span data-ttu-id="f8fbb-106">本教學課程要求您，先完成上一個教學課程 [準備伺服器進行複寫](tutorial-preparing-the-server-for-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-106">This tutorial requires that you have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="f8fbb-107">建立發行集並定義發行項</span><span class="sxs-lookup"><span data-stu-id="f8fbb-107">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="f8fbb-108">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-108">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="f8fbb-109">展開 [複寫]\*\*\*\* 資料夾，然後以滑鼠右鍵按一下 [本機發行集]\*\*\*\*，再按一下 [新增發行集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-109">Expand the **Replication** folder, right-click **Local Publications**, and click **New Publication**.</span></span>  
  
     <span data-ttu-id="f8fbb-110">[發行集設定精靈] 隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-110">The Publication Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="f8fbb-111">在 [發行集資料庫] 頁面上，選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-111">On the Publication Database page, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="f8fbb-112">在 [發行集類型] 頁面上，選取 [合併式發行集]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-112">On the Publication Type page, select **Merge publication**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="f8fbb-113">在 [訂閱者類型] 頁面上，確定只選取 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (含) 以後版本，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-113">On the Subscriber Types page, ensure that only [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later is selected, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="f8fbb-114">在 [發行項] 頁面上，展開 [資料表]\*\*\*\* 節點，選取 [SalesOrderHeader]\*\*\*\* 和 [SalesOrderDetail]\*\*\*\*，然後展開 [Employee]\*\*\*\*，選取 [EmployeeID]\*\*\*\* 或 [LoginID]\*\*\*\*，再按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-114">On the Articles page, expand the **Tables** node, select **SalesOrderHeader** and **SalesOrderDetail**, then expand **Employee**, select **EmployeeID** or **LoginID**, and then click **Next**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="f8fbb-115">系統會自動選取其他必要的資料行。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-115">Additional required columns are automatically selected.</span></span> <span data-ttu-id="f8fbb-116">選取任何一個自動選取的資料行，並檢視 [發行的物件]\*\*\*\* 清單下方有關為何需要資料行的說明。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-116">Select any of  the automatically selected columns and view the note below the **Objects to publish** list for an explanation why the column is required.</span></span>  
  
7.  <span data-ttu-id="f8fbb-117">在 [篩選資料表的資料列] 頁面上，按一下 [加入]\*\*\*\*，然後按一下 [加入篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-117">On the Filter Table Rows page, click **Add** and then click **Add Filter**.</span></span>  
  
8.  <span data-ttu-id="f8fbb-118">在 [加入篩選]\*\*\*\* 對話方塊中，選取 [請選取要篩選的資料表]\*\*\*\* 中的 [Employee (HumanResources)]\*\*\*\*，按一下 [LoginID]\*\*\*\* 資料行，按一下向右箭號，將資料行加入篩選查詢的 WHERE 子句，並依照下列方式修改 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="f8fbb-118">In the **Add Filter** dialog box, select **Employee (HumanResources)** in **Select the table to filter**, click the **LoginID** column, click the right arrow to add the column to the WHERE clause of the filter query, and modify the WHERE clause as follows:</span></span>  
  
    ```  
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
9. <span data-ttu-id="f8fbb-119">按一下 [這個資料表中的一個資料列只會提供給一個訂閱]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-119">Click **A row from this table will go to only one subscription**, and click **OK**.</span></span>  
  
10. <span data-ttu-id="f8fbb-120">在 [篩選資料表的資料列]\*\*\*\* 頁面上，依序按一下 [Employee (Human Resources)]\*\*\*\*、[加入]\*\*\*\* 和 [加入聯結以擴充選取的篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-120">On the **Filter Table Rows** page, click **Employee (Human Resources)**, click **Add,** and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
11. <span data-ttu-id="f8fbb-121">在 [加入聯結]\*\*\*\* 對話方塊中，選取 [聯結的資料表]\*\*\*\* 之下的 [Sales.SalesOrderHeader]\*\*\*\*，按一下 [手動寫入聯結陳述式]\*\*\*\*，如下完成聯結陳述式：</span><span class="sxs-lookup"><span data-stu-id="f8fbb-121">In the **Add Join** dialog box, select **Sales.SalesOrderHeader** under **Joined table**, click **Write the join statement manually**, and complete the join statement as follows:</span></span>  
  
    ```  
    ON Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
    ```  
  
12. <span data-ttu-id="f8fbb-122">在 [指定聯結選項]\*\*\*\* 中，選取 [唯一索引鍵]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-122">In **Specify join options**, select **Unique key**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="f8fbb-123">在 [篩選資料表的資料列] 頁面上，依序按一下 [SalesOrderHeader]\*\*\*\*、[加入]\*\*\*\* 和 [加入聯結以擴充選取的篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-123">On the Filter Table Rows page, click **SalesOrderHeader**, click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
14. <span data-ttu-id="f8fbb-124">在 [加入聯結]\*\*\*\* 對話方塊中，選取 [聯結的資料表]\*\*\*\* 之下的 [Sales.SalesOrderDetail]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-124">In the **Add Join** dialog box, select **Sales.SalesOrderDetail** under **Joined table**.</span></span>  
  
15. <span data-ttu-id="f8fbb-125">按一下 [手動寫入聯結陳述式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-125">Click **Write the join statement manually**.</span></span>  
  
16. <span data-ttu-id="f8fbb-126">在 [已篩選的資料表資料行]\*\*\*\* 中，選取 [BusinessEntityID]\*\*\*\*，然後按一下箭號按鈕將資料行名稱複製到聯結陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-126">In **Filtered table columns**, select **BusinessEntityID**, then click the arrow button to copy the column name to the loin statement.</span></span>  
  
17. <span data-ttu-id="f8fbb-127">在 [聯結陳述式]\*\*\*\* 方塊中，完成聯結陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f8fbb-127">In the **Join statement** box, complete the join statement as follows:</span></span>  
  
    ```  
    ON Employee.BusinessEntityID = SalesOrderHeader.SalesPersonID  
    ```  
  
18. <span data-ttu-id="f8fbb-128">在 [指定聯結選項]\*\*\*\* 中，選取 [唯一索引鍵]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-128">In **Specify join options**, select **Unique key**, and then click **OK**.</span></span>  
  
19. <span data-ttu-id="f8fbb-129">在 [篩選資料表的資料列]\*\*\*\* 頁面上，依序按一下 [SalesOrderHeader (Sales)]\*\*\*\*、[加入]\*\*\*\* 和 [加入聯結以擴充選取的篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-129">On the **Filter Table Rows** page, click **SalesOrderHeader (Sales)**, click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
20. <span data-ttu-id="f8fbb-130">在 [加入聯結]\*\*\*\* 對話方塊中，選取 [聯結的資料表]\*\*\*\* 之下的 [Sales.SalesOrderDetail]\*\*\*\*，按一下 [確定]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-130">In the **Add Join** dialog box, select **Sales.SalesOrderDetail** under **Joined table**, click **OK**, and then click **Next**.</span></span>  
  
21. <span data-ttu-id="f8fbb-131">選取 [立即建立快照集]\*\*\*\*，清除 [排程快照集代理程式在下列時間執行]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-131">Select **Create a snapshot immediately**, clear **Schedule the snapshot agent to run at the following times**, and click **Next**.</span></span>  
  
22. <span data-ttu-id="f8fbb-132">在 [代理程式安全性] 頁面上，按一下 [**安全性設定**]， \<_Machine_Name> 在 [**處理帳戶**] 方塊中輸入 _**\ repl_snapshot** ，提供此帳戶的密碼，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-132">On the Agent Security page, click **Security Settings**, type \<_Machine_Name>_**\repl_snapshot** in the **Process account** box, supply the password for this account, and then click **OK**.</span></span> <span data-ttu-id="f8fbb-133">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-133">Click **Finish**.</span></span>  
  
23. <span data-ttu-id="f8fbb-134">在 [完成精靈] 頁面的 [發行集名稱]\*\*\*\* 方塊中輸入 **AdvWorksSalesOrdersMerge**，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-134">On the Complete the Wizard page, enter **AdvWorksSalesOrdersMerge** in the **Publication name** box and click **Finish**.</span></span>  
  
24. <span data-ttu-id="f8fbb-135">建立發行集以後，按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-135">After the publication is created, click **Close**.</span></span>  
  
### <a name="to-view-the-status-of-snapshot-generation"></a><span data-ttu-id="f8fbb-136">檢視快照集產生的狀態</span><span class="sxs-lookup"><span data-stu-id="f8fbb-136">To view the status of snapshot generation</span></span>  
  
1.  <span data-ttu-id="f8fbb-137">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「發行者」，展開伺服器節點，然後展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-137">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="f8fbb-138">在 [本機發行集] 資料夾中，以滑鼠右鍵按一下 [AdvWorksSalesOrdersMerge]\*\*\*\*，然後按一下 [檢視快照集代理程式的狀態]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-138">In the Local Publications folder, right-click **AdvWorksSalesOrdersMerge**, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="f8fbb-139">發行集之快照集代理程式作業的目前狀態隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-139">The current status of the Snapshot Agent job for the publication is displayed.</span></span> <span data-ttu-id="f8fbb-140">確認快照集作業已成功，再繼續進行下一課。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-140">Ensure that the snapshot job has succeeded before you continue to the next lesson.</span></span>  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a><span data-ttu-id="f8fbb-141">將合併代理程式登入加入 PAL</span><span class="sxs-lookup"><span data-stu-id="f8fbb-141">To add the Merge Agent login to the PAL</span></span>  
  
1.  <span data-ttu-id="f8fbb-142">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「發行者」，展開伺服器節點，然後展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-142">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="f8fbb-143">在 [本機發行集] 資料夾中，以滑鼠右鍵按一下 [AdvWorksSalesOrdersMerge]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-143">In the Local Publications folder, right-click **AdvWorksSalesOrdersMerge**, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="f8fbb-144">[發行集屬性]\*\*\*\* 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-144">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="f8fbb-145">選取 [發行集存取清單]\*\*\*\* 頁面，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-145">Select the **Publication Access List** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="f8fbb-146">在 [加入發行集存取] 對話方塊中，選取 <電腦名稱>__**\repl_merge**，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-146">In the Add Publication Access dialog box, select _<Machine_Name>_**\repl_merge** and click **OK**.</span></span> <span data-ttu-id="f8fbb-147">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-147">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f8fbb-148">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f8fbb-148">Next Steps</span></span>  
 <span data-ttu-id="f8fbb-149">您已順利建立合併式發行集。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-149">You have successfully created the merge publication.</span></span> <span data-ttu-id="f8fbb-150">下一步，您將訂閱此發行集。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-150">Next, you will subscribe to this publication.</span></span> <span data-ttu-id="f8fbb-151">請參閱 [第 2 課：建立合併式發行集的訂閱](lesson-2-creating-a-subscription-to-the-merge-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="f8fbb-151">See [Lesson 2: Creating a Subscription to the Merge Publication](lesson-2-creating-a-subscription-to-the-merge-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fbb-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8fbb-152">See Also</span></span>  
 <span data-ttu-id="f8fbb-153">[篩選發行的資料](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="f8fbb-153">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="f8fbb-154">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="f8fbb-154">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="f8fbb-155">定義發行項</span><span class="sxs-lookup"><span data-stu-id="f8fbb-155">Define an Article</span></span>](publish/define-an-article.md)  
  
  
