---
title: 地圖色彩規則對話方塊、一般 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10541"
- sql12.rtp.rptdesigner.shared.mapcolorrulesgeneral.f1
ms.assetid: 14ff5fc1-4cf8-4a45-9d98-47a1bf1c52c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0dffc6c0b31400cb4eb9cecbbada1a52f8f41443
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606070"
---
# <a name="map-color-rules-dialog-box-general"></a><span data-ttu-id="ebb94-102">地圖色彩規則對話方塊、一般</span><span class="sxs-lookup"><span data-stu-id="ebb94-102">Map Color Rules Dialog Box, General</span></span>
  <span data-ttu-id="ebb94-103">選取 **[色彩規則屬性]** 對話方塊上的 **[一般]** ，定義此圖層上地圖元素的色彩選項。</span><span class="sxs-lookup"><span data-stu-id="ebb94-103">Select **General** on the **Color Rules Properties** dialog box to define color options for map elements on this layer.</span></span> <span data-ttu-id="ebb94-104">地圖元素包括多邊形、線條與點。</span><span class="sxs-lookup"><span data-stu-id="ebb94-104">Map elements include polygons, lines, and points.</span></span> <span data-ttu-id="ebb94-105">當您已經根據資料集欄位或空間資料來源欄位中的空間資料與分析資料建立地圖元素之間的關聯性時，可以套用色彩規則。</span><span class="sxs-lookup"><span data-stu-id="ebb94-105">Color rules can be applied when you have created a relationship between map elements based on spatial data and analytical data from a dataset field or from a spatial data source field.</span></span>  
  
 <span data-ttu-id="ebb94-106">若要在圖層上指定包含不同主要色彩與次要色彩的裝飾漸層來顯示所有地圖元素，請使用 [地圖多邊形屬性] 對話方塊的 **[填滿]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="ebb94-106">To display all map elements on a layer by specifying a decorative gradient with different primary and secondary colors, use the **Fill** page of the Map Polygon Properties Dialog Box.</span></span> <span data-ttu-id="ebb94-107">色彩規則優先於圖層的顯示屬性。</span><span class="sxs-lookup"><span data-stu-id="ebb94-107">Color rules take precedence over display properties for a layer.</span></span> <span data-ttu-id="ebb94-108">如需詳細資訊，請參閱[自訂地圖或地圖圖層的資料和顯示 &#40;報表產生器及 SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ebb94-108">For more information, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ebb94-109">選項</span><span class="sxs-lookup"><span data-stu-id="ebb94-109">Options</span></span>  
 <span data-ttu-id="ebb94-110">**套用範本樣式**</span><span class="sxs-lookup"><span data-stu-id="ebb94-110">**Apply template style**</span></span>  
 <span data-ttu-id="ebb94-111">選取此選項可以根據您在精靈中選擇的主題，或在多邊形、線條或點圖層屬性中設定的主題，使用色彩。</span><span class="sxs-lookup"><span data-stu-id="ebb94-111">Select this option to use color based on the theme that was chosen in the wizard or set in the Polygon, Line, or Point layer properties.</span></span> <span data-ttu-id="ebb94-112">主題會為地圖設定色彩、字型與框線的預設選項。</span><span class="sxs-lookup"><span data-stu-id="ebb94-112">A theme sets default options for color, font, and borders for the map.</span></span> <span data-ttu-id="ebb94-113">若是此選項，不會套用任何規則來指派色彩給每個地圖元素。</span><span class="sxs-lookup"><span data-stu-id="ebb94-113">For this option, no rule is applied to assign colors to each map element.</span></span>  
  
 <span data-ttu-id="ebb94-114">**使用調色盤將資料視覺化**</span><span class="sxs-lookup"><span data-stu-id="ebb94-114">**Visualize data by using color palette**</span></span>  
 <span data-ttu-id="ebb94-115">選取此選項可以透過使用特定色彩調色盤中的色彩來視覺化分析資料。</span><span class="sxs-lookup"><span data-stu-id="ebb94-115">Select this option to visualize analytical data by using colors from a specific color palette.</span></span>  
  
 <span data-ttu-id="ebb94-116">**使用色彩範圍將資料視覺化**</span><span class="sxs-lookup"><span data-stu-id="ebb94-116">**Visualize data by using color ranges**</span></span>  
 <span data-ttu-id="ebb94-117">選取此選項可以透過每個地圖元素使用一個範圍的色彩來視覺化分析資料。</span><span class="sxs-lookup"><span data-stu-id="ebb94-117">Select this option to visualize analytical data by using a range of colors for each map element.</span></span> <span data-ttu-id="ebb94-118">例如，當您指定 [紅色] 做為開始色彩、[黃色] 做為中間色彩，而 [綠色] 做為結束色彩時，下限範圍中的值為 [紅色]、中間範圍中的值為 [黃色]，而上限範圍中的值為 [綠色]。</span><span class="sxs-lookup"><span data-stu-id="ebb94-118">For example, when you specify Red as a start color, Yellow as a middle color, and Green as an end color, values in the low range are Red, values in the middle range are Yellow, and values in the top range are Green.</span></span>  
  
 <span data-ttu-id="ebb94-119">**使用自訂色彩將資料視覺化**</span><span class="sxs-lookup"><span data-stu-id="ebb94-119">**Visualize data by using custom colors**</span></span>  
 <span data-ttu-id="ebb94-120">選取此選項可以透過指定您自己的色彩清單來視覺化分析資料。</span><span class="sxs-lookup"><span data-stu-id="ebb94-120">Select this option to visualize analytical data by specifying your own list of colors.</span></span>  
  
 <span data-ttu-id="ebb94-121">**資料欄位**</span><span class="sxs-lookup"><span data-stu-id="ebb94-121">**Data field**</span></span>  
 <span data-ttu-id="ebb94-122">當您選取其中一個 **[將資料視覺化]** 選項時，會出現此選項。</span><span class="sxs-lookup"><span data-stu-id="ebb94-122">This option appears when you select one of the **Visualize data** options.</span></span>  
  
 <span data-ttu-id="ebb94-123">從下拉式清單中選取要使用的分析資料欄位。</span><span class="sxs-lookup"><span data-stu-id="ebb94-123">Select the analytical data field to use from the drop-down list.</span></span> <span data-ttu-id="ebb94-124">根據空間資料的來源，此清單會顯示空間資料來源與報表資料集 (擁有空間資料與分析資料之間的關聯性) 中的欄位。</span><span class="sxs-lookup"><span data-stu-id="ebb94-124">Depending on the source of spatial data, the list displays fields from the spatial data source and from a report dataset that has a relationship between the spatial data and analytical data.</span></span> <span data-ttu-id="ebb94-125">若要建立此種關聯性，請針對選取的地圖圖層，在 [分析資料] 頁面上設定資料選項。</span><span class="sxs-lookup"><span data-stu-id="ebb94-125">To create such a relationship, set the data options on the Analytical Data page for the selected map layer.</span></span>  
  
 <span data-ttu-id="ebb94-126">**調色**</span><span class="sxs-lookup"><span data-stu-id="ebb94-126">**Palette**</span></span>  
 <span data-ttu-id="ebb94-127">輸入或選取色彩調色盤的名稱。</span><span class="sxs-lookup"><span data-stu-id="ebb94-127">Type or select the name of the color palette.</span></span>  
  
 <span data-ttu-id="ebb94-128">**開始色彩**</span><span class="sxs-lookup"><span data-stu-id="ebb94-128">**Start color**</span></span>  
 <span data-ttu-id="ebb94-129">指定用於資料範圍下限之資料的色彩。</span><span class="sxs-lookup"><span data-stu-id="ebb94-129">Specify the color to use for data at the low end of the data range.</span></span>  
  
 <span data-ttu-id="ebb94-130">**中間色彩**</span><span class="sxs-lookup"><span data-stu-id="ebb94-130">**Middle color**</span></span>  
 <span data-ttu-id="ebb94-131">指定用於資料範圍中間之資料的色彩。</span><span class="sxs-lookup"><span data-stu-id="ebb94-131">Specify the color to use for data in the middle of the data range.</span></span> <span data-ttu-id="ebb94-132">選取 **[無色彩]** 即可移除此範圍。</span><span class="sxs-lookup"><span data-stu-id="ebb94-132">Select **No Color** to remove this range.</span></span>  
  
 <span data-ttu-id="ebb94-133">**結束色彩**</span><span class="sxs-lookup"><span data-stu-id="ebb94-133">**End color**</span></span>  
 <span data-ttu-id="ebb94-134">指定用於資料範圍上限之資料的色彩。</span><span class="sxs-lookup"><span data-stu-id="ebb94-134">Specify the color to use for data at the high end of the data range.</span></span>  
  
 <span data-ttu-id="ebb94-135">**加入**</span><span class="sxs-lookup"><span data-stu-id="ebb94-135">**Add**</span></span>  
 <span data-ttu-id="ebb94-136">按一下 **[加入]** ，針對色彩規則指定您自己的色彩。</span><span class="sxs-lookup"><span data-stu-id="ebb94-136">Click **Add** to specify your own colors for the color rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb94-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebb94-137">See Also</span></span>  
 <span data-ttu-id="ebb94-138">[地圖 &#40;報表產生器及 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ebb94-138">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ebb94-139">變更地圖圖例、色階與相關的規則 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ebb94-139">Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;</span></span>](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
