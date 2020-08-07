---
title: 將影像指定為量測計 (報表產生器和 SSRS) 的指標 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c694cdb90fb668c43eb7e9971bba967bad8dd9cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703778"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="e9775-102">將影像指定為量測計的指標 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e9775-102">Specify an Image as a Pointer on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e9775-103">量測計包含三個內建樣式，可用來自訂指標的外觀。</span><span class="sxs-lookup"><span data-stu-id="e9775-103">The gauge contains three built-in styles that can be used to customize the appearance of the pointer.</span></span> <span data-ttu-id="e9775-104">星形量測計的內建樣式如下：指針、標記和列。</span><span class="sxs-lookup"><span data-stu-id="e9775-104">For a radial gauge, the built in styles are: Needle, Marker and Bar.</span></span> <span data-ttu-id="e9775-105">線性量測計的內建樣式如下：標記、列和溫度計。</span><span class="sxs-lookup"><span data-stu-id="e9775-105">For a linear gauge, the built-in styles are Marker, Bar, and Thermometer.</span></span> <span data-ttu-id="e9775-106">如果需要唯一的指標，使用者可以建立並指定可當做完整功能之指標使用的影像。</span><span class="sxs-lookup"><span data-stu-id="e9775-106">If a unique pointer is required, the user can create and specify an image which can be used as a fully functional pointer.</span></span>  
  
 <span data-ttu-id="e9775-107">當您指定指標的影像時，影像必須具有下列規格：</span><span class="sxs-lookup"><span data-stu-id="e9775-107">When you are specifying an image for the pointer, your image must have the following specifications:</span></span>  
  
-   <span data-ttu-id="e9775-108">指標的原點或旋轉的中心必須位於影像的頂端。</span><span class="sxs-lookup"><span data-stu-id="e9775-108">The origin of the pointer, or center of rotation, must be at the top of the image.</span></span>  
  
-   <span data-ttu-id="e9775-109">指標的結尾必須指向下方。</span><span class="sxs-lookup"><span data-stu-id="e9775-109">The end of the pointer must be pointing down.</span></span>  
  
 <span data-ttu-id="e9775-110">因為指標是不規則的形狀，所以您必須指定透明色彩來隱藏指標的不必要部分。</span><span class="sxs-lookup"><span data-stu-id="e9775-110">Since the pointer is an irregular shape, you will need to specify a transparency color to hide the unnecessary portions of the image.</span></span> <span data-ttu-id="e9775-111">由於指定的色彩不會顯示在量測計上，因此請考慮使用通常不會顯示在量測計上的色彩當做透明色彩。</span><span class="sxs-lookup"><span data-stu-id="e9775-111">Consider using a color that would not normally be shown on the gauge as the transparency color, since the colors specified will not appear on the gauge.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a><span data-ttu-id="e9775-112">將影像指定為量測計的指標</span><span class="sxs-lookup"><span data-stu-id="e9775-112">To specify an image as a pointer on the gauge</span></span>  
  
1.  <span data-ttu-id="e9775-113">在 [設計] 檢視中，按一下量測計的指標。</span><span class="sxs-lookup"><span data-stu-id="e9775-113">In Design view, click the pointer of the gauge.</span></span>  
  
2.  <span data-ttu-id="e9775-114"> (選擇性) 如果量測計上沒有指標存在，請以滑鼠右鍵按一下量測計，然後選取 [**加入指標**]。</span><span class="sxs-lookup"><span data-stu-id="e9775-114">(Optional) If no pointer exists on the gauge, right-click on the gauge and select **Add Pointer**.</span></span> <span data-ttu-id="e9775-115">指標就會加入至量測計。</span><span class="sxs-lookup"><span data-stu-id="e9775-115">A pointer is added to the gauge.</span></span>  
  
3.  <span data-ttu-id="e9775-116">按一下功能區上的 [**插入**] 索引標籤，然後按兩下影像圖示。</span><span class="sxs-lookup"><span data-stu-id="e9775-116">Click the **Insert** tab on the ribbon and double-click the image icon.</span></span> <span data-ttu-id="e9775-117">[影像屬性]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e9775-117">The **Image Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="e9775-118">將影像加入至報表。</span><span class="sxs-lookup"><span data-stu-id="e9775-118">Add an image to your report.</span></span> <span data-ttu-id="e9775-119">如需詳細資訊，請參閱[在報表中內嵌影像 &#40;報表產生器和 SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e9775-119">For more information, see [Embed an Image in a Report &#40;Report Builder and SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md).</span></span>  
  
5.  <span data-ttu-id="e9775-120">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e9775-120">Open the Properties pane.</span></span>  
  
6.  <span data-ttu-id="e9775-121">在設計介面上按一下指標。</span><span class="sxs-lookup"><span data-stu-id="e9775-121">On the design surface, click on the pointer.</span></span> <span data-ttu-id="e9775-122">指標的屬性就會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e9775-122">The properties for the pointer are displayed in the Properties pane.</span></span>  
  
7.  <span data-ttu-id="e9775-123">展開 [PointerImage] 節點。</span><span class="sxs-lookup"><span data-stu-id="e9775-123">Expand the PointerImage node.</span></span>  
  
8.  <span data-ttu-id="e9775-124">在 [**來源**] 中，從下拉式清單中選取 [**內嵌**]。</span><span class="sxs-lookup"><span data-stu-id="e9775-124">In **Source**, select **Embedded** from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e9775-125">如果您的影像儲存在資料庫中或網路上，可以針對此屬性指定適當的選項。</span><span class="sxs-lookup"><span data-stu-id="e9775-125">If your image is stored in the database or on the web, you can specify the appropriate option for this property.</span></span> <span data-ttu-id="e9775-126">如需詳細資訊，請參閱[影像屬性對話方塊、一般 &#40;報表產生器和 SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e9775-126">For more information, see [Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md).</span></span>  
  
9. <span data-ttu-id="e9775-127">在 [**值**] 中，從下拉式清單中選取您的映射名稱。</span><span class="sxs-lookup"><span data-stu-id="e9775-127">In **Value**, select the name of your image from the drop-down list.</span></span>  
  
10. <span data-ttu-id="e9775-128">在 [ **TransparentColor**] 中，挑選您想要從影像中移除的色彩值。</span><span class="sxs-lookup"><span data-stu-id="e9775-128">In **TransparentColor**, pick a color value that you want to remove from the image.</span></span> <span data-ttu-id="e9775-129">這樣就會針對量測計的指標建立連續的外觀。</span><span class="sxs-lookup"><span data-stu-id="e9775-129">This will create a seamless appearance for the pointer in the gauge.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9775-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9775-130">See Also</span></span>  
 <span data-ttu-id="e9775-131">[格式化量測計上的指標 &#40;報表產生器和 SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e9775-131">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e9775-132">[將量測計加入報表 &#40;報表產生器和 SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e9775-132">[Add a Gauge to a Report &#40;Report Builder and SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e9775-133">[&#40;報表產生器和 SSRS 格式化線條、色彩和影像&#41;](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e9775-133">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e9775-134">量測計 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e9775-134">Gauges &#40;Report Builder and SSRS&#41;</span></span>](report-design/gauges-report-builder-and-ssrs.md)  
  
  
