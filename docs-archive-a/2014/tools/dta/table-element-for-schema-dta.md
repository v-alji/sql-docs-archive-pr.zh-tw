---
title: 用於架構 (DTA) 的 Table 元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd444b1da99b22e0259dc1f50818c1763b7052ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704577"
---
# <a name="table-element-for-schema-dta"></a><span data-ttu-id="d16dd-102">結構描述的 Table 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="d16dd-102">Table Element for Schema (DTA)</span></span>
  <span data-ttu-id="d16dd-103">指定要微調的資料表。</span><span class="sxs-lookup"><span data-stu-id="d16dd-103">Specifies the table for tuning.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d16dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="d16dd-104">Syntax</span></span>  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="d16dd-105">元素屬性</span><span class="sxs-lookup"><span data-stu-id="d16dd-105">Element Attributes</span></span>  
  
|<span data-ttu-id="d16dd-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d16dd-106">Attribute</span></span>|<span data-ttu-id="d16dd-107">描述</span><span class="sxs-lookup"><span data-stu-id="d16dd-107">Description</span></span>|  
|---------------|-----------------|  
|`NumberOfRows`|<span data-ttu-id="d16dd-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d16dd-108">Optional.</span></span> <span data-ttu-id="d16dd-109">可讓您模擬不同大小的資料表之整數。</span><span class="sxs-lookup"><span data-stu-id="d16dd-109">Integer that allows you to simulate tables of different sizes.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="d16dd-110">元素特性</span><span class="sxs-lookup"><span data-stu-id="d16dd-110">Element Characteristics</span></span>  
  
|<span data-ttu-id="d16dd-111">特性</span><span class="sxs-lookup"><span data-stu-id="d16dd-111">Characteristic</span></span>|<span data-ttu-id="d16dd-112">描述</span><span class="sxs-lookup"><span data-stu-id="d16dd-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d16dd-113">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="d16dd-113">**Data type and length**</span></span>|<span data-ttu-id="d16dd-114">**string**，在 1 和 255 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="d16dd-114">**string**, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="d16dd-115">**預設值**</span><span class="sxs-lookup"><span data-stu-id="d16dd-115">**Default value**</span></span>|<span data-ttu-id="d16dd-116">無。</span><span class="sxs-lookup"><span data-stu-id="d16dd-116">None.</span></span>|  
|<span data-ttu-id="d16dd-117">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="d16dd-117">**Occurrence**</span></span>|<span data-ttu-id="d16dd-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d16dd-118">Optional.</span></span> <span data-ttu-id="d16dd-119">依照工作負載的需要，列出儘可能多的資料表。</span><span class="sxs-lookup"><span data-stu-id="d16dd-119">List as many tables as appropriate for your workload.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d16dd-120">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="d16dd-120">Element Relationships</span></span>  
  
|<span data-ttu-id="d16dd-121">關聯性</span><span class="sxs-lookup"><span data-stu-id="d16dd-121">Relationship</span></span>|<span data-ttu-id="d16dd-122">元素</span><span class="sxs-lookup"><span data-stu-id="d16dd-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d16dd-123">**父元素**</span><span class="sxs-lookup"><span data-stu-id="d16dd-123">**Parent element**</span></span>|[<span data-ttu-id="d16dd-124">資料庫的 Schema 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d16dd-124">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
|<span data-ttu-id="d16dd-125">**子元素**</span><span class="sxs-lookup"><span data-stu-id="d16dd-125">**Child elements**</span></span>|[<span data-ttu-id="d16dd-126">資料表的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d16dd-126">Name Element for Table &#40;DTA&#41;</span></span>](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="d16dd-127">備註</span><span class="sxs-lookup"><span data-stu-id="d16dd-127">Remarks</span></span>  
 <span data-ttu-id="d16dd-128">如果您沒有指定 `Table` 元素，Database Engine Tuning Advisor 會假設指定資料庫的所有資料表都可以微調。</span><span class="sxs-lookup"><span data-stu-id="d16dd-128">If you do not specify a `Table` element, Database Engine Tuning Advisor will assume all tables on the specified database can be tuned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d16dd-129">範例</span><span class="sxs-lookup"><span data-stu-id="d16dd-129">Example</span></span>  
 <span data-ttu-id="d16dd-130">如需使用範例，請參閱[伺服器元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="d16dd-130">For a usage example, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d16dd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d16dd-131">See Also</span></span>  
 [<span data-ttu-id="d16dd-132">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="d16dd-132">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
