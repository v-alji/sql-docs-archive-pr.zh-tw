---
title: 檢視離線記錄檔 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, viewing offline logs
- offline log files
ms.assetid: 9223e474-f224-4907-a4f2-081e11db58f5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2afc1992b54c78f69bfae1fc152b41c20bcd4ea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598368"
---
# <a name="view-offline-log-files"></a><span data-ttu-id="0a438-102">檢視離線記錄檔</span><span class="sxs-lookup"><span data-stu-id="0a438-102">View Offline Log Files</span></span>
  <span data-ttu-id="0a438-103">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]開始，當目標執行個體已離線或無法啟動時，您就可以從本機或遠端 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0a438-103">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when the target instance is offline or cannot start.</span></span>  
  
 <span data-ttu-id="0a438-104">您可以從 [已註冊的伺服器] 存取離線記錄檔，也可以透過 WMI 和 WQL (WMI 查詢語言) 查詢以程式設計方式存取。</span><span class="sxs-lookup"><span data-stu-id="0a438-104">You can access the offline log files from Registered Servers, or programmatically through WMI and WQL (WMI Query Language) queries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a438-105">此外，您還可以使用這些方法來連接至已離線，但由於某些原因而無法透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接進行連接的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a438-105">You can also use these methods to connect to an instance that is online, but for some reason, you cannot connect through a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="0a438-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="0a438-106">Before you Begin</span></span>  
 <span data-ttu-id="0a438-107">若要連接至離線記錄檔， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須安裝在您用來檢視離線記錄檔的電腦上以及您想要檢視之記錄檔所在的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0a438-107">To connect to offline log files, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be installed on the computer that you are using to view the offline log files, and on the computer where the log files that you want to view are located.</span></span> <span data-ttu-id="0a438-108">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體安裝在這兩部電腦上，您就可以檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的離線記錄檔，以及在任何一部電腦上執行舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之執行個體的離線記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0a438-108">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on both computers, you can view offline files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and for instances that are running earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on either computer.</span></span>  
  
 <span data-ttu-id="0a438-109">如果您在使用 [已註冊的伺服器]，則所要連接的目標執行個體就必須在 [本機伺服器群組]  或 [中央管理伺服器] 底下註冊。</span><span class="sxs-lookup"><span data-stu-id="0a438-109">If you are using Registered Servers, the instance that you want to connect to must be registered under **Local Server Groups** or under **Central Management Servers**.</span></span> <span data-ttu-id="0a438-110">(此執行個體可獨立註冊，或成為伺服器群組的成員)。如需有關如何將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體加入至 [已註冊的伺服器] 的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="0a438-110">(The instance can be registered on its own or be a member of a server group.) For more information about how to add an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to Registered Servers, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0a438-111">建立或編輯伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0a438-111">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="0a438-112">註冊連接的伺服器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0a438-112">Register a Connected Server &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="0a438-113">建立中央管理伺服器與伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0a438-113">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
 <span data-ttu-id="0a438-114">如需有關如何透過 WMI 和 WQL 查詢以程式設計方式檢視離線記錄檔的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="0a438-114">For more information about how to view offline log files programmatically through WMI and WQL queries, see the following topics:</span></span>  
  
-   <span data-ttu-id="0a438-115">[SqlErrorLogEvent Class](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) (此主題會示範如何擷取指定之記錄檔中已記錄事件的值)。</span><span class="sxs-lookup"><span data-stu-id="0a438-115">[SqlErrorLogEvent Class](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) (This topic shows how to retrieve values for logged events in a specified log file.)</span></span>  
  
-   <span data-ttu-id="0a438-116">[SqlErrorLogFile Class](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) (此主題會示範如何擷取有關指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]記錄檔的資訊)。</span><span class="sxs-lookup"><span data-stu-id="0a438-116">[SqlErrorLogFile Class](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) (This topic shows how to retrieve information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files on a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0a438-117">權限</span><span class="sxs-lookup"><span data-stu-id="0a438-117">Permissions</span></span>  
 <span data-ttu-id="0a438-118">若要連接至離線記錄檔，您必須在本機和遠端電腦上具有下列權限：</span><span class="sxs-lookup"><span data-stu-id="0a438-118">To connect to an offline log file, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="0a438-119">**Root\Microsoft\SqlServer\ComputerManagement12** WMI 命名空間的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="0a438-119">Read access to the **Root\Microsoft\SqlServer\ComputerManagement12** WMI namespace.</span></span> <span data-ttu-id="0a438-120">根據預設，每個人都可從啟用帳戶權限取得讀取權限。</span><span class="sxs-lookup"><span data-stu-id="0a438-120">By default, everyone has read access through the Enable Account permission.</span></span> <span data-ttu-id="0a438-121">如需詳細資訊，請參閱本節後面的＜若要確認 WMI 權限＞程序。</span><span class="sxs-lookup"><span data-stu-id="0a438-121">For more information, see the "To verify WMI permissions" procedure later in this section.</span></span>  
  
-   <span data-ttu-id="0a438-122">包含錯誤記錄檔之資料夾的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="0a438-122">Read permission to the folder that contains the error log files.</span></span> <span data-ttu-id="0a438-123">根據預設，錯誤記錄檔會位於下列路徑 (其中 \<*Drive>\* 表示安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的磁碟機，而 \<*InstanceName*> 則是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體名稱)：</span><span class="sxs-lookup"><span data-stu-id="0a438-123">By default the error log files are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="0a438-124">**\<Drive>： \Program Files\Microsoft SQL Server\MSSQL12. \<InstanceName>\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="0a438-124">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="0a438-125">若要確認 WMI 命名空間安全性設定，您可以使用 [WMI 控制] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="0a438-125">To verify WMI namespace security settings, you can use the WMI Control snap-in.</span></span>  
  
#### <a name="to-verify-wmi-permissions"></a><span data-ttu-id="0a438-126">若要確認 WMI 權限</span><span class="sxs-lookup"><span data-stu-id="0a438-126">To verify WMI permissions</span></span>  
  
1.  <span data-ttu-id="0a438-127">開啟 [WMI 控制] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="0a438-127">Open the WMI Control snap-in.</span></span> <span data-ttu-id="0a438-128">若要這樣做，請根據作業系統執行下列其中一項作業：</span><span class="sxs-lookup"><span data-stu-id="0a438-128">To do this, do either of the following, depending on the operating system:</span></span>  
  
    -   <span data-ttu-id="0a438-129">按一下 [**開始**]， `wmimgmt.msc` 在 [**開始搜尋**] 方塊中輸入，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="0a438-129">Click **Start**, type `wmimgmt.msc` in the **Start Search** box, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="0a438-130">依序按一下 [**開始**] 和 [**執行**]，輸入 `wmimgmt.msc` ，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="0a438-130">Click **Start**, click **Run**, type `wmimgmt.msc`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="0a438-131">根據預設，[WMI 控制] 嵌入式管理單元會管理本機電腦。</span><span class="sxs-lookup"><span data-stu-id="0a438-131">By default, the WMI Control snap-in manages the local computer.</span></span>  
  
     <span data-ttu-id="0a438-132">如果您想要連接至遠端電腦，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0a438-132">If you want to connect to a remote computer, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="0a438-133">以滑鼠右鍵按一下 [WMI 控制 (本機)] ，然後按一下 [連線到另一台電腦] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-133">Right-click **WMI Control (Local)**, and then click **Connect to another computer**.</span></span>  
  
    2.  <span data-ttu-id="0a438-134">在 [變更受管理的電腦]  對話方塊中，按一下 [另一台電腦] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-134">In the **Change managed computer** dialog box, click **Another computer**.</span></span>  
  
    3.  <span data-ttu-id="0a438-135">輸入遠端電腦名稱，然後按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-135">Enter the remote computer name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0a438-136">以滑鼠右鍵按一下 [ \*\*Wmi 控制] (本機) \*\*或 [ **wmi 控制] (***RemoteComputerName***) **]，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="0a438-136">Right-click **WMI Control (Local)** or **WMI Control (***RemoteComputerName***)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0a438-137">在 [WMI Control Properties (WMI 控制內容)]  對話方塊中，按一下 [安全性]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0a438-137">In the **WMI Control Properties** dialog box, click the **Security** tab.</span></span>  
  
5.  <span data-ttu-id="0a438-138">在命名空間樹狀目錄中，找出下列命名空間，然後按一下：</span><span class="sxs-lookup"><span data-stu-id="0a438-138">In the namespace tree, locate and then click the following namespace:</span></span>  
  
     <span data-ttu-id="0a438-139">**Root\Microsoft\SqlServer\ComputerManagement10**</span><span class="sxs-lookup"><span data-stu-id="0a438-139">**Root\Microsoft\SqlServer\ComputerManagement10**</span></span>  
  
6.  <span data-ttu-id="0a438-140">按一下 **[安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="0a438-140">Click **Security**.</span></span>  
  
7.  <span data-ttu-id="0a438-141">確定將要使用的帳戶擁有 [啟用帳戶]  權限。</span><span class="sxs-lookup"><span data-stu-id="0a438-141">Make sure that the account that will be used has the **Enable Account** permission.</span></span> <span data-ttu-id="0a438-142">此權限允許對 WMI 物件進行讀取存取。</span><span class="sxs-lookup"><span data-stu-id="0a438-142">This permission allows Read access to WMI objects.</span></span>  
  
### <a name="view-log-files"></a><span data-ttu-id="0a438-143">檢視記錄檔</span><span class="sxs-lookup"><span data-stu-id="0a438-143">View Log Files</span></span>  
 <span data-ttu-id="0a438-144">下列程序會示範如何透過 [已註冊的伺服器] 檢視離線記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0a438-144">The following procedure shows how to view offline log files through Registered Servers.</span></span> <span data-ttu-id="0a438-145">此程序會假設下列條件：</span><span class="sxs-lookup"><span data-stu-id="0a438-145">The procedure assumes the following:</span></span>  
  
 <span data-ttu-id="0a438-146">您想要連接的目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體已經在 [已註冊的伺服器] 中註冊。</span><span class="sxs-lookup"><span data-stu-id="0a438-146">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to connect to is already registered in Registered Servers.</span></span>  
  
##### <a name="to-view-log-files-for-instances-that-are-offline"></a><span data-ttu-id="0a438-147">若要檢視已離線之執行個體的記錄檔</span><span class="sxs-lookup"><span data-stu-id="0a438-147">To view log files for instances that are offline</span></span>  
  
1.  <span data-ttu-id="0a438-148">如果您想要檢視本機執行個體的離線記錄檔，請確定您使用更高的權限來啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-148">If you want to view offline log files on a local instance, make sure that you start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] with elevated permissions.</span></span> <span data-ttu-id="0a438-149">若要這樣做，請在啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]時，以滑鼠右鍵按一下 [SQL Server Management Studio] ，然後按一下 [以系統管理員身分執行] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-149">To do this, when you start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click **SQL Server Management Studio**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="0a438-150">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 **[檢視]** 功能表中，按一下 **[已註冊的伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="0a438-150">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
3.  <span data-ttu-id="0a438-151">在主控台樹狀目錄中，找出您想要檢視離線檔案的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a438-151">In the console tree, locate the instance on which you want to view the offline files.</span></span>  
  
4.  <span data-ttu-id="0a438-152">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="0a438-152">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="0a438-153">如果此執行個體位於 [本機伺服器群組] 底下，請依序展開 [本機伺服器群組] 和伺服器群組 (如果此執行個體是群組成員)，以滑鼠右鍵按一下執行個體，然後按一下 [檢視 SQL Server 記錄檔] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-153">If the instance is under **Local Server Groups**, expand **Local Server Groups**, expand the server group (if the instance is a member of a group), right-click the instance, and then click **View SQL Server Log**.</span></span>  
  
    -   <span data-ttu-id="0a438-154">如果此執行個體是中央管理伺服器本身，請展開 [中央管理伺服器] ，以滑鼠右鍵按一下執行個體，指向 [中央管理伺服器動作] ，然後按一下 [檢視 SQL Server 記錄檔] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-154">If the instance is the Central Management Server itself, expand **Central Management Servers**, right-click the instance, point to **Central Management Server Actions**, and then click **View SQL Server Log**.</span></span>  
  
    -   <span data-ttu-id="0a438-155">如果此執行個體位於 [中央管理伺服器] 底下，請依序展開 [中央管理伺服器] 和中央管理伺服器，以滑鼠右鍵按一下執行個體 (或展開伺服器群組並以滑鼠右鍵按一下執行個體)，然後按一下 [檢視 SQL Server 記錄檔] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-155">If the instance is under **Central Management Servers**, expand **Central Management Servers**, expand the Central Management Server, right-click the instance (or expand a server group and right-click the instance), and then click **View SQL Server Log**.</span></span>  
  
5.  <span data-ttu-id="0a438-156">如果您要連接至本機執行個體，就會使用目前使用者認證來建立連接。</span><span class="sxs-lookup"><span data-stu-id="0a438-156">If you are connecting to a local instance, the connection is made using the current user credentials.</span></span>  
  
     <span data-ttu-id="0a438-157">如果您要連接至遠端執行個體，請在 [記錄檔檢視器 - 連接身分]  對話方塊中，執行下列其中一項作業：</span><span class="sxs-lookup"><span data-stu-id="0a438-157">If you are connecting to a remote instance, in the **Log File Viewer - Connect As** dialog box, do either of the following:</span></span>  
  
    -   <span data-ttu-id="0a438-158">若要以目前使用者的身分連接，請確定已清除 [以其他使用者身分連接]  核取方塊，然後按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-158">To connect as the current user, make sure that the **Connect as another user** check box is cleared, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="0a438-159">若要以其他使用者的身分連接，請選取 [以其他使用者身分連接]  核取方塊，然後按一下 [設定使用者] 。</span><span class="sxs-lookup"><span data-stu-id="0a438-159">To connect as another user, select the **Connect as another user** check box, and then click **Set User**.</span></span> <span data-ttu-id="0a438-160">當您收到提示時，請輸入使用者認證 (採用 *網域名稱*\\*使用者名稱*格式的使用者名稱)，按一下 [確定] ，然後再按一下 [確定]  連接。</span><span class="sxs-lookup"><span data-stu-id="0a438-160">When you are prompted, enter the user credentials (with the user name in the format *domain_name*\\*user_name*), click **OK**, and then click **OK** again to connect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a438-161">如果載入記錄檔所花費的時間太長，您可以在 [記錄檔檢視器] 工具列上按一下 [停止]  。</span><span class="sxs-lookup"><span data-stu-id="0a438-161">If the log files take too long to load, you can click **Stop** on the Log File Viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a438-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a438-162">See Also</span></span>  
 [<span data-ttu-id="0a438-163">記錄檔檢視器</span><span class="sxs-lookup"><span data-stu-id="0a438-163">Log File Viewer</span></span>](log-file-viewer.md)  
  
  
