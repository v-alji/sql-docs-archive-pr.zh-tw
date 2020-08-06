---
title: 遠端資料分割 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32fdf05d061d4e1c1da6ec0ef9179ecd12bda172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702046"
---
# <a name="remote-partitions"></a><span data-ttu-id="b96cb-102">遠端資料分割</span><span class="sxs-lookup"><span data-stu-id="b96cb-102">Remote Partitions</span></span>
  <span data-ttu-id="b96cb-103">遠端分割區的資料會儲存在不同的 Microsoft 實例上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，而實例包含資料分割和其父 cube (中繼資料) 的定義。</span><span class="sxs-lookup"><span data-stu-id="b96cb-103">The data of a remote partition is stored on a different instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] than the instance that contains the definitions (metadata) of the partition and its parent cube.</span></span> <span data-ttu-id="b96cb-104">遠端資料分割是在與定義資料分割和其父 Cube 的相同 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上進行管理。</span><span class="sxs-lookup"><span data-stu-id="b96cb-104">A remote partition is administered on the same instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube are defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b96cb-105">若要儲存遠端資料分割，電腦必須 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 安裝實例，而且執行的 Service Pack 層級與定義資料分割的實例相同。</span><span class="sxs-lookup"><span data-stu-id="b96cb-105">To store a remote partition, the computer must have an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installed and be running the same service pack level as the instance where the partition was defined.</span></span> <span data-ttu-id="b96cb-106">而舊版 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上的遠端資料分割則不予支援。</span><span class="sxs-lookup"><span data-stu-id="b96cb-106">Remote partitions on instances of an earlier version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are not supported.</span></span>  
  
 <span data-ttu-id="b96cb-107">量值群組中包含遠端資料分割時，會將 Cube 的記憶體和 CPU 使用情形分散在該量值群組的所有資料分割中。</span><span class="sxs-lookup"><span data-stu-id="b96cb-107">When remote partitions are included in a measure group, the memory and CPU utilization of the cube is distributed across all the partitions in the measure group.</span></span> <span data-ttu-id="b96cb-108">例如，單獨或當成父 Cube 處理的一部分來處理遠端資料分割時，該資料分割的大多數記憶體和 CPU 使用是發生在遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="b96cb-108">For example, when a remote partition is processed, either alone or as part of parent cube processing, most of the memory and CPU utilization for that partition occurs on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b96cb-109">包含遠端資料分割的 Cube 可以包含啟用寫入的維度。不過，這可能會影響 Cube 的效能。</span><span class="sxs-lookup"><span data-stu-id="b96cb-109">A cube that contains remote partitions can contain write-enabled dimensions; however, this may affect performance for the cube.</span></span> <span data-ttu-id="b96cb-110">如需已啟用寫入維度的詳細資訊，請參閱可[寫入維度](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="b96cb-110">For more information about write-enabled dimensions, see [Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span></span>  
  
## <a name="storage-modes-for-remote-partitions"></a><span data-ttu-id="b96cb-111">遠端資料分割的儲存模式</span><span class="sxs-lookup"><span data-stu-id="b96cb-111">Storage Modes for Remote Partitions</span></span>  
 <span data-ttu-id="b96cb-112">遠端資料分割可以使用本機資料分割所使用的任何儲存類型：多維度 OLAP (MOLAP)、混合式 OLAP (HOLAP) 或關聯式 OLAP (ROLAP)。</span><span class="sxs-lookup"><span data-stu-id="b96cb-112">Remote partitions may use any of the storage types used by local partitions: multidimensional OLAP (MOLAP), hybrid OLAP (HOLAP), or relational OLAP (ROLAP).</span></span> <span data-ttu-id="b96cb-113">遠端資料分割也可以使用主動式快取。</span><span class="sxs-lookup"><span data-stu-id="b96cb-113">Remote partitions may also use proactive caching.</span></span> <span data-ttu-id="b96cb-114">依遠端資料分割的儲存模式而定，下列資料是儲存在遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="b96cb-114">Depending on the storage mode of a remote partition, the following data is stored on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b96cb-115">儲存類型</span><span class="sxs-lookup"><span data-stu-id="b96cb-115">Storage Type</span></span>|<span data-ttu-id="b96cb-116">資料</span><span class="sxs-lookup"><span data-stu-id="b96cb-116">Data</span></span>|  
|<span data-ttu-id="b96cb-117">MOLAP</span><span class="sxs-lookup"><span data-stu-id="b96cb-117">MOLAP</span></span>|<span data-ttu-id="b96cb-118">資料分割的彙總，以及資料分割之來源資料的副本。</span><span class="sxs-lookup"><span data-stu-id="b96cb-118">The partition's aggregations and a copy of the partition's source data</span></span>|  
|<span data-ttu-id="b96cb-119">HOLAP</span><span class="sxs-lookup"><span data-stu-id="b96cb-119">HOLAP</span></span>|<span data-ttu-id="b96cb-120">資料分割的彙總</span><span class="sxs-lookup"><span data-stu-id="b96cb-120">The partitions aggregations</span></span>|  
|<span data-ttu-id="b96cb-121">ROLAP</span><span class="sxs-lookup"><span data-stu-id="b96cb-121">ROLAP</span></span>|<span data-ttu-id="b96cb-122">無資料分割資料</span><span class="sxs-lookup"><span data-stu-id="b96cb-122">No partition data</span></span>|  
  
 <span data-ttu-id="b96cb-123">如果量值群組包含多個儲存在多個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上的 MOLAP 或 HOLAP 資料分割，則 Cube 會將量值群組的資料分散到那些 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之間。</span><span class="sxs-lookup"><span data-stu-id="b96cb-123">If a measure group contains multiple MOLAP or HOLAP partitions stored on multiple instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cube distributes the data in the measure group data among those instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="merging-remote-partitions"></a><span data-ttu-id="b96cb-124">合併遠端資料分割</span><span class="sxs-lookup"><span data-stu-id="b96cb-124">Merging Remote Partitions</span></span>  
 <span data-ttu-id="b96cb-125">遠端資料分割只可與儲存在相同遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上的其他遠端資料分割合併。</span><span class="sxs-lookup"><span data-stu-id="b96cb-125">Remote partitions can be merged only with other remote partitions that are stored on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b96cb-126">如需合併資料分割的詳細資訊，請參閱[Analysis Services &#40;SSAS-多維度&#41;中的合併](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)資料分割。</span><span class="sxs-lookup"><span data-stu-id="b96cb-126">For more information about merging partitions, see [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).</span></span>  
  
## <a name="archiving-and-restoring-remote-partitions"></a><span data-ttu-id="b96cb-127">封存與還原遠端資料分割</span><span class="sxs-lookup"><span data-stu-id="b96cb-127">Archiving and Restoring Remote Partitions</span></span>  
 <span data-ttu-id="b96cb-128">封存或還原用來儲存遠端資料分割的資料庫時，可封存或還原遠端資料分割中的資料。</span><span class="sxs-lookup"><span data-stu-id="b96cb-128">Data in remote partitions can be archived or restored when the database that stores the remote partition is archived or restored.</span></span> <span data-ttu-id="b96cb-129">如果您還原資料庫，而未還原遠端資料分割，則必須先處理遠端資料分割後，才可使用該資料分割中的資料。</span><span class="sxs-lookup"><span data-stu-id="b96cb-129">If you restore a database without restoring a remote partition, you must process the remote partition before you can use the data in the partition.</span></span> <span data-ttu-id="b96cb-130">如需有關封存和還原資料庫的詳細資訊，請參閱[備份和還原 Analysis Services 資料庫](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="b96cb-130">For more information about archiving and restoring databases, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96cb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b96cb-131">See Also</span></span>  
 <span data-ttu-id="b96cb-132">[建立和管理遠端資料分割 &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b96cb-132">[Create and Manage a Remote Partition &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span></span>  
 [<span data-ttu-id="b96cb-133">處理 Analysis Services 物件</span><span class="sxs-lookup"><span data-stu-id="b96cb-133">Processing Analysis Services Objects</span></span>](../multidimensional-models/processing-analysis-services-objects.md)  
  
  
