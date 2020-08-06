---
title: 彙總轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregatetrans.f1
helpviewer_keywords:
- IsBig property
- aggregate functions [Integration Services]
- Aggregate transformation [Integration Services]
- large data, SSIS transformations
ms.assetid: 2871cf2a-fbd3-41ba-807d-26ffff960e81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9e69d741ddd2bd14a31d7aa79a8c825641713523
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687070"
---
# <a name="aggregate-transformation"></a><span data-ttu-id="96785-102">彙總轉換</span><span class="sxs-lookup"><span data-stu-id="96785-102">Aggregate Transformation</span></span>
  <span data-ttu-id="96785-103">「彙總」轉換會將彙總函式 (例如 Average) 套用至資料行值，並將結果複製到轉換輸出。</span><span class="sxs-lookup"><span data-stu-id="96785-103">The Aggregate transformation applies aggregate functions, such as Average, to column values and copies the results to the transformation output.</span></span> <span data-ttu-id="96785-104">除了彙總函式外，該轉換還提供 GROUP BY 子句，讓您用來指定要彙總的群組。</span><span class="sxs-lookup"><span data-stu-id="96785-104">Besides aggregate functions, the transformation provides the GROUP BY clause, which you can use to specify groups to aggregate across.</span></span>  
  
## <a name="operations"></a><span data-ttu-id="96785-105">作業</span><span class="sxs-lookup"><span data-stu-id="96785-105">Operations</span></span>  
 <span data-ttu-id="96785-106">「彙總」轉換支援下列作業。</span><span class="sxs-lookup"><span data-stu-id="96785-106">The Aggregate transformation supports the following operations.</span></span>  
  
|<span data-ttu-id="96785-107">作業</span><span class="sxs-lookup"><span data-stu-id="96785-107">Operation</span></span>|<span data-ttu-id="96785-108">描述</span><span class="sxs-lookup"><span data-stu-id="96785-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96785-109">群組依據</span><span class="sxs-lookup"><span data-stu-id="96785-109">Group by</span></span>|<span data-ttu-id="96785-110">將資料集分割成群組。</span><span class="sxs-lookup"><span data-stu-id="96785-110">Divides datasets into groups.</span></span> <span data-ttu-id="96785-111">任何資料類型的資料行都可用於群組。</span><span class="sxs-lookup"><span data-stu-id="96785-111">Columns of any data type can be used for grouping.</span></span> <span data-ttu-id="96785-112">如需詳細資訊，請參閱 [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96785-112">For more information, see [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql).</span></span>|  
|<span data-ttu-id="96785-113">Sum</span><span class="sxs-lookup"><span data-stu-id="96785-113">Sum</span></span>|<span data-ttu-id="96785-114">加總資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="96785-114">Sums the values in a column.</span></span> <span data-ttu-id="96785-115">只能加總具有數值資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="96785-115">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="96785-116">如需詳細資訊，請參閱 [SUM &#40;Transact-SQL&#41;](/sql/t-sql/functions/sum-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96785-116">For more information, see [SUM &#40;Transact-SQL&#41;](/sql/t-sql/functions/sum-transact-sql).</span></span>|  
|<span data-ttu-id="96785-117">Average</span><span class="sxs-lookup"><span data-stu-id="96785-117">Average</span></span>|<span data-ttu-id="96785-118">傳回資料行中資料行值的平均。</span><span class="sxs-lookup"><span data-stu-id="96785-118">Returns the average of the column values in a column.</span></span> <span data-ttu-id="96785-119">只能平均具有數值資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="96785-119">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="96785-120">如需詳細資訊，請參閱 [AVG &#40;Transact-SQL&#41;](/sql/t-sql/functions/avg-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96785-120">For more information, see [AVG &#40;Transact-SQL&#41;](/sql/t-sql/functions/avg-transact-sql).</span></span>|  
|<span data-ttu-id="96785-121">Count</span><span class="sxs-lookup"><span data-stu-id="96785-121">Count</span></span>|<span data-ttu-id="96785-122">傳回群組中的項目數。</span><span class="sxs-lookup"><span data-stu-id="96785-122">Returns the number of items in a group.</span></span> <span data-ttu-id="96785-123">如需詳細資訊，請參閱 [COUNT &#40;Transact-SQL&#41;](/sql/t-sql/functions/count-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96785-123">For more information, see [COUNT &#40;Transact-SQL&#41;](/sql/t-sql/functions/count-transact-sql).</span></span>|  
|<span data-ttu-id="96785-124">計算相異</span><span class="sxs-lookup"><span data-stu-id="96785-124">Count distinct</span></span>|<span data-ttu-id="96785-125">傳回群組中唯一非 Null 值的數目。</span><span class="sxs-lookup"><span data-stu-id="96785-125">Returns the number of unique nonnull values in a group.</span></span>|  
|<span data-ttu-id="96785-126">最小值</span><span class="sxs-lookup"><span data-stu-id="96785-126">Minimum</span></span>|<span data-ttu-id="96785-127">傳回群組中的最小值。</span><span class="sxs-lookup"><span data-stu-id="96785-127">Returns the minimum value in a group.</span></span> <span data-ttu-id="96785-128">如需詳細資訊，請參閱 [MIN &#40;Transact-SQL&#41;](/sql/t-sql/functions/min-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96785-128">For more information, see [MIN &#40;Transact-SQL&#41;](/sql/t-sql/functions/min-transact-sql).</span></span> <span data-ttu-id="96785-129">與 Transact-SQL MIN 函數的不同之處，在於此作業只適用於數值、日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="96785-129">In contrast to the Transact-SQL MIN function, this operation can be used only with numeric, date, and time data types.</span></span>|  
|<span data-ttu-id="96785-130">最大值</span><span class="sxs-lookup"><span data-stu-id="96785-130">Maximum</span></span>|<span data-ttu-id="96785-131">傳回群組中的最大值。</span><span class="sxs-lookup"><span data-stu-id="96785-131">Returns the maximum value in a group.</span></span> <span data-ttu-id="96785-132">如需詳細資訊，請參閱 [MAX &#40;Transact-SQL&#41;](/sql/t-sql/functions/max-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96785-132">For more information, see [MAX &#40;Transact-SQL&#41;](/sql/t-sql/functions/max-transact-sql).</span></span> <span data-ttu-id="96785-133">與 Transact-SQL MAX 函數的不同之處，在於此作業只適用於數值、日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="96785-133">In contrast to the Transact-SQL MAX function, this operation can be used only with numeric, date, and time data types.</span></span>|  
  
 <span data-ttu-id="96785-134">「彙總」轉換處理 Null 值的方式，與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 關聯式 Database Engine 的處理方式相同。</span><span class="sxs-lookup"><span data-stu-id="96785-134">The Aggregate transformation handles null values in the same way as the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] relational database engine.</span></span> <span data-ttu-id="96785-135">此行為是在 SQL-92 標準中所定義。</span><span class="sxs-lookup"><span data-stu-id="96785-135">The behavior is defined in the SQL-92 standard.</span></span> <span data-ttu-id="96785-136">適用的規則如下：</span><span class="sxs-lookup"><span data-stu-id="96785-136">The following rules apply:</span></span>  
  
-   <span data-ttu-id="96785-137">在 GROUP BY 子句中，處理 Null 的方式與處理其他資料行值的方式相同。</span><span class="sxs-lookup"><span data-stu-id="96785-137">In a GROUP BY clause, nulls are treated like other column values.</span></span> <span data-ttu-id="96785-138">若群組資料行內包含了多個 Null 值，Null 值將放入單一群組內。</span><span class="sxs-lookup"><span data-stu-id="96785-138">If the grouping column contains more than one null value, the null values are put into a single group.</span></span>  
  
-   <span data-ttu-id="96785-139">在 COUNT (資料行名稱) 與 COUNT (DISTINCT 資料行名稱) 函數中，會忽略 Null 值，且結果會排除具名資料行中包含 Null 值的資料列。</span><span class="sxs-lookup"><span data-stu-id="96785-139">In the COUNT (column name) and COUNT (DISTINCT column name) functions, nulls are ignored and the result excludes rows that contain null values in the named column.</span></span>  
  
-   <span data-ttu-id="96785-140">在 COUNT (\*) 函數中，會計算所有資料列，包括含有 Null 值的資料列在內。</span><span class="sxs-lookup"><span data-stu-id="96785-140">In the COUNT (\*) function, all rows are counted, including rows with null values.</span></span>  
  
## <a name="big-numbers-in-aggregates"></a><span data-ttu-id="96785-141">彙總中的大數值</span><span class="sxs-lookup"><span data-stu-id="96785-141">Big Numbers in Aggregates</span></span>  
 <span data-ttu-id="96785-142">資料行可能包含因為過大數值或有效位數需求而需要特殊考量的數值。</span><span class="sxs-lookup"><span data-stu-id="96785-142">A column may contain numeric values that require special consideration because of their large value or precision requirements.</span></span> <span data-ttu-id="96785-143">「彙總」轉換包含 IsBig 屬性，您可以在輸出資料行上設定該屬性，以叫用大型數值或高有效位數數值的特殊處理。</span><span class="sxs-lookup"><span data-stu-id="96785-143">The Aggregation transformation includes the IsBig property, which you can set on output columns to invoke special handling of big or high-precision numbers.</span></span> <span data-ttu-id="96785-144">如果資料行值可能超過 40 億，或需要比浮點資料類型更高的有效位數，則 IsBig 應設定為 1。</span><span class="sxs-lookup"><span data-stu-id="96785-144">If a column value may exceed 4 billion or a precision beyond a float data type is required, IsBig should be set to 1.</span></span>  
  
 <span data-ttu-id="96785-145">將 IsBig 屬性設定為 1，會對彙總轉換的輸出有下列影響：</span><span class="sxs-lookup"><span data-stu-id="96785-145">Setting the IsBig property to 1 affects the output of the aggregation transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="96785-146">使用 DT_R8 資料類型，而非 DT_R4 資料類型。</span><span class="sxs-lookup"><span data-stu-id="96785-146">The DT_R8 data type is used instead of the DT_R4 data type.</span></span>  
  
-   <span data-ttu-id="96785-147">計數結果會以 DT_UI8 資料類型儲存。</span><span class="sxs-lookup"><span data-stu-id="96785-147">Count results are stored as the DT_UI8 data type.</span></span>  
  
-   <span data-ttu-id="96785-148">相異計數結果會以 DT_UI4 資料類型儲存。</span><span class="sxs-lookup"><span data-stu-id="96785-148">Distinct count results are stored as the DT_UI4 data type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96785-149">您無法在 GROUP BY、Maximum 或 Minimum 作業所使用的資料行上，將 IsBig 設定為 1。</span><span class="sxs-lookup"><span data-stu-id="96785-149">You cannot set IsBig to 1 on columns that are used in the GROUP BY, Maximum, or Minimum operations.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="96785-150">效能考量</span><span class="sxs-lookup"><span data-stu-id="96785-150">Performance Considerations</span></span>  
 <span data-ttu-id="96785-151">「彙總」轉換包含一組屬性，可讓您用來增強轉換的效能。</span><span class="sxs-lookup"><span data-stu-id="96785-151">The Aggregate transformation includes a set of properties that you can set to enhance the performance of the transformation.</span></span>  
  
-   <span data-ttu-id="96785-152">當執行 [群組依據]  作業時，請設定元件的 Keys 或 KeysScale 屬性和元件輸出。</span><span class="sxs-lookup"><span data-stu-id="96785-152">When performing a **Group by** operation, set the Keys or KeysScale properties of the component and the component outputs.</span></span> <span data-ttu-id="96785-153">您可以使用 Keys，指定轉換預期要處理的確切索引鍵數目。</span><span class="sxs-lookup"><span data-stu-id="96785-153">Using Keys, you can specify the exact number of keys the transformation is expected to handle.</span></span> <span data-ttu-id="96785-154">(在此內容中，Keys 會參考預期要從 [群組依據]  作業產生的群組數)。您可以使用 KeysScale，指定索引鍵的近似數目。</span><span class="sxs-lookup"><span data-stu-id="96785-154">(In this context, Keys refers to the number of groups that are expected to result from a **Group by** operation.) Using KeysScale, you can specify an approximate number of keys.</span></span> <span data-ttu-id="96785-155">當您為 Keys 或 KeyScale 指定適當值時，您將會提高效能，因為轉換能夠針對轉換所快取的資料來配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="96785-155">When you specify an appropriate value for Keys or KeyScale, you improve performance because the tranformation is able to allocate adequate memory for the data that the transformation caches.</span></span>  
  
-   <span data-ttu-id="96785-156">當執行 [相異計數]  作業時，請設定元件的 CountDistinctKeys 或 CountDistinctScale 屬性。</span><span class="sxs-lookup"><span data-stu-id="96785-156">When performing a **Distinct count** operation, set the CountDistinctKeys or CountDistinctScale properties of the component.</span></span> <span data-ttu-id="96785-157">您可以使用 CountDistinctKeys，為相異計數作業指定轉換預期要處理的確切索引鍵數目。</span><span class="sxs-lookup"><span data-stu-id="96785-157">Using CountDistinctKeys, you can specify the exact number of keys the transformation is expected to handle for a count distinct operation.</span></span> <span data-ttu-id="96785-158">(在此內容中，CountDistinctKeys 會參考預期要從 [相異計數]  作業產生的相異值數目)。您可以使用 CountDistinctScale，為相異計數作業指定索引鍵的近似數目。</span><span class="sxs-lookup"><span data-stu-id="96785-158">(In this context, CountDistinctKeys refers to the number of distinct values that are expected to result from a **Distinct count** operation.) Using CountDistinctScale, you can specify an approximate number of keys for a count distinct operation.</span></span> <span data-ttu-id="96785-159">當您為 CountDistinctKeys 或 CountDistinctScale 指定適當值時，您將會提高效能，因為轉換能夠針對轉換所快取的資料來配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="96785-159">When you specify an appropriate value for CountDistinctKeys or CountDistinctScale, you improve performance because the transformation is able to allocate adequate memory for the data that the transformation caches.</span></span>  
  
## <a name="aggregate-transformation-configuration"></a><span data-ttu-id="96785-160">彙總轉換組態</span><span class="sxs-lookup"><span data-stu-id="96785-160">Aggregate Transformation Configuration</span></span>  
 <span data-ttu-id="96785-161">您可以在轉換、輸出和資料行層級設定「彙總」轉換。</span><span class="sxs-lookup"><span data-stu-id="96785-161">You configure the Aggregate transformation at the transformation, output, and column levels.</span></span>  
  
-   <span data-ttu-id="96785-162">在轉換層級上，您可以藉由指定下列值來設定「彙總」轉換的效能：</span><span class="sxs-lookup"><span data-stu-id="96785-162">At the transformation level, you configure the Aggregate transformation for performance by specifying the following values:</span></span>  
  
    -   <span data-ttu-id="96785-163">預期要從 **[群組依據]** 作業產生的群組數。</span><span class="sxs-lookup"><span data-stu-id="96785-163">The number of groups that are expected to result from a **Group by** operation.</span></span>  
  
    -   <span data-ttu-id="96785-164">預期要從 **[相異計數]** 作業產生的相異值數目。</span><span class="sxs-lookup"><span data-stu-id="96785-164">The number of distinct values that are expected to result from a **Count distinct** operation.</span></span>  
  
    -   <span data-ttu-id="96785-165">記憶體於彙總期間可以擴充的百分比。</span><span class="sxs-lookup"><span data-stu-id="96785-165">The percentage by which memory can be extended during the aggregation.</span></span>  
  
     <span data-ttu-id="96785-166">「彙總」轉換也可以設定為在除數的值為零時產生警告，而非發生失敗。</span><span class="sxs-lookup"><span data-stu-id="96785-166">The Aggregate transformation can also be configured to generate a warning instead of failing when the value of a divisor is zero.</span></span>  
  
-   <span data-ttu-id="96785-167">在輸出層級上，您可以藉由指定預期要從 **[群組依據]** 作業產生的群組數來設定「彙總」轉換的效能。</span><span class="sxs-lookup"><span data-stu-id="96785-167">At the output level, you configure the Aggregate transformation for performance by specifying the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="96785-168">「彙總」轉換支援多個輸出，且每個輸出能以不同的方式設定。</span><span class="sxs-lookup"><span data-stu-id="96785-168">The Aggregate transformation supports multiple outputs, and each can be configured differently.</span></span>  
  
-   <span data-ttu-id="96785-169">在資料行層級上，您可以指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="96785-169">At the column level, you specify the following values:</span></span>  
  
    -   <span data-ttu-id="96785-170">資料行執行的彙總。</span><span class="sxs-lookup"><span data-stu-id="96785-170">The aggregation that the column performs.</span></span>  
  
    -   <span data-ttu-id="96785-171">彙總的比較選項。</span><span class="sxs-lookup"><span data-stu-id="96785-171">The comparison options of the aggregation.</span></span>  
  
 <span data-ttu-id="96785-172">您也可以藉由指定下列值來設定「彙總」轉換的效能：</span><span class="sxs-lookup"><span data-stu-id="96785-172">You can also configure the Aggregate transformation for performance by specifying these values:</span></span>  
  
-   <span data-ttu-id="96785-173">預期資料行上要從 **[群組依據]** 作業產生的群組數。</span><span class="sxs-lookup"><span data-stu-id="96785-173">The number of groups that are expected to result from a **Group by** operation on the column.</span></span>  
  
-   <span data-ttu-id="96785-174">預期資料行上要從 **[相異計數]** 作業產生的相異值數目。</span><span class="sxs-lookup"><span data-stu-id="96785-174">The number of distinct values that are expected to result from a **Count distinct** operation on the column.</span></span>  
  
 <span data-ttu-id="96785-175">如果資料行包含大型數值或是有效位數很高的數值，您也可以將識別欄位指定為 IsBig。</span><span class="sxs-lookup"><span data-stu-id="96785-175">You can also identify columns as IsBig if a column contains large numeric values or numeric values with high precision.</span></span>  
  
 <span data-ttu-id="96785-176">「彙總」轉換是非同步的，這表示它不會以逐列的方式取用和發行資料，</span><span class="sxs-lookup"><span data-stu-id="96785-176">The Aggregate transformation is asynchronous, which means that it does not consume and publish data row by row.</span></span> <span data-ttu-id="96785-177">而是會取用整個資料列集、執行其群組和彙總，然後發行結果。</span><span class="sxs-lookup"><span data-stu-id="96785-177">Instead it consumes the whole rowset, performs its groupings and aggregations, and then publishes the results.</span></span>  
  
 <span data-ttu-id="96785-178">這個轉換不會通過任何資料行，但是會在資料流程中為其所發行的資料建立新的資料行。</span><span class="sxs-lookup"><span data-stu-id="96785-178">This transformation does not pass through any columns, but creates new columns in the data flow for the data it publishes.</span></span> <span data-ttu-id="96785-179">只有套用彙總函式的輸入資料行，或是轉換用於群組的輸入資料行，才會複製到轉換輸出。</span><span class="sxs-lookup"><span data-stu-id="96785-179">Only the input columns to which aggregate functions apply or the input columns the transformation uses for grouping are copied to the transformation output.</span></span> <span data-ttu-id="96785-180">例如，「彙總」轉換輸入可能有三個資料行：**CountryRegion**、**City** 和 **Population**。</span><span class="sxs-lookup"><span data-stu-id="96785-180">For example, an Aggregate transformation input might have three columns: **CountryRegion**, **City**, and **Population**.</span></span> <span data-ttu-id="96785-181">轉換會依 **CountryRegion** 資料行來分組，並將 Sum 函數套用至 **Population** 資料行。</span><span class="sxs-lookup"><span data-stu-id="96785-181">The transformation groups by the **CountryRegion** column and applies the Sum function to the **Population** column.</span></span> <span data-ttu-id="96785-182">因此，輸出不會包含 **City** 資料行。</span><span class="sxs-lookup"><span data-stu-id="96785-182">Therefore the output does not include the **City** column.</span></span>  
  
 <span data-ttu-id="96785-183">您也可以將多個輸出加入「彙總」轉換，並將每個彙總導向不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="96785-183">You can also add multiple outputs to the Aggregate transformation and direct each aggregation to a different output.</span></span> <span data-ttu-id="96785-184">例如，如果「彙總」轉換套用 Sum 和 Average 函數，則每個彙總可以導向至不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="96785-184">For example, if the Aggregate transformation applies the Sum and the Average functions, each aggregation can be directed to a different output.</span></span>  
  
 <span data-ttu-id="96785-185">您可以將多個彙總套用至單一輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="96785-185">You can apply multiple aggregations to a single input column.</span></span> <span data-ttu-id="96785-186">例如，如果您要計算名為 **Sales**之輸入資料行的總和與平均值，可以將轉換設定為套用 Sum 和 Average 函數至 **Sales** 資料行。</span><span class="sxs-lookup"><span data-stu-id="96785-186">For example, if you want the sum and average values for an input column named **Sales**, you can configure the transformation to apply both the Sum and Average functions to the **Sales** column.</span></span>  
  
 <span data-ttu-id="96785-187">「彙總」轉換有一個輸入，以及一個或多個輸出。</span><span class="sxs-lookup"><span data-stu-id="96785-187">The Aggregate transformation has one input and one or more outputs.</span></span> <span data-ttu-id="96785-188">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="96785-188">It does not support an error output.</span></span>  
  
 <span data-ttu-id="96785-189">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="96785-189">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="96785-190">如需有關可以在 **[彙總轉換編輯器]** 對話方塊中設定之屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="96785-190">For more information about the properties that you can set in the **Aggregate Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="96785-191">彙總轉換編輯器 &#40;彙總索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="96785-191">Aggregate Transformation Editor &#40;Aggregations Tab&#41;</span></span>](../../aggregate-transformation-editor-aggregations-tab.md)  
  
-   [<span data-ttu-id="96785-192">彙總轉換編輯器 &#40;進階索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="96785-192">Aggregate Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../aggregate-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="96785-193">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="96785-193">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="96785-194">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="96785-194">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="96785-195">Common Properties</span><span class="sxs-lookup"><span data-stu-id="96785-195">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="96785-196">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="96785-196">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="96785-197">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="96785-197">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="96785-198">使用彙總轉換來彙總資料集中的值</span><span class="sxs-lookup"><span data-stu-id="96785-198">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
-   [<span data-ttu-id="96785-199">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="96785-199">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="96785-200">排序合併和合併聯結轉換的資料</span><span class="sxs-lookup"><span data-stu-id="96785-200">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="96785-201">相關工作</span><span class="sxs-lookup"><span data-stu-id="96785-201">Related Tasks</span></span>  
 [<span data-ttu-id="96785-202">使用彙總轉換來彙總資料集中的值</span><span class="sxs-lookup"><span data-stu-id="96785-202">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
## <a name="see-also"></a><span data-ttu-id="96785-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96785-203">See Also</span></span>  
 <span data-ttu-id="96785-204">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="96785-204">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="96785-205">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="96785-205">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
