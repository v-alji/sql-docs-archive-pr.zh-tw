---
title: SQL Server 2014 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
author: minewiskan
ms.author: owend
ms.openlocfilehash: c111bdadefeb508897538089ecb9d9a7b583d410
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593189"
---
# <a name="sql-server-2014-analysis-services"></a><span data-ttu-id="de806-102">SQL Server 2014 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="de806-102">SQL Server 2014 Analysis Services</span></span>

  <span data-ttu-id="de806-103">SQL Server 2014 Analysis Services 是在決策支援和商業智慧 (BI) 方案中使用的分析資料引擎，供應商務報表和用戶端應用程式（例如 Excel、Reporting Services 報表和其他協力廠商 BI 工具）的分析資料。</span><span class="sxs-lookup"><span data-stu-id="de806-103">SQL Server 2014 Analysis Services is an analytical data engine used in decision support and business intelligence (BI) solutions, providing the analytical data for business reports and client applications such as Excel, Reporting Services reports, and other third-party BI tools.</span></span> 

## <a name="about-sql-server-analysis-services-documentation"></a><span data-ttu-id="de806-104">關於 SQL Server Analysis Services 檔</span><span class="sxs-lookup"><span data-stu-id="de806-104">About SQL Server Analysis Services documentation</span></span>

<span data-ttu-id="de806-105">檔會以版本分隔。</span><span class="sxs-lookup"><span data-stu-id="de806-105">Documentation is separated by version.</span></span> <span data-ttu-id="de806-106">您目前處於 SQL Server 2014 Analysis Services 檔。</span><span class="sxs-lookup"><span data-stu-id="de806-106">You are currently in SQL Server 2014 Analysis Services documentation.</span></span>

- <span data-ttu-id="de806-107">若要深入瞭解 SQL Server 2012 和更早版本，請參閱[SQL Server 舊版檔](https://docs.microsoft.com/previous-versions/sql/)。</span><span class="sxs-lookup"><span data-stu-id="de806-107">To learn more about SQL Server 2012 and earlier, see [SQL Server previous versions documentation](https://docs.microsoft.com/previous-versions/sql/).</span></span>
- <span data-ttu-id="de806-108">若要深入瞭解 SQL Server 2014，請參閱《[線上叢書》 SQL Server 2014](../index.yml)</span><span class="sxs-lookup"><span data-stu-id="de806-108">To learn more about SQL Server 2014, see [Books Online for SQL Server 2014](../index.yml)</span></span>
- <span data-ttu-id="de806-109">若要深入瞭解 SQL Server 2016 和更新版本，請參閱[Analysis Services 檔](https://docs.microsoft.com/analysis-services/)。</span><span class="sxs-lookup"><span data-stu-id="de806-109">To learn more about SQL Server 2016 and later, see [Analysis Services documentation](https://docs.microsoft.com/analysis-services/).</span></span>
- <span data-ttu-id="de806-110">若要深入瞭解 Azure Analysis Services，請參閱[azure Analysis Services 檔](https://docs.microsoft.com/azure/analysis-services/)。</span><span class="sxs-lookup"><span data-stu-id="de806-110">To learn more about Azure Analysis Services, see [Azure Analysis Services Documentation](https://docs.microsoft.com/azure/analysis-services/).</span></span>

## <a name="analysis-services-workflow"></a><span data-ttu-id="de806-111">Analysis Services 工作流程</span><span class="sxs-lookup"><span data-stu-id="de806-111">Analysis Services workflow</span></span>

<span data-ttu-id="de806-112">一般工作流程包括建立 OLAP 或表格式資料模型、將模型當做資料庫部署至伺服器實例、處理資料庫以載入資料，然後指派許可權以允許資料存取。</span><span class="sxs-lookup"><span data-stu-id="de806-112">A typical workflow includes building an OLAP or tabular data model, deploy the model as a database to a server instance, process the database to load it with data, and then assign permissions to allow data access.</span></span> <span data-ttu-id="de806-113">準備好開始執行時，任何支援 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 作為資料來源的用戶端應用程式，即可存取這個多用途資料模型。</span><span class="sxs-lookup"><span data-stu-id="de806-113">When it's ready to go, this multi-purpose data model can be accessed by any client application supporting [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] as a data source.</span></span>  
  
 <span data-ttu-id="de806-114">若要建立模型，請使用 SQL Server Data Tools (請參閱[Analysis Services) 中使用的工具和應用程式](tools-and-applications-used-in-analysis-services.md)，並選擇表格式或多維度和資料採礦專案範本。</span><span class="sxs-lookup"><span data-stu-id="de806-114">To create a model, use SQL Server Data Tools (see [Tools and applications used in Analysis Services](tools-and-applications-used-in-analysis-services.md)), choosing either a Tabular or Multidimensional and Data Mining project template.</span></span> <span data-ttu-id="de806-115">專案範本包含模型所需所有物件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="de806-115">The project template contains folders for all of the objects needed in a model.</span></span> <span data-ttu-id="de806-116">您可以使用精靈來建立所有基本項目，例如資料來源、資料來源檢視、維度、Cube 和角色。</span><span class="sxs-lookup"><span data-stu-id="de806-116">You can use wizards to create all of the basic elements, such as data sources, data source views, dimensions, cubes, and roles.</span></span>  
  
 <span data-ttu-id="de806-117">模型會填入外部資料系統中的資料，通常是在 SQL Server 或 Oracle 關聯式資料庫引擎上裝載的資料倉儲 (表格式模型支援其他資料來源類型)。</span><span class="sxs-lookup"><span data-stu-id="de806-117">Models are populated with data from external data systems, usually data warehouses hosted on a SQL Server or Oracle relational database engine (Tabular models support additional data source types).</span></span> <span data-ttu-id="de806-118">模型不僅會指定查詢物件 (例如 Cube)，也會指定維度 (可用於多個 Cube、計算和 KPI 以封裝商務邏輯) 以及互動 (例如瀏覽和鑽研行為)。</span><span class="sxs-lookup"><span data-stu-id="de806-118">Models specify query objects, such as cubes, but also specify dimensions that can be used in multiple cubes, calculations and KPIs that encapsulate business logic, and interactions such as navigation and drill-through behaviors.</span></span>  
  
 <span data-ttu-id="de806-119">若要使用模型，它會部署到以特定伺服器模式執行資料庫的伺服器實例，讓資料可供透過 Excel 或其他應用程式連接的授權使用者使用。</span><span class="sxs-lookup"><span data-stu-id="de806-119">To use a model, it's deployed to a server instance that runs databases in a particular server mode, making the data available to authorized users who connect through Excel or other applications.</span></span>  
  
 <span data-ttu-id="de806-120">您可以使用下列三種伺服器模式之一來安裝實例：</span><span class="sxs-lookup"><span data-stu-id="de806-120">You can install an instance in one of three server modes:</span></span>  
  
-   <span data-ttu-id="de806-121">當做表格式執行個體，執行表格式模型。</span><span class="sxs-lookup"><span data-stu-id="de806-121">As a Tabular instance, running Tabular models.</span></span>  
  
-   <span data-ttu-id="de806-122">當做多維度和資料採礦執行個體，執行 OLAP Cube 和資料採礦模型 (這是預設值)。</span><span class="sxs-lookup"><span data-stu-id="de806-122">As a Multidimensional and Data Mining instance, running OLAP cubes and data mining models (this is the default).</span></span>  
  
-   <span data-ttu-id="de806-123">當做 PowerPivot for SharePoint，在 SharePoint 中執行 PowerPivot 和 Excel 資料模型 (PowerPivot for SharePoint 是中間層資料引擎，可載入、查詢及重新整理 SharePoint 中所裝載的資料模型)。</span><span class="sxs-lookup"><span data-stu-id="de806-123">As PowerPivot for SharePoint, running PowerPivot and Excel data models in SharePoint (PowerPivot for SharePoint is a middle-tier data engine that loads, queries, and refreshes data models hosted in SharePoint).</span></span>  
  
 <span data-ttu-id="de806-124">相同資料引擎，三種不同的使用方式。</span><span class="sxs-lookup"><span data-stu-id="de806-124">Same data engine; three different ways to use it.</span></span> <span data-ttu-id="de806-125">請注意，安裝期間會設定伺服器模式，而且之後無法變更。</span><span class="sxs-lookup"><span data-stu-id="de806-125">Note that server modes are set during installation and cannot be changed later.</span></span> <span data-ttu-id="de806-126">如果您需要不同的模式，應該安裝新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="de806-126">You should install a new instance if you require a different mode.</span></span>  
  
 <span data-ttu-id="de806-127">Analysis Services 的基本文件集會組織成若干章節，這些章節會對應到您所建立的專案類型。</span><span class="sxs-lookup"><span data-stu-id="de806-127">Foundational documentation for Analysis Services is organized into sections that correspond to the type of project you are building.</span></span> <span data-ttu-id="de806-128">從下列連結進行選擇，以深入了解每一種模式或功能領域。</span><span class="sxs-lookup"><span data-stu-id="de806-128">Choose from the following links to learn more about each mode or feature area.</span></span>  
  
 <span data-ttu-id="de806-129">**依區域瀏覽內容**</span><span class="sxs-lookup"><span data-stu-id="de806-129">**Browse Content by Area**</span></span>  
 <span data-ttu-id="de806-130">[比較表格式和多維度方案 &#40;SSAS&#41;的](comparing-tabular-and-multidimensional-solutions-ssas.md)![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")</span><span class="sxs-lookup"><span data-stu-id="de806-130">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Comparing Tabular and Multidimensional Solutions &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)</span></span>  
  
 <span data-ttu-id="de806-131">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示") [Analysis Services 實例管理](instances/analysis-services-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="de806-131">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Analysis Services Instance Management](instances/analysis-services-instance-management.md)</span></span>  
  
 <span data-ttu-id="de806-132">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")[表格式模型化 &#40;SSAS 表格式&#41;](tabular-models/tabular-models-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="de806-132">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Tabular Modeling &#40;SSAS Tabular&#41;](tabular-models/tabular-models-ssas.md)</span></span>  
  
 <span data-ttu-id="de806-133">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")多[維度模型化 &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="de806-133">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Multidimensional Modeling &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)</span></span>  
  
 <span data-ttu-id="de806-134">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")[資料採礦 &#40;SSAS&#41;](data-mining/data-mining-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="de806-134">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Data Mining &#40;SSAS&#41;](data-mining/data-mining-ssas.md)</span></span>  
  
 <span data-ttu-id="de806-135">[&#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)的![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="de806-135">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [PowerPivot for SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="de806-136">功能會因版本而異。</span><span class="sxs-lookup"><span data-stu-id="de806-136">features vary by edition.</span></span> <span data-ttu-id="de806-137">Standard 版中可以使用多維度和資料採礦模型，但是功能少於較高的版本。</span><span class="sxs-lookup"><span data-stu-id="de806-137">Multidimensional and data mining models are available in standard edition, but with fewer features than higher editions.</span></span> <span data-ttu-id="de806-138">表格式模型和 PowerPivot for SharePoint 是高階功能，無法在 Standard 版授權之下使用。</span><span class="sxs-lookup"><span data-stu-id="de806-138">Tabular models and PowerPivot for SharePoint are premium features and are not available in a standard edition license.</span></span> <span data-ttu-id="de806-139">如需詳細資訊，請參閱＜ [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)＞。</span><span class="sxs-lookup"><span data-stu-id="de806-139">For more information, see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de806-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de806-140">See Also</span></span>  
 <span data-ttu-id="de806-141">[Analysis Services SSAS &#40;教學課程&#41;](analysis-services-tutorials-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="de806-141">[Analysis Services Tutorials &#40;SSAS&#41;](analysis-services-tutorials-ssas.md) </span></span>  
 <span data-ttu-id="de806-142">[SQL Server 2014 的安裝](../database-engine/install-windows/installation-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="de806-142">[Installation for SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md) </span></span>  
 <span data-ttu-id="de806-143">[開發人員指南 &#40;Analysis Services&#41;](analysis-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="de806-143">[Developer's Guide &#40;Analysis Services&#41;](analysis-services-developer-documentation.md) </span></span>  
 <span data-ttu-id="de806-144">[SQL Server 資源中心](https://go.microsoft.com/fwlink/?linkID=219676) </span><span class="sxs-lookup"><span data-stu-id="de806-144">[SQL Server Resource Center](https://go.microsoft.com/fwlink/?linkID=219676) </span></span>  
 [<span data-ttu-id="de806-145">SQLCat.com</span><span class="sxs-lookup"><span data-stu-id="de806-145">SQLCat.com</span></span>](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
