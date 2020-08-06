---
title: 從複寫監視器新增及移除發行者 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, adding and removing Publishers
ms.assetid: fa36c4b4-bfa5-494e-92e3-07a02d7332c3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 16c2876b55541e347e4e638132f36ad33932abb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709201"
---
# <a name="add-and-remove-publishers-from-replication-monitor"></a><span data-ttu-id="63fae-102">從複寫監視器加入及移除發行者</span><span class="sxs-lookup"><span data-stu-id="63fae-102">Add and Remove Publishers from Replication Monitor</span></span>
  <span data-ttu-id="63fae-103">從中啟動「複寫監視器」的伺服器會自動新增至監視器 (如果它是「發行者」)。</span><span class="sxs-lookup"><span data-stu-id="63fae-103">The server from which you launch Replication Monitor is automatically added to the monitor if it is a Publisher.</span></span> <span data-ttu-id="63fae-104">其他「發行者」可透過 **[加入發行者]** 對話方塊來新增。</span><span class="sxs-lookup"><span data-stu-id="63fae-104">Additional Publishers can be added through the **Add Publisher** dialog box.</span></span> <span data-ttu-id="63fae-105">在新增「發行者」之後，它會顯示在監視器左窗格的群組中。</span><span class="sxs-lookup"><span data-stu-id="63fae-105">After adding a Publisher, it is displayed in a group in the left pane of the monitor.</span></span> <span data-ttu-id="63fae-106">依預設會包括 **[我的發行者]** 群組，但您可以建立新的群組來管理一個或多個複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="63fae-106">The **My Publishers** group is included by default, but you can create new groups to manage one or more replication topologies.</span></span> <span data-ttu-id="63fae-107">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="63fae-107">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
### <a name="to-add-a-sql-server-publisher"></a><span data-ttu-id="63fae-108">若要新增 SQL Server 發行者</span><span class="sxs-lookup"><span data-stu-id="63fae-108">To add a SQL Server Publisher</span></span>  
  
1.  <span data-ttu-id="63fae-109">以滑鼠右鍵按一下左窗格裡的 **[複寫監視器]** 節點或發行者群組節點，然後按一下 **[加入發行者]**。</span><span class="sxs-lookup"><span data-stu-id="63fae-109">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="63fae-110">在 **[加入發行者]** 對話方塊中，按一下 **[加入]**，然後按一下 **[加入 SQL Server 發行者]**。</span><span class="sxs-lookup"><span data-stu-id="63fae-110">In the **Add Publisher** dialog box, click **Add**, and then click **Add SQL Server Publisher**.</span></span>  
  
3.  <span data-ttu-id="63fae-111">在 **[連接到伺服器]** 對話方塊中，輸入「發行者」的名稱，然後選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="63fae-111">In the **Connect to Server** dialog box, enter the name of the Publisher, and then select the authentication type.</span></span> <span data-ttu-id="63fae-112">如果您選取 **[SQL Server 驗證]**，請輸入登入與密碼。</span><span class="sxs-lookup"><span data-stu-id="63fae-112">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="63fae-113">複寫監視器會儲存您指定的認證，在未來連接到這個伺服器時使用。</span><span class="sxs-lookup"><span data-stu-id="63fae-113">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="63fae-114">指定的 Windows 帳戶或 SQL Server 登入必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，或者散發資料庫中 **replmonitor** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="63fae-114">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="63fae-115">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="63fae-115">Click **Connect**.</span></span> <span data-ttu-id="63fae-116">如果「發行者」使用遠端「散發者」，將會提示您在 **[連接到伺服器]** 對話方塊中連接到「散發者」。</span><span class="sxs-lookup"><span data-stu-id="63fae-116">If the Publisher uses a remote Distributor, you will be prompted to connect to the Distributor in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="63fae-117">複寫監視器會儲存您指定的認證，在未來連接到這個伺服器時使用。</span><span class="sxs-lookup"><span data-stu-id="63fae-117">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="63fae-118">指定的 Windows 帳戶或 SQL Server 登入必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，或者散發資料庫中 **replmonitor** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="63fae-118">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
5.  <span data-ttu-id="63fae-119">發行者與散發者的名稱會在 **[開始監視下列發行者]** 方格中顯示。</span><span class="sxs-lookup"><span data-stu-id="63fae-119">The name of the Publisher and Distributor are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span>  
  
6.  <span data-ttu-id="63fae-120">若要指定發行者的重新整理與連接選項，請從方格中選取發行者，然後依需要修改選項。</span><span class="sxs-lookup"><span data-stu-id="63fae-120">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="63fae-121">如需有關重新整理選項的詳細資訊，請參閱＜ [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)＞。</span><span class="sxs-lookup"><span data-stu-id="63fae-121">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="63fae-122">選取發行者應在複寫監視器中顯示的群組。</span><span class="sxs-lookup"><span data-stu-id="63fae-122">Select the group under which the Publisher should be displayed in Replication Monitor.</span></span> <span data-ttu-id="63fae-123">若要建立新群組，請按一下 **[新增群組]**，然後輸入群組名稱；從 **[在下列群組中顯示此發行者]** 清單裡選取群組。</span><span class="sxs-lookup"><span data-stu-id="63fae-123">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-add-an-oracle-publisher"></a><span data-ttu-id="63fae-124">若要新增 Oracle 發行者</span><span class="sxs-lookup"><span data-stu-id="63fae-124">To add an Oracle Publisher</span></span>  
  
1.  <span data-ttu-id="63fae-125">以滑鼠右鍵按一下左窗格裡的 **[複寫監視器]** 節點或發行者群組節點，然後按一下 **[加入發行者]**。</span><span class="sxs-lookup"><span data-stu-id="63fae-125">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="63fae-126">在 **[加入發行者]** 對話方塊中，按一下 **[加入]**，然後按一下 **[加入 Oracle 發行者]**。</span><span class="sxs-lookup"><span data-stu-id="63fae-126">In the **Add Publisher** dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span>  
  
3.  <span data-ttu-id="63fae-127">在 [連接到伺服器]\*\*\*\* 對話方塊中，輸入與「Oracle 發行者」關聯的「[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」的名稱，然後選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="63fae-127">In the **Connect to Server** dialog box, enter the name of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor associated with the Oracle Publisher, and then select the authentication type.</span></span> <span data-ttu-id="63fae-128">如果您選取 **[SQL Server 驗證]**，請輸入登入與密碼。</span><span class="sxs-lookup"><span data-stu-id="63fae-128">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="63fae-129">複寫監視器會儲存您指定的認證，在未來連接到這個伺服器時使用。</span><span class="sxs-lookup"><span data-stu-id="63fae-129">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="63fae-130">指定的 Windows 帳戶或 SQL Server 登入必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，或者散發資料庫中 **replmonitor** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="63fae-130">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="63fae-131">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="63fae-131">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="63fae-132">發行者與散發者的名稱會在 **[開始監視下列發行者]** 方格中顯示。</span><span class="sxs-lookup"><span data-stu-id="63fae-132">The name of the Publisher and Distributor are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span>  
  
6.  <span data-ttu-id="63fae-133">若要指定發行者的重新整理與連接選項，請從方格中選取發行者，然後依需要修改選項。</span><span class="sxs-lookup"><span data-stu-id="63fae-133">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="63fae-134">如需有關重新整理選項的詳細資訊，請參閱＜ [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)＞。</span><span class="sxs-lookup"><span data-stu-id="63fae-134">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="63fae-135">選取發行者應在複寫監視器中顯示的群組。</span><span class="sxs-lookup"><span data-stu-id="63fae-135">Select the group under which the Publisher should be displayed in Replication Monitor.</span></span> <span data-ttu-id="63fae-136">若要建立新群組，請按一下 **[新增群組]**，然後輸入群組名稱；從 **[在下列群組中顯示此發行者]** 清單裡選取群組。</span><span class="sxs-lookup"><span data-stu-id="63fae-136">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-add-one-or-more-publishers-that-use-the-same-distributor"></a><span data-ttu-id="63fae-137">若要新增一個或多個使用相同散發者的發行者</span><span class="sxs-lookup"><span data-stu-id="63fae-137">To add one or more Publishers that use the same Distributor</span></span>  
  
1.  <span data-ttu-id="63fae-138">以滑鼠右鍵按一下左窗格裡的 **[複寫監視器]** 節點或發行者群組節點，然後按一下 **[加入發行者]**。</span><span class="sxs-lookup"><span data-stu-id="63fae-138">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="63fae-139">在 **[加入發行者]** 對話方塊中，按一下 **[加入]**，然後按一下 **[指定散發者，並加入其發行者]**。</span><span class="sxs-lookup"><span data-stu-id="63fae-139">In the **Add Publisher** dialog box, click **Add**, and then click **Specify a Distributor and Add Its Publishers**.</span></span>  
  
3.  <span data-ttu-id="63fae-140">在 **[連接到伺服器]** 對話方塊中，輸入「散發者」的名稱，然後選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="63fae-140">In the **Connect to Server** dialog box, enter the name of the Distributor, and then select the authentication type.</span></span> <span data-ttu-id="63fae-141">如果您選取 **[SQL Server 驗證]**，請輸入登入與密碼。</span><span class="sxs-lookup"><span data-stu-id="63fae-141">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="63fae-142">複寫監視器會儲存您指定的認證，在未來連接到這個伺服器時使用。</span><span class="sxs-lookup"><span data-stu-id="63fae-142">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="63fae-143">指定的 Windows 帳戶或 SQL Server 登入必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，或者散發資料庫中 **replmonitor** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="63fae-143">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="63fae-144">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="63fae-144">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="63fae-145">「散發者」與每個「發行者」的名稱顯示在 **[開始監視下列發行者]** 方格中。</span><span class="sxs-lookup"><span data-stu-id="63fae-145">The name of the Distributor and each Publisher are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span> <span data-ttu-id="63fae-146">如果「發行者」已新增至「複寫監視器」，則不會顯示在方格中。</span><span class="sxs-lookup"><span data-stu-id="63fae-146">If a Publisher has already been added to Replication Monitor, it does not appear in the grid.</span></span>  
  
6.  <span data-ttu-id="63fae-147">若要指定發行者的重新整理與連接選項，請從方格中選取發行者，然後依需要修改選項。</span><span class="sxs-lookup"><span data-stu-id="63fae-147">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="63fae-148">如需有關重新整理選項的詳細資訊，請參閱＜ [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)＞。</span><span class="sxs-lookup"><span data-stu-id="63fae-148">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="63fae-149">選取在「複寫監視器」中應顯示「發行者」的群組。</span><span class="sxs-lookup"><span data-stu-id="63fae-149">Select the group under which Publishers should be displayed in Replication Monitor.</span></span> <span data-ttu-id="63fae-150">若要建立新群組，請按一下 **[新增群組]**，然後輸入群組名稱；從 **[在下列群組中顯示此發行者]** 清單裡選取群組。</span><span class="sxs-lookup"><span data-stu-id="63fae-150">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-modify-settings-for-the-publisher-and-publisher-groups"></a><span data-ttu-id="63fae-151">若要修改發行者與發行者群組的設定</span><span class="sxs-lookup"><span data-stu-id="63fae-151">To modify settings for the Publisher and Publisher Groups</span></span>  
  
1.  <span data-ttu-id="63fae-152">以滑鼠右鍵按一下左窗格中的「發行者」，然後按一下 **[發行者設定]**。</span><span class="sxs-lookup"><span data-stu-id="63fae-152">Right-click a Publisher in the left pane, and then click **Publisher Settings**.</span></span>  
  
2.  <span data-ttu-id="63fae-153">在 **[發行者設定]** 對話方塊中進行任何變更：</span><span class="sxs-lookup"><span data-stu-id="63fae-153">Make any changes in the **Publisher Settings** dialog box:</span></span>  
  
    -   <span data-ttu-id="63fae-154">若要變更「複寫監視器」用來連接到伺服器的認證，請按一下 **[發行者連接]** 或 **[散發者連接]**，然後在 **[連接到伺服器]** 對話方塊中輸入認證。</span><span class="sxs-lookup"><span data-stu-id="63fae-154">To change the credentials that Replication Monitor uses to connect to a server, click **Publisher Connection** or **Distributor Connection**, and then enter credentials in the **Connect to Server** dialog box.</span></span>  
  
    -   <span data-ttu-id="63fae-155">若要將某「發行者」從一個群組移至另一個群組，請在 **[開始監視下列發行者]** 方格中選取該「發行者」，然後在 **[在下列群組中顯示此發行者]** 清單中選取新群組。</span><span class="sxs-lookup"><span data-stu-id="63fae-155">To move a Publisher from one group to another, select the Publisher in the **Start monitoring the following Publisher(s)** grid, and then select the new group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-publisher-from-replication-monitor"></a><span data-ttu-id="63fae-156">若要從複寫監視器移除發行者</span><span class="sxs-lookup"><span data-stu-id="63fae-156">To remove a Publisher from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="63fae-157">以滑鼠右鍵按一下左窗格中的「發行者」：</span><span class="sxs-lookup"><span data-stu-id="63fae-157">Right-click a Publisher in the left pane.</span></span>  
  
2.  <span data-ttu-id="63fae-158">按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="63fae-158">Click **Remove**.</span></span>  
  
### <a name="to-add-a-publisher-group-to-replication-monitor"></a><span data-ttu-id="63fae-159">若要新增發行者群組至複寫監視器</span><span class="sxs-lookup"><span data-stu-id="63fae-159">To add a Publisher group to Replication Monitor</span></span>  
  
1.  <span data-ttu-id="63fae-160">發行者群組僅在新增「發行者」或修改「發行者」的設定時才可建立。</span><span class="sxs-lookup"><span data-stu-id="63fae-160">Publisher groups can be created only when adding a Publisher or modifying settings for a Publisher.</span></span> <span data-ttu-id="63fae-161">請參閱新增「發行者」的「如何」程序，以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="63fae-161">See the how to procedures on adding a Publisher for more information.</span></span>  
  
### <a name="to-remove-a-publisher-group-from-replication-monitor"></a><span data-ttu-id="63fae-162">若要從複寫監視器移除發行者群組</span><span class="sxs-lookup"><span data-stu-id="63fae-162">To remove a Publisher group from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="63fae-163">將所有「發行者」移至另一個群組或從「複寫監視器」移除它們。</span><span class="sxs-lookup"><span data-stu-id="63fae-163">Move all Publishers to a different group or remove them from Replication Monitor.</span></span> <span data-ttu-id="63fae-164">如需詳細資訊，請參閱本主題前文中的程序。</span><span class="sxs-lookup"><span data-stu-id="63fae-164">For more information, see previous procedures in this topic.</span></span>  
  
2.  <span data-ttu-id="63fae-165">以滑鼠右鍵按一下「發行者」群組，然後按一下 **[移除]**。</span><span class="sxs-lookup"><span data-stu-id="63fae-165">Right-click the Publisher group, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63fae-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63fae-166">See Also</span></span>  
 <span data-ttu-id="63fae-167">[[設定散發]](../configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="63fae-167">[Configure Distribution](../configure-distribution.md) </span></span>  
 [<span data-ttu-id="63fae-168">監視複寫</span><span class="sxs-lookup"><span data-stu-id="63fae-168">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
