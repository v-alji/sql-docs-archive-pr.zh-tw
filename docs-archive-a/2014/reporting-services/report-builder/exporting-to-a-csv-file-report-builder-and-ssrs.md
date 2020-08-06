---
title: 匯出至 CSV 檔案 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 68ec746e-8c82-47f5-8c3d-dbe403a441e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 635d5904acf6e616378f5423bfbaf4cf5390fa9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585107"
---
# <a name="exporting-to-a-csv-file-report-builder-and-ssrs"></a><span data-ttu-id="7d98e-102">匯出至 CSV 檔案 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7d98e-102">Exporting to a CSV File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7d98e-103">逗號分隔值 (CSV) 轉譯延伸模組會將報表從多數應用程式都可輕易讀取與交換的標準化純文字格式報表，轉譯為扁平化表示的資料。</span><span class="sxs-lookup"><span data-stu-id="7d98e-103">The Comma-Separated Value (CSV) rendering extension renders reports as a flattened representation of data from a report in a standardized, plain-text format that is easily readable and exchangeable with many applications.</span></span>  
  
 <span data-ttu-id="7d98e-104">CSV 轉譯延伸模組使用字串字元分隔符號來分隔欄位和資料列，可將此字串字元分隔符號設定為非逗號字元。</span><span class="sxs-lookup"><span data-stu-id="7d98e-104">The CSV rendering extension uses a string character delimiter to separate fields and rows, with the string character delimiter configurable to be a character other than a comma.</span></span> <span data-ttu-id="7d98e-105">所產生的檔案可以使用試算表程式 (例如 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ) 開啟，或當做其他程式的匯入格式使用。</span><span class="sxs-lookup"><span data-stu-id="7d98e-105">The resulting file can be opened in a spreadsheet program like [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] or used as an import format for other programs.</span></span> <span data-ttu-id="7d98e-106">匯出的報表會變成 .csv 檔案，並傳回 MIME 類型的 `text/csv`。</span><span class="sxs-lookup"><span data-stu-id="7d98e-106">The exported report becomes a .csv file, and returns a MIME type of `text/csv`.</span></span>  
  
 <span data-ttu-id="7d98e-107">如果您要使用與 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]中的圖表、資料橫條、走勢圖、量測計和指標相關的資料，請將報表匯出為 CSV 檔，然後在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="7d98e-107">If you want to work with data related to charts, data bars, sparklines, gauges, and indicators in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)], export the report to a CSV file, and then open the file in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="csv-rendering"></a><a name="CSVRendering"></a><span data-ttu-id="7d98e-108">CSV 轉譯</span><span class="sxs-lookup"><span data-stu-id="7d98e-108">CSV Rendering</span></span>  
 <span data-ttu-id="7d98e-109">使用預設值轉譯時，CSV 報表會具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="7d98e-109">When rendered using the default settings, a CSV report has the following characteristics:</span></span>  
  
-   <span data-ttu-id="7d98e-110">預設的欄位分隔符號字串是逗號 (,)。</span><span class="sxs-lookup"><span data-stu-id="7d98e-110">The default field delimiter string is a comma (,).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7d98e-111">您可以藉由變更裝置資訊設定的方式，將欄位分隔符號變更為所需的任何字元，包括 TAB。</span><span class="sxs-lookup"><span data-stu-id="7d98e-111">You can change the field delimiter to any character that you want, including TAB, by changing the device information settings.</span></span> <span data-ttu-id="7d98e-112">如需詳細資訊，請參閱 [CSV Device Information Settings](../csv-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="7d98e-112">For more information, see [CSV Device Information Settings](../csv-device-information-settings.md).</span></span>  
  
-   <span data-ttu-id="7d98e-113">記錄分隔符號字串是) 的回車和換行 (\<cr> \<lf> 。</span><span class="sxs-lookup"><span data-stu-id="7d98e-113">The record delimiter string is the carriage return and line feed (\<cr>\<lf>).</span></span>  
  
-   <span data-ttu-id="7d98e-114">文字限定詞字串是引號 (")。</span><span class="sxs-lookup"><span data-stu-id="7d98e-114">The text qualifier string is a quotation mark (").</span></span>  
  
     <span data-ttu-id="7d98e-115">CSV 轉譯器不會在所有文字字串周圍加上限定詞。</span><span class="sxs-lookup"><span data-stu-id="7d98e-115">The CSV renderer does not add qualifiers around all text strings.</span></span> <span data-ttu-id="7d98e-116">只有在值包含分隔符號字元時，或值擁有分行符號時，才會加上文字限定詞。</span><span class="sxs-lookup"><span data-stu-id="7d98e-116">Text qualifiers are added only when the value contains the delimiter character or when the value has a line break.</span></span>  
  
-   <span data-ttu-id="7d98e-117">如果文字包含內嵌的分隔符號字串或限定詞字串，則文字限定詞是放置於該文字周圍，且內嵌的限定詞字串是重複的。</span><span class="sxs-lookup"><span data-stu-id="7d98e-117">If the text contains an embedded delimiter string or qualifier string, the text qualifier is placed around the text, and the embedded qualifier strings are doubled.</span></span>  
  
-   <span data-ttu-id="7d98e-118">忽略格式和配置。</span><span class="sxs-lookup"><span data-stu-id="7d98e-118">Formatting and layout are ignored.</span></span>  
  
 <span data-ttu-id="7d98e-119">下列項目會在轉譯過程中忽略：</span><span class="sxs-lookup"><span data-stu-id="7d98e-119">The following items are ignored during rendering:</span></span>  
  
-   <span data-ttu-id="7d98e-120">頁首</span><span class="sxs-lookup"><span data-stu-id="7d98e-120">Page header</span></span>  
  
-   <span data-ttu-id="7d98e-121">頁尾</span><span class="sxs-lookup"><span data-stu-id="7d98e-121">Page footer</span></span>  
  
-   <span data-ttu-id="7d98e-122">自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="7d98e-122">Custom report items</span></span>  
  
-   <span data-ttu-id="7d98e-123">線</span><span class="sxs-lookup"><span data-stu-id="7d98e-123">Line</span></span>  
  
-   <span data-ttu-id="7d98e-124">映像</span><span class="sxs-lookup"><span data-stu-id="7d98e-124">Image</span></span>  
  
-   <span data-ttu-id="7d98e-125">矩形</span><span class="sxs-lookup"><span data-stu-id="7d98e-125">Rectangle</span></span>  
  
-   <span data-ttu-id="7d98e-126">自動小計</span><span class="sxs-lookup"><span data-stu-id="7d98e-126">Automatic subtotals</span></span>  
  
 <span data-ttu-id="7d98e-127">剩餘的報表項目會先由上至下，再由左至右排序。</span><span class="sxs-lookup"><span data-stu-id="7d98e-127">The remaining report items are sorted, from top to bottom, then left to right.</span></span> <span data-ttu-id="7d98e-128">接著，每個項目會轉譯成資料行。</span><span class="sxs-lookup"><span data-stu-id="7d98e-128">Each item is then rendered to a column.</span></span> <span data-ttu-id="7d98e-129">如果報表有巢狀資料項目 (例如，清單或資料表)，則父項目會在每一筆記錄中重複。</span><span class="sxs-lookup"><span data-stu-id="7d98e-129">If the report has nested data items like lists or tables, the parent items are repeated in each record.</span></span>  
  
 <span data-ttu-id="7d98e-130">下表指出報表項目轉譯時的外觀：</span><span class="sxs-lookup"><span data-stu-id="7d98e-130">The following table indicates the appearance of report items when rendered:</span></span>  
  
|<span data-ttu-id="7d98e-131">項目</span><span class="sxs-lookup"><span data-stu-id="7d98e-131">Item</span></span>|<span data-ttu-id="7d98e-132">轉譯行為</span><span class="sxs-lookup"><span data-stu-id="7d98e-132">Rendering behavior</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="7d98e-133">文字方塊</span><span class="sxs-lookup"><span data-stu-id="7d98e-133">Text box</span></span>|<span data-ttu-id="7d98e-134">轉譯文字方塊的內容。</span><span class="sxs-lookup"><span data-stu-id="7d98e-134">Renders the contents of the text box.</span></span> <span data-ttu-id="7d98e-135">在預設模式下，系統會根據項目的格式化屬性來設定項目的格式。</span><span class="sxs-lookup"><span data-stu-id="7d98e-135">In default mode, items are formatted based on the item's formatting properties.</span></span> <span data-ttu-id="7d98e-136">在相容模式下，格式可以依據裝置資訊設定來變更。</span><span class="sxs-lookup"><span data-stu-id="7d98e-136">In compliant mode, formatting can be changed by device information settings.</span></span> <span data-ttu-id="7d98e-137">如需有關 CSV 轉譯模式的詳細資訊，請參閱以下。</span><span class="sxs-lookup"><span data-stu-id="7d98e-137">For more information about CSV rendering modes, see below.</span></span>|  
|<span data-ttu-id="7d98e-138">資料表</span><span class="sxs-lookup"><span data-stu-id="7d98e-138">Table</span></span>|<span data-ttu-id="7d98e-139">藉由展開資料表，並為每個資料列與資料行以最低層級的詳細資料建立資料列與資料行，來進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="7d98e-139">Renders by expanding the table and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="7d98e-140">小計資料列和資料行沒有資料行或資料列標題。</span><span class="sxs-lookup"><span data-stu-id="7d98e-140">Subtotal rows and columns do not have column or row headings.</span></span> <span data-ttu-id="7d98e-141">不支援鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="7d98e-141">Drillthrough reports are not supported.</span></span>|  
|<span data-ttu-id="7d98e-142">Matrix</span><span class="sxs-lookup"><span data-stu-id="7d98e-142">Matrix</span></span>|<span data-ttu-id="7d98e-143">藉由展開矩陣，並為每個資料列與資料行以最低層級的詳細資料建立資料列與資料行，來進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="7d98e-143">Renders by expanding the matrix and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="7d98e-144">小計資料列和資料行沒有資料行或資料列標題。</span><span class="sxs-lookup"><span data-stu-id="7d98e-144">Subtotal rows and columns do not have column or row headings.</span></span>|  
|<span data-ttu-id="7d98e-145">清單</span><span class="sxs-lookup"><span data-stu-id="7d98e-145">List</span></span>|<span data-ttu-id="7d98e-146">轉譯每個詳細資料列或清單中執行個體的記錄。</span><span class="sxs-lookup"><span data-stu-id="7d98e-146">Renders a record for each detail row or instance in the list.</span></span>|  
|<span data-ttu-id="7d98e-147">子報表</span><span class="sxs-lookup"><span data-stu-id="7d98e-147">Subreport</span></span>|<span data-ttu-id="7d98e-148">內容的每個執行個體都會重複父項目。</span><span class="sxs-lookup"><span data-stu-id="7d98e-148">The parent item is repeated for each instance of the contents.</span></span>|  
|<span data-ttu-id="7d98e-149">圖表</span><span class="sxs-lookup"><span data-stu-id="7d98e-149">Chart</span></span>|<span data-ttu-id="7d98e-150">針對每個圖表值和成員標籤建立資料列以進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="7d98e-150">Renders by creating a row for each chart value and member labels.</span></span> <span data-ttu-id="7d98e-151">階層中數列和類別目錄的標籤會扁平化，並且包含在圖表值的資料列中。</span><span class="sxs-lookup"><span data-stu-id="7d98e-151">Labels from series and categories in hierarchies are flattened and included in the row for a chart value.</span></span>|  
|<span data-ttu-id="7d98e-152">資料橫條</span><span class="sxs-lookup"><span data-stu-id="7d98e-152">Data bar</span></span>|<span data-ttu-id="7d98e-153">像圖表一樣轉譯。</span><span class="sxs-lookup"><span data-stu-id="7d98e-153">Renders like a chart.</span></span> <span data-ttu-id="7d98e-154">資料橫條通常不包含階層或標籤。</span><span class="sxs-lookup"><span data-stu-id="7d98e-154">Typically, a data bar does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="7d98e-155">走勢圖</span><span class="sxs-lookup"><span data-stu-id="7d98e-155">Sparkline</span></span>|<span data-ttu-id="7d98e-156">像圖表一樣轉譯。</span><span class="sxs-lookup"><span data-stu-id="7d98e-156">Renders like a chart.</span></span> <span data-ttu-id="7d98e-157">走勢圖通常不包含階層或標籤。</span><span class="sxs-lookup"><span data-stu-id="7d98e-157">Typically, a sparkline does not  do not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="7d98e-158">量測計</span><span class="sxs-lookup"><span data-stu-id="7d98e-158">Gauge</span></span>|<span data-ttu-id="7d98e-159">轉譯為包含線性標尺的最小與最大值、範圍的開始與結束值，以及指標值的單一記錄。</span><span class="sxs-lookup"><span data-stu-id="7d98e-159">Renders as a single record with the minimum and maximum values of the linear scale, start and end values of the range, and the value of the pointer.</span></span>|  
|<span data-ttu-id="7d98e-160">指標</span><span class="sxs-lookup"><span data-stu-id="7d98e-160">Indicator</span></span>|<span data-ttu-id="7d98e-161">以作用中的狀態名稱、可用的狀態以及資料值轉譯成單一記錄。</span><span class="sxs-lookup"><span data-stu-id="7d98e-161">Renders as a single record with the active state name, available states, and the data value.</span></span>|  
|<span data-ttu-id="7d98e-162">對應</span><span class="sxs-lookup"><span data-stu-id="7d98e-162">Map</span></span>|<span data-ttu-id="7d98e-163">轉譯資料列，其中包含地圖圖層之每一個地圖成員的標籤和值。</span><span class="sxs-lookup"><span data-stu-id="7d98e-163">Renders a row with the labels and values for each map member of a map layer.</span></span><br /><br /> <span data-ttu-id="7d98e-164">如果地圖有多個圖層，則資料列中的值會根據地圖圖層是使用相同或不同的地圖資料區域而有所不同。</span><span class="sxs-lookup"><span data-stu-id="7d98e-164">If the map has multiple layers the values in the rows varies depending on whether the map layers use the same or different map data regions.</span></span> <span data-ttu-id="7d98e-165">如果多個地圖圖層使用相同的資料區域，則資料列會包含所有圖層中的資料。</span><span class="sxs-lookup"><span data-stu-id="7d98e-165">If multiple map layers use the same data region, the rows contain data from all layers.</span></span>|  
  
### <a name="hierarchical-and-grouped-data"></a><span data-ttu-id="7d98e-166">階層與群組資料</span><span class="sxs-lookup"><span data-stu-id="7d98e-166">Hierarchical and Grouped Data</span></span>  
 <span data-ttu-id="7d98e-167">階層與群組資料必須扁平化，才能以 CSV 格式表示。</span><span class="sxs-lookup"><span data-stu-id="7d98e-167">Hierarchical and grouped data must be flattened in order to be represented in the CSV format.</span></span>  
  
 <span data-ttu-id="7d98e-168">轉譯延伸模組會將報表扁平化為樹狀結構，可表示資料區域內的巢狀群組。</span><span class="sxs-lookup"><span data-stu-id="7d98e-168">The rendering extension flattens the report into a tree structure that represents the nested groups within the data region.</span></span> <span data-ttu-id="7d98e-169">若要將報表扁平化：</span><span class="sxs-lookup"><span data-stu-id="7d98e-169">To flatten the report:</span></span>  
  
-   <span data-ttu-id="7d98e-170">資料列階層要在資料行階層之前扁平化。</span><span class="sxs-lookup"><span data-stu-id="7d98e-170">A row hierarchy is flattened before a column hierarchy.</span></span>  
  
-   <span data-ttu-id="7d98e-171">資料行的排列順序如下：文字方塊在主體順序中為由左至右、由上至下，後面接著以由左至右、由上至下排列的資料區域。</span><span class="sxs-lookup"><span data-stu-id="7d98e-171">Columns are ordered as follows: text boxes in body order left-to-right, top-to-bottom followed by data regions ordered left-to-right, top-to-bottom.</span></span>  
  
-   <span data-ttu-id="7d98e-172">在資料區域中，資料行的排列順序如下：邊角成員、資料列階層成員、資料行階層成員，然後是資料格。</span><span class="sxs-lookup"><span data-stu-id="7d98e-172">Within a data region, the columns are ordered as follows: corner members, row hierarchy members, column hierarchy members, and then cells.</span></span>  
  
-   <span data-ttu-id="7d98e-173">對等資料區域是一種資料區域或動態群組，可以共用一般資料區域或動態上階。</span><span class="sxs-lookup"><span data-stu-id="7d98e-173">Peer data regions are data regions or dynamic groups that share a common data region or dynamic ancestor.</span></span> <span data-ttu-id="7d98e-174">對等資料會以扁平化樹狀結構的分支識別。</span><span class="sxs-lookup"><span data-stu-id="7d98e-174">Peer data is identified by branching of the flattened tree.</span></span>  
  
 <span data-ttu-id="7d98e-175">如需詳細資訊，請參閱 [資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7d98e-175">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="renderer-modes"></a><a name="RenderingModes"></a> <span data-ttu-id="7d98e-176">轉譯器模式</span><span class="sxs-lookup"><span data-stu-id="7d98e-176">Renderer Modes</span></span>  
 <span data-ttu-id="7d98e-177">CSV 轉譯延伸模組可以在兩種模式下操作：一種會針對 Excel 最佳化，而另一種則會針對需要 CSV 嚴格遵循 RFC 4180 中 CSV 合規性的協力廠商應用程式最佳化。</span><span class="sxs-lookup"><span data-stu-id="7d98e-177">The CSV rendering extension can operate in two modes: one is optimized for Excel and the other is optimized for third-party applications that require strict CSV compliance to the CSV specification in RFC 4180.</span></span> <span data-ttu-id="7d98e-178">根據所使用的模式，對等資料區域的處理方式也會不同。</span><span class="sxs-lookup"><span data-stu-id="7d98e-178">Depending on which mode you use, peer data regions are handled differently.</span></span>  
  
### <a name="default-mode"></a><span data-ttu-id="7d98e-179">預設模式</span><span class="sxs-lookup"><span data-stu-id="7d98e-179">Default Mode</span></span>  
 <span data-ttu-id="7d98e-180">預設模式會針對 Excel 最佳化。</span><span class="sxs-lookup"><span data-stu-id="7d98e-180">The default mode is optimized for Excel.</span></span> <span data-ttu-id="7d98e-181">以預設模式進行轉譯時，報表會轉譯為包含多個 CSV 轉譯資料區塊的 CSV 檔。</span><span class="sxs-lookup"><span data-stu-id="7d98e-181">When rendered in default mode, the report is rendered as a CSV file with multiple sections of CSV-rendered data.</span></span> <span data-ttu-id="7d98e-182">每個對等區域都會以一個空行分隔。</span><span class="sxs-lookup"><span data-stu-id="7d98e-182">Each peer data region is delimited by an empty line.</span></span> <span data-ttu-id="7d98e-183">報表主體內的對等資料區域在 CSV 檔中，會轉譯為個別的資料區塊。</span><span class="sxs-lookup"><span data-stu-id="7d98e-183">Peer data regions within the report body are rendered as separate blocks of data within the CSV file.</span></span> <span data-ttu-id="7d98e-184">結果是 CSV 檔，而其中：</span><span class="sxs-lookup"><span data-stu-id="7d98e-184">The result is a CSV file in which:</span></span>  
  
-   <span data-ttu-id="7d98e-185">報表主體內的各個文字方塊在 CSV 檔中會轉譯一次，而且會轉譯為第一個資料區塊。</span><span class="sxs-lookup"><span data-stu-id="7d98e-185">Individual text boxes within the report body are rendered once as the first block of data within the CSV file.</span></span>  
  
-   <span data-ttu-id="7d98e-186">報表主體中的每個最上層對等資料區域都會在自己的資料區塊中進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="7d98e-186">Each top-level peer data region in the report body is rendered in its own data block.</span></span>  
  
-   <span data-ttu-id="7d98e-187">巢狀資料區域會以對角方式轉譯為相同的資料區塊。</span><span class="sxs-lookup"><span data-stu-id="7d98e-187">Nested data regions are rendered diagonally into the same data block.</span></span>  
  
#### <a name="formatting"></a><span data-ttu-id="7d98e-188">格式化</span><span class="sxs-lookup"><span data-stu-id="7d98e-188">Formatting</span></span>  
 <span data-ttu-id="7d98e-189">數值會利用其格式化的狀態進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="7d98e-189">Numeric values are rendered in their formatted state.</span></span> <span data-ttu-id="7d98e-190">Excel 可以識別格式化的數值，例如，貨幣、百分比與日期，並在匯入 CSV 檔時，適當地格式化資料格。</span><span class="sxs-lookup"><span data-stu-id="7d98e-190">Excel can recognize formatted numeric values, such as currency, percentage and date, and format the cells appropriately when importing the CSV file.</span></span>  
  
### <a name="compliant-mode"></a><span data-ttu-id="7d98e-191">相容模式</span><span class="sxs-lookup"><span data-stu-id="7d98e-191">Compliant Mode</span></span>  
 <span data-ttu-id="7d98e-192">相容模式會針對協力廠商應用程式最佳化。</span><span class="sxs-lookup"><span data-stu-id="7d98e-192">Compliant mode is optimized for third-party applications.</span></span>  
  
#### <a name="data-regions"></a><span data-ttu-id="7d98e-193">資料區域</span><span class="sxs-lookup"><span data-stu-id="7d98e-193">Data Regions</span></span>  
 <span data-ttu-id="7d98e-194">只有檔案的第一個資料列包含資料行標頭，而且每個資料列都有相同數目的資料行。</span><span class="sxs-lookup"><span data-stu-id="7d98e-194">Only the first row of the file contains the column headers and each row has the same number of columns.</span></span>  
  
#### <a name="formatting"></a><span data-ttu-id="7d98e-195">格式化</span><span class="sxs-lookup"><span data-stu-id="7d98e-195">Formatting</span></span>  
 <span data-ttu-id="7d98e-196">這些值沒有格式化。</span><span class="sxs-lookup"><span data-stu-id="7d98e-196">Values are unformatted.</span></span>  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="7d98e-197">互動性</span><span class="sxs-lookup"><span data-stu-id="7d98e-197">Interactivity</span></span>  
 <span data-ttu-id="7d98e-198">此轉譯器產生的任一種 CSV 格式都不支援互動性。</span><span class="sxs-lookup"><span data-stu-id="7d98e-198">Interactivity is not supported by either CSV formats generated by this renderer.</span></span> <span data-ttu-id="7d98e-199">系統不會轉譯下列互動項目：</span><span class="sxs-lookup"><span data-stu-id="7d98e-199">The following interactive elements are not rendered:</span></span>  
  
-   <span data-ttu-id="7d98e-200">超連結</span><span class="sxs-lookup"><span data-stu-id="7d98e-200">Hyperlinks</span></span>  
  
-   <span data-ttu-id="7d98e-201">顯示或隱藏</span><span class="sxs-lookup"><span data-stu-id="7d98e-201">Show or Hide</span></span>  
  
-   <span data-ttu-id="7d98e-202">文件引導模式</span><span class="sxs-lookup"><span data-stu-id="7d98e-202">Document Map</span></span>  
  
-   <span data-ttu-id="7d98e-203">鑽研或點選連結的連結</span><span class="sxs-lookup"><span data-stu-id="7d98e-203">Drillthrough or clickthrough links</span></span>  
  
-   <span data-ttu-id="7d98e-204">使用者排序</span><span class="sxs-lookup"><span data-stu-id="7d98e-204">End user sort</span></span>  
  
-   <span data-ttu-id="7d98e-205">固定頁首</span><span class="sxs-lookup"><span data-stu-id="7d98e-205">Fixes headers</span></span>  
  
-   <span data-ttu-id="7d98e-206">書籤</span><span class="sxs-lookup"><span data-stu-id="7d98e-206">Bookmarks</span></span>  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="7d98e-207">裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="7d98e-207">Device Information Settings</span></span>  
 <span data-ttu-id="7d98e-208">您可以變更此轉譯器的某些預設值，包括要在哪個模式下進行轉譯、要使用哪些字元當做分隔符號，以及要使用哪些字元當做文字限定詞的預設字串，只要變更裝置資訊設定即可。</span><span class="sxs-lookup"><span data-stu-id="7d98e-208">You can change some default settings for this renderer, including which mode to render in, which characters to use as delimiters and which characters to use as the text qualifier default string, by changing the device information settings.</span></span> <span data-ttu-id="7d98e-209">如需詳細資訊，請參閱 [CSV Device Information Settings](../csv-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="7d98e-209">For more information, see [CSV Device Information Settings](../csv-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="7d98e-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d98e-210">See Also</span></span>  
 <span data-ttu-id="7d98e-211">[Reporting Services &#40;報表產生器和 SSRS 中的分頁&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d98e-211">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d98e-212">[轉譯行為 &#40;報表產生器和 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d98e-212">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d98e-213">[不同報表轉譯延伸模組的互動式功能 &#40;報表產生器和 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="7d98e-213">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="7d98e-214">[&#40;報表產生器和 SSRS 轉譯報表專案&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d98e-214">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7d98e-215">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7d98e-215">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
