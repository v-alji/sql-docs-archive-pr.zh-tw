---
title: PowerPivot for SharePoint (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58ebcf004224d21ab5b47aaee1e2e7e3ef2047ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596328"
---
# <a name="powerpivot-for-sharepoint-ssas"></a><span data-ttu-id="28ecc-102">PowerPivot for SharePoint (SSAS)</span><span class="sxs-lookup"><span data-stu-id="28ecc-102">PowerPivot for SharePoint (SSAS)</span></span>
  <span data-ttu-id="28ecc-103">PowerPivot for SharePoint 是以 SharePoint 模式執行的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="28ecc-103">PowerPivot for SharePoint is a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server running in SharePoint mode.</span></span> <span data-ttu-id="28ecc-104">PowerPivot for SharePoint 提供將 PowerPivot 資料裝載於 SharePoint 伺服器陣列的功能。</span><span class="sxs-lookup"><span data-stu-id="28ecc-104">PowerPivot for SharePoint provides server hosting of PowerPivot data in a SharePoint farm.</span></span> <span data-ttu-id="28ecc-105">PowerPivot 資料是您使用下列其中一個項目建立的分析資料模型：</span><span class="sxs-lookup"><span data-stu-id="28ecc-105">PowerPivot data is an analytical data model that you build using one of the following:</span></span>  
  
-   <span data-ttu-id="28ecc-106">PowerPivot for Excel 2010 增益集</span><span class="sxs-lookup"><span data-stu-id="28ecc-106">The PowerPivot for Excel 2010 add-in</span></span>  
  
-   <span data-ttu-id="28ecc-107">Excel 2013</span><span class="sxs-lookup"><span data-stu-id="28ecc-107">Excel 2013</span></span>  
  
 <span data-ttu-id="28ecc-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013 |[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010</span><span class="sxs-lookup"><span data-stu-id="28ecc-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010</span></span>  
  
 <span data-ttu-id="28ecc-109">這些資料的伺服器裝載需要 SharePoint、Excel Services 和 PowerPivot for SharePoint 安裝。</span><span class="sxs-lookup"><span data-stu-id="28ecc-109">Server hosting of that data requires SharePoint, Excel Services, and an installation of PowerPivot for SharePoint.</span></span> <span data-ttu-id="28ecc-110">資料載入到 PowerPivot for SharePoint 執行個體上，在此處可透過伺服器為 Excel 2010 活頁簿提供的 PowerPivot 資料重新整理功能或是為 Excel 2013 活頁簿提供的 SharePoint 2013 Excel Services，依排程間隔重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="28ecc-110">Data is loaded on PowerPivot for SharePoint instances where it can be refreshed at scheduled intervals using the PowerPivot data refresh capability that the server provides for Excel 2010 workbooks or that SharePoint 2013 Excel Services provides for Excel 2013 workbooks.</span></span>  
  
## <a name="powerpivot-for-sharepoint-2013"></a><span data-ttu-id="28ecc-111">PowerPivot for SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="28ecc-111">PowerPivot for SharePoint 2013</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="28ecc-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]支援 [!INCLUDE[msCoName](../../includes/msconame-md.md)]SharePoint 2013 Excel Services 使用包含資料模型和 Power View 報表的 Excel 活頁簿 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="28ecc-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] supports [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 2013 Excel Services usage of Excel workbooks containing data models and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Power View reports.</span></span>  
  
 <span data-ttu-id="28ecc-113">SharePoint 2013 中的 Excel Services 包含資料模型功能，可在瀏覽器中啟用與 PowerPivot 活頁簿的互動。</span><span class="sxs-lookup"><span data-stu-id="28ecc-113">Excel Services in SharePoint 2013 includes data model functionality to enable interaction with a PowerPivot workbook in the browser.</span></span> <span data-ttu-id="28ecc-114">您不需要將 PowerPivot for SharePoint 2013 增益集部署至伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="28ecc-114">You do not need to deploy the PowerPivot for SharePoint 2013 add-in into the farm.</span></span> <span data-ttu-id="28ecc-115">您只需要在 SharePoint 模式下安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器，並且在 Excel Services **[資料模型]** 設定中註冊伺服器即可。</span><span class="sxs-lookup"><span data-stu-id="28ecc-115">You only need to install an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server in SharePoint mode and register the server within the Excel Services **Data Model** settings.</span></span>  
  
 <span data-ttu-id="28ecc-116">若部署 PowerPivot for SharePoint 2013 增益集，會在 SharePoint 伺服器陣列中啟用其他功能與特性。</span><span class="sxs-lookup"><span data-stu-id="28ecc-116">Deploying the PowerPivot for SharePoint 2013 add-in enables additional functionality and features in your SharePoint farm.</span></span> <span data-ttu-id="28ecc-117">其他功能包括 PowerPivot 圖庫、排程資料重新整理及 PowerPivot 管理儀表板。</span><span class="sxs-lookup"><span data-stu-id="28ecc-117">The additional features include PowerPivot Gallery, Schedule Data Refresh, and the PowerPivot Management Dashboard.</span></span>  
  
 <span data-ttu-id="28ecc-118">![SSAS PowerPivot 模式 2 伺服器部署](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot 模式 2 伺服器部署")</span><span class="sxs-lookup"><span data-stu-id="28ecc-118">![SSAS PowerPivot Mode 2 Server Deployment](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot Mode 2 Server Deployment")</span></span>  
  
## <a name="powerpivot-for-sharepoint-2010"></a><span data-ttu-id="28ecc-119">PowerPivot for SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="28ecc-119">PowerPivot for SharePoint 2010</span></span>  
 <span data-ttu-id="28ecc-120">PowerPivot for SharePoint 2010 提供將 PowerPivot 資料裝載於 SharePoint 2010 伺服器陣列的功能。</span><span class="sxs-lookup"><span data-stu-id="28ecc-120">PowerPivot for SharePoint 2010 provides server hosting of PowerPivot data in a SharePoint 2010 farm.</span></span> <span data-ttu-id="28ecc-121">PowerPivot 資料是使用 PowerPivot for Excel 增益集在 Excel 中建立的分析資料模型。</span><span class="sxs-lookup"><span data-stu-id="28ecc-121">PowerPivot data is an analytical data model that you build in Excel using the PowerPivot for Excel add-in.</span></span> <span data-ttu-id="28ecc-122">這些資料的伺服器裝載需要 SharePoint 2010、Excel Services 和 PowerPivot for SharePoint 安裝。</span><span class="sxs-lookup"><span data-stu-id="28ecc-122">Server hosting of that data requires SharePoint 2010, Excel Services, and an installation of PowerPivot for SharePoint.</span></span> <span data-ttu-id="28ecc-123">資料載入到伺服器陣列中的 PowerPivot for SharePoint 執行個體，在此處可透過伺服器提供的 PowerPivot 資料重新整理功能，依排程間隔重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="28ecc-123">Data is loaded on PowerPivot for SharePoint instances in the farm, where it can be refreshed at scheduled intervals using the PowerPivot data refresh capability that the server provides.</span></span>  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a><span data-ttu-id="28ecc-124">PowerPivot for SharePoint 2010 的元件</span><span class="sxs-lookup"><span data-stu-id="28ecc-124">Components of PowerPivot for SharePoint 2010</span></span>  
 <span data-ttu-id="28ecc-125">PowerPivot for SharePoint 實作為共用服務，這表示內建功能和基礎結構可用來管理、保護和使用 PowerPivot 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="28ecc-125">PowerPivot for SharePoint is implemented as a shared service, which means that the built-in features and infrastructure can be used to administer, secure, and use a PowerPivot service application.</span></span> <span data-ttu-id="28ecc-126">伺服器和資料庫探索、重新導向和連接管理全都是在伺服器陣列層級管理。</span><span class="sxs-lookup"><span data-stu-id="28ecc-126">Server and database discovery, redirection, and connection management is all managed at the farm level.</span></span> <span data-ttu-id="28ecc-127">管理中心提供用來管理伺服器識別、伺服器狀態和組態屬性之服務的管理介面。</span><span class="sxs-lookup"><span data-stu-id="28ecc-127">Central Administration provides the administrative interface to the services used to manage server identity, server state, and configuration properties.</span></span>  
  
 <span data-ttu-id="28ecc-128">PowerPivot for SharePoint 的完整部署包含在 SharePoint 伺服器陣列中與 Excel 和 Excel Services 整合的用戶端與伺服器元件。</span><span class="sxs-lookup"><span data-stu-id="28ecc-128">A complete deployment of PowerPivot for SharePoint includes client and server components that integrate with Excel and Excel Services in a SharePoint farm.</span></span> <span data-ttu-id="28ecc-129">Excel 活頁簿內的 PowerPivot 資料是一種 Analysis Services 資料庫，它需要 Analysis Services xVelocity 記憶體中分析引擎 (VertiPaq) 以載入和查詢資料。</span><span class="sxs-lookup"><span data-stu-id="28ecc-129">The PowerPivot data inside an Excel workbook is an Analysis Services database that requires an Analysis Services xVelocity in-memory analytics engine (VertiPaq) to load and query the data.</span></span> <span data-ttu-id="28ecc-130">在用戶端工作站上，xVelocity 引擎會在 Excel 中以同處理序執行。</span><span class="sxs-lookup"><span data-stu-id="28ecc-130">On a client workstation, the xVelocity engine runs in-process within Excel.</span></span> <span data-ttu-id="28ecc-131">在 SharePoint 伺服器陣列中，Analysis Services 會在應用程式伺服器上執行，並與處理 PowerPivot 資料要求的相關服務搭配使用。</span><span class="sxs-lookup"><span data-stu-id="28ecc-131">On a SharePoint farm, Analysis Services runs on an application server where it is paired with related services that handle requests for PowerPivot data.</span></span> <span data-ttu-id="28ecc-132">下圖說明 PowerPivot 用戶端與伺服器元件：</span><span class="sxs-lookup"><span data-stu-id="28ecc-132">The following diagram illustrates PowerPivot client and server components:</span></span>  
  
 <span data-ttu-id="28ecc-133">![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")</span><span class="sxs-lookup"><span data-stu-id="28ecc-133">![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")</span></span>  
  
 <span data-ttu-id="28ecc-134">PowerPivot Web 服務在 Web 應用程式伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="28ecc-134">PowerPivot Web service runs on a web application server.</span></span> <span data-ttu-id="28ecc-135">它會將來自 Web 應用程式的要求導向至伺服器陣列中的 PowerPivot 系統服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="28ecc-135">It redirects requests from the web application to a PowerPivot System Service instance in the farm.</span></span>  
  
 <span data-ttu-id="28ecc-136">PowerPivot 系統服務會將載入要求發給 Analysis Services 伺服器，以及管理已載入記憶體之資料的進行中連接，並且於不再使用資料或系統資源有競爭時，快取或卸載資料。</span><span class="sxs-lookup"><span data-stu-id="28ecc-136">PowerPivot System Service issues load requests to the Analysis Services server and manages ongoing connections to data that is already loaded in memory, caching or unloading data if it is no longer used or when there is contention for system resources.</span></span> <span data-ttu-id="28ecc-137">它也會追蹤使用者活動。</span><span class="sxs-lookup"><span data-stu-id="28ecc-137">It also tracks user activity.</span></span> <span data-ttu-id="28ecc-138">在報表中收集及呈現伺服器健全狀況資料和其他使用量資料，以表示系統的執行效能。</span><span class="sxs-lookup"><span data-stu-id="28ecc-138">Server health data and other usage data is gathered and presented in reports to indicate how well the system is performing.</span></span>  
  
 <span data-ttu-id="28ecc-139">SharePoint 整合模式的 Analysis Service 伺服器執行個體會完成部署。</span><span class="sxs-lookup"><span data-stu-id="28ecc-139">An Analysis Service server instance in SharePoint integrated mode completes the deployment.</span></span> <span data-ttu-id="28ecc-140">它會載入、查詢和卸載資料。</span><span class="sxs-lookup"><span data-stu-id="28ecc-140">It loads, queries, and unloads data.</span></span> <span data-ttu-id="28ecc-141">如果活頁簿設定為使用 PowerPivot 資料重新整理，它也會處理資料。</span><span class="sxs-lookup"><span data-stu-id="28ecc-141">It also processes data if the workbook is configured for PowerPivot data refresh.</span></span>  <span data-ttu-id="28ecc-142">每個執行個體會與相同安裝中的本機 PowerPivot 系統服務緊密結合在一起。</span><span class="sxs-lookup"><span data-stu-id="28ecc-142">Each instance is tightly coupled with the local PowerPivot System Service that is part of the same installation.</span></span>  
  
##  <a name="in-this-section"></a><a name="bkmk_RelatedContent"></a> <span data-ttu-id="28ecc-143">本節內容</span><span class="sxs-lookup"><span data-stu-id="28ecc-143">In This Section</span></span>  
 [<span data-ttu-id="28ecc-144">管理中心的 PowerPivot 伺服器管理和設定</span><span class="sxs-lookup"><span data-stu-id="28ecc-144">PowerPivot Server Administration and Configuration in Central Administration</span></span>](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [<span data-ttu-id="28ecc-145">使用 Windows PowerShell 的 PowerPivot 設定</span><span class="sxs-lookup"><span data-stu-id="28ecc-145">PowerPivot Configuration using Windows PowerShell</span></span>](power-pivot-configuration-using-windows-powershell.md)  
  
 [<span data-ttu-id="28ecc-146">PowerPivot 設定工具</span><span class="sxs-lookup"><span data-stu-id="28ecc-146">PowerPivot Configuration Tools</span></span>](power-pivot-configuration-tools.md)  
  
 [<span data-ttu-id="28ecc-147">PowerPivot 驗證及授權</span><span class="sxs-lookup"><span data-stu-id="28ecc-147">PowerPivot Authentication and Authorization</span></span>](power-pivot-authentication-and-authorization.md)  
  
 [<span data-ttu-id="28ecc-148">PowerPivot 健全狀況規則 - 設定</span><span class="sxs-lookup"><span data-stu-id="28ecc-148">PowerPivot Health Rules - Configure</span></span>](configure-power-pivot-health-rules.md)  
  
 [<span data-ttu-id="28ecc-149">PowerPivot 管理儀表板和使用量資料</span><span class="sxs-lookup"><span data-stu-id="28ecc-149">PowerPivot Management Dashboard and Usage Data</span></span>](power-pivot-management-dashboard-and-usage-data.md)  
  
 [<span data-ttu-id="28ecc-150">PowerPivot 圖庫</span><span class="sxs-lookup"><span data-stu-id="28ecc-150">PowerPivot Gallery</span></span>](../../index.yml)  
  
 [<span data-ttu-id="28ecc-151">PowerPivot 資料存取</span><span class="sxs-lookup"><span data-stu-id="28ecc-151">PowerPivot Data Access</span></span>](power-pivot-data-access.md)  
  
 [<span data-ttu-id="28ecc-152">PowerPivot 資料重新整理</span><span class="sxs-lookup"><span data-stu-id="28ecc-152">PowerPivot Data Refresh</span></span>](power-pivot-data-refresh.md)  
  
 [<span data-ttu-id="28ecc-153">PowerPivot 資料摘要</span><span class="sxs-lookup"><span data-stu-id="28ecc-153">PowerPivot Data Feeds</span></span>](power-pivot-data-feeds.md)  
  
 [<span data-ttu-id="28ecc-154">PowerPivot BI 語義模型連接 &#40;. bism&#41;</span><span class="sxs-lookup"><span data-stu-id="28ecc-154">PowerPivot BI Semantic Model Connection &#40;.bism&#41;</span></span>](power-pivot-bi-semantic-model-connection-bism.md)  
  
 <span data-ttu-id="28ecc-155">**其他章節內容**</span><span class="sxs-lookup"><span data-stu-id="28ecc-155">**In other sections**</span></span>  
  
## <a name="additional-topics"></a><span data-ttu-id="28ecc-156">其他主題</span><span class="sxs-lookup"><span data-stu-id="28ecc-156">Additional topics</span></span>  
 [<span data-ttu-id="28ecc-157">升級 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="28ecc-157">Upgrade PowerPivot for SharePoint</span></span>](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [<span data-ttu-id="28ecc-158">PowerPivot for SharePoint 2013 安裝</span><span class="sxs-lookup"><span data-stu-id="28ecc-158">PowerPivot for SharePoint 2013 Installation</span></span>](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [<span data-ttu-id="28ecc-159">PowerPivot for SharePoint 的 PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="28ecc-159">PowerShell Reference for PowerPivot for SharePoint</span></span>](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [<span data-ttu-id="28ecc-160">SQL Server 2014 自助商業智慧的授權拓撲和成本範例</span><span class="sxs-lookup"><span data-stu-id="28ecc-160">Example License Topologies and Costs  for SQL Server 2014 Self-Service Business Intelligence</span></span>](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a><span data-ttu-id="28ecc-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28ecc-161">See Also</span></span>  
 <span data-ttu-id="28ecc-162">[PowerPivot 規劃與部署](https://go.microsoft.com/fwlink/?linkID=220972) </span><span class="sxs-lookup"><span data-stu-id="28ecc-162">[PowerPivot Planning and Deployment](https://go.microsoft.com/fwlink/?linkID=220972) </span></span>  
 [<span data-ttu-id="28ecc-163">PowerPivot for SharePoint 災害復原</span><span class="sxs-lookup"><span data-stu-id="28ecc-163">Disaster Recovery for PowerPivot for SharePoint</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
