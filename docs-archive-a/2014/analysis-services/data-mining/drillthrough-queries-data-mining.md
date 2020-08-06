---
title: 資料採礦)  (的鑽取查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- AllowDrillThrough property
- drillthrough [Analysis Services]
- drillthrough [DMX]
ms.assetid: 246c784b-1b0c-4f0b-96f7-3af265e67051
author: minewiskan
ms.author: owend
ms.openlocfilehash: 21e8c6f7cb6938e629be9d252c208c61c04d17d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598673"
---
# <a name="drillthrough-queries-data-mining"></a><span data-ttu-id="d3bbb-102">鑽研查詢 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="d3bbb-102">Drillthrough Queries (Data Mining)</span></span>
  <span data-ttu-id="d3bbb-103">*「鑽研查詢」* (Drillthrough query) 可讓您傳送查詢至採礦模型，以擷取基礎案例或結構的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-103">A *drillthrough query* lets you retrieve details from the underlying cases or structure data, by sending a query to the mining model.</span></span> <span data-ttu-id="d3bbb-104">如果您想要檢視用來定型模型的案例與用來測試模型的案例，或者您想要查看案例資料的其他詳細資料，鑽研就很有用。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-104">Drillthrough is useful if you want to view the cases that were used to train the model, versus the cases that are used to test the model, or if you want to see additional details from the case data.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d3bbb-105">資料採礦提供了兩種不同的鑽研選項：</span><span class="sxs-lookup"><span data-stu-id="d3bbb-105">Data Mining provides two different options for drillthrough:</span></span>  
  
-   <span data-ttu-id="d3bbb-106">鑽研到 **模型案例**</span><span class="sxs-lookup"><span data-stu-id="d3bbb-106">Drilling through to the **model cases**</span></span>  
  
     <span data-ttu-id="d3bbb-107">當您想要從模型中的特定模式（例如，決策樹的叢集或分支）移至模型案例時，會使用 [鑽取]，並查看有關個別案例的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-107">Drillthrough to model cases is used when you want to go from a specific pattern in the model-such as a cluster or branch of a decision tree-and view details about the individual cases.</span></span>  
  
-   <span data-ttu-id="d3bbb-108">鑽研到 **結構案例**</span><span class="sxs-lookup"><span data-stu-id="d3bbb-108">Drilling through to the **structure cases**</span></span>  
  
     <span data-ttu-id="d3bbb-109">當結構包含可能無法用於模型的資訊時，就適合鑽研到結構案例。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-109">Drillthrough to structure cases is used when the structure contains information that might not be available in the model.</span></span> <span data-ttu-id="d3bbb-110">例如，您不會將客戶連絡資訊用於叢集模型中，即使資料包含在結構中也一樣。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-110">For example, you would not use customer contact information in a clustering model, even if the data was included in the structure.</span></span> <span data-ttu-id="d3bbb-111">不過，在您建立模型之後，可能會想要擷取分組成特定叢集之客戶的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-111">However, after you create the model, you might want to retrieve contact information for customers who are grouped into a particular cluster.</span></span>  
  
 <span data-ttu-id="d3bbb-112">本章節提供如何建立這些查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-112">This section provides examples of how you can create these queries.</span></span>  
  
 [<span data-ttu-id="d3bbb-113">在資料採礦設計師中使用鑽研</span><span class="sxs-lookup"><span data-stu-id="d3bbb-113">Using Drillthrough in Data Mining Designer</span></span>](#bkmk_Designer)  
  
 [<span data-ttu-id="d3bbb-114">使用 DMX 來建立鑽研查詢</span><span class="sxs-lookup"><span data-stu-id="d3bbb-114">Creating Drillthrough Queries using DMX</span></span>](#bkmk_DMX)  
  
 [<span data-ttu-id="d3bbb-115">使用鑽取時的考慮</span><span class="sxs-lookup"><span data-stu-id="d3bbb-115">Considerations When Using Drillthrough</span></span>](#bkmk_Considerations)  
  
-   [<span data-ttu-id="d3bbb-116">安全性問題</span><span class="sxs-lookup"><span data-stu-id="d3bbb-116">Security Issues</span></span>](#bkmk_Security)  
  
-   [<span data-ttu-id="d3bbb-117">限制</span><span class="sxs-lookup"><span data-stu-id="d3bbb-117">Limitations</span></span>](#bkmk_Limits)  
  
##  <a name="using-drillthrough-in-data-mining-designer"></a><a name="bkmk_Designer"></a><span data-ttu-id="d3bbb-118">在資料採礦設計工具中使用鑽取</span><span class="sxs-lookup"><span data-stu-id="d3bbb-118">Using Drillthrough in Data Mining Designer</span></span>  
 <span data-ttu-id="d3bbb-119">如果採礦模型已經設定成允許鑽研，而且您擁有適當的權限，當您瀏覽此模型時，可以在適當的檢視器中按一下節點，然後擷取有關該特定節點中案例的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-119">If a mining model has been configured to allow drillthrough, and if you have the appropriate permissions, when you browse the model, you can click on a node in the appropriate viewer and retrieve detailed information about the cases in that particular node.</span></span>  
  
 <span data-ttu-id="d3bbb-120">[向下切入至來自「採礦模型」的案例資料](drill-through-to-case-data-from-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-120">[Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="d3bbb-121">如果在處理採礦結構時快取定型案例，而且您有必要的權限，您就可以從模型案例和採礦結構傳回資訊，包括沒有包含在採礦模型中的資料行。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-121">If the training cases were cached when you processed the mining structure, and you have the necessary permissions, you can return information from the model cases and from the mining structure, including columns that were not included in the mining model.</span></span>  
  
##  <a name="creating-drillthrough-queries-using-dmx"></a><a name="bkmk_DMX"></a><span data-ttu-id="d3bbb-122">使用 DMX 建立鑽取查詢</span><span class="sxs-lookup"><span data-stu-id="d3bbb-122">Creating Drillthrough Queries using DMX</span></span>  
 <span data-ttu-id="d3bbb-123">如果您有模型或結構的權限，可以透過建立 DMX 查詢來鑽研案例資料。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-123">You can drill through to case data by creating a DMX query, if you have permissions on the model or on the structure.</span></span> <span data-ttu-id="d3bbb-124">如需以 DMX 建立鑽研查詢的語法範例，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d3bbb-124">For examples of the syntax for creating drillthrough queries in DMX, see the following topic:</span></span>  
  
 [<span data-ttu-id="d3bbb-125">使用 DMX 建立鑽研查詢</span><span class="sxs-lookup"><span data-stu-id="d3bbb-125">Create Drillthrough Queries using DMX</span></span>](create-drillthrough-queries-using-dmx.md)  
  
##  <a name="considerations-when-using-drillthrough"></a><a name="bkmk_Considerations"></a> <span data-ttu-id="d3bbb-126">使用鑽研時的考量</span><span class="sxs-lookup"><span data-stu-id="d3bbb-126">Considerations When Using Drillthrough</span></span>  
  
-   <span data-ttu-id="d3bbb-127">如果您使用資料採礦精靈，啟用鑽研模型案例的選項位於精靈的最後一頁。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-127">If you use the Data Mining Wizard, the option to enable drillthrough to the model cases is on the final page of the wizard.</span></span> <span data-ttu-id="d3bbb-128">根據預設，系統會停用鑽研。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-128">Drillthrough is disabled by default.</span></span> <span data-ttu-id="d3bbb-129">如需詳細資訊，請參閱[正在完成精靈 &#40;資料採礦精靈&#41;](../completing-the-wizard-data-mining-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-129">For more information, see [Completing the Wizard &#40;Data Mining Wizard&#41;](../completing-the-wizard-data-mining-wizard.md).</span></span>  
  
-   <span data-ttu-id="d3bbb-130">您可以在現有的採礦模型上加入鑽研的能力，但是如果您這樣做，就必須先重新處理模型，然後才能鑽研資料。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-130">You can add the ability to drill through on an existing mining model, but if you do, the model must be reprocessed before you can drill through to the data.</span></span>  
  
-   <span data-ttu-id="d3bbb-131">鑽研藉由擷取處理採礦結構時快取之定型案例的相關資訊來運作。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-131">Drillthrough works by retrieving information about the training cases that was cached when you processed the mining structure.</span></span> <span data-ttu-id="d3bbb-132">因此，如果您要在處理結構之後，將 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性變更為 `ClearAfterProcessing` 來清除快取的資料，鑽研將不會運作。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-132">Therefore, if you cleared the cached data after processing the structure by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span> <span data-ttu-id="d3bbb-133">若要啟用結構資料行的鑽研功能，您必須將 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性變更為 `KeepTrainingCases`，然後重新處理結構。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-133">To enable drillthrough to structure columns, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `KeepTrainingCases` and then reprocess the structure.</span></span>  
  
-   <span data-ttu-id="d3bbb-134">如果採礦結構不允許鑽研，但是採礦模型允許，您就只能檢視模型案例的資訊，而無法檢視採礦結構的資訊。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-134">If the mining structure does not allow drillthrough but the mining model does, you can view information only from the model cases, and not from the mining structure.</span></span>  
  
###  <a name="security-issues-for-drillthrough"></a><a name="bkmk_Security"></a><span data-ttu-id="d3bbb-135">鑽取的安全性問題</span><span class="sxs-lookup"><span data-stu-id="d3bbb-135">Security Issues for Drillthrough</span></span>  
 <span data-ttu-id="d3bbb-136">如果您想要向下切入到模型的結構案例，您必須確認這兩個[AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl)屬性都設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-136">If you want to drill through to structure cases from the model, you must verify that both the mining structure and the mining model have the [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) property set to `True`.</span></span> <span data-ttu-id="d3bbb-137">此外，您必須是針對結構和模型同時擁有鑽研權限之角色的成員。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-137">Moreover, you must be a member of a role that has drillthrough permissions on both the structure and the model.</span></span> <span data-ttu-id="d3bbb-138">如需如何建立角色的資訊，請參閱[角色設計工具 &#40;Analysis Services - 多維度資料&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx)。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-138">For information about how to create roles, see [Role Designer &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx).</span></span> <span data-ttu-id="d3bbb-139">請參閱。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-139">see.</span></span>  
  
 <span data-ttu-id="d3bbb-140">鑽研權限是在結構和模型上分別設定的。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-140">Drillthrough permissions are set separately on the structure and model.</span></span> <span data-ttu-id="d3bbb-141">即使您沒有結構的權限，模型權限還是可以讓您從模型進行鑽研。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-141">The model permission lets you drill through from the model, even if you do not have permissions on the structure.</span></span> <span data-ttu-id="d3bbb-142">結構的鑽研權限可以使用 [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 函數，提供將結構資料行從模型加入到鑽研查詢的額外功能。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-142">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3bbb-143">如果您在採礦結構和採礦模型上都啟用鑽研，則任何使用者 (針對採礦模型具有鑽研權限之角色的成員) 也可以檢視採礦結構中的資料行，即使這些資料行未包含在採礦模型中也一樣。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-143">If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="d3bbb-144">因此，若要保護機密資料，您應該設定資料來源檢視來遮罩個人資訊，並只有在必要時才允許採礦結構的鑽研存取。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-144">Therefore, to protect sensitive data, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
###  <a name="limitations-on-drillthrough"></a><a name="bkmk_Limits"></a><span data-ttu-id="d3bbb-145">鑽取的限制</span><span class="sxs-lookup"><span data-stu-id="d3bbb-145">Limitations on Drillthrough</span></span>  
  
-   <span data-ttu-id="d3bbb-146">下列限制會套用至模型的鑽研作業，端視用來建立模型的演算法而定：</span><span class="sxs-lookup"><span data-stu-id="d3bbb-146">The following limitations apply to drillthrough operations on a model, depending on the algorithm that was used to create the model:</span></span>  
  
|<span data-ttu-id="d3bbb-147">演算法名稱</span><span class="sxs-lookup"><span data-stu-id="d3bbb-147">Algorithm name</span></span>|<span data-ttu-id="d3bbb-148">問題</span><span class="sxs-lookup"><span data-stu-id="d3bbb-148">Issue</span></span>|  
|--------------------|-----------|  
|<span data-ttu-id="d3bbb-149">Microsoft 貝氏機率分類演算法</span><span class="sxs-lookup"><span data-stu-id="d3bbb-149">Microsoft Naïve Bayes algorithm</span></span>|<span data-ttu-id="d3bbb-150">不支援。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-150">Not supported.</span></span> <span data-ttu-id="d3bbb-151">這些演算法不會將案例指派給內容中的特定節點。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-151">These algorithms do not assign cases to specific nodes in the content.</span></span>|  
|<span data-ttu-id="d3bbb-152">Microsoft 類神經網路演算法</span><span class="sxs-lookup"><span data-stu-id="d3bbb-152">Microsoft Neural Network algorithm</span></span>|<span data-ttu-id="d3bbb-153">不支援。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-153">Not supported.</span></span> <span data-ttu-id="d3bbb-154">這些演算法不會將案例指派給內容中的特定節點。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-154">These algorithms do not assign cases to specific nodes in the content.</span></span>|  
|<span data-ttu-id="d3bbb-155">Microsoft 羅吉斯迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="d3bbb-155">Microsoft Logistic Regression algorithm</span></span>|<span data-ttu-id="d3bbb-156">不支援。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-156">Not supported.</span></span> <span data-ttu-id="d3bbb-157">這些演算法不會將案例指派給內容中的特定節點。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-157">These algorithms do not assign cases to specific nodes in the content.</span></span>|  
|<span data-ttu-id="d3bbb-158">Microsoft 線性迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="d3bbb-158">Microsoft Linear Regression algorithm</span></span>|<span data-ttu-id="d3bbb-159">支援。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-159">Supported.</span></span> <span data-ttu-id="d3bbb-160">不過，由於此模型會建立單一節點 `All`，因此鑽研會傳回模型的所有培訓案例。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-160">However, because the model creates a single node, `All`, drilling through returns all the training cases for the model.</span></span> <span data-ttu-id="d3bbb-161">如果定型集很龐大，載入結果的時間可能會很長。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-161">If the training set is large, loading the results may take a very long time.</span></span>|  
|<span data-ttu-id="d3bbb-162">Microsoft 時間序列演算法</span><span class="sxs-lookup"><span data-stu-id="d3bbb-162">Microsoft Time Series algorithm</span></span>|<span data-ttu-id="d3bbb-163">支援。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-163">Supported.</span></span> <span data-ttu-id="d3bbb-164">不過，您無法使用資料採礦設計師中的 **[採礦模型檢視器]** ，鑽研結構或案例資料。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-164">However, you cannot drill through to structure or case data by using the **Mining Model Viewer** in Data Mining Designer.</span></span> <span data-ttu-id="d3bbb-165">您必須改為建立 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-165">You must create a DMX query instead.</span></span><br /><br /> <span data-ttu-id="d3bbb-166">此外，您無法鑽研至特定節點，或撰寫 DMX 查詢來擷取時間序列模型之特定節點中的案例。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-166">Also, you cannot drill through to specific nodes, or write a DMX query to retrieve cases in specific nodes of a time series model.</span></span> <span data-ttu-id="d3bbb-167">您可以使用其他準則 (例如日期或屬性值)，從模型或結構內部擷取案例資料。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-167">You can retrieve case data from either the model or the structure by using other criteria, such as date or attribute values.</span></span><br /><br /> <span data-ttu-id="d3bbb-168">您也可以使用 [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) 函數來傳回模型中案例的日期。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-168">You can also return the dates from the cases in the model, by using the [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) function.</span></span><br /><br /> <span data-ttu-id="d3bbb-169">如果您想要檢視 Microsoft 時間序列演算法所建立之 ARTXP 和 ARIMA 節點的詳細資料，可以使用 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-169">If you wish to view details of the ARTXP and ARIMA nodes created by the Microsoft Time Series algorithm, you can use the [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>|  
  
##  <a name="related-tasks"></a><a name="bkmk_Tasks"></a> <span data-ttu-id="d3bbb-170">相關工作</span><span class="sxs-lookup"><span data-stu-id="d3bbb-170">Related Tasks</span></span>  
 <span data-ttu-id="d3bbb-171">使用下列連結，在特定案例中使用鑽研。</span><span class="sxs-lookup"><span data-stu-id="d3bbb-171">Use the following links to work with drillthrough in specific scenarios.</span></span>  
  
|<span data-ttu-id="d3bbb-172">Task</span><span class="sxs-lookup"><span data-stu-id="d3bbb-172">Task</span></span>|<span data-ttu-id="d3bbb-173">連結</span><span class="sxs-lookup"><span data-stu-id="d3bbb-173">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="d3bbb-174">描述在資料採礦設計師中使用鑽研的程序</span><span class="sxs-lookup"><span data-stu-id="d3bbb-174">Procedure describing use of drillthrough in the Data Mining Designer</span></span>|[<span data-ttu-id="d3bbb-175">鑽研採礦模型的案例資料</span><span class="sxs-lookup"><span data-stu-id="d3bbb-175">Drill Through to Case Data from a Mining Model</span></span>](drill-through-to-case-data-from-a-mining-model.md)|  
|<span data-ttu-id="d3bbb-176">改變現有的採礦模型以允許鑽研</span><span class="sxs-lookup"><span data-stu-id="d3bbb-176">To alter an existing mining model to allow drillthrough</span></span>|[<span data-ttu-id="d3bbb-177">針對採礦模型啟用鑽研</span><span class="sxs-lookup"><span data-stu-id="d3bbb-177">Enable Drillthrough for a Mining Model</span></span>](enable-drillthrough-for-a-mining-model.md)|  
|<span data-ttu-id="d3bbb-178">使用 DMX WITH DRILLTHROUGH 子句，在採礦結構上啟用鑽研</span><span class="sxs-lookup"><span data-stu-id="d3bbb-178">Enabling drillthrough on a mining structure by using the DMX WITH DRILLTHROUGH clause</span></span>|[<span data-ttu-id="d3bbb-179">CREATE MINING STRUCTURE &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="d3bbb-179">CREATE MINING STRUCTURE &#40;DMX&#41;</span></span>](/sql/dmx/create-mining-structure-dmx)|  
|<span data-ttu-id="d3bbb-180">如需有關指派套用至採礦結構和採礦模型之權限的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="d3bbb-180">For information about assigning permissions that apply to drillthrough on mining structures and mining models</span></span>|[<span data-ttu-id="d3bbb-181">授與資料採礦結構和模型的權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d3bbb-181">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](../multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a><span data-ttu-id="d3bbb-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3bbb-182">See Also</span></span>  
 <span data-ttu-id="d3bbb-183">[資料採礦模型檢視器](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="d3bbb-183">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 [<span data-ttu-id="d3bbb-184">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="d3bbb-184">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
