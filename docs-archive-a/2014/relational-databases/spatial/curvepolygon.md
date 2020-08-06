---
title: CurvePolygon | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e000a1d8-a049-4542-bfeb-943fd6ab3969
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b90fdbd9a0bc80dfc6a82416d0193b2951fe13ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585802"
---
# <a name="curvepolygon"></a><span data-ttu-id="0454d-102">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="0454d-102">CurvePolygon</span></span>
  <span data-ttu-id="0454d-103">`CurvePolygon` 是由一個外部週框環形以及零或多個內部環形所定義的拓撲封閉介面。</span><span class="sxs-lookup"><span data-stu-id="0454d-103">A `CurvePolygon` is a topologically closed surface defined by an exterior bounding ring and zero or more interior rings</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0454d-104">如需中引進的空間功能（包括子類型）的詳細描述和範例，請下載技術白皮書 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] `CurvePolygon` ： [SQL Server 2012 中的新空間功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="0454d-104">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including the `CurvePolygon` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
 <span data-ttu-id="0454d-105">下列準則會定義實例的屬性 `CurvePolygon` ：</span><span class="sxs-lookup"><span data-stu-id="0454d-105">The following criteria define attributes of a `CurvePolygon` instance:</span></span>  
  
-   <span data-ttu-id="0454d-106">`CurvePolygon` 執行個體的界限是由外部環形和所有內部環形所定義。</span><span class="sxs-lookup"><span data-stu-id="0454d-106">The boundary of the `CurvePolygon` instance is defined by the exterior ring and all interior rings.</span></span>  
  
-   <span data-ttu-id="0454d-107"> 執行個體的內部是外部環形與所有內部環形之間的空間。</span><span class="sxs-lookup"><span data-stu-id="0454d-107">The interior of the `CurvePolygon` instance is the space between the exterior ring and all of the interior rings.</span></span>  
  
 <span data-ttu-id="0454d-108"> 執行個體與  執行個體不同之處在於， 執行個體可能會包含下列圓弧線段： 和 。</span><span class="sxs-lookup"><span data-stu-id="0454d-108">A `CurvePolygon` instance differs from a `Polygon` instance in that a `CurvePolygon` instance may contain the following circular arc segments: `CircularString` and `CompoundCurve`.</span></span>  
  
## <a name="compoundcurve-instances"></a><span data-ttu-id="0454d-109">CompoundCurve 執行個體</span><span class="sxs-lookup"><span data-stu-id="0454d-109">CompoundCurve instances</span></span>  
 <span data-ttu-id="0454d-110">下圖顯示了有效的 `CurvePolygon` 圖形：</span><span class="sxs-lookup"><span data-stu-id="0454d-110">Illustration below shows valid `CurvePolygon` figures:</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="0454d-111">已接受的執行個體</span><span class="sxs-lookup"><span data-stu-id="0454d-111">Accepted instances</span></span>  
 <span data-ttu-id="0454d-112">若要讓系統接受 `CurvePolygon` 執行個體，它必須是空的，或僅包含已接受的圓弧環形。</span><span class="sxs-lookup"><span data-stu-id="0454d-112">For a `CurvePolygon` instance to be accepted, it needs to be either empty or contain only circular arc rings that are accepted.</span></span> <span data-ttu-id="0454d-113">已接受的圓弧環形符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="0454d-113">An accepted circular arc ring meets the following requirements.</span></span>  
  
1.  <span data-ttu-id="0454d-114">是已接受的 `LineString`、`CircularString` 或 `CompoundCurve` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0454d-114">Is an accepted `LineString`, `CircularString`, or `CompoundCurve` instance.</span></span> <span data-ttu-id="0454d-115">如需有關已接受之執行個體的詳細資訊，請參閱 [LineString](linestring.md)、 [CircularString](circularstring.md)，和 [CompoundCurve](compoundcurve.md)。</span><span class="sxs-lookup"><span data-stu-id="0454d-115">For more information on accepted instances, see [LineString](linestring.md), [CircularString](circularstring.md), and [CompoundCurve](compoundcurve.md).</span></span>  
  
2.  <span data-ttu-id="0454d-116">至少具有四個點。</span><span class="sxs-lookup"><span data-stu-id="0454d-116">Has at least four points.</span></span>  
  
3.  <span data-ttu-id="0454d-117">開始和結束點都具有相同的 X 和 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="0454d-117">The start and end point have the same X and Y coordinates.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0454d-118">已忽略 Z 和 M 值。</span><span class="sxs-lookup"><span data-stu-id="0454d-118">Z and M values are ignored.</span></span>  
  
 <span data-ttu-id="0454d-119">下列範例會顯示已接受的 `CurvePolygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0454d-119">The following example shows accepted `CurvePolygon` instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0, 0 0))';  
DECLARE @g3 geometry = 'CURVEPOLYGON((0 0 1, 0 0 2, 0 0 3, 0 0 3))'  
DECLARE @g4 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
DECLARE @g5 geography = 'CURVEPOLYGON((-122.3 47, 122.3 -47, 125.7 -49, 121 -38, -122.3 47))';  
```  
  
 <span data-ttu-id="0454d-120">`@g3` 即使起點和終點的 Z 值不同仍會接受，因為會忽略 Z 值。</span><span class="sxs-lookup"><span data-stu-id="0454d-120">`@g3` is accepted even though the start and end points have different Z values because Z values are ignored.</span></span> <span data-ttu-id="0454d-121">即使 `geography` 類型執行個體無效，仍會接受 `@g5`。</span><span class="sxs-lookup"><span data-stu-id="0454d-121">`@g5` is accepted even though the `geography` type instance is not valid.</span></span>  
  
 <span data-ttu-id="0454d-122">下列範例會擲回 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="0454d-122">The following examples throw `System.FormatException`.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON((0 5, 0 0, 0 0, 0 0))';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0))';  
```  
  
 <span data-ttu-id="0454d-123">`@g1` 不被接受，因為起點和終點的 Y 值不相同。</span><span class="sxs-lookup"><span data-stu-id="0454d-123">`@g1` is not accepted because the start and end points do not have the same Y value.</span></span> <span data-ttu-id="0454d-124">`@g2` 不被接受，因為環形未包含足夠的點。</span><span class="sxs-lookup"><span data-stu-id="0454d-124">`@g2` is not accepted because the ring does not have enough points.</span></span>  
  
### <a name="valid-instances"></a><span data-ttu-id="0454d-125">有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="0454d-125">Valid instances</span></span>  
 <span data-ttu-id="0454d-126">若要讓 `CurvePolygon` 執行個體有效，外部與內部環形都必須符合下列準則：</span><span class="sxs-lookup"><span data-stu-id="0454d-126">For a `CurvePolygon` instance to be valid both exterior and interior rings must meet the following criteria:</span></span>  
  
1.  <span data-ttu-id="0454d-127">它們只能在單一正切點接觸。</span><span class="sxs-lookup"><span data-stu-id="0454d-127">They may only touch at single tangent points.</span></span>  
  
2.  <span data-ttu-id="0454d-128">它們不得彼此相交。</span><span class="sxs-lookup"><span data-stu-id="0454d-128">They cannot cross each other.</span></span>  
  
3.  <span data-ttu-id="0454d-129">每個環形至少必須包含四個點。</span><span class="sxs-lookup"><span data-stu-id="0454d-129">Each ring must contain at least four points.</span></span>  
  
4.  <span data-ttu-id="0454d-130">每個環形都必須是可接受的曲線類型。</span><span class="sxs-lookup"><span data-stu-id="0454d-130">Each ring must be an acceptable curve type.</span></span>  
  
 <span data-ttu-id="0454d-131">根據 `CurvePolygon` 執行個體是 `geometry` 或 `geography` 資料類型而定，它們也必須符合特定準則。</span><span class="sxs-lookup"><span data-stu-id="0454d-131">`CurvePolygon` instances also need to meet specific criteria depending on whether they are `geometry` or `geography` data types.</span></span>  
  
#### <a name="geometry-data-type"></a><span data-ttu-id="0454d-132">Geometry 資料類型</span><span class="sxs-lookup"><span data-stu-id="0454d-132">Geometry data type</span></span>  
 <span data-ttu-id="0454d-133">有效的 **geometryCurvePolygon** 執行個體必須具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0454d-133">A valid **geometryCurvePolygon** instance must have the following attributes:</span></span>  
  
1.  <span data-ttu-id="0454d-134">所有內部環形都必須包含在外部環形中。</span><span class="sxs-lookup"><span data-stu-id="0454d-134">All the interior rings must be contained within the exterior ring.</span></span>  
  
2.  <span data-ttu-id="0454d-135">可以具有多個內部環形，但是某個內部環形不得包含另一個內部環形。</span><span class="sxs-lookup"><span data-stu-id="0454d-135">May have multiple interior rings, but an interior ring cannot contain another interior ring.</span></span>  
  
3.  <span data-ttu-id="0454d-136">所有環形都不得跨越它本身或其他環形。</span><span class="sxs-lookup"><span data-stu-id="0454d-136">No ring can cross itself or another ring.</span></span>  
  
4.  <span data-ttu-id="0454d-137">環形只能在單一正切點接觸 (環形接觸的點數必須是有限的)。</span><span class="sxs-lookup"><span data-stu-id="0454d-137">Rings can only touch at single tangent points (number of points where rings touch must be finite).</span></span>  
  
5.  <span data-ttu-id="0454d-138">多邊形的內部必須連接在一起。</span><span class="sxs-lookup"><span data-stu-id="0454d-138">The interior of the polygon must be connected.</span></span>  
  
 <span data-ttu-id="0454d-139">下列範例會顯示有效的 **geometryCurvePolygon** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0454d-139">The following example shows valid **geometryCurvePolygon** instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
 <span data-ttu-id="0454d-140">CurvePolygon 執行個體與 Polygon 執行個體具有相同的有效性規則，不過 CurvePolygon 執行個體可接受新的圓弧線段類型。</span><span class="sxs-lookup"><span data-stu-id="0454d-140">CurvePolygon instances have the same validity rules as Polygon instances with the exception that CurvePolygon instances may accept the new circular arc segment types.</span></span> <span data-ttu-id="0454d-141">如需有效或無效執行個體的其他範例，請參閱 [Polygon](polygon.md)。</span><span class="sxs-lookup"><span data-stu-id="0454d-141">For more examples of instances that are valid or not valid, see [Polygon](polygon.md).</span></span>  
  
#### <a name="geography-data-type"></a><span data-ttu-id="0454d-142">Geography 資料類型</span><span class="sxs-lookup"><span data-stu-id="0454d-142">Geography data type</span></span>  
 <span data-ttu-id="0454d-143">有效的 **geographyCurvePolygon** 執行個體必須具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0454d-143">A valid **geographyCurvePolygon** instance must have the following attributes:</span></span>  
  
1.  <span data-ttu-id="0454d-144">多邊形的內部是使用左側規則來連接。</span><span class="sxs-lookup"><span data-stu-id="0454d-144">The interior of the polygon is connected using the left-hand rule.</span></span>  
  
2.  <span data-ttu-id="0454d-145">所有環形都不得跨越它本身或其他環形。</span><span class="sxs-lookup"><span data-stu-id="0454d-145">No ring can cross itself or another ring.</span></span>  
  
3.  <span data-ttu-id="0454d-146">環形只能在單一正切點接觸 (環形接觸的點數必須是有限的)。</span><span class="sxs-lookup"><span data-stu-id="0454d-146">Rings can only touch at single tangent points (number of points where rings touch must be finite).</span></span>  
  
4.  <span data-ttu-id="0454d-147">多邊形的內部必須連接在一起。</span><span class="sxs-lookup"><span data-stu-id="0454d-147">The interior of the polygon must be connected.</span></span>  
  
 <span data-ttu-id="0454d-148">下列範例會顯示有效的 geography CurvePolygon 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0454d-148">The following example shows a valid geography CurvePolygon instance.</span></span>  
  
```  
DECLARE @g geography = 'CURVEPOLYGON((-122.3 47, 122.3 47, 125.7 49, 121 38, -122.3 47))';  
SELECT @g.STIsValid();  
```  
  
## <a name="examples"></a><span data-ttu-id="0454d-149">範例</span><span class="sxs-lookup"><span data-stu-id="0454d-149">Examples</span></span>  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-curvepolygon"></a><span data-ttu-id="0454d-150">A.</span><span class="sxs-lookup"><span data-stu-id="0454d-150">A.</span></span> <span data-ttu-id="0454d-151">使用空的 CurvePolygon 來具現化 Geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="0454d-151">Instantiating a Geometry Instance with an Empty CurvePolygon</span></span>  
 <span data-ttu-id="0454d-152">這個範例會示範如何建立空的 `CurvePolygon` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="0454d-152">This example shows how to create an empty `CurvePolygon` instance:</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-with-a-curvepolygon-in-the-same-statement"></a><span data-ttu-id="0454d-153">B.</span><span class="sxs-lookup"><span data-stu-id="0454d-153">B.</span></span> <span data-ttu-id="0454d-154">在相同的陳述式中使用 CurvePolygon 來宣告和具現化 Geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="0454d-154">Declaring and Instantiating a Geometry Instance with a CurvePolygon in the Same Statement</span></span>  
 <span data-ttu-id="0454d-155">這個程式碼片段會示範如何在相同的陳述式中使用 `CurvePolygon` 來宣告和初始化 geometry 執行個體：</span><span class="sxs-lookup"><span data-stu-id="0454d-155">This code snippet shows how to declare and initialize a geometry instance with a `CurvePolygon` in the same statement:</span></span>  
  
```sql  
DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))'  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-curvepolygon"></a><span data-ttu-id="0454d-156">C.</span><span class="sxs-lookup"><span data-stu-id="0454d-156">C.</span></span> <span data-ttu-id="0454d-157">使用 CurvePolygon 來具現化 Geography 執行個體</span><span class="sxs-lookup"><span data-stu-id="0454d-157">Instantiating a Geography Instance with a CurvePolygon</span></span>  
 <span data-ttu-id="0454d-158">這個程式碼片段會示範如何使用 `geography` 來宣告和初始化 `CurvePolygon` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="0454d-158">This code snippet shows how to declare and initialize a `geography` instance with a `CurvePolygon`:</span></span>  
  
```sql  
DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-curvepolygon-with-only-an-exterior-bounding-ring"></a><span data-ttu-id="0454d-159">D.</span><span class="sxs-lookup"><span data-stu-id="0454d-159">D.</span></span> <span data-ttu-id="0454d-160">儲存只有一個外部週框環形的 CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="0454d-160">Storing a CurvePolygon with Only an Exterior Bounding Ring</span></span>  
 <span data-ttu-id="0454d-161">這個範例會示範如何將簡單的圓形儲存在 `CurvePolygon` 執行個體中 (只用一個外部週框環形來定義圓形)：</span><span class="sxs-lookup"><span data-stu-id="0454d-161">This example shows how to store a simple circle in a `CurvePolygon` instance (only an exterior bounding ring is used to define the circle):</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
### <a name="e-storing-a-curvepolygon-containing-interior-rings"></a><span data-ttu-id="0454d-162">E.</span><span class="sxs-lookup"><span data-stu-id="0454d-162">E.</span></span> <span data-ttu-id="0454d-163">儲存包含內部環形的 CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="0454d-163">Storing a CurvePolygon Containing Interior Rings</span></span>  
 <span data-ttu-id="0454d-164">這個範例會在 `CurvePolygon` 執行個體中建立甜甜圈 (外部週框環形與內部環形都用來定義甜甜圈)：</span><span class="sxs-lookup"><span data-stu-id="0454d-164">This example creates a donut in a `CurvePolygon` instance (both an exterior bounding ring and an interior ring is used to define the donut):</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
 <span data-ttu-id="0454d-165">這個範例會顯示使用內部環形時有效的 `CurvePolygon` 執行個體與無效的執行個體：</span><span class="sxs-lookup"><span data-stu-id="0454d-165">This example shows both a valid `CurvePolygon` instance and an invalid instance when using interior rings:</span></span>  
  
```sql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (-2 2, 2 2, 2 -2, -2 -2, -2 2))');  
IF @g1.STIsValid() = 1  
  BEGIN  
     SELECT @g1.STArea();  
  END  
SET @g2 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (0 5, 5 0, 0 -5, -5 0, 0 5))');  
IF @g2.STIsValid() = 1  
  BEGIN  
     SELECT @g2.STArea();  
  END  
SELECT @g1.STIsValid() AS G1, @g2.STIsValid() AS G2;  
```  
  
 <span data-ttu-id="0454d-166">@g1 和 @g2 都會使用相同的外部週框環形：半徑為 5 的圓形，而且它們都使用正方形代表內部環形。</span><span class="sxs-lookup"><span data-stu-id="0454d-166">Both @g1 and @g2 use the same exterior bounding ring: a circle with a radius of 5 and they both use a square for an interior ring.</span></span>  <span data-ttu-id="0454d-167">不過，執行個體 @g1 有效，但執行個體 @g2 卻無效。</span><span class="sxs-lookup"><span data-stu-id="0454d-167">However, the instance @g1 is valid, but the instance @g2 is invalid.</span></span>  <span data-ttu-id="0454d-168">@g2 無效的原因是，內部環形會將外部環形所限定的內部空間分割成四個不同的區域。</span><span class="sxs-lookup"><span data-stu-id="0454d-168">The reason that @g2 is invalid is that the interior ring splits the interior space bounded by the exterior ring into four separate regions.</span></span>  <span data-ttu-id="0454d-169">下圖將顯示所發生的情況：</span><span class="sxs-lookup"><span data-stu-id="0454d-169">The following drawing shows what occurred:</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0454d-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0454d-170">See Also</span></span>  
 <span data-ttu-id="0454d-171">[多邊形](polygon.md) </span><span class="sxs-lookup"><span data-stu-id="0454d-171">[Polygon](polygon.md) </span></span>  
 <span data-ttu-id="0454d-172">[CircularString](circularstring.md) </span><span class="sxs-lookup"><span data-stu-id="0454d-172">[CircularString](circularstring.md) </span></span>  
 <span data-ttu-id="0454d-173">[CompoundCurve](compoundcurve.md) </span><span class="sxs-lookup"><span data-stu-id="0454d-173">[CompoundCurve](compoundcurve.md) </span></span>  
 <span data-ttu-id="0454d-174">[geometry 資料類型方法參考](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0454d-174">[geometry Data Type Method Reference](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) </span></span>  
 <span data-ttu-id="0454d-175">[geography 資料類型方法參考](/sql/t-sql/spatial-geography/spatial-types-geography) </span><span class="sxs-lookup"><span data-stu-id="0454d-175">[geography Data Type Method Reference](/sql/t-sql/spatial-geography/spatial-types-geography) </span></span>  
 [<span data-ttu-id="0454d-176">空間資料類型概觀</span><span class="sxs-lookup"><span data-stu-id="0454d-176">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
  
  
