---
title: 設定用於資料庫引擎存取的 Windows 防火牆 | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], firewall systems
- firewall systems, [Database Engine]
- security [SQL Server], firewalls
ms.assetid: 0093b43c-c6b5-4574-9b30-3a0e91e1a1f9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f76eecb4dd48f3e7f54cad79953773f8432f416e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607103"
---
# <a name="configure-a-windows-firewall-for-database-engine-access"></a><span data-ttu-id="6778d-102">設定用於 Database Engine 存取的 Windows 防火牆</span><span class="sxs-lookup"><span data-stu-id="6778d-102">Configure a Windows Firewall for Database Engine Access</span></span>
  <span data-ttu-id="6778d-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定用於 Database Engine 存取的 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="6778d-103">This topic describes how to configure a Windows firewall for Database Engine access in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="6778d-104">防火牆系統有助於預防未經授權存取電腦資源。</span><span class="sxs-lookup"><span data-stu-id="6778d-104">Firewall systems help prevent unauthorized access to computer resources.</span></span> <span data-ttu-id="6778d-105">若要透過防火牆存取 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，您必須在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之電腦上的防火牆設定為允許存取。</span><span class="sxs-lookup"><span data-stu-id="6778d-105">To access an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] through a firewall, you must configure the firewall on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to allow access.</span></span>  
  
 <span data-ttu-id="6778d-106">如需預設 Windows 防火牆設定的詳細資訊以及影響 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、Analysis Services、Reporting Services 和 Integration Services 之 TCP 通訊埠的描述，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="6778d-106">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span> <span data-ttu-id="6778d-107">有許多防火牆系統可用。</span><span class="sxs-lookup"><span data-stu-id="6778d-107">There are many firewall systems available.</span></span> <span data-ttu-id="6778d-108">如需系統專用的資訊，請參閱防火牆文件集。</span><span class="sxs-lookup"><span data-stu-id="6778d-108">For information specific to your system, see the firewall documentation.</span></span>  
  
 <span data-ttu-id="6778d-109">允許存取的主要步驟包括：</span><span class="sxs-lookup"><span data-stu-id="6778d-109">The principal steps to allow access are:</span></span>  
  
1.  <span data-ttu-id="6778d-110">將 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 設定為使用特定 TCP/IP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="6778d-110">Configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to use a specific TCP/IP port.</span></span> <span data-ttu-id="6778d-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的預設執行個體會使用 1433 通訊埠，不過這是可以變更的。</span><span class="sxs-lookup"><span data-stu-id="6778d-111">The default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] uses port 1433, but that can be changed.</span></span> <span data-ttu-id="6778d-112">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 所使用的通訊埠列在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="6778d-112">The port used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span> <span data-ttu-id="6778d-113">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]、[!INCLUDE[ssEW](../../includes/ssew-md.md)] 的執行個體及 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的具名執行個體都使用動態通訊埠。</span><span class="sxs-lookup"><span data-stu-id="6778d-113">Instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)], and named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] use dynamic ports.</span></span> <span data-ttu-id="6778d-114">若要將這些執行個體都設定為使用特定通訊埠，請參閱[設定伺服器接聽特定 TCP 通訊埠 &#40;SQL Server 組態管理員&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md)。</span><span class="sxs-lookup"><span data-stu-id="6778d-114">To configure these instances to use a specific port, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).</span></span>  
  
2.  <span data-ttu-id="6778d-115">針對經過授權的使用者或電腦，將防火牆設定為允許存取該通訊埠。</span><span class="sxs-lookup"><span data-stu-id="6778d-115">Configure the firewall to allow access to that port for authorized users or computers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6778d-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務可讓使用者連接至並未接聽通訊埠 1433 的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，而不用知道通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="6778d-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service lets users connect to instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that are not listening on port 1433, without knowing the port number.</span></span> <span data-ttu-id="6778d-117">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser，您必須開啟 UDP 通訊埠 1434。</span><span class="sxs-lookup"><span data-stu-id="6778d-117">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, you must open UDP port 1434.</span></span> <span data-ttu-id="6778d-118">若要提升至最安全的環境，請將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務保留在停止狀態，並將用戶端設定為使用此通訊埠編號連接。</span><span class="sxs-lookup"><span data-stu-id="6778d-118">To promote the most secure environment, leave the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service stopped, and configure clients to connect using the port number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6778d-119">根據預設， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 會啟用 Windows 防火牆，它會關閉通訊埠 1433 來防止網際網路電腦連接到您電腦上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="6778d-119">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows enables the Windows Firewall, which closes port 1433 to prevent Internet computers from connecting to a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on your computer.</span></span> <span data-ttu-id="6778d-120">除非您重新開啟通訊埠 1433，否則無法使用 TCP/IP 連接至預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="6778d-120">Connections to the default instance using TCP/IP are not possible unless you reopen port 1433.</span></span> <span data-ttu-id="6778d-121">下列程序將說明設定 Windows 防火牆的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="6778d-121">The basic steps to configure the Windows firewall are provided in the following procedures.</span></span> <span data-ttu-id="6778d-122">如需詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="6778d-122">For more information, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="6778d-123">除了將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為接聽固定通訊埠並開啟此通訊埠以外，您也可以列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可執行檔 (Sqlservr.exe) 做為被封鎖程式的例外。</span><span class="sxs-lookup"><span data-stu-id="6778d-123">As an alternative to configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a fixed port and opening the port, you can list the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable (Sqlservr.exe) as an exception to the blocked programs.</span></span> <span data-ttu-id="6778d-124">當您想要繼續使用動態通訊埠時，請使用此方法。</span><span class="sxs-lookup"><span data-stu-id="6778d-124">Use this method when you want to continue to use dynamic ports.</span></span> <span data-ttu-id="6778d-125">不過，這個方法只能存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其中一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="6778d-125">Only one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be accessed in this way.</span></span>  
  
 <span data-ttu-id="6778d-126">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6778d-126">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6778d-127">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6778d-127">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6778d-128">安全性</span><span class="sxs-lookup"><span data-stu-id="6778d-128">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6778d-129">**使用下列工具設定用於資料庫引擎存取的 Windows 防火牆：**</span><span class="sxs-lookup"><span data-stu-id="6778d-129">**To configure a Windows Firewall for Database Engine access, using:**</span></span>  
  
     [<span data-ttu-id="6778d-130">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="6778d-130">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
## <a name="before-you-begin"></a><span data-ttu-id="6778d-131">開始之前</span><span class="sxs-lookup"><span data-stu-id="6778d-131">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6778d-132">Security</span><span class="sxs-lookup"><span data-stu-id="6778d-132">Security</span></span>  
 <span data-ttu-id="6778d-133">在防火牆中開啟通訊埠可能會讓您的伺服器面臨惡意攻擊的威脅。</span><span class="sxs-lookup"><span data-stu-id="6778d-133">Opening ports in your firewall can leave your server exposed to malicious attacks.</span></span> <span data-ttu-id="6778d-134">請先確定您已了解防火牆系統，然後再開啟通訊埠。</span><span class="sxs-lookup"><span data-stu-id="6778d-134">Make sure that you understand firewall systems before you open ports.</span></span> <span data-ttu-id="6778d-135">如需相關資訊，請參閱 [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)</span><span class="sxs-lookup"><span data-stu-id="6778d-135">For more information, see [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6778d-136">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="6778d-136">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="6778d-137">適用於 Windows Vista、Windows 7 和 Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="6778d-137">Applies to Windows Vista, Windows 7, and Windows Server 2008</span></span>  
  
 <span data-ttu-id="6778d-138">下列程序使用「具有進階安全性的 Windows 防火牆」Microsoft Management Console (MMC) 嵌入式管理單元設定 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="6778d-138">The following procedures configure the Windows Firewall by using the Windows Firewall with Advanced Security Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="6778d-139">「具有進階安全性的 Windows 防火牆」只會設定目前的設定檔。</span><span class="sxs-lookup"><span data-stu-id="6778d-139">The Windows Firewall with Advanced Security only configures the current profile.</span></span> <span data-ttu-id="6778d-140">如需 [具有進階安全性的 Windows 防火牆] 的詳細資訊，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)</span><span class="sxs-lookup"><span data-stu-id="6778d-140">For more information about the Windows Firewall with Advanced Security, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)</span></span>  
  
#### <a name="to-open-a-port-in-the-windows-firewall-for-tcp-access"></a><span data-ttu-id="6778d-141">若要在 Windows 防火牆中開啟通訊埠以便 TCP 存取</span><span class="sxs-lookup"><span data-stu-id="6778d-141">To open a port in the Windows firewall for TCP access</span></span>  
  
1.  <span data-ttu-id="6778d-142">在 **[開始]** 功能表上、按一下 **[執行]** ，輸入 **WF.msc**，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-142">On the **Start** menu, click **Run**, type **WF.msc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="6778d-143">在 **[具有進階安全性的 Windows 防火牆]** 的左窗格中，以滑鼠右鍵按一下 **[輸入規則]** ，然後按一下動作窗格中的 **[新增規則]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-143">In the **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then click **New Rule** in the action pane.</span></span>  
  
3.  <span data-ttu-id="6778d-144">在 **[規則類型]** 對話方塊中，選取 **[通訊埠]** ，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-144">In the **Rule Type** dialog box, select **Port**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="6778d-145">在 **[通訊協定及連接埠]** 對話方塊中，選取 **[TCP]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-145">In the **Protocol and Ports** dialog box, select **TCP**.</span></span> <span data-ttu-id="6778d-146">選取 [**特定本機埠**]，然後輸入實例的通訊埠編號 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，例如 `1433` [預設實例]。</span><span class="sxs-lookup"><span data-stu-id="6778d-146">Select **Specific local ports**, and then type the port number of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], such as `1433` for the default instance.</span></span> <span data-ttu-id="6778d-147">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="6778d-147">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="6778d-148">在 **[執行動作]** 對話方塊中，選取 **[允許連線]** ，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-148">In the **Action** dialog box, select **Allow the connection**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="6778d-149">在 **[設定檔]** 對話方塊中，選取您想要連線至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]時，描述電腦連線環境的設定檔，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-149">In the **Profile** dialog box, select any profiles that describe the computer connection environment when you want to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="6778d-150">在 [名稱] 對話方塊中輸入此規則的名稱和描述，然後按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="6778d-150">In the **Name** dialog box, type a name and description for this rule, and then click **Finish**.</span></span>  
  
#### <a name="to-open-access-to-sql-server-when-using-dynamic-ports"></a><span data-ttu-id="6778d-151">若要在使用動態通訊埠時開放 SQL Server 的存取</span><span class="sxs-lookup"><span data-stu-id="6778d-151">To open access to SQL Server when using dynamic ports</span></span>  
  
1.  <span data-ttu-id="6778d-152">在 **[開始]** 功能表上、按一下 **[執行]** ，輸入 **WF.msc**，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-152">On the **Start** menu, click **Run**, type **WF.msc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="6778d-153">在 **[具有進階安全性的 Windows 防火牆]** 的左窗格中，以滑鼠右鍵按一下 **[輸入規則]** ，然後按一下動作窗格中的 **[新增規則]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-153">In the **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then click **New Rule** in the action pane.</span></span>  
  
3.  <span data-ttu-id="6778d-154">在 **[規則類型]** 對話方塊中，選取 **[程式]** ，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-154">In the **Rule Type** dialog box, select **Program**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="6778d-155">在 **[程式]** 對話方塊中，選取 **[這個程式路徑]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-155">In the **Program** dialog box, select **This program path**.</span></span> <span data-ttu-id="6778d-156">按一下 **[瀏覽]** ，並導覽至您想要透過防火牆存取的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，然後按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-156">Click **Browse**, and navigate to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to access through the firewall, and then click **Open**.</span></span> <span data-ttu-id="6778d-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設位於 **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe**。</span><span class="sxs-lookup"><span data-stu-id="6778d-157">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is at **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe**.</span></span> <span data-ttu-id="6778d-158">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="6778d-158">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="6778d-159">在 **[執行動作]** 對話方塊中，選取 **[允許連線]** ，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-159">In the **Action** dialog box, select **Allow the connection**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="6778d-160">在 **[設定檔]** 對話方塊中，選取您想要連線至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]時，描述電腦連線環境的設定檔，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="6778d-160">In the **Profile** dialog box, select any profiles that describe the computer connection environment when you want to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="6778d-161">在 [名稱] 對話方塊中輸入此規則的名稱和描述，然後按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="6778d-161">In the **Name** dialog box, type a name and description for this rule, and then click **Finish**.</span></span>  
  
  
