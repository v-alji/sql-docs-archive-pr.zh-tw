---
title: 第 3 課：設定散發 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 52b284b6186e599b7afe73bd37ab0a8348ec38da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707377"
---
# <a name="lesson-3-configuring-distribution"></a><span data-ttu-id="58716-102">第 3 課：設定散發</span><span class="sxs-lookup"><span data-stu-id="58716-102">Lesson 3: Configuring Distribution</span></span>
  <span data-ttu-id="58716-103">在這一課，您將在「發行集」端設定散發，並在發行集和散發資料庫上設定所需權限。</span><span class="sxs-lookup"><span data-stu-id="58716-103">In this lesson, you will configure distribution at the Publisher and set the required permissions on the publication and distribution databases.</span></span> <span data-ttu-id="58716-104">如果您已經設定「散發者」，則必須先停用發行和散發，再開始進行本課。</span><span class="sxs-lookup"><span data-stu-id="58716-104">If you have already configured the Distributor, you must first disable publishing and distribution before you begin this lesson.</span></span> <span data-ttu-id="58716-105">如果您必須保留現有的複寫拓撲，請勿執行上述動作。</span><span class="sxs-lookup"><span data-stu-id="58716-105">Do not do this if you must retain an existing replication topology.</span></span>  
  
 <span data-ttu-id="58716-106">利用遠端「散發者」設定「發行者」已超出本教學課程的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="58716-106">Configuring a Publisher with a remote Distributor is outside the scope of this tutorial.</span></span>  
  
### <a name="configuring-distribution-at-the-publisher"></a><span data-ttu-id="58716-107">在發行者端設定散發</span><span class="sxs-lookup"><span data-stu-id="58716-107">Configuring distribution at the Publisher</span></span>  
  
1.  <span data-ttu-id="58716-108">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="58716-108">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="58716-109">以滑鼠右鍵按一下 [複寫]\*\*\*\* 資料夾，然後按一下 [設定散發]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="58716-109">Right-click the **Replication** folder and click **Configure Distribution**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58716-110">如果您是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] localhost **而非實際伺服器名稱連接到** ，系統會以警告提示您 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法連接到伺服器 **'localhost'**。</span><span class="sxs-lookup"><span data-stu-id="58716-110">If you have connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using **localhost** rather than the actual server name you will be prompted with a warning that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is unable to connect to server **'localhost'**.</span></span> <span data-ttu-id="58716-111">在警告對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="58716-111">Click **OK** on the warning dialog.</span></span> <span data-ttu-id="58716-112">在 [連接到伺服器]\*\*\*\* 對話方塊中，將 [伺服器名稱]\*\*\*\* 從 **localhost** 變更為伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="58716-112">In the **Connect to Server** dialog change the **Server name** from **localhost** to the name of your server.</span></span> <span data-ttu-id="58716-113">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="58716-113">Click **Connect**.</span></span>  
  
     <span data-ttu-id="58716-114">[散發組態精靈] 隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="58716-114">The Distribution Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="58716-115">在 [**散發**者] 頁面上 **，選取 ['** _\<ServerName>_ **' 將扮演自己的散發者;SQL Server 將建立散發資料庫和記錄**檔，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="58716-115">On the **Distributor** page, select **'**_\<ServerName>_**' will act as its own Distributor; SQL Server will create a distribution database and log**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="58716-116">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未執行，請在 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 啟動]\*\*\*\* 頁面上選取 [是]\*\*\*\*，將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務設定為自動啟動。</span><span class="sxs-lookup"><span data-stu-id="58716-116">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running, on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Agent Start** page, select **Yes**, configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to start automatically.</span></span> <span data-ttu-id="58716-117">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="58716-117">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="58716-118">在 **\\\\** \<_Machine_Name> [**快照集資料夾**] 文字方塊中輸入 _**\repldata** ，其中 \<*Machine_Name> \* 是發行者的名稱，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="58716-118">Enter **\\\\**\<_Machine_Name>_**\repldata** in the **Snapshot folder** text box, where \<*Machine_Name>\* is the name of the Publisher, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="58716-119">接受精靈其餘頁面上的預設值。</span><span class="sxs-lookup"><span data-stu-id="58716-119">Accept the default values on the remaining pages of the wizard.</span></span>  
  
7.  <span data-ttu-id="58716-120">按一下 [完成]\*\*\*\*，以啟用散發。</span><span class="sxs-lookup"><span data-stu-id="58716-120">Click **Finish** to enable distribution.</span></span>  
  
### <a name="setting-database-permissions-at-the-publisher"></a><span data-ttu-id="58716-121">在發行者端設定資料庫權限</span><span class="sxs-lookup"><span data-stu-id="58716-121">Setting database permissions at the Publisher</span></span>  
  
1.  <span data-ttu-id="58716-122">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，展開 [**安全性**]， **Logins**以滑鼠右鍵按一下 [登入]，然後選取 **[新增登**入]。</span><span class="sxs-lookup"><span data-stu-id="58716-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Security**, right-click **Logins**, and then select **New Login**.</span></span>  
  
2.  <span data-ttu-id="58716-123">在 [**一般**] 頁面上，按一下 [**搜尋**]， \<_Machine_Name> 在 [**輸入要選取的物件名稱**] 方塊中輸入 _**\ repl_snapshot** ，其中 \<*Machine_Name> \* 是本機發行者伺服器的名稱，按一下 [**檢查名稱**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="58716-123">On the **General** page, click **Search**, enter \<_Machine_Name>_**\repl_snapshot** in the **Enter the object name to select** box, where \<*Machine_Name>\* is the name of the local Publisher server, click **Check Names**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="58716-124">在 [**使用者對應**] 頁面的 [**對應到此登**入的使用者] 清單中，選取 [**散發**] 和 [ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫]。</span><span class="sxs-lookup"><span data-stu-id="58716-124">On the **User Mapping** page, in the **Users mapped to this login** list select both the **distribution** and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] databases.</span></span>  
  
     <span data-ttu-id="58716-125">在 [**資料庫角色成員資格**] 清單中，選取 `db_owner` 兩個資料庫的登入角色。</span><span class="sxs-lookup"><span data-stu-id="58716-125">In the **Database role membership** list select the `db_owner` role for the login for both databases.</span></span>  
  
4.  <span data-ttu-id="58716-126">按一下 [確定]\*\*\*\*，以建立登入。</span><span class="sxs-lookup"><span data-stu-id="58716-126">Click **OK** to create the login.</span></span>  
  
5.  <span data-ttu-id="58716-127">重複執行步驟 1-4，以建立本機 repl_logreader 帳戶的登入。</span><span class="sxs-lookup"><span data-stu-id="58716-127">Repeat steps 1-4 to create a login for the local repl_logreader account.</span></span> <span data-ttu-id="58716-128">此登入也必須對應至 `db_owner` **散發**和**AdventureWorks**資料庫中固定資料庫角色成員的使用者。</span><span class="sxs-lookup"><span data-stu-id="58716-128">This login must also be mapped to users that are members of the `db_owner` fixed database role in the **distribution** and **AdventureWorks** databases.</span></span>  
  
6.  <span data-ttu-id="58716-129">重複執行步驟 1-4，以建立本機 repl_distribution 帳戶的登入。</span><span class="sxs-lookup"><span data-stu-id="58716-129">Repeat steps 1-4 to create a login for the local repl_distribution account.</span></span> <span data-ttu-id="58716-130">此登入必須對應到屬於 `db_owner` **散發**資料庫中固定資料庫角色成員的使用者。</span><span class="sxs-lookup"><span data-stu-id="58716-130">This login must be mapped to a user that is a member of the `db_owner` fixed database role in the **distribution** database.</span></span>  
  
7.  <span data-ttu-id="58716-131">重複執行步驟 1-4，以建立本機 repl_merge 帳戶的登入。</span><span class="sxs-lookup"><span data-stu-id="58716-131">Repeat steps 1-4 to create a login for the local repl_merge account.</span></span> <span data-ttu-id="58716-132">此登入必須在 **distribution** 和 **AdventureWorks** 資料庫中有使用者對應。</span><span class="sxs-lookup"><span data-stu-id="58716-132">This login must have user mappings in the **distribution** and **AdventureWorks** databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58716-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58716-133">See Also</span></span>  
 <span data-ttu-id="58716-134">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="58716-134">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="58716-135">複寫代理程式安全性模型</span><span class="sxs-lookup"><span data-stu-id="58716-135">Replication Agent Security Model</span></span>](security/replication-agent-security-model.md)  
  
  
