---
title: LineString | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- LineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: e50d0b86-8b31-4285-be71-ad05c7712cbd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5a0f77959cfe4492eca6c38951ba2868452d41ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606176"
---
# <a name="linestring"></a><span data-ttu-id="00071-102">LineString</span><span class="sxs-lookup"><span data-stu-id="00071-102">LineString</span></span>
  <span data-ttu-id="00071-103">`LineString` 是代表一連串的點及連接這些點之線段的一維度物件。</span><span class="sxs-lookup"><span data-stu-id="00071-103">A `LineString` is a one-dimensional object representing a sequence of points and the line segments connecting them.</span></span>

## <a name="linestring-instances"></a><span data-ttu-id="00071-104">LineString 執行個體</span><span class="sxs-lookup"><span data-stu-id="00071-104">LineString Instances</span></span>
 <span data-ttu-id="00071-105">下圖顯示 `LineString` 執行個體的範例。</span><span class="sxs-lookup"><span data-stu-id="00071-105">The illustration below shows examples of `LineString` instances.</span></span>

 <span data-ttu-id="00071-106">![幾何 LineString 執行個體的範例](../../database-engine/media/linestring.gif "幾何 LineString 執行個體的範例")</span><span class="sxs-lookup"><span data-stu-id="00071-106">![Examples of geometry LineString instances](../../database-engine/media/linestring.gif "Examples of geometry LineString instances")</span></span>

 <span data-ttu-id="00071-107">如本圖所示：</span><span class="sxs-lookup"><span data-stu-id="00071-107">As shown in the illustration:</span></span>

-   <span data-ttu-id="00071-108">圖 1 是簡單、非封閉的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-108">Figure 1 is a simple, nonclosed `LineString` instance.</span></span>

-   <span data-ttu-id="00071-109">圖 2 是非簡單、非封閉的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-109">Figure 2 is a nonsimple, nonclosed `LineString` instance.</span></span>

-   <span data-ttu-id="00071-110">圖 3 是簡單、封閉的 `LineString` 執行個體，因此它是環形。</span><span class="sxs-lookup"><span data-stu-id="00071-110">Figure 3 is a closed, simple `LineString` instance, and therefore is a ring.</span></span>

-   <span data-ttu-id="00071-111">圖 4 是非簡單、封閉的 `LineString` 執行個體，因此它不是環形。</span><span class="sxs-lookup"><span data-stu-id="00071-111">Figure 4 is a closed, nonsimple `LineString` instance, and therefore is not a ring.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="00071-112">已接受的執行個體</span><span class="sxs-lookup"><span data-stu-id="00071-112">Accepted Instances</span></span>
 <span data-ttu-id="00071-113">您可以將已接受的 `LineString` 執行個體放入 geometry 變數中，但是它們可能不是有效的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-113">Accepted `LineString` instances can be input into a geometry variable, but they may not be valid `LineString` instances.</span></span> <span data-ttu-id="00071-114">若要讓系統接受 `LineString` 執行個體，就必須符合下列準則。</span><span class="sxs-lookup"><span data-stu-id="00071-114">The following criteria must be met for a `LineString` instance to be accepted.</span></span> <span data-ttu-id="00071-115">此執行個體至少必須由兩個點所組成，或者它必須是空的。</span><span class="sxs-lookup"><span data-stu-id="00071-115">The instance must be formed of at least two points or it must be empty.</span></span> <span data-ttu-id="00071-116">下面是已接受的 LineString 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-116">The following LineString instances are accepted.</span></span>

```
DECLARE @g1 geometry = 'LINESTRING EMPTY';
DECLARE @g2 geometry = 'LINESTRING(1 1,2 3,4 8, -6 3)';
DECLARE @g3 geometry = 'LINESTRING(1 1, 1 1)';
```

 <span data-ttu-id="00071-117">`@g3` 顯示 `LineString` 執行個體可被系統接受但卻無效。</span><span class="sxs-lookup"><span data-stu-id="00071-117">`@g3` shows that a `LineString` instance can be accepted, but not valid.</span></span>

 <span data-ttu-id="00071-118">下面是無法接受的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-118">The following `LineString` instance is not accepted.</span></span> <span data-ttu-id="00071-119">它將擲回 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="00071-119">It will throw a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'LINESTRING(1 1)';
```

### <a name="valid-instances"></a><span data-ttu-id="00071-120">有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="00071-120">Valid Instances</span></span>
 <span data-ttu-id="00071-121">`LineString` 執行個體必須符合下列準則，才會是有效的。</span><span class="sxs-lookup"><span data-stu-id="00071-121">For a `LineString` instance to be valid it must meet the following criteria.</span></span>

1.  <span data-ttu-id="00071-122">系統必須接受 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-122">The `LineString` instance must be accepted.</span></span>

2.  <span data-ttu-id="00071-123">如果 `LineString` 執行個體不是空的，則它至少必須包含兩個相異點。</span><span class="sxs-lookup"><span data-stu-id="00071-123">If a `LineString` instance is not empty then it must contain at least two distinct points.</span></span>

3.  <span data-ttu-id="00071-124">`LineString` 執行個體本身不得在兩個或多個連續點的間隔上重疊。</span><span class="sxs-lookup"><span data-stu-id="00071-124">The `LineString` instance cannot overlap itself over an interval of two or more consecutive points.</span></span>

 <span data-ttu-id="00071-125">下面是有效的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-125">The following `LineString` instances are valid.</span></span>

```
DECLARE @g1 geometry= 'LINESTRING EMPTY';
DECLARE @g2 geometry= 'LINESTRING(1 1, 3 3)';
DECLARE @g3 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0)';
DECLARE @g4 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();

```

 <span data-ttu-id="00071-126">下面是無效的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-126">The following `LineString` instances are not valid.</span></span>

```
DECLARE @g1 geometry = 'LINESTRING(1 4, 3 4, 2 4, 2 0)';
DECLARE @g2 geometry = 'LINESTRING(1 1, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

> [!WARNING]
>  <span data-ttu-id="00071-127">`LineString` 重疊的偵測是以浮點計算為基礎，但這些計算並不精確。</span><span class="sxs-lookup"><span data-stu-id="00071-127">The detection of `LineString` overlaps is based on floating-point calculations, which are not exact.</span></span>

## <a name="examples"></a><span data-ttu-id="00071-128">範例</span><span class="sxs-lookup"><span data-stu-id="00071-128">Examples</span></span>
 <span data-ttu-id="00071-129">下列範例示範如何建立具有三個點且 SRID 為 0 的 `geometry``LineString` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="00071-129">The following example shows how to create a `geometry``LineString` instance with three points and an SRID of 0:</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1, 2 4, 3 9)', 0);
```

 <span data-ttu-id="00071-130">`LineString` 執行個體中的每個點都可包含 Z (高度) 和 M (測量) 值。</span><span class="sxs-lookup"><span data-stu-id="00071-130">Each point in the `LineString` instance may contain Z (elevation) and M (measure) values.</span></span> <span data-ttu-id="00071-131">此範例會將 M 值加入到上述範例所建立的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-131">This example adds M values to the `LineString` instance created in the example above.</span></span> <span data-ttu-id="00071-132">M 和 Z 可以是 null 值。</span><span class="sxs-lookup"><span data-stu-id="00071-132">M and Z can be null values.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1 NULL 0, 2 4 NULL 12.3, 3 9 NULL 24.5)', 0);
```

 <span data-ttu-id="00071-133">下列範例會示範如何建立具有兩個相同點的 `geometry LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00071-133">The following example shows how to create a `geometry LineString` instance with two points that are the same.</span></span> <span data-ttu-id="00071-134">`IsValid` 的呼叫表示 `LineString` 執行個體無效，而 `MakeValid` 的呼叫會將 `LineString` 執行個體轉換成 `Point`。</span><span class="sxs-lookup"><span data-stu-id="00071-134">A call to `IsValid` indicates that the `LineString` instance is not valid and a call to `MakeValid` will convert the `LineString` instance into a `Point`.</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::STGeomFromText('LINESTRING(1 3, 1 3)',0);
IF @g.STIsValid() = 1
  BEGIN
     SELECT @g.ToString() + ' is a valid LineString.';  
  END
ELSE
  BEGIN
     SELECT @g.ToString() + ' is not a valid LineString.';
     SET @g = @g.MakeValid();
     SELECT @g.ToString() + ' is a valid Point.';  
  END

```

 <span data-ttu-id="00071-135">上述程式碼片段會傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="00071-135">The above code snippet will return the following:</span></span>

```
LINESTRING(1 3, 1 3) is not a valid LineString
POINT(1 3) is a valid Point.
```

## <a name="see-also"></a><span data-ttu-id="00071-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00071-136">See Also</span></span>
 <span data-ttu-id="00071-137">[STLength &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry 資料類型](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)&#41;[STPointOnSurface &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [空間資料 &#40;SQL Server](../spatial/spatial-data-sql-server.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="00071-137">[STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)</span></span>


