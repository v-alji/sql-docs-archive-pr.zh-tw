---
title: " (DTA) 的建議元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4eb54a106d67f0217a2604b2d08754d0d2c0765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592415"
---
# <a name="recommendation-element-dta"></a><span data-ttu-id="1fb6e-102">Recommendation 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="1fb6e-102">Recommendation Element (DTA)</span></span>
  <span data-ttu-id="1fb6e-103">包含屬於使用者指定組態之一部份的假設性索引的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-103">Contains information about the hypothetical indexes that are part of a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1fb6e-104">Syntax</span></span>  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="1fb6e-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="1fb6e-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="1fb6e-106">特性</span><span class="sxs-lookup"><span data-stu-id="1fb6e-106">Characteristic</span></span>|<span data-ttu-id="1fb6e-107">描述</span><span class="sxs-lookup"><span data-stu-id="1fb6e-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1fb6e-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-108">**Data type and length**</span></span>|<span data-ttu-id="1fb6e-109">無。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-109">None.</span></span>|  
|<span data-ttu-id="1fb6e-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-110">**Default value**</span></span>|<span data-ttu-id="1fb6e-111">無。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-111">None.</span></span>|  
|<span data-ttu-id="1fb6e-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-112">**Occurrence**</span></span>|<span data-ttu-id="1fb6e-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-113">Optional.</span></span> <span data-ttu-id="1fb6e-114">每個 `Table` 元素可以使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-114">Can use once for each `Table` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="1fb6e-115">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="1fb6e-115">Element Relationships</span></span>  
  
|<span data-ttu-id="1fb6e-116">關聯性</span><span class="sxs-lookup"><span data-stu-id="1fb6e-116">Relationship</span></span>|<span data-ttu-id="1fb6e-117">元素</span><span class="sxs-lookup"><span data-stu-id="1fb6e-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="1fb6e-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-118">**Parent element**</span></span>|[<span data-ttu-id="1fb6e-119">結構描述的 Table 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="1fb6e-119">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
|<span data-ttu-id="1fb6e-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="1fb6e-120">**Child elements**</span></span>|[<span data-ttu-id="1fb6e-121">Create 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="1fb6e-121">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)<br /><br /> <span data-ttu-id="1fb6e-122">`Drop` 元素。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-122">`Drop` element.</span></span> <span data-ttu-id="1fb6e-123">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-123">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fb6e-124">備註</span><span class="sxs-lookup"><span data-stu-id="1fb6e-124">Remarks</span></span>  
 <span data-ttu-id="1fb6e-125">在 Database Engine Tuning Advisor XML 結構描述中，這個元素的名稱為 **RecommendationTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-125">This element is of the **RecommendationTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="1fb6e-126">它用來指定假設性組態的索引。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-126">It is used to specify indexes for a hypothetical configuration.</span></span> <span data-ttu-id="1fb6e-127">請勿混淆這個 `Recommendation` 元素與可用來指定資料分割 (`RecommendationPType`) 或檢視 (`RecommendationViewType`) 的其他類型。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-127">Do not confuse this `Recommendation` element with the other types that can be used to specify partitioning (`RecommendationPType`) or views (`RecommendationViewType`).</span></span> <span data-ttu-id="1fb6e-128">如需這些其他元素類型的詳細資訊 `Recommendation` ，請參閱[Database Engine Tuning Advisor XML 架構](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-128">For information about these other `Recommendation` element types, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fb6e-129">範例</span><span class="sxs-lookup"><span data-stu-id="1fb6e-129">Example</span></span>  
 <span data-ttu-id="1fb6e-130">如需此元素的使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="1fb6e-130">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb6e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fb6e-131">See Also</span></span>  
 [<span data-ttu-id="1fb6e-132">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="1fb6e-132">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
