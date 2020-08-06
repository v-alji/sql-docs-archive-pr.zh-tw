---
title: 設定屬性關聯性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 241fa2af16377fd2cacf657ec6f99c5ca4bd0c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585658"
---
# <a name="configure-attribute-relationship-properties"></a><span data-ttu-id="7cd5b-102">設定屬性 (Attribute) 關聯性屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="7cd5b-102">Configure Attribute Relationship Properties</span></span>
  <span data-ttu-id="7cd5b-103">下表列出及描述屬性 (Attribute) 關聯性的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-103">The following table lists and describes the properties of an attribute relationship.</span></span>  
  
|<span data-ttu-id="7cd5b-104">屬性</span><span class="sxs-lookup"><span data-stu-id="7cd5b-104">Property</span></span>|<span data-ttu-id="7cd5b-105">描述</span><span class="sxs-lookup"><span data-stu-id="7cd5b-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7cd5b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="7cd5b-106">Attribute</span></span>|<span data-ttu-id="7cd5b-107">包含屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-107">Contains the name of the attribute.</span></span>|  
|<span data-ttu-id="7cd5b-108">基數</span><span class="sxs-lookup"><span data-stu-id="7cd5b-108">Cardinality</span></span>|<span data-ttu-id="7cd5b-109">指出關聯性的基數。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-109">Indicates the cardinality of the relationship.</span></span> <span data-ttu-id="7cd5b-110">值可為許多 (針對多對一的關聯性)，或是一 (針對一對一的關聯性)。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-110">Values are Many, for a many to one relationship, or One, for a one to one relationship.</span></span> <span data-ttu-id="7cd5b-111">預設值是「許多」。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-111">Default value is Many.</span></span> <span data-ttu-id="7cd5b-112">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，基數屬性沒有作用-它的用途是保留供未來的執行。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cardinality property has no effect - its use is reserved for a future implementation.</span></span>|  
|<span data-ttu-id="7cd5b-113">名稱</span><span class="sxs-lookup"><span data-stu-id="7cd5b-113">Name</span></span>|<span data-ttu-id="7cd5b-114">包含屬性的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-114">Contains the friendly name of the attribute.</span></span>|  
|<span data-ttu-id="7cd5b-115">RelationshipType</span><span class="sxs-lookup"><span data-stu-id="7cd5b-115">RelationshipType</span></span>|<span data-ttu-id="7cd5b-116">指出成員關聯性是否會隨時間變更。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-116">Indicates whether member relationships change over time.</span></span> <span data-ttu-id="7cd5b-117">值可為 Rigid，表示成員之間的關聯性並不會隨著時間變更；或為 Flexible，表示成員之間的關聯性會隨時間變更。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-117">Values are Rigid, which means that relationships between members do not change over time, or Flexible, which means that relationships between members change over time.</span></span> <span data-ttu-id="7cd5b-118">預設值是 Flexible。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-118">Default is Flexible.</span></span> <span data-ttu-id="7cd5b-119">如果將關聯性定義為彈性，彙總會進行卸除，並重新計算做為累加式更新的一部分 (如果只是加入新成員，就不會卸除)。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-119">If you define a relationship as flexible, aggregations are dropped and recomputed as part of an incremental update (they will not be dropped if only new members are added).</span></span> <span data-ttu-id="7cd5b-120">如果將關聯性定義為固定，當維度進行累加式更新時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會保留彙總。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-120">If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retains aggregations when the dimension is incrementally updated.</span></span> <span data-ttu-id="7cd5b-121">如果定義為固定的關聯性變更了， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 就會在累加式處理期間產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-121">If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generates an error during incremental processing.</span></span> <span data-ttu-id="7cd5b-122">指定適當的關聯性和關聯性屬性可增加查詢和處理效能。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-122">Specifying the appropriate relationships and relationship properties increases query and processing performance.</span></span>|  
|<span data-ttu-id="7cd5b-123">可見</span><span class="sxs-lookup"><span data-stu-id="7cd5b-123">Visible</span></span>|<span data-ttu-id="7cd5b-124">決定屬性關聯性是否可見。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-124">Determines the visibility of the attribute relationship.</span></span> <span data-ttu-id="7cd5b-125">值為 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-125">Values are True or False.</span></span> <span data-ttu-id="7cd5b-126">預設值是 True。</span><span class="sxs-lookup"><span data-stu-id="7cd5b-126">Default is True.</span></span>|  
  
  
