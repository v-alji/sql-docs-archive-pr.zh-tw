---
title: 使用 URL 存取整合 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- URL access [Reporting Services], about URL access
- integrating reports [Reporting Services]
ms.assetid: f1014f7d-fafa-4aa8-8bd2-5bdba835d9b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fedf4ce3011d9caae9d673acf354265537115057
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703957"
---
# <a name="integrating-reporting-services-using-url-access"></a><span data-ttu-id="40de7-102">使用 URL 存取整合 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="40de7-102">Integrating Reporting Services Using URL Access</span></span>
  <span data-ttu-id="40de7-103">使用 URL 存取，即可透過報表伺服器 URL 來存取報表。</span><span class="sxs-lookup"><span data-stu-id="40de7-103">With URL access, you access reports through a report server URL.</span></span> <span data-ttu-id="40de7-104">URL 要求可讓您存取特定的報表伺服器，以及在報表伺服器資料庫中的報表、資源和其他項目。</span><span class="sxs-lookup"><span data-stu-id="40de7-104">A URL request enables you to access a specific report server as well as the reports, resources, and other items in the report server database.</span></span> <span data-ttu-id="40de7-105">您也可以自訂使用者的報表檢視和導覽經驗。</span><span class="sxs-lookup"><span data-stu-id="40de7-105">You can also customize the report viewing and navigation experience for your users.</span></span> <span data-ttu-id="40de7-106">URL 的查詢字串包含裝置資訊設定，以及以報表和所選轉譯輸出為目標的報表參數。</span><span class="sxs-lookup"><span data-stu-id="40de7-106">The query string of the URL contains device information settings, as well as report parameters targeted at your report and the chosen rendering output.</span></span> <span data-ttu-id="40de7-107">報表伺服器處理 URL 要求的方法須視透過 URL 存取的參數、參數前置詞以及項目類型而定。</span><span class="sxs-lookup"><span data-stu-id="40de7-107">The way the report server handles URL requests depends on the parameters, parameter prefixes, and type of item that you are accessing through the URL.</span></span>  
  
 <span data-ttu-id="40de7-108">您可以使用 URL 存取，將超連結內嵌到您開發的應用程式中之報表和其他報表伺服器項目，不論是在 Windows 或是 Web 環境中。</span><span class="sxs-lookup"><span data-stu-id="40de7-108">You can use URL access to embed hyperlinks to reports and other report server items in the applications that you develop, whether in a Windows or Web environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40de7-109">本章節中的主題提供整合的一些基本想法。</span><span class="sxs-lookup"><span data-stu-id="40de7-109">The topics in the section provide you with some basic ideas for integration.</span></span> <span data-ttu-id="40de7-110">您可以使用此資訊開始設計和開發自己的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合案例。</span><span class="sxs-lookup"><span data-stu-id="40de7-110">You can use the information to begin to design and develop your own [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] integration scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40de7-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="40de7-111">In This Section</span></span>  
 [<span data-ttu-id="40de7-112">在 Web 應用程式中使用 URL 存取</span><span class="sxs-lookup"><span data-stu-id="40de7-112">Using URL Access in a Web Application</span></span>](integrating-reporting-services-using-url-access-web-application.md)  
 <span data-ttu-id="40de7-113">描述如何使用 URL 存取將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合到 Web 環境。</span><span class="sxs-lookup"><span data-stu-id="40de7-113">Describes how to use URL access to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Web environment.</span></span>  
  
 [<span data-ttu-id="40de7-114">在 Windows 應用程式中使用 URL 存取</span><span class="sxs-lookup"><span data-stu-id="40de7-114">Using URL Access in a Windows Application</span></span>](integrating-reporting-services-using-url-access-windows-application.md)  
 <span data-ttu-id="40de7-115">描述如何使用 URL 存取將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 環境。</span><span class="sxs-lookup"><span data-stu-id="40de7-115">Describes how to use URL access to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40de7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40de7-116">See Also</span></span>  
 <span data-ttu-id="40de7-117">[將 Reporting Services 整合至應用程式](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="40de7-117">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="40de7-118">URL 存取 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="40de7-118">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
