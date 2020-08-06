---
title: GeometryCollection | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 71d2234a9b73b7647554e364fe3864f089a47a0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606178"
---
# <a name="geometrycollection"></a><span data-ttu-id="e5aa7-102">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="e5aa7-102">GeometryCollection</span></span>
  <span data-ttu-id="e5aa7-103">`GeometryCollection` 是零或多個 `geometry` 或 `geography` 執行個體的集合。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-103">A `GeometryCollection` is a collection of zero or more `geometry` or `geography` instances.</span></span> <span data-ttu-id="e5aa7-104">`GeometryCollection` 可以是空的。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-104">A `GeometryCollection` can be empty.</span></span>  
  
## <a name="geometrycollection-instances"></a><span data-ttu-id="e5aa7-105">GeometryCollection 執行個體</span><span class="sxs-lookup"><span data-stu-id="e5aa7-105">GeometryCollection Instances</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="e5aa7-106">已接受的執行個體</span><span class="sxs-lookup"><span data-stu-id="e5aa7-106">Accepted Instances</span></span>  
 <span data-ttu-id="e5aa7-107">若要接受 `GeometryCollection` 執行個體，該執行個體必須是空的 `GeometryCollection` 執行個體，或者組成 `GeometryCollection` 執行個體的所有執行個體都必須是已接受的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-107">For a `GeometryCollection` instance to be accepted, it must either be an empty `GeometryCollection` instance or all the instances comprising the `GeometryCollection` instance must be accepted instances.</span></span> <span data-ttu-id="e5aa7-108">下列範例會顯示可接受的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-108">The following example shows accepted instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 <span data-ttu-id="e5aa7-109">下列範例會擲回 `System.FormatException`，因為不接受 `LinesString` 執行個體中的 `GeometryCollection` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-109">The following example throws a `System.FormatException` because the `LinesString` instance in the `GeometryCollection` instance is not accepted.</span></span>  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a><span data-ttu-id="e5aa7-110">有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="e5aa7-110">Valid Instances</span></span>  
 <span data-ttu-id="e5aa7-111">當組成 `GeometryCollection` 執行個體的所有執行個體都有效時，`GeometryCollection` 執行個體是有效的。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-111">A `GeometryCollection` instance is valid when all instances that comprise the `GeometryCollection` instance are valid.</span></span> <span data-ttu-id="e5aa7-112">下列範例示範三個有效的 `GeometryCollection` 執行個體和一個無效的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-112">The following shows three valid `GeometryCollection` instances and one instance that is not valid.</span></span>  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 <span data-ttu-id="e5aa7-113">`@g4` 無效，因為 `Polygon` 執行個體中的 `GeometryCollection` 執行個體無效。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-113">`@g4` is not valid because the `Polygon` instance in the `GeometryCollection` instance is not valid.</span></span>  
  
 <span data-ttu-id="e5aa7-114">如需可接受和有效執行個體的詳細資訊，請參閱＜ [Point](point.md)＞、＜ [MultiPoint](multipoint.md)＞、＜ [LineString](linestring.md)＞、＜ [MultiLineString](multilinestring.md)＞、＜ [Polygon](polygon.md)＞和＜ [MultiPolygon](multipolygon.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-114">For more information on accepted and valid instances, see [Point](point.md), [MultiPoint](multipoint.md), [LineString](linestring.md), [MultiLineString](multilinestring.md), [Polygon](polygon.md), and [MultiPolygon](multipolygon.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e5aa7-115">範例</span><span class="sxs-lookup"><span data-stu-id="e5aa7-115">Examples</span></span>  
 <span data-ttu-id="e5aa7-116">下列範例會具現化 `geometry``GeometryCollection` ，其中包含 SRID 1 中具有 `Point` 執行個體和 `Polygon` 執行個體的 Z 值。</span><span class="sxs-lookup"><span data-stu-id="e5aa7-116">The following example instantiates a `geometry``GeometryCollection` with Z values in SRID 1 containing a `Point` instance and a `Polygon` instance.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5aa7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5aa7-117">See Also</span></span>  
 [<span data-ttu-id="e5aa7-118">空間資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e5aa7-118">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
