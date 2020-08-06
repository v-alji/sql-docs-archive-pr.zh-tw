---
title: 變更 SQL Server (SQL Server 組態管理員) 所使用之帳戶的密碼 |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7da2b5f60187d7e3060dc6616686c493c893c21d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709937"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="bd78a-102">變更 SQL Server 所使用之帳戶的密碼 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="bd78a-102">Change the Password of the Accounts Used by SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="bd78a-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Agent 所使用之帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="bd78a-103">This topic describes how to change the password of the accounts used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="bd78a-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會使用安裝過程中最初提供的認證，在電腦上當做服務執行。</span><span class="sxs-lookup"><span data-stu-id="bd78a-104">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent run on a computer as a service using credentials that are initially provided during setup.</span></span> <span data-ttu-id="bd78a-105">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體在網域帳戶下執行，而且該帳戶的密碼已變更時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所使用的密碼就必須更新為新的密碼。</span><span class="sxs-lookup"><span data-stu-id="bd78a-105">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running under a domain account and the password for that account is changed, the password used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be updated to the new password.</span></span> <span data-ttu-id="bd78a-106">如果沒有更新密碼， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能會喪失某些網域資源的存取權，而且如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 停止，服務就要等到密碼更新後才會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="bd78a-106">If the password is not updated, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may lose access to some domain resources and if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stops, the service will not restart until the password is updated.</span></span>  
  
 <span data-ttu-id="bd78a-107">若要變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的密碼，請參閱 [密碼已過期](../password-expired.md)。</span><span class="sxs-lookup"><span data-stu-id="bd78a-107">To change [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication passwords, see [Password Expired](../password-expired.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bd78a-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="bd78a-108">Before You Begin</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bd78a-109">組態管理員是已獲授權專供變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務各項設定而設計的工具。</span><span class="sxs-lookup"><span data-stu-id="bd78a-109">Configuration Manager is the tool designed and authorized to change the settings of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span> <span data-ttu-id="bd78a-110">使用 Windows 服務控制管理員 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.msc **) 應用程式變更**服務時，不一定能變更所有必要的設定，而且可能導致服務無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="bd78a-110">Changing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service by using the Windows Service Control Manager (**services.msc**) application does not always change all of the necessary settings and might prevent the service from functioning properly.</span></span> <span data-ttu-id="bd78a-111">不過，在叢集環境的使用中節點上透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員變更密碼之後，必須在被動節點上使用服務控制管理員變更密碼。</span><span class="sxs-lookup"><span data-stu-id="bd78a-111">However, in a clustered environment, after changing the password on the active node by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, you must change the password on the passive node by using the Service Control Manager.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bd78a-112">Security</span><span class="sxs-lookup"><span data-stu-id="bd78a-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bd78a-113">權限</span><span class="sxs-lookup"><span data-stu-id="bd78a-113">Permissions</span></span>  
 <span data-ttu-id="bd78a-114">您必須是電腦的系統管理員才能變更服務所使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="bd78a-114">You must be an administrator of the computer to change the password used by a service.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bd78a-115">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="bd78a-115">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a><span data-ttu-id="bd78a-116">變更 SQL Server Agent (Database Engine) 服務所使用的密碼</span><span class="sxs-lookup"><span data-stu-id="bd78a-116">To change the password used by the SQL Server (Database Engine) service</span></span>  
  
1.  <span data-ttu-id="bd78a-117">按一下 **[開始]** 按鈕，然後依序指向 **[所有程式]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="bd78a-117">Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd78a-118">因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理主控台程式的嵌入式管理單元，而不是獨立的程式，所以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員在較新版本的 Windows 中不會作為應用程式出現。</span><span class="sxs-lookup"><span data-stu-id="bd78a-118">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="bd78a-119">**Windows 10**：</span><span class="sxs-lookup"><span data-stu-id="bd78a-119">**Windows 10**:</span></span>  
    >          <span data-ttu-id="bd78a-120">若要開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，請在 [**開始] 頁面**上，輸入適用于) 的 sqlservermanager12.msc (。 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd78a-120">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="bd78a-121">針對先前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，以較小的數字取代 12。</span><span class="sxs-lookup"><span data-stu-id="bd78a-121">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="bd78a-122">按一下 SQLServerManager12.msc 即可開啟 Configuration Manager。</span><span class="sxs-lookup"><span data-stu-id="bd78a-122">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="bd78a-123">若要將 Configuration Manager 釘選到起始頁或工作列，請在 [Sqlservermanager12.msc] 上按一下滑鼠右鍵，然後按一下 [**開啟檔案位置**]。</span><span class="sxs-lookup"><span data-stu-id="bd78a-123">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="bd78a-124">在 Windows 檔案瀏覽器中，以滑鼠右鍵按一下 [Sqlservermanager12.msc]，然後按一下 [**釘選到開始**] 或 [**釘選到工作列**]。</span><span class="sxs-lookup"><span data-stu-id="bd78a-124">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="bd78a-125">**Windows 8**：</span><span class="sxs-lookup"><span data-stu-id="bd78a-125">**Windows 8**:</span></span>  
    >          <span data-ttu-id="bd78a-126">若要開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，請在 [**搜尋**] 快速鍵的 [**應用程式**] 底下，輸入**SQLServerManager \<version> \*\* （例如 `SQLServerManager12.msc` ），然後按**enter\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd78a-126">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="bd78a-127">在 [SQL Server 組態管理員] 中，按一下 **[SQL Server 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="bd78a-127">In SQL Server Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="bd78a-128">在詳細資料窗格中，以滑鼠右鍵按一下 [SQL Server (\<instancename>)]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="bd78a-128">In the details pane, right-click **SQL Server (**\<instancename>**)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="bd78a-129">在 [SQL Server (\<instancename>) 屬性] 對話方塊的 [登入] 索引標籤上，針對列於 [帳戶名稱] 方塊的帳戶，在 [密碼] 和 [確認密碼] 方塊中輸入新密碼，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="bd78a-129">In the **SQL Server (**\<instancename>**) Properties** dialog box, on the Log On tab, for the account listed in the **Account Name** box, type the new password in the **Password** and **Confirm Password** boxes, and then click **OK**.</span></span>  
  
     <span data-ttu-id="bd78a-130">密碼會立即生效，不需重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bd78a-130">The password takes effect immediately, without restarting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a><span data-ttu-id="bd78a-131">變更 SQL Server Agent 服務所使用的密碼</span><span class="sxs-lookup"><span data-stu-id="bd78a-131">To change the password used by the SQL Server Agent service</span></span>  
  
1.  <span data-ttu-id="bd78a-132">按一下 **[開始]** 按鈕，然後依序指向 **[所有程式]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="bd78a-132">Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="bd78a-133">在 [SQL Server 組態管理員] 中，按一下 **[SQL Server 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="bd78a-133">In SQL Server Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="bd78a-134">在詳細資料窗格中，以滑鼠右鍵按一下 [SQL Server Agent (\<instancename>)]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="bd78a-134">In the details pane, right-click **SQL Server Agent (**\<instancename>**)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="bd78a-135">在 [SQL Server Agent (\<instancename>) 屬性] 對話方塊的 [登入] 索引標籤上，針對列於 [帳戶名稱] 方塊的帳戶，在 [密碼] 和 [確認密碼] 方塊中輸入新密碼，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="bd78a-135">In the **SQL Server Agent (**\<instancename>**) Properties** dialog box, on the Log On tab, for the account listed in the **Account Name** box, type the new password in the **Password** and **Confirm Password** boxes, and then click **OK**.</span></span>  
  
     <span data-ttu-id="bd78a-136">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]獨立執行個體上，密碼會立即生效，不需要重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bd78a-136">On a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the password takes effect immediately, without restarting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bd78a-137">在叢集執行個體上， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能會讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源離線，而且需要重新啟動。</span><span class="sxs-lookup"><span data-stu-id="bd78a-137">On a clustered instance, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might take the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource offline, and require a restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd78a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd78a-138">See Also</span></span>  
 [<span data-ttu-id="bd78a-139">管理服務的如何主題 &#40;SQL Server 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="bd78a-139">Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;</span></span>](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  
