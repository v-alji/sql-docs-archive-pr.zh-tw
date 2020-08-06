---
title: " (DTA) 的索引的資料行元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67853dc7d1193d3a0f80e56023846bc55a20bdaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686647"
---
# <a name="column-element-for-index-dta"></a><span data-ttu-id="6c51c-102">索引的 Column 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="6c51c-102">Column Element for Index (DTA)</span></span>
  <span data-ttu-id="6c51c-103">指定針對使用者指定的組態來建立索引的資料行。</span><span class="sxs-lookup"><span data-stu-id="6c51c-103">Specifies the columns on which the index is created for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c51c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c51c-104">Syntax</span></span>  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="6c51c-105">元素屬性</span><span class="sxs-lookup"><span data-stu-id="6c51c-105">Element Attributes</span></span>  
  
|<span data-ttu-id="6c51c-106">資料行屬性</span><span class="sxs-lookup"><span data-stu-id="6c51c-106">Column Attribute</span></span>|<span data-ttu-id="6c51c-107">描述</span><span class="sxs-lookup"><span data-stu-id="6c51c-107">Description</span></span>|  
|----------------------|-----------------|  
|`Type`|<span data-ttu-id="6c51c-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6c51c-108">Optional.</span></span> <span data-ttu-id="6c51c-109">指定索引資料行類型。</span><span class="sxs-lookup"><span data-stu-id="6c51c-109">Specifies the index column type.</span></span> <span data-ttu-id="6c51c-110">請利用 **string** 資料類型和下列其中一個允許的值，來指定這個屬性：</span><span class="sxs-lookup"><span data-stu-id="6c51c-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="6c51c-111">`KeyColumn`:</span><span class="sxs-lookup"><span data-stu-id="6c51c-111">`KeyColumn`:</span></span><br />                  <span data-ttu-id="6c51c-112">指定由索引鍵參考資料行。</span><span class="sxs-lookup"><span data-stu-id="6c51c-112">Specifies that the column is referenced by an index key.</span></span> <span data-ttu-id="6c51c-113">請利用下列語法來設定這個屬性：</span><span class="sxs-lookup"><span data-stu-id="6c51c-113">Use the following syntax to set this attribute:</span></span><br />`<Column Type="KeyColumn">`<br /><span data-ttu-id="6c51c-114">如需索引鍵資料行的詳細資訊，請參閱 [叢集與非叢集索引說明](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)。</span><span class="sxs-lookup"><span data-stu-id="6c51c-114">For more information about key columns, see [Clustered and Nonclustered Indexes Described](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).</span></span><br /><br /> <span data-ttu-id="6c51c-115">`IncludedColumn`：指定資料行是包含的資料行 (，而不是索引鍵資料行) 。</span><span class="sxs-lookup"><span data-stu-id="6c51c-115">`IncludedColumn`: Specifies that the column is an included column (instead of a key column).</span></span> <span data-ttu-id="6c51c-116">請利用下列語法來設定這個屬性：</span><span class="sxs-lookup"><span data-stu-id="6c51c-116">Use the following syntax to set this attribute:</span></span><br />`<Column Type="IncludedColumn">`<br /><span data-ttu-id="6c51c-117">如需內含資料行的詳細資訊，請參閱 [建立內含資料行的索引](../../relational-databases/indexes/create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="6c51c-117">For more information about included columns, see [Create Indexes with Included Columns](../../relational-databases/indexes/create-indexes-with-included-columns.md).</span></span>|  
|`SortOrder`|<span data-ttu-id="6c51c-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6c51c-118">Optional.</span></span> <span data-ttu-id="6c51c-119">指定資料行的排序順序。</span><span class="sxs-lookup"><span data-stu-id="6c51c-119">Specifies the sorting order of the column.</span></span> <span data-ttu-id="6c51c-120">請依照下列方式，利用 **string** 資料類型來指定「遞增」  或「遞減」  排列順序：</span><span class="sxs-lookup"><span data-stu-id="6c51c-120">Use a **string** data type to specify either an **"Ascending"** or **"Descending"** sorting order as follows:</span></span><br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="6c51c-121">元素特性</span><span class="sxs-lookup"><span data-stu-id="6c51c-121">Element Characteristics</span></span>  
  
|<span data-ttu-id="6c51c-122">特性</span><span class="sxs-lookup"><span data-stu-id="6c51c-122">Characteristic</span></span>|<span data-ttu-id="6c51c-123">描述</span><span class="sxs-lookup"><span data-stu-id="6c51c-123">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6c51c-124">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="6c51c-124">**Data type and length**</span></span>|<span data-ttu-id="6c51c-125">無。</span><span class="sxs-lookup"><span data-stu-id="6c51c-125">None.</span></span>|  
|<span data-ttu-id="6c51c-126">**預設值**</span><span class="sxs-lookup"><span data-stu-id="6c51c-126">**Default value**</span></span>|<span data-ttu-id="6c51c-127">無。</span><span class="sxs-lookup"><span data-stu-id="6c51c-127">None.</span></span>|  
|<span data-ttu-id="6c51c-128">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="6c51c-128">**Occurrence**</span></span>|<span data-ttu-id="6c51c-129"> 元素可以指定最多 1024 個資料行。</span><span class="sxs-lookup"><span data-stu-id="6c51c-129">Can specify up to 1024 columns for the `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="6c51c-130">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="6c51c-130">Element Relationships</span></span>  
  
|<span data-ttu-id="6c51c-131">關聯性</span><span class="sxs-lookup"><span data-stu-id="6c51c-131">Relationship</span></span>|<span data-ttu-id="6c51c-132">元素</span><span class="sxs-lookup"><span data-stu-id="6c51c-132">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="6c51c-133">**父元素**</span><span class="sxs-lookup"><span data-stu-id="6c51c-133">**Parent element**</span></span>|[<span data-ttu-id="6c51c-134">Index 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="6c51c-134">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="6c51c-135">**子元素**</span><span class="sxs-lookup"><span data-stu-id="6c51c-135">**Child elements**</span></span>|[<span data-ttu-id="6c51c-136">資料行的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="6c51c-136">Name Element for Column &#40;DTA&#41;</span></span>](name-element-for-column-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="6c51c-137">範例</span><span class="sxs-lookup"><span data-stu-id="6c51c-137">Example</span></span>  
 <span data-ttu-id="6c51c-138">如需此元素的使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="6c51c-138">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c51c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c51c-139">See Also</span></span>  
 [<span data-ttu-id="6c51c-140">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="6c51c-140">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
