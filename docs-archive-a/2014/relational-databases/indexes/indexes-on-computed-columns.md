---
title: 計算資料行的索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, index creation
- index creation [SQL Server], computed columns
- imprecise columns
- persisted computed columns
- precise [SQL Server]
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ecbca9e7838c4c9395a8bcb6e11351c40f7037f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709421"
---
# <a name="indexes-on-computed-columns"></a><span data-ttu-id="346da-102">計算資料行的索引</span><span class="sxs-lookup"><span data-stu-id="346da-102">Indexes on Computed Columns</span></span>
  <span data-ttu-id="346da-103">只要符合下列要求，您就可以在計算資料行上定義索引：</span><span class="sxs-lookup"><span data-stu-id="346da-103">You can define indexes on computed columns as long as the following requirements are met:</span></span>  
  
-   <span data-ttu-id="346da-104">擁有權需求</span><span class="sxs-lookup"><span data-stu-id="346da-104">Ownership requirements</span></span>  
  
-   <span data-ttu-id="346da-105">決定性需求</span><span class="sxs-lookup"><span data-stu-id="346da-105">Determinism requirements</span></span>  
  
-   <span data-ttu-id="346da-106">有效位數需求</span><span class="sxs-lookup"><span data-stu-id="346da-106">Precision requirements</span></span>  
  
-   <span data-ttu-id="346da-107">資料類型需求</span><span class="sxs-lookup"><span data-stu-id="346da-107">Data type requirements</span></span>  
  
-   <span data-ttu-id="346da-108">SET 選項需求</span><span class="sxs-lookup"><span data-stu-id="346da-108">SET option requirements</span></span>  
  
 <span data-ttu-id="346da-109">**Ownership Requirements**</span><span class="sxs-lookup"><span data-stu-id="346da-109">**Ownership Requirements**</span></span>  
  
 <span data-ttu-id="346da-110">計算資料行中的所有函數參考都必須與資料表具有相同的擁有者。</span><span class="sxs-lookup"><span data-stu-id="346da-110">All function references in the computed column must have the same owner as the table.</span></span>  
  
 <span data-ttu-id="346da-111">**Determinism Requirements**</span><span class="sxs-lookup"><span data-stu-id="346da-111">**Determinism Requirements**</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="346da-112">如果運算式一定會針對指定的輸入集傳回相同的結果，這些運算式就具有決定性。</span><span class="sxs-lookup"><span data-stu-id="346da-112">Expressions are deterministic if they always return the same result for a specified set of inputs.</span></span> <span data-ttu-id="346da-113">**COLUMNPROPERTY** 函數的 [IsDeterministic](/sql/t-sql/functions/columnproperty-transact-sql) 屬性會報告 *computed_column_expression* 是否具決定性。</span><span class="sxs-lookup"><span data-stu-id="346da-113">The **IsDeterministic** property of the [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) function reports whether a *computed_column_expression* is deterministic.</span></span>  
  
 <span data-ttu-id="346da-114">*computed_column_expression* 必須具決定性。</span><span class="sxs-lookup"><span data-stu-id="346da-114">The *computed_column_expression* must be deterministic.</span></span> <span data-ttu-id="346da-115">若下列一或多種情況成立， *computed_column_expression* 就會具決定性：</span><span class="sxs-lookup"><span data-stu-id="346da-115">A *computed_column_expression* is deterministic when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="346da-116">運算式所參考的所有函數都具有決定性而且是精確的。</span><span class="sxs-lookup"><span data-stu-id="346da-116">All functions that are referenced by the expression are deterministic and precise.</span></span> <span data-ttu-id="346da-117">這些函數包括使用者自訂函數與內建函數。</span><span class="sxs-lookup"><span data-stu-id="346da-117">These functions include both user-defined and built-in functions.</span></span> <span data-ttu-id="346da-118">如需詳細資訊，請參閱 [決定性與非決定性函數](../user-defined-functions/deterministic-and-nondeterministic-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="346da-118">For more information, see [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span> <span data-ttu-id="346da-119">如果計算的資料行是 PERSISTED，函數可能就不精確。</span><span class="sxs-lookup"><span data-stu-id="346da-119">Functions might be imprecise if the computed column is PERSISTED.</span></span> <span data-ttu-id="346da-120">如需詳細資訊，請參閱本主題稍後的 [在保存的計算資料行上建立索引](#BKMK_persisted) 。</span><span class="sxs-lookup"><span data-stu-id="346da-120">For more information, see [Creating Indexes on Persisted Computed Columns](#BKMK_persisted) later in this topic.</span></span>  
  
-   <span data-ttu-id="346da-121">運算式中參考的所有資料行都來自包含計算資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="346da-121">All columns that are referenced in the expression come from the table that contains the computed column.</span></span>  
  
-   <span data-ttu-id="346da-122">沒有資料行參考從多個資料列中提取資料。</span><span class="sxs-lookup"><span data-stu-id="346da-122">No column reference pulls data from multiple rows.</span></span> <span data-ttu-id="346da-123">例如，SUM 或 AVG 這類彙總函數將取決於來自多個資料列的資料，並使得 *computed_column_expression* 不具決定性。</span><span class="sxs-lookup"><span data-stu-id="346da-123">For example, aggregate functions such as SUM or AVG depend on data from multiple rows and would make a *computed_column_expression* nondeterministic.</span></span>  
  
-   <span data-ttu-id="346da-124">*computed_column_expression* 沒有系統資料存取或使用者資料存取。</span><span class="sxs-lookup"><span data-stu-id="346da-124">The *computed_column_expression* has no system data access or user data access.</span></span>  
  
 <span data-ttu-id="346da-125">任何包含 Common Language Runtime (CLR) 運算式的計算資料行都必須具有決定性，而且必須在製作索引前標示為 PERSISTED。</span><span class="sxs-lookup"><span data-stu-id="346da-125">Any computed column that contains a common language runtime (CLR) expression must be deterministic and marked PERSISTED before the column can be indexed.</span></span> <span data-ttu-id="346da-126">在計算的資料行定義中允許 CLR 使用者自訂類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="346da-126">CLR user-defined type expressions are allowed in computed column definitions.</span></span> <span data-ttu-id="346da-127">具有 CLR 使用者自訂類型的計算資料行，只要類型是可比較的就可製作索引。</span><span class="sxs-lookup"><span data-stu-id="346da-127">Computed columns whose type is a CLR user-defined type can be indexed as long as the type is comparable.</span></span> <span data-ttu-id="346da-128">如需詳細資訊，請參閱 [CLR 使用者定義型別](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="346da-128">For more information, see [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="346da-129">當您在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中參考索引計算資料行內的日期資料類型字串常值時，我們建議您使用具有決定性的日期格式樣式，將常值明確轉換成您想要的日期類型。</span><span class="sxs-lookup"><span data-stu-id="346da-129">When you refer to string literals of the date data type in indexed computed columns in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], we recommend that you explicitly convert the literal to the date type that you want by using a deterministic date format style.</span></span> <span data-ttu-id="346da-130">如需具決定性之日期格式樣式的清單，請參閱 [CAST 和 CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="346da-130">For a list of the date format styles that are deterministic, see [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span> <span data-ttu-id="346da-131">除非資料庫相容性層級設定為 80 或以下，否則牽涉到將字元字串隱含轉換成日期資料類型的運算式都會視為不具決定性。</span><span class="sxs-lookup"><span data-stu-id="346da-131">Expressions that involve implicit conversion of character strings to date data types are considered nondeterministic, unless the database compatibility level is set to 80 or earlier.</span></span> <span data-ttu-id="346da-132">這是因為結果需視伺服器工作階段的 [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) 和 [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) 設定而定。</span><span class="sxs-lookup"><span data-stu-id="346da-132">This is because the results depend on the [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) and [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) settings of the server session.</span></span> <span data-ttu-id="346da-133">例如，運算式 `CONVERT (datetime, '30 listopad 1996', 113)` 的結果需視 LANGUAGE 設定而定，因為字串 '`30 listopad 1996`' 在不同的語言中表示不同的月份。</span><span class="sxs-lookup"><span data-stu-id="346da-133">For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`30 listopad 1996`' means different months in different languages.</span></span> <span data-ttu-id="346da-134">同樣地，在運算式 `DATEADD(mm,3,'2000-12-01')`中，「 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 」會根據 DATEFORMAT 設定來解譯 `'2000-12-01'` 字串。</span><span class="sxs-lookup"><span data-stu-id="346da-134">Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.</span></span>  
>   
>  <span data-ttu-id="346da-135">除非相容性層級設定為 80 或以下，否則，定序之間的非 Unicode 字元資料的隱含轉換被視為不具決定性。</span><span class="sxs-lookup"><span data-stu-id="346da-135">Implicit conversion of non-Unicode character data between collations is also considered nondeterministic, unless the compatibility level is set to 80 or earlier.</span></span>  
>   
>  <span data-ttu-id="346da-136">當資料庫相容性層級設定為 90 時，您就不能在包含這些運算式的計算資料行上建立索引。</span><span class="sxs-lookup"><span data-stu-id="346da-136">When the database compatibility level setting is 90, you cannot create indexes on computed columns that contain these expressions.</span></span> <span data-ttu-id="346da-137">但是，包含這些來自升級資料庫之運算式的現有計算資料行是可以維護的。</span><span class="sxs-lookup"><span data-stu-id="346da-137">However, existing computed columns that contain these expressions from an upgraded database are maintainable.</span></span> <span data-ttu-id="346da-138">如果您使用包含字串到日期之隱含轉換的索引計算資料行，請確定資料庫和應用程式中 LANGUAGE 和 DATEFORMAT 設定是一致的，以避免索引損毀。</span><span class="sxs-lookup"><span data-stu-id="346da-138">If you use indexed computed columns that contain implicit string to date conversions, to avoid possible index corruption, make sure that the LANGUAGE and DATEFORMAT settings are consistent in your databases and applications.</span></span>  
  
 <span data-ttu-id="346da-139">**Precision Requirements**</span><span class="sxs-lookup"><span data-stu-id="346da-139">**Precision Requirements**</span></span>  
  
 <span data-ttu-id="346da-140">*computed_column_expression* 必須精確。</span><span class="sxs-lookup"><span data-stu-id="346da-140">The *computed_column_expression* must be precise.</span></span> <span data-ttu-id="346da-141">若下列一或多種情況成立， *computed_column_expression* 就會精確：</span><span class="sxs-lookup"><span data-stu-id="346da-141">A *computed_column_expression* is precise when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="346da-142">它並非 `float` 或 `real` 資料類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="346da-142">It is not an expression of the `float` or `real` data types.</span></span>  
  
-   <span data-ttu-id="346da-143">它的定義中並沒有使用 `float` 或 `real` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="346da-143">It does not use a `float` or `real` data type in its definition.</span></span> <span data-ttu-id="346da-144">例如，在下列陳述式中，`y` 資料行是 `int` 且具有決定性，但並不是精確的。</span><span class="sxs-lookup"><span data-stu-id="346da-144">For example, in the following statement, column `y` is `int` and deterministic but not precise.</span></span>  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="346da-145">任何 `float` 或 `real` 運算式都被視為非精確，並且不能作為索引的索引鍵；`float` 或 `real` 運算式可用於索引檢視中，但不能作為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="346da-145">Any `float` or `real` expression is considered imprecise and cannot be a key of an index; a `float` or `real` expression can be used in an indexed view but not as a key.</span></span> <span data-ttu-id="346da-146">對於計算資料行也是如此。</span><span class="sxs-lookup"><span data-stu-id="346da-146">This is true also for computed columns.</span></span> <span data-ttu-id="346da-147">若任何函數、運算式、使用者自訂函數包含任何 `float` 或 `real` 運算式，均會被視為不精確。</span><span class="sxs-lookup"><span data-stu-id="346da-147">Any function, expression, or user-defined function is considered imprecise if it contains any `float` or `real` expressions.</span></span> <span data-ttu-id="346da-148">這包含邏輯運算式 (比較)。</span><span class="sxs-lookup"><span data-stu-id="346da-148">This includes logical ones (comparisons).</span></span>  
  
 <span data-ttu-id="346da-149">COLUMNPROPERTY 函數的 **IsPrecise** 屬性會報告 *computed_column_expression* 是否精確。</span><span class="sxs-lookup"><span data-stu-id="346da-149">The **IsPrecise** property of the COLUMNPROPERTY function reports whether a *computed_column_expression* is precise.</span></span>  
  
 <span data-ttu-id="346da-150">**資料類型需求**</span><span class="sxs-lookup"><span data-stu-id="346da-150">**Data Type Requirements**</span></span>  
  
-   <span data-ttu-id="346da-151">為計算資料行定義的*computed_column_expression*無法評估為 `text` 、 `ntext` 或 `image` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="346da-151">The *computed_column_expression* defined for the computed column cannot evaluate to the `text`, `ntext`, or `image` data types.</span></span>  
  
-   <span data-ttu-id="346da-152">從 `image`、`ntext`、`text`、`varchar(max)`、`nvarchar(max)`、`varbinary(max)` 以及 `xml` 資料類型所衍生的計算資料行，只要其資料類型可作為索引鍵資料行，就可以製作成索引。</span><span class="sxs-lookup"><span data-stu-id="346da-152">Computed columns derived from `image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, and `xml` data types can be indexed as long as the computed column data type is allowable as an index key column.</span></span>  
  
-   <span data-ttu-id="346da-153">從 `image`、`ntext` 以及 `text` 資料類型所衍生的計算資料行，只要其資料類型可作為非索引鍵之索引資料行，就可作為非叢集索引中無索引鍵 (內含) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="346da-153">Computed columns derived from `image`, `ntext`, and `text` data types can be nonkey (included) columns in a nonclustered index as long as the computed column data type is allowable as a nonkey index column.</span></span>  
  
 <span data-ttu-id="346da-154">**SET 選項需求**</span><span class="sxs-lookup"><span data-stu-id="346da-154">**SET Option Requirements**</span></span>  
  
-   <span data-ttu-id="346da-155">執行定義計算資料行的 CREATE TABLE 或 ALTER TABLE 陳述式時，ANSI_NULLS 連接層級選項必須設定為 ON。</span><span class="sxs-lookup"><span data-stu-id="346da-155">The ANSI_NULLS connection-level option must be set to ON when the CREATE TABLE or ALTER TABLE statement that defines the computed column is executed.</span></span> <span data-ttu-id="346da-156">[OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) 函數將透過 **IsAnsiNullsOn** 屬性，報告選項是否為開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="346da-156">The [OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) function reports whether the option is on through the **IsAnsiNullsOn** property.</span></span>  
  
-   <span data-ttu-id="346da-157">建立索引的連接，以及嘗試執行會變更索引值之 INSERT、UPDATE 或 DELETE 陳述式的所有連線，都必須有六個 SET 選項設成 ON，以及一個選項設成 OFF。</span><span class="sxs-lookup"><span data-stu-id="346da-157">The connection on which the index is created, and all connections trying INSERT, UPDATE, or DELETE statements that will change values in the index, must have six SET options set to ON and one option set to OFF.</span></span> <span data-ttu-id="346da-158">若有任何 SELECT 陳述式是由不具相同選項設定的連接所執行，最佳化工具將略過計算資料行上的索引。</span><span class="sxs-lookup"><span data-stu-id="346da-158">The optimizer ignores an index on a computed column for any SELECT statement executed by a connection that does not have these same option settings.</span></span>  
  
    -   <span data-ttu-id="346da-159">NUMERIC_ROUNDABORT 選項必須設為 OFF，而且下列選項必須設為 ON：</span><span class="sxs-lookup"><span data-stu-id="346da-159">The NUMERIC_ROUNDABORT option must be set to OFF, and the following options must be set to ON:</span></span>  
  
    -   <span data-ttu-id="346da-160">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="346da-160">ANSI_NULLS</span></span>  
  
    -   <span data-ttu-id="346da-161">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="346da-161">ANSI_PADDING</span></span>  
  
    -   <span data-ttu-id="346da-162">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="346da-162">ANSI_WARNINGS</span></span>  
  
    -   <span data-ttu-id="346da-163">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="346da-163">ARITHABORT</span></span>  
  
    -   <span data-ttu-id="346da-164">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="346da-164">CONCAT_NULL_YIELDS_NULL</span></span>  
  
    -   <span data-ttu-id="346da-165">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="346da-165">QUOTED_IDENTIFIER</span></span>  
  
     <span data-ttu-id="346da-166">當資料庫的相容性層級設定為 90 或以上時，將 ANSI_WARNINGS 設定為 ON 也會將 ARITHABORT 隱含設定為 ON。</span><span class="sxs-lookup"><span data-stu-id="346da-166">Setting ANSI_WARNINGS to ON implicitly sets ARITHABORT to ON when the database compatibility level is set to 90 or higher.</span></span>  
  
##  <a name="creating-indexes-on-persisted-computed-columns"></a><a name="BKMK_persisted"></a> <span data-ttu-id="346da-167">在保存的計算資料行上建立索引</span><span class="sxs-lookup"><span data-stu-id="346da-167">Creating Indexes on Persisted Computed Columns</span></span>  
 <span data-ttu-id="346da-168">如果計算的資料行在 CREATE TABLE 或 ALTER TABLE 陳述式中是標示成 PERSISTED，就可在以具有決定性但不精確的運算式所定義的計算資料行上建立索引。</span><span class="sxs-lookup"><span data-stu-id="346da-168">You can create an index on a computed column that is defined with a deterministic, but imprecise, expression if the column is marked PERSISTED in the CREATE TABLE or ALTER TABLE statement.</span></span> <span data-ttu-id="346da-169">這表示當在 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 資料行上建立索引時，以及在查詢中參考索引時，會使用這些保存的值。</span><span class="sxs-lookup"><span data-stu-id="346da-169">This means that the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] uses these persisted values when it creates an index on the column, and when the index is referenced in a query.</span></span> <span data-ttu-id="346da-170">此選項可讓您在計算資料行上建立索引 [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)] ，但同時具有決定性且精確。</span><span class="sxs-lookup"><span data-stu-id="346da-170">This option enables you to create an index on a computed column when [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)], is both deterministic and precise.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="346da-171">相關內容</span><span class="sxs-lookup"><span data-stu-id="346da-171">Related Content</span></span>  
 [<span data-ttu-id="346da-172">COLUMNPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="346da-172">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)  
  
  
