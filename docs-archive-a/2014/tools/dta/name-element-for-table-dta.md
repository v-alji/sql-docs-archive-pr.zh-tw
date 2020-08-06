---
title: 資料表 (DTA) 的 Name 元素 |Microsoft Docs
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
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fa8481cf8990fb63995abcb6300cd9a352c859a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598100"
---
# <a name="name-element-for-table-dta"></a><span data-ttu-id="ae0e5-102">資料表的 Name 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ae0e5-102">Name Element for Table (DTA)</span></span>
  <span data-ttu-id="ae0e5-103">指定要微調的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="ae0e5-103">Specifies a table name for tuning.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae0e5-104">Syntax</span></span>  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="ae0e5-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="ae0e5-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="ae0e5-106">特性</span><span class="sxs-lookup"><span data-stu-id="ae0e5-106">Characteristic</span></span>|<span data-ttu-id="ae0e5-107">描述</span><span class="sxs-lookup"><span data-stu-id="ae0e5-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ae0e5-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="ae0e5-108">**Data type and length**</span></span>|<span data-ttu-id="ae0e5-109">`string`，在 1 和 255 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="ae0e5-109">`string`, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="ae0e5-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="ae0e5-110">**Default value**</span></span>|<span data-ttu-id="ae0e5-111">無。</span><span class="sxs-lookup"><span data-stu-id="ae0e5-111">None.</span></span>|  
|<span data-ttu-id="ae0e5-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="ae0e5-112">**Occurrence**</span></span>|<span data-ttu-id="ae0e5-113">必要。</span><span class="sxs-lookup"><span data-stu-id="ae0e5-113">Required.</span></span> <span data-ttu-id="ae0e5-114">每個 `Table` 元素使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="ae0e5-114">Once for each `Table` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="ae0e5-115">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="ae0e5-115">Element Relationships</span></span>  
  
|<span data-ttu-id="ae0e5-116">關聯性</span><span class="sxs-lookup"><span data-stu-id="ae0e5-116">Relationship</span></span>|<span data-ttu-id="ae0e5-117">元素</span><span class="sxs-lookup"><span data-stu-id="ae0e5-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="ae0e5-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="ae0e5-118">**Parent element**</span></span>|[<span data-ttu-id="ae0e5-119">結構描述的 Table 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="ae0e5-119">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
|<span data-ttu-id="ae0e5-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="ae0e5-120">**Child elements**</span></span>|<span data-ttu-id="ae0e5-121">無。</span><span class="sxs-lookup"><span data-stu-id="ae0e5-121">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae0e5-122">範例</span><span class="sxs-lookup"><span data-stu-id="ae0e5-122">Example</span></span>  
 <span data-ttu-id="ae0e5-123">如需使用範例，請參閱[伺服器元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="ae0e5-123">For a usage example, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0e5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae0e5-124">See Also</span></span>  
 [<span data-ttu-id="ae0e5-125">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="ae0e5-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
