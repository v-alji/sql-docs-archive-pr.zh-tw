---
title: " (DTA) 的 Configuration 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d11938d9a9a694f994a3ea977022a393cbae23d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686645"
---
# <a name="configuration-element-dta"></a><span data-ttu-id="7e404-102">Configuration 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="7e404-102">Configuration Element (DTA)</span></span>
  <span data-ttu-id="7e404-103">指定由現有的實體設計結構和假設的實體設計結構所組成，供 Database Engine Tuning Advisor 在微調工作負載時進行分析的使用者指定組態。</span><span class="sxs-lookup"><span data-stu-id="7e404-103">Specifies a user-specified configuration consisting of existing and hypothetical physical design structures for the Database Engine Tuning Advisor to analyze when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e404-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e404-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="7e404-105">元素屬性</span><span class="sxs-lookup"><span data-stu-id="7e404-105">Element Attributes</span></span>  
  
|<span data-ttu-id="7e404-106">組態屬性</span><span class="sxs-lookup"><span data-stu-id="7e404-106">Configuration Attribute</span></span>|<span data-ttu-id="7e404-107">描述</span><span class="sxs-lookup"><span data-stu-id="7e404-107">Description</span></span>|  
|-----------------------------|-----------------|  
|`SpecificationMode`|<span data-ttu-id="7e404-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7e404-108">Optional.</span></span> <span data-ttu-id="7e404-109">指定 Database Engine Tuning Advisor 應該關聯於目前現有的組態來分析指定的組態，或將它當作全新的獨立組態來進行分析。</span><span class="sxs-lookup"><span data-stu-id="7e404-109">Specifies whether Database Engine Tuning Advisor should analyze the specified configuration in relation to the current existing configuration, or as a completely new, standalone one.</span></span> <span data-ttu-id="7e404-110">請利用 **string** 資料類型和下列其中一個允許的值，來指定這個屬性：</span><span class="sxs-lookup"><span data-stu-id="7e404-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="7e404-111">`Relative`:</span><span class="sxs-lookup"><span data-stu-id="7e404-111">`Relative`:</span></span> <br />                  <span data-ttu-id="7e404-112">關聯於正在微調的資料庫其中之實體設計結構 (索引、索引檢視、資料分割) 目前現有的組態來評估指定的組態。</span><span class="sxs-lookup"><span data-stu-id="7e404-112">Evaluates the specified configuration in relation to the current existing configuration of physical design structures (indexes, indexed views, partitioning) in the database that is being tuned.</span></span> <span data-ttu-id="7e404-113">例如：</span><span class="sxs-lookup"><span data-stu-id="7e404-113">For example:</span></span> <br />`<Configuration SpecificationMode="Relative">`<br /><br /> <span data-ttu-id="7e404-114">`Absolute`:</span><span class="sxs-lookup"><span data-stu-id="7e404-114">`Absolute`:</span></span> <br />                  <span data-ttu-id="7e404-115">將指定的組態當作獨立組態來評估。</span><span class="sxs-lookup"><span data-stu-id="7e404-115">Evaluates the specified configuration as a standalone configuration.</span></span> <span data-ttu-id="7e404-116">當指定 Absolute 時，Database Engine Tuning Advisor 不會考慮現有的組態。</span><span class="sxs-lookup"><span data-stu-id="7e404-116">When Absolute is specified, Database Engine Tuning Advisor does not consider the existing configuration.</span></span> <span data-ttu-id="7e404-117">例如：</span><span class="sxs-lookup"><span data-stu-id="7e404-117">For example:</span></span><br />`<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="7e404-118">元素特性</span><span class="sxs-lookup"><span data-stu-id="7e404-118">Element Characteristics</span></span>  
  
|<span data-ttu-id="7e404-119">特性</span><span class="sxs-lookup"><span data-stu-id="7e404-119">Characteristic</span></span>|<span data-ttu-id="7e404-120">描述</span><span class="sxs-lookup"><span data-stu-id="7e404-120">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="7e404-121">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="7e404-121">**Data type and length**</span></span>|<span data-ttu-id="7e404-122">無。</span><span class="sxs-lookup"><span data-stu-id="7e404-122">None.</span></span>|  
|<span data-ttu-id="7e404-123">**預設值**</span><span class="sxs-lookup"><span data-stu-id="7e404-123">**Default value**</span></span>|<span data-ttu-id="7e404-124">無。</span><span class="sxs-lookup"><span data-stu-id="7e404-124">None.</span></span>|  
|<span data-ttu-id="7e404-125">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="7e404-125">**Occurrence**</span></span>|<span data-ttu-id="7e404-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7e404-126">Optional.</span></span> <span data-ttu-id="7e404-127">每個 `DTAInput` 元素可以使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="7e404-127">Can use once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="7e404-128">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="7e404-128">Element Relationships</span></span>  
  
|<span data-ttu-id="7e404-129">關聯性</span><span class="sxs-lookup"><span data-stu-id="7e404-129">Relationship</span></span>|<span data-ttu-id="7e404-130">元素</span><span class="sxs-lookup"><span data-stu-id="7e404-130">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="7e404-131">**父元素**</span><span class="sxs-lookup"><span data-stu-id="7e404-131">**Parent element**</span></span>|[<span data-ttu-id="7e404-132">DTAInput 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7e404-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="7e404-133">**子元素**</span><span class="sxs-lookup"><span data-stu-id="7e404-133">**Child elements**</span></span>|[<span data-ttu-id="7e404-134">組態的 Server 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="7e404-134">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="7e404-135">範例</span><span class="sxs-lookup"><span data-stu-id="7e404-135">Example</span></span>  
 <span data-ttu-id="7e404-136">如需此元素的使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="7e404-136">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e404-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e404-137">See Also</span></span>  
 [<span data-ttu-id="7e404-138">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="7e404-138">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
