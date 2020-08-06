---
title: 指定資料行內容和資料類型 (Data 採集 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0634be64-4c38-4381-9b19-fe9a5889306c
author: minewiskan
ms.author: owend
ms.openlocfilehash: e22f46808877391376f721bcab55ea4fd9074186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594721"
---
# <a name="specify-column-content-and-data-type-data-mining-wizard"></a><span data-ttu-id="3d62c-102">指定資料行內容和資料類型 (資料採礦精靈)</span><span class="sxs-lookup"><span data-stu-id="3d62c-102">Specify Column Content and Data Type (Data Mining Wizard)</span></span>
  <span data-ttu-id="3d62c-103">使用 **[指定資料行的內容和資料類型]** 頁面，針對每個在精靈的前一頁上所選取的資料行指定使用方式和資料類型。</span><span class="sxs-lookup"><span data-stu-id="3d62c-103">Use the **Specify Column Content and Data Type** page to specify the usage and data type for each column that you selected on the previous page of the wizard.</span></span> <span data-ttu-id="3d62c-104">如果想要忽略資料行，請按一下 **[上一步]** 返回 **[指定培訓資料]**，然後清除所有核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3d62c-104">If you want to ignore the column, click **Back** to return to the page **Specify the Training Data**, and clear all checkboxes.</span></span>  
  
 <span data-ttu-id="3d62c-105">資料行的使用方式代表資料在模型中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="3d62c-105">The usage of a column indicates how the data will be used in the model.</span></span> <span data-ttu-id="3d62c-106">資料行可用來當做識別序列的索引鍵、用於分析的輸入值，或者您要預測的值。</span><span class="sxs-lookup"><span data-stu-id="3d62c-106">A column can be used as a key to identify a series, as an input value to use in analysis, or as the value that you want to predict.</span></span> <span data-ttu-id="3d62c-107">資料行可以同時用於預測和輸入。</span><span class="sxs-lookup"><span data-stu-id="3d62c-107">Columns can be used for both prediction and input.</span></span>  
  
 <span data-ttu-id="3d62c-108">資料類型會指定有關資料行所包含之資料類型以及在培訓期間如何使用資料的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3d62c-108">The data type specifies additional detail about the type of data that is contained in the column, and how the data will be used during training.</span></span> <span data-ttu-id="3d62c-109">某些內容類型需要使用特定的資料類型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="3d62c-109">Some content types require a specific data type, and vice versa.</span></span> <span data-ttu-id="3d62c-110">根據在建立採礦模型時所使用的演算法，您可能也需要指定特定的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3d62c-110">You might also need to specify a particular data type depending on the algorithm that you use when you create a mining model.</span></span> <span data-ttu-id="3d62c-111">如需採礦模型和結構中的內容類型及資料類型的資訊，請參閱[內容類型 &#40;資料採礦&#41;](data-mining/content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="3d62c-111">For information about content types and data types in mining models and structures, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="3d62c-112">**如需詳細資訊，請參閱** [採礦結構 &#40;Analysis Services - 資料採礦&#41;](data-mining/mining-structures-analysis-services-data-mining.md)、[採礦模型資料行](data-mining/mining-model-columns.md)、[資料採礦精靈 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="3d62c-112">**For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Mining Model Columns](data-mining/mining-model-columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="3d62c-113">選項</span><span class="sxs-lookup"><span data-stu-id="3d62c-113">Options</span></span>  
 <span data-ttu-id="3d62c-114">**採礦模型結構**</span><span class="sxs-lookup"><span data-stu-id="3d62c-114">**Mining model structure**</span></span>  
 <span data-ttu-id="3d62c-115">顯示在精靈的上一頁上所選取的檢視及巢狀資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="3d62c-115">Displays the columns from the views and nested tables that you selected on the previous page of the wizard.</span></span>  
  
 <span data-ttu-id="3d62c-116">**資料行**</span><span class="sxs-lookup"><span data-stu-id="3d62c-116">**Columns**</span></span>  
 <span data-ttu-id="3d62c-117">列出資料行。</span><span class="sxs-lookup"><span data-stu-id="3d62c-117">Lists the columns.</span></span>  
  
 <span data-ttu-id="3d62c-118">**內容類型**</span><span class="sxs-lookup"><span data-stu-id="3d62c-118">**Content type**</span></span>  
 <span data-ttu-id="3d62c-119">指定資料行的內容類型。</span><span class="sxs-lookup"><span data-stu-id="3d62c-119">Specify the content type for the column.</span></span> <span data-ttu-id="3d62c-120">如果將資料行指定為精靈前一頁上的索引鍵，則可使用下列值：</span><span class="sxs-lookup"><span data-stu-id="3d62c-120">If you specified that the column is a key on the previous page of the wizard, the following values are available:</span></span>  
  
|<span data-ttu-id="3d62c-121">選項</span><span class="sxs-lookup"><span data-stu-id="3d62c-121">Option</span></span>|<span data-ttu-id="3d62c-122">描述</span><span class="sxs-lookup"><span data-stu-id="3d62c-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3d62c-123">Key</span><span class="sxs-lookup"><span data-stu-id="3d62c-123">Key</span></span>|<span data-ttu-id="3d62c-124">指定資料行包含案例序列的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="3d62c-124">Specify that the column contains a unique identifier for the case series.</span></span>|  
|<span data-ttu-id="3d62c-125">Key Sequence</span><span class="sxs-lookup"><span data-stu-id="3d62c-125">Key Sequence</span></span>|<span data-ttu-id="3d62c-126">指定資料行包含順序識別碼。</span><span class="sxs-lookup"><span data-stu-id="3d62c-126">Specify that the column contains a sequence identifier.</span></span>|  
|<span data-ttu-id="3d62c-127">Key Time</span><span class="sxs-lookup"><span data-stu-id="3d62c-127">Key Time</span></span>|<span data-ttu-id="3d62c-128">指定資料行包含日期或其他的唯一連續號碼，以用來識別日期或時間序列。</span><span class="sxs-lookup"><span data-stu-id="3d62c-128">Specify that the column contains a date or other unique continuous number that is used to identify a date or time series.</span></span>|  
  
 <span data-ttu-id="3d62c-129">如果將資料行選取為非索引鍵的資料行，則根據資料類型，可以使用下列值：</span><span class="sxs-lookup"><span data-stu-id="3d62c-129">If you selected the column as a non-key column, the following values are available, depending on the data type:</span></span>  
  
|<span data-ttu-id="3d62c-130">選項</span><span class="sxs-lookup"><span data-stu-id="3d62c-130">Option</span></span>|<span data-ttu-id="3d62c-131">描述</span><span class="sxs-lookup"><span data-stu-id="3d62c-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3d62c-132">連續</span><span class="sxs-lookup"><span data-stu-id="3d62c-132">Continuous</span></span>|<span data-ttu-id="3d62c-133">指定資料行包含連續的數字值。</span><span class="sxs-lookup"><span data-stu-id="3d62c-133">Specify that the column contains continuous numeric values.</span></span>|  
|<span data-ttu-id="3d62c-134">Discretized</span><span class="sxs-lookup"><span data-stu-id="3d62c-134">Discretized</span></span>|<span data-ttu-id="3d62c-135">指定資料行包含的數字值已離散化，或可以視為離散的值。</span><span class="sxs-lookup"><span data-stu-id="3d62c-135">Specify that the column contains numeric values that either have been discretized, or can be treated as discrete values.</span></span>|  
|<span data-ttu-id="3d62c-136">Discrete</span><span class="sxs-lookup"><span data-stu-id="3d62c-136">Discrete</span></span>|<span data-ttu-id="3d62c-137">指定資料行包含文字或其他非數字的值。</span><span class="sxs-lookup"><span data-stu-id="3d62c-137">Specify that the column contains text or other nonnumeric values.</span></span>|  
  
 <span data-ttu-id="3d62c-138">**Data type**</span><span class="sxs-lookup"><span data-stu-id="3d62c-138">**Data type**</span></span>  
 <span data-ttu-id="3d62c-139">指定資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3d62c-139">Specify the data type for the column.</span></span>  
  
 <span data-ttu-id="3d62c-140">有下列可用的值：</span><span class="sxs-lookup"><span data-stu-id="3d62c-140">The following values are available:</span></span>  
  
-   `Boolean`  
  
-   `Date`  
  
-   `Double`  
  
-   `Long`  
  
-   `Text`  
  
 <span data-ttu-id="3d62c-141">**偵測**</span><span class="sxs-lookup"><span data-stu-id="3d62c-141">**Detect**</span></span>  
 <span data-ttu-id="3d62c-142">分析所有數字資料行中的資料範例。</span><span class="sxs-lookup"><span data-stu-id="3d62c-142">Analyze a sample of data in all numeric columns.</span></span> <span data-ttu-id="3d62c-143">以推薦的內容類型取代指定的 **[內容類型]** 值。</span><span class="sxs-lookup"><span data-stu-id="3d62c-143">Replaces specified **Content Type** values with a recommended content type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d62c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d62c-144">See Also</span></span>  
 <span data-ttu-id="3d62c-145">[資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3d62c-145">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3d62c-146">[建議相關資料行 &#40;Data 採集 Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3d62c-146">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="3d62c-147">[指定資料表類型 &#40;資料採礦嚮導&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3d62c-147">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="3d62c-148">[指定資料行的內容和資料類型 &#40;[Data] [Wizard]&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="3d62c-148">[Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)</span></span>  
  
  
