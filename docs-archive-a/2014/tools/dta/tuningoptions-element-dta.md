---
title: " (DTA) 的 TuningOptions 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fab1c55c9d036424142b2692e8335ea65c22340
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704557"
---
# <a name="tuningoptions-element-dta"></a><span data-ttu-id="fd935-102">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="fd935-102">TuningOptions Element (DTA)</span></span>
  <span data-ttu-id="fd935-103">包含特定微調工作階段的微調選項。</span><span class="sxs-lookup"><span data-stu-id="fd935-103">Contains the tuning options for a specific tuning session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd935-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd935-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="fd935-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="fd935-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="fd935-106">特性</span><span class="sxs-lookup"><span data-stu-id="fd935-106">Characteristic</span></span>|<span data-ttu-id="fd935-107">描述</span><span class="sxs-lookup"><span data-stu-id="fd935-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="fd935-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="fd935-108">**Data type and length**</span></span>|<span data-ttu-id="fd935-109">無。</span><span class="sxs-lookup"><span data-stu-id="fd935-109">None.</span></span>|  
|<span data-ttu-id="fd935-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="fd935-110">**Default value**</span></span>|<span data-ttu-id="fd935-111">無。</span><span class="sxs-lookup"><span data-stu-id="fd935-111">None.</span></span>|  
|<span data-ttu-id="fd935-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="fd935-112">**Occurrence**</span></span>|<span data-ttu-id="fd935-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="fd935-113">Optional.</span></span> <span data-ttu-id="fd935-114">如果使用這個元素的話，每個 `DTAInput` 元素只能使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="fd935-114">If used, can only be used once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="fd935-115">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="fd935-115">Element Relationships</span></span>  
  
|<span data-ttu-id="fd935-116">關聯性</span><span class="sxs-lookup"><span data-stu-id="fd935-116">Relationship</span></span>|<span data-ttu-id="fd935-117">元素</span><span class="sxs-lookup"><span data-stu-id="fd935-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="fd935-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="fd935-118">**Parent element**</span></span>|[<span data-ttu-id="fd935-119">DTAInput 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-119">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="fd935-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="fd935-120">**Child elements**</span></span>|<span data-ttu-id="fd935-121">`ReportSet` 元素。</span><span class="sxs-lookup"><span data-stu-id="fd935-121">`ReportSet` element.</span></span> <span data-ttu-id="fd935-122">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞。</span><span class="sxs-lookup"><span data-stu-id="fd935-122">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="fd935-123">`TuningLogTable` 元素。</span><span class="sxs-lookup"><span data-stu-id="fd935-123">`TuningLogTable` element.</span></span> <span data-ttu-id="fd935-124">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞。</span><span class="sxs-lookup"><span data-stu-id="fd935-124">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="fd935-125">`NumberOfEvents` 元素。</span><span class="sxs-lookup"><span data-stu-id="fd935-125">`NumberOfEvents` element.</span></span> <span data-ttu-id="fd935-126">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞。</span><span class="sxs-lookup"><span data-stu-id="fd935-126">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> [<span data-ttu-id="fd935-127">TuningTimeInMin 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-127">TuningTimeInMin Element &#40;DTA&#41;</span></span>](tuningtimeinmin-element-dta.md)<br /><br /> [<span data-ttu-id="fd935-128">StorageBoundInMB 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-128">StorageBoundInMB Element &#40;DTA&#41;</span></span>](storageboundinmb-element-dta.md)<br /><br /> <span data-ttu-id="fd935-129">`MaxKeyColumnsInIndex` 元素。</span><span class="sxs-lookup"><span data-stu-id="fd935-129">`MaxKeyColumnsInIndex` element.</span></span> <span data-ttu-id="fd935-130">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞。</span><span class="sxs-lookup"><span data-stu-id="fd935-130">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="fd935-131">`MaxColumnsInIndex` 元素。</span><span class="sxs-lookup"><span data-stu-id="fd935-131">`MaxColumnsInIndex` element.</span></span> <span data-ttu-id="fd935-132">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞。</span><span class="sxs-lookup"><span data-stu-id="fd935-132">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="fd935-133">`MinPercentageImprovement` 元素。</span><span class="sxs-lookup"><span data-stu-id="fd935-133">`MinPercentageImprovement` element.</span></span> <span data-ttu-id="fd935-134">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞</span><span class="sxs-lookup"><span data-stu-id="fd935-134">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100)</span></span><br /><br /> [<span data-ttu-id="fd935-135">TestServer 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-135">TestServer Element &#40;DTA&#41;</span></span>](server-element-dta.md)<br /><br /> [<span data-ttu-id="fd935-136">FeatureSet 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-136">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)<br /><br /> [<span data-ttu-id="fd935-137">Partitioning 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-137">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)<br /><br /> [<span data-ttu-id="fd935-138">DropOnlyMode 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-138">DropOnlyMode Element &#40;DTA&#41;</span></span>](droponlymode-element-dta.md)<br /><br /> [<span data-ttu-id="fd935-139">KeepExisting 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-139">KeepExisting Element &#40;DTA&#41;</span></span>](keepexisting-element-dta.md)<br /><br /> [<span data-ttu-id="fd935-140">OnlineIndexOperation 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-140">OnlineIndexOperation Element &#40;DTA&#41;</span></span>](onlineindexoperation-element-dta.md)<br /><br /> [<span data-ttu-id="fd935-141">DatabaseToConnect 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-141">DatabaseToConnect Element &#40;DTA&#41;</span></span>](databasetoconnect-element-dta.md)<br /><br /> <span data-ttu-id="fd935-142">`IgnoreConstantsInWorkload` 元素。</span><span class="sxs-lookup"><span data-stu-id="fd935-142">`IgnoreConstantsInWorkload` element.</span></span> <span data-ttu-id="fd935-143">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞。</span><span class="sxs-lookup"><span data-stu-id="fd935-143">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="fd935-144">`RetainShellDB` 元素。</span><span class="sxs-lookup"><span data-stu-id="fd935-144">`RetainShellDB` element.</span></span> <span data-ttu-id="fd935-145">如需詳細資訊，請參閱＜ [Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?linkid=43100)＞。</span><span class="sxs-lookup"><span data-stu-id="fd935-145">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fd935-146">範例</span><span class="sxs-lookup"><span data-stu-id="fd935-146">Example</span></span>  
 <span data-ttu-id="fd935-147">如需元素的範例 `TuningOptions` ，請參閱[&#40;DTA&#41;的 XML 輸入檔範例](xml-input-file-samples-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="fd935-147">For examples of the `TuningOptions` element, see the [XML Input File Samples &#40;DTA&#41;](xml-input-file-samples-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd935-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd935-148">See Also</span></span>  
 [<span data-ttu-id="fd935-149">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="fd935-149">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
