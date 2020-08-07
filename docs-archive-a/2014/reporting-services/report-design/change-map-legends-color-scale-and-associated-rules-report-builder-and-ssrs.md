---
title: 變更地圖圖例、色階和相關聯的規則 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.maprulesdistribution.f1
- "10512"
- "10539"
- "10533"
- sql12.rtp.rptdesigner.mappointlayerproperties.typerules.f1
- "10534"
- sql12.rtp.rptdesigner.maplegendproperties.general.f1
- sql12.rtp.rptdesigner.mapdistancescaleproperties.general.f1
- "10516"
- sql12.rtp.rptdesigner.mapcolorscaleproperties.labels.f1
- sql12.rtp.rptdesigner.maplegendtitleproperties.general.f1
- "10514"
- sql12.rtp.rptdesigner.shared.mapruleslegend.f1
- sql12.rtp.rptdesigner.mapcolorscaleproperties.general.f1
- sql12.rtp.rptdesigner.shared.embeddedlabels.f1
- "10513"
- sql12.rtp.rptdesigner.mappointlayerproperties.sizerules.f1
- sql12.rtp.rptdesigner.mapcolorscaletitleproperties.general.f1
- "10510"
- "10509"
- "10540"
- "10517"
ms.assetid: a1d691b2-c5ae-420f-af60-b7c54a7385a4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 17220c12e672ce49d3c5b1023f2a00db04e7613e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593805"
---
# <a name="change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs"></a><span data-ttu-id="ca984-102">變更地圖圖例、色階與相關的規則 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ca984-102">Change Map Legends, Color Scale, and Associated Rules (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ca984-103">地圖可包含地圖圖例、色階和距離標尺。</span><span class="sxs-lookup"><span data-stu-id="ca984-103">A map can contain map legends, a color scale, and a distance scale.</span></span> <span data-ttu-id="ca984-104">這些地圖組件可協助使用者解譯地圖上的資料視覺化。</span><span class="sxs-lookup"><span data-stu-id="ca984-104">These parts of a map help users interpret the data visualization on the map.</span></span>  
  
 <span data-ttu-id="ca984-105">圖例包括下列地圖組件：</span><span class="sxs-lookup"><span data-stu-id="ca984-105">Legends include the following parts of a map:</span></span>  
  
-   <span data-ttu-id="ca984-106">**地圖圖例** ：顯示指引，協助解譯改變地圖圖層上地圖元素之顯示的分析資料。</span><span class="sxs-lookup"><span data-stu-id="ca984-106">**Map legend** Displays a guide to help interpret the analytical data that varies the display of a map elements on a map layer.</span></span> <span data-ttu-id="ca984-107">地圖可以擁有多個圖例。</span><span class="sxs-lookup"><span data-stu-id="ca984-107">A map can have multiple legends.</span></span> <span data-ttu-id="ca984-108">您可以指定每一個地圖圖層要使用的圖例。</span><span class="sxs-lookup"><span data-stu-id="ca984-108">For each map layer, you A specify which legend to use.</span></span> <span data-ttu-id="ca984-109">圖例可提供多個地圖圖層的指引。</span><span class="sxs-lookup"><span data-stu-id="ca984-109">A legend can provide a guide to more than one map layer.</span></span>  
  
-   <span data-ttu-id="ca984-110">**色階** ：顯示指引，協助解譯地圖上的色彩。</span><span class="sxs-lookup"><span data-stu-id="ca984-110">**Color scale** Displays a guide to help interpret colors on the map.</span></span> <span data-ttu-id="ca984-111">地圖可以擁有一個色階。</span><span class="sxs-lookup"><span data-stu-id="ca984-111">A map has one color scale.</span></span> <span data-ttu-id="ca984-112">色階的資料可由多個圖層提供。</span><span class="sxs-lookup"><span data-stu-id="ca984-112">Multiple layers can provide the data for the color scale.</span></span>  
  
-   <span data-ttu-id="ca984-113">**距離標尺** ：顯示指引，協助解譯地圖的標尺。</span><span class="sxs-lookup"><span data-stu-id="ca984-113">**Distance scale** Displays a guide to help interpret the scale of the map.</span></span> <span data-ttu-id="ca984-114">地圖可以擁有一個距離標尺。</span><span class="sxs-lookup"><span data-stu-id="ca984-114">A map has one distance scale.</span></span> <span data-ttu-id="ca984-115">目前的地圖檢視區縮放值會決定距離標尺。</span><span class="sxs-lookup"><span data-stu-id="ca984-115">The current map viewport zoom value determines the distance scale.</span></span>  
  
 <span data-ttu-id="ca984-116">![rs_MapElements](../media/rs-mapelements.gif "rs_MapElements")</span><span class="sxs-lookup"><span data-stu-id="ca984-116">![rs_MapElements](../media/rs-mapelements.gif "rs_MapElements")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a><a name="Viewport"></a> <span data-ttu-id="ca984-117">變更圖例相對於檢視區的位置</span><span class="sxs-lookup"><span data-stu-id="ca984-117">To change the position of a legend relative to the viewport</span></span>  
  
#### <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a><span data-ttu-id="ca984-118">變更圖例相對於檢視區的位置</span><span class="sxs-lookup"><span data-stu-id="ca984-118">To change the position of a legend relative to the viewport</span></span>  
  
1.  <span data-ttu-id="ca984-119">在設計檢視中，以滑鼠右鍵按一下圖例，然後開啟 [ _\<report item->_ **屬性**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ca984-119">In Design view, right-click the legend and open the _\<report item->_**Properties** page.</span></span>  
  
2.  <span data-ttu-id="ca984-120">在 [位置]  中，按一下指定讓圖例顯示在相對於檢視區的位置。</span><span class="sxs-lookup"><span data-stu-id="ca984-120">In **Position**, click the location that specifies where to display the legend relative to the viewport.</span></span>  
  
3.  <span data-ttu-id="ca984-121">若要在視口外部顯示圖例，請選取 [**顯示在 \<report item> 區外**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-121">To display the legend outside the viewport, select **Show \<report item> outside viewport**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="ca984-122">在預覽中，只有在與該圖例相關的規則有結果時，才會顯示地圖圖例和色階。</span><span class="sxs-lookup"><span data-stu-id="ca984-122">In preview, map legends and the color scale appear only when there are results from the rules related to that legend.</span></span> <span data-ttu-id="ca984-123">如果沒有要顯示的項目，則圖例不會出現在轉譯的報表中。</span><span class="sxs-lookup"><span data-stu-id="ca984-123">If there are no items to display, the legend does not appear in the rendered report.</span></span>  
  
  
  
##  <a name="to-change-the-layout-of-a-map-legend"></a><a name="MapLegend"></a> <span data-ttu-id="ca984-124">變更地圖圖例的配置</span><span class="sxs-lookup"><span data-stu-id="ca984-124">To change the layout of a map legend</span></span>  
  
#### <a name="to-change-the-layout-of-a-map-legend"></a><span data-ttu-id="ca984-125">變更地圖圖例的配置</span><span class="sxs-lookup"><span data-stu-id="ca984-125">To change the layout of a map legend</span></span>  
  
1.  <span data-ttu-id="ca984-126">在 [設計] 檢視中，以滑鼠右鍵按一下圖例，然後開啟 [圖例屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ca984-126">In Design view, right-click the legend and open the **Legend Properties** page.</span></span>  
  
2.  <span data-ttu-id="ca984-127">在 [圖例配置]  中，按一下您要用於圖例的表格版面配置。</span><span class="sxs-lookup"><span data-stu-id="ca984-127">In **Legend layout**, click the table layout that you want to use for the legend.</span></span> <span data-ttu-id="ca984-128">當您按一下不同的選項時，設計介面上的配置就會變更。</span><span class="sxs-lookup"><span data-stu-id="ca984-128">As you click different options, the layout on the design surface changes.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-show-or-hide-a-map-legend-title"></a><a name="MapLegendTitle"></a> <span data-ttu-id="ca984-129">顯示或隱藏地圖圖例標題</span><span class="sxs-lookup"><span data-stu-id="ca984-129">To show or hide a map legend title</span></span>  
  
#### <a name="to-show-or-hide-a-map-legend-title"></a><span data-ttu-id="ca984-130">顯示或隱藏地圖圖例標題</span><span class="sxs-lookup"><span data-stu-id="ca984-130">To show or hide a map legend title</span></span>  
  
-   <span data-ttu-id="ca984-131">在設計介面上以滑鼠右鍵按一下地圖圖例，然後按一下 [顯示圖例標題]  。</span><span class="sxs-lookup"><span data-stu-id="ca984-131">Right-click the map legend on the design surface, and then click **Show Legend Title**.</span></span>  
  
  
  
##  <a name="to-show-or-hide-a-color-scale-title"></a><a name="ColorScaleTitle"></a> <span data-ttu-id="ca984-132">顯示或隱藏色階標題</span><span class="sxs-lookup"><span data-stu-id="ca984-132">To show or hide a color scale title</span></span>  
  
#### <a name="to-show-or-hide-a-color-scale-title"></a><span data-ttu-id="ca984-133">顯示或隱藏色階標題</span><span class="sxs-lookup"><span data-stu-id="ca984-133">To show or hide a color scale title</span></span>  
  
-   <span data-ttu-id="ca984-134">在設計介面上以滑鼠右鍵按一下色階，然後按一下 [顯示色階標題]  。</span><span class="sxs-lookup"><span data-stu-id="ca984-134">Right-click the color scale on the design surface, and then click **Show Color Scale Title**.</span></span>  
  
  
  
##  <a name="to-move-items-out-of-the-first-legend"></a><a name="MoveItems"></a> <span data-ttu-id="ca984-135">從第一個圖例中移出項目</span><span class="sxs-lookup"><span data-stu-id="ca984-135">To move items out of the first legend</span></span>  
 <span data-ttu-id="ca984-136">依您需要建立多個額外的圖例，然後更新每個地圖圖層的規則，指定要在哪一個圖例中顯示規則結果。</span><span class="sxs-lookup"><span data-stu-id="ca984-136">Create as many additional legends as you need and then update the rules for each map layer specify which legend to display the rule results in.</span></span>  
  
#### <a name="to-create-a-new-legend"></a><span data-ttu-id="ca984-137">建立新的圖例</span><span class="sxs-lookup"><span data-stu-id="ca984-137">To create a new legend</span></span>  
  
-   <span data-ttu-id="ca984-138">在 [設計] 檢視中，以滑鼠右鍵按一下地圖檢視區外的地圖，然後按一下 [新增圖例]  。</span><span class="sxs-lookup"><span data-stu-id="ca984-138">In Design view, right-click the map outside the map viewport, and then click **Add Legend**.</span></span>  
  
     <span data-ttu-id="ca984-139">新的圖例會出現在地圖上。</span><span class="sxs-lookup"><span data-stu-id="ca984-139">A new legend appears on the map.</span></span>  
  
#### <a name="to-display-rule-results-in-a-legend"></a><span data-ttu-id="ca984-140">在圖例中顯示規則結果</span><span class="sxs-lookup"><span data-stu-id="ca984-140">To display rule results in a legend</span></span>  
  
1.  <span data-ttu-id="ca984-141">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-141">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-142">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **色彩規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-142">Right-click the layer that has the data that you want and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-143">按一下 **[圖例]** 。</span><span class="sxs-lookup"><span data-stu-id="ca984-143">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="ca984-144">在 [在此圖例中顯示]  下拉式清單中，按一下要在其中顯示規則結果的圖例名稱。</span><span class="sxs-lookup"><span data-stu-id="ca984-144">In the **Show in this legend** drop-down list, click the name of the legend to display the rule results in.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-a-template-style"></a><a name="TemplateStyle"></a> <span data-ttu-id="ca984-145">根據範本樣式更改地圖元素色彩</span><span class="sxs-lookup"><span data-stu-id="ca984-145">To vary map element colors based on a template style</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-a-template-style"></a><span data-ttu-id="ca984-146">根據範本樣式更改地圖元素色彩</span><span class="sxs-lookup"><span data-stu-id="ca984-146">To vary map element colors based on a template style</span></span>  
  
1.  <span data-ttu-id="ca984-147">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-147">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-148">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **色彩規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-148">Right-click the layer that has the data that you want and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-149">按一下 [套用範本樣式]  。</span><span class="sxs-lookup"><span data-stu-id="ca984-149">Click **Apply template style**.</span></span>  
  
     <span data-ttu-id="ca984-150">範本樣式會指定字型、框線樣式以及色彩調色盤。</span><span class="sxs-lookup"><span data-stu-id="ca984-150">A template style specifies font, border style, and color palette.</span></span> <span data-ttu-id="ca984-151">系統會針對在「地圖精靈」或「地圖圖層精靈」中指定的主題，從色彩調色盤指派一個不同的色彩給每個地圖元素。</span><span class="sxs-lookup"><span data-stu-id="ca984-151">Each map element is assigned a different color from the color palette for the theme that was specified in the Map Wizard or Map Layer Wizard.</span></span> <span data-ttu-id="ca984-152">這是套用到沒有相關分析資料之圖層的唯一選項。</span><span class="sxs-lookup"><span data-stu-id="ca984-152">This is the only option that applies to layers that do not have associated analytical data.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-color-palette"></a><a name="ColorPalette"></a> <span data-ttu-id="ca984-153">根據色彩調色盤更改地圖元素色彩</span><span class="sxs-lookup"><span data-stu-id="ca984-153">To vary map element colors based on color palette</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-color-palette"></a><span data-ttu-id="ca984-154">根據色彩調色盤更改地圖元素色彩</span><span class="sxs-lookup"><span data-stu-id="ca984-154">To vary map element colors based on color palette</span></span>  
  
1.  <span data-ttu-id="ca984-155">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-155">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-156">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **色彩規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-156">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-157">按一下 [使用調色盤將資料視覺化]  。</span><span class="sxs-lookup"><span data-stu-id="ca984-157">Click **Visualize data by using color palette**.</span></span>  
  
     <span data-ttu-id="ca984-158">此選項會使用內建調色盤或您指定的自訂調色盤。</span><span class="sxs-lookup"><span data-stu-id="ca984-158">This option uses a built-in or custom palette that you specify.</span></span> <span data-ttu-id="ca984-159">系統會根據相關的分析資料，從調色盤指派一個不同的色彩或色彩陰影給每個地圖元素。</span><span class="sxs-lookup"><span data-stu-id="ca984-159">Based on related analytical data, each map element is assigned a different color or shade of color from the palette.</span></span>  
  
4.  <span data-ttu-id="ca984-160">在 [資料欄位]  中，鍵入包含您要依色彩視覺化之分析資料的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="ca984-160">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="ca984-161">在 [調色盤]  的下拉式清單中，選取要使用的調色盤名稱。</span><span class="sxs-lookup"><span data-stu-id="ca984-161">In **Palette**, from the drop-down list, select the name of the palette to use.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-color-ranges"></a><a name="ColorRanges"></a> <span data-ttu-id="ca984-162">根據色彩範圍更改地圖元素色彩</span><span class="sxs-lookup"><span data-stu-id="ca984-162">To vary map element colors based on color ranges</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-color-ranges"></a><span data-ttu-id="ca984-163">根據色彩範圍更改地圖元素色彩</span><span class="sxs-lookup"><span data-stu-id="ca984-163">To vary map element colors based on color ranges</span></span>  
  
1.  <span data-ttu-id="ca984-164">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-164">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-165">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **色彩規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-165">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-166">按一下 [使用色彩範圍將資料視覺化]  。</span><span class="sxs-lookup"><span data-stu-id="ca984-166">Click **Visualize data by using color ranges**.</span></span>  
  
     <span data-ttu-id="ca984-167">此選項結合您在此頁面上指定的開始色彩、中間色彩與結束色彩，以及您在 [分佈]  頁面上指定的選項，將相關的分析資料分成多個範圍。</span><span class="sxs-lookup"><span data-stu-id="ca984-167">This option, combined with the start, middle, and end colors that you specify on this page and the options that you specify on the **Distribution** page, divide the related analytical data into ranges.</span></span> <span data-ttu-id="ca984-168">報表處理器會根據其相關的資料與所在範圍，指派適當的色彩給每個地圖元素。</span><span class="sxs-lookup"><span data-stu-id="ca984-168">The report processor assigns the appropriate color to each map element based on the its associated data and the range that it falls into.</span></span>  
  
4.  <span data-ttu-id="ca984-169">在 [資料欄位]  中，鍵入包含您要依色彩視覺化之分析資料的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="ca984-169">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="ca984-170">在 [開始色彩]  中，指定要用於最低範圍的色彩。</span><span class="sxs-lookup"><span data-stu-id="ca984-170">In **Start color**, specify the color to use for the lowest range.</span></span>  
  
6.  <span data-ttu-id="ca984-171">在 [中間色彩]  中，指定要用於中間範圍的色彩。</span><span class="sxs-lookup"><span data-stu-id="ca984-171">In **Middle color**, specify the color to use for the middle range.</span></span>  
  
7.  <span data-ttu-id="ca984-172">在 [結束色彩]  中，指定要用於最高範圍的色彩。</span><span class="sxs-lookup"><span data-stu-id="ca984-172">In **End color**, specify the color to use for the highest range.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-custom-colors"></a><a name="CustomColors"></a> <span data-ttu-id="ca984-173">根據自訂色彩更改地圖元素色彩</span><span class="sxs-lookup"><span data-stu-id="ca984-173">To vary map element colors based on custom colors</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-custom-colors"></a><span data-ttu-id="ca984-174">根據自訂色彩更改地圖元素色彩</span><span class="sxs-lookup"><span data-stu-id="ca984-174">To vary map element colors based on custom colors</span></span>  
  
1.  <span data-ttu-id="ca984-175">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-175">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-176">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **色彩規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-176">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-177">按一下 [使用自訂色彩將資料視覺化]  。</span><span class="sxs-lookup"><span data-stu-id="ca984-177">Click **Visualize data by using custom colors**.</span></span>  
  
     <span data-ttu-id="ca984-178">此選項會使用您指定之色彩的清單。</span><span class="sxs-lookup"><span data-stu-id="ca984-178">This option uses the list of colors that you specify.</span></span> <span data-ttu-id="ca984-179">系統會根據相關的分析資料，從清單指派一個色彩給每個地圖元素。</span><span class="sxs-lookup"><span data-stu-id="ca984-179">Based on related analytical data, each map element is assigned a color from the list.</span></span> <span data-ttu-id="ca984-180">如果地圖元素多於色彩，則不會指派任何色彩。</span><span class="sxs-lookup"><span data-stu-id="ca984-180">If there are more map elements than colors, no color is assigned.</span></span>  
  
4.  <span data-ttu-id="ca984-181">在 [資料欄位]  中，鍵入包含您要依色彩視覺化之分析資料的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="ca984-181">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="ca984-182">在 [自訂色彩]  中按一下 [加入]  ，指定每一個自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="ca984-182">In **Custom colors**, click **Add** to specify each custom color.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-set-distribution-options-for-a-legend"></a><a name="DistributionOptions"></a> <span data-ttu-id="ca984-183">設定圖例的分佈選項</span><span class="sxs-lookup"><span data-stu-id="ca984-183">To set distribution options for a legend</span></span>  
  
#### <a name="to-set-distribution-options-for-a-legend"></a><span data-ttu-id="ca984-184">設定圖例的分佈選項</span><span class="sxs-lookup"><span data-stu-id="ca984-184">To set distribution options for a legend</span></span>  
  
1.  <span data-ttu-id="ca984-185">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-185">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-186">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **色彩規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-186">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-187">選取 [使用] 選項將**資料視覺化** \<rule type\> 。</span><span class="sxs-lookup"><span data-stu-id="ca984-187">Select the **Visualize data by using** \<rule type\> option.</span></span> <span data-ttu-id="ca984-188">若要使用分佈選項，您必須根據與圖層相關聯的分析資料，在 [分佈]  頁面上建立範圍。</span><span class="sxs-lookup"><span data-stu-id="ca984-188">To use distribution options, you must create ranges on the **Distribution** page based on analytical data that is associated with the layer.</span></span>  
  
4.  <span data-ttu-id="ca984-189">按一下 **[分佈]** 。</span><span class="sxs-lookup"><span data-stu-id="ca984-189">Click **Distribution**.</span></span>  
  
5.  <span data-ttu-id="ca984-190">選取下列其中一種分佈類型：</span><span class="sxs-lookup"><span data-stu-id="ca984-190">Select one of the following distribution types:</span></span>  
  
    -   <span data-ttu-id="ca984-191">**EqualInterval**：</span><span class="sxs-lookup"><span data-stu-id="ca984-191">**EqualInterval**.</span></span> <span data-ttu-id="ca984-192">指定的範圍會將資料分割成相等的範圍間隔。</span><span class="sxs-lookup"><span data-stu-id="ca984-192">Specifies ranges that divide the data into equal range intervals.</span></span>  
  
    -   <span data-ttu-id="ca984-193">**EqualDistribution**：</span><span class="sxs-lookup"><span data-stu-id="ca984-193">**EqualDistribution**.</span></span> <span data-ttu-id="ca984-194">指定的範圍會分割該資料，讓每個範圍都有相等的項目數目。</span><span class="sxs-lookup"><span data-stu-id="ca984-194">Specifies ranges that divide that data so that each range has an equal number of items.</span></span>  
  
    -   <span data-ttu-id="ca984-195">**最佳**：</span><span class="sxs-lookup"><span data-stu-id="ca984-195">**Optimal**.</span></span> <span data-ttu-id="ca984-196">指定會自動調整分佈的範圍來建立對稱的子範圍。</span><span class="sxs-lookup"><span data-stu-id="ca984-196">Specifies ranges that automatically adjust distribution to create balanced subranges.</span></span>  
  
    -   <span data-ttu-id="ca984-197">**自訂**。</span><span class="sxs-lookup"><span data-stu-id="ca984-197">**Custom**.</span></span> <span data-ttu-id="ca984-198">指定您自己的範圍數目來控制值的分佈。</span><span class="sxs-lookup"><span data-stu-id="ca984-198">Specify your own number of ranges to control the distribution of values.</span></span>  
  
     <span data-ttu-id="ca984-199">如需分佈選項的詳細資訊，請參閱[使用規則與分析資料更改多邊形、線條與點顯示 &#40;報表產生器及 SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ca984-199">For more information about distribution options, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
6.  <span data-ttu-id="ca984-200">在 [子範圍的數目]  中，鍵入要使用的子範圍數目。</span><span class="sxs-lookup"><span data-stu-id="ca984-200">In **Number of subranges**, type the number of subranges to use.</span></span> <span data-ttu-id="ca984-201">當分佈類型為 [最佳]  時，會自動計算子範圍的數目。</span><span class="sxs-lookup"><span data-stu-id="ca984-201">When the distribution type is **Optimal**, the number of subranges is automatically calculated.</span></span>  
  
7.  <span data-ttu-id="ca984-202">在 [範圍開始]  中，鍵入最小範圍值。</span><span class="sxs-lookup"><span data-stu-id="ca984-202">In **Range start**, type a minimum range value.</span></span> <span data-ttu-id="ca984-203">小於此數字的所有值都與範圍最小值相同。</span><span class="sxs-lookup"><span data-stu-id="ca984-203">All values less than this number are the same as the range minimum.</span></span>  
  
8.  <span data-ttu-id="ca984-204">在 [範圍結束]  中，鍵入最大範圍值。</span><span class="sxs-lookup"><span data-stu-id="ca984-204">In **Range end**, type a maximum range value.</span></span> <span data-ttu-id="ca984-205">大於此數字的所有值都與範圍最大值相同。</span><span class="sxs-lookup"><span data-stu-id="ca984-205">All values larger than this number are the same as the range maximum.</span></span>  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-contents-of-a-rule-legend"></a><a name="RuleLegend"></a> <span data-ttu-id="ca984-206">變更規則圖例的內容</span><span class="sxs-lookup"><span data-stu-id="ca984-206">To change the contents of a rule legend</span></span>  
  
#### <a name="to-change-the-contents-of-a-color-size-width-or-marker-type-legend"></a><span data-ttu-id="ca984-207">變更色彩、大小、寬度或標記類型圖例的內容</span><span class="sxs-lookup"><span data-stu-id="ca984-207">To change the contents of a color, size, width, or marker type legend</span></span>  
  
1.  <span data-ttu-id="ca984-208">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-208">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-209">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-209">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-210">確認已選取 [**使用將資料視覺化**] \<*rule type*> 。</span><span class="sxs-lookup"><span data-stu-id="ca984-210">Verify that **Visualize data by using** \<*rule type*> is selected.</span></span>  
  
4.  <span data-ttu-id="ca984-211">在 [資料欄位]  中，確認已選取您要在圖層上視覺化的分析資料。</span><span class="sxs-lookup"><span data-stu-id="ca984-211">In **Data field**, verify that the analytical data that you are visualizing on the layer is selected.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ca984-212">如果下拉式清單中沒有顯示任何欄位，請以滑鼠右鍵按一下圖層，然後按一下 [圖層資料]  來開啟 [地圖圖層資料屬性] 對話方塊的 [分析資料] 頁面，並驗證您已經指定此圖層的分析資料。</span><span class="sxs-lookup"><span data-stu-id="ca984-212">If no fields appear in the drop-down list, right-click the layer, and then click **Layer Data** to open the Map Layer Data Properties Dialog Box, Analytical Data page and verify that you have specified analytical data for this layer.</span></span>  
  
5.  <span data-ttu-id="ca984-213">按一下 **[圖例]** 。</span><span class="sxs-lookup"><span data-stu-id="ca984-213">Click **Legend**.</span></span>  
  
6.  <span data-ttu-id="ca984-214">在 [在此圖例中顯示]  中，選取要用來顯示規則結果的地圖圖例。</span><span class="sxs-lookup"><span data-stu-id="ca984-214">In **Show in this legend**, select the map legend to use to display the rule results.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-contents-of-the-color-scale"></a><a name="ColorScale"></a> <span data-ttu-id="ca984-215">變更色階的內容</span><span class="sxs-lookup"><span data-stu-id="ca984-215">To change the contents of the color scale</span></span>  
  
#### <a name="to-change-the-contents-of-the-color-scale-or-a-color-legend"></a><span data-ttu-id="ca984-216">變更色階或色彩圖例的內容</span><span class="sxs-lookup"><span data-stu-id="ca984-216">To change the contents of the color scale or a color legend</span></span>  
  
1.  <span data-ttu-id="ca984-217">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-217">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-218">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **色彩規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-218">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-219">選取要使用的色彩規則選項。</span><span class="sxs-lookup"><span data-stu-id="ca984-219">Select the color rule option to use.</span></span> <span data-ttu-id="ca984-220">若要以地圖圖例或色階顯示專案，您必須選取其中一個 [使用選項將**資料視覺化**] \<rule type> 。</span><span class="sxs-lookup"><span data-stu-id="ca984-220">To display items in a map legend or color scale, you must select one of the **Visualize data by using** \<rule type> options.</span></span>  
  
4.  <span data-ttu-id="ca984-221">在 [資料欄位]  中，確認已選取您要在圖層上視覺化的分析資料。</span><span class="sxs-lookup"><span data-stu-id="ca984-221">In **Data field**, verify that the analytical data that you are visualizing on the layer is selected.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ca984-222">如果下拉式清單中沒有顯示任何欄位，請以滑鼠右鍵按一下圖層，然後按一下 [圖層資料]  來開啟 [地圖圖層資料屬性] 對話方塊的 [分析資料] 頁面，並驗證您已經指定此圖層的分析資料。</span><span class="sxs-lookup"><span data-stu-id="ca984-222">If no fields appear in the drop-down list, right-click the layer, and then click **Layer Data** to open the Map Layer Data Properties Dialog Box, Analytical Data page and verify that you have specified analytical data for this layer.</span></span>  
  
5.  <span data-ttu-id="ca984-223">按一下 **[圖例]** 。</span><span class="sxs-lookup"><span data-stu-id="ca984-223">Click **Legend**.</span></span>  
  
6.  <span data-ttu-id="ca984-224">在 [色階選項]  中，選取 [以色階顯示]  ，使用色階顯示規則結果。</span><span class="sxs-lookup"><span data-stu-id="ca984-224">In **Color scale options**, select **Show in color scale** to display the rule results in the color scale.</span></span> <span data-ttu-id="ca984-225">您可以為多個色彩規則指定這個選項。</span><span class="sxs-lookup"><span data-stu-id="ca984-225">You can specify this option for more than one color rule.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-remove-all-items-from-a-legend"></a><a name="HideItems"></a> <span data-ttu-id="ca984-226">移除圖例中的所有項目</span><span class="sxs-lookup"><span data-stu-id="ca984-226">To remove all items from a legend</span></span>  
  
#### <a name="to-hide-items-based-on-a-rule"></a><span data-ttu-id="ca984-227">根據規則隱藏項目</span><span class="sxs-lookup"><span data-stu-id="ca984-227">To hide items based on a rule</span></span>  
  
1.  <span data-ttu-id="ca984-228">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-228">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-229">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-229">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-230">按一下 **[圖例]** 。</span><span class="sxs-lookup"><span data-stu-id="ca984-230">Click **Legend**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-format-of-content-in-a-legend"></a><a name="ChangeFormatItems"></a> <span data-ttu-id="ca984-231">變更圖例中的內容格式</span><span class="sxs-lookup"><span data-stu-id="ca984-231">To change the format of content in a legend</span></span>  
 <span data-ttu-id="ca984-232">設定與地圖圖例相關聯之規則的圖例選項。</span><span class="sxs-lookup"><span data-stu-id="ca984-232">Set legend options for the rule that is associated with the map legend.</span></span>  
  
#### <a name="to-change-the-format-of-content-in-a-legend"></a><span data-ttu-id="ca984-233">變更圖例中的內容格式</span><span class="sxs-lookup"><span data-stu-id="ca984-233">To change the format of content in a legend</span></span>  
  
1.  <span data-ttu-id="ca984-234">在 [設計] 檢視中，按一下地圖，直到 [地圖] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="ca984-234">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="ca984-235">以滑鼠右鍵按一下包含所需資料的圖層，然後按一下 [ _\<map element type\>_ **規則**]。</span><span class="sxs-lookup"><span data-stu-id="ca984-235">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="ca984-236">按一下 **[圖例]** 。</span><span class="sxs-lookup"><span data-stu-id="ca984-236">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="ca984-237">[圖例文字]  會顯示關鍵字，這些關鍵字會指定出現在圖例中的資料。</span><span class="sxs-lookup"><span data-stu-id="ca984-237">**Legend text** displays keywords that specify which data appears in the legend.</span></span> <span data-ttu-id="ca984-238">使用地圖關鍵字和自訂格式，有助於控制圖例文字的格式。</span><span class="sxs-lookup"><span data-stu-id="ca984-238">Use map keywords and custom formats to help control the format of legend text.</span></span> <span data-ttu-id="ca984-239">例如，#FROMVALUE {C2} 會指定包含兩位小數位數的貨幣格式。</span><span class="sxs-lookup"><span data-stu-id="ca984-239">For example, #FROMVALUE {C2} specifies a currency format with two decimal places.</span></span> <span data-ttu-id="ca984-240">如需詳細資訊，請參閱 [使用規則與分析資料更改多邊形、線條與點顯示 &#40;報表產生器及 SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ca984-240">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="ca984-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca984-241">See Also</span></span>  
 <span data-ttu-id="ca984-242">[地圖 &#40;報表產生器及 SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ca984-242">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ca984-243">[新增、變更或刪除地圖或地圖圖層 &#40;報表產生器及 SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ca984-243">[Add, Change, or Delete a Map or Map Layer &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ca984-244">[自訂地圖或地圖圖層的資料和顯示 &#40;報表產生器及 SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ca984-244">[Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ca984-245">[報表疑難排解：地圖報表 &#40;報表產生器及 SSRS&#41;](troubleshoot-reports-map-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ca984-245">[Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;](troubleshoot-reports-map-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ca984-246">地圖精靈與地圖圖層精靈 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ca984-246">Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;</span></span>](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)  
  
  
