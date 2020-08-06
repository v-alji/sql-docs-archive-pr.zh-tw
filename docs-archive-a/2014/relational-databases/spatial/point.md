---
title: 點 | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4b12069d84e00738e3ddac8c414f33903f4f0999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606161"
---
# <a name="point"></a><span data-ttu-id="5e446-102">Point</span><span class="sxs-lookup"><span data-stu-id="5e446-102">Point</span></span>
  <span data-ttu-id="5e446-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 空間資料中，`Point` 是一個代表單一位置的 0 維度物件，而且可包含 Z (高度) 和 M (測量) 值。</span><span class="sxs-lookup"><span data-stu-id="5e446-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spatial data, a `Point` is a 0-dimensional object representing a single location and may contain Z (elevation) and M (measure) values.</span></span>  
  
## <a name="geography-data-type"></a><span data-ttu-id="5e446-104">Geography 資料類型</span><span class="sxs-lookup"><span data-stu-id="5e446-104">Geography Data Type</span></span>  
 <span data-ttu-id="5e446-105">geography 資料類型的 Point 類型代表單一位置，其中 *Lat* 和 *Long* 分別表示緯度和經度。</span><span class="sxs-lookup"><span data-stu-id="5e446-105">The Point type for the geography data type represents a single location where *Lat* represents latitude and *Long* represents longitude.</span></span> <span data-ttu-id="5e446-106">緯度和經度值會以度數測量。</span><span class="sxs-lookup"><span data-stu-id="5e446-106">The values for latitude and longitude are measured in degrees.</span></span> <span data-ttu-id="5e446-107">緯度的值一定會在 [-90, 90] 間隔內，在這個範圍之外輸入的值將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5e446-107">Values for latitude always lie in the interval [-90, 90], and values that are inputted outside this range will throw an exception.</span></span> <span data-ttu-id="5e446-108">經度的值一定會在 [-180, 180] 間隔內，在這個範圍之外的輸入值會折返，以配合這個範圍。</span><span class="sxs-lookup"><span data-stu-id="5e446-108">Values for longitude always lie in the interval (-180, 180], and values inputted outside this range are wrapped around to fit in this range.</span></span> <span data-ttu-id="5e446-109">例如，如果輸入 190 當作經度，則它會折返到 -170 值。</span><span class="sxs-lookup"><span data-stu-id="5e446-109">For example, if 190 is inputted for longitude, then it will be wrapped to the value -170.</span></span> <span data-ttu-id="5e446-110">*SRID* 表示要傳回之 **geography** 例項的空間參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="5e446-110">*SRID* represents the spatial reference ID of the **geography** instance that you wish to return.</span></span>  
  
## <a name="geometry-data-type"></a><span data-ttu-id="5e446-111">Geometry 資料類型</span><span class="sxs-lookup"><span data-stu-id="5e446-111">Geometry Data Type</span></span>  
 <span data-ttu-id="5e446-112">geometry 資料類型的 Point 類型代表單一位置，其中 *X* 代表正在產生之 Point 的 X 座標， *Y* 則代表正在產生之 Point 的 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="5e446-112">The Point type for the geometry data type represents a single location where *X* represents the X-coordinate of the Point being generated and *Y* represents the Y-coordinate of the Point being generated.</span></span> <span data-ttu-id="5e446-113">*SRID* 表示要傳回之 **geometry** 例項的空間參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="5e446-113">*SRID* represents the spatial reference ID of the **geometry** instance that you wish to return.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5e446-114">範例</span><span class="sxs-lookup"><span data-stu-id="5e446-114">Examples</span></span>  
 <span data-ttu-id="5e446-115">下列範例會建立代表 SRID 為 0 之 (3, 4) 點的 `geometry Point`執行個體。</span><span class="sxs-lookup"><span data-stu-id="5e446-115">The following example creates a `geometry Point`instance representing the point (3, 4) with an SRID of 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 <span data-ttu-id="5e446-116">下一個範例會建立 `geometry``Point` 執行個體，它代表 Z (高度) 值為 7 且 M (測量) 值為 2.5 的 (3, 4) 點，而且預設 SRID 為 0。</span><span class="sxs-lookup"><span data-stu-id="5e446-116">The next example creates a `geometry``Point` instance representing the point (3, 4) with a Z (elevation) value of 7, an M (measure) value of 2.5, and the default SRID of 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 <span data-ttu-id="5e446-117">最後一個範例會傳回 `geometry``Point` 執行個體的 X、Y、Z 和 M 值。</span><span class="sxs-lookup"><span data-stu-id="5e446-117">The final example returns the X, Y, Z, and M values for the `geometry``Point` instance.</span></span>  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 <span data-ttu-id="5e446-118">Z 和 M 值可明確指定為 NULL，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5e446-118">Z and M values may be explicitly specified as NULL, as shown in the following example.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e446-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e446-119">See Also</span></span>  
 <span data-ttu-id="5e446-120">[MultiPoint](multipoint.md) </span><span class="sxs-lookup"><span data-stu-id="5e446-120">[MultiPoint](multipoint.md) </span></span>  
 <span data-ttu-id="5e446-121">[STX &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="5e446-121">[STX &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type) </span></span>  
 <span data-ttu-id="5e446-122">[STY &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="5e446-122">[STY &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type) </span></span>  
 [<span data-ttu-id="5e446-123">空間資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5e446-123">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
