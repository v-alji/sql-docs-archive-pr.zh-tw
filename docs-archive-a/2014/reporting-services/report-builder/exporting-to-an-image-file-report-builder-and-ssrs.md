---
title: 匯出至影像檔 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dc1c8539b39a99c252ebfcb0275b674f657de6c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595790"
---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a><span data-ttu-id="35c1c-102">匯出至影像檔 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="35c1c-102">Exporting to an Image File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="35c1c-103">影像轉譯延伸模組會將報表轉譯成點陣圖或中繼檔。</span><span class="sxs-lookup"><span data-stu-id="35c1c-103">The Image rendering extension renders a report to a bitmap or metafile.</span></span> <span data-ttu-id="35c1c-104">依預設，影像轉譯延伸模組會產生報表的 TIFF 檔，可在多個頁面中檢視。</span><span class="sxs-lookup"><span data-stu-id="35c1c-104">By default, the Image rendering extension produces a TIFF file of the report, which can be viewed in multiple pages.</span></span> <span data-ttu-id="35c1c-105">當用戶端接收到影像時，可以在影像檢視器中顯示和列印影像。</span><span class="sxs-lookup"><span data-stu-id="35c1c-105">When the client receives the image, it can be displayed in an image viewer and printed.</span></span> <span data-ttu-id="35c1c-106">本主題提供影像轉譯器的特定資訊並描述轉譯延伸模組的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35c1c-106">This topic provides Image renderer-specific information and describes exceptions to the rendering rules.</span></span>  
  
 <span data-ttu-id="35c1c-107">影像轉譯延伸模組可產生 [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]支援的任何格式檔案：BMP、EMF、EMFPlus、GIF、JPEG、PNG 和 TIFF。</span><span class="sxs-lookup"><span data-stu-id="35c1c-107">The Image rendering extension can generate files in any of the formats supported by [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]: BMP, EMF, EMFPlus, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="35c1c-108">針對 TIFF 格式，主要資料流的檔案名稱為 *ReportName*.tif。</span><span class="sxs-lookup"><span data-stu-id="35c1c-108">For TIFF format, the file name of the primary stream is *ReportName*.tif.</span></span> <span data-ttu-id="35c1c-109">針對每個檔案轉譯成單一頁面的其他所有格式，檔案名稱為 *ReportName_Page.ext* ，其中</span><span class="sxs-lookup"><span data-stu-id="35c1c-109">For all other formats, which render as a single page per file, the file name is *ReportName_Page.ext* where.</span></span> <span data-ttu-id="35c1c-110">*ext* 是所選格式的副檔名。</span><span class="sxs-lookup"><span data-stu-id="35c1c-110">*ext* is the file extension for the chosen format.</span></span> <span data-ttu-id="35c1c-111">若要以影像支援的其他格式產生檔案，請在 **OutputFormatDeviceInfo** 設定中指定以上列出的任何字串。</span><span class="sxs-lookup"><span data-stu-id="35c1c-111">To produce a file in another Image-supported format, specify any of the above listed strings in the **OutputFormatDeviceInfo** setting.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="supported-image-formats"></a><a name="SupportedImageFormats"></a> <span data-ttu-id="35c1c-112">支援的影像格式</span><span class="sxs-lookup"><span data-stu-id="35c1c-112">Supported Image Formats</span></span>  
 <span data-ttu-id="35c1c-113">下表顯示每個影像轉譯器格式的副檔名和 MimeType。</span><span class="sxs-lookup"><span data-stu-id="35c1c-113">The following table shows the file extension and MimeType for each Image renderer format.</span></span>  
  
|<span data-ttu-id="35c1c-114">**型別**</span><span class="sxs-lookup"><span data-stu-id="35c1c-114">**Type**</span></span>|<span data-ttu-id="35c1c-115">**分機**</span><span class="sxs-lookup"><span data-stu-id="35c1c-115">**Extension**</span></span>|<span data-ttu-id="35c1c-116">**MIMEType**</span><span class="sxs-lookup"><span data-stu-id="35c1c-116">**MIMEType**</span></span>|  
|--------------|-------------------|------------------|  
|<span data-ttu-id="35c1c-117">BMP</span><span class="sxs-lookup"><span data-stu-id="35c1c-117">BMP</span></span>|<span data-ttu-id="35c1c-118">bmp</span><span class="sxs-lookup"><span data-stu-id="35c1c-118">bmp</span></span>|<span data-ttu-id="35c1c-119">image/bmp</span><span class="sxs-lookup"><span data-stu-id="35c1c-119">image/bmp</span></span>|  
|<span data-ttu-id="35c1c-120">GIF</span><span class="sxs-lookup"><span data-stu-id="35c1c-120">GIF</span></span>|<span data-ttu-id="35c1c-121">GIF</span><span class="sxs-lookup"><span data-stu-id="35c1c-121">gif</span></span>|<span data-ttu-id="35c1c-122">image/gif</span><span class="sxs-lookup"><span data-stu-id="35c1c-122">image/gif</span></span>|  
|<span data-ttu-id="35c1c-123">JPEG</span><span class="sxs-lookup"><span data-stu-id="35c1c-123">JPEG</span></span>|<span data-ttu-id="35c1c-124">jpeg</span><span class="sxs-lookup"><span data-stu-id="35c1c-124">jpeg</span></span>|<span data-ttu-id="35c1c-125">image/jpeg</span><span class="sxs-lookup"><span data-stu-id="35c1c-125">image/jpeg</span></span>|  
|<span data-ttu-id="35c1c-126">PNG</span><span class="sxs-lookup"><span data-stu-id="35c1c-126">PNG</span></span>|<span data-ttu-id="35c1c-127">png</span><span class="sxs-lookup"><span data-stu-id="35c1c-127">png</span></span>|<span data-ttu-id="35c1c-128">image/png</span><span class="sxs-lookup"><span data-stu-id="35c1c-128">image/png</span></span>|  
|<span data-ttu-id="35c1c-129">TIFF</span><span class="sxs-lookup"><span data-stu-id="35c1c-129">TIFF</span></span>|<span data-ttu-id="35c1c-130">tif</span><span class="sxs-lookup"><span data-stu-id="35c1c-130">tif</span></span>|<span data-ttu-id="35c1c-131">image/tiff</span><span class="sxs-lookup"><span data-stu-id="35c1c-131">image/tiff</span></span>|  
|<span data-ttu-id="35c1c-132">EMF</span><span class="sxs-lookup"><span data-stu-id="35c1c-132">EMF</span></span>|<span data-ttu-id="35c1c-133">EMF</span><span class="sxs-lookup"><span data-stu-id="35c1c-133">emf</span></span>|<span data-ttu-id="35c1c-134">image/emf</span><span class="sxs-lookup"><span data-stu-id="35c1c-134">image/emf</span></span>|  
|<span data-ttu-id="35c1c-135">EMFPlus</span><span class="sxs-lookup"><span data-stu-id="35c1c-135">EMFPlus</span></span>|<span data-ttu-id="35c1c-136">EMF</span><span class="sxs-lookup"><span data-stu-id="35c1c-136">emf</span></span>|<span data-ttu-id="35c1c-137">image/emf</span><span class="sxs-lookup"><span data-stu-id="35c1c-137">image/emf</span></span>|  
  
  
##  <a name="rendering-multiple-pages"></a><a name="RenderingMultiplePages"></a> <span data-ttu-id="35c1c-138">轉譯多頁</span><span class="sxs-lookup"><span data-stu-id="35c1c-138">Rendering Multiple Pages</span></span>  
 <span data-ttu-id="35c1c-139">TIFF 是在單一檔案中，支援多頁文件的唯一格式。</span><span class="sxs-lookup"><span data-stu-id="35c1c-139">TIFF is the only format that supports multiple page documents in a single file.</span></span> <span data-ttu-id="35c1c-140">JPG 或 PNG 之類的其他格式一次輸出一頁，而且需要為每一頁個別呼叫轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="35c1c-140">Other formats, such as JPG or PNG, output one page at a time and require a separate call to the rendering extension for each page.</span></span>  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="35c1c-141">互動性</span><span class="sxs-lookup"><span data-stu-id="35c1c-141">Interactivity</span></span>  
 <span data-ttu-id="35c1c-142">此轉譯器產生的任何影像格式都不支援互動性。</span><span class="sxs-lookup"><span data-stu-id="35c1c-142">Interactivity is not supported in any Image formats generated by this renderer.</span></span> <span data-ttu-id="35c1c-143">系統不會轉譯下列互動項目：</span><span class="sxs-lookup"><span data-stu-id="35c1c-143">The following interactive elements are not rendered:</span></span>  
  
-   <span data-ttu-id="35c1c-144">超連結</span><span class="sxs-lookup"><span data-stu-id="35c1c-144">Hyperlinks</span></span>  
  
-   <span data-ttu-id="35c1c-145">顯示或隱藏</span><span class="sxs-lookup"><span data-stu-id="35c1c-145">Show or Hide</span></span>  
  
-   <span data-ttu-id="35c1c-146">文件引導模式</span><span class="sxs-lookup"><span data-stu-id="35c1c-146">Document Map</span></span>  
  
-   <span data-ttu-id="35c1c-147">鑽研或點選連結的連結</span><span class="sxs-lookup"><span data-stu-id="35c1c-147">Drillthrough or clickthrough links</span></span>  
  
-   <span data-ttu-id="35c1c-148">使用者排序</span><span class="sxs-lookup"><span data-stu-id="35c1c-148">End user sort</span></span>  
  
-   <span data-ttu-id="35c1c-149">固定頁首</span><span class="sxs-lookup"><span data-stu-id="35c1c-149">Fixed headers</span></span>  
  
-   <span data-ttu-id="35c1c-150">書籤</span><span class="sxs-lookup"><span data-stu-id="35c1c-150">Bookmarks</span></span>  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="35c1c-151">裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="35c1c-151">Device Information Settings</span></span>  
 <span data-ttu-id="35c1c-152">您可以透過變更裝置資訊設定，變更此轉譯器的某些預設設定。</span><span class="sxs-lookup"><span data-stu-id="35c1c-152">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="35c1c-153">如需詳細資訊，請參閱＜ [Image Device Information Settings](../image-device-information-settings.md)＞。</span><span class="sxs-lookup"><span data-stu-id="35c1c-153">For more information, see [Image Device Information Settings](../image-device-information-settings.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="35c1c-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35c1c-154">See Also</span></span>  
 <span data-ttu-id="35c1c-155">[Reporting Services &#40;報表產生器和 SSRS 中的分頁&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="35c1c-155">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="35c1c-156">[轉譯行為 &#40;報表產生器和 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="35c1c-156">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="35c1c-157">[不同報表轉譯延伸模組的互動式功能 &#40;報表產生器和 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="35c1c-157">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="35c1c-158">[&#40;報表產生器和 SSRS 轉譯報表專案&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="35c1c-158">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="35c1c-159">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="35c1c-159">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
