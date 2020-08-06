---
title: 建立、建構及查詢 geometry 執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- planar spatial data [SQL Server], getting started
- geometry data type [SQL Server], getting started
ms.assetid: c6b5c852-37d2-48d0-a8ad-e43bb80d6514
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 539f3f8bb1d9a1c277d6317cc571cf8bcb281833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585803"
---
# <a name="create-construct-and-query-geometry-instances"></a><span data-ttu-id="abd96-102">建立、建構及查詢幾何執行個體</span><span class="sxs-lookup"><span data-stu-id="abd96-102">Create, Construct, and Query geometry Instances</span></span>
  <span data-ttu-id="abd96-103">平面空間資料類型 (`geometry`) 代表 Euclidean (平面) 座標系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="abd96-103">The planar spatial data type, `geometry`, represents data in a Euclidean (flat) coordinate system.</span></span> <span data-ttu-id="abd96-104">這種類型在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中是實作為 Common Language Runtime (CLR) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="abd96-104">This type is implemented as a common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="abd96-105">`geometry` 類型已預先定義，而且可在每一個資料庫中使用。</span><span class="sxs-lookup"><span data-stu-id="abd96-105">The `geometry` type is predefined and available in each database.</span></span> <span data-ttu-id="abd96-106">您可以建立 `geometry` 類型的資料表資料行，並使用與其他 CLR 類型相同的方式來操作 `geometry` 資料。</span><span class="sxs-lookup"><span data-stu-id="abd96-106">You can create table columns of type `geometry` and operate on `geometry` data in the same manner as you would use other CLR types.</span></span>  
  
 <span data-ttu-id="abd96-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援的 `geometry` 資料類型 (平面) 符合開放式地理空間協會 (Open Geospatial Consortium，OGC) 的 SQL 簡單特徵規格 1.1.0 版。</span><span class="sxs-lookup"><span data-stu-id="abd96-107">The `geometry` data type (planar) supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0.</span></span>  
  
 <span data-ttu-id="abd96-108">如需有關 OGC 規格的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="abd96-108">For more information on OGC specifications, see the following:</span></span>  
  
-   [<span data-ttu-id="abd96-109">OGC 規格，簡單特徵存取第一部 - 常見架構</span><span class="sxs-lookup"><span data-stu-id="abd96-109">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span></span>](https://go.microsoft.com/fwlink/?LinkId=93628)  
  
-   <span data-ttu-id="abd96-110">[OGC 規格，簡單特徵存取第二部 - SQL 選項](https://go.microsoft.com/fwlink/?LinkId=93629) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="abd96-110">[OGC Specifications, Simple Feature Access Part 2 - SQL Options](https://go.microsoft.com/fwlink/?LinkId=93629)</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="abd96-111">支援以下列結構描述定義之現有 GML 3.1 標準的子集：[https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959)。</span><span class="sxs-lookup"><span data-stu-id="abd96-111">supports a subset of the existing GML 3.1 standard which is defined in the following schema: [https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959).</span></span>  
  
##  <a name="creating-or-constructing-a-new-geometry-instance"></a><a name="creating"></a> <span data-ttu-id="abd96-112">建立或建構新的 geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="abd96-112">Creating or constructing a new geometry instance</span></span>  
  
###  <a name="creating-a-new-geometry-instance-from-an-existing-instance"></a><a name="existing"></a> <span data-ttu-id="abd96-113">從現有的執行個體建立新的 geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="abd96-113">Creating a New geometry Instance from an Existing Instance</span></span>  
 <span data-ttu-id="abd96-114">`geometry` 資料類型提供許多內建方法，您可以使用這些方法來根據現有執行個體建立新的 `geometry` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="abd96-114">The `geometry` data type provides numerous built-in methods you can use to create new `geometry` instances based on existing instances.</span></span>  
  
 <span data-ttu-id="abd96-115">**在幾何周圍建立緩衝區**</span><span class="sxs-lookup"><span data-stu-id="abd96-115">**To create a buffer around a geometry**</span></span>  
 [<span data-ttu-id="abd96-116">STBuffer &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-116">STBuffer &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stbuffer-geometry-data-type)  
  
 [<span data-ttu-id="abd96-117">BufferWithTolerance #40; geometry 資料類型 &#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-117">BufferWithTolerance &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type)  
  
 <span data-ttu-id="abd96-118">**建立簡化版本的幾何**</span><span class="sxs-lookup"><span data-stu-id="abd96-118">**To create a simplified version of a geometry**</span></span>  
 [<span data-ttu-id="abd96-119">減少 &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-119">Reduce &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/reduce-geometry-data-type)  
  
 <span data-ttu-id="abd96-120">**建立幾何的凸面**</span><span class="sxs-lookup"><span data-stu-id="abd96-120">**To create the convex hull of a geometry**</span></span>  
 [<span data-ttu-id="abd96-121">STConvexHull &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-121">STConvexHull &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stconvexhull-geometry-data-type)  
  
 <span data-ttu-id="abd96-122">**從兩個幾何的交集建立幾何**</span><span class="sxs-lookup"><span data-stu-id="abd96-122">**To create a geometry from the intersection of two geometries**</span></span>  
 [<span data-ttu-id="abd96-123">STIntersection &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-123">STIntersection &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stintersection-geometry-data-type)  
  
 <span data-ttu-id="abd96-124">**從兩個幾何的聯集建立幾何**</span><span class="sxs-lookup"><span data-stu-id="abd96-124">**To create a geometry from the union of two geometries**</span></span>  
 [<span data-ttu-id="abd96-125">STUnion &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-125">STUnion &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stunion-geometry-data-type)  
  
 <span data-ttu-id="abd96-126">**從兩個幾何不重疊的點建立幾何**</span><span class="sxs-lookup"><span data-stu-id="abd96-126">**To create a geometry from the points where one geometry does not overlap another**</span></span>  
 [<span data-ttu-id="abd96-127">STDifference &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-127">STDifference &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdifference-geometry-data-type)  
  
 <span data-ttu-id="abd96-128">**從兩個幾何不重疊的點建立幾何**</span><span class="sxs-lookup"><span data-stu-id="abd96-128">**To create a geometry from the points where two geometries do not overlap**</span></span>  
 [<span data-ttu-id="abd96-129">STSymDifference &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-129">STSymDifference &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stsymdifference-geometry-data-type)  
  
 <span data-ttu-id="abd96-130">**建立位於現有幾何上的任意 Point 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-130">**To create an arbitrary Point instance that lies on an existing geometry**</span></span>  
 [<span data-ttu-id="abd96-131">STPointOnSurface &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-131">STPointOnSurface &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-well-known-text-input"></a><a name="wkt"></a> <span data-ttu-id="abd96-132">從已知的文字輸入建構 geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="abd96-132">Constructing a geometry Instance from Well-Known Text Input</span></span>  
 <span data-ttu-id="abd96-133">`geometry` 資料類型提供數種內建方法，可從開放式地理空間協會 (Open Geospatial Consortium，OGC) 的 WKT 表示法產生幾何。</span><span class="sxs-lookup"><span data-stu-id="abd96-133">The `geometry` data type provides several built-in methods that generate a geometry from the Open Geospatial Consortium (OGC) WKT representation.</span></span> <span data-ttu-id="abd96-134">WKT 標準是一種文字字串，可允許使用文字格式交換幾何資料。</span><span class="sxs-lookup"><span data-stu-id="abd96-134">The WKT standard is a text string that allows geometry data to be exchanged in textual form.</span></span>  
  
 <span data-ttu-id="abd96-135">**從 WKT 輸入建構任何類型的 geometry 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-135">**To construct any type of geometry instance from WKT input**</span></span>  
 [<span data-ttu-id="abd96-136">STGeomFromText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-136">STGeomFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type)  
  
 [<span data-ttu-id="abd96-137">剖析 &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-137">Parse &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/parse-geometry-data-type)  
  
 <span data-ttu-id="abd96-138">**從 WKT 輸入建構幾何 Point 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-138">**To construct a geometry Point instance from WKT input**</span></span>  
 [<span data-ttu-id="abd96-139">STPointFromText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-139">STPointFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointfromtext-geometry-data-type)  
  
 <span data-ttu-id="abd96-140">**從 WKT 輸入建構幾何 MultiPoint 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-140">**To construct a geometry MultiPoint instance from WKT input**</span></span>  
 [<span data-ttu-id="abd96-141">STMPointFromText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-141">STMPointFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpointfromtext-geometry-data-type)  
  
 <span data-ttu-id="abd96-142">**從 WKT 輸入建構幾何 LineString 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-142">**To construct a geometry LineString instance from WKT input**</span></span>  
 [<span data-ttu-id="abd96-143">STLineFromText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-143">STLineFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stlinefromtext-geometry-data-type)  
  
 <span data-ttu-id="abd96-144">**從 WKT 輸入建構幾何 MultiLineString 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-144">**To construct a geometry MultiLineString instance from WKT input**</span></span>  
 [<span data-ttu-id="abd96-145">STMLineFromText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-145">STMLineFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmlinefromtext-geometry-data-type)  
  
 <span data-ttu-id="abd96-146">**從 WKT 輸入建構幾何 Polygon 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-146">**To construct a geometry Polygon instance from WKT input**</span></span>  
 [<span data-ttu-id="abd96-147">STPolyFromText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-147">STPolyFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpolyfromtext-geometry-data-type)  
  
 <span data-ttu-id="abd96-148">**從 WKT 輸入建構幾何 MultiPolygon 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-148">**To construct a geometry MultiPolygon instance from WKT input**</span></span>  
 [<span data-ttu-id="abd96-149">STMPolyFromText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-149">STMPolyFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpolyfromtext-geometry-data-type)  
  
 <span data-ttu-id="abd96-150">**從 WKT 輸入建構幾何 GeometryCollection 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-150">**To construct a geometry GeometryCollection instance from WKT input**</span></span>  
 [<span data-ttu-id="abd96-151">STGeomCollFromText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-151">STGeomCollFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomcollfromtext-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-well-known-binary-input"></a><a name="wkb"></a> <span data-ttu-id="abd96-152">從已知的二進位輸入建構 geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="abd96-152">Constructing a geometry Instance from Well-Known Binary Input</span></span>  
 <span data-ttu-id="abd96-153">WKB 是 OGC 指定的一種二進位格式，可允許在用戶端應用程式與 SQL 資料庫之間交換 `geometry` 資料。</span><span class="sxs-lookup"><span data-stu-id="abd96-153">WKB is a binary format specified by the Open Geospatial Consortium (OGC) that permits `geometry` data to be exchanged between a client application and an SQL database.</span></span> <span data-ttu-id="abd96-154">下列函數可接受 WKB 輸入來建構幾何：</span><span class="sxs-lookup"><span data-stu-id="abd96-154">The following functions accept WKB input to construct geometries:</span></span>  
  
 <span data-ttu-id="abd96-155">**從 WKB 輸入建構任何類型的 geometry 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-155">**To construct any type of geometry instance from WKB input**</span></span>  
 [<span data-ttu-id="abd96-156">STGeomFromWKB &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-156">STGeomFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomfromwkb-geometry-data-type)  
  
 <span data-ttu-id="abd96-157">**從 WKB 輸入建構幾何 Point 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-157">**To construct a geometry Point instance from WKB input**</span></span>  
 [<span data-ttu-id="abd96-158">STPointFromWKB &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-158">STPointFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointfromwkb-geometry-data-type)  
  
 <span data-ttu-id="abd96-159">**從 WKB 輸入建構幾何 MultiPoint 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-159">**To construct a geometry MultiPoint instance from WKB input**</span></span>  
 [<span data-ttu-id="abd96-160">STMPointFromWKB &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-160">STMPointFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpointfromwkb-geometry-data-type)  
  
 <span data-ttu-id="abd96-161">**從 WKB 輸入建構幾何 LineString 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-161">**To construct a geometry LineString instance from WKB input**</span></span>  
 [<span data-ttu-id="abd96-162">STLineFromWKB &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-162">STLineFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stlinefromwkb-geometry-data-type)  
  
 <span data-ttu-id="abd96-163">**從 WKB 輸入建構幾何 MultiLineString 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-163">**To construct a geometry MultiLineString instance from WKB input**</span></span>  
 [<span data-ttu-id="abd96-164">STMLineFromWKB &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-164">STMLineFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmlinefromwkb-geometry-data-type)  
  
 <span data-ttu-id="abd96-165">**從 WKB 輸入建構幾何 Polygon 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-165">**To construct a geometry Polygon instance from WKB input**</span></span>  
 [<span data-ttu-id="abd96-166">STPolyFromWKB &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-166">STPolyFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpolyfromwkb-geometry-data-type)  
  
 <span data-ttu-id="abd96-167">**從 WKB 輸入建構幾何 MultiPolygon 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-167">**To construct a geometry MultiPolygon instance from WKB input**</span></span>  
 [<span data-ttu-id="abd96-168">STMPolyFromWKB &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-168">STMPolyFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpolyfromwkb-geometry-data-type)  
  
 <span data-ttu-id="abd96-169">**從 WKB 輸入建構幾何 GeometryCollection 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-169">**To construct a geometry GeometryCollection instance from WKB input**</span></span>  
 [<span data-ttu-id="abd96-170">STGeomCollFromWKB &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-170">STGeomCollFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomcollfromwkb-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-gml-text-input"></a><a name="gml"></a> <span data-ttu-id="abd96-171">從 GML 文字輸入建構 geometry 執行個體</span><span class="sxs-lookup"><span data-stu-id="abd96-171">Constructing a geometry Instance from GML Text Input</span></span>  
 <span data-ttu-id="abd96-172">`geometry`資料類型提供的方法會 `geometry` 從 GML 產生實例，這是幾何物件的 XML 標記法。</span><span class="sxs-lookup"><span data-stu-id="abd96-172">The `geometry` data type provides a method that generates a `geometry` instance from GML, an XML representation of geometric objects.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="abd96-173">可支援 GML 的子集。</span><span class="sxs-lookup"><span data-stu-id="abd96-173">supports a subset of GML.</span></span>  
  
 <span data-ttu-id="abd96-174">**從 GML 輸入建構任何類型的 geometry 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-174">**To construct any type of geometry instance from GML input**</span></span>  
 [<span data-ttu-id="abd96-175">GeomFromGml &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-175">GeomFromGml &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/geomfromgml-geometry-data-type)  
  
  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geometry-instance"></a><a name="returning"></a> <span data-ttu-id="abd96-176">從 geometry 執行個體傳回已知的文字和已知的二進位</span><span class="sxs-lookup"><span data-stu-id="abd96-176">Returning Well-Known Text and Well-Known Binary from a geometry Instance</span></span>  
 <span data-ttu-id="abd96-177">您可以使用下列方法傳回 WKT 或 WKB 格式的 `geometry` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="abd96-177">You can use the following methods to return either the WKT or WKB format of a `geometry` instance:</span></span>  
  
 <span data-ttu-id="abd96-178">**傳回 WKT 表示法的 geometry 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-178">**To return the WKT representation of a geometry instance**</span></span>  
 [<span data-ttu-id="abd96-179">STAsText &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-179">STAsText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stastext-geometry-data-type)  
  
 [<span data-ttu-id="abd96-180">ToString &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-180">ToString &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/tostring-geometry-data-type)  
  
 <span data-ttu-id="abd96-181">**傳回 WKT 表示法的 geometry 執行個體 (包含任何 Z 和 M 值)**</span><span class="sxs-lookup"><span data-stu-id="abd96-181">**To return the WKT representation of a geometry instance including any Z and M values**</span></span>  
 [<span data-ttu-id="abd96-182">AsTextZM &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-182">AsTextZM &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/astextzm-geometry-data-type)  
  
 <span data-ttu-id="abd96-183">**傳回 WKB 表示法的 geometry 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-183">**To return the WKB representation of a geometry instance**</span></span>  
 [<span data-ttu-id="abd96-184">STAsBinary &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-184">STAsBinary &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stasbinary-geometry-data-type)  
  
 <span data-ttu-id="abd96-185">**傳回 GML 表示法的 geometry 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-185">**To return a GML representation of a geometry instance**</span></span>  
 [<span data-ttu-id="abd96-186">AsGml &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-186">AsGml &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/asgml-geometry-data-type)  
  
  
  
##  <a name="querying-the-properties-and-behaviors-of-geometry-instances"></a><a name="querying"></a> <span data-ttu-id="abd96-187">查詢 geometry 執行個體的屬性和行為</span><span class="sxs-lookup"><span data-stu-id="abd96-187">Querying the Properties and Behaviors of geometry Instances</span></span>  
 <span data-ttu-id="abd96-188">所有 `geometry` 實例都有許多屬性，可以透過提供的方法來抓取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="abd96-188">All `geometry` instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides.</span></span> <span data-ttu-id="abd96-189">下列主題定義幾何類型的屬性和行為以及用來查詢每一個類型的方法。</span><span class="sxs-lookup"><span data-stu-id="abd96-189">The following topics define the properties and behaviors of geometry types, and the methods for querying each one.</span></span>  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> <span data-ttu-id="abd96-190">有效性、執行個體類型和 GeometryCollection 資訊</span><span class="sxs-lookup"><span data-stu-id="abd96-190">Validity, Instance Type, and GeometryCollection Information</span></span>  
 <span data-ttu-id="abd96-191">一旦建構了 `geometry` 執行個體之後，您就可以使用下列方法來判斷它的格式是否正確、傳回執行個體類型，或者如果它是集合執行個體，就會傳回特定的 `geometry` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="abd96-191">Once a `geometry` instance is constructed, you can use the following methods to determine if it is well-formed, return the instance type, or, if it is a collection instance, return a specific `geometry` instance.</span></span>  
  
 <span data-ttu-id="abd96-192">**傳回 geometry 類型的執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-192">**To return the instance type of a geometry**</span></span>  
 [<span data-ttu-id="abd96-193">STGeometryType &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-193">STGeometryType &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeometrytype-geometry-data-type)  
  
 <span data-ttu-id="abd96-194">**判斷 geometry 是否為特定的執行個體類型**</span><span class="sxs-lookup"><span data-stu-id="abd96-194">**To determine if a geometry is a given instance type**</span></span>  
 [<span data-ttu-id="abd96-195">InstanceOf &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-195">InstanceOf &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/instanceof-geometry-data-type)  
  
 <span data-ttu-id="abd96-196">**判斷 geometry 執行個體對於它的執行個體類型而言是否格式正確**</span><span class="sxs-lookup"><span data-stu-id="abd96-196">**To determine if a geometry instance is well-formed for its instance type**</span></span>  
 [<span data-ttu-id="abd96-197">STIsValid &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-197">STIsValid &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)  
  
 <span data-ttu-id="abd96-198">**將 geometry 執行個體轉換成具有執行個體類型的正確格式 geometry 執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-198">**To convert a geometry instance to a well-formed geometry instance with an instance type**</span></span>  
 [<span data-ttu-id="abd96-199">MakeValid &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-199">MakeValid &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)  
  
 <span data-ttu-id="abd96-200">**傳回幾何集合執行個體中的幾何數**</span><span class="sxs-lookup"><span data-stu-id="abd96-200">**To return the number of geometries in a geometry collection instance**</span></span>  
 [<span data-ttu-id="abd96-201">STNumGeometries &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-201">STNumGeometries &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stnumgeometries-geometry-data-type)  
  
 <span data-ttu-id="abd96-202">傳回幾何集合執行個體中的特定幾何</span><span class="sxs-lookup"><span data-stu-id="abd96-202">To return a specific geometry in a geometry collection instance</span></span>  
 <span data-ttu-id="abd96-203">[STGeometryN &#40;geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN (geometry 資料類型)</span><span class="sxs-lookup"><span data-stu-id="abd96-203">[STGeometryN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN (geometry Data type)</span></span>  
  
  
  
###  <a name="number-of-points"></a><a name="number"></a> <span data-ttu-id="abd96-204">點數</span><span class="sxs-lookup"><span data-stu-id="abd96-204">Number of Points</span></span>  
 <span data-ttu-id="abd96-205">所有非空 `geometry` 的實例都是由*點*組成。</span><span class="sxs-lookup"><span data-stu-id="abd96-205">All nonempty `geometry` instances are comprised of *points*.</span></span> <span data-ttu-id="abd96-206">這些點代表幾何繪製所在平面的 X 和 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="abd96-206">These points represent the X- and Y-coordinates of the plane on which the geometries are drawn.</span></span> <span data-ttu-id="abd96-207">`geometry`提供許多內建方法來查詢執行個體的點。</span><span class="sxs-lookup"><span data-stu-id="abd96-207">`geometry` provides numerous built-in methods for querying the points of an instance.</span></span>  
  
 <span data-ttu-id="abd96-208">**傳回組成執行個體的點數**</span><span class="sxs-lookup"><span data-stu-id="abd96-208">**To return the number of points that comprise an instance**</span></span>  
 [<span data-ttu-id="abd96-209">STNumPoints &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-209">STNumPoints &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)  
  
 <span data-ttu-id="abd96-210">**傳回執行個體中的特定點**</span><span class="sxs-lookup"><span data-stu-id="abd96-210">**To return a specific point in an instance**</span></span>  
 [<span data-ttu-id="abd96-211">STPointN</span><span class="sxs-lookup"><span data-stu-id="abd96-211">STPointN</span></span>](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 <span data-ttu-id="abd96-212">**傳回位於執行個體上的任意點**</span><span class="sxs-lookup"><span data-stu-id="abd96-212">**To return an arbitrary point that lies on an instance**</span></span>  
 [<span data-ttu-id="abd96-213">STPointOnSurface</span><span class="sxs-lookup"><span data-stu-id="abd96-213">STPointOnSurface</span></span>](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
 <span data-ttu-id="abd96-214">**傳回執行個體的起點**</span><span class="sxs-lookup"><span data-stu-id="abd96-214">**To return the start point of an instance**</span></span>  
 [<span data-ttu-id="abd96-215">STStartPoint</span><span class="sxs-lookup"><span data-stu-id="abd96-215">STStartPoint</span></span>](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)  
  
 <span data-ttu-id="abd96-216">**傳回執行個體的終點**</span><span class="sxs-lookup"><span data-stu-id="abd96-216">**To return the end point of an instance**</span></span>  
 [<span data-ttu-id="abd96-217">STEndpoint</span><span class="sxs-lookup"><span data-stu-id="abd96-217">STEndpoint</span></span>](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)  
  
 <span data-ttu-id="abd96-218">**傳回 Point 執行個體的 X 座標**</span><span class="sxs-lookup"><span data-stu-id="abd96-218">**To return the X-coordinate of a Point instance**</span></span>  
 [<span data-ttu-id="abd96-219">STX &#40;geometry 資料類型&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-219">STX &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stx-geometry-data-type)  
  
 <span data-ttu-id="abd96-220">**傳回 Point 執行個體的 Y 座標**</span><span class="sxs-lookup"><span data-stu-id="abd96-220">**To return the Y-coordinate of a Point instance**</span></span>  
 [<span data-ttu-id="abd96-221">STY</span><span class="sxs-lookup"><span data-stu-id="abd96-221">STY</span></span>](/sql/t-sql/spatial-geometry/sty-geometry-data-type)  
  
 <span data-ttu-id="abd96-222">**傳回 Polygon、CurvePolygon 或 MultiPolygon 執行個體的幾何中心點**</span><span class="sxs-lookup"><span data-stu-id="abd96-222">**To return the geometric center point of a Polygon, CurvePolygon, or MultiPolygon instance**</span></span>  
 [<span data-ttu-id="abd96-223">STCentroid</span><span class="sxs-lookup"><span data-stu-id="abd96-223">STCentroid</span></span>](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)  
  
  
  
###  <a name="dimension"></a><a name="dimension"></a> <span data-ttu-id="abd96-224">維度</span><span class="sxs-lookup"><span data-stu-id="abd96-224">Dimension</span></span>  
 <span data-ttu-id="abd96-225">非空的 `geometry` 執行個體可以是 0 維度、1 維度或 2 維度。</span><span class="sxs-lookup"><span data-stu-id="abd96-225">A nonempty `geometry` instance can be 0-, 1-, or 2-dimensional.</span></span> <span data-ttu-id="abd96-226">零維度 `geometries` (如 `Point` 和 `MultiPoint`) 沒有長度或區域。</span><span class="sxs-lookup"><span data-stu-id="abd96-226">Zero-dimensional `geometries`, such as `Point` and `MultiPoint`, have no length or area.</span></span> <span data-ttu-id="abd96-227">一維度物件 (如 `LineString, CircularString, CompoundCurve` 和 `MultiLineString`) 具有長度。</span><span class="sxs-lookup"><span data-stu-id="abd96-227">One-dimensional objects, such as `LineString, CircularString, CompoundCurve`, and `MultiLineString`, have length.</span></span> <span data-ttu-id="abd96-228">二維度執行個體 (如 `Polygon`、`CurvePolygon` 和 `MultiPolygon`) 具有區域和長度。</span><span class="sxs-lookup"><span data-stu-id="abd96-228">Two-dimensional instances, such as `Polygon`, `CurvePolygon`, and `MultiPolygon`, have area and length.</span></span> <span data-ttu-id="abd96-229">空的執行個體將會報告 -1 的維度，而 `GeometryCollection` 則會報告與其內容類型相依的區域。</span><span class="sxs-lookup"><span data-stu-id="abd96-229">Empty instances will report a dimension of -1, and a `GeometryCollection` will report an area dependent on the types of its contents.</span></span>  
  
 <span data-ttu-id="abd96-230">**傳回執行個體的維度**</span><span class="sxs-lookup"><span data-stu-id="abd96-230">**To return the dimension of an instance**</span></span>  
 [<span data-ttu-id="abd96-231">STDimension</span><span class="sxs-lookup"><span data-stu-id="abd96-231">STDimension</span></span>](/sql/t-sql/spatial-geometry/stdimension-geometry-data-type)  
  
 <span data-ttu-id="abd96-232">**傳回執行個體的長度**</span><span class="sxs-lookup"><span data-stu-id="abd96-232">**To return the length of an instance**</span></span>  
 [<span data-ttu-id="abd96-233">STLength</span><span class="sxs-lookup"><span data-stu-id="abd96-233">STLength</span></span>](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)  
  
 <span data-ttu-id="abd96-234">**傳回執行個體的區域**</span><span class="sxs-lookup"><span data-stu-id="abd96-234">**To return the area of an instance**</span></span>  
 [<span data-ttu-id="abd96-235">STArea</span><span class="sxs-lookup"><span data-stu-id="abd96-235">STArea</span></span>](/sql/t-sql/spatial-geometry/starea-geometry-data-type)  
  
  
  
###  <a name="empty"></a><a name="empty"></a> <span data-ttu-id="abd96-236">Empty</span><span class="sxs-lookup"><span data-stu-id="abd96-236">Empty</span></span>  
 <span data-ttu-id="abd96-237">*空*的 `geometry` 實例沒有任何點。</span><span class="sxs-lookup"><span data-stu-id="abd96-237">An *empty*`geometry` instance does not have any points.</span></span> <span data-ttu-id="abd96-238">空的 `LineString, CircularString`、`CompoundCurve` 和 `MultiLineString` 執行個體的長度是零。</span><span class="sxs-lookup"><span data-stu-id="abd96-238">The length of empty `LineString, CircularString`, `CompoundCurve`, and `MultiLineString` instances is zero.</span></span> <span data-ttu-id="abd96-239">空的 `Polygon`、`CurvePolygon` 和 `MultiPolygon` 執行個體的區域是 0。</span><span class="sxs-lookup"><span data-stu-id="abd96-239">The area of empty `Polygon`, `CurvePolygon`, and `MultiPolygon` instances is 0.</span></span>  
  
 <span data-ttu-id="abd96-240">**判斷執行個體是否為空的**</span><span class="sxs-lookup"><span data-stu-id="abd96-240">**To determine if an instance is empty**</span></span>  
 <span data-ttu-id="abd96-241">[STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type)。</span><span class="sxs-lookup"><span data-stu-id="abd96-241">[STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type).</span></span>  
  
  
  
###  <a name="simple"></a><a name="simple"></a> <span data-ttu-id="abd96-242">Simple</span><span class="sxs-lookup"><span data-stu-id="abd96-242">Simple</span></span>  
 <span data-ttu-id="abd96-243">`geometry`若要讓實例成為*簡單*的，它必須符合這兩項需求：</span><span class="sxs-lookup"><span data-stu-id="abd96-243">For a `geometry` of the instance to be *simple*, it must meet both of these requirements:</span></span>  
  
-   <span data-ttu-id="abd96-244">此例項的每一個圖形都不能自己相交 (除了在它的端點上以外)。</span><span class="sxs-lookup"><span data-stu-id="abd96-244">Each figure of the instance must not intersect itself, except at its endpoints.</span></span>  
  
-   <span data-ttu-id="abd96-245">此例項的兩個圖形不能在非兩者界限內的點上彼此相交。</span><span class="sxs-lookup"><span data-stu-id="abd96-245">No two figures of the instance can intersect each other at a point that is not in both of their boundaries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="abd96-246">空的幾何一定是簡單的幾何。</span><span class="sxs-lookup"><span data-stu-id="abd96-246">Empty geometries are always simple.</span></span>  
  
 <span data-ttu-id="abd96-247">**判斷執行個體是否為簡單**</span><span class="sxs-lookup"><span data-stu-id="abd96-247">**To determine if an instance is simple**</span></span>  
 <span data-ttu-id="abd96-248">[STIsSimple](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type)。</span><span class="sxs-lookup"><span data-stu-id="abd96-248">[STIsSimple](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type).</span></span>  
  
  
  
###  <a name="boundary-interior-and-exterior"></a><a name="boundary"></a> <span data-ttu-id="abd96-249">界限、內部和外部</span><span class="sxs-lookup"><span data-stu-id="abd96-249">Boundary, Interior, and Exterior</span></span>  
 <span data-ttu-id="abd96-250">實例的*內部* `geometry` 是實例所佔用的空間，而*外部*則是未佔用的空間。</span><span class="sxs-lookup"><span data-stu-id="abd96-250">The *interior* of a `geometry` instance is the space occupied by the instance, and the *exterior* is the space not occupied it.</span></span>  
  
 <span data-ttu-id="abd96-251">*「界限」* (Boundary) 是由 OGC 定義如下：</span><span class="sxs-lookup"><span data-stu-id="abd96-251">*Boundary* is defined by the OGC as follows:</span></span>  
  
-   <span data-ttu-id="abd96-252">`Point` 和 `MultiPoint` 執行個體沒有界限。</span><span class="sxs-lookup"><span data-stu-id="abd96-252">`Point` and `MultiPoint` instances do not have a boundary.</span></span>  
  
-   <span data-ttu-id="abd96-253">`LineString` 和 `MultiLineString` 界限是由起點和終點所組成，移除發生偶數次數的點。</span><span class="sxs-lookup"><span data-stu-id="abd96-253">`LineString` and `MultiLineString` boundaries are formed by the start points and end points, removing those that occur an even number of times.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 1, 0 0, 1 0, 0 1), (1 1, 1 0))');  
SELECT @g.STBoundary().ToString();  
```  
  
 <span data-ttu-id="abd96-254">`Polygon` 或 `MultiPolygon` 執行個體的界限是它的環形集合。</span><span class="sxs-lookup"><span data-stu-id="abd96-254">The boundary of a `Polygon` or `MultiPolygon` instance is the set of its rings.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0), (1 1, 1 2, 2 2, 2 1, 1 1))');  
SELECT @g.STBoundary().ToString();  
```  
  
 <span data-ttu-id="abd96-255">**傳回執行個體的界限**</span><span class="sxs-lookup"><span data-stu-id="abd96-255">**To return the boundary of an instance**</span></span>  
 [<span data-ttu-id="abd96-256">STBoundary</span><span class="sxs-lookup"><span data-stu-id="abd96-256">STBoundary</span></span>](/sql/t-sql/spatial-geometry/stboundary-geometry-data-type)  
  
  
  
###  <a name="envelope"></a><a name="envelope"></a> <span data-ttu-id="abd96-257">範圍</span><span class="sxs-lookup"><span data-stu-id="abd96-257">Envelope</span></span>  
 <span data-ttu-id="abd96-258">實例的*信封* `geometry` （也稱為周*框*方塊）是以軸對齊的矩形，由實例的最小值和最大值 (X，Y) 座標所組成。</span><span class="sxs-lookup"><span data-stu-id="abd96-258">The *envelope* of a `geometry` instance, also known as the *bounding box*, is the axis-aligned rectangle formed by the minimum and maximum (X,Y) coordinates of the instance.</span></span>  
  
 <span data-ttu-id="abd96-259">**傳回執行個體的範圍**</span><span class="sxs-lookup"><span data-stu-id="abd96-259">**To return the envelope of an instance**</span></span>  
 [<span data-ttu-id="abd96-260">STEnvelope</span><span class="sxs-lookup"><span data-stu-id="abd96-260">STEnvelope</span></span>](/sql/t-sql/spatial-geometry/stenvelope-geometry-data-type)  
  
  
  
###  <a name="closure"></a><a name="closure"></a> <span data-ttu-id="abd96-261">封閉性</span><span class="sxs-lookup"><span data-stu-id="abd96-261">Closure</span></span>  
 <span data-ttu-id="abd96-262">*封閉式* `geometry` 實例是起始點和結束點相同的圖形。</span><span class="sxs-lookup"><span data-stu-id="abd96-262">A *closed*`geometry` instance is a figure whose start points and end points are the same.</span></span> <span data-ttu-id="abd96-263">`Polygon` 執行個體視為封閉式。</span><span class="sxs-lookup"><span data-stu-id="abd96-263">`Polygon` instances are considered closed.</span></span> <span data-ttu-id="abd96-264">`Point` 執行個體視為非封閉式。</span><span class="sxs-lookup"><span data-stu-id="abd96-264">`Point` instances are not closed.</span></span>  
  
 <span data-ttu-id="abd96-265">環形是簡單、封閉的 `LineString` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="abd96-265">A ring is a simple, closed `LineString` instance.</span></span>  
  
 <span data-ttu-id="abd96-266">**判斷執行個體是否為封閉**</span><span class="sxs-lookup"><span data-stu-id="abd96-266">**To determine if an instance is closed**</span></span>  
 [<span data-ttu-id="abd96-267">STIsClosed</span><span class="sxs-lookup"><span data-stu-id="abd96-267">STIsClosed</span></span>](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)  
  
 <span data-ttu-id="abd96-268">**判斷執行個體是否為環形**</span><span class="sxs-lookup"><span data-stu-id="abd96-268">**To determine if an instance is a ring**</span></span>  
 [<span data-ttu-id="abd96-269">STIsRing</span><span class="sxs-lookup"><span data-stu-id="abd96-269">STIsRing</span></span>](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)  
  
 <span data-ttu-id="abd96-270">**傳回 Polygon 執行個體的外部環形**</span><span class="sxs-lookup"><span data-stu-id="abd96-270">**To return the exterior ring of a Polygon instance**</span></span>  
 [<span data-ttu-id="abd96-271">STExteriorRing</span><span class="sxs-lookup"><span data-stu-id="abd96-271">STExteriorRing</span></span>](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type)  
  
 <span data-ttu-id="abd96-272">**傳回 Polygon 中的內部環形數**</span><span class="sxs-lookup"><span data-stu-id="abd96-272">**To return the number of interior rings in a Polygon**</span></span>  
 [<span data-ttu-id="abd96-273">STNumInteriorRing</span><span class="sxs-lookup"><span data-stu-id="abd96-273">STNumInteriorRing</span></span>](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type)  
  
 <span data-ttu-id="abd96-274">**傳回 Polygon 的指定內部環形**</span><span class="sxs-lookup"><span data-stu-id="abd96-274">**To return a specified interior ring of a Polygon**</span></span>  
 [<span data-ttu-id="abd96-275">STInteriorRingN</span><span class="sxs-lookup"><span data-stu-id="abd96-275">STInteriorRingN</span></span>](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type)  
  
  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> <span data-ttu-id="abd96-276">空間參考識別碼 (SRID)</span><span class="sxs-lookup"><span data-stu-id="abd96-276">Spatial Reference ID (SRID)</span></span>  
 <span data-ttu-id="abd96-277">空間參考識別碼 (SRID) 是用來指定代表 `geometry` 執行個體之座標系統的識別碼。</span><span class="sxs-lookup"><span data-stu-id="abd96-277">The spatial reference ID (SRID) is an identifier specifying which coordinate system the `geometry` instance is represented in.</span></span> <span data-ttu-id="abd96-278">具有不同 SRID 的兩個執行個體無法進行比較。</span><span class="sxs-lookup"><span data-stu-id="abd96-278">Two instances with different SRIDs are incomparable.</span></span>  
  
 <span data-ttu-id="abd96-279">**設定或傳回執行個體的 SRID**</span><span class="sxs-lookup"><span data-stu-id="abd96-279">**To set or return the SRID of an instance**</span></span>  
 [<span data-ttu-id="abd96-280">STSrid</span><span class="sxs-lookup"><span data-stu-id="abd96-280">STSrid</span></span>](/sql/t-sql/spatial-geometry/stsrid-geometry-data-type)  
  
 <span data-ttu-id="abd96-281">這個屬性可以修改。</span><span class="sxs-lookup"><span data-stu-id="abd96-281">This property can be modified.</span></span>  
  
  
  
##  <a name="determining-relationships-between-geometry-instances"></a><a name="rel"></a> <span data-ttu-id="abd96-282">判斷 geometry 執行個體之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="abd96-282">Determining Relationships between geometry Instances</span></span>  
 <span data-ttu-id="abd96-283">`geometry` 資料類型提供許多內建方法，您可以使用這些方法來判斷兩個 `geometry` 執行個體之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="abd96-283">The `geometry` data type provides many built-in methods you can use to determine relationships between two `geometry` instances.</span></span>  
  
 <span data-ttu-id="abd96-284">**判斷兩個執行個體是否組成相同的點集合**</span><span class="sxs-lookup"><span data-stu-id="abd96-284">**To determine if two instances comprise the same point set**</span></span>  
 [<span data-ttu-id="abd96-285">STEquals</span><span class="sxs-lookup"><span data-stu-id="abd96-285">STEquals</span></span>](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 <span data-ttu-id="abd96-286">**判斷兩個執行個體是否不相交**</span><span class="sxs-lookup"><span data-stu-id="abd96-286">**To determine if two instances are disjoint**</span></span>  
 [<span data-ttu-id="abd96-287">STDisjoint</span><span class="sxs-lookup"><span data-stu-id="abd96-287">STDisjoint</span></span>](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 <span data-ttu-id="abd96-288">**判斷兩個執行個體是否相交**</span><span class="sxs-lookup"><span data-stu-id="abd96-288">**To determine if two instances intersect**</span></span>  
 [<span data-ttu-id="abd96-289">STIntersects</span><span class="sxs-lookup"><span data-stu-id="abd96-289">STIntersects</span></span>](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 <span data-ttu-id="abd96-290">**判斷兩個執行個體是否接觸**</span><span class="sxs-lookup"><span data-stu-id="abd96-290">**To determine if two instances touch**</span></span>  
 [<span data-ttu-id="abd96-291">STTouches</span><span class="sxs-lookup"><span data-stu-id="abd96-291">STTouches</span></span>](/sql/t-sql/spatial-geometry/sttouches-geometry-data-type)  
  
 <span data-ttu-id="abd96-292">**判斷兩個執行個體是否重疊**</span><span class="sxs-lookup"><span data-stu-id="abd96-292">**To determine if two instances overlap**</span></span>  
 [<span data-ttu-id="abd96-293">STOverlaps</span><span class="sxs-lookup"><span data-stu-id="abd96-293">STOverlaps</span></span>](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 <span data-ttu-id="abd96-294">**判斷兩個執行個體是否交叉**</span><span class="sxs-lookup"><span data-stu-id="abd96-294">**To determine if two instances cross**</span></span>  
 [<span data-ttu-id="abd96-295">STCrosses</span><span class="sxs-lookup"><span data-stu-id="abd96-295">STCrosses</span></span>](/sql/t-sql/spatial-geometry/stcrosses-geometry-data-type)  
  
 <span data-ttu-id="abd96-296">**判斷某個執行個體是否在另一個執行個體內**</span><span class="sxs-lookup"><span data-stu-id="abd96-296">**To determine if one instance is within another**</span></span>  
 [<span data-ttu-id="abd96-297">STWithin</span><span class="sxs-lookup"><span data-stu-id="abd96-297">STWithin</span></span>](/sql/t-sql/spatial-geometry/stwithin-geometry-data-type)  
  
 <span data-ttu-id="abd96-298">**判斷某個執行個體是否包含另一個執行個體**</span><span class="sxs-lookup"><span data-stu-id="abd96-298">**To determine if one instance contains another**</span></span>  
 [<span data-ttu-id="abd96-299">STContains</span><span class="sxs-lookup"><span data-stu-id="abd96-299">STContains</span></span>](/sql/t-sql/spatial-geometry/stcontains-geometry-data-type)  
  
 <span data-ttu-id="abd96-300">**判斷某個執行個體是否與另一個執行個體重疊**</span><span class="sxs-lookup"><span data-stu-id="abd96-300">**To determine if one instance overlaps another**</span></span>  
 [<span data-ttu-id="abd96-301">STOverlaps</span><span class="sxs-lookup"><span data-stu-id="abd96-301">STOverlaps</span></span>](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 <span data-ttu-id="abd96-302">**判斷兩個執行個體在空間上是否相關**</span><span class="sxs-lookup"><span data-stu-id="abd96-302">**To determine if two instances are spatially related**</span></span>  
 [<span data-ttu-id="abd96-303">STRelate</span><span class="sxs-lookup"><span data-stu-id="abd96-303">STRelate</span></span>](/sql/t-sql/spatial-geometry/strelate-geometry-data-type)  
  
 <span data-ttu-id="abd96-304">**判斷兩個 geometry 內點與點之間的最短距離**</span><span class="sxs-lookup"><span data-stu-id="abd96-304">**To determine the shortest distance between points in two geometries**</span></span>  
 [<span data-ttu-id="abd96-305">STDistance</span><span class="sxs-lookup"><span data-stu-id="abd96-305">STDistance</span></span>](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
  
  
##  <a name="geometry-instances-default-to-zero-srid"></a><a name="defaultsrid"></a> <span data-ttu-id="abd96-306">geometry 執行個體預設為零 SRID</span><span class="sxs-lookup"><span data-stu-id="abd96-306">geometry Instances Default to Zero SRID</span></span>  
 <span data-ttu-id="abd96-307">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中 `geometry` 執行個體的預設 SRID 是 0。</span><span class="sxs-lookup"><span data-stu-id="abd96-307">The default SRID for `geometry` instances in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is 0.</span></span> <span data-ttu-id="abd96-308">有了 `geometry` 空間資料，執行計算時並不需要空間執行個體的特定 SRID；因此，執行個體可位於未定義的平面空間內。</span><span class="sxs-lookup"><span data-stu-id="abd96-308">With `geometry` spatial data, the specific SRID of the spatial instance is not required to perform calculations; thus, instances can reside in undefined planar space.</span></span> <span data-ttu-id="abd96-309">若要在 `geometry` 資料類型方法的計算中指示未定義的平面空間，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會使用 SRID 0。</span><span class="sxs-lookup"><span data-stu-id="abd96-309">To indicate undefined planar space in the calculations of `geometry` data type methods, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses SRID 0.</span></span>  
  
##  <a name="examples"></a><a name="examples"></a> <span data-ttu-id="abd96-310">範例</span><span class="sxs-lookup"><span data-stu-id="abd96-310">Examples</span></span>  
 <span data-ttu-id="abd96-311">下列兩個範例示範如何加入及查詢幾何資料。</span><span class="sxs-lookup"><span data-stu-id="abd96-311">The following two examples show how to add and query geometry data.</span></span>  
  
-   <span data-ttu-id="abd96-312">第一個範例會建立具有識別資料行及 `geometry` 資料行 `GeomCol1`的資料表。</span><span class="sxs-lookup"><span data-stu-id="abd96-312">The first example creates a table with an identity column and a `geometry` column `GeomCol1`.</span></span> <span data-ttu-id="abd96-313">第三個資料行會將 `geometry` 資料行轉譯成它的開放地理空間協會 (Open Geospatial Consortium，OGC) 已知的文字 (Well-Known Text，WKT) 表示法，並使用 `STAsText()` 方法。</span><span class="sxs-lookup"><span data-stu-id="abd96-313">A third column renders the `geometry` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method.</span></span> <span data-ttu-id="abd96-314">然後會插入兩個資料列：一個資料列包含 `LineString` 的 `geometry`執行個體，另一個資料列包含 `Polygon` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="abd96-314">Two rows are then inserted: one row contains a `LineString` instance of `geometry`, and one row contains a `Polygon` instance.</span></span>  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeomCol1 geometry,   
        GeomCol2 AS GeomCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('LINESTRING (100 100, 20 180, 180 180)', 0));  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('POLYGON ((0 0, 150 0, 150 150, 0 150, 0 0))', 0));  
    GO  
    ```  
  
-   <span data-ttu-id="abd96-315">第二個範例使用 `STIntersection()` 方法傳回之前插入之兩個 `geometry` 執行個體相交的點。</span><span class="sxs-lookup"><span data-stu-id="abd96-315">The second example uses the `STIntersection()` method to return the points where the two previously inserted `geometry` instances intersect.</span></span>  
  
    ```  
    DECLARE @geom1 geometry;  
    DECLARE @geom2 geometry;  
    DECLARE @result geometry;  
  
    SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geom1.STIntersection(@geom2);  
    SELECT @result.STAsText();  
    ```  
  
  
  
## <a name="see-also"></a><span data-ttu-id="abd96-316">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abd96-316">See Also</span></span>  
 [<span data-ttu-id="abd96-317">空間資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="abd96-317">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
