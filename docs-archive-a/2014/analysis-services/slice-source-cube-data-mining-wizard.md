---
title: 配量來源 Cube (資料採礦嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762248d4c2a268ac36b0dfa3ffeba20123017017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705482"
---
# <a name="slice-source-cube-data-mining-wizard"></a><span data-ttu-id="31928-102">配量來源 Cube (資料採礦精靈)</span><span class="sxs-lookup"><span data-stu-id="31928-102">Slice Source Cube (Data Mining Wizard)</span></span>
  <span data-ttu-id="31928-103">\*\*\*\* 您可以使用 [配量來源 Cube] 對話方塊來限制用於培訓模型的資料。</span><span class="sxs-lookup"><span data-stu-id="31928-103">You can use the **Slice Source Cube** dialog box to restrict the data used to train the model.</span></span> <span data-ttu-id="31928-104">Cube 通常包含了與許多不同維度及屬性相關的資料，例如所有商店、所有區域和所有產品。</span><span class="sxs-lookup"><span data-stu-id="31928-104">Typically a cube contains data related to many different dimensions and attributes, such as all stores, all regions, and all products.</span></span> <span data-ttu-id="31928-105">根據無限制的屬性組合來培訓模型並不實用，所以您要使用此對話方塊選擇用於培訓模型的一組特定項目。</span><span class="sxs-lookup"><span data-stu-id="31928-105">It is not practical to train a model on unlimited combinations of attributes, so you use this dialog box to choose a specific set to use in training a model.</span></span>  
  
 <span data-ttu-id="31928-106">例如，針對 AdventureWorks Cube，您可能會依特定產品線、地區或年份配量，以取得一部分的資料。</span><span class="sxs-lookup"><span data-stu-id="31928-106">For example, in the AdventureWorks cube, you might slice by a particular product line, region, or year, to get a portion of the data.</span></span>  
  
 <span data-ttu-id="31928-107">如果您不熟悉配量和 Cube，建議您檢閱這些文章：</span><span class="sxs-lookup"><span data-stu-id="31928-107">If you are unfamiliar with slices and cubes, we recommend that you review these articles:</span></span>  
  
-   [<span data-ttu-id="31928-108">將分割區配量屬性設定 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="31928-108">Set the Partition Slice Property &#40;Analysis Services&#41;</span></span>](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [<span data-ttu-id="31928-109">建立及管理本機資料分割 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="31928-109">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  <span data-ttu-id="31928-110">請注意，資料分割的 Slice 屬性不支援動態多維度運算式 (MDX) 函數 (例如 [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) 或 [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function))。</span><span class="sxs-lookup"><span data-stu-id="31928-110">Note that dynamic MDX functions (such as [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) or [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) are not supported in the Slice property for partitions.</span></span> <span data-ttu-id="31928-111">您必須使用明確的 Tuple 或成員參考來定義配量。</span><span class="sxs-lookup"><span data-stu-id="31928-111">You must define the slice by using explicit tuples or member references.</span></span>  
>   
>  <span data-ttu-id="31928-112">例如，您必須依特定年份列舉每個成員，而不是使用[： &#40;範圍&#41; &#40;MDX&#41;](/sql/mdx/range-mdx)來定義範圍。</span><span class="sxs-lookup"><span data-stu-id="31928-112">For example, rather than using  [: &#40;Range&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) to define a range, you would need to enumerate each member by the specific years.</span></span>  
>   
>  <span data-ttu-id="31928-113">如果您需要定義複雜的配量，我們建議您使用 XMLA Alter 指令碼在配量中定義 Tuple。</span><span class="sxs-lookup"><span data-stu-id="31928-113">If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script.</span></span> <span data-ttu-id="31928-114">然後在處理資料分割區之前，您可以使用 ascmd 命令列工具或 SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) 立即執行該指令碼並建立指定集合的成員。</span><span class="sxs-lookup"><span data-stu-id="31928-114">Then, you can use either the ascmd command-line tool or the SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) to run the script and create the specified set of members immediately before you process the partition.</span></span>  
  
 <span data-ttu-id="31928-115">**如需詳細資訊，請參閱** [資料採礦精靈 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="31928-115">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="31928-116">選項</span><span class="sxs-lookup"><span data-stu-id="31928-116">Options</span></span>  
 <span data-ttu-id="31928-117">**維度**</span><span class="sxs-lookup"><span data-stu-id="31928-117">**Dimension**</span></span>  
 <span data-ttu-id="31928-118">選取您要配量的維度。</span><span class="sxs-lookup"><span data-stu-id="31928-118">Select the dimension that you want to slice.</span></span>  
  
 <span data-ttu-id="31928-119">**階層**</span><span class="sxs-lookup"><span data-stu-id="31928-119">**Hierarchy**</span></span>  
 <span data-ttu-id="31928-120">選取您要配量的階層。</span><span class="sxs-lookup"><span data-stu-id="31928-120">Select the hierarchy that you want to slice.</span></span> <span data-ttu-id="31928-121">您可以選擇階層的任一層級，但是模型中所用的屬性將只拘限於您自選的層級。</span><span class="sxs-lookup"><span data-stu-id="31928-121">You can choose any level of a hierarchy, but the attributes used in the model will be only at the level that you choose.</span></span>  
  
 <span data-ttu-id="31928-122">例如，假設您選擇 Geography 階層並且選取 Country 當做層級，便無法建立使用 City 做為屬性的模型。</span><span class="sxs-lookup"><span data-stu-id="31928-122">For example, if you choose the Geography hierarchy, and select Country as the level, you cannot build a model that uses City as the attributes.</span></span> <span data-ttu-id="31928-123">相對地，若是選擇了 City 做為要配量的階層層級，您就無法建立以 Country 為根據的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="31928-123">Conversely, if you choose City as the level of the hierarchy on which to slice, you cannot create a mining model based on Country.</span></span>  
  
 <span data-ttu-id="31928-124">**運算子**</span><span class="sxs-lookup"><span data-stu-id="31928-124">**Operator**</span></span>  
 <span data-ttu-id="31928-125">選取要用於建立配量運算式的運算子。</span><span class="sxs-lookup"><span data-stu-id="31928-125">Select the operator to use in building a slice expression.</span></span>  
  
 <span data-ttu-id="31928-126">例如，如果您選擇 [Geography] 做為階層，則可以選取 [運算子 =]，然後輸入 "歐洲" 作為篩選準則，僅取得歐洲的 cube 資料。</span><span class="sxs-lookup"><span data-stu-id="31928-126">For example, if you chose Geography as the hierarchy, you could select the operator = and then type "Europe" as the filter, to get cube data for Europe only.</span></span>  
  
 <span data-ttu-id="31928-127">**篩選運算式**</span><span class="sxs-lookup"><span data-stu-id="31928-127">**Filter Expression**</span></span>  
 <span data-ttu-id="31928-128">輸入根據選取的維度篩選 Cube 時要當做準則使用的運算式。</span><span class="sxs-lookup"><span data-stu-id="31928-128">Type an expression to use as a criterion when filtering the cube on the selected dimension.</span></span>  
  
 <span data-ttu-id="31928-129">**參數**</span><span class="sxs-lookup"><span data-stu-id="31928-129">**Parameters**</span></span>  
 <span data-ttu-id="31928-130">此選項不適用於資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="31928-130">This option is not used for data mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31928-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31928-131">See Also</span></span>  
 <span data-ttu-id="31928-132">[正在完成 Wizard &#40;資料採礦嚮導&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="31928-132">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="31928-133">[資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="31928-133">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="31928-134">指定 &#40;資料採礦嚮導&#41;的「採礦模型資料行使用方式」</span><span class="sxs-lookup"><span data-stu-id="31928-134">Specify Mining Model Column Usage &#40;Data Mining Wizard&#41;</span></span>](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  
