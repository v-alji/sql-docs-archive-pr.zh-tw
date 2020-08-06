---
title: 在 Web 應用程式中使用 SOAP API | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e228f01915df633f50b23bf93e892446863c28ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687550"
---
# <a name="using-the-soap-api-in-a-web-application"></a><span data-ttu-id="e065f-102">在 Web 應用程式中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="e065f-102">Using the SOAP API in a Web Application</span></span>
  <span data-ttu-id="e065f-103">您可以透過 Reporting Services SOAP API 存取報表伺服器的完整功能。</span><span class="sxs-lookup"><span data-stu-id="e065f-103">You can access the full functionality of the report server through the Reporting Services SOAP API.</span></span> <span data-ttu-id="e065f-104">因為它是一種 Web 服務，所以可以輕易地存取 SOAP API，以提供企業報表功能給自訂商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="e065f-104">Because it's a Web service, the SOAP API can be easily accessed to provide enterprise reporting features to your custom business applications.</span></span> <span data-ttu-id="e065f-105">您可以從 Web 應用程式存取報表伺服器 Web 服務，這與從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 應用程式存取 SOAP API 非常類似。</span><span class="sxs-lookup"><span data-stu-id="e065f-105">You access the Report Server Web service from a Web application in much the same way that you access the SOAP API from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application.</span></span> <span data-ttu-id="e065f-106">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ，您可以產生 proxy 類別，以公開報表伺服器 Web 服務的屬性和方法，並可讓您使用熟悉的基礎結構和工具來建立技術上的商務應用程式 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e065f-106">Using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can generate a proxy class that exposes the properties and methods of the Report Server Web service and enables you to use a familiar infrastructure and tools to build business applications on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technology.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e065f-107">報表管理功能可以從 Web 應用程式存取，就和從 Windows 應用程式存取一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="e065f-107">report management functionality is just as easily accessed from a Web application as from a Windows application.</span></span> <span data-ttu-id="e065f-108">從 Web 應用程式，您可以從報表伺服器資料庫新增和移除項目、設定項目安全性、修改報表伺服器資料庫項目、管理排程和傳遞等等。</span><span class="sxs-lookup"><span data-stu-id="e065f-108">From a Web application, you can add and remove items from the report server database, set item security, modify report server database items, manage scheduling and delivery, and more.</span></span>  
  
## <a name="enabling-impersonation"></a><span data-ttu-id="e065f-109">啟用模擬</span><span class="sxs-lookup"><span data-stu-id="e065f-109">Enabling Impersonation</span></span>  
 <span data-ttu-id="e065f-110">設定 Web 應用程式的第一個步驟是從 Web 服務用戶端啟用模擬。</span><span class="sxs-lookup"><span data-stu-id="e065f-110">The first step in configuring your Web application is to enable impersonation from the Web service client.</span></span> <span data-ttu-id="e065f-111">透過模擬，[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 應用程式可以使用它們正在操作的用戶端識別來執行。</span><span class="sxs-lookup"><span data-stu-id="e065f-111">With impersonation, [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications can execute with the identity of the client on whose behalf they are operating.</span></span> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="e065f-112">依賴 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 驗證使用者並將已驗證的 Token 傳遞給 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 應用程式，或者如果無法驗證使用者，請傳遞未驗證的 Token。</span><span class="sxs-lookup"><span data-stu-id="e065f-112">relies on [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) to authenticate the user and either pass an authenticated token to the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] application or, if unable to authenticate the user, pass an unauthenticated token.</span></span> <span data-ttu-id="e065f-113">不論是哪一種情況，若有啟用模擬，[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 應用程式不論收到哪一個 Token，都會進行模擬。</span><span class="sxs-lookup"><span data-stu-id="e065f-113">In either case, the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] application impersonates whichever token is received if impersonation is enabled.</span></span> <span data-ttu-id="e065f-114">您可以透過修改用戶端應用程式的 Web.config 檔案，啟用在用戶端上的模擬：</span><span class="sxs-lookup"><span data-stu-id="e065f-114">You can enable impersonation on the client, by modifying the Web.config file of the client application as follows:</span></span>  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e065f-115">預設會啟用模擬。</span><span class="sxs-lookup"><span data-stu-id="e065f-115">Impersonation is disabled by default.</span></span>  
  
 <span data-ttu-id="e065f-116">如需有關模擬的詳細資訊 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] ，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 檔。</span><span class="sxs-lookup"><span data-stu-id="e065f-116">For more information about [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] impersonation, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="managing-the-report-server-using-soap-api"></a><span data-ttu-id="e065f-117">使用 SOAP API 管理報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="e065f-117">Managing the Report Server using SOAP API</span></span>  
 <span data-ttu-id="e065f-118">您也可以使用 Web 應用程式來管理報表伺服器及其內容。</span><span class="sxs-lookup"><span data-stu-id="e065f-118">You can also use your Web application to manage a report server and its contents.</span></span> <span data-ttu-id="e065f-119">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 隨附的報表管理員，是完全使用 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 與 Reporting Services SOAP API 建立的 Web 應用程式範例。</span><span class="sxs-lookup"><span data-stu-id="e065f-119">Report Manager, included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], is an example of a Web application that is completely built using [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] and the Reporting Services SOAP API.</span></span> <span data-ttu-id="e065f-120">您可以將報表管理員的報表管理功能加入自訂 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e065f-120">You can add the report management functionality of Report Manager to your custom Web applications.</span></span> <span data-ttu-id="e065f-121">例如，您可能會想要傳回報表伺服器資料庫中可用報表的清單，並將其顯示在控制項中， [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` 供您的使用者選擇。</span><span class="sxs-lookup"><span data-stu-id="e065f-121">For example, you might want to return a list of available reports in the report server database and display them in a [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` control for your users to choose from.</span></span> <span data-ttu-id="e065f-122">下列程式碼會連接報表伺服器資料庫，並在報表伺服器資料庫中傳回項目的清單。</span><span class="sxs-lookup"><span data-stu-id="e065f-122">The following code connects to the report server database and returns a list of items in the report server database.</span></span> <span data-ttu-id="e065f-123">接著會將可用的報表加入 Listbox 控制項，如此會顯示每個報表的路徑。</span><span class="sxs-lookup"><span data-stu-id="e065f-123">The available reports are then added to a Listbox control, which displays the path of each report.</span></span>  
  
```vb  
Private Sub Page_Load(sender As Object, e As System.EventArgs)  
   ' Create a Web service proxy object and set credentials  
   Dim rs As New ReportingService2005()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return a list of catalog items in the report server database  
   Dim items As CatalogItem() = rs.ListChildren("/", True)  
  
   ' For each report, display the path of the report in a Listbox  
   Dim ci As CatalogItem  
   For Each ci In  items  
      If ci.Type = ItemTypeEnum.Report Then  
         catalogListBox.Items.Add(ci.Path)  
      End If  
   Next ci  
End Sub ' Page_Load   
```  
  
```csharp  
private void Page_Load(object sender, System.EventArgs e)  
{  
   // Create a Web service proxy object and set credentials  
   ReportingService2005 rs = new ReportingService2005();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return a list of catalog items in the report server database  
   CatalogItem[] items = rs.ListChildren("/", true);  
  
   // For each report, display the path of the report in a Listbox  
   foreach(CatalogItem ci in items)  
   {  
      if (ci.Type == ItemTypeEnum.Report)  
         catalogListBox.Items.Add(ci.Path);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e065f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e065f-124">See Also</span></span>  
 <span data-ttu-id="e065f-125">[使用 Web 服務和 .NET Framework 建置應用程式](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="e065f-125">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="e065f-126">[將 Reporting Services 整合至應用程式](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e065f-126">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="e065f-127">[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e065f-127">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="e065f-128">在 Windows 應用程式中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="e065f-128">Using the SOAP API in a Windows Application</span></span>](integrating-reporting-services-using-soap-windows-application.md)  
  
  
