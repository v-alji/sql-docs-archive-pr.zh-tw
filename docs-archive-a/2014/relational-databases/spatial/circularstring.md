---
title: CircularString | Microsoft 文件
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c701cdc2e8538a5b91093e17714fd9f6508d1c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585809"
---
# <a name="circularstring"></a><span data-ttu-id="5e843-102">CircularString</span><span class="sxs-lookup"><span data-stu-id="5e843-102">CircularString</span></span>
  <span data-ttu-id="5e843-103">`CircularString` 是零個或多個連續圓弧線段的集合。</span><span class="sxs-lookup"><span data-stu-id="5e843-103">A `CircularString` is a collection of zero or more continuous circular arc segments.</span></span> <span data-ttu-id="5e843-104">圓弧線段是指由二維平面中三個點所定義的弧形線段。第一個點不得與第三個點相同。</span><span class="sxs-lookup"><span data-stu-id="5e843-104">A circular arc segment is a curved segment defined by three points in a two-dimensional plane; the first point cannot be the same as the third point.</span></span> <span data-ttu-id="5e843-105">如果圓弧線段的三個點都是共線，此圓弧線段就會被視為直線線段。</span><span class="sxs-lookup"><span data-stu-id="5e843-105">If all three points of a circular arc segment are collinear, the arc segment is treated as a line segment.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="5e843-106">如需中引進的新空間功能（包括子類型）的詳細描述和範例，請下載技術白皮書 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] `CircularString` ： [SQL Server 2012 中的新空間功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="5e843-106">For a detailed description and examples of the new spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including the `CircularString` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

## <a name="circularstring-instances"></a><span data-ttu-id="5e843-107">CircularString 執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-107">CircularString instances</span></span>
 <span data-ttu-id="5e843-108">下圖顯示有效的 `CircularString` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="5e843-108">The drawing below shows valid `CircularString` instances:</span></span>

 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")

### <a name="accepted-instances"></a><span data-ttu-id="5e843-109">已接受的執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-109">Accepted instances</span></span>
 <span data-ttu-id="5e843-110">`CircularString`如果實例是空的或包含奇數的點（n），其中 n > 1，則會接受實例。</span><span class="sxs-lookup"><span data-stu-id="5e843-110">A `CircularString` instance is accepted if it is either empty or contains an odd number of points, n, where n > 1.</span></span> <span data-ttu-id="5e843-111">下面是已接受的 `CircularString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5e843-111">The following `CircularString` instances are accepted.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';
```

 <span data-ttu-id="5e843-112">`@g3` 顯示 `CircularString` 執行個體可被系統接受但卻無效。</span><span class="sxs-lookup"><span data-stu-id="5e843-112">`@g3` shows that `CircularString` instance may be accepted, but not valid.</span></span> <span data-ttu-id="5e843-113">系統無法接受下列 CircularString 執行個體宣告。</span><span class="sxs-lookup"><span data-stu-id="5e843-113">The following CircularString instance declaration is not accepted.</span></span> <span data-ttu-id="5e843-114">這個宣告會擲回 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="5e843-114">This declaration throws a `System.FormatException`.</span></span>

```sql
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';
```

### <a name="valid-instances"></a><span data-ttu-id="5e843-115">有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-115">Valid instances</span></span>
 <span data-ttu-id="5e843-116">有效的 `CircularString` 執行個體必須是空的或具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5e843-116">A valid `CircularString` instance must be empty or have the following attributes:</span></span>

-   <span data-ttu-id="5e843-117">它至少必須包含一個圓弧弧線 (亦即，至少有三個點)。</span><span class="sxs-lookup"><span data-stu-id="5e843-117">It must contain at least one circular arc segment (that is, have a minimum of three points).</span></span>

-   <span data-ttu-id="5e843-118">序列中每個圓弧線段的最後一個端點 (最後一個線段除外) 必須是序列中下一個線段的第一個端點。</span><span class="sxs-lookup"><span data-stu-id="5e843-118">The last endpoint for each circular arc segment in the sequence, except for the last segment, must be the first endpoint for the next segment in the sequence.</span></span>

-   <span data-ttu-id="5e843-119">它必須有奇數點。</span><span class="sxs-lookup"><span data-stu-id="5e843-119">It must have an odd number of points.</span></span>

-   <span data-ttu-id="5e843-120">它本身不得在間隔上重疊。</span><span class="sxs-lookup"><span data-stu-id="5e843-120">It cannot overlap itself over an interval.</span></span>

-   <span data-ttu-id="5e843-121">雖然 `CircularString` 執行個體可包含直線線段，不過這些線段必須由三個共線點定義。</span><span class="sxs-lookup"><span data-stu-id="5e843-121">Although `CircularString` instances may contain line segments, these line segments must be defined by three collinear points.</span></span>

 <span data-ttu-id="5e843-122">下列範例會顯示有效的 `CircularString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5e843-122">The following example shows valid `CircularString` instances.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();
```

 <span data-ttu-id="5e843-123">`CircularString` 執行個體至少必須包含兩個圓弧線段，才能定義完整的圓形。</span><span class="sxs-lookup"><span data-stu-id="5e843-123">A `CircularString` instance must contain at least two circular arc segments to define a complete circle.</span></span> <span data-ttu-id="5e843-124">`CircularString` 執行個體無法使用單一圓弧線段 (例如 (1 1, 3 1, 1 1)) 來定義完整的圓形。</span><span class="sxs-lookup"><span data-stu-id="5e843-124">A `CircularString` instance cannot use a single circular arc segment (such as (1 1, 3 1, 1 1)) to define a complete circle.</span></span> <span data-ttu-id="5e843-125">您可以使用 (1 1, 2 2, 3 1, 2 0, 1 1) 來定義圓形。</span><span class="sxs-lookup"><span data-stu-id="5e843-125">Use (1 1, 2 2, 3 1, 2 0, 1 1) to define the circle.</span></span>

 <span data-ttu-id="5e843-126">下列範例會顯示無效的 CircularString 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5e843-126">The following example shows CircularString instances that are not valid.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

### <a name="instances-with-collinear-points"></a><span data-ttu-id="5e843-127">具有共線點的執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-127">Instances with collinear points</span></span>
 <span data-ttu-id="5e843-128">在下列情況中，圓弧線段會被視為直線線段：</span><span class="sxs-lookup"><span data-stu-id="5e843-128">In the following cases a circular arc segment will be treated as a line segment:</span></span>

-   <span data-ttu-id="5e843-129">當三個點都是共線 (例如 (1 3, 4 4, 7 5)) 時。</span><span class="sxs-lookup"><span data-stu-id="5e843-129">When all three points are collinear (for example, (1 3, 4 4, 7 5)).</span></span>

-   <span data-ttu-id="5e843-130">當第一個和中間點相同，但是第三個點不同 (例如 (1 3, 1 3, 7 5)) 時。</span><span class="sxs-lookup"><span data-stu-id="5e843-130">When the first and middle point are the same, but the third point is different (for example, (1 3, 1 3, 7 5)).</span></span>

-   <span data-ttu-id="5e843-131">當中間和最後一個點相同，但是第一個點不同 (例如 (1 3, 4 4, 4 4)) 時。</span><span class="sxs-lookup"><span data-stu-id="5e843-131">When the middle and last point are the same, but the first point is different (for example, (1 3, 4 4, 4 4)).</span></span>

## <a name="examples"></a><span data-ttu-id="5e843-132">範例</span><span class="sxs-lookup"><span data-stu-id="5e843-132">Examples</span></span>

### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a><span data-ttu-id="5e843-133">A.</span><span class="sxs-lookup"><span data-stu-id="5e843-133">A.</span></span> <span data-ttu-id="5e843-134">使用空的 CircularString 來具現化 Geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-134">Instantiating a Geometry Instance with an Empty CircularString</span></span>
 <span data-ttu-id="5e843-135">這個範例會示範如何建立空的 `CircularString` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="5e843-135">This example shows how to create an empty `CircularString` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');
```

### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a><span data-ttu-id="5e843-136">B.</span><span class="sxs-lookup"><span data-stu-id="5e843-136">B.</span></span> <span data-ttu-id="5e843-137">使用 CircularString 搭配一個圓弧線段來具現化 Geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-137">Instantiating a Geometry Instance Using a CircularString with One Circular Arc Segment</span></span>
 <span data-ttu-id="5e843-138">下列範例會示範如何建立具有單一圓弧線段 (半圓形) 的 `CircularString` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="5e843-138">The following example shows how to create a `CircularString` instance with a single circular arc segment (half-circle):</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);
SELECT @g.ToString();
```

### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a><span data-ttu-id="5e843-139">C.</span><span class="sxs-lookup"><span data-stu-id="5e843-139">C.</span></span> <span data-ttu-id="5e843-140">使用 CircularString 搭配多個圓弧線段來具現化 Geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-140">Instantiating a Geometry Instance Using a CircularString with Multiple Circular Arc Segments</span></span>
 <span data-ttu-id="5e843-141">下列範例會示範如何建立具有多個圓弧線段 (完整圓形) 的 `CircularString` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="5e843-141">The following example shows how to create a `CircularString` instance with more than one circular arc segment (full circle):</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```

 <span data-ttu-id="5e843-142">這會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5e843-142">This produces the following output:</span></span>

```
Circumference = 6.28319
```

 <span data-ttu-id="5e843-143">當您使用 `LineString` 而非 `CircularString` 時，請比較輸出：</span><span class="sxs-lookup"><span data-stu-id="5e843-143">Compare the output when `LineString` is used instead of `CircularString`:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));
```

 <span data-ttu-id="5e843-144">這會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5e843-144">This produces the following output:</span></span>

```
Perimeter = 5.65685
```

 <span data-ttu-id="5e843-145">請注意，此範例的值 `CircularString` 接近 2&#x03c0; (2 \* pi) ，這是圓形的實際圓周。</span><span class="sxs-lookup"><span data-stu-id="5e843-145">Notice that the value for the `CircularString` example is close to 2&#x03c0; (2 \* pi), which is the actual circumference of the circle.</span></span>

### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a><span data-ttu-id="5e843-146">D.</span><span class="sxs-lookup"><span data-stu-id="5e843-146">D.</span></span> <span data-ttu-id="5e843-147">在相同的陳述式中使用 CircularString 來宣告和具現化 Geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-147">Declaring and Instantiating a Geometry Instance with a CircularString in the Same Statement</span></span>
 <span data-ttu-id="5e843-148">這個程式碼片段會示範如何在相同的陳述式中使用 `geometry` 來宣告和具現化 `CircularString` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="5e843-148">This snippet shows how to declare and instantiate a `geometry` instance with a `CircularString` in the same statement:</span></span>

```sql
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';
```

### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a><span data-ttu-id="5e843-149">E.</span><span class="sxs-lookup"><span data-stu-id="5e843-149">E.</span></span> <span data-ttu-id="5e843-150">使用 CircularString 來具現化 Geography 執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-150">Instantiating a Geography Instance with a CircularString</span></span>
 <span data-ttu-id="5e843-151">下列範例會示範如何使用 `geography` 來宣告和具現化 `CircularString` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="5e843-151">The following example shows how to declare and instantiate a `geography` instance with a `CircularString`:</span></span>

```sql
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';
```

### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a><span data-ttu-id="5e843-152">F.</span><span class="sxs-lookup"><span data-stu-id="5e843-152">F.</span></span> <span data-ttu-id="5e843-153">使用直線的 CircularString 來具現化 Geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="5e843-153">Instantiating a Geometry Instance with a CircularString that is a Straight Line</span></span>
 <span data-ttu-id="5e843-154">下列範例會示範如何建立直線的 `CircularString` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="5e843-154">The following example shows how to create a `CircularString` instance that is a straight line:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);
```

## <a name="see-also"></a><span data-ttu-id="5e843-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e843-155">See Also</span></span>
 <span data-ttu-id="5e843-156">[空間資料類型總覽](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [MakeValid &#40;geography 資料類型&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [MakeValid &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [STIsValid &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STIsValid &#40;geography 資料類型&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STLength &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry 資料類型](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [&#41;STPointN &#40;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) geometry 資料類型[&#41;STNumPoints &#40;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [geometry 資料](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)型[別&#41;STIsRing](linestring.md) &#40;[geometry&#41;geometry](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)資料類型[&#40;STIsClosed](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)</span><span class="sxs-lookup"><span data-stu-id="5e843-156">[Spatial Data Types Overview](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [MakeValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [MakeValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STIsValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [LineString](linestring.md)</span></span>


