---
title: 查詢最接近像素的空間資料 | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 644b3e5cfdaeff7457639bc2da77260b64011735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606158"
---
# <a name="query-spatial-data-for-nearest-neighbor"></a><span data-ttu-id="e5628-102">查詢最接近像素的空間資料</span><span class="sxs-lookup"><span data-stu-id="e5628-102">Query Spatial Data for Nearest Neighbor</span></span>
  <span data-ttu-id="e5628-103">最接近像素查詢是搭配空間資料使用的常見查詢。</span><span class="sxs-lookup"><span data-stu-id="e5628-103">A common query used with spatial data is the Nearest Neighbor query.</span></span> <span data-ttu-id="e5628-104">最接近像素查詢是用來尋找最接近特定空間物件的空間物件。</span><span class="sxs-lookup"><span data-stu-id="e5628-104">Nearest Neighbor queries are used to find the closest spatial objects to a specific spatial object.</span></span> <span data-ttu-id="e5628-105">例如，網站的商店定位器通常必須尋找最接近客戶位置的商店位置。</span><span class="sxs-lookup"><span data-stu-id="e5628-105">For example a store locater for a Web site often must find the closest store locations to a customer location.</span></span>  
  
 <span data-ttu-id="e5628-106">您可以用各種有效的查詢格式來撰寫最接近像素查詢，但是若要讓最接近像素查詢使用空間索引，則必須使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="e5628-106">A Nearest Neighbor query can be written in a variety of valid query formats, but for the Nearest Neighbor query to use a spatial index the following syntax must be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5628-107">語法</span><span class="sxs-lookup"><span data-stu-id="e5628-107">Syntax</span></span>  
  
```vb  
SELECT TOP ( number )  
        [ WITH TIES ]  
        [ * | expression ]   
        [, ...]  
    FROM spatial_table_reference, ...   
        [ WITH   
            (   
                [ INDEX ( index_ref ) ]   
                [ , SPATIAL_WINDOW_MAX_CELLS = <value>]   
                [ ,... ]   
            )   
        ]  
    WHERE   
        column_ref.STDistance ( @spatial_ object )   
            {   
                [ IS NOT NULL ] | [ < const ] | [ > const ]   
                | [ <= const ] | [ >= const ] | [ <> const ] ]   
            }  
            [ AND { other_predicate } ]   
    }  
    ORDER BY column_ref.STDistance ( @spatial_ object ) [ ,...n ]  
[ ; ]  
  
```  
  
## <a name="nearest-neighbor-query-and-spatial-indexes"></a><span data-ttu-id="e5628-108">最接近像素查詢和空間索引</span><span class="sxs-lookup"><span data-stu-id="e5628-108">Nearest Neighbor Query and Spatial Indexes</span></span>  
 <span data-ttu-id="e5628-109">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，`TOP` 及 `ORDER BY` 子句是用來針對空間資料資料行執行最接近像素查詢。</span><span class="sxs-lookup"><span data-stu-id="e5628-109">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `TOP` and `ORDER BY` clauses are used to perform a Nearest Neighbor query on spatial data columns.</span></span> <span data-ttu-id="e5628-110">`ORDER BY` 子句包含空間資料行資料類型的 `STDistance()` 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="e5628-110">The `ORDER BY` clause contains a call to the `STDistance()` method for the spatial column data type.</span></span> <span data-ttu-id="e5628-111">`TOP` 子句會指出要針對查詢傳回的物件數目。</span><span class="sxs-lookup"><span data-stu-id="e5628-111">The `TOP` clause indicates the number of objects to return for the query.</span></span>  
  
 <span data-ttu-id="e5628-112">若要讓最接近像素查詢使用空間索引，您必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="e5628-112">The following requirements must be met for a Nearest Neighbor query to use a spatial index:</span></span>  
  
1.  <span data-ttu-id="e5628-113">空間索引必須存在其中一個空間資料行上，而且 `STDistance()` 方法必須在 `WHERE` 和 `ORDER BY` 子句中使用該資料行。</span><span class="sxs-lookup"><span data-stu-id="e5628-113">A spatial index must be present on one of the spatial columns and the `STDistance()` method must use that column in the `WHERE` and `ORDER BY` clauses.</span></span>  
  
2.  <span data-ttu-id="e5628-114">`TOP` 子句不得包含 `PERCENT` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e5628-114">The `TOP` clause cannot contain a `PERCENT` statement.</span></span>  
  
3.  <span data-ttu-id="e5628-115">`WHERE` 子句必須包含 `STDistance()` 方法。</span><span class="sxs-lookup"><span data-stu-id="e5628-115">The `WHERE` clause must contain a `STDistance()` method.</span></span>  
  
4.  <span data-ttu-id="e5628-116">如果 `WHERE` 子句中存在多個述詞，則包含 `STDistance()` 方法的述詞就必須透過 `AND` 結合連接至其他述詞。</span><span class="sxs-lookup"><span data-stu-id="e5628-116">If there are multiple predicates in the `WHERE` clause then the predicate containing `STDistance()` method must be connected by an `AND` conjunction to the other predicates.</span></span> <span data-ttu-id="e5628-117">`STDistance()` 方法不得位於 `WHERE` 子句的選擇性部分中。</span><span class="sxs-lookup"><span data-stu-id="e5628-117">The `STDistance()` method cannot be in an optional part of the `WHERE` clause.</span></span>  
  
5.  <span data-ttu-id="e5628-118">`ORDER BY` 子句中的第一個運算式必須使用 `STDistance()` 方法。</span><span class="sxs-lookup"><span data-stu-id="e5628-118">The first expression in the `ORDER BY` clause must use the `STDistance()` method.</span></span>  
  
6.  <span data-ttu-id="e5628-119">`ORDER BY` 子句中第一個 `STDistance()` 運算式的排序次序必須是 `ASC`。</span><span class="sxs-lookup"><span data-stu-id="e5628-119">Sort order for the first `STDistance()` expression in the `ORDER BY` clause must be `ASC`.</span></span>  
  
7.  <span data-ttu-id="e5628-120">`STDistance` 傳回 `NULL` 的所有資料列都必須篩選出來。</span><span class="sxs-lookup"><span data-stu-id="e5628-120">All the rows for which `STDistance` returns `NULL` must be filtered out.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="e5628-121">如果 `geography` 或 `geometry` 資料類型的 SRID 不相同，則接受這些類型做為引數的方法就會傳回 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="e5628-121">Methods that take `geography` or `geometry` data types as arguments will return `NULL` if the SRIDs are not the same for the types.</span></span>  
  
 <span data-ttu-id="e5628-122">建議您針對最接近像素查詢中使用的索引使用新的空間索引鑲嵌。</span><span class="sxs-lookup"><span data-stu-id="e5628-122">It is recommended that the new spatial index tessellations be used for indexes used in Nearest Neighbor queries.</span></span> <span data-ttu-id="e5628-123">如需空間索引鑲嵌的詳細資訊，請參閱 [空間資料 &#40;SQL Server&#41;](spatial-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e5628-123">For more information on spatial index tessellations, see [Spatial Data &#40;SQL Server&#41;](spatial-data-sql-server.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5628-124">範例</span><span class="sxs-lookup"><span data-stu-id="e5628-124">Example</span></span>  
 <span data-ttu-id="e5628-125">下列程式碼範例會顯示可使用空間索引的最接近像素查詢。</span><span class="sxs-lookup"><span data-stu-id="e5628-125">The following code example shows a Nearest Neighbor query that can use a spatial index.</span></span> <span data-ttu-id="e5628-126">此範例會使用 `Person.Address` 資料庫中的 `AdventureWorks2012` 資料表。</span><span class="sxs-lookup"><span data-stu-id="e5628-126">The example uses the `Person.Address` table in `AdventureWorks2012` database.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
WHERE SpatialLocation.STDistance(@g) IS NOT NULL  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 <span data-ttu-id="e5628-127">您可以針對 SpatialLocation 資料行建立空間索引，以便查看最接近像素查詢如何使用空間索引。</span><span class="sxs-lookup"><span data-stu-id="e5628-127">Create a spatial index on the column SpatialLocation to see how a Nearest Neighbor query uses a spatial index.</span></span> <span data-ttu-id="e5628-128">如需建立空間索引的詳細資訊，請參閱 [建立、修改及卸除空間索引](create-modify-and-drop-spatial-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="e5628-128">For more information on creating spatial indexes, see [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5628-129">範例</span><span class="sxs-lookup"><span data-stu-id="e5628-129">Example</span></span>  
 <span data-ttu-id="e5628-130">下列程式碼範例會顯示無法使用空間索引的最接近像素查詢。</span><span class="sxs-lookup"><span data-stu-id="e5628-130">The following code example shows a Nearest Neighbor query that cannot use a spatial index.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 <span data-ttu-id="e5628-131">這個查詢缺少按照語法區段中指定之格式使用 `STDistance()` 的 `WHERE` 子句，因此這個查詢無法使用空間索引。</span><span class="sxs-lookup"><span data-stu-id="e5628-131">The query lacks a `WHERE` clause that uses `STDistance()` in a form specified in the syntax section so the query cannot use a spatial index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5628-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5628-132">See Also</span></span>  
 [<span data-ttu-id="e5628-133">空間資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e5628-133">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
