---
title: '[圖表] 索引標籤 () 的採礦模型檢視器 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.timeseries.chart.f1
ms.assetid: 8803cdbb-f1b3-436c-994d-ee662ecf64dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c4d3aefb785bf3b5495a7c4c9a0cdea334b9d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593706"
---
# <a name="chart-tab-mining-model-viewers"></a><span data-ttu-id="6c6b5-102">圖表索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="6c6b5-102">Chart Tab (Mining Model Viewers)</span></span>
  <span data-ttu-id="6c6b5-103">使用 [圖表]\*\*\*\* 窗格，即可顯示用於定型時間序列模型的歷程記錄資料以及預測值。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-103">Use the **Chart** pane to display the historical data used in training a time series model, together with the predicted values.</span></span> <span data-ttu-id="6c6b5-104">圖表的垂直軸代表序列的值，而水平軸代表時間。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-104">The vertical axis of the chart represents the value of the series, and the horizontal axis represents time.</span></span> <span data-ttu-id="6c6b5-105">虛線代表未來預測。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-105">Future predictions are represented by a dotted line.</span></span>  
  
 <span data-ttu-id="6c6b5-106">**如需詳細資訊，請參閱** [Microsoft 時間序列演算法](data-mining/microsoft-time-series-algorithm.md)、 [使用 Microsoft 時間序列檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="6c6b5-106">**For More Information:** [Microsoft Time Series Algorithm](data-mining/microsoft-time-series-algorithm.md), [Browse a Model Using the Microsoft Time Series Viewer](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="6c6b5-107">選項</span><span class="sxs-lookup"><span data-stu-id="6c6b5-107">Options</span></span>  
 <span data-ttu-id="6c6b5-108">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-108">**Refresh viewer content**</span></span>  
 <span data-ttu-id="6c6b5-109">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-109">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="6c6b5-110">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-110">**Mining Model**</span></span>  
 <span data-ttu-id="6c6b5-111">在目前採礦結構中選擇採礦模型。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-111">Choose a mining model, from those in the current mining structure.</span></span> <span data-ttu-id="6c6b5-112">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-112">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="6c6b5-113">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-113">**Viewer**</span></span>  
 <span data-ttu-id="6c6b5-114">選擇檢視器以瀏覽選取的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-114">Choose a viewer to explore the selected mining model.</span></span> <span data-ttu-id="6c6b5-115">可以使用自訂的時間序列模型檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-115">You can use the custom viewer for time series models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="6c6b5-116">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-116">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="6c6b5-117">**放大**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-117">**Zoom In**</span></span>  
 <span data-ttu-id="6c6b5-118">放大圖表。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-118">Zoom in to the chart.</span></span>  
  
 <span data-ttu-id="6c6b5-119">**縮小**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-119">**Zoom Out**</span></span>  
 <span data-ttu-id="6c6b5-120">縮小圖表。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-120">Zoom out from the chart.</span></span>  
  
 <span data-ttu-id="6c6b5-121">**將圖表縮放至視窗大小**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-121">**Scale diagram to fit window**</span></span>  
 <span data-ttu-id="6c6b5-122">縮小圖表直到整個圖表納入螢幕內。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-122">Zoom out from the chart until the whole chart fits within the screen.</span></span>  
  
 <span data-ttu-id="6c6b5-123">**Abs**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-123">**Abs**</span></span>  
 <span data-ttu-id="6c6b5-124">在兩個圖表檢視之間切換：在預設檢視中，數字相對於整體分佈來繪製圖形 (以百分比表示)。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-124">Switch between two chart views: in the default view numbers are graphed relative to the overall distribution (as percentage).</span></span> <span data-ttu-id="6c6b5-125">如果您按一下 [Abs]\*\*\*\*，則會將數字做為絕對值繪製圖形。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-125">If you click **Abs**, the numbers are graphed as absolute values.</span></span>  
  
 <span data-ttu-id="6c6b5-126">**將圖表複製到剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-126">**Copy the charts to the clipboard**</span></span>  
 <span data-ttu-id="6c6b5-127">將完整圖表複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-127">Copy the complete chart to the clipboard.</span></span>  
  
 <span data-ttu-id="6c6b5-128">**顯示偏差**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-128">**Show Deviations**</span></span>  
 <span data-ttu-id="6c6b5-129">選取這個選項，將誤差線加入到圖形中。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-129">Select this option to add error bars to the graph.</span></span> <span data-ttu-id="6c6b5-130">誤差線表示預測的變異數，因此只在預測值上顯示。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-130">Error bars represent the variance of the predictions and therefore appear only on the predicted values.</span></span>  
  
 <span data-ttu-id="6c6b5-131">**預測步驟**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-131">**Prediction steps**</span></span>  
 <span data-ttu-id="6c6b5-132">選擇您要在檢視器中查看的未來時間步驟數目。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-132">Choose how many future time steps you want to see in the viewer.</span></span>  
  
 <span data-ttu-id="6c6b5-133">**序列選取**</span><span class="sxs-lookup"><span data-stu-id="6c6b5-133">**Series selection**</span></span>  
 <span data-ttu-id="6c6b5-134">開啟對話方塊，您可以在此處選取要包含在檢視器中的數列。</span><span class="sxs-lookup"><span data-stu-id="6c6b5-134">Open a dialog box from which you can select series to include in the viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6b5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c6b5-135">See Also</span></span>  
 <span data-ttu-id="6c6b5-136">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="6c6b5-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="6c6b5-137">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="6c6b5-137">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="6c6b5-138">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="6c6b5-138">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
