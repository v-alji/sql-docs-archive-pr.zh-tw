---
title: 匯出至 PDF 檔案 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f22497b7-f6c1-4c7b-b831-8c731e26ae37
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b4a324ad40d01d302196fe40ffb4232deb62a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585105"
---
# <a name="exporting-to-a-pdf-file-report-builder-and-ssrs"></a><span data-ttu-id="46e7f-102">匯出至 PDF 檔案 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="46e7f-102">Exporting to a PDF File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="46e7f-103">PDF 轉譯延伸模組會將報表轉譯成可在 Adobe Acrobat 與支援 PDF 1.3 之其他協力廠商 PDF 檢視器中開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="46e7f-103">The PDF rendering extension renders a report to files that can be opened in Adobe Acrobat and other third-party PDF viewers that support PDF 1.3.</span></span> <span data-ttu-id="46e7f-104">雖然 PDF 1.3 與 Adobe Acrobat 4.0 和更新版本相容，但是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 只支援 Adobe Acrobat 6 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="46e7f-104">Although PDF 1.3 is compatible with Adobe Acrobat 4.0 and later versions, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supports Adobe Acrobat 6 or later.</span></span> <span data-ttu-id="46e7f-105">轉譯延伸模組不需要 Adobe 軟體就能轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="46e7f-105">The rendering extension does not require Adobe software to render the report.</span></span> <span data-ttu-id="46e7f-106">但是，若要檢視或列印 PDF 格式的報表，則需要 PDF 檢視器 (例如 Adobe Acrobat)。</span><span class="sxs-lookup"><span data-stu-id="46e7f-106">However, PDF viewers such as Adobe Acrobat are required to view or print a report in PDF format.</span></span>  
  
 <span data-ttu-id="46e7f-107">PDF 轉譯延伸模組支援 ANSI 字元，而且可以從日文、韓文、繁體中文、簡體中文、斯拉夫文、希伯來文和阿拉伯文，轉譯 Unicode 字元 (有特定限制)。</span><span class="sxs-lookup"><span data-stu-id="46e7f-107">The PDF rendering extension supports ANSI characters and can translate Unicode characters from Japanese, Korean, Traditional Chinese, Simplified Chinese, Cyrillic, Hebrew, and Arabic with certain limitations.</span></span> <span data-ttu-id="46e7f-108">如需有關限制的詳細資訊，請參閱[報表產生器和 SSRS&#41;匯出報表 &#40;](export-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="46e7f-108">For more information about the limitations, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="46e7f-109">PDF 轉譯器是一種實體頁面轉譯器，因此，其分頁行為與 HTML 和 Excel 之類的其他轉譯器不同。</span><span class="sxs-lookup"><span data-stu-id="46e7f-109">The PDF renderer is a physical page renderer and, therefore, has pagination behavior that differs from other renderers such as HTML and Excel.</span></span> <span data-ttu-id="46e7f-110">本主題提供 PDF 轉譯器的特定資訊並描述規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="46e7f-110">This topic provides PDF renderer-specific information and describes exceptions to the rules.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="font-embedding"></a><a name="FontRequirements"></a><span data-ttu-id="46e7f-111">字型內嵌</span><span class="sxs-lookup"><span data-stu-id="46e7f-111">Font Embedding</span></span>  
 <span data-ttu-id="46e7f-112">如果可以的話，PDF 轉譯延伸模組會內嵌在 PDF 檔中顯示報表所需之每個字型的子集。</span><span class="sxs-lookup"><span data-stu-id="46e7f-112">When possible, the PDF rendering extension embeds the subset of each font that is needed to display the report in the PDF file.</span></span> <span data-ttu-id="46e7f-113">報表中使用的字型必須安裝在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="46e7f-113">Fonts that are used in the report must be installed on the report server.</span></span> <span data-ttu-id="46e7f-114">報表伺服器產生 PDF 格式的報表時，會使用以報表參考之字型儲存的資訊，來建立 PDF 檔案中的字元對應。</span><span class="sxs-lookup"><span data-stu-id="46e7f-114">When the report server generates a report in PDF format, it uses the information stored in the font referenced by the report to create character mappings within the PDF file.</span></span> <span data-ttu-id="46e7f-115">如果報表伺服器上未安裝參考字型，則產生的 PDF 檔案可能不會包含正確的對應，而且檢視時可能也無法正確地顯示。</span><span class="sxs-lookup"><span data-stu-id="46e7f-115">If the referenced font is not installed on the report server, the resulting PDF file might not contain the correct mappings and might not display correctly when viewed.</span></span>  
  
 <span data-ttu-id="46e7f-116">當下列條件成立時，字型會內嵌在 PDF 檔案中：</span><span class="sxs-lookup"><span data-stu-id="46e7f-116">Fonts are embedded in the PDF file when the following conditions apply:</span></span>  
  
-   <span data-ttu-id="46e7f-117">字型作者授與字型內嵌權限。</span><span class="sxs-lookup"><span data-stu-id="46e7f-117">Font embedding privileges are granted by the font author.</span></span> <span data-ttu-id="46e7f-118">已安裝的字型包含表示字型作者是否想要讓字型內嵌在文件中的屬性。</span><span class="sxs-lookup"><span data-stu-id="46e7f-118">Installed fonts include a property that indicates whether the font author intends to allow embedding a font in a document.</span></span> <span data-ttu-id="46e7f-119">如果屬性值為 EMBED_NOEMBEDDING，字型就不會內嵌在 PDF 檔案中。</span><span class="sxs-lookup"><span data-stu-id="46e7f-119">If the property value is EMBED_NOEMBEDDING, the font is not embedded in the PDF file.</span></span> <span data-ttu-id="46e7f-120">如需詳細資訊，請參閱 msdn.microsoft.com 上的「TTGetEmbeddingType」。</span><span class="sxs-lookup"><span data-stu-id="46e7f-120">For more information, see "TTGetEmbeddingType" on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="46e7f-121">字型為 TrueType。</span><span class="sxs-lookup"><span data-stu-id="46e7f-121">The Font is TrueType.</span></span>  
  
-   <span data-ttu-id="46e7f-122">字型由報表中的可見項目參考。</span><span class="sxs-lookup"><span data-stu-id="46e7f-122">Fonts are referenced by visible items in a report.</span></span> <span data-ttu-id="46e7f-123">如果字型由 Hidden 屬性設定為 True 的項目所參考，則不需要字型來顯示轉譯的資料，而且字型將不會包含在檔案中。</span><span class="sxs-lookup"><span data-stu-id="46e7f-123">If a font is referenced by an item that has the Hidden property set to True, the font is not needed to display rendered data and will not be included in the file.</span></span> <span data-ttu-id="46e7f-124">只有在需要字型來顯示轉譯的報表資料時，才會內嵌字型。</span><span class="sxs-lookup"><span data-stu-id="46e7f-124">Fonts are embedded only when they are needed to display the rendered report data.</span></span>  
  
 <span data-ttu-id="46e7f-125">如果字型符合所有的條件，就會內嵌在 PDF 檔案中。</span><span class="sxs-lookup"><span data-stu-id="46e7f-125">If all of these conditions are met for a font, the font is embedded in the PDF file.</span></span> <span data-ttu-id="46e7f-126">如果其中有一或多個條件不符合，字型就不會內嵌在 PDF 檔案中。</span><span class="sxs-lookup"><span data-stu-id="46e7f-126">If one or more of these conditions is not met, the font is not embedded in the PDF file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46e7f-127">雖然符合這些條件，但是有一個情況不會在 PDF 檔案中內嵌字型。</span><span class="sxs-lookup"><span data-stu-id="46e7f-127">Although the conditions are met, there is one circumstance under which fonts are not embedded in the PDF file.</span></span> <span data-ttu-id="46e7f-128">如果使用的字型是 PDF 規格中一般稱為標準第一類字型或是基本十四種字型中的字型，則 ANSI 內容不會內嵌字型。</span><span class="sxs-lookup"><span data-stu-id="46e7f-128">If the fonts used are the ones in the PDF specification that are commonly known as standard type 1 fonts or the base fourteen fonts, then fonts are not embedded for ANSI content.</span></span>  
  
  
  
### <a name="fonts-on-the-client-computer"></a><span data-ttu-id="46e7f-129">用戶端電腦上的字型</span><span class="sxs-lookup"><span data-stu-id="46e7f-129">Fonts on the Client Computer</span></span>  
 <span data-ttu-id="46e7f-130">當字型內嵌在 PDF 檔案中時，用來檢視報表的電腦 (用戶端電腦) 不需要安裝字型，即可正確顯示報表。</span><span class="sxs-lookup"><span data-stu-id="46e7f-130">When a font is embedded in the PDF file, the computer that is used to view the report (the client computer) does not need to have the font installed for the report to display correctly.</span></span>  
  
 <span data-ttu-id="46e7f-131">當字型沒有內嵌在 PDF 檔案中時，用戶端電腦必須已安裝正確的字型，才能正確顯示報表。</span><span class="sxs-lookup"><span data-stu-id="46e7f-131">When a font is not embedded in the PDF file, the client computer must have the correct font installed for the report to display correctly.</span></span> <span data-ttu-id="46e7f-132">如果字型未安裝在用戶端電腦上，PDF 檔案會針對不支援的字元顯示一個問號字元 (?)。</span><span class="sxs-lookup"><span data-stu-id="46e7f-132">If the font is not installed on the client computer, the PDF file displays a question mark character (?) for unsupported characters.</span></span>  
  
### <a name="verifying-fonts-in-a-pdf-file"></a><span data-ttu-id="46e7f-133">確認 PDF 檔案中的字型</span><span class="sxs-lookup"><span data-stu-id="46e7f-133">Verifying Fonts in a PDF File</span></span>  
 <span data-ttu-id="46e7f-134">當在報表中使用不支援非拉丁字元的字型，然後將非拉丁字元加入至報表中時，PDF 的輸出中最常發生差異的情形。</span><span class="sxs-lookup"><span data-stu-id="46e7f-134">Differences in PDF output occur most often when a font that does not support non-Latin characters is used in a report and then non-Latin characters are added to the report.</span></span> <span data-ttu-id="46e7f-135">您應該在報表伺服器和用戶端電腦上皆測試 PDF 轉譯輸出，以確認報表正確轉譯。</span><span class="sxs-lookup"><span data-stu-id="46e7f-135">You should test the PDF rendering output on both the report server and the client computers to verify that the report renders correctly.</span></span>  
  
 <span data-ttu-id="46e7f-136">請勿依賴在預覽中檢視報表，或匯出至 HTML，因為報表會由於圖形設計介面或 Microsoft Internet Explorer 個別所執行的字型自動替換，而使其外觀看起來是正確的。</span><span class="sxs-lookup"><span data-stu-id="46e7f-136">Do not rely on viewing the report in Preview or exporting to HTML because the report will look correct due to automatic font substitution performed by the graphical design interface or by Microsoft Internet Explorer, respectively.</span></span> <span data-ttu-id="46e7f-137">如果伺服器上有缺少 Unicode 圖像，您會看到這些字元會以問號 (?) 取代。</span><span class="sxs-lookup"><span data-stu-id="46e7f-137">If there are Unicode Glyphs missing on the server, you may see characters replaced with a question mark (?).</span></span> <span data-ttu-id="46e7f-138">如果用戶端上有缺少字型，您會看到這些字元以方塊 (□) 取代。</span><span class="sxs-lookup"><span data-stu-id="46e7f-138">If there is a font missing on the client, you may see characters replaced with boxes (□).</span></span>  
  
 <span data-ttu-id="46e7f-139">內嵌在 PDF 檔案中的字型包含在 Fonts 屬性中，而此屬性則以中繼資料的形式和檔案一起儲存。</span><span class="sxs-lookup"><span data-stu-id="46e7f-139">The fonts that are embedded in the PDF file are included in the Fonts property that is saved with the file, as metadata.</span></span>  
  
##  <a name="metadata"></a><a name="Metadata"></a> <span data-ttu-id="46e7f-140">中繼資料</span><span class="sxs-lookup"><span data-stu-id="46e7f-140">Metadata</span></span>  
 <span data-ttu-id="46e7f-141">除了報表配置之外，PDF 轉譯延伸模組也會將下列中繼資料寫入 PDF 文件資訊字典。</span><span class="sxs-lookup"><span data-stu-id="46e7f-141">In addition to the report layout, the PDF rendering extension writes the following metadata to the PDF Document Information Dictionary.</span></span>  
  
|<span data-ttu-id="46e7f-142">PDF 屬性</span><span class="sxs-lookup"><span data-stu-id="46e7f-142">PDF property</span></span>|<span data-ttu-id="46e7f-143">來源</span><span class="sxs-lookup"><span data-stu-id="46e7f-143">Created from</span></span>|  
|------------------|------------------|  
|`Title`|<span data-ttu-id="46e7f-144">`Name` RDL 元素的 `Report` 屬性。</span><span class="sxs-lookup"><span data-stu-id="46e7f-144">The `Name` attribute of the `Report` RDL element.</span></span>|  
|`Author`|<span data-ttu-id="46e7f-145">`Author` RDL 元素。</span><span class="sxs-lookup"><span data-stu-id="46e7f-145">The `Author` RDL element.</span></span>|  
|`Subject`|<span data-ttu-id="46e7f-146">`Description` RDL 元素。</span><span class="sxs-lookup"><span data-stu-id="46e7f-146">The `Description` RDL element.</span></span>|  
|`Creator`|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="46e7f-147">產品名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="46e7f-147">product name and version.</span></span>|  
|`Producer`|<span data-ttu-id="46e7f-148">轉譯延伸模組名稱與版本。</span><span class="sxs-lookup"><span data-stu-id="46e7f-148">Rendering extension name and version.</span></span>|  
|`CreationDate`|<span data-ttu-id="46e7f-149">PDF `datetime` 格式的報表執行時間。</span><span class="sxs-lookup"><span data-stu-id="46e7f-149">Report execution time in PDF `datetime` format.</span></span>|  
  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="46e7f-150">互動性</span><span class="sxs-lookup"><span data-stu-id="46e7f-150">Interactivity</span></span>  
 <span data-ttu-id="46e7f-151">在 PDF 中支援某些互動項目。</span><span class="sxs-lookup"><span data-stu-id="46e7f-151">Some interactive elements are supported in PDF.</span></span> <span data-ttu-id="46e7f-152">下列是特定行為的描述。</span><span class="sxs-lookup"><span data-stu-id="46e7f-152">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="46e7f-153">顯示與隱藏</span><span class="sxs-lookup"><span data-stu-id="46e7f-153">Show and Hide</span></span>  
 <span data-ttu-id="46e7f-154">在 PDF 中不支援動態顯示與隱藏元素。</span><span class="sxs-lookup"><span data-stu-id="46e7f-154">Dynamic show and hide elements are not supported in PDF.</span></span> <span data-ttu-id="46e7f-155">系統會轉譯 PDF 文件以符合報表中任何項目的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="46e7f-155">The PDF document is rendered to match the current state of any items in the report.</span></span> <span data-ttu-id="46e7f-156">例如，如果項目在一開始執行報表時顯示，則會轉譯該項目。</span><span class="sxs-lookup"><span data-stu-id="46e7f-156">For example, if the item is displayed when the report is run initially, then the item is rendered.</span></span> <span data-ttu-id="46e7f-157">如果在匯出報表時，可以切換的影像是隱藏的，就不會轉譯這些影像。</span><span class="sxs-lookup"><span data-stu-id="46e7f-157">Images that can be toggled are not rendered, if they are hidden when the report is exported.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="46e7f-158">文件引導模式</span><span class="sxs-lookup"><span data-stu-id="46e7f-158">Document Map</span></span>  
 <span data-ttu-id="46e7f-159">如果報表中有任何文件引導模式標籤，就會在 PDF 檔案中加入文件大綱。</span><span class="sxs-lookup"><span data-stu-id="46e7f-159">If there are any document map labels present in the report, a document outline is added to the PDF file.</span></span> <span data-ttu-id="46e7f-160">每個文件引導模式標籤都會以該標籤在報表中出現的順序，顯示為文件大綱中的一個項目。</span><span class="sxs-lookup"><span data-stu-id="46e7f-160">Each document map label appears as an entry in the document outline in the order that it appears in the report.</span></span> <span data-ttu-id="46e7f-161">在 Acrobat 中，只有在轉譯目標書籤所在頁面時，才會將該書籤加入到文件大綱中。</span><span class="sxs-lookup"><span data-stu-id="46e7f-161">In Acrobat, a target bookmark is added to the document outline only if the page it is on is rendered.</span></span>  
  
 <span data-ttu-id="46e7f-162">如果只轉譯單一頁面，則不會加入任何文件大綱。</span><span class="sxs-lookup"><span data-stu-id="46e7f-162">If only a single page is rendered, no document outline is added.</span></span> <span data-ttu-id="46e7f-163">系統會以階層的方式排列文件引導模式，來反映報表中的巢狀層級。</span><span class="sxs-lookup"><span data-stu-id="46e7f-163">The document map is arranged hierarchically to reflect the level of nesting in the report.</span></span> <span data-ttu-id="46e7f-164">[書簽] 索引標籤底下的 Acrobat 可存取檔大綱。按一下 [檔大綱] 中的專案，會使檔移至已加入書簽的位置。</span><span class="sxs-lookup"><span data-stu-id="46e7f-164">The document outline is accessible in Acrobat under the Bookmarks tab. Clicking an entry within the document outline causes the document to go to the bookmarked location.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="46e7f-165">書籤</span><span class="sxs-lookup"><span data-stu-id="46e7f-165">Bookmarks</span></span>  
 <span data-ttu-id="46e7f-166">在 PDF 轉譯中不支援書籤。</span><span class="sxs-lookup"><span data-stu-id="46e7f-166">Bookmarks are not supported in PDF rendering.</span></span>  
  
### <a name="drillthrough-links"></a><span data-ttu-id="46e7f-167">鑽研連結</span><span class="sxs-lookup"><span data-stu-id="46e7f-167">Drillthrough Links</span></span>  
 <span data-ttu-id="46e7f-168">在 PDF 轉譯中不支援鑽研連結。</span><span class="sxs-lookup"><span data-stu-id="46e7f-168">Drillthrough links are not supported in PDF rendering.</span></span> <span data-ttu-id="46e7f-169">鑽研連結不會轉譯為可點按的連結，而且鑽研報表無法連接到鑽研的目標。</span><span class="sxs-lookup"><span data-stu-id="46e7f-169">The drillthrough links are not rendered as clickable links and drillthrough reports cannot connect to the target of the drillthrough.</span></span>  
  
### <a name="hyperlinks"></a><span data-ttu-id="46e7f-170">超連結</span><span class="sxs-lookup"><span data-stu-id="46e7f-170">Hyperlinks</span></span>  
 <span data-ttu-id="46e7f-171">報表中的超連結會轉譯為 PDF 檔案中可點按的連結。</span><span class="sxs-lookup"><span data-stu-id="46e7f-171">Hyperlinks in reports are rendered as clickable links in the PDF file.</span></span> <span data-ttu-id="46e7f-172">當您按一下超連結時，Acrobat 會開啟預設的用戶端瀏覽器，並導覽至超連結 URL。</span><span class="sxs-lookup"><span data-stu-id="46e7f-172">When clicked, Acrobat will open the default client browser and navigate to the hyperlink URL.</span></span>  
  
  
  
##  <a name="compression"></a><a name="Compression"></a><span data-ttu-id="46e7f-173">程度</span><span class="sxs-lookup"><span data-stu-id="46e7f-173">Compression</span></span>  
 <span data-ttu-id="46e7f-174">影像壓縮會以影像的原始檔案類型為基礎。</span><span class="sxs-lookup"><span data-stu-id="46e7f-174">Image compression is based on the original file type of the image.</span></span> <span data-ttu-id="46e7f-175">PDF 轉譯延伸模組預設會壓縮 PDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="46e7f-175">The PDF rendering extension compresses PDF files by default.</span></span>  
  
 <span data-ttu-id="46e7f-176">若要盡可能保留 PDF 檔案隨附的任何壓縮影像，JPEG 影像會儲存為 JPEG，而其他所有影像類型則會儲存為 BMP。</span><span class="sxs-lookup"><span data-stu-id="46e7f-176">To preserve any compression for images included in the PDF file when possible, JPEG images are stored as JPEG and all other image types are stored as BMP.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46e7f-177">PDF 檔案不支援內嵌 PNG 影像。</span><span class="sxs-lookup"><span data-stu-id="46e7f-177">PDF files don't support embedding PNG images.</span></span>  
  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="46e7f-178">裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="46e7f-178">Device Information Settings</span></span>  
 <span data-ttu-id="46e7f-179">您可以透過變更裝置資訊設定，變更此轉譯器的某些預設設定。</span><span class="sxs-lookup"><span data-stu-id="46e7f-179">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="46e7f-180">如需詳細資訊，請參閱 [PDF Device Information Settings](../pdf-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="46e7f-180">For more information, see [PDF Device Information Settings](../pdf-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="46e7f-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46e7f-181">See Also</span></span>  
 <span data-ttu-id="46e7f-182">[Reporting Services &#40;報表產生器和 SSRS 中的分頁&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="46e7f-182">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="46e7f-183">[轉譯行為 &#40;報表產生器和 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="46e7f-183">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="46e7f-184">[不同報表轉譯延伸模組的互動式功能 &#40;報表產生器和 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="46e7f-184">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="46e7f-185">[&#40;報表產生器和 SSRS 轉譯報表專案&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="46e7f-185">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="46e7f-186">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="46e7f-186">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
