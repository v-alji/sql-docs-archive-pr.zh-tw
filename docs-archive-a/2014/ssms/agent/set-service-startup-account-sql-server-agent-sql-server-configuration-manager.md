---
title: 設定 SQL Server Agent (SQL Server 組態管理員) 的服務啟動帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: stevestein
ms.author: sstein
ms.openlocfilehash: 63e5ba7c24f1aa1a3f79f80e5ca28c02a0cd5812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699172"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a><span data-ttu-id="7aa6f-102">Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)</span><span class="sxs-lookup"><span data-stu-id="7aa6f-102">Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="7aa6f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務啟動帳戶會定義 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行的 Windows 帳戶以及它的網路權限。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service startup account defines the Windows account that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs as, as well as its network permissions.</span></span> <span data-ttu-id="7aa6f-104">此主題描述如何透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 組態管理員來設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Agent 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-104">This topic describes how to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="7aa6f-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="7aa6f-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7aa6f-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="7aa6f-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7aa6f-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="7aa6f-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7aa6f-108">安全性</span><span class="sxs-lookup"><span data-stu-id="7aa6f-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="7aa6f-109">若要使用 SQL Server Management Studio，為 SQL Server Agent 設定服務啟動帳戶</span><span class="sxs-lookup"><span data-stu-id="7aa6f-109">To set the Service Startup Account for SQL Server Agent using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7aa6f-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="7aa6f-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7aa6f-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="7aa6f-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7aa6f-112">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]開始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 不再要求服務啟動帳戶一定是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-112">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer requires that the service startup account be a member of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators group.</span></span> <span data-ttu-id="7aa6f-113">不過， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務啟動帳戶必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-113">However, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service startup account must be a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin fixed server role.</span></span> <span data-ttu-id="7aa6f-114">如果使用多伺服器作業處理，帳戶也必須是主要伺服器上 msdb 資料庫角色 TargetServersRole 的成員。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-114">The account must also be a member of the msdb database role TargetServersRole on the master server if multiserver job processing is used.</span></span>  
  
-   <span data-ttu-id="7aa6f-115">只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7aa6f-116">Security</span><span class="sxs-lookup"><span data-stu-id="7aa6f-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7aa6f-117">權限</span><span class="sxs-lookup"><span data-stu-id="7aa6f-117">Permissions</span></span>  
 <span data-ttu-id="7aa6f-118">若要執行它的函 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 式，必須將 Agent 設定為使用帳戶的認證，該帳戶是 `sysadmin` 中的固定伺服器角色的成員 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the `sysadmin` fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7aa6f-119">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="7aa6f-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="7aa6f-120">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="7aa6f-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="7aa6f-121">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="7aa6f-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="7aa6f-122">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="7aa6f-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="7aa6f-123">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="7aa6f-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="7aa6f-124">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7aa6f-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7aa6f-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a><span data-ttu-id="7aa6f-126">若要為 SQL Server Agent 設定服務啟動帳戶</span><span class="sxs-lookup"><span data-stu-id="7aa6f-126">To set the Service Startup Account for SQL Server Agent</span></span>  
  
1.  <span data-ttu-id="7aa6f-127">在 **[已註冊的伺服器]**，按一下加號展開 **[Database Engine]**。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-127">In **Registered Servers**, click the plus sign to expand **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="7aa6f-128">按一下加號展開 **[本機伺服器群組]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-128">Click the plus sign to expand the **Local Server Groups** folder.</span></span>  
  
3.  <span data-ttu-id="7aa6f-129">以滑鼠右鍵按一下您要設定服務啟動帳戶的伺服器執行個體，並選取 [SQL Server 組態管理員...]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-129">Right-click the server instance where you want set up the Service Startup Account, and select **SQL Server Configuration Manager...**.</span></span>  
  
4.  <span data-ttu-id="7aa6f-130">在 [使用者帳戶控制] 對話方塊中，按一下 [是]。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-130">In the **User Account Control** dialog box, click **Yes**.</span></span>  
  
5.  <span data-ttu-id="7aa6f-131">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員的主控台窗格中，選取 **[SQL Server 服務]**。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-131">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the console pane, select **SQL Server Services**.</span></span>  
  
6.  <span data-ttu-id="7aa6f-132">在詳細資料窗格中，以滑鼠右鍵按一下**SQL Server Agent** _ (server_name) _，其中*server_name*是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 您要變更服務啟動帳戶的代理程式實例名稱，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-132">In the details pane, right-click **SQL Server Agent**_(server_name)_, where *server_name* is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent instance for which you want to change the service startup account, and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="7aa6f-133">在 [ **SQL Server Agent** _ (server_name) _ **屬性**] 對話方塊的 [**登**入] 索引標籤中，選取 [**登**入身分] 底下的下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="7aa6f-133">In the **SQL Server Agent**_(server_name)_ **Properties** dialog box, in the **Log On** tab, select one of the following options under **Log on as**:</span></span>  
  
    -   <span data-ttu-id="7aa6f-134">**內建帳戶**：如果您的作業僅需來自本機伺服器的資源，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-134">**Built-in account**: select this option if your jobs require resources from the local server only.</span></span> <span data-ttu-id="7aa6f-135">如需有關如何選擇 Windows 內建帳戶類型的詳細資訊，請參閱 [選取 SQL Server Agent 服務的帳戶](https://msdn.microsoft.com/library/ms191543.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-135">For information about how to choose a Windows built-in account type, see [Selecting an Account for SQL Server Agent Service.](https://msdn.microsoft.com/library/ms191543.aspx)</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="7aa6f-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務不支援 \*\*\*\* 中的 [本機服務] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]帳戶。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service does not support the **Local Service** account in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
    -   <span data-ttu-id="7aa6f-137">**這個帳戶**：如果您的作業需要網路上的資源 (包括應用程式資源)，或想要將事件轉寄給其他 Windows 應用程式記錄檔，又或者想要透過電子郵件或呼叫器來通知操作員，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-137">**This account**: select this option if your jobs require resources across the network, including application resources; if you want to forward events to other Windows application logs; or if you want to notify operators through e-mail or pagers.</span></span>  
  
         <span data-ttu-id="7aa6f-138">如果您選取這個選項：</span><span class="sxs-lookup"><span data-stu-id="7aa6f-138">If you select this option:</span></span>  
  
        1.  <span data-ttu-id="7aa6f-139">在 **[帳戶名稱]** 方塊中，輸入將用來執行 SQL Server Agent 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-139">In the **Account Name** box, enter the account that will be used to run SQL Server Agent.</span></span> <span data-ttu-id="7aa6f-140">或者，按一下 **[瀏覽]** 開啟 **[選取使用者或群組]** 對話方塊，然後選取要使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-140">Alternately, click **Browse** to open the **Select User or Group** dialog box and select the account to use.</span></span>  
  
        2.  <span data-ttu-id="7aa6f-141">在 **[密碼]** 方塊中，輸入帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-141">In the **Password** box, enter the password for the account.</span></span> <span data-ttu-id="7aa6f-142">在 [確認密碼]\*\*\*\* 方塊中重新輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-142">Re-enter the password in the **Confirm password** box.</span></span>  
  
8.  <span data-ttu-id="7aa6f-143">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-143">Click **OK**.</span></span>  
  
9. <span data-ttu-id="7aa6f-144">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，按一下 **[關閉]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7aa6f-144">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click the **Close** button.</span></span>  
  
  
