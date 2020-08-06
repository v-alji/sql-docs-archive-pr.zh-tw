---
title: 空間資料類型概觀 | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c0548d974e83bfe2b1e103d4458b17078fba8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703981"
---
# <a name="spatial-data-types-overview"></a><span data-ttu-id="a31a2-102">空間資料類型概觀</span><span class="sxs-lookup"><span data-stu-id="a31a2-102">Spatial Data Types Overview</span></span>
  <span data-ttu-id="a31a2-103">空間資料有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="a31a2-103">There are two types of spatial data.</span></span> <span data-ttu-id="a31a2-104"> 資料類型支援平面或 Euclidean (扁平表面) 資料。</span><span class="sxs-lookup"><span data-stu-id="a31a2-104">The `geometry` data type supports planar, or Euclidean (flat-earth), data.</span></span> <span data-ttu-id="a31a2-105"> 資料類型同時符合開放式地理空間協會 (Open Geospatial Consortium，OGC) 的 SQL 簡單特徵規格 1.1.0 版，而且符合 SQL MM (ISO 標準)。</span><span class="sxs-lookup"><span data-stu-id="a31a2-105">The `geometry` data type both conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0 and is compliant with SQL MM (ISO standard).</span></span>

 <span data-ttu-id="a31a2-106">此外，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 也支援 `geography` 資料類型，它會儲存橢圓體 (圓形表面) 資料，例如 GPS 經緯度座標。</span><span class="sxs-lookup"><span data-stu-id="a31a2-106">In addition, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supports the `geography` data type, which stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a31a2-107">如需 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中空間功能 (包括空間資料類型的增強功能) 的詳細描述和範例，請下載技術白皮書： [New Spatial Features in SQL Server Code-Named "Denali"](https://go.microsoft.com/fwlink/?LinkId=226407)(SQL Server 代號 "Denali" 中的新空間功能)。</span><span class="sxs-lookup"><span data-stu-id="a31a2-107">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including enhancements to the spatial data types, download the white paper, [New Spatial Features in SQL Server Code-Named "Denali"](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

##  <a name="spatial-data-objects"></a><a name="objects"></a> <span data-ttu-id="a31a2-108">空間資料物件</span><span class="sxs-lookup"><span data-stu-id="a31a2-108">Spatial Data Objects</span></span>
 <span data-ttu-id="a31a2-109">`geometry` 和 `geography` 資料類型支援十六種空間資料物件或執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="a31a2-109">The `geometry` and `geography` data types support sixteen spatial data objects, or instance types.</span></span> <span data-ttu-id="a31a2-110">但是，其中只有十一種執行個體類型「可具現化」  ；因此，您可以在資料庫中建立及處理這些執行個體 (或加以具現化)。</span><span class="sxs-lookup"><span data-stu-id="a31a2-110">However, only eleven of these instance types are *instantiable*; you can create and work with these instances (or instantiate them) in a database.</span></span> <span data-ttu-id="a31a2-111">這些實例會從父資料類型衍生某些屬性，以將其區分為 `Points` 、 **linestring、CircularStrings**、 `CompoundCurves` 、 `Polygons` ， `CurvePolygons` 或做為 `geometry` 中的多個或 `geography` 實例 `GeometryCollection` 。</span><span class="sxs-lookup"><span data-stu-id="a31a2-111">These instances derive certain properties from their parent data types that distinguish them as `Points`, **LineStrings, CircularStrings**, `CompoundCurves`, `Polygons`, `CurvePolygons` or as multiple `geometry` or `geography` instances in a `GeometryCollection`.</span></span> <span data-ttu-id="a31a2-112">`Geography` 類型具有一種額外的執行個體類型：`FullGlobe`。</span><span class="sxs-lookup"><span data-stu-id="a31a2-112">`Geography` type has an additional instance type, `FullGlobe`.</span></span>

 <span data-ttu-id="a31a2-113">下圖說明 `geometry` 和 `geometry` 資料類型所根據的 `geography` 階層。</span><span class="sxs-lookup"><span data-stu-id="a31a2-113">The figure below depicts the `geometry` hierarchy upon which the `geometry` and `geography` data types are based.</span></span> <span data-ttu-id="a31a2-114">和的可具 `geometry` 現化類型 `geography` 會以藍色表示。</span><span class="sxs-lookup"><span data-stu-id="a31a2-114">The instantiable types of `geometry` and `geography` are indicated in blue.</span></span>

 <span data-ttu-id="a31a2-115">![Geometry 類型的階層](../../database-engine/media/geom-hierarchy.gif "Geometry 類型的階層")</span><span class="sxs-lookup"><span data-stu-id="a31a2-115">![Hierarchy of the geometry type](../../database-engine/media/geom-hierarchy.gif "Hierarchy of the geometry type")</span></span>

 <span data-ttu-id="a31a2-116">如圖所示，和資料類型的十種 `geometry` 可具現化類型 `geography` 為 `Point` 、 `MultiPoint` 、、 `LineString` 、 `CircularString` `MultiLineString` `CompoundCurve` `Polygon` `CurvePolygon` `MultiPolygon` `GeometryCollection` 、、、、和。</span><span class="sxs-lookup"><span data-stu-id="a31a2-116">As the figure indicates, the ten instantiable types of the `geometry` and `geography` data types are `Point`, `MultiPoint`, `LineString`, `CircularString`, `MultiLineString`, `CompoundCurve`, `Polygon`, `CurvePolygon`, `MultiPolygon`, and `GeometryCollection`.</span></span> <span data-ttu-id="a31a2-117">geography 資料類型還有一種額外的可具現化類型：`FullGlobe`。</span><span class="sxs-lookup"><span data-stu-id="a31a2-117">There is one additional instantiable type for the geography data type: `FullGlobe`.</span></span> <span data-ttu-id="a31a2-118">`geometry`和 `geography` 類型可以辨識特定的實例（只要它是格式正確的實例），即使未明確定義實例亦然。</span><span class="sxs-lookup"><span data-stu-id="a31a2-118">The `geometry` and `geography` types can recognize a specific instance as long as it is a well-formed instance, even if the instance is not defined explicitly.</span></span> <span data-ttu-id="a31a2-119">例如，如果您 `Point` 使用 STPointFromText ( # A1 方法明確地定義實例，並將 `geometry` `geography` 實例辨識為 `Point` ，只要方法輸入的格式正確。</span><span class="sxs-lookup"><span data-stu-id="a31a2-119">For example, if you define a `Point` instance explicitly using the STPointFromText() method, `geometry` and `geography` recognize the instance as a `Point`, as long as the method input is well-formed.</span></span> <span data-ttu-id="a31a2-120">如果您使用 `STGeomFromText()` 方法定義相同的執行個體，`geometry` 和 `geography` 資料類型都會將此執行個體辨識為 `Point`。</span><span class="sxs-lookup"><span data-stu-id="a31a2-120">If you define the same instance using the `STGeomFromText()` method, both the `geometry` and `geography` data types recognize the instance as a `Point`.</span></span>

 <span data-ttu-id="a31a2-121">geometry 和 geography 類型的子類型可區分為簡單與集合類型。</span><span class="sxs-lookup"><span data-stu-id="a31a2-121">The subtypes for geometry and geography types are divided into simple and collection types.</span></span>  <span data-ttu-id="a31a2-122">某些方法 (例如 `STNumCurves()` ) 只能使用簡單類型。</span><span class="sxs-lookup"><span data-stu-id="a31a2-122">Some methods like `STNumCurves()` work only with simple types.</span></span>

 <span data-ttu-id="a31a2-123">簡單類型包括：</span><span class="sxs-lookup"><span data-stu-id="a31a2-123">Simple types include:</span></span>

-   [<span data-ttu-id="a31a2-124">點</span><span class="sxs-lookup"><span data-stu-id="a31a2-124">Point</span></span>](../spatial/point.md)

-   [<span data-ttu-id="a31a2-125">LineString</span><span class="sxs-lookup"><span data-stu-id="a31a2-125">LineString</span></span>](../spatial/linestring.md)

-   [<span data-ttu-id="a31a2-126">CircularString</span><span class="sxs-lookup"><span data-stu-id="a31a2-126">CircularString</span></span>](../spatial/circularstring.md)

-   [<span data-ttu-id="a31a2-127">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="a31a2-127">CompoundCurve</span></span>](../spatial/compoundcurve.md)

-   [<span data-ttu-id="a31a2-128">Polygon</span><span class="sxs-lookup"><span data-stu-id="a31a2-128">Polygon</span></span>](../spatial/polygon.md)

-   [<span data-ttu-id="a31a2-129">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="a31a2-129">CurvePolygon</span></span>](../spatial/curvepolygon.md)

 <span data-ttu-id="a31a2-130">集合類型包括：</span><span class="sxs-lookup"><span data-stu-id="a31a2-130">Collection types include:</span></span>

-   [<span data-ttu-id="a31a2-131">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="a31a2-131">MultiPoint</span></span>](../spatial/multipoint.md)

-   [<span data-ttu-id="a31a2-132">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="a31a2-132">MultiLineString</span></span>](../spatial/multilinestring.md)

-   [<span data-ttu-id="a31a2-133">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="a31a2-133">MultiPolygon</span></span>](../spatial/multipolygon.md)

-   [<span data-ttu-id="a31a2-134">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="a31a2-134">GeometryCollection</span></span>](../spatial/geometrycollection.md)


##  <a name="differences-between-the-geometry-and-geography-data-types"></a><a name="differences"></a> <span data-ttu-id="a31a2-135">Geometry 和 geography 資料類型之間的差異</span><span class="sxs-lookup"><span data-stu-id="a31a2-135">Differences Between the geometry and geography Data Types</span></span>
 <span data-ttu-id="a31a2-136">這兩種類型的空間資料通常會有非常類似的行為，但是儲存及操作資料的方式會有一些重要的差異。</span><span class="sxs-lookup"><span data-stu-id="a31a2-136">The two types of spatial data often behave quite similarly, but there are some key differences in how the data is stored and manipulated.</span></span>

### <a name="how-connecting-edges-are-defined"></a><span data-ttu-id="a31a2-137">連接邊緣的定義方式</span><span class="sxs-lookup"><span data-stu-id="a31a2-137">How connecting edges are defined</span></span>
 <span data-ttu-id="a31a2-138">`LineString` 和 `Polygon` 類型的定義資料僅為頂點。</span><span class="sxs-lookup"><span data-stu-id="a31a2-138">The defining data for `LineString` and `Polygon` types are vertices only.</span></span>  <span data-ttu-id="a31a2-139">幾何類型中兩個頂點的連接邊緣為直線。</span><span class="sxs-lookup"><span data-stu-id="a31a2-139">The connecting edge between two vertices in a geometry type is a straight line.</span></span>  <span data-ttu-id="a31a2-140">不過，地理位置類型中兩個頂點的連接邊緣為兩個頂點的最短大橢圓弧形。</span><span class="sxs-lookup"><span data-stu-id="a31a2-140">However, the connecting edge between two vertices in a geography type is a short great elliptic arc between the two vertices.</span></span>  <span data-ttu-id="a31a2-141">大橢圓形是橢圓體與經過其中心之平面的交集，而大橢圓弧形為大橢圓形上的弧形線段。</span><span class="sxs-lookup"><span data-stu-id="a31a2-141">A great ellipse is the intersection of the ellipsoid with a plane through its center and a great elliptic arc is an arc segment on the great ellipse.</span></span>

### <a name="how-circular-arc-segments-are-defined"></a><span data-ttu-id="a31a2-142">圓弧線段的定義方式</span><span class="sxs-lookup"><span data-stu-id="a31a2-142">How circular arc segments are defined</span></span>
 <span data-ttu-id="a31a2-143">geometry 類型的圓弧線段定義於 XY 笛卡兒座標平面上 (忽略 Z 值)。</span><span class="sxs-lookup"><span data-stu-id="a31a2-143">Circular arc segments for geometry types are defined on the XY Cartesian coordinate plane (Z values are ignored).</span></span> <span data-ttu-id="a31a2-144">geography 類型的圓弧線段則由參考球面的曲線線段定義。</span><span class="sxs-lookup"><span data-stu-id="a31a2-144">Circular arc segments for geography types are defined by curve segments on a reference sphere.</span></span> <span data-ttu-id="a31a2-145">參考球面上的任何緯線都可由兩個互補的圓弧定義，其中這兩個弧形的點都具有固定緯度角度。</span><span class="sxs-lookup"><span data-stu-id="a31a2-145">Any parallel on the reference sphere can be defined by two complementary circular arcs where the points for both arcs have a constant latitude angle.</span></span>

### <a name="measurements-in-spatial-data-types"></a><span data-ttu-id="a31a2-146">空間資料類型的度量</span><span class="sxs-lookup"><span data-stu-id="a31a2-146">Measurements in spatial data types</span></span>
 <span data-ttu-id="a31a2-147">在平面或扁平表面系統中，系統會使用與座標相同的度量單位來測量距離和區域。</span><span class="sxs-lookup"><span data-stu-id="a31a2-147">In the planar, or flat-earth, system, measurements of distances and areas are given in the same unit of measurement as coordinates.</span></span> <span data-ttu-id="a31a2-148">使用 `geometry` 資料類型時，(2, 2) 與 (5, 6) 之間的距離就是 5 單位 (不論所用的單位為何)。</span><span class="sxs-lookup"><span data-stu-id="a31a2-148">Using the `geometry` data type, the distance between (2, 2) and (5, 6) is 5 units, regardless of the units used.</span></span>

 <span data-ttu-id="a31a2-149">在橢圓體 (或圓形地球) 系統中，會使用經緯度來提供座標。</span><span class="sxs-lookup"><span data-stu-id="a31a2-149">In the ellipsoidal, or round-earth system, coordinates are given in degrees of latitude and longitude.</span></span> <span data-ttu-id="a31a2-150">但是，長度和區域通常會使用公尺和平方公尺來測量，但是這樣的測量可能取決於 `geography` 執行個體的空間參考識別碼 (SRID)。</span><span class="sxs-lookup"><span data-stu-id="a31a2-150">However, lengths and areas are usually measured in meters and square meters, though the measurement may depend on the spatial reference identifier (SRID) of the `geography` instance.</span></span> <span data-ttu-id="a31a2-151"> 資料類型最常見的度量單位是公尺。</span><span class="sxs-lookup"><span data-stu-id="a31a2-151">The most common unit of measurement for the `geography` data type is meters.</span></span>

### <a name="orientation-of-spatial-data"></a><span data-ttu-id="a31a2-152">空間資料的方向</span><span class="sxs-lookup"><span data-stu-id="a31a2-152">Orientation of spatial data</span></span>
 <span data-ttu-id="a31a2-153">在平面系統中，多邊形的環形方向不是重要的因素。</span><span class="sxs-lookup"><span data-stu-id="a31a2-153">In the planar system, the ring orientation of a polygon is not an important factor.</span></span> <span data-ttu-id="a31a2-154">例如，((0, 0), (10, 0), (0, 20), (0, 0)) 描述的多邊形與 ((0, 0), (0, 20), (10, 0), (0, 0)) 描述的多邊形相同。</span><span class="sxs-lookup"><span data-stu-id="a31a2-154">For example, a polygon described by ((0, 0), (10, 0), (0, 20), (0, 0)) is the same as a polygon described by ((0, 0), (0, 20), (10, 0), (0, 0)).</span></span> <span data-ttu-id="a31a2-155">OGC 的 SQL 簡單特徵規格並未指示環形順序，而且 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 並未強制使用環形順序。</span><span class="sxs-lookup"><span data-stu-id="a31a2-155">The OGC Simple Features for SQL Specification does not dictate a ring ordering, and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not enforce ring ordering.</span></span>

 <span data-ttu-id="a31a2-156">在橢圓體系統中，多邊形如果沒有方向的話，將沒有任何意義或是會模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="a31a2-156">In an ellipsoidal system, a polygon has no meaning, or is ambiguous, without an orientation.</span></span> <span data-ttu-id="a31a2-157">例如，包圍赤道的環形是要描述北半球還是南半球？</span><span class="sxs-lookup"><span data-stu-id="a31a2-157">For example, does a ring around the equator describe the northern or southern hemisphere?</span></span> <span data-ttu-id="a31a2-158">如果我們使用 `geography` 資料類型來儲存空間執行個體，就必須指定此環形的方向，並正確描述此執行個體的位置。</span><span class="sxs-lookup"><span data-stu-id="a31a2-158">If we use the `geography` data type to store the spatial instance, we must specify the orientation of the ring and accurately describe the location of the instance.</span></span> <span data-ttu-id="a31a2-159">在橢圓體系統中，多邊形的內部是由左側規則定義。</span><span class="sxs-lookup"><span data-stu-id="a31a2-159">The interior of the polygon in an ellipsoidal system is defined by the left-hand rule.</span></span>

 <span data-ttu-id="a31a2-160">當相容性層級為100或以下的時 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ， `geography` 資料類型會有下列限制：</span><span class="sxs-lookup"><span data-stu-id="a31a2-160">When the compatibility level is 100 or below in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] then the `geography` data type has the following restrictions:</span></span>

-   <span data-ttu-id="a31a2-161">每一個 `geography` 執行個體都必須納入單一半球。</span><span class="sxs-lookup"><span data-stu-id="a31a2-161">Each `geography` instance must fit inside a single hemisphere.</span></span> <span data-ttu-id="a31a2-162">大於半球的空間物件將無法儲存。</span><span class="sxs-lookup"><span data-stu-id="a31a2-162">No spatial objects larger than a hemisphere can be stored.</span></span>

-   <span data-ttu-id="a31a2-163">當來自開放式地理空間協會 (Open Geospatial Consortium，OGC) 已知的文字 (Well-Known Text，WKT) 或已知的二進位 (Well-Known Binary，WKB) 表示法的任何 `geography` 執行個體產生大於半球的物件時，都會擲回 `ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="a31a2-163">Any `geography` instance from an Open Geospatial Consortium (OGC) Well-Known Text (WKT) or Well-Known Binary (WKB) representation that produces an object larger than a hemisphere throws an `ArgumentException`.</span></span>

-   <span data-ttu-id="a31a2-164">`geography`需要兩個實例輸入的資料類型方法（ `geography` 例如 STIntersection ( # A1、STUnion ( # A3、STDifference ( # A5 和 STSymDifference ( # A7）將會在方法的結果無法放入單一半球內時傳回 null。</span><span class="sxs-lookup"><span data-stu-id="a31a2-164">The `geography` data type methods that require the input of two `geography` instances, such as STIntersection(), STUnion(), STDifference(), and STSymDifference(), will return null if the results from the methods do not fit inside a single hemisphere.</span></span> <span data-ttu-id="a31a2-165">如果輸出超過單一半球，STBuffer() 也會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="a31a2-165">STBuffer() will also return null if the output exceeds a single hemisphere.</span></span>

 <span data-ttu-id="a31a2-166">在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中，`FullGlobe` 是一種特殊類型的多邊形，它涵蓋了整個地球。</span><span class="sxs-lookup"><span data-stu-id="a31a2-166">In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], `FullGlobe` is a special type of Polygon that covers the entire globe.</span></span> <span data-ttu-id="a31a2-167">`FullGlobe` 有面積，但沒有框線或頂點。</span><span class="sxs-lookup"><span data-stu-id="a31a2-167">`FullGlobe` has an area, but no borders or vertices.</span></span>

### <a name="outer-and-inner-rings-not-important-in-geography-data-type"></a><span data-ttu-id="a31a2-168">外部和內部環形在 geography 資料類型中不重要</span><span class="sxs-lookup"><span data-stu-id="a31a2-168">Outer and inner rings not important in geography data type</span></span>
 <span data-ttu-id="a31a2-169">適用于 SQL 規格的 OGC 簡單功能會討論外部環形和內部環形，但是這種區別對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` 資料類型而言並沒有意義; 任何多邊形的環形都可以成為外部環形。</span><span class="sxs-lookup"><span data-stu-id="a31a2-169">The OGC Simple Features for SQL Specification discusses outer rings and inner rings, but this distinction makes little sense for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` data type; any ring of a polygon can be taken to be the outer ring.</span></span>

 <span data-ttu-id="a31a2-170">如需有關 OGC 規格的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a31a2-170">For more information on OGC specifications, see the following:</span></span>

-   [<span data-ttu-id="a31a2-171">OGC 規格，簡單特徵存取第一部 - 常見架構</span><span class="sxs-lookup"><span data-stu-id="a31a2-171">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span></span>](https://go.microsoft.com/fwlink/?LinkId=93627)

-   <span data-ttu-id="a31a2-172">[OGC 規格，簡單特徵存取第二部 - SQL 選項](https://go.microsoft.com/fwlink/?LinkId=93628) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="a31a2-172">[OGC Specifications, Simple Feature Access Part 2 - SQL Options](https://go.microsoft.com/fwlink/?LinkId=93628)</span></span>


##  <a name="circular-arc-segments"></a><a name="circular"></a> <span data-ttu-id="a31a2-173">圓弧線段</span><span class="sxs-lookup"><span data-stu-id="a31a2-173">Circular Arc Segments</span></span>
 <span data-ttu-id="a31a2-174">三種可具現化的類型可以採用圓弧線段：`CircularString`、`CompoundCurve` 和 `CurvePolygon`。</span><span class="sxs-lookup"><span data-stu-id="a31a2-174">Three instantiable types can take circular arc segments: `CircularString`, `CompoundCurve`, and `CurvePolygon`.</span></span>  <span data-ttu-id="a31a2-175">圓弧線段是由二維平面中的三個點定義，而且第三個點不得與第一個點相同。</span><span class="sxs-lookup"><span data-stu-id="a31a2-175">A circular arc segment is defined by three points in a two dimensional plane and the third point cannot be the same as the first point.</span></span>

 <span data-ttu-id="a31a2-176">圖 A 和 B 顯示一般圓弧線段。</span><span class="sxs-lookup"><span data-stu-id="a31a2-176">Figures A and B show typical circular arc segments.</span></span> <span data-ttu-id="a31a2-177">請注意，這三個點如何分別位於圓形的圓周上。</span><span class="sxs-lookup"><span data-stu-id="a31a2-177">Note how each of the three points lie on the perimeter of a circle.</span></span>

 <span data-ttu-id="a31a2-178">圖 C 和 D 顯示如何將直線線段定義為圓弧線段。</span><span class="sxs-lookup"><span data-stu-id="a31a2-178">Figures C and D show how a line segment can be defined as a circular arc segment.</span></span>  <span data-ttu-id="a31a2-179">請注意，仍然需要三個點才能定義圓弧線段，這與只由兩個點定義的一般直線線段不同。</span><span class="sxs-lookup"><span data-stu-id="a31a2-179">Note that three points are still needed to define the circular arc segment unlike a regular line segment which can be defined by just two points.</span></span>

 <span data-ttu-id="a31a2-180">在圓弧線段類型上運作的方法會使用直線線段來模擬圓弧。用於模擬弧形的直線線段數目將取決於弧形的長度和曲度。您可以針對每種圓弧線段類型儲存 Z 值。不過，方法不會在計算中使用 Z 值。</span><span class="sxs-lookup"><span data-stu-id="a31a2-180">Methods operating on circular arc segment types use straight line segments to approximate the circular arc. The number of line segments used to approximate the arc will depend on the length and curvature of the arc. Z values can be stored for each of the circular arc segment types; however, methods will not use the Z values in their calculations.</span></span>

> [!NOTE]
>  <span data-ttu-id="a31a2-181">如果針對圓弧線段提供了 Z 值，則圓弧線段中所有點的這些值都必須相同，系統才會接受輸入。</span><span class="sxs-lookup"><span data-stu-id="a31a2-181">If Z values are given for circular arc segments then they must be the same for all points in the circular arc segment for it to be accepted for input.</span></span> <span data-ttu-id="a31a2-182">例如：系統可接受 `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` ，但無法接受 `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` 。</span><span class="sxs-lookup"><span data-stu-id="a31a2-182">For example: `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` is accepted, but `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` is not accepted.</span></span>

### <a name="linestring-and-circularstring-comparison"></a><span data-ttu-id="a31a2-183">LineString 和 CircularString 的比較</span><span class="sxs-lookup"><span data-stu-id="a31a2-183">LineString and CircularString comparison</span></span>
 <span data-ttu-id="a31a2-184">下圖顯示完全相同的等腰三角形 (三角形 A 會使用直線線段來定義三角形，而三角形 B 則使用圓弧線段來定義三角形)：</span><span class="sxs-lookup"><span data-stu-id="a31a2-184">The following diagram shows identical isosceles triangles (triangle A uses line segments to define the triangle and triangle B uses circular arc segments to defined the triangle):</span></span>

 ![](../../database-engine/media/7e382f76-59da-4b62-80dc-caf93e637c14.png "7e382f76-59da-4b62-80dc-caf93e637c14")

 <span data-ttu-id="a31a2-185">此範例會示範如何使用 `LineString` 執行個體和 `CircularString` 執行個體來儲存上述等腰三角形：</span><span class="sxs-lookup"><span data-stu-id="a31a2-185">This example shows how to store the above isosceles triangles using both a `LineString` instance and `CircularString` instance:</span></span>

```sql
DECLARE @g1 geometry;
DECLARE @g2 geometry;
SET @g1 = geometry::STGeomFromText('LINESTRING(1 1, 5 1, 3 5, 1 1)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(1 1, 3 1, 5 1, 4 3, 3 5, 2 3, 1 1)', 0);
IF @g1.STIsValid() = 1 AND @g2.STIsValid() = 1
  BEGIN
      SELECT @g1.ToString(), @g2.ToString()
      SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length]
  END
```

 <span data-ttu-id="a31a2-186">請注意，`CircularString` 執行個體需要使用七個點來定義三角形，但是 `LineString` 執行個體只需要使用四個點來定義三角形。</span><span class="sxs-lookup"><span data-stu-id="a31a2-186">Notice that a `CircularString` instance requires seven points to define the triangle, but a `LineString` instance requires only four points to define the triangle.</span></span> <span data-ttu-id="a31a2-187">這是因為 `CircularString` 執行個體會儲存圓弧線段而非直線線段。</span><span class="sxs-lookup"><span data-stu-id="a31a2-187">The reason for this is that a `CircularString` instance stores circular arc segments and not line segments.</span></span> <span data-ttu-id="a31a2-188">因此，儲存在 `CircularString` 執行個體中的三角形側邊為 ABC、CDE 和 EFA，而儲存在 `LineString` 執行個體中的三角形側邊為 AC、CE 和 EA。</span><span class="sxs-lookup"><span data-stu-id="a31a2-188">So the sides of the triangle stored in the `CircularString` instance are ABC, CDE, and EFA whereas the sides of the triangle stored in the `LineString` instance are AC, CE, and EA.</span></span>

 <span data-ttu-id="a31a2-189">請考慮下列程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="a31a2-189">Consider the following code snippet:</span></span>

```sql
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];
```

 <span data-ttu-id="a31a2-190">這個程式碼片段會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="a31a2-190">This snippet will produce the following results:</span></span>

```
LS LengthCS Length
5.65685...6.28318...
```

 <span data-ttu-id="a31a2-191">下圖顯示每種類型的儲存方式， (紅線顯示 `LineString``@g1` ，藍線顯示 `CircularString``@g2`) ：</span><span class="sxs-lookup"><span data-stu-id="a31a2-191">The following illustration shows how each type is stored (red line shows `LineString``@g1`, blue line shows `CircularString``@g2`):</span></span>

 ![](../../database-engine/media/e52157b5-5160-4a4b-8560-50cdcf905b76.png "e52157b5-5160-4a4b-8560-50cdcf905b76")

 <span data-ttu-id="a31a2-192">如上圖所示，`CircularString` 執行個體會使用較少的點來儲存曲線界限，而精確度卻高於 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a31a2-192">As the illustration above shows, `CircularString` instances use fewer points to store curve boundaries with greater precision than `LineString` instances.</span></span> <span data-ttu-id="a31a2-193">`CircularString` 執行個體適合用於儲存圓形邊界，像是從特定點起算的二十英哩搜尋半徑。</span><span class="sxs-lookup"><span data-stu-id="a31a2-193">`CircularString` instances are useful for storing circular boundaries like a twenty-mile search radius from a specific point.</span></span> <span data-ttu-id="a31a2-194">`LineString` 執行個體適合用於儲存線性邊界，像是方形的城市街區。</span><span class="sxs-lookup"><span data-stu-id="a31a2-194">`LineString` instances are good for storing boundaries that are linear like a square city block.</span></span>

### <a name="linestring-and-compoundcurve-comparison"></a><span data-ttu-id="a31a2-195">LineString 和 CompoundCurve 的比較</span><span class="sxs-lookup"><span data-stu-id="a31a2-195">LineString and CompoundCurve comparison</span></span>
 <span data-ttu-id="a31a2-196">下列程式碼範例會示範如何使用 `LineString` 和 `CompoundCurve` 執行個體來儲存相同的圖形：</span><span class="sxs-lookup"><span data-stu-id="a31a2-196">The following code examples show how to store the same figure using `LineString` and `CompoundCurve` instances:</span></span>

```sql
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');
```

 <span data-ttu-id="a31a2-197">或</span><span class="sxs-lookup"><span data-stu-id="a31a2-197">or</span></span>

 <span data-ttu-id="a31a2-198">在上述範例中，`LineString` 執行個體或 `CompoundCurve` 執行個體都可以儲存此圖形。</span><span class="sxs-lookup"><span data-stu-id="a31a2-198">In the examples above, either a `LineString` instance or a `CompoundCurve` instance could store the figure.</span></span>  <span data-ttu-id="a31a2-199">下一個範例會使用 `CompoundCurve` 來儲存圓形圖配量：</span><span class="sxs-lookup"><span data-stu-id="a31a2-199">This next example uses a `CompoundCurve` to store a pie slice:</span></span>

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');
```

 <span data-ttu-id="a31a2-200"> 執行個體可以直接儲存圓弧線段 (2 2, 1 3, 0 2)，而  執行個體則必須將曲線轉換成許多較小的直線線段。</span><span class="sxs-lookup"><span data-stu-id="a31a2-200">A `CompoundCurve` instance can store the circular arc segment (2 2, 1 3, 0 2) directly whereas a `LineString` instance would have to convert the curve into several smaller line segments.</span></span>

### <a name="circularstring-and-compoundcurve-comparison"></a><span data-ttu-id="a31a2-201">CircularString 和 CompoundCurve 的比較</span><span class="sxs-lookup"><span data-stu-id="a31a2-201">CircularString and CompoundCurve comparison</span></span>
 <span data-ttu-id="a31a2-202">下列程式碼範例會示範如何將圓形圖配量儲存在 `CircularString` 執行個體中：</span><span class="sxs-lookup"><span data-stu-id="a31a2-202">The following code example shows how the pie slice can be stored in a `CircularString` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');
SELECT @g.ToString(), @g.STLength();
```

 <span data-ttu-id="a31a2-203">若要使用 `CircularString` 執行個體來儲存圓形圖配量，每個直線線段都必須使用三個點。</span><span class="sxs-lookup"><span data-stu-id="a31a2-203">To store the pie slice using a `CircularString` instance requires that three points be used for each line segment.</span></span>  <span data-ttu-id="a31a2-204">如果中繼點為未知，則必須計算此點，或者直線線段的端點必須加倍，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="a31a2-204">If an intermediate point is not known, it either has to be calculated or the endpoint of the line segment has to be doubled as the following snippet shows:</span></span>

```sql
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');
```

 <span data-ttu-id="a31a2-205">`CompoundCurve`實例允許 `LineString` 和 `CircularString` 元件，因此只需要知道圓形圖配量之直線線段的兩個點。</span><span class="sxs-lookup"><span data-stu-id="a31a2-205">`CompoundCurve` instances allow both `LineString` and `CircularString` components so that only two points to the line segments of the pie slice need to be known.</span></span>  <span data-ttu-id="a31a2-206">此程式碼範例會示範如何使用 `CompoundCurve` 來儲存相同的圖形：</span><span class="sxs-lookup"><span data-stu-id="a31a2-206">This code example shows how to use a `CompoundCurve` to store the same figure:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');
SELECT @g.ToString(), @g.STLength();
```

### <a name="polygon-and-curvepolygon-comparison"></a><span data-ttu-id="a31a2-207">Polygon 和 CurvePolygon 的比較</span><span class="sxs-lookup"><span data-stu-id="a31a2-207">Polygon and CurvePolygon comparison</span></span>
 <span data-ttu-id="a31a2-208"> 執行個體可以在定義其外部與內部環形時，使用  和  執行個體。</span><span class="sxs-lookup"><span data-stu-id="a31a2-208">`CurvePolygon` instances can use `CircularString` and `CompoundCurve` instances when defining their exterior and interior rings.</span></span>  <span data-ttu-id="a31a2-209"> 執行個體無法使用圓弧線段類型： 和 。</span><span class="sxs-lookup"><span data-stu-id="a31a2-209">`Polygon` instances cannot use the circular arc segment types: `CircularString` and `CompoundCurve`.</span></span>


## <a name="see-also"></a><span data-ttu-id="a31a2-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a31a2-210">See Also</span></span>
 <span data-ttu-id="a31a2-211">[空間資料 &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [Geometry 資料類型方法參考](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) [geography 資料類型方法參考](/sql/t-sql/spatial-geography/spatial-types-geography) [STNumCurves &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) [STNumCurves &#40;geography 資料類型&#41;](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type) [STGeomFromText &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type) [STGeomFromText &#40;geography 資料類型&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)</span><span class="sxs-lookup"><span data-stu-id="a31a2-211">[Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [geometry Data Type Method Reference](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) [geography Data Type Method Reference](/sql/t-sql/spatial-geography/spatial-types-geography) [STNumCurves &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) [STNumCurves &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type) [STGeomFromText &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type) [STGeomFromText &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)</span></span>


