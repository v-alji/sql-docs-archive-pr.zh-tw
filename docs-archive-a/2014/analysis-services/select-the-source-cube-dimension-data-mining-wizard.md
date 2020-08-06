---
title: 選取 [資料採礦嚮導] ([來源 Cube] 維度) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectsourcecube.f1
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6295a5312b4501236e0ce8f5776fc43c0d014581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592889"
---
# <a name="select-the-source-cube-dimension-data-mining-wizard"></a><span data-ttu-id="2e68e-102">選取來源 Cube 維度 (資料採礦精靈)</span><span class="sxs-lookup"><span data-stu-id="2e68e-102">Select the Source Cube Dimension (Data Mining Wizard)</span></span>
  <span data-ttu-id="2e68e-103">使用 [選取來源 Cube 維度]\*\*\*\* 頁面，即可從包含您要分析之案例的 Cube 中選取維度。</span><span class="sxs-lookup"><span data-stu-id="2e68e-103">Use the **Select the Source Cube Dimension** page to select the dimension from the cube that contains the cases you want to analyze.</span></span> <span data-ttu-id="2e68e-104">例如，如果您要建立根據人口統計分析客戶購買行為的模型，您要選取 [客戶] 維度，其中通常包含每個客戶的唯一記錄，以及表示人口統計的各種屬性，例如性別、居住地或收入。</span><span class="sxs-lookup"><span data-stu-id="2e68e-104">For example, if you are building a model that analyzes the purchasing behavior of customers based on demographics, you would select the Customer dimension, which typically contains a unique record for each customer and various attributes that represent demographics, such as gender, location, or income.</span></span> <span data-ttu-id="2e68e-105">在此精靈的後半部，您將有機會加入與此案例資料表相關的資料表：例如，您可以加入顯示客戶已購買之產品的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="2e68e-105">Later in the wizard you will have the opportunity to add a table that is related to this case table: for example, you might add a nested table that shows which products the customer has purchased.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e68e-106">唯有在精靈的 [選取定義方法] \*\*\*\* 頁面上選取了 [從現有的 Cube] \*\*\*\* 之後，才會顯示這個頁面。</span><span class="sxs-lookup"><span data-stu-id="2e68e-106">This page will appear only if you have selected **From existing cube** on the **Select the Definition Method** page of the wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2e68e-107">選項</span><span class="sxs-lookup"><span data-stu-id="2e68e-107">Options</span></span>  
 <span data-ttu-id="2e68e-108">**選取來源 Cube 維度**</span><span class="sxs-lookup"><span data-stu-id="2e68e-108">**Select a Source Cube Dimension**</span></span>  
 <span data-ttu-id="2e68e-109">選取提供採礦結構之來源資料的 Cube 維度。</span><span class="sxs-lookup"><span data-stu-id="2e68e-109">Select the dimension of the cube that will provide the source data for your mining structure.</span></span>  
  
## <a name="choosing-a-dimension"></a><span data-ttu-id="2e68e-110">選擇維度</span><span class="sxs-lookup"><span data-stu-id="2e68e-110">Choosing a Dimension</span></span>  
 <span data-ttu-id="2e68e-111">由於您僅能選取一個維度用於模型中，因此，了解 Cube 結構並選取為您的模型提供最佳資訊的維度相當重要。</span><span class="sxs-lookup"><span data-stu-id="2e68e-111">Because you can select only one dimension for use in your model, it is important that you understand the cube structure and select the dimension that provides the best information for your model.</span></span> <span data-ttu-id="2e68e-112">如果您不確定要使用哪個維度，請瀏覽 Cube 並使用維度設計師檢閱其中的欄位和資料，應該有所幫助。</span><span class="sxs-lookup"><span data-stu-id="2e68e-112">If you are not sure which dimension to use, it might be helpful to browse the cube and review the fields and the data in them by using Dimension Designer.</span></span> <span data-ttu-id="2e68e-113">如需詳細資訊，請參閱[在維度設計師中瀏覽維度資料](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="2e68e-113">For more information, see [Browse Dimension Data in Dimension Designer](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md).</span></span>  
  
 <span data-ttu-id="2e68e-114">如果您不熟悉一般維度，請參閱[維度簡介 &#40;Analysis Services - 多維度資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2e68e-114">If you are unfamiliar with dimensions in general, see [Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="2e68e-115">如需單一維度中通常會包含的資訊類型，以及有助於資料採礦之屬性和量值的詳細資訊，請參閱[維度關聯性](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="2e68e-115">For more information about the type of information that is typically contained in a single dimension, including attributes and measures that might be useful for data mining, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
 <span data-ttu-id="2e68e-116">如果您選擇的維度不包含建立資料採礦模型所需的所有相關屬性，您可能需要修改維度。</span><span class="sxs-lookup"><span data-stu-id="2e68e-116">If the dimension that you choose does not contain all of the related attributes that you need to build the data mining model, you might need to modify the dimension.</span></span> <span data-ttu-id="2e68e-117">如需詳細資訊，請參閱 [定義資料庫維度](multidimensional-models/define-database-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="2e68e-117">For more information, see [Define Database Dimensions](multidimensional-models/define-database-dimensions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e68e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e68e-118">See Also</span></span>  
 <span data-ttu-id="2e68e-119">[資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2e68e-119">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="2e68e-120">[建立資料採礦結構 &#40;資料採礦嚮導&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="2e68e-120">[Create the Data Mining Structure &#40;Data Mining Wizard&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="2e68e-121">[選取 [資料採礦嚮導] &#40;[案例金鑰]&#41;](select-the-case-key-data-mining-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="2e68e-121">[Select the Case Key &#40;Data Mining Wizard&#41;](select-the-case-key-data-mining-wizard.md)</span></span>  
  
  
