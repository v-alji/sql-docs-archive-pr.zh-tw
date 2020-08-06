---
title: " (DTA) 的索引的 Filegroup 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Filegroup element [DTA]
ms.assetid: 7078d2fb-fa77-44fc-beb3-c095088fcb85
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ed8ea723d6c0798b93e16411ee47d6e956c6c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704581"
---
# <a name="filegroup-element-for-index-dta"></a><span data-ttu-id="46689-102">索引的 Filegroup 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="46689-102">Filegroup Element for Index (DTA)</span></span>
  <span data-ttu-id="46689-103">指定要針對使用者指定的組態來建立索引的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="46689-103">Specifies the filegroup on which the index is to be created for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46689-104">語法</span><span class="sxs-lookup"><span data-stu-id="46689-104">Syntax</span></span>  
  
```  
  
<Index>  
  <Name>...</Name>  
  <Column>  
    <Name>...</Name>  
  <Filegroup>...</Filegroup>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="46689-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="46689-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="46689-106">特性</span><span class="sxs-lookup"><span data-stu-id="46689-106">Characteristic</span></span>|<span data-ttu-id="46689-107">描述</span><span class="sxs-lookup"><span data-stu-id="46689-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="46689-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="46689-108">**Data type and length**</span></span>|<span data-ttu-id="46689-109">`string`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="46689-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="46689-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="46689-110">**Default value**</span></span>|<span data-ttu-id="46689-111">無。</span><span class="sxs-lookup"><span data-stu-id="46689-111">None.</span></span>|  
|<span data-ttu-id="46689-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="46689-112">**Occurrence**</span></span>|<span data-ttu-id="46689-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="46689-113">Optional.</span></span> <span data-ttu-id="46689-114">每個 `Index` 元素可以使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="46689-114">Can use once for each `Index` element.</span></span> <span data-ttu-id="46689-115">如果指定了 `PartitionScheme` 元素的 `PartitionColumn` 和 `Index` 元素，就不能使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="46689-115">This element cannot be used if the `PartitionScheme` and `PartitionColumn` elements are specified for the `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="46689-116">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="46689-116">Element Relationships</span></span>  
  
|<span data-ttu-id="46689-117">關聯性</span><span class="sxs-lookup"><span data-stu-id="46689-117">Relationship</span></span>|<span data-ttu-id="46689-118">元素</span><span class="sxs-lookup"><span data-stu-id="46689-118">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="46689-119">**父元素**</span><span class="sxs-lookup"><span data-stu-id="46689-119">**Parent element**</span></span>|[<span data-ttu-id="46689-120">Index 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="46689-120">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="46689-121">**子元素**</span><span class="sxs-lookup"><span data-stu-id="46689-121">**Child elements**</span></span>|<span data-ttu-id="46689-122">無。</span><span class="sxs-lookup"><span data-stu-id="46689-122">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="46689-123">範例</span><span class="sxs-lookup"><span data-stu-id="46689-123">Example</span></span>  
 <span data-ttu-id="46689-124">如需此元素的使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="46689-124">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46689-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46689-125">See Also</span></span>  
 [<span data-ttu-id="46689-126">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="46689-126">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
