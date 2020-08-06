---
title: 啟用或停用伺服器網路通訊協定 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], disabling
- remote connections [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], disabling using Configuration Manager
- disabling network protocols, Configuration Manager
- network protocols [SQL Server], enabling
- enabling network protocols, Configuration Manager
- surface area configuration [SQL Server], connection protocols
- connections [SQL Server], enabling remote using Configuration Manager
ms.assetid: ec5ccb69-61c9-4576-8843-014b976fd46e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 737edae84ff284ed726ade69cb48e574b830611e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700213"
---
# <a name="enable-or-disable-a-server-network-protocol"></a><span data-ttu-id="db798-102">啟用或停用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="db798-102">Enable or Disable a Server Network Protocol</span></span>
  <span data-ttu-id="db798-103">所有網路通訊協定都是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式所安裝，但是有些會啟用，有些不會啟用。</span><span class="sxs-lookup"><span data-stu-id="db798-103">All network protocols are installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, but may or may not be enabled.</span></span> <span data-ttu-id="db798-104">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 組態管理員或 PowerShell，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中啟用或停用伺服器網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="db798-104">This topic describes how to enable or disable a server network protocol in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or PowerShell.</span></span> <span data-ttu-id="db798-105">必須停止並重新啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，才能讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="db798-105">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be stopped and restarted for the change to take effect.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db798-106">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 安裝期間會在 BUILTIN\Users 群組中加入一個登入。</span><span class="sxs-lookup"><span data-stu-id="db798-106">During setup of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] a login is added for the BUILTIN\Users group.</span></span> <span data-ttu-id="db798-107">這個登入可讓電腦上所有經過驗證的使用者以 public 角色成員的身分存取 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="db798-107">This allows all authenticated users of the computer to access the instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as a member of the public role.</span></span> <span data-ttu-id="db798-108">BUILTIN\Users 登入可以安全地移除，藉此限制擁有個別登入或為其他擁有登入之 Windows 群組成員的電腦使用者對 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的存取。</span><span class="sxs-lookup"><span data-stu-id="db798-108">The BUILTIN\Users login can be safely removed to restrict [!INCLUDE[ssDE](../../includes/ssde-md.md)] access to computer users who have individual logins or are members of other Windows groups with logins.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db798-109">的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 資料提供者支援 TLS 1.0 和 SSL 3.0。</span><span class="sxs-lookup"><span data-stu-id="db798-109">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] data providers for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support TLS 1.0 and SSL 3.0.</span></span> <span data-ttu-id="db798-110">如果您以在作業系統 SChannel 層級中進行變更的方式，強制執行不同的通訊協定 (例如 TLS 1.1 或 TLS 1.2)，您與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的連線可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="db798-110">If you enforce a different protocol (such as TLS 1.1 or TLS 1.2) by making changes in the operating system SChannel layer, your connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might fail.</span></span>  
  
 <span data-ttu-id="db798-111">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="db798-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="db798-112">**若要使用下列項目來啟用或停用伺服器網路通訊協定：**</span><span class="sxs-lookup"><span data-stu-id="db798-112">**To enable or disable a server network protocol using:**</span></span>  
  
     [<span data-ttu-id="db798-113">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="db798-113">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="db798-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="db798-114">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="db798-115">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="db798-115">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-enable-a-server-network-protocol"></a><span data-ttu-id="db798-116">若要啟用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="db798-116">To enable a server network protocol</span></span>  
  
1.  <span data-ttu-id="db798-117">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員的主控台窗格中，展開 **[SQL Server 網路組態]** 。</span><span class="sxs-lookup"><span data-stu-id="db798-117">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the console pane, expand **SQL Server  Network Configuration**.</span></span>  
  
2.  <span data-ttu-id="db798-118">在主控台窗格中，按一下 [ *\<instance name>* 的通訊協定]。</span><span class="sxs-lookup"><span data-stu-id="db798-118">In the console pane, click **Protocols for** *\<instance name>*.</span></span>  
  
3.  <span data-ttu-id="db798-119">在詳細資料窗格中，以滑鼠右鍵按一下要變更的通訊協定，然後按一下 [啟用] 或 [停用]。</span><span class="sxs-lookup"><span data-stu-id="db798-119">In the details pane, right-click the protocol you want to change, and then click **Enable** or **Disable**.</span></span>  
  
4.  <span data-ttu-id="db798-120">在主控台窗格中，按一下 [SQL Server 服務]。</span><span class="sxs-lookup"><span data-stu-id="db798-120">In the console pane, click **SQL Server Services**.</span></span>  
  
5.  <span data-ttu-id="db798-121">在詳細資料窗格中，以滑鼠右鍵按一下**SQL Server (***\<instance name>***) **]，然後按一下 [**重新開機**]，以停止並重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="db798-121">In the details pane, right-click **SQL Server (***\<instance name>***)**, and then click **Restart**, to stop and restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
##  <a name="using-sql-server-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="db798-122">使用 SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="db798-122">Using SQL Server PowerShell</span></span>  
  
#### <a name="to-enable-a-server-network-protocol-using-powershell"></a><span data-ttu-id="db798-123">若要使用 PowerShell 來啟用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="db798-123">To Enable a Server Network Protocol Using PowerShell</span></span>  
  
1.  <span data-ttu-id="db798-124">使用管理員權限來開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="db798-124">Using administrator permissions open a command prompt.</span></span>  
  
2.  <span data-ttu-id="db798-125">從工作列啟動 Windows PowerShell 2.0，或是依序按一下 [開始]、[所有程式]、[附屬應用程式]、[Windows PowerShell]，然後按一下 [Windows PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="db798-125">Start Windows PowerShell 2.0 from the taskbar, or click Start, then All Programs, then Accessories, then Windows PowerShell, then Windows PowerShell.</span></span>  
  
3.  <span data-ttu-id="db798-126">輸入以匯入**sqlps**模組`Import-Module "sqlps"`</span><span class="sxs-lookup"><span data-stu-id="db798-126">Import the **sqlps** module by entering `Import-Module "sqlps"`</span></span>  
  
4.  <span data-ttu-id="db798-127">執行下列陳述式，即可同時啟用 TCP 和具名管道通訊協定。</span><span class="sxs-lookup"><span data-stu-id="db798-127">Execute the following statements to enable both the TCP and named pipes protocols.</span></span> <span data-ttu-id="db798-128">請將 `<computer_name>` 取代成執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="db798-128">Replace `<computer_name>` with the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="db798-129">如果您要設定具名執行個體，請將 `MSSQLSERVER` 取代成執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="db798-129">If you are configuring a named instance, replace `MSSQLSERVER` with the instance name.</span></span>  
  
     <span data-ttu-id="db798-130">若要停用通訊協定，請將 `IsEnabled` 屬性設定為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="db798-130">To disable protocols, set the `IsEnabled` properties to `$false`.</span></span>  
  
    ```powershell
    $smo = 'Microsoft.SqlServer.Management.Smo.'  
    $wmi = new-object ($smo + 'Wmi.ManagedComputer').  
  
    # List the object properties, including the instance names.  
    $Wmi  
  
    # Enable the TCP protocol on the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    $Tcp = $wmi.GetSmoObject($uri)  
    $Tcp.IsEnabled = $true  
    $Tcp.Alter()  
    $Tcp  
  
    # Enable the named pipes protocol for the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Np']"  
    $Np = $wmi.GetSmoObject($uri)  
    $Np.IsEnabled = $true  
    $Np.Alter()  
    $Np  
    ```  
  
#### <a name="to-configure-the-protocols-for-the-local-computer"></a><span data-ttu-id="db798-131">若要設定本機電腦的通訊協定</span><span class="sxs-lookup"><span data-stu-id="db798-131">To configure the protocols for the local computer</span></span>  
  
-   <span data-ttu-id="db798-132">在本機執行此指令碼並且設定本機電腦時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 可能會用動態方式決定本機電腦名稱，讓指令碼更具彈性。</span><span class="sxs-lookup"><span data-stu-id="db798-132">When the script is run locally and configures the local computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell can make the script more flexible by dynamically determining the local computer name.</span></span> <span data-ttu-id="db798-133">若要擷取本機電腦名稱，請將設定 `$uri` 變數的程式碼行取代成下列程式碼行：</span><span class="sxs-lookup"><span data-stu-id="db798-133">To retrieve the local computer name, replace the line setting the `$uri` variable with the following line.</span></span>  
  
    ```powershell
    $uri = "ManagedComputer[@Name='" + (Get-Item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    ```  
  
#### <a name="to-restart-the-database-engine-by-using-sql-server-powershell"></a><span data-ttu-id="db798-134">若要使用 SQL Server PowerShell 來重新啟動 Database Engine</span><span class="sxs-lookup"><span data-stu-id="db798-134">To restart the Database Engine by using SQL Server PowerShell</span></span>  
  
-   <span data-ttu-id="db798-135">啟用或停用通訊協定之後，您必須停止並重新啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，才能讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="db798-135">After you enable or disable protocols, you must stop and restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for the change to take effect.</span></span> <span data-ttu-id="db798-136">您可以執行下列陳述式，利用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 來停止並啟用預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="db798-136">Execute the following statements to stop and start the default instance by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.</span></span> <span data-ttu-id="db798-137">若要停止並啟動具名執行個體，請將 `'MSSQLSERVER'` 取代成 `'MSSQL$<instance_name>'`。</span><span class="sxs-lookup"><span data-stu-id="db798-137">To stop and start a named instance replace `'MSSQLSERVER'` with `'MSSQL$<instance_name>'`.</span></span>  
  
    ```powershell
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\<computer_name>  
    $Wmi = (Get-Item .).ManagedComputer  
    # Get a reference to the default instance of the Database Engine.  
    $DfltInstance = $Wmi.Services['MSSQLSERVER']  
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Start the service again.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache and display the state of the service.  
    $DfltInstance.Refresh(); $DfltInstance  
    ```  
