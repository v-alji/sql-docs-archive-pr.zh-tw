---
title: 維度儲存體 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa68ebcfa8f4136bcd4a131842c852665ee9851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687314"
---
# <a name="dimension-storage"></a><span data-ttu-id="dc00b-102">維度儲存</span><span class="sxs-lookup"><span data-stu-id="dc00b-102">Dimension Storage</span></span>
  <span data-ttu-id="dc00b-103">中的維度 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支援兩種儲存模式：</span><span class="sxs-lookup"><span data-stu-id="dc00b-103">Dimensions in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] support two storage modes:</span></span>  
  
-   <span data-ttu-id="dc00b-104">關聯式 OLAP (ROLAP)</span><span class="sxs-lookup"><span data-stu-id="dc00b-104">Relational OLAP (ROLAP)</span></span>  
  
-   <span data-ttu-id="dc00b-105">多維度 OLAP (MOLAP)</span><span class="sxs-lookup"><span data-stu-id="dc00b-105">Multidimensional OLAP (MOLAP)</span></span>  
  
 <span data-ttu-id="dc00b-106">儲存模式決定維度之資料的位置和形式。</span><span class="sxs-lookup"><span data-stu-id="dc00b-106">The storage mode determines the location and form of a dimension's data.</span></span> <span data-ttu-id="dc00b-107">維度的預設儲存模式為 MOLAP。</span><span class="sxs-lookup"><span data-stu-id="dc00b-107">MOLAP is the default storage mode for dimensions.</span></span> <span data-ttu-id="dc00b-108">**相關主題：** 資料[分割儲存模式和處理](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)</span><span class="sxs-lookup"><span data-stu-id="dc00b-108">**Related topics:**[Partition Storage Modes and Processing](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)</span></span>  
  
## <a name="molap"></a><span data-ttu-id="dc00b-109">MOLAP</span><span class="sxs-lookup"><span data-stu-id="dc00b-109">MOLAP</span></span>  
 <span data-ttu-id="dc00b-110">使用 MOLAP 的維度資料，會儲存在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的多維度結構中。</span><span class="sxs-lookup"><span data-stu-id="dc00b-110">Data for a dimension that uses MOLAP is stored in a multidimensional structure in the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="dc00b-111">在處理維度時，會建立及擴展這種多維度結構。</span><span class="sxs-lookup"><span data-stu-id="dc00b-111">This multidimensional structure is created and populated when the dimension is processed.</span></span> <span data-ttu-id="dc00b-112">MOLAP 維度提供比 ROLAP 維度更好的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="dc00b-112">MOLAP dimensions provide better query performance than ROLAP dimensions.</span></span>  
  
## <a name="rolap"></a><span data-ttu-id="dc00b-113">ROLAP</span><span class="sxs-lookup"><span data-stu-id="dc00b-113">ROLAP</span></span>  
 <span data-ttu-id="dc00b-114">使用 ROLAP 的維度資料，實際上是儲存在用來定義該維度的資料表中。</span><span class="sxs-lookup"><span data-stu-id="dc00b-114">Data for a dimension that uses ROLAP is actually stored in the tables used to define the dimension.</span></span> <span data-ttu-id="dc00b-115">ROLAP 儲存模式可用於在不複製大量資料的情況下支援大型維度，但需要犧牲查詢效能。</span><span class="sxs-lookup"><span data-stu-id="dc00b-115">The ROLAP storage mode can be used to support large dimensions without duplicating large amounts of data, but at the expense of query performance.</span></span> <span data-ttu-id="dc00b-116">因為維度會直接依賴用來定義該維度之資料來源檢視中的資料表，所以 ROLAP 儲存模式也可以支援即時 OLAP。</span><span class="sxs-lookup"><span data-stu-id="dc00b-116">Because the dimension relies directly on the tables in the data source view used to define the dimension, the ROLAP storage mode also supports real-time OLAP.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dc00b-117">如果維度使用 ROLAP 儲存模式，而且該維度包含在使用 MOLAP 儲存的 Cube 中，則對於其來源資料表進行任何結構描述變更之後，必須立即處理此 Cube。</span><span class="sxs-lookup"><span data-stu-id="dc00b-117">If a dimension uses the ROLAP storage mode and the dimension is included in a cube that uses MOLAP storage, any schema changes to its source table must be followed by immediate processing of the cube.</span></span> <span data-ttu-id="dc00b-118">如果沒有這樣做，則在查詢 Cube 時，可能會產生不一致的結果。</span><span class="sxs-lookup"><span data-stu-id="dc00b-118">Failure to do this may result in inconsistent results when querying the cube.</span></span> <span data-ttu-id="dc00b-119">**相關主題：**[使用 SSIS 將 Analysis Services 管理工作自動化](../instances/automate-analysis-services-administrative-tasks-with-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="dc00b-119">**Related topic:**[Automate Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc00b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc00b-120">See Also</span></span>  
 [<span data-ttu-id="dc00b-121">資料分割儲存模式及處理</span><span class="sxs-lookup"><span data-stu-id="dc00b-121">Partition Storage Modes and Processing</span></span>](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
