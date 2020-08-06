---
title: MultiPolygon | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f18fd2485c9b2e62586d9f3e81f76f6cf680dbfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606164"
---
# <a name="multipolygon"></a><span data-ttu-id="bc443-102">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="bc443-102">MultiPolygon</span></span>
  <span data-ttu-id="bc443-103">`MultiPolygon` 執行個體是零或多個 `Polygon` 執行個體的集合。</span><span class="sxs-lookup"><span data-stu-id="bc443-103">A `MultiPolygon` instance is a collection of zero or more `Polygon` instances.</span></span>

## <a name="polygon-instances"></a><span data-ttu-id="bc443-104">多邊形執行個體</span><span class="sxs-lookup"><span data-stu-id="bc443-104">Polygon Instances</span></span>
 <span data-ttu-id="bc443-105">下圖顯示 `MultiPolygon` 執行個體的範例。</span><span class="sxs-lookup"><span data-stu-id="bc443-105">The illustration below shows examples of `MultiPolygon` instances.</span></span>

 <span data-ttu-id="bc443-106">![幾何 MultiPolygon 執行個體的範例](../../database-engine/media/multipolygon.gif "幾何 MultiPolygon 執行個體的範例")</span><span class="sxs-lookup"><span data-stu-id="bc443-106">![Examples of geometry MultiPolygon instances](../../database-engine/media/multipolygon.gif "Examples of geometry MultiPolygon instances")</span></span>

 <span data-ttu-id="bc443-107">如本圖所示：</span><span class="sxs-lookup"><span data-stu-id="bc443-107">As shown in the illustration:</span></span>

-   <span data-ttu-id="bc443-108">圖 1 是具有兩個 `Polygon` 元素的 `MultiPolygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-108">Figure 1 is a `MultiPolygon` instance with two `Polygon` elements.</span></span> <span data-ttu-id="bc443-109">界限是由兩個外部環形和三個內部環形所定義。</span><span class="sxs-lookup"><span data-stu-id="bc443-109">The boundary is defined by the two exterior rings and the three interior rings.</span></span>

-   <span data-ttu-id="bc443-110">圖 2 是具有兩個 `MultiPolygon` 元素的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-110">Figure 2 is a `MultiPolygon` instance with two `Polygon` elements.</span></span> <span data-ttu-id="bc443-111">界限是由兩個外部環形和三個內部環形所定義。</span><span class="sxs-lookup"><span data-stu-id="bc443-111">The boundary is defined by the two exterior rings and the three interior rings.</span></span> <span data-ttu-id="bc443-112">這兩個 `Polygon` 元素會在正切點相交。</span><span class="sxs-lookup"><span data-stu-id="bc443-112">The two `Polygon` elements intersect at a tangent point.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="bc443-113">已接受的執行個體</span><span class="sxs-lookup"><span data-stu-id="bc443-113">Accepted Instances</span></span>
 <span data-ttu-id="bc443-114">如果下列其中一個條件成立，則接受 `MultiPolygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-114">A `MultiPolygon` instance is accepted one of the following conditions is met.</span></span>

-   <span data-ttu-id="bc443-115">它是空的 `MultiPolygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-115">It is an empty `MultiPolygon` instance.</span></span>

-   <span data-ttu-id="bc443-116">組成 `MultiPolygon` 執行個體的所有執行個體都是可接受的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-116">All instances comprising the `MultiPolygon` instance are accepted `Polygon` instances.</span></span> <span data-ttu-id="bc443-117">如需已接受之實例的詳細資訊 `Polygon` ，請參閱[多邊形](../spatial/polygon.md)。</span><span class="sxs-lookup"><span data-stu-id="bc443-117">For more information on accepted `Polygon` instances, see [Polygon](../spatial/polygon.md).</span></span>

 <span data-ttu-id="bc443-118">下列範例會顯示可接受的 `MultiPolygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-118">The following examples show accepted `MultiPolygon` instances.</span></span>

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
```

 <span data-ttu-id="bc443-119">下列範例示範會擲出 `System.FormatException`的 MultiPolygon 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-119">The following example shows a MultiPolygon instance that will throw a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';
```

 <span data-ttu-id="bc443-120">MultiPolygon 中的第二個執行個體是 LineString 執行個體，不是可接受的 Polygon 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-120">The second instance in the MultiPolygon is a LineString instance and not an accepted Polygon instance.</span></span>

### <a name="valid-instances"></a><span data-ttu-id="bc443-121">有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="bc443-121">Valid Instances</span></span>
 <span data-ttu-id="bc443-122">如果 `MultiPolygon` 執行個體是空的 `MultiPolygon` 執行個體或符合下列準則，則為有效的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-122">A `MultiPolygon` instance is valid if it is an empty `MultiPolygon` instance or if it meets the following criteria.</span></span>

1.  <span data-ttu-id="bc443-123">組成 `MultiPolygon` 執行個體的所有執行個體都是有效的 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-123">All of the instances comprising the `MultiPolygon` instance are valid `Polygon` instances.</span></span> <span data-ttu-id="bc443-124">如需有效的 `Polygon` 實例，請參閱[多邊形](../spatial/polygon.md)。</span><span class="sxs-lookup"><span data-stu-id="bc443-124">For valid `Polygon` instances, see [Polygon](../spatial/polygon.md).</span></span>

2.  <span data-ttu-id="bc443-125">組成 `Polygon` 執行個體的所有 `MultiPolygon` 執行個體彼此不會重疊。</span><span class="sxs-lookup"><span data-stu-id="bc443-125">None of the `Polygon` instances comprising the `MultiPolygon` instance overlap.</span></span>

 <span data-ttu-id="bc443-126">下列範例示範兩個有效的 `MultiPolygon` 執行個體和一個無效的 `MultiPolygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-126">The following example shows two valid `MultiPolygon` instances and one invalid `MultiPolygon` instance.</span></span>

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="bc443-127">`@g2` 有效，因為這兩個 `Polygon` 執行個體只在一個相切點接觸。</span><span class="sxs-lookup"><span data-stu-id="bc443-127">`@g2` is valid because the two `Polygon` instances touch only at a tangent point.</span></span> <span data-ttu-id="bc443-128">`@g3` 無效，因為這兩個 `Polygon` 執行個體的內部互相重疊。</span><span class="sxs-lookup"><span data-stu-id="bc443-128">`@g3` is not valid because the interiors of the two `Polygon` instances overlap each other.</span></span>

## <a name="examples"></a><span data-ttu-id="bc443-129">範例</span><span class="sxs-lookup"><span data-stu-id="bc443-129">Examples</span></span>
 <span data-ttu-id="bc443-130">下列範例示範 `geometry``MultiPolygon` 執行個體的建立作業，並傳回第二個元件的 Well-Known Text (WKT)。</span><span class="sxs-lookup"><span data-stu-id="bc443-130">The following example shows the creation of a `geometry``MultiPolygon` instance and returns the Well-Known Text (WKT) of the second component.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');
SELECT @g.STGeometryN(2).STAsText();
```

 <span data-ttu-id="bc443-131">此範例會具現化空的 `MultiPolygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc443-131">This example instantiates an empty `MultiPolygon` instance.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');
```

## <a name="see-also"></a><span data-ttu-id="bc443-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc443-132">See Also</span></span>
 <span data-ttu-id="bc443-133">[多邊形](../spatial/polygon.md) [STArea &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STCentroid &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [空間資料 &#40;SQL Server](../spatial/spatial-data-sql-server.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="bc443-133">[Polygon](../spatial/polygon.md) [STArea &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STCentroid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)</span></span>


