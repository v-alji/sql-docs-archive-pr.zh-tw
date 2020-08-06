---
title: " (Partition Wizard) 的處理和儲存位置 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifyprocessingandstorage.f1
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00ab88bac184f57bd2b4dcfdb8d00909a85ece4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708713"
---
# <a name="processing-and-storage-locations-partition-wizard"></a><span data-ttu-id="8cc2d-102">處理與儲存位置 (資料分割精靈)</span><span class="sxs-lookup"><span data-stu-id="8cc2d-102">Processing and Storage Locations (Partition Wizard)</span></span>
  <span data-ttu-id="8cc2d-103">使用 [處理與儲存位置]\*\*\*\* 頁面，即可指定擁有資料分割之 Cube 的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體，以及儲存該資料分割之資料的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-103">Use the **Processing and Storage Locations** page to specify the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance of the cube that owns the partition, as well as the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that stores the data for the partition.</span></span> <span data-ttu-id="8cc2d-104">藉由指定遠端 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體或指定預設儲存位置以外的儲存位置，即可將資料分割定義為遠端資料分割。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-104">You can define a partition as a remote partition by specifying either a remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a storage location other than the default storage location.</span></span> <span data-ttu-id="8cc2d-105">如需遠端資料分割的詳細資訊，請參閱 [遠端資料分割](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-105">For more information about remote partitions, see [Remote Partitions](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).</span></span>  
  
## <a name="processing-location-options"></a><span data-ttu-id="8cc2d-106">處理位置選項</span><span class="sxs-lookup"><span data-stu-id="8cc2d-106">Processing location Options</span></span>  
 <span data-ttu-id="8cc2d-107">**目前伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="8cc2d-107">**Current server instance**</span></span>  
 <span data-ttu-id="8cc2d-108">使目前的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體負責處理資料分割。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-108">Makes the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing the partition.</span></span>  
  
 <span data-ttu-id="8cc2d-109">**遠端 Analysis Services 資料來源**</span><span class="sxs-lookup"><span data-stu-id="8cc2d-109">**Remote Analysis Services data source**</span></span>  
 <span data-ttu-id="8cc2d-110">使遠端 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體負責處理此資料分割。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-110">Makes a remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing this partition.</span></span>  
  
 <span data-ttu-id="8cc2d-111">從下拉式清單中，選取代表負責處理資料分割之遠端 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-111">From the dropdown list, select the data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that will be responsible for processing the partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cc2d-112">如果您選取的資料來源之 `Initial Catalog` 連接字串屬性並未設定為有效的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，或是如果 `Initial Catalog` 連接字串屬性中所指定的資料庫並不支援遠端資料分割 (換言之，指定之資料庫的 `MasterDatasourceID` 屬性並未設定為有效值)，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-112">An error occurs if you select a data source in which the `Initial Catalog` connection string property is not set to a valid [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or if the database specified in the `Initial Catalog` connection string property does not support remote partitions (in other words, the `MasterDatasourceID` property of the specified database is not set to a valid value).</span></span>  
  
 <span data-ttu-id="8cc2d-113">**新增**</span><span class="sxs-lookup"><span data-stu-id="8cc2d-113">**New**</span></span>  
 <span data-ttu-id="8cc2d-114">建立代表負責處理資料分割之遠端 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的新資料來源。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-114">Creates a new data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing the partition.</span></span>  
  
## <a name="storage-location-options"></a><span data-ttu-id="8cc2d-115">儲存位置選項</span><span class="sxs-lookup"><span data-stu-id="8cc2d-115">Storage location Options</span></span>  
 <span data-ttu-id="8cc2d-116">**預設伺服器位置**</span><span class="sxs-lookup"><span data-stu-id="8cc2d-116">**Default server location**</span></span>  
 <span data-ttu-id="8cc2d-117">使目前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體資料的資料夾，成為資料分割之彙總與索引資料的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-117">Makes the data folder of the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance the storage location of the aggregation and indexing data for the partition.</span></span>  
  
 <span data-ttu-id="8cc2d-118">**指定的資料夾**</span><span class="sxs-lookup"><span data-stu-id="8cc2d-118">**Specified folder**</span></span>  
 <span data-ttu-id="8cc2d-119">指定資料分割之彙總與索引資料的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-119">Specifies the storage location of the aggregation and indexing data for the partition.</span></span>  
  
 <span data-ttu-id="8cc2d-120">**...**</span><span class="sxs-lookup"><span data-stu-id="8cc2d-120">**...**</span></span>  
 <span data-ttu-id="8cc2d-121">顯示 [瀏覽遠端資料夾]\*\*\*\* 對話方塊，您可以在其中為 [指定的資料夾]\*\*\*\* 選取資料夾。</span><span class="sxs-lookup"><span data-stu-id="8cc2d-121">Displays the **Browse for Remote Folder** dialog box in which you can select a folder for **Specified folder**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc2d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cc2d-122">See Also</span></span>  
 <span data-ttu-id="8cc2d-123">[分割區 Wizard F1 說明 &#40;Analysis Services-多維度資料&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8cc2d-123">[Partition Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8cc2d-124">[分割區 &#40;Analysis Services 多維度資料&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8cc2d-124">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8cc2d-125">[[流覽遠端資料夾] 對話方塊 &#40;Analysis Services-多維度資料&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="8cc2d-125">[Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
