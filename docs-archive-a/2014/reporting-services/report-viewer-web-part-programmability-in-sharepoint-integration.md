---
title: SharePoint 整合中的報表檢視器網頁組件可程式性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 494ebc3e6668e4d95480019e522caf46b83a6c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703825"
---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a><span data-ttu-id="1f79a-102">SharePoint 整合中的報表檢視器 Web 組件可程式性</span><span class="sxs-lookup"><span data-stu-id="1f79a-102">Report Viewer Web Part Programmability in SharePoint Integration</span></span>
  <span data-ttu-id="1f79a-103">報表檢視器 Web 組件是 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` 伺服器控制項，這個控制項包含一組公用應用程式開發介面 (API)，可讓開發人員建立自訂 SharePoint 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f79a-103">The Report Viewer Web Part is a `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` server control, which contains a set of public application programming interfaces (API) that enables developers to create custom SharePoint applications.</span></span> <span data-ttu-id="1f79a-104">您可以建立自訂 Web 組件，利用 Web 組件連接提供報表路徑和參數給報表檢視器 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-104">You can create custom Web Parts that supply report path and parameters to Report Viewer Web Part using Web Part connections.</span></span> <span data-ttu-id="1f79a-105">您也可以將 Web 組件內嵌在自訂 SharePoint Web 組件頁面中，並使用公用 API 來自訂該組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-105">You can also embed the Web Part in a custom SharePoint Web Part page and customize it using the public API.</span></span>  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a><span data-ttu-id="1f79a-106">使用自訂 Web 組件連接到報表檢視器 Web 組件</span><span class="sxs-lookup"><span data-stu-id="1f79a-106">Connecting to Report Viewer Web Part with Custom Web Parts</span></span>  
 <span data-ttu-id="1f79a-107">報表檢視器 Web 組件是實作 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 或 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 之 SharePoint Web 組件的連接取用者。</span><span class="sxs-lookup"><span data-stu-id="1f79a-107">The Report Viewer Web Part is a connection consumer to SharePoint Web Parts that implement <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> or `T:Microsoft.SharePoint.WebPartPages.IFilterValues`.</span></span> <span data-ttu-id="1f79a-108">如果將 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 網頁組件 (例如**文件**網頁組件) 放在與報表檢視器網頁組件相同的網頁組件頁面上，此網頁組件也可以提供報表路徑給報表檢視器網頁組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-108">An <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part, such as the **Documents** Web Part can supply a report path to a Report Viewer Web Part when placed on the same Web Part page as the Report Viewer Web Part.</span></span> <span data-ttu-id="1f79a-109">同樣地， `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 當與報表檢視器 web 元件放在相同的 Web 元件頁面上時，Web 元件（例如，**文字篩選**或**選擇篩選**）可以提供報表參數給報表檢視器 web 元件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-109">Likewise, an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part, such as the **Text Filter** or the **Choice Filter**, can supply a report parameter to a Report Viewer Web Part when placed on the same Web Part page as the Report Viewer Web Part.</span></span>  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a><span data-ttu-id="1f79a-110">使用 IWebPartRow 實作報表路徑提供者</span><span class="sxs-lookup"><span data-stu-id="1f79a-110">Implementing a Report Path Provider with IWebPartRow</span></span>  
 <span data-ttu-id="1f79a-111">若要透過 Web 組件連接將報表路徑提供給報表檢視器 Web 組件，請執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="1f79a-111">To supply a report path to the Report Viewer Web Part through Web Part connections, do the following:</span></span>  
  
1.  <span data-ttu-id="1f79a-112">建立實作 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 介面的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-112">Create a Web Part that implements the <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> interface.</span></span>  
  
2.  <span data-ttu-id="1f79a-113">將此 Web 組件加入至與報表檢視器 Web 組件相同的 Web 組件頁面上。</span><span class="sxs-lookup"><span data-stu-id="1f79a-113">Add the Web Part to the same Web Part page as the Report Viewer Web Part.</span></span>  
  
3.  <span data-ttu-id="1f79a-114">在 Web 式 Web 組件設計使用者介面上，將您的 Web 組件連接到報表檢視器 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-114">Connect your Web Part to the Report Viewer Web Part in the Web-based Web Part design user interface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f79a-115">您一次只能將一個 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 組件連接到報表檢視器 Web 組件，而且不能同時將 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 組件和 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 組件連接到報表檢視器 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-115">You can only connect one <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part to the Report Viewer Web Part at a time, and you cannot connect both an <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part and an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part at the same time.</span></span>  
  
 <span data-ttu-id="1f79a-116">為了讓 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 組件能夠搭配 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` 正常運作，您必須在 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> 方法中執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1f79a-116">For your <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part to work properly with the `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`, you must do the following in the <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> method:</span></span>  
  
-   <span data-ttu-id="1f79a-117">使用 <xref:System.Data.DataRowView> 物件當做輸入參數來叫用回撥方法。</span><span class="sxs-lookup"><span data-stu-id="1f79a-117">Invoke the callback method with a <xref:System.Data.DataRowView> object as the input parameter.</span></span>  
  
-   <span data-ttu-id="1f79a-118">確定 <xref:System.Data.DataRowView> 物件包含名為 "DocUrl" 的資料行 (其中包含報表路徑)。</span><span class="sxs-lookup"><span data-stu-id="1f79a-118">Make sure that the <xref:System.Data.DataRowView> object contains a column called "DocUrl" that contains the report path.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f79a-119">適用於 [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 的報表檢視器 Web 組件也支援使用 "FileRef" 資料行接收報表路徑。</span><span class="sxs-lookup"><span data-stu-id="1f79a-119">The Report Viewer Web Part in the add-in for [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 also supports receiving the report path using the "FileRef" column.</span></span>  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a><span data-ttu-id="1f79a-120">使用 IFilterValues 實作報表參數提供者</span><span class="sxs-lookup"><span data-stu-id="1f79a-120">Implementing a Report Parameter Provider with IFilterValues</span></span>  
 <span data-ttu-id="1f79a-121">實作 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 的 Web 組件可以提供一個參數值給報表檢視器 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-121">A Web Part that implements `T:Microsoft.SharePoint.WebPartPages.IFilterValues` can provide one parameter value to the Report Viewer Web Part.</span></span> <span data-ttu-id="1f79a-122">傳送給報表檢視器 Web 組件的參數值會受到與報表參數相同的限制，如同報表定義中所指定 (例如資料類型、有效值等等)。</span><span class="sxs-lookup"><span data-stu-id="1f79a-122">The parameter value sent to the Report Viewer Web Part is subject to the same restrictions placed on the report parameter as specified in the report definition, such as data type, valid values, and so on</span></span>  
  
 <span data-ttu-id="1f79a-123">若要將報表參數提供給報表檢視器 Web 組件，請執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="1f79a-123">To supply a report parameter to the Report Viewer Web Part, do the following:</span></span>  
  
1.  <span data-ttu-id="1f79a-124">建立實作 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 介面的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-124">Create a Web Part that implements the `T:Microsoft.SharePoint.WebPartPages.IFilterValues` interface.</span></span>  
  
2.  <span data-ttu-id="1f79a-125">將此 Web 組件加入至與 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` 相同的頁面上。</span><span class="sxs-lookup"><span data-stu-id="1f79a-125">Add the Web Part to the same page as the `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`.</span></span>  
  
3.  <span data-ttu-id="1f79a-126">在 Web 式 Web 組件設計使用者介面上，將您的 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 組件連接到報表檢視器 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-126">Connect your `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part in the Web-based Web Part design user interface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f79a-127">您一次可以將多個 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 組件連接到報表檢視器 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-127">You can connect multiple `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Parts to the Report Viewer Web Part at a time.</span></span> <span data-ttu-id="1f79a-128">不過，您不能同時將 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 組件和 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 組件連接到報表檢視器 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="1f79a-128">However, you cannot connect both an <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part and an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part at the same time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f79a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f79a-129">See Also</span></span>  
 <span data-ttu-id="1f79a-130">[IFilterValues 介面](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1f79a-130">[IFilterValues interface](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)</span></span>  
  
  
