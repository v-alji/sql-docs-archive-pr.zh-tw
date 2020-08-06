---
title: 將自訂匯總加入至維度 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed843b8b0005ff62f05b13ebd20024d528857388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585645"
---
# <a name="add-a-custom-aggregation-to-a-dimension"></a><span data-ttu-id="2b32c-102">將自訂彙總加入維度中</span><span class="sxs-lookup"><span data-stu-id="2b32c-102">Add a Custom Aggregation to a Dimension</span></span>
  <span data-ttu-id="2b32c-103">將自訂彙總增強功能加入至 Cube 或維度中，以不同的一元運算子取代與維度成員相關聯的預設彙總。</span><span class="sxs-lookup"><span data-stu-id="2b32c-103">Add a custom aggregation enhancement to a cube or dimension to replace the default aggregations that are associated with a dimension member with a different unary operator.</span></span> <span data-ttu-id="2b32c-104">此增強功能指定維度資料表中的一元運算子資料行，它定義父子式階層中的成員積存。</span><span class="sxs-lookup"><span data-stu-id="2b32c-104">This enhancement specifies a unary operator column in the dimension table that defines rollup for members in a parent-child hierarchy.</span></span> <span data-ttu-id="2b32c-105">一元運算子是在父子式階層的父屬性上作用。</span><span class="sxs-lookup"><span data-stu-id="2b32c-105">The unary operator acts on the parent attribute in a parent-child hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b32c-106">只有以現有的資料來源為基礎的維度，才可使用自訂彙總。</span><span class="sxs-lookup"><span data-stu-id="2b32c-106">A custom aggregation is available only for dimensions that are based on existing data sources.</span></span> <span data-ttu-id="2b32c-107">對於沒有使用資料來源建立的維度，在加入自訂彙總之前，您必須執行結構描述產生精靈來建立資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="2b32c-107">For dimensions that were created without using a data source, you must run the Schema Generation Wizard to create a data source view before adding the custom aggregation.</span></span>  
  
 <span data-ttu-id="2b32c-108">若要加入自訂彙總，您可以使用商業智慧精靈，並選取 **[選擇增強功能]** 頁面上的 **[指定一元運算子]** 選項。</span><span class="sxs-lookup"><span data-stu-id="2b32c-108">To add a custom aggregation, you use the Business Intelligence Wizard, and select the **Specify a unary operator** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="2b32c-109">此精靈會引導您完成一些步驟，來選取您要套用自訂彙總的維度及識別自訂彙總。</span><span class="sxs-lookup"><span data-stu-id="2b32c-109">This wizard then guides you through the steps of selecting a dimension to which you want to apply a custom aggregation and identifying the custom aggregation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b32c-110">在執行商業智慧精靈來加入自訂彙總之前，請確定您要增強的維度有包含父子屬性階層。</span><span class="sxs-lookup"><span data-stu-id="2b32c-110">Before you run the Business Intelligence Wizard to add a custom aggregation, make sure that the dimension that you want to enhance contains a parent-child attribute hierarchy.</span></span> <span data-ttu-id="2b32c-111">如需詳細資訊，請參閱[父子式](parent-child-dimension.md)階層。</span><span class="sxs-lookup"><span data-stu-id="2b32c-111">For more information, see [Parent-Child Hierarchy](parent-child-dimension.md).</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="2b32c-112">選取維度</span><span class="sxs-lookup"><span data-stu-id="2b32c-112">Selecting a Dimension</span></span>  
 <span data-ttu-id="2b32c-113">在精靈的第一個 **[指定一元運算子]** 頁面上，您可以選取要套用自訂彙總的維度。</span><span class="sxs-lookup"><span data-stu-id="2b32c-113">On the first **Specify a Unary Operator** page of the wizard, you specify the dimension to which you want to apply a custom aggregation.</span></span> <span data-ttu-id="2b32c-114">自訂彙總加入至這個選取的維度之後，會導致維度變更。</span><span class="sxs-lookup"><span data-stu-id="2b32c-114">The custom aggregation added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="2b32c-115">包含選取之維度的所有 Cube，都會繼承這些變更。</span><span class="sxs-lookup"><span data-stu-id="2b32c-115">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="adding-custom-aggregation-unary-operator"></a><span data-ttu-id="2b32c-116">加入自訂彙總 (一元運算子)</span><span class="sxs-lookup"><span data-stu-id="2b32c-116">Adding Custom Aggregation (Unary Operator)</span></span>  
 <span data-ttu-id="2b32c-117">在第二個 **[指定一元運算子]** 頁面上，您可以指定自訂彙總的父屬性，以及維度資料表中供一元運算子使用的來源資料行。</span><span class="sxs-lookup"><span data-stu-id="2b32c-117">On the second **Specify a Unary Operator** page, you specify the parent attribute that you want for the custom aggregation and the source column in the dimension table for the unary operator.</span></span> <span data-ttu-id="2b32c-118">**Parent 屬性**會列出其 `Usage` 屬性設定為的屬性 `Parent` 。</span><span class="sxs-lookup"><span data-stu-id="2b32c-118">**Parent attribute** lists attributes that have their `Usage` property set to `Parent`.</span></span> <span data-ttu-id="2b32c-119">如果有一個以上的父屬性，請選擇對應到您要使用之父子式階層關聯性的父屬性。</span><span class="sxs-lookup"><span data-stu-id="2b32c-119">If there is more than one parent attribute, choose the parent attribute that corresponds to the parent-child relationship that you want to use.</span></span> <span data-ttu-id="2b32c-120">如果沒有列出父屬性，表示該維度不含有效的父子式階層。</span><span class="sxs-lookup"><span data-stu-id="2b32c-120">If there is no parent attribute listed, then the dimension does not have a valid parent-child hierarchy.</span></span>  
  
 <span data-ttu-id="2b32c-121">在 **[來源資料行]** 中，您可以選取包含一元運算子的字串資料行。</span><span class="sxs-lookup"><span data-stu-id="2b32c-121">In **Source column**, you select the string column that contains the unary operators.</span></span> <span data-ttu-id="2b32c-122"> (此選項會設定 `UnaryOperatorColumn` 父屬性上的屬性。 ) 維度資料表也應該有指定一元匯總運算子的字串資料行。</span><span class="sxs-lookup"><span data-stu-id="2b32c-122">(This selection sets the `UnaryOperatorColumn` property on the parent attribute.) The dimension table should also have a string column that specifies the unary rollup operator.</span></span> <span data-ttu-id="2b32c-123">此資料行的字串值應包含有效彙總運算子。</span><span class="sxs-lookup"><span data-stu-id="2b32c-123">The string values in this column should contain valid aggregation operators.</span></span> <span data-ttu-id="2b32c-124">如果資料列空白，會正常計算相對應的成員。</span><span class="sxs-lookup"><span data-stu-id="2b32c-124">If a row is empty, the corresponding member is calculated normally.</span></span> <span data-ttu-id="2b32c-125">如果資料行中的公式無效，當擷取使用該成員的資料格值時，會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="2b32c-125">If the formula in a column is not valid, a run-time error occurs when a cell value that uses the member is retrieved.</span></span> <span data-ttu-id="2b32c-126">如需詳細資訊，請參閱 [父子式維度中的一元運算子](parent-child-dimension-attributes-unary-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="2b32c-126">For more information, see [Unary Operators in Parent-Child Dimensions](parent-child-dimension-attributes-unary-operators.md).</span></span>  
  
  
