---
title: '[叢集設定檔] 索引標籤 () 的 [模型檢視器] |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.profiles.f1
ms.assetid: 1ebafa1f-74e9-4c05-b278-a690fa8543bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7ec1ce5b5204ae81a9313ca7b7e5df58c98c5da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593687"
---
# <a name="cluster-profiles-tab-mining-model-viewer"></a><span data-ttu-id="153fd-102">叢集設定檔索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="153fd-102">Cluster Profiles Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="153fd-103">使用 **[叢集設定檔]** 索引標籤以取得演算法在叢集模型中所發現之叢集的整體檢視。</span><span class="sxs-lookup"><span data-stu-id="153fd-103">Use the **Cluster Profiles** tab for an overall view of the clusters that the algorithm discovered within a clustering model.</span></span> <span data-ttu-id="153fd-104">索引標籤會顯示每一個屬性，以及該屬性在每一個叢集中的分佈。</span><span class="sxs-lookup"><span data-stu-id="153fd-104">The tab displays each attribute, together with the distribution of the attribute in each cluster.</span></span>  
  
 <span data-ttu-id="153fd-105">**如需詳細資訊，請參閱** [Microsoft 叢集演算法](data-mining/microsoft-clustering-algorithm.md)、 [使用 Microsoft 叢集檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="153fd-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="153fd-106">選項</span><span class="sxs-lookup"><span data-stu-id="153fd-106">Options</span></span>  
 <span data-ttu-id="153fd-107">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="153fd-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="153fd-108">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="153fd-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="153fd-109">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="153fd-109">**Mining Model**</span></span>  
 <span data-ttu-id="153fd-110">在目前採礦結構中選擇採礦模型。</span><span class="sxs-lookup"><span data-stu-id="153fd-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="153fd-111">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="153fd-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="153fd-112">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="153fd-112">**Viewer**</span></span>  
 <span data-ttu-id="153fd-113">選擇用來檢視選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="153fd-113">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="153fd-114">可以使用自訂的採礦模型檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。</span><span class="sxs-lookup"><span data-stu-id="153fd-114">You can use the custom viewer for the mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="153fd-115">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="153fd-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="153fd-116">**顯示圖例**</span><span class="sxs-lookup"><span data-stu-id="153fd-116">**Show Legend**</span></span>  
 <span data-ttu-id="153fd-117">選取此選項可顯示圖例符號，該圖例符號會顯示檢視器中的色彩與 [狀態]\*\*\*\* 資料行中的值之間的對應。</span><span class="sxs-lookup"><span data-stu-id="153fd-117">Select this option to display a key that shows the mapping of colors in the viewer to values in the **States** column.</span></span>  
  
 <span data-ttu-id="153fd-118">**長條圖列**</span><span class="sxs-lookup"><span data-stu-id="153fd-118">**Histogram Bars**</span></span>  
 <span data-ttu-id="153fd-119">變更此值可控制每個長條圖中包含的狀態數目。</span><span class="sxs-lookup"><span data-stu-id="153fd-119">Change this value to control how many states are included in each histogram.</span></span> <span data-ttu-id="153fd-120">如果狀態的總數超出您選擇要顯示的狀態，長條圖中會顯示機率最高的狀態，而其餘的狀態將會分組放入 **[其他]** 中。</span><span class="sxs-lookup"><span data-stu-id="153fd-120">If there are more states than you choose to display, the states with the highest probability are shown in the histogram, and the remaining states are grouped together into **Other**.</span></span>  
  
 <span data-ttu-id="153fd-121">**屬性**</span><span class="sxs-lookup"><span data-stu-id="153fd-121">**Attributes**</span></span>  
 <span data-ttu-id="153fd-122">列出位於叢集模型中的資料行。</span><span class="sxs-lookup"><span data-stu-id="153fd-122">Lists the columns that are in the clustering model.</span></span> <span data-ttu-id="153fd-123">每個屬性的長條圖都會顯示該屬性在演算法所識別叢集之間的分佈情形。</span><span class="sxs-lookup"><span data-stu-id="153fd-123">The histograms for each attribute show how the attribute is distributed among the clusters identified by the algorithm.</span></span>  
  
 <span data-ttu-id="153fd-124">**狀態**</span><span class="sxs-lookup"><span data-stu-id="153fd-124">**States**</span></span>  
 <span data-ttu-id="153fd-125">提供圖例符號，用於表示代表叢集的對應資料列中每個狀態的色彩，或表示連續數值分佈的菱形滑動軸。</span><span class="sxs-lookup"><span data-stu-id="153fd-125">Provides a key that either denotes what color represents each state in the corresponding row of clusters, or a slider with diamond that indicates the distribution of continuous numeric values.</span></span> <span data-ttu-id="153fd-126">可以使用 **[顯示圖例]** 核取方塊來顯示或隱藏此資料行。</span><span class="sxs-lookup"><span data-stu-id="153fd-126">You can show or hide this column by using the **Show Legend** check box.</span></span>  
  
 <span data-ttu-id="153fd-127">**叢集設定檔**</span><span class="sxs-lookup"><span data-stu-id="153fd-127">**Cluster Profiles**</span></span>  
 <span data-ttu-id="153fd-128">此區段會針對模型中的每個叢集包含一個資料行。</span><span class="sxs-lookup"><span data-stu-id="153fd-128">This section contains a column for each cluster in the model.</span></span> <span data-ttu-id="153fd-129">針對每個屬性，長條圖只會顯示屬性值在該叢集中的分佈。</span><span class="sxs-lookup"><span data-stu-id="153fd-129">For each attribute, the histogram shows the distribution of the values in the attribute for just that cluster.</span></span> <span data-ttu-id="153fd-130">此圖表還包含 **[母體]** 資料行，該資料行也使用長條圖來顯示每個屬性值在模型中所有案例的分佈。</span><span class="sxs-lookup"><span data-stu-id="153fd-130">The chart also has a column for **Population**, which also uses histograms to display the distribution of values for each attribute, but for all cases in the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="153fd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="153fd-131">See Also</span></span>  
 <span data-ttu-id="153fd-132">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="153fd-132">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="153fd-133">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="153fd-133">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="153fd-134">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="153fd-134">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
