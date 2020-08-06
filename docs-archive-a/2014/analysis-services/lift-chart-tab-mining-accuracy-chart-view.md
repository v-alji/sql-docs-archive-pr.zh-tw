---
title: 增益圖索引標籤 () 的挖掘精確度圖表視圖 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.liftchart.f1
ms.assetid: f1674e2e-d38e-40c7-b8d1-5585ce9a0168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cdad01ff3549140bf4fed606b1e8f9eaed10dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710937"
---
# <a name="lift-chart-tab-mining-accuracy-chart-view"></a><span data-ttu-id="2b616-102">增益圖索引標籤 (採礦精確度圖表檢視)</span><span class="sxs-lookup"><span data-stu-id="2b616-102">Lift Chart Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="2b616-103">使用 [增益圖]\*\*\*\* 窗格可檢視比較選取的採礦結構中所有選取的採礦模型的圖表。</span><span class="sxs-lookup"><span data-stu-id="2b616-103">Use the **Lift Chart** pane to view a chart that compares all the selected mining models in the selected mining structure.</span></span>  
  
 <span data-ttu-id="2b616-104">如果模型預測離散的屬性，則此窗格可以顯示增益圖或收益圖。</span><span class="sxs-lookup"><span data-stu-id="2b616-104">If the model predicts a discrete attribute, the pane can display either a lift chart or a profit chart.</span></span> <span data-ttu-id="2b616-105">如需增益圖的資訊，請參閱[增益圖 &#40;Analysis Services - 資料採礦&#41;](data-mining/lift-chart-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="2b616-105">For information about lift charts, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="2b616-106">若要建立收益圖，則必須提供有關實作採礦模型建議的成本以及預期回收的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2b616-106">To create a profit chart, you must provide additional information about the cost of implementing the recommendations of the mining model, as well as the expected return.</span></span> <span data-ttu-id="2b616-107">如需詳細資訊，請參閱[收益圖 &#40;Analysis Services - 資料採礦&#41;](data-mining/profit-chart-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="2b616-107">For more information, see [Profit Chart &#40;Analysis Services - Data Mining&#41;](data-mining/profit-chart-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="2b616-108">如果模型預測連續的屬性，則此窗格會顯示散佈圖。</span><span class="sxs-lookup"><span data-stu-id="2b616-108">If the model predicts a continuous attribute, the pane will display a scatter plot graph.</span></span>  
  
 <span data-ttu-id="2b616-109">如需採礦模型精確度測量方法的一般資訊，請參閱[增益圖 &#40;Analysis Services - 資料採礦&#41;](data-mining/lift-chart-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="2b616-109">For general information about methods of measuring the accuracy of a mining model, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2b616-110">選項</span><span class="sxs-lookup"><span data-stu-id="2b616-110">Options</span></span>  
 <span data-ttu-id="2b616-111">**圖表類型**</span><span class="sxs-lookup"><span data-stu-id="2b616-111">**Chart Type**</span></span>  
 <span data-ttu-id="2b616-112">設定要在檢視器中顯示之圖表的類型。</span><span class="sxs-lookup"><span data-stu-id="2b616-112">Sets the type of chart to display in the viewer.</span></span> <span data-ttu-id="2b616-113">您可以選取 [增益圖]\*\*\*\* 或是 [收益圖]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b616-113">You can select either **Lift Chart** or **Profit Chart**.</span></span>  
  
 <span data-ttu-id="2b616-114">**設定**</span><span class="sxs-lookup"><span data-stu-id="2b616-114">**Settings**</span></span>  
 <span data-ttu-id="2b616-115">開啟 [收益圖設定]\*\*\*\* 對話方塊，且您可以使用它設定收益圖。</span><span class="sxs-lookup"><span data-stu-id="2b616-115">Opens the **Profit Chart Settings** dialog box, which you can use to configure a profit chart.</span></span>  
  
 <span data-ttu-id="2b616-116">如果在 [資料行對應]\*\*\*\* 索引標籤中選取連續的可預測資料行，就無法使用收益圖。</span><span class="sxs-lookup"><span data-stu-id="2b616-116">The profit chart is not available if a continuous predictable column was selected in the **Column Mapping** tab.</span></span>  
  
 <span data-ttu-id="2b616-117">**複製**</span><span class="sxs-lookup"><span data-stu-id="2b616-117">**Copy**</span></span>  
 <span data-ttu-id="2b616-118">將圖表複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="2b616-118">Copies the chart to the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b616-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b616-119">See Also</span></span>  
 <span data-ttu-id="2b616-120">[&#40;資料採礦&#41;的挖掘精確度圖表設計工具](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2b616-120">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="2b616-121">[測試和驗證工作，以及如何 &#40;資料採礦&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2b616-121">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="2b616-122">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="2b616-122">Testing and Validation &#40;Data Mining&#41;</span></span>](data-mining/testing-and-validation-data-mining.md)  
  
  
