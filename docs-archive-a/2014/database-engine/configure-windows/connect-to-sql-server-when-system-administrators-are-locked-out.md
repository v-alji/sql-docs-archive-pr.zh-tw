---
title: 當系統管理員遭鎖定在外時連線到 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- connecting when locked out [SQL Server]
- locked out [SQL Server]
ms.assetid: c0c0082e-b867-480f-a54b-79f2a94ceb67
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 47b9659943e51a2d31a2354740660aebd652745c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597326"
---
# <a name="connect-to-sql-server-when-system-administrators-are-locked-out"></a><span data-ttu-id="2d3c6-102">當系統管理員遭到鎖定時連接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d3c6-102">Connect to SQL Server When System Administrators Are Locked Out</span></span>
  <span data-ttu-id="2d3c6-103">本主題描述如何以系統管理員的身分，重新取得 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的存取權。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-103">This topic describes how you can regain access to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] as a system administrator.</span></span> <span data-ttu-id="2d3c6-104">系統管理員可能因為下列其中一個原因而失去 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的存取權：</span><span class="sxs-lookup"><span data-stu-id="2d3c6-104">A system administrator can lose access to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="2d3c6-105">屬於 sysadmin 固定伺服器角色之成員的所有登入都因為錯誤而遭到移除。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-105">All logins that are members of the sysadmin fixed server role have been removed by mistake.</span></span>  
  
-   <span data-ttu-id="2d3c6-106">屬於 sysadmin 固定伺服器角色之成員的所有 Windows 群組都因為錯誤而遭到移除。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-106">All Windows Groups that are members of the sysadmin fixed server role have been removed by mistake.</span></span>  
  
-   <span data-ttu-id="2d3c6-107">屬於 sysadmin 固定伺服器角色之成員的登入供已經離開公司或沒有空的個人使用。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-107">The logins that are members of the sysadmin fixed server role are for individuals who have left the company or who are not available.</span></span>  
  
-   <span data-ttu-id="2d3c6-108">sa 帳戶已遭到停用或沒有人知道密碼。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-108">The sa account is disabled or no one knows the password.</span></span>  
  
 <span data-ttu-id="2d3c6-109">您可以重新取得存取權的其中一種方式就是重新安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並將所有資料庫附加到新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-109">One way in which you can regain access is to reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and attach all the databases to the new instance.</span></span> <span data-ttu-id="2d3c6-110">這個解決方案相當耗時，而且，若要復原登入，可能需要從備份還原 master 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-110">This solution is time-consuming; and, to recover the logins, it might require restoring the master database from a backup.</span></span> <span data-ttu-id="2d3c6-111">如果 master 資料庫的備份較舊，可能不會有所有的資訊。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-111">If the backup of the master database is older, it might not have all the information.</span></span> <span data-ttu-id="2d3c6-112">如果 master 資料庫的備份比較新，可能與先前的執行個體擁有相同的登入，因此，系統管理員仍然會遭到鎖定。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-112">If the backup of the master database is more recent, it might have the same logins as the previous instance; therefore, administrators will still be locked out.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2d3c6-113">解決方法</span><span class="sxs-lookup"><span data-stu-id="2d3c6-113">Resolution</span></span>  
 <span data-ttu-id="2d3c6-114">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -m **或** -f **選項，在單一使用者模式中啟動** 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-114">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode by using either the **-m** or **-f** options.</span></span> <span data-ttu-id="2d3c6-115">接著，電腦本機管理員群組的任何成員都可以利用 sysadmin 固定伺服器角色的成員身分，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-115">Any member of the computer's local Administrators group can then connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the sysadmin fixed server role.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d3c6-116">當您以單一使用者模式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，請先停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-116">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, first stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="2d3c6-117">否則， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 可能會先進行連接，您就無法以另一個使用者的身分進行連接。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-117">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent might connect first and prevent you from connecting as a second user.</span></span>  
  
 <span data-ttu-id="2d3c6-118">當您搭配**sqlcmd**或使用 **-m**選項時 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，可以限制與指定之用戶端應用程式的連接。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-118">When you use the **-m** option with **sqlcmd** or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can limit the connections to a specified client application.</span></span> <span data-ttu-id="2d3c6-119">例如， **-m "sqlcmd"** 會將連接限制為單一連接，而且該連接必須將自己識別為**sqlcmd**用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-119">For example, **-m"sqlcmd"** limits connections to a single connection and that connection must identify itself as the **sqlcmd** client program.</span></span> <span data-ttu-id="2d3c6-120">當您在單一使用者模式下啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而且有未知的用戶端應用程式佔用唯一可用的連接時，請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-120">Use this option when you are starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode and an unknown client application is taking the only available connection.</span></span> <span data-ttu-id="2d3c6-121">若要透過 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的查詢編輯器進行連接，請使用 **-m"Microsoft SQL Server Management Studio - Query"** 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-121">To connect through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], use **-m"Microsoft SQL Server Management Studio - Query"**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2d3c6-122">請勿將這個選項當做安全性功能使用。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-122">Do not use this option as a security feature.</span></span> <span data-ttu-id="2d3c6-123">用戶端應用程式會提供用戶端應用程式名稱，而且可能會在連接字串中提供假的名稱。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-123">The client application provides the client application name, and can provide a false name as part of the connection string.</span></span>  
  
 <span data-ttu-id="2d3c6-124">如需如何以單一使用者模式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的逐步指示，請參閱[設定伺服器啟動選項 &#40;SQL Server 組態管理員&#41;](scm-services-configure-server-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-124">For step-by-step instructions about how to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span></span>  
  
## <a name="step-by-step-instructions"></a><span data-ttu-id="2d3c6-125">逐步指示</span><span class="sxs-lookup"><span data-stu-id="2d3c6-125">Step-By-Step Instructions</span></span>  
 <span data-ttu-id="2d3c6-126">下列指示描述連接到在 Windows 8 或更新版上執行之 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的程序。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-126">The following instructions describe the process for connecting to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] running on Windows 8 or higher.</span></span> <span data-ttu-id="2d3c6-127">針對舊版 SQL Server 或 Windows 提供了些微調整。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-127">Slight adjustments for earlier versions of SQL Server or Windows are provided.</span></span> <span data-ttu-id="2d3c6-128">您必須在登入 Windows 成為本機 Administrators 群組的成員時執行這些指示，而且這些指示會假設電腦已安裝了 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-128">These instructions must be performed while logged in to Windows as a member of the local administrators group, and they assume that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is installed on the computer.</span></span>  
  
1.  <span data-ttu-id="2d3c6-129">在起始頁上，啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-129">From the Start page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="2d3c6-130">在 [檢視]\*\*\*\* 功能表上，選取 [已註冊的伺服器]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="2d3c6-130">On the **View** menu, select **Registered Servers**.</span></span> <span data-ttu-id="2d3c6-131">(如果您的伺服器尚未註冊，請以滑鼠右鍵按一下 [本機伺服器群組]\*\*\*\*，指向 [工作]\*\*\*\*，然後按一下 [註冊本機伺服器]\*\*\*\*)。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-131">(If your server is not already registered, right-click **Local Server Groups**, point to **Tasks**, and then click **Register Local Servers**.)</span></span>  
  
2.  <span data-ttu-id="2d3c6-132">在 [已註冊的伺服器] 區域中，以滑鼠右鍵按一下您的伺服器，然後按一下 [SQL Server 組態管理員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-132">In the Registered Servers area, right-click your server, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="2d3c6-133">這樣應該會要求以系統管理員身分執行的權限，然後開啟組態管理員程式。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-133">This should ask for permission to run as administrator, and then open the Configuration Manager program.</span></span>  
  
3.  <span data-ttu-id="2d3c6-134">關閉 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-134">Close [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="2d3c6-135">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員的左窗格中，選取 [SQL Server 服務]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-135">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, select **SQL Server Services**.</span></span> <span data-ttu-id="2d3c6-136">在右窗格中，尋找您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體</span><span class="sxs-lookup"><span data-stu-id="2d3c6-136">In the right-pane, find your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d3c6-137">([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體會在電腦名稱後面加上 **(MSSQLSERVER)** 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-137">(The default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] includes **(MSSQLSERVER)** after the computer name.</span></span> <span data-ttu-id="2d3c6-138">具名執行個體會以 [已註冊的伺服器] 中顯示的相同大寫名稱出現)。以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-138">Named instances appear in upper case with the same name that they have in Registered Servers.) Right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="2d3c6-139">在 [**啟動參數**] 索引標籤的 [**指定啟動參數**] 方塊中，輸入， `-m` 然後按一下 `Add` 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-139">On the **Startup Parameters** tab, in the **Specify a startup parameter** box, type `-m` and then click `Add`.</span></span> <span data-ttu-id="2d3c6-140">(這是虛線，然後接著小寫字母 m)。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-140">(That's a dash then lower case letter m.)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2d3c6-141">如果是某些舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則沒有 [啟動參數] 索引標籤。在該情況下，請在 [進階] 索引標籤上，按兩下 [啟動參數]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-141">For some earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] there is no **Startup Parameters** tab. In that case, on the **Advanced** tab, double-click **Startup Parameters**.</span></span> <span data-ttu-id="2d3c6-142">這些參數就會在非常小的視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-142">The parameters open up in a very small window.</span></span> <span data-ttu-id="2d3c6-143">請小心不要變更任何現有參數。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-143">Be careful not to change any of the existing parameters.</span></span> <span data-ttu-id="2d3c6-144">在結尾處，加上新的參數 `;-m`，然後按一下 [`OK`] </span><span class="sxs-lookup"><span data-stu-id="2d3c6-144">At the very end, add a new parameter `;-m` and then click `OK`.</span></span> <span data-ttu-id="2d3c6-145">(這是分號，然後接著虛線和小寫字母 m)。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-145">(That's a semi-colon then a dash then lower case letter m.)</span></span>  
  
6.  <span data-ttu-id="2d3c6-146">按一下 `OK` ，然後在要重新開機的訊息之後，以滑鼠右鍵按一下您的伺服器名稱，然後按一下 [**重新開機**]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-146">Click `OK`, and after the message to restart, right-click your server name, and then click **Restart**.</span></span>  
  
7.  <span data-ttu-id="2d3c6-147">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後，您的伺服器即會處於單一使用者模式。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-147">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has restarted your server will be in single-user mode.</span></span> <span data-ttu-id="2d3c6-148">確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 並未執行。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-148">Make sure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is not running.</span></span> <span data-ttu-id="2d3c6-149">如果已啟動，它將會佔用您的唯一連接。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-149">If started, it will take your only connection.</span></span>  
  
8.  <span data-ttu-id="2d3c6-150">在 Windows 8 的 [開始] 畫面上，以滑鼠右鍵按一下 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的圖示。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-150">On the Windows 8 start screen, right-click the icon for [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="2d3c6-151">在畫面底部，選取 [以系統管理員身分執行]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="2d3c6-151">At the bottom of the screen, select **Run as administrator**.</span></span> <span data-ttu-id="2d3c6-152">(這樣會將您的系統管理員認證傳遞給 SSMS)。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-152">(This will pass your administrator credentials to SSMS.)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2d3c6-153">如果是舊版 Windows，[以系統管理員身分執行] 選項會顯示成子功能表。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-153">For earlier versions of Windows, the **Run as administrator** option appears as a sub-menu.</span></span>  
  
     <span data-ttu-id="2d3c6-154">在某些組態中，SSMS 會嘗試建立許多連接。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-154">In some configurations, SSMS will attempt to make several connections.</span></span> <span data-ttu-id="2d3c6-155">多重連接將會失敗，因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處於單一使用者模式。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-155">Multiple connections will fail because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is in single-user mode.</span></span> <span data-ttu-id="2d3c6-156">您可以選取下列其中一項動作來執行。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-156">You can select one of the following actions to perform.</span></span> <span data-ttu-id="2d3c6-157">執行下列其中一項動作。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-157">Do one of the following.</span></span>  
  
    1.  <span data-ttu-id="2d3c6-158">使用 Windows 驗證 (包含您的系統管理員認證) 透過 [物件總管] 連接。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-158">Connect with Object Explorer using Windows Authentication (which includes your Administrator credentials).</span></span> <span data-ttu-id="2d3c6-159">依序展開 [安全性] 和 [登入]，然後按兩下您自己的登入。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-159">Expand **Security**, expand **Logins**, and double-click your own login.</span></span> <span data-ttu-id="2d3c6-160">在 [**伺服器角色**] 頁面上，選取 `sysadmin` ，然後按一下 `OK` 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-160">On the **Server Roles** page, select `sysadmin`, and then click `OK`.</span></span>  
  
    2.  <span data-ttu-id="2d3c6-161">不透過 [物件總管] 連接，而是使用 Windows 驗證 (包含您的系統管理員認證) 透過查詢視窗連接</span><span class="sxs-lookup"><span data-stu-id="2d3c6-161">Instead of connecting with Object Explorer, connect with a Query Window using Windows Authentication (which includes your Administrator credentials).</span></span> <span data-ttu-id="2d3c6-162"> (只有在您未使用物件總管連接時，才能以這種方式連接。 ) 執行下列程式碼來加入屬於固定伺服器角色成員的新 Windows 驗證登入 `sysadmin` 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-162">(You can only connect this way if you did not connect with Object Explorer.) Execute code such as the following to add a new Windows Authentication login that is a member of the `sysadmin` fixed server role.</span></span> <span data-ttu-id="2d3c6-163">下列範例會加入名為 `CONTOSO\PatK` 的網域使用者。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-163">The following example adds a domain user named `CONTOSO\PatK`.</span></span>  
  
        ```  
        CREATE LOGIN [CONTOSO\PatK] FROM WINDOWS;  
        ALTER SERVER ROLE sysadmin ADD MEMBER [CONTOSO\PatK];  
        ```  
  
    3.  <span data-ttu-id="2d3c6-164">如果您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是以混合驗證模式執行，請使用 Windows 驗證 (包含您的系統管理員認證) 透過查詢視窗連接。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-164">If your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in mixed authentication mode, connect with a Query Window using Windows Authentication (which includes your Administrator credentials).</span></span> <span data-ttu-id="2d3c6-165">執行如下所示的程式碼，以建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 屬於固定伺服器角色成員的新驗證登入 `sysadmin` 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-165">Execute code such as the following to create a new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login that is a member of the `sysadmin` fixed server role.</span></span>  
  
        ```  
        CREATE LOGIN TempLogin WITH PASSWORD = '************';  
        ALTER SERVER ROLE sysadmin ADD MEMBER TempLogin;  
        ```  
  
        > [!WARNING]  
        >  <span data-ttu-id="2d3c6-166">請將 \*\*\*\*\*\*\*\*\*\*\*\* 取代成增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-166">Replace \*\*\*\*\*\*\*\*\*\*\*\* with a strong password.</span></span>  
  
    4.  <span data-ttu-id="2d3c6-167">如果您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是以混合驗證模式執行，而您想要重設帳戶的密碼 `sa` ，請使用 Windows 驗證（包含您的系統管理員認證)  (）與查詢視窗連接。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-167">If your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in mixed authentication mode and you want to reset the password of the `sa` account, connect with a Query Window using Windows Authentication (which includes your Administrator credentials).</span></span> <span data-ttu-id="2d3c6-168">`sa`使用下列語法變更帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-168">Change the password of the `sa` account with the following syntax.</span></span>  
  
        ```  
        ALTER LOGIN sa WITH PASSWORD = '************';  
        ```  
  
        > [!WARNING]  
        >  <span data-ttu-id="2d3c6-169">請將 \*\*\*\*\*\*\*\*\*\*\*\* 取代成增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-169">Replace \*\*\*\*\*\*\*\*\*\*\*\* with a strong password.</span></span>  
  
9. <span data-ttu-id="2d3c6-170">下列步驟現在會將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 變更回多使用者模式。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-170">The following steps now change [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] back to multi-user mode.</span></span> <span data-ttu-id="2d3c6-171">關閉 SSMS。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-171">Close SSMS.</span></span>  
  
10. <span data-ttu-id="2d3c6-172">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員的左窗格中，選取 [SQL Server 服務]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-172">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, select **SQL Server Services**.</span></span> <span data-ttu-id="2d3c6-173">在右窗格中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-173">In the right-pane, right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then click **Properties**.</span></span>  
  
11. <span data-ttu-id="2d3c6-174">在 [**啟動參數**] 索引標籤的 [**現有參數**] 方塊中，選取 `-m` ，然後按一下 `Remove` 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-174">On the **Startup Parameters** tab, in the **Existing parameters** box, select `-m` and then click `Remove`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2d3c6-175">如果是某些舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則沒有 [啟動參數] 索引標籤。在該情況下，請在 [進階] 索引標籤上，按兩下 [啟動參數]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-175">For some earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] there is no **Startup Parameters** tab. In that case, on the **Advanced** tab, double-click **Startup Parameters**.</span></span> <span data-ttu-id="2d3c6-176">這些參數就會在非常小的視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-176">The parameters open up in a very small window.</span></span> <span data-ttu-id="2d3c6-177">移除 `;-m` 您先前加入的，然後按一下 `OK` 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-177">Remove the `;-m` which you added earlier, and then click `OK`.</span></span>  
  
12. <span data-ttu-id="2d3c6-178">以滑鼠右鍵按一下您的伺服器名稱，然後按一下 [重新啟動]。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-178">Right-click your server name, and then click **Restart**.</span></span>  
  
 <span data-ttu-id="2d3c6-179">現在，您應該能夠使用其中一個目前是固定伺服器角色成員的帳戶進行正常連接 `sysadmin` 。</span><span class="sxs-lookup"><span data-stu-id="2d3c6-179">Now you should be able to connect normally with one of the accounts which is now a member of the `sysadmin` fixed server role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3c6-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d3c6-180">See Also</span></span>  
 <span data-ttu-id="2d3c6-181">[以單一使用者模式啟動 SQL Server](start-sql-server-in-single-user-mode.md) </span><span class="sxs-lookup"><span data-stu-id="2d3c6-181">[Start SQL Server in Single-User Mode](start-sql-server-in-single-user-mode.md) </span></span>  
 [<span data-ttu-id="2d3c6-182">Database Engine 服務啟動選項</span><span class="sxs-lookup"><span data-stu-id="2d3c6-182">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
