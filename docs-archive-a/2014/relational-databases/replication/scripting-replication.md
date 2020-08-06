---
title: 編寫複寫指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server replication], replication objects
- merge replication scripting [SQL Server replication]
- replication [SQL Server], scripting
- snapshot replication [SQL Server], scripting
- scripts [SQL Server replication]
- transactional replication, scripting
ms.assetid: e50fac44-54c0-470c-a4ea-9c111fa4322b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e865e2664a399bca4738c1fc157bef176f35e96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585260"
---
# <a name="scripting-replication"></a><span data-ttu-id="8aa68-102">編寫複寫指令碼</span><span class="sxs-lookup"><span data-stu-id="8aa68-102">Scripting Replication</span></span>
  <span data-ttu-id="8aa68-103">拓撲中的所有複寫元件都應作為損毀復原計畫的一部份來編寫指令碼，而指令碼也可以用於自動執行重複性工作。</span><span class="sxs-lookup"><span data-stu-id="8aa68-103">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="8aa68-104">指令碼包含實作已編寫指令碼之複寫元件所必要的 Transact-SQL 系統預存程序，例如，發行集或訂閱。</span><span class="sxs-lookup"><span data-stu-id="8aa68-104">A script contains the Transact-SQL system stored procedures necessary to implement the replication component(s) scripted, such as a publication or subscription.</span></span> <span data-ttu-id="8aa68-105">指令碼可以在精靈中建立 (例如 [新增發行集精靈])，或可在建立元件之後，於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中建立。</span><span class="sxs-lookup"><span data-stu-id="8aa68-105">Scripts can be created in a wizard (such as the New Publication Wizard) or in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] after you create a component.</span></span> <span data-ttu-id="8aa68-106">您可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 **sqlcmd**，檢視、修改和執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="8aa68-106">You can view, modify, and run the script using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or **sqlcmd**.</span></span> <span data-ttu-id="8aa68-107">指令碼可以和備份檔案一起儲存，萬一必須重新設定複寫拓撲時即可使用。</span><span class="sxs-lookup"><span data-stu-id="8aa68-107">Scripts can be stored with backup files to be used in case a replication topology must be reconfigured.</span></span>  
  
 <span data-ttu-id="8aa68-108">如果對任何屬性進行了變更，則應對該元件重新編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="8aa68-108">A component should be re-scripted if any property changes are made.</span></span> <span data-ttu-id="8aa68-109">若您在異動複寫中使用自訂預存程序，每個程序副本會與指令碼同時儲存；若程序變更，則副本必須更新 (程序通常在結構描述變更或改變應用程式需求時進行更新)。</span><span class="sxs-lookup"><span data-stu-id="8aa68-109">If you use custom stored procedures with transactional replication, a copy of each procedure should be stored with the scripts; the copy should be updated if the procedure changes (procedures are typically updated due to schema changes or changing application requirements).</span></span> <span data-ttu-id="8aa68-110">如需自訂程序的詳細資訊，請參閱[指定交易式發行項變更的傳播方式](transactional/transactional-articles-specify-how-changes-are-propagated.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa68-110">For more information about custom procedures, see [Specify How Changes Are Propagated for Transactional Articles](transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
 <span data-ttu-id="8aa68-111">對於使用參數化篩選的合併式複寫，發行集指令碼包含對建立資料分割的預存程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="8aa68-111">For merge publications that use parameterized filters, publication scripts contain the stored procedure calls to create data partitions.</span></span> <span data-ttu-id="8aa68-112">指令碼提供所建立資料分割的參考，並提供必要時重新建立一或多個資料分割的方式。</span><span class="sxs-lookup"><span data-stu-id="8aa68-112">The script provides a reference for the partitions created and a way in which to re-create one or more partitions if necessary.</span></span>  
  
## <a name="example-of-automating-a-task-with-scripts"></a><span data-ttu-id="8aa68-113">利用指令碼自動化工作的範例</span><span class="sxs-lookup"><span data-stu-id="8aa68-113">Example of Automating a Task with Scripts</span></span>  
 <span data-ttu-id="8aa68-114">請考慮 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]，它實作合併式複寫以將資料散發到它的遠端銷售團隊。</span><span class="sxs-lookup"><span data-stu-id="8aa68-114">Consider [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], which implements merge replication to distribute data to its remote sales force.</span></span> <span data-ttu-id="8aa68-115">一個銷售代表使用提取訂閱下載與其區域客戶有關的所有資料。</span><span class="sxs-lookup"><span data-stu-id="8aa68-115">A sales representative downloads all the data that pertains to the customers in her territory using pull subscriptions.</span></span> <span data-ttu-id="8aa68-116">離線工作時，該銷售代表可以更新資料並輸入新的客戶與訂單。</span><span class="sxs-lookup"><span data-stu-id="8aa68-116">When working offline, the sales representative updates data and enters new customers and orders.</span></span> <span data-ttu-id="8aa68-117">由於 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 在各地共有 50 位以上的銷售代表，若是利用「新增訂閱精靈」在每個「訂閱者」上建立不同的訂閱，將相當耗時。</span><span class="sxs-lookup"><span data-stu-id="8aa68-117">Because [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] has more than fifty sales representatives in different territories, it would be time-consuming to create the different subscriptions at each Subscriber with the New Subscription Wizard.</span></span> <span data-ttu-id="8aa68-118">反之，複寫管理員可遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8aa68-118">Instead, the replication administrator can follow these steps:</span></span>  
  
1.  <span data-ttu-id="8aa68-119">使用根據銷售代表或其區域所進行之資料分割設定必要的合併式發行集。</span><span class="sxs-lookup"><span data-stu-id="8aa68-119">Set up the necessary merge publications with partitions based on the sales representative or their territory.</span></span>  
  
2.  <span data-ttu-id="8aa68-120">為一個「訂閱者」建立提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="8aa68-120">Create a pull subscription for one Subscriber.</span></span>  
  
3.  <span data-ttu-id="8aa68-121">根據該提取訂閱產生指令碼。</span><span class="sxs-lookup"><span data-stu-id="8aa68-121">Generate a script based on that pull subscription.</span></span>  
  
4.  <span data-ttu-id="8aa68-122">修改指令碼，變更例如「訂閱者」名稱等的值。</span><span class="sxs-lookup"><span data-stu-id="8aa68-122">Modify the script, changing such values as the name of the Subscriber.</span></span>  
  
5.  <span data-ttu-id="8aa68-123">在多個「訂閱者」端執行指令碼以產生需要的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="8aa68-123">Run the script at multiple Subscribers to generate the required pull subscriptions.</span></span>  
  
## <a name="script-replication-objects"></a><span data-ttu-id="8aa68-124">撰寫複寫物件的指令碼</span><span class="sxs-lookup"><span data-stu-id="8aa68-124">Script Replication Objects</span></span>  
 <span data-ttu-id="8aa68-125">您可以從複寫精靈或從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [複寫] 資料夾來撰寫複寫物件指令碼。</span><span class="sxs-lookup"><span data-stu-id="8aa68-125">Script replication objects from the replication wizards or from the **Replication** folder in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="8aa68-126">如果您從精靈編寫指令碼，可以選擇建立物件並編寫其指令碼，也可以選擇只編寫其指令碼。</span><span class="sxs-lookup"><span data-stu-id="8aa68-126">If you script from the wizards, you can choose to create objects and script them, or you can choose only to script them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8aa68-127">所有密碼的指令碼都會編寫為 NULL。</span><span class="sxs-lookup"><span data-stu-id="8aa68-127">All passwords are scripted as NULL.</span></span> <span data-ttu-id="8aa68-128">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="8aa68-128">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="8aa68-129">如果您將認證儲存在指令碼檔案中，必須保護該檔案免於未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="8aa68-129">If you store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="8aa68-130">如需使用複寫精靈的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="8aa68-130">For more information about using the replication wizards, see:</span></span>  
  
-   [<span data-ttu-id="8aa68-131">設定發行和散發</span><span class="sxs-lookup"><span data-stu-id="8aa68-131">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
-   [<span data-ttu-id="8aa68-132">建立發行集</span><span class="sxs-lookup"><span data-stu-id="8aa68-132">Create a Publication</span></span>](publish/create-a-publication.md)  
  
-   [<span data-ttu-id="8aa68-133">建立發送訂閱</span><span class="sxs-lookup"><span data-stu-id="8aa68-133">Create a Push Subscription</span></span>](create-a-push-subscription.md)  
  
-   [<span data-ttu-id="8aa68-134">建立提取訂閱</span><span class="sxs-lookup"><span data-stu-id="8aa68-134">Create a Pull Subscription</span></span>](create-a-pull-subscription.md)  
  
#### <a name="to-script-an-object-from-a-replication-wizard"></a><span data-ttu-id="8aa68-135">若要從複寫精靈編寫物件指令碼</span><span class="sxs-lookup"><span data-stu-id="8aa68-135">To script an object from a replication wizard</span></span>  
  
1.  <span data-ttu-id="8aa68-136">在精靈的 **[精靈動作]** 頁面上，選取適用於精靈的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="8aa68-136">On the **Wizard Actions** page of a wizard, select the check box appropriate for the wizard:</span></span>  
  
    -   <span data-ttu-id="8aa68-137">**產生含有建立發行集步驟的指令碼檔案**</span><span class="sxs-lookup"><span data-stu-id="8aa68-137">**Generate a script file with steps to create a publication**</span></span>  
  
    -   <span data-ttu-id="8aa68-138">**產生含有建立訂閱步驟的指令碼檔案**</span><span class="sxs-lookup"><span data-stu-id="8aa68-138">**Generate a script file with steps to create the subscription(s)**</span></span>  
  
    -   <span data-ttu-id="8aa68-139">**產生含有設定散發步驟的指令碼檔案**</span><span class="sxs-lookup"><span data-stu-id="8aa68-139">**Generate a script file with steps to configure distribution**</span></span>  
  
2.  <span data-ttu-id="8aa68-140">指定 **[指令碼檔案屬性]** 頁面上的選項。</span><span class="sxs-lookup"><span data-stu-id="8aa68-140">Specify options on the **Script File Properties** page.</span></span>  
  
3.  <span data-ttu-id="8aa68-141">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="8aa68-141">Complete the wizard.</span></span>  
  
#### <a name="to-script-an-object-from-management-studio"></a><span data-ttu-id="8aa68-142">若要從 Management Studio 編寫物件指令碼</span><span class="sxs-lookup"><span data-stu-id="8aa68-142">To script an object from Management Studio</span></span>  
  
1.  <span data-ttu-id="8aa68-143">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的散發者、發行者或訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="8aa68-143">Connect to the Distributor, Publisher, or Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="8aa68-144">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾或 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8aa68-144">Expand the **Replication** folder, and then expand the **Local Publications** folder or the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="8aa68-145">以滑鼠右鍵按一下發行集或訂閱，然後按一下 **[產生指令碼]** 。</span><span class="sxs-lookup"><span data-stu-id="8aa68-145">Right-click a publication or subscription, and then click **Generate Scripts**.</span></span>  
  
4.  <span data-ttu-id="8aa68-146">指定 [產生 SQL 指令碼 - \<ReplicationObject>] 對話方塊中的選項。</span><span class="sxs-lookup"><span data-stu-id="8aa68-146">Specify options in the **Generate SQL Script - \<ReplicationObject>** dialog box.</span></span>  
  
5.  <span data-ttu-id="8aa68-147">按一下 **[編寫指令碼至檔案]** 。</span><span class="sxs-lookup"><span data-stu-id="8aa68-147">Click **Script to File**.</span></span>  
  
6.  <span data-ttu-id="8aa68-148">在 **[指令碼檔案位置]** 對話方塊中輸入檔案名稱，然後按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="8aa68-148">Enter a file name in the **Script File Location** dialog box, and then click **Save**.</span></span> <span data-ttu-id="8aa68-149">就會顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="8aa68-149">A status message is displayed.</span></span>  
  
7.  <span data-ttu-id="8aa68-150">按一下 **[確定]** ，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="8aa68-150">Click **OK**, and then click **Close**.</span></span>  
  
#### <a name="to-script-multiple-objects-from-management-studio"></a><span data-ttu-id="8aa68-151">若要從 Management Studio 編寫多個物件的指令碼</span><span class="sxs-lookup"><span data-stu-id="8aa68-151">To script multiple objects from Management Studio</span></span>  
  
1.  <span data-ttu-id="8aa68-152">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的散發者、發行者或訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="8aa68-152">Connect to the Distributor, Publisher, or Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="8aa68-153">以滑鼠右鍵按一下 **[複寫]** 資料夾，然後按一下 **[產生指令碼]** 。</span><span class="sxs-lookup"><span data-stu-id="8aa68-153">Right-click the **Replication** folder, and then click **Generate Scripts**.</span></span>  
  
3.  <span data-ttu-id="8aa68-154">指定 **[產生 SQL 指令碼]** 對話方塊中的選項。</span><span class="sxs-lookup"><span data-stu-id="8aa68-154">Specify options in the **Generate SQL Script** dialog box.</span></span>  
  
4.  <span data-ttu-id="8aa68-155">按一下 **[編寫指令碼至檔案]** 。</span><span class="sxs-lookup"><span data-stu-id="8aa68-155">Click **Script to File**.</span></span>  
  
5.  <span data-ttu-id="8aa68-156">在 **[指令碼檔案位置]** 對話方塊中輸入檔案名稱，然後按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="8aa68-156">Enter a file name in the **Script File Location** dialog box, and then click **Save**.</span></span> <span data-ttu-id="8aa68-157">就會顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="8aa68-157">A status message is displayed.</span></span>  
  
6.  <span data-ttu-id="8aa68-158">按一下 **[確定]** ，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="8aa68-158">Click **OK, and then** click **Close**.</span></span>  
  
  
