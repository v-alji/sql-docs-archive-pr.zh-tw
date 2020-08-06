---
title: 從圓形圖頂端開始繪製圓形圖值 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed010eeaf3e4d581cce2f7242144c4f73ec2895b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585007"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a><span data-ttu-id="d58d9-102">從圓形圖頂端開始繪製圓形圖值 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d58d9-102">Start Pie Chart Values at the Top of the Pie (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d58d9-103">根據預設，在圓形圖中，資料集的第一個值是從 90 度開始 (從圓形圖頂端算起)。</span><span class="sxs-lookup"><span data-stu-id="d58d9-103">By default in pie charts, the first value in the dataset starts at 90 degrees from the top of the pie.</span></span> <span data-ttu-id="d58d9-104">您可能希望第一個值是從頂端開始繪製。</span><span class="sxs-lookup"><span data-stu-id="d58d9-104">You may prefer that the first value start from the top.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a><span data-ttu-id="d58d9-105">若要從圓形圖頂端開始繪製圓形圖</span><span class="sxs-lookup"><span data-stu-id="d58d9-105">To Start the Pie Chart at the Top of the Pie</span></span>  
  
1.  <span data-ttu-id="d58d9-106">按一下圓形圖本身。</span><span class="sxs-lookup"><span data-stu-id="d58d9-106">Click the pie itself.</span></span>  
  
2.  <span data-ttu-id="d58d9-107">如果 [屬性]\*\*\*\* 窗格沒有開啟，請按一下 [檢視]\*\*\*\* 索引標籤上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d58d9-107">If the **Properties** pane is not open, on the **View** tab, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d58d9-108">在 [**屬性**] 窗格的 [**自訂屬性**] 底下，將**PieStartAngle**從**0**變更為**270**。</span><span class="sxs-lookup"><span data-stu-id="d58d9-108">In the **Properties** pane, under **Custom Attributes**, change **PieStartAngle** from **0** to **270**.</span></span>  
  
4.  <span data-ttu-id="d58d9-109">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="d58d9-109">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="d58d9-110">第一個值現在從圓形圖的頂端開始繪製。</span><span class="sxs-lookup"><span data-stu-id="d58d9-110">The first value now starts at the top of the pie chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58d9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d58d9-111">See Also</span></span>  
 <span data-ttu-id="d58d9-112">[將圖表格式化 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d58d9-112">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d58d9-113">圓形圖 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d58d9-113">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
