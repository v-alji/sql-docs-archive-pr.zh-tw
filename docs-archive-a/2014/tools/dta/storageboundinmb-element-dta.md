---
title: " (DTA) 的 StorageBoundInMB 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea49b0af981b8f8d96efb087033d8f1466364c76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704585"
---
# <a name="storageboundinmb-element-dta"></a><span data-ttu-id="51fd0-102">StorageBoundInMB 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="51fd0-102">StorageBoundInMB Element (DTA)</span></span>
  <span data-ttu-id="51fd0-103">指定 Database Engine Tuning Advisor 微調建議 (索引和資料分割集) 所能取用的最大空間 (MB)。</span><span class="sxs-lookup"><span data-stu-id="51fd0-103">Specifies the maximum space in megabytes that can be consumed by the Database Engine Tuning Advisor tuning recommendation (index and partitioning set).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51fd0-104">語法</span><span class="sxs-lookup"><span data-stu-id="51fd0-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="51fd0-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="51fd0-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="51fd0-106">特性</span><span class="sxs-lookup"><span data-stu-id="51fd0-106">Characteristic</span></span>|<span data-ttu-id="51fd0-107">描述</span><span class="sxs-lookup"><span data-stu-id="51fd0-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="51fd0-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="51fd0-108">**Data type and length**</span></span>|<span data-ttu-id="51fd0-109">`unsignedInt`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="51fd0-109">`unsignedInt`, unlimited length.</span></span>|  
|<span data-ttu-id="51fd0-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="51fd0-110">**Default value**</span></span>|<span data-ttu-id="51fd0-111">無。</span><span class="sxs-lookup"><span data-stu-id="51fd0-111">None.</span></span>|  
|<span data-ttu-id="51fd0-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="51fd0-112">**Occurrence**</span></span>|<span data-ttu-id="51fd0-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="51fd0-113">Optional.</span></span> <span data-ttu-id="51fd0-114">`TuningOptions` 元素只能使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="51fd0-114">Can only be used once for the `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="51fd0-115">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="51fd0-115">Element Relationships</span></span>  
  
|<span data-ttu-id="51fd0-116">關聯性</span><span class="sxs-lookup"><span data-stu-id="51fd0-116">Relationship</span></span>|<span data-ttu-id="51fd0-117">元素</span><span class="sxs-lookup"><span data-stu-id="51fd0-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="51fd0-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="51fd0-118">**Parent element**</span></span>|[<span data-ttu-id="51fd0-119">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="51fd0-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="51fd0-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="51fd0-120">**Child elements**</span></span>|<span data-ttu-id="51fd0-121">None</span><span class="sxs-lookup"><span data-stu-id="51fd0-121">None</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51fd0-122">備註</span><span class="sxs-lookup"><span data-stu-id="51fd0-122">Remarks</span></span>  
 <span data-ttu-id="51fd0-123">微調多個資料庫時，所有資料庫的建議內容都考量了空間的計算。</span><span class="sxs-lookup"><span data-stu-id="51fd0-123">When multiple databases are tuned, recommendations for all databases are considered for the space calculation.</span></span> <span data-ttu-id="51fd0-124">依預設，Database Engine Tuning Advisor 會採用下列中較小的儲存體大小：</span><span class="sxs-lookup"><span data-stu-id="51fd0-124">By default, Database Engine Tuning Advisor assumes the smaller of the following storage sizes:</span></span>  
  
-   <span data-ttu-id="51fd0-125">目前的原始資料大小的三倍，其中包括各資料表的堆積和叢集索引的總大小。</span><span class="sxs-lookup"><span data-stu-id="51fd0-125">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables.</span></span>  
  
-   <span data-ttu-id="51fd0-126">所有相連硬碟的可用空間，加上原始資料大小。</span><span class="sxs-lookup"><span data-stu-id="51fd0-126">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="51fd0-127">預設儲存體大小不包括非叢集索引和索引檢視。</span><span class="sxs-lookup"><span data-stu-id="51fd0-127">The default storage size does not include nonclustered indexes and indexed views.</span></span>  
  
 <span data-ttu-id="51fd0-128">如果指定給 `StorageBoundInMB` 元素的值超出實際的磁碟大小，Database Engine Tuning Advisor 會傳回錯誤，但會繼續微調。</span><span class="sxs-lookup"><span data-stu-id="51fd0-128">If the value specified for the `StorageBoundInMB` element exceeds the actual disk space, Database Engine Tuning Advisor returns an error, but continues tuning.</span></span> <span data-ttu-id="51fd0-129">微調完成之後，如果您決定實作建議，您可以增加磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="51fd0-129">After tuning is complete, you can add disk space if you decide to implement the recommendation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51fd0-130">範例</span><span class="sxs-lookup"><span data-stu-id="51fd0-130">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="51fd0-131">描述</span><span class="sxs-lookup"><span data-stu-id="51fd0-131">Description</span></span>  
 <span data-ttu-id="51fd0-132">下列程式碼範例顯示如何將 1500 MB 的限制設為微調建議所能取用的最大磁碟空間：</span><span class="sxs-lookup"><span data-stu-id="51fd0-132">The following code example shows how to set a limit of 1500 megabytes as the maximum disk space that a tuning recommendation can consume:</span></span>  
  
## <a name="code"></a><span data-ttu-id="51fd0-133">程式碼</span><span class="sxs-lookup"><span data-stu-id="51fd0-133">Code</span></span>  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51fd0-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51fd0-134">See Also</span></span>  
 [<span data-ttu-id="51fd0-135">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="51fd0-135">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
