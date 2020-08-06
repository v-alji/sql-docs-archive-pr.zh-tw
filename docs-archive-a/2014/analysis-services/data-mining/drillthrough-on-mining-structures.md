---
title: 對採礦結構的鑽取 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a0b00a3b-f9db-4289-a8cb-ddf600cd64ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: e8b3dad28227547f88956f1ac49e2878b2940f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607157"
---
# <a name="drillthrough-on-mining-structures"></a><span data-ttu-id="025d7-102">採礦結構的鑽研</span><span class="sxs-lookup"><span data-stu-id="025d7-102">Drillthrough on Mining Structures</span></span>
  <span data-ttu-id="025d7-103">「鑽研」\*\* 表示查詢採礦模型或採礦結構並取得模型中未公開之詳細資料的能力。</span><span class="sxs-lookup"><span data-stu-id="025d7-103">*Drillthrough* means the ability to query either a mining model or a mining structure and get detailed data that is not exposed in the model.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="025d7-104">提供了兩種不同的鑽研選項來鑽研案例資料。</span><span class="sxs-lookup"><span data-stu-id="025d7-104">provides two different options for drilling through into case data.</span></span> <span data-ttu-id="025d7-105">您可以鑽研用來建立採礦模型的資料，也可以鑽研採礦結構中的來源資料。</span><span class="sxs-lookup"><span data-stu-id="025d7-105">You can drill through to the data that were used to build the mining model, or you can drill through to the source data in the mining structure.</span></span>  
  
## <a name="drillthrough-to-model-cases-vs-drillthrough-to-structure"></a><span data-ttu-id="025d7-106">鑽研模型案例和鑽研結構的比較</span><span class="sxs-lookup"><span data-stu-id="025d7-106">Drillthrough to Model Cases vs. Drillthrough to Structure</span></span>  
 <span data-ttu-id="025d7-107">鑽研 **模型案例** 對於尋找模型中規則、模式或叢集的詳細資料很有幫助。</span><span class="sxs-lookup"><span data-stu-id="025d7-107">Drilling through to **model cases** is useful for finding additional details about rules, patterns or clusters in a model.</span></span>  
  
 <span data-ttu-id="025d7-108">反之， **鑽研結構** 資料用意在於提供對模型中無法使用之資訊的存取。</span><span class="sxs-lookup"><span data-stu-id="025d7-108">In contrast, **drillthrough to structure** data is intended to provide access to information that was not made available in the model.</span></span> <span data-ttu-id="025d7-109">例如，如果您具有適當的權限，可能要確定哪些資料列用於模型定型，哪些資料列用於測試。</span><span class="sxs-lookup"><span data-stu-id="025d7-109">For example, if you have the appropriate permissions, you might want to find out which rows of data were used for training the model and which were used for testing.</span></span>  
  
 <span data-ttu-id="025d7-110">還可以檢視分析中未使用之資料的屬性，只要這些屬性已包含在結構定義中。</span><span class="sxs-lookup"><span data-stu-id="025d7-110">You can also view attributes of the data that were not used in analysis, provided they have been included in the structure definition.</span></span> <span data-ttu-id="025d7-111">例如，採礦結構通常支援許多不同類型的模型，並且一些結構資料行可能因為資料類型不相容或者資料未用於分析而從模型中排除。</span><span class="sxs-lookup"><span data-stu-id="025d7-111">For example, often mining structures support many different kinds of models, and some structure columns might have been excluded from a model because the data type was incompatible or the data was not useful for analysis.</span></span> <span data-ttu-id="025d7-112">例如，您不會在叢集模型中使用客戶連絡資訊，即使資料已包含在結構中，但透過啟用鑽研，不需要對資料來源執行單獨查詢即可取得對此資訊的存取。</span><span class="sxs-lookup"><span data-stu-id="025d7-112">For example, you would not use customer contact information in a clustering model, even if the data was included in the structure, but by enabling drillthrough you gain access to this information without running separate queries against the data source.</span></span>  
  
## <a name="enabling-drillthrough-to-structure-data"></a><span data-ttu-id="025d7-113">啟用結構資料鑽研</span><span class="sxs-lookup"><span data-stu-id="025d7-113">Enabling Drillthrough to Structure Data</span></span>  
 <span data-ttu-id="025d7-114">若要對採礦結構使用鑽研，必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="025d7-114">To use drillthrough on the mining structure, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="025d7-115">還必須在模型上啟用鑽研。</span><span class="sxs-lookup"><span data-stu-id="025d7-115">Drillthrough on the model must also be enabled.</span></span> <span data-ttu-id="025d7-116">根據預設，這兩種類型的鑽研都已停用。</span><span class="sxs-lookup"><span data-stu-id="025d7-116">By default, drillthrough of both kinds is disabled.</span></span> <span data-ttu-id="025d7-117">若要在資料採礦精靈中啟用鑽研，請選取位於精靈最後一頁啟用鑽研模型案例的選項。</span><span class="sxs-lookup"><span data-stu-id="025d7-117">To enable drillthrough in the Data Mining Wizard, select the option to enable drillthrough to model cases on the final page of the wizard.</span></span> <span data-ttu-id="025d7-118">您也可以稍後變更 `AllowDrillthrough` 屬性，在模型上新增鑽研的能力。</span><span class="sxs-lookup"><span data-stu-id="025d7-118">You can also add the ability to drillthrough on a model later by changing the `AllowDrillthrough` property.</span></span>  
  
-   <span data-ttu-id="025d7-119">如果您使用 DMX 來建立採礦結構，請使用 WITH DRILLTHROUGH 子句。</span><span class="sxs-lookup"><span data-stu-id="025d7-119">If you create the mining structure by using DMX, use the WITH DRILLTHROUGH clause.</span></span> <span data-ttu-id="025d7-120">如需詳細資訊，請參閱 [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)。</span><span class="sxs-lookup"><span data-stu-id="025d7-120">For more information, see [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).</span></span>  
  
-   <span data-ttu-id="025d7-121">鑽研藉由擷取處理採礦結構時快取之定型案例的相關資訊來運作。</span><span class="sxs-lookup"><span data-stu-id="025d7-121">Drillthrough works by retrieving information about the training cases that was cached when you processed the mining structure.</span></span> <span data-ttu-id="025d7-122">因此，如果您將 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性變更為 `ClearAfterProcessing`，在處理結構之後清除快取的資料，鑽研將不會運作。</span><span class="sxs-lookup"><span data-stu-id="025d7-122">Therefore, if you clear the cached data after processing the structure by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span> <span data-ttu-id="025d7-123">若要啟用結構資料行的鑽研功能，您必須將 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性變更為 `KeepTrainingCases`，然後重新處理結構。</span><span class="sxs-lookup"><span data-stu-id="025d7-123">To enable drillthrough to structure columns, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `KeepTrainingCases` and then reprocess the structure.</span></span>  
  
-   <span data-ttu-id="025d7-124">確認這兩個[AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl)屬性都設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="025d7-124">Verify that both the mining structure and the mining model have the [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) property set to `True`.</span></span> <span data-ttu-id="025d7-125">此外，您必須是針對結構和模型同時擁有鑽研權限之角色的成員。</span><span class="sxs-lookup"><span data-stu-id="025d7-125">Moreover, you must be a member of a role that has drillthrough permissions on both the structure and the model.</span></span>  
  
## <a name="security-issues-for-drillthrough"></a><span data-ttu-id="025d7-126">鑽研的安全性問題</span><span class="sxs-lookup"><span data-stu-id="025d7-126">Security Issues for Drillthrough</span></span>  
 <span data-ttu-id="025d7-127">鑽研權限是在結構和模型上分別設定的。</span><span class="sxs-lookup"><span data-stu-id="025d7-127">Drillthrough permissions are set separately on the structure and model.</span></span> <span data-ttu-id="025d7-128">即使您沒有結構的權限，模型權限還是可以讓您從模型進行鑽研。</span><span class="sxs-lookup"><span data-stu-id="025d7-128">The model permission lets you drill through from the model, even if you do not have permissions on the structure.</span></span> <span data-ttu-id="025d7-129">結構的鑽研權限可以使用 [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 函數，提供將結構資料行從模型加入到鑽研查詢的額外功能。</span><span class="sxs-lookup"><span data-stu-id="025d7-129">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
 <span data-ttu-id="025d7-130">如需如何在 Analysis Services 中建立角色和指派權限的資訊，請參閱[角色設計師 &#40;Analysis Services - 多維度資料&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx)。</span><span class="sxs-lookup"><span data-stu-id="025d7-130">For information about how to create roles and assign permissions in Analysis Services, see [Role Designer &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="025d7-131">如果您在採礦結構和採礦模型上都啟用鑽研，則任何使用者 (針對採礦模型具有鑽研權限之角色的成員) 也可以檢視採礦結構中的資料行，即使這些資料行未包含在採礦模型中也一樣。</span><span class="sxs-lookup"><span data-stu-id="025d7-131">If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="025d7-132">因此，若要保護機密資料，您應該設定資料來源檢視來遮罩個人資訊，並只有在必要時才允許採礦結構的鑽研存取。</span><span class="sxs-lookup"><span data-stu-id="025d7-132">Therefore, to protect sensitive data, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="025d7-133">相關工作</span><span class="sxs-lookup"><span data-stu-id="025d7-133">Related Tasks</span></span>  
 <span data-ttu-id="025d7-134">如需有關如何將鑽研用於採礦模型的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="025d7-134">See the following topics for more information about how to use drillthrough with mining models.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="025d7-135">從採礦模型檢視器對結構使用鑽研</span><span class="sxs-lookup"><span data-stu-id="025d7-135">Use drillthrough to structure from the mining model viewers</span></span>|[<span data-ttu-id="025d7-136">從模型檢視器使用鑽研</span><span class="sxs-lookup"><span data-stu-id="025d7-136">Use Drillthrough from the Model Viewers</span></span>](use-drillthrough-from-the-model-viewers.md)|  
|<span data-ttu-id="025d7-137">參閱特定模型類型的鑽研查詢範例。</span><span class="sxs-lookup"><span data-stu-id="025d7-137">See examples of drillthrough queries for specific model types.</span></span>|[<span data-ttu-id="025d7-138">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="025d7-138">Data Mining Queries</span></span>](data-mining-queries.md)|  
|<span data-ttu-id="025d7-139">取得有關適用於特定採礦結構和採礦模型之權限的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="025d7-139">Get information about permissions that apply to specific mining structures and mining models.</span></span>|[<span data-ttu-id="025d7-140">授與資料採礦結構和模型的權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="025d7-140">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](../multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a><span data-ttu-id="025d7-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="025d7-141">See Also</span></span>  
 [<span data-ttu-id="025d7-142">採礦模型的鑽研</span><span class="sxs-lookup"><span data-stu-id="025d7-142">Drillthrough on Mining Models</span></span>](drillthrough-on-mining-models.md)  
  
  
