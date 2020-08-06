---
title: '[選取色彩] 對話方塊 (報表產生器和 SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.selectcolor.f1
- "10090"
helpviewer_keywords:
- Select Color dialog box
ms.assetid: ac7089a3-5c7b-4f53-8348-180610e86da2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a2526b755fd4e08faf79998d351e824371fac2f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707005"
---
# <a name="select-color-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="da445-102">選取色彩對話方塊 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="da445-102">Select Color Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="da445-103">使用 **Select Color** 對話方塊，可以指定資料區或文字方塊內，單一資料格或多個資料格的背景色彩選項或圖表色彩選項。</span><span class="sxs-lookup"><span data-stu-id="da445-103">Use the **Select Color** dialog box to specify color options for the background of a single cell or multiple cells within a data region or a text box, or for a chart.</span></span>  
  
## <a name="options"></a><span data-ttu-id="da445-104">選項</span><span class="sxs-lookup"><span data-stu-id="da445-104">Options</span></span>  
 <span data-ttu-id="da445-105">**色彩選取器**</span><span class="sxs-lookup"><span data-stu-id="da445-105">**Color selector**</span></span>  
 <span data-ttu-id="da445-106">從指定如何選取色彩的三個選項選擇。</span><span class="sxs-lookup"><span data-stu-id="da445-106">Choose from three options that specify how you want to select colors:</span></span>  
  
-   <span data-ttu-id="da445-107">**選擇器 - 色彩圓形** ：使用「色調/飽和/亮度」(HSB) 色彩值來選擇色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-107">**Picker - Color circle** Choose a color using Hue/Saturation/Brightness (HSB) color values.</span></span>  
  
-   <span data-ttu-id="da445-108">**選擇器 - 色彩方塊** ：使用「紅色/綠色/藍色」(RGB) 色彩值來選擇色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-108">**Picker - Color square** Choose a color using Red/Green/Blue (RGB) color values.</span></span>  
  
-   <span data-ttu-id="da445-109">**調色盤 - 標準色彩** ：從預先定義的色彩值清單選擇色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-109">**Palette - Standard colors** Choose a color from a predefined list of color values.</span></span>  
  
 <span data-ttu-id="da445-110">**色彩圓形**</span><span class="sxs-lookup"><span data-stu-id="da445-110">**Color circle**</span></span>  
 <span data-ttu-id="da445-111">用於 HSB 色彩，因為 HSB 值會對應到圓柱座標系統。</span><span class="sxs-lookup"><span data-stu-id="da445-111">Use for HSB colors because HSB values are mapped onto a cylindrical coordinate system.</span></span> <span data-ttu-id="da445-112">色調是實際的色彩、飽和度是色彩的純度，而亮度是相對亮度或暗度。</span><span class="sxs-lookup"><span data-stu-id="da445-112">Hue is the actual color, saturation is purity of color, brightness is relative brightness or darkness.</span></span>  
  
 <span data-ttu-id="da445-113">挑選色彩時，圓形的中心會決定色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-113">When you pick a color, the center of the circle determines the color.</span></span> <span data-ttu-id="da445-114">使用色彩滑動軸來變更色調。</span><span class="sxs-lookup"><span data-stu-id="da445-114">Use the color slider to change the hue.</span></span> <span data-ttu-id="da445-115">X 和 Y 座標分別表示飽和度和亮度的值。</span><span class="sxs-lookup"><span data-stu-id="da445-115">The x and y coordinates represent saturation and brightness values respectively.</span></span>  
  
 <span data-ttu-id="da445-116">**色彩正方形**</span><span class="sxs-lookup"><span data-stu-id="da445-116">**Color square**</span></span>  
 <span data-ttu-id="da445-117">用於 RGB 色彩，因為 RGB 值會對應到笛卡兒 (Cartesian) 座標系統。</span><span class="sxs-lookup"><span data-stu-id="da445-117">Use for RGB colors because RGB values are mapped to a Cartesian coordinate system.</span></span> <span data-ttu-id="da445-118">R 的值代表紅色、G 的值代表綠色，而 B 的值則代表藍色。</span><span class="sxs-lookup"><span data-stu-id="da445-118">R is the value for Red, G is the value for Green, B is the value for Blue.</span></span>  
  
 <span data-ttu-id="da445-119">挑選色彩時，正方形的中心會決定色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-119">When you pick a color, the center of the square determines the color.</span></span> <span data-ttu-id="da445-120">使用色彩滑動軸來變更所選色彩的範圍。</span><span class="sxs-lookup"><span data-stu-id="da445-120">Use the color slider to change the range of the chosen color.</span></span> <span data-ttu-id="da445-121">X 和 Y 座標代表其他兩種色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-121">The x and y coordinates represent the other two colors.</span></span> <span data-ttu-id="da445-122">例如，如果您挑選綠色，滑動軸會顯示綠色值的範圍，而 X 和 Y 座標則分別代表紅色和藍色值。</span><span class="sxs-lookup"><span data-stu-id="da445-122">For example, if you pick green, the slider shows the range of green values, the x and y coordinates represent red and blue values respectively.</span></span>  
  
 <span data-ttu-id="da445-123">**標準的調色盤色彩**</span><span class="sxs-lookup"><span data-stu-id="da445-123">**Standard palette color**</span></span>  
 <span data-ttu-id="da445-124">用於列舉中的命名色彩 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` 。</span><span class="sxs-lookup"><span data-stu-id="da445-124">Use for named colors from the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` enumeration.</span></span>  
  
 <span data-ttu-id="da445-125">**色彩系統**</span><span class="sxs-lookup"><span data-stu-id="da445-125">**Color system**</span></span>  
 <span data-ttu-id="da445-126">指定 RGB 或 HSB 色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-126">Specify RGB or HSB colors.</span></span> <span data-ttu-id="da445-127">此選項會將顯示變更為顯示 RGB 或 HSB 值，這些值會在您將色彩圓形或色彩正方形用於 **[色彩選取器]** 時，以互動方式更新。</span><span class="sxs-lookup"><span data-stu-id="da445-127">This choice changes the display to show RGB or HSB values, which are updated interactively when you use a color circle or color square for the **Color selector**.</span></span>  
  
 <span data-ttu-id="da445-128">如果色彩可以包含透明值，系統會針對某些屬性顯示 **Alpha** 值。</span><span class="sxs-lookup"><span data-stu-id="da445-128">The **Alpha** value displays for some properties when a color can include a transparency value.</span></span> <span data-ttu-id="da445-129">例如，圖表數列填滿。</span><span class="sxs-lookup"><span data-stu-id="da445-129">For example, Chart series fill.</span></span> <span data-ttu-id="da445-130">對於不支援透明的屬性，系統會停用這個值。</span><span class="sxs-lookup"><span data-stu-id="da445-130">For properties that do not support transparency, this value is disabled.</span></span>  
  
 <span data-ttu-id="da445-131">**安全**</span><span class="sxs-lookup"><span data-stu-id="da445-131">**Red**</span></span>  
 <span data-ttu-id="da445-132">RGB 色彩紅色部分的十進位值。</span><span class="sxs-lookup"><span data-stu-id="da445-132">The decimal value for the red part of the RGB color.</span></span> <span data-ttu-id="da445-133">使用微調方塊來變更值，或輸入一個介於 0 和 255 之間的值。</span><span class="sxs-lookup"><span data-stu-id="da445-133">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="da445-134">**綠色**</span><span class="sxs-lookup"><span data-stu-id="da445-134">**Green**</span></span>  
 <span data-ttu-id="da445-135">RGB 色彩綠色部分的十進位值。</span><span class="sxs-lookup"><span data-stu-id="da445-135">The decimal value for the green part of the RGB color.</span></span> <span data-ttu-id="da445-136">使用微調方塊來變更值，或輸入一個介於 0 和 255 之間的值。</span><span class="sxs-lookup"><span data-stu-id="da445-136">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="da445-137">**藍色**</span><span class="sxs-lookup"><span data-stu-id="da445-137">**Blue**</span></span>  
 <span data-ttu-id="da445-138">RGB 色彩藍色部分的十進位值。</span><span class="sxs-lookup"><span data-stu-id="da445-138">The decimal value for the blue part of the RGB color.</span></span> <span data-ttu-id="da445-139">使用微調方塊來變更值，或輸入一個介於 0 和 255 之間的值。</span><span class="sxs-lookup"><span data-stu-id="da445-139">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="da445-140">**Alpha**</span><span class="sxs-lookup"><span data-stu-id="da445-140">**Alpha**</span></span>  
 <span data-ttu-id="da445-141">色彩 α 或透明部分的十進位值。</span><span class="sxs-lookup"><span data-stu-id="da445-141">The decimal value for the alpha or transparency part of the color.</span></span> <span data-ttu-id="da445-142">啟用這個值時，您可以使用滑動軸參數來調整您需要的透明程度。</span><span class="sxs-lookup"><span data-stu-id="da445-142">When this value is enabled, you can use the slider switch to adjust the degree of transparency you want.</span></span>  
  
 <span data-ttu-id="da445-143">**Hue**</span><span class="sxs-lookup"><span data-stu-id="da445-143">**Hue**</span></span>  
 <span data-ttu-id="da445-144">HSB 色彩色調的十進位值。</span><span class="sxs-lookup"><span data-stu-id="da445-144">The decimal value for the hue of the HSB color.</span></span> <span data-ttu-id="da445-145">使用微調方塊來變更值，或輸入一個介於 0 和 255 之間的值。</span><span class="sxs-lookup"><span data-stu-id="da445-145">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="da445-146">**飽和度**</span><span class="sxs-lookup"><span data-stu-id="da445-146">**Saturation**</span></span>  
 <span data-ttu-id="da445-147">HSB 色彩飽和度的十進位值。</span><span class="sxs-lookup"><span data-stu-id="da445-147">The decimal value for the saturation of the HSB color.</span></span> <span data-ttu-id="da445-148">使用微調方塊來變更值，或輸入一個介於 0 和 255 之間的值。</span><span class="sxs-lookup"><span data-stu-id="da445-148">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="da445-149">**亮度**</span><span class="sxs-lookup"><span data-stu-id="da445-149">**Brightness**</span></span>  
 <span data-ttu-id="da445-150">HSB 色彩亮度的十進位值。</span><span class="sxs-lookup"><span data-stu-id="da445-150">The decimal value for the brightness of the HSB color.</span></span> <span data-ttu-id="da445-151">使用微調方塊來變更值，或輸入一個介於 0 和 255 之間的值。</span><span class="sxs-lookup"><span data-stu-id="da445-151">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="da445-152">**色彩範例**</span><span class="sxs-lookup"><span data-stu-id="da445-152">**Color sample**</span></span>  
 <span data-ttu-id="da445-153">在窗格的左半部顯示目前的色彩，並在窗格的右半部以互動方式顯示您所選擇的新色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-153">Shows the current color on the left half of the pane and interactively shows the new color you are choosing on the right half of the pane.</span></span> <span data-ttu-id="da445-154">如果沒有預設色彩，窗格的左半部為白色。</span><span class="sxs-lookup"><span data-stu-id="da445-154">If there is no default color, the left half of the pane is white.</span></span> <span data-ttu-id="da445-155">大部分的 RDL 屬性都沒有預設色彩。</span><span class="sxs-lookup"><span data-stu-id="da445-155">Most RDL properties have no default color.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da445-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da445-156">See Also</span></span>  
 <span data-ttu-id="da445-157">[將報表專案的格式設定 &#40;報表產生器和 SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="da445-157">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="da445-158">格式化文字和預留位置 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="da445-158">Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;</span></span>](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)  
  
  
