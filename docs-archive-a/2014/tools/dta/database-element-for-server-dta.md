---
title: 伺服器 (DTA) 的 Database 元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9a48d255898eff6bd780f8edf2c8d2da7229b0ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686632"
---
# <a name="database-element-for-server-dta"></a><span data-ttu-id="d722b-102">伺服器的 Database 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="d722b-102">Database Element for Server (DTA)</span></span>
  <span data-ttu-id="d722b-103">指定特定伺服器中需要微調的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d722b-103">Specifies the database you want to tune on a specific server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d722b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d722b-104">Syntax</span></span>  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="d722b-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="d722b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="d722b-106">特性</span><span class="sxs-lookup"><span data-stu-id="d722b-106">Characteristic</span></span>|<span data-ttu-id="d722b-107">描述</span><span class="sxs-lookup"><span data-stu-id="d722b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d722b-108">資料類型和長度</span><span class="sxs-lookup"><span data-stu-id="d722b-108">Data type and length</span></span>|<span data-ttu-id="d722b-109">無。</span><span class="sxs-lookup"><span data-stu-id="d722b-109">None.</span></span>|  
|<span data-ttu-id="d722b-110">預設值</span><span class="sxs-lookup"><span data-stu-id="d722b-110">Default value</span></span>|<span data-ttu-id="d722b-111">無。</span><span class="sxs-lookup"><span data-stu-id="d722b-111">None.</span></span>|  
|<span data-ttu-id="d722b-112">出現次數</span><span class="sxs-lookup"><span data-stu-id="d722b-112">Occurrence</span></span>|<span data-ttu-id="d722b-113">每個 `Server` 元素需要這個元素一或多次。</span><span class="sxs-lookup"><span data-stu-id="d722b-113">Required one or more times per `Server` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d722b-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="d722b-114">Element Relationships</span></span>  
  
|<span data-ttu-id="d722b-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="d722b-115">Relationship</span></span>|<span data-ttu-id="d722b-116">元素</span><span class="sxs-lookup"><span data-stu-id="d722b-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d722b-117">父元素</span><span class="sxs-lookup"><span data-stu-id="d722b-117">Parent element</span></span>|[<span data-ttu-id="d722b-118">Server 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d722b-118">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)|  
|<span data-ttu-id="d722b-119">子元素</span><span class="sxs-lookup"><span data-stu-id="d722b-119">Child elements</span></span>|[<span data-ttu-id="d722b-120">資料庫的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d722b-120">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="d722b-121">資料庫的 Schema 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d722b-121">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="d722b-122">備註</span><span class="sxs-lookup"><span data-stu-id="d722b-122">Remarks</span></span>  
 <span data-ttu-id="d722b-123">在 Database Engine Tuning Advisor XML 結構描述中，這個元素的名稱為 **DatabaseDetailsTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="d722b-123">This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="d722b-124">請勿混淆這個 `Database` 元素與根父系是 `Configuration` 元素的元素。</span><span class="sxs-lookup"><span data-stu-id="d722b-124">Do not confuse this `Database` element with the one whose root parent is the `Configuration` element.</span></span> <span data-ttu-id="d722b-125">如需詳細資訊，請參閱[組態的 Database 元素 &#40;DTA&#41;](database-element-for-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="d722b-125">For more information, see [Database Element for Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d722b-126">範例</span><span class="sxs-lookup"><span data-stu-id="d722b-126">Example</span></span>  
 <span data-ttu-id="d722b-127">如需元素的使用範例 `Database` ，請參閱[Server 元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="d722b-127">For a usage example of the `Database` element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d722b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d722b-128">See Also</span></span>  
 [<span data-ttu-id="d722b-129">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="d722b-129">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
