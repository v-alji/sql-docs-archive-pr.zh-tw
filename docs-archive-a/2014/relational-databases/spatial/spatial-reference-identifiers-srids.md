---
title: 空間參考識別碼 (SRID) | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 15db59b43731b9a39ff4bef78e3a6cb6929e9b47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597057"
---
# <a name="spatial-reference-identifiers-srids"></a><span data-ttu-id="d68f5-102">空間參考識別碼 (SRID)</span><span class="sxs-lookup"><span data-stu-id="d68f5-102">Spatial Reference Identifiers (SRIDs)</span></span>
  <span data-ttu-id="d68f5-103">每一個空間執行個體都有空間參考識別碼 (SRID)，</span><span class="sxs-lookup"><span data-stu-id="d68f5-103">Each spatial instance has a spatial reference identifier (SRID).</span></span> <span data-ttu-id="d68f5-104">此 SRID 會對應到空間參考系統，此系統是以用於扁平表面對應或圓形表面對應的特定橢圓體為根據。</span><span class="sxs-lookup"><span data-stu-id="d68f5-104">The SRID corresponds to a spatial reference system based on the specific ellipsoid used for either flat-earth mapping or round-earth mapping.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d68f5-105">如需 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引進之空間功能 (包括新的 SRID) 的詳細描述和範例，請下載技術白皮書： [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407)(SQL Server 2012 的新空間功能)。</span><span class="sxs-lookup"><span data-stu-id="d68f5-105">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including a new SRID, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
 <span data-ttu-id="d68f5-106">空間資料行可包含具有不同 SRID 的物件。</span><span class="sxs-lookup"><span data-stu-id="d68f5-106">A spatial column can contain objects with different SRIDs.</span></span> <span data-ttu-id="d68f5-107">但是，當針對資料使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 空間資料方法來執行作業時，只能使用具有相同 SRID 的空間執行個體。</span><span class="sxs-lookup"><span data-stu-id="d68f5-107">However, only spatial instances with the same SRID can be used when performing operations with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spatial data methods on your data.</span></span> <span data-ttu-id="d68f5-108">衍生自兩個空間資料執行個體的任何空間方法結果只有在這兩個執行個體具有相同的 SRID (根據用來判斷執行個體座標的相同度量、資料和投射單位) 時，才是有效的。</span><span class="sxs-lookup"><span data-stu-id="d68f5-108">The result of any spatial method derived from two spatial data instances is valid only if those instances have the same SRID that is based on the same unit of measurement, datum, and projection used to determine the coordinates of the instances.</span></span> <span data-ttu-id="d68f5-109">最常見的 SRID 度量單位是公尺或平方公尺。</span><span class="sxs-lookup"><span data-stu-id="d68f5-109">The most common units of measurement of a SRID are meters or square meters.</span></span>  
  
 <span data-ttu-id="d68f5-110">如果兩個空間執行個體沒有相同的 SRID，則執行個體上所用之 `geometry` 或 `geography` 資料類型方法的結果將會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="d68f5-110">If two spatial instances do not have the same SRID, the results from a `geometry` or `geography` Data Type method used on the instances will return NULL.</span></span> <span data-ttu-id="d68f5-111">例如，如果要讓下列述詞傳回非 NULL 的結果，兩個 `geometry` 執行個體 (`geometry1` 和 `geometry2`) 必須有相同的 SRID：</span><span class="sxs-lookup"><span data-stu-id="d68f5-111">For example, for the following predicate term to return a non-NULL result, the two `geometry` instances, `geometry1` and `geometry2`, must have the same SRID:</span></span>  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  <span data-ttu-id="d68f5-112">空間參考識別系統是由 [歐洲石油探勘組織 (EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) 標準所定義，這是為了地圖製作、探勘和測地資料儲存所開發的一套標準。</span><span class="sxs-lookup"><span data-stu-id="d68f5-112">The spatial reference identification system is defined by the [European Petroleum Survey Group (EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) standard, which is a set of standards developed for cartography, surveying, and geodetic data storage.</span></span> <span data-ttu-id="d68f5-113">這項標準的擁有者為石油生產者 (OGP) 探勘和定位委員會 (Oil and Gas Producers (OGP) Surveying and Positioning Committee)。</span><span class="sxs-lookup"><span data-stu-id="d68f5-113">This standard is owned by the Oil and Gas Producers (OGP) Surveying and Positioning Committee.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68f5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d68f5-114">See Also</span></span>  
 [<span data-ttu-id="d68f5-115">空間資料類型概觀</span><span class="sxs-lookup"><span data-stu-id="d68f5-115">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
  
  
