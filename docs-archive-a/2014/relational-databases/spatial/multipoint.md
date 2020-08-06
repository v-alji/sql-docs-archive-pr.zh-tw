---
title: MultiPoint | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b741071b7986aceea4e49d4fde8293ef2c96fc2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606165"
---
# <a name="multipoint"></a><span data-ttu-id="c30db-102">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="c30db-102">MultiPoint</span></span>
  <span data-ttu-id="c30db-103">`MultiPoint` 是零或多個點的集合。</span><span class="sxs-lookup"><span data-stu-id="c30db-103">A `MultiPoint` is a collection of zero or more points.</span></span> <span data-ttu-id="c30db-104">`MultiPoint` 執行個體的界限是空的。</span><span class="sxs-lookup"><span data-stu-id="c30db-104">The boundary of a `MultiPoint` instance is empty.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c30db-105">範例</span><span class="sxs-lookup"><span data-stu-id="c30db-105">Examples</span></span>  
 <span data-ttu-id="c30db-106">下列範例會建立具有 SRID 23 和兩個點的 `geometry MultiPoint` 執行個體：一個點的座標為 (2, 3)，另一個點的座標為 (7, 8)，而 Z 值為 9.5。</span><span class="sxs-lookup"><span data-stu-id="c30db-106">The following example creates a `geometry MultiPoint` instance with SRID 23 and two points: one point with the coordinates (2, 3), one point with the coordinates (7, 8), and a Z value of 9.5.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 <span data-ttu-id="c30db-107">也可以使用 `MultiPoint` 來表示這個 `STMPointFromText()` 執行個體，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c30db-107">This `MultiPoint` instance can also be expressed using `STMPointFromText()` as shown below.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 <span data-ttu-id="c30db-108">下列範例使用 `STGeometryN()` 方法來擷取集合中第一個點的描述。</span><span class="sxs-lookup"><span data-stu-id="c30db-108">The following example uses the method `STGeometryN()` to retrieve a description of the first point in the collection.</span></span>  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a><span data-ttu-id="c30db-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c30db-109">See Also</span></span>  
 <span data-ttu-id="c30db-110">[此處](point.md) </span><span class="sxs-lookup"><span data-stu-id="c30db-110">[Point](point.md) </span></span>  
 [<span data-ttu-id="c30db-111">空間資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c30db-111">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
