---
title: 將裝置資訊設定傳遞至轉譯延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea50de3955ab152cbd92d5fd50ef8b2281a67eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688533"
---
# <a name="passing-device-information-settings-to-rendering-extensions"></a><span data-ttu-id="aa40a-102">將裝置資訊設定傳遞至轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="aa40a-102">Passing Device Information Settings to Rendering Extensions</span></span>
  <span data-ttu-id="aa40a-103">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]中，裝置資訊設定會用於將轉譯參數傳遞給轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="aa40a-103">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], device information settings are used to pass rendering parameters to a rendering extension.</span></span> <span data-ttu-id="aa40a-104">Report Server Web 服務中的設定會當做 **DeviceInfo** XML 元素傳遞，並由報表伺服器進行處理。</span><span class="sxs-lookup"><span data-stu-id="aa40a-104">Settings in the Report Server Web service are passed as a **DeviceInfo** XML element and processed by the report server.</span></span> <span data-ttu-id="aa40a-105">因為裝置資訊設定具有預設值，所以這些值被視為轉譯程序中的選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="aa40a-105">Because device information settings have default values, they are considered optional arguments in the rendering process.</span></span> <span data-ttu-id="aa40a-106">不過，您可以使用裝置資訊設定來自訂轉譯，並覆寫伺服器所套用的預設值。</span><span class="sxs-lookup"><span data-stu-id="aa40a-106">However, you can use device information settings to customize rendering and to override the default values that are supplied by the server.</span></span>  
  
 <span data-ttu-id="aa40a-107">您可以用多種方法來指定裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="aa40a-107">You can specify device information settings in a variety of ways.</span></span> <span data-ttu-id="aa40a-108">您可以用程式設計的方式來使用 Render 方法。</span><span class="sxs-lookup"><span data-stu-id="aa40a-108">Programmatically, you can use the Render method.</span></span> <span data-ttu-id="aa40a-109">如果要透過報表的 URL 存取報表，可以將裝置資訊指定為 URL 參數。</span><span class="sxs-lookup"><span data-stu-id="aa40a-109">If you are accessing a report through its URL, you can specify device information as URL parameters.</span></span> <span data-ttu-id="aa40a-110">也可以在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 組態檔中編輯裝置資訊設定，以指定全域的轉譯參數。</span><span class="sxs-lookup"><span data-stu-id="aa40a-110">You can also edit the device information settings in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files to specify rendering parameters globally.</span></span> <span data-ttu-id="aa40a-111">如需全域指定轉譯參數的詳細資訊，請參閱[在 RSReportServer.Config 中自訂轉譯延伸模組參數](../../customize-rendering-extension-parameters-in-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="aa40a-111">For more information about specifying rendering parameters globally, see [Customize Rendering Extension Parameters in RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md).</span></span>  
  
## <a name="passing-device-information-using-the-render-method"></a><span data-ttu-id="aa40a-112">使用轉譯方法傳遞裝置資訊</span><span class="sxs-lookup"><span data-stu-id="aa40a-112">Passing Device Information Using the Render Method</span></span>  
 <span data-ttu-id="aa40a-113">若要將裝置資訊設定傳遞至轉譯延伸模組，請使用 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="aa40a-113">To pass device information settings to a rendering extension, use the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method.</span></span> <span data-ttu-id="aa40a-114">例如，下列的 XML 字串可以傳遞至 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法，以在轉譯為 HTML 時建立 HTML 片段。</span><span class="sxs-lookup"><span data-stu-id="aa40a-114">For example, the following XML string can be passed to the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method to create an HTML fragment when rendering to HTML.</span></span>  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 <span data-ttu-id="aa40a-115">當報表轉譯為 HTML 片段時，報表的內容會包含在 TABLE 元素內，而不會使用 HTML 或 BODY 元素。</span><span class="sxs-lookup"><span data-stu-id="aa40a-115">When a report is rendered as an HTML fragment, the content of the report is contained within a TABLE element without the use of an HTML or BODY element.</span></span> <span data-ttu-id="aa40a-116">您可以使用 HTML 片段來將報表整合到現有的 HTML 文件中。</span><span class="sxs-lookup"><span data-stu-id="aa40a-116">You can use the HTML fragment to incorporate the report into an existing HTML document.</span></span> <span data-ttu-id="aa40a-117">如需 HTML 輸出之裝置資訊設定的詳細資訊，請參閱 [HTML 裝置資訊設定](../../html-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="aa40a-117">For more information about device information settings for HTML output, see [HTML Device Information Settings](../../html-device-information-settings.md).</span></span>  
  
## <a name="passing-device-information-using-url-access"></a><span data-ttu-id="aa40a-118">使用 URL 存取傳遞裝置資訊</span><span class="sxs-lookup"><span data-stu-id="aa40a-118">Passing Device Information Using URL Access</span></span>  
 <span data-ttu-id="aa40a-119">您也可以透過 URL 存取來傳遞裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="aa40a-119">You can also pass device information settings through URL access.</span></span> <span data-ttu-id="aa40a-120">裝置資訊設定會當做 URL 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="aa40a-120">Device information settings are passed as URL parameters.</span></span> <span data-ttu-id="aa40a-121">下列的 URL 存取字串可以傳遞至報表伺服器以產生轉譯的報表 (沒有 HTML 檢視器工具列)。</span><span class="sxs-lookup"><span data-stu-id="aa40a-121">The following URL access string can be passed to the report server to generate a rendered report without the HTML viewer toolbar.</span></span>  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 <span data-ttu-id="aa40a-122">如需詳細資訊，請參閱[在 URL 中指定裝置資訊設定](../../specify-device-information-settings-in-a-url.md)。</span><span class="sxs-lookup"><span data-stu-id="aa40a-122">For more information, see [Specify Device Information Settings in a URL](../../specify-device-information-settings-in-a-url.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa40a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa40a-123">See Also</span></span>  
 <span data-ttu-id="aa40a-124">[轉譯延伸模組的裝置資訊設定 &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="aa40a-124">[Device Information Settings for Rendering Extensions &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md) </span></span>  
 <span data-ttu-id="aa40a-125">[在 RSReportServer.Config中自訂轉譯延伸模組參數](../../customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="aa40a-125">[Customize Rendering Extension Parameters in RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="aa40a-126">使用 Web 服務和 .NET Framework 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="aa40a-126">Building Applications Using the Web Service and the .NET Framework</span></span>](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
