---
title: 叢集 Wizard (適用于 Excel) 的資料採礦增益集 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90500ae627bcafd1ca5ce17114dac9df9939691d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593688"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="825b2-102">叢集精靈 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="825b2-102">Cluster Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="825b2-103">![資料採礦功能區中的群集精靈](media/dmc-cluster.gif "資料採礦功能區中的群集精靈")</span><span class="sxs-lookup"><span data-stu-id="825b2-103">![Cluster wizard in Data Mining ribbon](media/dmc-cluster.gif "Cluster wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="825b2-104">叢集精靈可協助您建立模型，此模型會偵測共用類似特性的資料列，並將這些資料列分組以最大化群組間的差距。</span><span class="sxs-lookup"><span data-stu-id="825b2-104">The Cluster wizard helps you build a model that detects rows that share similar characteristics and groups them to maximize the distance between groups.</span></span> <span data-ttu-id="825b2-105">這個精靈對於尋找所有資料類型中的模式很有幫助。</span><span class="sxs-lookup"><span data-stu-id="825b2-105">This wizard is useful for finding patterns in all kinds of data.</span></span>  
  
 <span data-ttu-id="825b2-106">叢集精靈使用 Microsoft 叢集演算法，並可廣泛地加以自訂。</span><span class="sxs-lookup"><span data-stu-id="825b2-106">The Cluster wizard uses the Microsoft Clustering algorithm and can be extensively customized.</span></span> <span data-ttu-id="825b2-107">該精靈使用 Excel 資料表、Excel 範圍或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 查詢中的現有資料。</span><span class="sxs-lookup"><span data-stu-id="825b2-107">It works on existing data from an Excel table, an Excel range, or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] query.</span></span> <span data-ttu-id="825b2-108">適用于 Excel 的資料表分析工具中提供的 [偵測[類別目錄](detect-categories-table-analysis-tools-for-excel.md)] 工具提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="825b2-108">Similar functionality is provided by the [Detect Categories](detect-categories-table-analysis-tools-for-excel.md) tool, provided in the Table Analysis Tools for Excel.</span></span> <span data-ttu-id="825b2-109">但是，您無法自訂偵測類別目錄工具，且該工具必須使用 Excel 資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="825b2-109">However, the Detect Categories tool cannot be customized and must use data in Excel tables.</span></span>  
  
## <a name="using-the-cluster-wizard"></a><span data-ttu-id="825b2-110">使用叢集精靈</span><span class="sxs-lookup"><span data-stu-id="825b2-110">Using the Cluster Wizard</span></span>  
  
1.  <span data-ttu-id="825b2-111">在 [資料採礦] 功能區中 **，按一下 [** 叢集]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="825b2-111">In the Data Mining ribbon, click **Cluster**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="825b2-112">在 [**選取來源資料**] 頁面中，選取 Excel 資料表或範圍。</span><span class="sxs-lookup"><span data-stu-id="825b2-112">In the **Select Source Data** page, select an Excel table or range.</span></span> <span data-ttu-id="825b2-113">或指定外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="825b2-113">Or specify and external data source.</span></span>  
  
     <span data-ttu-id="825b2-114">如果使用外部資料來源，您可以建立自訂檢視或貼入自訂查詢文字，然後將資料集儲存為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料來源。</span><span class="sxs-lookup"><span data-stu-id="825b2-114">If you use an external data source, you can create custom views or paste in custom query text, and save the data set as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="825b2-115">在 [**群集**] 頁面上，您可以自訂模型的建立方式。</span><span class="sxs-lookup"><span data-stu-id="825b2-115">On the **Clustering** page, you can customize the way the model is built.</span></span>  
  
    -   <span data-ttu-id="825b2-116">對於**區段數目**，您可以告訴 wizard 建立固定數目的類別，或讓它自動偵測最佳的群組數目。</span><span class="sxs-lookup"><span data-stu-id="825b2-116">For **Number of segments**, you can tell the wizard to create a fixed number of categories, or let it automatically detect the optimum number of groupings.</span></span>  
  
    -   <span data-ttu-id="825b2-117">檢查 [**輸入資料行**] 清單中的資料行清單，並取消選取在建立模式時不適用的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="825b2-117">Review the list of columns in the **Input columns** list, and deselect any columns that are not useful in creating patterns.</span></span> <span data-ttu-id="825b2-118">您應排除的資料行包括識別碼、客戶名稱等。</span><span class="sxs-lookup"><span data-stu-id="825b2-118">Columns you should exclude include ID numbers, customer names, and so on.</span></span>  
  
4.  <span data-ttu-id="825b2-119">（選擇性）按一下 [**參數**] 以變更演算法參數，並自訂群集模型的行為。</span><span class="sxs-lookup"><span data-stu-id="825b2-119">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the clustering model.</span></span>  
  
5.  <span data-ttu-id="825b2-120">在 [將**資料分割成定型集和測試集**] 頁面上，指定要保留多少資料來進行測試。</span><span class="sxs-lookup"><span data-stu-id="825b2-120">In the **Split data into training and testing sets** page, specify how much data to hold out for testing.</span></span> <span data-ttu-id="825b2-121">定型模型時，一律會使用其餘資料。</span><span class="sxs-lookup"><span data-stu-id="825b2-121">The remainder is always used for training the model.</span></span>  
  
     <span data-ttu-id="825b2-122">預設設定為 30% 測試資料和 70% 定型資料。</span><span class="sxs-lookup"><span data-stu-id="825b2-122">The default setting is 30% testing data and 70% training data.</span></span>  
  
6.  <span data-ttu-id="825b2-123">在 [**完成]** 頁面上，為您的資料集和模型提供描述性的名稱，並設定下列選項來控制如何使用完成的模型：</span><span class="sxs-lookup"><span data-stu-id="825b2-123">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="825b2-124">**流覽模型**。</span><span class="sxs-lookup"><span data-stu-id="825b2-124">**Browse model**.</span></span> <span data-ttu-id="825b2-125">選取這個選項時，一旦 wizard 完成模型的處理，就會開啟 **[流覽**] 視窗以協助您流覽結果。</span><span class="sxs-lookup"><span data-stu-id="825b2-125">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="825b2-126">檢視器的內容取決於建立的模型類型。</span><span class="sxs-lookup"><span data-stu-id="825b2-126">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="825b2-127">如需詳細資訊，請參閱[流覽群集模型](browsing-a-clustering-model.md)。</span><span class="sxs-lookup"><span data-stu-id="825b2-127">For more information, see [Browsing a Clustering Model](browsing-a-clustering-model.md).</span></span>  
  
    -   <span data-ttu-id="825b2-128">**啟用 [鑽取**]。</span><span class="sxs-lookup"><span data-stu-id="825b2-128">**Enable drillthrough**.</span></span> <span data-ttu-id="825b2-129">選取此選項可檢視完成模型中的基礎資料。</span><span class="sxs-lookup"><span data-stu-id="825b2-129">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="825b2-130">只有建立決策樹模型時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="825b2-130">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="825b2-131">**使用暫時性模型**。</span><span class="sxs-lookup"><span data-stu-id="825b2-131">**Use temporary model**.</span></span> <span data-ttu-id="825b2-132">如果選取這個選項，此模型將無法儲存到伺服器。</span><span class="sxs-lookup"><span data-stu-id="825b2-132">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="825b2-133">當您關閉 Excel 時，即會刪除暫時性模型。</span><span class="sxs-lookup"><span data-stu-id="825b2-133">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-clustering-models"></a><span data-ttu-id="825b2-134">進一步了解叢集模型</span><span class="sxs-lookup"><span data-stu-id="825b2-134">More about Clustering Models</span></span>  
 <span data-ttu-id="825b2-135">您可以按一下 [ **Advanced** ]，然後使用 [**演算法參數**] 對話方塊來變更此 wizard 所使用的群集演算法。</span><span class="sxs-lookup"><span data-stu-id="825b2-135">You can change the clustering algorithm used by this wizard by clicking **Advanced** and using the **Algorithm Parameters** dialog box.</span></span>  
  
 <span data-ttu-id="825b2-136">Microsoft 群集演算法提供下列群集方法：</span><span class="sxs-lookup"><span data-stu-id="825b2-136">The Microsoft Clustering algorithm provides these clustering methods:</span></span>  
  
-   <span data-ttu-id="825b2-137">K-means - 可擴充或不可擴充。</span><span class="sxs-lookup"><span data-stu-id="825b2-137">K-means -  scalable or non-scaling.</span></span>  
  
-   <span data-ttu-id="825b2-138">Expectation Maximization (EM) - 可擴充或不可擴充。</span><span class="sxs-lookup"><span data-stu-id="825b2-138">Expectation Maximization (EM) - scalable or non-scaling.</span></span>  
  
 <span data-ttu-id="825b2-139">您也可以使用 CLUSTER_SEED 參數控制此起始值，以確保使用相同資料集的重複模型擁有相同的結果。</span><span class="sxs-lookup"><span data-stu-id="825b2-139">You can also use the CLUSTER_SEED parameter to control the starting value and ensure that repeated models using the same data set have the same results.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="825b2-140">需求</span><span class="sxs-lookup"><span data-stu-id="825b2-140">Requirements</span></span>  
 <span data-ttu-id="825b2-141">您必須連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，才能使用 [叢集] 精靈。</span><span class="sxs-lookup"><span data-stu-id="825b2-141">To use the Cluster wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="825b2-142">如需詳細資訊，請參閱[連接到來源資料 &#40;適用于 Excel&#41;的資料採礦用戶端](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="825b2-142">For more information, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825b2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="825b2-143">See Also</span></span>  
 <span data-ttu-id="825b2-144">[建立資料採礦模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="825b2-144">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="825b2-145">偵測適用于 Excel&#41;&#40;資料表分析工具的分類</span><span class="sxs-lookup"><span data-stu-id="825b2-145">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
  
