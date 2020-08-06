---
title: " (DTA) 建立元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 407f16c3898e56cd393e36c39ed799b83e0092ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686635"
---
# <a name="create-element-dta"></a><span data-ttu-id="88db3-102">Create 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="88db3-102">Create Element (DTA)</span></span>
  <span data-ttu-id="88db3-103">包含使用者指定組態中之索引、統計資料或堆積結構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="88db3-103">Contains information about the indexes, statistics, or heap structures in a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88db3-104">語法</span><span class="sxs-lookup"><span data-stu-id="88db3-104">Syntax</span></span>  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="88db3-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="88db3-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="88db3-106">特性</span><span class="sxs-lookup"><span data-stu-id="88db3-106">Characteristic</span></span>|<span data-ttu-id="88db3-107">描述</span><span class="sxs-lookup"><span data-stu-id="88db3-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="88db3-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="88db3-108">**Data type and length**</span></span>|<span data-ttu-id="88db3-109">無。</span><span class="sxs-lookup"><span data-stu-id="88db3-109">None.</span></span>|  
|<span data-ttu-id="88db3-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="88db3-110">**Default value**</span></span>|<span data-ttu-id="88db3-111">無。</span><span class="sxs-lookup"><span data-stu-id="88db3-111">None.</span></span>|  
|<span data-ttu-id="88db3-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="88db3-112">**Occurrence**</span></span>|<span data-ttu-id="88db3-113">每個實體設計結構類型 (索引、統計資料或堆積結構) 都需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="88db3-113">Required once for each physical design structure type (indexes, statistics, or heap structures).</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="88db3-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="88db3-114">Element Relationships</span></span>  
  
|<span data-ttu-id="88db3-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="88db3-115">Relationship</span></span>|<span data-ttu-id="88db3-116">元素</span><span class="sxs-lookup"><span data-stu-id="88db3-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="88db3-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="88db3-117">**Parent element**</span></span>|[<span data-ttu-id="88db3-118">Recommendation 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="88db3-118">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)|  
|<span data-ttu-id="88db3-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="88db3-119">**Child elements**</span></span>|[<span data-ttu-id="88db3-120">Index 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="88db3-120">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)<br /><br /> <span data-ttu-id="88db3-121">`Statistics`元素 (如需資訊，請參閱[DATABASE ENGINE TUNING ADVISOR XML 架構](https://schemas.microsoft.com/sqlserver/)) </span><span class="sxs-lookup"><span data-stu-id="88db3-121">`Statistics` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span><br /><br /> <span data-ttu-id="88db3-122">`Heap`元素 (如需資訊，請參閱[DATABASE ENGINE TUNING ADVISOR XML 架構](https://schemas.microsoft.com/sqlserver/)) </span><span class="sxs-lookup"><span data-stu-id="88db3-122">`Heap` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88db3-123">備註</span><span class="sxs-lookup"><span data-stu-id="88db3-123">Remarks</span></span>  
 <span data-ttu-id="88db3-124">在 Database Engine Tuning Advisor XML 結構描述中，這個元素的名稱為 **CreateTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="88db3-124">This element is of the **CreateTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="88db3-125">它用來建立使用者指定組態的索引、統計資料和堆積結構。</span><span class="sxs-lookup"><span data-stu-id="88db3-125">It is used to create indexes, statistics, and heap structures for a user-specified configuration.</span></span> <span data-ttu-id="88db3-126">請勿混淆這個 `Create` 元素與可用來建立檢視 (`CreateViewType`) 或資料分割 (`CreatePType`) 的其他類型。</span><span class="sxs-lookup"><span data-stu-id="88db3-126">Do not confuse this `Create` element with the other types that can be used to create views (`CreateViewType`) or partitioning (`CreatePType`).</span></span> <span data-ttu-id="88db3-127">如需這些其他元素類型的相關資訊，請參閱[DATABASE ENGINE TUNING ADVISOR XML 架構](https://schemas.microsoft.com/sqlserver/) `Create` 。</span><span class="sxs-lookup"><span data-stu-id="88db3-127">Refer to the [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information about these other `Create` element types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88db3-128">範例</span><span class="sxs-lookup"><span data-stu-id="88db3-128">Example</span></span>  
 <span data-ttu-id="88db3-129">如需此元素的使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="88db3-129">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88db3-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88db3-130">See Also</span></span>  
 [<span data-ttu-id="88db3-131">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="88db3-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
