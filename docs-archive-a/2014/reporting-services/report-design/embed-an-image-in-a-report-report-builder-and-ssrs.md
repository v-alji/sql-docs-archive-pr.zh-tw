---
title: 在報表中內嵌影像 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.embeddedimages.f1
- "10060"
ms.assetid: aed77345-5eeb-41f0-96c9-db6b4a11ec6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6599092e0ef37dd9bbc15f4815c0315c77e7943b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686828"
---
# <a name="embed-an-image-in-a-report-report-builder-and-ssrs"></a><span data-ttu-id="017f0-102">在報表中內嵌影像 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="017f0-102">Embed an Image in a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="017f0-103">報表可以包含內嵌影像。</span><span class="sxs-lookup"><span data-stu-id="017f0-103">A report can include an embedded image.</span></span> <span data-ttu-id="017f0-104">內嵌影像可確保影像隨時可供報表使用，但是可能會影響報表定義 (定義報表的檔案) 的大小。</span><span class="sxs-lookup"><span data-stu-id="017f0-104">Embedding an image ensures that the image is always available to a report, but can affect the size of the report definition, the file that defines the report.</span></span> <span data-ttu-id="017f0-105">內嵌在報表中的影像會列在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="017f0-105">The images embedded in a report are listed in the Report Data pane.</span></span>  
  
 <span data-ttu-id="017f0-106">您可以在將影像加入至設計介面之前，先將影像內嵌在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="017f0-106">You might want to embed an image in the report definition before adding the image to the design surface.</span></span> <span data-ttu-id="017f0-107">如需詳細資訊，請參閱[新增背景影像 &#40;報表產生器及 SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="017f0-107">For more information, see [Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-a-report"></a><span data-ttu-id="017f0-108">若要在報表中內嵌影像</span><span class="sxs-lookup"><span data-stu-id="017f0-108">To embed an image in a report</span></span>  
  
1.  <span data-ttu-id="017f0-109">在報表設計檢視的 **[插入]** 索引標籤上，按一下 **[影像]** 。</span><span class="sxs-lookup"><span data-stu-id="017f0-109">In report design view, on the **Insert** tab, click **Image**.</span></span>  
  
2.  <span data-ttu-id="017f0-110">在設計介面上，按一下然後將方塊拖曳至所需的影像大小。</span><span class="sxs-lookup"><span data-stu-id="017f0-110">On the design surface, click and then drag a box to the desired size of the image.</span></span>  
  
3.  <span data-ttu-id="017f0-111">在 **[影像屬性]** 對話方塊的 **[一般]** 頁面上，於 **[名稱]** 文字方塊內輸入名稱，或是接受預設值。</span><span class="sxs-lookup"><span data-stu-id="017f0-111">In the **General** page of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
4.  <span data-ttu-id="017f0-112">(選擇性) 在 [工具提示]  文字方塊中，鍵入您希望使用者將滑鼠停留在轉譯報表內的影像上方時，所要出現的文字。</span><span class="sxs-lookup"><span data-stu-id="017f0-112">(Optional) In the **ToolTip** text box, type the text that you want to appear when the user hovers over the image in the rendered report.</span></span>  
  
5.  <span data-ttu-id="017f0-113">在 **[選取影像來源]** 中，選取 **[內嵌]** 。</span><span class="sxs-lookup"><span data-stu-id="017f0-113">In **Select the image source**, select **Embedded**.</span></span>  
  
6.  <span data-ttu-id="017f0-114">按一下 **[使用此影像]** 文字方塊旁邊的 **[匯入]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="017f0-114">Click the **Import** button next to the **Use this image** text box</span></span>  
  
7.  <span data-ttu-id="017f0-115">在 **[檔案類型]** 中，選取影像檔類型，瀏覽到該檔案，然後按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="017f0-115">In **Files of type**, select the image file type, navigate to the file, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="017f0-116">在 **[影像屬性]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="017f0-116">In the **Image Properties** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="017f0-117">影像隨即顯示在您在設計介面上繪製的方塊中，而且檔案會顯示在 [報表資料] 窗格的 [影像] 資料夾底下。</span><span class="sxs-lookup"><span data-stu-id="017f0-117">The image is displayed in the box you drew on the design surface, and the file is displayed under the Images folder in the Report Data pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="017f0-118">MIME 類型 (例如 bmp) 是在影像匯入時自動衍生的。</span><span class="sxs-lookup"><span data-stu-id="017f0-118">The MIME type (for example, bmp) is derived automatically when the image is imported.</span></span> <span data-ttu-id="017f0-119">若要變更 MIME 類型，請參閱下一個程序。</span><span class="sxs-lookup"><span data-stu-id="017f0-119">To change the MIME type, see the next procedure.</span></span>  
  
### <a name="optional-to-change-the-mime-type-of-an-imported-image"></a><span data-ttu-id="017f0-120">(選擇性) 若要變更匯入之影像的 MIME 類型</span><span class="sxs-lookup"><span data-stu-id="017f0-120">(optional) To change the MIME type of an imported image</span></span>  
  
1.  <span data-ttu-id="017f0-121">在 [設計] 檢視中開啟報表。</span><span class="sxs-lookup"><span data-stu-id="017f0-121">Open the report in Design view.</span></span>  
  
2.  <span data-ttu-id="017f0-122">在設計介面上選取影像。</span><span class="sxs-lookup"><span data-stu-id="017f0-122">Select the image on the design surface.</span></span> <span data-ttu-id="017f0-123">**[屬性]** 窗格會顯示影像屬性。</span><span class="sxs-lookup"><span data-stu-id="017f0-123">The **Properties** pane displays the image properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="017f0-124">如果看不到 [屬性] 窗格，請按一下 [檢視]  索引標籤上的 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="017f0-124">If the Properties pane is not visible, on the **View** tab, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="017f0-125">在 [MIMEType]  屬性旁邊的文字方塊內按一下，然後從下拉式清單中選取新的 MIME 類型。</span><span class="sxs-lookup"><span data-stu-id="017f0-125">Click in the text box next to the **MIMEType** property and select a new MIME type from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017f0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="017f0-126">See Also</span></span>  
 <span data-ttu-id="017f0-127">[影像 &#40;報表產生器及 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="017f0-127">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="017f0-128">[新增資料繫結影像 &#40;報表產生器及 SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="017f0-128">[Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="017f0-129">影像屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="017f0-129">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
