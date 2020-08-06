---
title: 新增背景影像 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c777fefb-8695-44a7-b5cd-a18c587583f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7bc15e1b063a73c463cdb1e7e99075af2a3dce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707169"
---
# <a name="add-a-background-image-report-builder-and-ssrs"></a><span data-ttu-id="22a68-102">加入背景影像 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="22a68-102">Add a Background Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="22a68-103">您可以將背景影像加入至報表項目 (如矩形、文字方塊、清單、矩陣、資料表和部分圖表) 或是加入至報表區段 (如頁首、頁尾或報表主體)。</span><span class="sxs-lookup"><span data-stu-id="22a68-103">You can add a background image to a report item such as a rectangle, text box, list, matrix, table, and some parts of a chart, or a report section such as the page header, page footer, or report body.</span></span> <span data-ttu-id="22a68-104">您可以針對在 [屬性] 窗格中顯示 **[BackgroundImage]** 之報表設計介面上的任何選定項目來定義背景影像。</span><span class="sxs-lookup"><span data-stu-id="22a68-104">You can define a background image for any selected item on the report design surface that displays **BackgroundImage** in the Properties pane.</span></span> <span data-ttu-id="22a68-105">如同其他影像，背景影像可以是報表伺服器上影像的 URL、資料集欄位中的影像，或是報表定義中內嵌的影像。</span><span class="sxs-lookup"><span data-stu-id="22a68-105">Like other images, the background image can be a URL to an image on the report server, an image from a dataset field, or an image embedded in the report definition.</span></span> <span data-ttu-id="22a68-106">若要使用內嵌在報表中的影像，您必須先將影像加入至報表定義，然後才可以將影像加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="22a68-106">To use an image embedded in the report, you must first add the image to the report definition before you can add the image to the design surface.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-the-report-definition"></a><span data-ttu-id="22a68-107">將影像內嵌在報表定義中</span><span class="sxs-lookup"><span data-stu-id="22a68-107">To embed an image in the report definition</span></span>  
  
1.  <span data-ttu-id="22a68-108">在 [報表資料] 窗格中，以滑鼠右鍵按一下 [影像]  節點，然後按一下 [新增影像]  。</span><span class="sxs-lookup"><span data-stu-id="22a68-108">In the Report Data pane, right-click the **Images** node, and then click **Add Image**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="22a68-109">如果看不到 [報表資料] 窗格，請按一下 [檢視]  索引標籤上的 [報表資料]  。</span><span class="sxs-lookup"><span data-stu-id="22a68-109">If the Report Data pane is not visible, on the **View** tab, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="22a68-110">瀏覽至您要內嵌在報表定義中的影像，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="22a68-110">Navigate to the image you want to embed in your report definition, and then click **OK**.</span></span>  
  
### <a name="to-add-a-background-image"></a><span data-ttu-id="22a68-111">加入背景影像</span><span class="sxs-lookup"><span data-stu-id="22a68-111">To add a background image</span></span>  
  
1.  <span data-ttu-id="22a68-112">在報表設計檢視中，選取您想要將背景影像加入其中的報表項目。</span><span class="sxs-lookup"><span data-stu-id="22a68-112">In report design view, select the report item to which you want to add a background image.</span></span>  
  
2.  <span data-ttu-id="22a68-113">如果看不到 [屬性] 窗格，請選取 **[檢視]** 索引標籤上的 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="22a68-113">If the Properties pane is not visible, on the **View** tab, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="22a68-114">在 [屬性] 窗格中，展開 **[BackgroundImage]** ，並執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="22a68-114">In the Properties pane, expand **BackgroundImage**, and then do the following:</span></span>  
  
    -   <span data-ttu-id="22a68-115">如果是內嵌的影像：</span><span class="sxs-lookup"><span data-stu-id="22a68-115">For an embedded image:</span></span>  
  
         <span data-ttu-id="22a68-116">將 **[來源]** 設定為 **[內嵌]** 。</span><span class="sxs-lookup"><span data-stu-id="22a68-116">Set **Source** to **Embedded**.</span></span>  
  
         <span data-ttu-id="22a68-117">將 **[值]** 設定為內嵌在報表中之影像的名稱。</span><span class="sxs-lookup"><span data-stu-id="22a68-117">Set **Value** to the name of an image that is embedded in the report.</span></span>  
  
    -   <span data-ttu-id="22a68-118">如果是外部影像：</span><span class="sxs-lookup"><span data-stu-id="22a68-118">For an external image:</span></span>  
  
         <span data-ttu-id="22a68-119">將 **[來源]** 設定為 **[外部]** 。</span><span class="sxs-lookup"><span data-stu-id="22a68-119">Set **Source** to **External**.</span></span>  
  
         <span data-ttu-id="22a68-120">將 **[值]** 設定為影像的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="22a68-120">Set **Value** to a valid path to an image.</span></span> <span data-ttu-id="22a68-121">這可以位於原生模式或 SharePoint 整合模式的報表伺服器上，也可以位於其他任何網站上。</span><span class="sxs-lookup"><span data-stu-id="22a68-121">This can be on a report server in native mode or SharePoint integrated mode, or it can be on any other Web site.</span></span> <span data-ttu-id="22a68-122">如需詳細資訊，請參閱[新增外部影像 &#40;報表產生器及 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="22a68-122">For more information, see [Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).</span></span>  
  
    -   <span data-ttu-id="22a68-123">如果是包含在報表項目所連接之資料庫欄位中的影像：</span><span class="sxs-lookup"><span data-stu-id="22a68-123">For an image is that is contained in a field in the database to which the report item is connected:</span></span>  
  
         <span data-ttu-id="22a68-124">將 **[來源]** 設定為 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="22a68-124">Set **Source** to **Database**.</span></span>  
  
         <span data-ttu-id="22a68-125">將 **[值]** 設定為報表資料集中欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="22a68-125">Set **Value** to the name of a field in the report dataset.</span></span> <span data-ttu-id="22a68-126">如需詳細資訊，請參閱[新增資料繫結影像 &#40;報表產生器及 SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="22a68-126">For more information, see [Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).</span></span>  
  
         <span data-ttu-id="22a68-127">針對 **MIMEType** 或檔案格式，選取適用於影像的 MIME 類型，例如 .bmp。</span><span class="sxs-lookup"><span data-stu-id="22a68-127">For **MIMEType**, or file format, select the appropriate MIME type for the image-for example, .bmp.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="22a68-128">唯有 **[來源]** 屬性設定為 **[資料庫]** 時，MIMEType 才適用。</span><span class="sxs-lookup"><span data-stu-id="22a68-128">MIMEType applies only if the **Source** property is set to **Database**.</span></span> <span data-ttu-id="22a68-129">如果 **[來源]** 屬性設定為 **[外部]** 或 **[內嵌]** ，就會忽略 **[MIMEType]** 的值。</span><span class="sxs-lookup"><span data-stu-id="22a68-129">If the **Source** property is set to **External** or **Embedded**, the value of **MIMEType** is ignored.</span></span>  
  
    -   <span data-ttu-id="22a68-130">針對 **[BackgroundRepeat]** ，請選取運算式、 **[Default]** 、 **[Repeat]** 、 **[RepeatX]** 、 **[RepeatY]** 或 **[Clip]** 。</span><span class="sxs-lookup"><span data-stu-id="22a68-130">For **BackgroundRepeat**, select an expression, **Default**, **Repeat**, **RepeatX**, or **RepeatY**, or **Clip**.</span></span>  
  
         <span data-ttu-id="22a68-131">如果是圖表中的背景影像， **[BackgroundRepeat]** 可以設定為 **[Default]** 、 **[Repeat]** 、 **[Fit]** 和 **[Clip]** ，但是不能設定為 **[RepeatX]** 或 **[RepeatY]** 。</span><span class="sxs-lookup"><span data-stu-id="22a68-131">For background images in a chart, **BackgroundRepeat** can be set to **Default**, **Repeat**, **Fit**, and **Clip**, but not **RepeatX** or **RepeatY**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a68-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22a68-132">See Also</span></span>  
 <span data-ttu-id="22a68-133">[影像 &#40;報表產生器及 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22a68-133">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="22a68-134">影像屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="22a68-134">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
