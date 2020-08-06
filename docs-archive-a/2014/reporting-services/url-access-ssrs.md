---
title: URL 存取 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services]
- links [Reporting Services], URL access
- URL access [Reporting Services], about URL access
- parameters [Reporting Services], URL access
- report servers [Reporting Services], URL access
- hyperlinks [Reporting Services]
ms.assetid: 52c3f2a3-3d6d-4fee-9c46-83f366919398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf44ea3c15c12f37eebf6e89faf4ff3affd64433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594357"
---
# <a name="url-access-ssrs"></a><span data-ttu-id="cb791-102">URL 存取 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="cb791-102">URL Access (SSRS)</span></span>
  <span data-ttu-id="cb791-103">在 SQL Server Reporting Services (SSRS) 中，報表伺服器的 URL 存取權可讓您透過 URL 要求，傳送命令至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="cb791-103">URL access of the report server in SQL Server Reporting Services (SSRS) enables you to send commands to a report server through a URL request.</span></span> <span data-ttu-id="cb791-104">例如，您可在原生模式報表伺服器或 SharePoint 文件庫中自訂報表的轉譯。</span><span class="sxs-lookup"><span data-stu-id="cb791-104">For example, you can customize the rendering of a report on a native mode report server or in a SharePoint library.</span></span> <span data-ttu-id="cb791-105">您可能已使用特定一組報表參數值來檢視過報表，或報表中您感興趣的特定頁面。</span><span class="sxs-lookup"><span data-stu-id="cb791-105">You may have viewed the report using a specific set of report parameter values, or you may have been viewing a particular page of interest in the report.</span></span> <span data-ttu-id="cb791-106">您可以使用預先定義的 URL 存取參數，封裝 URL 中的資訊。</span><span class="sxs-lookup"><span data-stu-id="cb791-106">You can encapsulate this information in the URL using predefined URL access parameters.</span></span> <span data-ttu-id="cb791-107">您還可以內嵌轉譯格式或調整報表檢視器外觀的參數，以進一步自訂報表伺服器處理報表的方式。</span><span class="sxs-lookup"><span data-stu-id="cb791-107">You can further customize how the report server processes the report by embedding parameters for rendering formats or for the look and feel of the report viewer.</span></span> <span data-ttu-id="cb791-108">然後，您可以直接將此 URL 貼入電子郵件或網頁，讓其他人在瀏覽器中用相同方式存取您的報表。</span><span class="sxs-lookup"><span data-stu-id="cb791-108">You can then paste this URL directly into an email or Web page to let others to access your report in the same manner in the browser.</span></span>  
  
 <span data-ttu-id="cb791-109">您還可利用 URL 存取執行下列其他動作：</span><span class="sxs-lookup"><span data-stu-id="cb791-109">Other actions you can perform through URL access are:</span></span>  
  
-   <span data-ttu-id="cb791-110">傳送命令至 HTML 檢視器，例如調整其外觀</span><span class="sxs-lookup"><span data-stu-id="cb791-110">Send commands to the HTML viewer, such as adjusting its look and feel</span></span>  
  
-   <span data-ttu-id="cb791-111">列出目錄資料夾的子系</span><span class="sxs-lookup"><span data-stu-id="cb791-111">List the children of a catalog folder</span></span>  
  
-   <span data-ttu-id="cb791-112">擷取目錄項目的 XML 定義</span><span class="sxs-lookup"><span data-stu-id="cb791-112">Retrieve the XML definition of a catalog item</span></span>  
  
-   <span data-ttu-id="cb791-113">轉譯特定的報表記錄快照集</span><span class="sxs-lookup"><span data-stu-id="cb791-113">Render a specific report history snapshot</span></span>  
  
-   <span data-ttu-id="cb791-114">管理報表工作階段</span><span class="sxs-lookup"><span data-stu-id="cb791-114">Manage report sessions</span></span>  
  
 <span data-ttu-id="cb791-115">如需透過 URL 存取可用之命令與設定的完整清單，請參閱 [URL 存取參數參考](url-access-parameter-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="cb791-115">For the complete list of commands and settings available through URL access, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span>  
  
## <a name="url-access-concepts"></a><span data-ttu-id="cb791-116">URL 存取概念</span><span class="sxs-lookup"><span data-stu-id="cb791-116">URL Access Concepts</span></span>  
 <span data-ttu-id="cb791-117">報表伺服器的 URL 要求包含由報表伺服器處理的參數。</span><span class="sxs-lookup"><span data-stu-id="cb791-117">URL requests to the report server contain parameters that are processed by the report server.</span></span> <span data-ttu-id="cb791-118">報表伺服器處理 URL 要求的方法須視 URL 中包含的參數、參數前置詞以及項目類型而定。</span><span class="sxs-lookup"><span data-stu-id="cb791-118">The way in which the report server handles URL requests depends on the parameters, parameter prefixes, and types of items that are included in the URL.</span></span> <span data-ttu-id="cb791-119">報表伺服器 URL 會遵循聯合全球資訊網協會 W3C/IETF 草案標準所提議的 URL 格式指導方針。</span><span class="sxs-lookup"><span data-stu-id="cb791-119">Report server URLs adhere to the URL formatting guidelines as proposed by the joint World Wide Web Consortium W3C/IETF draft standard.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="cb791-120">URL 功能與大部分的網際網路瀏覽器或是支援標準 URL 定址的應用程式相容。</span><span class="sxs-lookup"><span data-stu-id="cb791-120">URL functionality is compatible with most Internet browsers or applications that support standard URL addressing.</span></span>  
  
### <a name="url-access-syntax"></a><span data-ttu-id="cb791-121">URL 存取語法</span><span class="sxs-lookup"><span data-stu-id="cb791-121">URL Access Syntax</span></span>  
 <span data-ttu-id="cb791-122">URL 要求可包含以任何順序所列的多個參數。</span><span class="sxs-lookup"><span data-stu-id="cb791-122">URL requests can contain multiple parameters that are listed in any order.</span></span> <span data-ttu-id="cb791-123">參數是用連字號 (&) 分隔，而名稱/值組則是由等號 (=) 所分隔。</span><span class="sxs-lookup"><span data-stu-id="cb791-123">Parameters are separated by an ampersand (&) and name/value pairs are separated by an equal sign (=).</span></span>  
  
```  
  
rswebserviceurl  
?  
reportpath  
      [&prefix:param=value]...n]  
  
```  
  
### <a name="syntax-description"></a><span data-ttu-id="cb791-124">語法描述</span><span class="sxs-lookup"><span data-stu-id="cb791-124">Syntax Description</span></span>  
 <span data-ttu-id="cb791-125">*rswebserviceurl*</span><span class="sxs-lookup"><span data-stu-id="cb791-125">*rswebserviceurl*</span></span>  
 <span data-ttu-id="cb791-126">報表伺服器 Web 服務 URL。</span><span class="sxs-lookup"><span data-stu-id="cb791-126">The Web service URL of the report server.</span></span> <span data-ttu-id="cb791-127">針對原生模式，其為 Reporting Services 設定管理員中設定之報表伺服器執行個體的 Web 服務 URL (請參閱[設定報表伺服器 URL &#40;SSRS 設定管理員&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md))。</span><span class="sxs-lookup"><span data-stu-id="cb791-127">For native mode, it is the Web service URL of the report server instance configured in Reporting Services Configuration Manager (see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)).</span></span> <span data-ttu-id="cb791-128">例如：</span><span class="sxs-lookup"><span data-stu-id="cb791-128">For example:</span></span>  
  
```  
http://myrshost/reportserver  
https://machine.adventure-works.com/reportserver_MYNAMEDINSTANCE  
```  
  
 <span data-ttu-id="cb791-129">針對 SharePoint 整合模式，其為整合 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 之 SharePoint 網站的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Proxy URL。</span><span class="sxs-lookup"><span data-stu-id="cb791-129">For SharePoint integrated mode, it is the URL of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] proxy at a SharePoint site integrated with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="cb791-130">例如：</span><span class="sxs-lookup"><span data-stu-id="cb791-130">For example:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver  
```  
  
> [!TIP]  
>  <span data-ttu-id="cb791-131">請務必讓 URL 包含 `_vti_bin` Proxy 語法，以便透過 SharePoint 和 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP Proxy 路由傳送要求。</span><span class="sxs-lookup"><span data-stu-id="cb791-131">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="cb791-132">此 Proxy 會將某些內容加入至 HTTP 要求，也就是確保針對 SharePoint 模式報表伺服器正確執行報表所需的內容。</span><span class="sxs-lookup"><span data-stu-id="cb791-132">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
  
 <span data-ttu-id="cb791-133">*pathinfo*</span><span class="sxs-lookup"><span data-stu-id="cb791-133">*pathinfo*</span></span>  
 <span data-ttu-id="cb791-134">原生模式報表伺服器資料庫中項目的相對路徑名稱，或 SharePoint 目錄中項目的完整 URL。</span><span class="sxs-lookup"><span data-stu-id="cb791-134">The relative path name of the item in the native mode report server database, or the fully qualified URL of the item in a SharePoint catalog.</span></span>  
  
 <span data-ttu-id="cb791-135">目錄項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="cb791-135">The path of the catalog item.</span></span> <span data-ttu-id="cb791-136">針對原生模式，其為報表伺服器資料庫中項目的相對路徑名稱，以斜線 (`/`) 開頭。</span><span class="sxs-lookup"><span data-stu-id="cb791-136">For native mode, it is the relative path of the item in the report server database, beginning with a slash (`/`).</span></span> <span data-ttu-id="cb791-137">例如：</span><span class="sxs-lookup"><span data-stu-id="cb791-137">For example:</span></span>  
  
```  
/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2  
```  
  
 <span data-ttu-id="cb791-138">若為 SharePoint 整合模式，其為 SharePoint 文件庫中項目的完整 URL，包括項目延伸模組。</span><span class="sxs-lookup"><span data-stu-id="cb791-138">For SharePoint integrated mode, it is the fully qualified URL of the item in the SharePoint library, including the item extension.</span></span> <span data-ttu-id="cb791-139">例如：</span><span class="sxs-lookup"><span data-stu-id="cb791-139">For example:</span></span>  
  
```  
http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl  
```  
  
 `&`  
 <span data-ttu-id="cb791-140">用以分隔 URL 存取參數的名稱與值組。</span><span class="sxs-lookup"><span data-stu-id="cb791-140">Used to separate name and value pairs of URL access parameters.</span></span>  
  
 <span data-ttu-id="cb791-141">**prefix**</span><span class="sxs-lookup"><span data-stu-id="cb791-141">**prefix**</span></span>  
 <span data-ttu-id="cb791-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cb791-142">Optional.</span></span> <span data-ttu-id="cb791-143">URL 存取參數前置詞 (例如 `rs:` 或 `rc:`)，用以存取在報表伺服器中執行的特定處理序。</span><span class="sxs-lookup"><span data-stu-id="cb791-143">A prefix for the URL access parameter (for example, `rs:` or `rc:`) that accesses a specific process running within the report server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb791-144">如果未包括 URL 存取參數的前置詞，報表伺服器會以報表參數來處理參數。</span><span class="sxs-lookup"><span data-stu-id="cb791-144">If a prefix for a URL access parameter is not included, the parameter is processed by the report server as a report parameter.</span></span> <span data-ttu-id="cb791-145">報表參數不使用參數前置詞，且有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="cb791-145">Report parameters do not use a parameter prefix and are case-sensitive.</span></span>  
  
 <span data-ttu-id="cb791-146">**param**</span><span class="sxs-lookup"><span data-stu-id="cb791-146">**param**</span></span>  
 <span data-ttu-id="cb791-147">參數名稱。</span><span class="sxs-lookup"><span data-stu-id="cb791-147">The parameter name.</span></span>  
  
 <span data-ttu-id="cb791-148">*value*</span><span class="sxs-lookup"><span data-stu-id="cb791-148">*value*</span></span>  
 <span data-ttu-id="cb791-149">對應至要使用的參數值之 URL 文字。</span><span class="sxs-lookup"><span data-stu-id="cb791-149">URL text corresponding to the value of the parameter being used.</span></span>  
  
 <span data-ttu-id="cb791-150">**注意** ：如需可用的 URL 存取參數清單，請參閱 [URL 存取參數參考](url-access-parameter-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="cb791-150">**Note:** For a list of the available URL access parameters, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span> <span data-ttu-id="cb791-151">如需透過 URL 傳遞報表參數的範例，請參閱 [在 URL 內傳遞報表參數](pass-a-report-parameter-within-a-url.md)。</span><span class="sxs-lookup"><span data-stu-id="cb791-151">For examples passing report parameters on the URL, see [Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="cb791-152">相關工作</span><span class="sxs-lookup"><span data-stu-id="cb791-152">Related Tasks</span></span>  
  
|<span data-ttu-id="cb791-153">工作描述</span><span class="sxs-lookup"><span data-stu-id="cb791-153">Task Descriptions</span></span>|<span data-ttu-id="cb791-154">連結</span><span class="sxs-lookup"><span data-stu-id="cb791-154">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="cb791-155">存取報表伺服器項目，如報表、共用資料來源和資源。</span><span class="sxs-lookup"><span data-stu-id="cb791-155">Access report server items, such as reports, shared data sources, and resources.</span></span>|[<span data-ttu-id="cb791-156">使用 URL 存取來存取報表伺服器項目</span><span class="sxs-lookup"><span data-stu-id="cb791-156">Access Report Server Items Using URL Access</span></span>](access-report-server-items-using-url-access.md)|  
|<span data-ttu-id="cb791-157">將報表參數傳遞至報表。</span><span class="sxs-lookup"><span data-stu-id="cb791-157">Pass report parameters to a report.</span></span>|[<span data-ttu-id="cb791-158">在 URL 內傳遞報表參數</span><span class="sxs-lookup"><span data-stu-id="cb791-158">Pass a Report Parameter Within a URL</span></span>](pass-a-report-parameter-within-a-url.md)|  
|<span data-ttu-id="cb791-159">在 URL 存取字串中設定報表參數的地區設定，以定義特定地區的日期、貨幣等轉換。</span><span class="sxs-lookup"><span data-stu-id="cb791-159">Set the locale of the report parameters in the URL access string, which defines the locale-specific interpretations of dates, currencies, and so on.</span></span>|[<span data-ttu-id="cb791-160">在 URL 中設定報表參數的語言</span><span class="sxs-lookup"><span data-stu-id="cb791-160">Set the Language for Report Parameters in a URL</span></span>](set-the-language-for-report-parameters-in-a-url.md)|  
|<span data-ttu-id="cb791-161">傳送可自訂報表轉譯方式的轉譯延伸模組特定設定。</span><span class="sxs-lookup"><span data-stu-id="cb791-161">Send rendering extension specific settings that customize how the report is rendered.</span></span>|[<span data-ttu-id="cb791-162">在 URL 中指定裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="cb791-162">Specify Device Information Settings in a URL</span></span>](specify-device-information-settings-in-a-url.md)|  
|<span data-ttu-id="cb791-163">不在瀏覽器中檢視，而直接將報表匯出至檔案格式。</span><span class="sxs-lookup"><span data-stu-id="cb791-163">Export a report directly to a file format without viewing it in the browser.</span></span>|[<span data-ttu-id="cb791-164">使用 URL 存取匯出報表</span><span class="sxs-lookup"><span data-stu-id="cb791-164">Export a Report Using URL Access</span></span>](export-a-report-using-url-access.md)|  
|<span data-ttu-id="cb791-165">開啟報表，並直接導覽至字串位置。</span><span class="sxs-lookup"><span data-stu-id="cb791-165">Open a report and navigate directly to the location of a string.</span></span>|[<span data-ttu-id="cb791-166">使用 URL 存取搜尋報表</span><span class="sxs-lookup"><span data-stu-id="cb791-166">Search a Report Using URL Access</span></span>](search-a-report-using-url-access.md)|  
|<span data-ttu-id="cb791-167">轉譯特定的報表記錄快照集。</span><span class="sxs-lookup"><span data-stu-id="cb791-167">Render a specific report history snapshot.</span></span>|[<span data-ttu-id="cb791-168">使用 URL 存取轉譯報表記錄快照集</span><span class="sxs-lookup"><span data-stu-id="cb791-168">Render a Report History Snapshot Using URL Access</span></span>](render-a-report-history-snapshot-using-url-access.md)|  
  
## <a name="see-also"></a><span data-ttu-id="cb791-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb791-169">See Also</span></span>  
 <span data-ttu-id="cb791-170">[在 URL 內傳遞報表參數](pass-a-report-parameter-within-a-url.md) </span><span class="sxs-lookup"><span data-stu-id="cb791-170">[Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md) </span></span>  
 <span data-ttu-id="cb791-171">[URL 存取參數參考](url-access-parameter-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cb791-171">[URL Access Parameter Reference](url-access-parameter-reference.md) </span></span>  
 <span data-ttu-id="cb791-172">[使用 URL 存取整合 Reporting Services](application-integration/integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="cb791-172">[Integrating Reporting Services Using URL Access](application-integration/integrating-reporting-services-using-url-access.md) </span></span>  
 [<span data-ttu-id="cb791-173">尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;</span><span class="sxs-lookup"><span data-stu-id="cb791-173">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
