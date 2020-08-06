---
title: 匯總設計嚮導 F1 說明 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregation Design Wizard
ms.assetid: 39e23cf1-6405-4fb6-bc14-ba103314362d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ace30a07970b1871d037ebe6f31b2079f1895ffa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593234"
---
# <a name="aggregation-design-wizard-f1-help"></a><span data-ttu-id="8ae94-102">彙總設計精靈 F1 說明</span><span class="sxs-lookup"><span data-stu-id="8ae94-102">Aggregation Design Wizard F1 Help</span></span>
  <span data-ttu-id="8ae94-103">匯總藉由允許 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 直接從 cube 儲存體抓取預先計算的總計，而不需要重新計算每個查詢之基礎資料來源中的資料，來改善效能。</span><span class="sxs-lookup"><span data-stu-id="8ae94-103">Aggregations provide performance improvements by allowing [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to retrieve pre-calculated totals directly from cube storage instead of having to recalculate data from an underlying data source for each query.</span></span>  
  
 <span data-ttu-id="8ae94-104">若要設計這些彙總，您可以使用彙總設計精靈。</span><span class="sxs-lookup"><span data-stu-id="8ae94-104">To design these aggregations, you can use the Aggregation Design Wizard.</span></span> <span data-ttu-id="8ae94-105">這個精靈會引導您執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8ae94-105">This wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="8ae94-106">針對資料分割、量值群組或 Cube 的儲存和快取選項，選取標準或自訂設定。</span><span class="sxs-lookup"><span data-stu-id="8ae94-106">Selecting standard or custom settings for the storage and caching options of a partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="8ae94-107">提供資料分割、量值群組或 Cube 所參考之物件的估計或實際計數。</span><span class="sxs-lookup"><span data-stu-id="8ae94-107">Providing estimated or actual counts for objects referenced by the partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="8ae94-108">指定彙總選項與限制，將設計彙總所提供的儲存和查詢效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="8ae94-108">Specifying aggregation options and limits to optimize the storage and query performance delivered by designed aggregations.</span></span>  
  
-   <span data-ttu-id="8ae94-109">儲存和選擇性地處理資料分割、量值群組或 Cube，以產生定義的彙總。</span><span class="sxs-lookup"><span data-stu-id="8ae94-109">Saving and optionally processing the partition, measure group, or cube to generate the defined aggregations.</span></span>  
  
 <span data-ttu-id="8ae94-110">使用彙總設計精靈之後，您可以使用 [基於使用方式的最佳化精靈]，根據商務使用者的使用模式和查詢 Cube 的用戶端應用程式來設計彙總。</span><span class="sxs-lookup"><span data-stu-id="8ae94-110">After you use the Aggregation Design Wizard, you can use the Usage-Based Optimization Wizard to design aggregations based on the usage patterns of the business users and client applications that query the cube.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ae94-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="8ae94-111">In This Section</span></span>  
  
-   [<span data-ttu-id="8ae94-112">選取要修改的資料分割 &#40;匯總設計嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="8ae94-112">Select Partitions to Modify &#40;Aggregation Design Wizard&#41;</span></span>](select-partitions-to-modify-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="8ae94-113">查看匯總使用 &#40;匯總設計嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="8ae94-113">Review Aggregation Usage &#40;Aggregation Design Wizard&#41;</span></span>](review-aggregation-usage-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="8ae94-114">指定 &#40;匯總設計嚮導的物件計數&#41;</span><span class="sxs-lookup"><span data-stu-id="8ae94-114">Specify Object Counts &#40;Aggregation Design Wizard&#41;</span></span>](specify-object-counts-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="8ae94-115">設定匯總選項 &#40;匯總設計嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="8ae94-115">Set Aggregation Options &#40;Aggregation Design Wizard&#41;</span></span>](set-aggregation-options-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="8ae94-116">完成 Wizard &#40;匯總設計嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="8ae94-116">Completing the Wizard &#40;Aggregation Design Wizard&#41;</span></span>](completing-the-wizard-aggregation-design-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ae94-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ae94-117">See Also</span></span>  
 <span data-ttu-id="8ae94-118">[匯總和匯總設計](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span><span class="sxs-lookup"><span data-stu-id="8ae94-118">[Aggregations and Aggregation Designs](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span></span>  
 <span data-ttu-id="8ae94-119">[多維度模型中的 cube](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="8ae94-119">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="8ae94-120">[基於使用方式的優化嚮導 F1 說明](usage-based-optimization-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="8ae94-120">[Usage-Based Optimization Wizard F1 Help](usage-based-optimization-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="8ae94-121">Analysis Services 的 &#40;多維度資料的嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="8ae94-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
