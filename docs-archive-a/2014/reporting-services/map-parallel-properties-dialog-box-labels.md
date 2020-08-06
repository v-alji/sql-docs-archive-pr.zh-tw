---
title: 地圖平行屬性對話方塊、標籤 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapparallelproperties.labels.f1
- "10519"
ms.assetid: 4560a7e4-e19b-4a6e-8ef4-e963497e01ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c08baa31ad8ee65f1f096ecf4304803a79e0fbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585129"
---
# <a name="map-parallel-properties-dialog-box-labels"></a><span data-ttu-id="1e6ab-102">地圖平行屬性對話方塊、標籤</span><span class="sxs-lookup"><span data-stu-id="1e6ab-102">Map Parallel Properties Dialog Box, Labels</span></span>
  <span data-ttu-id="1e6ab-103">使用 [ **MapParallel 屬性**] 對話方塊，即可變更地圖區中水準方格的標籤選項。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-103">Use the **MapParallel Properties** dialog box to change label options for the horizontal grid in the map viewport.</span></span> <span data-ttu-id="1e6ab-104">根據指定之檢視區的座標系統，平行表示下列值：</span><span class="sxs-lookup"><span data-stu-id="1e6ab-104">A parallel represents the following value depending on the specified coordinate system for the viewport:</span></span>  
  
-   <span data-ttu-id="1e6ab-105">**平面.**</span><span class="sxs-lookup"><span data-stu-id="1e6ab-105">**Planar.**</span></span> <span data-ttu-id="1e6ab-106">X 座標。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-106">The X coordinate.</span></span>  
  
-   <span data-ttu-id="1e6ab-107">**地理：**</span><span class="sxs-lookup"><span data-stu-id="1e6ab-107">**Geographic.**</span></span> <span data-ttu-id="1e6ab-108">目前投射的緯度。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-108">The latitude for the current projection.</span></span>  
  
 <span data-ttu-id="1e6ab-109">按一下 **[運算式]** (*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-109">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e6ab-110">選項</span><span class="sxs-lookup"><span data-stu-id="1e6ab-110">Options</span></span>  
 <span data-ttu-id="1e6ab-111">**間隔**</span><span class="sxs-lookup"><span data-stu-id="1e6ab-111">**Interval**</span></span>  
 <span data-ttu-id="1e6ab-112">輸入指定平行之間間隔的整數值 (以度數為單位)。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-112">Type an integer value in degrees that specifies the interval between parallels.</span></span> <span data-ttu-id="1e6ab-113">根據預設，會選取 **[自動]** 。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-113">By default, **Auto** is selected.</span></span> <span data-ttu-id="1e6ab-114">如果此選項設定為 **[自動]**，則值由地圖資料集的資料決定。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-114">If this option is set to **Auto**, the value is determined by the data from the map dataset.</span></span>  
  
 <span data-ttu-id="1e6ab-115">**顯示標籤**</span><span class="sxs-lookup"><span data-stu-id="1e6ab-115">**Show labels**</span></span>  
 <span data-ttu-id="1e6ab-116">選取此選項即可顯示平行的標籤。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-116">Select this option to display labels for the parallels.</span></span>  
  
 <span data-ttu-id="1e6ab-117">**放置**</span><span class="sxs-lookup"><span data-stu-id="1e6ab-117">**Placement**</span></span>  
 <span data-ttu-id="1e6ab-118">選取要顯示相對於檢視區上方、中間與下方之標籤的位置。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-118">Select a location to display the labels relative to the top, center, and bottom of the viewport.</span></span> <span data-ttu-id="1e6ab-119">預設位置為 **[靠近]**。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-119">The default placement is **Near**.</span></span>  
  
-   <span data-ttu-id="1e6ab-120">**靠近** ：在上方顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-120">**Near** Display labels at the top.</span></span>  
  
-   <span data-ttu-id="1e6ab-121">**四分之一** ：在上方和中間之間的一半位置顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-121">**One Quarter** Display labels half way between the top and the center.</span></span>  
  
-   <span data-ttu-id="1e6ab-122">**中間** ：在中間顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-122">**Center** Display labels at the center.</span></span>  
  
-   <span data-ttu-id="1e6ab-123">**四分之三** ：在中間和下方之間的一半位置顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-123">**Three Quarters** Display labels half way between the center and the bottom.</span></span>  
  
-   <span data-ttu-id="1e6ab-124">**遠方** ：在下方顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="1e6ab-124">**Far** Display labels at the bottom.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e6ab-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e6ab-125">See Also</span></span>  
 <span data-ttu-id="1e6ab-126">[地圖 &#40;報表產生器及 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1e6ab-126">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1e6ab-127">變更地圖圖例、色階與相關的規則 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1e6ab-127">Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;</span></span>](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
