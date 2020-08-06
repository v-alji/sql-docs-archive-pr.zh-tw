---
title: 空間資料 (SQL Server) | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4d491420a9eca7c35b89b254a03381c6467c834c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606156"
---
# <a name="spatial-data-sql-server"></a><span data-ttu-id="80ef3-102">空間資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="80ef3-102">Spatial Data (SQL Server)</span></span>
  <span data-ttu-id="80ef3-103">空間資料代表幾何物件的實體位置和圖形相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80ef3-103">Spatial data represents information about the physical location and shape of geometric objects.</span></span> <span data-ttu-id="80ef3-104">這些物件可以是點位置或更複雜的物件，例如國家/地區、道路或湖泊。</span><span class="sxs-lookup"><span data-stu-id="80ef3-104">These objects can be point locations or more complex objects such as countries, roads, or lakes.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="80ef3-105">支援兩種空間資料類型：`geometry` 資料類型和 `geography` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="80ef3-105">supports two spatial data types: the `geometry` data type and the `geography` data type.</span></span>  
  
-   <span data-ttu-id="80ef3-106"> 類型代表 Euclidean (平面) 座標系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="80ef3-106">The `geometry` type represents data in a Euclidean (flat) coordinate system.</span></span>  
  
-   <span data-ttu-id="80ef3-107"> 類型代表圓形表面座標系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="80ef3-107">The `geography` type represents data in a round-earth coordinate system.</span></span>  
  
 <span data-ttu-id="80ef3-108">這兩種資料類型都會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中實作為 .NET Common Language Runtime (CLR) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="80ef3-108">Both data types are implemented as .NET common language runtime (CLR) data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="80ef3-109">如需 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引進之空間功能的詳細描述和範例，請下載技術白皮書： [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407)(SQL Server 2012 的新空間功能)。</span><span class="sxs-lookup"><span data-stu-id="80ef3-109">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="80ef3-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="80ef3-110">Related Tasks</span></span>  
 [<span data-ttu-id="80ef3-111">建立、建構及查詢幾何執行個體</span><span class="sxs-lookup"><span data-stu-id="80ef3-111">Create, Construct, and Query geometry Instances</span></span>](create-construct-and-query-geometry-instances.md)  
 <span data-ttu-id="80ef3-112">描述可以與 geometry 資料類型執行個體搭配使用的方法。</span><span class="sxs-lookup"><span data-stu-id="80ef3-112">Describes the methods that you can use with instances of the geometry data type.</span></span>  
  
 [<span data-ttu-id="80ef3-113">建立、建構及查詢地理位置執行個體</span><span class="sxs-lookup"><span data-stu-id="80ef3-113">Create, Construct, and Query geography Instances</span></span>](create-construct-and-query-geography-instances.md)  
 <span data-ttu-id="80ef3-114">描述可以與 geography 資料類型執行個體搭配使用的方法。</span><span class="sxs-lookup"><span data-stu-id="80ef3-114">Describes the methods that you can use with instances of the geography data type.</span></span>  
  
 [<span data-ttu-id="80ef3-115">查詢最接近像素的空間資料</span><span class="sxs-lookup"><span data-stu-id="80ef3-115">Query Spatial Data for Nearest Neighbor</span></span>](query-spatial-data-for-nearest-neighbor.md)  
 <span data-ttu-id="80ef3-116">描述用以尋找最接近特定空間物件之空間物件的一般查詢模式。</span><span class="sxs-lookup"><span data-stu-id="80ef3-116">Describes the common query pattern that is used to find the closest spatial objects to a specific spatial object.</span></span>  
  
 [<span data-ttu-id="80ef3-117">建立、修改及卸除空間索引</span><span class="sxs-lookup"><span data-stu-id="80ef3-117">Create, Modify, and Drop Spatial Indexes</span></span>](create-modify-and-drop-spatial-indexes.md)  
 <span data-ttu-id="80ef3-118">提供有關建立、改變及卸除空間索引的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="80ef3-118">Provides information about creating, altering, and dropping a spatial index.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="80ef3-119">相關內容</span><span class="sxs-lookup"><span data-stu-id="80ef3-119">Related Content</span></span>  
 [<span data-ttu-id="80ef3-120">空間資料類型概觀</span><span class="sxs-lookup"><span data-stu-id="80ef3-120">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
 <span data-ttu-id="80ef3-121">介紹空間資料類型。</span><span class="sxs-lookup"><span data-stu-id="80ef3-121">Introduces the spatial data types.</span></span>  
  
-   [<span data-ttu-id="80ef3-122">點</span><span class="sxs-lookup"><span data-stu-id="80ef3-122">Point</span></span>](point.md)  
  
-   [<span data-ttu-id="80ef3-123">LineString</span><span class="sxs-lookup"><span data-stu-id="80ef3-123">LineString</span></span>](linestring.md)  
  
-   [<span data-ttu-id="80ef3-124">CircularString</span><span class="sxs-lookup"><span data-stu-id="80ef3-124">CircularString</span></span>](circularstring.md)  
  
-   [<span data-ttu-id="80ef3-125">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="80ef3-125">CompoundCurve</span></span>](compoundcurve.md)  
  
-   [<span data-ttu-id="80ef3-126">Polygon</span><span class="sxs-lookup"><span data-stu-id="80ef3-126">Polygon</span></span>](polygon.md)  
  
-   [<span data-ttu-id="80ef3-127">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="80ef3-127">CurvePolygon</span></span>](curvepolygon.md)  
  
-   [<span data-ttu-id="80ef3-128">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="80ef3-128">MultiPoint</span></span>](multipoint.md)  
  
-   [<span data-ttu-id="80ef3-129">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="80ef3-129">MultiLineString</span></span>](multilinestring.md)  
  
-   [<span data-ttu-id="80ef3-130">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="80ef3-130">MultiPolygon</span></span>](multipolygon.md)  
  
-   [<span data-ttu-id="80ef3-131">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="80ef3-131">GeometryCollection</span></span>](geometrycollection.md)  
  
 [<span data-ttu-id="80ef3-132">空間索引概觀</span><span class="sxs-lookup"><span data-stu-id="80ef3-132">Spatial Indexes Overview</span></span>](spatial-indexes-overview.md)  
 <span data-ttu-id="80ef3-133">介紹空間索引並描述鑲嵌和鑲嵌式配置。</span><span class="sxs-lookup"><span data-stu-id="80ef3-133">Introduces spatial indexes and describes tessellation and tessellation schemes.</span></span>  
  
  
