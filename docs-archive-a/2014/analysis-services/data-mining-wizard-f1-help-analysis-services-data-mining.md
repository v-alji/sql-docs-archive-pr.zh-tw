---
title: 資料採礦嚮導 F1 說明 (Analysis Services-資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.welcome.f1
helpviewer_keywords:
- Mining Model Wizard
ms.assetid: fd443f55-d725-43d4-ae2e-9847f0105a7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c3a64d22ddb853daccb1a8c3900343495d4ad472
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598070"
---
# <a name="data-mining-wizard-f1-help-analysis-services---data-mining"></a><span data-ttu-id="38509-102">資料採礦精靈 F1 說明 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="38509-102">Data Mining Wizard F1 Help (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="38509-103">使用 **[資料採礦精靈]** ，即可建立新的採礦結構和選擇性的相關採礦模型。</span><span class="sxs-lookup"><span data-stu-id="38509-103">Use the **Data Mining Wizard** to create a new mining structure and an optional associated mining model.</span></span>  
  
-   <span data-ttu-id="38509-104">採礦結構代表有關您要解決之商務問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="38509-104">A mining structure represents information about the business problem you are trying to solve.</span></span> <span data-ttu-id="38509-105">其中包含資料行，以描述屬性和資料行資料來源的繫結。</span><span class="sxs-lookup"><span data-stu-id="38509-105">It contains columns that describe attributes and the bindings to the source of the data in the columns.</span></span> <span data-ttu-id="38509-106">您可以根據關聯式資料或 Cube 中的資料來建立採礦結構。</span><span class="sxs-lookup"><span data-stu-id="38509-106">You can create a mining structure based on relational data or based on data in a cube.</span></span>  
  
-   <span data-ttu-id="38509-107">採礦模型讓您分析採礦結構中的資料以找出模式，並根據這些模式做預測。</span><span class="sxs-lookup"><span data-stu-id="38509-107">A mining model lets you analyze the data in the mining structure for patterns, and then make predictions based on those patterns.</span></span> <span data-ttu-id="38509-108">您可以在單一的採礦結構上，根據不同的演算法建立不同類型的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="38509-108">You can create different types of mining models, based on different algorithms, on a single mining structure.</span></span>  
  
 <span data-ttu-id="38509-109">如需詳細資訊，請參閱[資料採礦嚮導 &#40;Analysis Services 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="38509-109">For more information, see [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="38509-110">**[資料採礦精靈]** 會引導您完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="38509-110">The **Data Mining Wizard** guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="38509-111">選取要作為採礦模型基礎之資料來源的類型。</span><span class="sxs-lookup"><span data-stu-id="38509-111">Select the type of data source on which to base the mining model.</span></span>  
  
-   <span data-ttu-id="38509-112">選取資料採礦技術。</span><span class="sxs-lookup"><span data-stu-id="38509-112">Select the data mining technique.</span></span>  
  
-   <span data-ttu-id="38509-113">指定資料來源。</span><span class="sxs-lookup"><span data-stu-id="38509-113">Specify the data source.</span></span>  
  
-   <span data-ttu-id="38509-114">選取採礦模型的培訓資料。</span><span class="sxs-lookup"><span data-stu-id="38509-114">Select the training data for the mining model.</span></span>  
  
-   <span data-ttu-id="38509-115">選取案例索引鍵。</span><span class="sxs-lookup"><span data-stu-id="38509-115">Select the case key.</span></span>  
  
-   <span data-ttu-id="38509-116">識別案例層級資料行的屬性和量值。</span><span class="sxs-lookup"><span data-stu-id="38509-116">Identify the attributes and measures for case-level columns.</span></span> <span data-ttu-id="38509-117">(只限 OLAP)</span><span class="sxs-lookup"><span data-stu-id="38509-117">(OLAP only)</span></span>  
  
-   <span data-ttu-id="38509-118">指定採礦模型資料行的使用方式，並加入巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="38509-118">Specify how the mining model columns will be used, and add nested tables.</span></span>  
  
-   <span data-ttu-id="38509-119">指定採礦模型資料行的內容和資料類型。</span><span class="sxs-lookup"><span data-stu-id="38509-119">Specify the content and data type of the mining model columns.</span></span>  
  
-   <span data-ttu-id="38509-120">篩選用來培訓模型的資料。</span><span class="sxs-lookup"><span data-stu-id="38509-120">Filter the data that is used to train the model.</span></span> <span data-ttu-id="38509-121">(只限 OLAP)</span><span class="sxs-lookup"><span data-stu-id="38509-121">(OLAP only)</span></span>  
  
-   <span data-ttu-id="38509-122">將資料分割成培訓集和測試集。</span><span class="sxs-lookup"><span data-stu-id="38509-122">Partition the data into training and testing sets.</span></span>  
  
-   <span data-ttu-id="38509-123">完成 **[資料採礦精靈]**。</span><span class="sxs-lookup"><span data-stu-id="38509-123">Complete the **Data Mining Wizard**.</span></span>  
  
 <span data-ttu-id="38509-124">在建立採礦結構和選擇性的採礦模型之後，可以使用 **[資料採礦設計師]** 來修改其屬性。</span><span class="sxs-lookup"><span data-stu-id="38509-124">After you create the mining structure and an optional mining model, you can use **Data Mining Designer** to modify their properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38509-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38509-125">See Also</span></span>  
 <span data-ttu-id="38509-126">[資料採礦嚮導 &#40;Analysis Services 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="38509-126">[Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="38509-127">[資料採礦設計工具](data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="38509-127">[Data Mining Designer](data-mining/data-mining-designer.md) </span></span>  
 <span data-ttu-id="38509-128">[建立關聯式的採礦結構](data-mining/create-a-relational-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="38509-128">[Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md) </span></span>  
 <span data-ttu-id="38509-129">[選取定義方法 &#40;資料採礦嚮導&#41;](select-the-definition-method-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-129">[Select the Definition Method &#40;Data Mining Wizard&#41;](select-the-definition-method-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-130">[建立資料採礦結構 &#40;資料採礦嚮導&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-130">[Create the Data Mining Structure &#40;Data Mining Wizard&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-131">[選取資料來源視圖 &#40;資料採礦嚮導&#41;](select-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-131">[Select Data Source View &#40;Data Mining Wizard&#41;](select-data-source-view-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-132">[流覽資料來源視圖 &#40;資料採礦嚮導&#41;](browse-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-132">[Browse Data Source View &#40;Data Mining Wizard&#41;](browse-data-source-view-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-133">[指定資料表類型 &#40;資料採礦嚮導&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-133">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-134">[指定定型資料 &#40;資料採礦嚮導&#41;](specify-the-training-data-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-134">[Specify the Training Data &#40;Data Mining Wizard&#41;](specify-the-training-data-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-135">[建議相關資料行 &#40;Data 採集 Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-135">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-136">[選取 [來源 Cube] 維度 &#40;資料採礦嚮導]&#41;](select-the-source-cube-dimension-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-136">[Select the Source Cube Dimension &#40;Data Mining Wizard&#41;](select-the-source-cube-dimension-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-137">[選取 [資料採礦嚮導] &#40;[案例金鑰]&#41;](select-the-case-key-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-137">[Select the Case Key &#40;Data Mining Wizard&#41;](select-the-case-key-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-138">[選取案例層級資料行 &#40;資料採礦嚮導&#41;](select-case-level-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-138">[Select Case Level Columns &#40;Data Mining Wizard&#41;](select-case-level-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-139">[指定 &#40;資料採礦嚮導&#41;的「採礦模型資料行使用方式」](specify-mining-model-column-usage-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-139">[Specify Mining Model Column Usage &#40;Data Mining Wizard&#41;](specify-mining-model-column-usage-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-140">[選取量值群組維度 &#40;[加入新的嵌套資料表] Wizard&#41;](select-a-measure-group-dimension-add-new-nested-table-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-140">[Select a Measure Group Dimension &#40;Add New Nested Table Wizard&#41;](select-a-measure-group-dimension-add-new-nested-table-wizard.md) </span></span>  
 <span data-ttu-id="38509-141">[選取 [嵌套資料表索引鍵] &#40;[加入新的嵌套資料表 Wizard]&#41;](select-nested-table-key-add-new-nested-table-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-141">[Select Nested Table Key &#40;Add New Nested Table Wizard&#41;](select-nested-table-key-add-new-nested-table-wizard.md) </span></span>  
 <span data-ttu-id="38509-142">[選取 [嵌套資料表資料行] &#40;[加入新的嵌套資料表 Wizard]&#41;](select-nested-table-columns-add-new-nested-table-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-142">[Select Nested Table Columns &#40;Add New Nested Table Wizard&#41;](select-nested-table-columns-add-new-nested-table-wizard.md) </span></span>  
 <span data-ttu-id="38509-143">[指定資料行的內容和資料類型 &#40;[Data] [Wizard]&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-143">[Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-144">[配量來源 Cube &#40;資料採礦嚮導&#41;](slice-source-cube-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-144">[Slice Source Cube &#40;Data Mining Wizard&#41;](slice-source-cube-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-145">[正在完成 Wizard &#40;資料採礦嚮導&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-145">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="38509-146">[指定資料行內容和資料類型 &#40;Data 採集 Wizard&#41;](specify-column-content-and-data-type-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="38509-146">[Specify Column Content and Data Type &#40;Data Mining Wizard&#41;](specify-column-content-and-data-type-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="38509-147">建立測試集 &#40;資料採礦嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="38509-147">Create Testing Set &#40;Data Mining Wizard&#41;</span></span>](create-testing-set-data-mining-wizard.md)  
  
  
