---
title: 匯出成員表單編輯器 ([計算] 索引標籤、Cube 設計工具)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationexpression.calculatedmember.f1
ms.assetid: f7719b9e-b1e6-4792-90a6-30d9d8eb1196
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9dd45ece03fd81e0e7356e7bdcd0ec8dc53287bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593093"
---
# <a name="calculated-member-form-editor-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="4e965-102">導出成員表單編輯器 (計算索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="4e965-102">Calculated Member Form Editor (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="4e965-103">在 Cube 設計師中，使用 **[計算]** 索引標籤上的 **[導出成表單編輯器]** 窗格，即可建立或修改導出成員。</span><span class="sxs-lookup"><span data-stu-id="4e965-103">Use the **Calculated Member Form Editor** pane on the **Calculations** tab in Cube Designer to create or modify a calculated member.</span></span>  
  
 <span data-ttu-id="4e965-104">**請注意** 這個窗格只會在表單檢視中顯示。</span><span class="sxs-lookup"><span data-stu-id="4e965-104">**Note** This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4e965-105">選項。</span><span class="sxs-lookup"><span data-stu-id="4e965-105">Options</span></span>  
 <span data-ttu-id="4e965-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4e965-106">**Name**</span></span>  
 <span data-ttu-id="4e965-107">鍵入導出成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e965-107">Type the name of the calculated member.</span></span>  
  
 <span data-ttu-id="4e965-108">**父屬性**</span><span class="sxs-lookup"><span data-stu-id="4e965-108">**Parent Properties**</span></span>  
 <span data-ttu-id="4e965-109">展開以檢視 [父階層]\*\*\*\*、[父成員]\*\*\*\* 和 [變更]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="4e965-109">Expand to view the **Parent hierarchy**, **Parent member**, and **Change** options.</span></span>  
  
 <span data-ttu-id="4e965-110">**父階層**</span><span class="sxs-lookup"><span data-stu-id="4e965-110">**Parent hierarchy**</span></span>  
 <span data-ttu-id="4e965-111">在選取的 Cube 中，選取要包含導出成員的維度和階層。</span><span class="sxs-lookup"><span data-stu-id="4e965-111">Select the dimension and hierarchy in the selected cube that is to include the calculated member.</span></span> <span data-ttu-id="4e965-112">選取 MEASURES 即可定義導出量值。</span><span class="sxs-lookup"><span data-stu-id="4e965-112">Select MEASURES to define a calculated measure.</span></span>  
  
 <span data-ttu-id="4e965-113">**父成員**</span><span class="sxs-lookup"><span data-stu-id="4e965-113">**Parent member**</span></span>  
 <span data-ttu-id="4e965-114">選取將在其下方出現導出成員的成員。</span><span class="sxs-lookup"><span data-stu-id="4e965-114">Select the member beneath which the calculated member is to appear.</span></span>  
  
 <span data-ttu-id="4e965-115">**請注意** 如果 **[父階層]** 指定 MEASURES 以外的階層，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="4e965-115">**Note** This option is available if **Parent hierarchy** specifies a hierarchy other than MEASURES.</span></span>  
  
 <span data-ttu-id="4e965-116">**變更**</span><span class="sxs-lookup"><span data-stu-id="4e965-116">**Change**</span></span>  
 <span data-ttu-id="4e965-117">選取即可顯示 [選取父成員]\*\*\*\* 對話方塊，然後選擇 [父成員]\*\*\*\* 的成員。</span><span class="sxs-lookup"><span data-stu-id="4e965-117">Select to display the **Select Parent Member** dialog box and choose a member for **Parent member**.</span></span> <span data-ttu-id="4e965-118">如需 [選取父成員]\*\*\*\* 對話方塊的詳細資訊，請參閱[選取父成員對話方塊 &#40;Analysis Services - 多維度資料&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4e965-118">For more information about the **Select Parent Member** dialog box, see [Select Parent Member Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="4e965-119">**運算式**</span><span class="sxs-lookup"><span data-stu-id="4e965-119">**Expression**</span></span>  
 <span data-ttu-id="4e965-120">展開以檢視或編輯導出成員的多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-120">Expand to view or edit the Multidimensional Expressions (MDX) expression for the calculated member.</span></span>  
  
 <span data-ttu-id="4e965-121">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="4e965-121">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e965-122">建議將此運算式評估為字串或數值。</span><span class="sxs-lookup"><span data-stu-id="4e965-122">It is recommended that this expression evaluate to a string or to a numeric value.</span></span>  
  
 <span data-ttu-id="4e965-123">**其他屬性**</span><span class="sxs-lookup"><span data-stu-id="4e965-123">**Additional Properties**</span></span>  
 <span data-ttu-id="4e965-124">展開以檢視 [格式字串]\*\*\*\*、[可見]\*\*\*\*、[非空白行為]\*\*\*\*、[色彩運算式]\*\*\*\* 和 [字型運算式]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="4e965-124">Expand to view the **Format string**, **Visible**, **Non-empty behavior**, **Color Expressions**, and **Font Expressions** options.</span></span>  
  
 <span data-ttu-id="4e965-125">**格式字串**</span><span class="sxs-lookup"><span data-stu-id="4e965-125">**Format string**</span></span>  
 <span data-ttu-id="4e965-126">鍵入用來將導出成員所傳回值格式化的 MDX 格式字串，或是選取預先定義的格式字串。</span><span class="sxs-lookup"><span data-stu-id="4e965-126">Type the MDX format string used to format the value returned by the calculated member, or select a predefined format string.</span></span>  
  
 <span data-ttu-id="4e965-127">如需 MDX 格式字串的詳細資訊，請參閱 [FORMAT_STRING 內容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="4e965-127">For more information about MDX format strings, see [FORMAT_STRING Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md).</span></span>  
  
 <span data-ttu-id="4e965-128">**亮起**</span><span class="sxs-lookup"><span data-stu-id="4e965-128">**Visible**</span></span>  
 <span data-ttu-id="4e965-129">選取 [True]\*\*\*\* 即可讓用戶端應用程式看見導出成員。</span><span class="sxs-lookup"><span data-stu-id="4e965-129">Select **True** to allow the calculated member to be visible to client applications.</span></span>  
  
 <span data-ttu-id="4e965-130">**非空白行為**</span><span class="sxs-lookup"><span data-stu-id="4e965-130">**Non-empty behavior**</span></span>  
 <span data-ttu-id="4e965-131">為導出成員選取用來解析 MDX 中之 NON EMPTY 查詢的量值名稱。</span><span class="sxs-lookup"><span data-stu-id="4e965-131">Select the name of the measure used to resolve NON EMPTY queries in MDX for the calculated member.</span></span> <span data-ttu-id="4e965-132">如果 **[非空白行為]** 屬性為空白，就必須重複評估導出成員來決定成員是否為空白。</span><span class="sxs-lookup"><span data-stu-id="4e965-132">If the **Non Empty Behavior** property is blank, the calculated member must be evaluated repeatedly to determine if a member is empty.</span></span> <span data-ttu-id="4e965-133">如果 **[非空白行為]** 屬性包含量值的名稱，且指定的量值是空白的，就會將導出成員視為空白。</span><span class="sxs-lookup"><span data-stu-id="4e965-133">If the **Non Empty Behavior** property contains the name of a measure, the calculated member is treated as empty if the specified measure is empty.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="4e965-134">此屬性已被取代。</span><span class="sxs-lookup"><span data-stu-id="4e965-134">This property is deprecated.</span></span> <span data-ttu-id="4e965-135">請勿設定。</span><span class="sxs-lookup"><span data-stu-id="4e965-135">Avoid setting it.</span></span> <span data-ttu-id="4e965-136">如需詳細資訊，請參閱[SQL Server 2014 中已淘汰的 Analysis Services 功能](deprecated-analysis-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="4e965-136">See [Deprecated Analysis Services Features in SQL Server 2014](deprecated-analysis-services-features-in-sql-server-2014.md) for details.</span></span>  
  
 <span data-ttu-id="4e965-137">**色彩運算式**</span><span class="sxs-lookup"><span data-stu-id="4e965-137">**Color Expressions**</span></span>  
 <span data-ttu-id="4e965-138">展開以檢視 [前景色彩]\*\*\*\* 和 [背景色彩]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="4e965-138">Expand to view the **Fore color** and **Back color** options.</span></span>  
  
 <span data-ttu-id="4e965-139">**前景色彩**</span><span class="sxs-lookup"><span data-stu-id="4e965-139">**Fore color**</span></span>  
 <span data-ttu-id="4e965-140">鍵入會提供導出成員之前景色彩的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-140">Type the MDX expression that provides the foreground color of the calculated member.</span></span>  
  
 <span data-ttu-id="4e965-141">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="4e965-141">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="4e965-142">按一下色彩選擇按鈕即可顯示 [色彩]\*\*\*\* 對話方塊，並將指定色彩的 RGB (紅-綠-藍) 值插入 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-142">Click the color selection button to display the **Color** dialog box and insert the RGB (Red-Green-Blue) value for a specified color into the MDX expression.</span></span> <span data-ttu-id="4e965-143">如需 RGB 值的詳細資訊，請參閱 [FORE_COLOR 及 BACK_COLOR 內容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="4e965-143">For more information about RGB values, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>  
  
 <span data-ttu-id="4e965-144">**背景色彩**</span><span class="sxs-lookup"><span data-stu-id="4e965-144">**Back color**</span></span>  
 <span data-ttu-id="4e965-145">鍵入會提供導出成員之背景色彩的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-145">Type the MDX expression that provides the background color of the calculated member.</span></span>  
  
 <span data-ttu-id="4e965-146">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="4e965-146">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="4e965-147">按一下色彩選擇按鈕即可顯示 [色彩]\*\*\*\* 對話方塊，並將指定色彩的 RGB (紅-綠-藍) 值插入 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-147">Click the color selection button to display the **Color** dialog box and insert the RGB (Red-Green-Blue) value for a specified color into the MDX expression.</span></span> <span data-ttu-id="4e965-148">如需 RGB 值的詳細資訊，請參閱 [FORE_COLOR 及 BACK_COLOR 內容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="4e965-148">For more information about RGB values, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>  
  
 <span data-ttu-id="4e965-149">**字型運算式**</span><span class="sxs-lookup"><span data-stu-id="4e965-149">**Font Expressions**</span></span>  
 <span data-ttu-id="4e965-150">展開以檢視 [字型名稱]\*\*\*\*、[字型大小]\*\*\*\* 和 [字型旗標]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="4e965-150">Expand to view the **Font name**, **Font size**, and **Font flags** options.</span></span>  
  
 <span data-ttu-id="4e965-151">**字型名稱**</span><span class="sxs-lookup"><span data-stu-id="4e965-151">**Font name**</span></span>  
 <span data-ttu-id="4e965-152">鍵入會提供用於導出成員之字型名稱的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-152">Type the MDX expression that provides the name of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="4e965-153">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="4e965-153">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="4e965-154">按一下字型選擇按鈕即可顯示 **[字型]** 對話方塊，並將指定字型的屬性值插入 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-154">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="4e965-155">如需屬性值的詳細資訊，請參閱[建立和使用屬性值 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="4e965-155">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
 <span data-ttu-id="4e965-156">**字型大小**</span><span class="sxs-lookup"><span data-stu-id="4e965-156">**Font size**</span></span>  
 <span data-ttu-id="4e965-157">鍵入會提供用於導出成員之字型大小的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-157">Type the MDX expression that provides the size of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="4e965-158">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="4e965-158">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="4e965-159">按一下字型選擇按鈕即可顯示 **[字型]** 對話方塊，並將指定字型的屬性值插入 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-159">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="4e965-160">如需屬性值的詳細資訊，請參閱[建立和使用屬性值 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="4e965-160">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
 <span data-ttu-id="4e965-161">**字型旗標**</span><span class="sxs-lookup"><span data-stu-id="4e965-161">**Font flags**</span></span>  
 <span data-ttu-id="4e965-162">鍵入會提供包含導出成員所用字型的字型旗標 (例如底線或粗體字) 之點陣圖值的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-162">Type the MDX expression that provides the bitmapped value containing the font flags, such as underline or bold, of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="4e965-163">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="4e965-163">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="4e965-164">按一下字型選擇按鈕即可顯示 **[字型]** 對話方塊，並將指定字型的屬性值插入 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e965-164">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="4e965-165">如需屬性值的詳細資訊，請參閱[建立和使用屬性值 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="4e965-165">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e965-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e965-166">See Also</span></span>  
 <span data-ttu-id="4e965-167">[Acwp](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="4e965-167">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="4e965-168">[建立匯出成員](multidimensional-models/create-calculated-members.md) </span><span class="sxs-lookup"><span data-stu-id="4e965-168">[Create Calculated Members](multidimensional-models/create-calculated-members.md) </span></span>  
 <span data-ttu-id="4e965-169">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4e965-169">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="4e965-170">[&#40;Cube 設計師的計算&#41; &#40;Analysis Services 多維度資料&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4e965-170">[Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="4e965-171">[工具列 &#40;計算] 索引標籤，Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4e965-171">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="4e965-172">[腳本召集人 &#40;計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4e965-172">[Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="4e965-173">[計算工具 &#40;計算] 索引標籤，Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4e965-173">[Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="4e965-174">[命名集表單編輯器 &#40;計算] 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4e965-174">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="4e965-175">[腳本編輯器 &#40;[計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="4e965-175">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
