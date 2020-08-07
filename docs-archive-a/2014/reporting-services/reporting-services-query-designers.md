---
title: Reporting Services 查詢設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4febd0b0e0bf028d16aa3ef13ce4294feb930072
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703782"
---
# <a name="reporting-services-query-designers"></a><span data-ttu-id="8c5f5-102">Reporting Services 查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="8c5f5-102">Reporting Services Query Designers</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="8c5f5-103">提供圖形化查詢設計工具以及以文字為基礎的查詢設計工具，可協助您為報表中的每個資料來源類型建立查詢。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-103">provides graphical and text-based query designers to help you build queries for each data source type in your report.</span></span>  
  
 <span data-ttu-id="8c5f5-104">某些資料來源支援可協助您以互動方式建立查詢的圖形化設計工具。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-104">Some data sources support graphical designers that help you build a query interactively.</span></span> <span data-ttu-id="8c5f5-105">其他資料來源則使用以文字為基礎的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-105">Other data sources use a text-based query designer.</span></span> <span data-ttu-id="8c5f5-106">利用圖形化查詢設計工具，您可以將資料來源上，表示基礎資料的中繼資料項目拖曳到查詢設計介面。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-106">By using a graphical query designer, you can drag metadata items that represent the underlying data on a data source to the query design surface.</span></span> <span data-ttu-id="8c5f5-107">利用以文字為基礎的查詢設計工具，您可以將命令文字輸入到查詢窗格中。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-107">By using a text-based query designer, you can type command text into a query pane.</span></span> <span data-ttu-id="8c5f5-108">您可以從圖形化查詢設計工具切換到以文字為基礎的查詢設計工具，方法是按一下工具列上以文字為基礎的查詢設計工具圖示。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-108">You can change from a graphical query designer to a text-based query designer by clicking the text-based query designer icon on the toolbar.</span></span>  
  
 <span data-ttu-id="8c5f5-109">報表中的可用資料來源類型取決於用戶端或報表伺服器上安裝的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 資料延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-109">The data source types that are available in your report are determined by the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data extensions installed on your client or report server.</span></span> <span data-ttu-id="8c5f5-110">如需詳細資訊，請參閱[Rsreportdesigner.config 設定檔](report-server/rsreportdesigner-configuration-file.md)案和[rsreportserver.config 設定檔](report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-110">For more information, see [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) and [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="8c5f5-111">資料處理延伸模組及其相關聯的查詢設計工具，在資料來源支援的下列方式可能會有不同：</span><span class="sxs-lookup"><span data-stu-id="8c5f5-111">A data processing extension and its associated query designer can differ in support for data sources in the following ways:</span></span>  
  
-   <span data-ttu-id="8c5f5-112">**依查詢設計工具類型。**</span><span class="sxs-lookup"><span data-stu-id="8c5f5-112">**By query designer type.**</span></span> <span data-ttu-id="8c5f5-113">例如， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料來源同時支援圖形化查詢設計工具以及以文字為基礎的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-113">For example, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source supports both the graphical and text-based query designers.</span></span>  
  
-   <span data-ttu-id="8c5f5-114">**依查詢語言變化。**</span><span class="sxs-lookup"><span data-stu-id="8c5f5-114">**By query language variation.**</span></span> <span data-ttu-id="8c5f5-115">例如， [!INCLUDE[tsql](../includes/tsql-md.md)] 這類的查詢語言在語法上可能會視資料來源類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-115">For example, a query language such as [!INCLUDE[tsql](../includes/tsql-md.md)] can differ in syntax depending on the data source type.</span></span> <span data-ttu-id="8c5f5-116">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] 語言和 Oracle SQL 語言在查詢命令的語法上有一些變化。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-116">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] language and the Oracle SQL language have some variation in syntax for a query command.</span></span>  
  
-   <span data-ttu-id="8c5f5-117">**依資料庫物件名稱的結構描述部分支援。**</span><span class="sxs-lookup"><span data-stu-id="8c5f5-117">**By support for the schema part of a database object name.**</span></span> <span data-ttu-id="8c5f5-118">當資料來源使用結構描述做為資料庫物件識別碼的一部分時，必須針對不使用預設結構描述的任何名稱，提供結構描述名稱做為查詢的一部分。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-118">When a data source uses schemas as part of the database object identifier, the schema name must be supplied as part of the query for any names that do not use the default schema.</span></span> <span data-ttu-id="8c5f5-119">例如，`SELECT FirstName, LastName FROM [Person].[Person]`。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-119">For example, `SELECT FirstName, LastName FROM [Person].[Person]`.</span></span>  
  
-   <span data-ttu-id="8c5f5-120">**依查詢參數支援。**</span><span class="sxs-lookup"><span data-stu-id="8c5f5-120">**By support for query parameters.**</span></span> <span data-ttu-id="8c5f5-121">資料提供者的差異在於參數的支援。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-121">Data providers differ in support for parameters.</span></span> <span data-ttu-id="8c5f5-122">有些資料提供者支援指名參數，例如， `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-122">Some data providers support named parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`.</span></span> <span data-ttu-id="8c5f5-123">有些資料提供者則支援未指名參數，例如， `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-123">Some data providers support unnamed parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`.</span></span> <span data-ttu-id="8c5f5-124">參數識別碼可能依資料提供者而有所不同，例如， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用 @ 符號，而 Oracle 使用冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-124">The parameter identifier might differ by data provider; for example, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses the "at" (@) symbol, Oracle uses the colon (:).</span></span> <span data-ttu-id="8c5f5-125">而有些資料提供者不支援參數。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-125">Some data providers do not support parameters.</span></span>  
  
-   <span data-ttu-id="8c5f5-126">**依匯入查詢的能力。**</span><span class="sxs-lookup"><span data-stu-id="8c5f5-126">**By ability to import queries.**</span></span> <span data-ttu-id="8c5f5-127">例如，若為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料來源，您可以從報表定義檔案 (.rdl) 或 .sql 檔案匯入查詢。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-127">For example, for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source, you can import a query from a report definition file (.rdl) or from a .sql file.</span></span>  
  
## <a name="query-designers"></a><span data-ttu-id="8c5f5-128">查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="8c5f5-128">Query Designers</span></span>  
 <span data-ttu-id="8c5f5-129">下列主題會描述每一個查詢設計工具的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="8c5f5-129">The following topics describe the user interface for each query designer.</span></span>  
  
-   [<span data-ttu-id="8c5f5-130">Analysis Services MDX 查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="8c5f5-130">Analysis Services MDX Query Designer User Interface</span></span>](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="8c5f5-131">Analysis Services DMX 查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="8c5f5-131">Analysis Services DMX Query Designer User Interface</span></span>](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="8c5f5-132">圖形化查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="8c5f5-132">Graphical Query Designer User Interface</span></span>](report-data/graphical-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="8c5f5-133">關聯式查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="8c5f5-133">Relational Query Designer User Interface</span></span>](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="8c5f5-134">Hyperion Essbase 查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="8c5f5-134">Hyperion Essbase Query Designer User Interface</span></span>](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="8c5f5-135">報表模型查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="8c5f5-135">Report Model Query Designer User Interface</span></span>](report-data/report-model-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="8c5f5-136">SAP NetWeaver BI 查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="8c5f5-136">SAP NetWeaver BI Query Designer User Interface</span></span>](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="8c5f5-137">SharePoint 清單查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="8c5f5-137">SharePoint List Query Designer</span></span>](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [<span data-ttu-id="8c5f5-138">以文字為基礎的查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="8c5f5-138">Text-based Query Designer User Interface</span></span>](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c5f5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c5f5-139">See Also</span></span>  
 <span data-ttu-id="8c5f5-140">[Reporting Services &#40;SSRS 支援的資料來源&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="8c5f5-140">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="8c5f5-141">[從 &#40;SSRS&#41;的外部資料源加入資料](report-data/add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8c5f5-141">[Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="8c5f5-142">[&#40;SSRS 的資料處理延伸模組和 .NET Framework 資料提供者&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8c5f5-142">[Data Processing Extensions and .NET Framework Data Providers &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span></span>  
 [<span data-ttu-id="8c5f5-143">延伸模組 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8c5f5-143">Extensions &#40;SSRS&#41;</span></span>](extensions-ssrs.md)  
  
  
