---
title: 基於使用方式的優化嚮導 F1 說明 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
ms.openlocfilehash: 517c122f79421294e1dfa562665948c4dc7bf95f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704377"
---
# <a name="usage-based-optimization-wizard-f1-help"></a><span data-ttu-id="c9596-102">基於使用方式的最佳化精靈 F1 說明</span><span class="sxs-lookup"><span data-stu-id="c9596-102">Usage-Based Optimization Wizard F1 Help</span></span>
  <span data-ttu-id="c9596-103">基於使用方式的最佳化精靈，在輸出方面類似於彙總設計精靈，並可用於設計資料分割的彙總。</span><span class="sxs-lookup"><span data-stu-id="c9596-103">The Usage-Based Optimization Wizard is similar in output to the Aggregation Design Wizard, and is used to design aggregations for a partition.</span></span> <span data-ttu-id="c9596-104">然而，基於使用方式的最佳化精靈會依據查詢的特定使用模式來設計彙總，而這些使用模式是記錄於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的查詢記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="c9596-104">However, the Usage-Based Optimization Wizard designs aggregations based on the specific usage patterns of queries recorded in the query log of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="c9596-105">匯總藉由允許 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 直接從 cube 儲存體抓取預先計算的總計，而不需要重新計算每個查詢之基礎資料來源中的資料，來改善效能。</span><span class="sxs-lookup"><span data-stu-id="c9596-105">Aggregations provide performance improvements by allowing [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to retrieve pre-calculated totals directly from cube storage instead of having to recalculate data from an underlying data source for each query.</span></span>  
  
 <span data-ttu-id="c9596-106">若要從開啟 [基於使用方式的優化嚮導] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，請開啟專案的 cube 設計師 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，然後按一下 [ **Aggregations**匯總] 索引標籤。按一下工具列中的 [以使用量為基礎的**優化**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9596-106">To open the Usage-Based Optimization Wizard from within [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the cube designer for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click the **Aggregations** tab. Click the **Usage Based Optimization** button in the toolbar.</span></span>  
  
 <span data-ttu-id="c9596-107">若要從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 開啟 [基於使用方式的最佳化精靈]，請連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，然後開啟 [Cubes]\*\*\*\* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9596-107">To open the Usage-Based Optimization Wizard from within [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and then open the **Cubes** folder.</span></span> <span data-ttu-id="c9596-108">選取一個 Cube，接著開啟 **[Measure Groups]** 資料夾，並展開您要修改的量值群組。</span><span class="sxs-lookup"><span data-stu-id="c9596-108">Select a cube and then open the **Measure Groups** folder and expand the measure group that you want to modify.</span></span> <span data-ttu-id="c9596-109">以滑鼠右鍵按一下 [資料分割]\*\*\*\* 資料夾，然後選取 [基於使用方式的最佳化]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c9596-109">Right-click the **Partitions** folder and then select **Usage Based Optimization**.</span></span>  
  
 <span data-ttu-id="c9596-110">若要設計這些彙總，您可以使用彙總設計精靈。</span><span class="sxs-lookup"><span data-stu-id="c9596-110">To design these aggregations, you can use the Aggregation Design Wizard.</span></span> <span data-ttu-id="c9596-111">這個精靈會引導您執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c9596-111">This wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="c9596-112">針對資料分割、量值群組或 Cube 的儲存和快取選項，選取標準或自訂設定。</span><span class="sxs-lookup"><span data-stu-id="c9596-112">Selecting standard or custom settings for the storage and caching options of a partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="c9596-113">提供資料分割、量值群組或 Cube 所參考之物件的估計或實際計數。</span><span class="sxs-lookup"><span data-stu-id="c9596-113">Providing estimated or actual counts for objects referenced by the partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="c9596-114">指定彙總選項與限制，將設計彙總所提供的儲存和查詢效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="c9596-114">Specifying aggregation options and limits to optimize the storage and query performance delivered by designed aggregations.</span></span>  
  
-   <span data-ttu-id="c9596-115">儲存和選擇性地處理資料分割、量值群組或 Cube，以產生定義的彙總。</span><span class="sxs-lookup"><span data-stu-id="c9596-115">Saving and optionally processing the partition, measure group, or cube to generate the defined aggregations.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="c9596-116">提供的彙總設計精靈，可以依據資料分割結構的統計分析來設計彙總，以提供可受儲存體大小或估計之效能改善限制的彙總設計。</span><span class="sxs-lookup"><span data-stu-id="c9596-116">provides the Aggregation Design Wizard to design aggregations based on statistical analysis of the structure of the partition to deliver an aggregation design that can be limited by storage size or estimated performance gain.</span></span> <span data-ttu-id="c9596-117">您可以使用彙總設計精靈來改善資料分割的整體效能，但是其中的彙總設計不一定適用於商務使用者的特定需求。</span><span class="sxs-lookup"><span data-stu-id="c9596-117">You can use the Aggregation Design Wizard to improve the overall performance of a partition, but the aggregation design is not targeted to the specific needs of your business users.</span></span> <span data-ttu-id="c9596-118">基於使用方式的最佳化精靈可以提供針對這些特定需求的彙總設計，但前提是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的查詢記錄檔必須包含足以建構這種查詢的資訊。</span><span class="sxs-lookup"><span data-stu-id="c9596-118">The Usage-Based Optimization Wizard can provide an aggregation design targeted to these specific needs, but the wizard can do so only if the query log for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance contains enough information to construct such queries.</span></span>  
  
 <span data-ttu-id="c9596-119">通常這兩種精靈都會搭配使用，以改善部署之初以及經過一段時間之後的效能。</span><span class="sxs-lookup"><span data-stu-id="c9596-119">Typically, both wizards are used together to improve performance both upon deployment and over time.</span></span> <span data-ttu-id="c9596-120">在最初部署資料分割 (或包含資料分割的 Cube 或量值群組) 時，應先使用彙總設計精靈，才能提供整體效能上的益處。</span><span class="sxs-lookup"><span data-stu-id="c9596-120">The Aggregation Design Wizard should be used first, when the partition (or the cube or measure group containing the partition) is initially deployed, to provide an overall performance benefit.</span></span> <span data-ttu-id="c9596-121">在查詢記錄檔中記錄了商務使用者針對資料分割的查詢一段時間之後，您就可以使用基於使用方式的最佳化精靈，進一步改善彙總設計，將重點放在滿足商務使用者對於效能及查詢的需求上。</span><span class="sxs-lookup"><span data-stu-id="c9596-121">After a period of time during which you have recorded the queries of business users for the partition in the query log, you can then use the Usage-Based Optimization Wizard to further focus the aggregation design to better serve the performance and query requirements of your business users.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9596-122"> 如需有關設定查詢記錄的詳細資訊，請參閱＜ [設定 Analysis Services 查詢記錄](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog)＞(英文)。</span><span class="sxs-lookup"><span data-stu-id="c9596-122">For information about configuring the query log, see [Configuring the Analysis Services Query Log](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9596-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="c9596-123">In This Section</span></span>  
  
-   <span data-ttu-id="c9596-124">[選取 [分割區] 以修改 &#40;以使用方式為基礎的優化 Wizard&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="c9596-124">[Select Partitions to Modify &#40;Usage-Based Optimization Wizard&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)</span></span>  
  
-   [<span data-ttu-id="c9596-125">指定查詢準則 &#40;基於使用方式的優化 Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="c9596-125">Specify Query Criteria &#40;Usage-Based Optimization Wizard&#41;</span></span>](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="c9596-126">查看將優化的查詢，&#40;基於使用方式的優化 Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="c9596-126">Review the Queries that will be Optimized &#40;Usage-Based Optimization Wizard&#41;</span></span>](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="c9596-127">查看匯總使用量 &#40;以使用方式為基礎的基於優化 Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="c9596-127">Review Aggregation Usage &#40;Usage-Based Optimiation Wizard&#41;</span></span>](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [<span data-ttu-id="c9596-128">指定物件計數 &#40;以使用方式為基礎的優化 Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="c9596-128">Specify Object Counts &#40;Usage-Based Optimization Wizard&#41;</span></span>](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="c9596-129">設定匯總選項 &#40;基於使用方式的優化 Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="c9596-129">Set Aggregation Options &#40;Usage-Based Optimization Wizard&#41;</span></span>](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="c9596-130">正在完成 Wizard &#40;基於使用方式的優化 Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="c9596-130">Completing the Wizard &#40;Usage-Based Optimization Wizard&#41;</span></span>](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9596-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9596-131">See Also</span></span>  
 <span data-ttu-id="c9596-132">[匯總和匯總設計](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span><span class="sxs-lookup"><span data-stu-id="c9596-132">[Aggregations and Aggregation Designs](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span></span>  
 <span data-ttu-id="c9596-133">[多維度模型中的 cube](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="c9596-133">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="c9596-134">[匯總設計嚮導 F1 說明](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="c9596-134">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="c9596-135">Analysis Services 的 &#40;多維度資料的嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="c9596-135">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
