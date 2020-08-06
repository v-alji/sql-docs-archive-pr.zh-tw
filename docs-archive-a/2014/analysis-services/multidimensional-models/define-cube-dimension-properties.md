---
title: 定義 Cube 維度屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c58cf6a2f55e57c9faa65ddec72fe1bda6000c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585637"
---
# <a name="define-cube-dimension-properties"></a><span data-ttu-id="9f0ec-102">定義 Cube 維度屬性</span><span class="sxs-lookup"><span data-stu-id="9f0ec-102">Define Cube Dimension Properties</span></span>
  <span data-ttu-id="9f0ec-103">Cube 維度是 Cube 內之資料庫維度的一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-103">A cube dimension is an instance of a database dimension within a cube.</span></span> <span data-ttu-id="9f0ec-104">資料庫維度可用於多個 Cube 中，而多個 Cube 維度的基礎是單一資料庫維度。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-104">A database dimension can be used in multiple cubes, and multiple cube dimensions can be based on a single database dimension.</span></span> <span data-ttu-id="9f0ec-105">下表描述 Cube 維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-105">The following table describes the properties of a cube dimension.</span></span>  
  
|<span data-ttu-id="9f0ec-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9f0ec-106">Property</span></span>|<span data-ttu-id="9f0ec-107">描述</span><span class="sxs-lookup"><span data-stu-id="9f0ec-107">Description</span></span>|  
|--------------|-----------------|  
|`AllMemberAggregationUsage`|<span data-ttu-id="9f0ec-108">控制匯總設計師在中的設計方式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-108">Controls how aggregations are designed by the Aggregation Designer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9f0ec-109">此屬性可以有下列的值：</span><span class="sxs-lookup"><span data-stu-id="9f0ec-109">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="9f0ec-110">**完整**：Cube 的每個彙總必須包含「全部」成員。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-110">**Full**: Every aggregation for the cube must include the All member.</span></span><br /><br /> <span data-ttu-id="9f0ec-111">**無**：Cube 的彙總都不可包含全部」成員。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-111">**None**: No aggregation for the cube can include the All member.</span></span> <span data-ttu-id="9f0ec-112">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-112">This is the default value.</span></span><br /><br /> <span data-ttu-id="9f0ec-113">**不受限制**：彙總設計師沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-113">**Unrestricted**: No restrictions are placed on the Aggregation Designer.</span></span><br /><br /> <span data-ttu-id="9f0ec-114">**預設**：與 [不受限制] 的功能相同。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-114">**Default**: The same functionality as Unrestricted.</span></span>|  
|`Description`|<span data-ttu-id="9f0ec-115">提供層級的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-115">Provides a descriptive name for the level.</span></span>|  
|`DimensionID`|<span data-ttu-id="9f0ec-116">包含資料庫維度的唯一識別碼 (ID)。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-116">Contains the unique identifier (ID) of the database dimension.</span></span>|  
|`HierarchyUniqueNameStyle`|<span data-ttu-id="9f0ec-117">決定如何為 Cube 維度內所包含的階層產生唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-117">Determines how unique names are generated for hierarchies that are contained within the cube dimension.</span></span> <span data-ttu-id="9f0ec-118">此屬性可以有下列的值：</span><span class="sxs-lookup"><span data-stu-id="9f0ec-118">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="9f0ec-119">`IncludeDimensionName`：階層之名稱中包含維度的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-119">`IncludeDimensionName`: The name of the dimension is included as part of the name of the hierarchy.</span></span> <span data-ttu-id="9f0ec-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-120">This is the default value.</span></span><br /><br /> <span data-ttu-id="9f0ec-121">`ExcludeDimensionName`：階層之名稱中不包含維度的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-121">`ExcludeDimensionName`: The name of the dimension is not included as part of the name of the hierarchy.</span></span>|  
|`ID`|<span data-ttu-id="9f0ec-122">包含 Cube 維度的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-122">Contains the unique identifier of the cube dimension.</span></span>|  
|`MemberUniqueNameStyle`|<span data-ttu-id="9f0ec-123">決定如何為 Cube 維度內所包含之階層的成員，產生唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-123">Determines how unique names are generated for members of hierarchies contained within the cube dimension.</span></span> <span data-ttu-id="9f0ec-124">此屬性可以有下列的值：</span><span class="sxs-lookup"><span data-stu-id="9f0ec-124">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="9f0ec-125">`Native`：[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會自動決定成員的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-125">`Native`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] automatically determines the unique names of members.</span></span> <span data-ttu-id="9f0ec-126">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-126">This is the default value.</span></span><br /><br /> <span data-ttu-id="9f0ec-127">`NamePath`：[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會產生複合名稱，而這個名稱是由成員之每個層級的名稱和標題所組成。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-127">`NamePath`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generates a compound name consisting of the name of each level and the caption of the member.</span></span>|  
|`Name`|<span data-ttu-id="9f0ec-128">包含 Cube 維度的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-128">Contains the friendly name of the cube dimension.</span></span> <span data-ttu-id="9f0ec-129">依預設，除非已經定義了相同名稱的其他 Cube 維度，否則 Cube 維度的名稱與資料庫維度的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-129">By default, the name of a cube dimension is the same as the name of the database dimension, unless another cube dimension of the same name is already defined.</span></span>|  
|`Visible`|<span data-ttu-id="9f0ec-130">決定 Cube 維度是否可見。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-130">Determines whether the cube dimension is visible.</span></span> <span data-ttu-id="9f0ec-131">預設值是 `True`。</span><span class="sxs-lookup"><span data-stu-id="9f0ec-131">The default value is `True`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f0ec-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f0ec-132">See Also</span></span>  
 [<span data-ttu-id="9f0ec-133">維度 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="9f0ec-133">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
