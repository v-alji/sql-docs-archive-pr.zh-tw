---
title: 管理 Reporting Services 原生模式報表伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d44a9329074a20c04f878c055674ea563b297f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597579"
---
# <a name="manage-a-reporting-services-native-mode-report-server"></a><span data-ttu-id="03954-102">管理 Reporting Services 原生模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="03954-102">Manage a Reporting Services Native Mode Report Server</span></span>
  <span data-ttu-id="03954-103">本節包含使用 Reporting Services 組態管理員來設定原生模式報表伺服器執行個體的程序。</span><span class="sxs-lookup"><span data-stu-id="03954-103">This section contains procedures for configuring a native mode report server instance using the Reporting Services Configuration Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="03954-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="03954-104">In This Section</span></span>  
 <span data-ttu-id="03954-105">本章節的主題將組織成數個類別，好讓您可以更輕鬆地找到所要的指示。</span><span class="sxs-lookup"><span data-stu-id="03954-105">The topics in this section are organized into categories so that you can more easily find the instructions you want.</span></span> <span data-ttu-id="03954-106">第一節包含原生模式報表伺服器之基本組態工作的主題，</span><span class="sxs-lookup"><span data-stu-id="03954-106">The first section contains topics for basic configuration tasks for a native mode report server.</span></span> <span data-ttu-id="03954-107">第二節包含進階組態主題，</span><span class="sxs-lookup"><span data-stu-id="03954-107">The second section contains advanced configuration topics.</span></span> <span data-ttu-id="03954-108">第三節包含設定報表伺服器於 SharePoint 整合模式下執行的主題。</span><span class="sxs-lookup"><span data-stu-id="03954-108">The third section contains topics for configuring a report server to run in SharePoint integrated mode.</span></span>  
  
### <a name="basic-configuration"></a><span data-ttu-id="03954-109">基本組態</span><span class="sxs-lookup"><span data-stu-id="03954-109">Basic Configuration</span></span>  
 [<span data-ttu-id="03954-110">Reporting Services 組態管理員 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-110">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
 <span data-ttu-id="03954-111">提供啟動 Reporting Services 組態工具的步驟。</span><span class="sxs-lookup"><span data-stu-id="03954-111">Provides steps for starting the Reporting Services Configuration tool.</span></span>  
  
 [<span data-ttu-id="03954-112">設定服務帳戶 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-112">Configure a Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="03954-113">說明如何指定報表伺服器服務的帳戶和密碼資訊。</span><span class="sxs-lookup"><span data-stu-id="03954-113">Explains how to specify account and password information for the Report Server service.</span></span>  
  
 [<span data-ttu-id="03954-114">為報表伺服器註冊服務主要名稱 &#40;SPN&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-114">Register a Service Principal Name &#40;SPN&#41; for a Report Server</span></span>](register-a-service-principal-name-spn-for-a-report-server.md)  
 <span data-ttu-id="03954-115">說明如何手動為報表伺服器註冊 SPN，該伺服器會在使用 Kerberos 驗證之網路的網域使用者帳戶之下執行。</span><span class="sxs-lookup"><span data-stu-id="03954-115">Explains how to manually register an SPN for a report server that runs under a domain user account on a network that uses Kerberos authentication.</span></span>  
  
 [<span data-ttu-id="03954-116">設定 URL &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-116">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-a-url-ssrs-configuration-manager.md)  
 <span data-ttu-id="03954-117">說明如何建立用來存取報表伺服器 Web 服務和報表管理員的一個或多個 URL。</span><span class="sxs-lookup"><span data-stu-id="03954-117">Explains how to establish one or more URLs used to access the Report Server Web service and Report Manager.</span></span>  
  
 [<span data-ttu-id="03954-118">建立原生模式報表伺服器資料庫 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-118">Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 <span data-ttu-id="03954-119">提供建立報表伺服器資料庫的步驟。</span><span class="sxs-lookup"><span data-stu-id="03954-119">Provides steps for creating a report server database.</span></span> <span data-ttu-id="03954-120">這是部署 Reporting Services 安裝的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="03954-120">This step is required for deploying a Reporting Services installation.</span></span>  
  
### <a name="advanced-or-optional-configuration"></a><span data-ttu-id="03954-121">進階或選擇性組態</span><span class="sxs-lookup"><span data-stu-id="03954-121">Advanced or Optional Configuration</span></span>  
 [<span data-ttu-id="03954-122">設定原生模式報表伺服器向外延展部署 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-122">Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 <span data-ttu-id="03954-123">提供設定多個報表伺服器來共用報表伺服器資料庫的步驟。</span><span class="sxs-lookup"><span data-stu-id="03954-123">Provides steps for configuring multiple report servers to share a report server database.</span></span>  
  
 [<span data-ttu-id="03954-124">針對 &#40;SSRS Configuration Manager 的電子郵件傳遞設定報表伺服器&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-124">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 <span data-ttu-id="03954-125">提供有關為電子郵件散發設定報表伺服器的步驟。</span><span class="sxs-lookup"><span data-stu-id="03954-125">Provides steps for configuring a report server for e-mail distribution.</span></span>  
  
 [<span data-ttu-id="03954-126">設定供報表伺服器存取的防火牆</span><span class="sxs-lookup"><span data-stu-id="03954-126">Configure a Firewall for Report Server Access</span></span>](configure-a-firewall-for-report-server-access.md)  
 <span data-ttu-id="03954-127">說明如何開啟用於來自報表伺服器之傳入要求和傳出回應的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="03954-127">Explains how to open ports used for inbound requests and outbound responses from a report server.</span></span>  
  
 [<span data-ttu-id="03954-128">設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-128">Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;</span></span>](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 <span data-ttu-id="03954-129">描述使用 http://localhost 連線報表管理員或報表伺服器所需的其他步驟。</span><span class="sxs-lookup"><span data-stu-id="03954-129">Describes additional steps required to connect to Report Manager or a report server using http://localhost.</span></span>  
  
 [<span data-ttu-id="03954-130">設定報表伺服器來進行遠端管理</span><span class="sxs-lookup"><span data-stu-id="03954-130">Configure a Report Server for Remote Administration</span></span>](configure-a-report-server-for-remote-administration.md)  
 <span data-ttu-id="03954-131">說明如何設定遠端報表伺服器執行個體，好讓您可以從其他電腦連接及設定它。</span><span class="sxs-lookup"><span data-stu-id="03954-131">Explains how to configure a remote report server instance so that you can connect to and configure it from a different computer.</span></span>  
  
 [<span data-ttu-id="03954-132">開啟或關閉 Reporting Services 功能</span><span class="sxs-lookup"><span data-stu-id="03954-132">Turn Reporting Services Features On or Off</span></span>](turn-reporting-services-features-on-or-off.md)  
 <span data-ttu-id="03954-133">說明如何移除 Reporting Services 安裝中未使用的功能。</span><span class="sxs-lookup"><span data-stu-id="03954-133">Explains how to remove unused features in a Reporting Services installation.</span></span>  
  
 [<span data-ttu-id="03954-134">啟用遠端錯誤 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-134">Enable Remote Errors &#40;Reporting Services&#41;</span></span>](enable-remote-errors-reporting-services.md)  
 <span data-ttu-id="03954-135">說明如何在報表伺服器上設定伺服器屬性，以傳回有關遠端伺服器上發生之錯誤狀況的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="03954-135">Explains how to set server properties on a report server to return additional information about error conditions that occur on remote servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03954-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03954-136">See Also</span></span>  
 <span data-ttu-id="03954-137">[設定和管理報表伺服器 &#40;SSRS 原生模式&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="03954-137">[Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="03954-138">設定和管理報表伺服器 &#40;Reporting Services SharePoint 模式&#41;</span><span class="sxs-lookup"><span data-stu-id="03954-138">Configuration and Administration of a Report Server &#40;Reporting Services SharePoint Mode&#41;</span></span>](../configure-administer-report-server-reporting-services-sharepoint-mode.md)  
  
  
