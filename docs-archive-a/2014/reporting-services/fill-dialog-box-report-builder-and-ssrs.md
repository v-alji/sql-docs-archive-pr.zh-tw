---
title: '[填滿] 對話方塊 (報表產生器和 SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportbody.fill.f1
- "10065"
- "10501"
- sql12.rtp.rptdesigner.shared.filldv.f1
- sql12.rtp.rptdesigner.rectangleproperties.fill.f1
- "10064"
- sql12.rtp.rptdesigner.textboxproperties.fill.f1
- "10124"
ms.assetid: 93a91d02-d558-4a0e-8d17-3fdf21e208d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae7f2b05d4d108c77f1dcae9ce7fefe5073e2522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596509"
---
# <a name="fill-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="1a1b2-102">填滿對話方塊 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1a1b2-102">Fill Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1a1b2-103">在 [填滿]\*\*\*\* 索引標籤上，您可以指定資料區或文字方塊內，單一資料格或多個資料格的背景選項。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-103">On the **Fill** tab, you can specify color options for the background of a single cell or multiple cells within a data region or a text box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1a1b2-104">選項</span><span class="sxs-lookup"><span data-stu-id="1a1b2-104">Options</span></span>  
 <span data-ttu-id="1a1b2-105">**填滿色彩**</span><span class="sxs-lookup"><span data-stu-id="1a1b2-105">**Fill Color**</span></span>  
 <span data-ttu-id="1a1b2-106">按一下色彩按鈕，為矩形選取一個填滿色彩。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-106">Click the color button to select a fill color for the rectangle.</span></span> <span data-ttu-id="1a1b2-107">按一下 [運算式]\*\*\*\*_(fx)_ 按鈕來編輯運算式，這個運算式可以是 RGB 色彩的十六進位值，或在 [運算式]\*\*\*\* 對話方塊中提供之預先定義的其中一個色彩名稱。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-107">Click the **Expression**_(fx)_ button to edit the expression, which can be a hexadecimal value for the RGB color or one of the predefined color names that are provided in the **Expression** dialog box.</span></span> <span data-ttu-id="1a1b2-108">若要查看預先定義之色彩的清單，選取 [項目]\*\*\*\* 窗格中的 [Web]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-108">To see a list of predefined colors, in the **Item** pane, select **Web**.</span></span> <span data-ttu-id="1a1b2-109">您可以將列在 [標題]\*\*\*\* 窗格中的色彩名稱輸入到運算式文字窗格中。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-109">The color names listed in the **Title** pane can be typed into the expression text pane.</span></span> <span data-ttu-id="1a1b2-110">輸入色彩名稱時，請勿使用等號 (=) 或引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-110">Do not use an equal sign (=) or quotation marks ("") when typing the color name.</span></span>  
  
 <span data-ttu-id="1a1b2-111">**選取影像來源**</span><span class="sxs-lookup"><span data-stu-id="1a1b2-111">**Select the image source**</span></span>  
 <span data-ttu-id="1a1b2-112">指出影像儲存的位置，以便在轉譯報表時，讓報表處理器可以顯示該影像。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-112">Indicate where the image is stored so that when the report is rendered, the report processor can display it.</span></span>  
  
-   <span data-ttu-id="1a1b2-113">**外部** ：當您希望影像在報表伺服器或網頁伺服器上繼續當作檔案存在時，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-113">**External** Choose this option when you want the image to continue to exist as a file on a report server or Web server.</span></span>  
  
-   <span data-ttu-id="1a1b2-114">**內嵌** ：當您要將影片內嵌到報表中時，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-114">**Embedded** Choose this option when you want to embed the image into the report.</span></span>  
  
-   <span data-ttu-id="1a1b2-115">**資料庫** ：當您要加入的資料庫欄位名稱代表您要包含在報表中的影像時，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-115">**Database** Choose this option when you want to include a database field name that represents the images that you want to include in your report.</span></span>  
  
 <span data-ttu-id="1a1b2-116">**使用此影像**</span><span class="sxs-lookup"><span data-stu-id="1a1b2-116">**Use this image**</span></span>  
 <span data-ttu-id="1a1b2-117">此選項會在您選取 [內嵌]\*\*\*\* 或 [外部]\*\*\*\* 選項時出現。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-117">This option appears when you select the **Embedded** or **External** option.</span></span>  
  
 <span data-ttu-id="1a1b2-118">如果您要內嵌影像，從下拉式清單中選擇您要加入報表的圖片。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-118">If you are embedding the image, choose the picture that you want to add to the report from the drop-down list.</span></span> <span data-ttu-id="1a1b2-119">按一下 [匯入]\*\*\*\*，將影像加入到下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-119">Click **Import** to add the image to the drop-down list.</span></span> <span data-ttu-id="1a1b2-120">如果您要將影像加入到 [資料]\*\*\*\* 窗格中，您可以選擇 [內嵌]\*\*\*\*，然後從下拉式清單中選取影像，就可以選取該影像。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-120">If you added an image to the **Data** pane, you can select that image by choosing **Embedded** and then selecting the image from the drop-down list.</span></span>  
  
 <span data-ttu-id="1a1b2-121">如果您選取 [外部]\*\*\*\* 選項，輸入影像的 URL。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-121">If you select the **External** option, type the URL of the image.</span></span> <span data-ttu-id="1a1b2-122">對於發行到設定為原生模式之報表伺服器的報表，請使用完整或相對路徑 (例如，HTTP:// *\<servername>* /images/image1.jpg) 。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-122">For a report published to a report server configured for native mode, use a full or relative path (for example, http://*\<servername>*/images/image1.jpg).</span></span> <span data-ttu-id="1a1b2-123">對於發行到設定為 SharePoint 整合模式之報表伺服器的報表，請使用完整的 URL (例如，HTTP:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg) 。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-123">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL (for example, http://*\<SharePointservername>/\<site>*/Documents/images/image1.jpg).</span></span>  
  
 <span data-ttu-id="1a1b2-124">**匯入**</span><span class="sxs-lookup"><span data-stu-id="1a1b2-124">**Import**</span></span>  
 <span data-ttu-id="1a1b2-125">適用於選取 [內嵌]\*\*\*\* 時。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-125">Available when you select **Embedded**.</span></span> <span data-ttu-id="1a1b2-126">按一下此選項，即可將影像加入到 [使用此影像]\*\*\*\* 下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-126">Click to add an image to the **Use this image** drop-down list.</span></span>  
  
 <span data-ttu-id="1a1b2-127">**使用此欄位**</span><span class="sxs-lookup"><span data-stu-id="1a1b2-127">**Use this field**</span></span>  
 <span data-ttu-id="1a1b2-128">適用於選取 [資料庫]\*\*\*\* 時。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-128">Available when you select **Database**.</span></span> <span data-ttu-id="1a1b2-129">選取欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-129">Select the field name.</span></span>  
  
 <span data-ttu-id="1a1b2-130">**使用此 MIME 類型**</span><span class="sxs-lookup"><span data-stu-id="1a1b2-130">**Use this MIME type**</span></span>  
 <span data-ttu-id="1a1b2-131">選擇資料庫中包含的適當圖片格式 (例如，.bmp、.jpeg、.gif、.png 或 .x-png)。</span><span class="sxs-lookup"><span data-stu-id="1a1b2-131">Choose the appropriate format of the pictures contained in the database (for example, .bmp, .jpeg, .gif, .png, or .x-png).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1b2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a1b2-132">See Also</span></span>  
 <span data-ttu-id="1a1b2-133">[將報表專案的格式設定 &#40;報表產生器和 SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a1b2-133">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1a1b2-134">[&#40;報表產生器和 SSRS 設定文字和預留位置的格式&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a1b2-134">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1a1b2-135">影像 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1a1b2-135">Images &#40;Report Builder and SSRS&#41;</span></span>](report-design/images-report-builder-and-ssrs.md)  
  
  
