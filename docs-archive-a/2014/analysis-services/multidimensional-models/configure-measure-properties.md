---
title: 設定量值屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- additivity [Analysis Services]
- ID property
- ErrorConfiguration property
- AggregateFunction property
- DisplayFolder property
- IgnoreUnrelatedDimensions property
- FormatString property
- Description property
- semiadditive
- properties [Analysis Services], measure groups
- aggregate functions [Analysis Services]
- DataType property
- ProcessingMode property
- MeasureExpression property
- AggregationPrefix property
- Visible property
- properties [Analysis Services], measures
- StorageLocation property
- StorageMode property
- formats [Analysis Services], measures
- Source property
- aggregations [Analysis Services], measures
- measures [Analysis Services], properties
- nonadditive [Analysis Services]
- Name property
- measures [Analysis Services], display formats
- ProcessingPriority property
- measure groups [Analysis Services], properties
- Type property
- ProactiveCaching property
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ca291a5181fdb3f7a88845431d61ffd7a1034eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705649"
---
# <a name="configure-measure-properties"></a><span data-ttu-id="52e16-102">設定量值屬性</span><span class="sxs-lookup"><span data-stu-id="52e16-102">Configure Measure Properties</span></span>
  <span data-ttu-id="52e16-103">量值有一些屬性可讓您定義量值的運作方式以及控制量值讓使用者看到的樣子。</span><span class="sxs-lookup"><span data-stu-id="52e16-103">Measures have properties that enable you to define how the measures function and to control how the measures appear to users.</span></span>  
  
 <span data-ttu-id="52e16-104">您可以在建立或編輯 Cube 或量值時，在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="52e16-104">You can set properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] when creating or editing a cube or measure.</span></span> <span data-ttu-id="52e16-105">您也可以使用 MDX 或 AMO，透過程式設計方式來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="52e16-105">You can also set them programmatically, using MDX or AMO.</span></span> <span data-ttu-id="52e16-106">如需詳細資訊，請參閱[在多維度模型中建立量值和量值群組](create-measures-and-measure-groups-in-multidimensional-models.md)、[CREATE MEMBER 陳述式 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) 或[設計 AMO OLAP 基本物件的程式](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects)。</span><span class="sxs-lookup"><span data-stu-id="52e16-106">See [Create Measures and Measure Groups in Multidimensional Models](create-measures-and-measure-groups-in-multidimensional-models.md) or [CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) or [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects) for details.</span></span>  
  
## <a name="measure-properties"></a><span data-ttu-id="52e16-107">量值屬性</span><span class="sxs-lookup"><span data-stu-id="52e16-107">Measure Properties</span></span>  
 <span data-ttu-id="52e16-108">量值會從其隸屬為成員的量值群組中繼承特定屬性，除非這些屬性在量值層級受到覆寫。</span><span class="sxs-lookup"><span data-stu-id="52e16-108">Measures inherit certain properties from the measure group of which they are a member, unless those properties are overridden at the measure level.</span></span> <span data-ttu-id="52e16-109">量值屬性決定如何彙總量值、量值的資料類型、向使用者顯示的名稱、量值所在的顯示資料夾、量值的格式字串、任何量值運算式、基礎來源資料行，以及對使用者的可見性。</span><span class="sxs-lookup"><span data-stu-id="52e16-109">Measure properties determine how a measure is aggregated, its data type, the name that is displayed to the user, the display folder in which the measure will appear, its format string, any measure expression, the underlying source column, and its visibility to users.</span></span>  
  
|<span data-ttu-id="52e16-110">屬性</span><span class="sxs-lookup"><span data-stu-id="52e16-110">Property</span></span>|<span data-ttu-id="52e16-111">定義</span><span class="sxs-lookup"><span data-stu-id="52e16-111">Definition</span></span>|  
|--------------|----------------|  
|`AggregateFunction`|<span data-ttu-id="52e16-112">必要。</span><span class="sxs-lookup"><span data-stu-id="52e16-112">Required.</span></span> <span data-ttu-id="52e16-113">決定如何彙總量值。</span><span class="sxs-lookup"><span data-stu-id="52e16-113">Determines how measures are aggregated.</span></span> <span data-ttu-id="52e16-114">`Sum` 為預設彙總。</span><span class="sxs-lookup"><span data-stu-id="52e16-114">`Sum` is the default aggregation.</span></span> <span data-ttu-id="52e16-115">如需詳細資訊，請參閱 [使用彙總函式](use-aggregate-functions.md) 中每個函數的描述。</span><span class="sxs-lookup"><span data-stu-id="52e16-115">For more information, see [Use Aggregate Functions](use-aggregate-functions.md) for a description of each function.</span></span>|  
|`DataType`|<span data-ttu-id="52e16-116">必要。</span><span class="sxs-lookup"><span data-stu-id="52e16-116">Required.</span></span> <span data-ttu-id="52e16-117">指定量值所繫結之基礎事實資料表資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="52e16-117">Specifies the data type of the column in the underlying fact table to which the measure is bound.</span></span> <span data-ttu-id="52e16-118">這個值預設從來源資料行繼承而來。</span><span class="sxs-lookup"><span data-stu-id="52e16-118">This value is inherited from the source column by default.</span></span>|  
|`Description`|<span data-ttu-id="52e16-119">提供量值的描述，可以在用戶端應用程式中公開。</span><span class="sxs-lookup"><span data-stu-id="52e16-119">Provides a description of the measure, which may be exposed in client applications.</span></span>|  
|`DisplayFolder`|<span data-ttu-id="52e16-120">指定使用者連接到 Cube 時，可在其中看到量值的資料夾。</span><span class="sxs-lookup"><span data-stu-id="52e16-120">Specifies the folder in which the measure will appear when users connect to the cube.</span></span> <span data-ttu-id="52e16-121">Cube 具有許多量值時，您可使用顯示資料夾來分類量值，並改進使用者瀏覽經驗。</span><span class="sxs-lookup"><span data-stu-id="52e16-121">When a cube has many measures, you can use display folders to categorize the measures and improve the user browsing experience.</span></span>|  
|`FormatString`|<span data-ttu-id="52e16-122">您可使用屬性的 `FormatString` 屬性，來選取用於對使用者顯示量值的格式。</span><span class="sxs-lookup"><span data-stu-id="52e16-122">You can select the format that is used to display measure values to users by using the `FormatString` property of the measure.</span></span><br /><br /> <span data-ttu-id="52e16-123">雖然 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]會提供顯示格式的清單，但您仍可指定清單中未提供的其他格式。</span><span class="sxs-lookup"><span data-stu-id="52e16-123">Although a list of display formats is provided in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can specify many additional formats that are not in the list.</span></span> <span data-ttu-id="52e16-124">您可以指定在 Microsoft Visual Basic 中有效的任何具名格式或使用者自訂格式。</span><span class="sxs-lookup"><span data-stu-id="52e16-124">You can specify any named or user-defined format that is valid in Microsoft Visual Basic.</span></span>|  
|`ID`|<span data-ttu-id="52e16-125">必要。</span><span class="sxs-lookup"><span data-stu-id="52e16-125">Required.</span></span> <span data-ttu-id="52e16-126">顯示量值的唯一識別碼 (ID)。</span><span class="sxs-lookup"><span data-stu-id="52e16-126">Displays the unique identifier (ID) of the measure.</span></span> <span data-ttu-id="52e16-127">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="52e16-127">This property is read-only.</span></span>|  
|`MeasureExpression`|<span data-ttu-id="52e16-128">指定受條件約束的 MDX 運算式來定義量值的值。</span><span class="sxs-lookup"><span data-stu-id="52e16-128">Specifies a constrained MDX expression defining the value of the measure.</span></span> <span data-ttu-id="52e16-129">運算式會在彙總之前，先在分葉層級求取值，以便於對值進行加權。</span><span class="sxs-lookup"><span data-stu-id="52e16-129">The expression is evaluated at the leaf level before being aggregated, and allows for weighting of a value.</span></span> <span data-ttu-id="52e16-130">例如，在匯率轉換時，銷售金額會以匯率加權。</span><span class="sxs-lookup"><span data-stu-id="52e16-130">For example, in currency conversion where a sales amount is weighted by the exchange rate.</span></span>|  
|`Name`|<span data-ttu-id="52e16-131">必要。</span><span class="sxs-lookup"><span data-stu-id="52e16-131">Required.</span></span> <span data-ttu-id="52e16-132">指定量值的名稱。</span><span class="sxs-lookup"><span data-stu-id="52e16-132">Specifies the name of the measure.</span></span>|  
|`Source`|<span data-ttu-id="52e16-133">必要。</span><span class="sxs-lookup"><span data-stu-id="52e16-133">Required.</span></span> <span data-ttu-id="52e16-134">指定量值所繫結之資料來源檢視中的資料行。</span><span class="sxs-lookup"><span data-stu-id="52e16-134">Specifies the column in the data source view to which the measure is bound.</span></span> <span data-ttu-id="52e16-135">請參閱[資料來源和繫結 &#40;SSAS 多維度&#41;](data-sources-and-bindings-ssas-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="52e16-135">See [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](data-sources-and-bindings-ssas-multidimensional.md).</span></span>|  
|`Visible`|<span data-ttu-id="52e16-136">指定量值是否要在用戶端應用程式中顯示。</span><span class="sxs-lookup"><span data-stu-id="52e16-136">Determines the visibility of the measure in client applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52e16-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52e16-137">See Also</span></span>  
 <span data-ttu-id="52e16-138">[設定量值群組屬性](configure-measure-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="52e16-138">[Configure Measure Group Properties](configure-measure-group-properties.md) </span></span>  
 [<span data-ttu-id="52e16-139">修改量值</span><span class="sxs-lookup"><span data-stu-id="52e16-139">Modifying Measures</span></span>](../lesson-3-1-modifying-measures.md)  
  
  
