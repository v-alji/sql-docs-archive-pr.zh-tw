---
title: 記載 (適用于 Excel 的資料採礦增益集) 的採礦模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- documenting models
- mining structures, managing
- mining models, managing
- model properties
ms.assetid: 0a663e11-e40c-4708-ad18-fabb6c976fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00d84f7ff1dc27d19d497dd11315d3efde603f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599252"
---
# <a name="documenting-mining-models-data-mining-add-ins-for-excel"></a><span data-ttu-id="2b19e-102">記錄採礦模型 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="2b19e-102">Documenting Mining Models (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="2b19e-103">![資料採礦功能區中的文件模型按鈕](media/dmc-docmodel.gif "資料採礦功能區中的文件模型按鈕")</span><span class="sxs-lookup"><span data-stu-id="2b19e-103">![Document Model button, Data Mining ribbon](media/dmc-docmodel.gif "Document Model button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="2b19e-104">[**檔模型**] wizard 會建立一份報表，提供有關您已建立之採礦模型的實用資訊。</span><span class="sxs-lookup"><span data-stu-id="2b19e-104">The **Document Model** wizard creates a report that provides useful information about the mining models that you have created.</span></span> <span data-ttu-id="2b19e-105">您可以藉由記錄所建立的模型來追蹤產生模型所使用之資料的來源、取得處理模型時間的其他相關資訊，以及追蹤影響模型結果的參數變更。</span><span class="sxs-lookup"><span data-stu-id="2b19e-105">By documenting the models that you create, you can track the source of the data used to generate a model, get additional information about when the model was processed, and track parameter changes that affect the results of the model.</span></span>  
  
## <a name="using-the-document-model-wizard"></a><span data-ttu-id="2b19e-106">使用文件模型精靈</span><span class="sxs-lookup"><span data-stu-id="2b19e-106">Using the Document Model Wizard</span></span>  
  
1.  <span data-ttu-id="2b19e-107">按一下 [**資料採礦**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2b19e-107">Click the **Data Mining** tab.</span></span>  
  
2.  <span data-ttu-id="2b19e-108">在 [**模型使用**方式] 群組中，按一下 [**檔模型**]。</span><span class="sxs-lookup"><span data-stu-id="2b19e-108">In the **Model Usage** group, click **Document Model**.</span></span>  
  
3.  <span data-ttu-id="2b19e-109">在 [**選取模型**] 對話方塊中，選取要報告的模型，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2b19e-109">In the **Select Model** dialog box, select the model on which to report, and then click **Next**.</span></span> <span data-ttu-id="2b19e-110">您必須針對想要記載的每個模型，分別執行 [**檔模型**]。</span><span class="sxs-lookup"><span data-stu-id="2b19e-110">You must run the **Document Model** wizard separately for each model that you want to document.</span></span>  
  
4.  <span data-ttu-id="2b19e-111">在 [**選取檔詳細資料**] 對話方塊中，選擇下列兩個選項的其中一個： [**完整資訊**] 或 [**摘要資訊**]。</span><span class="sxs-lookup"><span data-stu-id="2b19e-111">In the **Select documentation details** dialog box, choose one of two options: **Complete information** or **Summary information**.</span></span>  
  
5.  <span data-ttu-id="2b19e-112">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="2b19e-112">Click **Finish**.</span></span>  
  
6.  <span data-ttu-id="2b19e-113">Wizard 會自動建立新的工作表，其中包含指定的報表，標題為**Model 檔**，</span><span class="sxs-lookup"><span data-stu-id="2b19e-113">The wizard automatically creates a new worksheet that contains the specified report, titled **Model Documentation**,</span></span>  
  
## <a name="understanding-the-report"></a><span data-ttu-id="2b19e-114">了解報表</span><span class="sxs-lookup"><span data-stu-id="2b19e-114">Understanding the Report</span></span>  
 <span data-ttu-id="2b19e-115">當您建立記錄資料採礦模型的報表時，您可以建立摘要報表 (其中含有包含模型之名稱和描述的基本資訊)，或完整報表 (其中包含基礎結構的相關詳細資料，以及採礦模型的相關進階資訊)。</span><span class="sxs-lookup"><span data-stu-id="2b19e-115">When you create a report that documents a data mining model, you can create a summary,which contains basic information containing the name and description of the model, or a complete report, which contains details about the underlying structure and advanced information about the mining model.</span></span>  
  
 <span data-ttu-id="2b19e-116">系統會根據建立模型所使用的演算法，提供不同類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b19e-116">Depending on the algorithm that was used to create the model, different types of information is provided.</span></span> <span data-ttu-id="2b19e-117">例如，在關聯模型中，您會對於所產生之項目與規則的數目比較感興趣。</span><span class="sxs-lookup"><span data-stu-id="2b19e-117">For example, in an association model, you are more interested in knowing the number of itemsets and rules that were generated.</span></span> <span data-ttu-id="2b19e-118">但如果是群集模型，叢集的數目則比較有趣。</span><span class="sxs-lookup"><span data-stu-id="2b19e-118">For a clustering model, the number of clusters is more interesting.</span></span>  
  
 <span data-ttu-id="2b19e-119">下表列出一些選項以及報表中每個選項所提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b19e-119">The following table lists the options and the information that is provided in the report for each option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b19e-120">根據預設，報表中的資料行會設定為特定的大小。</span><span class="sxs-lookup"><span data-stu-id="2b19e-120">The columns in the report are set to a particular size by default.</span></span> <span data-ttu-id="2b19e-121">因此，如果資料行名稱或值非常冗長，則可能會看不到，或在 Excel 中顯示為 ###。</span><span class="sxs-lookup"><span data-stu-id="2b19e-121">Therefore, if any columns names or values are very long, they might not be visible, or might appear as ### in Excel.</span></span> <span data-ttu-id="2b19e-122">若要顯示這些值，您可以調整資料列的大小。</span><span class="sxs-lookup"><span data-stu-id="2b19e-122">To make the values visible, you can resize the row.</span></span> <span data-ttu-id="2b19e-123">如果有選取資料格，您可以在公式列的右邊按一下並拖曳雙箭頭，就可以顯示完整的值或字串。</span><span class="sxs-lookup"><span data-stu-id="2b19e-123">If the cell is selected, you can click and drag the double arrows at the right end of the formula bar to show the complete value or string.</span></span>  
  
### <a name="summary-report"></a><span data-ttu-id="2b19e-124">摘要報表</span><span class="sxs-lookup"><span data-stu-id="2b19e-124">Summary Report</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="2b19e-125">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="2b19e-125">**Metadata**</span></span>|<span data-ttu-id="2b19e-126">模型名稱</span><span class="sxs-lookup"><span data-stu-id="2b19e-126">Model name</span></span><br /><br /> <span data-ttu-id="2b19e-127">模型描述</span><span class="sxs-lookup"><span data-stu-id="2b19e-127">Model description</span></span><br /><br /> <span data-ttu-id="2b19e-128">演算法名稱</span><span class="sxs-lookup"><span data-stu-id="2b19e-128">Algorithm name</span></span><br /><br /> <span data-ttu-id="2b19e-129">上次處理的日期</span><span class="sxs-lookup"><span data-stu-id="2b19e-129">Date last processed</span></span>||  
|<span data-ttu-id="2b19e-130">**模型結果**</span><span class="sxs-lookup"><span data-stu-id="2b19e-130">**Model results**</span></span>|<span data-ttu-id="2b19e-131">關聯</span><span class="sxs-lookup"><span data-stu-id="2b19e-131">Association</span></span>|<span data-ttu-id="2b19e-132">項目集的計數</span><span class="sxs-lookup"><span data-stu-id="2b19e-132">Count of itemsets</span></span><br /><br /> <span data-ttu-id="2b19e-133">規則的計數</span><span class="sxs-lookup"><span data-stu-id="2b19e-133">Count of rules</span></span>|  
||<span data-ttu-id="2b19e-134">叢集</span><span class="sxs-lookup"><span data-stu-id="2b19e-134">Clustering</span></span>|<span data-ttu-id="2b19e-135">叢集的計數</span><span class="sxs-lookup"><span data-stu-id="2b19e-135">Count of clusters</span></span><br /><br /> <span data-ttu-id="2b19e-136">每個叢集的支援</span><span class="sxs-lookup"><span data-stu-id="2b19e-136">Support for each cluster</span></span>|  
||<span data-ttu-id="2b19e-137">決策樹</span><span class="sxs-lookup"><span data-stu-id="2b19e-137">Decision tree</span></span>|<span data-ttu-id="2b19e-138">樹狀結構數目</span><span class="sxs-lookup"><span data-stu-id="2b19e-138">Number of trees</span></span><br /><br /> <span data-ttu-id="2b19e-139">每個樹狀結構中的節點數目</span><span class="sxs-lookup"><span data-stu-id="2b19e-139">Number of nodes in each tree</span></span>|  
||<span data-ttu-id="2b19e-140">線性迴歸</span><span class="sxs-lookup"><span data-stu-id="2b19e-140">Linear regression</span></span>|<span data-ttu-id="2b19e-141">樹狀結構數目 (永遠為 1)</span><span class="sxs-lookup"><span data-stu-id="2b19e-141">Number of trees (always 1)</span></span><br /><br /> <span data-ttu-id="2b19e-142">節點數目 (永遠為 1)</span><span class="sxs-lookup"><span data-stu-id="2b19e-142">Number of nodes (always 1)</span></span>|  
||<span data-ttu-id="2b19e-143">貝氏機率分類</span><span class="sxs-lookup"><span data-stu-id="2b19e-143">Naïve Bayes</span></span>|<span data-ttu-id="2b19e-144">重要屬性</span><span class="sxs-lookup"><span data-stu-id="2b19e-144">Important attributes</span></span>|  
||<span data-ttu-id="2b19e-145">類神經網路</span><span class="sxs-lookup"><span data-stu-id="2b19e-145">Neural network</span></span>|<span data-ttu-id="2b19e-146">輸入節點的數目</span><span class="sxs-lookup"><span data-stu-id="2b19e-146">Number of input nodes</span></span><br /><br /> <span data-ttu-id="2b19e-147">輸出節點的數目</span><span class="sxs-lookup"><span data-stu-id="2b19e-147">Number of output nodes</span></span><br /><br /> <span data-ttu-id="2b19e-148">隱藏節點的數目</span><span class="sxs-lookup"><span data-stu-id="2b19e-148">Number of hidden nodes</span></span>|  
||<span data-ttu-id="2b19e-149">時序群集</span><span class="sxs-lookup"><span data-stu-id="2b19e-149">Sequence clustering</span></span>|<span data-ttu-id="2b19e-150">叢集數目</span><span class="sxs-lookup"><span data-stu-id="2b19e-150">Number of clusters</span></span>|  
  
### <a name="complete-report"></a><span data-ttu-id="2b19e-151">完整報表</span><span class="sxs-lookup"><span data-stu-id="2b19e-151">Complete Report</span></span>  
 <span data-ttu-id="2b19e-152">完整報表包含摘要報表中的所有資訊，加上模型中使用之資料的資料行詳細資訊以及分析結果：</span><span class="sxs-lookup"><span data-stu-id="2b19e-152">The complete report contains everything that is in the summary report, plus  detailed information about the columns of data used in the model and the results of analysis:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="2b19e-153">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="2b19e-153">**Metadata**</span></span>|<span data-ttu-id="2b19e-154">模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="2b19e-154">Model metadata</span></span>|<span data-ttu-id="2b19e-155">演算法參數與值</span><span class="sxs-lookup"><span data-stu-id="2b19e-155">Algorithm parameters and values</span></span>|  
||<span data-ttu-id="2b19e-156">資料行中繼資料</span><span class="sxs-lookup"><span data-stu-id="2b19e-156">Column metadata</span></span>|<span data-ttu-id="2b19e-157">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="2b19e-157">Column name</span></span><br /><br /> <span data-ttu-id="2b19e-158">使用量</span><span class="sxs-lookup"><span data-stu-id="2b19e-158">Usage</span></span><br /><br /> <span data-ttu-id="2b19e-159">資料類型</span><span class="sxs-lookup"><span data-stu-id="2b19e-159">Data type</span></span><br /><br /> <span data-ttu-id="2b19e-160">內容類型</span><span class="sxs-lookup"><span data-stu-id="2b19e-160">Content type</span></span><br /><br /> <span data-ttu-id="2b19e-161">值 (離散值的清單或值的範圍)</span><span class="sxs-lookup"><span data-stu-id="2b19e-161">Values (list of discrete values, or range of values)</span></span>|  
|<span data-ttu-id="2b19e-162">**模型統計資料**</span><span class="sxs-lookup"><span data-stu-id="2b19e-162">**Model statistics**</span></span>|<span data-ttu-id="2b19e-163">連續資料行</span><span class="sxs-lookup"><span data-stu-id="2b19e-163">Continuous columns</span></span>|<span data-ttu-id="2b19e-164">平均值</span><span class="sxs-lookup"><span data-stu-id="2b19e-164">Mean value</span></span><br /><br /> <span data-ttu-id="2b19e-165">最小值</span><span class="sxs-lookup"><span data-stu-id="2b19e-165">Minimum value</span></span><br /><br /> <span data-ttu-id="2b19e-166">最大值</span><span class="sxs-lookup"><span data-stu-id="2b19e-166">Maximum value</span></span><br /><br /> <span data-ttu-id="2b19e-167">均方根誤差</span><span class="sxs-lookup"><span data-stu-id="2b19e-167">Root mean square error</span></span><br /><br /> <span data-ttu-id="2b19e-168">平均絕對誤差</span><span class="sxs-lookup"><span data-stu-id="2b19e-168">Mean absolute error</span></span><br /><br /> <span data-ttu-id="2b19e-169">對數分數</span><span class="sxs-lookup"><span data-stu-id="2b19e-169">Log score</span></span><br /><br /> <span data-ttu-id="2b19e-170">迴歸公式 (僅適用於線性迴歸模型)</span><span class="sxs-lookup"><span data-stu-id="2b19e-170">Regression formula (for linear regression models only)</span></span>|  
||<span data-ttu-id="2b19e-171">離散資料行</span><span class="sxs-lookup"><span data-stu-id="2b19e-171">Discrete columns</span></span>|<span data-ttu-id="2b19e-172">通過的計數</span><span class="sxs-lookup"><span data-stu-id="2b19e-172">Count of passing</span></span><br /><br /> <span data-ttu-id="2b19e-173">失敗的計數</span><span class="sxs-lookup"><span data-stu-id="2b19e-173">Count of failing</span></span><br /><br /> <span data-ttu-id="2b19e-174">對數分數</span><span class="sxs-lookup"><span data-stu-id="2b19e-174">Log score</span></span><br /><br /> <span data-ttu-id="2b19e-175">增益</span><span class="sxs-lookup"><span data-stu-id="2b19e-175">Lift</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="2b19e-176">您可以記錄 SQL Server Analysis Services 支援的任何模型類型。</span><span class="sxs-lookup"><span data-stu-id="2b19e-176">You can document any model type that is supported by SQL Server Analysis Services.</span></span> <span data-ttu-id="2b19e-177">因此，此資料表會列出使用「資料表分析工具」或使用「資料採礦用戶端」之精靈無法建立的一些模型類型。</span><span class="sxs-lookup"><span data-stu-id="2b19e-177">Therefore, the table lists some model types that cannot be created by using the Table Analysis Tools or by using the wizards in the Data Mining Client.</span></span> <span data-ttu-id="2b19e-178">不過，您可以使用 [ **Advanced Data 挖掘查詢編輯器**] 來建立所有模型類型。</span><span class="sxs-lookup"><span data-stu-id="2b19e-178">However, you can create all model types by using the **Advanced Data Mining Query Editor**.</span></span> <span data-ttu-id="2b19e-179">如需詳細資訊，請參閱[SQL Server 資料採礦增益集&#41;的查詢 &#40;](query-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="2b19e-179">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b19e-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b19e-180">See Also</span></span>  
 [<span data-ttu-id="2b19e-181">&#40;適用于 Excel 的資料採礦增益集部署和調整採礦模型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b19e-181">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
