---
title: 在 Server Core 安裝上設定 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- IsHadrEnabled server property
- Server Core Installation [SQL Server]
ms.assetid: ed6e5e94-4b8d-422a-a17e-61b05a4df903
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e74307374e0d07d69107649b42e0bc2f0897e98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703258"
---
# <a name="configure-sql-server-on-a-server-core-installation"></a><span data-ttu-id="6bf01-102">在 Server Core 安裝上設定 SQL Server</span><span class="sxs-lookup"><span data-stu-id="6bf01-102">Configure SQL Server on a Server Core Installation</span></span>
  <span data-ttu-id="6bf01-103">本主題涵蓋有關在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 的 Server Core 安裝上設定 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6bf01-103">This topic covers details about configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span> 
  
##  <a name="configure-and-manage-server-core-on-windows-server"></a><span data-ttu-id="6bf01-104">在 Windows Server 上設定及管理 Server Core</span><span class="sxs-lookup"><span data-stu-id="6bf01-104">Configure and Manage Server Core on Windows Server</span></span>  
 <span data-ttu-id="6bf01-105">本節提供有助於設定及管理 Server Core 安裝的主題參考。</span><span class="sxs-lookup"><span data-stu-id="6bf01-105">The section provides references to the topics that help configure and manage a Server Core installation.</span></span>  
  
 <span data-ttu-id="6bf01-106">並非所有 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能都在 Server Core 模式中受到支援。</span><span class="sxs-lookup"><span data-stu-id="6bf01-106">Not all features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] are supported in Server Core mode.</span></span>  <span data-ttu-id="6bf01-107">部分功能可以安裝在用戶端電腦或是未執行 Server Core 的另一部伺服器上，並且連接到 Server Core 上安裝的 Database Engine 服務。</span><span class="sxs-lookup"><span data-stu-id="6bf01-107">Some of these features can be installed on a client computer or a different server that is not running Server Core, and connected to the Database Engine services installed on Server Core.</span></span>  
  
 <span data-ttu-id="6bf01-108">如需有關在遠端設定及管理 Server Core 安裝的詳細資訊，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="6bf01-108">For more information about configuring and managing a Server Core installation remotely, see the following topics:</span></span>  
  
-   <span data-ttu-id="6bf01-109">[Windows server 2008 R2：伺服器核心部署的最佳作法](https://go.microsoft.com/fwlink/?LinkID=245957) (https://go.microsoft.com/fwlink/?LinkID=245957)</span><span class="sxs-lookup"><span data-stu-id="6bf01-109">[Windows Server 2008 R2: Best Practices for Server Core Deployments](https://go.microsoft.com/fwlink/?LinkID=245957) (https://go.microsoft.com/fwlink/?LinkID=245957)</span></span>  
  
-   <span data-ttu-id="6bf01-110">設定[Server Core 安裝：總覽](https://go.microsoft.com/fwlink/?LinkId=245958) (https://go.microsoft.com/fwlink/?LinkId=245958)</span><span class="sxs-lookup"><span data-stu-id="6bf01-110">[Configuring a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=245958) (https://go.microsoft.com/fwlink/?LinkId=245958)</span></span>  
  
-   <span data-ttu-id="6bf01-111">[使用 Sconfig 設定 Windows server 2008 R2 的 Server Core 安裝](https://go.microsoft.com/fwlink/?LinkId=245959) (https://go.microsoft.com/fwlink/?LinkId=245959)</span><span class="sxs-lookup"><span data-stu-id="6bf01-111">[Configuring a Server Core installation of Windows Server 2008 R2 with Sconfig.cmd](https://go.microsoft.com/fwlink/?LinkId=245959) (https://go.microsoft.com/fwlink/?LinkId=245959)</span></span>  
  
-   <span data-ttu-id="6bf01-112">[在執行 Windows server 2008 R2 之 Server Core 安裝的伺服器上安裝伺服器角色：總覽](https://go.microsoft.com/fwlink/?LinkId=245960) (https://go.microsoft.com/fwlink/?LinkId=245960)</span><span class="sxs-lookup"><span data-stu-id="6bf01-112">[Installing a server role on a server running a Server Core installation of Windows Server 2008 R2: Overview](https://go.microsoft.com/fwlink/?LinkId=245960) (https://go.microsoft.com/fwlink/?LinkId=245960)</span></span>  
  
-   <span data-ttu-id="6bf01-113">[在執行 Windows server 2008 R2 之 Server Core 安裝的伺服器上安裝 Windows 功能：總覽](https://go.microsoft.com/fwlink/?LinkId=245961) (https://go.microsoft.com/fwlink/?LinkId=245961)</span><span class="sxs-lookup"><span data-stu-id="6bf01-113">[Installing Windows Features on a server running a Server Core installation of Windows Server 2008 R2: Overview](https://go.microsoft.com/fwlink/?LinkId=245961) (https://go.microsoft.com/fwlink/?LinkId=245961)</span></span>  
  
-   <span data-ttu-id="6bf01-114">[管理 Server Core 安裝：總覽](https://go.microsoft.com/fwlink/?LinkId=245962) (https://go.microsoft.com/fwlink/?LinkId=245962)</span><span class="sxs-lookup"><span data-stu-id="6bf01-114">[Managing a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=245962) (https://go.microsoft.com/fwlink/?LinkId=245962)</span></span>  
  
-   <span data-ttu-id="6bf01-115">[管理 Server Core 安裝](https://go.microsoft.com/fwlink/?LinkId=245963) (https://go.microsoft.com/fwlink/?LinkId=245963)</span><span class="sxs-lookup"><span data-stu-id="6bf01-115">[Administering a Server Core installation](https://go.microsoft.com/fwlink/?LinkId=245963) (https://go.microsoft.com/fwlink/?LinkId=245963)</span></span>  
  
##  <a name="install-updates"></a><span data-ttu-id="6bf01-116">安裝 更新</span><span class="sxs-lookup"><span data-stu-id="6bf01-116">Install updates</span></span>  
 <span data-ttu-id="6bf01-117">本節提供有關在 Windows Server Core 機器上安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="6bf01-117">This section provides information about installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Windows Server Core machine.</span></span> <span data-ttu-id="6bf01-118">我們建議客戶及時評估並安裝最新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新，以便確保系統保持在最新狀態而且具有最新的安全性更新。</span><span class="sxs-lookup"><span data-stu-id="6bf01-118">We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates.</span></span> <span data-ttu-id="6bf01-119">如需 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 Windows Server core 機器上安裝的詳細資訊，請參閱[在 Server Core 上安裝 SQL Server 2014](install-sql-server-on-server-core.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-119">For more information about installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Windows Server Core machine, see [Install SQL Server 2014 on Server Core](install-sql-server-on-server-core.md).</span></span>  
  
 <span data-ttu-id="6bf01-120">以下是安裝產品更新的兩種狀況：</span><span class="sxs-lookup"><span data-stu-id="6bf01-120">The following are the two scenarios for installing product updates:</span></span>  
  
-   [<span data-ttu-id="6bf01-121">在新安裝期間安裝 SQL Server 2014 的更新</span><span class="sxs-lookup"><span data-stu-id="6bf01-121">Installing Updates for SQL Server 2014 During a New Installation</span></span>](#installing-updates-during-a-new-installation) 
  
-   [<span data-ttu-id="6bf01-122">安裝之後安裝 SQL Server 2014 的更新</span><span class="sxs-lookup"><span data-stu-id="6bf01-122">Installing Updates for SQL Server 2014 After It Has Been Installed</span></span>](#installing-updates-after-installation) 
  
### <a name="installing-updates-during-a-new-installation"></a><span data-ttu-id="6bf01-123">在新安裝期間安裝更新</span><span class="sxs-lookup"><span data-stu-id="6bf01-123">Installing updates during a new installation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6bf01-124">安裝程式只支援 Server Core 作業系統上的命令提示字元安裝。</span><span class="sxs-lookup"><span data-stu-id="6bf01-124">Setup supports only command prompt installations on Server Core operating system.</span></span> <span data-ttu-id="6bf01-125">如需詳細資訊，請參閱[從命令提示字元安裝 SQL Server 2014](install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-125">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6bf01-126">安裝程式會整合最新產品更新與主要產品安裝，因此主要產品及其適用的更新可同時安裝。</span><span class="sxs-lookup"><span data-stu-id="6bf01-126">setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span>  
  
 <span data-ttu-id="6bf01-127">安裝程式找到最新版本的可用更新後，會使用目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程序進行下載與整合。</span><span class="sxs-lookup"><span data-stu-id="6bf01-127">After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup process.</span></span> <span data-ttu-id="6bf01-128">產品更新可以引入累計更新、Service Pack，或 Service Pack 加上累計更新。</span><span class="sxs-lookup"><span data-stu-id="6bf01-128">Product Update can pull in a cumulative update, service pack, or service pack plus cumulative update.</span></span>  
  
 <span data-ttu-id="6bf01-129">指定 UpdateEnabled 和 UpdateSource 參數在主要產品安裝中包含最新的產品更新。</span><span class="sxs-lookup"><span data-stu-id="6bf01-129">Specify the UpdateEnabled, and UpdateSource parameters to include the latest product updates with the main product installation.</span></span> <span data-ttu-id="6bf01-130">請參考以下範例，了解如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間啟用產品更新：</span><span class="sxs-lookup"><span data-stu-id="6bf01-130">Refer the following example to enable product updates during the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup:</span></span>  
  
```cmd 
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /UpdateEnabled=True /UpdateSource="<SourcePath>" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
### <a name="installing-updates-after-installation"></a><span data-ttu-id="6bf01-131">安裝之後安裝更新</span><span class="sxs-lookup"><span data-stu-id="6bf01-131">Installing updates after installation</span></span> 
 <span data-ttu-id="6bf01-132">在已安裝的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體上，建議您套用最新的安全性更新和重大更新，包括一般發行版本 (GDR) 和 Service Pack (SP)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-132">On an installed instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you apply the latest security updates and critical updates including General Distribution Releases (GDRs), and Service Packs (SPs).</span></span> <span data-ttu-id="6bf01-133">您應該視需要並依案例採用個別的累計更新和安全性更新。</span><span class="sxs-lookup"><span data-stu-id="6bf01-133">Individual Cumulative updates and security updates should be adopted on a case-by-case, "as-needed" basis.</span></span> <span data-ttu-id="6bf01-134">請評估更新，如有需要，則套用它。</span><span class="sxs-lookup"><span data-stu-id="6bf01-134">Evaluate the update; if it's needed, then apply it.</span></span>  
  
 <span data-ttu-id="6bf01-135">在命令提示字元中套用更新，並以您的更新封裝名稱取代 <package_name>：</span><span class="sxs-lookup"><span data-stu-id="6bf01-135">Apply an update at a command prompt, replacing <package_name> with the name of your update package:</span></span>  
  
-   <span data-ttu-id="6bf01-136">更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的單一執行個體和所有共用元件。</span><span class="sxs-lookup"><span data-stu-id="6bf01-136">Update a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and all shared components.</span></span> <span data-ttu-id="6bf01-137">您可以使用 InstanceName 參數或 InstanceID 參數指定執行個體。</span><span class="sxs-lookup"><span data-stu-id="6bf01-137">You can specify the instance either by using the InstanceName parameter or the InstanceID parameter.</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance  
    ```  
  
-   <span data-ttu-id="6bf01-138">只更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共用元件：</span><span class="sxs-lookup"><span data-stu-id="6bf01-138">Update [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared components only:</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
    ```  
  
-   <span data-ttu-id="6bf01-139">更新電腦上的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體和所有共用元件：</span><span class="sxs-lookup"><span data-stu-id="6bf01-139">Update all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer and all shared components:</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances  
    ```  
  
##  <a name="startstop-sql-server-service"></a><span data-ttu-id="6bf01-140">啟動/停止 SQL Server 服務</span><span class="sxs-lookup"><span data-stu-id="6bf01-140">Start/Stop SQL Server service</span></span>  
 <span data-ttu-id="6bf01-141">[sqlservr 應用程式](../../tools/sqlservr-application.md) 應用程式會在命令提示字元之下，啟動、停止、暫停和繼續執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6bf01-141">The [sqlservr Application](../../tools/sqlservr-application.md) application starts, stops, pauses, and continues an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a command prompt.</span></span>  
  
 <span data-ttu-id="6bf01-142">您也可以使用 Net 服務來啟動及停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="6bf01-142">You can also use Net services to start and stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
## <a name="enable-alwayson-availability-groups"></a><span data-ttu-id="6bf01-143">啟用 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="6bf01-143">Enable AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="6bf01-144">啟用 AlwaysOn 可用性群組是伺服器執行個體將可用性群組做為高可用性和災害復原方案的必要條件。</span><span class="sxs-lookup"><span data-stu-id="6bf01-144">Being enabled for AlwaysOn Availability Groups is a prerequisite for a server instance to use availability groups as a high availability and disaster recovery solution.</span></span> <span data-ttu-id="6bf01-145">如需有關管理 AlwaysOn 可用性群組的詳細資訊，請參閱[啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-145">For more information about managing the AlwaysOn Availability Groups, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
### <a name="using-sql-server-configuration-manager-remotely"></a><span data-ttu-id="6bf01-146">遠端使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="6bf01-146">Using SQL Server Configuration Manager Remotely</span></span>  
 <span data-ttu-id="6bf01-147">這些步驟是為了在執行用戶端版的 [!INCLUDE[win7](../../includes/win7-md.md)] 或更新版本的電腦上以及已安裝伺服器圖形化介面的另一部伺服器上執行 (也就是 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的完整安裝，或是已啟用伺服器圖形化介面功能的 Windows Server 8 安裝)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-147">These steps are meant to be performed on a PC running the client edition of [!INCLUDE[win7](../../includes/win7-md.md)] or later, or another server that has the Server Graphical Shell installed (i.e. a full installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] or a Windows Server 8 installation with the Server Graphical Shell feature enabled).</span></span>  
  
1.  <span data-ttu-id="6bf01-148">開啟 [電腦管理]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-148">Open Computer Management.</span></span> <span data-ttu-id="6bf01-149">若要開啟 [電腦管理]，請執行下列其中一項作業：</span><span class="sxs-lookup"><span data-stu-id="6bf01-149">To open Computer Management do one of the following:</span></span>  
  
    1.  <span data-ttu-id="6bf01-150">在 [!INCLUDE[win7](../../includes/win7-md.md)]、Windows Server 2008 或 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]上：</span><span class="sxs-lookup"><span data-stu-id="6bf01-150">On [!INCLUDE[win7](../../includes/win7-md.md)], Windows Server 2008, or [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="6bf01-151">依序按一下 [開始]、[所有程式]、[系統管理工具]，然後按一下 [電腦管理]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-151">Click Start, click All Programs, click Administrative Tools, and then click Computer Management.</span></span>  
  
        2.  <span data-ttu-id="6bf01-152">依序按一下 [開始] 和 [執行]，並輸入 COMPMGMT.MSC，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-152">Click Start, click Run, type COMPMGMT.MSC, and then click OK.</span></span>  
  
    2.  <span data-ttu-id="6bf01-153">在啟用伺服器圖形化介面的 Windows 8 上：</span><span class="sxs-lookup"><span data-stu-id="6bf01-153">On Windows 8 with Server Graphical Shell enabled:</span></span>  
  
        1.  <span data-ttu-id="6bf01-154">將滑鼠移到畫面的左下角，然後在看到 [開始] 覆疊時，按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="6bf01-154">Move your mouse to the bottom-left corner of the screen and right-click when you see the Start overlay.</span></span>  
  
        2.  <span data-ttu-id="6bf01-155">從操作功能表選取 [電腦管理]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-155">Select Computer Management  from the context menu.</span></span>  
  
2.  <span data-ttu-id="6bf01-156">在主控台樹狀目錄中，以滑鼠右鍵按一下 [電腦管理]，然後按一下 [連線到另一台電腦]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-156">In the console tree, right-click Computer Management, and then click Connect to another computer.</span></span>  
  
3.  <span data-ttu-id="6bf01-157">在 [選取電腦] 對話方塊中，輸入要管理的 Server Core 電腦名稱，或按一下 [瀏覽] 尋找此電腦，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-157">In the Select Computer dialog box, type the name of the Server Core machine that you want to manage, or click Browse to find it, and then click OK.</span></span>  
  
4.  <span data-ttu-id="6bf01-158">在主控台樹狀目錄中，於 Server Core 電腦的 [電腦管理] 底下按一下 [服務與應用程式]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-158">In the console tree, under Computer Management of the Server Core machine, click Services and Applications.</span></span>  
  
5.  <span data-ttu-id="6bf01-159">按兩下 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-159">Double click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
6.  <span data-ttu-id="6bf01-160">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager 中，按一下 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務]，以滑鼠右鍵按一下 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] () ] \<instance name> ，其中 \<instance name> 是您要啟用 AlwaysOn 可用性群組的本機伺服器實例名稱，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-160">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Services, right-click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (\<instance name>), where \<instance name> is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click Properties.</span></span>  
  
7.  <span data-ttu-id="6bf01-161">選取 [AlwaysOn 高可用性] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6bf01-161">Select the AlwaysOn High Availability tab.</span></span>  
  
8.  <span data-ttu-id="6bf01-162">確認 [Windows 容錯移轉叢集名稱] 欄位包含本機容錯移轉叢集節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="6bf01-162">Verify that Windows failover cluster name field contains the name of the local failover cluster node.</span></span> <span data-ttu-id="6bf01-163">如果此欄位為空白，表示此伺服器執行個體目前不支援 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="6bf01-163">If this field is blank, this server instance currently does not support AlwaysOn Availability Groups.</span></span> <span data-ttu-id="6bf01-164">有可能本機電腦不是叢集節點、WSFC 叢集已經關閉，或者此 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本不支援 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="6bf01-164">Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that does not support AlwaysOn Availability Groups.</span></span>  
  
9. <span data-ttu-id="6bf01-165">選取 [啟用 AlwaysOn 可用性群組] 核取方塊，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-165">Select the Enable AlwaysOn Availability Groups check box, and click OK.</span></span>  
  
10. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6bf01-166">組態管理員會儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="6bf01-166">Configuration Manager saves your change.</span></span> <span data-ttu-id="6bf01-167">然後您必須手動重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="6bf01-167">Then, you must manually restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="6bf01-168">這讓您可以選擇最適合您業務需求的重新啟動時間。</span><span class="sxs-lookup"><span data-stu-id="6bf01-168">This enables you to choose a restart time that is best for your business requirements.</span></span> <span data-ttu-id="6bf01-169">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務重新啟動時，AlwaysOn 就會啟用，而且 IsHadrEnabled 伺服器屬性會設定為 1。</span><span class="sxs-lookup"><span data-stu-id="6bf01-169">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be enabled, and the IsHadrEnabled server property will be set to 1.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="6bf01-170">您必須擁有適當的使用者權限，或者必須已被委派目標電腦的適當權限，才能連接該部電腦。</span><span class="sxs-lookup"><span data-stu-id="6bf01-170">You must have the appropriate user rights or you must have been delegated the appropriate authority on the target computer to connect to that computer.</span></span>  
> -   <span data-ttu-id="6bf01-171">您要管理的電腦名稱會出現在主控台樹狀目錄中 [電腦管理] 旁邊的括號內。</span><span class="sxs-lookup"><span data-stu-id="6bf01-171">The name of the computer that you are managing appears in parentheses next to Computer Management in the console tree.</span></span>  
  
### <a name="using-powershell-cmdlets-to-enable-alwayson-availability-groups"></a><span data-ttu-id="6bf01-172">使用 PowerShell 指令程式來啟用 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="6bf01-172">Using PowerShell Cmdlets to Enable AlwaysOn Availability Groups</span></span>

 <span data-ttu-id="6bf01-173">PowerShell 指令程式 Enable-SqlAlwaysOn 是用來在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上啟用 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="6bf01-173">The PowerShell Cmdlet, Enable-SqlAlwaysOn, is used to enable AlwaysOn Availability Group on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6bf01-174">如果在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務執行時啟用 AlwaysOn 可用性群組，就必須重新啟動 Database Engine 服務，才能完成變更。</span><span class="sxs-lookup"><span data-stu-id="6bf01-174">If AlwaysOn Availability Groups is enable while the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is running, the Database Engine service must be restarted for the change to complete.</span></span> <span data-ttu-id="6bf01-175">除非您指定 -Force 參數，否則此 Cmdlet 會詢問您是否想要重新啟動服務。如果取消，就不會進行任何作業。</span><span class="sxs-lookup"><span data-stu-id="6bf01-175">Unless you specify the -Force parameter, the cmdlet prompts you to ask whether you wish to restart the service; if cancelled, no operation occurs.</span></span>  
  
 <span data-ttu-id="6bf01-176">您必須擁有系統管理員權限，才能執行這個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6bf01-176">You must have Administrator permissions to execute this cmdlet.</span></span>  
  
 <span data-ttu-id="6bf01-177">您可以使用下列其中一個語法來針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體啟用 AlwaysOn 可用性群組：</span><span class="sxs-lookup"><span data-stu-id="6bf01-177">You can use one of the following syntaxes to enable AlwaysOn Availability Groups for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```  
Enable-SqlAlwaysOn [-Path <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn -InputObject <Server> [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn [-ServerInstance <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
 <span data-ttu-id="6bf01-178">下列 PowerShell 命令會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體 (機器\執行個體) 上啟用 AlwaysOn 可用性群組：</span><span class="sxs-lookup"><span data-stu-id="6bf01-178">The following PowerShell command enables AlwaysOn Availability Groups on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Machine\Instance):</span></span>  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Machine\Instance  
```  
  
## <a name="configuring-remote-access-of-sql-server-running-on-server-core"></a><span data-ttu-id="6bf01-179">設定在 Server Core 上執行之 SQL Server 的遠端存取</span><span class="sxs-lookup"><span data-stu-id="6bf01-179">Configuring remote access of SQL Server running on Server Core</span></span>  
 <span data-ttu-id="6bf01-180">您可以執行下面描述的動作，來設定在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Server Core SP1 上執行之 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 執行個體的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="6bf01-180">Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance that is running on [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1.</span></span>  
  
### <a name="enable-remote-connections-on-an-instance-of-sql-server"></a><span data-ttu-id="6bf01-181">在 SQL Server 的實例上啟用遠端連線</span><span class="sxs-lookup"><span data-stu-id="6bf01-181">Enable remote connections on an instance of SQL Server</span></span> 
 <span data-ttu-id="6bf01-182">若要啟用遠端連接，請在本機使用 SQLCMD.exe，然後針對 Server Core 執行個體執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="6bf01-182">To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:</span></span>  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-sql-server-browser-service"></a><span data-ttu-id="6bf01-183">啟用及啟動 SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="6bf01-183">Enable and start the SQL Server Browser service</span></span>  
 <span data-ttu-id="6bf01-184">根據預設，Browser 服務是停用的。</span><span class="sxs-lookup"><span data-stu-id="6bf01-184">By default, the Browser service is disabled.</span></span>  <span data-ttu-id="6bf01-185">如果在 Server Core 上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體已停用此服務，請從命令提示字元執行下列命令，以啟用服務：</span><span class="sxs-lookup"><span data-stu-id="6bf01-185">If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on Server Core, run the following command from the command prompt to enable it:</span></span>  
  
 `sc config SQLBROWSER start= auto`  
  
 <span data-ttu-id="6bf01-186">啟用後，請從命令提示字元執行下列命令，以啟動服務：</span><span class="sxs-lookup"><span data-stu-id="6bf01-186">After it is enabled, run the following command from the command prompt to start the service:</span></span>  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a><span data-ttu-id="6bf01-187">在 Windows 防火牆中建立例外狀況</span><span class="sxs-lookup"><span data-stu-id="6bf01-187">Create exceptions in Windows Firewall</span></span>  
 <span data-ttu-id="6bf01-188">若要在 Windows 防火牆中建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取的例外狀況，請遵循 [設定 Windows 防火牆以允許 SQL Server 存取](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)中指定的步驟。</span><span class="sxs-lookup"><span data-stu-id="6bf01-188">To create exceptions for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
### <a name="enable-tcpip-on-an-instance-of-sql-server"></a><span data-ttu-id="6bf01-189">在 SQL Server 的實例上啟用 TCP/IP</span><span class="sxs-lookup"><span data-stu-id="6bf01-189">Enable TCP/IP on an instance of SQL Server</span></span>
 <span data-ttu-id="6bf01-190">您可以針對 Server Core 上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，透過 Windows PowerShell 啟用 TCP/IP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6bf01-190">The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Server Core.</span></span> <span data-ttu-id="6bf01-191">請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6bf01-191">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="6bf01-192">在執行 Windows Server 2008 R2 Server Core SP1 的電腦上，啟動 [工作管理員]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-192">On the computer that is running Windows Server 2008 R2 Server Core SP1, launch Task Manager.</span></span>  
  
2.  <span data-ttu-id="6bf01-193">在 [應用程式] 索引標籤上，按一下 [新工作]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-193">On the **Applications** tab, click **New Task**.</span></span>  
  
3.  <span data-ttu-id="6bf01-194">在 [建立新工作] 對話方塊的 [開啟] 欄位中輸入 **sqlps.exe**，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6bf01-194">In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**.</span></span> <span data-ttu-id="6bf01-195">隨即開啟 [**Microsoft[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="6bf01-195">This opens the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window.</span></span>  
  
4.  <span data-ttu-id="6bf01-196">在 [**Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell**] 視窗中，執行下列指令碼以啟用 TCP/IP 通訊協定：</span><span class="sxs-lookup"><span data-stu-id="6bf01-196">In the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:</span></span>  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = new-object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
##  <a name="sql-server-profiler"></a><span data-ttu-id="6bf01-197">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="6bf01-197">SQL Server Profiler</span></span>  
 <span data-ttu-id="6bf01-198">在遠端電腦上啟動 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，且從 [檔案] 功能表中選取 [新增追蹤] 時，應用程式會顯示一個 [連接到伺服器] 對話方塊，供您指定要連接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 (位於 Server Core 電腦上)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-198">On a remote machine, start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and select New Trace from the File menu, the application displays a Connect to Server dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, residing on the Server Core machine, to which you want to connect.</span></span> <span data-ttu-id="6bf01-199">如需詳細資訊，請參閱 [啟動 SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-199">For more information, see [Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="6bf01-200">如需有關執行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]所需權限的資訊，請參閱 [執行 SQL Server Profiler 所需的權限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-200">For more information on the permissions required to run [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], see [Permissions Required to Run SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="6bf01-201">如需有關 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]的其他詳細資料，請參閱 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-201">For additional details about [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], see [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md).</span></span>  
  
##  <a name="sql-server-auditing"></a><span data-ttu-id="6bf01-202">SQL Server 稽核</span><span class="sxs-lookup"><span data-stu-id="6bf01-202">SQL Server Auditing</span></span>  
 <span data-ttu-id="6bf01-203">您可以在遠端使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 定義稽核。</span><span class="sxs-lookup"><span data-stu-id="6bf01-203">You can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] remotely to define an audit.</span></span> <span data-ttu-id="6bf01-204">在建立及啟用稽核之後，目標將會收到項目。</span><span class="sxs-lookup"><span data-stu-id="6bf01-204">After the audit is created and enabled, the target will receive entries.</span></span> <span data-ttu-id="6bf01-205">如需有關建立和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 稽核，請參閱 [SQL Server Audit &#40;Database Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf01-205">For more information about creating and managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] audits, see [SQL Server Audit &#40;Database Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).</span></span>  
  
##  <a name="sql-servevr-command-prompt-utilities"></a><span data-ttu-id="6bf01-206">SQL Servevr 命令提示字元公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-206">SQL Servevr Command Prompt Utilities</span></span>  
 <span data-ttu-id="6bf01-207">您可以使用下列命令提示字元公用程式，好讓您在 Server Core 電腦上編寫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作業的指令碼。</span><span class="sxs-lookup"><span data-stu-id="6bf01-207">You can use the following command prompt utilities that enable you to script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operations on a Server Core machine.</span></span> <span data-ttu-id="6bf01-208">下表列出 Server Core 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 隨附的命令提示字元公用程式清單：</span><span class="sxs-lookup"><span data-stu-id="6bf01-208">The following table contains a list of command prompt utilities that ship with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Server Core:</span></span>  
  
|<span data-ttu-id="6bf01-209">**公用程式**</span><span class="sxs-lookup"><span data-stu-id="6bf01-209">**Utility**</span></span>|<span data-ttu-id="6bf01-210">**說明**</span><span class="sxs-lookup"><span data-stu-id="6bf01-210">**Description**</span></span>|<span data-ttu-id="6bf01-211">**安裝位置**</span><span class="sxs-lookup"><span data-stu-id="6bf01-211">**Installed in**</span></span>|  
|-----------------|---------------------|----------------------|  
|[<span data-ttu-id="6bf01-212">bcp 公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-212">bcp Utility</span></span>](../../tools/bcp-utility.md)|<span data-ttu-id="6bf01-213">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體和使用者指定之格式的資料檔案之間，用來複製資料。</span><span class="sxs-lookup"><span data-stu-id="6bf01-213">Used to copy data between an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and a data file in a user-specified format.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="6bf01-214">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-214">Tools\Binn</span></span>|  
|[<span data-ttu-id="6bf01-215">dtexec 公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-215">dtexec Utility</span></span>](../../integration-services/packages/dtexec-utility.md)|<span data-ttu-id="6bf01-216">用以設定及執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="6bf01-216">Used to configure and execute an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="6bf01-217">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-217">DTS\Binn</span></span>|  
|[<span data-ttu-id="6bf01-218">dtutil 公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-218">dtutil Utility</span></span>](../../integration-services/dtutil-utility.md)|<span data-ttu-id="6bf01-219">用來管理 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="6bf01-219">Used to manage SSIS packages.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="6bf01-220">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-220">DTS\Binn</span></span>|  
|[<span data-ttu-id="6bf01-221">osql 公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-221">osql Utility</span></span>](../../tools/osql-utility.md)|<span data-ttu-id="6bf01-222">可讓您在命令提示字元之下，輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式、系統程序和指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="6bf01-222">Allows you to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="6bf01-223">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-223">Tools\Binn</span></span>|  
|[<span data-ttu-id="6bf01-224">sqlagent90 應用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-224">sqlagent90 Application</span></span>](../../tools/sqlagent90-application.md)|<span data-ttu-id="6bf01-225">用來從命令提示字元啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="6bf01-225">Used to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent from a command prompt.</span></span>|<span data-ttu-id="6bf01-226">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*執行個體名稱*>\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-226">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*instance_name*>\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="6bf01-227">sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-227">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)|<span data-ttu-id="6bf01-228">可讓您在命令提示字元之下，輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式、系統程序和指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="6bf01-228">Allows you to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="6bf01-229">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-229">Tools\Binn</span></span>|  
|[<span data-ttu-id="6bf01-230">SQLdiag 公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-230">SQLdiag Utility</span></span>](../../tools/sqldiag-utility.md)|<span data-ttu-id="6bf01-231">用以收集可供 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務與支援部門使用的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="6bf01-231">Used to collect diagnostic information for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="6bf01-232">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-232">Tools\Binn</span></span>|  
|[<span data-ttu-id="6bf01-233">sqlmaint 公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-233">sqlmaint Utility</span></span>](../../tools/sqlmaint-utility.md)|<span data-ttu-id="6bf01-234">用來執行舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所建立的資料庫維護計畫。</span><span class="sxs-lookup"><span data-stu-id="6bf01-234">Used to execute database maintenance plans created in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="6bf01-235">\<drive>： \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12。MSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-235">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="6bf01-236">sqlps 公用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-236">sqlps Utility</span></span>](../../tools/sqlps-utility.md)|<span data-ttu-id="6bf01-237">用來執行 PowerShell 命令和指令碼。</span><span class="sxs-lookup"><span data-stu-id="6bf01-237">Used to run PowerShell commands and scripts.</span></span> <span data-ttu-id="6bf01-238">載入並註冊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 提供者和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6bf01-238">Loads and registers the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="6bf01-239">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-239">Tools\Binn</span></span>|  
|[<span data-ttu-id="6bf01-240">sqlservr 應用程式</span><span class="sxs-lookup"><span data-stu-id="6bf01-240">sqlservr Application</span></span>](../../tools/sqlservr-application.md)|<span data-ttu-id="6bf01-241">用來從命令提示字元啟動和停止 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，以進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="6bf01-241">Used to start and stop an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] from the command prompt for troubleshooting.</span></span>|<span data-ttu-id="6bf01-242">\<drive>： \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12。MSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="6bf01-242">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
  
##  <a name="use-troubleshooting-tools"></a><span data-ttu-id="6bf01-243">使用疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="6bf01-243">Use troubleshooting tools</span></span>  
 <span data-ttu-id="6bf01-244">您可以使用 [SQLdiag 公用程式](../../tools/sqldiag-utility.md) ，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和其他類型的伺服器收集記錄檔案和資料檔案，並使用其監視您的伺服器一段時間，或為伺服器的特定問題疑難排解。</span><span class="sxs-lookup"><span data-stu-id="6bf01-244">You can use [SQLdiag Utility](../../tools/sqldiag-utility.md) to collect logs and data files from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers.</span></span> <span data-ttu-id="6bf01-245">SQLdiag 用於加速和簡化 Microsoft 客戶支援服務部門對診斷資訊的收集過程。</span><span class="sxs-lookup"><span data-stu-id="6bf01-245">SQLdiag is intended to expedite and simplify diagnostic information gathering for Microsoft Customer Support Services.</span></span>  
  
 <span data-ttu-id="6bf01-246">您可以在 Server Core 上的系統管理員命令提示字元中，使用 [SQLdiag 公用程式](../../tools/sqldiag-utility.md)主題中指定的語法啟動此公用程式。</span><span class="sxs-lookup"><span data-stu-id="6bf01-246">You can launch the utility on the administrator command prompt on the Server Core, using the syntax specified in the topic: [SQLdiag Utility](../../tools/sqldiag-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf01-247">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bf01-247">See Also</span></span>  
 <span data-ttu-id="6bf01-248">[在 Server Core 上安裝 SQL Server 2014](install-sql-server-on-server-core.md) </span><span class="sxs-lookup"><span data-stu-id="6bf01-248">[Install SQL Server 2014 on Server Core](install-sql-server-on-server-core.md) </span></span>  
 [<span data-ttu-id="6bf01-249">安裝的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="6bf01-249">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
