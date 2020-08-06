---
title: 設定伺服器啟動選項 (SQL Server 組態管理員) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 405a96208c774a6326a69cf9826a14ca3552eae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688198"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a><span data-ttu-id="3a848-102">設定伺服器啟動選項 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="3a848-102">Configure Server Startup Options (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="3a848-103">本主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，設定每次 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 於 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中啟動時要使用的啟動選項。</span><span class="sxs-lookup"><span data-stu-id="3a848-103">This topic describes how to configure startup options that will be used every time the [!INCLUDE[ssDE](../../includes/ssde-md.md)] starts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="3a848-104">如需啟動選項的清單，請參閱 [Database Engine 服務啟動選項](database-engine-service-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="3a848-104">For a list of startup options, see [Database Engine Service Startup Options](database-engine-service-startup-options.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3a848-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="3a848-105">Before You Begin</span></span>  
  
### <a name="limitations-and-restrictions"></a><span data-ttu-id="3a848-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="3a848-106">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3a848-107">組態管理員會將啟動參數寫入登錄中。</span><span class="sxs-lookup"><span data-stu-id="3a848-107">Configuration Manager writes startup parameters to the registry.</span></span> <span data-ttu-id="3a848-108">下次啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)]時，這些參數就會生效。</span><span class="sxs-lookup"><span data-stu-id="3a848-108">They take effect upon the next startup of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="3a848-109">在叢集中，您必須在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上線時在使用中伺服器上進行變更；當 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 重新啟動時，這些變更就會生效。</span><span class="sxs-lookup"><span data-stu-id="3a848-109">On a cluster, changes must be made on the active server when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is online, and will take effect when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is restarted.</span></span> <span data-ttu-id="3a848-110">下次容錯移轉時則會在另一個節點上進行啟動選項的登錄更新。</span><span class="sxs-lookup"><span data-stu-id="3a848-110">The registry update of the startup options on the other node will occur upon the next failover.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3a848-111">Security</span><span class="sxs-lookup"><span data-stu-id="3a848-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3a848-112">權限</span><span class="sxs-lookup"><span data-stu-id="3a848-112">Permissions</span></span>  
 <span data-ttu-id="3a848-113">設定伺服器啟動選項僅限於能夠在登錄中變更相關項目的使用者，</span><span class="sxs-lookup"><span data-stu-id="3a848-113">Configuring server startup options is restricted to users who can change the related entries in the registry.</span></span> <span data-ttu-id="3a848-114">包括下列使用者。</span><span class="sxs-lookup"><span data-stu-id="3a848-114">This includes the following users.</span></span>  
  
-   <span data-ttu-id="3a848-115">本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="3a848-115">Members of the local administrators group.</span></span>  
  
-   <span data-ttu-id="3a848-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的網域帳戶 (如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 設定為使用網域帳戶來執行的話)。</span><span class="sxs-lookup"><span data-stu-id="3a848-116">The domain account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to run under a domain account.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3a848-117">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="3a848-117">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-configure-startup-options"></a><span data-ttu-id="3a848-118">若要設定啟動選項</span><span class="sxs-lookup"><span data-stu-id="3a848-118">To configure startup options</span></span>  
  
1.  <span data-ttu-id="3a848-119">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，按一下 **[SQL Server 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="3a848-119">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click **SQL Server Services**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3a848-120">因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理主控台程式的嵌入式管理單元，而不是獨立的程式，所以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員在較新版本的 Windows 中不會作為應用程式出現。</span><span class="sxs-lookup"><span data-stu-id="3a848-120">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="3a848-121">**Windows 10**：</span><span class="sxs-lookup"><span data-stu-id="3a848-121">**Windows 10**:</span></span>  
    >          <span data-ttu-id="3a848-122">若要開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，請在 [**開始] 頁面**上，輸入適用于) 的 sqlservermanager12.msc (。 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a848-122">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="3a848-123">針對先前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，以較小的數字取代 12。</span><span class="sxs-lookup"><span data-stu-id="3a848-123">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="3a848-124">按一下 SQLServerManager12.msc 即可開啟 Configuration Manager。</span><span class="sxs-lookup"><span data-stu-id="3a848-124">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="3a848-125">若要將 Configuration Manager 釘選到起始頁或工作列，請在 [Sqlservermanager12.msc] 上按一下滑鼠右鍵，然後按一下 [**開啟檔案位置**]。</span><span class="sxs-lookup"><span data-stu-id="3a848-125">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="3a848-126">在 Windows 檔案瀏覽器中，以滑鼠右鍵按一下 [Sqlservermanager12.msc]，然後按一下 [**釘選到開始**] 或 [**釘選到工作列**]。</span><span class="sxs-lookup"><span data-stu-id="3a848-126">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="3a848-127">**Windows 8**：</span><span class="sxs-lookup"><span data-stu-id="3a848-127">**Windows 8**:</span></span>  
    >          <span data-ttu-id="3a848-128">若要開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，請在 [**搜尋**] 快速鍵的 [**應用程式**] 底下，輸入**SQLServerManager \<version> \*\* （例如 `SQLServerManager12.msc` ），然後按**enter\*\*。</span><span class="sxs-lookup"><span data-stu-id="3a848-128">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="3a848-129">在右窗格中，以滑鼠右鍵按一下 [ **SQL Server (***<instance_name>***) **]，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="3a848-129">In the right pane, right-click **SQL Server (***<instance_name>***)**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3a848-130">在 **[啟動參數]** 索引標籤的 **[指定啟動參數]** 方塊中輸入參數，然後按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="3a848-130">On the **Startup Parameters** tab, in the **Specify a startup parameter** box, type the parameter, and then click **Add**.</span></span>  
  
     <span data-ttu-id="3a848-131">例如，若要在單一使用者模式中啟動，請 `-m` 在 [**指定啟動參數**] 方塊中輸入，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="3a848-131">For example, to start in single-user mode, type `-m` in the **Specify a startup parameter** box and then click **Add**.</span></span> <span data-ttu-id="3a848-132">(當您以單一使用者模式重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，請先停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="3a848-132">(When you restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="3a848-133">否則， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 可能會先進行連接，您就無法以另一個使用者的身分進行連接)。</span><span class="sxs-lookup"><span data-stu-id="3a848-133">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent might connect first and prevent you from connecting as a second user.)</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="3a848-134">重新啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3a848-134">Restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="3a848-135">當您完成使用單一使用者模式之後，請在 [啟動參數] 方塊的 `-m` [**現有參數**] 方塊中選取參數，然後按一下 [**移除**]。</span><span class="sxs-lookup"><span data-stu-id="3a848-135">After you are finished using single-user mode, in the Startup Parameters box, select the `-m` parameter in the **Existing Parameters** box, and then click **Remove**.</span></span> <span data-ttu-id="3a848-136">重新啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 還原為一般多使用者模式。</span><span class="sxs-lookup"><span data-stu-id="3a848-136">Restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to restore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the typical multi-user mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a848-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a848-137">See Also</span></span>  
 <span data-ttu-id="3a848-138">[以單一使用者模式啟動 SQL Server](start-sql-server-in-single-user-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3a848-138">[Start SQL Server in Single-User Mode](start-sql-server-in-single-user-mode.md) </span></span>  
 <span data-ttu-id="3a848-139">[當系統管理員遭到鎖定時連接到 SQL Server](connect-to-sql-server-when-system-administrators-are-locked-out.md) </span><span class="sxs-lookup"><span data-stu-id="3a848-139">[Connect to SQL Server When System Administrators Are Locked Out](connect-to-sql-server-when-system-administrators-are-locked-out.md) </span></span>  
 [<span data-ttu-id="3a848-140">啟動、停止或暫停 SQL Server Agent 服務</span><span class="sxs-lookup"><span data-stu-id="3a848-140">Start, Stop, or Pause the SQL Server Agent Service</span></span>](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
