---
title: SQL Server 2014 中資料庫引擎功能的行為變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- behavior changes [SQL Server]
- Database Engine [SQL Server], what's new
- Transact-SQL behavior changes
ms.assetid: 65eaafa1-9e06-4264-b547-cbee8013c995
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9072b851f3512113b23dedc91f8c9b7151136a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700240"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a><span data-ttu-id="16469-102">SQL Server 2014 中對於 Database Engine 功能的行為變更</span><span class="sxs-lookup"><span data-stu-id="16469-102">Behavior Changes to Database Engine Features in SQL Server 2014</span></span>
  <span data-ttu-id="16469-103">本主題描述 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中的行為變更。</span><span class="sxs-lookup"><span data-stu-id="16469-103">This topic describes behavior changes in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="16469-104">行為變更會影響 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 功能的運作或互動方式 (相較於舊版的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="16469-104">Behavior changes affect how features work or interact in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] as compared to earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="behavior-changes-in-sssql14"></a><a name="SQL14"></a><span data-ttu-id="16469-105">中的行為變更[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16469-105">Behavior Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="16469-106">在舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中，針對包含超過特定長度 (超過 4020 個字元) 之字串的 XML 文件進行查詢，可能會傳回不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="16469-106">In earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], queries against an XML document that contains strings over a certain length (more than 4020 characters) can return incorrect results.</span></span> <span data-ttu-id="16469-107">在 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 中，這類查詢會傳回正確的結果。</span><span class="sxs-lookup"><span data-stu-id="16469-107">In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], such queries return the correct results.</span></span>  
  
## <a name="behavior-changes-in-sssql11"></a><a name="Denali"></a><span data-ttu-id="16469-108">中的行為變更[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16469-108">Behavior Changes in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
  
### <a name="metadata-discovery"></a><span data-ttu-id="16469-109">中繼資料探索</span><span class="sxs-lookup"><span data-stu-id="16469-109">Metadata Discovery</span></span>  
 <span data-ttu-id="16469-110">中的改良功能， [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 可讓 SQLDescribeCol 取得比舊版中的 SQLDescribeCol 所傳回的預期結果更精確的描述 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="16469-110">Improvements in the [!INCLUDE[ssDE](../includes/ssde-md.md)] starting with [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] allow SQLDescribeCol to obtain more accurate descriptions of the expected results than those returned by SQLDescribeCol in previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="16469-111">如需詳細資訊，請參閱[中繼資料探索](../relational-databases/native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="16469-111">For more information, see [Metadata Discovery](../relational-databases/native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="16469-112">用來判斷回應格式而不實際執行查詢的[SET set fmtonly](/sql/t-sql/statements/set-fmtonly-transact-sql)選項，會取代為[sp_describe_first_result_set &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql)、 [sp_describe_undeclared_parameters &#40;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql)transact-sql&#41;，以及[dm_exec_describe_first_result_set &#40;transact-sql ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql)&#41;[中 dm_exec_describe_first_result_set_for_object](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql)的 transact-sql &#40;。</span><span class="sxs-lookup"><span data-stu-id="16469-112">The [SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql) option for determining the format of a response without actually running the query is replaced with [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql), [sp_describe_undeclared_parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql), [sys.dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql), and [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql).</span></span>  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a><span data-ttu-id="16469-113">編寫 SQL Server Agent 工作之指令碼時的行為變更</span><span class="sxs-lookup"><span data-stu-id="16469-113">Changes to Behavior in Scripting a SQL Server Agent Task</span></span>  
<span data-ttu-id="16469-114">從開始 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ，如果您從現有作業複製腳本來建立新作業，新的作業可能會不小心影響現有的作業。</span><span class="sxs-lookup"><span data-stu-id="16469-114">Starting with [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], if you create a new job by copying the script from an existing job, the new job might inadvertently affect the existing job.</span></span> <span data-ttu-id="16469-115">若要使用現有作業中的腳本建立新作業，請手動刪除參數\* \@ schedule_uid\*這通常是在現有作業中建立作業排程之區段的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="16469-115">To create a new job using the script from an existing job, manually delete the parameter *\@schedule_uid* which is usually the last parameter of the section which creates the job schedule in the existing job.</span></span> <span data-ttu-id="16469-116">這將會為新的作業建立新的獨立排程，而不會影響現有的作業。</span><span class="sxs-lookup"><span data-stu-id="16469-116">This will create a new independent schedule for the new job without affecting existing jobs.</span></span>  
  
### <a name="constant-folding-for-clr-user-defined-functions-and-methods"></a><span data-ttu-id="16469-117">CLR 使用者定義函數和方法的常數摺疊</span><span class="sxs-lookup"><span data-stu-id="16469-117">Constant Folding for CLR User-Defined Functions and Methods</span></span>  
<span data-ttu-id="16469-118">從開始 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ，下列使用者定義的 CLR 物件現在可以折迭：</span><span class="sxs-lookup"><span data-stu-id="16469-118">Starting with [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the following user-defined CLR objects are now foldable:</span></span>  

-   <span data-ttu-id="16469-119">具決定性、純量值的 CLR 使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="16469-119">Deterministic scalar-valued CLR user-defined functions.</span></span>  
-   <span data-ttu-id="16469-120">CLR 使用者定義類型的具決定性方法。</span><span class="sxs-lookup"><span data-stu-id="16469-120">Deterministic methods of CLR user-defined types.</span></span>  
  
 <span data-ttu-id="16469-121">此改進旨在於這些函數或方法都使用相同的引數多次呼叫時提高效能。</span><span class="sxs-lookup"><span data-stu-id="16469-121">This improvement seeks to enhance performance when these functions or methods are called more than once with the same arguments.</span></span> <span data-ttu-id="16469-122">但在不具決定性函數或方法因誤標記為具決定性時，此變更可能會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="16469-122">However, this change may cause unexpected results when non-deterministic functions or methods have been marked as deterministic in error.</span></span> <span data-ttu-id="16469-123">CLR 函數或方法的決定性是由 `IsDeterministic` 或 `SqlFunctionAttribute` 的 `SqlMethodAttribute` 屬性值所指出。</span><span class="sxs-lookup"><span data-stu-id="16469-123">The determinism of a CLR function or method is indicated by the value of the `IsDeterministic` property of the `SqlFunctionAttribute` or `SqlMethodAttribute`.</span></span>  
  
### <a name="behavior-of-stenvelope-method-has-changed-with-empty-spatial-types"></a><span data-ttu-id="16469-124">空白空間類型之 STEnvelope() 方法的行為已變更</span><span class="sxs-lookup"><span data-stu-id="16469-124">Behavior of STEnvelope() Method Has Changed with Empty Spatial Types</span></span>  
 <span data-ttu-id="16469-125">具有空白物件之 `STEnvelope` 方法的行為現在與其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 空間方法的行為一致。</span><span class="sxs-lookup"><span data-stu-id="16469-125">The behavior of the `STEnvelope` method with empty objects is now consistent with the behavior of other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spatial methods.</span></span>  
  
 <span data-ttu-id="16469-126">在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 中，以空白物件呼叫 `STEnvelope` 方法時，此方法傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="16469-126">In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], the `STEnvelope` method returned the following results when called with empty objects:</span></span>  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns POINT EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns LINESTRING EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns POLYGON EMPTY  
```  
  
 <span data-ttu-id="16469-127">在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中，以空白物件呼叫 `STEnvelope` 方法時，此方法現在傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="16469-127">In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the `STEnvelope` method now returns the following results when called with empty objects:</span></span>  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
```  
  
 <span data-ttu-id="16469-128">若要判斷空間物件是否為空白，請呼叫[STIsEmpty &#40;Geometry 資料類型&#41;](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type)方法。</span><span class="sxs-lookup"><span data-stu-id="16469-128">To determine whether a spatial object is empty, call the [STIsEmpty &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) method.</span></span>  
  
### <a name="log-function-has-new-optional-parameter"></a><span data-ttu-id="16469-129">LOG 函數有新的選擇性參數</span><span class="sxs-lookup"><span data-stu-id="16469-129">LOG Function Has New Optional Parameter</span></span>  
 <span data-ttu-id="16469-130">`LOG`函數現在有選擇性的*基底*參數。</span><span class="sxs-lookup"><span data-stu-id="16469-130">The `LOG` function now has an optional *base* parameter.</span></span> <span data-ttu-id="16469-131">如需詳細資訊，請參閱[LOG &#40;transact-sql&#41;](/sql/t-sql/functions/log-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="16469-131">For more information, see [LOG &#40;Transact-SQL&#41;](/sql/t-sql/functions/log-transact-sql).</span></span>  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a><span data-ttu-id="16469-132">分割區索引作業期間的統計資料計算已變更</span><span class="sxs-lookup"><span data-stu-id="16469-132">Statistics Computation during Partitioned Index Operations Has Changed</span></span>  
<span data-ttu-id="16469-133"> 並不會在建立或重建分割區索引之後掃描資料表中所有的資料列建立統計資料。</span><span class="sxs-lookup"><span data-stu-id="16469-133">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], statistics are not created by scanning all rows in the table when a partitioned index is created or rebuilt.</span></span> <span data-ttu-id="16469-134">反之，查詢最佳化工具會使用預設的取樣演算法來產生統計資料。</span><span class="sxs-lookup"><span data-stu-id="16469-134">Instead, the Query Optimizer uses the default sampling algorithm to generate statistics.</span></span> <span data-ttu-id="16469-135">升級具有分割區索引的資料庫之後，可能會注意到這些索引之長條圖資料的差異。</span><span class="sxs-lookup"><span data-stu-id="16469-135">After upgrading a database with partitioned indexes, you may notice a difference in the histogram data for these indexes.</span></span> <span data-ttu-id="16469-136">此行為變更可能不會影響查詢效能。</span><span class="sxs-lookup"><span data-stu-id="16469-136">This change in behavior may not affect query performance.</span></span> <span data-ttu-id="16469-137">若要在掃描資料表中所有資料列時取得分割區索引的統計資料，使用子句 `FULLSCAN` 時請使用 `CREATE STATISTICS` 或 `UPDATE STATISTICS`。</span><span class="sxs-lookup"><span data-stu-id="16469-137">To obtain statistics on partitioned indexes by scanning all the rows in the table, use `CREATE STATISTICS` or `UPDATE STATISTICS` with the `FULLSCAN` clause.</span></span>  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a><span data-ttu-id="16469-138">XML value 方法的資料類型轉換已變更</span><span class="sxs-lookup"><span data-stu-id="16469-138">Data Type Conversion by the XML value Method Has Changed</span></span>  
<span data-ttu-id="16469-139">資料類型之 方法的內部行為已變更。</span><span class="sxs-lookup"><span data-stu-id="16469-139">The internal behavior of the `value` method of the `xml` data type has changed.</span></span> <span data-ttu-id="16469-140">此方法會針對 XML 執行 XQuery 並傳回指定之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料類型的純量值。</span><span class="sxs-lookup"><span data-stu-id="16469-140">This method performs an XQuery against the XML and returns a scalar value of the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="16469-141">xs 類型必須轉換為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="16469-141">The xs type has to be converted to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="16469-142">以前 `value` 方法會在內部將來源值轉換為 xs:string，然後將 xs:string 轉換為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="16469-142">Previously, the `value` method internally converted the source value to an xs:string, then converted the xs:string to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="16469-143">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中，下列情況下會略過 xs:string 的轉換：</span><span class="sxs-lookup"><span data-stu-id="16469-143">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], the conversion to xs:string is skipped in the following cases:</span></span>  
  
|<span data-ttu-id="16469-144">來源 XS 資料類型</span><span class="sxs-lookup"><span data-stu-id="16469-144">Source XS data type</span></span>|<span data-ttu-id="16469-145">目的地 SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="16469-145">Destination SQL Server data type</span></span>|  
|-------------------------|--------------------------------------|  
|<span data-ttu-id="16469-146">byte</span><span class="sxs-lookup"><span data-stu-id="16469-146">byte</span></span><br /><br /> <span data-ttu-id="16469-147">short</span><span class="sxs-lookup"><span data-stu-id="16469-147">short</span></span><br /><br /> <span data-ttu-id="16469-148">int</span><span class="sxs-lookup"><span data-stu-id="16469-148">int</span></span><br /><br /> <span data-ttu-id="16469-149">integer</span><span class="sxs-lookup"><span data-stu-id="16469-149">integer</span></span><br /><br /> <span data-ttu-id="16469-150">long</span><span class="sxs-lookup"><span data-stu-id="16469-150">long</span></span><br /><br /> <span data-ttu-id="16469-151">unsignedByte</span><span class="sxs-lookup"><span data-stu-id="16469-151">unsignedByte</span></span><br /><br /> <span data-ttu-id="16469-152">unsignedShort</span><span class="sxs-lookup"><span data-stu-id="16469-152">unsignedShort</span></span><br /><br /> <span data-ttu-id="16469-153">unsignedInt</span><span class="sxs-lookup"><span data-stu-id="16469-153">unsignedInt</span></span><br /><br /> <span data-ttu-id="16469-154">unsignedLong</span><span class="sxs-lookup"><span data-stu-id="16469-154">unsignedLong</span></span><br /><br /> <span data-ttu-id="16469-155">positiveInteger</span><span class="sxs-lookup"><span data-stu-id="16469-155">positiveInteger</span></span><br /><br /> <span data-ttu-id="16469-156">nonPositiveInteger</span><span class="sxs-lookup"><span data-stu-id="16469-156">nonPositiveInteger</span></span><br /><br /> <span data-ttu-id="16469-157">negativeInteger</span><span class="sxs-lookup"><span data-stu-id="16469-157">negativeInteger</span></span><br /><br /> <span data-ttu-id="16469-158">nonNegativeInteger</span><span class="sxs-lookup"><span data-stu-id="16469-158">nonNegativeInteger</span></span>|<span data-ttu-id="16469-159">TINYINT</span><span class="sxs-lookup"><span data-stu-id="16469-159">tinyint</span></span><br /><br /> <span data-ttu-id="16469-160">SMALLINT</span><span class="sxs-lookup"><span data-stu-id="16469-160">smallint</span></span><br /><br /> <span data-ttu-id="16469-161">int</span><span class="sxs-lookup"><span data-stu-id="16469-161">int</span></span><br /><br /> <span data-ttu-id="16469-162">BIGINT</span><span class="sxs-lookup"><span data-stu-id="16469-162">bigint</span></span><br /><br /> <span data-ttu-id="16469-163">decimal</span><span class="sxs-lookup"><span data-stu-id="16469-163">decimal</span></span><br /><br /> <span data-ttu-id="16469-164">NUMERIC</span><span class="sxs-lookup"><span data-stu-id="16469-164">numeric</span></span>|  
|<span data-ttu-id="16469-165">decimal</span><span class="sxs-lookup"><span data-stu-id="16469-165">decimal</span></span>|<span data-ttu-id="16469-166">decimal</span><span class="sxs-lookup"><span data-stu-id="16469-166">decimal</span></span><br /><br /> <span data-ttu-id="16469-167">NUMERIC</span><span class="sxs-lookup"><span data-stu-id="16469-167">numeric</span></span>|  
|<span data-ttu-id="16469-168">FLOAT</span><span class="sxs-lookup"><span data-stu-id="16469-168">float</span></span>|<span data-ttu-id="16469-169">real</span><span class="sxs-lookup"><span data-stu-id="16469-169">real</span></span>|  
|<span data-ttu-id="16469-170">double</span><span class="sxs-lookup"><span data-stu-id="16469-170">double</span></span>|<span data-ttu-id="16469-171">FLOAT</span><span class="sxs-lookup"><span data-stu-id="16469-171">float</span></span>|  
  
 <span data-ttu-id="16469-172">可以略過中繼轉換時，新行為會提高效能。</span><span class="sxs-lookup"><span data-stu-id="16469-172">The new behavior improves performance when the intermediate conversion can be skipped.</span></span> <span data-ttu-id="16469-173">但在資料類型轉換失敗時，您會看到不同於從中繼 xs:string 值轉換時所引發的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="16469-173">However, when data type conversions fail, you see different error messages than those that were raised when converting from the intermediate xs:string value.</span></span> <span data-ttu-id="16469-174">例如，如果 value 方法無法將 `int` 值 100000 轉換為 `smallint`，以前的錯誤訊息是：</span><span class="sxs-lookup"><span data-stu-id="16469-174">For example, if the value method failed to convert the `int` value 100000 to a `smallint`, the previous error message was:</span></span>  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 <span data-ttu-id="16469-175">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]，如果沒有 xs:string 的中繼轉換，錯誤訊息是：</span><span class="sxs-lookup"><span data-stu-id="16469-175">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], without the intermediate conversion to xs:string, the error message is:</span></span>  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a><span data-ttu-id="16469-176">XML 模式中的 sqlcmd.exe 行為變更</span><span class="sxs-lookup"><span data-stu-id="16469-176">sqlcmd.exe Behavior Change in XML Mode</span></span>  
 <span data-ttu-id="16469-177">如果您在執行 SELECT \* from T FOR XML ... 時，在命令) 上使用 sqlcmd.exe 搭配 XML 模式 (： XML，則會有行為變更。</span><span class="sxs-lookup"><span data-stu-id="16469-177">There are behavior changes if you use sqlcmd.exe with XML mode (:XML ON command) when executing a SELECT \* from T FOR XML ....</span></span>  
  
### <a name="dbcc-checkident-revised-message"></a><span data-ttu-id="16469-178">DBCC CHECKIDENT 修訂的訊息</span><span class="sxs-lookup"><span data-stu-id="16469-178">DBCC CHECKIDENT Revised Message</span></span>  
 <span data-ttu-id="16469-179">在中 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ，DBCC CHECKIDENT 命令所傳回的訊息只有在與重新植入*new_reseed_value*變更目前的識別值一起使用時才會變更。</span><span class="sxs-lookup"><span data-stu-id="16469-179">In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the message returned by the DBCC CHECKIDENT command has changed only when it is used with RESEED *new_reseed_value*  to change current identity value.</span></span> <span data-ttu-id="16469-180">新訊息是「*正在檢查識別資訊：目前的識別值 ' \<current identity value> '*」。</span><span class="sxs-lookup"><span data-stu-id="16469-180">The new message is *"Checking identity information: current identity value '\<current identity value>'"*.</span></span> <span data-ttu-id="16469-181">DBCC 的執行已經完成。</span><span class="sxs-lookup"><span data-stu-id="16469-181">DBCC execution completed.</span></span> <span data-ttu-id="16469-182">如果 DBCC 印出錯誤訊息，請連絡您的系統管理員」。</span><span class="sxs-lookup"><span data-stu-id="16469-182">If DBCC printed error messages, contact your system administrator."</span></span>  
  
 <span data-ttu-id="16469-183">在舊版中，訊息是「*正在檢查識別資訊：目前的識別值 ' \<current identity value> '，目前的資料行值 ' \<current column value> '。DBCC 執行已完成。如果 DBCC 印出錯誤訊息，請洽詢您的系統管理員。* 」</span><span class="sxs-lookup"><span data-stu-id="16469-183">In earlier versions, the message is *"Checking identity information: current identity value '\<current identity value>', current column value '\<current column value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator."*</span></span> <span data-ttu-id="16469-184">當 `DBCC CHECKIDENT` 指定了 `NORESEED` 、但沒有第二個參數，或沒有重新植入值時，訊息會原封不動。</span><span class="sxs-lookup"><span data-stu-id="16469-184">The message is unchanged when `DBCC CHECKIDENT` is specified with `NORESEED`, without a second parameter, or without a reseed value.</span></span> <span data-ttu-id="16469-185">如需詳細資訊，請參閱 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="16469-185">For more information, see [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).</span></span>  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a><span data-ttu-id="16469-186">XML 資料類型上之 exist() 函數的行為已變更</span><span class="sxs-lookup"><span data-stu-id="16469-186">Behavior of exist() function on XML datatype has changed</span></span>  
 <span data-ttu-id="16469-187">將 `exist()` 具有 null 值的 XML 資料類型與 0 (零) 進行比較時，函數的行為已變更。</span><span class="sxs-lookup"><span data-stu-id="16469-187">The behavior of the `exist()` function has changed when comparing an XML data type with a null value to 0 (zero).</span></span> <span data-ttu-id="16469-188">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="16469-188">Consider the following example:</span></span>  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 0;  
```  
  
 <span data-ttu-id="16469-189">在舊版中，此比較傳回 1 (true)；現在，此比較傳回 0 (零，false)。</span><span class="sxs-lookup"><span data-stu-id="16469-189">In earlier versions, this comparison return 1 (true); now, this comparison returns 0 (zero, false).</span></span>  
  
 <span data-ttu-id="16469-190">下列比較尚未變更：</span><span class="sxs-lookup"><span data-stu-id="16469-190">The following comparisons have not changed:</span></span>  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 1; -- 0 expected, 0 returned  
SELECT COUNT(1) WHERE @test.exist('/dogs') IS NULL; -- 1 expected, 1 returned  
```  
  
## <a name="see-also"></a><span data-ttu-id="16469-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16469-191">See Also</span></span>  
 <span data-ttu-id="16469-192">[SQL Server 2014 中資料庫引擎功能的重大變更](breaking-changes-to-database-engine-features-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="16469-192">[Breaking Changes to Database Engine Features in SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="16469-193">[SQL Server 2014 中已淘汰的資料庫引擎功能](deprecated-database-engine-features-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="16469-193">[Deprecated Database Engine Features in SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="16469-194">[SQL Server 2014 中已停止的資料庫引擎功能](discontinued-database-engine-functionality-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="16469-194">[Discontinued Database Engine Functionality in SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md) </span></span>  
 [<span data-ttu-id="16469-195">ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="16469-195">ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
