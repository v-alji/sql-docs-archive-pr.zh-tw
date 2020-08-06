---
title: MultiLineString | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fdd093d99d055df8e15fc22e3e570e6805e35d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606168"
---
# <a name="multilinestring"></a><span data-ttu-id="6e243-102">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="6e243-102">MultiLineString</span></span>
  <span data-ttu-id="6e243-103">`MultiLineString`是零個或多個 `geometry` 或**geographyLineString**實例的集合。</span><span class="sxs-lookup"><span data-stu-id="6e243-103">A `MultiLineString` is a collection of zero or more `geometry` or **geographyLineString** instances.</span></span>  
  
## <a name="multilinestring-instances"></a><span data-ttu-id="6e243-104">MultiLineString 執行個體</span><span class="sxs-lookup"><span data-stu-id="6e243-104">MultiLineString instances</span></span>  
 <span data-ttu-id="6e243-105">下圖顯示 `MultiLineString` 執行個體的範例。</span><span class="sxs-lookup"><span data-stu-id="6e243-105">The illustration below shows examples of `MultiLineString` instances.</span></span>  
  
 <span data-ttu-id="6e243-106">![幾何 MultiLineString 執行個體的範例](../../database-engine/media/multilinestring.gif "幾何 MultiLineString 執行個體的範例")</span><span class="sxs-lookup"><span data-stu-id="6e243-106">![Examples of geometry MultiLineString instances](../../database-engine/media/multilinestring.gif "Examples of geometry MultiLineString instances")</span></span>  
  
 <span data-ttu-id="6e243-107">如本圖所示：</span><span class="sxs-lookup"><span data-stu-id="6e243-107">As shown in the illustration:</span></span>  
  
-   <span data-ttu-id="6e243-108">[圖 1] 是一個簡單的 `MultiLineString` 實例，其界限是其兩個元素的四個端點 `LineString` 。</span><span class="sxs-lookup"><span data-stu-id="6e243-108">Figure 1 is a simple `MultiLineString` instance whose boundary is the four endpoints of its two `LineString` elements.</span></span>  
  
-   <span data-ttu-id="6e243-109">圖 2 是簡單 `MultiLineString` 執行個體，因為只有 `LineString` 元素的端點才會相交。</span><span class="sxs-lookup"><span data-stu-id="6e243-109">Figure 2 is a simple `MultiLineString` instance because only the endpoints of the `LineString` elements intersect.</span></span> <span data-ttu-id="6e243-110">界限是兩個非重疊的端點。</span><span class="sxs-lookup"><span data-stu-id="6e243-110">The boundary is the two non-overlapping endpoints.</span></span>  
  
-   <span data-ttu-id="6e243-111">圖 3 是非簡單的 `MultiLineString` 執行個體，因為它的其中一個 `LineString` 元素的內部會相交。</span><span class="sxs-lookup"><span data-stu-id="6e243-111">Figure 3 is a nonsimple `MultiLineString` instance because the interior of one of its `LineString` elements is intersected.</span></span> <span data-ttu-id="6e243-112">此 `MultiLineString` 執行個體的界限是這四個端點。</span><span class="sxs-lookup"><span data-stu-id="6e243-112">The boundary of this `MultiLineString` instance is the four endpoints.</span></span>  
  
-   <span data-ttu-id="6e243-113">圖 4 是非簡單、非封閉的 `MultiLineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e243-113">Figure 4 is a nonsimple, nonclosed `MultiLineString` instance.</span></span>  
  
-   <span data-ttu-id="6e243-114">圖 5 是簡單、非封閉的 `MultiLineString`。</span><span class="sxs-lookup"><span data-stu-id="6e243-114">Figure 5 is a simple, nonclosed `MultiLineString`.</span></span> <span data-ttu-id="6e243-115">它不會關閉，因為它的 `LineStrings` 元素不會關閉。</span><span class="sxs-lookup"><span data-stu-id="6e243-115">It is not closed because its `LineStrings` elements are not closed.</span></span> <span data-ttu-id="6e243-116">因為任何 `LineStrings` 執行個體的內部都不相交，所以它是簡單的。</span><span class="sxs-lookup"><span data-stu-id="6e243-116">It is simple because none of the interiors of any of the `LineStrings` instances intersect.</span></span>  
  
-   <span data-ttu-id="6e243-117">圖 6 是簡單、封閉的 `MultiLineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e243-117">Figure 6 is a simple, closed `MultiLineString` instance.</span></span> <span data-ttu-id="6e243-118">它是封閉的，因為它的所有元素都是封閉的。</span><span class="sxs-lookup"><span data-stu-id="6e243-118">It is closed because all its elements are closed.</span></span> <span data-ttu-id="6e243-119">因為它的所有元素在內部都不相交，所以它是簡單的。</span><span class="sxs-lookup"><span data-stu-id="6e243-119">It is simple because none of its elements intersect at the interiors.</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="6e243-120">已接受的執行個體</span><span class="sxs-lookup"><span data-stu-id="6e243-120">Accepted instances</span></span>  
 <span data-ttu-id="6e243-121">若要接受 `MultiLineString`執行個體，則該執行個體必須是空的，或是僅由可接受的 `LineString` 執行個體組成。</span><span class="sxs-lookup"><span data-stu-id="6e243-121">For a `MultiLineString` instance to be accepted it must either be empty or comprised of only `LineString` intances that are accepted.</span></span> <span data-ttu-id="6e243-122">如需已接受之實例的詳細資訊 `LineString` ，請參閱[LineString](../spatial/linestring.md)。</span><span class="sxs-lookup"><span data-stu-id="6e243-122">For more information on accepted `LineString` instances, see [LineString](../spatial/linestring.md).</span></span> <span data-ttu-id="6e243-123">以下為可接受之 `MultiLineString` 執行個體的範例。</span><span class="sxs-lookup"><span data-stu-id="6e243-123">The following are examples of accepted `MultiLineString` instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 <span data-ttu-id="6e243-124">下列範例會擲回 `System.FormatException`，因為第二個 `LineString` 執行個體無效。</span><span class="sxs-lookup"><span data-stu-id="6e243-124">The following example throws a `System.FormatException` because the second `LineString` instance is not valid.</span></span>  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a><span data-ttu-id="6e243-125">有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="6e243-125">Valid instances</span></span>  
 <span data-ttu-id="6e243-126">`MultiLineString` 執行個體必須符合下列準則，才會是有效的：</span><span class="sxs-lookup"><span data-stu-id="6e243-126">For a `MultiLineString` instance to be valid it must meet the following criteria:</span></span>  
  
1.  <span data-ttu-id="6e243-127">組成 `MultiLineString` 執行個體的所有執行個體必須都是有效的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e243-127">All instances comprising the `MultiLineString` instance must be valid `LineString` instances.</span></span>  
  
2.  <span data-ttu-id="6e243-128">組成 `LineString` 執行個體的任兩個 `MultiLineString` 執行個體都不可在間隔上重疊。</span><span class="sxs-lookup"><span data-stu-id="6e243-128">No two `LineString` instances comprising the `MultiLineString` instance may overlap over an interval.</span></span> <span data-ttu-id="6e243-129">`LineString` 執行個體只能在有限的點數內彼此交集或接觸，或是接觸其他 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e243-129">The `LineString` instances can only intersect or touch themselves or other `LineString` instances at a finite number of points.</span></span>  
  
 <span data-ttu-id="6e243-130">下列範例示範三個有效的 `MultiLineString` 執行個體和一個無效的 `MultiLineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e243-130">The following example shows three valid `MultiLineString` instances and one `MultiLineString` instance that is not valid.</span></span>  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 <span data-ttu-id="6e243-131">`@g4` 無效，因為第二個 `LineString` 執行個體與第一個 `LineString` 執行個體於間隔處重疊。</span><span class="sxs-lookup"><span data-stu-id="6e243-131">`@g4` is not valid because the second `LineString` instance overlaps the first `LineString` instance at an interval.</span></span> <span data-ttu-id="6e243-132">兩者以無限點數接觸。</span><span class="sxs-lookup"><span data-stu-id="6e243-132">They touch at an infinite number of points.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6e243-133">範例</span><span class="sxs-lookup"><span data-stu-id="6e243-133">Examples</span></span>  
 <span data-ttu-id="6e243-134">下列範例會建立包含兩個具有 SRID 0 之 `geometry``MultiLineString` 元素的簡單 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e243-134">The following example creates a simple `geometry``MultiLineString` instance containing two `LineString` elements with the SRID 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 <span data-ttu-id="6e243-135">若要使用不同的 SRID 來具現化這個執行個體，請使用 `STGeomFromText()` 或 `STMLineStringFromText()`。</span><span class="sxs-lookup"><span data-stu-id="6e243-135">To instantiate this instance with a different SRID, use `STGeomFromText()` or `STMLineStringFromText()`.</span></span> <span data-ttu-id="6e243-136">您也可以使用 `Parse()` ，然後修改 SRID，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6e243-136">You can also use `Parse()` and then modify the SRID, as shown in the following example.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e243-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e243-137">See Also</span></span>  
 <span data-ttu-id="6e243-138">[STLength &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="6e243-138">[STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) </span></span>  
 <span data-ttu-id="6e243-139">[STIsClosed &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="6e243-139">[STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) </span></span>  
 <span data-ttu-id="6e243-140">[LineString](../spatial/linestring.md) </span><span class="sxs-lookup"><span data-stu-id="6e243-140">[LineString](../spatial/linestring.md) </span></span>  
 [<span data-ttu-id="6e243-141">空間資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6e243-141">Spatial Data &#40;SQL Server&#41;</span></span>](../spatial/spatial-data-sql-server.md)  
  
  
