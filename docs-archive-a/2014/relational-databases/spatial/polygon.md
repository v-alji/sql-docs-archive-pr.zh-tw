---
title: Polygon | Microsoft Docs
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 040bb8a2558cc57b1b99a3ce984bec3c8925bc0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606160"
---
# <a name="polygon"></a><span data-ttu-id="14a06-102">Polygon</span><span class="sxs-lookup"><span data-stu-id="14a06-102">Polygon</span></span>
  <span data-ttu-id="14a06-103">`Polygon` 是儲存為一連串點的二維度介面，這些點可定義一個外部週框環形以及零個或多個內部環形。</span><span class="sxs-lookup"><span data-stu-id="14a06-103">A `Polygon` is a two-dimensional surface stored as a sequence of points defining an exterior bounding ring and zero or more interior rings.</span></span>

## <a name="polygon-instances"></a><span data-ttu-id="14a06-104">Polygon 執行個體</span><span class="sxs-lookup"><span data-stu-id="14a06-104">Polygon instances</span></span>
 <span data-ttu-id="14a06-105">`Polygon` 執行個體可以從環形組成 (此環形至少有三個相異點)。</span><span class="sxs-lookup"><span data-stu-id="14a06-105">A `Polygon` instance can be formed from a ring that has at least three distinct points.</span></span> <span data-ttu-id="14a06-106">`Polygon` 執行個體也可以是空的。</span><span class="sxs-lookup"><span data-stu-id="14a06-106">A `Polygon` instance can also be empty.</span></span>

 <span data-ttu-id="14a06-107">`Polygon` 的外部和任何內部環形定義了它的界限。</span><span class="sxs-lookup"><span data-stu-id="14a06-107">The exterior and any interior rings of a `Polygon` define its boundary.</span></span> <span data-ttu-id="14a06-108">此環形內的空間定義了 `Polygon` 的內部。</span><span class="sxs-lookup"><span data-stu-id="14a06-108">The space within the rings defines the interior of the `Polygon`.</span></span>

 <span data-ttu-id="14a06-109">下圖顯示 `Polygon` 執行個體的範例。</span><span class="sxs-lookup"><span data-stu-id="14a06-109">The illustration below shows examples of `Polygon` instances.</span></span>

 <span data-ttu-id="14a06-110">![幾何多邊形執行個體的範例](../../database-engine/media/polygon.gif "幾何多邊形執行個體的範例")</span><span class="sxs-lookup"><span data-stu-id="14a06-110">![Examples of geometry Polygon instances](../../database-engine/media/polygon.gif "Examples of geometry Polygon instances")</span></span>

 <span data-ttu-id="14a06-111">如本圖所示：</span><span class="sxs-lookup"><span data-stu-id="14a06-111">As shown in the illustration:</span></span>

1.  <span data-ttu-id="14a06-112">圖 1 是 `Polygon` 執行個體，其界限是由外部環形所定義。</span><span class="sxs-lookup"><span data-stu-id="14a06-112">Figure 1 is a `Polygon` instance whose boundary is defined by an exterior ring.</span></span>

2.  <span data-ttu-id="14a06-113">圖 2 是 `Polygon` 執行個體，其界限是由一個外部環形和兩個內部環形所定義。</span><span class="sxs-lookup"><span data-stu-id="14a06-113">Figure 2 is a `Polygon` instance whose boundary is defined by an exterior ring and two interior rings.</span></span> <span data-ttu-id="14a06-114">內部環形內的區域是 `Polygon` 執行個體外部的一部分。</span><span class="sxs-lookup"><span data-stu-id="14a06-114">The area inside the interior rings is part of the exterior of the `Polygon` instance.</span></span>

3.  <span data-ttu-id="14a06-115">圖 3 是有效的 `Polygon` 執行個體，因為它的內部環形會在單一正切點上相交。</span><span class="sxs-lookup"><span data-stu-id="14a06-115">Figure 3 is a valid `Polygon` instance because its interior rings intersect at a single tangent point.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="14a06-116">已接受的執行個體</span><span class="sxs-lookup"><span data-stu-id="14a06-116">Accepted instances</span></span>
 <span data-ttu-id="14a06-117">已接受的 `Polygon` 執行個體是指可儲存在 `geometry` 或 `geography` 變數中而不會擲回例外狀況的執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-117">Accepted `Polygon` instances are instances that can be stored in a `geometry` or `geography` variable without throwing an exception.</span></span> <span data-ttu-id="14a06-118">已接受的 `Polygon` 執行個體如下：</span><span class="sxs-lookup"><span data-stu-id="14a06-118">The following are accepted `Polygon` instances:</span></span>

-   <span data-ttu-id="14a06-119">空的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-119">An Empty `Polygon` instance</span></span>

-   <span data-ttu-id="14a06-120">具有可接受之外部環形以及零或多個可接受之內部環形的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-120">A `Polygon` instance that has an acceptable exterior ring and zero or more acceptable interior rings</span></span>

 <span data-ttu-id="14a06-121">要讓環形成為可接受環形所需的準則如下。</span><span class="sxs-lookup"><span data-stu-id="14a06-121">The following criteria are needed for a ring to be acceptable.</span></span>

-   <span data-ttu-id="14a06-122">系統必須接受 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-122">The `LineString` instance must be accepted.</span></span>

-   <span data-ttu-id="14a06-123">`LineString` 執行個體至少必須具有四個點。</span><span class="sxs-lookup"><span data-stu-id="14a06-123">The `LineString` instance must have at least four points.</span></span>

-   <span data-ttu-id="14a06-124">`LineString` 執行個體的開始和結束點必須相同。</span><span class="sxs-lookup"><span data-stu-id="14a06-124">The starting and ending points of the `LineString` instance must be the same.</span></span>

 <span data-ttu-id="14a06-125">下列範例會顯示已接受的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-125">The following example shows accepted `Polygon` instances.</span></span>

```
DECLARE @g1 geometry = 'POLYGON EMPTY';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
```

 <span data-ttu-id="14a06-126">如 `@g4` 和 `@g5` 所示，已接受的 `Polygon` 執行個體可能不是有效的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-126">As `@g4` and `@g5` show an accepted `Polygon` instance may not be a valid `Polygon` instance.</span></span> <span data-ttu-id="14a06-127">`@g5` 也會顯示 Polygon 執行個體必須只包含具有任何四個點的環形才能被接受。</span><span class="sxs-lookup"><span data-stu-id="14a06-127">`@g5` also shows that a Polygon instance needs to only contain a ring with any four points to be accepted.</span></span>

 <span data-ttu-id="14a06-128">下列範例會擲回 `System.FormatException`，因為系統不接受 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-128">The following examples throw a `System.FormatException` because the `Polygon` instances are not accepted.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';
```

 <span data-ttu-id="14a06-129">不接受 `@g1`，因為外部環形的 `LineString` 執行個體未包含足夠的點。</span><span class="sxs-lookup"><span data-stu-id="14a06-129">`@g1` is not accepted because the `LineString` instance for the exterior ring does not contain enough points.</span></span> <span data-ttu-id="14a06-130">不接受 `@g2`，因為外部環形 `LineString` 執行個體的起點與終點不相同。</span><span class="sxs-lookup"><span data-stu-id="14a06-130">`@g2` is not accepted because the starting point of the exterior ring `LineString` instance is not the same as the ending point.</span></span> <span data-ttu-id="14a06-131">下列範例具有可接受的外部環形，但是內部環形不是可接受的環形。</span><span class="sxs-lookup"><span data-stu-id="14a06-131">The following example has an acceptable exterior ring, but the interior ring is not acceptable.</span></span> <span data-ttu-id="14a06-132">這也會擲回 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="14a06-132">This also throws a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';
```

### <a name="valid-instances"></a><span data-ttu-id="14a06-133">有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="14a06-133">Valid instances</span></span>
 <span data-ttu-id="14a06-134">`Polygon` 的內部環形可以在單一正切點上接觸其本身及彼此接觸，但是如果 `Polygon` 的內部環形相交，此執行個體就會無效。</span><span class="sxs-lookup"><span data-stu-id="14a06-134">The interior rings of a `Polygon` can touch both themselves and each other at single tangent points, but if the interior rings of a `Polygon` cross, the instance is not valid.</span></span>

 <span data-ttu-id="14a06-135">下列範例會顯示有效的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-135">The following example shows valid `Polygon` instances.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="14a06-136">`@g3` 有效，因為這兩個內部環形在單一點接觸，而且沒有彼此相交。</span><span class="sxs-lookup"><span data-stu-id="14a06-136">`@g3` is valid because the two interior rings touch at a single point and do not cross each other.</span></span> <span data-ttu-id="14a06-137">下列範例會顯示無效的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-137">The following example shows `Polygon` instances that are not valid.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();
```

 <span data-ttu-id="14a06-138">`@g1` 無效，因為內部環形與外部環形有兩個接觸點。</span><span class="sxs-lookup"><span data-stu-id="14a06-138">`@g1` is not valid because the inner ring touches the exterior ring in two places.</span></span> <span data-ttu-id="14a06-139">`@g2` 無效，因為第二個內部環形位於第一個內部環形的內部。</span><span class="sxs-lookup"><span data-stu-id="14a06-139">`@g2` is not valid because the second inner ring in within the interior of the first inner ring.</span></span> <span data-ttu-id="14a06-140">`@g3` 無效，因為兩個內部環形有多個連續接觸點。</span><span class="sxs-lookup"><span data-stu-id="14a06-140">`@g3` is not valid because the two inner rings touch at multiple consecutive points.</span></span> <span data-ttu-id="14a06-141">`@g4` 無效，因為兩個內部環形的內部互相重疊。</span><span class="sxs-lookup"><span data-stu-id="14a06-141">`@g4` is not valid because the interiors of the two inner rings overlap.</span></span> <span data-ttu-id="14a06-142">`@g5` 無效，因為內部環形不是第一個環形。</span><span class="sxs-lookup"><span data-stu-id="14a06-142">`@g5` is not valid because the exterior ring is not the first ring.</span></span> <span data-ttu-id="14a06-143">`@g6` 無效，因為環形並未包含至少三個不同的點。</span><span class="sxs-lookup"><span data-stu-id="14a06-143">`@g6` is not valid because the ring does not have at least three distinct points.</span></span>

## <a name="examples"></a><span data-ttu-id="14a06-144">範例</span><span class="sxs-lookup"><span data-stu-id="14a06-144">Examples</span></span>
 <span data-ttu-id="14a06-145">下列範例會建立包含一個洞及 SRID 10 的簡單 `geometry``Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-145">The following example creates a simple `geometry``Polygon` instance with a hole and SRID 10.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STPolyFromText('POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))', 10);
```

 <span data-ttu-id="14a06-146">可輸入無效的執行個體，並將它轉換成有效的 `geometry` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14a06-146">Aninstance that is not valid may be entered and converted to a valid `geometry` instance.</span></span> <span data-ttu-id="14a06-147">在下列 `Polygon`範例中，內部和外部環形會重疊，而且此執行個體無效。</span><span class="sxs-lookup"><span data-stu-id="14a06-147">In the following example of a `Polygon`, the interior and exterior rings overlap and the instance is not valid.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))');
```

 <span data-ttu-id="14a06-148">在下列範例中，會使用 `MakeValid()`讓無效的執行個體變成有效。</span><span class="sxs-lookup"><span data-stu-id="14a06-148">In the following example, the invalid instance is made valid with `MakeValid()`.</span></span>

```
SET @g = @g.MakeValid();
SELECT @g.ToString();
```

 <span data-ttu-id="14a06-149">上述範例傳回的 `geometry` 執行個體是 `MultiPolygon`。</span><span class="sxs-lookup"><span data-stu-id="14a06-149">The `geometry` instance returned from the above example is a `MultiPolygon`.</span></span>

```
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)), ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))
```

 <span data-ttu-id="14a06-150">下面是另一個將無效執行個體轉換成有效 geometry 執行個體的範例。</span><span class="sxs-lookup"><span data-stu-id="14a06-150">Here is another example of converting an invalid instance to a valid geometry instance.</span></span> <span data-ttu-id="14a06-151">在下列範例中，我們已經使用三個完全相同的點來建立 `Polygon` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="14a06-151">In the following example the `Polygon` instance has been created using three points that are exactly the same:</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');
SET @g = @g.MakeValid();
SELECT @g.ToString()
```

 <span data-ttu-id="14a06-152">上述傳回的 geometry 執行個體是 `Point(1 3)`。</span><span class="sxs-lookup"><span data-stu-id="14a06-152">The geometry instance returned above is a `Point(1 3)`.</span></span>  <span data-ttu-id="14a06-153">如果給定的 `Polygon` 為 `POLYGON((1 3, 1 5, 1 3, 1 3))` ，則 `MakeValid()` 就會傳回 `LINESTRING(1 3, 1 5)`。</span><span class="sxs-lookup"><span data-stu-id="14a06-153">If the `Polygon` given is `POLYGON((1 3, 1 5, 1 3, 1 3))` then `MakeValid()` would return `LINESTRING(1 3, 1 5)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="14a06-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14a06-154">See Also</span></span>
 <span data-ttu-id="14a06-155">[STArea &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) [STNumInteriorRing &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) [STInteriorRingN &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) [STCentroid &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [MultiPolygon](../spatial/polygon.md) [空間資料 &#40;SQL Server](../spatial/spatial-data-sql-server.md)&#41;[STIsValid &#40;geography 資料類型&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STIsValid &#40;geometry 資料類型](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)&#41;</span><span class="sxs-lookup"><span data-stu-id="14a06-155">[STArea &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) [STNumInteriorRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) [STInteriorRingN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) [STCentroid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [MultiPolygon](../spatial/polygon.md) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [STIsValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)</span></span>


