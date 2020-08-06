---
title: PowerPivot 資料存取 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 83dc82da-91fb-4e47-91a8-0e0db67339b8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8faeec7b2e12871467b93f136360e9a68a0e5acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599198"
---
# <a name="powerpivot-data-access"></a><span data-ttu-id="d25dd-102">PowerPivot 資料存取</span><span class="sxs-lookup"><span data-stu-id="d25dd-102">PowerPivot Data Access</span></span>
  <span data-ttu-id="d25dd-103">本主題描述從發佈到 SharePoint 文件庫的 PowerPivot 活頁簿擷取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="d25dd-103">This topic describes the ways in which data is retrieved from a PowerPivot workbook that is published to a SharePoint library.</span></span>  
  
 <span data-ttu-id="d25dd-104">PowerPivot 資料會儲存在 Excel 活頁簿內。</span><span class="sxs-lookup"><span data-stu-id="d25dd-104">PowerPivot data is stored inside an Excel workbook.</span></span> <span data-ttu-id="d25dd-105">連接字串是 SharePoint 網站上活頁簿的 URL。</span><span class="sxs-lookup"><span data-stu-id="d25dd-105">The connection string is a URL to a workbook on a SharePoint site.</span></span>  
  
 <span data-ttu-id="d25dd-106">PowerPivot 資料最常由包含它的活頁簿所使用 (當做樞紐分析表和樞紐分析圖背後的資料)。</span><span class="sxs-lookup"><span data-stu-id="d25dd-106">PowerPivot data is most often used by the workbook that contains it, as the data behind PivotTables and PivotCharts.</span></span> <span data-ttu-id="d25dd-107">此外，PowerPivot 資料也可當做外部資料來源使用，其中活頁簿、儀表板或報表會連接到 SharePoint 中的個別 Excel (.xlsx) 檔案，並且擷取資料以供後續使用。</span><span class="sxs-lookup"><span data-stu-id="d25dd-107">Alternatively, PowerPivot data can also be used as an external data source, where a workbook, dashboard, or report connects to a separate Excel (.xlsx) file in SharePoint and retrieves the data for subsequent use.</span></span> <span data-ttu-id="d25dd-108">通常使用 PowerPivot 資料的用戶端工具為 Excel、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、其他 Reporting Services 報表和 PerformancePoint。</span><span class="sxs-lookup"><span data-stu-id="d25dd-108">Client tools that typically use PowerPivot data are Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], other Reporting Services reports, and PerformancePoint.</span></span>  
  
 <span data-ttu-id="d25dd-109">PowerPivot 增益集會在桌面上使用 AMO 與 ADOMD.NET 來建立、處理及查詢用戶端工作空間中的 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="d25dd-109">On the desktop, the PowerPivot add-in uses AMO and ADOMD.NET to create, process, and query the PowerPivot data in the client workspace.</span></span>  
  
 <span data-ttu-id="d25dd-110">在 SharePoint 伺服器陣列上，Excel Services 會使用本機 MSOLAP OLE DB 提供者連接到 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="d25dd-110">On a SharePoint farm, Excel Services uses the local MSOLAP OLE DB provider to connect to PowerPivot data.</span></span> <span data-ttu-id="d25dd-111">此提供者會將連接要求傳送到伺服器陣列中的 PowerPivot for SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d25dd-111">The provider sends the connection request to a PowerPivot for SharePoint server in the farm.</span></span> <span data-ttu-id="d25dd-112">該伺服器會載入資料、執行查詢，然後傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="d25dd-112">That server loads the data, runs the query, and returns the result set.</span></span>  
  
##  <a name="querying-powerpivot-data-in-sharepoint"></a><a name="queryproc"></a><span data-ttu-id="d25dd-113">查詢 SharePoint 中的 PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="d25dd-113">Querying PowerPivot Data in SharePoint</span></span>  
 <span data-ttu-id="d25dd-114">當您從 SharePoint 文件庫檢視 PowerPivot 活頁簿時，會在伺服器陣列中的 Analysis Services 伺服器執行個體上，個別偵測、擷取及處理活頁簿內的 PowerPivot 資料，同時 Excel Services 會轉譯展示層。</span><span class="sxs-lookup"><span data-stu-id="d25dd-114">When you view a PowerPivot workbook from a SharePoint library, the PowerPivot data that is inside the workbook is detected, extracted, and processed separately on Analysis Services server instances within the farm, while Excel Services renders the presentation layer.</span></span> <span data-ttu-id="d25dd-115">您可以在瀏覽器視窗或在具有 PowerPivot 增益集的 Excel 2010 桌面應用程式中，檢視已完全處理的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="d25dd-115">You can view the fully-processed workbook in a browser window or in an Excel 2010 desktop application that has the PowerPivot add-in.</span></span>  
  
 <span data-ttu-id="d25dd-116">下圖顯示查詢處理的要求如何透過伺服陣列移動。</span><span class="sxs-lookup"><span data-stu-id="d25dd-116">The following diagram shows how a request for query processing moves through the farm.</span></span> <span data-ttu-id="d25dd-117">因為 PowerPivot 資料是 Excel 2010 活頁簿的一部分，所以對於查詢處理的要求會在使用者從 SharePoint 文件庫開啟 Excel 活頁簿時發生，並與包含 PowerPivot 資料的樞紐分析表或樞紐分析圖互動。</span><span class="sxs-lookup"><span data-stu-id="d25dd-117">Because PowerPivot data is part of an Excel 2010 workbook, a request for query processing occurs when a user opens an Excel workbook from a SharePoint library and interacts with a PivotTable or PivotChart that contains PowerPivot data.</span></span>  
  
 <span data-ttu-id="d25dd-118">![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")</span><span class="sxs-lookup"><span data-stu-id="d25dd-118">![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")</span></span>  
  
 <span data-ttu-id="d25dd-119">Excel Services 及 PowerPivot for SharePoint 元件會處理相同活頁簿 (.xlsx) 檔案的不同部分。</span><span class="sxs-lookup"><span data-stu-id="d25dd-119">Excel Services and PowerPivot for SharePoint components process different parts of the same workbook (.xlsx) file.</span></span> <span data-ttu-id="d25dd-120">Excel Services 會偵測到 PowerPivot 資料，並要求從伺服陣列中的 PowerPivot 伺服器進行處理。</span><span class="sxs-lookup"><span data-stu-id="d25dd-120">Excel Services detects PowerPivot data and requests processing from a PowerPivot server in the farm.</span></span> <span data-ttu-id="d25dd-121">PowerPivot 伺服器會將要求配置到 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 執行個體，這將會從內容文件庫的活頁簿中擷取資料並載入資料。</span><span class="sxs-lookup"><span data-stu-id="d25dd-121">The PowerPivot server allocates the request to an [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance, which extracts the data from the workbook in the content library and loads the data.</span></span> <span data-ttu-id="d25dd-122">儲存在記憶體中的資料會合併至轉譯的活頁簿，並傳回給 Excel Web Access，以便在瀏覽器視窗中顯示。</span><span class="sxs-lookup"><span data-stu-id="d25dd-122">Data that is stored in memory is merged back into the rendered workbook, and passed back to Excel Web Access for presentation in a browser window.</span></span>  
  
 <span data-ttu-id="d25dd-123">並非在 PowerPivot 活頁簿中的所有資料都是由 PowerPivot for SharePoint 進行處理。</span><span class="sxs-lookup"><span data-stu-id="d25dd-123">Not all data in a PowerPivot workbook is handled by PowerPivot for SharePoint.</span></span> <span data-ttu-id="d25dd-124">Excel Services 會處理工作表中的資料表與資料格資料。</span><span class="sxs-lookup"><span data-stu-id="d25dd-124">Excel Services processes tables and cell data in a worksheet.</span></span> <span data-ttu-id="d25dd-125">只有與 PowerPivot 資料相反的樞紐分析表、樞紐分析圖和交叉分析篩選器，是由 PowerPivot for SharePoint 所處理。</span><span class="sxs-lookup"><span data-stu-id="d25dd-125">Only PivotTables, PivotCharts, and Slicers that go against PowerPivot data are handled by the PowerPivot for SharePoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d25dd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d25dd-126">See Also</span></span>  
 <span data-ttu-id="d25dd-127">[連接到 Analysis Services](../instances/connect-to-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d25dd-127">[Connect to Analysis Services](../instances/connect-to-analysis-services.md) </span></span>  
 [<span data-ttu-id="d25dd-128">表格式模型資料存取</span><span class="sxs-lookup"><span data-stu-id="d25dd-128">Tabular Model Data Access</span></span>](../tabular-models/tabular-model-data-access.md)  
  
  
