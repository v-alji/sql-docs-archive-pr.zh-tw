---
title: 資料行 (DTA) 的名稱元素 |Microsoft Docs
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
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
author: stevestein
ms.author: sstein
ms.openlocfilehash: fad3d9a86a7c5db6b6a7503dc90b5a1540e3618b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686621"
---
# <a name="name-element-for-column-dta"></a><span data-ttu-id="813de-102">資料行的 Name 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="813de-102">Name Element for Column (DTA)</span></span>
  <span data-ttu-id="813de-103">在使用者指定的組態中，指定索引資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="813de-103">Specifies the name for an index column in a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813de-104">語法</span><span class="sxs-lookup"><span data-stu-id="813de-104">Syntax</span></span>  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="813de-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="813de-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="813de-106">特性</span><span class="sxs-lookup"><span data-stu-id="813de-106">Characteristic</span></span>|<span data-ttu-id="813de-107">描述</span><span class="sxs-lookup"><span data-stu-id="813de-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="813de-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="813de-108">**Data type and length**</span></span>|<span data-ttu-id="813de-109">`string`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="813de-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="813de-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="813de-110">**Default value**</span></span>|<span data-ttu-id="813de-111">無。</span><span class="sxs-lookup"><span data-stu-id="813de-111">None.</span></span>|  
|<span data-ttu-id="813de-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="813de-112">**Occurrence**</span></span>|<span data-ttu-id="813de-113">每個 `Column` 元素需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="813de-113">Required once for each `Column` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="813de-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="813de-114">Element Relationships</span></span>  
  
|<span data-ttu-id="813de-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="813de-115">Relationship</span></span>|<span data-ttu-id="813de-116">元素</span><span class="sxs-lookup"><span data-stu-id="813de-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="813de-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="813de-117">**Parent element**</span></span>|[<span data-ttu-id="813de-118">索引的 Column 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="813de-118">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)|  
|<span data-ttu-id="813de-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="813de-119">**Child elements**</span></span>|<span data-ttu-id="813de-120">無。</span><span class="sxs-lookup"><span data-stu-id="813de-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="813de-121">範例</span><span class="sxs-lookup"><span data-stu-id="813de-121">Example</span></span>  
 <span data-ttu-id="813de-122">如需此元素的使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="813de-122">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813de-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="813de-123">See Also</span></span>  
 [<span data-ttu-id="813de-124">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="813de-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
