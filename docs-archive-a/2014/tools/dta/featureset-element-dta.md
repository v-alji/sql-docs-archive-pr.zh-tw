---
title: " (DTA) 的 FeatureSet 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d36c28b24a56ef2dcdf69578fb7e8c196306a416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705766"
---
# <a name="featureset-element-dta"></a><span data-ttu-id="bbb8e-102">FeatureSet 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="bbb8e-102">FeatureSet Element (DTA)</span></span>
  <span data-ttu-id="bbb8e-103">包含在分析期間，Database Engine Tuning Advisor 所要使用的實體設計結構 (索引或索引檢視)。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-103">Contains the physical design structures (indexes or indexed views) that you would like Database Engine Tuning Advisor to use during analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="bbb8e-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="bbb8e-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="bbb8e-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="bbb8e-106">特性</span><span class="sxs-lookup"><span data-stu-id="bbb8e-106">Characteristic</span></span>|<span data-ttu-id="bbb8e-107">描述</span><span class="sxs-lookup"><span data-stu-id="bbb8e-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="bbb8e-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-108">**Data type and length**</span></span>|<span data-ttu-id="bbb8e-109">`string`，沒有最大長度。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="bbb8e-110">**允許的值**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-110">**Allowed values**</span></span>|<span data-ttu-id="bbb8e-111">**IDX_IV**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-111">**IDX_IV**</span></span><br /> <span data-ttu-id="bbb8e-112">索引和索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-112">Indexes and indexed views.</span></span><br /><br /> <span data-ttu-id="bbb8e-113">**IDX**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-113">**IDX**</span></span><br /> <span data-ttu-id="bbb8e-114">只有索引。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-114">Indexes only.</span></span><br /><br /> <span data-ttu-id="bbb8e-115">**IV**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-115">**IV**</span></span><br /> <span data-ttu-id="bbb8e-116">只有索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-116">Indexed views only.</span></span><br /><br /> <span data-ttu-id="bbb8e-117">**NCL_IDX**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-117">**NCL_IDX**</span></span><br /> <span data-ttu-id="bbb8e-118">只有非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-118">Nonclustered indexes only.</span></span><br /><br /> <span data-ttu-id="bbb8e-119">這個元素使用這些值的其中之一。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-119">Use one of these values with this element.</span></span>|  
|<span data-ttu-id="bbb8e-120">**預設值**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-120">**Default value**</span></span>|<span data-ttu-id="bbb8e-121">**IDX**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-121">**IDX**</span></span>|  
|<span data-ttu-id="bbb8e-122">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-122">**Occurrence**</span></span>|<span data-ttu-id="bbb8e-123">除非使用 `TuningOptions` 元素，否則，每個 `DropOnlyMode` 元素都需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-123">Required once for each `TuningOptions` element, unless the `DropOnlyMode` element is used.</span></span> <span data-ttu-id="bbb8e-124">如果使用 `DropOnlyMode`，您便無法使用 `FeatureSet`。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-124">If `DropOnlyMode` is used, you cannot use `FeatureSet`.</span></span> <span data-ttu-id="bbb8e-125">這些元素互斥。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-125">These elements are mutually exclusive.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="bbb8e-126">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="bbb8e-126">Element Relationships</span></span>  
  
|<span data-ttu-id="bbb8e-127">關聯性</span><span class="sxs-lookup"><span data-stu-id="bbb8e-127">Relationship</span></span>|<span data-ttu-id="bbb8e-128">元素</span><span class="sxs-lookup"><span data-stu-id="bbb8e-128">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="bbb8e-129">**父元素**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-129">**Parent element**</span></span>|[<span data-ttu-id="bbb8e-130">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="bbb8e-130">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="bbb8e-131">**子元素**</span><span class="sxs-lookup"><span data-stu-id="bbb8e-131">**Child elements**</span></span>|<span data-ttu-id="bbb8e-132">無。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-132">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bbb8e-133">範例</span><span class="sxs-lookup"><span data-stu-id="bbb8e-133">Example</span></span>  
 <span data-ttu-id="bbb8e-134">如需此元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="bbb8e-134">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb8e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbb8e-135">See Also</span></span>  
 [<span data-ttu-id="bbb8e-136">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="bbb8e-136">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
