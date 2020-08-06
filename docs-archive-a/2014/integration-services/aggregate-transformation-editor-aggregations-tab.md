---
title: 匯總轉換編輯器 (匯總] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.aggregations.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30cafb68a69a061fe4b79e832f356b82926c9761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593529"
---
# <a name="aggregate-transformation-editor-aggregations-tab"></a><span data-ttu-id="93f23-102">彙總轉換編輯器 (彙總索引標籤)</span><span class="sxs-lookup"><span data-stu-id="93f23-102">Aggregate Transformation Editor (Aggregations Tab)</span></span>
  <span data-ttu-id="93f23-103">使用 [彙總轉換編輯器]\*\*\*\* 對話方塊的 [彙總]\*\*\*\* 索引標籤，即可指定彙總的資料行與彙總屬性。</span><span class="sxs-lookup"><span data-stu-id="93f23-103">Use the **Aggregations** tab of the **Aggregate Transformation Editor** dialog box to specify columns for aggregation and aggregation properties.</span></span> <span data-ttu-id="93f23-104">您可以套用多個彙總。</span><span class="sxs-lookup"><span data-stu-id="93f23-104">You can apply multiple aggregations.</span></span> <span data-ttu-id="93f23-105">此轉換不會產生錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="93f23-105">This transformation does not generate an error output.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93f23-106">索引鍵計數、索引鍵小數位數、相異索引鍵計數和相異索引鍵小數位數的選項，若是指定在 [進階]\*\*\*\* 索引標籤上，就會套用至元件層級；若是指定在 [彙總]\*\*\*\* 索引標籤的進階畫面上，則會套用至輸出層級；若是指定在 [彙總]\*\*\*\* 索引標籤底端的資料行清單中，則會套用至資料行層級。</span><span class="sxs-lookup"><span data-stu-id="93f23-106">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="93f23-107">在彙總轉換中， **[索引鍵]** 和 **[索引鍵小數位數]** 會參考預期要從 **[群組依據]** 作業產生的群組數。</span><span class="sxs-lookup"><span data-stu-id="93f23-107">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="93f23-108">**[計算相異索引鍵]** 和 **[計算相異小數位數]** 會參考預期要從 **[相異計數]** 作業產生的相異值數目。</span><span class="sxs-lookup"><span data-stu-id="93f23-108">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="93f23-109">若要了解有關彙總轉換的詳細資訊，請參閱＜ [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="93f23-109">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="93f23-110">選項</span><span class="sxs-lookup"><span data-stu-id="93f23-110">Options</span></span>  
 <span data-ttu-id="93f23-111">**進階 / 基本**</span><span class="sxs-lookup"><span data-stu-id="93f23-111">**Advanced / Basic**</span></span>  
 <span data-ttu-id="93f23-112">顯示或隱藏設定多個輸出之多個彙總的選項。</span><span class="sxs-lookup"><span data-stu-id="93f23-112">Display or hide options to configure multiple aggregations for multiple outputs.</span></span> <span data-ttu-id="93f23-113">依預設，會隱藏 [進階] 選項。</span><span class="sxs-lookup"><span data-stu-id="93f23-113">By default, the Advanced options are hidden.</span></span>  
  
 <span data-ttu-id="93f23-114">**彙總名稱**</span><span class="sxs-lookup"><span data-stu-id="93f23-114">**Aggregation Name**</span></span>  
 <span data-ttu-id="93f23-115">在 [進階] 顯示中，輸入彙總的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="93f23-115">In the Advanced display, type a friendly name for the aggregation.</span></span>  
  
 <span data-ttu-id="93f23-116">**群組依據資料行**</span><span class="sxs-lookup"><span data-stu-id="93f23-116">**Group By Columns**</span></span>  
 <span data-ttu-id="93f23-117">在 [進階] 顯示中，使用 [可用的輸入資料行]\*\*\*\* 清單選取要群組的資料行，如下所述。</span><span class="sxs-lookup"><span data-stu-id="93f23-117">In the Advanced display, select columns for grouping by using the **Available Input Columns** list as described below.</span></span>  
  
 <span data-ttu-id="93f23-118">**索引鍵小數位數**</span><span class="sxs-lookup"><span data-stu-id="93f23-118">**Key Scale**</span></span>  
 <span data-ttu-id="93f23-119">在 [進階] 顯示中，選擇性地指定彙總可以寫入的大約索引鍵數目。</span><span class="sxs-lookup"><span data-stu-id="93f23-119">In the Advanced display, optionally specify the approximate number of keys that the aggregation can write.</span></span> <span data-ttu-id="93f23-120">根據預設，此選項的值為 **[未指定]**。</span><span class="sxs-lookup"><span data-stu-id="93f23-120">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="93f23-121">如果 [索引鍵小數位數]\*\*\*\* 和 [索引鍵]\*\*\*\* 屬性都有設定，會優先使用 [索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="93f23-121">If both the **Key Scale** and **Keys** properties are set, the value of **Keys** takes precedence.</span></span>  
  
|<span data-ttu-id="93f23-122">值</span><span class="sxs-lookup"><span data-stu-id="93f23-122">Value</span></span>|<span data-ttu-id="93f23-123">描述</span><span class="sxs-lookup"><span data-stu-id="93f23-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93f23-124">[未指定]</span><span class="sxs-lookup"><span data-stu-id="93f23-124">Unspecified</span></span>|<span data-ttu-id="93f23-125">不使用 [索引鍵小數位數] 屬性。</span><span class="sxs-lookup"><span data-stu-id="93f23-125">The Key Scale property is not used.</span></span>|  
|<span data-ttu-id="93f23-126">低</span><span class="sxs-lookup"><span data-stu-id="93f23-126">Low</span></span>|<span data-ttu-id="93f23-127">彙總可寫入大約 500,000 個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93f23-127">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="93f23-128">中</span><span class="sxs-lookup"><span data-stu-id="93f23-128">Medium</span></span>|<span data-ttu-id="93f23-129">彙總可寫入大約 5,000,000 個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93f23-129">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="93f23-130">高</span><span class="sxs-lookup"><span data-stu-id="93f23-130">High</span></span>|<span data-ttu-id="93f23-131">彙總可寫入超過 25,000,000 個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93f23-131">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="93f23-132">**[索引鍵]**</span><span class="sxs-lookup"><span data-stu-id="93f23-132">**Keys**</span></span>  
 <span data-ttu-id="93f23-133">在 [進階] 顯示中，選擇性地指定彙總可以寫入的確切索引鍵數目。</span><span class="sxs-lookup"><span data-stu-id="93f23-133">In the Advanced display, optionally specify the exact number of keys that the aggregation can write.</span></span> <span data-ttu-id="93f23-134">如果 [索引鍵小數位數]\*\*\*\* 和 [索引鍵]\*\*\*\* 都有指定，會優先使用 [索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="93f23-134">If both **Key Scale** and **Keys** are specified, **Keys** takes precedence.</span></span>  
  
 <span data-ttu-id="93f23-135">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="93f23-135">**Available Input Columns**</span></span>  
 <span data-ttu-id="93f23-136">使用此資料表中的核取方塊，從可用的輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="93f23-136">Select from the list of available input columns by using the check boxes in this table.</span></span>  
  
 <span data-ttu-id="93f23-137">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="93f23-137">**Input Column**</span></span>  
 <span data-ttu-id="93f23-138">從可用的輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="93f23-138">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="93f23-139">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="93f23-139">**Output Alias**</span></span>  
 <span data-ttu-id="93f23-140">輸入每個資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="93f23-140">Type an alias for each column.</span></span> <span data-ttu-id="93f23-141">預設是輸入資料行的名稱；但是，您可以選擇任何唯一的、描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="93f23-141">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="93f23-142">**作業**</span><span class="sxs-lookup"><span data-stu-id="93f23-142">**Operation**</span></span>  
 <span data-ttu-id="93f23-143">使用下表作為指南，從可用的作業清單中選擇。</span><span class="sxs-lookup"><span data-stu-id="93f23-143">Choose from the list of available operations, using the following table as a guide.</span></span>  
  
|<span data-ttu-id="93f23-144">作業</span><span class="sxs-lookup"><span data-stu-id="93f23-144">Operation</span></span>|<span data-ttu-id="93f23-145">描述</span><span class="sxs-lookup"><span data-stu-id="93f23-145">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93f23-146">**GroupBy**</span><span class="sxs-lookup"><span data-stu-id="93f23-146">**GroupBy**</span></span>|<span data-ttu-id="93f23-147">將資料集分割成群組。</span><span class="sxs-lookup"><span data-stu-id="93f23-147">Divides datasets into groups.</span></span> <span data-ttu-id="93f23-148">具有任何資料類型的資料行可用於分組。</span><span class="sxs-lookup"><span data-stu-id="93f23-148">Columns with any data type can be used for grouping.</span></span> <span data-ttu-id="93f23-149">如需詳細資訊，請參閱 GROUP BY。</span><span class="sxs-lookup"><span data-stu-id="93f23-149">For more information, see GROUP BY.</span></span>|  
|<span data-ttu-id="93f23-150">**要求**</span><span class="sxs-lookup"><span data-stu-id="93f23-150">**Sum**</span></span>|<span data-ttu-id="93f23-151">加總資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="93f23-151">Sums the values in a column.</span></span> <span data-ttu-id="93f23-152">只能加總具有數值資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="93f23-152">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="93f23-153">如需詳細資訊，請參閱 SUM。</span><span class="sxs-lookup"><span data-stu-id="93f23-153">For more information, see SUM.</span></span>|  
|<span data-ttu-id="93f23-154">**Average**</span><span class="sxs-lookup"><span data-stu-id="93f23-154">**Average**</span></span>|<span data-ttu-id="93f23-155">傳回資料行中資料行值的平均。</span><span class="sxs-lookup"><span data-stu-id="93f23-155">Returns the average of the column values in a column.</span></span> <span data-ttu-id="93f23-156">只能平均具有數值資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="93f23-156">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="93f23-157">如需詳細資訊，請參閱 AVG。</span><span class="sxs-lookup"><span data-stu-id="93f23-157">For more information, see AVG.</span></span>|  
|<span data-ttu-id="93f23-158">**Count**</span><span class="sxs-lookup"><span data-stu-id="93f23-158">**Count**</span></span>|<span data-ttu-id="93f23-159">傳回群組中的項目數。</span><span class="sxs-lookup"><span data-stu-id="93f23-159">Returns the number of items in a group.</span></span> <span data-ttu-id="93f23-160">如需詳細資訊，請參閱 COUNT。</span><span class="sxs-lookup"><span data-stu-id="93f23-160">For more information, see COUNT.</span></span>|  
|<span data-ttu-id="93f23-161">**CountDistinct**</span><span class="sxs-lookup"><span data-stu-id="93f23-161">**CountDistinct**</span></span>|<span data-ttu-id="93f23-162">傳回群組中唯一非 Null 值的數目。</span><span class="sxs-lookup"><span data-stu-id="93f23-162">Returns the number of unique nonnull values in a group.</span></span> <span data-ttu-id="93f23-163">如需詳細資訊，請參閱 COUNT 和 Distinct。</span><span class="sxs-lookup"><span data-stu-id="93f23-163">For more information, see COUNT and Distinct.</span></span>|  
|<span data-ttu-id="93f23-164">**最低**</span><span class="sxs-lookup"><span data-stu-id="93f23-164">**Minimum**</span></span>|<span data-ttu-id="93f23-165">傳回群組中的最小值。</span><span class="sxs-lookup"><span data-stu-id="93f23-165">Returns the minimum value in a group.</span></span> <span data-ttu-id="93f23-166">限制為數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="93f23-166">Restricted to numeric data types.</span></span>|  
|<span data-ttu-id="93f23-167">**最大值**</span><span class="sxs-lookup"><span data-stu-id="93f23-167">**Maximum**</span></span>|<span data-ttu-id="93f23-168">傳回群組中的最大值。</span><span class="sxs-lookup"><span data-stu-id="93f23-168">Returns the maximum value in a group.</span></span> <span data-ttu-id="93f23-169">限制為數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="93f23-169">Restricted to numeric data types.</span></span>|  
  
 <span data-ttu-id="93f23-170">**比較旗標**</span><span class="sxs-lookup"><span data-stu-id="93f23-170">**Comparison Flags**</span></span>  
 <span data-ttu-id="93f23-171">如果您選擇 [群組依據]\*\*\*\*，請使用核取方塊來控制轉換執行比較的方式。</span><span class="sxs-lookup"><span data-stu-id="93f23-171">If you choose **Group By**, use the check boxes to control how the transformation performs the comparison.</span></span> <span data-ttu-id="93f23-172">如需字串比較選項的資訊，請參閱 [比較字串資料](data-flow/comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="93f23-172">For information on the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="93f23-173">**計數相異小數值**</span><span class="sxs-lookup"><span data-stu-id="93f23-173">**Count Distinct Scale**</span></span>  
 <span data-ttu-id="93f23-174">可選擇性地指定彙總可寫入之相異值的近似數目。</span><span class="sxs-lookup"><span data-stu-id="93f23-174">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="93f23-175">根據預設，此選項的值為 **[未指定]**。</span><span class="sxs-lookup"><span data-stu-id="93f23-175">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="93f23-176">如果同時 `CountDistinctScale` 指定了和**CountDistinctKeys** ， **CountDistinctKeys**會優先使用。</span><span class="sxs-lookup"><span data-stu-id="93f23-176">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
|<span data-ttu-id="93f23-177">值</span><span class="sxs-lookup"><span data-stu-id="93f23-177">Value</span></span>|<span data-ttu-id="93f23-178">描述</span><span class="sxs-lookup"><span data-stu-id="93f23-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93f23-179">[未指定]</span><span class="sxs-lookup"><span data-stu-id="93f23-179">Unspecified</span></span>|<span data-ttu-id="93f23-180">不使用 `CountDistinctScale` 屬性。</span><span class="sxs-lookup"><span data-stu-id="93f23-180">The `CountDistinctScale` property is not used.</span></span>|  
|<span data-ttu-id="93f23-181">低</span><span class="sxs-lookup"><span data-stu-id="93f23-181">Low</span></span>|<span data-ttu-id="93f23-182">彙總可寫入大約 500,000 個相異值。</span><span class="sxs-lookup"><span data-stu-id="93f23-182">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="93f23-183">中</span><span class="sxs-lookup"><span data-stu-id="93f23-183">Medium</span></span>|<span data-ttu-id="93f23-184">彙總可寫入大約 5,000,000 個相異值。</span><span class="sxs-lookup"><span data-stu-id="93f23-184">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="93f23-185">高</span><span class="sxs-lookup"><span data-stu-id="93f23-185">High</span></span>|<span data-ttu-id="93f23-186">彙總可寫入超過 25,000,000 個相異值。</span><span class="sxs-lookup"><span data-stu-id="93f23-186">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="93f23-187">**計算相異索引鍵**</span><span class="sxs-lookup"><span data-stu-id="93f23-187">**Count Distinct Keys**</span></span>  
 <span data-ttu-id="93f23-188">可選擇性地指定彙總可寫入之相異值的確實數目。</span><span class="sxs-lookup"><span data-stu-id="93f23-188">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="93f23-189">如果同時 `CountDistinctScale` 指定了和**CountDistinctKeys** ， **CountDistinctKeys**會優先使用。</span><span class="sxs-lookup"><span data-stu-id="93f23-189">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f23-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93f23-190">See Also</span></span>  
 <span data-ttu-id="93f23-191">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="93f23-191">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="93f23-192">[匯總轉換編輯器 &#40;[Advanced] 索引標籤&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="93f23-192">[Aggregate Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="93f23-193">使用彙總轉換來彙總資料集中的值</span><span class="sxs-lookup"><span data-stu-id="93f23-193">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
