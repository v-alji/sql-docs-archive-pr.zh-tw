---
title: 繪製次要座標軸上的資料 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cec58820e0373bb1e9ef2d50d022e5b4ef7e962b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686772"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a><span data-ttu-id="f4a18-102">繪製次要座標軸上的資料 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f4a18-102">Plot Data on a Secondary Axis (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f4a18-103">圖表有兩種軸類型：主要及次要。</span><span class="sxs-lookup"><span data-stu-id="f4a18-103">The chart has two axis types: primary and secondary.</span></span> <span data-ttu-id="f4a18-104">在比較共用相同類別目錄，但具有不同資料範圍的值組時，次要軸很有用。</span><span class="sxs-lookup"><span data-stu-id="f4a18-104">The secondary axis is useful when comparing two value sets with two distinct data ranges that share a common category.</span></span>  
  
 <span data-ttu-id="f4a18-105">例如，假設您有一個計算 2008 年度營收及稅額的圖表。</span><span class="sxs-lookup"><span data-stu-id="f4a18-105">For example, suppose you have a chart that calculates Revenue vs. Tax for the year 2008.</span></span> <span data-ttu-id="f4a18-106">在此例中，兩個值組都共用 2008 時間週期。</span><span class="sxs-lookup"><span data-stu-id="f4a18-106">In this case, the 2008 time period is common to both value sets.</span></span> <span data-ttu-id="f4a18-107">不過，如果在同一 Y 軸上繪製這兩個數列，我們將無法進行有效的比較，因為 Y 軸的刻度會針對資料組中最大的值進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="f4a18-107">However, when both series are plotted on the same y-axis, we cannot make a useful comparison because the scale of the y-axis is optimized for the largest values in the dataset.</span></span> <span data-ttu-id="f4a18-108">如果在主要軸上顯示「營收」，而在次要軸上顯示「稅額」，就可以在 Y 軸上以每個數列本身的值刻度來顯示數列。</span><span class="sxs-lookup"><span data-stu-id="f4a18-108">If we show Revenue on the primary axis, and Tax on the secondary axis, we can display each series on its own y-axis with its own scale of values.</span></span> <span data-ttu-id="f4a18-109">數列仍會共用相同的 X 軸。</span><span class="sxs-lookup"><span data-stu-id="f4a18-109">The series still share a common x-axis.</span></span>  
  
 <span data-ttu-id="f4a18-110">如果比較的數列超過兩個，請考慮不同的方法來在圖表中比較及顯示多個數列。</span><span class="sxs-lookup"><span data-stu-id="f4a18-110">In situations where there are more than two series to be compared, consider a different approach for comparing and displaying multiple series in a chart.</span></span> <span data-ttu-id="f4a18-111">如需詳細資訊，請參閱 [圖表上的多個數列 &#40;報表產生器及 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)：</span><span class="sxs-lookup"><span data-stu-id="f4a18-111">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f4a18-112">此圖表的範例可從範例報表取得。</span><span class="sxs-lookup"><span data-stu-id="f4a18-112">An example of this chart is available as a sample report.</span></span> <span data-ttu-id="f4a18-113">如需下載這個範例報表及其他項目的詳細資訊，請參閱 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)：</span><span class="sxs-lookup"><span data-stu-id="f4a18-113">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a><span data-ttu-id="f4a18-114">若要在次要座標軸上繪製數列</span><span class="sxs-lookup"><span data-stu-id="f4a18-114">To plot a series on the secondary axis</span></span>  
  
1.  <span data-ttu-id="f4a18-115">以滑鼠右鍵按一下圖表中的數列，或以滑鼠右鍵按一下要在次要軸上顯示之 **[值]** 區域中的欄位，然後按一下 **[數列屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="f4a18-115">Right-click the series in the chart or right-click on a field in the **Values** area that you want to display on the secondary axis and click **Series Properties**.</span></span> <span data-ttu-id="f4a18-116">**[數列屬性]** 對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="f4a18-116">The **Series Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="f4a18-117">按一下 **[軸和圖表區域]** ，然後選取要啟用的次要軸、值軸或類別目錄軸。</span><span class="sxs-lookup"><span data-stu-id="f4a18-117">Click **Axes and Chart Area**, and select which of the secondary axes you want to enable, the value axis or the category axis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a18-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4a18-118">See Also</span></span>  
 <span data-ttu-id="f4a18-119">[格式化圖表上的軸標籤 &#40;報表產生器和 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4a18-119">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f4a18-120">指定軸間隔 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f4a18-120">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
