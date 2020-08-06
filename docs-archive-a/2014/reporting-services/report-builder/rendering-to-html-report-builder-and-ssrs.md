---
title: 轉譯為 HTML (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf559b0a-499a-4d74-b520-b382b87e0b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 44f43d079aa81b566a39fe053bdf80c7800fc500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593322"
---
# <a name="rendering-to-html-report-builder-and-ssrs"></a><span data-ttu-id="7065f-102">轉譯為 HTML (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7065f-102">Rendering to HTML (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7065f-103">HTML 轉譯延伸模組會轉譯 HTML 格式的報表。</span><span class="sxs-lookup"><span data-stu-id="7065f-103">The HTML rendering extension renders a report in HTML format.</span></span> <span data-ttu-id="7065f-104">轉譯延伸模組也可產生完整的 HTML 頁面，或內嵌在其他 HTML 頁面中的 HTML 片段。</span><span class="sxs-lookup"><span data-stu-id="7065f-104">The rendering extension can also produce fully formed HTML pages or fragments of HTML to embed in other HTML pages.</span></span> <span data-ttu-id="7065f-105">所有 HTML 均以 UTF-8 編碼產生。</span><span class="sxs-lookup"><span data-stu-id="7065f-105">All HTML is generated with UTF-8 encoding.</span></span>  
  
 <span data-ttu-id="7065f-106">HTML 轉譯延伸模組是在瀏覽器中檢視之報表的預設轉譯延伸模組，包括在報表管理員中執行時。</span><span class="sxs-lookup"><span data-stu-id="7065f-106">The HTML rendering extension is the default rendering extension for reports that are viewed in a browser, including when run in Report Manager.</span></span>  
  
 <span data-ttu-id="7065f-107">HTML 轉譯延伸模組是在瀏覽器中檢視之報表的預設轉譯延伸模組，包括在報表管理員中執行時。</span><span class="sxs-lookup"><span data-stu-id="7065f-107">The HTML rendering extension is the default rendering extension for reports that are viewed in a browser, including when run in Report Manager.</span></span> <span data-ttu-id="7065f-108">HTML 轉譯延伸模組可以將 HTML 轉譯成片段，或完整的 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="7065f-108">The HTML rendering extension can render HTML as a fragment or as a full HTML document.</span></span> <span data-ttu-id="7065f-109">如果 HTML 是片段，則會移除 HTML 文件的 `HEAD`、`HTML` 和 `BODY` 標記。</span><span class="sxs-lookup"><span data-stu-id="7065f-109">If the HTML is a fragment, the `HEAD`, `HTML`, and `BODY` tags of the HTML document are removed.</span></span> <span data-ttu-id="7065f-110">系統只會轉譯 `BODY` 標記的內容。</span><span class="sxs-lookup"><span data-stu-id="7065f-110">Only the contents of the `BODY` tag are rendered.</span></span> <span data-ttu-id="7065f-111">這很適合用於將 HTML 內嵌於其他應用程式所產生的 HTML 中。</span><span class="sxs-lookup"><span data-stu-id="7065f-111">This is useful for embedding the HTML in the HTML produced by another application.</span></span>  
  
 <span data-ttu-id="7065f-112">在某些情況下，當報表轉譯為 HTML 時，報表參數可能會被用來發動指令碼資料隱碼攻擊。</span><span class="sxs-lookup"><span data-stu-id="7065f-112">In some scenarios, report parameters can be used to launch script injection attacks when rendering reports to HTML.</span></span> <span data-ttu-id="7065f-113">如需保護報表安全的詳細資訊，請參閱 [保護報表和資源的安全](../security/secure-reports-and-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="7065f-113">For more information about securing reports, see [Secure Reports and Resources](../security/secure-reports-and-resources.md).</span></span>  
  
 <span data-ttu-id="7065f-114">如需瀏覽器的詳細資訊，請參閱[規劃 Reporting Services 和 Power View 瀏覽器支援 &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7065f-114">For more information about browsers, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rendering-in-mhtml"></a><a name="RenderingMHTML"></a> <span data-ttu-id="7065f-115">在 MHTML 中轉譯</span><span class="sxs-lookup"><span data-stu-id="7065f-115">Rendering in MHTML</span></span>  
 <span data-ttu-id="7065f-116">HTML 轉譯延伸模組也可以在 MHTML (彙總 HTML 文件的 MIME 封裝) 中轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="7065f-116">The HTML rendering extension can also render reports in MHTML (MIME Encapsulation of Aggregate HTML Documents).</span></span> <span data-ttu-id="7065f-117">MHTML 擴充了 HTML，可以在 HTML 文件中內嵌編碼的物件，例如影像。</span><span class="sxs-lookup"><span data-stu-id="7065f-117">MHTML extends HTML to embed encoded objects, such as images, in the HTML document.</span></span> <span data-ttu-id="7065f-118">使用 MHTML 轉譯延伸模組時，您可以利用 MIME 結構，將影像、文件或其他二進位檔案等資源內嵌在單一檔案的報表 HTML 中。</span><span class="sxs-lookup"><span data-stu-id="7065f-118">Using the MHTML rendering extension, you can embed resources such as images, documents, or other binary files as MIME structures within the report HTML, into a single file.</span></span> <span data-ttu-id="7065f-119">MHTML 報表也適合用於內嵌在電子郵件訊息中，因為所有的資源都包含在報表中。</span><span class="sxs-lookup"><span data-stu-id="7065f-119">MHTML reports are also useful for embedding within e-mail messages because all resources are included with the report.</span></span> <span data-ttu-id="7065f-120">雖然實際上是 HTML 轉譯延伸模組轉譯 MHTML，此功能也可視為 MHTML 轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7065f-120">Although it is actually the HTML rendering extension that renders MHTML, this functionality may also be referred to as the MHTML rendering extension.</span></span>  
  
##  <a name="browser-support"></a><a name="BrowserSupport"></a><span data-ttu-id="7065f-121">瀏覽器支援</span><span class="sxs-lookup"><span data-stu-id="7065f-121">Browser Support</span></span>  
 <span data-ttu-id="7065f-122">此轉譯延伸模組支援下列瀏覽器版本：</span><span class="sxs-lookup"><span data-stu-id="7065f-122">This rendering extension supports the following browser versions:</span></span>  
  
-   <span data-ttu-id="7065f-123">Internet Explorer 5.5 及更新版本</span><span class="sxs-lookup"><span data-stu-id="7065f-123">Internet Explorer 5.5 and later</span></span>  
  
-   <span data-ttu-id="7065f-124">Firefox 1.5 及更新版本</span><span class="sxs-lookup"><span data-stu-id="7065f-124">Firefox 1.5 and later</span></span>  
  
-   <span data-ttu-id="7065f-125">Safari 3.0 及更新版本</span><span class="sxs-lookup"><span data-stu-id="7065f-125">Safari 3.0 and later</span></span>  
  
 <span data-ttu-id="7065f-126">由於跨瀏覽器的考量，轉譯的報表在不同的瀏覽器中可能略有不同。</span><span class="sxs-lookup"><span data-stu-id="7065f-126">Due to cross browser considerations, the rendered report may vary slightly from browser to browser.</span></span> <span data-ttu-id="7065f-127">例如，文字方塊包含稱為 WritingMode 的屬性。</span><span class="sxs-lookup"><span data-stu-id="7065f-127">For example, the text box contains a property called WritingMode.</span></span> <span data-ttu-id="7065f-128">Firefox 中不支援此屬性。</span><span class="sxs-lookup"><span data-stu-id="7065f-128">This property is not supported in Firefox.</span></span>  
  
##  <a name="html-specific-rendering-rules"></a><a name="HTMLSpecificRenderingRules"></a> <span data-ttu-id="7065f-129">HTML 特定的轉譯規則</span><span class="sxs-lookup"><span data-stu-id="7065f-129">HTML-Specific Rendering Rules</span></span>  
 <span data-ttu-id="7065f-130">下列 HTML 特定規則會在轉譯時套用：</span><span class="sxs-lookup"><span data-stu-id="7065f-130">The following HTML-specific rules are applied when rendering:</span></span>  
  
-   <span data-ttu-id="7065f-131">轉譯器會建立一個 HTML 資料表結構，以便在每個 `ReportItems` 集合 (如果有一個以上) 中包含所有項目。</span><span class="sxs-lookup"><span data-stu-id="7065f-131">The renderer builds an HTML table structure to contain all of the items in each `ReportItems` collection, if there is more than one.</span></span>  
  
-   <span data-ttu-id="7065f-132">資料表結構中的每個項目都會佔用一個單一的資料格。</span><span class="sxs-lookup"><span data-stu-id="7065f-132">Every item within the table structure occupies a single cell.</span></span>  
  
-   <span data-ttu-id="7065f-133">空的資料格會盡量摺疊在一起以減少 HTML 的大小。</span><span class="sxs-lookup"><span data-stu-id="7065f-133">Empty cells are collapsed together as much as possible to reduce the size of the HTML.</span></span>  
  
-   <span data-ttu-id="7065f-134">系統會將空白資料格的資料列加入到上邊緣，並將另一個資料行加入到左邊緣，就可以增進瀏覽器轉譯資料表的速度。</span><span class="sxs-lookup"><span data-stu-id="7065f-134">A row of empty cells is added to the top edge and another column to the left edge to improve the speed at which browsers can render the table.</span></span>  
  
-   <span data-ttu-id="7065f-135">不包含任何項目，只包含項目間之間距的資料表資料列或資料行，其寬度和高度是固定的。</span><span class="sxs-lookup"><span data-stu-id="7065f-135">Table rows or columns that contain no items, just gaps between items, are given fixed widths and heights.</span></span>  
  
-   <span data-ttu-id="7065f-136">其他所有資料列和資料行都可以根據每個報表項目的大小成長。</span><span class="sxs-lookup"><span data-stu-id="7065f-136">All other rows and columns are allowed to grow depending on the size of each report item.</span></span>  
  
-   <span data-ttu-id="7065f-137">所有座標和報表項目大小都會轉換為公釐。</span><span class="sxs-lookup"><span data-stu-id="7065f-137">All coordinates and report item sizes are converted to millimeters.</span></span> <span data-ttu-id="7065f-138">包括樣式屬性在內的其他所有大小則會保留其原始單位。</span><span class="sxs-lookup"><span data-stu-id="7065f-138">All other sizes, including style properties, retain their original units.</span></span> <span data-ttu-id="7065f-139">大小和位置的差異小於 .2 公釐時，則會視為 0 公釐。</span><span class="sxs-lookup"><span data-stu-id="7065f-139">Size and position differences smaller than .2mm are treated as 0mm.</span></span>  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="7065f-140">互動性</span><span class="sxs-lookup"><span data-stu-id="7065f-140">Interactivity</span></span>  
 <span data-ttu-id="7065f-141">HTML 中支援某些互動元素。</span><span class="sxs-lookup"><span data-stu-id="7065f-141">Some interactive elements are supported in HTML.</span></span> <span data-ttu-id="7065f-142">下列是特定行為的描述。</span><span class="sxs-lookup"><span data-stu-id="7065f-142">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="7065f-143">顯示與隱藏</span><span class="sxs-lookup"><span data-stu-id="7065f-143">Show and Hide</span></span>  
 <span data-ttu-id="7065f-144">可以切換其可見性的報表項目會以 +/- 切換影像轉譯，而且可以點按。</span><span class="sxs-lookup"><span data-stu-id="7065f-144">A report item whose visibility can be toggled is rendered with a +/- toggle image and is clickable.</span></span> <span data-ttu-id="7065f-145">按一下項目時，系統會回呼伺服器，才能利用已變更的顯示或隱藏狀態重新轉譯輸出。</span><span class="sxs-lookup"><span data-stu-id="7065f-145">When the item is clicked, a call back to the server takes place in order to re-render the output with the changed show or hide state.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="7065f-146">文件引導模式</span><span class="sxs-lookup"><span data-stu-id="7065f-146">Document Map</span></span>  
 <span data-ttu-id="7065f-147">文件引導模式標籤可以轉譯，而且可以使用檢視器控制項中的文件引導模式來導覽。</span><span class="sxs-lookup"><span data-stu-id="7065f-147">Document map labels are rendered and can be navigated to by using the document map in the viewer control.</span></span> <span data-ttu-id="7065f-148">若是省略的資料區域標頭，就會在第一個子資料格上轉譯標籤。</span><span class="sxs-lookup"><span data-stu-id="7065f-148">For omitted data region headers, labels are rendered on the first child cell.</span></span> <span data-ttu-id="7065f-149">如果沒有顯示任何子資料格，則會在第一個子資料格前的子系上轉譯標籤。</span><span class="sxs-lookup"><span data-stu-id="7065f-149">If there is no child cell present, the label is rendered on the child that precedes it.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="7065f-150">書籤</span><span class="sxs-lookup"><span data-stu-id="7065f-150">Bookmarks</span></span>  
 <span data-ttu-id="7065f-151">系統會轉譯書籤連結並顯示為超連結。</span><span class="sxs-lookup"><span data-stu-id="7065f-151">Bookmark links are rendered and appear as hyperlinks.</span></span> <span data-ttu-id="7065f-152">同時，系統會轉譯書籤目標，而且按一下書籤連結就可以導覽。</span><span class="sxs-lookup"><span data-stu-id="7065f-152">Bookmark targets are rendered and can be navigated to by clicking the bookmark links.</span></span> <span data-ttu-id="7065f-153">按一下書籤連結時，報表會移到第一個出現的目標書籤標籤，而且，如果可能，瀏覽器會捲動，讓書籤連結位於視窗最上方。</span><span class="sxs-lookup"><span data-stu-id="7065f-153">When a bookmark link is clicked, the report goes to the first occurrence of the target bookmark label and, when possible, the browser is scrolled so that the bookmark link is at the top of the window.</span></span> <span data-ttu-id="7065f-154">HTML 錨點 (\<a>) 標記用來標示書簽目標。</span><span class="sxs-lookup"><span data-stu-id="7065f-154">HTML anchor (\<a>) tags are used to mark bookmark targets.</span></span>  
  
### <a name="interactive-sorting"></a><span data-ttu-id="7065f-155">互動式排序</span><span class="sxs-lookup"><span data-stu-id="7065f-155">Interactive Sorting</span></span>  
 <span data-ttu-id="7065f-156">如果文字方塊中已定義使用者排序，HTML 轉譯延伸模組會將文字方塊中的排序圖示轉譯到其內容的右側。</span><span class="sxs-lookup"><span data-stu-id="7065f-156">If a text box has user sort defined, the HTML rendering extension renders the sort icons in the text box to the right of its contents.</span></span> <span data-ttu-id="7065f-157">如果報表內含其中已定義使用者排序的任何文字方塊，按一下排序影像時，會轉譯導致回傳至伺服器的 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="7065f-157">If a report contains any text box where user sort is defined, JavaScript is rendered that causes a postback to the server when the sort image is clicked.</span></span>  
  
### <a name="hyperlinks-and-drillthrough"></a><span data-ttu-id="7065f-158">超連結與鑽研</span><span class="sxs-lookup"><span data-stu-id="7065f-158">Hyperlinks and Drillthrough</span></span>  
 <span data-ttu-id="7065f-159">超連結和鑽取連結會使用 HTML 錨點轉譯為報表專案上的超連結， (在其 \<a> 定義所在的專案周圍) 標記。</span><span class="sxs-lookup"><span data-stu-id="7065f-159">Hyperlinks and drillthrough links are rendered as hyperlinks on report items using the HTML anchor (\<a>) tags around the item on which they are defined.</span></span>  
  
### <a name="search"></a><span data-ttu-id="7065f-160">搜尋</span><span class="sxs-lookup"><span data-stu-id="7065f-160">Search</span></span>  
 <span data-ttu-id="7065f-161">[搜尋] 功能可讓使用者在報表內搜尋文字的字串。</span><span class="sxs-lookup"><span data-stu-id="7065f-161">The Search feature allows users to search for a string of text within the report.</span></span>  
  
 <span data-ttu-id="7065f-162">其他搜尋和尋找功能是由 ReportViewer Web 表單控制項提供。</span><span class="sxs-lookup"><span data-stu-id="7065f-162">Additional search and find functionality is provided by the ReportViewer Web Forms control.</span></span>  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="7065f-163">裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="7065f-163">Device Information Settings</span></span>  
 <span data-ttu-id="7065f-164">您可以變更此轉譯器的某些預設值，包括要在哪個模式下轉譯，方法是，變更裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="7065f-164">You can change some default settings for this renderer, including which mode to render in, by changing the device information settings.</span></span> <span data-ttu-id="7065f-165">如需相關資訊，請參閱 [HTML Device Information Settings](../html-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="7065f-165">For more information, see [HTML Device Information Settings](../html-device-information-settings.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="7065f-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7065f-166">See Also</span></span>  
 <span data-ttu-id="7065f-167">[Reporting Services &#40;報表產生器和 SSRS 中的分頁&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7065f-167">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7065f-168">[轉譯行為 &#40;報表產生器和 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7065f-168">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7065f-169">[不同報表轉譯延伸模組的互動式功能 &#40;報表產生器和 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="7065f-169">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="7065f-170">[&#40;報表產生器和 SSRS 轉譯報表專案&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7065f-170">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7065f-171">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7065f-171">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
