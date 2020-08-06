---
title: " (DTA) 的 DropOnlyMode 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b274dc394a933308cf2161cc271d09b8391900c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686628"
---
# <a name="droponlymode-element-dta"></a><span data-ttu-id="8ba52-102">DropOnlyMode 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="8ba52-102">DropOnlyMode Element (DTA)</span></span>
  <span data-ttu-id="8ba52-103">指定在微調工作階段期間，Database Engine Tuning Advisor 只應考慮卸除現有的索引、索引檢視或資料分割。</span><span class="sxs-lookup"><span data-stu-id="8ba52-103">Specifies that Database Engine Tuning Advisor should only consider dropping existing indexes, indexed views, or partitions during the tuning session.</span></span> <span data-ttu-id="8ba52-104">當指定這個微調選項時，不考慮任何新的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="8ba52-104">No new physical design structures are considered when this tuning option is specified.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ba52-105">語法</span><span class="sxs-lookup"><span data-stu-id="8ba52-105">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="8ba52-106">元素特性</span><span class="sxs-lookup"><span data-stu-id="8ba52-106">Element Characteristics</span></span>  
  
|<span data-ttu-id="8ba52-107">特性</span><span class="sxs-lookup"><span data-stu-id="8ba52-107">Characteristic</span></span>|<span data-ttu-id="8ba52-108">描述</span><span class="sxs-lookup"><span data-stu-id="8ba52-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8ba52-109">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="8ba52-109">**Data type and length**</span></span>|<span data-ttu-id="8ba52-110">無。</span><span class="sxs-lookup"><span data-stu-id="8ba52-110">None.</span></span>|  
|<span data-ttu-id="8ba52-111">**預設值**</span><span class="sxs-lookup"><span data-stu-id="8ba52-111">**Default value**</span></span>|<span data-ttu-id="8ba52-112">無。</span><span class="sxs-lookup"><span data-stu-id="8ba52-112">None.</span></span>|  
|<span data-ttu-id="8ba52-113">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="8ba52-113">**Occurrence**</span></span>|<span data-ttu-id="8ba52-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8ba52-114">Optional.</span></span> <span data-ttu-id="8ba52-115">每個 `TuningOptions` 元素只能使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="8ba52-115">Can use only once for each `TuningOptions` element.</span></span> <span data-ttu-id="8ba52-116">如果在 `TuningOptions` 元素中指定了下列元素，就不能使用這個元素：</span><span class="sxs-lookup"><span data-stu-id="8ba52-116">Cannot be used if the following elements are specified in the `TuningOptions` element:</span></span><br /><br /> [<span data-ttu-id="8ba52-117">FeatureSet 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8ba52-117">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)<br /><br /> [<span data-ttu-id="8ba52-118">Partitioning 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8ba52-118">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)<br /><br /> <span data-ttu-id="8ba52-119">[KeepExisting 元素 &#40;DTA&#41;](keepexisting-element-dta.md) 設為 **ALL**</span><span class="sxs-lookup"><span data-stu-id="8ba52-119">[KeepExisting Element &#40;DTA&#41;](keepexisting-element-dta.md) is set to **ALL**</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8ba52-120">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="8ba52-120">Element Relationships</span></span>  
  
|<span data-ttu-id="8ba52-121">關聯性</span><span class="sxs-lookup"><span data-stu-id="8ba52-121">Relationship</span></span>|<span data-ttu-id="8ba52-122">元素</span><span class="sxs-lookup"><span data-stu-id="8ba52-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8ba52-123">**父元素**</span><span class="sxs-lookup"><span data-stu-id="8ba52-123">**Parent element**</span></span>|[<span data-ttu-id="8ba52-124">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8ba52-124">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="8ba52-125">**子元素**</span><span class="sxs-lookup"><span data-stu-id="8ba52-125">**Child elements**</span></span>|<span data-ttu-id="8ba52-126">無。</span><span class="sxs-lookup"><span data-stu-id="8ba52-126">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8ba52-127">範例</span><span class="sxs-lookup"><span data-stu-id="8ba52-127">Example</span></span>  
 <span data-ttu-id="8ba52-128">下列範例顯示指定了 `TuningOptions` 的 Database Engine Tuning Advisor XML 輸入檔的 `DropOnlyMode` 區段。</span><span class="sxs-lookup"><span data-stu-id="8ba52-128">The following example shows the `TuningOptions` section of a Database Engine Tuning Advisor XML input file where the `DropOnlyMode` is specified.</span></span> <span data-ttu-id="8ba52-129">在這個範例中，微調時間只限 24 小時 (1440 分鐘)，所有現有的叢集和非叢集索引都將考慮卸除：</span><span class="sxs-lookup"><span data-stu-id="8ba52-129">In this example the tuning time is limited to 24 hours (1440 minutes) and all existing clustered and nonclustered indexes will be considered for dropping:</span></span>  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ba52-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ba52-130">See Also</span></span>  
 [<span data-ttu-id="8ba52-131">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="8ba52-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
