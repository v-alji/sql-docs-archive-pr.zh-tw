---
title: 變更圖表類型 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fff24978-e3bd-4fac-8cd7-d6aa81f3cc25
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb466bed475b27206bf6837a60d0867f5fb745be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686829"
---
# <a name="change-a-chart-type-report-builder-and-ssrs"></a><span data-ttu-id="1bd8d-102">變更圖表類型 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1bd8d-102">Change a Chart Type (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1bd8d-103">當您第一次將圖表插入報表時，[**選取圖表類型**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-103">When you first insert a chart into a report, the **Select Chart Type** dialog appears.</span></span> <span data-ttu-id="1bd8d-104">如果您取消此對話方塊，預設會加入直條圖圖表類型。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-104">If you cancel this dialog, a Column chart type is added by default.</span></span>  
  
 <span data-ttu-id="1bd8d-105">在您設計報表的任何時間點，都可以將圖表類型變更為更適合報表的項目。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-105">At any point when designing the report, you can change the chart type to something more suitable to the report.</span></span> <span data-ttu-id="1bd8d-106">為資料選取正確的圖表類型非常重要，這樣才能正確加以解譯。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-106">It is important to select the correct chart type for your data so that it can be interpreted correctly.</span></span> <span data-ttu-id="1bd8d-107">您應該了解每一個圖表的特性，以判斷哪一個圖表類型最適合您的資料。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-107">You should understand each chart type's characteristics to determine what chart type is best suited for your data.</span></span> <span data-ttu-id="1bd8d-108">如需詳細資訊，請參閱 [圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-108">For more information, see [Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1bd8d-109">當多個數列顯示在圖表上時，您可能會想要變更個別數列的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-109">When multiple series are displayed on a chart, you may want to change the chart type of an individual series.</span></span> <span data-ttu-id="1bd8d-110">只有當圖表類型為區域圖、直條圖、折線圖或散佈圖時，才可以變更個別數列的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-110">You can only change the chart type of an individual series if the chart type is Area, Column, Line, or Scatter.</span></span> <span data-ttu-id="1bd8d-111">如果是所有其他圖表類型，圖表中的所有數列都將會變更為選取的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-111">For all other chart types, all series in your chart will be changed to the selected chart type.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-chart-type"></a><span data-ttu-id="1bd8d-112">變更圖表類型</span><span class="sxs-lookup"><span data-stu-id="1bd8d-112">To change the chart type</span></span>  
  
1.  <span data-ttu-id="1bd8d-113">在 [設計] 檢視中，以滑鼠右鍵按一下圖表，然後按一下 [變更圖表類型]  。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-113">In Design view, right-click the chart and then click **Change Chart Type**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1bd8d-114">當圖表上有多個數列時，您必須以滑鼠右鍵按一下您想要變更的數列，而非圖表。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-114">When there are multiple series on a chart, you must right-click on the series, not the chart, which you want to change.</span></span>  
  
2.  <span data-ttu-id="1bd8d-115">在 [選取圖表類型]  對話方塊中，從清單中選取圖表類型。</span><span class="sxs-lookup"><span data-stu-id="1bd8d-115">In the **SelectChart Type** dialog box, select a chart type from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd8d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bd8d-116">See Also</span></span>  
 <span data-ttu-id="1bd8d-117">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bd8d-117">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1bd8d-118">[量測計 &#40;報表產生器及 SSRS&#41;](gauges-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bd8d-118">[Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1bd8d-119">將圖表加入至報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1bd8d-119">Add a Chart to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
  
