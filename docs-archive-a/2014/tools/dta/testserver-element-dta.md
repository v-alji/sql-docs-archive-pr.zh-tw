---
title: " (DTA) 的 TestServer 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TestServer element
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d1f1fadf76a43caca262652254e8a778602183c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704578"
---
# <a name="testserver-element-dta"></a><span data-ttu-id="3ab14-102">TestServer 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="3ab14-102">TestServer Element (DTA)</span></span>
  <span data-ttu-id="3ab14-103">指定微調實際伺服器時所用的測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="3ab14-103">Specifies the test server to use when tuning a production server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab14-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ab14-104">Syntax</span></span>  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="3ab14-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="3ab14-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="3ab14-106">特性</span><span class="sxs-lookup"><span data-stu-id="3ab14-106">Characteristic</span></span>|<span data-ttu-id="3ab14-107">描述</span><span class="sxs-lookup"><span data-stu-id="3ab14-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="3ab14-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="3ab14-108">**Data type and length**</span></span>|<span data-ttu-id="3ab14-109">**string**，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="3ab14-109">**string**, unlimited length.</span></span>|  
|<span data-ttu-id="3ab14-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="3ab14-110">**Default value**</span></span>|<span data-ttu-id="3ab14-111">無。</span><span class="sxs-lookup"><span data-stu-id="3ab14-111">None.</span></span>|  
|<span data-ttu-id="3ab14-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="3ab14-112">**Occurrence**</span></span>|<span data-ttu-id="3ab14-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3ab14-113">Optional.</span></span> <span data-ttu-id="3ab14-114">每個 `TuningOptions` 元素可以使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="3ab14-114">Can use once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="3ab14-115">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="3ab14-115">Element Relationships</span></span>  
  
|<span data-ttu-id="3ab14-116">關聯性</span><span class="sxs-lookup"><span data-stu-id="3ab14-116">Relationship</span></span>|<span data-ttu-id="3ab14-117">元素</span><span class="sxs-lookup"><span data-stu-id="3ab14-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="3ab14-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="3ab14-118">**Parent element**</span></span>|[<span data-ttu-id="3ab14-119">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="3ab14-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="3ab14-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="3ab14-120">**Child elements**</span></span>|<span data-ttu-id="3ab14-121">無。</span><span class="sxs-lookup"><span data-stu-id="3ab14-121">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3ab14-122">範例</span><span class="sxs-lookup"><span data-stu-id="3ab14-122">Example</span></span>  
 <span data-ttu-id="3ab14-123">如需此元素的使用範例，請參閱 [降低生產伺服器的微調負載](../../relational-databases/performance/reduce-the-production-server-tuning-load.md)。</span><span class="sxs-lookup"><span data-stu-id="3ab14-123">For a usage example of this element, see [Reduce the Production Server Tuning Load](../../relational-databases/performance/reduce-the-production-server-tuning-load.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab14-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ab14-124">See Also</span></span>  
 [<span data-ttu-id="3ab14-125">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="3ab14-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
