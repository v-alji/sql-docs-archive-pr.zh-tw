---
title: 將自訂位置新增至地圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 167558534280f08d576205b5ff1b94d0588fcb78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706245"
---
# <a name="add-custom-locations-to-a-map-report-builder-and-ssrs"></a><span data-ttu-id="e22c6-102">將自訂位置加入至地圖 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e22c6-102">Add Custom Locations to a Map (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e22c6-103">將地圖加入至報表後，您可以加入自己的點位置。</span><span class="sxs-lookup"><span data-stu-id="e22c6-103">After you add a map to a report, you can add your own point locations.</span></span>  
  
 <span data-ttu-id="e22c6-104">圖層上所有點的顯示屬性都可以透過設定圖層之點屬性的選項來控制。</span><span class="sxs-lookup"><span data-stu-id="e22c6-104">Display properties for all points on a layer are controlled by setting options for the point properties for the layer.</span></span> <span data-ttu-id="e22c6-105">若是選取的內嵌點，您可以覆寫顯示屬性。</span><span class="sxs-lookup"><span data-stu-id="e22c6-105">For a selected embedded point, you can override the display properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e22c6-106">當您覆寫內嵌點的圖層顯示屬性時，無法回復您所做的變更。</span><span class="sxs-lookup"><span data-stu-id="e22c6-106">When you override the layer display properties for the embedded point, the changes that you make are not reversible.</span></span>  
  
 <span data-ttu-id="e22c6-107">如需詳細資訊，請參閱 [使用規則與分析資料更改多邊形、線條與點顯示 &#40;報表產生器及 SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e22c6-107">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-point-layer"></a><span data-ttu-id="e22c6-108">加入點圖層</span><span class="sxs-lookup"><span data-stu-id="e22c6-108">To add a point layer</span></span>  
  
1.  <span data-ttu-id="e22c6-109">在報表設計介面上，按一下地圖來選取它，然後顯示 [地圖] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e22c6-109">On the report design surface, click the map to select it and display the Map pane.</span></span>  
  
2.  <span data-ttu-id="e22c6-110">在工具列上，按一下 [新增圖層]  。</span><span class="sxs-lookup"><span data-stu-id="e22c6-110">On the toolbar, click **Add Layer**.</span></span>  
  
3.  <span data-ttu-id="e22c6-111">從下拉式清單中，按一下 [新增點圖層]  。</span><span class="sxs-lookup"><span data-stu-id="e22c6-111">From the drop-down list, click **Add Point Layer**.</span></span> <span data-ttu-id="e22c6-112">不含點的點圖層便會加入至地圖中。</span><span class="sxs-lookup"><span data-stu-id="e22c6-112">A point layer with no points is added to the map.</span></span> <span data-ttu-id="e22c6-113">根據預設，內嵌點的點圖層已經準備就緒。</span><span class="sxs-lookup"><span data-stu-id="e22c6-113">By default, the point layer is ready for embedded points.</span></span>  
  
### <a name="to-add-a-custom-point"></a><span data-ttu-id="e22c6-114">加入自訂點</span><span class="sxs-lookup"><span data-stu-id="e22c6-114">To add a custom point</span></span>  
  
1.  <span data-ttu-id="e22c6-115">在報表設計介面上，按一下地圖來選取它，然後顯示 [地圖] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e22c6-115">On the report design surface, click the map to select it and display the Map pane.</span></span>  
  
2.  <span data-ttu-id="e22c6-116">在 [地圖] 窗格中，以滑鼠右鍵按一下 [內嵌]  類型的點圖層，然後按一下 [新增點]  。</span><span class="sxs-lookup"><span data-stu-id="e22c6-116">In the Map pane, right-click a point layer that has type **Embedded**, and then click **Add Point**.</span></span> <span data-ttu-id="e22c6-117">游標會變更為十字形狀。</span><span class="sxs-lookup"><span data-stu-id="e22c6-117">The cursor changes to crosshairs.</span></span>  
  
3.  <span data-ttu-id="e22c6-118">若要加入點，按一下地圖上的某個位置。</span><span class="sxs-lookup"><span data-stu-id="e22c6-118">To add a point, click a location on the map.</span></span> <span data-ttu-id="e22c6-119">內嵌點就會加入至您所按之位置的選定圖層。</span><span class="sxs-lookup"><span data-stu-id="e22c6-119">An embedded point is added to the selected layer at the location where you click.</span></span>  
  
### <a name="to-customize-the-display-for-an-embedded-point"></a><span data-ttu-id="e22c6-120">若要自訂內嵌點的顯示</span><span class="sxs-lookup"><span data-stu-id="e22c6-120">To customize the display for an embedded point</span></span>  
  
1.  <span data-ttu-id="e22c6-121">以滑鼠右鍵按一下點，然後按一下 [點屬性]  。</span><span class="sxs-lookup"><span data-stu-id="e22c6-121">Right-click the point, and then click **Point Properties**.</span></span> <span data-ttu-id="e22c6-122">[地圖內嵌點屬性]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e22c6-122">The **Map Embedded Point Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="e22c6-123">按一下 [覆寫此圖層的點選項]  。</span><span class="sxs-lookup"><span data-stu-id="e22c6-123">Click **Override point options for this layer**.</span></span> <span data-ttu-id="e22c6-124">多個屬性頁面隨即出現在左窗格。</span><span class="sxs-lookup"><span data-stu-id="e22c6-124">Multiple property pages appear in the left pane.</span></span>  
  
3.  <span data-ttu-id="e22c6-125">按一下這些頁面，然後設定您要套用到這個點的顯示屬性。</span><span class="sxs-lookup"><span data-stu-id="e22c6-125">Click the pages and set the display properties that you want to apply to this point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22c6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e22c6-126">See Also</span></span>  
 <span data-ttu-id="e22c6-127">[地圖 &#40;報表產生器及 SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e22c6-127">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e22c6-128">使用規則與分析資料更改多邊形、線條與點顯示 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e22c6-128">Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;</span></span>](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
