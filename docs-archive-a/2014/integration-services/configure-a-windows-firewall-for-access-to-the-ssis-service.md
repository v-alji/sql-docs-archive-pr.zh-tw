---
title: 設定 Windows 防火牆以存取 SSIS 服務 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], firewalls
- Windows Firewall [Integration Services]
- unauthorized access [Integration Services]
- Integration Services service, firewalls
- firewall systems [Integration Services]
- SQL Server Integration Services, firewalls
- SSIS, firewalls
ms.assetid: 39975cf2-c351-4205-8c39-27a0fadfb010
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d18b061ce16c88c50bbc08874efec455c28e15a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606994"
---
# <a name="configure-a-windows-firewall-for-access-to-the-ssis-service"></a><span data-ttu-id="4a093-102">針對 SSIS 服務的存取設定 Windows 防火牆</span><span class="sxs-lookup"><span data-stu-id="4a093-102">Configure a Windows Firewall for Access to the SSIS Service</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="4a093-103">本主題會討論 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，即用於管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="4a093-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="4a093-104">支援此服務能與舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]回溯相容。</span><span class="sxs-lookup"><span data-stu-id="4a093-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="4a093-105">從 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]開始，您可以管理 Integration Services 伺服器上的物件，例如封裝。</span><span class="sxs-lookup"><span data-stu-id="4a093-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="4a093-106">Windows 防火牆系統有助於防止未經授權的使用者透過網路連接來存取電腦資源。</span><span class="sxs-lookup"><span data-stu-id="4a093-106">The windowsfirewall system helps prevent unauthorized access to computer resources over a network connection.</span></span> <span data-ttu-id="4a093-107">若要透過此防火牆存取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ，必須設定防火牆來啟用存取。</span><span class="sxs-lookup"><span data-stu-id="4a093-107">To access [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] through this firewall, you have to configure the firewall to enable access.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4a093-108">若要管理儲存在遠端伺服器上的封裝，您不必連接到該遠端伺服器上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務執行個體，</span><span class="sxs-lookup"><span data-stu-id="4a093-108">To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on that remote server.</span></span> <span data-ttu-id="4a093-109">而是要編輯 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務的組態檔，好讓 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 顯示儲存在遠端伺服器上的封裝。</span><span class="sxs-lookup"><span data-stu-id="4a093-109">Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service so that [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] displays the packages that are stored on the remote server.</span></span> <span data-ttu-id="4a093-110">如需詳細資訊，請參閱 [設定 Integration Services 服務 &#40;SSIS 服務&#41;](configuring-the-integration-services-service-ssis-service.md)回溯相容。</span><span class="sxs-lookup"><span data-stu-id="4a093-110">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](configuring-the-integration-services-service-ssis-service.md).</span></span>  
  
 <span data-ttu-id="4a093-111">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務使用 DCOM 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4a093-111">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service uses the DCOM protocol.</span></span> <span data-ttu-id="4a093-112">如需 DCOM 通訊協定如何透過防火牆運作的詳細資訊，請參閱「搭配[防火牆使用分散式 COM](https://manualzz.com/doc/19762578/using-distributed-com-with-firewalls-by-michael-nelson-in...)」一文。</span><span class="sxs-lookup"><span data-stu-id="4a093-112">For more information about how the DCOM protocol works through firewalls, see the article, "[Using Distributed COM with Firewalls](https://manualzz.com/doc/19762578/using-distributed-com-with-firewalls-by-michael-nelson-in...)".</span></span>  
  
 <span data-ttu-id="4a093-113">有許多防火牆系統可用。</span><span class="sxs-lookup"><span data-stu-id="4a093-113">There are many firewall systems available.</span></span> <span data-ttu-id="4a093-114">如果您是執行 Windows 防火牆以外的其他防火牆，請參閱該防火牆的文件以獲取您正在使用之系統的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="4a093-114">If you are running a firewall other than windowsfirewall, see your firewall documentation for information that is specific to the system you are using.</span></span>  
  
 <span data-ttu-id="4a093-115">如果防火牆支援應用程式層級篩選，您可以使用 Windows 提供的使用者介面，指定允許穿越防火牆的例外狀況，例如程式和服務。</span><span class="sxs-lookup"><span data-stu-id="4a093-115">If the firewall supports application-level filtering, you can use the user interface that Windows provides to specify the exceptions that are allowed through the firewall, such as programs and services.</span></span> <span data-ttu-id="4a093-116">否則，您必須設定 DCOM 使用有限的一組 TCP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="4a093-116">Otherwise, you have to configure DCOM to use a limited set of TCP ports.</span></span> <span data-ttu-id="4a093-117">上一段落提供的 Microsoft 網站連結包含有關如何指定所要使用之 TCP 通訊埠的資訊。</span><span class="sxs-lookup"><span data-stu-id="4a093-117">The Microsoft website link previously provided includes information about how to specify the TCP ports to use.</span></span>  
  
 <span data-ttu-id="4a093-118">Integration Services 服務使用通訊埠 135，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="4a093-118">The Integration Services service uses port 135, and the port cannot be changed.</span></span> <span data-ttu-id="4a093-119">您必須開啟 TCP 通訊埠 135 供服務控制管理員 (SCM) 存取。</span><span class="sxs-lookup"><span data-stu-id="4a093-119">You have to open TCP port 135 for access to the service control manager (SCM).</span></span> <span data-ttu-id="4a093-120">SCM 會執行工作，例如啟動和停止 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，以及將控制要求傳送至執行中服務。</span><span class="sxs-lookup"><span data-stu-id="4a093-120">SCM performs tasks such as starting and stopping [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] services and transmitting control requests to the running service.</span></span>  
  
 <span data-ttu-id="4a093-121">下一節內容為適用於 Windows 防火牆的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="4a093-121">The information in the following section is specific to windowsfirewall.</span></span> <span data-ttu-id="4a093-122">您可以在命令提示字元下執行命令，或在 Windows 防火牆對話方塊中設定屬性，來設定 Windows 防火牆系統。</span><span class="sxs-lookup"><span data-stu-id="4a093-122">You can configure the windowsfirewall system by running a command at the command prompt, or by setting properties in the windowsfirewall dialog box.</span></span>  
  
 <span data-ttu-id="4a093-123">如需預設 Windows 防火牆設定的詳細資訊，以及影響 Database Engine、Analysis Services、Reporting Services 和 Integration Services 之 TCP 通訊埠的描述，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="4a093-123">For more information about the default windowsfirewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="configuring-a-windowsfirewall"></a><span data-ttu-id="4a093-124">設定 Windows 防火牆</span><span class="sxs-lookup"><span data-stu-id="4a093-124">Configuring a windowsfirewall</span></span>  
 <span data-ttu-id="4a093-125">您可以使用下列命令來開啟 TCP 通訊埠 135，將 MsDtsSrvr.exe 加入至例外狀況清單，並指定防火牆的不封鎖範圍。</span><span class="sxs-lookup"><span data-stu-id="4a093-125">You can use the following commands to open TCP port 135, add MsDtsSrvr.exe to the exception list, and specify the scope of unblocking for the firewall.</span></span>  
  
#### <a name="to-configure-a-windowsfirewall-using-the-command-prompt-window"></a><span data-ttu-id="4a093-126">若要使用命令提示字元視窗設定 Windows 防火牆</span><span class="sxs-lookup"><span data-stu-id="4a093-126">To configure a windowsfirewall using the Command Prompt window</span></span>  
  
1.  <span data-ttu-id="4a093-127">執行命令：`netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET`</span><span class="sxs-lookup"><span data-stu-id="4a093-127">Run the command: `netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET`</span></span>  
  
2.  <span data-ttu-id="4a093-128">執行命令：`netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET`</span><span class="sxs-lookup"><span data-stu-id="4a093-128">Run the command: `netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET`</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a093-129">若要為所有電腦以及網際網路上的電腦開啟防火牆，請以 scope=ALL 取代 scope=SUBNET。</span><span class="sxs-lookup"><span data-stu-id="4a093-129">To open the firewall for all computers, and also for computers on the Internet, replace scope=SUBNET with scope=ALL.</span></span>  
  
 <span data-ttu-id="4a093-130">下列程序描述如何使用 Windows 使用者介面來開啟 TCP 通訊埠 135，將 MsDtsSrvr.exe 加入例外狀況清單中，並指定防火牆的不封鎖範圍。</span><span class="sxs-lookup"><span data-stu-id="4a093-130">The following procedure describes how to use the Windows user interface to open TCP port 135, add MsDtsSrvr.exe to the exception list, and specify the scope of unblocking for the firewall.</span></span>  
  
#### <a name="to-configure-a-firewall-using-the-windowsfirewall-dialog-box"></a><span data-ttu-id="4a093-131">若要使用 Windows 防火牆對話方塊設定防火牆</span><span class="sxs-lookup"><span data-stu-id="4a093-131">To configure a firewall using the windowsfirewall dialog box</span></span>  
  
1.  <span data-ttu-id="4a093-132">在 [控制台] 中按兩下 [Windows 防火牆]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a093-132">In the Control Panel, double-click **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="4a093-133">在 **[Windows 防火牆]** 對話方塊中，按一下 **[例外狀況]** 索引標籤，然後再按一下 **[加入程式]**。</span><span class="sxs-lookup"><span data-stu-id="4a093-133">In the **Windows Firewall** dialog box, click the **Exceptions** tab and then click **Add Program.**</span></span>  
  
3.  <span data-ttu-id="4a093-134">在 [新增程式]\*\*\*\* 對話方塊中，按一下 [瀏覽]\*\*\*\* 巡覽至 Program Files\Microsoft SQL Server\100\DTS\Binn 資料夾，然後按一下 MsDtsSrvr.exe，再按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a093-134">In the **Add a Program** dialog box, **click Browse**, navigate to the Program Files\Microsoft SQL Server\100\DTS\Binn folder, click MsDtsSrvr.exe, and then click **Open**.</span></span> <span data-ttu-id="4a093-135">按一下 **[確定]** 以關閉 **[新增程式]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4a093-135">Click **OK** to close the **Add a Program** dialog box.</span></span>  
  
4.  <span data-ttu-id="4a093-136">在 **[例外狀況]** 索引標籤上，按一下 **[新增連接埠]**。</span><span class="sxs-lookup"><span data-stu-id="4a093-136">On the **Exceptions** tab, click **Add Port.**</span></span>  
  
5.  <span data-ttu-id="4a093-137">在 [新增連接埠]\*\*\*\* 對話方塊的 [名稱]\*\*\*\* 方塊中，輸入 **RPC(TCP/135)** 或其他描述性名稱，在 [連接埠編號]\*\*\*\* 方塊中輸入 **135**，然後選取 [TCP]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a093-137">In the **Add a Port** dialog box, type **RPC(TCP/135)** or another descriptive name in the **Nam**e box, type **135** in the **Port Number** box, and then select **TCP**.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="4a093-138">服務會一直使用通訊埠 135。</span><span class="sxs-lookup"><span data-stu-id="4a093-138">service always uses port 135.</span></span> <span data-ttu-id="4a093-139">您無法指定不同的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="4a093-139">You cannot specify a different port.</span></span>  
  
6.  <span data-ttu-id="4a093-140">在 **[新增連接埠]** 對話方塊中，可以選擇性地按一下 **[變更範圍]** 以修改預設範圍。</span><span class="sxs-lookup"><span data-stu-id="4a093-140">In the **Add a Port** dialog box, you can optionally click **Change Scope** to modify the default scope.</span></span>  
  
7.  <span data-ttu-id="4a093-141">在 [變更範圍]\*\*\*\* 對話方塊中，選取 [只有我的網路 (子網路)]\*\*\*\* 或輸入自訂清單，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a093-141">In the **Change Scope** dialog box, select **My network (subnet only)** or type a custom list, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="4a093-142">若要關閉 **[新增連接埠]** 對話方塊，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4a093-142">To close the **Add a Port** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="4a093-143">若要關閉 **[Windows 防火牆]** 對話方塊，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4a093-143">To close the **Windows Firewall** dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a093-144">此程序是使用 [控制台] 中的 **[Windows 防火牆]** 項目設定 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="4a093-144">To configure the windowsfirewall, this procedure uses the **Windows Firewall** item in Control Panel.</span></span> <span data-ttu-id="4a093-145">**[Windows 防火牆]** 項目只會針對目前網路位置設定檔來設定防火牆。</span><span class="sxs-lookup"><span data-stu-id="4a093-145">The **Windows Firewall** item only configures the firewall for the current network location profile.</span></span> <span data-ttu-id="4a093-146">但若要設定 Windows 防火牆，您也可以使用 **netsh** 命令列工具或是 [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC) 嵌入式管理單元，名為「具有進階安全性的 Windows 防火牆」。</span><span class="sxs-lookup"><span data-stu-id="4a093-146">However, you can also configure the windowsfirewall by using the **netsh** command line tool or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC) snap-in named windowsfirewall with Advanced Security.</span></span> <span data-ttu-id="4a093-147">如需這些工具的詳細資訊，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="4a093-147">For more information about these tools, see [Configure the Windows Firewall to Allow SQL Server Access](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a093-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a093-148">See Also</span></span>  
 <span data-ttu-id="4a093-149">[設定 Integration Services 服務 &#40;SSIS 服務&#41;](service/integration-services-service-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="4a093-149">[Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md) </span></span>  
 [<span data-ttu-id="4a093-150">Integration Services 服務 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="4a093-150">Integration Services Service &#40;SSIS Service&#41;</span></span>](service/integration-services-service-ssis-service.md)  
  
  
