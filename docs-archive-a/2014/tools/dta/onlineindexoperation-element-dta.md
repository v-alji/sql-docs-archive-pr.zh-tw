---
title: " (DTA) 的 OnlineIndexOperation 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48943c1b31d7a0a24ae939050d44494476e50034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598099"
---
# <a name="onlineindexoperation-element-dta"></a><span data-ttu-id="0a19b-102">OnlineIndexOperation 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="0a19b-102">OnlineIndexOperation Element (DTA)</span></span>
  <span data-ttu-id="0a19b-103">指定是否能夠在線上建立 Database Engine Tuning Advisor 建議的索引、索引檢視或資料分割。</span><span class="sxs-lookup"><span data-stu-id="0a19b-103">Specifies whether the indexes, indexed views, or partitions that Database Engine Tuning Advisor recommends can be created online.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a19b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a19b-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="0a19b-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="0a19b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="0a19b-106">特性</span><span class="sxs-lookup"><span data-stu-id="0a19b-106">Characteristic</span></span>|<span data-ttu-id="0a19b-107">描述</span><span class="sxs-lookup"><span data-stu-id="0a19b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0a19b-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="0a19b-108">**Data type and length**</span></span>|<span data-ttu-id="0a19b-109">`string`，沒有最大長度。</span><span class="sxs-lookup"><span data-stu-id="0a19b-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="0a19b-110">**允許的值**</span><span class="sxs-lookup"><span data-stu-id="0a19b-110">**Allowed values**</span></span>|<span data-ttu-id="0a19b-111">**OFF**</span><span class="sxs-lookup"><span data-stu-id="0a19b-111">**OFF**</span></span><br /> <span data-ttu-id="0a19b-112">不能在線上建立任何建議的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="0a19b-112">No recommended physical design structures can be created online.</span></span><br /><br /> <span data-ttu-id="0a19b-113">**ON**</span><span class="sxs-lookup"><span data-stu-id="0a19b-113">**ON**</span></span><br /> <span data-ttu-id="0a19b-114">可以在線上建立所有建議的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="0a19b-114">All recommended physical design structures can be created online.</span></span><br /><br /> <span data-ttu-id="0a19b-115">**MIXED**</span><span class="sxs-lookup"><span data-stu-id="0a19b-115">**MIXED**</span></span><br /> <span data-ttu-id="0a19b-116">Database Engine Tuning Advisor 嘗試建議在可能的情況下，能夠在線上建立的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="0a19b-116">Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.</span></span><br /><br /> <span data-ttu-id="0a19b-117">這個元素使用這些值的其中之一。</span><span class="sxs-lookup"><span data-stu-id="0a19b-117">Use one of these values with this element.</span></span> <span data-ttu-id="0a19b-118">如果在線上建立索引，就會在它的物件定義上附加關鍵字 **ONLINE = ON** 。</span><span class="sxs-lookup"><span data-stu-id="0a19b-118">If indexes are created online, the keyword **ONLINE = ON** is appended to its object definition.</span></span>|  
|<span data-ttu-id="0a19b-119">**預設值**</span><span class="sxs-lookup"><span data-stu-id="0a19b-119">**Default value**</span></span>|<span data-ttu-id="0a19b-120">無。</span><span class="sxs-lookup"><span data-stu-id="0a19b-120">None.</span></span>|  
|<span data-ttu-id="0a19b-121">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="0a19b-121">**Occurrence**</span></span>|<span data-ttu-id="0a19b-122">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a19b-122">Optional.</span></span> <span data-ttu-id="0a19b-123">如果使用這個元素的話，`TuningOptions` 元素只能使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="0a19b-123">If used, can only be used once for the `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="0a19b-124">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="0a19b-124">Element Relationships</span></span>  
  
|<span data-ttu-id="0a19b-125">關聯性</span><span class="sxs-lookup"><span data-stu-id="0a19b-125">Relationship</span></span>|<span data-ttu-id="0a19b-126">元素</span><span class="sxs-lookup"><span data-stu-id="0a19b-126">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="0a19b-127">**父元素**</span><span class="sxs-lookup"><span data-stu-id="0a19b-127">**Parent element**</span></span>|[<span data-ttu-id="0a19b-128">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0a19b-128">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="0a19b-129">**子元素**</span><span class="sxs-lookup"><span data-stu-id="0a19b-129">**Child elements**</span></span>|<span data-ttu-id="0a19b-130">無。</span><span class="sxs-lookup"><span data-stu-id="0a19b-130">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0a19b-131">範例</span><span class="sxs-lookup"><span data-stu-id="0a19b-131">Example</span></span>  
 <span data-ttu-id="0a19b-132">如需此元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="0a19b-132">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a19b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a19b-133">See Also</span></span>  
 [<span data-ttu-id="0a19b-134">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="0a19b-134">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
