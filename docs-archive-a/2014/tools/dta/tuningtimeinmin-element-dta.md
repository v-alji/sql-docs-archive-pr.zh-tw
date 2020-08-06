---
title: " (DTA) 的 TuningTimeInMin 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningTimeInMin element
ms.assetid: 4973d9ac-20fd-4ac3-bc9f-5d60e39fdb7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dae3fe4e9ac3126f43ec017c34d2bc548fda6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704554"
---
# <a name="tuningtimeinmin-element-dta"></a><span data-ttu-id="0b6cf-102">TuningTimeInMin 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="0b6cf-102">TuningTimeInMin Element (DTA)</span></span>
  <span data-ttu-id="0b6cf-103">指定微調工作階段的最長時間 (分鐘)。</span><span class="sxs-lookup"><span data-stu-id="0b6cf-103">Specifies the maximum length of a tuning session in minutes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b6cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b6cf-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <TuningTimeInMin>...</TuningTimeInMin>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="0b6cf-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="0b6cf-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="0b6cf-106">特性</span><span class="sxs-lookup"><span data-stu-id="0b6cf-106">Characteristic</span></span>|<span data-ttu-id="0b6cf-107">描述</span><span class="sxs-lookup"><span data-stu-id="0b6cf-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0b6cf-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="0b6cf-108">**Data type and length**</span></span>|<span data-ttu-id="0b6cf-109">`unsignedInt`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="0b6cf-109">`unsignedInt`, unlimited length.</span></span>|  
|<span data-ttu-id="0b6cf-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="0b6cf-110">**Default value**</span></span>|<span data-ttu-id="0b6cf-111">480 分鐘 (8 小時)。</span><span class="sxs-lookup"><span data-stu-id="0b6cf-111">480 minutes (8 hours).</span></span>|  
|<span data-ttu-id="0b6cf-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="0b6cf-112">**Occurrence**</span></span>|<span data-ttu-id="0b6cf-113">除非指定了 `NumberOfEvents` 元素值，否則，需要這個元素。</span><span class="sxs-lookup"><span data-stu-id="0b6cf-113">Required unless a value has been specified for the `NumberOfEvents` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="0b6cf-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="0b6cf-114">Element Relationships</span></span>  
  
|<span data-ttu-id="0b6cf-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="0b6cf-115">Relationship</span></span>|<span data-ttu-id="0b6cf-116">元素</span><span class="sxs-lookup"><span data-stu-id="0b6cf-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="0b6cf-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="0b6cf-117">**Parent element**</span></span>|[<span data-ttu-id="0b6cf-118">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0b6cf-118">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="0b6cf-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="0b6cf-119">**Child elements**</span></span>|<span data-ttu-id="0b6cf-120">None</span><span class="sxs-lookup"><span data-stu-id="0b6cf-120">None</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b6cf-121">範例</span><span class="sxs-lookup"><span data-stu-id="0b6cf-121">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="0b6cf-122">描述</span><span class="sxs-lookup"><span data-stu-id="0b6cf-122">Description</span></span>  
 <span data-ttu-id="0b6cf-123">下列程式碼範例顯示如何設定 12 小時作為最大微調時間：</span><span class="sxs-lookup"><span data-stu-id="0b6cf-123">The following code example shows how to set 12 hours as the maximum tuning time:</span></span>  
  
## <a name="code"></a><span data-ttu-id="0b6cf-124">程式碼</span><span class="sxs-lookup"><span data-stu-id="0b6cf-124">Code</span></span>  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <TuningTimeInMin>720</TuningTimeInMin>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b6cf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b6cf-125">See Also</span></span>  
 [<span data-ttu-id="0b6cf-126">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="0b6cf-126">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
