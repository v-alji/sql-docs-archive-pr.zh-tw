---
title: 報表資料窗格
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fc09c100cc8391bb1fd025b4bb5ac5f3b5e4379a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585059"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a><span data-ttu-id="813ea-102">SQL Server Reporting Services (SSRS) 中的報表資料窗格</span><span class="sxs-lookup"><span data-stu-id="813ea-102">Report Data pane in SQL Server Reporting Services (SSRS)</span></span>

  <span data-ttu-id="813ea-103">[報表資料]  窗格可用於檢視報表中目前定義的參數、資料來源、資料集、欄位集合和影像。</span><span class="sxs-lookup"><span data-stu-id="813ea-103">Use the **Report Data** pane to view the currently defined parameters, data sources, datasets, field collections, and images in your report.</span></span> <span data-ttu-id="813ea-104">[圖表資料] 會以階層檢視來顯示表示報表中資料的項目。</span><span class="sxs-lookup"><span data-stu-id="813ea-104">The Report Dane displays a hierarchical view of the items that represent data in your report.</span></span> <span data-ttu-id="813ea-105">最上層節點代表內建欄位、參數、影像和資料來源參考。</span><span class="sxs-lookup"><span data-stu-id="813ea-105">The top level nodes represent built-in fields, parameters, images, and data source references.</span></span> <span data-ttu-id="813ea-106">請展開每個節點以檢視資料項目。</span><span class="sxs-lookup"><span data-stu-id="813ea-106">Expand each node to view the data items.</span></span> <span data-ttu-id="813ea-107">例如，當您展開資料來源節點時，為該資料來源所定義的資料集就會顯示。</span><span class="sxs-lookup"><span data-stu-id="813ea-107">For example, when you expand a data source node, the datasets defined for that data source appear.</span></span> <span data-ttu-id="813ea-108">在展開資料集時，其欄位集合就會顯示。</span><span class="sxs-lookup"><span data-stu-id="813ea-108">When you expand a dataset, its field collection appears.</span></span> <span data-ttu-id="813ea-109">將項目拖曳到報表設計介面，以將資料連結到報表頁面的報表項目。</span><span class="sxs-lookup"><span data-stu-id="813ea-109">Drag items to the report design surface to link data with report items on the report page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="813ea-110">選項。</span><span class="sxs-lookup"><span data-stu-id="813ea-110">Options</span></span>

 <span data-ttu-id="813ea-111">**內建欄位**</span><span class="sxs-lookup"><span data-stu-id="813ea-111">**Built-in Fields**</span></span>  
 <span data-ttu-id="813ea-112">代表 Reporting Services 所提供的欄位，這些欄位常用於報表中，例如報表名稱或頁碼。</span><span class="sxs-lookup"><span data-stu-id="813ea-112">Represents fields provided by Reporting Services that are commonly used in a report, such as the report name or page number.</span></span> <span data-ttu-id="813ea-113">如需詳細資訊，請參閱[運算式中的內建集合 &#40;報表產生器及 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="813ea-113">For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
 <span data-ttu-id="813ea-114">**參數**</span><span class="sxs-lookup"><span data-stu-id="813ea-114">**Parameters**</span></span>  
 <span data-ttu-id="813ea-115">代表報表參數的集合，每個參數都可以是單一數值或多重值。</span><span class="sxs-lookup"><span data-stu-id="813ea-115">Represents the collection of report parameters, each of which can be single-valued or multivalued.</span></span> <span data-ttu-id="813ea-116">如需詳細資訊，請參閱 MSDN 上的 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="813ea-116">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
 <span data-ttu-id="813ea-117">**影像**</span><span class="sxs-lookup"><span data-stu-id="813ea-117">**Images**</span></span>  
 <span data-ttu-id="813ea-118">代表用於報表中的一組影像。</span><span class="sxs-lookup"><span data-stu-id="813ea-118">Represents the set of images used in the report.</span></span> <span data-ttu-id="813ea-119">如需詳細資訊，請參閱[影像 &#40;報表產生器及 SSRS&#41;](../report-design/images-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="813ea-119">For more information, see [Images &#40;Report Builder and SSRS&#41;](../report-design/images-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="813ea-120">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="813ea-120">**Data source**</span></span>  
 <span data-ttu-id="813ea-121">代表內嵌資料來源或共用資料來源的單一資料來源參考。</span><span class="sxs-lookup"><span data-stu-id="813ea-121">Represents a single data source reference to an embedded data source or to a shared data source.</span></span> <span data-ttu-id="813ea-122">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，共用資料來源會出現在方案總管的 [共用資料來源] 資料夾下方。</span><span class="sxs-lookup"><span data-stu-id="813ea-122">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], shared data sources appear in Solution Explorer under the Shared Data Sources folder.</span></span> <span data-ttu-id="813ea-123">資料來源指定 Reporting Services 所支援的資料來源類型之一。</span><span class="sxs-lookup"><span data-stu-id="813ea-123">A data source specifies one of the data source types supported by Reporting Services.</span></span> <span data-ttu-id="813ea-124">資料來源是以其為基礎之資料集集合的父節點。</span><span class="sxs-lookup"><span data-stu-id="813ea-124">A data source is the parent node for the collection of datasets based on it.</span></span> <span data-ttu-id="813ea-125">如需詳細資訊，請參閱[Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="813ea-125">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) .</span></span>  
  
 <span data-ttu-id="813ea-126">**資料集**</span><span class="sxs-lookup"><span data-stu-id="813ea-126">**Dataset**</span></span>  
 <span data-ttu-id="813ea-127">代表單一資料集。</span><span class="sxs-lookup"><span data-stu-id="813ea-127">Represents a single dataset.</span></span> <span data-ttu-id="813ea-128">資料集是由查詢所指定之欄位集合的父節點，包含任何導出欄位。</span><span class="sxs-lookup"><span data-stu-id="813ea-128">A dataset is the parent node for the collection of fields specified by the query and including any calculated fields.</span></span> <span data-ttu-id="813ea-129">Reporting Services 支援查詢設計工具，可協助您指定查詢。</span><span class="sxs-lookup"><span data-stu-id="813ea-129">Reporting Services supports query designers to help you specify a query.</span></span> <span data-ttu-id="813ea-130">如需詳細資訊，請參閱[在報表設計師 SQL Server Data Tools &#40;SSRS&#41;中](query-design-tools-ssrs.md)，[將資料加入報表 &#40;報表產生器和 Ssrs&#41;](report-datasets-ssrs.md)和查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="813ea-130">For more information, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) and [Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="813ea-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="813ea-131">Next steps</span></span>

 - [<span data-ttu-id="813ea-132">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="813ea-132">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)
 - [<span data-ttu-id="813ea-133">群組窗格</span><span class="sxs-lookup"><span data-stu-id="813ea-133">Grouping Pane</span></span>](../tools/grouping-pane.md)