---
title: " (DTA) 的索引名稱元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 2300e9cf-f0a8-49e6-b1f5-45ffe03ccb5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a878923a3d483fae5ad6b55421a2b286f15ceb29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707982"
---
# <a name="name-element-for-index-dta"></a><span data-ttu-id="1074b-102">索引的 Name 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="1074b-102">Name Element for Index (DTA)</span></span>
  <span data-ttu-id="1074b-103">在使用者指定的組態中，指定索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="1074b-103">Specifies a name for an index in the user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1074b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1074b-104">Syntax</span></span>  
  
```  
  
<Create>  
    <Index>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="1074b-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="1074b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="1074b-106">特性</span><span class="sxs-lookup"><span data-stu-id="1074b-106">Characteristic</span></span>|<span data-ttu-id="1074b-107">描述</span><span class="sxs-lookup"><span data-stu-id="1074b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1074b-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="1074b-108">**Data type and length**</span></span>|<span data-ttu-id="1074b-109">`string`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="1074b-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="1074b-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="1074b-110">**Default value**</span></span>|<span data-ttu-id="1074b-111">無。</span><span class="sxs-lookup"><span data-stu-id="1074b-111">None.</span></span>|  
|<span data-ttu-id="1074b-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="1074b-112">**Occurrence**</span></span>|<span data-ttu-id="1074b-113">每個 `Index` 元素需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="1074b-113">Required once for each `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="1074b-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="1074b-114">Element Relationships</span></span>  
  
|<span data-ttu-id="1074b-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="1074b-115">Relationship</span></span>|<span data-ttu-id="1074b-116">元素</span><span class="sxs-lookup"><span data-stu-id="1074b-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="1074b-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="1074b-117">**Parent element**</span></span>|[<span data-ttu-id="1074b-118">Index 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="1074b-118">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="1074b-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="1074b-119">**Child elements**</span></span>|<span data-ttu-id="1074b-120">無。</span><span class="sxs-lookup"><span data-stu-id="1074b-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1074b-121">範例</span><span class="sxs-lookup"><span data-stu-id="1074b-121">Example</span></span>  
 <span data-ttu-id="1074b-122">如需此元素的使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="1074b-122">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1074b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1074b-123">See Also</span></span>  
 [<span data-ttu-id="1074b-124">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="1074b-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
