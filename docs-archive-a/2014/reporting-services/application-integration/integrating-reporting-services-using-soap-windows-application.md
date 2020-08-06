---
title: 在 Windows 應用程式中使用 SOAP API | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- Windows applications [Reporting Services]
- Windows Forms [Reporting Services]
- SOAP [Reporting Services], Windows applications
ms.assetid: e4804792-20cd-4df2-9257-fb958ff447b4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 115ce02da69a8adb2c7a3de4175e528f281eb2b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584302"
---
# <a name="using-the-soap-api-in-a-windows-application"></a><span data-ttu-id="cec96-102">在 Windows 應用程式中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="cec96-102">Using the SOAP API in a Windows Application</span></span>
  <span data-ttu-id="cec96-103">您可以透過 Reporting Services SOAP API 存取報表伺服器的完整功能。</span><span class="sxs-lookup"><span data-stu-id="cec96-103">You can access the full functionality of the report server through the Reporting Services SOAP API.</span></span> <span data-ttu-id="cec96-104">SOAP API 是一種 Web 服務，因此可以輕易地存取，以提供企業報表功能給自訂商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="cec96-104">The SOAP API is a Web service and, as such, can be easily accessed to provide enterprise reporting features to your custom business applications.</span></span> <span data-ttu-id="cec96-105">您只要撰寫呼叫服務的程式碼，即可在 Windows 應用程式中存取 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="cec96-105">You can access the Web service in a Windows application simply by writing code that makes calls to the service.</span></span> <span data-ttu-id="cec96-106">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ，您可以產生 proxy 類別，以公開 Web 服務的屬性和方法，並可讓您使用熟悉的基礎結構和工具，建立以技術為基礎的商務應用程式 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cec96-106">Using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can generate a proxy class that exposes the properties and methods of the Web service and enables you to use a familiar infrastructure and tools to build business applications built on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technology.</span></span>  
  
## <a name="integrating-report-management-functionality-using-windows-forms"></a><span data-ttu-id="cec96-107">使用 Windows Form 整合報表管理功能</span><span class="sxs-lookup"><span data-stu-id="cec96-107">Integrating Report Management Functionality Using Windows Forms</span></span>  
 <span data-ttu-id="cec96-108">與 URL 存取不同的是，SOAP API 會公開一組透過報表伺服器取得的完整管理功能。</span><span class="sxs-lookup"><span data-stu-id="cec96-108">Unlike URL access, the SOAP API exposes the complete set of management functions that are available through the report server.</span></span> <span data-ttu-id="cec96-109">這表示報表管理員的整個系統管理功能，是透過 SOAP 提供給開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="cec96-109">This means that the entire administrative functionality of Report Manager is available to developers through SOAP.</span></span> <span data-ttu-id="cec96-110">因此，您可以使用 Windows Form 開發完整的管理工具。</span><span class="sxs-lookup"><span data-stu-id="cec96-110">As such, you can develop a complete management and administration tool using Windows Forms.</span></span> <span data-ttu-id="cec96-111">例如，在 Windows 應用程式中，您可以讓使用者擷取報表伺服器命名空間的內容。</span><span class="sxs-lookup"><span data-stu-id="cec96-111">For example, in your Windows application, you might want to enable your users to retrieve the contents of the report server namespace.</span></span> <span data-ttu-id="cec96-112">若要這樣做，您可以使用 Web 服務的 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 方法，列出報表伺服器資料庫中的所有項目，然後使用 Listview、Treeview 或 Combobox 控制項來對使用者顯示這些項目。</span><span class="sxs-lookup"><span data-stu-id="cec96-112">To do this, you could use the Web service <xref:ReportService2010.ReportingService2010.ListChildren%2A> method to list all the items in the report server database and then use a Listview, Treeview, or Combobox control to display those items to your users.</span></span> <span data-ttu-id="cec96-113">下列 Web 服務程式碼可用於當使用者按一下表單上的按鈕時，擷取使用者的 [我的報表] 資料夾中可用報表的目前清單：</span><span class="sxs-lookup"><span data-stu-id="cec96-113">The following Web service code might be used to retrieve the current list of available reports in a user's My Reports folder when a user clicks a button on a form:</span></span>  
  
```vb  
' Button click event that retrieves a list of reports from  
' the My Reports folder and displays them in a combo box  
Private Sub listReportsButton_Click(sender As Object, e As System.EventArgs)  
   ' Create a new Web service object and set credentials  
   ' to Windows Authentication  
   Dim rs As New ReportingService2010()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return the list of items in My Reports  
   Dim items As CatalogItem() = rs.ListChildren("/Adventureworks 2008 Sample Reports", False)  
  
   Dim ci As CatalogItem  
   For Each ci In  items  
      ' If the item is a report, add it to   
      ' a combo box  
      If ci.TypeName = "Report" Then  
         catalogComboBox.Items.Add(ci.Name)  
      End If  
   Next ci  
End Sub 'listReportsButton_Click  
```  
  
```csharp  
// Button click event that retrieves a list of reports from  
// the My Reports folder and displays them in a combo box  
private void listReportsButton_Click(object sender, System.EventArgs e)  
{  
   // Create a new Web service object and set credentials  
   // to Windows Authentication  
   ReportingService2010 rs = new ReportingService2010();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return the list of items in My Reports  
   CatalogItem[] items = rs.ListChildren("/Adventureworks 2008 Sample Reports", false);  
  
   foreach (CatalogItem ci in items)  
   {  
      // If the item is a report, add it to   
      // a combo box  
      if (ci.TypeName == "Report")  
         catalogComboBox.Items.Add(ci.Name);  
   }  
}  
```  
  
 <span data-ttu-id="cec96-114">從這裡，您可以讓使用者從下拉式方塊選取報表，並使用網頁瀏覽器控制項或是影像控制項來預覽表單上的報表。</span><span class="sxs-lookup"><span data-stu-id="cec96-114">From there, you might enable users to select the report from the Combo box and preview the report on the form either using a Web browser control or an image control.</span></span>  
  
## <a name="enabling-report-viewing-and-navigation-using-windows-forms"></a><span data-ttu-id="cec96-115">使用 Windows Form 啟用報表檢視與導覽</span><span class="sxs-lookup"><span data-stu-id="cec96-115">Enabling Report Viewing and Navigation Using Windows Forms</span></span>  
 <span data-ttu-id="cec96-116">將報表整合到 Windows Form 應用程式有兩種方法。</span><span class="sxs-lookup"><span data-stu-id="cec96-116">There are two methods available for integrating reports into your Windows Forms applications.</span></span>  
  
 <span data-ttu-id="cec96-117">您可以使用 SOAP API 將報表轉譯成任何使用 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法的支援轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="cec96-117">You can use the SOAP API to render reports to any of the supported rendering formats using the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method.</span></span> <span data-ttu-id="cec96-118">透過 SOAP 啟用報表檢視與導覽有些輕微的缺點：</span><span class="sxs-lookup"><span data-stu-id="cec96-118">There are slight disadvantages to enabling report viewing and navigation through SOAP:</span></span>  
  
-   <span data-ttu-id="cec96-119">您無法透過 URL 存取利用 HTML 檢視器隨附的報表工具列之內建功能。</span><span class="sxs-lookup"><span data-stu-id="cec96-119">You cannot take advantage of the built-in functionality of the report toolbar that is included with the HTML Viewer through URL access.</span></span>  
  
-   <span data-ttu-id="cec96-120">如果您轉譯為 HTML，必須使用 <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> 方法，將任何影像或是資源個別轉譯為其他的資料流。</span><span class="sxs-lookup"><span data-stu-id="cec96-120">If you render to HTML, you must separately render any images or resources as additional streams using the <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> method.</span></span>  
  
-   <span data-ttu-id="cec96-121">比起 SOAP API，使用 URL 存取來轉譯報表具有些許效能優點。</span><span class="sxs-lookup"><span data-stu-id="cec96-121">There is a slight performance advantage to rendering reports using URL access over using the SOAP API.</span></span>  
  
 <span data-ttu-id="cec96-122">不過，您可以用程式設計方式使用 SOAP API 的 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法來轉譯報表，並將它們儲存為各個輸出格式。</span><span class="sxs-lookup"><span data-stu-id="cec96-122">However, the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method of the SOAP API can be used to render reports and save them to various output formats programmatically.</span></span> <span data-ttu-id="cec96-123">這個優點勝過需要使用者互動的 URL 存取。</span><span class="sxs-lookup"><span data-stu-id="cec96-123">This is an advantage over URL access, which requires user interaction.</span></span> <span data-ttu-id="cec96-124">當您使用 SOAP API <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法轉譯報表時，可以轉譯為任何支援的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="cec96-124">When you render a report using the SOAP API <xref:ReportExecution2005.ReportExecutionService.Render%2A> method, you can render to any of the supported output formats.</span></span>  
  
 <span data-ttu-id="cec96-125">您也可以使用隨附的免費可散發 ReportViewer 控制項 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cec96-125">You can also use the freely distributable ReportViewer controls that are included with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].</span></span> <span data-ttu-id="cec96-126">ReportViewer 控制項可輕鬆地將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能內嵌至自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="cec96-126">The ReportViewer controls make it easy to embed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] functionality into custom applications.</span></span> <span data-ttu-id="cec96-127">ReportViewer 控制項主要是供開發人員使用，他們想要提供預先設計、完整撰寫的報表作為應用程式功能集的一部份 (例如，網站管理應用程式可能包含在公司網站上顯示點選流向分析的報表)。</span><span class="sxs-lookup"><span data-stu-id="cec96-127">The ReportViewer controls are intended for developers who want to provide predesigned, fully authored reports as part of an application feature set (for example, a Web site management application might include reports that show click-stream analysis on company Web sites).</span></span> <span data-ttu-id="cec96-128">將控制項內嵌在應用程式中，是將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 伺服器元件包含在應用程式部署中的簡化替代方案。</span><span class="sxs-lookup"><span data-stu-id="cec96-128">Embedding the controls in an application provides a streamlined alternative to including the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server components in your application deployment.</span></span> <span data-ttu-id="cec96-129">控制項雖然提供報表功能，但沒有您在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中所看到的其他報表撰寫、發行或散發和傳遞支援。</span><span class="sxs-lookup"><span data-stu-id="cec96-129">The controls provide report functionality, but without the additional report authoring, publication, or distribution and delivery support that you find in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="cec96-130">ReportViewer 控制項有兩個版本，一個用於豐富的 Windows 用戶端應用程式，一個用於 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cec96-130">There are two versions of the ReportViewer controls, one for rich Windows client applications and one for [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications.</span></span> <span data-ttu-id="cec96-131">控制項同時支援本機處理和遠端處理模式。</span><span class="sxs-lookup"><span data-stu-id="cec96-131">The controls support both local processing and remote processing modes.</span></span> <span data-ttu-id="cec96-132">在本機處理模式中，應用程式提供報表定義和資料集以及觸發程序報表處理。</span><span class="sxs-lookup"><span data-stu-id="cec96-132">In local processing mode, your application provides the report definition and datasets and triggers report processing.</span></span> <span data-ttu-id="cec96-133">在遠端處理模式中，資料擷取和報表處理是在報表伺服器上進行，而控制項則是用於顯示和報表導覽。</span><span class="sxs-lookup"><span data-stu-id="cec96-133">In remote processing mode, data retrieval and report processing happen on the report server and the control is used for display and report navigation.</span></span> <span data-ttu-id="cec96-134">這個模式可讓您建立豐富的應用程式，其範圍從桌上型到企業型都有。</span><span class="sxs-lookup"><span data-stu-id="cec96-134">This model allows you to build rich applications that can be scaled from desktop to the enterprise.</span></span>  
  
 <span data-ttu-id="cec96-135">ReportViewer 控制項的相關資訊記載於 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 線上說明中。</span><span class="sxs-lookup"><span data-stu-id="cec96-135">ReportViewer controls are documented in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] online Help.</span></span> <span data-ttu-id="cec96-136">如需詳細資訊，請參閱 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 產品文件集。</span><span class="sxs-lookup"><span data-stu-id="cec96-136">For more information, see the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] product documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec96-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cec96-137">See Also</span></span>  
 <span data-ttu-id="cec96-138">[使用 Web 服務和 .NET Framework 建置應用程式](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="cec96-138">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="cec96-139">[將 Reporting Services 整合至應用程式](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="cec96-139">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="cec96-140">在 Web 應用程式中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="cec96-140">Using the SOAP API in a Web Application</span></span>](integrating-reporting-services-using-soap-web-application.md)  
  
  
