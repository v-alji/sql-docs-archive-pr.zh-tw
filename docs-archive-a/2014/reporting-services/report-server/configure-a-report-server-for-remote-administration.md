---
title: 設定報表伺服器來進行遠端管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- WMI provider [Reporting Services], remote configuration
- configuration management [WMI]
- report servers [Reporting Services], configuring
- remote server administration [Reporting Services]
ms.assetid: 8c7f145f-3ac2-4203-8cd6-2a4694395d09
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c34db5299fc1b82a7896a41519e55466c3b3b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597605"
---
# <a name="configure-a-report-server-for-remote-administration"></a><span data-ttu-id="8a483-102">設定報表伺服器來進行遠端管理</span><span class="sxs-lookup"><span data-stu-id="8a483-102">Configure a Report Server for Remote Administration</span></span>
  <span data-ttu-id="8a483-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，您可以在本機或遠端設定報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="8a483-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can configure report server instances locally or remotely.</span></span> <span data-ttu-id="8a483-104">若要設定遠端報表伺服器執行個體，您可以使用 Reporting Services 組態工具，或是撰寫使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) 提供者的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a483-104">To configure a remote report server instance, you can use the Reporting Services Configuration tool or write custom code that uses the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) provider.</span></span> <span data-ttu-id="8a483-105">Reporting Services 組態工具提供了 WMI 提供者的圖形介面，好讓您不需要撰寫程式碼就可以設定報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a483-105">The Reporting Services Configuration tool provides a graphical interface to the WMI provider so that you can configure a report server without having to write code.</span></span> <span data-ttu-id="8a483-106">當您啟動這個工具時，可以指定要連接的遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a483-106">When you start the tool, you can specify a remote server to connect to.</span></span>  
  
 <span data-ttu-id="8a483-107">在您可以使用此工具來設定遠端報表伺服器以前，您必須遵循本主題的指示，在 Windows 防火牆中啟用通訊埠、啟用遠端連接，以及啟用 WMI 要求。</span><span class="sxs-lookup"><span data-stu-id="8a483-107">Before you can use the tool to configure a remote report server, you must follow the instructions in this topic to enable ports in Windows Firewall, enable remote connections, and enable remote WMI requests.</span></span>  
  
 <span data-ttu-id="8a483-108">適當的組態設定可協助您避免下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="8a483-108">Proper configuration helps you avoid the following error:</span></span>  
  
 `The machine could not be found.`  
  
 `"The RPC server is unavailable. (Exception from HRESULT: 0x800706BA)".`  
  
## <a name="prerequisites"></a><span data-ttu-id="8a483-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="8a483-109">Prerequisites</span></span>  
 <span data-ttu-id="8a483-110">若要修改防火牆設定，您必須在本機登入，而且必須是本機管理員群組的成員；</span><span class="sxs-lookup"><span data-stu-id="8a483-110">To modify firewall settings, you must be logged on locally and you must be a member of the local Administrators group.</span></span> <span data-ttu-id="8a483-111">您不能透過遠端連接修改遠端電腦的 Windows 防火牆設定。</span><span class="sxs-lookup"><span data-stu-id="8a483-111">You cannot modify the Windows firewall settings of a remote computer over a remote connection.</span></span>  
  
 <span data-ttu-id="8a483-112">如果您想要針對非管理員的使用者啟用遠端管理，必須將遠端啟動權限授與給「分散式元件物件模型」(DCOM) 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8a483-112">If you want to enable remote administration for a non-administrator user, you must grant the account Distributed Component Object Model (DCOM) Remote Activation permissions.</span></span> <span data-ttu-id="8a483-113">本主題有提供針對非管理員存取權設定伺服器的指示。</span><span class="sxs-lookup"><span data-stu-id="8a483-113">Instructions for configuring the server for non-administrator access are provided in this topic.</span></span>  
  
 <span data-ttu-id="8a483-114">某些組織有一些群組原則，可防止某些作業系統或使用者管理遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a483-114">Some organizations have group policies that prevent remote server administration for certain operating systems or users.</span></span> <span data-ttu-id="8a483-115">在您開始修改防火牆設定之前，請先洽詢網路管理員，以確認遠端管理是否有任何限制。</span><span class="sxs-lookup"><span data-stu-id="8a483-115">Before you begin modifying firewall settings, check with your network administrator to verify whether there are restrictions on remote administration.</span></span>  
  
 <span data-ttu-id="8a483-116">如需詳細資訊，請參閱 MSDN 上 Platform SDK 文件集內的 [通過 Windows 防火牆進行連接](https://go.microsoft.com/fwlink/?LinkId=63615) 。</span><span class="sxs-lookup"><span data-stu-id="8a483-116">For more information, see [Connecting Through Windows Firewall](https://go.microsoft.com/fwlink/?LinkId=63615) in the Platform SDK documentation on MSDN.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="8a483-117">工作</span><span class="sxs-lookup"><span data-stu-id="8a483-117">Tasks</span></span>  
 <span data-ttu-id="8a483-118">啟用遠端報表伺服器組態的工作包括以下項目：</span><span class="sxs-lookup"><span data-stu-id="8a483-118">Tasks that enable remote report server configuration include the following:</span></span>  
  
-   <span data-ttu-id="8a483-119">在 Windows 防火牆中啟用通訊埠，以允許報表伺服器和 SQL Server Database Engine 執行個體所使用的通訊埠要求。</span><span class="sxs-lookup"><span data-stu-id="8a483-119">Enable ports in Windows Firewall to allow requests on ports used by the report server and by the SQL Server Database Engine instance.</span></span>  
  
-   <span data-ttu-id="8a483-120">啟用與主控報表伺服器資料庫之 Database Engine 執行個體之間的遠端連接。</span><span class="sxs-lookup"><span data-stu-id="8a483-120">Enable remote connections to the instance of the Database Engine instance that hosts the report server database.</span></span> <span data-ttu-id="8a483-121">如果要設定報表伺服器資料庫連接及管理加密金鑰，必須要有遠端連接；</span><span class="sxs-lookup"><span data-stu-id="8a483-121">A remote connection is necessary for configuring the report server database connection and managing the encryption keys.</span></span>  
  
-   <span data-ttu-id="8a483-122">啟用要通過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 防火牆傳遞的遠端 WMI 要求。</span><span class="sxs-lookup"><span data-stu-id="8a483-122">Enable remote WMI requests to pass through the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows firewall.</span></span>  
  
-   <span data-ttu-id="8a483-123">如果您要設定遠端報表伺服器供非管理使用者進行管理，您必須設定 DCOM 權限，好讓遠端 WMI 可存取標準 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8a483-123">If you are configuring a remote report server for administration by a non-administrative user, you must set DCOM permissions to enable remote WMI access to a standard Windows user account.</span></span> <span data-ttu-id="8a483-124">由於 WMI 會使用 DCOM 當做遠端呼叫的傳輸，所以您必須設定 DCOM 權限，好讓不是以本機管理員身分登入的使用者可以設定伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a483-124">Because WMI uses DCOM as transport for remote calls, you must set the DCOM permissions so that users who are not logged on as the local administrator can configure the server.</span></span>  
  
-   <span data-ttu-id="8a483-125">如果您要設定遠端報表伺服器供非管理使用者進行管理，您也必須設定報表伺服器 WMI 命名空間的 WMI 權限。</span><span class="sxs-lookup"><span data-stu-id="8a483-125">If you are configuring a remote report server for administration by a non-administrative user, you must also set WMI permissions on the report server WMI namespace.</span></span> <span data-ttu-id="8a483-126">依預設，本機管理員群組的所有成員都有權存取報表伺服器 WMI 命名空間；</span><span class="sxs-lookup"><span data-stu-id="8a483-126">By default, all members of the local Administrator group have access to the report server WMI namespace.</span></span> <span data-ttu-id="8a483-127">如果您將存取權授與非管理員，則必須設定權限。</span><span class="sxs-lookup"><span data-stu-id="8a483-127">If you want to grant access to non-administrators, you must set permissions.</span></span>  
  
 <span data-ttu-id="8a483-128">本主題將提供如何執行這些工作的相關指示。</span><span class="sxs-lookup"><span data-stu-id="8a483-128">Instructions on how to perform these tasks are provided in this topic.</span></span>  
  
### <a name="to-open-ports-in-windows-firewall"></a><span data-ttu-id="8a483-129">在 Windows 防火牆中開啟通訊埠</span><span class="sxs-lookup"><span data-stu-id="8a483-129">To open ports in Windows Firewall</span></span>  
  
1.  <span data-ttu-id="8a483-130">[設定 Windows 防火牆以進行資料庫引擎存取](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)。</span><span class="sxs-lookup"><span data-stu-id="8a483-130">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).</span></span>  
  
2.  <span data-ttu-id="8a483-131">[設定用於報表伺服器存取的防火牆](configure-a-firewall-for-report-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="8a483-131">[Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
### <a name="to-configure-remote-connections-to-the-report-server-database"></a><span data-ttu-id="8a483-132">設定與報表伺服器資料庫的遠端連接</span><span class="sxs-lookup"><span data-stu-id="8a483-132">To configure remote connections to the report server database</span></span>  
  
1.  <span data-ttu-id="8a483-133">按一下 **[開始]**，並依序指向 **[程式集]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]**，然後按一下 **[SQL Server 組態管理員]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-133">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="8a483-134">在左窗格中，展開 [SQL Server 網路設定]\*\*\*\*，然後針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體按一下 [通訊協定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8a483-134">In the left pane, expand **SQL Server Network Configuration**, and then click **Protocols** for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="8a483-135">在詳細資料窗格中，啟用 TCP/IP 和具名管道通訊協定，然後重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="8a483-135">In the details pane, enable the TCP/IP and Named Pipes protocols, and then restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
### <a name="to-enable-remote-administration-in-windows-firewall"></a><span data-ttu-id="8a483-136">在 Windows 防火牆中啟用遠端管理</span><span class="sxs-lookup"><span data-stu-id="8a483-136">To enable remote administration in Windows Firewall</span></span>  
  
1.  <span data-ttu-id="8a483-137">以本機管理員的身分登入您想要啟用遠端管理的電腦。</span><span class="sxs-lookup"><span data-stu-id="8a483-137">Log on as a local administrator to the computer for which you want to enable remote administration.</span></span>  
  
2.  <span data-ttu-id="8a483-138">如果報表伺服器是在 Windows Vista 上執行，請以滑鼠右鍵按一下 [**命令提示**字元]，然後選取 [以**系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="8a483-138">If the report server is running on Windows Vista, right-click **Command Prompt** and select **Run as administrator**.</span></span> <span data-ttu-id="8a483-139">如果是其他作業系統，請開啟命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="8a483-139">For other operating systems, open a command prompt window.</span></span>  
  
3.  <span data-ttu-id="8a483-140">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="8a483-140">Run the following command:</span></span>  
  
    ```  
    netsh.exe firewall set service type=REMOTEADMIN mode=ENABLE scope=ALL  
    ```  
  
     <span data-ttu-id="8a483-141">您可以對 Scope 指定不同的選項。</span><span class="sxs-lookup"><span data-stu-id="8a483-141">You can specify different options for Scope.</span></span> <span data-ttu-id="8a483-142">如需詳細資訊，請參閱 Windows Firewall 產品文件集。</span><span class="sxs-lookup"><span data-stu-id="8a483-142">For more information, see the Windows Firewall product documentation.</span></span>  
  
4.  <span data-ttu-id="8a483-143">確認是否啟用遠端管理；</span><span class="sxs-lookup"><span data-stu-id="8a483-143">Verify that remote administration is enabled.</span></span> <span data-ttu-id="8a483-144">您可以執行下列命令來顯示狀態：</span><span class="sxs-lookup"><span data-stu-id="8a483-144">You can run the following command to show the status:</span></span>  
  
    ```  
    netsh.exe firewall show state  
    ```  
  
5.  <span data-ttu-id="8a483-145">重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8a483-145">Reboot the computer.</span></span>  
  
### <a name="to-set-dcom-permissions-to-enable-remote-wmi-access-for-non-administrators"></a><span data-ttu-id="8a483-146">設定 DCOM 權限來對非管理員啟用遠端 WMI 存取</span><span class="sxs-lookup"><span data-stu-id="8a483-146">To set DCOM permissions to enable remote WMI access for non-administrators</span></span>  
  
1.  <span data-ttu-id="8a483-147">在 [開始] 功能表上，指向 **[系統管理工具]**，然後按一下 **[元件服務]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-147">On the Start menu, point to **Administrative Tools**, click **Component Services**.</span></span>  
  
     <span data-ttu-id="8a483-148">若是 Windows Vista，請在 [開始] 功能表上，依序按一下 [**所有程式**]、[**執行**] 和 [輸入] `mmc comexp.msc` 。</span><span class="sxs-lookup"><span data-stu-id="8a483-148">For Windows Vista, on the Start menu, click **All Programs**, click **Run**, and then enter `mmc comexp.msc`.</span></span>  
  
2.  <span data-ttu-id="8a483-149">開啟 [元件服務] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-149">Open the Component Services folder.</span></span>  
  
3.  <span data-ttu-id="8a483-150">開啟 [電腦] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-150">Open the Computers folder.</span></span>  
  
4.  <span data-ttu-id="8a483-151">選取 [我的電腦]。</span><span class="sxs-lookup"><span data-stu-id="8a483-151">Select My Computer.</span></span>  
  
5.  <span data-ttu-id="8a483-152">選取 **[執行]** 功能表上的 **[內容]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-152">On the **Action** menu, and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="8a483-153">按一下 **[COM 安全設定]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-153">Click **COM Security**.</span></span>  
  
7.  <span data-ttu-id="8a483-154">在 **[啟動和啟用權限]** 中，按一下 **[編輯限制]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-154">In **Launch and Activation Permissions**, click **Edit Limits**.</span></span>  
  
8.  <span data-ttu-id="8a483-155">如果您沒有在 **[啟動權限]** 中看到您的名稱，請按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-155">If you do not see your name in **Launch Permission**, click **Add**.</span></span>  
  
9. <span data-ttu-id="8a483-156">輸入您的使用者帳戶名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-156">Type the name of your user account, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="8a483-157">在 [**許可權 \<User or Group> **] 的 [**允許**] 欄中，選取 [**遠端啟動**和**遠端啟用**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-157">In **Permissions for \<User or Group>**, in the **Allow** column, select **Remote Launch** and **Remote Activation**, and then click **OK**.</span></span>  
  
### <a name="to-set-permissions-on-the-report-server-wmi-namespace-for-non-administrators"></a><span data-ttu-id="8a483-158">針對非管理員設定報表伺服器 WMI 命名空間的權限</span><span class="sxs-lookup"><span data-stu-id="8a483-158">To set permissions on the report server WMI namespace for non-administrators</span></span>  
  
1.  <span data-ttu-id="8a483-159">在 [開始] 功能表上，指向 **[系統管理工具]**，然後按一下 **[電腦管理]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-159">On the Start menu, point to **Administrative Tools**, click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="8a483-160">開啟 [服務及應用程式] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-160">Open the Services and Applications folder.</span></span>  
  
3.  <span data-ttu-id="8a483-161">以滑鼠右鍵按一下 [WMI 控制]\*\*\*\*，然後選取 [內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8a483-161">Right-click **WMI Control**, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="8a483-162">按一下 **[安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="8a483-162">Click **Security**.</span></span>  
  
5.  <span data-ttu-id="8a483-163">開啟 [Root] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-163">Open the Root folder.</span></span>  
  
6.  <span data-ttu-id="8a483-164">開啟 [Microsoft] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-164">Open the Microsoft folder.</span></span>  
  
7.  <span data-ttu-id="8a483-165">開啟 [SQLServer] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-165">Open the SQLServer folder.</span></span>  
  
8.  <span data-ttu-id="8a483-166">開啟 [ReportServer] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-166">Open the ReportServer folder.</span></span>  
  
9. <span data-ttu-id="8a483-167">開啟執行個體資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-167">Open instance folder.</span></span> <span data-ttu-id="8a483-168">如果您已安裝預設執行個體，此資料夾就是 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="8a483-168">If you installed the default instance, the folder is MSSQLSERVER.</span></span>  
  
10. <span data-ttu-id="8a483-169">開啟 [v10] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a483-169">Open the v10 folder.</span></span>  
  
11. <span data-ttu-id="8a483-170">選取 [Admin] 資料夾，然後按一下 **[安全性]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-170">Select the Admin folder, and then click **Security**.</span></span>  
  
12. <span data-ttu-id="8a483-171">按一下 **[新增]**，然後輸入將用來管理伺服器的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8a483-171">Click **Add**, and then type the user account you will use to manage the server.</span></span>  
  
13. <span data-ttu-id="8a483-172">在 **[允許]** 一欄中，選取 **[啟用帳戶]**、 **[遠端啟用]** 及 **[讀取安全性]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8a483-172">In the **Allow** column, select **Enable Account**, **Remote Enable**, and **Read Security**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a483-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a483-173">See Also</span></span>  
 [<span data-ttu-id="8a483-174">Reporting Services 組態管理員 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="8a483-174">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
