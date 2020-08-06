---
title: '[在 Excel 中進行分析] (瀏覽器索引標籤、Cube 設計師)  (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.datapane.f1
- sql12.asvs.ssms.analyzeinexcel.f1
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9fa27ae291d40b7f5637e3968438fcaec1de03d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593188"
---
# <a name="analyze-in-excel-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="68e7c-102">在 Excel 中進行分析 (瀏覽器索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="68e7c-102">Analyze in Excel (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="68e7c-103">**[在 Excel 中進行分析]** 提供 Cube 開發人員一種方式，可快速檢閱使用者所看到的專案外觀。</span><span class="sxs-lookup"><span data-stu-id="68e7c-103">**Analyze in Excel** provides the cube developer with a way to quickly review how a project would look to the end user.</span></span> <span data-ttu-id="68e7c-104">**[在 Excel 中進行分析]** 功能可開啟 Microsoft Excel、建立工作空間資料庫的資料來源連接，以及自動將樞紐分析表加入工作表。</span><span class="sxs-lookup"><span data-stu-id="68e7c-104">The **Analyze in Excel** feature opens Microsoft Excel, creates a data source connection to the workspace database, and automatically adds a PivotTable to the worksheet.</span></span> <span data-ttu-id="68e7c-105">此功能取代舊版 [瀏覽器] 索引標籤中提供內嵌樞紐分析表的 Office Web 元件。</span><span class="sxs-lookup"><span data-stu-id="68e7c-105">This feature replaces the Office Web Control that provided an embedded PivotTable in the Browser tab in previous releases.</span></span>  
  
 <span data-ttu-id="68e7c-106">**若要檢視 Cube 資料：**</span><span class="sxs-lookup"><span data-stu-id="68e7c-106">**To view cube data:**</span></span>  
  
1.  <span data-ttu-id="68e7c-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]的方案總管中，按兩下 Cube，在 Cube 設計師中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="68e7c-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in Solution Explorer, double-click a cube to open it in Cube Designer.</span></span>  
  
2.  <span data-ttu-id="68e7c-108">按一下 **[瀏覽器]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="68e7c-108">Click the **Browser** tab.</span></span>  
  
3.  <span data-ttu-id="68e7c-109">按一下 **[重新連接]** 驗證連接。</span><span class="sxs-lookup"><span data-stu-id="68e7c-109">Click **Reconnect** to validate the connection.</span></span>  
  
4.  <span data-ttu-id="68e7c-110">按一下功能表列上的 Excel 圖示。</span><span class="sxs-lookup"><span data-stu-id="68e7c-110">Click the Excel icon in the menu bar.</span></span>  
  
5.  <span data-ttu-id="68e7c-111">當系統要求您啟用資料連接時，按一下 **[啟用]**。</span><span class="sxs-lookup"><span data-stu-id="68e7c-111">When asked to enable data connections, click **Enable**.</span></span> <span data-ttu-id="68e7c-112">Excel 會使用目前的資料連接來開啟，並將樞紐分析表加入工作表中，讓您可以開始瀏覽資料。</span><span class="sxs-lookup"><span data-stu-id="68e7c-112">Excel opens using the current data connection, adding a PivotTable to the worksheet so that you can begin browsing your data.</span></span>  
  
 <span data-ttu-id="68e7c-113">您現在可透過將事實資料表中的量值拖曳至 [值] 區域，並將維度屬性拖曳至 [資料列] 和 [資料行] 區域，以互動方式建立樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="68e7c-113">You can now build a PivotTable interactively by dragging measures from the fact table to the Values area, and dimension attributes to the Row and Column areas.</span></span> <span data-ttu-id="68e7c-114">如果您有階層，可將它們加入至 [資料列] 或 [資料行] 區域。</span><span class="sxs-lookup"><span data-stu-id="68e7c-114">If you have hierarchies, add them to Rows or Column areas.</span></span> <span data-ttu-id="68e7c-115">您可以積存或向下鑽研階層，瀏覽不同層級的事實資料。</span><span class="sxs-lookup"><span data-stu-id="68e7c-115">You can roll up or drill down the hierarchy to browse fact data at different levels.</span></span>  
  
 <span data-ttu-id="68e7c-116">物件及資料是在有效使用者或角色及檢視方塊的內容中進行檢視。</span><span class="sxs-lookup"><span data-stu-id="68e7c-116">Objects and data are viewed within the context of the effective user or role and perspective.</span></span> <span data-ttu-id="68e7c-117">使用 Excel 執行查詢時，目前使用者的認證 (而非在 **[模擬資訊]** 頁面中指定的認證) 會用來連接資料來源。</span><span class="sxs-lookup"><span data-stu-id="68e7c-117">When using Excel, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68e7c-118">若要使用 [在 Excel 中進行分析] 功能，您必須在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]所在電腦上安裝 Excel。</span><span class="sxs-lookup"><span data-stu-id="68e7c-118">To use the Analyze in Excel feature, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="68e7c-119">如果未將 Excel 安裝在相同的電腦上，您可以在其他電腦上使用 Excel，然後連接至 Cube 做為資料來源。</span><span class="sxs-lookup"><span data-stu-id="68e7c-119">If Excel is not installed on the same computer, you can use Excel on another computer and connect to the cube as a data source.</span></span> <span data-ttu-id="68e7c-120">然後即可手動將樞紐分析表加入工作表。</span><span class="sxs-lookup"><span data-stu-id="68e7c-120">You can then manually add a PivotTable to the worksheet.</span></span> <span data-ttu-id="68e7c-121">模型物件 (資料表、資料行、量值及 KPI) 會包含在樞紐分析表欄位清單中當做欄位。</span><span class="sxs-lookup"><span data-stu-id="68e7c-121">Model objects (tables, columns, measures, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
 <span data-ttu-id="68e7c-122">如需有關 **[在 Excel 中進行分析]** 功能的詳細資訊，請參閱以下資源：</span><span class="sxs-lookup"><span data-stu-id="68e7c-122">For more information about the **Analyze in Excel** feature, see these resources:</span></span>  
  
 [<span data-ttu-id="68e7c-123">在 Excel 中進行分析 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="68e7c-123">Analyze in Excel &#40;SSAS Tabular&#41;</span></span>](tabular-models/analyze-in-excel-ssas-tabular.md)  
  
 [<span data-ttu-id="68e7c-124">在 Excel 中分析表格式模型 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="68e7c-124">Analyze a Tabular Model in Excel &#40;SSAS Tabular&#41;</span></span>](tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)  
  
 [<span data-ttu-id="68e7c-125">瀏覽 Cube 中的資料和中繼資料</span><span class="sxs-lookup"><span data-stu-id="68e7c-125">Browse data and metadata in Cube</span></span>](multidimensional-models/browse-data-and-metadata-in-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="68e7c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68e7c-126">See Also</span></span>  
 <span data-ttu-id="68e7c-127">[瀏覽器 &#40;Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="68e7c-127">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="68e7c-128">[工具列 &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="68e7c-128">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="68e7c-129">[中繼資料 &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="68e7c-129">[Metadata &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="68e7c-130">查詢和篩選 &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="68e7c-130">Query and Filter &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
