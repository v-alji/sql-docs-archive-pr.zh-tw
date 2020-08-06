---
title: " (DTA) 的 DTAInput 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7d2ff380a4ae1595e50aae472efc5fb4ac72efe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687398"
---
# <a name="dtainput-element-dta"></a><span data-ttu-id="e988d-102">DTAInput 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e988d-102">DTAInput Element (DTA)</span></span>
  <span data-ttu-id="e988d-103">包含 Database Engine Tuning Advisor 的 XML 輸入定義。</span><span class="sxs-lookup"><span data-stu-id="e988d-103">Contains the definition of XML input for Database Engine Tuning Advisor.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e988d-104">語法</span><span class="sxs-lookup"><span data-stu-id="e988d-104">Syntax</span></span>  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="e988d-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="e988d-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="e988d-106">特性</span><span class="sxs-lookup"><span data-stu-id="e988d-106">Characteristics</span></span>|<span data-ttu-id="e988d-107">描述</span><span class="sxs-lookup"><span data-stu-id="e988d-107">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="e988d-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="e988d-108">**Data type and length**</span></span>|<span data-ttu-id="e988d-109">無。</span><span class="sxs-lookup"><span data-stu-id="e988d-109">None.</span></span>|  
|<span data-ttu-id="e988d-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="e988d-110">**Default value**</span></span>|<span data-ttu-id="e988d-111">無。</span><span class="sxs-lookup"><span data-stu-id="e988d-111">None.</span></span>|  
|<span data-ttu-id="e988d-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="e988d-112">**Occurrence**</span></span>|<span data-ttu-id="e988d-113">每個 **DTAXML** 元素可以選擇性地使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="e988d-113">Optional once per **DTAXML** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e988d-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="e988d-114">Element Relationships</span></span>  
  
|<span data-ttu-id="e988d-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="e988d-115">Relationship</span></span>|<span data-ttu-id="e988d-116">元素</span><span class="sxs-lookup"><span data-stu-id="e988d-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e988d-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="e988d-117">**Parent element**</span></span>|[<span data-ttu-id="e988d-118">DTAXML 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e988d-118">DTAXML Element &#40;DTA&#41;</span></span>](dtaxml-element-dta.md)|  
|<span data-ttu-id="e988d-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="e988d-119">**Child elements**</span></span>|[<span data-ttu-id="e988d-120">Server 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e988d-120">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)<br /><br /> [<span data-ttu-id="e988d-121">Workload 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e988d-121">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)<br /><br /> [<span data-ttu-id="e988d-122">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e988d-122">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)<br /><br /> [<span data-ttu-id="e988d-123">Configuration 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e988d-123">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="e988d-124">備註</span><span class="sxs-lookup"><span data-stu-id="e988d-124">Remarks</span></span>  
 <span data-ttu-id="e988d-125">這個元素是 Database Engine Tuning Advisor 輸入結構描述階層的根。</span><span class="sxs-lookup"><span data-stu-id="e988d-125">This element is the root of the Database Engine Tuning Advisor input schema hierarchy.</span></span> <span data-ttu-id="e988d-126">Database Engine Tuning Advisor 的輸入可以是指定資料庫需要微調之伺服器、工作負載、微調選項或使用者指定組態的引數。</span><span class="sxs-lookup"><span data-stu-id="e988d-126">Input to Database Engine Tuning Advisor can be arguments that specify the servers whose databases you want to tune, workloads, tuning options, or a user-specified configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e988d-127">範例</span><span class="sxs-lookup"><span data-stu-id="e988d-127">Example</span></span>  
 <span data-ttu-id="e988d-128">如需 **DTAInput** 元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="e988d-128">For a usage example of the **DTAInput** element, see [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e988d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e988d-129">See Also</span></span>  
 [<span data-ttu-id="e988d-130">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="e988d-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
