---
title: 轉譯報表項目 (報表產生器及) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 99ebb4dc-41cc-42ac-82dd-a2b0e31155a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4e0b1dabee096cfbaab53227926633f8d7a3697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595732"
---
# <a name="rendering-report-items-report-builder-and-ssrs"></a><span data-ttu-id="f4066-102">Rendering Report Items (Report Builder and SSRS)</span><span class="sxs-lookup"><span data-stu-id="f4066-102">Rendering Report Items (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f4066-103">報表項目的數目、大小和位置會影響轉譯器為報表主體分頁的方式。</span><span class="sxs-lookup"><span data-stu-id="f4066-103">The number, size, and location of report items affect how the renderers paginate the report body.</span></span> <span data-ttu-id="f4066-104">下列是如何轉譯各種報表項目的描述。</span><span class="sxs-lookup"><span data-stu-id="f4066-104">Below is a description of how various report items are rendered.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="overlapping-report-items"></a><span data-ttu-id="f4066-105">重疊的報表項目</span><span class="sxs-lookup"><span data-stu-id="f4066-105">Overlapping Report Items</span></span>  
 <span data-ttu-id="f4066-106">在 HTML、MHTML、Word、Excel、[預覽] 或「報表檢視器」中不支援重疊的報表項目。</span><span class="sxs-lookup"><span data-stu-id="f4066-106">Overlapping report items are not supported in HTML, MHTML, Word, Excel, in Preview, or the Report Viewer.</span></span> <span data-ttu-id="f4066-107">如果有重疊的項目，它們會移動。</span><span class="sxs-lookup"><span data-stu-id="f4066-107">If overlapping items exist, they are moved.</span></span> <span data-ttu-id="f4066-108">下列規則適用於重疊的報表項目：</span><span class="sxs-lookup"><span data-stu-id="f4066-108">The following rules are applied to overlapping report items:</span></span>  
  
-   <span data-ttu-id="f4066-109">如果報表項目的垂直重疊較大，系統會將其中一個重疊項目移到右側。</span><span class="sxs-lookup"><span data-stu-id="f4066-109">If the vertical overlap of report items is greater, one of the overlapping items is moved to the right.</span></span> <span data-ttu-id="f4066-110">最左邊的項目則維持在所在的位置。</span><span class="sxs-lookup"><span data-stu-id="f4066-110">The left-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="f4066-111">如果報表項目的水平重疊較大，系統會將其中一個重疊項目移到下方。</span><span class="sxs-lookup"><span data-stu-id="f4066-111">If the horizontal overlap of report items is greater, one of the overlapping items is moved down.</span></span> <span data-ttu-id="f4066-112">最上面的項目則維持在所在的位置。</span><span class="sxs-lookup"><span data-stu-id="f4066-112">The top-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="f4066-113">如果垂直重疊與水平重疊相等，系統會將其中一個重疊項目移到右側。</span><span class="sxs-lookup"><span data-stu-id="f4066-113">If the vertical and horizontal overlap is equal, one of the overlapping items is moved to the right.</span></span> <span data-ttu-id="f4066-114">最左邊的項目則維持在所在的位置。</span><span class="sxs-lookup"><span data-stu-id="f4066-114">The left-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="f4066-115">如果必須移動項目來更正重疊，相鄰的報表項目會向下和/或向右移動，以維持該項目與其上方和/或左方之報表項目之間的最小間距。</span><span class="sxs-lookup"><span data-stu-id="f4066-115">If an item must be moved to correct overlapping, adjacent report items move down and/or to the right to maintain a minimum amount of spacing between the item and the report items that end above it and/or to the left of it.</span></span> <span data-ttu-id="f4066-116">例如，假設有兩個報表項目垂直重疊，而第三個報表項目與右側的報表項目距離 2 英吋。</span><span class="sxs-lookup"><span data-stu-id="f4066-116">For example, suppose two report items overlap vertically and a third report item is 2 inches to the right of them.</span></span> <span data-ttu-id="f4066-117">當重疊的報表項目向右移動時，第三個報表項目也會向右移動，才能讓本身與其左側的報表項目維持 2 英吋的距離。</span><span class="sxs-lookup"><span data-stu-id="f4066-117">When the overlapping report item is moved to the right, the third report item moves to the right as well in order to maintain the 2 inches between itself and the report item to its left.</span></span>  
  
 <span data-ttu-id="f4066-118">手動分頁符號格式支援重疊的報表項目，包括列印。</span><span class="sxs-lookup"><span data-stu-id="f4066-118">Overlapping report items are supported in hard page-break formats, including print.</span></span>  
  
## <a name="visibility-and-report-items"></a><span data-ttu-id="f4066-119">可見性與報表項目</span><span class="sxs-lookup"><span data-stu-id="f4066-119">Visibility and Report Items</span></span>  
 <span data-ttu-id="f4066-120">根據預設，系統可以隱藏或顯示報表項目，會使用運算式有條件地隱藏或顯示。</span><span class="sxs-lookup"><span data-stu-id="f4066-120">Report items can be hidden or displayed by default, or hidden or displayed conditionally using expressions.</span></span> <span data-ttu-id="f4066-121">或者，您可以按一下其他報表項目來切換可見性。</span><span class="sxs-lookup"><span data-stu-id="f4066-121">Optionally, the visibility can be switched by clicking another report item.</span></span>  
  
 <span data-ttu-id="f4066-122">轉譯報表項目時，可以使用下列可見性規則：</span><span class="sxs-lookup"><span data-stu-id="f4066-122">The following visibility rules apply when rendering report items:</span></span>  
  
-   <span data-ttu-id="f4066-123">如果報表項目及其內容永遠是隱藏的 (根據運算式，該報表項目不是隱藏的，或其可見性無法透過按一下其他報表項目切換)，則其右方或下方的其他報表項目就不會移動，也不會填滿空的空間。</span><span class="sxs-lookup"><span data-stu-id="f4066-123">If a report item and its contents are always hidden (it is not hidden based on an expression or its visibility cannot be switched by clicking another report item), then other report items to the right or below it do not move to fill the empty space.</span></span> <span data-ttu-id="f4066-124">例如，如果矩形及其中的影像是隱藏的，矩形右側開始的報表項目就不會移到左側，也不會填滿看似空的空間。</span><span class="sxs-lookup"><span data-stu-id="f4066-124">For example, if a rectangle and the image contained within it are hidden, the report item that starts to the right of the rectangle does not move to the left to fill what appears to be empty space.</span></span> <span data-ttu-id="f4066-125">而矩形佔用的空間則會保留。</span><span class="sxs-lookup"><span data-stu-id="f4066-125">The space occupied by the rectangle is preserved.</span></span>  
  
-   <span data-ttu-id="f4066-126">如果報表項目及其內容是有條件隱藏的 (根據運算式，該報表項目是隱藏的，或其可見性可透過按一下其他報表項目切換)，則其右方或下方的報表項目就會移動到左側，來填滿隱藏項目時的空間。</span><span class="sxs-lookup"><span data-stu-id="f4066-126">If a report item and its contents are hidden conditionally (it is hidden based on an expression or its visibility is switched by clicking another report item), then report items to the right or below it move to the left to fill in the space when the item is hidden.</span></span>  
  
-   <span data-ttu-id="f4066-127">如果報表項目及其內容的可見性可以透過按一下其他報表項目切換，則分頁會變更，只在一開始顯示報表項目時，容納報表項目及其內容。</span><span class="sxs-lookup"><span data-stu-id="f4066-127">If the visibility of a report item and its contents can be switched by clicking another report item, then pagination changes to accommodate the report item and its contents only when it is initially displayed.</span></span>  
  
## <a name="keeping-report-items-together-on-a-single-page"></a><span data-ttu-id="f4066-128">讓報表項目在單一頁面上保持在一起</span><span class="sxs-lookup"><span data-stu-id="f4066-128">Keeping Report Items Together on a Single Page</span></span>  
 <span data-ttu-id="f4066-129">您可以設定保持群組或保持在一起屬性，在單一頁面上以隱含或明確的方式，讓報表內的許多報表項目保持在一起。</span><span class="sxs-lookup"><span data-stu-id="f4066-129">Many report items within a report can be kept together on a single page implicitly or explicitly by setting the keep with group or keep together properties.</span></span> <span data-ttu-id="f4066-130">如果報表項目沒有任何邏輯分頁符號，而且在尺寸上小於可用的頁面區域，則永遠會在相同的頁面上轉譯報表項目。</span><span class="sxs-lookup"><span data-stu-id="f4066-130">Report items are always rendered on the same page if the report item does not have any logical page breaks and is smaller in size than the usable page area.</span></span> <span data-ttu-id="f4066-131">如果報表項目無法完全容納在通常報表一開始的頁面上，就會在報表項目前插入一個手動分頁符號，強制該報表項目移到下一頁。</span><span class="sxs-lookup"><span data-stu-id="f4066-131">If a report item does not fit completely on the page on which it would usually start, a hard page break is inserted before the report item, forcing it to the next page.</span></span> <span data-ttu-id="f4066-132">若是軟分頁符號轉譯器，頁面則會擴張，以容納報表項目。</span><span class="sxs-lookup"><span data-stu-id="f4066-132">For soft page-break renderers, the page grows to accommodate the report item.</span></span>  
  
 <span data-ttu-id="f4066-133">當報表項目永遠呈隱藏狀態時，就會忽略將項目保持在一起的規則。</span><span class="sxs-lookup"><span data-stu-id="f4066-133">When the report item is always hidden, the rules for keeping items together are ignored.</span></span>  
  
 <span data-ttu-id="f4066-134">下列項目會永遠保持在一起：</span><span class="sxs-lookup"><span data-stu-id="f4066-134">The following items are always kept together:</span></span>  
  
-   <span data-ttu-id="f4066-135">影像。</span><span class="sxs-lookup"><span data-stu-id="f4066-135">Images.</span></span>  
  
-   <span data-ttu-id="f4066-136">線條：</span><span class="sxs-lookup"><span data-stu-id="f4066-136">Lines.</span></span>  
  
-   <span data-ttu-id="f4066-137">圖表、量測計和對應。</span><span class="sxs-lookup"><span data-stu-id="f4066-137">Charts, gauges, and maps.</span></span>  
  
-   <span data-ttu-id="f4066-138">資料區域中的單一資料列，選取保持群組選項時，該資料列會單獨出現在另一個頁面上。</span><span class="sxs-lookup"><span data-stu-id="f4066-138">A single row in a data region that appears separately on another page, by selecting the keep with group option.</span></span> <span data-ttu-id="f4066-139">這樣會將單一資料列與群組的至少一個執行個體隱含的保持在一起，讓該資料列不會遭到遺棄。</span><span class="sxs-lookup"><span data-stu-id="f4066-139">This will implicitly keep together the single row with at least one instance of the group so that the row is not orphaned.</span></span> <span data-ttu-id="f4066-140">您可以在資料區域或群組上設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="f4066-140">You can set this option on a data region or a group.</span></span>  
  
-   <span data-ttu-id="f4066-141">資料區域的頁首區域。</span><span class="sxs-lookup"><span data-stu-id="f4066-141">Header area of a data region.</span></span>  
  
-   <span data-ttu-id="f4066-142">資料區的頁首區域以及資料的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="f4066-142">Header area of a data region and the first row of data.</span></span>  
  
-   <span data-ttu-id="f4066-143">在 Tablix 資料區中可以切換的報表項目。</span><span class="sxs-lookup"><span data-stu-id="f4066-143">Report items that can be toggled in a tablix data region.</span></span>  
  
### <a name="priority-order"></a><span data-ttu-id="f4066-144">優先順序</span><span class="sxs-lookup"><span data-stu-id="f4066-144">Priority Order</span></span>  
 <span data-ttu-id="f4066-145">由於頁面大小的限制，讓報表項目保持在一起的規則之間可能會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="f4066-145">Due to page size limitations, conflicts can arise between the rules for keeping report items together.</span></span> <span data-ttu-id="f4066-146">當衝突發生時，系統會使用下列優先順序，以便在轉譯時讓項目保持在一起：</span><span class="sxs-lookup"><span data-stu-id="f4066-146">When conflicts occur, the following priority order is used to keep items together when rendering:</span></span>  
  
-   <span data-ttu-id="f4066-147">線條、圖表和影像。</span><span class="sxs-lookup"><span data-stu-id="f4066-147">Lines, charts, and images.</span></span>  
  
-   <span data-ttu-id="f4066-148">段落遺留字串控制。</span><span class="sxs-lookup"><span data-stu-id="f4066-148">Widow and orphan control.</span></span>  
  
-   <span data-ttu-id="f4066-149">重複的資料行標頭和資料列標頭。</span><span class="sxs-lookup"><span data-stu-id="f4066-149">Repeated column headers and row headers.</span></span>  
  
     <span data-ttu-id="f4066-150">頁首優先於頁尾。</span><span class="sxs-lookup"><span data-stu-id="f4066-150">Headers take precedence over footers.</span></span> <span data-ttu-id="f4066-151">內部重複的群組優先於外部群組。</span><span class="sxs-lookup"><span data-stu-id="f4066-151">Inner repeated groups have priority over outer groups.</span></span> <span data-ttu-id="f4066-152">設定 `RepeatWith` 屬性的項目中，與目標資料區域較近的項目優先於與資料區域較遠的項目。</span><span class="sxs-lookup"><span data-stu-id="f4066-152">Items where the `RepeatWith` property is set that are closer to the target data region have priority over items that are farther away from the data region.</span></span>  
  
-   <span data-ttu-id="f4066-153">具有明確的 [保持等式] 屬性設定為的小型報表專案（例如文字方塊或矩形） `true` 。</span><span class="sxs-lookup"><span data-stu-id="f4066-153">Small report items, such as text boxes or rectangles, with an explicit KeepTogether property set to `true`.</span></span>  
  
-   <span data-ttu-id="f4066-154">大型報表專案，例如子報表或非最內部的 tablix 成員，其明確的 [保持與] 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f4066-154">Large report items, such as subreports or a non-innermost tablix member, with an explicit KeepTogether property set to `true`.</span></span>  
  
-   <span data-ttu-id="f4066-155">具有明確的保持屬性的 Tablix 資料區域會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f4066-155">Tablix data regions with an explicit KeepTogether property set to `true`.</span></span>  
  
### <a name="subreports"></a><span data-ttu-id="f4066-156">子報表</span><span class="sxs-lookup"><span data-stu-id="f4066-156">Subreports</span></span>  
 <span data-ttu-id="f4066-157">子報表會轉譯為包含在個別報表 .rdl 檔案中定義之其他報表的矩形。</span><span class="sxs-lookup"><span data-stu-id="f4066-157">A subreport renders as a rectangle that contains another report that is defined in a separate report .rdl file.</span></span> <span data-ttu-id="f4066-158">子報表檔案必須先發行到報表伺服器上，父報表才能進行存取。</span><span class="sxs-lookup"><span data-stu-id="f4066-158">The subreport file must be published to a report server before it can be accessed by the parent report.</span></span>  
  
 <span data-ttu-id="f4066-159">轉譯子報表時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="f4066-159">The following rules apply when rendering subreports:</span></span>  
  
-   <span data-ttu-id="f4066-160">子報表可以擴張到定義子報表之 .rdl 檔案中所定義的主體大小。</span><span class="sxs-lookup"><span data-stu-id="f4066-160">Subreports can grow to the size of the body defined in the .rdl file that defines the subreport.</span></span> <span data-ttu-id="f4066-161">例如，如果子報表的 RDL 指出子報表主體的寬度為 5 英吋，則子報表在父報表內的寬度為 5 英吋。</span><span class="sxs-lookup"><span data-stu-id="f4066-161">For example, if the RDL for the subreport states that the subreport body is 5 inches wide, then the subreport will be 5 inches wide within the parent report.</span></span>  
  
-   <span data-ttu-id="f4066-162">子報表會從父報表繼承資料行設定。</span><span class="sxs-lookup"><span data-stu-id="f4066-162">Subreports inherit column settings from the parent report.</span></span> <span data-ttu-id="f4066-163">而原始 RDL 中定義的資料行設定永遠會遭到忽略。</span><span class="sxs-lookup"><span data-stu-id="f4066-163">Column settings that are defined in the original RDL are always ignored.</span></span>  
  
-   <span data-ttu-id="f4066-164">系統只會轉譯子報表的主體。</span><span class="sxs-lookup"><span data-stu-id="f4066-164">Only the body of the subreport is rendered.</span></span> <span data-ttu-id="f4066-165">在父報表中轉譯子報表時，不會轉譯在子報表 .rdl 檔案中所定義的頁首和頁尾區段。</span><span class="sxs-lookup"><span data-stu-id="f4066-165">Header and footer sections that are defined in the subreport's .rdl file are not rendered when the subreport is rendered in the parent report.</span></span>  
  
-   <span data-ttu-id="f4066-166">子報表擁有一個明確的 KeepTogether 屬性。</span><span class="sxs-lookup"><span data-stu-id="f4066-166">Subreports have an explicit KeepTogether property.</span></span> <span data-ttu-id="f4066-167">當該屬性設定為 `true` 時，子報表中的所有項目在單一頁面中都會盡可能保持在一起。</span><span class="sxs-lookup"><span data-stu-id="f4066-167">When it is set to `true`, all the items in the subreport are kept together on one page when possible.</span></span>  
  
-   <span data-ttu-id="f4066-168">如果子報表無法執行，就會在報表中顯示為包含錯誤訊息的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f4066-168">If a subreport cannot run, it is displayed in the report as a text box with an error message.</span></span> <span data-ttu-id="f4066-169">套用到子報表的樣式屬性會改為套用到文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f4066-169">The style properties applied to the subreport are applied to the text box instead.</span></span>  
  
-   <span data-ttu-id="f4066-170">如果透過分頁符號分割子報表， **[省略分頁符號上的框線]** 設定會控制子報表上的框線是封閉的還是開放的。</span><span class="sxs-lookup"><span data-stu-id="f4066-170">If the subreport is split by a page break, the **Omit border on page break** setting controls whether or not the borders on the subreport are closed or open.</span></span>  
  
 <span data-ttu-id="f4066-171">如需子報表的詳細資訊，請參閱[子報表 &#40;報表產生器及 SSRS&#41;](subreports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f4066-171">For more information about subreports, see [Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4066-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4066-172">See Also</span></span>  
 <span data-ttu-id="f4066-173">[Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4066-173">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f4066-174">[轉譯行為 &#40;報表產生器及 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4066-174">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f4066-175">[不同報表轉譯延伸模組的互動式功能 &#40;報表產生器及 SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="f4066-175">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 [<span data-ttu-id="f4066-176">清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f4066-176">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
