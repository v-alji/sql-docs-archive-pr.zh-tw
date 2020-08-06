---
title: 教學課程：如何尋找及啟動 Reporting Services 工具 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder 1.0, locating and starting tool
- Reporting Services, tutorials
- Reporting Services, tools
- Reporting Services Configuration tool
- Business Intelligence Development Studio, locating and starting tool
- Model Designer [Reporting Services], locating and starting tool
- Report Designer [Reporting Services], tutorials
- tools [Reporting Services]
- tutorials [Reporting Services]
- Report Manager [Reporting Services]
ms.assetid: 51ad69d8-fe92-4662-a7cd-d235692f0c03
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b7a981a53378ea6b37959e891cac8bd891c2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704810"
---
# <a name="tutorial-how-to-locate-and-start-reporting-services-tools-ssrs"></a><span data-ttu-id="0e8be-102">教學課程：如何尋找及啟動 Reporting Services 工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="0e8be-102">Tutorial: How to Locate and Start Reporting Services Tools (SSRS)</span></span>
  <span data-ttu-id="0e8be-103">此教學課程介紹用來設定報表伺服器、管理報表伺服器內容和作業，以及建立並發行報表的工具。</span><span class="sxs-lookup"><span data-stu-id="0e8be-103">This tutorial introduces the tools used to configure a report server, manage report server content and operations, and create and publish reports.</span></span> <span data-ttu-id="0e8be-104">此教學課程的目的是協助新手使用者了解：如何尋找和開啟各項工具。</span><span class="sxs-lookup"><span data-stu-id="0e8be-104">The purpose of this tutorial is to help new users understand how to find and open each tool.</span></span> <span data-ttu-id="0e8be-105">如果您已經熟悉這些工具，可以移至其他教學課程，協助您了解使用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]的重要技巧。</span><span class="sxs-lookup"><span data-stu-id="0e8be-105">If you are already familiar with the tools, you can move on to other tutorials that can help you learn important skills for using [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="0e8be-106">如需其他教學課程的詳細資訊，請參閱[Reporting Services &#40;SSRS&#41;的教學](../reporting-services-tutorials-ssrs.md)課程。</span><span class="sxs-lookup"><span data-stu-id="0e8be-106">For more information about other tutorials, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).</span></span>  
  
 <span data-ttu-id="0e8be-107">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="0e8be-107">In this topic:</span></span>  
  
-   [<span data-ttu-id="0e8be-108">Reporting Services 組態管理員 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="0e8be-108">Reporting Services Configuration Manager (Native Mode)</span></span>](#bkmk_configuration_manager)  
  
-   [<span data-ttu-id="0e8be-109">報表管理員 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="0e8be-109">Report Manager (Native Mode)</span></span>](#bkmk_report_manager)  
  
-   [<span data-ttu-id="0e8be-110">Management Studio</span><span class="sxs-lookup"><span data-stu-id="0e8be-110">Management Studio</span></span>](#bkmk_managements_studio)  
  
-   [<span data-ttu-id="0e8be-111">含有報表設計師和報表精靈的 SQL Server 資料工具</span><span class="sxs-lookup"><span data-stu-id="0e8be-111">SQL Server Data Tools with Report Designer and Report Wizard</span></span>](#bkmk_ssdt)  
  
-   [<span data-ttu-id="0e8be-112">報表產生器</span><span class="sxs-lookup"><span data-stu-id="0e8be-112">Report Builder</span></span>](#bkmk_report_builder)  
  
##  <a name="reporting-services-configuration-manager-native-mode"></a><a name="bkmk_configuration_manager"></a><span data-ttu-id="0e8be-113">Reporting Services 組態管理員 (原生模式) </span><span class="sxs-lookup"><span data-stu-id="0e8be-113">Reporting Services Configuration Manager (Native Mode)</span></span>  
 <span data-ttu-id="0e8be-114">使用原生模式組態管理員來完成下列動作：</span><span class="sxs-lookup"><span data-stu-id="0e8be-114">Use the Native mode configuration manager to complete the following:, , , , , and.</span></span>  
  
-   <span data-ttu-id="0e8be-115">指定服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="0e8be-115">Specify the service account.</span></span>  
  
-   <span data-ttu-id="0e8be-116">建立或升級報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="0e8be-116">Create or upgrade the report server database.</span></span>  
  
-   <span data-ttu-id="0e8be-117">修改連接屬性。</span><span class="sxs-lookup"><span data-stu-id="0e8be-117">Modify the connection properties.</span></span>  
  
-   <span data-ttu-id="0e8be-118">指定 URL。</span><span class="sxs-lookup"><span data-stu-id="0e8be-118">Specify URLs.</span></span>  
  
-   <span data-ttu-id="0e8be-119">管理加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="0e8be-119">Manage encryption keys.</span></span>  
  
-   <span data-ttu-id="0e8be-120">設定自動報表處理和電子郵件報表傳遞。</span><span class="sxs-lookup"><span data-stu-id="0e8be-120">Configure unattended report processing and e-mail report delivery.</span></span>  
  
 <span data-ttu-id="0e8be-121">**安裝** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 原生模式時，就會安裝 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="0e8be-121">**Installation:** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Configuration Manager is installed when you install [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode.</span></span> <span data-ttu-id="0e8be-122">如需詳細資訊，請參閱 [安裝 Reporting Services 原生模式報表伺服器](../install-windows/install-reporting-services-native-mode-report-server.md)</span><span class="sxs-lookup"><span data-stu-id="0e8be-122">For more information, see [Install Reporting Services Native Mode Report Server](../install-windows/install-reporting-services-native-mode-report-server.md)</span></span>  
  
#### <a name="to-start-the-reporting-services-configuration-manager"></a><span data-ttu-id="0e8be-123">啟動 Reporting Services 組態管理員</span><span class="sxs-lookup"><span data-stu-id="0e8be-123">To start the Reporting Services Configuration Manager</span></span>  
  
1.  <span data-ttu-id="0e8be-124">在 Windows [開始] 畫面上，于 `reporting` [**應用程式**] 搜尋結果中輸入，然後按一下 [ **Reporting Services 組態管理員**]。</span><span class="sxs-lookup"><span data-stu-id="0e8be-124">On the Windows start screen, type `reporting` and in the **Apps** search results, click **Reporting Services Configuration Manager**.</span></span>  
  
     <span data-ttu-id="0e8be-125">![啟動時的 Reporting Services 組態管理員](../media/bi-ssrs-configmanager-win8-startscreen.gif "啟動時的 Reporting Services 組態管理員")</span><span class="sxs-lookup"><span data-stu-id="0e8be-125">![reporting services configuration manager on start](../media/bi-ssrs-configmanager-win8-startscreen.gif "reporting services configuration manager on start")</span></span>  
  
     <span data-ttu-id="0e8be-126">**或**</span><span class="sxs-lookup"><span data-stu-id="0e8be-126">**Or**</span></span>  
  
     <span data-ttu-id="0e8be-127">依序按一下 **[開始]**、 **[程式集]**、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[組態工具]** 和 **[Reporting Services 組態管理員]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-127">Click **Start**, then click **Programs**, then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], then click **Configuration Tools**, and then click **Reporting Services Configuration Manager**.</span></span>  
  
     <span data-ttu-id="0e8be-128">**[報表伺服器安裝執行個體選取範圍]** 對話方塊隨即出現，以便讓您選取所要設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0e8be-128">The **Report Server Installation Instance Selection** dialog box appears so that you can select the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="0e8be-129">在 **[伺服器名稱]** 中，指定安裝報表伺服器執行個體的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="0e8be-129">In **Server Name**, specify the name of the computer on which the report server instance is installed.</span></span> <span data-ttu-id="0e8be-130">依預設，會指定本機電腦的名稱，但您也可以輸入遠端 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="0e8be-130">The name of the local computer is specified by default, but you can also type the name of a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="0e8be-131">如果您指定遠端電腦，請按一下 **[尋找]** 來建立連接。</span><span class="sxs-lookup"><span data-stu-id="0e8be-131">If you specify a remote computer, click **Find** to establish a connection.</span></span> <span data-ttu-id="0e8be-132">必須事先設定報表伺服器的遠端管理功能。</span><span class="sxs-lookup"><span data-stu-id="0e8be-132">The report server must be configured for remote administration in advance.</span></span> <span data-ttu-id="0e8be-133">如需詳細資訊，請參閱 [設定報表伺服器來進行遠端管理](../report-server/configure-a-report-server-for-remote-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-133">For more information, see [Configure a Report Server for Remote Administration](../report-server/configure-a-report-server-for-remote-administration.md).</span></span>  
  
3.  <span data-ttu-id="0e8be-134">在 [執行個體名稱]\*\*\*\* 中，選擇您要設定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0e8be-134">In **Instance Name**, choose the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span> <span data-ttu-id="0e8be-135">只有 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 報表伺服器執行個體會出現在此清單中。</span><span class="sxs-lookup"><span data-stu-id="0e8be-135">Only [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server instances appear in the list.</span></span> <span data-ttu-id="0e8be-136">您不能設定舊版的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e8be-136">You cannot configure earlier versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="0e8be-137">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="0e8be-137">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="0e8be-138">若要確認您已啟動工具，請將結果與下圖相比較：</span><span class="sxs-lookup"><span data-stu-id="0e8be-138">To verify that you launched the tool, compare your results to the following image:</span></span>  
  
     <span data-ttu-id="0e8be-139">![Reporting Services 組態工具](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services 組態工具")</span><span class="sxs-lookup"><span data-stu-id="0e8be-139">![Reporting Services Configuration tool](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services Configuration tool")</span></span>  
  
 <span data-ttu-id="0e8be-140">**後續步驟︰** [設定和管理報表伺服器 &#40;SSRS 原生模式&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) 和[Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-140">**Next Steps:** [Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) and [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
##  <a name="report-manager-native-mode"></a><a name="bkmk_report_manager"></a><span data-ttu-id="0e8be-141">報表管理員 (原生模式) </span><span class="sxs-lookup"><span data-stu-id="0e8be-141">Report Manager (Native Mode)</span></span>  
 <span data-ttu-id="0e8be-142">使用[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)來設定許可權、管理訂閱與排程，以及處理報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-142">Use [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) to set permissions, manage subscriptions and schedules, and work with reports.</span></span> <span data-ttu-id="0e8be-143">您也可以使用報表管理員，檢視報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-143">You can also use Report Manager to view reports.</span></span>  
  
 <span data-ttu-id="0e8be-144">**安裝：** 當您安裝原生模式時，會安裝報表管理員 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ：[安裝 Reporting Services 原生模式報表伺服器](../install-windows/install-reporting-services-native-mode-report-server.md)</span><span class="sxs-lookup"><span data-stu-id="0e8be-144">**Installation:** Report Manager Is installed when you install [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode: [Install Reporting Services Native Mode Report Server](../install-windows/install-reporting-services-native-mode-report-server.md)</span></span>  
  
 <span data-ttu-id="0e8be-145">在您開啟報表管理員之前，必須有足夠的權限 (一開始，只有本機管理員群組成員才有權限，可以存取報表管理員功能)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-145">Before you can open Report Manager, you must have sufficient permissions (initially, only members of the local Administrators group have permissions that provide access to Report Manager features).</span></span> <span data-ttu-id="0e8be-146">依目前使用者的指派角色而定，報表管理員會提供不同的頁面和選項。</span><span class="sxs-lookup"><span data-stu-id="0e8be-146">Report Manager provides different pages and options depending on the role assignments of the current user.</span></span> <span data-ttu-id="0e8be-147">沒有權限的使用者就會看到空白頁。</span><span class="sxs-lookup"><span data-stu-id="0e8be-147">Users who have no permissions will get an empty page.</span></span> <span data-ttu-id="0e8be-148">有權限檢視報表的使用者會取得連結，按一下就可以開啟報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-148">Users with permissions to view reports will get links that they can click to open the reports.</span></span> <span data-ttu-id="0e8be-149">若要深入了解權限，請參閱[角色與權限 &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-149">To learn more about permissions, see [Roles and Permissions &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).</span></span>  
  
#### <a name="to-start-report-manager"></a><span data-ttu-id="0e8be-150">啟動報表管理員</span><span class="sxs-lookup"><span data-stu-id="0e8be-150">To start Report Manager</span></span>  
  
1.  <span data-ttu-id="0e8be-151">開啟瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="0e8be-151">Open your browser.</span></span> <span data-ttu-id="0e8be-152">如需支援的瀏覽器和瀏覽器版本的資訊，請參閱[規劃 Reporting Services 和 Power View 瀏覽器支援 &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-152">For information on supported browsers and browser versions, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
2.  <span data-ttu-id="0e8be-153">在網頁瀏覽器的網址列中，輸入報表管理員 URL。</span><span class="sxs-lookup"><span data-stu-id="0e8be-153">In the address bar of the Web browser, type the Report Manager URL.</span></span> <span data-ttu-id="0e8be-154">根據預設，URL 為**HTTP:// \<serverName> /reports**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-154">By default, the URL is **http://\<serverName>/reports**.</span></span> <span data-ttu-id="0e8be-155">您可以使用 Reporting Services 組態工具，以確認伺服器名稱和 URL。</span><span class="sxs-lookup"><span data-stu-id="0e8be-155">You can use the Reporting Services Configuration tool to confirm the server name and URL.</span></span> <span data-ttu-id="0e8be-156">如需 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中所使用之 URL 的詳細資訊，請參閱[設定報表伺服器 URL &#40;SSRS 組態管理員&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-156">For more information about URLs used in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="0e8be-157">報表管理員在瀏覽器視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="0e8be-157">Report Manager opens in the browser window.</span></span> <span data-ttu-id="0e8be-158">啟動頁面是 [主資料夾] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e8be-158">The startup page is the Home folder.</span></span> <span data-ttu-id="0e8be-159">視權限而定，您可能會看到其他資料夾、報表超連結，以及啟動頁面之內的資源檔案。</span><span class="sxs-lookup"><span data-stu-id="0e8be-159">Depending on permissions, you might see additional folders, hyperlinks to reports, and resource files within the startup page.</span></span> <span data-ttu-id="0e8be-160">您也可能會在工具列上看其他按鈕和命令。</span><span class="sxs-lookup"><span data-stu-id="0e8be-160">You might also see additional buttons and commands on the toolbar.</span></span>  
  
4.  <span data-ttu-id="0e8be-161">如果您在本機報表伺服器上執行報表管理員，請參閱[設定原生模式報表伺服器以進行本機管理 &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-161">If you run Report Manager on the local report server, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
 <span data-ttu-id="0e8be-162">**後續步驟：** [設定報表管理員 &#40;原生模式&#41;](../report-server/configure-web-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-162">**Next Steps:** [Configure Report Manager &#40;Native Mode&#41;](../report-server/configure-web-portal.md).</span></span>  
  
##  <a name="management-studio"></a><a name="bkmk_managements_studio"></a> <span data-ttu-id="0e8be-163">Management Studio</span><span class="sxs-lookup"><span data-stu-id="0e8be-163">Management Studio</span></span>  
 <span data-ttu-id="0e8be-164">報表伺服器管理員可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ，將報表伺服器連同其他 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 元件伺服器一起管理。</span><span class="sxs-lookup"><span data-stu-id="0e8be-164">Report server administrators can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to manage a report server alongside other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] component servers.</span></span> <span data-ttu-id="0e8be-165">如需詳細資訊，請參閱 [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-165">For more information, see [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-start-sql-server-management-studio"></a><span data-ttu-id="0e8be-166">若要啟動 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0e8be-166">To Start SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="0e8be-167">從 Windows [開始] 畫面輸入， `sql server` 然後在**應用程式**搜尋結果中，按一下 [ **SQL Server Management Studio**]。</span><span class="sxs-lookup"><span data-stu-id="0e8be-167">From the Windows Start Screen type `sql server` and in the **Apps** search results, click **SQL Server Management Studio**.</span></span>  
  
     <span data-ttu-id="0e8be-168">![Windows 開始畫面中的 Management Studio](../media/bi-ssms-win8-startscreen.gif "Windows 開始畫面中的 Management Studio")</span><span class="sxs-lookup"><span data-stu-id="0e8be-168">![managment studio from windows start screen](../media/bi-ssms-win8-startscreen.gif "managment studio from windows start screen")</span></span>  
  
     <span data-ttu-id="0e8be-169">**或**</span><span class="sxs-lookup"><span data-stu-id="0e8be-169">**Or**</span></span>  
  
     <span data-ttu-id="0e8be-170">依序按一下 [開始] \*\*\*\*、[所有程式] \*\*\*\* 和 [ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]，然後按一下 [SQL Server Management Studio] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e8be-170">Click **Start**, then click **All Programs**, then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span> <span data-ttu-id="0e8be-171">[連線到伺服器] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0e8be-171">The **Connect to Server** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="0e8be-172">如果 **[連接到伺服器]** 對話方塊沒有出現，請在 **[物件總管]** 中按一下 **[連接]** ，然後選取 **[Reporting Services]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-172">If the **Connect to Server** dialog box does not appear, in **Object Explorer**, click **Connect** and then select **Reporting Services**.</span></span>  
  
3.  <span data-ttu-id="0e8be-173">在 **[伺服器類型]** 清單中，選取 **[Reporting Services]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-173">In the **Server type** list, select **Reporting Services**.</span></span> <span data-ttu-id="0e8be-174">如果 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 不在清單上，就表示未安裝。</span><span class="sxs-lookup"><span data-stu-id="0e8be-174">If [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is not on the list, it is not installed.</span></span>  
  
4.  <span data-ttu-id="0e8be-175">在 **[伺服器名稱]** 清單中，選取一個報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0e8be-175">In the **Server name** list, select a report server instance.</span></span> <span data-ttu-id="0e8be-176">本機執行個體隨即出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="0e8be-176">Local instances appear in the list.</span></span> <span data-ttu-id="0e8be-177">您也可以輸入遠端 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="0e8be-177">You can also type the name of a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="0e8be-178">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="0e8be-178">Click **Connect**.</span></span> <span data-ttu-id="0e8be-179">您可以展開根節點以設定伺服器屬性、修改角色定義，或關閉報表伺服器功能。</span><span class="sxs-lookup"><span data-stu-id="0e8be-179">You can expand the root node to set server properties, modify role definitions, or turn off report server features.</span></span>  
  
##  <a name="sql-server-data-tools-with-report-designer-and-report-wizard"></a><a name="bkmk_ssdt"></a><span data-ttu-id="0e8be-180">報表設計師和報表精靈的 SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="0e8be-180">SQL Server Data Tools with Report Designer and Report Wizard</span></span>  
 <span data-ttu-id="0e8be-181">報表設計師是在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] - Business Intelligence for Visual Studio 2012 中提供的。</span><span class="sxs-lookup"><span data-stu-id="0e8be-181">Report Designer is available within [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] - Business Intelligence for Visual Studio 2012.</span></span> <span data-ttu-id="0e8be-182">工具中的設計介面包括：索引標籤式視窗、精靈和用來存取報表撰寫功能的功能表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-182">The design surface in the tool includes tabbed windows, wizards, and menus used to access report authoring features.</span></span> <span data-ttu-id="0e8be-183">報表設計師工具會在您選擇「報表伺服器專案」或「報表伺服器精靈」範本時提供使用。</span><span class="sxs-lookup"><span data-stu-id="0e8be-183">The report designer tool becomes available when you choose a Report Server Project or a Report Server Wizard template.</span></span> <span data-ttu-id="0e8be-184">若要深入了解，請參閱 [SQL Server Data Tools &#40;SSDT&#41; 中的 Reporting Services](reporting-services-in-sql-server-data-tools-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-184">To learn more, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).</span></span>  
  
#### <a name="to-start-report-designer"></a><span data-ttu-id="0e8be-185">啟動報表設計師</span><span class="sxs-lookup"><span data-stu-id="0e8be-185">To start Report Designer</span></span>  
  
1.  <span data-ttu-id="0e8be-186">在 Windows 的 [開始] 畫面中，輸入 **data** ，然後在 **[應用程式]** 搜尋結果中，按一下 **[SQL Server Data Tools for Visual Studio 2012]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-186">From the Windows start screen, type **data** and in the **Apps** search results, click **SQL Server Data Tools for Visual Studio 2012**.</span></span>  
  
     <span data-ttu-id="0e8be-187">**或**</span><span class="sxs-lookup"><span data-stu-id="0e8be-187">**Or**</span></span>  
  
     <span data-ttu-id="0e8be-188">按一下 [**開始**]，依序指向 [**所有程式**] 和 [] [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] ，然後按一下 [ \*\*SQL Server Data Tools (SSDT) \*\*]。</span><span class="sxs-lookup"><span data-stu-id="0e8be-188">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], and then click **SQL Server Data Tools (SSDT)**.</span></span>  
  
2.  <span data-ttu-id="0e8be-189">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-189">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="0e8be-190">在 **[專案類型]** 清單中，按一下 **[商業智慧專案]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-190">In the **Project Types** list, click **Business Intelligence Projects**.</span></span>  
  
4.  <span data-ttu-id="0e8be-191">在 **[範本]** 清單中，按一下 **[報表伺服器專案]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-191">In the **Templates** list, click **Report Server Project**.</span></span> <span data-ttu-id="0e8be-192">下圖顯示專案範本出現在對話方塊中的情形：</span><span class="sxs-lookup"><span data-stu-id="0e8be-192">The following diagram shows how the project templates appear in the dialog box:</span></span>  
  
     <span data-ttu-id="0e8be-193">![新增專案範本對話方塊](../media/rs-ui-newrsproject.gif "新增專案範本對話方塊")</span><span class="sxs-lookup"><span data-stu-id="0e8be-193">![New Project template dialog box](../media/rs-ui-newrsproject.gif "New Project template dialog box")</span></span>  
  
5.  <span data-ttu-id="0e8be-194">輸入專案的名稱與位置，或者按一下 **[瀏覽]** 然後選取位置。</span><span class="sxs-lookup"><span data-stu-id="0e8be-194">Type a name and location for the project, or click **Browse** and select a location.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]<span data-ttu-id="0e8be-195">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]隨即開啟，並出現 [ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 起始頁]。</span><span class="sxs-lookup"><span data-stu-id="0e8be-195">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] opens with the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] start page.</span></span> <span data-ttu-id="0e8be-196">方案總管提供類別，以供建立報表和資料來源。</span><span class="sxs-lookup"><span data-stu-id="0e8be-196">Solution Explorer provides categories for creating reports and data sources.</span></span> <span data-ttu-id="0e8be-197">您可以使用這些類別，建立新報表和資料來源。</span><span class="sxs-lookup"><span data-stu-id="0e8be-197">You can use these categories to create new reports and data sources.</span></span> <span data-ttu-id="0e8be-198">建立報表定義時，會顯示索引標籤式視窗。</span><span class="sxs-lookup"><span data-stu-id="0e8be-198">Tabbed windows appear when you create a report definition.</span></span> <span data-ttu-id="0e8be-199">索引標籤式視窗包括 [資料]、[配置] 和 [預覽] 等視窗。</span><span class="sxs-lookup"><span data-stu-id="0e8be-199">The tabbed windows are Data, Layout, and Preview..</span></span>  
  
 <span data-ttu-id="0e8be-200">若要著手建立第一份報表，請參閱[建立基本資料表報表 &#40;SSRS 教學課程&#41;](../create-a-basic-table-report-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-200">To get started on your first report, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md).</span></span> <span data-ttu-id="0e8be-201">若要深入瞭解您可以在報表設計師內使用的查詢設計工具，請參閱[報表設計師 SQL Server Data Tools &#40;SSRS&#41;中的查詢設計工具](../report-data/query-design-tools-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0e8be-201">To learn more about query designers you can use within Report Designer, see [Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md).</span></span>  
  
##  <a name="report-builder"></a><a name="bkmk_report_builder"></a> <span data-ttu-id="0e8be-202">報表產生器</span><span class="sxs-lookup"><span data-stu-id="0e8be-202">Report Builder</span></span>  
 <span data-ttu-id="0e8be-203">使用[報表產生器 &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md) ，在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類似 Office 的撰寫環境中建立報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-203">Use [Report Builder &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md) to create reports in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office-like authoring environment.</span></span> <span data-ttu-id="0e8be-204">不論報表是利用報表設計師還是利用舊版報表產生器所建立，您都可以自訂與更新所有現有的報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-204">You can customize and update all existing reports, regardless of whether they were created in Report Designer or in the previous versions of Report Builder.</span></span> <span data-ttu-id="0e8be-205">如需您可以執行以便在本機電腦上安裝報表產生器之 ReportBuilder3.msi 檔案的位置，請連絡管理員。</span><span class="sxs-lookup"><span data-stu-id="0e8be-205">Contact your administrator for the location of the ReportBuilder3.msi file that you run to install Report Builder on your local computer.</span></span>  
  
 <span data-ttu-id="0e8be-206">**安裝：** 報表產生器的按一下一次版本是由 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 原生模式或 SharePoint 模式安裝。</span><span class="sxs-lookup"><span data-stu-id="0e8be-206">**Installation:** The click-once version of report builder is installed by either [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode or SharePoint mode.</span></span> <span data-ttu-id="0e8be-207">單機版報表產生器則需要個別下載。</span><span class="sxs-lookup"><span data-stu-id="0e8be-207">The Stand-alone version of Report Builder is a separate download.</span></span>  <span data-ttu-id="0e8be-208">請參閱[安裝獨立版本的報表產生器 &#40;報表產生器&#41;](../install-windows/install-report-builder.md)</span><span class="sxs-lookup"><span data-stu-id="0e8be-208">See [Install the Stand-Alone Version of Report Builder &#40;Report Builder&#41;](../install-windows/install-report-builder.md)</span></span>  
  
#### <a name="to-start-report-builder-clickonce-from-report-manager-native-mode"></a><span data-ttu-id="0e8be-209">若要從報表管理員啟動報表產生器 ClickOnce (原生模式)</span><span class="sxs-lookup"><span data-stu-id="0e8be-209">To start Report Builder ClickOnce from Report Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="0e8be-210">在網頁瀏覽器中，輸入報表伺服器的報表管理員 URL。</span><span class="sxs-lookup"><span data-stu-id="0e8be-210">In your Web browser, type the Report Manager URL for your report server.</span></span> <span data-ttu-id="0e8be-211">根據預設，URL 為 HTTP:// \<*servername*> /reports。</span><span class="sxs-lookup"><span data-stu-id="0e8be-211">By default, the URL is http://\<*servername*>/reports.</span></span> <span data-ttu-id="0e8be-212">報表管理員隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0e8be-212">Report Manager opens.</span></span>  
  
2.  <span data-ttu-id="0e8be-213">按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-213">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="0e8be-214">報表產生器隨即開啟，而且您可以在報表伺服器上建立報表或開啟報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-214">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-clickonce-using-a-url"></a><span data-ttu-id="0e8be-215">若要使用 URL 來啟動報表產生器 ClickOnce</span><span class="sxs-lookup"><span data-stu-id="0e8be-215">To start Report Builder ClickOnce using a URL</span></span>  
  
1.  <span data-ttu-id="0e8be-216">在網頁瀏覽器中，於網址列中輸入下列 URL：</span><span class="sxs-lookup"><span data-stu-id="0e8be-216">In your Web browser, type the following URL in the address bar:</span></span>  
  
     <span data-ttu-id="0e8be-217">**HTTP:// \<servername> /reportserver/reportbuilder/ReportBuilder_3_0_0_0. 應用程式**</span><span class="sxs-lookup"><span data-stu-id="0e8be-217">**http://\<servername>/reportserver/reportbuilder/ReportBuilder_3_0_0_0.application**</span></span>  
  
2.  <span data-ttu-id="0e8be-218">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="0e8be-218">Press ENTER.</span></span>  
  
     <span data-ttu-id="0e8be-219">報表產生器隨即開啟，而且您可以在報表伺服器上建立報表或開啟報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-219">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-clickonce-in-reporting-services-sharepoint-mode"></a><span data-ttu-id="0e8be-220">若要以 Reporting Services SharePoint 模式啟動報表產生器 ClickOnce</span><span class="sxs-lookup"><span data-stu-id="0e8be-220">To start Report Builder ClickOnce in Reporting Services SharePoint mode</span></span>  
  
1.  <span data-ttu-id="0e8be-221">巡覽至包含您想要建立新報表之文件庫的網站。</span><span class="sxs-lookup"><span data-stu-id="0e8be-221">Navigate to the site that contains the library where you want to create a new report.</span></span>  
  
2.  <span data-ttu-id="0e8be-222">開啟文件庫。</span><span class="sxs-lookup"><span data-stu-id="0e8be-222">Open the library.</span></span>  
  
3.  <span data-ttu-id="0e8be-223">在 **[新增]** 功能表上，按一下 **[報表產生器報表]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-223">On the **New** menu, click **Report Builder Report**.</span></span>  
  
     <span data-ttu-id="0e8be-224">報表產生器隨即開啟，而且您可以在報表伺服器上建立報表或開啟報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-224">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-stand-alone"></a><span data-ttu-id="0e8be-225">若要啟動單機版報表產生器</span><span class="sxs-lookup"><span data-stu-id="0e8be-225">To start Report Builder Stand-alone</span></span>  
  
1.  <span data-ttu-id="0e8be-226">在 Windows 的 [開始] 畫面中，輸入 **報表產生器** ，然後按一下 **[報表產生器 3.0]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-226">From the Windows start screen, type **report builder** and then click **Report Builder 3.0**.</span></span>  
  
     <span data-ttu-id="0e8be-227">**或**</span><span class="sxs-lookup"><span data-stu-id="0e8be-227">**Or**</span></span>  
  
     <span data-ttu-id="0e8be-228">在 [開始] 功能表上，按一下 **[所有程式]**，然後按一下 **[Microsoft SQL Server 2014 報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-228">On the Start menu, click **All Programs**, and then click **Microsoft SQL Server 2014 Report Builder**.</span></span>  
  
2.  <span data-ttu-id="0e8be-229">按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="0e8be-229">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="0e8be-230">報表產生器隨即開啟，而且您可以建立或開啟報表。</span><span class="sxs-lookup"><span data-stu-id="0e8be-230">Report Builder opens and you can create or open a report.</span></span>  
  
3.  <span data-ttu-id="0e8be-231">按一下 **[報表產生器說明]** 開啟報表產生器的文件集。</span><span class="sxs-lookup"><span data-stu-id="0e8be-231">Click **Report Builder Help** to open the documentation for Report Builder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e8be-232">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e8be-232">See Also</span></span>  
 <span data-ttu-id="0e8be-233">[安裝、卸載和報表產生器支援](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="0e8be-233">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="0e8be-234">[Sharepoint 2010 和 SharePoint 2013 Reporting Services SharePoint 模式安裝 &#40;&#41;](../install-windows/install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="0e8be-234">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](../install-windows/install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="0e8be-235">[Reporting Services 報表伺服器](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e8be-235">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="0e8be-236">[報表設計師 SQL Server Data Tools &#40;SSRS&#41;中的查詢設計工具](../report-data/query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0e8be-236">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md) </span></span>  
 [<span data-ttu-id="0e8be-237">Reporting Services 教學課程 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0e8be-237">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
