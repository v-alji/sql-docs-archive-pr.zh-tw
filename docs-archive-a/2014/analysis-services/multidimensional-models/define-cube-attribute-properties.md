---
title: 定義 Cube 屬性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
author: minewiskan
ms.author: owend
ms.openlocfilehash: c02d57e8d24e625dc0613f25d97765c9ae018803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585641"
---
# <a name="define-cube-attribute-properties"></a><span data-ttu-id="2798f-102">定義 Cube 屬性 (Attribute) 屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="2798f-102">Define Cube Attribute Properties</span></span>
  <span data-ttu-id="2798f-103">Cube 屬性 (Attribute) 的屬性 (Property) 可讓您根據同一個資料庫維度，為 Cube 維度中的維度屬性 (Attribute) 指定唯一的設定。</span><span class="sxs-lookup"><span data-stu-id="2798f-103">Cube attribute properties enable you to specify unique settings for dimension attributes in cube dimensions based on the same database dimension.</span></span> <span data-ttu-id="2798f-104">下表描述 Cube 屬性 (Attribute) 的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="2798f-104">The following table describes the properties of a cube attribute.</span></span>  
  
|<span data-ttu-id="2798f-105">屬性</span><span class="sxs-lookup"><span data-stu-id="2798f-105">Property</span></span>|<span data-ttu-id="2798f-106">描述</span><span class="sxs-lookup"><span data-stu-id="2798f-106">Description</span></span>|  
|--------------|-----------------|  
|`AggregationUsage`|<span data-ttu-id="2798f-107">指定 [彙總設計精靈] 將如何設計這個屬性的彙總。</span><span class="sxs-lookup"><span data-stu-id="2798f-107">Specifies how the Aggregation Design Wizard will design aggregations for the attribute.</span></span> <span data-ttu-id="2798f-108">此屬性可以有下列的值：</span><span class="sxs-lookup"><span data-stu-id="2798f-108">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="2798f-109">`Default`：預設。</span><span class="sxs-lookup"><span data-stu-id="2798f-109">`Default`: Default.</span></span> <span data-ttu-id="2798f-110">[彙總設計精靈] 會根據屬性的類型來套用預設規則 (Full 代表索引鍵，Unrestricted 代表其他項目)。</span><span class="sxs-lookup"><span data-stu-id="2798f-110">The Aggregation Design Wizard applies a default rule based on the type of attribute (Full for keys, Unrestricted for others).</span></span><br /><br /> <span data-ttu-id="2798f-111">`None`：此 Cube 不應該有任何彙總包含這個屬性。</span><span class="sxs-lookup"><span data-stu-id="2798f-111">`None`: No aggregation for the cube should include this attribute.</span></span><br /><br /> <span data-ttu-id="2798f-112">`Unrestricted`：匯總設計嚮導不會有任何限制。</span><span class="sxs-lookup"><span data-stu-id="2798f-112">`Unrestricted`: No restrictions are placed on the Aggregation Design Wizard.</span></span><br /><br /> <span data-ttu-id="2798f-113">`Full`：此 Cube 的每一個彙總都必須包含這個屬性。</span><span class="sxs-lookup"><span data-stu-id="2798f-113">`Full`: Every aggregation for the cube must include this attribute.</span></span>|  
|`AttributeHierarchyEnabled`|<span data-ttu-id="2798f-114">識別這個 Cube 維度上是否啟用此屬性階層，</span><span class="sxs-lookup"><span data-stu-id="2798f-114">Identifies whether the attribute hierarchy is enables on this cube dimension.</span></span> <span data-ttu-id="2798f-115">如此可允許在特定 Cube 或維度角色上停用屬性階層。</span><span class="sxs-lookup"><span data-stu-id="2798f-115">This allows attribute hierarchies to be disabled on specific cubes or dimension roles.</span></span> <span data-ttu-id="2798f-116">如果已停用基礎屬性階層，這個設定不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="2798f-116">This setting has no effect if the underlying attribute hierarchy is disabled.</span></span> <span data-ttu-id="2798f-117">預設值為 `True`。</span><span class="sxs-lookup"><span data-stu-id="2798f-117">Default value is `True`.</span></span>|  
|`OptimizedState`|<span data-ttu-id="2798f-118">指出這個 Cube 維度上是否要最佳化此屬性階層，</span><span class="sxs-lookup"><span data-stu-id="2798f-118">Indicates whether the attribute hierarchy is optimized on this cube dimension.</span></span> <span data-ttu-id="2798f-119">如此可允許在特定 Cube 或維度角色上最佳化屬性階層。</span><span class="sxs-lookup"><span data-stu-id="2798f-119">This allows attribute hierarchies to be optimized on specific cubes or dimension roles.</span></span> <span data-ttu-id="2798f-120">如果基礎屬性階層並未最佳化，這個設定不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="2798f-120">This setting has no effect if the underlying attribute hierarchy is not optimized.</span></span> <span data-ttu-id="2798f-121">此屬性可以有下列的值：</span><span class="sxs-lookup"><span data-stu-id="2798f-121">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="2798f-122">`FullyOptimized`：預設。</span><span class="sxs-lookup"><span data-stu-id="2798f-122">`FullyOptimized`: Default.</span></span> <span data-ttu-id="2798f-123">執行個體會建立階層的索引，以增進查詢效能。</span><span class="sxs-lookup"><span data-stu-id="2798f-123">The instance builds indexes for the hierarchy to improve query performance.</span></span> <span data-ttu-id="2798f-124">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2798f-124">This is the default value.</span></span><br /><br /> <span data-ttu-id="2798f-125">`NotOptimized`：執行個體不會建立其他索引。</span><span class="sxs-lookup"><span data-stu-id="2798f-125">`NotOptimized`: The instance does not build additional indexes.</span></span>|  
|`AttributeHierarchyVisible`|<span data-ttu-id="2798f-126">指出這個 Cube 維度上是否可以看見此屬性階層，</span><span class="sxs-lookup"><span data-stu-id="2798f-126">Indicates whether the attribute hierarchy is visible on this cube dimension.</span></span> <span data-ttu-id="2798f-127">如此可允許在特定 Cube 或維度角色上看見屬性階層。</span><span class="sxs-lookup"><span data-stu-id="2798f-127">This allows attribute hierarchies to be visible on specific cubes or dimension roles.</span></span> <span data-ttu-id="2798f-128">如果看不到基礎屬性階層，這個設定不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="2798f-128">This setting has no effect if the underlying attribute hierarchy is not visible.</span></span> <span data-ttu-id="2798f-129">預設值是 `True`。</span><span class="sxs-lookup"><span data-stu-id="2798f-129">The default value is `True`.</span></span>|  
|`AttributeID`|<span data-ttu-id="2798f-130">包含此屬性的唯一識別碼 (ID)。</span><span class="sxs-lookup"><span data-stu-id="2798f-130">Contains the unique identifier (ID) of the attribute.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2798f-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2798f-131">See Also</span></span>  
 <span data-ttu-id="2798f-132">[定義 Cube 維度屬性](define-cube-dimension-properties.md) </span><span class="sxs-lookup"><span data-stu-id="2798f-132">[Define Cube Dimension Properties](define-cube-dimension-properties.md) </span></span>  
 [<span data-ttu-id="2798f-133">定義 Cube 階層屬性</span><span class="sxs-lookup"><span data-stu-id="2798f-133">Define Cube Hierarchy Properties</span></span>](define-cube-hierarchy-properties.md)  
  
  
