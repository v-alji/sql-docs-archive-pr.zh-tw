---
title: Teradata 連線類型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 73e51c82a824bb607d75c2e78cfc9b0f37476e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598220"
---
# <a name="teradata-connection-type-ssrs"></a><span data-ttu-id="a141c-102">Teradata 連接類型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="a141c-102">Teradata Connection Type (SSRS)</span></span>
  <span data-ttu-id="a141c-103">若要在報表中包含來自 Teradata 關聯式資料庫的資料，您必須具有以 Teradata 類型的報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="a141c-103">To include data from a Teradata relational database in your report, you must have a dataset that is based on a report data source of type Teradata.</span></span> <span data-ttu-id="a141c-104">此內建的資料來源類型是以 .NET Managed Provider for Teradata 資料處理延伸模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="a141c-104">This built-in data source type is based on the .NET Managed Provider for Teradata data processing extension.</span></span>  
  
 <span data-ttu-id="a141c-105">您可以使用本主題中的資訊來建置資料來源。</span><span class="sxs-lookup"><span data-stu-id="a141c-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="a141c-106">如需逐步指示，請參閱 [加入及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a141c-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="a141c-107">連接字串</span><span class="sxs-lookup"><span data-stu-id="a141c-107">Connection String</span></span>  
 <span data-ttu-id="a141c-108">請洽詢資料庫管理員，以取得用來連接資料來源的連接資訊和認證。</span><span class="sxs-lookup"><span data-stu-id="a141c-108">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="a141c-109">下列連接字串範例會在使用 IP 位址所指定的伺服器上指定 Teradata 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a141c-109">The following connection string example specifies a Teradata database on the server specified with an IP address:</span></span>  
  
```  
data source=<IP Address>  
```  
  
 <span data-ttu-id="a141c-110">如需更多連接字串範例，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="a141c-110">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="a141c-111">認證</span><span class="sxs-lookup"><span data-stu-id="a141c-111">Credentials</span></span>  
 <span data-ttu-id="a141c-112">需要有認證才能夠執行報表、於本機預覽報表並且從報表伺服器預覽報表。</span><span class="sxs-lookup"><span data-stu-id="a141c-112">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="a141c-113">發行報表之後，您可能需要變更資料來源的認證，如此當報表在報表伺服器上執行時，擷取資料的權限就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="a141c-113">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="a141c-114">如需詳細資訊，請參閱 [Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ，或 [在 Report Builder 中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="a141c-114">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  

##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="a141c-115">備註</span><span class="sxs-lookup"><span data-stu-id="a141c-115">Remarks</span></span>  
 <span data-ttu-id="a141c-116">系統管理員必須先安裝支援從 Teradata 資料庫擷取資料的 .NET Data Provider for Teradata 版本，您才能夠連接 Teradata 資料來源。</span><span class="sxs-lookup"><span data-stu-id="a141c-116">Before you can connect a Teradata data source, the system administrator must have installed the version of the .NET Data Provider for Teradata that supports retrieving data from the Teradata database.</span></span> <span data-ttu-id="a141c-117">此資料提供者必須與報表產生器安裝在同一部電腦上，並且同樣位於報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a141c-117">This data provider must be installed on the same computer as Report Builder and also on the report server.</span></span>  
  
 <span data-ttu-id="a141c-118">這個資料提供者並沒有支援所有的報表傳遞模式。</span><span class="sxs-lookup"><span data-stu-id="a141c-118">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="a141c-119">這個資料處理延伸模組不支援透過資料驅動訂閱所傳遞的報表。</span><span class="sxs-lookup"><span data-stu-id="a141c-119">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="a141c-120">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [線上叢書](https://go.microsoft.com/fwlink/?linkid=121312)》中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文件的[使用外部資料來源以取得訂閱者資料 &#40;資料驅動訂閱&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="a141c-120">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  

##  <a name="report-models"></a><a name="Models"></a> <span data-ttu-id="a141c-121">報表模型</span><span class="sxs-lookup"><span data-stu-id="a141c-121">Report Models</span></span>  
 <span data-ttu-id="a141c-122">若要從以 Teradata 資料來源為基礎的報表模型建立資料集，該模型必須是在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的模型設計師中所設計，並在報表伺服器上發佈。</span><span class="sxs-lookup"><span data-stu-id="a141c-122">To create a dataset from a report model that is based on a Teradata data source, the model must be designed in Model Designer in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and published on a report server.</span></span>  

##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="a141c-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="a141c-123">Related Sections</span></span>  
 <span data-ttu-id="a141c-124">本文件集的這些章節會提供報表資料的深入概念性資訊，以及如何定義、自訂和使用與報表資料相關組件的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="a141c-124">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="a141c-125">將資料加入至報表 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a141c-125">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="a141c-126">提供存取報表資料的概觀。</span><span class="sxs-lookup"><span data-stu-id="a141c-126">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="a141c-127">報表產生器中的資料連接、資料來源及連接字串</span><span class="sxs-lookup"><span data-stu-id="a141c-127">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="a141c-128">提供資料連接與資料來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a141c-128">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="a141c-129">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a141c-129">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="a141c-130">提供內嵌與共用資料集的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a141c-130">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="a141c-131">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a141c-131">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="a141c-132">提供資料集查詢所產生之欄位集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a141c-132">Provides information about the field collection that is generated by the dataset query.</span></span>  
  
 <span data-ttu-id="a141c-133">《[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services 支援的資料來源 &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="a141c-133">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="a141c-134">提供支援每一個資料延伸模組之平台與版本的深入資訊。</span><span class="sxs-lookup"><span data-stu-id="a141c-134">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 [<span data-ttu-id="a141c-135">使用 SQL Server 2008 Reporting Services 搭配 .NET Framework Data Provider for Teradata</span><span class="sxs-lookup"><span data-stu-id="a141c-135">Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata</span></span>](https://go.microsoft.com/fwlink/?LinkID=130848)  
 <span data-ttu-id="a141c-136">提供有關使用這個資料延伸模組的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a141c-136">Provides detailed information about working with this data extension.</span></span>  

## <a name="see-also"></a><span data-ttu-id="a141c-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a141c-137">See Also</span></span>  
 <span data-ttu-id="a141c-138">[報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="a141c-138">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="a141c-139">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a141c-139">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a141c-140">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a141c-140">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
