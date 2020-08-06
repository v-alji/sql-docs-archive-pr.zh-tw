---
title: 從模型檢視器使用 [鑽取] |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e5e065ad-c688-4c2c-8c82-7f3038e04915
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97bf20023009ec0e245126644d9fd38537182b2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704401"
---
# <a name="use-drillthrough-from-the-model-viewers"></a><span data-ttu-id="6af85-102">從模型檢視器使用鑽研</span><span class="sxs-lookup"><span data-stu-id="6af85-102">Use Drillthrough from the Model Viewers</span></span>
  <span data-ttu-id="6af85-103">根據模型類型，您可以從資料採礦設計師的 [採礦模型檢視器]\*\*\*\* 索引標籤上的瀏覽檢視器中使用鑽研，以瀏覽採礦模型中使用的案例或查看採礦結構中的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="6af85-103">Depending on the model type, you can use drillthrough from the browse viewers on the **Mining Model Viewer** tab of Data Mining Designer to explore the cases used in the mining model or to see additional columns in the mining structure.</span></span> <span data-ttu-id="6af85-104">雖然因為模型中的模式無法直接連結到特定案例，導致許多模型類型不支援鑽研，但下列模型類型支援鑽研。</span><span class="sxs-lookup"><span data-stu-id="6af85-104">Although many model types do not support drillthrough because the patterns in the model cannot be directly linked to specific cases, the following model types do support drillthrough.</span></span>  
  
 <span data-ttu-id="6af85-105">請注意，模型上必須已啟用鑽研，而且您必須擁有適當的權限。</span><span class="sxs-lookup"><span data-stu-id="6af85-105">Note that drillthrough must have been enabled on the model, and you must have the appropriate permissions.</span></span> <span data-ttu-id="6af85-106">無論模型是否以前已處理並具有內容，如果模型處於未處理狀態，鑽研選項也可能會停用。</span><span class="sxs-lookup"><span data-stu-id="6af85-106">The drillthrough option might also be disabled if the model is in an unprocessed state, regardless of whether the model was previously processed and has content.</span></span> <span data-ttu-id="6af85-107">若要透過使用鑽研擷取模型案例資料，結構和模型的快取必須是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="6af85-107">To retrieve model case data by using drillthrough, the cache of the structure and model must be current.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-tree-viewer"></a><span data-ttu-id="6af85-108">在 Microsoft 樹狀檢視器中使用鑽研</span><span class="sxs-lookup"><span data-stu-id="6af85-108">Use drillthrough in the Microsoft Tree Viewer</span></span>  
  
1.  <span data-ttu-id="6af85-109">在資料採礦設計師中，選取決策樹模型，然後選取 [瀏覽模型]\*\*\*\*，在 [Microsoft 樹狀檢視器]\*\*\*\* 中開啟模型。</span><span class="sxs-lookup"><span data-stu-id="6af85-109">In Data Mining Designer, select a decision trees model, and select **Browse Model** to open the model in the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="6af85-110">在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 [瀏覽]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6af85-110">In SQL Server Management Studio, right-click the model, and select **Browse**</span></span>  
  
2.  <span data-ttu-id="6af85-111">以滑鼠右鍵按一下樹狀圖表中的任何節點，然後選取 [鑽研]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6af85-111">Right-click any node in the tree graph, and select **Drill through**.</span></span>  
  
3.  <span data-ttu-id="6af85-112">選取下列其中一個選項：[僅模型資料行]\*\*\*\* 或 [模型和結構資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6af85-112">Select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="6af85-113">如果您沒有權限，選項可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="6af85-113">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="6af85-114">[鑽研]\*\*\*\* 對話方塊隨即開啟，並顯示案例資料和/或結構資料。</span><span class="sxs-lookup"><span data-stu-id="6af85-114">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="6af85-115">對話方塊的標題列也包含說明，識別執行鑽研查詢的節點。</span><span class="sxs-lookup"><span data-stu-id="6af85-115">The title bar of the dialog box also contains a description that identifies the node from which the drillthrough query was executed.</span></span>  
  
5.  <span data-ttu-id="6af85-116">以滑鼠右鍵按一下結果中的任何位置，然後選取 [全部複製]\*\*\*\*，將結果儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="6af85-116">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-cluster-viewer"></a><span data-ttu-id="6af85-117">在 Microsoft 叢集檢視器中使用鑽研</span><span class="sxs-lookup"><span data-stu-id="6af85-117">Use drillthrough in the Microsoft Cluster Viewer</span></span>  
  
1.  <span data-ttu-id="6af85-118">在資料採礦設計師中，選取叢集模型，然後選取 [瀏覽模型]\*\*\*\*，在 [Microsoft 叢集檢視器]\*\*\*\* 中開啟模型。</span><span class="sxs-lookup"><span data-stu-id="6af85-118">In Data Mining Designer, select a clustering model, and select **Browse Model** to open the model in the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="6af85-119">在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 **[流覽]**。</span><span class="sxs-lookup"><span data-stu-id="6af85-119">In SQL Server Management Studio, right-click the model, and select **Browse**.</span></span>  
  
2.  <span data-ttu-id="6af85-120">在 [叢集]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下任何節點。</span><span class="sxs-lookup"><span data-stu-id="6af85-120">On the **Cluster** tab, right-click any node.</span></span>  
  
3.  <span data-ttu-id="6af85-121">選取 [鑽研]\*\*\*\*，然後選取下列其中一個選項：[僅模型資料行]\*\*\*\* 或 [模型和結構資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6af85-121">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="6af85-122">如果您沒有權限，選項可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="6af85-122">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="6af85-123">[鑽研]\*\*\*\* 對話方塊隨即開啟，並顯示案例資料和/或結構資料。</span><span class="sxs-lookup"><span data-stu-id="6af85-123">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="6af85-124">對話方塊的標題列也包含識別案例叢集的說明。</span><span class="sxs-lookup"><span data-stu-id="6af85-124">The title bar of the dialog box also contains a description that identifies the cluster for the cases.</span></span>  
  
5.  <span data-ttu-id="6af85-125">以滑鼠右鍵按一下結果中的任何位置，然後選取 [全部複製]\*\*\*\*，將結果儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="6af85-125">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-association-rules-viewer"></a><span data-ttu-id="6af85-126">在 Microsoft 關聯規則檢視器中使用鑽研</span><span class="sxs-lookup"><span data-stu-id="6af85-126">Use drillthrough in the Microsoft Association Rules Viewer</span></span>  
  
1.  <span data-ttu-id="6af85-127">在資料採礦設計師中，選取關聯模型，然後選取 [瀏覽模型]\*\*\*\*，在 [Microsoft 關聯規則檢視器]\*\*\*\* 中開啟模型。</span><span class="sxs-lookup"><span data-stu-id="6af85-127">In Data Mining Designer, select an association model, and select **Browse Model** to open the model in the **Microsoft Association Rules Viewer**.</span></span> <span data-ttu-id="6af85-128">在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 [瀏覽]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6af85-128">In SQL Server Management Studio, right-click the model, and select **Browse**</span></span>  
  
2.  <span data-ttu-id="6af85-129">在 [規則]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下表示規則的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="6af85-129">On the **Rules** tab, right-click any row that represents a rule.</span></span> <span data-ttu-id="6af85-130">在 [項目集]\*\*\*\* 索引標籤上，按一下包含項目集的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="6af85-130">On the **Itemsets** tab, click on any row that contains an itemset.</span></span>  
  
3.  <span data-ttu-id="6af85-131">選取 [鑽研]\*\*\*\*，然後選取下列其中一個選項：[僅模型資料行]\*\*\*\* 或 [模型和結構資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6af85-131">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="6af85-132">如果您沒有權限，選項可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="6af85-132">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="6af85-133">[鑽研]\*\*\*\* 對話方塊隨即開啟，並顯示案例資料和/或結構資料。</span><span class="sxs-lookup"><span data-stu-id="6af85-133">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="6af85-134">對話方塊的標題列也包含識別規則名稱的說明。</span><span class="sxs-lookup"><span data-stu-id="6af85-134">The title bar of the dialog box also contains a description that identifies the rule name.</span></span>  
  
5.  <span data-ttu-id="6af85-135">以滑鼠右鍵按一下結果中的任何位置，然後選取 [全部複製]\*\*\*\*，將完整案例結果儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="6af85-135">Right-click anywhere in the results and select **Copy All** to save the complete case results to the Clipboard.</span></span> <span data-ttu-id="6af85-136">您也可以選取 [複製]\*\*\*\*，只複製選取的案例。</span><span class="sxs-lookup"><span data-stu-id="6af85-136">You can also select **Copy** to copy just the selected case.</span></span> <span data-ttu-id="6af85-137">如果模型包含巢狀資料表資料行，只會貼上巢狀資料表資料行的名稱；若要擷取每個案例的巢狀資料表資料行內的資料值，您必須對模型內容建立查詢。</span><span class="sxs-lookup"><span data-stu-id="6af85-137">If the model contains a nested table column, only the name of the nested table column is pasted; to retrieve the data values inside the nested table column for each case you must create a query on the model content.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-sequence-cluster-viewer"></a><span data-ttu-id="6af85-138">在 Microsoft 時序叢集檢視器中使用鑽研</span><span class="sxs-lookup"><span data-stu-id="6af85-138">Use drillthrough in the Microsoft Sequence Cluster Viewer</span></span>  
  
1.  <span data-ttu-id="6af85-139">在資料採礦設計師中，選取叢集模型，然後選取 [瀏覽模型]\*\*\*\*，在 [Microsoft 叢集檢視器]\*\*\*\* 中開啟模型。</span><span class="sxs-lookup"><span data-stu-id="6af85-139">In Data Mining Designer, select a clustering model, and select **Browse Model** to open the model in the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="6af85-140">在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 **[流覽]**。</span><span class="sxs-lookup"><span data-stu-id="6af85-140">In SQL Server Management Studio, right-click the model, and select **Browse**.</span></span>  
  
2.  <span data-ttu-id="6af85-141">在 [叢集圖表]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下表示叢集的任何節點。</span><span class="sxs-lookup"><span data-stu-id="6af85-141">On the **Cluster Diagram tab**, right-click any node that represents a cluster.</span></span> <span data-ttu-id="6af85-142">從 [叢集設定檔]\*\*\*\* 索引標籤，按一下叢集設定檔中或表示模型總母體之叢集中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="6af85-142">From the **Cluster Profiles** tab, click anywhere in a cluster profile or in the cluster representing the total model population.</span></span>  
  
3.  <span data-ttu-id="6af85-143">選取 [鑽研]\*\*\*\*，然後選取下列其中一個選項：[僅模型資料行]\*\*\*\* 或 [模型和結構資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6af85-143">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="6af85-144">如果您沒有權限，選項可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="6af85-144">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="6af85-145">[鑽研]\*\*\*\* 對話方塊隨即開啟，並顯示案例資料和/或結構資料。</span><span class="sxs-lookup"><span data-stu-id="6af85-145">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="6af85-146">對話方塊的標題列也包含識別案例叢集的說明。</span><span class="sxs-lookup"><span data-stu-id="6af85-146">The title bar of the dialog box also contains a description that identifies the cluster for the cases.</span></span>  
  
5.  <span data-ttu-id="6af85-147">以滑鼠右鍵按一下結果中的任何位置，然後選取 [全部複製]\*\*\*\*，將結果儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="6af85-147">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span> <span data-ttu-id="6af85-148">如果模型包含巢狀資料表資料行，只會貼上巢狀資料表資料行的名稱；若要擷取每個案例的巢狀資料表資料行內的資料值，您必須對模型內容建立查詢。</span><span class="sxs-lookup"><span data-stu-id="6af85-148">If the model contains a nested table column, only the name of the nested table column is pasted; to retrieve the data values inside the nested table column for each case you must create a query on the model content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af85-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af85-149">See Also</span></span>  
 <span data-ttu-id="6af85-150">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="6af85-150">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="6af85-151">[對採礦模型的鑽取](drillthrough-on-mining-models.md) </span><span class="sxs-lookup"><span data-stu-id="6af85-151">[Drillthrough on Mining Models](drillthrough-on-mining-models.md) </span></span>  
 [<span data-ttu-id="6af85-152">採礦結構的鑽研</span><span class="sxs-lookup"><span data-stu-id="6af85-152">Drillthrough on Mining Structures</span></span>](drillthrough-on-mining-structures.md)  
  
  
