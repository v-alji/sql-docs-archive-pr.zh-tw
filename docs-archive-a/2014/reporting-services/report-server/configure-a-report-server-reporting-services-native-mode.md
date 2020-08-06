---
title: 設定報表伺服器 (Reporting Services 原生模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report server configuration
- report servers [Reporting Services], configuring
ms.assetid: ef84ce9d-9156-48e9-8073-7e0535476932
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 64c63f52c373e034f0242101de0a27ee775920ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597600"
---
# <a name="configure-a-report-server-reporting-services-native-mode"></a><span data-ttu-id="d1267-102">設定報表伺服器 (Reporting Services 原生模式)</span><span class="sxs-lookup"><span data-stu-id="d1267-102">Configure a Report Server (Reporting Services Native Mode)</span></span>
  <span data-ttu-id="d1267-103">根據您在安裝期間選取的選項而定，報表伺服器可能需要其他組態設定才能使用。</span><span class="sxs-lookup"><span data-stu-id="d1267-103">Depending on options you selected during installation, the Report Server might require additional configuration before you can use it.</span></span> <span data-ttu-id="d1267-104">報表伺服器組態至少要包含以下項目：</span><span class="sxs-lookup"><span data-stu-id="d1267-104">At a minimum, a report server configuration consists of the following:</span></span>  
  
-   <span data-ttu-id="d1267-105">報表伺服器服務帳戶 (在安裝期間設定)。</span><span class="sxs-lookup"><span data-stu-id="d1267-105">A Report Server service account (configured during installation).</span></span>  
  
-   <span data-ttu-id="d1267-106">提供對報表伺服器之存取的 Web 服務 URL。</span><span class="sxs-lookup"><span data-stu-id="d1267-106">A Web service URL that provides access to the report server.</span></span>  
  
-   <span data-ttu-id="d1267-107">儲存應用程式資料、報表和其他項目的報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="d1267-107">A report server database that stores application data, reports, and other items.</span></span>  
  
 <span data-ttu-id="d1267-108">如果您選取以下兩個安裝選項的其中一種，安裝程式會進行最小的設定：原生模式預設組態或 SharePoint 整合模式預設組態。</span><span class="sxs-lookup"><span data-stu-id="d1267-108">Setup configures the minimum settings if you select either of the following installation options: Native mode default configuration or SharePoint integrated mode default configuration.</span></span> <span data-ttu-id="d1267-109">如果您在僅限檔案模式中安裝報表伺服器 (這是安裝精靈中的 **[安裝但不設定伺服器]** 選項)，則只會設定服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="d1267-109">If you installed the report server in files-only mode (this is the **Install but do not configure** option in the Installation wizard), only the service account is configured.</span></span> <span data-ttu-id="d1267-110">在安裝程式完成之後，必須設定 Web 服務 URL 和報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="d1267-110">The Web service URL and report server database must be configured after Setup is finished.</span></span>  
  
 <span data-ttu-id="d1267-111">報表管理員是適用於原生模式報表伺服器的選擇性功能，但是建議您設定報表管理員，讓您可以授與使用者對報表伺服器的存取權，並管理報表伺服器內容。</span><span class="sxs-lookup"><span data-stu-id="d1267-111">Report Manager is an optional feature for a native mode report server, but it is recommended that you configure Report Manager so that you can grant user access to the report server and manage report server content.</span></span> <span data-ttu-id="d1267-112">如果您在 SharePoint 整合模式中部署報表伺服器，請使用 SharePoint 伺服器的 Web 前端來授與存取權。</span><span class="sxs-lookup"><span data-stu-id="d1267-112">If you deploy a report server in SharePoint integrated mode, use the Web front-end of a SharePoint server to grant access.</span></span>  
  
 <span data-ttu-id="d1267-113">也可以視需要設定其他功能，例如報表伺服器電子郵件和自動執行帳戶。</span><span class="sxs-lookup"><span data-stu-id="d1267-113">Additional features, such as report server e-mail and the unattended execution account, can be configured as needed.</span></span> <span data-ttu-id="d1267-114">如需詳細資訊，請參閱 [管理 Reporting Services 原生模式報表伺服器](manage-a-reporting-services-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d1267-114">For more information, see [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="d1267-115">若要設定報表伺服器，請使用 Reporting Services 組態工具。</span><span class="sxs-lookup"><span data-stu-id="d1267-115">To configure a report server, use the Reporting Services Configuration tool.</span></span>  
  
### <a name="to-minimally-configure-a-report-server-installation"></a><span data-ttu-id="d1267-116">以最低限度的方式設定報表伺服器安裝</span><span class="sxs-lookup"><span data-stu-id="d1267-116">To minimally configure a report server installation</span></span>  
  
1.  <span data-ttu-id="d1267-117">啟動 Reporting Services 組態管理員，並連接到報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1267-117">Start the Reporting Services Configuration Manager and connect to the report server instance.</span></span> <span data-ttu-id="d1267-118">如需指示，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="d1267-118">For instructions, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="d1267-119">按一下 **[Web 服務 URL]** ，開啟為報表伺服器設定 URL 的頁面。</span><span class="sxs-lookup"><span data-stu-id="d1267-119">Click **Web Service URL** to open the page for configuring a URL for the report server.</span></span> <span data-ttu-id="d1267-120">如需如何定義 URL 的指示，請參閱[設定 URL &#40;SSRS 設定管理員&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d1267-120">For instructions on how to define the URL, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="d1267-121">按一下 **[資料庫]** ，建立報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="d1267-121">Click **Database** to create the report server database.</span></span> <span data-ttu-id="d1267-122">如需指示，請參閱[建立原生模式報表伺服器資料庫 &#40;SSRS 設定管理員&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)。</span><span class="sxs-lookup"><span data-stu-id="d1267-122">For instructions, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
4.  <span data-ttu-id="d1267-123">回到 **[Web 服務 URL]** 頁面，並按一下此 URL 確認它是否有效。</span><span class="sxs-lookup"><span data-stu-id="d1267-123">Go back to the **Web Service URL** page and click the URL to verify it works.</span></span>  
  
5.  <span data-ttu-id="d1267-124">遵循「後續步驟」中的指示來完成部署。</span><span class="sxs-lookup"><span data-stu-id="d1267-124">Follow the instructions in "Next Steps" to complete your deployment.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d1267-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d1267-125">Next Steps</span></span>  
 <span data-ttu-id="d1267-126">若要完成部署，您應該設定報表管理員或 SharePoint 整合。</span><span class="sxs-lookup"><span data-stu-id="d1267-126">To complete your deployment, you should configure Report Manager or SharePoint integration.</span></span> <span data-ttu-id="d1267-127">如需詳細資訊，請參閱[設定報表管理員 &#40;原生模式&#41;](configure-web-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="d1267-127">For more information, see [Configure Report Manager &#40;Native Mode&#41;](configure-web-portal.md).</span></span>  
  
 <span data-ttu-id="d1267-128">如果開啟了 Windows 防火牆，則設定報表伺服器使用的通訊埠很可能已關閉。</span><span class="sxs-lookup"><span data-stu-id="d1267-128">If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed.</span></span> <span data-ttu-id="d1267-129">當您嘗試從遠端用戶端電腦開啟報表管理員時出現空白頁面，即表示通訊埠可能已關閉。</span><span class="sxs-lookup"><span data-stu-id="d1267-129">One indication that a port might be closed is a blank page when you attempt to open Report Manager from a remote client computer.</span></span> <span data-ttu-id="d1267-130">如需設定防火牆的詳細資訊，請參閱＜ [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d1267-130">For information on configuring the firewall, see [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
 <span data-ttu-id="d1267-131">如果您正在使用 Windows Vista 或 Windows Server 2008，需要進行其他步驟，才能在本機開啟報表管理員。</span><span class="sxs-lookup"><span data-stu-id="d1267-131">If you are using Windows Vista or Windows Server 2008, additional steps are required before you can open Report Manager locally.</span></span> <span data-ttu-id="d1267-132">如需詳細資訊，請參閱 [設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d1267-132">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
 <span data-ttu-id="d1267-133">建立資料夾、上傳項目及執行報表來確認您的安裝。</span><span class="sxs-lookup"><span data-stu-id="d1267-133">Verify your installation by creating folders, uploading items, and running reports.</span></span> <span data-ttu-id="d1267-134">請依照 [驗證 Reporting Services 安裝](../install-windows/verify-a-reporting-services-installation.md) 中的指示來確認安裝。</span><span class="sxs-lookup"><span data-stu-id="d1267-134">Follow the instructions in [Verify a Reporting Services Installation](../install-windows/verify-a-reporting-services-installation.md) to verify your installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1267-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1267-135">See Also</span></span>  
 <span data-ttu-id="d1267-136">[管理 Reporting Services 原生模式報表伺服器](manage-a-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1267-136">[Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="d1267-137">[設定供報表伺服器存取的防火牆](configure-a-firewall-for-report-server-access.md) </span><span class="sxs-lookup"><span data-stu-id="d1267-137">[Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md) </span></span>  
 <span data-ttu-id="d1267-138">[設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d1267-138">[Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md) </span></span>  
 <span data-ttu-id="d1267-139">[設定報表伺服器來進行遠端管理](configure-a-report-server-for-remote-administration.md) </span><span class="sxs-lookup"><span data-stu-id="d1267-139">[Configure a Report Server for Remote Administration](configure-a-report-server-for-remote-administration.md) </span></span>  
 [<span data-ttu-id="d1267-140">Reporting Services 組態管理員 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="d1267-140">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
