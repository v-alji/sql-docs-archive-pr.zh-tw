---
title: 設定供報表伺服器存取的防火牆 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b578c980522d24f5a24a73fdfd080ec425335aac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597609"
---
# <a name="configure-a-firewall-for-report-server-access"></a><span data-ttu-id="616f2-102">Configure a Firewall for Report Server Access</span><span class="sxs-lookup"><span data-stu-id="616f2-102">Configure a Firewall for Report Server Access</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="616f2-103">報表伺服器應用程式和發行的報表是透過指定 IP 位址、通訊埠和虛擬目錄的 URL 來加以存取。</span><span class="sxs-lookup"><span data-stu-id="616f2-103">Report server applications and published reports are accessed through URLs that specify an IP address, port, and virtual directory.</span></span> <span data-ttu-id="616f2-104">如果開啟了 Windows 防火牆，則設定報表伺服器使用的通訊埠很可能已關閉。</span><span class="sxs-lookup"><span data-stu-id="616f2-104">If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed.</span></span> <span data-ttu-id="616f2-105">當要求報表之後出現空白網頁，或是當您從遠端用戶端電腦嘗試開啟報表管理員時出現空白網頁，就表示某個通訊埠編號可能已關閉。</span><span class="sxs-lookup"><span data-stu-id="616f2-105">Indications that a port might be closed are the appearance of a blank Web page after requesting a report, or a blank page when you attempt to open Report Manager from a remote client computer.</span></span>  
  
 <span data-ttu-id="616f2-106">若要開啟通訊埠，您必須在報表伺服器電腦上使用 Windows 防火牆公用程式。</span><span class="sxs-lookup"><span data-stu-id="616f2-106">To open a port, you must use the Windows Firewall utility on the report server computer.</span></span> <span data-ttu-id="616f2-107">Reporting Services 將不會為您開啟通訊埠，您必須手動執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="616f2-107">Reporting Services will not open ports for you; you must perform this step manually.</span></span>  
  
 <span data-ttu-id="616f2-108">根據預設，報表伺服器會接聽通訊埠 80 上的 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="616f2-108">By default, the report server listens for HTTP requests on port 80.</span></span> <span data-ttu-id="616f2-109">因此，下列指示包含了指定該通訊埠的步驟。</span><span class="sxs-lookup"><span data-stu-id="616f2-109">As such, the following instructions include steps that specify that port.</span></span> <span data-ttu-id="616f2-110">如果您設定報表伺服器 URL 使用不同的通訊埠，當您遵循底下的指示進行時，就必須指定該通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="616f2-110">If you configured the report server URLs to use a different port, you must specify that port number when following the instructions below.</span></span>  
  
 <span data-ttu-id="616f2-111">如果您要存取外部電腦上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 關聯式資料庫，或者報表伺服器資料庫位於外部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上，您就必須開啟外部電腦上的通訊埠 1433 和 1434。</span><span class="sxs-lookup"><span data-stu-id="616f2-111">If you are accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational databases on external computers, or if the report server database is on an external [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, you must open port 1433 and 1434 on the external computer.</span></span> <span data-ttu-id="616f2-112">如需詳細資訊，請參閱《 [線上叢書》的](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) 設定用於 Database Engine 存取的 Windows 防火牆 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="616f2-112">For more information, see [Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="616f2-113">如需預設 Windows 防火牆設定的詳細資訊，以及影響 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]之 TCP 通訊埠的描述，請參閱《 [線上叢書》中的](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) 設定 Windows 防火牆以允許 SQL Server 存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="616f2-113">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="616f2-114">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="616f2-114">Prerequisites</span></span>  
 <span data-ttu-id="616f2-115">這些指示假設您已經為報表伺服器 Web 服務和報表管理員設定服務帳戶、建立報表伺服器資料庫及設定 URL。</span><span class="sxs-lookup"><span data-stu-id="616f2-115">These instructions assume that you already configured the service account, created the report server database, and configured URLs for the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="616f2-116">如需詳細資訊，請參閱 [管理 Reporting Services 原生模式報表伺服器](manage-a-reporting-services-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="616f2-116">For more information, see [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="616f2-117">您也應該已經確認，報表伺服器可透過本機報表伺服器執行個體的本機網頁瀏覽器連接來加以存取。</span><span class="sxs-lookup"><span data-stu-id="616f2-117">You should also have verified that the report server is accessible over a local Web browser connection to the local report server instance.</span></span> <span data-ttu-id="616f2-118">此步驟會確認您有使用中的安裝。</span><span class="sxs-lookup"><span data-stu-id="616f2-118">This step establishes that you have a working installation.</span></span> <span data-ttu-id="616f2-119">在您開始開啟通訊埠之前，應該先確認安裝已正確設定。</span><span class="sxs-lookup"><span data-stu-id="616f2-119">You should verify that the installation is configured correctly before you begin opening ports.</span></span> <span data-ttu-id="616f2-120">若要在 Windows Server 上完成這個步驟，您也必須已經將報表伺服器網站加入至 [信任的網站]。</span><span class="sxs-lookup"><span data-stu-id="616f2-120">To complete this step on  Windows Server, you must have also added the report server site to Trusted Sites.</span></span> <span data-ttu-id="616f2-121">如需詳細資訊，請參閱 [設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="616f2-121">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="opening-ports-in-windows-firewall"></a><span data-ttu-id="616f2-122">在 Windows 防火牆中開啟通訊埠</span><span class="sxs-lookup"><span data-stu-id="616f2-122">Opening Ports in Windows Firewall</span></span>  
 <span data-ttu-id="616f2-123">不同版本的 Windows 防火牆有不同的指示。</span><span class="sxs-lookup"><span data-stu-id="616f2-123">There are separate instructions for different versions of Windows Firewall.</span></span>  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a><span data-ttu-id="616f2-124">在 Windows 7、Windows Server 2008 R2、Windows Server 2012 和 2012 R2 上開啟通訊埠 80</span><span class="sxs-lookup"><span data-stu-id="616f2-124">To open port 80 on Windows 7, Windows Server 2008 R2, Windows Server 2012 and 2012 R2</span></span>  
  
1.  <span data-ttu-id="616f2-125">在 **[開始]** 功能表中，按一下 **[控制台]**、按一下 **[系統及安全性]**，然後按一下 **[Windows 防火牆]**。</span><span class="sxs-lookup"><span data-stu-id="616f2-125">From the **Start** menu, click **Control Panel**, click **System and Security**, and then click **Windows Firewall**.</span></span> <span data-ttu-id="616f2-126">如果 [控制台] 沒有設定為「類別目錄」檢視，您只需要選取 **[Windows 防火牆]**。</span><span class="sxs-lookup"><span data-stu-id="616f2-126">Control Panel is not configured for 'Category' view, you only need to select **Windows Firewall.**</span></span>  
  
2.  <span data-ttu-id="616f2-127">按一下 [進階設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="616f2-127">Click **Advanced Settings**.</span></span>  
  
3.  <span data-ttu-id="616f2-128">按一下 **[輸入規則]**。</span><span class="sxs-lookup"><span data-stu-id="616f2-128">Click **Inbound Rules.**</span></span>  
  
4.  <span data-ttu-id="616f2-129">在 **[動作]** 視窗中，按一下 **[新增規則]** 。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="616f2-129">Click **New Rule** in the **Actions** window **.**</span></span>  
  
5.  <span data-ttu-id="616f2-130">按一下 **[連接埠]** 的 **[規則類型]**。</span><span class="sxs-lookup"><span data-stu-id="616f2-130">Click **Rule Type** of **Port.**</span></span>  
  
6.  <span data-ttu-id="616f2-131">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="616f2-131">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="616f2-132">在 **[通訊協定及連接埠]** 頁面上，按一下 **[TCP]**。</span><span class="sxs-lookup"><span data-stu-id="616f2-132">On the **Protocol and Ports** page click **TCP**.</span></span>  
  
8.  <span data-ttu-id="616f2-133">選取 **[特定本機連接埠]** ，然後輸入值： **80**。</span><span class="sxs-lookup"><span data-stu-id="616f2-133">Select **Specific Local Ports** and type a value of **80**.</span></span>  
  
9. <span data-ttu-id="616f2-134">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="616f2-134">Click **Next**.</span></span>  
  
10. <span data-ttu-id="616f2-135">在 **[動作]** 頁面上，按一下 **[允許該連線]**。</span><span class="sxs-lookup"><span data-stu-id="616f2-135">On the **Action** page click **Allow the connection**.</span></span>  
  
11. <span data-ttu-id="616f2-136">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="616f2-136">Click **Next**.</span></span>  
  
12. <span data-ttu-id="616f2-137">在 **[設定檔]** 頁面上，按一下適用於您環境的選項。</span><span class="sxs-lookup"><span data-stu-id="616f2-137">On the **Profile** page click the appropriate options for your environment.</span></span>  
  
13. <span data-ttu-id="616f2-138">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="616f2-138">Click **Next**.</span></span>  
  
14. <span data-ttu-id="616f2-139">在 [名稱]\*\*\*\* 頁面上，輸入名稱：**ReportServer (TCP 在連接埠 80 上)**</span><span class="sxs-lookup"><span data-stu-id="616f2-139">On the **Name** page enter a name of**ReportServer (TCP on port 80)**</span></span>  
  
15. <span data-ttu-id="616f2-140">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="616f2-140">Click **Finish**.</span></span>  
  
16. <span data-ttu-id="616f2-141">重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="616f2-141">Restart the computer.</span></span>  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a><span data-ttu-id="616f2-142">若要在 Windows Vista 或 Windows Server 2008 上開啟通訊埠 80</span><span class="sxs-lookup"><span data-stu-id="616f2-142">To open port 80 on Windows Vista or Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="616f2-143">在 [**開始**] 功能表中，按一下 [**控制台**]，按一下 [**安全性**]，然後按一下 [ **Windows 防火牆**]。</span><span class="sxs-lookup"><span data-stu-id="616f2-143">From the **Start** menu, click **Control Panel**, click **Security**, and then click **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="616f2-144">按一下 [**允許程式通過 Windows 防火牆**]。</span><span class="sxs-lookup"><span data-stu-id="616f2-144">Click **Allow a program through Windows Firewall**.</span></span>  
  
3.  <span data-ttu-id="616f2-145">按一下 **[繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="616f2-145">Click **Continue**.</span></span>  
  
4.  <span data-ttu-id="616f2-146">在 [例外] 索引標籤上，按一下 [**新增埠**]。</span><span class="sxs-lookup"><span data-stu-id="616f2-146">On the Exceptions tab, click **Add Port**.</span></span>  
  
5.  <span data-ttu-id="616f2-147">在 [名稱] 中，輸入\*\*ReportServer (TCP on 埠 80) \*\*。</span><span class="sxs-lookup"><span data-stu-id="616f2-147">In Name, type **ReportServer (TCP on port 80)**.</span></span>  
  
6.  <span data-ttu-id="616f2-148">在 [埠號碼] 中，輸入**80**。</span><span class="sxs-lookup"><span data-stu-id="616f2-148">In Port number, type **80**.</span></span>  
  
7.  <span data-ttu-id="616f2-149">確認已選取 [ **TCP** ]。</span><span class="sxs-lookup"><span data-stu-id="616f2-149">Verify that **TCP** is selected.</span></span>  
  
8.  <span data-ttu-id="616f2-150">按一下 [**變更領域**]。</span><span class="sxs-lookup"><span data-stu-id="616f2-150">Click **Change Scope**.</span></span>  
  
9. <span data-ttu-id="616f2-151">按一下 [\*\*我的網路 (子網僅) \*\*]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="616f2-151">Click **My network (subnet) only**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="616f2-152">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="616f2-152">Click **OK** to close the dialog box.</span></span>  
  
11. <span data-ttu-id="616f2-153">重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="616f2-153">Restart the computer.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="616f2-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="616f2-154">Next Steps</span></span>  
 <span data-ttu-id="616f2-155">在您開啟此通訊埠之後，以及確認遠端使用者是否可以在您開啟的通訊埠上存取報表伺服器之前，您必須透過首頁和網站層級的角色指派，為使用者授與此報表伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="616f2-155">After you open the port and before you confirm whether remote users can access the report server on the port that you open, you must grant user access to the report server through role assignments on Home and at the site level.</span></span> <span data-ttu-id="616f2-156">如果使用者沒有足夠的權限，雖然您可以正確開啟通訊埠，不過報表伺服器連接仍然會失敗。</span><span class="sxs-lookup"><span data-stu-id="616f2-156">You can open a port correctly and still have report server connections fail if users do not have sufficient permissions.</span></span> <span data-ttu-id="616f2-157">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的[將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](../security/grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="616f2-157">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../security/grant-user-access-to-a-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="616f2-158">您也可以在另一部電腦上啟動報表管理員，以確認此通訊埠已正確開啟。</span><span class="sxs-lookup"><span data-stu-id="616f2-158">You can also verify that the port is opened correctly by starting Report Manager on a different computer.</span></span> <span data-ttu-id="616f2-159">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="616f2-159">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="616f2-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="616f2-160">See Also</span></span>  
 <span data-ttu-id="616f2-161">[設定報表伺服器服務帳戶 &#40;SSRS 組態管理員&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="616f2-161">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="616f2-162">[設定報表伺服器 URL &#40;SSRS 組態管理員&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="616f2-162">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="616f2-163">[建立 &#40;SSRS Configuration Manager 的報表伺服器資料庫&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="616f2-163">[Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="616f2-164">[設定報表伺服器服務帳戶 &#40;SSRS 組態管理員&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="616f2-164">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="616f2-165">管理 Reporting Services 原生模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="616f2-165">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
