---
title: 轉譯行為 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8f873ef9-27a3-40e5-b58b-6774f8027a58
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d6a6aa91c547f4739b172f9303ac9e61bde5771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704905"
---
# <a name="rendering-behaviors-report-builder--and-ssrs"></a><span data-ttu-id="053a7-102">轉譯行為 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="053a7-102">Rendering Behaviors (Report Builder  and SSRS)</span></span>
  <span data-ttu-id="053a7-103">根據所選取的轉譯器，當轉譯報表時，系統會將某些規則套用到報表主體及其內容。</span><span class="sxs-lookup"><span data-stu-id="053a7-103">Depending on the renderer you select, certain rules are applied to the report body and its contents when rendering a report.</span></span> <span data-ttu-id="053a7-104">將報表項目全部容納在一頁的方式，取決於下列因素的組合：</span><span class="sxs-lookup"><span data-stu-id="053a7-104">How report items fit together on a page is determined by the combination of these factors:</span></span>  
  
-   <span data-ttu-id="053a7-105">轉譯規則。</span><span class="sxs-lookup"><span data-stu-id="053a7-105">Rendering rules.</span></span>  
  
-   <span data-ttu-id="053a7-106">報表項目的寬度和高度。</span><span class="sxs-lookup"><span data-stu-id="053a7-106">The width and height of report items.</span></span>  
  
-   <span data-ttu-id="053a7-107">報表主體的大小。</span><span class="sxs-lookup"><span data-stu-id="053a7-107">The size of the report body.</span></span>  
  
-   <span data-ttu-id="053a7-108">頁面的寬度和高度。</span><span class="sxs-lookup"><span data-stu-id="053a7-108">The width and height of the page.</span></span>  
  
-   <span data-ttu-id="053a7-109">用於分頁的轉譯器特定支援。</span><span class="sxs-lookup"><span data-stu-id="053a7-109">Renderer-specific support for paging.</span></span>  
  
 <span data-ttu-id="053a7-110">本主題討論 Reporting Services 所應用的一般規則。</span><span class="sxs-lookup"><span data-stu-id="053a7-110">This topic discusses the general rules that are applied by Reporting Services.</span></span> <span data-ttu-id="053a7-111">如需詳細資訊，請參閱[轉譯報表項目 &#40;報表產生器及 SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md)、[轉譯資料區 &#40;報表產生器及 SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md) 和[轉譯資料 &#40;報表產生器及 SSRS&#41;](rendering-data-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="053a7-111">For more information, see [Rendering Report Items &#40;Report Builder and SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md), [Rendering Data Regions &#40;Report Builder and SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md), and [Rendering Data &#40;Report Builder and SSRS&#41;](rendering-data-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="general-behaviors-for-html-mhtml-word-and-excel-soft-page-break-renderers"></a><span data-ttu-id="053a7-112">適用於 HTML、MHTML、Word 與 Excel (軟分頁轉譯器) 的一般行為</span><span class="sxs-lookup"><span data-stu-id="053a7-112">General Behaviors for HTML, MHTML, Word, and Excel (Soft Page-Break Renderers)</span></span>  
 <span data-ttu-id="053a7-113">使用 HTML 和 MHTML 格式匯出的報表會針對各種長度的頁面，提供最佳的電腦螢幕檢視效果。</span><span class="sxs-lookup"><span data-stu-id="053a7-113">Reports exported using HTML and MHTML formats are optimized for a computer screen-based experience where pages can be various lengths.</span></span> <span data-ttu-id="053a7-114">分頁符號只會以垂直方式插入到報表主體內的約略位置。</span><span class="sxs-lookup"><span data-stu-id="053a7-114">Page breaks are inserted vertically only at approximate locations within the report body.</span></span> <span data-ttu-id="053a7-115">這些約略位置取決於 [屬性] 窗格中的互動式高度設定。</span><span class="sxs-lookup"><span data-stu-id="053a7-115">These approximate locations are determined by the interactive height setting in the Properties pane.</span></span> <span data-ttu-id="053a7-116">例如，假設互動式高度設定為 5 英吋。</span><span class="sxs-lookup"><span data-stu-id="053a7-116">For example, suppose the interactive height is set to 5 inches.</span></span> <span data-ttu-id="053a7-117">轉譯報表時，頁面高度的長度大約是 5 英吋。</span><span class="sxs-lookup"><span data-stu-id="053a7-117">When the report is rendered, the page height is approximately 5 inches in length.</span></span> <span data-ttu-id="053a7-118">Word 和 Excel 會根據邏輯分頁符號分頁，並忽略互動式高度設定。</span><span class="sxs-lookup"><span data-stu-id="053a7-118">Word and Excel paginate based on logical page breaks and ignore the interactive height setting.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="053a7-119">若要判定報表出現在軟分頁符號轉譯器的方式，請使用 [報表預覽]。</span><span class="sxs-lookup"><span data-stu-id="053a7-119">To determine how a report will appear in a soft page-break renderer, use Report Preview.</span></span> <span data-ttu-id="053a7-120">報表會 HTML、MHTML、Word 或 Excel 格式出現。</span><span class="sxs-lookup"><span data-stu-id="053a7-120">The report appears as it would in a HTML, MHTML, Word, or Excel format.</span></span>  
  
 <span data-ttu-id="053a7-121">將報表匯出為 HTML、MHTML、Word 或 Excel 時，會遵循下列一般規則進行：</span><span class="sxs-lookup"><span data-stu-id="053a7-121">When exporting a report to HTML, MHTML, Word, or Excel, the following general rules are followed:</span></span>  
  
-   <span data-ttu-id="053a7-122">系統會將您明確插入的分頁符號，也就是邏輯分頁符號，套用到報表項目中。</span><span class="sxs-lookup"><span data-stu-id="053a7-122">Logical page breaks, the page breaks that you explicitly insert, are applied to report items.</span></span> <span data-ttu-id="053a7-123">例如，如果您在每個群組之間插入分頁符號，則會在轉譯報表時套用這些分頁符號。</span><span class="sxs-lookup"><span data-stu-id="053a7-123">For example, if you insert a page break between each group, they are applied when the report is rendered.</span></span>  
  
-   <span data-ttu-id="053a7-124">系統會使用報表項目上顯示的頁面高度與次數來建立約略的版面配置。</span><span class="sxs-lookup"><span data-stu-id="053a7-124">An approximate layout is created using the page height and the number of times that the report item appears.</span></span> <span data-ttu-id="053a7-125">例如，如果文字方塊的高度為 .5 英吋，而且會在報表中重複 5 次，就會保留 2.5 英吋。</span><span class="sxs-lookup"><span data-stu-id="053a7-125">For example, if a text box is .5 inches in height and repeats five times in the report, 2.5 inches are reserved.</span></span>  
  
-   <span data-ttu-id="053a7-126">系統會根據互動式高度設定，插入多個軟分頁符號。</span><span class="sxs-lookup"><span data-stu-id="053a7-126">Multiple soft page breaks are inserted based on the interactive height setting.</span></span> <span data-ttu-id="053a7-127">若要在 HTML 和 ReportViewer 控制項中隱藏分頁符號，而且僅控制具有明確分頁符號的分頁，請將 [互動高度]  值設定為 0 或非常大的數字。</span><span class="sxs-lookup"><span data-stu-id="053a7-127">To suppress in HTML and the ReportViewer controls, and control pagination only with explicit page breaks, set the **interactive height** value to 0 or an extremely large number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="053a7-128">在軟分頁符號轉譯器中不會使用互動式寬度設定。</span><span class="sxs-lookup"><span data-stu-id="053a7-128">The interactive width setting is not used in the soft page break renderers.</span></span>  
  
-   <span data-ttu-id="053a7-129">報表頁面可以擴展以配合需要保持在一起的視窗、孤立項目以及報表項目。</span><span class="sxs-lookup"><span data-stu-id="053a7-129">Report pages can grow to accommodate widows, orphans and report items that need to be kept together.</span></span> <span data-ttu-id="053a7-130">也就是說，報表可以擴展到超出畫面寬度，而且可以使用滑動軸檢視。</span><span class="sxs-lookup"><span data-stu-id="053a7-130">This means that the report can extend beyond the screen width and can be viewed by using slider bars.</span></span>  
  
-   <span data-ttu-id="053a7-131">分頁只會以垂直方式套用到報表中。</span><span class="sxs-lookup"><span data-stu-id="053a7-131">Pagination is applied to reports vertically only.</span></span>  
  
-   <span data-ttu-id="053a7-132">系統不會套用頁面邊界。</span><span class="sxs-lookup"><span data-stu-id="053a7-132">Page margins are not applied.</span></span>  
  
## <a name="general-behaviors-for-pdf-image-and-print-hard-page-break-renderers"></a><span data-ttu-id="053a7-133">適用於 PDF、影像與列印 (手動分頁符號轉譯器) 的一般行為</span><span class="sxs-lookup"><span data-stu-id="053a7-133">General Behaviors for PDF, Image, and Print (Hard Page-Break Renderers)</span></span>  
 <span data-ttu-id="053a7-134">使用 PDF 和影像匯出的報表會針對大小一致的頁面，提供最佳的書籍或列印效果。</span><span class="sxs-lookup"><span data-stu-id="053a7-134">Reports exported using PDF and Image are optimized for a book-like or printed experience where pages are a consistent size.</span></span> <span data-ttu-id="053a7-135">分頁符號會以垂直和水平的方式插入到報表主體內的特定位置。</span><span class="sxs-lookup"><span data-stu-id="053a7-135">Page breaks are inserted vertically and horizontally at specific locations within the report body.</span></span> <span data-ttu-id="053a7-136">這些特定位置取決於頁面寬度與頁面高度設定。</span><span class="sxs-lookup"><span data-stu-id="053a7-136">These specific locations are determined by the page width and page height settings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="053a7-137">若要判定報表出現在手動分頁符號轉譯器的方式，請使用 [預覽列印]。</span><span class="sxs-lookup"><span data-stu-id="053a7-137">To determine how a report will appear in a hard page-break renderer, use Print Preview.</span></span> <span data-ttu-id="053a7-138">報表會 PDF 或影像格式出現。</span><span class="sxs-lookup"><span data-stu-id="053a7-138">The report appears as it would in a PDF or Image format.</span></span>  
  
-   <span data-ttu-id="053a7-139">頁面會先由左至右，再由上至下循序編號。</span><span class="sxs-lookup"><span data-stu-id="053a7-139">Pages are numbered sequentially from left to right, then top to bottom.</span></span>  
  
-   <span data-ttu-id="053a7-140">系統會將您明確插入的分頁符號，也就是邏輯分頁符號，套用到報表項目中。</span><span class="sxs-lookup"><span data-stu-id="053a7-140">Logical page breaks, the page breaks that you explicitly insert, are applied to report items.</span></span> <span data-ttu-id="053a7-141">這些分頁符號可能會使報表項目將其他項目推移到下一頁。</span><span class="sxs-lookup"><span data-stu-id="053a7-141">These page breaks can cause report items to push other items to the next page.</span></span>  
  
-   <span data-ttu-id="053a7-142">如果實體分頁符號穿過必須保持在一起的報表項目，必須保持在一起的項目就會移到下一頁。</span><span class="sxs-lookup"><span data-stu-id="053a7-142">If a physical page break occurs through report items that must be kept together, the items that must be kept together are moved to the next page.</span></span>  
  
-   <span data-ttu-id="053a7-143">由於頁面大小的限制，可能無法將所有項目保持在一起，也可能無法重複項目。</span><span class="sxs-lookup"><span data-stu-id="053a7-143">Because of page size constraints, it may not be possible to keep all the items together or to repeat items.</span></span> <span data-ttu-id="053a7-144">如果發生這個情況，轉譯器可能會忽略某些與其他項目重複的規則，才能讓報表項目容納在該頁面上。</span><span class="sxs-lookup"><span data-stu-id="053a7-144">If that occurs, the renderer might ignore certain rules for repeating with another item in order to allow the report item to fit on the page.</span></span>  
  
-   <span data-ttu-id="053a7-145">如果有項目無法保持在一起 (例如，因為擴展到太大而無法容納在垂直之可用頁面區域內的文字方塊)，則該項目將會在實體頁面界限遭到裁剪，而且繼續留到下一頁。</span><span class="sxs-lookup"><span data-stu-id="053a7-145">If an item cannot be kept together, for example a text box that grows too large to fit within the vertical usable page area, then the item will be clipped at the physical page boundary and will continue on the next page.</span></span>  
  
-   <span data-ttu-id="053a7-146">分頁會以垂直和水平的方式套用到報表中。</span><span class="sxs-lookup"><span data-stu-id="053a7-146">Pagination is applied to reports vertically and horizontally.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="053a7-147">在手動分頁符號轉譯器中不會使用互動式寬度設定。</span><span class="sxs-lookup"><span data-stu-id="053a7-147">The interactive width setting is not used in the hard page break renderers.</span></span>  
  
## <a name="minimum-spacing-between-report-items"></a><span data-ttu-id="053a7-148">報表項目間的最小間距</span><span class="sxs-lookup"><span data-stu-id="053a7-148">Minimum Spacing Between Report Items</span></span>  
 <span data-ttu-id="053a7-149">報表項目會在報表主體內擴展以容納其內容。</span><span class="sxs-lookup"><span data-stu-id="053a7-149">Report items grow within the report body to accommodate their contents.</span></span> <span data-ttu-id="053a7-150">例如，轉譯報表時，矩陣資料區域在頁面中通常會以橫向往下擴展，而且文字方塊的高度為隨著運算式所傳回的資料而調整。</span><span class="sxs-lookup"><span data-stu-id="053a7-150">For example, a matrix data region typically expands across and down the page when the report is rendered, and the height of a text box adjusts depending on the data returned from an expression.</span></span>  
  
 <span data-ttu-id="053a7-151">轉譯器會在報表配置中定義的報表項目之間維持最小的空間。</span><span class="sxs-lookup"><span data-stu-id="053a7-151">Renderers maintain the minimum space between report items that you define in the report layout.</span></span> <span data-ttu-id="053a7-152">當您在報表配置上，將某個報表項目放置在另一個報表項目旁邊時，報表項目間的距離會變成報表項目水平或垂直擴展時所必須維持的最小距離。</span><span class="sxs-lookup"><span data-stu-id="053a7-152">When you place a report item adjacent to another on the report layout, the distance between the report items becomes the minimum distance that must be maintained as the report grows horizontally or vertically.</span></span> <span data-ttu-id="053a7-153">例如，如果您在報表中加入矩陣資料區域，然後在矩陣右側加入矩形 .25 英吋，該空間就會隨著矩陣的擴展來維持。</span><span class="sxs-lookup"><span data-stu-id="053a7-153">For example, if you add a matrix data region to a report and then add a rectangle .25 inches to the right of the matrix, that space is maintained as the matrix grows.</span></span> <span data-ttu-id="053a7-154">每一個項目都會往右移動，以維持其本身與其左邊結束之項目之間的最小空間。</span><span class="sxs-lookup"><span data-stu-id="053a7-154">Each item moves to the right to maintain the minimum distance from items that end to the left of it.</span></span>  
  
## <a name="page-headers-and-footers"></a><span data-ttu-id="053a7-155">頁首和頁尾</span><span class="sxs-lookup"><span data-stu-id="053a7-155">Page Headers and Footers</span></span>  
 <span data-ttu-id="053a7-156">頁首和頁尾會出現在每個轉譯頁面的頂端和底部。</span><span class="sxs-lookup"><span data-stu-id="053a7-156">Page headers and footers appear at the top and bottom of each rendered page.</span></span> <span data-ttu-id="053a7-157">您可以設定頁首和頁尾的格式，讓其包含框線色彩、框線樣式，以及框線寬度。</span><span class="sxs-lookup"><span data-stu-id="053a7-157">You can format the page header and footer so that there is a border color, border style, and border width.</span></span> <span data-ttu-id="053a7-158">您也可以加入背景色彩或背景影像。</span><span class="sxs-lookup"><span data-stu-id="053a7-158">You can also add a background color or background image.</span></span> <span data-ttu-id="053a7-159">這些格式選項全部都會根據您選擇的格式進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="053a7-159">These formatting options are all rendered, depending on the format that you choose.</span></span>  
  
 <span data-ttu-id="053a7-160">以 HTML 或 MHTML 轉譯格式進行轉譯時，下列規則會套用到頁首和頁尾：</span><span class="sxs-lookup"><span data-stu-id="053a7-160">The following rules apply to page headers and footers when rendered in the HTML or MHTML rendering format:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="053a7-161">如需 Excel 如何轉譯頁首和頁尾的資訊，請參閱[匯出至 Microsoft Excel &#40;報表產生器及 SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="053a7-161">For information about how Excel renders headers and footers, see [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="053a7-162">如需 Word 如何轉譯頁首和頁尾的資訊，請參閱[匯出至 Microsoft Word &#40;報表產生器及 SSRS&#41;](../report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="053a7-162">For information about how Word renders headers and footers, see [Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="053a7-163">頁面出現時，在每頁頂端和底部的可用頁面區域內，會轉譯頁首和頁尾。</span><span class="sxs-lookup"><span data-stu-id="053a7-163">When present, the header and footer is rendered at the top and bottom of every page within the usable page area.</span></span>  
  
-   <span data-ttu-id="053a7-164">在隱藏頁首或頁尾的頁面上，即使沒有轉譯頁首或頁尾，仍然會在可用的頁面區域內保留頁首或頁尾的高度。</span><span class="sxs-lookup"><span data-stu-id="053a7-164">On pages where the header or footer is hidden, the height of the header or footer is still reserved within the usable page area, even though the header or footer is not rendered.</span></span>  
  
-   <span data-ttu-id="053a7-165">如果頁首或頁尾的內容擴展到超出頁首或頁尾的界限，頁首或頁尾的大小會增加來容納這些內容。</span><span class="sxs-lookup"><span data-stu-id="053a7-165">If the contents of the header or footer grows beyond the boundaries of the header or footer, the header or footer increases in size to accommodate the contents.</span></span>  
  
 <span data-ttu-id="053a7-166">以 PDF 或影像轉譯格式進行轉譯時，下列規則會套用到頁首和頁尾：</span><span class="sxs-lookup"><span data-stu-id="053a7-166">The following rules apply to page headers and footers when rendered in the PDF or Image rendering format:</span></span>  
  
-   <span data-ttu-id="053a7-167">在每頁頂端和底部的可用頁面區域內，會轉譯頁首或頁尾。</span><span class="sxs-lookup"><span data-stu-id="053a7-167">The header or footer is rendered at the top and bottom of every page within the usable page area.</span></span>  
  
-   <span data-ttu-id="053a7-168">在隱藏頁首或頁尾的頁面上，即使沒有轉譯頁首或頁尾，仍然會在可用的頁面區域內保留頁首或頁尾的高度。</span><span class="sxs-lookup"><span data-stu-id="053a7-168">On pages where the header or footer is hidden, the height of the header or footer is still reserved within the usable page area, even though the header or footer is not rendered.</span></span>  
  
-   <span data-ttu-id="053a7-169">頁首和頁尾不會擴展，也不會縮減。</span><span class="sxs-lookup"><span data-stu-id="053a7-169">The header and footer do not grow or shrink.</span></span> <span data-ttu-id="053a7-170">當您建立頁首或頁尾時，會以指定的高度，在每一頁上進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="053a7-170">They are rendered on every page at the height specified when you created the header or footer.</span></span>  
  
-   <span data-ttu-id="053a7-171">不管報表內的資料行數目有多少，每頁都只有一個頁首和頁尾。</span><span class="sxs-lookup"><span data-stu-id="053a7-171">Regardless of the number of columns within the report, there is only one header and footer per page.</span></span>  
  
-   <span data-ttu-id="053a7-172">如果頁首或頁尾的內容擴展到超出頁首或頁尾的界限，這些內容會遭到裁剪。</span><span class="sxs-lookup"><span data-stu-id="053a7-172">If the contents of the header or footer grow beyond the boundaries of the header or footer, the contents are clipped.</span></span>  
  
-   <span data-ttu-id="053a7-173">將報表轉譯為子報表時，不會轉譯在原始 RDL 檔案中所定義的頁首和頁尾。</span><span class="sxs-lookup"><span data-stu-id="053a7-173">Headers and footers that are defined in the original RDL file are not rendered when the report is rendered as a subreport.</span></span>  
  
## <a name="logical-page-breaks"></a><span data-ttu-id="053a7-174">邏輯分頁符號</span><span class="sxs-lookup"><span data-stu-id="053a7-174">Logical Page Breaks</span></span>  
 <span data-ttu-id="053a7-175">邏輯分頁符號是您在報表項目或群組前後插入的分頁符號。</span><span class="sxs-lookup"><span data-stu-id="053a7-175">Logical page breaks are page breaks that you insert before or after report items or groups.</span></span> <span data-ttu-id="053a7-176">轉譯或匯出報表時，分頁符號有助於決定如何將內容納入報表頁面，以獲得最佳的檢視效果。</span><span class="sxs-lookup"><span data-stu-id="053a7-176">Page breaks help to determine how the content is fitted to a report page for optimal viewing when rendering or exporting the report.</span></span>  
  
 <span data-ttu-id="053a7-177">轉譯邏輯分頁符號時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="053a7-177">The following rules apply when rendering logical page breaks:</span></span>  
  
-   <span data-ttu-id="053a7-178">對於持續隱藏的報表項目，以及透過按一下其他報表項目來控制可見性的報表項目，系統會忽略邏輯分頁符號。</span><span class="sxs-lookup"><span data-stu-id="053a7-178">Logical page breaks are ignored for report items that are constantly hidden and for report items where the visibility is controlled by clicking another report item.</span></span>  
  
-   <span data-ttu-id="053a7-179">如果目前在轉譯報表時可以看到邏輯分頁符號，就會有條件地在可見的項目上套用邏輯分頁符號。</span><span class="sxs-lookup"><span data-stu-id="053a7-179">Logical page breaks are applied on conditionally visible items if they are currently visible at the time the report is rendered.</span></span>  
  
-   <span data-ttu-id="053a7-180">系統會保留含有邏輯分頁符號之報表項目與其對等報表項目之間的空間。</span><span class="sxs-lookup"><span data-stu-id="053a7-180">Space is preserved between the report item with the logical page break and its peer report items.</span></span>  
  
-   <span data-ttu-id="053a7-181">在報表項目之前插入的邏輯分頁符號會將報表項目向下推送到下一頁。</span><span class="sxs-lookup"><span data-stu-id="053a7-181">Logical page breaks that are inserted before a report item push the report item down to the next page.</span></span> <span data-ttu-id="053a7-182">系統會在下一頁的頂端轉譯報表項目。</span><span class="sxs-lookup"><span data-stu-id="053a7-182">The report item is rendered at the top of the next page.</span></span>  
  
-   <span data-ttu-id="053a7-183">系統不會保留在資料表或矩陣資料格之項目上定義的邏輯分頁符號。</span><span class="sxs-lookup"><span data-stu-id="053a7-183">Logical page breaks defined on items in table or matrix cells are not kept.</span></span> <span data-ttu-id="053a7-184">這不適用於清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="053a7-184">This does not apply to items in lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="053a7-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="053a7-185">See Also</span></span>  
 <span data-ttu-id="053a7-186">[不同報表轉譯延伸模組的互動式功能 &#40;報表產生器及 SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="053a7-186">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="053a7-187">[轉譯為 HTML &#40;報表產生器及 SSRS&#41;](../report-builder/rendering-to-html-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="053a7-187">[Rendering to HTML &#40;Report Builder and SSRS&#41;](../report-builder/rendering-to-html-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="053a7-188">頁面配置和轉譯 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="053a7-188">Page Layout and Rendering &#40;Report Builder and SSRS&#41;</span></span>](page-layout-and-rendering-report-builder-and-ssrs.md)  
  
  
