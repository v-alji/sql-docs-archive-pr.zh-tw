---
title: 架構 (DTA) 的 Name 元素 |Microsoft Docs
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
ms.assetid: 014e4854-fed2-454b-8557-5f7c5bb6b17a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 678a6d58b35b25be2aed6d91fcae7ceb2640bdcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703598"
---
# <a name="name-element-for-schema-dta"></a><span data-ttu-id="96dd7-102">結構描述的 Name 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="96dd7-102">Name Element for Schema (DTA)</span></span>
  <span data-ttu-id="96dd7-103">包含結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="96dd7-103">Contains name of the schema.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96dd7-104">語法</span><span class="sxs-lookup"><span data-stu-id="96dd7-104">Syntax</span></span>  
  
```  
  
<Database>  
...code removed here  
    <Schema>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="96dd7-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="96dd7-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="96dd7-106">特性</span><span class="sxs-lookup"><span data-stu-id="96dd7-106">Characteristic</span></span>|<span data-ttu-id="96dd7-107">描述</span><span class="sxs-lookup"><span data-stu-id="96dd7-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="96dd7-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="96dd7-108">**Data type and length**</span></span>|<span data-ttu-id="96dd7-109">`string`，在 1 和 255 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="96dd7-109">`string`, between 1 and 255 characters</span></span>|  
|<span data-ttu-id="96dd7-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="96dd7-110">**Default value**</span></span>|<span data-ttu-id="96dd7-111">無。</span><span class="sxs-lookup"><span data-stu-id="96dd7-111">None.</span></span>|  
|<span data-ttu-id="96dd7-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="96dd7-112">**Occurrence**</span></span>|<span data-ttu-id="96dd7-113">每個 **Schema** 元素需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="96dd7-113">Required once per **Schema** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="96dd7-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="96dd7-114">Element Relationships</span></span>  
  
|<span data-ttu-id="96dd7-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="96dd7-115">Relationship</span></span>|<span data-ttu-id="96dd7-116">元素</span><span class="sxs-lookup"><span data-stu-id="96dd7-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="96dd7-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="96dd7-117">**Parent element**</span></span>|[<span data-ttu-id="96dd7-118">資料庫的 Schema 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="96dd7-118">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
|<span data-ttu-id="96dd7-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="96dd7-119">**Child elements**</span></span>|<span data-ttu-id="96dd7-120">無。</span><span class="sxs-lookup"><span data-stu-id="96dd7-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96dd7-121">範例</span><span class="sxs-lookup"><span data-stu-id="96dd7-121">Example</span></span>  
 <span data-ttu-id="96dd7-122">如需此元素的使用範例，請參閱 [Server 元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="96dd7-122">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96dd7-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96dd7-123">See Also</span></span>  
 [<span data-ttu-id="96dd7-124">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="96dd7-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
