---
title: 維度類型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5e0c16a57081aa1d9ed3cc6964d1f17fa7135986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607118"
---
# <a name="dimension-types"></a><span data-ttu-id="098d3-102">維度類型</span><span class="sxs-lookup"><span data-stu-id="098d3-102">Dimension Types</span></span>
  <span data-ttu-id="098d3-103">`Type` 屬性設定會提供關於維度內容的資訊給伺服器和用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="098d3-103">The `Type` property setting provides information about the contents of a dimension to server and client applications.</span></span> <span data-ttu-id="098d3-104">在某些情況下，`Type` 設定只會提供用戶端應用程式的指導，而且是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="098d3-104">In some cases, the `Type` setting only provides guidance for client applications and is optional.</span></span> <span data-ttu-id="098d3-105">在其他情況下 (例如 `Accounts` 或 `Time` 維度)，維度的 `Type` 屬性 (Property) 設定及其屬性 (Attribute) 會決定特定的伺服器型行為，且在 Cube 中實作某些行為時可能會需要用到。</span><span class="sxs-lookup"><span data-stu-id="098d3-105">In other cases, such as `Accounts` or `Time` dimensions, the `Type` property settings for the dimension and its attributes determine specific server-based behaviors and may be required to implement certain behaviors in the cube.</span></span> <span data-ttu-id="098d3-106">例如，維度的 `Type` 屬性可設定為 `Accounts`，對用戶端應用程式指出標準維度包含帳戶屬性。</span><span class="sxs-lookup"><span data-stu-id="098d3-106">For example, the `Type` property of a dimension can be set to `Accounts` to indicate to client applications that the standard dimension contains account attributes.</span></span> <span data-ttu-id="098d3-107">如需有關時間、帳戶和貨幣維度的詳細資訊，請參閱[建立日期類型維度](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md)、[建立父子式類型維度的財務帳戶](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)和[建立貨幣類型維度](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="098d3-107">For more information about time, account, and currency dimensions, see [Create a Date type Dimension](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Create a Finance Account of parent-child type Dimension](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), and [Create a Currency type Dimension](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).</span></span>  
  
 <span data-ttu-id="098d3-108">維度類型的預設值是 `Regular`，亦即不會對維度的內容進行假設。</span><span class="sxs-lookup"><span data-stu-id="098d3-108">The default setting for the dimension type is `Regular`, which makes no assumptions about the contents of the dimension.</span></span> <span data-ttu-id="098d3-109">除非您在使用維度精靈定義維度時指定 `Time`，否則當您初始定義維度時，這就是所有維度的預設值。</span><span class="sxs-lookup"><span data-stu-id="098d3-109">This is the default setting for all dimensions when you initially define a dimension unless you specify `Time` when defining the dimension using the Dimension Wizard.</span></span> <span data-ttu-id="098d3-110">如果維度精靈未列出維度類型的適當類型，則您也應將 `Regular` 保留為維度類型。</span><span class="sxs-lookup"><span data-stu-id="098d3-110">You should also leave `Regular` as the dimension type if the Dimension Wizard does not list an appropriate type for Dimension type.</span></span>  
  
## <a name="available-dimension-types"></a><span data-ttu-id="098d3-111">可用的維度類型</span><span class="sxs-lookup"><span data-stu-id="098d3-111">Available Dimension Types</span></span>  
 <span data-ttu-id="098d3-112">下表描述中可用的維度類型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="098d3-112">The following table describes the dimension types available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="098d3-113">維度類型</span><span class="sxs-lookup"><span data-stu-id="098d3-113">Dimension type</span></span>|<span data-ttu-id="098d3-114">描述</span><span class="sxs-lookup"><span data-stu-id="098d3-114">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="098d3-115">定期</span><span class="sxs-lookup"><span data-stu-id="098d3-115">Regular</span></span>|<span data-ttu-id="098d3-116">此維度的類型並未設定為特殊維度類型。</span><span class="sxs-lookup"><span data-stu-id="098d3-116">A dimension whose type has not been set to a special dimension type.</span></span>|  
|<span data-ttu-id="098d3-117">Time</span><span class="sxs-lookup"><span data-stu-id="098d3-117">Time</span></span>|<span data-ttu-id="098d3-118">此維度的屬性代表時間週期，例如年數、半年數、季數、月數和日數。</span><span class="sxs-lookup"><span data-stu-id="098d3-118">A dimension whose attributes represent time periods, such as years, semesters, quarters, months, and days.</span></span>|  
|<span data-ttu-id="098d3-119">組織</span><span class="sxs-lookup"><span data-stu-id="098d3-119">Organization</span></span>|<span data-ttu-id="098d3-120">此維度的屬性代表組織的資訊，例如員工或分公司。</span><span class="sxs-lookup"><span data-stu-id="098d3-120">A dimension whose attributes represent organizational information, such as employees or subsidiaries.</span></span>|  
|<span data-ttu-id="098d3-121">[地理位置]</span><span class="sxs-lookup"><span data-stu-id="098d3-121">Geography</span></span>|<span data-ttu-id="098d3-122">此維度的屬性代表地理資訊，例如城市或郵遞區號。</span><span class="sxs-lookup"><span data-stu-id="098d3-122">A dimension whose attributes represent geographic information, such as cities or postal codes.</span></span>|  
|<span data-ttu-id="098d3-123">BillOfMaterials</span><span class="sxs-lookup"><span data-stu-id="098d3-123">BillOfMaterials</span></span>|<span data-ttu-id="098d3-124">維度的屬性代表存貨或製造資訊 (例如產品的組件清單)。</span><span class="sxs-lookup"><span data-stu-id="098d3-124">A dimension whose attributes represent inventory or manufacturing information, such as parts lists for products.</span></span>|  
|<span data-ttu-id="098d3-125">帳戶</span><span class="sxs-lookup"><span data-stu-id="098d3-125">Accounts</span></span>|<span data-ttu-id="098d3-126">此維度的屬性代表財務報表用途的帳戶圖表。</span><span class="sxs-lookup"><span data-stu-id="098d3-126">A dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>|  
|<span data-ttu-id="098d3-127">客戶</span><span class="sxs-lookup"><span data-stu-id="098d3-127">Customers</span></span>|<span data-ttu-id="098d3-128">此維度的屬性代表客戶或連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="098d3-128">A dimension whose attributes represent customer or contact information.</span></span>|  
|<span data-ttu-id="098d3-129">產品</span><span class="sxs-lookup"><span data-stu-id="098d3-129">Products</span></span>|<span data-ttu-id="098d3-130">此維度的屬性代表產品資訊。</span><span class="sxs-lookup"><span data-stu-id="098d3-130">A dimension whose attributes represent product information.</span></span>|  
|<span data-ttu-id="098d3-131">案例</span><span class="sxs-lookup"><span data-stu-id="098d3-131">Scenario</span></span>|<span data-ttu-id="098d3-132">此維度的屬性代表計畫或策略分析資訊。</span><span class="sxs-lookup"><span data-stu-id="098d3-132">A dimension whose attributes represent planning or strategic analysis information.</span></span>|  
|<span data-ttu-id="098d3-133">數量</span><span class="sxs-lookup"><span data-stu-id="098d3-133">Quantitative</span></span>|<span data-ttu-id="098d3-134">此維度的屬性代表數量的資訊。</span><span class="sxs-lookup"><span data-stu-id="098d3-134">A dimension whose attributes represent quantitative information.</span></span>|  
|<span data-ttu-id="098d3-135">公用程式</span><span class="sxs-lookup"><span data-stu-id="098d3-135">Utility</span></span>|<span data-ttu-id="098d3-136">此維度的屬性代表其他資訊。</span><span class="sxs-lookup"><span data-stu-id="098d3-136">A dimension whose attributes represent miscellaneous information.</span></span>|  
|<span data-ttu-id="098d3-137">貨幣</span><span class="sxs-lookup"><span data-stu-id="098d3-137">Currency</span></span>|<span data-ttu-id="098d3-138">此維度類型包含貨幣資料和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="098d3-138">This type of dimension contains currency data and metadata.</span></span>|  
|<span data-ttu-id="098d3-139">匯率</span><span class="sxs-lookup"><span data-stu-id="098d3-139">Rates</span></span>|<span data-ttu-id="098d3-140">此維度的屬性代表貨幣匯率的資訊。</span><span class="sxs-lookup"><span data-stu-id="098d3-140">A dimension whose attributes represent currency rate information.</span></span>|  
|<span data-ttu-id="098d3-141">通路</span><span class="sxs-lookup"><span data-stu-id="098d3-141">Channel</span></span>|<span data-ttu-id="098d3-142">此維度的屬性代表通道資訊。</span><span class="sxs-lookup"><span data-stu-id="098d3-142">A dimension whose attributes represent channel information.</span></span>|  
|<span data-ttu-id="098d3-143">促銷</span><span class="sxs-lookup"><span data-stu-id="098d3-143">Promotion</span></span>|<span data-ttu-id="098d3-144">此維度的屬性代表行銷促銷資訊。</span><span class="sxs-lookup"><span data-stu-id="098d3-144">A dimension whose attributes represent marketing promotion information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="098d3-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="098d3-145">See Also</span></span>  
 <span data-ttu-id="098d3-146">[使用現有的資料表建立維度](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="098d3-146">[Create a Dimension by Using an Existing Table](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="098d3-147">維度 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="098d3-147">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  
