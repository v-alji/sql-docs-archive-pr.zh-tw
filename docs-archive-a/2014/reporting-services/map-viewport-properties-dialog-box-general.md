---
title: 地圖視口屬性對話方塊、一般 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d760d6a0572cbbd1bd948eab382c0727eb276c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585128"
---
# <a name="map-viewport-properties-dialog-box-general"></a><span data-ttu-id="5d25d-102">地圖檢視區屬性對話方塊、一般</span><span class="sxs-lookup"><span data-stu-id="5d25d-102">Map Viewport Properties Dialog Box, General</span></span>
  <span data-ttu-id="5d25d-103">選取 **[地圖檢視區屬性]** 對話方塊上的 **[一般]** 來變更座標系統、投射以及界限選項。</span><span class="sxs-lookup"><span data-stu-id="5d25d-103">Select **General** on the **Map Viewport Properties** dialog box to change the coordinate system, the projection, and the boundary options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d25d-104">選項</span><span class="sxs-lookup"><span data-stu-id="5d25d-104">Options</span></span>  
 <span data-ttu-id="5d25d-105">**座標系統**</span><span class="sxs-lookup"><span data-stu-id="5d25d-105">**Coordinate system**</span></span>  
 <span data-ttu-id="5d25d-106">指出地圖資料使用之座標系統的類型。</span><span class="sxs-lookup"><span data-stu-id="5d25d-106">Indicate the type of coordinate system that the map data uses.</span></span>  
  
-   <span data-ttu-id="5d25d-107">**平面** ：當地圖資料使用 X 和 Y 座標 (例如建置規劃) 時，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="5d25d-107">**Planar** Choose this option when map data is in X and Y coordinates, for example, for building plans.</span></span>  
  
-   <span data-ttu-id="5d25d-108">**地理** ：當地圖資料使用經度和緯度座標 (例如城市位置) 時，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="5d25d-108">**Geographic** Choose this option when map data is in longitude and latitude coordinates, for example, for city locations.</span></span>  
  
 <span data-ttu-id="5d25d-109">**Projection**</span><span class="sxs-lookup"><span data-stu-id="5d25d-109">**Projection**</span></span>  
 <span data-ttu-id="5d25d-110">指定將地理座標投射在二維度介面所使用的方法。</span><span class="sxs-lookup"><span data-stu-id="5d25d-110">Specify the method to use to project geographic coordinates onto a two-dimensional surface.</span></span> <span data-ttu-id="5d25d-111">選擇與您要視覺化之資料相容的投射。</span><span class="sxs-lookup"><span data-stu-id="5d25d-111">Choose a projection that is compatible with the data that you are visualizing.</span></span> <span data-ttu-id="5d25d-112">受到投射影響的四個空間屬性為區域、形狀、距離與方向。</span><span class="sxs-lookup"><span data-stu-id="5d25d-112">The four spatial properties that are affected by projection are area, shape, distance, and direction.</span></span> <span data-ttu-id="5d25d-113">若是地球檢視，良好的投射選項取決於置中檢視、地圖界限與縮放因數。</span><span class="sxs-lookup"><span data-stu-id="5d25d-113">For views of the earth, a good choice of projection depends on the center view, the map boundaries, and the zoom factor.</span></span>  
  
 <span data-ttu-id="5d25d-114">下列每個屬性都會保留其中一個或多個空間屬性：</span><span class="sxs-lookup"><span data-stu-id="5d25d-114">Each of the following projections preserves one or more of these spatial properties:</span></span>  
  
-   <span data-ttu-id="5d25d-115">**Equirectangular** ：選擇此選項可以將經度和緯度當做矩形座標使用。</span><span class="sxs-lookup"><span data-stu-id="5d25d-115">**Equirectangular** Choose this option to use longitude and latitude as rectangular coordinates.</span></span>  
  
-   <span data-ttu-id="5d25d-116">**Mercator** ：如果區域較小、赤道周圍扭曲程度較小，或者您想要以使用 Mercator 投射的現有影像分割圖層加入地圖圖層時，選擇這個常用的投射方法。</span><span class="sxs-lookup"><span data-stu-id="5d25d-116">**Mercator** Choose this popular projection for smaller areas, for less distortion around the equator, or when you want to add a map layer with an existing tile layer that uses the Mercator projection.</span></span>  
  
-   <span data-ttu-id="5d25d-117">**Robinson** ：如果從赤道跨越兩極的大型區域扭曲程度較少，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="5d25d-117">**Robinson** Choose this option for less distortion of large areas that span from the equator to the poles.</span></span> <span data-ttu-id="5d25d-118">此屬性是由 Arthur H. Robinson 在 1963 年開發。</span><span class="sxs-lookup"><span data-stu-id="5d25d-118">Developed by Arthur H. Robinson in 1963.</span></span>  
  
-   <span data-ttu-id="5d25d-119">**Fahey** ：如果從赤道跨越兩極的大型區域扭曲程度較少，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="5d25d-119">**Fahey** Choose this option for less distortion of large areas that span from the equator to the poles.</span></span> <span data-ttu-id="5d25d-120">此屬性是由 Lawrence Fahey 在 1975 年開發。</span><span class="sxs-lookup"><span data-stu-id="5d25d-120">Developed by Lawrence Fahey in 1975.</span></span>  
  
-   <span data-ttu-id="5d25d-121">**Eckert1** ：使用此選項以便針對緯度使用等距的平行線，並針對經度的經線使用直線。</span><span class="sxs-lookup"><span data-stu-id="5d25d-121">**Eckert1** Choose this option to use equally spaced parallels in latitude and straight lines for meridians in longitude.</span></span>  
  
-   <span data-ttu-id="5d25d-122">**Eckert3** ：使用此選項以便針對緯度使用等距的平行線，並針對經度的經線使用曲線。</span><span class="sxs-lookup"><span data-stu-id="5d25d-122">**Eckert3** Choose this option to use equally spaced parallels in latitude and curved lines for meridians in longitude.</span></span>  
  
-   <span data-ttu-id="5d25d-123">**HammerAitoff** ：針對極地地圖或世界地圖使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5d25d-123">**HammerAitoff** Choose this option for polar maps or world maps.</span></span>  
  
-   <span data-ttu-id="5d25d-124">**Wagner3** ：針對世界地圖使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5d25d-124">**Wagner3** Choose this option for world maps.</span></span>  
  
-   <span data-ttu-id="5d25d-125">**Bonne** ：選擇此選項可以在世界出現在地圖集時進行檢視。</span><span class="sxs-lookup"><span data-stu-id="5d25d-125">**Bonne** Choose this option to view the world as it appears in an atlas.</span></span>  
  
 <span data-ttu-id="5d25d-126">**分頁符號選項**</span><span class="sxs-lookup"><span data-stu-id="5d25d-126">**Page break options**</span></span>  
 <span data-ttu-id="5d25d-127">選取選項來指示如何將內容納入報表頁面。</span><span class="sxs-lookup"><span data-stu-id="5d25d-127">Select options to indicate how content is fitted to a report page.</span></span>  
  
 <span data-ttu-id="5d25d-128">**界限摘要**</span><span class="sxs-lookup"><span data-stu-id="5d25d-128">**Boundary options**</span></span>  
 <span data-ttu-id="5d25d-129">指定座標的下限與上限來控制地圖出現在報表中的部分。</span><span class="sxs-lookup"><span data-stu-id="5d25d-129">Specify the lower and upper boundaries for coordinates to control which part of the map appears in the report.</span></span>  
  
 <span data-ttu-id="5d25d-130">**最小 X**</span><span class="sxs-lookup"><span data-stu-id="5d25d-130">**Minimum X**</span></span>  
 <span data-ttu-id="5d25d-131">最小的 X 值。</span><span class="sxs-lookup"><span data-stu-id="5d25d-131">Lowest X value.</span></span> <span data-ttu-id="5d25d-132">僅適用於 **[平面]** 。</span><span class="sxs-lookup"><span data-stu-id="5d25d-132">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="5d25d-133">**最大 X**</span><span class="sxs-lookup"><span data-stu-id="5d25d-133">**Maximum X**</span></span>  
 <span data-ttu-id="5d25d-134">最大的 X 值。</span><span class="sxs-lookup"><span data-stu-id="5d25d-134">Highest X value.</span></span> <span data-ttu-id="5d25d-135">僅適用於 **[平面]** 。</span><span class="sxs-lookup"><span data-stu-id="5d25d-135">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="5d25d-136">**最小 Y**</span><span class="sxs-lookup"><span data-stu-id="5d25d-136">**Minimum Y**</span></span>  
 <span data-ttu-id="5d25d-137">最小的 Y 值。</span><span class="sxs-lookup"><span data-stu-id="5d25d-137">Lowest Y value.</span></span> <span data-ttu-id="5d25d-138">僅適用於 **[平面]** 。</span><span class="sxs-lookup"><span data-stu-id="5d25d-138">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="5d25d-139">**最大 Y**</span><span class="sxs-lookup"><span data-stu-id="5d25d-139">**Maximum Y**</span></span>  
 <span data-ttu-id="5d25d-140">最大的 Y 值。</span><span class="sxs-lookup"><span data-stu-id="5d25d-140">Highest Y value.</span></span> <span data-ttu-id="5d25d-141">僅適用於 **[平面]** 。</span><span class="sxs-lookup"><span data-stu-id="5d25d-141">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="5d25d-142">**最小經度**</span><span class="sxs-lookup"><span data-stu-id="5d25d-142">**Minimum Longitude**</span></span>  
 <span data-ttu-id="5d25d-143">最小的經度值。</span><span class="sxs-lookup"><span data-stu-id="5d25d-143">Lowest longitude value.</span></span> <span data-ttu-id="5d25d-144">僅適用於 **[地理]** 。</span><span class="sxs-lookup"><span data-stu-id="5d25d-144">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="5d25d-145">**最大經度**</span><span class="sxs-lookup"><span data-stu-id="5d25d-145">**Maximum Longitude**</span></span>  
 <span data-ttu-id="5d25d-146">最大的經度值。</span><span class="sxs-lookup"><span data-stu-id="5d25d-146">Highest longitude value.</span></span> <span data-ttu-id="5d25d-147">僅適用於 **[地理]** 。</span><span class="sxs-lookup"><span data-stu-id="5d25d-147">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="5d25d-148">**最小緯度**</span><span class="sxs-lookup"><span data-stu-id="5d25d-148">**Minimum Latitude**</span></span>  
 <span data-ttu-id="5d25d-149">最小的緯度值。</span><span class="sxs-lookup"><span data-stu-id="5d25d-149">Lowest latitude value.</span></span> <span data-ttu-id="5d25d-150">僅適用於 **[地理]** 。</span><span class="sxs-lookup"><span data-stu-id="5d25d-150">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="5d25d-151">**最大緯度**</span><span class="sxs-lookup"><span data-stu-id="5d25d-151">**Maximum Latitude**</span></span>  
 <span data-ttu-id="5d25d-152">最大的緯度值。</span><span class="sxs-lookup"><span data-stu-id="5d25d-152">Highest latitude value.</span></span> <span data-ttu-id="5d25d-153">僅適用於 **[地理]** 。</span><span class="sxs-lookup"><span data-stu-id="5d25d-153">Available for **Geographic** only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d25d-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d25d-154">See Also</span></span>  
 [<span data-ttu-id="5d25d-155">地圖 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5d25d-155">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
