---
title: '[匯總轉換編輯器] ([Advanced] 索引標籤) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb3742a83f363f74004a5aac0eefc589ee2a5be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593532"
---
# <a name="aggregate-transformation-editor-advanced-tab"></a><span data-ttu-id="5f5fd-102">彙總轉換編輯器 (進階索引標籤)</span><span class="sxs-lookup"><span data-stu-id="5f5fd-102">Aggregate Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="5f5fd-103">使用 **[彙總轉換編輯器]** 對話方塊的 **[進階]** 索引標籤，即可設定元件屬性、指定彙總，以及設定輸入和輸出資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-103">Use the **Advanced** tab of the **Aggregate Transformation Editor** dialog box to set component properties, specify aggregations, and set properties of input and output columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f5fd-104">索引鍵計數、索引鍵小數位數、相異索引鍵計數和相異索引鍵小數位數的選項，若是指定在 [進階]\*\*\*\* 索引標籤上，就會套用至元件層級；若是指定在 [彙總]\*\*\*\* 索引標籤的進階畫面上，則會套用至輸出層級；若是指定在 [彙總]\*\*\*\* 索引標籤底端的資料行清單中，則會套用至資料行層級。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-104">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="5f5fd-105">在彙總轉換中， **[索引鍵]** 和 **[索引鍵小數位數]** 會參考預期要從 **[群組依據]** 作業產生的群組數。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-105">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="5f5fd-106">**[計算相異索引鍵]** 和 **[計算相異小數位數]** 會參考預期要從 **[相異計數]** 作業產生的相異值數目。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-106">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="5f5fd-107">若要了解有關彙總轉換的詳細資訊，請參閱＜ [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-107">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5f5fd-108">選項</span><span class="sxs-lookup"><span data-stu-id="5f5fd-108">Options</span></span>  
 <span data-ttu-id="5f5fd-109">**[索引鍵小數位數]**</span><span class="sxs-lookup"><span data-stu-id="5f5fd-109">**Keys scale**</span></span>  
 <span data-ttu-id="5f5fd-110">選擇性地指定彙總預期的近似索引鍵數目。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-110">Optionally specify the approximate number of keys that the aggregation expects.</span></span> <span data-ttu-id="5f5fd-111">轉換時會使用此資訊來最佳化初始快取大小。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-111">The transformation uses this information to optimize its initial cache size.</span></span> <span data-ttu-id="5f5fd-112">根據預設，此選項的值為 **[未指定]**。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-112">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="5f5fd-113">如果 **[索引鍵小數位數]** 和 **[索引鍵數目]** 都有指定，會優先使用 **[索引鍵數目]** 。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-113">If both **Keys scale** and **Number of keys** are specified, **Number of keys** takes precedence.</span></span>  
  
|<span data-ttu-id="5f5fd-114">值</span><span class="sxs-lookup"><span data-stu-id="5f5fd-114">Value</span></span>|<span data-ttu-id="5f5fd-115">描述</span><span class="sxs-lookup"><span data-stu-id="5f5fd-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5f5fd-116">[未指定]</span><span class="sxs-lookup"><span data-stu-id="5f5fd-116">Unspecified</span></span>|<span data-ttu-id="5f5fd-117">不使用 **[索引鍵小數位數]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-117">The **Keys scale** property is not used.</span></span>|  
|<span data-ttu-id="5f5fd-118">低</span><span class="sxs-lookup"><span data-stu-id="5f5fd-118">Low</span></span>|<span data-ttu-id="5f5fd-119">彙總可寫入大約 500,000 個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-119">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="5f5fd-120">中</span><span class="sxs-lookup"><span data-stu-id="5f5fd-120">Medium</span></span>|<span data-ttu-id="5f5fd-121">彙總可寫入大約 5,000,000 個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-121">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="5f5fd-122">高</span><span class="sxs-lookup"><span data-stu-id="5f5fd-122">High</span></span>|<span data-ttu-id="5f5fd-123">彙總可寫入超過 25,000,000 個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-123">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="5f5fd-124">**金鑰數目**</span><span class="sxs-lookup"><span data-stu-id="5f5fd-124">**Number of keys**</span></span>  
 <span data-ttu-id="5f5fd-125">選擇性地指定彙總預期的確實索引鍵數目。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-125">Optionally specify the exact number of keys that the aggregation expects.</span></span> <span data-ttu-id="5f5fd-126">轉換時會使用此資訊來最佳化初始快取大小。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-126">The transformation uses this information to optimize its initial cache size.</span></span> <span data-ttu-id="5f5fd-127">如果 **[索引鍵小數位數]** 和 **[索引鍵數目]** 都有指定，會優先使用 **[索引鍵數目]** 。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-127">If both **Keys scale** and **Number of keys** are specified, **Number of keys** takes precedence.</span></span>  
  
 <span data-ttu-id="5f5fd-128">**[計算相異小數位數]**</span><span class="sxs-lookup"><span data-stu-id="5f5fd-128">**Count distinct scale**</span></span>  
 <span data-ttu-id="5f5fd-129">可選擇性地指定彙總可寫入之相異值的近似數目。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-129">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="5f5fd-130">根據預設，此選項的值為 **[未指定]**。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-130">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="5f5fd-131">如果 **[計算相異小數位數]** 和 **[計算相異索引鍵]** 都有指定，會優先使用 **[計算相異索引鍵]** 。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-131">If both **Count distinct scale** and **Count distinct keys** are specified, **Count distinct keys** takes precedence.</span></span>  
  
|<span data-ttu-id="5f5fd-132">值</span><span class="sxs-lookup"><span data-stu-id="5f5fd-132">Value</span></span>|<span data-ttu-id="5f5fd-133">描述</span><span class="sxs-lookup"><span data-stu-id="5f5fd-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5f5fd-134">[未指定]</span><span class="sxs-lookup"><span data-stu-id="5f5fd-134">Unspecified</span></span>|<span data-ttu-id="5f5fd-135">不使用 CountDistinctScale 屬性。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-135">The CountDistinctScale property is not used.</span></span>|  
|<span data-ttu-id="5f5fd-136">低</span><span class="sxs-lookup"><span data-stu-id="5f5fd-136">Low</span></span>|<span data-ttu-id="5f5fd-137">彙總可寫入大約 500,000 個相異值。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-137">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="5f5fd-138">中</span><span class="sxs-lookup"><span data-stu-id="5f5fd-138">Medium</span></span>|<span data-ttu-id="5f5fd-139">彙總可寫入大約 5,000,000 個相異值。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-139">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="5f5fd-140">高</span><span class="sxs-lookup"><span data-stu-id="5f5fd-140">High</span></span>|<span data-ttu-id="5f5fd-141">彙總可寫入超過 25,000,000 個相異值。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-141">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="5f5fd-142">**[計算相異索引鍵]**</span><span class="sxs-lookup"><span data-stu-id="5f5fd-142">**Count distinct keys**</span></span>  
 <span data-ttu-id="5f5fd-143">可選擇性地指定彙總可寫入之相異值的確實數目。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-143">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="5f5fd-144">如果 **[計算相異小數位數]** 和 **[計算相異索引鍵]** 都有指定，會優先使用 **[計算相異索引鍵]** 。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-144">If both **Count distinct scale** and **Count distinct keys** are specified, **Count distinct keys** takes precedence.</span></span>  
  
 <span data-ttu-id="5f5fd-145">**自動擴充因數**</span><span class="sxs-lookup"><span data-stu-id="5f5fd-145">**Auto extend factor**</span></span>  
 <span data-ttu-id="5f5fd-146">使用介於 1 到 100 之間的值，指定記憶體於彙總期間可以擴充的百分比。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-146">Use a value between 1 and 100 to specify the percentage by which memory can be extended during the aggregation.</span></span> <span data-ttu-id="5f5fd-147">根據預設，此選項的值為 **25%**。</span><span class="sxs-lookup"><span data-stu-id="5f5fd-147">By default, the value of this option is **25%**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5fd-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f5fd-148">See Also</span></span>  
 <span data-ttu-id="5f5fd-149">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5f5fd-149">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="5f5fd-150">[匯總轉換編輯器 &#40;匯總] 索引標籤&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md) </span><span class="sxs-lookup"><span data-stu-id="5f5fd-150">[Aggregate Transformation Editor &#40;Aggregations Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md) </span></span>  
 [<span data-ttu-id="5f5fd-151">使用彙總轉換來彙總資料集中的值</span><span class="sxs-lookup"><span data-stu-id="5f5fd-151">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
