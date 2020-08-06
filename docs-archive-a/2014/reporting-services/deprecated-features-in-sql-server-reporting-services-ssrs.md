---
title: SQL Server 2014 中 SQL Server Reporting Services 已被取代的功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af858ae94bf5ea3d9f0cfe0b99759442dabd6629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596540"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a><span data-ttu-id="a313c-102">SQL Server 2014 中 SQL Server Reporting Services 已被取代的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-102">Deprecated Features in SQL Server Reporting Services in SQL Server 2014</span></span>
  <span data-ttu-id="a313c-103">本主題描述已被取代的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="a313c-103">This topic describes the deprecated [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="a313c-104">在此版本中仍然提供已被取代的功能，不過，這些功能排程在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]之後版本中移除。</span><span class="sxs-lookup"><span data-stu-id="a313c-104">The features are still available in the release in which they are deprecated; however the features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a313c-105">已被取代的功能不應在新應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="a313c-105">Deprecated features should not be used in new applications.</span></span>  
  
 <span data-ttu-id="a313c-106">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="a313c-106">In this topic:</span></span>  
  
-   [<span data-ttu-id="a313c-107">SQL Server 2014 Reporting Services 已淘汰功能</span><span class="sxs-lookup"><span data-stu-id="a313c-107">SQL Server 2014 Reporting Services Deprecated Features</span></span>](#bkmk_2014)  
  
-   [<span data-ttu-id="a313c-108">SQL Server 2012 SP1 Reporting Services 已被取代的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-108">SQL Server 2012 SP1 Reporting Services Deprecated Features</span></span>](#bkmk_2012sp1)  
  
-   [<span data-ttu-id="a313c-109">SQL Server 2012 Reporting Services 已淘汰功能</span><span class="sxs-lookup"><span data-stu-id="a313c-109">SQL Server 2012 Reporting Services Deprecated Features</span></span>](#bkmk_2012)  
  
-   [<span data-ttu-id="a313c-110">SQL Server 2008 R2 Reporting Services 已被取代的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-110">SQL Server 2008 R2 Reporting Services Deprecated Features</span></span>](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a><span data-ttu-id="a313c-111">SQL Server 2014 Reporting Services 已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-111">SQL Server 2014 Reporting Services Deprecated Features</span></span>  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a><span data-ttu-id="a313c-112">下一版的 SQL Server 不支援的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-112">Features Not Supported in the Next Version of SQL Server</span></span>  
 <span data-ttu-id="a313c-113">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]**下一**版的將不再支援下列功能 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a313c-113">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features will not be supported in the **next** version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a313c-114">請勿在新的開發工作中使用這些功能，並且儘速修改使用這些功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a313c-114">Do not use these features in new development work, and modify applications that currently use these features as soon as possible.</span></span>  
  
#### <a name="html-rendering-extension-device-information-settings"></a><span data-ttu-id="a313c-115">HTML 轉譯延伸模組的裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="a313c-115">HTML Rendering Extension Device Information Settings</span></span>  
 <span data-ttu-id="a313c-116">下列 HTML 轉譯延伸模組的裝置資訊設定已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-116">The following device information settings for the HTML rendering extension are deprecated.</span></span>  
  
-   <span data-ttu-id="a313c-117">ActionScript</span><span class="sxs-lookup"><span data-stu-id="a313c-117">ActionScript</span></span>  
  
-   <span data-ttu-id="a313c-118">ActiveXControls</span><span class="sxs-lookup"><span data-stu-id="a313c-118">ActiveXControls</span></span>  
  
-   <span data-ttu-id="a313c-119">GetImage</span><span class="sxs-lookup"><span data-stu-id="a313c-119">GetImage</span></span>  
  
-   <span data-ttu-id="a313c-120">OnlyVisibleStyles</span><span class="sxs-lookup"><span data-stu-id="a313c-120">OnlyVisibleStyles</span></span>  
  
-   <span data-ttu-id="a313c-121">ReplacementRoot</span><span class="sxs-lookup"><span data-stu-id="a313c-121">ReplacementRoot</span></span>  
  
-   <span data-ttu-id="a313c-122">ResourceStreamRoot</span><span class="sxs-lookup"><span data-stu-id="a313c-122">ResourceStreamRoot</span></span>  
  
-   <span data-ttu-id="a313c-123">StreamRoot</span><span class="sxs-lookup"><span data-stu-id="a313c-123">StreamRoot</span></span>  
  
-   <span data-ttu-id="a313c-124">UsePx</span><span class="sxs-lookup"><span data-stu-id="a313c-124">UsePx</span></span>  
  
-   <span data-ttu-id="a313c-125">Zoom</span><span class="sxs-lookup"><span data-stu-id="a313c-125">Zoom</span></span>  
  
 <span data-ttu-id="a313c-126">如需有關 HTML 轉譯延伸模組的詳細資訊，請參閱＜ [HTML Device Information Settings](html-device-information-settings.md)＞</span><span class="sxs-lookup"><span data-stu-id="a313c-126">For more information on the HTML rendering extension, see [HTML Device Information Settings](html-device-information-settings.md)</span></span>  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a><span data-ttu-id="a313c-127">Microsoft Word 和 Microsoft Excel 1997-2003 轉譯</span><span class="sxs-lookup"><span data-stu-id="a313c-127">Microsoft Word and Microsoft Excel 1997-2003 Rendering</span></span>  
 <span data-ttu-id="a313c-128">BIFF8 轉譯延伸模組會 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 向 [!INCLUDE[msCoName](../includes/msconame-md.md)] Word 和 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 二進位交換檔案格式報告。</span><span class="sxs-lookup"><span data-stu-id="a313c-128">The[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 rendering extensions [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Word and [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 binary interchange file format.</span></span> [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="a313c-129">包含以 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 OPEN XML 格式呈現的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a313c-129">includes extensions that render in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML format.</span></span>  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a><span data-ttu-id="a313c-130">報表定義語言 (RDL) 2005 和更早版本</span><span class="sxs-lookup"><span data-stu-id="a313c-130">Report Definition Language (RDL) 2005 and Earlier</span></span>  
 <span data-ttu-id="a313c-131">報表定義語言 (RDL) 和更早版本已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-131">Report Definition Language (RDL) 2005 and earlier is deprecated.</span></span> <span data-ttu-id="a313c-132">如需 RDL 的詳細資訊，請參閱[報表定義語言 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a313c-132">For more information about RDL, see [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).</span></span>  
  
 <span data-ttu-id="a313c-133">如需有關升級報表的詳細資訊，請參閱＜ [Upgrade Reports](install-windows/upgrade-reports.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a313c-133">For more information on upgrading reports, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a><span data-ttu-id="a313c-134">SQL Server 2005 和更早版本的自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="a313c-134">SQL Server 2005 and earlier Custom Report Items</span></span>  
 <span data-ttu-id="a313c-135">針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005 和更早版本編譯的自訂報表專案 (CRI) 已 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-135">Custom Report Items (CRI) compiled for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a><span data-ttu-id="a313c-136">Reporting Services Snapshots 2005 和更早版本</span><span class="sxs-lookup"><span data-stu-id="a313c-136">Reporting Services Snapshots 2005 and earlier</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="a313c-137">以 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 和更早版本轉譯的快照集已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-137">snapshots rendered with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
#### <a name="report-models"></a><span data-ttu-id="a313c-138">報表模型</span><span class="sxs-lookup"><span data-stu-id="a313c-138">Report Models</span></span>  
 <span data-ttu-id="a313c-139">語意模型語言 (SMDL) 報表模型已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-139">Semantic modeling language (SMDL) report models are deprecated.</span></span> <span data-ttu-id="a313c-140">雖然您可以繼續使用現有的報表模型做為報表中的資料來源，但您 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 應該考慮更新報表，以便移除它們對報表模型的相依性。</span><span class="sxs-lookup"><span data-stu-id="a313c-140">Although you can you continue to use existing report models as data sources in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports you should consider updating your reports to remove their dependency on report models.</span></span>  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="a313c-141">不 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 包含用來建立或更新報表模型的工具。</span><span class="sxs-lookup"><span data-stu-id="a313c-141">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] does not include tools for creating or updating report models.</span></span> <span data-ttu-id="a313c-142">如需詳細資訊，請參閱[SQL Server 2014 中 SQL Server Reporting Services 的重大變更](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="a313c-142">For more information, see [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).</span></span>  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a><span data-ttu-id="a313c-143">Web 服務端點中已被取代的方法</span><span class="sxs-lookup"><span data-stu-id="a313c-143">Deprecated Methods in the Web Service Endpoint</span></span>  
 <span data-ttu-id="a313c-144"> Web 服務端點中的下列作業已被取代：</span><span class="sxs-lookup"><span data-stu-id="a313c-144">The following operations are deprecated in the <xref:ReportService2010.ReportingService2010> Web service endpoint:</span></span>  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a><span data-ttu-id="a313c-145">SharePoint Web 組件</span><span class="sxs-lookup"><span data-stu-id="a313c-145">SharePoint Web Parts</span></span>  
 <span data-ttu-id="a313c-146">安裝封包檔 **RSWebParts.cab** 以及可從此 cab 檔案解壓縮的 SharePoint Web 組件已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-146">The installation cabinet file **RSWebParts.cab** and the SharePoint web parts that can be extracted from the cab file, are deprecated.</span></span> <span data-ttu-id="a313c-147">已被取代的 web 元件是報表瀏覽器 (**spexplorer.dwp**) 和報表檢視器 (**spviewer.dwp**) 。</span><span class="sxs-lookup"><span data-stu-id="a313c-147">The deprecated web parts are Report Explorer (**SPExplorer.dwp**) and Report Viewer (**SPViewer.dwp**).</span></span>  
  
 <span data-ttu-id="a313c-148">如需已被取代之 web 元件的詳細資訊，請參閱[使用 SharePoint Web 組件 (SSRS 查看和流覽原生模式報表) ](https://msdn.microsoft.com/library/ms159772.aspx)</span><span class="sxs-lookup"><span data-stu-id="a313c-148">For more information on the deprecated web parts, see [View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span></span>  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a><span data-ttu-id="a313c-149">SQL Server 的未來版本不支援的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-149">Features Not Supported in a Future Version of SQL Server</span></span>  
 <span data-ttu-id="a313c-150">下一版的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 可支援下列 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]功能，但會在更新的版本中移除。</span><span class="sxs-lookup"><span data-stu-id="a313c-150">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="a313c-151">確實的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本尚未決定。</span><span class="sxs-lookup"><span data-stu-id="a313c-151">The specific version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has not been determined.</span></span>  
  
 <span data-ttu-id="a313c-152">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中沒有已被取代的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="a313c-152">No [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features were deprecated in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a><span data-ttu-id="a313c-153">SQL Server 2012 SP1 Reporting Services 已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-153">SQL Server 2012 SP1 Reporting Services Deprecated Features</span></span>  
 <span data-ttu-id="a313c-154">本節描述 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中已被取代的 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="a313c-154">This section describes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features deprecated in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].</span></span> <span data-ttu-id="a313c-155">下一版的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 可支援下列 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]功能，但會在更新的版本中移除。</span><span class="sxs-lookup"><span data-stu-id="a313c-155">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="a313c-156">確實的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 版本尚未決定。</span><span class="sxs-lookup"><span data-stu-id="a313c-156">The specific version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] has not been determined.</span></span>  
  
### <a name="sharepoint-web-parts"></a><span data-ttu-id="a313c-157">SharePoint Web 組件</span><span class="sxs-lookup"><span data-stu-id="a313c-157">SharePoint Web Parts</span></span>  
 <span data-ttu-id="a313c-158">安裝封包檔 **RSWebParts.cab** 以及可從此 cab 檔案解壓縮的 SharePoint Web 組件已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-158">The installation cabinet file **RSWebParts.cab** and the SharePoint web parts that can be extracted from the cab file, are deprecated.</span></span> <span data-ttu-id="a313c-159">已被取代的 web 元件是報表瀏覽器 (**spexplorer.dwp**) 和報表檢視器 (**spviewer.dwp**) 。</span><span class="sxs-lookup"><span data-stu-id="a313c-159">The deprecated web parts are Report Explorer (**SPExplorer.dwp**) and Report Viewer (**SPViewer.dwp**).</span></span>  
  
 <span data-ttu-id="a313c-160">如需已被取代之 web 元件的詳細資訊，請參閱[使用 SharePoint Web 組件 (SSRS 查看和流覽原生模式報表) ](https://msdn.microsoft.com/library/ms159772.aspx)</span><span class="sxs-lookup"><span data-stu-id="a313c-160">For more information on the deprecated web parts, see [View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span></span>  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a><span data-ttu-id="a313c-161">SQL Server 2012 Reporting Services 已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-161">SQL Server 2012 Reporting Services Deprecated Features</span></span>  
 <span data-ttu-id="a313c-162">本節描述 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中已被取代的 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="a313c-162">This section describes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features deprecated in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="html-rendering-extension-device-information-settings"></a><span data-ttu-id="a313c-163">HTML 轉譯延伸模組的裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="a313c-163">HTML Rendering Extension Device Information Settings</span></span>  
 <span data-ttu-id="a313c-164">下列 HTML 轉譯延伸模組的裝置資訊設定已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-164">The following device information settings for the HTML rendering extension are deprecated.</span></span>  
  
-   <span data-ttu-id="a313c-165">ActionScript</span><span class="sxs-lookup"><span data-stu-id="a313c-165">ActionScript</span></span>  
  
-   <span data-ttu-id="a313c-166">ActiveXControls</span><span class="sxs-lookup"><span data-stu-id="a313c-166">ActiveXControls</span></span>  
  
-   <span data-ttu-id="a313c-167">GetImage</span><span class="sxs-lookup"><span data-stu-id="a313c-167">GetImage</span></span>  
  
-   <span data-ttu-id="a313c-168">OnlyVisibleStyles</span><span class="sxs-lookup"><span data-stu-id="a313c-168">OnlyVisibleStyles</span></span>  
  
-   <span data-ttu-id="a313c-169">ReplacementRoot</span><span class="sxs-lookup"><span data-stu-id="a313c-169">ReplacementRoot</span></span>  
  
-   <span data-ttu-id="a313c-170">ResourceStreamRoot</span><span class="sxs-lookup"><span data-stu-id="a313c-170">ResourceStreamRoot</span></span>  
  
-   <span data-ttu-id="a313c-171">StreamRoot</span><span class="sxs-lookup"><span data-stu-id="a313c-171">StreamRoot</span></span>  
  
-   <span data-ttu-id="a313c-172">UsePx</span><span class="sxs-lookup"><span data-stu-id="a313c-172">UsePx</span></span>  
  
-   <span data-ttu-id="a313c-173">Zoom</span><span class="sxs-lookup"><span data-stu-id="a313c-173">Zoom</span></span>  
  
 <span data-ttu-id="a313c-174">如需有關 HTML 轉譯延伸模組的詳細資訊，請參閱＜ [HTML Device Information Settings](html-device-information-settings.md)＞</span><span class="sxs-lookup"><span data-stu-id="a313c-174">For more information on the HTML rendering extension, see [HTML Device Information Settings](html-device-information-settings.md)</span></span>  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a><span data-ttu-id="a313c-175">Microsoft Word 和 Microsoft Excel 1997-2003 轉譯</span><span class="sxs-lookup"><span data-stu-id="a313c-175">Microsoft Word and Microsoft Excel 1997-2003 Rendering</span></span>  
 <span data-ttu-id="a313c-176">BIFF8 轉譯延伸模組會 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 向 [!INCLUDE[msCoName](../includes/msconame-md.md)] Word 和 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 二進位交換檔案格式報告。</span><span class="sxs-lookup"><span data-stu-id="a313c-176">The[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 rendering extensions [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Word and [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 binary interchange file format.</span></span> [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="a313c-177">包含以 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 OPEN XML 格式呈現的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a313c-177">includes extensions that render in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML format.</span></span>  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a><span data-ttu-id="a313c-178">報表定義語言 (RDL) 2005 和更早版本</span><span class="sxs-lookup"><span data-stu-id="a313c-178">Report Definition Language (RDL) 2005 and Earlier</span></span>  
 <span data-ttu-id="a313c-179">報表定義語言 (RDL) 和更早版本已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-179">Report Definition Language (RDL) 2005 and earlier is deprecated.</span></span> <span data-ttu-id="a313c-180">如需 RDL 的詳細資訊，請參閱[報表定義語言 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a313c-180">For more information about RDL, see [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).</span></span>  
  
 <span data-ttu-id="a313c-181">如需有關升級報表的詳細資訊，請參閱＜ [Upgrade Reports](install-windows/upgrade-reports.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a313c-181">For more information on upgrading reports, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a><span data-ttu-id="a313c-182">SQL Server 2005 和更早版本的自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="a313c-182">SQL Server 2005 and earlier Custom Report Items</span></span>  
 <span data-ttu-id="a313c-183">針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005 和更早版本編譯的自訂報表專案 (CRI) 已 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-183">Custom Report Items (CRI) compiled for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a><span data-ttu-id="a313c-184">Reporting Services Snapshots 2005 和更早版本</span><span class="sxs-lookup"><span data-stu-id="a313c-184">Reporting Services Snapshots 2005 and earlier</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="a313c-185">以 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 和更早版本轉譯的快照集已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-185">snapshots rendered with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
### <a name="report-models"></a><span data-ttu-id="a313c-186">報表模型</span><span class="sxs-lookup"><span data-stu-id="a313c-186">Report Models</span></span>  
 <span data-ttu-id="a313c-187">語意模型語言 (SMDL) 報表模型已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-187">Semantic modeling language (SMDL) report models are deprecated.</span></span> <span data-ttu-id="a313c-188">雖然您可以繼續使用現有的報表模型做為報表中的資料來源，但您 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 應該考慮更新報表，以便移除它們對報表模型的相依性。</span><span class="sxs-lookup"><span data-stu-id="a313c-188">Although you can you continue to use existing report models as data sources in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports you should consider updating your reports to remove their dependency on report models.</span></span>  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="a313c-189">不 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 包含用來建立或更新報表模型的工具。</span><span class="sxs-lookup"><span data-stu-id="a313c-189">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] does not include tools for creating or updating report models.</span></span> <span data-ttu-id="a313c-190">如需詳細資訊，請參閱[SQL Server 2014 中 SQL Server Reporting Services 的重大變更](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="a313c-190">For more information, see [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).</span></span>  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a><span data-ttu-id="a313c-191">Web 服務端點中已被取代的方法</span><span class="sxs-lookup"><span data-stu-id="a313c-191">Deprecated Methods in the Web Service Endpoint</span></span>  
 <span data-ttu-id="a313c-192"> Web 服務端點中的下列作業已被取代：</span><span class="sxs-lookup"><span data-stu-id="a313c-192">The following operations are deprecated in the <xref:ReportService2010.ReportingService2010> Web service endpoint:</span></span>  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a><span data-ttu-id="a313c-193">SQL Server 2008 R2 Reporting Services 已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="a313c-193">SQL Server 2008 R2 Reporting Services Deprecated Features</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a313c-194">因為 SQL Server 2008 R2 是 SQL Server 2008 的次要版本更新，所以建議您也檢閱 SQL Server 2008 章節中的內容。</span><span class="sxs-lookup"><span data-stu-id="a313c-194">Because SQL Server 2008 R2 is a minor version upgrade of SQL Server 2008, we recommend that you also review the content in the SQL Server 2008 section.</span></span>  
  
### <a name="report-server-web-service-endpoints"></a><span data-ttu-id="a313c-195">報表伺服器 Web 服務端點</span><span class="sxs-lookup"><span data-stu-id="a313c-195">Report Server Web Service Endpoints</span></span>  
 <span data-ttu-id="a313c-196">Web 服務 <xref:ReportService2005.ReportingService2005> 和 <xref:ReportService2006.ReportingService2006> 在此版本中已被取代。</span><span class="sxs-lookup"><span data-stu-id="a313c-196">The Web services <xref:ReportService2005.ReportingService2005> and <xref:ReportService2006.ReportingService2006> have been deprecated in this release.</span></span> <span data-ttu-id="a313c-197">這些端點已由新端點所取代：<xref:ReportService2010.ReportingService2010>。</span><span class="sxs-lookup"><span data-stu-id="a313c-197">These endpoints have been replaced by a new endpoint: <xref:ReportService2010.ReportingService2010>.</span></span>  
  
 <span data-ttu-id="a313c-198">新端點包含可在已被取代之端點中使用的所有功能，以及 SQL Server 2008 R2 中所引進的新功能。</span><span class="sxs-lookup"><span data-stu-id="a313c-198">The new endpoint includes all the functionality available in the deprecated endpoints and the new features introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a313c-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a313c-199">See Also</span></span>  
 <span data-ttu-id="a313c-200">[Reporting Services 的新 &#40;&#41;](what-s-new-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="a313c-200">[What's New &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span></span>  
 <span data-ttu-id="a313c-201">[回溯相容性](../getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="a313c-201">[Backward Compatibility](../getting-started/backward-compatibility.md) </span></span>  
 <span data-ttu-id="a313c-202">[SQL Server 2014 中 SQL Server Reporting Services 的行為變更](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="a313c-202">[Behavior Changes to SQL Server Reporting Services  in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md) </span></span>  
 [<span data-ttu-id="a313c-203">SQL Server 2014 中已中止的 SQL Server Reporting Services 功能</span><span class="sxs-lookup"><span data-stu-id="a313c-203">Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014</span></span>](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
