---
title: CompoundCurve | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 6a899bbe9a17a64083592e1078e8cac93365f02b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585807"
---
# <a name="compoundcurve"></a><span data-ttu-id="ef173-102">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="ef173-102">CompoundCurve</span></span>
  <span data-ttu-id="ef173-103">`CompoundCurve` 是零個或多個屬於 geometry 或 geography 類型之連續 `CircularString` 或 `LineString` 執行個體的集合。</span><span class="sxs-lookup"><span data-stu-id="ef173-103">A `CompoundCurve` is a collection of zero or more continuous `CircularString` or `LineString` instances of either geometry or geography types.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ef173-104">如需此版本中新空間功能（包括子類型）的詳細描述和範例，請下載技術白皮書 `CompoundCurve` ： [SQL Server 2012 中的新空間功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="ef173-104">For a detailed description and examples of the new spatial features in this release, including the `CompoundCurve` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

 <span data-ttu-id="ef173-105">您可以具現化空的 `CompoundCurve` 執行個體，但是若要讓 `CompoundCurve` 有效，它就必須符合下列準則：</span><span class="sxs-lookup"><span data-stu-id="ef173-105">An empty `CompoundCurve` instance can be instantiated, but for a `CompoundCurve` to be valid it must meet the following criteria:</span></span>

1.  <span data-ttu-id="ef173-106">它至少必須包含一個 `CircularString` 或 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-106">It must contain at least one `CircularString` or `LineString` instance.</span></span>

2.  <span data-ttu-id="ef173-107">`CircularString` 或 `LineString` 執行個體的序列必須是連續的。</span><span class="sxs-lookup"><span data-stu-id="ef173-107">The sequence of `CircularString` or `LineString` instances must be continuous.</span></span>

 <span data-ttu-id="ef173-108">如果 `CompoundCurve` 包含多個 `CircularString` 和實例的序列 `LineString` ，則每個實例的結束端點（最後一個實例除外）都必須是序列中下一個實例的起始端點。</span><span class="sxs-lookup"><span data-stu-id="ef173-108">If a `CompoundCurve` contains a sequence of multiple `CircularString` and `LineString` instances, the ending endpoint for every instance except for the last instance must be the starting endpoint for the next instance in the sequence.</span></span> <span data-ttu-id="ef173-109">這表示，如果序列中前一個執行個體的結束點為 (4 3 7 2)，則序列中下一個執行個體的開始點就必須是 (4 3 7 2)。</span><span class="sxs-lookup"><span data-stu-id="ef173-109">This means that if the ending point of a prior instance in the sequence is (4 3 7 2), the starting point for the next instance in the sequence must be (4 3 7 2).</span></span> <span data-ttu-id="ef173-110">請注意，點的 Z (高度) 和 M (測量) 值也必須相同。</span><span class="sxs-lookup"><span data-stu-id="ef173-110">Note that Z(elevation) and M(measure) values for the point must also be the same.</span></span> <span data-ttu-id="ef173-111">如果兩個點存在差異，就會擲回 `System.FormatException` 。</span><span class="sxs-lookup"><span data-stu-id="ef173-111">If there is a difference in the two points, a `System.FormatException` is thrown.</span></span> <span data-ttu-id="ef173-112">`CircularString` 中的點不需要具有 Z 或 M 值。</span><span class="sxs-lookup"><span data-stu-id="ef173-112">Points in a `CircularString` do not have to have a Z or M value.</span></span> <span data-ttu-id="ef173-113">如果沒有針對前一個執行個體的結束點給定 Z 或 M 值，下一個執行個體的開始點就不得包括 Z 或 M 值。</span><span class="sxs-lookup"><span data-stu-id="ef173-113">If no Z or M values are given for the ending point of the prior instance, the starting point of the next instance cannot include Z or M values.</span></span> <span data-ttu-id="ef173-114">如果前一個序列的結束點為 (4 3)，下一個序列的開始點就必須是 (4 3)，不得為 (4 3 7 2)。</span><span class="sxs-lookup"><span data-stu-id="ef173-114">If the ending point for the prior sequence is (4 3), the starting point for the next sequence must be (4 3); it cannot be (4 3 7 2).</span></span> <span data-ttu-id="ef173-115">`CompoundCurve` 執行個體中的所有點都必須沒有 Z 值或具有相同的 Z 值。</span><span class="sxs-lookup"><span data-stu-id="ef173-115">All points in a `CompoundCurve` instance must have either no Z value or the same Z value.</span></span>

## <a name="compoundcurve-instances"></a><span data-ttu-id="ef173-116">CompoundCurve 執行個體</span><span class="sxs-lookup"><span data-stu-id="ef173-116">CompoundCurve instances</span></span>
 <span data-ttu-id="ef173-117">下圖顯示有效的 `CompoundCurve` 類型。</span><span class="sxs-lookup"><span data-stu-id="ef173-117">The following illustration shows valid `CompoundCurve` types.</span></span>

 ![](../../database-engine/media/f278742e-b861-4555-8b51-3d972b7602bf.png "f278742e-b861-4555-8b51-3d972b7602bf")

### <a name="accepted-instances"></a><span data-ttu-id="ef173-118">已接受的執行個體</span><span class="sxs-lookup"><span data-stu-id="ef173-118">Accepted instances</span></span>
 <span data-ttu-id="ef173-119">如果 `CompoundCurve` 執行個體是空的執行個體或符合下列準則，系統就會接受此執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-119">`CompoundCurve` instance is accepted if it is an empty instance or meets the following criteria.</span></span>

1.  <span data-ttu-id="ef173-120">`CompoundCurve` 執行個體所包含的所有執行個體都是已接受的圓弧線段執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-120">All the instances contained by `CompoundCurve` instance are accepted circular arc segment instances.</span></span> <span data-ttu-id="ef173-121">如需已接受之圓弧線段執行個體的詳細資訊，請參閱 [LineString](linestring.md) 和 [CircularString](circularstring.md)。</span><span class="sxs-lookup"><span data-stu-id="ef173-121">For more information on accepted circular arc segment instances, see [LineString](linestring.md) and [CircularString](circularstring.md).</span></span>

2.  <span data-ttu-id="ef173-122">`CompoundCurve` 執行個體中的所有圓弧線段都已連接。</span><span class="sxs-lookup"><span data-stu-id="ef173-122">All of the circular arc segments in the `CompoundCurve` instance are connected.</span></span> <span data-ttu-id="ef173-123">每個後續圓弧線段的第一個點都與前一個圓弧線段的最後一個點相同。</span><span class="sxs-lookup"><span data-stu-id="ef173-123">The first point for each succeeding circular arc segment is the same as the last point on the preceding circular arc segment.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ef173-124">這包括 Z 和 M 座標。</span><span class="sxs-lookup"><span data-stu-id="ef173-124">This includes the Z and M coordinates.</span></span> <span data-ttu-id="ef173-125">因此，X、Y、Z 和 M 這四個座標都必須相同。</span><span class="sxs-lookup"><span data-stu-id="ef173-125">So, all four coordinates X, Y, Z, and M must be the same.</span></span>

3.  <span data-ttu-id="ef173-126">所有包含的執行個體都不是空的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-126">None of the contained instances are empty instances.</span></span>

 <span data-ttu-id="ef173-127">下列範例會顯示已接受的 `CompoundCurve` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-127">The following example shows accepted `CompoundCurve` instances.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';
```

 <span data-ttu-id="ef173-128">下列範例會顯示無法接受的 `CompoundCurve` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-128">The following example shows `CompoundCurve` instances that are not accepted.</span></span> <span data-ttu-id="ef173-129">這些執行個體會擲回 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="ef173-129">These instances throw `System.FormatException`.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';
```

### <a name="valid-instances"></a><span data-ttu-id="ef173-130">有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="ef173-130">Valid instances</span></span>
 <span data-ttu-id="ef173-131">如果 `CompoundCurve` 執行個體符合下列準則，它就是有效的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-131">A `CompoundCurve` instance is valid if it meets the following criteria.</span></span>

1.  <span data-ttu-id="ef173-132">系統已接受 `CompoundCurve` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-132">The `CompoundCurve` instance is accepted.</span></span>

2.  <span data-ttu-id="ef173-133">`CompoundCurve` 執行個體所包含的所有圓弧線段執行個體都是有效的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-133">All circular arc segment instances contained by the `CompoundCurve` instance are valid instances.</span></span>

 <span data-ttu-id="ef173-134">下列範例會顯示有效的 `CompoundCurve` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-134">The following example shows valid `CompoundCurve` instances.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();

```

 <span data-ttu-id="ef173-135">`@g3` 有效，因為 `CircularString` 執行個體有效。</span><span class="sxs-lookup"><span data-stu-id="ef173-135">`@g3` is valid because the `CircularString` instance is valid.</span></span> <span data-ttu-id="ef173-136">如需有關實例有效性的詳細資訊 `CircularString` ，請參閱[CircularString](circularstring.md)。</span><span class="sxs-lookup"><span data-stu-id="ef173-136">For more information on the validity of the `CircularString` instance, see [CircularString](circularstring.md).</span></span>

 <span data-ttu-id="ef173-137">下列範例會顯示無效的 `CompoundCurve` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-137">The following example shows `CompoundCurve` instances that are not valid.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="ef173-138">`@g1` 無效，因為第二個執行個體不是有效的 LineString 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-138">`@g1` is not valid because the second instance is not a valid LineString instance.</span></span> <span data-ttu-id="ef173-139">`@g2` 無效，因為 `LineString` 執行個體無效。</span><span class="sxs-lookup"><span data-stu-id="ef173-139">`@g2` is not valid because the `LineString` instance is not valid.</span></span> <span data-ttu-id="ef173-140">`@g3` 無效，因為 `CircularString` 執行個體無效。</span><span class="sxs-lookup"><span data-stu-id="ef173-140">`@g3` is not valid because the `CircularString` instance is not valid.</span></span> <span data-ttu-id="ef173-141">如需有效和實例的詳細資訊 `CircularString` `LineString` ，請參閱[CircularString](circularstring.md)和[LineString](linestring.md)。</span><span class="sxs-lookup"><span data-stu-id="ef173-141">For more information on valid `CircularString` and `LineString` instances, see [CircularString](circularstring.md) and [LineString](linestring.md).</span></span>

## <a name="examples"></a><span data-ttu-id="ef173-142">範例</span><span class="sxs-lookup"><span data-stu-id="ef173-142">Examples</span></span>

### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a><span data-ttu-id="ef173-143">A.</span><span class="sxs-lookup"><span data-stu-id="ef173-143">A.</span></span> <span data-ttu-id="ef173-144">使用空的 CompooundCurve 來具現化 geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="ef173-144">Instantiating a geometry instance with an empty CompooundCurve</span></span>
 <span data-ttu-id="ef173-145">下列範例會示範如何建立空的 `CompoundCurve` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="ef173-145">The following example shows how to create an empty `CompoundCurve` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');
```

### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a><span data-ttu-id="ef173-146">B.</span><span class="sxs-lookup"><span data-stu-id="ef173-146">B.</span></span> <span data-ttu-id="ef173-147">在相同的陳述式中使用 CompoundCurve 來宣告和具現化 geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="ef173-147">Declaring and instantiating a geometry instance using a CompoundCurve in the same statement</span></span>
 <span data-ttu-id="ef173-148">下列範例會示範如何在相同的陳述式中使用 `geometry` 來宣告和初始化 `CompoundCurve`執行個體：</span><span class="sxs-lookup"><span data-stu-id="ef173-148">The following example shows how to declare and initialize a `geometry` instance with a `CompoundCurve`in the same statement:</span></span>

```sql
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';
```

### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a><span data-ttu-id="ef173-149">C.</span><span class="sxs-lookup"><span data-stu-id="ef173-149">C.</span></span> <span data-ttu-id="ef173-150">使用 CompoundCurve 來具現化 geography 執行個體</span><span class="sxs-lookup"><span data-stu-id="ef173-150">Instantiating a geography instance with a CompoundCurve</span></span>
 <span data-ttu-id="ef173-151">下列範例會示範如何使用 `CompoundCurve` 來宣告和初始化 `geography` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="ef173-151">The following example shows how to declare and initialize a `geography` instance with a `CompoundCurve`:</span></span>

```sql
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';
```

### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a><span data-ttu-id="ef173-152">D.</span><span class="sxs-lookup"><span data-stu-id="ef173-152">D.</span></span> <span data-ttu-id="ef173-153">將正方形儲存在 CompoundCurve 執行個體中</span><span class="sxs-lookup"><span data-stu-id="ef173-153">Storing a square in a CompoundCurve instance</span></span>
 <span data-ttu-id="ef173-154">下列範例會以兩種不同的方式使用 `CompoundCurve` 執行個體來儲存正方形。</span><span class="sxs-lookup"><span data-stu-id="ef173-154">The following example uses two different ways to use a `CompoundCurve` instance to store a square.</span></span>

```sql
DECLARE @g1 geometry, @g2 geometry;
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');
SELECT @g1.STLength(), @g2.STLength();
```

 <span data-ttu-id="ef173-155">`@g1` 和 `@g2` 的長度都相同。</span><span class="sxs-lookup"><span data-stu-id="ef173-155">The lengths for both `@g1` and `@g2` are the same.</span></span> <span data-ttu-id="ef173-156">在此範例中，請注意 `CompoundCurve` 執行個體可以儲存一個或多個 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-156">Notice from the example that a `CompoundCurve` instance can store one or more instances of `LineString`.</span></span>

### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a><span data-ttu-id="ef173-157">E.</span><span class="sxs-lookup"><span data-stu-id="ef173-157">E.</span></span> <span data-ttu-id="ef173-158">使用 CompoundCurve 搭配多個 CircularString 來具現化 geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="ef173-158">Instantiating a geometry instance using a CompoundCurve with multiple CircularStrings</span></span>
 <span data-ttu-id="ef173-159">下列範例會示範如何使用兩個不同的 `CircularString` 執行個體來初始化 `CompoundCurve`執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-159">The following example shows how to use two different `CircularString` instances to initialize a `CompoundCurve`.</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');
SELECT @g.STLength();
```

 <span data-ttu-id="ef173-160">這會產生下列輸出： 12.566370 .。。這相當於 4&#x03c0; (4 \* pi) 。</span><span class="sxs-lookup"><span data-stu-id="ef173-160">This produces the following output: 12.566370... which is the equivalent of 4&#x03c0; (4 \* pi).</span></span> <span data-ttu-id="ef173-161">在此範例中， `CompoundCurve` 執行個體會儲存半徑為 2 的圓形。</span><span class="sxs-lookup"><span data-stu-id="ef173-161">The `CompoundCurve` instance in the example stores a circle with a radius of 2.</span></span> <span data-ttu-id="ef173-162">前兩個程式碼範例都不需要使用 `CompoundCurve`。</span><span class="sxs-lookup"><span data-stu-id="ef173-162">Both of the previous code examples did not have to use a `CompoundCurve`.</span></span> <span data-ttu-id="ef173-163">在第一個範例中， `LineString` 執行個體已經簡化了，而在第二個範例中， `CircularString` 執行個體也已經簡化了。</span><span class="sxs-lookup"><span data-stu-id="ef173-163">For the first example a `LineString` instance would have been simpler, and a `CircularString` instance would have been simpler for the second example.</span></span> <span data-ttu-id="ef173-164">不過，下一個範例會顯示 `CompoundCurve` 提供較佳替代方式之處。</span><span class="sxs-lookup"><span data-stu-id="ef173-164">However, the next example shows where a `CompoundCurve` provides a better alternative.</span></span>

### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a><span data-ttu-id="ef173-165">F.</span><span class="sxs-lookup"><span data-stu-id="ef173-165">F.</span></span> <span data-ttu-id="ef173-166">使用 CompoundCurve 來儲存半圓形</span><span class="sxs-lookup"><span data-stu-id="ef173-166">Using a CompoundCurve to store a semicircle</span></span>
 <span data-ttu-id="ef173-167">下列範例會使用 `CompoundCurve` 執行個體來儲存半圓形。</span><span class="sxs-lookup"><span data-stu-id="ef173-167">The following example uses a `CompoundCurve` instance to store a semicircle.</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');
SELECT @g.STLength();
```

### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a><span data-ttu-id="ef173-168">G.</span><span class="sxs-lookup"><span data-stu-id="ef173-168">G.</span></span> <span data-ttu-id="ef173-169">將多個 CircularString 和 LineString 執行個體儲存在 CompoundCurve 中</span><span class="sxs-lookup"><span data-stu-id="ef173-169">Storing multiple CircularString and LineString instances in a CompoundCurve</span></span>
 <span data-ttu-id="ef173-170">下列範例會示範如何使用 `CircularString` 來儲存多個 `LineString` 和 `CompoundCurve`執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-170">The following example shows how multiple `CircularString` and `LineString` instances can be stored by using a `CompoundCurve`.</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');
SELECT @g.STLength();
```

### <a name="h-storing-instances-with-z-and-m-values"></a><span data-ttu-id="ef173-171">H.</span><span class="sxs-lookup"><span data-stu-id="ef173-171">H.</span></span> <span data-ttu-id="ef173-172">儲存具有 Z 和 M 值的執行個體</span><span class="sxs-lookup"><span data-stu-id="ef173-172">Storing instances with Z and M values</span></span>
 <span data-ttu-id="ef173-173">下列範例會示範如何使用 `CompoundCurve` 執行個體來儲存具有 Z 和 M 值的 `CircularString` 和 `LineString` 執行個體序列。</span><span class="sxs-lookup"><span data-stu-id="ef173-173">The following example shows how to use a `CompoundCurve` instance to store a sequence of `CircularString` and `LineString` instances with both Z and M values.</span></span>

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');
```

### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a><span data-ttu-id="ef173-174">I.</span><span class="sxs-lookup"><span data-stu-id="ef173-174">I.</span></span> <span data-ttu-id="ef173-175">說明必須明確宣告 CircularString 執行個體的原因</span><span class="sxs-lookup"><span data-stu-id="ef173-175">Illustrating why CircularString instances must be explicitly declared</span></span>
 <span data-ttu-id="ef173-176">下列範例會顯示必須明確宣告 `CircularString` 執行個體的原因。</span><span class="sxs-lookup"><span data-stu-id="ef173-176">The following example shows why `CircularString` instances must be explicitly declared.</span></span> <span data-ttu-id="ef173-177">程式設計人員正嘗試將圓形儲存在 `CompoundCurve` 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="ef173-177">The programmer is trying to store a circle in a `CompoundCurve` instance.</span></span>

```sql
DECLARE @g1 geometry;  
DECLARE @g2 geometry;
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount
```

 <span data-ttu-id="ef173-178">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="ef173-178">The output is as follows:</span></span>

```
Circle One11.940039...
Circle Two12.566370...
```

 <span data-ttu-id="ef173-179">Circle 二的周邊大約是 4&#x03c0; (4 \* pi) ，這是周邊的實際值。</span><span class="sxs-lookup"><span data-stu-id="ef173-179">The perimeter for Circle Two is approximately 4&#x03c0; (4 \* pi), which is the actual value for the perimeter.</span></span> <span data-ttu-id="ef173-180">不過，Circle One 的圓周則明顯不精確。</span><span class="sxs-lookup"><span data-stu-id="ef173-180">However, the perimeter for Circle One is significantly inaccurate.</span></span> <span data-ttu-id="ef173-181">Circle One 的 `CompoundCurve` 執行個體會儲存一個圓弧線段 (ABC) 和兩個直線線段 (CD, DA)。</span><span class="sxs-lookup"><span data-stu-id="ef173-181">Circle One's `CompoundCurve` instance stores one circular arc segment (ABC) and two line segments (CD, DA).</span></span> <span data-ttu-id="ef173-182">`CompoundCurve` 執行個體必須儲存兩個圓弧線段 (ABC, CDA) 才能定義圓形。</span><span class="sxs-lookup"><span data-stu-id="ef173-182">The `CompoundCurve` instance has to store two circular arc segments (ABC, CDA) to define a circle.</span></span> <span data-ttu-id="ef173-183">`LineString` 執行個體會在 Circle One 的 `CompoundCurve` 執行個體中定義第二組點 (4 2, 2 4, 0 2)。</span><span class="sxs-lookup"><span data-stu-id="ef173-183">A `LineString` instance defines the second set of points (4 2, 2 4, 0 2) in Circle One's `CompoundCurve` instance.</span></span> <span data-ttu-id="ef173-184">您必須在 `CircularString` 內部明確宣告 `CompoundCurve`執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef173-184">You have to explicitly declare a `CircularString` instance inside a `CompoundCurve`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef173-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef173-185">See Also</span></span>
 <span data-ttu-id="ef173-186">[STIsValid &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STLength &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [LineString](linestring.md) [CircularString](circularstring.md) [空間資料類型總覽](spatial-data-types-overview.md)[點](point.md)</span><span class="sxs-lookup"><span data-stu-id="ef173-186">[STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [LineString](linestring.md) [CircularString](circularstring.md) [Spatial Data Types Overview](spatial-data-types-overview.md) [Point](point.md)</span></span>


