---
title: 向下切入至來自于分析模型的案例資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74129c44fc92984a767a79c579a495084ae68754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599263"
---
# <a name="drill-through-to-case-data-from-a-mining-model"></a><span data-ttu-id="6dd03-102">鑽研採礦模型的案例資料</span><span class="sxs-lookup"><span data-stu-id="6dd03-102">Drill Through to Case Data from a Mining Model</span></span>
  <span data-ttu-id="6dd03-103">如果採礦模型已經設定為讓您鑽研模型案例，當您瀏覽此模型時，可以擷取有關用來建立模型之案例的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6dd03-103">If a mining model has been configured to let you drill through to model cases, when you browse the model, you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="6dd03-104">此外，如果基礎採礦結構已經設定為允許鑽研結構案例，而且您擁有適當的權限，就可以從採礦結構傳回資訊。</span><span class="sxs-lookup"><span data-stu-id="6dd03-104">Moreover, if the underlying mining structure has been configured to allow drillthrough to structure cases, and you have the appropriate permissions, you can return information from the mining structure.</span></span> <span data-ttu-id="6dd03-105">這可能包括沒有包含在採礦模型中的資料行。</span><span class="sxs-lookup"><span data-stu-id="6dd03-105">This can include columns that were not included in the mining model.</span></span>  
  
 <span data-ttu-id="6dd03-106">如果採礦結構不允許您鑽研基礎資料，但是採礦模型允許，您就可以檢視模型案例的資訊，但無法檢視採礦結構的資訊。</span><span class="sxs-lookup"><span data-stu-id="6dd03-106">If the mining structure does not allow you to drill through to the underlying data, but the mining model does, you can view information from the model cases, but not from the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6dd03-107">您可以將 `AllowDrillthrough` 屬性設定為 `True` 來新增鑽研現有採礦模型的能力。</span><span class="sxs-lookup"><span data-stu-id="6dd03-107">You can add the ability to drillthrough on an existing mining model by setting the property `AllowDrillthrough` to `True`.</span></span> <span data-ttu-id="6dd03-108">不過，在您啟用鑽研之後，必須先重新處理此模型，然後才能查看案例資料。</span><span class="sxs-lookup"><span data-stu-id="6dd03-108">However, after you enable drillthrough, the model must be reprocessed before you can see the case data.</span></span> <span data-ttu-id="6dd03-109">如需詳細資訊，請參閱 [針對採礦模型啟用鑽研](enable-drillthrough-for-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd03-109">For more information, see [Enable Drillthrough for a Mining Model](enable-drillthrough-for-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="6dd03-110">根據您所使用的檢視器類型，可以透過下列方式來選取鑽研的節點：</span><span class="sxs-lookup"><span data-stu-id="6dd03-110">Depending on the type of viewer you are using, you can select the node for drillthrough in the following ways:</span></span>  
  
|<span data-ttu-id="6dd03-111">檢視器名稱</span><span class="sxs-lookup"><span data-stu-id="6dd03-111">Viewer name</span></span>|<span data-ttu-id="6dd03-112">窗格或索引標籤名稱</span><span class="sxs-lookup"><span data-stu-id="6dd03-112">Pane or tab name</span></span>|<span data-ttu-id="6dd03-113">選取節點</span><span class="sxs-lookup"><span data-stu-id="6dd03-113">Select node</span></span>|  
|-----------------|----------------------|-----------------|  
|<span data-ttu-id="6dd03-114">**Microsoft 樹狀檢視器**</span><span class="sxs-lookup"><span data-stu-id="6dd03-114">**Microsoft Tree Viewer**</span></span>|<span data-ttu-id="6dd03-115">**決策樹**索引標籤</span><span class="sxs-lookup"><span data-stu-id="6dd03-115">**Decision Tree** tab</span></span>|<span data-ttu-id="6dd03-116">按一下樹狀節點。</span><span class="sxs-lookup"><span data-stu-id="6dd03-116">Click a tree node.</span></span><br /><br /> <span data-ttu-id="6dd03-117">**注意**請避免在節點上使用「鑽看」 `All` ，因為它可能需要很長的時間才能傳回結果。</span><span class="sxs-lookup"><span data-stu-id="6dd03-117">**Note** Avoid using drillthrough on the `All` node, because it may take a very long time to return results.</span></span>|  
|<span data-ttu-id="6dd03-118">**Microsoft 叢集檢視器**</span><span class="sxs-lookup"><span data-stu-id="6dd03-118">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="6dd03-119">**群集圖表**</span><span class="sxs-lookup"><span data-stu-id="6dd03-119">**Cluster Diagram**</span></span>|<span data-ttu-id="6dd03-120">按一下叢集節點。</span><span class="sxs-lookup"><span data-stu-id="6dd03-120">Click a cluster node.</span></span>|  
|<span data-ttu-id="6dd03-121">**Microsoft 叢集檢視器**</span><span class="sxs-lookup"><span data-stu-id="6dd03-121">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="6dd03-122">**叢集設定檔**</span><span class="sxs-lookup"><span data-stu-id="6dd03-122">**Cluster Profiles**</span></span>|<span data-ttu-id="6dd03-123">按一下群集資料行中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="6dd03-123">Click anywhere in cluster column.</span></span>|  
|<span data-ttu-id="6dd03-124">**Microsoft 關聯檢視器**</span><span class="sxs-lookup"><span data-stu-id="6dd03-124">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="6dd03-125">**規則**索引標籤</span><span class="sxs-lookup"><span data-stu-id="6dd03-125">**Rules** tab</span></span>|<span data-ttu-id="6dd03-126">按一下包含一組規則的資料列。</span><span class="sxs-lookup"><span data-stu-id="6dd03-126">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="6dd03-127">**Microsoft 關聯檢視器**</span><span class="sxs-lookup"><span data-stu-id="6dd03-127">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="6dd03-128">**專案集**索引標籤</span><span class="sxs-lookup"><span data-stu-id="6dd03-128">**Itemsets** tab</span></span>|<span data-ttu-id="6dd03-129">按一下包含項目集的資料列。</span><span class="sxs-lookup"><span data-stu-id="6dd03-129">Click a row that contains an itemset.</span></span>|  
|<span data-ttu-id="6dd03-130">**Microsoft 時序群集檢視器**</span><span class="sxs-lookup"><span data-stu-id="6dd03-130">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="6dd03-131">**規則**索引標籤</span><span class="sxs-lookup"><span data-stu-id="6dd03-131">**Rules** tab</span></span>|<span data-ttu-id="6dd03-132">按一下包含一組規則的資料列。</span><span class="sxs-lookup"><span data-stu-id="6dd03-132">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="6dd03-133">**Microsoft 時序群集檢視器**</span><span class="sxs-lookup"><span data-stu-id="6dd03-133">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="6dd03-134">**專案集**索引標籤</span><span class="sxs-lookup"><span data-stu-id="6dd03-134">**Itemsets** tab</span></span>|<span data-ttu-id="6dd03-135">按一下包含項目集的資料列。</span><span class="sxs-lookup"><span data-stu-id="6dd03-135">Click a row that contains an itemset.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="6dd03-136">有些模型無法使用鑽研。</span><span class="sxs-lookup"><span data-stu-id="6dd03-136">Some models cannot use drillthrough.</span></span> <span data-ttu-id="6dd03-137">使用鑽研的能力取決於建立模型所使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="6dd03-137">The ability to use drillthrough depends on the algorithm that was used to create the model.</span></span> <span data-ttu-id="6dd03-138">如需支援鑽研之採礦模型類型的清單，請參閱 [鑽研查詢 &#40;資料採礦&#41;](drillthrough-queries-data-mining.md)來加入鑽研現有採礦模型的功能。</span><span class="sxs-lookup"><span data-stu-id="6dd03-138">For a list of the mining model types that support drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="6dd03-139">若要檢視採礦模型中的鑽研資料</span><span class="sxs-lookup"><span data-stu-id="6dd03-139">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="6dd03-140">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需之採礦模型的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="6dd03-140">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the mining structure that contains the mining model you want.</span></span>  
  
2.  <span data-ttu-id="6dd03-141">在資料採礦設計師中，按一下 **[採礦模型檢視器]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6dd03-141">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="6dd03-142">從 [採礦模型]\*\*\*\* 下拉式清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="6dd03-142">Select the model from the **Mining Model** drop-down list.</span></span>  
  
4.  <span data-ttu-id="6dd03-143">從 [檢視器]\*\*\*\* 下拉式清單中選取一個檢視器，然後以滑鼠右鍵按一下特定的節點。</span><span class="sxs-lookup"><span data-stu-id="6dd03-143">Select a viewer from the **Viewer** drop-down list, and right-click the specific node.</span></span>  
  
5.  <span data-ttu-id="6dd03-144">選取 [鑽研]\*\*\*\*，然後選取 [僅模型資料行]\*\*\*\* 或 [模型和結構資料行]\*\*\*\*，即可開啟 [鑽研]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="6dd03-144">Select **Drill Through**, and then select either **Models Columns Only**, or **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="6dd03-145">若要將資料複製到剪貼簿，請以滑鼠右鍵按一下資料表中的任何資料列，然後選取 [全部複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6dd03-145">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd03-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dd03-146">See Also</span></span>  
 [<span data-ttu-id="6dd03-147">鑽研查詢 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="6dd03-147">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  
