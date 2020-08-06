---
title: 矩形和線條 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 96b795c3edeabb938e836be3486e28e08737a8e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599352"
---
# <a name="rectangles-and-lines-report-builder-and-ssrs"></a><span data-ttu-id="8d7ed-102">矩形和線條 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8d7ed-102">Rectangles and Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8d7ed-103">矩形和線條可在報表內建立視覺效果。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-103">Rectangles and lines can create visual effects within a report.</span></span> <span data-ttu-id="8d7ed-104">您可以從 [主資料夾] 索引標籤的 [框線] 區段設定這些報表項目的顯示屬性，而且可以使用 [屬性] 窗格來設定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-104">You can set display properties on these report items from the Border section of the Home tab, and set other properties by using the Properties pane.</span></span> <span data-ttu-id="8d7ed-105">您可以將背景色彩或影像、工具提示或書籤等功能加入至矩形。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-105">You can add features like a background color or image, a tooltip, or a bookmark to a rectangle.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rectangles-and-lines-as-report-parts"></a><a name="RectanglesLinesReportParts"></a> <span data-ttu-id="8d7ed-106">矩形和線條做為報表組件</span><span class="sxs-lookup"><span data-stu-id="8d7ed-106">Rectangles and Lines as Report Parts</span></span>  
 <span data-ttu-id="8d7ed-107">您可以將矩形及其包含的項目當做報表組件，與報表分開發行。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-107">You can publish rectangles with the items that they contain separately from the report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="8d7ed-108">您無法發行矩形內的報表項目做為報表組件。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-108">You cannot publish the report items within the rectangle as report parts.</span></span> <span data-ttu-id="8d7ed-109">將矩形加入至報表時，會獲得矩形和其中包含的項目。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-109">When people add the rectangle to a report, they get the rectangle and the items it contains.</span></span>  
  

  
##  <a name="using-a-rectangle-as-a-container"></a><a name="RectangleAsContainer"></a> <span data-ttu-id="8d7ed-110">使用矩形做為容器</span><span class="sxs-lookup"><span data-stu-id="8d7ed-110">Using a Rectangle as a Container</span></span>  
 <span data-ttu-id="8d7ed-111">您可以使用矩形做為其他項目的容器。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-111">You can use a rectangle as a container for other items.</span></span> <span data-ttu-id="8d7ed-112">當您移動矩形時，包含在矩形中的項目會跟著它移動。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-112">When you move the rectangle, the items that are contained within the rectangle move along with it.</span></span> <span data-ttu-id="8d7ed-113">矩形內部的項目會以其 **Parent** 屬性顯示矩形的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-113">An item within the rectangle shows the name of the rectangle in its **Parent** property.</span></span> <span data-ttu-id="8d7ed-114">如需使用矩形作為容器的詳細資訊，請參閱[新增矩形或容器 &#40;報表產生器及 SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md) 和[在矩陣和圖表上顯示相同的資料 &#40;報表產生器&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-114">For more information about using a rectangle as a container, see [Add a Rectangle or Container &#40;Report Builder and SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d7ed-115">矩形只是您可以在矩形中建立或拖曳至矩形之項目的容器。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-115">A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle.</span></span> <span data-ttu-id="8d7ed-116">如果您在已經存在設計介面上的項目周圍繪製矩形，該矩形將不會當做其容器。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-116">If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.</span></span> <span data-ttu-id="8d7ed-117">該矩形不會列在項目的 Parent 屬性中。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-117">The rectangle will not be listed in the item's Parent property.</span></span>  
  
 <span data-ttu-id="8d7ed-118">使用矩形來包含報表項目時，請考慮在報表轉譯時，可能對項目造成的整體影響。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-118">When using rectangles to contain report items, consider how the items will be affected as a whole during report rendering.</span></span> <span data-ttu-id="8d7ed-119">包含重複資料列的報表項目 (例如資料表) 會展開，以容納查詢所傳回的資料，而這會影響矩形中之其他項目的定位。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-119">Report items that contain repeated rows of data (for example, tables) will expand to accommodate the data that is returned by a query, and this affects the positioning of other items in the rectangle.</span></span> <span data-ttu-id="8d7ed-120">如果項目放在資料區域之下，資料表會將項目往下推。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-120">A table will push items down if they are positioned below the data region.</span></span> <span data-ttu-id="8d7ed-121">若要將項目放在固定位置，可以將報表項目放在一個上邊緣位於資料表下邊緣上方的矩形中。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-121">To anchor an item in place, you can place the report item inside of a rectangle that has an upper edge above the lower edge of the table.</span></span> <span data-ttu-id="8d7ed-122">如需詳細資訊，請參閱[轉譯行為 &#40;報表產生器及 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-122">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="adding-a-report-border"></a><a name="ReportBorder"></a> <span data-ttu-id="8d7ed-123">加入報表框線</span><span class="sxs-lookup"><span data-stu-id="8d7ed-123">Adding a Report Border</span></span>  
 <span data-ttu-id="8d7ed-124">您可以藉由將框線加入頁首、頁尾和報表主體本身來在報表中加入框線，而不必加入線條或矩形。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-124">You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.</span></span> <span data-ttu-id="8d7ed-125">如需詳細資訊，請參閱 [在報表中加入框線 &#40;報表產生器及 SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8d7ed-125">For more information, see [Add a Border to a Report &#40;Report Builder and SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="8d7ed-126">How To 主題</span><span class="sxs-lookup"><span data-stu-id="8d7ed-126">How-To Topics</span></span>  
 [<span data-ttu-id="8d7ed-127">在報表中加入框線 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8d7ed-127">Add a Border to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-border-to-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="8d7ed-128">加入矩形或容器 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8d7ed-128">Add a Rectangle or Container &#40;Report Builder and SSRS&#41;</span></span>](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="8d7ed-129">加入和修改線條 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8d7ed-129">Add and Modify a Line &#40;Report Builder and SSRS&#41;</span></span>](add-and-modify-a-line-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="8d7ed-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d7ed-130">See Also</span></span>  
 [<span data-ttu-id="8d7ed-131">加入矩形或容器 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8d7ed-131">Add a Rectangle or Container &#40;Report Builder and SSRS&#41;</span></span>](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
  
