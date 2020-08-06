---
title: 定義自訂成員公式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- members [Analysis Services], custom
- custom rollup formulas [Analysis Services]
- MDX [Analysis Services], custom rollup formulas
- custom member formulas [Analysis Services]
ms.assetid: 258304e2-d900-4013-97e3-871f51dfdce2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51649bea0c4134971b342b779c778b857343e62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708802"
---
# <a name="define-custom-member-formulas"></a><span data-ttu-id="b121f-102">定義自訂成員公式</span><span class="sxs-lookup"><span data-stu-id="b121f-102">Define Custom Member Formulas</span></span>
  <span data-ttu-id="b121f-103">您可以定義多維度運算式 (MDX) 運算式 (稱為自訂成員公式)，來提供所指定屬性之成員的值。</span><span class="sxs-lookup"><span data-stu-id="b121f-103">You can define a Multidimensional Expressions (MDX) expression, called a custom member formula, to supply the values for the members of a specified attribute.</span></span> <span data-ttu-id="b121f-104">來自資料來源檢視之資料表中的資料行，為屬性的每一個成員提供該運算式，來提供該成員的值。</span><span class="sxs-lookup"><span data-stu-id="b121f-104">A column in a table from a data source view provides, for each member in an attribute, the expression used to supply the value for that member.</span></span>  
  
 <span data-ttu-id="b121f-105">自訂成員公式決定與成員相關聯的資料格值，並覆寫量值的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="b121f-105">Custom member formulas determine the cell values that are associated with members and override the aggregate functions of measures.</span></span> <span data-ttu-id="b121f-106">自訂成員公式是用 MDX 撰寫。</span><span class="sxs-lookup"><span data-stu-id="b121f-106">Custom member formulas are written in MDX.</span></span> <span data-ttu-id="b121f-107">每個自訂成員公式適用於單一成員。</span><span class="sxs-lookup"><span data-stu-id="b121f-107">Each custom member formula applies to a single member.</span></span> <span data-ttu-id="b121f-108">自訂成員公式會儲存在維度資料表中，或者儲存在與維度資料表有外部索引鍵關聯性的另一個資料表中。</span><span class="sxs-lookup"><span data-stu-id="b121f-108">Custom member formulas are stored in the dimension table or in another table that has a foreign key relationship with the dimension table.</span></span>  
  
 <span data-ttu-id="b121f-109">屬性 (Attribute) 上的 `CustomRollupColumn` 屬性 (Property) 指定含有屬性 (Attribute) 成員之自訂成員公式的資料行。</span><span class="sxs-lookup"><span data-stu-id="b121f-109">The `CustomRollupColumn` property on an attribute specifies the column that contains custom member formulas for members of the attribute.</span></span> <span data-ttu-id="b121f-110">如果資料行中的資料列是空的，則會正常傳回成員的資料格值。</span><span class="sxs-lookup"><span data-stu-id="b121f-110">If a row in the column is empty, the cell value for the member is returned normally.</span></span> <span data-ttu-id="b121f-111">如果資料行中的公式無效，則只要擷取使用成員的資料格值時，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="b121f-111">If the formula in the column is not valid, a run-time error occurs whenever a cell value that uses the member is retrieved.</span></span>  
  
 <span data-ttu-id="b121f-112">在為屬性指定自訂成員公式之前，請確認包含該屬性的維度資料表，或直接相關的資料表中有字串資料行可儲存自訂成員公式。</span><span class="sxs-lookup"><span data-stu-id="b121f-112">Before you can specify custom member formulas for an attribute, make sure that the dimension table that contains the attribute, or a directly related table, has a string column to store the custom member formulas.</span></span> <span data-ttu-id="b121f-113">如果是這種情況，您可以手動設定屬性的 `CustomRollupColumn` 屬性，或使用商業智慧 Wizard 的 [設定自訂成員公式增強功能]，在屬性上啟用自訂成員公式。</span><span class="sxs-lookup"><span data-stu-id="b121f-113">If this is the case, you can either set the `CustomRollupColumn` property on an attribute manually or use the Set Custom Member Formula enhancement of the Business Intelligence Wizard to enable a custom member formula on an attribute.</span></span> <span data-ttu-id="b121f-114">如需如何使用這項增強功能的詳細資訊，請參閱 [在維度中設定屬性的自訂成員公式](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="b121f-114">For more information about how to use this enhancement, see [Set Custom Member Formulas for Attributes in a Dimension](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md).</span></span>  
  
## <a name="evaluating-custom-member-formulas"></a><span data-ttu-id="b121f-115">評估自訂成員公式</span><span class="sxs-lookup"><span data-stu-id="b121f-115">Evaluating Custom Member Formulas</span></span>  
 <span data-ttu-id="b121f-116">自訂成員公式與導出成員不同。</span><span class="sxs-lookup"><span data-stu-id="b121f-116">Custom member formulas differ from calculated members.</span></span> <span data-ttu-id="b121f-117">自訂成員公式是套用至維度資料表中的成員，並只提供成員的值。</span><span class="sxs-lookup"><span data-stu-id="b121f-117">Custom member formulas apply to members that exist in dimension tables, and only provide the value of the member.</span></span> <span data-ttu-id="b121f-118">相反地，導出成員不是儲存在維度資料表中，而導出成員運算式會定義維度或階層所含之其他成員的資料和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b121f-118">In contrast, calculated members are not stored in dimension tables, and calculated member expressions define both data and metadata for additional members included in a dimension or hierarchy.</span></span>  
  
 <span data-ttu-id="b121f-119">自訂成員公式覆寫與量值相關聯的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="b121f-119">Custom member formulas override the aggregate functions associated with measures.</span></span> <span data-ttu-id="b121f-120">例如，在指定自訂成員公式之前，使用 `Sum` 彙總函式的量值含有 Time 維度下列成員的下列值：</span><span class="sxs-lookup"><span data-stu-id="b121f-120">For example, before a custom member formula is specified, a measure using the `Sum` aggregate function has the following values for the following members of the Time dimension:</span></span>  
  
-   <span data-ttu-id="b121f-121">2003: 2100</span><span class="sxs-lookup"><span data-stu-id="b121f-121">2003: 2100</span></span>  
  
    -   <span data-ttu-id="b121f-122">第 1 季：700</span><span class="sxs-lookup"><span data-stu-id="b121f-122">Quarter 1: 700</span></span>  
  
    -   <span data-ttu-id="b121f-123">第 2 季：500</span><span class="sxs-lookup"><span data-stu-id="b121f-123">Quarter 2: 500</span></span>  
  
    -   <span data-ttu-id="b121f-124">第 3 季：100</span><span class="sxs-lookup"><span data-stu-id="b121f-124">Quarter 3: 100</span></span>  
  
    -   <span data-ttu-id="b121f-125">第 4 季：800</span><span class="sxs-lookup"><span data-stu-id="b121f-125">Quarter 4: 800</span></span>  
  
-   <span data-ttu-id="b121f-126">2004: 1500</span><span class="sxs-lookup"><span data-stu-id="b121f-126">2004: 1500</span></span>  
  
    -   <span data-ttu-id="b121f-127">第 1 季：600</span><span class="sxs-lookup"><span data-stu-id="b121f-127">Quarter 1: 600</span></span>  
  
    -   <span data-ttu-id="b121f-128">第 2 季：200</span><span class="sxs-lookup"><span data-stu-id="b121f-128">Quarter 2: 200</span></span>  
  
    -   <span data-ttu-id="b121f-129">第 3 季：300</span><span class="sxs-lookup"><span data-stu-id="b121f-129">Quarter 3: 300</span></span>  
  
    -   <span data-ttu-id="b121f-130">第 4 季：400</span><span class="sxs-lookup"><span data-stu-id="b121f-130">Quarter 4: 400</span></span>  
  
 <span data-ttu-id="b121f-131">利用自訂成員公式，成員的值將改由自訂積存公式提供。</span><span class="sxs-lookup"><span data-stu-id="b121f-131">With a custom member formula, the value of the member is instead supplied by the custom rollup formula.</span></span> <span data-ttu-id="b121f-132">例如，可使用以下自訂成員公式，提供 Time 維度之 2004 成員 Quarter 4 子成員的值 450。</span><span class="sxs-lookup"><span data-stu-id="b121f-132">For example, the following custom member formula can be used to supply the value for the Quarter 4 child member of the 2004 member in the Time dimension as 450.</span></span>  
  
```  
Time.[Quarter 3] * 1.5  
```  
  
 <span data-ttu-id="b121f-133">自訂成員公式儲存在維度資料表的一個資料行中。</span><span class="sxs-lookup"><span data-stu-id="b121f-133">Custom member formulas are stored in a column of the dimension table.</span></span> <span data-ttu-id="b121f-134">您可以在屬性上設定 `CustomRollupColumn` 屬性，來啟用自訂積存公式。</span><span class="sxs-lookup"><span data-stu-id="b121f-134">You enable custom rollup formulas by setting the `CustomRollupColumn` property on an attribute.</span></span>  
  
 <span data-ttu-id="b121f-135">若要將單一 MDX 運算式套用至屬性的所有成員，請在維度資料表上建立具名計算，以常值字串傳回 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="b121f-135">To apply a single MDX expression to all members of an attribute, create a named calculation on the dimension table that returns an MDX expression as a literal string.</span></span> <span data-ttu-id="b121f-136">然後，以您要設定之屬性上的 `CustomRollupColumn` 屬性設定，來指定具名計算。</span><span class="sxs-lookup"><span data-stu-id="b121f-136">Then, specify the named calculation with the `CustomRollupColumn` property setting on the attribute that you want to configure.</span></span> <span data-ttu-id="b121f-137">具名計算是資料來源檢視資料表中的一個資料行，它傳回 SQL 運算式所定義的資料列值。</span><span class="sxs-lookup"><span data-stu-id="b121f-137">A named calculation is a column in a data source view table that returns row values defined by a SQL expression.</span></span> <span data-ttu-id="b121f-138">如需建構具名計算的詳細資訊，請參閱[在資料來源檢視中定義具名計算 &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="b121f-138">For more information about constructing named calculations, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b121f-139">若要將 MDX 運算式套用至特定層級的成員，而非以特定屬性為基礎之所有層級的成員，則可將運算式定義為層級上的 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="b121f-139">To apply an MDX expression to members of a particular level instead of to members of all levels based on a particular attribute, you can define the expression as an MDX script on the level.</span></span> <span data-ttu-id="b121f-140">如需詳細資訊，請參閱 [MDX 指令碼基礎觀念 &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b121f-140">For more information, see [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md).</span></span>  
  
 <span data-ttu-id="b121f-141">如果您對屬性的成員同時使用導出成員和自訂積存公式，則必須知道評估順序。</span><span class="sxs-lookup"><span data-stu-id="b121f-141">If you use both calculated members and custom rollup formulas for members of an attribute, you should be aware of the order of evaluation.</span></span> <span data-ttu-id="b121f-142">導出成員是在解析自訂積存公式之前解析。</span><span class="sxs-lookup"><span data-stu-id="b121f-142">Calculated members are resolved before custom rollup formulas are resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b121f-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b121f-143">See Also</span></span>  
 <span data-ttu-id="b121f-144">[屬性和屬性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="b121f-144">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 [<span data-ttu-id="b121f-145">在維度中設定屬性的自訂成員公式</span><span class="sxs-lookup"><span data-stu-id="b121f-145">Set Custom Member Formulas for Attributes in a Dimension</span></span>](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)  
  
  
