---
title: 格式化線條、色彩和影像 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.textboxproperties.border.f1
- "10502"
- "10094"
- sql12.rtp.rptdesigner.pictureproperties.border.f1
- "10063"
- sql12.rtp.rptdesigner.rectangleproperties.border.f1
- "10055"
- sql12.rtp.rptdesigner.subreportproperties.border.f1
- "10126"
- sql12.rtp.rptdesigner.shared.borderdv.f1
- "10066"
- sql12.rtp.rptdesigner.reportbody.border.f1
ms.assetid: 0f5f0d2a-9537-4152-b441-b40d7f04cf4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 681ff6b46f692804aef5c7cbbc16e5abe99dbb2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686815"
---
# <a name="formatting-lines-colors-and-images-report-builder-and-ssrs"></a><span data-ttu-id="8144b-102">格式化線條、色彩和影像 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8144b-102">Formatting Lines, Colors, and Images (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8144b-103">讓您能夠格式化線條、色彩、資料區、影像和其他報表項目。</span><span class="sxs-lookup"><span data-stu-id="8144b-103">gives you the ability to format lines, colors, data regions, images, and other report items.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="borders-lines-and-gridlines"></a><span data-ttu-id="8144b-104">框線、線條和格線</span><span class="sxs-lookup"><span data-stu-id="8144b-104">Borders, Lines and Gridlines</span></span>  
 <span data-ttu-id="8144b-105">框線、線條和格線可透過視覺方式將項目一起繫結在頁面上，並協助您的報表讀者輕鬆地閱讀報表的內容。</span><span class="sxs-lookup"><span data-stu-id="8144b-105">Borders, lines, and gridlines can visually tie items together on the page and help your report readers easily read the contents of the report.</span></span> <span data-ttu-id="8144b-106">使用預先定義的框線樣式，可以快速地在一個文字方塊、一組文字方塊或影像的周圍加入框線。</span><span class="sxs-lookup"><span data-stu-id="8144b-106">Using the predefined border styles, you can quickly add a border around a text box, a group of text boxes, or an image.</span></span> <span data-ttu-id="8144b-107">此外，您也可以變更框線、線條和格線的樣式、寬度和色彩。</span><span class="sxs-lookup"><span data-stu-id="8144b-107">In addition, you can change the style, width, and color for the borders, lines, and gridlines.</span></span> <span data-ttu-id="8144b-108">整個選取的項目周圍或是此項目邊緣框線的周圍會加入框線，例如，文字方塊底部的框線。</span><span class="sxs-lookup"><span data-stu-id="8144b-108">Borders are added around the entire item selected or around a border along an edge of the item, for example, a border along the bottom of a text box.</span></span>  
  
 <span data-ttu-id="8144b-109">若要格式化文字方塊中、報表配置中或影像周圍的框線和格線，請使用報表項目之 **[屬性]** 對話方塊的 **[框線]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8144b-109">To format borders and gridlines in a text box, report layout, or around an image, use the **Border** tab of the report item's **Properties** dialog box.</span></span> <span data-ttu-id="8144b-110">例如，如果您想在影像周圍加上框線，請以滑鼠右鍵按一下影像，然後在 **[影像屬性]** 對話方塊中，按一下 **[框線]** 。</span><span class="sxs-lookup"><span data-stu-id="8144b-110">For example, if you want to add a border around an image, right-click the image and then in the **Image Properties** dialog box, click **Border**.</span></span>  
  
 <span data-ttu-id="8144b-111">除了標準邊框以外，還可以將其他邊框套用到圖表。</span><span class="sxs-lookup"><span data-stu-id="8144b-111">In addition to the standard border frames, additional border frames can be applied to charts.</span></span> <span data-ttu-id="8144b-112">如需詳細資訊，請參閱[將邊框新增至圖表 &#40;報表產生器及 SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8144b-112">For more information, see [Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8144b-113">您也可以在報表本身加上框線。</span><span class="sxs-lookup"><span data-stu-id="8144b-113">You can also add a border to the report itself.</span></span> <span data-ttu-id="8144b-114">如需詳細資訊，請參閱 [在報表中加入框線 &#40;報表產生器及 SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8144b-114">For more information, see [Add a Border to a Report &#40;Report Builder and SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
## <a name="applying-background-colors"></a><span data-ttu-id="8144b-115">套用背景色彩</span><span class="sxs-lookup"><span data-stu-id="8144b-115">Applying Background Colors</span></span>  
 <span data-ttu-id="8144b-116">純色可以加入至整個報表的背景、報表內的文字方塊，或是加入至資料區內的一個資料格或一組資料格。</span><span class="sxs-lookup"><span data-stu-id="8144b-116">A solid color can be added to the background of the entire report, a text box within the report, or to a cell or group of cells within a data region.</span></span> <span data-ttu-id="8144b-117">依預設，背景色彩為白色，不過您可以從報表項目之 **[屬性]** 對話方塊的 **[填滿]** 索引標籤選取色彩。</span><span class="sxs-lookup"><span data-stu-id="8144b-117">By default, the background color is white; however, you can select a color from the **Fill** tab of the report item's **Properties** dialog box.</span></span> <span data-ttu-id="8144b-118">例如，如果您想要變更文字方塊的背景色彩，請以滑鼠右鍵按一下此文字方塊，並選取 **[文字方塊屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="8144b-118">For example, if you want to change the background color of a text box, right-click the text box and select **Text Box Properties**.</span></span> <span data-ttu-id="8144b-119">按一下 **[填滿]** ，然後再選取您想要的色彩。</span><span class="sxs-lookup"><span data-stu-id="8144b-119">Click **Fill** and then select the color you want.</span></span> <span data-ttu-id="8144b-120">在此對話方塊中，您可以針對選取的項目選取背景色彩，或是加入出現在背景中的影像。</span><span class="sxs-lookup"><span data-stu-id="8144b-120">In this dialog box, you can select a background color for the selected item or you can add an image that appears in the background.</span></span>  
  
 <span data-ttu-id="8144b-121">當您使用圖表時，也可以為背景色彩指定漸層和圖樣樣式。</span><span class="sxs-lookup"><span data-stu-id="8144b-121">When you use the chart, you can also specify gradients and pattern styles for background colors.</span></span> <span data-ttu-id="8144b-122">如需詳細資訊，請參閱[格式化圖表 &#40;報表產生器及 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8144b-122">For more information, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-images-as-formatting"></a><span data-ttu-id="8144b-123">在格式化時使用影像</span><span class="sxs-lookup"><span data-stu-id="8144b-123">Using Images as Formatting</span></span>  
 <span data-ttu-id="8144b-124">您可以將包含影像的欄位加入至資料區。</span><span class="sxs-lookup"><span data-stu-id="8144b-124">Fields that contain images can be added to a data region.</span></span> <span data-ttu-id="8144b-125">如果您使用影像欄位，則影像會在執行報表時顯示於報表中。</span><span class="sxs-lookup"><span data-stu-id="8144b-125">If you use an image field, the images appear in the report with the report is run.</span></span>  
  
 <span data-ttu-id="8144b-126">您也可以將標誌之類的影像加入至報表的背景，或是加入到矩形、文字方塊、資料表、矩陣或圖表的某些部分，或者是加入到報表的主體和頁面區段。</span><span class="sxs-lookup"><span data-stu-id="8144b-126">You can also add images such as logos to the background of your report or to a rectangle, text box, table, matrix, or some parts of a chart, or to the body and page sections of a report.</span></span> <span data-ttu-id="8144b-127">如需詳細資訊，請參閱[影像 &#40;報表產生器及 SSRS&#41;](images-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8144b-127">For more information, see [Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8144b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8144b-128">See Also</span></span>  
 <span data-ttu-id="8144b-129">[格式化文字和預留位置 &#40;報表產生器及 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8144b-129">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8144b-130">[格式化數字和日期 &#40;報表產生器及 SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8144b-130">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8144b-131">[格式化文字方塊中的文字 &#40;報表產生器及 SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8144b-131">[Format Text in a Text Box &#40;Report Builder and SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8144b-132">填滿對話方塊 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8144b-132">Fill Dialog Box &#40;Report Builder and SSRS&#41;</span></span>](../fill-dialog-box-report-builder-and-ssrs.md)  
  
  
