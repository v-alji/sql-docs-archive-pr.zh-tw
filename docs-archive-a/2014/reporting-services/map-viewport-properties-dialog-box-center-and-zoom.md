---
title: 地圖區屬性對話方塊、置中和縮放 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.centerandzoom.f1
- "10506"
ms.assetid: 642a06f5-293f-48e0-97a6-1489dbefa719
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 913c00773abf71ca627b8cc2a94a873484e8ab30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593856"
---
# <a name="map-viewport-properties-dialog-box-center-and-zoom"></a><span data-ttu-id="d549c-102">地圖檢視區屬性對話方塊、置中與縮放</span><span class="sxs-lookup"><span data-stu-id="d549c-102">Map Viewport Properties Dialog Box, Center and Zoom</span></span>
  <span data-ttu-id="d549c-103">選取 **[地圖檢視區屬性]** 對話方塊的 **[置中與縮放]** 來設定地圖的置中檢視與縮放因數。</span><span class="sxs-lookup"><span data-stu-id="d549c-103">Select **Center and Zoom** for the **Map Viewport Properties** dialog box to set the center view and zoom factor for a map.</span></span> <span data-ttu-id="d549c-104">指定地圖資料來源與您要包含在報表中之報表的界限之後，您可以指定檢視置中與縮放因數來進一步控制地圖顯示。</span><span class="sxs-lookup"><span data-stu-id="d549c-104">After you specify a map data source and the boundaries of the map that you want to include in your report, you can specify the view center and the zoom factor to further control the map display.</span></span> <span data-ttu-id="d549c-105">根據您用來指定置中與縮放值的方法，選項可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="d549c-105">Options change depending on which method you use to specify the center and zoom values.</span></span> <span data-ttu-id="d549c-106">按一下 **[運算式]** (*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="d549c-106">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d549c-107">選項</span><span class="sxs-lookup"><span data-stu-id="d549c-107">Options</span></span>  
 <span data-ttu-id="d549c-108">**設定檢視置中與縮放層級**</span><span class="sxs-lookup"><span data-stu-id="d549c-108">**Set a view center and zoom level**</span></span>  
 <span data-ttu-id="d549c-109">選擇此選項來指定檢視置中與縮放層級的自訂值。</span><span class="sxs-lookup"><span data-stu-id="d549c-109">Choose this option to specify custom values for the view center and the zoom level.</span></span>  
  
 <span data-ttu-id="d549c-110">**地圖置中以顯示地圖圖層**</span><span class="sxs-lookup"><span data-stu-id="d549c-110">**Center map to show a map layer**</span></span>  
 <span data-ttu-id="d549c-111">選擇此選項來指定圖層，並自動將檢視在其地圖資料上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-111">Choose this option to specify a layer and automatically center the view on its map data.</span></span> <span data-ttu-id="d549c-112">例如，將檢視在 LineLayer1 上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-112">For example, center the view on LineLayer1.</span></span>  
  
 <span data-ttu-id="d549c-113">**地圖置中以顯示內嵌地圖元素**</span><span class="sxs-lookup"><span data-stu-id="d549c-113">**Center map to show an embedded map element**</span></span>  
 <span data-ttu-id="d549c-114">選擇此選項，將檢視在特定的資料繫結地圖元素上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-114">Choose this option to center the view on a specific data-bound map element.</span></span> <span data-ttu-id="d549c-115">空間資料與分析資料必須擁有關聯性，才能指定此選項。</span><span class="sxs-lookup"><span data-stu-id="d549c-115">The spatial data must have a relationship with analytical data to specify this option.</span></span>  
  
 <span data-ttu-id="d549c-116">例如，將檢視在符合欄位名稱為 [City] 而符合值為 "Seattle" 的地圖元素上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-116">For example, center the view on the map element where the name of the match field is [City] and the match value is "Seattle".</span></span>  
  
 <span data-ttu-id="d549c-117">**地圖置中以顯示所有資料繫結地圖元素**</span><span class="sxs-lookup"><span data-stu-id="d549c-117">**Center map to show all data-bound map elements**</span></span>  
 <span data-ttu-id="d549c-118">選擇此選項，將檢視在圖層中的所有地圖元素上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-118">Choose this option to center the view on all map elements in the layer.</span></span> <span data-ttu-id="d549c-119">空間資料與分析資料必須擁有關聯性，才能指定此選項。</span><span class="sxs-lookup"><span data-stu-id="d549c-119">The spatial data must have a relationship with analytical data to specify this option.</span></span>  
  
 <span data-ttu-id="d549c-120">例如，將檢視在顯示城市和泡泡大小與人口有關的多邊形泡泡圖層上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-120">For example, center the view on the polygon bubble layer that shows cities and the bubble size is related to population.</span></span> <span data-ttu-id="d549c-121">計算檢視區的中心時，只會包含人口值相符的城市。</span><span class="sxs-lookup"><span data-stu-id="d549c-121">Only those cities with a matching population value are included when calculating the center for the viewport.</span></span>  
  
 <span data-ttu-id="d549c-122">**置中與縮放選項**</span><span class="sxs-lookup"><span data-stu-id="d549c-122">**Center and zoom options**</span></span>  
 <span data-ttu-id="d549c-123">選取一個選項來指定檢視置中與縮放層級。</span><span class="sxs-lookup"><span data-stu-id="d549c-123">Select an option to specify the view center and zoom level.</span></span>  
  
 <span data-ttu-id="d549c-124">**檢視置中 (X) %**</span><span class="sxs-lookup"><span data-stu-id="d549c-124">**View center (X) %**</span></span>  
 <span data-ttu-id="d549c-125">水平座標。</span><span class="sxs-lookup"><span data-stu-id="d549c-125">The horizontal coordinate.</span></span> <span data-ttu-id="d549c-126">預設值 50%。</span><span class="sxs-lookup"><span data-stu-id="d549c-126">The default value, 50%.</span></span> <span data-ttu-id="d549c-127">表示將檢視在最小與最大水平值之間的中點上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-127">centers the view at the midpoint between the minimum and maximum horizontal values.</span></span>  
  
 <span data-ttu-id="d549c-128">**檢視置中 (Y) %**</span><span class="sxs-lookup"><span data-stu-id="d549c-128">**View center (Y) %**</span></span>  
 <span data-ttu-id="d549c-129">垂直座標。</span><span class="sxs-lookup"><span data-stu-id="d549c-129">The vertical coordinate.</span></span> <span data-ttu-id="d549c-130">預設值 50% 表示將檢視在最小與最大垂直值之間的中點上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-130">The default value, 50%, centers the view at the midpoint between the minimum and maximum vertical values.</span></span>  
  
 <span data-ttu-id="d549c-131">**縮放層級 (%)**</span><span class="sxs-lookup"><span data-stu-id="d549c-131">**Zoom level (%)**</span></span>  
 <span data-ttu-id="d549c-132">縮放因數。</span><span class="sxs-lookup"><span data-stu-id="d549c-132">The zoom factor.</span></span> <span data-ttu-id="d549c-133">預設值 100% 表示無縮放比例。</span><span class="sxs-lookup"><span data-stu-id="d549c-133">The default value, 100%, indicates no magnification.</span></span>  
  
 <span data-ttu-id="d549c-134">**在此圖層上置中檢視**</span><span class="sxs-lookup"><span data-stu-id="d549c-134">**Center view on this layer**</span></span>  
 <span data-ttu-id="d549c-135">指定圖層的名稱。</span><span class="sxs-lookup"><span data-stu-id="d549c-135">Specify the name of the layer.</span></span>  
  
 <span data-ttu-id="d549c-136">**在符合此條件的地圖元素上置中檢視**</span><span class="sxs-lookup"><span data-stu-id="d549c-136">**Center view on the map element that matches this condition**</span></span>  
 <span data-ttu-id="d549c-137">顯示的唯讀欄位用於比對地圖資料和分析資料。</span><span class="sxs-lookup"><span data-stu-id="d549c-137">The read-only field that is displayed is used to match map data and analytical data.</span></span> <span data-ttu-id="d549c-138">指定您要比對時所依據的值。</span><span class="sxs-lookup"><span data-stu-id="d549c-138">Specify the value that you want to match on.</span></span> <span data-ttu-id="d549c-139">檢視會自動在此地圖元素上置中。</span><span class="sxs-lookup"><span data-stu-id="d549c-139">The view automatically centers on this map element.</span></span> <span data-ttu-id="d549c-140">例如，NAME = TEXAS。</span><span class="sxs-lookup"><span data-stu-id="d549c-140">For example, NAME = TEXAS.</span></span> <span data-ttu-id="d549c-141">根據預設，條件的資料類型為字串，而且比對時會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d549c-141">By default, the data type for the condition is String and the match is case-sensitive.</span></span>  
  
 <span data-ttu-id="d549c-142">若要針對包含不同資料類型的欄位進行比對，您必須撰寫評估為該資料類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="d549c-142">To match on a field that has a different data type, you must write an expression that evaluates to that data type.</span></span> <span data-ttu-id="d549c-143">例如，如果符合欄位為儲存為整數的 5 位數郵遞區號，則您必須使用運算式 =98053 來指定郵遞區號 98053。</span><span class="sxs-lookup"><span data-stu-id="d549c-143">For example, if the match field is a 5 digit postal code that is stored as an integer, then to specify the postal code 98053, you must use the expression =98053.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d549c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d549c-144">See Also</span></span>  
 [<span data-ttu-id="d549c-145">地圖 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d549c-145">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
