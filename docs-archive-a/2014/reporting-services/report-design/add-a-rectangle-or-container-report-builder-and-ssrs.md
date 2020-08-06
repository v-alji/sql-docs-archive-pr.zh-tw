---
title: 新增矩形或容器 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10061"
- sql12.rtp.rptdesigner.rectangleproperties.general.f1
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fddda2f02b9f370d9742ae6add5bae444f8f55f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585037"
---
# <a name="add-a-rectangle-or-container-report-builder-and-ssrs"></a><span data-ttu-id="674bd-102">加入矩形或容器 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="674bd-102">Add a Rectangle or Container (Report Builder and SSRS)</span></span>
  <span data-ttu-id="674bd-103">當您希望使用圖形元素來區隔報表的區域、強調報表的區域或是提供一個或多個報表項目的背景時，請將矩形加入至報表中。</span><span class="sxs-lookup"><span data-stu-id="674bd-103">Add a rectangle to your report when you want a graphical element to separate areas of the report, emphasize areas of a report, or provide a background for one or more report items.</span></span> <span data-ttu-id="674bd-104">矩形也可當做容器使用，有助於控制資料區在報表中的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="674bd-104">Rectangles are also used as containers to help control the way data regions render in a report.</span></span> <span data-ttu-id="674bd-105">您可以自訂矩形的外觀，其方式是編輯矩形屬性 (如背景色彩和框線色彩)。</span><span class="sxs-lookup"><span data-stu-id="674bd-105">You can customize the appearance of a rectangle by editing rectangle properties such as the background and border colors.</span></span> <span data-ttu-id="674bd-106">如需使用矩形作為容器的詳細資訊，請參閱[矩形和線條 &#40;報表產生器及 SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) 和[在矩陣和圖表上顯示相同的資料 &#40;報表產生器&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="674bd-106">For more information about using a rectangle as a container, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-rectangle"></a><span data-ttu-id="674bd-107">若要加入矩形</span><span class="sxs-lookup"><span data-stu-id="674bd-107">To add a rectangle</span></span>  
  
1.  <span data-ttu-id="674bd-108">在 [插入]  索引標籤的 [報表項目]  群組中，按一下 [矩形]  。</span><span class="sxs-lookup"><span data-stu-id="674bd-108">On the **Insert** tab, in the **Report Items** group, click **Rectangle.**</span></span>  
  
2.  <span data-ttu-id="674bd-109">在設計介面上，按一下您要放置矩形左上角的位置，然後拖曳到您要放置圖表右下角的位置。</span><span class="sxs-lookup"><span data-stu-id="674bd-109">On the design surface, click the location where you want the upper left corner of the rectangle, and drag to where you want the lower-right corner.</span></span>  
  
     <span data-ttu-id="674bd-110">請注意，當您移動游標時，只要游標與設計介面上的其他物件對齊，就會出現「對齊線」。</span><span class="sxs-lookup"><span data-stu-id="674bd-110">Note that as you move the cursor, "snap lines" appear as the cursor lines up with other objects on the design surface.</span></span> <span data-ttu-id="674bd-111">這些線條能協助您對齊物件。</span><span class="sxs-lookup"><span data-stu-id="674bd-111">These help you if you want objects to be aligned.</span></span>  
  
### <a name="to-create-a-container"></a><span data-ttu-id="674bd-112">建立容器</span><span class="sxs-lookup"><span data-stu-id="674bd-112">To create a container</span></span>  
  
1.  <span data-ttu-id="674bd-113">將矩形報表項目加入至報表。</span><span class="sxs-lookup"><span data-stu-id="674bd-113">Add a rectangle report item to the report.</span></span>  
  
2.  <span data-ttu-id="674bd-114">將其他報表項目拖曳至矩形中。</span><span class="sxs-lookup"><span data-stu-id="674bd-114">Drag other report items into the rectangle.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="674bd-115">矩形只是您可以在矩形中建立或拖曳至矩形之項目的容器。</span><span class="sxs-lookup"><span data-stu-id="674bd-115">A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle.</span></span> <span data-ttu-id="674bd-116">如果您在已經存在設計介面上的項目周圍繪製矩形，該矩形將不會當做其容器。</span><span class="sxs-lookup"><span data-stu-id="674bd-116">If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.</span></span>  
  
### <a name="to-change-rectangle-properties-such-as-color-style-or-weight"></a><span data-ttu-id="674bd-117">若要變更色彩、樣式或粗細等矩形屬性</span><span class="sxs-lookup"><span data-stu-id="674bd-117">To change rectangle properties such as color, style, or weight</span></span>  
  
1.  <span data-ttu-id="674bd-118">選取矩形，然後在 [主資料夾] 索引標籤的 [框線]  區段中，按一下線條色彩、樣式或粗細選項。</span><span class="sxs-lookup"><span data-stu-id="674bd-118">Select the rectangle, and then click the line color, style, or weight options in the **Border** section of the Home tab.</span></span>  
  
2.  <span data-ttu-id="674bd-119">按一下 [框線]  按鈕旁的箭號，以便決定要變更矩形的哪一面。</span><span class="sxs-lookup"><span data-stu-id="674bd-119">Click the arrow next to the **Border** button to determine which sides of the rectangle to change.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="674bd-120">如果將線條樣式設定為 [**雙**線]，而線條寬度為 1 1/2 pt 或更窄，當您在報表產生器、報表設計師或報表管理員中執行報表時，線條可能不會出現雙線。</span><span class="sxs-lookup"><span data-stu-id="674bd-120">If you set the line style to **Double** and the line width is 1 1/2 pt or narrower, the line may not appear double when you run the report in Report Builder, Report Designer, or Report Manager.</span></span> <span data-ttu-id="674bd-121">當您將報表匯出為其他格式時才會出現雙線，例如 Microsoft Word 及 Acrobat PDF。</span><span class="sxs-lookup"><span data-stu-id="674bd-121">It will appear double when you export the report to other formats such as Microsoft Word and Acrobat PDF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="674bd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="674bd-122">See Also</span></span>  
 <span data-ttu-id="674bd-123">[矩形和線條 &#40;報表產生器及 SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="674bd-123">[Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="674bd-124">轉譯行為 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="674bd-124">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
