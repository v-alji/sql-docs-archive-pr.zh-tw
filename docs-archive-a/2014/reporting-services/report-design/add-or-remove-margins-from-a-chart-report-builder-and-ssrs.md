---
title: 新增或移除圖表中的邊界 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d8bad99591964540bcd14fc5609560a3d324515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703870"
---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="f4f94-102">加入或移除圖表中的邊界 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f4f94-102">Add or Remove Margins from a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f4f94-103">在直條圖和散佈圖類型中，圖表會自動在 X 軸的端點加入側邊界。</span><span class="sxs-lookup"><span data-stu-id="f4f94-103">In Column and Scatter chart types, the chart automatically adds side margins on the ends of the x-axis.</span></span> <span data-ttu-id="f4f94-104">在橫條圖類型中，圖表會自動在 Y 軸的端點加入側邊界。</span><span class="sxs-lookup"><span data-stu-id="f4f94-104">In Bar chart types, the chart automatically adds side margins on the ends of the y-axis.</span></span> <span data-ttu-id="f4f94-105">在所有其他圖表類型中，圖表中都不會加入側邊界。</span><span class="sxs-lookup"><span data-stu-id="f4f94-105">In all other chart types, the chart does not add side margins.</span></span> <span data-ttu-id="f4f94-106">您不可以變更邊界的大小。</span><span class="sxs-lookup"><span data-stu-id="f4f94-106">You cannot change the size of the margin.</span></span>  
  
 <span data-ttu-id="f4f94-107">此主題不適用於圓形圖、環圈圖、漏斗圖或金字塔圖等圖表類型。</span><span class="sxs-lookup"><span data-stu-id="f4f94-107">This topic does not apply to pie, doughnut, funnel, or pyramid chart types.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-or-disable-side-margins"></a><span data-ttu-id="f4f94-108">啟用或停用側邊界</span><span class="sxs-lookup"><span data-stu-id="f4f94-108">To enable or disable side margins</span></span>  
  
1.  <span data-ttu-id="f4f94-109">以滑鼠右鍵按一下座標軸，然後選取 [軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="f4f94-109">Right-click the axis and select **Axis Properties**.</span></span> <span data-ttu-id="f4f94-110">[垂直軸屬性]  或 [水平軸屬性]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f4f94-110">The **Vertical** or **HorizontalAxis Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="f4f94-111">在 [軸選項]  頁面上，設定 [側邊界]  屬性：</span><span class="sxs-lookup"><span data-stu-id="f4f94-111">On the **Axis Options** page, set the **Side margins** property:</span></span>  
  
    -   <span data-ttu-id="f4f94-112">**自動** ：圖表將會判斷是否要根據圖表類型加入側邊界。</span><span class="sxs-lookup"><span data-stu-id="f4f94-112">**Auto** The chart will determine whether to add a side margin based on the chart type.</span></span>  
  
    -   <span data-ttu-id="f4f94-113">**停用** ：橫條圖、直條圖和散佈圖不會有側邊界。</span><span class="sxs-lookup"><span data-stu-id="f4f94-113">**Disabled** Bar, column, and scatter charts will have no side margins.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4f94-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4f94-114">See Also</span></span>  
 <span data-ttu-id="f4f94-115">[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4f94-115">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f4f94-116">[軸屬性對話方塊、軸選項 &#40;報表產生器及 SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4f94-116">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f4f94-117">[指定軸間隔 &#40;報表產生器及 SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4f94-117">[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f4f94-118">[將軸標籤格式化成日期或貨幣 &#40;報表產生器及 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4f94-118">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f4f94-119">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f4f94-119">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
