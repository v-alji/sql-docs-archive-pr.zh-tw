---
title: Cube 物件 (Analysis Services 多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e6dfb75be696ab26893e668b99dc36c7340f86c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596943"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="db868-102">Cube 物件 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="db868-102">Cube Objects (Analysis Services - Multidimensional Data)</span></span>
    
## <a name="introducing-cube-objects"></a><span data-ttu-id="db868-103">Cube 物件簡介</span><span class="sxs-lookup"><span data-stu-id="db868-103">Introducing Cube Objects</span></span>  
 <span data-ttu-id="db868-104">簡單的 <xref:Microsoft.AnalysisServices.Cube> 物件是由以下項目所組成：基本資訊、維度和量值群組。</span><span class="sxs-lookup"><span data-stu-id="db868-104">A simple <xref:Microsoft.AnalysisServices.Cube> object is composed of: basic information, dimensions, and measure groups.</span></span> <span data-ttu-id="db868-105">基本資訊包括 Cube 的名稱、Cube 的預設量值、資料來源、儲存模式等等。</span><span class="sxs-lookup"><span data-stu-id="db868-105">Basic information includes the name of the cube, the default measure of the cube, the data source, the storage mode, and others.</span></span>  
  
 <span data-ttu-id="db868-106">Dimensions 集合包含在 Cube 中使用的一組來自資料庫維度集合的實際維度。</span><span class="sxs-lookup"><span data-stu-id="db868-106">The Dimensions collection contains the actual set of dimensions used in the cube from the database dimensions colection.</span></span> <span data-ttu-id="db868-107">所有維度都必須先定義在資料庫的維度集合中，才能在 Cube 中參考。</span><span class="sxs-lookup"><span data-stu-id="db868-107">All dimensions have to be defined in the dimensions collection of the database before being referenced in the cube.</span></span> <span data-ttu-id="db868-108">無法在中使用私用維度 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="db868-108">Private dimensions are not available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="db868-109">量值群組是 Cube 中的量值集合。</span><span class="sxs-lookup"><span data-stu-id="db868-109">Measure groups are sets of measures in the cube.</span></span> <span data-ttu-id="db868-110">量值群組是具有共同資料來源檢視及共同一組維度的量值集合。</span><span class="sxs-lookup"><span data-stu-id="db868-110">A measure group is a collection of measures that have a common data source view and a common set of dimensions.</span></span> <span data-ttu-id="db868-111">量值群組是量值的處理單位；量值群組可以個別處理，然後進行瀏覽。</span><span class="sxs-lookup"><span data-stu-id="db868-111">A measure group is the unit of process for measures; measure groups can be processed individually and then browsed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db868-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="db868-112">In this section</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db868-113">主題</span><span class="sxs-lookup"><span data-stu-id="db868-113">Topic</span></span>||  
|[<span data-ttu-id="db868-114">動作 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="db868-114">Actions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="db868-115">彙總和彙總設計</span><span class="sxs-lookup"><span data-stu-id="db868-115">Aggregations and Aggregation Designs</span></span>](aggregations-and-aggregation-designs.md)||  
|[<span data-ttu-id="db868-116">計算</span><span class="sxs-lookup"><span data-stu-id="db868-116">Calculations</span></span>](calculations.md)||  
|[<span data-ttu-id="db868-117">Cube 資料格 &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="db868-117">Cube Cells &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-cells-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="db868-118">Cube 屬性</span><span class="sxs-lookup"><span data-stu-id="db868-118">Cube Properties</span></span>](cube-properties-multidimensional-model-programming.md)||  
|[<span data-ttu-id="db868-119">Cube 儲存體 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="db868-119">Cube Storage &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-storage-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="db868-120">Cube 翻譯</span><span class="sxs-lookup"><span data-stu-id="db868-120">Cube Translations</span></span>](cube-translations.md)||  
|[<span data-ttu-id="db868-121">維度關聯性</span><span class="sxs-lookup"><span data-stu-id="db868-121">Dimension Relationships</span></span>](dimension-relationships.md)||  
|[<span data-ttu-id="db868-122">多維度模型中的關鍵效能指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="db868-122">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](../multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[<span data-ttu-id="db868-123">量值和量值群組</span><span class="sxs-lookup"><span data-stu-id="db868-123">Measures and Measure Groups</span></span>](../multidimensional-models/measures-and-measure-groups.md)||  
|[<span data-ttu-id="db868-124">資料分割 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="db868-124">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partitions-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="db868-125">檢視方塊</span><span class="sxs-lookup"><span data-stu-id="db868-125">Perspectives</span></span>](perspectives.md)||  
  
  
