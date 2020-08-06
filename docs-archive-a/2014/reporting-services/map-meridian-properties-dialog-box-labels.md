---
title: 地圖經線屬性對話方塊、標籤 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapmeridianproperties.labels.f1
- "10518"
ms.assetid: 47650a82-3b0c-4e32-8565-e9332bdcf4d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 146e2062185b4b4cd07ab791bd7552e9fd0064cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708913"
---
# <a name="map-meridian-properties-dialog-box-labels"></a><span data-ttu-id="0b228-102">地圖經線屬性對話方塊、標籤</span><span class="sxs-lookup"><span data-stu-id="0b228-102">Map Meridian Properties Dialog Box, Labels</span></span>
  <span data-ttu-id="0b228-103">使用 [ **MapMeridian 屬性**] 對話方塊，即可變更地圖區中垂直方格的標籤選項。</span><span class="sxs-lookup"><span data-stu-id="0b228-103">Use the **MapMeridian Properties** dialog box to change label options for the vertical grid in the map viewport.</span></span> <span data-ttu-id="0b228-104">根據指定之檢視區的座標系統，經線表示下列值：</span><span class="sxs-lookup"><span data-stu-id="0b228-104">A meridian represents the following value depending on the specified coordinate system for the viewport:</span></span>  
  
-   <span data-ttu-id="0b228-105">**平面**：</span><span class="sxs-lookup"><span data-stu-id="0b228-105">**Planar**.</span></span> <span data-ttu-id="0b228-106">Y 座標。</span><span class="sxs-lookup"><span data-stu-id="0b228-106">The Y coordinate.</span></span>  
  
-   <span data-ttu-id="0b228-107">**地理**。</span><span class="sxs-lookup"><span data-stu-id="0b228-107">**Geographic**.</span></span> <span data-ttu-id="0b228-108">目前投射的經度。</span><span class="sxs-lookup"><span data-stu-id="0b228-108">The longitude for the current projection.</span></span>  
  
 <span data-ttu-id="0b228-109">按一下 **[運算式]** (*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="0b228-109">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0b228-110">選項</span><span class="sxs-lookup"><span data-stu-id="0b228-110">Options</span></span>  
 <span data-ttu-id="0b228-111">**間隔**</span><span class="sxs-lookup"><span data-stu-id="0b228-111">**Interval**</span></span>  
 <span data-ttu-id="0b228-112">輸入指定經線之間間隔的整數值 (以度數為單位)。</span><span class="sxs-lookup"><span data-stu-id="0b228-112">Type an integer value in degrees that specifies the interval between meridians.</span></span> <span data-ttu-id="0b228-113">根據預設，會選取 **[自動]** 。</span><span class="sxs-lookup"><span data-stu-id="0b228-113">By default, **Auto** is selected.</span></span> <span data-ttu-id="0b228-114">**[自動]** 表示此值由空間資料自動決定。</span><span class="sxs-lookup"><span data-stu-id="0b228-114">**Auto** indicates that value is automatically determined by spatial data.</span></span>  
  
 <span data-ttu-id="0b228-115">**顯示標籤**</span><span class="sxs-lookup"><span data-stu-id="0b228-115">**Show labels**</span></span>  
 <span data-ttu-id="0b228-116">選取此選項即可顯示經線的標籤。</span><span class="sxs-lookup"><span data-stu-id="0b228-116">Select this option to display labels for the meridians.</span></span>  
  
 <span data-ttu-id="0b228-117">**放置**</span><span class="sxs-lookup"><span data-stu-id="0b228-117">**Placement**</span></span>  
 <span data-ttu-id="0b228-118">選取要顯示相對於檢視區上方、中間與下方之標籤的位置。</span><span class="sxs-lookup"><span data-stu-id="0b228-118">Select a location to display the labels relative to the top, center, and bottom of the viewport.</span></span> <span data-ttu-id="0b228-119">預設位置為 **[靠近]**。</span><span class="sxs-lookup"><span data-stu-id="0b228-119">The default placement is **Near**.</span></span>  
  
-   <span data-ttu-id="0b228-120">**靠近** ：在左邊緣顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="0b228-120">**Near** Display labels at the left edge.</span></span>  
  
-   <span data-ttu-id="0b228-121">**四分之一** ：在左邊緣和中間之間的一半位置顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="0b228-121">**One Quarter** Display labels half way between the left edge and the center.</span></span>  
  
-   <span data-ttu-id="0b228-122">**中間** ：在中間顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="0b228-122">**Center** Display labels at the center.</span></span>  
  
-   <span data-ttu-id="0b228-123">**四分之三** ：在中間和右邊緣之間的一半位置顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="0b228-123">**Three Quarters** Display labels half way between the center and the right edge.</span></span>  
  
-   <span data-ttu-id="0b228-124">**遠方** ：在右邊緣顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="0b228-124">**Far** Display labels at the right edge.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b228-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b228-125">See Also</span></span>  
 [<span data-ttu-id="0b228-126">地圖 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0b228-126">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
