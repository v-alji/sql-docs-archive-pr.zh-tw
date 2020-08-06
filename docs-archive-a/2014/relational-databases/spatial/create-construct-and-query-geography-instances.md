---
title: 建立、建構並查詢 geography 執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d744457cc517a6172cca96b27eae1f456deca24e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585805"
---
# <a name="create-construct-and-query-geography-instances"></a><span data-ttu-id="e6dd5-102">建立、建構並查詢地理位置執行個體</span><span class="sxs-lookup"><span data-stu-id="e6dd5-102">Create, Construct, and Query geography Instances</span></span>
  <span data-ttu-id="e6dd5-103">地理位置空間資料類型 (`geography`) 代表圓形表面座標系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-103">The geography spatial data type, `geography`, represents data in a round-earth coordinate system.</span></span> <span data-ttu-id="e6dd5-104">這種類型在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中是實作為 .NET Common Language Runtime (CLR) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-104">This type is implemented as a .NET common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e6dd5-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` 資料類型會儲存橢圓體 (圓形表面) 資料，例如 GPS 經緯度座標。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` data type stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.</span></span>  
  
 <span data-ttu-id="e6dd5-106">`geography` 類型已預先定義，而且可在每一個資料庫中使用。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-106">The `geography` type is predefined and available in each database.</span></span> <span data-ttu-id="e6dd5-107">您可以建立 `geography` 類型的資料表資料行，並使用與其他系統提供之類型相同的方式來操作 `geography` 資料。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-107">You can create table columns of type `geography` and operate on `geography` data in the same manner as you would use other system-supplied types.</span></span>  
  
##  <a name="creating-or-constructing-a-new-geography-instance"></a><a name="creating"></a> <span data-ttu-id="e6dd5-108">建立或建構新的地理位置執行個體</span><span class="sxs-lookup"><span data-stu-id="e6dd5-108">Creating or constructing a new geography instance</span></span>  
  
###  <a name="creating-a-new-geography-instance-from-an-existing-instance"></a><a name="existing"></a> <span data-ttu-id="e6dd5-109">從現有的執行個體建立新的地理位置執行個體</span><span class="sxs-lookup"><span data-stu-id="e6dd5-109">Creating a New geography Instance from an Existing Instance</span></span>  
 <span data-ttu-id="e6dd5-110">`geography` 資料類型提供許多內建方法，您可以使用這些方法來根據現有執行個體建立新的 `geography` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-110">The `geography` data type provides numerous built-in methods you can use to create new `geography` instances based on existing instances.</span></span>  
  
 <span data-ttu-id="e6dd5-111">**在地理位置周圍建立緩衝區**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-111">**To create a buffer around a geography**</span></span>  
 [<span data-ttu-id="e6dd5-112">STBuffer &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-112">STBuffer &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 <span data-ttu-id="e6dd5-113">**在地理位置周圍建立緩衝區，允許容錯**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-113">**To create a buffer around a geography, allowing for a tolerance**</span></span>  
 [<span data-ttu-id="e6dd5-114">BufferWithTolerance &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-114">BufferWithTolerance &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 <span data-ttu-id="e6dd5-115">**從兩個 geography 執行個體的交集建立地理位置**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-115">**To create a geography from the intersection of two geography instances**</span></span>  
 [<span data-ttu-id="e6dd5-116">STIntersection &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-116">STIntersection &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 <span data-ttu-id="e6dd5-117">**從兩個 geography 執行個體的聯集建立地理位置**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-117">**To create a geography from the union of two geography instances**</span></span>  
 [<span data-ttu-id="e6dd5-118">STUnion &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-118">STUnion &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 <span data-ttu-id="e6dd5-119">**從兩個地理位置不重疊的點建立地理位置**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-119">**To create a geography from the points where one geography does not overlap another**</span></span>  
 [<span data-ttu-id="e6dd5-120">STDifference &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-120">STDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-text-input"></a><a name="wkt"></a> <span data-ttu-id="e6dd5-121">從已知的文字輸入建構地理位置執行個體</span><span class="sxs-lookup"><span data-stu-id="e6dd5-121">Constructing a geography Instance from Well-Known Text Input</span></span>  
 <span data-ttu-id="e6dd5-122">`geography` 資料類型提供數種內建方法，可從開放式地理空間協會 (Open Geospatial Consortium，OGC) 的 WKT 表示法產生地理位置。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-122">The `geography` data type provides several built-in methods that generate a geography from the Open Geospatial Consortium (OGC) WKT representation.</span></span> <span data-ttu-id="e6dd5-123">WKT 標準是一種文字字串，可允許使用文字格式交換地理位置資料。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-123">The WKT standard is a text string that allows geography data to be exchanged in textual form.</span></span>  
  
 <span data-ttu-id="e6dd5-124">**從 WKT 輸入建構任何類型的地理位置執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-124">**To construct any type of geography instance from WKT input**</span></span>  
 [<span data-ttu-id="e6dd5-125">STGeomFromText &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-125">STGeomFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [<span data-ttu-id="e6dd5-126">Parse &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-126">Parse &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 <span data-ttu-id="e6dd5-127">**從 WKT 輸入建構地理位置 Point 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-127">**To construct a geography Point instance from WKT input**</span></span>  
 [<span data-ttu-id="e6dd5-128">STPointFromText &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-128">STPointFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 <span data-ttu-id="e6dd5-129">**從 WKT 輸入建構地理位置 MultiPoint 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-129">**To construct a geography MultiPoint instance from WKT input**</span></span>  
 [<span data-ttu-id="e6dd5-130">STMPointFromText &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-130">STMPointFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 <span data-ttu-id="e6dd5-131">**從 WKT 輸入建構地理位置 LineString 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-131">**To construct a geography LineString instance from WKT input**</span></span>  
 <span data-ttu-id="e6dd5-132">STLineFromText (geography 資料類型)</span><span class="sxs-lookup"><span data-stu-id="e6dd5-132">STLineFromText (geography Data Type)</span></span>  
  
 <span data-ttu-id="e6dd5-133">**從 WKT 輸入建構地理位置 MultiLineString 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-133">**To construct a geography MultiLineString instance from WKT input**</span></span>  
 [<span data-ttu-id="e6dd5-134">STMLineFromText &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-134">STMLineFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 <span data-ttu-id="e6dd5-135">**從 WKT 輸入建構地理位置 Polygon 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-135">**To construct a geography Polygon instance from WKT input**</span></span>  
 [<span data-ttu-id="e6dd5-136">STPolyFromText &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-136">STPolyFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 <span data-ttu-id="e6dd5-137">**從 WKT 輸入建構地理位置 MultiPolygon 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-137">**To construct a geography MultiPolygon instance from WKT input**</span></span>  
 [<span data-ttu-id="e6dd5-138">STMPolyFromText &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-138">STMPolyFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 <span data-ttu-id="e6dd5-139">**從 WKT 輸入建構地理位置 GeometryCollection 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-139">**To construct a geography GeometryCollection instance from WKT input**</span></span>  
 [<span data-ttu-id="e6dd5-140">STGeomCollFromText &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-140">STGeomCollFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-binary-input"></a><a name="wkb"></a> <span data-ttu-id="e6dd5-141">從已知的二進位輸入建構地理位置執行個體</span><span class="sxs-lookup"><span data-stu-id="e6dd5-141">Constructing a geography Instance from Well-Known Binary Input</span></span>  
 <span data-ttu-id="e6dd5-142">WKB 是 OGC 指定的一種二進位格式，可允許在用戶端應用程式與 SQL 資料庫之間交換 `Geography` 資料。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-142">WKB is a binary format specified by the OGC that permits `Geography` data to be exchanged between a client application and an SQL database.</span></span> <span data-ttu-id="e6dd5-143">下列函數可接受 WKB 輸入來建構地理位置執行個體：</span><span class="sxs-lookup"><span data-stu-id="e6dd5-143">The following functions accept WKB input to construct geography instances:</span></span>  
  
 <span data-ttu-id="e6dd5-144">**從 WKB 輸入建構任何類型的地理位置執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-144">**To construct any type of geography instance from WKB input**</span></span>  
 [<span data-ttu-id="e6dd5-145">STGeomFromWKB &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-145">STGeomFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 <span data-ttu-id="e6dd5-146">**從 WKB 輸入建構地理位置 Point 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-146">**To construct a geography Point instance from WKB input**</span></span>  
 [<span data-ttu-id="e6dd5-147">STPointFromWKB &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-147">STPointFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 <span data-ttu-id="e6dd5-148">**從 WKB 輸入建構地理位置 MultiPoint 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-148">**To construct a geography MultiPoint instance from WKB input**</span></span>  
 [<span data-ttu-id="e6dd5-149">STMPointFromWKB &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-149">STMPointFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 <span data-ttu-id="e6dd5-150">**從 WKB 輸入建構地理位置 LineString 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-150">**To construct a geography LineString instance from WKB input**</span></span>  
 [<span data-ttu-id="e6dd5-151">STLineFromWKB &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-151">STLineFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 <span data-ttu-id="e6dd5-152">**從 WKB 輸入建構地理位置 MultiLineString 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-152">**To construct a geography MultiLineString instance from WKB input**</span></span>  
 [<span data-ttu-id="e6dd5-153">STMLineFromWKB &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-153">STMLineFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 <span data-ttu-id="e6dd5-154">**從 WKB 輸入建構地理位置 Polygon 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-154">**To construct a geography Polygon instance from WKB input**</span></span>  
 [<span data-ttu-id="e6dd5-155">STPolyFromWKB &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-155">STPolyFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 <span data-ttu-id="e6dd5-156">**從 WKB 輸入建構地理位置 MultiPolygon 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-156">**To construct a geography MultiPolygon instance from WKB input**</span></span>  
 [<span data-ttu-id="e6dd5-157">STMPolyFromWKB &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-157">STMPolyFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 <span data-ttu-id="e6dd5-158">**從 WKB 輸入建構地理位置 GeometryCollection 執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-158">**To construct a geography GeometryCollection instance from WKB input**</span></span>  
 <span data-ttu-id="e6dd5-159">[STGeomCollFromWKB &#40;geography 資料類型&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (geography 資料類型)</span><span class="sxs-lookup"><span data-stu-id="e6dd5-159">[STGeomCollFromWKB &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (geography Data Type)</span></span>  
  
###  <a name="constructing-a-geography-instance-from-gml-text-input"></a><a name="gml"></a> <span data-ttu-id="e6dd5-160">從 GML 文字輸入建構地理位置執行個體</span><span class="sxs-lookup"><span data-stu-id="e6dd5-160">Constructing a geography Instance from GML Text Input</span></span>  
 <span data-ttu-id="e6dd5-161">`geography`資料類型提供從 GML 產生實例的方法 `geography` ，這是實例的 XML 標記法 `geography` 。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-161">The `geography` data type provides a method that generates a `geography` instance from GML, an XML representation of a `geography` instance.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e6dd5-162">可支援 GML 的子集。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-162">supports a subset of GML.</span></span>  
  
 <span data-ttu-id="e6dd5-163">如需地理標記語言的詳細資訊，請參閱 OGC 規格： [OGC 規格、地理標記語言](https://go.microsoft.com/fwlink/?LinkId=93629)。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-163">For more information on Geography Markup Language, see the OGC Specification: [OGC Specifications, Geography Markup Language.](https://go.microsoft.com/fwlink/?LinkId=93629)</span></span>  
  
 <span data-ttu-id="e6dd5-164">**從 GML 輸入建構任何類型的地理位置執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-164">**To construct any type of geography instance from GML input**</span></span>  
 [<span data-ttu-id="e6dd5-165">GeomFromGML &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-165">GeomFromGML &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geography-instance"></a><a name="returning"></a> <span data-ttu-id="e6dd5-166">從地理位置執行個體傳回已知的文字和已知的二進位</span><span class="sxs-lookup"><span data-stu-id="e6dd5-166">Returning Well-Known Text and Well-Known Binary from a geography Instance</span></span>  
 <span data-ttu-id="e6dd5-167">您可以使用下列方法傳回 WKT 或 WKB 格式的 `geography` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="e6dd5-167">You can use the following methods to return either the WKT or WKB format of a `geography` instance:</span></span>  
  
 <span data-ttu-id="e6dd5-168">**傳回 WKT 表示法的地理位置執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-168">**To return the WKT representation of a geography instance**</span></span>  
 [<span data-ttu-id="e6dd5-169">STAsText &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-169">STAsText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [<span data-ttu-id="e6dd5-170">ToString &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-170">ToString &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 <span data-ttu-id="e6dd5-171">**傳回 WKT 表示法的地理位置執行個體 (包含任何 Z 和 M 值)**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-171">**To return the WKT representation of a geography instance including any Z and M values**</span></span>  
 [<span data-ttu-id="e6dd5-172">AsTextZM &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-172">AsTextZM &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 <span data-ttu-id="e6dd5-173">**傳回 WKB 表示法的地理位置執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-173">**To return the WKB representation of a geography instance**</span></span>  
 [<span data-ttu-id="e6dd5-174">STAsBinary &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-174">STAsBinary &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 <span data-ttu-id="e6dd5-175">**傳回地理位置執行個體的 GML 表示法**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-175">**To return a GML representation of a geography instance**</span></span>  
 [<span data-ttu-id="e6dd5-176">AsGml &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-176">AsGml &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="querying-the-properties-and-behaviors-of-geography-instances"></a><a name="query"></a> <span data-ttu-id="e6dd5-177">查詢地理位置執行個體的屬性和行為</span><span class="sxs-lookup"><span data-stu-id="e6dd5-177">Querying the Properties and Behaviors of geography Instances</span></span>  
 <span data-ttu-id="e6dd5-178">所有 `geography` 實例都有許多屬性，可以透過提供的方法來抓取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-178">All `geography` instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides.</span></span> <span data-ttu-id="e6dd5-179">下列主題定義地理位置類型的屬性和行為以及用來查詢每一個類型的方法。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-179">The following topics define the properties and behaviors of geography types, and the methods for querying each one.</span></span>  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> <span data-ttu-id="e6dd5-180">有效性、執行個體類型和 GeometryCollection 資訊</span><span class="sxs-lookup"><span data-stu-id="e6dd5-180">Validity, Instance Type, and GeometryCollection Information</span></span>  
 <span data-ttu-id="e6dd5-181">建構 `geography` 執行個體之後，您就可以使用下列方法來傳回執行個體類型，或者，如果它是 `GeometryCollection` 執行個體，就會傳回特定的 `geography` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-181">After a `geography` instance is constructed, you can use the following methods to return the instance type, or if it is a `GeometryCollection` instance, return a specific `geography` instance.</span></span>  
  
 <span data-ttu-id="e6dd5-182">**傳回 geography 類型的執行個體**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-182">**To return the instance type of a geography**</span></span>  
 [<span data-ttu-id="e6dd5-183">STGeometryType &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-183">STGeometryType &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 <span data-ttu-id="e6dd5-184">**判斷 geography 是否為特定的執行個體類型**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-184">**To determine if a geography is a given instance type**</span></span>  
 [<span data-ttu-id="e6dd5-185">InstanceOf &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-185">InstanceOf &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 <span data-ttu-id="e6dd5-186">**判斷 geography 執行個體對於它的執行個體類型而言是否格式正確**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-186">**To determine if a geography instance is well-formed for its instance type**</span></span>  
 [<span data-ttu-id="e6dd5-187">STNumGeometries &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-187">STNumGeometries &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 <span data-ttu-id="e6dd5-188">**傳回 GeometryCollection 執行個體中的特定地理位置**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-188">**To return a specific geography in a GeometryCollection instance**</span></span>  
 <span data-ttu-id="e6dd5-189">[STGeometryN &#40;geography 資料類型&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (geography 資料類型)</span><span class="sxs-lookup"><span data-stu-id="e6dd5-189">[STGeometryN &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (geography Data Type)</span></span>  
  
###  <a name="number-of-points"></a><a name="number"></a> <span data-ttu-id="e6dd5-190">點數</span><span class="sxs-lookup"><span data-stu-id="e6dd5-190">Number of Points</span></span>  
 <span data-ttu-id="e6dd5-191">所有非空 `geography` 的實例都是由*點*組成。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-191">All nonempty `geography` instances are comprised of *points*.</span></span> <span data-ttu-id="e6dd5-192">這些點代表 `geography` 執行個體繪製所在之地球的經緯度座標。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-192">These points represent the latitude and longitude coordinates of the earth on which the `geography` instances are drawn.</span></span> <span data-ttu-id="e6dd5-193">`geography` 資料類型提供了許多內建方法來查詢執行個體的點。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-193">The data type `geography` provides numerous built-in methods for querying the points of an instance.</span></span>  
  
 <span data-ttu-id="e6dd5-194">**傳回組成執行個體的點數**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-194">**To return the number of points that comprise an instance**</span></span>  
 [<span data-ttu-id="e6dd5-195">STNumPoints &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-195">STNumPoints &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 <span data-ttu-id="e6dd5-196">**傳回執行個體中的特定點**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-196">**To return a specific point in an instance**</span></span>  
 [<span data-ttu-id="e6dd5-197">STPointN &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-197">STPointN &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 <span data-ttu-id="e6dd5-198">**傳回執行個體的起點**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-198">**To return the start point of an instance**</span></span>  
 [<span data-ttu-id="e6dd5-199">STStartPoint &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-199">STStartPoint &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 <span data-ttu-id="e6dd5-200">**傳回執行個體的終點**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-200">**To return the end point of an instance**</span></span>  
 [<span data-ttu-id="e6dd5-201">STEndpoint &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-201">STEndpoint &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a><a name="dimension"></a> <span data-ttu-id="e6dd5-202">維度</span><span class="sxs-lookup"><span data-stu-id="e6dd5-202">Dimension</span></span>  
 <span data-ttu-id="e6dd5-203">非空的 `geography` 執行個體可以是 0 維度、1 維度或 2 維度。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-203">A nonempty `geography` instance can be 0-, 1-, or 2-dimensional.</span></span> <span data-ttu-id="e6dd5-204">零維度的 `geography` 實例（例如 `Point` 和 `MultiPoint` ）沒有長度或區域。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-204">Zero-dimensional `geography` instances, such as `Point` and `MultiPoint`, have no length or area.</span></span> <span data-ttu-id="e6dd5-205">一維度物件 (如 `LineString, CircularString`、`CompoundCurve` 和 `MultiLineString`) 具有長度。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-205">One-dimensional objects, such as `LineString, CircularString`, `CompoundCurve`, and `MultiLineString`, have length.</span></span> <span data-ttu-id="e6dd5-206">二維度執行個體 (如 `Polygon, CurvePolygon` 和 `MultiPolygon`) 具有區域和長度。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-206">Two-dimensional instances, such as `Polygon, CurvePolygon`, and `MultiPolygon`, have area and length.</span></span> <span data-ttu-id="e6dd5-207">空的執行個體會報告 -1 的維度，而 `GeometryCollection` 則會報告其內容的最大維度。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-207">Empty instances report a dimension of -1, and a `GeometryCollection` reports the maximum dimension of its contents.</span></span>  
  
 <span data-ttu-id="e6dd5-208">**傳回執行個體的維度**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-208">**To return the dimension of an instance**</span></span>  
 [<span data-ttu-id="e6dd5-209">STDimension &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-209">STDimension &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 <span data-ttu-id="e6dd5-210">**傳回執行個體的長度**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-210">**To return the length of an instance**</span></span>  
 [<span data-ttu-id="e6dd5-211">STLength &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-211">STLength &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 <span data-ttu-id="e6dd5-212">**傳回執行個體的區域**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-212">**To return the area of an instance**</span></span>  
 [<span data-ttu-id="e6dd5-213">STArea &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-213">STArea &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a><a name="empty"></a> <span data-ttu-id="e6dd5-214">Empty</span><span class="sxs-lookup"><span data-stu-id="e6dd5-214">Empty</span></span>  
 <span data-ttu-id="e6dd5-215">*空*的 `geography` 實例沒有任何點。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-215">An *empty*`geography` instance does not have any points.</span></span> <span data-ttu-id="e6dd5-216">空的 `LineString, CircularString`、`CompoundCurve` 和 `MultiLineString` 執行個體的長度是 0。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-216">The length of empty `LineString, CircularString`, `CompoundCurve`, and `MultiLineString` instances is 0.</span></span> <span data-ttu-id="e6dd5-217">空的 `Polygon, CurvePolygon` 和 `MultiPolygon` 執行個體的區域是 0。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-217">The area of empty `Polygon, CurvePolygon` and `MultiPolygon` instances is 0.</span></span>  
  
 <span data-ttu-id="e6dd5-218">**判斷執行個體是否為空的**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-218">**To determine if an instance is empty**</span></span>  
 [<span data-ttu-id="e6dd5-219">STIsEmpty &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-219">STIsEmpty &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a><a name="closure"></a> <span data-ttu-id="e6dd5-220">封閉性</span><span class="sxs-lookup"><span data-stu-id="e6dd5-220">Closure</span></span>  
 <span data-ttu-id="e6dd5-221">*封閉式* `geography` 實例是起始點和結束點相同的圖形。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-221">A *closed*`geography` instance is a figure whose start points and end points are the same.</span></span> <span data-ttu-id="e6dd5-222">`Polygon` 執行個體視為封閉式。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-222">`Polygon` instances are considered closed.</span></span> <span data-ttu-id="e6dd5-223">`Point` 執行個體視為非封閉式。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-223">`Point` instances are not closed.</span></span>  
  
 <span data-ttu-id="e6dd5-224">環形是簡單、封閉的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-224">A ring is a simple, closed `LineString` instance.</span></span>  
  
 <span data-ttu-id="e6dd5-225">**判斷執行個體是否為封閉**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-225">**To determine if an instance is closed**</span></span>  
 [<span data-ttu-id="e6dd5-226">STIsClosed &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-226">STIsClosed &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 <span data-ttu-id="e6dd5-227">**傳回 Polygon 執行個體中的環形數**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-227">**To return the number of rings in a Polygon instance**</span></span>  
 [<span data-ttu-id="e6dd5-228">NumRings &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-228">NumRings &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 <span data-ttu-id="e6dd5-229">**傳回 geography 執行個體的指定環形**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-229">**To return a specified ring of a geography instance**</span></span>  
 [<span data-ttu-id="e6dd5-230">RingN &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-230">RingN &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> <span data-ttu-id="e6dd5-231">空間參考識別碼 (SRID)</span><span class="sxs-lookup"><span data-stu-id="e6dd5-231">Spatial Reference ID (SRID)</span></span>  
 <span data-ttu-id="e6dd5-232">空間參考識別碼 (SRID) 是用來指定代表 `geography` 執行個體之橢圓體座標系統的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-232">The spatial reference ID (SRID) is an identifier specifying which ellipsoidal coordinate system the `geography` instance is represented in.</span></span> <span data-ttu-id="e6dd5-233">具有不同 SRID 的兩個 `geography` 執行個體無法進行比較。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-233">Two `geography` instances with different SRIDs cannot be compared.</span></span>  
  
 <span data-ttu-id="e6dd5-234">**設定或傳回執行個體的 SRID**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-234">**To set or return the SRID of an instance**</span></span>  
 [<span data-ttu-id="e6dd5-235">STSrid &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-235">STSrid &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 <span data-ttu-id="e6dd5-236">這個屬性可以修改。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-236">This property can be modified.</span></span>  
  
##  <a name="determining-relationships-between-geography-instances"></a><a name="rel"></a> <span data-ttu-id="e6dd5-237">判斷地理位置執行個體之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="e6dd5-237">Determining Relationships between geography Instances</span></span>  
 <span data-ttu-id="e6dd5-238">`geography` 資料類型提供許多內建方法，您可以使用這些方法來判斷兩個 `geography` 執行個體之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-238">The `geography` data type provides many built-in methods you can use to determine relationships between two `geography` instances.</span></span>  
  
 <span data-ttu-id="e6dd5-239">**判斷兩個執行個體是否組成相同的點集合**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-239">**To determine if two instances comprise the same point set**</span></span>  
 [<span data-ttu-id="e6dd5-240">STEquals &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-240">STEquals &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 <span data-ttu-id="e6dd5-241">**判斷兩個執行個體是否不相交**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-241">**To determine if two instances are disjoint**</span></span>  
 [<span data-ttu-id="e6dd5-242">STDisjoint &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-242">STDisjoint &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 <span data-ttu-id="e6dd5-243">**判斷兩個執行個體是否相交**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-243">**To determine if two instances intersect**</span></span>  
 [<span data-ttu-id="e6dd5-244">STIntersects &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-244">STIntersects &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 <span data-ttu-id="e6dd5-245">**判斷兩個執行個體相交所在的點**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-245">**To determine the point or points where two instances intersect**</span></span>  
 [<span data-ttu-id="e6dd5-246">STIntersection &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-246">STIntersection &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 <span data-ttu-id="e6dd5-247">**判斷兩個 geography 執行個體中點與點之間的最短距離**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-247">**To determine the shortest distance between points in two geography instances**</span></span>  
 [<span data-ttu-id="e6dd5-248">STDistance &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-248">STDistance &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 <span data-ttu-id="e6dd5-249">**判斷兩個 geography 執行個體中點與點之間的差異**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-249">**To determine the difference in points between two geography instances**</span></span>  
 [<span data-ttu-id="e6dd5-250">STDifference &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-250">STDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 <span data-ttu-id="e6dd5-251">**導出一個地理位置執行個體與另一個執行個體相較之下的對稱差異或唯一的點**</span><span class="sxs-lookup"><span data-stu-id="e6dd5-251">**To derive the symmetric difference, or unique points, of one geography instance compared with another instance**</span></span>  
 [<span data-ttu-id="e6dd5-252">STSymDifference &#40;geography 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-252">STSymDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="geography-instances-must-use-supported-srid"></a><a name="supportedsrid"></a> <span data-ttu-id="e6dd5-253">地理位置執行個體必須使用支援的 SRID</span><span class="sxs-lookup"><span data-stu-id="e6dd5-253">geography Instances Must Use Supported SRID</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e6dd5-254">支援以 EPSG 標準為根據的 SRID。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-254">supports SRIDs based on the EPSG standards.</span></span> <span data-ttu-id="e6dd5-255">當執行計算或是搭配地理位置空間資料使用方法時，必須使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援之 `geography` 執行個體的 SRID。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-255">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-supported SRID for `geography` instances must be used when performing calculations or using methods with geography spatial data.</span></span> <span data-ttu-id="e6dd5-256">SRID 必須符合 **sys.spatial_reference_systems** 目錄檢視中所顯示的其中一個 SRID。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-256">The SRID must match one of the SRIDs displayed in the **sys.spatial_reference_systems** catalog view.</span></span> <span data-ttu-id="e6dd5-257">如同之前所述，當您使用 `geography` 資料類型在您的空間資料上執行計算時，您的結果將會依據建立資料時使用哪一個橢圓體而定，因為每一個橢圓體都會指派一個特定的空間參考識別碼 (SRID)。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-257">As mentioned previously, when you perform calculations on your spatial data using the `geography` data type, your results will depend on which ellipsoid was used in the creation of your data, as each ellipsoid is assigned a specific spatial reference identifier (SRID).</span></span>  
  
 <span data-ttu-id="e6dd5-258">在 `geography` 執行個體上使用方法時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用預設 SRID 4326，此 SRID 會對應到 WGS 84 空間參考系統。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-258">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the default SRID of 4326, which maps to the WGS 84 spatial reference system, when using methods on `geography` instances.</span></span> <span data-ttu-id="e6dd5-259">如果您使用 WGS 84 (或 SRID 4326) 以外之空間參考系統內的資料，您需要為您的地理位置空間資料決定特定的 SRID。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-259">If you use data from a spatial reference system other than WGS 84 (or SRID 4326), you will need to determine the specific SRID for your geography spatial data.</span></span>  
  
##  <a name="examples"></a><a name="examples"></a> <span data-ttu-id="e6dd5-260">範例</span><span class="sxs-lookup"><span data-stu-id="e6dd5-260">Examples</span></span>  
 <span data-ttu-id="e6dd5-261">下列範例示範如何加入及查詢地理位置資料。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-261">The following examples show how to add and query geography data.</span></span>  
  
-   <span data-ttu-id="e6dd5-262">第一個範例會建立具有識別資料行及 `geography` 資料行 `GeogCol1`的資料表。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-262">The first example creates a table with an identity column and a `geography` column `GeogCol1`.</span></span> <span data-ttu-id="e6dd5-263">第三個資料行會將 `geography` 資料行轉譯成它的開放地理空間協會 (Open Geospatial Consortium，OGC) 已知的文字 (Well-Known Text，WKT) 表示法，並使用 `STAsText()` 方法。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-263">A third column renders the `geography` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method.</span></span> <span data-ttu-id="e6dd5-264">然後會插入兩個資料列：一個資料列包含 `LineString` 的 `geography`執行個體，另一個資料列包含 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-264">Two rows are then inserted: one row contains a `LineString` instance of `geography`, and one row contains a `Polygon` instance.</span></span>  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   <span data-ttu-id="e6dd5-265">第二個範例使用 `STIntersection()` 方法傳回之前插入之兩個 `geography` 執行個體相交的點。</span><span class="sxs-lookup"><span data-stu-id="e6dd5-265">The second example uses the `STIntersection()` method to return the points where the two previously inserted `geography` instances intersect.</span></span>  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6dd5-266">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6dd5-266">See Also</span></span>  
 [<span data-ttu-id="e6dd5-267">空間資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e6dd5-267">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
