---
title: 在 Web 應用程式中使用 URL 存取 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- links [Reporting Services], URL access
- URL access [Reporting Services], Web applications
- POST requests
- direct addressing [Reporting Services]
- Web applications [Reporting Services]
- hyperlinks [Reporting Services]
ms.assetid: 39e7918c-ad2d-4ca6-b099-2dd4dbdb83dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cd31f76658f8160cbb2a576debc335588f77e72c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584297"
---
# <a name="using-url-access-in-a-web-application"></a><span data-ttu-id="8169e-102">在 Web 應用程式中使用 URL 存取</span><span class="sxs-lookup"><span data-stu-id="8169e-102">Using URL Access in a Web Application</span></span>
  <span data-ttu-id="8169e-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 URL 存取是特別針對可透過網路存取個別報表所設計。</span><span class="sxs-lookup"><span data-stu-id="8169e-103">URL access in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is specifically designed to enable access to individual reports over a network.</span></span> <span data-ttu-id="8169e-104">這種類型的存取最適於將報表檢視與導覽整合到自訂 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8169e-104">This type of access is best for integrating report viewing and navigation into a custom Web application.</span></span> <span data-ttu-id="8169e-105">若要在 Web 應用程式中使用 URL 存取，您可以：</span><span class="sxs-lookup"><span data-stu-id="8169e-105">To use URL access in Web applications, you can:</span></span>  
  
-   <span data-ttu-id="8169e-106">從網站或是入口網站將 URL 定址到特定的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="8169e-106">Address a URL to a specific report server from a Web site or portal.</span></span>  
  
-   <span data-ttu-id="8169e-107">使用表單 POST 方法，並使用表單欄位將查詢字串參數傳遞到報表伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="8169e-107">Use a form POST method and pass query string parameters to a report server URL using form fields.</span></span>  
  
## <a name="url-access-through-direct-addressing"></a><span data-ttu-id="8169e-108">透過直接定址的 URL 存取</span><span class="sxs-lookup"><span data-stu-id="8169e-108">URL Access Through Direct Addressing</span></span>  
 <span data-ttu-id="8169e-109">若要使用 URL 來存取報表伺服器或是報表伺服器資料庫項目，請直接在網頁瀏覽器或應用程式中提供 URL 位址。</span><span class="sxs-lookup"><span data-stu-id="8169e-109">To access a report server or report server database item using a URL, simply provide the URL address from within a Web browser or application.</span></span> <span data-ttu-id="8169e-110">您也可以提供參數給 URL，這將可影響正在存取的報表或資源的外觀。</span><span class="sxs-lookup"><span data-stu-id="8169e-110">You can also supply parameters to the URL that can affect the appearance of the report or resource that is being accessed.</span></span> <span data-ttu-id="8169e-111">URL 可以透過網頁瀏覽器的位址列來鎖定報表伺服器，或者 URL 可以是較大的 Web 應用程式或是入口網站一部分之 **IFrame** 的來源。</span><span class="sxs-lookup"><span data-stu-id="8169e-111">A URL can target a report server through the address bar of a Web browser, or a URL can be the source of an **IFrame** that is part of a larger Web application or portal.</span></span> <span data-ttu-id="8169e-112">您可以將超連結包括到入口網站之各個網頁上的報表中，以及鎖定報表的特定框架，或是在處理序中開啟一個新的瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="8169e-112">You can include hyperlinks to reports on various Web pages of your portal, as well as target a specific frame for the report or open a new browser window in the process.</span></span>  
  
 <span data-ttu-id="8169e-113">在下列範例中，超連結會鎖定名為 "main" 的框架，這可能與包含超連結的框架不同。</span><span class="sxs-lookup"><span data-stu-id="8169e-113">In the following example, the hyperlink targets a frame named "main", which might be different from the one that includes the hyperlink.</span></span> <span data-ttu-id="8169e-114">超連結可能是 Web 入口網站的一部分。</span><span class="sxs-lookup"><span data-stu-id="8169e-114">The hyperlink might be part of Web portal.</span></span>  
  
```  
<a href="http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main" target="main" >  
   Click here for the Territory Sales Drilldown sample report  
</a>  
```  
  
 <span data-ttu-id="8169e-115">在上述範例中，會使用 URL 的查詢字串中 "main" 的值來傳遞 **LinkTarget** 裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="8169e-115">In the previous example, the device information setting **LinkTarget** is passed with a value of "main" in the query string of the URL.</span></span> <span data-ttu-id="8169e-116">這可確保在報表中的任何鑽研超連結也鎖定名為 "main" 的框架。</span><span class="sxs-lookup"><span data-stu-id="8169e-116">This ensures that any drillthrough hyperlinks in the report also target the frame named "main".</span></span>  
  
 <span data-ttu-id="8169e-117">如需裝置資訊設定的詳細資訊，請參閱[將裝置資訊設定傳遞至轉譯延伸模組](../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="8169e-117">For more information about device information settings, see [Passing Device Information Settings to Rendering Extensions](../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
 <span data-ttu-id="8169e-118">請注意，許多伺服器與瀏覽器會限制在 URL 中允許的字元數目。</span><span class="sxs-lookup"><span data-stu-id="8169e-118">Note that many servers and browsers limit the number of characters allowed in a URL.</span></span> <span data-ttu-id="8169e-119">在某些情況下，會加諸 256 個字元的限制。</span><span class="sxs-lookup"><span data-stu-id="8169e-119">In some cases, a 256-character limit is imposed.</span></span> <span data-ttu-id="8169e-120">若要解決此限制，您可以使用表單提交來使用 POST 要求。</span><span class="sxs-lookup"><span data-stu-id="8169e-120">To get around this limitation, you can use POST requests using form submission.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8169e-121">Internet Explorer 最大的 URL 長度為 2,083 個字元。</span><span class="sxs-lookup"><span data-stu-id="8169e-121">Internet Explorer has a maximum URL length of 2,083 characters.</span></span> <span data-ttu-id="8169e-122">這個限制適用於 POST 與 GET 要求 URL。</span><span class="sxs-lookup"><span data-stu-id="8169e-122">This limit applies to both POST and GET request URLs.</span></span> <span data-ttu-id="8169e-123">不過，在提交名稱/值組做為表單一部分時，POST 並未受到 URL 大小的限制，因為會在標頭中而不是 URL 中傳輸它們。</span><span class="sxs-lookup"><span data-stu-id="8169e-123">POST, however, is not limited by the size of the URL for submitting name/value pairs as part of a form, because they are transferred in the header and not the URL.</span></span>  
  
## <a name="url-access-through-a-form-post-method"></a><span data-ttu-id="8169e-124">透過表單 POST 方法的 URL 存取</span><span class="sxs-lookup"><span data-stu-id="8169e-124">URL Access Through a Form POST Method</span></span>  
 <span data-ttu-id="8169e-125">當使用者使用 URL 存取從報表伺服器要求資料時，HTTP 要求會使用 GET 方法。</span><span class="sxs-lookup"><span data-stu-id="8169e-125">When a user requests data from a report server using URL access, the HTTP request uses the GET method.</span></span> <span data-ttu-id="8169e-126">這等於 METHOD="GET" 的表單提交。</span><span class="sxs-lookup"><span data-stu-id="8169e-126">This is equivalent to a form submission where METHOD="GET".</span></span> <span data-ttu-id="8169e-127">使用 METHOD="GET" 的 URL 要求或是表單提交受限於伺服器或網頁瀏覽器可以處理的最大字元數目。</span><span class="sxs-lookup"><span data-stu-id="8169e-127">URL requests or form submissions that use METHOD="GET" are limited by the maximum number of characters that a server or Web browser can process.</span></span>  
  
 <span data-ttu-id="8169e-128">透過 POST 要求 (METHOD="POST" 與輸入欄位)，會在標頭中而不是 URL 中傳輸名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="8169e-128">With POST requests (METHOD="POST" and input fields), the name/value pairs are transferred in the header and not the URL.</span></span> <span data-ttu-id="8169e-129">因此，查詢字串的名稱/值組不是 URL 的一部分，因此可讓您提供更長且更複雜的參數清單。</span><span class="sxs-lookup"><span data-stu-id="8169e-129">Therefore, the name/value pairs of the query string are not part of the URL, thus enabling you to provide much longer and more complex parameter lists.</span></span>  
  
 <span data-ttu-id="8169e-130">透過直接存取，使用者可以查看報表伺服器的 URL，而且可以修改查詢字串或是注意特定的 URL 要求與報表伺服器參數以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="8169e-130">Using direct access, a user can see the URL for the report server, and may be able to modify the  query string or note the particular URL request and report server parameters for later use.</span></span>  
  
 <span data-ttu-id="8169e-131">下列範例 HTML 示範表單的使用，您可以透過特定的 URL 來使用目標報表伺服器，並將查詢字串參數以表單的輸入欄位之一部分來傳遞。</span><span class="sxs-lookup"><span data-stu-id="8169e-131">The following sample HTML demonstrates the use of a form that you can use to target a report server with a specific URL and pass query string parameters as part of the form's input fields.</span></span>  
  
```  
<FORM id="frmRender" action="http://server/reportserver?/SampleReports/  
   Territory Sales Drilldown" method="post" target="_self">  
   <INPUT type="hidden" name="rs:Command" value="Render">   
   <INPUT type="hidden" name="rc:LinkTarget" value="main">  
   <INPUT type="hidden" name="rs:Format" value="HTML4.0">  
   <INPUT type="submit" value="Button">  
</FORM>  
```  
  
 <span data-ttu-id="8169e-132">在上述範例中，如果使用者按一下表單上的按鈕，報表伺服器會傳回在目前框架鎖定的 HTML 轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="8169e-132">In the previous example, if a user clicks the button on the form, the report server returns an HTML-rendered report targeted at the current frame.</span></span> <span data-ttu-id="8169e-133">可比較的 URL 存取字串可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="8169e-133">A comparable URL access string might look like the following:</span></span>  
  
```  
http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main&rs:Format=HTML4.0  
```  
  
## <a name="see-also"></a><span data-ttu-id="8169e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8169e-134">See Also</span></span>  
 <span data-ttu-id="8169e-135">[將 Reporting Services 整合至應用程式](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="8169e-135">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="8169e-136">[使用 URL 存取來整合 Reporting Services](integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="8169e-136">[Integrating Reporting Services Using URL Access](integrating-reporting-services-using-url-access.md) </span></span>  
 <span data-ttu-id="8169e-137">[在 Windows 應用程式中使用 URL 存取](integrating-reporting-services-using-url-access-windows-application.md) </span><span class="sxs-lookup"><span data-stu-id="8169e-137">[Using URL Access in a Windows Application](integrating-reporting-services-using-url-access-windows-application.md) </span></span>  
 [<span data-ttu-id="8169e-138">URL 存取 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8169e-138">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
