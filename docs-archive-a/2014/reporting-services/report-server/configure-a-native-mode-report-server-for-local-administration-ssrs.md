---
title: 設定原生模式報表伺服器進行本機管理 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- UAC
- installing Reporting Services
- Windows Vista
- Localhost
- windows server 2008
- Vista
ms.assetid: 312c6bb8-b3f7-4142-a55f-c69ee15bbf52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad53f293ef825a382d9e39b58527a36ef291687a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597608"
---
# <a name="configure-a-native-mode-report-server-for-local-administration-ssrs"></a><span data-ttu-id="5c2bb-102">設定原生模式報表伺服器進行本機管理 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5c2bb-102">Configure a Native Mode Report Server for Local Administration (SSRS)</span></span>
  <span data-ttu-id="5c2bb-103">如果您想要在本機管理報表伺服器執行個體，則在下列其中一個作業系統上部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器需要其他組態步驟。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-103">Deploying a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server on one of the following operating systems requires more configuration steps if you want to administer the report server instance locally.</span></span> <span data-ttu-id="5c2bb-104">本主題說明如何設定報表伺服器以進行本機管理。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-104">This topic explains how to configure the report server for local administration.</span></span> <span data-ttu-id="5c2bb-105">如果您尚未安裝或設定報表伺服器，請參閱安裝[SQL Server 2014，從安裝精靈 &#40;安裝程式&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)和[管理 Reporting Services 原生模式報表伺服器](manage-a-reporting-services-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-105">If you have not yet installed or configured the report server, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) and [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="5c2bb-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式</span><span class="sxs-lookup"><span data-stu-id="5c2bb-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
-   [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)]  
  
-   [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]  
  
-   [!INCLUDE[win8](../../includes/win8-md.md)]  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
 <span data-ttu-id="5c2bb-107">由於標示的作業系統會限制權限，所以屬於本機管理員群組的成員會執行大部分的應用程式，就像使用標準使用者帳戶一樣。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-107">Because the noted operating systems limit permissions, members of the local Administrators group run most applications as if they are using the Standard User account.</span></span>  
  
 <span data-ttu-id="5c2bb-108">雖然這個作法會提升系統的整體安全性，但是也會妨礙您使用 Reporting Services 為本機管理員建立之預先定義的內建角色指派。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-108">While this practice improves the overall security of your system, it prevents you from using the predefined, built-in role assignments that Reporting Services creates for local administrators.</span></span>  
  
-   [<span data-ttu-id="5c2bb-109">組態變更概觀</span><span class="sxs-lookup"><span data-stu-id="5c2bb-109">Overview of Configuration Changes</span></span>](#bkmk_configuraiton_overview)  
  
-   [<span data-ttu-id="5c2bb-110">若要設定本機報表伺服器和報表管理員的管理</span><span class="sxs-lookup"><span data-stu-id="5c2bb-110">To Configure Local Report Server and Report Manager Administration</span></span>](#bkmk_configure_local_server)  
  
-   [<span data-ttu-id="5c2bb-111">若要設定 SQL Server Management Studio (SSMS) 來進行本機報表伺服器管理</span><span class="sxs-lookup"><span data-stu-id="5c2bb-111">To Configure SQL Server Management Studio (SSMS) for local report server administration</span></span>](#bkmk_configure_ssms)  
  
-   [<span data-ttu-id="5c2bb-112">若要設定 SQL Server Data Tools BI (SSDT) 來發行至本機報表伺服器</span><span class="sxs-lookup"><span data-stu-id="5c2bb-112">To Configure SQL Server Data Tools BI (SSDT) to Publish to a Local Report Server</span></span>](#bkmk_configure_ssdt)  
  
-   [<span data-ttu-id="5c2bb-113">其他資訊</span><span class="sxs-lookup"><span data-stu-id="5c2bb-113">Additional Information</span></span>](#bkmk_addiitonal_informaiton)  
  
##  <a name="overview-of-configuration-changes"></a><a name="bkmk_configuraiton_overview"></a><span data-ttu-id="5c2bb-114">設定變更總覽</span><span class="sxs-lookup"><span data-stu-id="5c2bb-114">Overview of Configuration Changes</span></span>  
 <span data-ttu-id="5c2bb-115">下列組態變更會設定伺服器，好讓您可以使用標準使用者權限來管理報表伺服器內容和作業：</span><span class="sxs-lookup"><span data-stu-id="5c2bb-115">The following configuration changes configure the server so that you can use standard user permissions to manage report server content and operations:</span></span>  
  
-   <span data-ttu-id="5c2bb-116">將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 加入至信任的網站。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-116">Add [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs to trusted sites.</span></span> <span data-ttu-id="5c2bb-117">根據預設，在列出的作業系統上執行的 Internet Explorer 會在 **[受保護模式]** 下執行，此功能會封鎖瀏覽器要求，使其無法到達相同電腦上執行的高層級處理序。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-117">By default, Internet Explorer running on the listed operating systems runs in **Protected Mode**, a feature that blocks browser requests from reaching high-level processes that run on the same computer.</span></span> <span data-ttu-id="5c2bb-118">您可以為報表伺服器應用程式停用受保護模式，只要將這些應用程式加入為信任的網站即可。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-118">You can disable protected mode for the report server applications by adding them as Trusted Sites.</span></span>  
  
-   <span data-ttu-id="5c2bb-119">建立授與您 (亦即報表伺服器管理員) 有權管理內容和作業的角色指派，而不需要使用 Internet Explorer 上的 **[以系統管理員身分執行]** 功能。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-119">Create role assignments that grant you, the report server administrator, permission to manage content and operations without having to use the **Run as administrator** feature on Internet Explorer.</span></span> <span data-ttu-id="5c2bb-120">為 Windows 使用者帳戶建立角色指派，就可以使用內容管理員和系統管理員權限取得報表伺服器的存取權 (透過可取代 Reporting Services 建立之預先定義的內建角色指派的明確角色指派)。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-120">By creating role assignments for your Windows user account, you gain access to a report server with Content Manager and System Administrator permissions through explicit role assignments that replace the predefined, built-in role assignments that Reporting Services creates.</span></span>  
  
##  <a name="to-configure-local-report-server-and-report-manager-administration"></a><a name="bkmk_configure_local_server"></a><span data-ttu-id="5c2bb-121">若要設定本機報表伺服器和報表管理員系統管理</span><span class="sxs-lookup"><span data-stu-id="5c2bb-121">To Configure Local Report Server and Report Manager Administration</span></span>  
 <span data-ttu-id="5c2bb-122">如果您瀏覽至本機報表伺服器而且看到類似於以下的錯誤，請完成本章節的組態步驟：</span><span class="sxs-lookup"><span data-stu-id="5c2bb-122">Complete the configuration steps in this section if you are browsing to a local report server and you see errors similar to the following:</span></span>  
  
-   <span data-ttu-id="5c2bb-123">使用者 `'Domain\[user name]`' 沒有必要權限。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-123">User `'Domain\[user name]`' does not have required permissions.</span></span> <span data-ttu-id="5c2bb-124">請確認已授與足夠的權限，而且滿足 Windows 使用者帳戶控制 (UAC) 的限制。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-124">Verify that sufficient permissions have been granted and Windows User Account Control (UAC) restrictions have been addressed.</span></span>  
  
###  <a name="trusted-site-settings-in-the-browser"></a><a name="bkmk_site_settings"></a><span data-ttu-id="5c2bb-125">瀏覽器中受信任的網站設定</span><span class="sxs-lookup"><span data-stu-id="5c2bb-125">Trusted Site Settings in the Browser</span></span>  
  
1.  <span data-ttu-id="5c2bb-126">使用 [以系統管理員身分執行] 權限開啟瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-126">Open a browser window with Run as administrator permissions.</span></span> <span data-ttu-id="5c2bb-127">從 **[開始]** 功能表按一下 **[所有程式]**，再以滑鼠右鍵按一下 **[Internet Explorer]**，並選取 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-127">From the **Start** menu, click **All Programs**, right-click **Internet Explorer**, and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="5c2bb-128">按一下 **[允許]** 繼續進行。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-128">Click **Allow** to continue.</span></span>  
  
3.  <span data-ttu-id="5c2bb-129">在 URL 網址中，輸入報表管理員 URL。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-129">In the URL address, enter the Report Manager URL.</span></span> <span data-ttu-id="5c2bb-130">如需指示，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-130">For instructions, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="5c2bb-131">按一下 **[工具]** 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-131">Click **Tools**.</span></span>  
  
5.  <span data-ttu-id="5c2bb-132">按一下 **[網際網路選項]** 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-132">Click **Internet Options**.</span></span>  
  
6.  <span data-ttu-id="5c2bb-133">按一下 **[安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-133">Click **Security**.</span></span>  
  
7.  <span data-ttu-id="5c2bb-134">按一下 **[信任的網站]** 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-134">Click **Trusted Sites**.</span></span>  
  
8.  <span data-ttu-id="5c2bb-135">按一下 **[網站]** 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-135">Click **Sites**.</span></span>  
  
9. <span data-ttu-id="5c2bb-136">加入 `http://<your-server-name>`。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-136">Add `http://<your-server-name>`.</span></span>  
  
10. <span data-ttu-id="5c2bb-137">如果您並未針對預設網站使用 HTTPS，請清除 **[此區域內的所有網站需要伺服器驗證 (https:)]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-137">Clear the check box **Require server certification (https:) for all sites in this zone** if you are not using HTTPS for the default site.</span></span>  
  
11. <span data-ttu-id="5c2bb-138">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-138">Click **Add**.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-folder-settings"></a><a name="bkmk_configure_folder_settings"></a> <span data-ttu-id="5c2bb-139">報表管理員資料夾設定</span><span class="sxs-lookup"><span data-stu-id="5c2bb-139">Report Manager Folder Settings</span></span>  
  
1.  <span data-ttu-id="5c2bb-140">在報表管理員的首頁上，按一下 **[資料夾設定]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-140">In Report Manager, on the Home page, click **Folder Settings**.</span></span>  
  
2.  <span data-ttu-id="5c2bb-141">在 [資料夾設定] 頁面中，按一下 **[安全性]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-141">In the Folder Settings page, click **Security**.</span></span>  
  
3.  <span data-ttu-id="5c2bb-142">按一下 **[新增角色指派]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-142">Click **New Role Assignment**.</span></span>  
  
4.  <span data-ttu-id="5c2bb-143">在 [群組或使用者名稱] \*\*\*\* 欄位中，使用以下格式輸入您的 Windows 使用者帳戶： `<domain>\<user>`。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-143">In the **Group or user name** field, type your Windows user account in this format: `<domain>\<user>`.</span></span>  
  
5.  <span data-ttu-id="5c2bb-144">選取 **[內容管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-144">Select **Content Manager**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-site-settings"></a><a name="bkmk_configure_site_settings"></a> <span data-ttu-id="5c2bb-145">報表管理員網站設定</span><span class="sxs-lookup"><span data-stu-id="5c2bb-145">Report Manager Site Settings</span></span>  
  
1.  <span data-ttu-id="5c2bb-146">以系統管理權限開啟瀏覽器，並瀏覽至報表管理員 `http://<server name>/reports`。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-146">Open your browser with administrative privileges and browse to report manager, `http://<server name>/reports`.</span></span>  
  
2.  <span data-ttu-id="5c2bb-147">按一下首頁上方角落的 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-147">Click **Site Settings** in the upper corner of the Home page.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="5c2bb-148">**注意：** 如果您沒看到 **[站台設定]** 選項，請使用系統管理權限關閉並重新開啟瀏覽器，然後瀏覽至報表管理員。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-148">**Note:** If you do not see the **Site Settings** option, close and reopen your browser and browse to report manager with administrative privileges.</span></span>  
  
3.  <span data-ttu-id="5c2bb-149">按一下 [**安全性**]。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-149">Click **security**.</span></span>  
  
4.  <span data-ttu-id="5c2bb-150">按一下 **[新增角色指派]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-150">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="5c2bb-151">在 [群組或使用者名稱] \*\*\*\* 欄位中，使用以下格式輸入您的 Windows 使用者帳戶： `<domain>\<user>`。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-151">In the **Group or user name** field, type your Windows user account in this format: `<domain>\<user>`.</span></span>  
  
6.  <span data-ttu-id="5c2bb-152">選取 **[系統管理員]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-152">Select **System Administrator**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="5c2bb-153">關閉報表管理員。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-153">Close Report Manager.</span></span>  
  
9. <span data-ttu-id="5c2bb-154">在 Internet Explorer 中重新開啟報表管理員，而不使用 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-154">Re-open Report Manager in Internet Explorer, without using **Run as administrator**.</span></span>  
  
##  <a name="to-configure-sql-server-management-studio-ssms-for-local-report-server-administration"></a><a name="bkmk_configure_ssms"></a><span data-ttu-id="5c2bb-155">若要設定 SQL Server Management Studio (SSMS) 進行本機報表伺服器管理</span><span class="sxs-lookup"><span data-stu-id="5c2bb-155">To Configure SQL Server Management Studio (SSMS) for local report server administration</span></span>  
 <span data-ttu-id="5c2bb-156">根據預設，您無法存取 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中所提供的所有報表伺服器屬性，除非您使用系統管理權限啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-156">By default, you cannot access all of the report server properties available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] unless you start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
 <span data-ttu-id="5c2bb-157">**若要設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** 角色屬性和角色指派，好讓您不必每次都使用更高權限啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="5c2bb-157">**To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** role properties and role assignments so you do not need to start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with elevated permissions each time:</span></span>  
  
-   <span data-ttu-id="5c2bb-158">在 [開始]\*\*\*\* 功能表中，依序按一下 [所有程式]\*\*\*\* 與 [SQL Server 2014]\*\*\*\*、以滑鼠右鍵按一下 [[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]]\*\*\*\*，然後按一下 [以系統管理員身分執行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-158">From the **Start** menu, click **All Programs**, click **SQL Server 2014**, right-click **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**, and then click **Run as administrator**.</span></span>  
  
-   <span data-ttu-id="5c2bb-159">連接到本機 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-159">Connect to your local [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server.</span></span>  
  
-   <span data-ttu-id="5c2bb-160">在 **[安全性]** 節點中，按一下 **[系統角色]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-160">In the **Security** node, click **System Roles**.</span></span>  
  
-   <span data-ttu-id="5c2bb-161">以滑鼠右鍵按一下 **[系統管理員]** ，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-161">Right-click **System Administrator** and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="5c2bb-162">在 **[系統角色屬性]** 頁面中，選取 **[檢視報表伺服器屬性]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-162">In the **System Role Properties** page, select **View report server properties**.</span></span> <span data-ttu-id="5c2bb-163">選取您想要與系統管理員角色成員產生關聯的任何其他屬性。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-163">Select any other properties you want associated with members of the system administrators role.</span></span>  
  
-   <span data-ttu-id="5c2bb-164">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-164">Click **OK**.</span></span>  
  
-   <span data-ttu-id="5c2bb-165">關閉 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c2bb-165">Close [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]</span></span>  
  
-   <span data-ttu-id="5c2bb-166">若要將使用者加入「系統管理員」系統角色，請參閱本主題稍早的＜ [報表管理員網站設定](#bkmk_configure_site_settings) ＞一節。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-166">To add a user to the system role "system administrator", see the [Report Manager Site Settings](#bkmk_configure_site_settings) section earlier in this topic.</span></span>  
  
 <span data-ttu-id="5c2bb-167">現在當您開啟 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 而且未明確選取 **[以系統管理員身分執行]** 時，還是可以存取報表伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-167">Now when you open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and do not explicitly select **Run as administrator** you have access to the report server properties.</span></span>  
  
##  <a name="to-configure-sql-server-data-tools-bi-ssdt-to-publish-to-a-local-report-server"></a><a name="bkmk_configure_ssdt"></a><span data-ttu-id="5c2bb-168">若要設定 SQL Server Data Tools BI (SSDT) 發行至本機報表伺服器</span><span class="sxs-lookup"><span data-stu-id="5c2bb-168">To Configure SQL Server Data Tools BI (SSDT) to Publish to a Local Report Server</span></span>  
 <span data-ttu-id="5c2bb-169">如果您已經在本主題的第一個章節所列的其中一個作業系統上安裝 [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] ，而且您希望 SSDT 與本機原生模式報表伺服器互動，您將會遇到權限錯誤，除非您以更高權限開啟 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或設定報表服務角色。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-169">If you installed [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] on one of the operating systems listed in the first section of this topic, and you want SSDT to interact with a local Native mode report server, you will experiences permission errors unless you open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] with elevated permissions or configure reporting services roles.</span></span> <span data-ttu-id="5c2bb-170">例如，如果您沒有足夠的權限，您將會遇到類似以下的問題：</span><span class="sxs-lookup"><span data-stu-id="5c2bb-170">For example, if you do not have sufficient permissions, you experience issues similar to the following:</span></span>  
  
-   <span data-ttu-id="5c2bb-171">當您嘗試將報表項目部署到本機報表伺服器時，您會在 **[錯誤清單]** 視窗中看到類似下列的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="5c2bb-171">When you attempt to deploy report items to the local report server, you see an error message similar to the following in the **Error List** window:</span></span>  
  
    -   <span data-ttu-id="5c2bb-172">授與使用者 'Domain\\<使用者名稱\>' 的權限不足，無法執行此作業。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-172">The permissions granted to user 'Domain\\<user name\>' are insufficient for performing this operation.</span></span>  
  
 <span data-ttu-id="5c2bb-173">**若要在每次開啟 SSDT 時都以更高權限執行：**</span><span class="sxs-lookup"><span data-stu-id="5c2bb-173">**To run with elevated permissions each time you open SSDT:**</span></span>  
  
1.  <span data-ttu-id="5c2bb-174">在 [開始] 畫面上，輸入 `sql server` ，然後以滑鼠右鍵按一下**Visual Studio 的 [SQL Server Data Tools**]。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-174">From the start screen, type `sql server` and then right-click **SQL Server Data Tools for Visual Studio**.</span></span> <span data-ttu-id="5c2bb-175">按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-175">Click **Run as administrator**</span></span>  
  
     <span data-ttu-id="5c2bb-176">**或者**，在舊版作業系統上：</span><span class="sxs-lookup"><span data-stu-id="5c2bb-176">**Or**, on older operating systems:</span></span>  
  
     <span data-ttu-id="5c2bb-177">在 [開始] \*\*\*\* 功能表中，依序按一下 [所有程式] \*\*\*\* 與 [SQL Server 2014] \*\*\*\*、以滑鼠右鍵按一下 [SQL Server Data Tools] \*\*\*\*，然後按一下 [以系統管理員身分執行] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-177">From the **Start** menu, click **All Programs**, click **SQL Server 2014**, right-click **SQL Server Data Tools**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="5c2bb-178">按一下 **[繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-178">Click **Continue**.</span></span>  
  
3.  <span data-ttu-id="5c2bb-179">按一下 **[執行程式]**。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-179">Click **Run Program**.</span></span>  
  
 <span data-ttu-id="5c2bb-180">您現在應該能夠將報表和其他項目部署到本機報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-180">You should now be able to deploy reports and other items to a local report server.</span></span>  
  
 <span data-ttu-id="5c2bb-181">**若要設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 角色指派，好讓您不必每次都使用更高權限啟動 SSDT：**</span><span class="sxs-lookup"><span data-stu-id="5c2bb-181">**To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] role assignments so you do not need to start SSDT with elevated permissions each time:**</span></span>  
  
-   <span data-ttu-id="5c2bb-182">請參閱本主題稍早的＜ [報表管理員資料夾設定](#bkmk_configure_folder_settings) ＞和＜ [報表管理員網站設定](#bkmk_configure_site_settings) ＞章節。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-182">See the [Report Manager Folder Settings](#bkmk_configure_folder_settings) and [Report Manager Site Settings](#bkmk_configure_site_settings) sections earlier in this topic.</span></span>  
  
##  <a name="additional-information"></a><a name="bkmk_addiitonal_informaiton"></a><span data-ttu-id="5c2bb-183">其他資訊</span><span class="sxs-lookup"><span data-stu-id="5c2bb-183">Additional Information</span></span>  
 <span data-ttu-id="5c2bb-184">與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 管理相關的額外且常見的組態步驟如下：在 Windows 防火牆中開啟通訊埠 80，以允許存取報表伺服器電腦。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-184">An additional and common configuration step related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] administration is to open port 80 in Windows Firewall to allow access to the report server computer.</span></span> <span data-ttu-id="5c2bb-185">如需指示，請參閱 [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="5c2bb-185">For instructions, see [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c2bb-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c2bb-186">See Also</span></span>  
 [<span data-ttu-id="5c2bb-187">管理 Reporting Services 原生模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="5c2bb-187">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
