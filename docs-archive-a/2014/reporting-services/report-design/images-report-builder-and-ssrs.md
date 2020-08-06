---
title: 映像 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fcc2db5c-5c26-4607-ae2b-f65c80360536
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f0840a10cc1082ba8dc7912862f7cf34c64972d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688586"
---
# <a name="images-report-builder-and-ssrs"></a><span data-ttu-id="1c7f3-102">影像 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1c7f3-102">Images (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1c7f3-103">影像是一種報表項目，其中包含了內嵌在報表中、儲存在資料庫中、儲存在報表伺服器上或儲存在網路上其他位置之影像的參考。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-103">An image is a report item that contains a reference to an image that is embedded in the report, stored in a database, stored on the report server, or stored elsewhere on the Web.</span></span> <span data-ttu-id="1c7f3-104">影像可能是一個隨資料列數重複顯示的圖片。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-104">An image can be a picture that is repeated with rows of data.</span></span> <span data-ttu-id="1c7f3-105">您也可以將影像當做某些報表項目的背景。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-105">You can also use an image as a background for certain report items.</span></span>  
  
 <span data-ttu-id="1c7f3-106">您最好將標誌儲存在伺服器上，因為您可以在許多報表中使用相同的標誌。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-106">Storing logos on a server is a good idea because you can use the same logo in many reports.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="comparing-external-embedded-and-data-bound-images"></a><a name="ComparingImages"></a> <span data-ttu-id="1c7f3-107">比較外部、內嵌與資料繫結影像</span><span class="sxs-lookup"><span data-stu-id="1c7f3-107">Comparing External, Embedded, and Data-Bound Images</span></span>  
 <span data-ttu-id="1c7f3-108">當您在報表中使用以伺服器為基礎或其他外部的影像時，影像項目會包含指向報表伺服器之影像或網路上所在位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-108">When you use a server-based or other external image in a report, the image item contains a path that points to an image on the report server or wherever it exists on the Web.</span></span> <span data-ttu-id="1c7f3-109">不過，使用內嵌影像時，影像資料是儲存在報表定義中，而不是以個別檔案存在。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-109">When you use an embedded image, however, the image data is stored within the report definition and does not exist as a separate file.</span></span>  
  
 <span data-ttu-id="1c7f3-110">以伺服器為基礎的影像在數個報表或網頁共用標誌或靜態圖片時，非常有用。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-110">Server-based images work well for logos and static pictures that are shared among several reports or Web pages.</span></span> <span data-ttu-id="1c7f3-111">內嵌影像可確保影像總是能供報表使用，但是不能共用它們。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-111">Embedded images ensure that the images are always available to the report, but they cannot be shared.</span></span> <span data-ttu-id="1c7f3-112">使用外部影像的報表定義小於使用內嵌影像的報表定義。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-112">Report definitions with external images are smaller than definitions with embedded images.</span></span>  
  
 <span data-ttu-id="1c7f3-113">資料繫結影像也可以從儲存在資料庫中的二進位資料顯示。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-113">Data-bound images can also be displayed from binary data stored in a database.</span></span> <span data-ttu-id="1c7f3-114">例如，出現在產品清單中產品名稱旁邊的圖片，即是資料庫影像。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-114">For example, the pictures that appear alongside product names in a product list are database images.</span></span> <span data-ttu-id="1c7f3-115">在下列圖片中，自行車的影像會儲存在資料庫中，並可以報表中擷取，以說明每個產品。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-115">In the following picture, the images of bicycles are stored in a database and retrieved in the report to illustrate each product.</span></span>  
  
 <span data-ttu-id="1c7f3-116">![rs_DataboundBikes](../media/rs-databoundbikes.gif "rs_DataboundBikes")</span><span class="sxs-lookup"><span data-stu-id="1c7f3-116">![rs_DataboundBikes](../media/rs-databoundbikes.gif "rs_DataboundBikes")</span></span>  
  

  
##  <a name="images-as-report-parts"></a><a name="ImagesReportParts"></a> <span data-ttu-id="1c7f3-117">當做報表組件的影像</span><span class="sxs-lookup"><span data-stu-id="1c7f3-117">Images as Report Parts</span></span>  
 <span data-ttu-id="1c7f3-118">您可以將影像當做報表組件，與報表分開儲存。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-118">You can save images separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 
  
##  <a name="embedding-images"></a><a name="EmbedImages"></a> <span data-ttu-id="1c7f3-119">內嵌影像</span><span class="sxs-lookup"><span data-stu-id="1c7f3-119">Embedding Images</span></span>  
 <span data-ttu-id="1c7f3-120">您可以在報表中內嵌影像，讓所有影像資料都儲存在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-120">You can embed images in a report so that all image data is stored within the report definition.</span></span> <span data-ttu-id="1c7f3-121">當您內嵌影像時，影像會以 MIME 編碼，並當做文字儲存在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-121">When you embed an image, the image is MIME-encoded and stored as text in the report definition.</span></span> <span data-ttu-id="1c7f3-122">使用內嵌影像來確保報表隨時都可以使用影像，但它也會增加報表定義的大小。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-122">Using an embedded image ensures that the image is always available to the report, but it also increases the size of the report definition.</span></span>  
  
 <span data-ttu-id="1c7f3-123">如需內嵌影像的詳細資訊，請參閱 [在報表中內嵌影像 &#40;報表產生器及 SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-123">For more information about embedding an image, see [Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="external-images"></a><a name="ExternalImages"></a> <span data-ttu-id="1c7f3-124">外部影像</span><span class="sxs-lookup"><span data-stu-id="1c7f3-124">External Images</span></span>  
 <span data-ttu-id="1c7f3-125">您可以指定影像的 URL，在報表中包含預存影像。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-125">You can include stored images in a report by specifying a URL to the image.</span></span> <span data-ttu-id="1c7f3-126">當您在報表中使用外部影像時，影像來源會設定為 `External`，而影像的值則是影像的 URL 位址或路徑。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-126">When you use an external image in a report, the image source is set to `External` and the value for the image is the URL address or path to the image.</span></span>  
  
 <span data-ttu-id="1c7f3-127">如需詳細資訊，請參閱[指定外部項目的路徑 &#40;報表產生器及 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-127">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1c7f3-128">在報表產生器或報表設計師中執行報表時，預覽會以使用者的認證來顯示影像。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-128">When the report is run in Report Builder or Report Designer, preview uses the credentials of the user to display the image.</span></span> <span data-ttu-id="1c7f3-129">在報表伺服器上執行報表時，如果伺服器認證不足以存取影像，可能就不會顯示報表中的影像。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-129">When the report is run on the report server, the image in the report may not be displayed if the server credentials are not sufficient to access the image.</span></span> <span data-ttu-id="1c7f3-130">在這種情況下，請連絡系統管理員。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-130">In that case, contact your system administrator.</span></span>  
  
 <span data-ttu-id="1c7f3-131">如需將外部影像加入報表中的詳細資訊，請參閱 [加入外部影像 &#40;報表產生器及 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-131">For more information about adding an external image to a report, see [Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="background-images"></a><a name="BackgroundImages"></a> <span data-ttu-id="1c7f3-132">背景影像</span><span class="sxs-lookup"><span data-stu-id="1c7f3-132">Background Images</span></span>  
 <span data-ttu-id="1c7f3-133">影像可當做報表之主體、矩形、文字方塊、清單、矩陣或資料表中的背景影像。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-133">You can use an image as a background image in the body of the report or in a rectangle, text box, list, matrix, or table.</span></span> <span data-ttu-id="1c7f3-134">背景影像和影像具有類似的屬性。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-134">A background image and an image have similar properties.</span></span> <span data-ttu-id="1c7f3-135">您也可以指定如何重複影像將項目的背景填滿。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-135">You can also specify how the image is repeated to fill the background of the item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c7f3-136">某些轉譯延伸模組 (例如 HTML 轉譯延伸模組) 會在主體、頁首和頁尾中轉譯報表主體的背景影像。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-136">Some rendering extensions, like the HTML rendering extension, render the background image for the report body in the body, the page header, and the page footer.</span></span> <span data-ttu-id="1c7f3-137">您可以為頁首和頁尾定義個別的背景影像，但是如果沒有定義影像，報表就會使用主體的背景影像。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-137">You can define a separate background image for the page header and footer, but if no image is defined, the report uses the background image of the body.</span></span> <span data-ttu-id="1c7f3-138">其他的轉譯延伸模組 (如影像轉譯延伸模組) 並不會在頁首和頁尾中轉譯主體背景影像。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-138">Other rendering extensions, like the Image rendering extension, do not render the body background image in the page header and footer.</span></span>  
  
 <span data-ttu-id="1c7f3-139">如需加入背景影像的詳細資訊，請參閱 [加入背景影像 &#40;報表產生器及 SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-139">For more information about adding a background image, see [Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="data-bound-images"></a><a name="DataboundImages"></a> <span data-ttu-id="1c7f3-140">資料繫結影像</span><span class="sxs-lookup"><span data-stu-id="1c7f3-140">Data-bound Images</span></span>  
 <span data-ttu-id="1c7f3-141">您可以將儲存在資料庫中的影像加入至您的報表。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-141">You can add images that are stored in a database to your report.</span></span> <span data-ttu-id="1c7f3-142">您使用的影像報表項目與靜態影像所使用的相同，不過多了一組屬性來指示影像儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-142">You use the same image report item as the one used for static images, but with a set of properties that indicate that the image is stored in a database.</span></span> <span data-ttu-id="1c7f3-143">若要檢視資料繫結影像的使用指示，請參閱 [加入資料繫結影像 &#40;報表產生器及 SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1c7f3-143">To view instructions about working with data-bound images, see [Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="1c7f3-144">如何主題</span><span class="sxs-lookup"><span data-stu-id="1c7f3-144">How-to Topics</span></span>  
 [<span data-ttu-id="1c7f3-145">加入外部影像 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1c7f3-145">Add an External Image &#40;Report Builder and SSRS&#41;</span></span>](add-an-external-image-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="1c7f3-146">在報表中內嵌影像 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1c7f3-146">Embed an Image in a Report &#40;Report Builder and SSRS&#41;</span></span>](embed-an-image-in-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="1c7f3-147">加入背景影像 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1c7f3-147">Add a Background Image &#40;Report Builder and SSRS&#41;</span></span>](add-a-background-image-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="1c7f3-148">加入資料繫結影像 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1c7f3-148">Add a Data-Bound Image &#40;Report Builder and SSRS&#41;</span></span>](add-a-data-bound-image-report-builder-and-ssrs.md)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="1c7f3-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c7f3-149">See Also</span></span>  
 <span data-ttu-id="1c7f3-150">[匯出至影像檔 &#40;報表產生器及 SSRS&#41;](../report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1c7f3-150">[Exporting to an Image File &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1c7f3-151">轉譯行為 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1c7f3-151">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
