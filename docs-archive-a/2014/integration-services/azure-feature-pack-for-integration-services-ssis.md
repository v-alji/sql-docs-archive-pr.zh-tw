---
title: Azure Feature Pack |Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.SSIS.AZURE.F1
- SQL12.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8bca2b4d3ce91f6010fbe01da836efd8a67ca6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687133"
---
# <a name="azure-feature-pack"></a><span data-ttu-id="d04d9-102">Azure 功能套件</span><span class="sxs-lookup"><span data-stu-id="d04d9-102">Azure Feature Pack</span></span>
<span data-ttu-id="d04d9-103">SQL Server Integration Services (SSIS) Feature Pack for Azure 是一個延伸模組，可提供此頁面上所列的元件，以便讓 SSIS 連接到 Azure 服務、在 Azure 和內部部署資料來源之間轉送資料，以及處理儲存在 Azure 中的資料。</span><span class="sxs-lookup"><span data-stu-id="d04d9-103">SQL Server Integration Services (SSIS) Feature Pack for Azure is an extension that provides the components listed on this page for SSIS to connect to Azure services, transfer data between Azure and on-premises data sources, and process data stored in Azure.</span></span>

## <a name="components-in-the-feature-pack"></a><span data-ttu-id="d04d9-104">Feature Pack 中的元件</span><span class="sxs-lookup"><span data-stu-id="d04d9-104">Components in the Feature Pack</span></span>
  
-   <span data-ttu-id="d04d9-105">連接管理員</span><span class="sxs-lookup"><span data-stu-id="d04d9-105">Connection Managers</span></span>  
  
    -   [<span data-ttu-id="d04d9-106">Azure 儲存體連線管理員</span><span class="sxs-lookup"><span data-stu-id="d04d9-106">Azure Storage Connection Manager</span></span>](connection-manager/azure-storage-connection-manager.md)  
  
    -   [<span data-ttu-id="d04d9-107">Azure 訂用帳戶連線管理員</span><span class="sxs-lookup"><span data-stu-id="d04d9-107">Azure Subscription Connection Manager</span></span>](connection-manager/azure-subscription-connection-manager.md)  
    
    -   [<span data-ttu-id="d04d9-108">Azure Data Lake Store 連線管理員</span><span class="sxs-lookup"><span data-stu-id="d04d9-108">Azure Data Lake Store Connection Manager</span></span>](../../2014/integration-services/azure-data-lake-store-connection-manager.md)
    
    -   [<span data-ttu-id="d04d9-109">Azure Resource Manager 連線管理員</span><span class="sxs-lookup"><span data-stu-id="d04d9-109">Azure Resource Manager Connection Manager</span></span>](../../2014/integration-services/azure-resource-manager-connection-manager.md)
    
    -   [<span data-ttu-id="d04d9-110">Azure HDInsight 連線管理員</span><span class="sxs-lookup"><span data-stu-id="d04d9-110">Azure HDInsight Connection Manager</span></span>](../../2014/integration-services/azure-hdinsight-connection-manager.md)
  
-   <span data-ttu-id="d04d9-111">工作</span><span class="sxs-lookup"><span data-stu-id="d04d9-111">Tasks</span></span>  
  
    -   [<span data-ttu-id="d04d9-112">Azure Blob 上傳工作</span><span class="sxs-lookup"><span data-stu-id="d04d9-112">Azure Blob Upload Task</span></span>](control-flow/azure-blob-upload-task.md)  
  
    -   [<span data-ttu-id="d04d9-113">Azure Blob 下載工作</span><span class="sxs-lookup"><span data-stu-id="d04d9-113">Azure Blob Download Task</span></span>](control-flow/azure-blob-download-task.md)  
  
    -   [<span data-ttu-id="d04d9-114">Azure HDInsight Hive 工作</span><span class="sxs-lookup"><span data-stu-id="d04d9-114">Azure HDInsight Hive Task</span></span>](control-flow/azure-hdinsight-hive-task.md)  
  
    -   <span data-ttu-id="d04d9-115">[Azure HDInsight Pig 工作](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="d04d9-115">[Azure HDInsight Pig Task](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)</span></span>
  
    -   [<span data-ttu-id="d04d9-116">Azure HDInsight 建立叢集工作</span><span class="sxs-lookup"><span data-stu-id="d04d9-116">Azure HDInsight Create Cluster Task</span></span>](control-flow/azure-hdinsight-create-cluster-task.md)  
  
    -   [<span data-ttu-id="d04d9-117">Azure HDInsight 刪除叢集工作</span><span class="sxs-lookup"><span data-stu-id="d04d9-117">Azure HDInsight Delete Cluster Task</span></span>](control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [<span data-ttu-id="d04d9-118">Azure SQL DW 上傳工作</span><span class="sxs-lookup"><span data-stu-id="d04d9-118">Azure SQL DW Upload Task</span></span>](../../2014/integration-services/azure-sql-dw-upload-task.md)    
    
    -   [<span data-ttu-id="d04d9-119">Azure Data Lake Store 檔案系統工作</span><span class="sxs-lookup"><span data-stu-id="d04d9-119">Azure Data Lake Store File System Task</span></span>](control-flow/file-system-task.md)    
  
-   <span data-ttu-id="d04d9-120">資料流程元件</span><span class="sxs-lookup"><span data-stu-id="d04d9-120">Data Flow Components</span></span>  
  
    -   <span data-ttu-id="d04d9-121">[Azure Blob 來源](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="d04d9-121">[Azure Blob Source](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)</span></span>  
  
    -   [<span data-ttu-id="d04d9-122">Azure Blob 目的地</span><span class="sxs-lookup"><span data-stu-id="d04d9-122">Azure Blob Destination</span></span>](data-flow/azure-blob-destination.md)  
    
    -   [<span data-ttu-id="d04d9-123">Azure Data Lake Store 來源</span><span class="sxs-lookup"><span data-stu-id="d04d9-123">Azure Data Lake Store Source</span></span>](../../2014/integration-services/azure-data-lake-store-source.md)
    
    -   [<span data-ttu-id="d04d9-124">Azure Data Lake Store 目的地</span><span class="sxs-lookup"><span data-stu-id="d04d9-124">Azure Data Lake Store Destination</span></span>](../../2014/integration-services/azure-data-lake-store-destination.md)
  
-   <span data-ttu-id="d04d9-125">Azure Blob 列舉值 & ADLS 檔案列舉值。</span><span class="sxs-lookup"><span data-stu-id="d04d9-125">Azure Blob Enumerator & ADLS File Enumerator.</span></span> <span data-ttu-id="d04d9-126">請參閱[Foreach 迴圈容器](control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="d04d9-126">See [Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
 
## <a name="download-the-feature-pack"></a><span data-ttu-id="d04d9-127">下載功能套件</span><span class="sxs-lookup"><span data-stu-id="d04d9-127">Download the Feature Pack</span></span>  
<span data-ttu-id="d04d9-128">下載 SQL Server Integration Services (SSIS) Feature Pack for Azure。</span><span class="sxs-lookup"><span data-stu-id="d04d9-128">Download the SQL Server Integration Services (SSIS) Feature Pack for Azure.</span></span>  
  
-   [<span data-ttu-id="d04d9-129">Azure 的 Microsoft SQL Server 2014 Integration Services 功能套件</span><span class="sxs-lookup"><span data-stu-id="d04d9-129">Microsoft SQL Server 2014 Integration Services Feature Pack for Azure</span></span>](https://www.microsoft.com/download/details.aspx?id=47366)  

## <a name="prerequisites"></a><span data-ttu-id="d04d9-130">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d04d9-130">Prerequisites</span></span>  
<span data-ttu-id="d04d9-131">您必須先安裝下列必要條件，再安裝這個功能套件。</span><span class="sxs-lookup"><span data-stu-id="d04d9-131">You must install the following prerequisites before installing this feature pack.</span></span>  
  
-   <span data-ttu-id="d04d9-132">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="d04d9-132">SQL Server Integration Services</span></span>  
-   <span data-ttu-id="d04d9-133">.Net Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d04d9-133">.Net Framework 4.5</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="d04d9-134">案例</span><span class="sxs-lookup"><span data-stu-id="d04d9-134">Scenarios</span></span>  
  
### <a name="big-data-processing"></a><span data-ttu-id="d04d9-135">巨量資料處理</span><span class="sxs-lookup"><span data-stu-id="d04d9-135">Big Data Processing</span></span>  
 <span data-ttu-id="d04d9-136">您可以使用 Azure 連接器來完成下列巨量資料處理工作：</span><span class="sxs-lookup"><span data-stu-id="d04d9-136">Use Azure Connector to complete following big data processing work:</span></span>  
  
1.  <span data-ttu-id="d04d9-137">使用 Azure Blob 上傳工作，將輸入資料上傳至 Azure Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="d04d9-137">Use the Azure Blob Upload Task to upload input data to Azure Blob Storage.</span></span>  
  
2.  <span data-ttu-id="d04d9-138">使用 Azure HDInsight 建立叢集工作，建立 Azure HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="d04d9-138">Use the Azure HDInsight Create Cluster Task to create an Azure HDInsight cluster.</span></span> <span data-ttu-id="d04d9-139">如果您要使用自己的叢集，這是選擇性步驟。</span><span class="sxs-lookup"><span data-stu-id="d04d9-139">This step is optional if you want to use your own cluster.</span></span>  
  
3.  <span data-ttu-id="d04d9-140">使用 Azure HDInsight 登錄區工作或 Azure HDInsight Pig 工作，在 Azure HDInsight 叢集上叫用 Pig 或登錄區工作。</span><span class="sxs-lookup"><span data-stu-id="d04d9-140">Use the Azure HDInsight Hive Task or Azure HDInsight Pig Task to invoke a Pig or Hive job on the Azure HDInsight cluster.</span></span>  
  
4.  <span data-ttu-id="d04d9-141">如果在步驟 2 中建立了隨選 HDInsight 叢集，在使用過後，可使用 Azure HDInsight 刪除叢集工作來刪除該 HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="d04d9-141">Use the Azure HDInsight Delete Cluster Task to delete the HDInsight Cluster after use if you have created an on-demand HDInsight cluster in step #2.</span></span>  
  
5.  <span data-ttu-id="d04d9-142">使用 Azure HDInsight Blob 下載工作，從 Azure Blob 儲存體下載 Pig/登錄區輸出資料。</span><span class="sxs-lookup"><span data-stu-id="d04d9-142">Use the Azure HDInsight Blob Download Task to download the Pig/Hive output data from the Azure Blob Storage.</span></span>  
  
 <span data-ttu-id="d04d9-143">![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")</span><span class="sxs-lookup"><span data-stu-id="d04d9-143">![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")</span></span>  
  
### <a name="cloud-data-archiving"></a><span data-ttu-id="d04d9-144">雲端資料封存</span><span class="sxs-lookup"><span data-stu-id="d04d9-144">Cloud Data Archiving</span></span>  
 <span data-ttu-id="d04d9-145">您可以使用 SSIS 封裝中的 Azure Blob 目的地，將輸出資料寫入 Azure Blob 儲存體，或者使用 Azure Blob 來源，從 Azure Blob 儲存體讀取資料。</span><span class="sxs-lookup"><span data-stu-id="d04d9-145">Use the Azure Blob Destination in an SSIS package to write output data to an Azure Blob Storage, or use the Azure Blob Source to read data from an Azure Blob Storage.</span></span>  
  
 <span data-ttu-id="d04d9-146">![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")</span><span class="sxs-lookup"><span data-stu-id="d04d9-146">![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")</span></span>  
  
 <span data-ttu-id="d04d9-147">![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")</span><span class="sxs-lookup"><span data-stu-id="d04d9-147">![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")</span></span>  
  
 <span data-ttu-id="d04d9-148">此外，您還可以搭配 Azure Blob 列舉程式使用 Foreach 迴圈容器，來處理多個 Bob 檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="d04d9-148">And use the Foreach Loop Container with Azure Blob Enumerator to process data in multiple bob files.</span></span>  
  
 <span data-ttu-id="d04d9-149">![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")</span><span class="sxs-lookup"><span data-stu-id="d04d9-149">![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")</span></span>  
  
  
