---
title: " (DTA) 的 KeepExisting 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: cde9b3091b75f55e4b9c79137853fbd7d4e0daf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703629"
---
# <a name="keepexisting-element-dta"></a><span data-ttu-id="e00fe-102">KeepExisting 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e00fe-102">KeepExisting Element (DTA)</span></span>
  <span data-ttu-id="e00fe-103">指定在產生建議時，Database Engine Tuning Advisor 必須保留的實體設計結構 (索引、索引檢視或資料分割)。</span><span class="sxs-lookup"><span data-stu-id="e00fe-103">Specifies the physical design structures (indexes, indexed views, or partitioning) that Database Engine Tuning Advisor must retain when generating its recommendation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e00fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="e00fe-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="e00fe-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="e00fe-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="e00fe-106">特性</span><span class="sxs-lookup"><span data-stu-id="e00fe-106">Characteristic</span></span>|<span data-ttu-id="e00fe-107">描述</span><span class="sxs-lookup"><span data-stu-id="e00fe-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e00fe-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="e00fe-108">**Data type and length**</span></span>|<span data-ttu-id="e00fe-109">`string`，伺服器強制實施長度限制。</span><span class="sxs-lookup"><span data-stu-id="e00fe-109">`string`, length limit enforced by the server.</span></span>|  
|<span data-ttu-id="e00fe-110">**允許的值**</span><span class="sxs-lookup"><span data-stu-id="e00fe-110">**Allowed values**</span></span>|<span data-ttu-id="e00fe-111">**NONE**</span><span class="sxs-lookup"><span data-stu-id="e00fe-111">**NONE**</span></span><br /> <span data-ttu-id="e00fe-112">無現有結構。</span><span class="sxs-lookup"><span data-stu-id="e00fe-112">No existing structures.</span></span><br /><br /> <span data-ttu-id="e00fe-113">**ALL**</span><span class="sxs-lookup"><span data-stu-id="e00fe-113">**ALL**</span></span><br /> <span data-ttu-id="e00fe-114">所有現有結構。</span><span class="sxs-lookup"><span data-stu-id="e00fe-114">All existing structures.</span></span><br /><br /> <span data-ttu-id="e00fe-115">**ALIGNED**</span><span class="sxs-lookup"><span data-stu-id="e00fe-115">**ALIGNED**</span></span><br /> <span data-ttu-id="e00fe-116">所有資料分割對齊結構。</span><span class="sxs-lookup"><span data-stu-id="e00fe-116">All partition-aligned structures.</span></span><br /><br /> <span data-ttu-id="e00fe-117">**CL_IDX**</span><span class="sxs-lookup"><span data-stu-id="e00fe-117">**CL_IDX**</span></span><br /> <span data-ttu-id="e00fe-118">資料表的所有叢集索引。</span><span class="sxs-lookup"><span data-stu-id="e00fe-118">All clustered indexes on tables.</span></span><br /><br /> <span data-ttu-id="e00fe-119">**IDX**</span><span class="sxs-lookup"><span data-stu-id="e00fe-119">**IDX**</span></span><br /> <span data-ttu-id="e00fe-120">資料表的所有叢集和非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="e00fe-120">All clustered and nonclustered indexes on tables.</span></span><br /><br /> <span data-ttu-id="e00fe-121">這個元素只能使用這些值的其中之一。</span><span class="sxs-lookup"><span data-stu-id="e00fe-121">Use only one of these values with this element.</span></span>|  
|<span data-ttu-id="e00fe-122">**預設值**</span><span class="sxs-lookup"><span data-stu-id="e00fe-122">**Default value**</span></span>|<span data-ttu-id="e00fe-123">無。</span><span class="sxs-lookup"><span data-stu-id="e00fe-123">None.</span></span>|  
|<span data-ttu-id="e00fe-124">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="e00fe-124">**Occurrence**</span></span>|<span data-ttu-id="e00fe-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e00fe-125">Optional.</span></span> <span data-ttu-id="e00fe-126">每個 `TuningOptions` 元素只能使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="e00fe-126">Can use only once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e00fe-127">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="e00fe-127">Element Relationships</span></span>  
  
|<span data-ttu-id="e00fe-128">關聯性</span><span class="sxs-lookup"><span data-stu-id="e00fe-128">Relationship</span></span>|<span data-ttu-id="e00fe-129">元素</span><span class="sxs-lookup"><span data-stu-id="e00fe-129">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e00fe-130">**父元素**</span><span class="sxs-lookup"><span data-stu-id="e00fe-130">**Parent element**</span></span>|[<span data-ttu-id="e00fe-131">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e00fe-131">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="e00fe-132">**子元素**</span><span class="sxs-lookup"><span data-stu-id="e00fe-132">**Child elements**</span></span>|<span data-ttu-id="e00fe-133">無。</span><span class="sxs-lookup"><span data-stu-id="e00fe-133">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e00fe-134">範例</span><span class="sxs-lookup"><span data-stu-id="e00fe-134">Example</span></span>  
 <span data-ttu-id="e00fe-135">如需此元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="e00fe-135">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e00fe-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e00fe-136">See Also</span></span>  
 [<span data-ttu-id="e00fe-137">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="e00fe-137">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
