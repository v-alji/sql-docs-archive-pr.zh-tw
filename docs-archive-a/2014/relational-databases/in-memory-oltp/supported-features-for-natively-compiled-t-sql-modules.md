---
title: 原生編譯預存程式中支援的結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
author: rothja
ms.author: jroth
ms.openlocfilehash: 65e6e794c5858a68c4b2a9b298513911b487cf52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606311"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a><span data-ttu-id="4a3a6-102">原生編譯的預存程序中支援的建構</span><span class="sxs-lookup"><span data-stu-id="4a3a6-102">Supported Constructs in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="4a3a6-103">本主題包含原生編譯預存程式支援的功能清單 ([CREATE PROCEDURE &#40;transact-sql&#41;](/sql/t-sql/statements/create-procedure-transact-sql)) ：</span><span class="sxs-lookup"><span data-stu-id="4a3a6-103">This topic contains a list of supported features for natively compiled stored procedures ([CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)):</span></span>  
  
-   [<span data-ttu-id="4a3a6-104">原生編譯預存程序的程式設計功能</span><span class="sxs-lookup"><span data-stu-id="4a3a6-104">Programmability in Natively Compiled Stored Procedures</span></span>](#pncsp)  
  
-   [<span data-ttu-id="4a3a6-105">支援的運算子</span><span class="sxs-lookup"><span data-stu-id="4a3a6-105">Supported Operators</span></span>](#so)  
  
-   [<span data-ttu-id="4a3a6-106">原生編譯預存程序中的內建函數</span><span class="sxs-lookup"><span data-stu-id="4a3a6-106">Built-in Functions in Natively Compiled Stored Procedures</span></span>](#bfncsp)  
  
-   [<span data-ttu-id="4a3a6-107">原生編譯預存程序中的查詢介面區</span><span class="sxs-lookup"><span data-stu-id="4a3a6-107">Query Surface Area in Natively Compiled Stored Procedures</span></span>](#qsancsp)  
  
-   [<span data-ttu-id="4a3a6-108">稽核</span><span class="sxs-lookup"><span data-stu-id="4a3a6-108">Auditing</span></span>](#auditing)  
  
-   [<span data-ttu-id="4a3a6-109">資料表、查詢和聯結提示</span><span class="sxs-lookup"><span data-stu-id="4a3a6-109">Table, Query, and Join Hints</span></span>](#tqh)  
  
-   [<span data-ttu-id="4a3a6-110">排序的限制</span><span class="sxs-lookup"><span data-stu-id="4a3a6-110">Limitations on Sorting</span></span>](#los)  
  
 <span data-ttu-id="4a3a6-111">如需原生編譯預存程序支援的資料類型資訊，請參閱 [Supported Data Types](supported-data-types-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-111">For information on data types supported in natively compiled stored procedures, see [Supported Data Types](supported-data-types-for-in-memory-oltp.md).</span></span>  
  
 <span data-ttu-id="4a3a6-112">如需有關不支援之建構的完整資訊，請參閱＜ [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-112">For complete information about unsupported constructs, and for information about how to work around some of the unsupported features in natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).</span></span> <span data-ttu-id="4a3a6-113">如需不支援功能的詳細資訊，請參閱 [記憶體中的 OLTP 不支援 Transact-SQL 建構](transact-sql-constructs-not-supported-by-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-113">For more information about unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
##  <a name="programmability-in-natively-compiled-stored-procedures"></a><a name="pncsp"></a><span data-ttu-id="4a3a6-114">原生編譯預存程式中的可程式性</span><span class="sxs-lookup"><span data-stu-id="4a3a6-114">Programmability in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="4a3a6-115">支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="4a3a6-115">The following are supported:</span></span>  
  
-   <span data-ttu-id="4a3a6-116">BEGIN ATOMIC (在預存程序的外部層級)、LANGUAGE、ISOLATION LEVEL、DATEFORMAT 和 DATEFIRST。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-116">BEGIN ATOMIC (at the outer level of the stored procedure), LANGUAGE, ISOLATION LEVEL, DATEFORMAT, and DATEFIRST.</span></span>  
  
-   <span data-ttu-id="4a3a6-117">將變數宣告為 NULL 或 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-117">Declaring variables as NULL or NOT NULL.</span></span> <span data-ttu-id="4a3a6-118">如果變數宣告為 NOT NULL，宣告必須有初始設定式。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-118">If a variable is declared as NOT NULL, the declaration must have an initializer.</span></span> <span data-ttu-id="4a3a6-119">如果變數未宣告為 NOT NULL，初始設定式是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-119">If a variable is not declared as NOT NULL, an initializer is optional.</span></span>  
  
-   <span data-ttu-id="4a3a6-120">IF 和 WHILE</span><span class="sxs-lookup"><span data-stu-id="4a3a6-120">IF and WHILE</span></span>  
  
-   <span data-ttu-id="4a3a6-121">INSERT/UPDATE/DELETE</span><span class="sxs-lookup"><span data-stu-id="4a3a6-121">INSERT/UPDATE/DELETE</span></span>  
  
     <span data-ttu-id="4a3a6-122">不支援子查詢。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-122">Subqueries are not supported.</span></span> <span data-ttu-id="4a3a6-123">在 WHERE 或 HAVING 子句，支援 AND 和 BETWEEN，但不支援 OR、NOT 和 IN。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-123">In the WHERE or HAVING clause, AND and BETWEEN are supported; OR, NOT, and IN are not supported.</span></span>  
  
-   <span data-ttu-id="4a3a6-124">記憶體最佳化的資料表類型和資料表變數。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-124">Memory-optimized table types and table variables.</span></span>  
  
-   <span data-ttu-id="4a3a6-125">RETURN</span><span class="sxs-lookup"><span data-stu-id="4a3a6-125">RETURN</span></span>  
  
-   <span data-ttu-id="4a3a6-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="4a3a6-126">SELECT</span></span>  
  
-   <span data-ttu-id="4a3a6-127">SET</span><span class="sxs-lookup"><span data-stu-id="4a3a6-127">SET</span></span>  
  
-   <span data-ttu-id="4a3a6-128">TRY/CATCH/THROW</span><span class="sxs-lookup"><span data-stu-id="4a3a6-128">TRY/CATCH/THROW</span></span>  
  
     <span data-ttu-id="4a3a6-129">若要最佳化效能，整個原生編譯預存程序必須使用單一 TRY/CATCH 區塊。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-129">To optimize performance, use a single TRY/CATCH block for an entire natively compiled stored procedure.</span></span>  
  
##  <a name="supported-operators"></a><a name="so"></a> <span data-ttu-id="4a3a6-130">支援的運算子</span><span class="sxs-lookup"><span data-stu-id="4a3a6-130">Supported Operators</span></span>  
 <span data-ttu-id="4a3a6-131">下列為支援的運算子。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-131">The following operators are supported.</span></span>  
  
-   <span data-ttu-id="4a3a6-132">[&#40;transact-sql&#41;的比較運算子](/sql/t-sql/language-elements/comparison-operators-transact-sql) (例如， \<, > 如果 <，則在條件) 中支援 >、= 和 (=) 。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-132">[Comparison Operators &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/comparison-operators-transact-sql) (for example, >, \<, >=, and <=) are supported in conditionals (IF, WHILE).</span></span>  
  
-   <span data-ttu-id="4a3a6-133">一元運算子 (+、-)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-133">Unary operators (+, -).</span></span>  
  
-   <span data-ttu-id="4a3a6-134">二元運算子 (\*、/、+、-、% (模數) )。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-134">Binary operators (\*, /, +, -, % (modulo)).</span></span>  
  
     <span data-ttu-id="4a3a6-135">數字和字串都支援加號運算子 (+)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-135">The plus operator (+) is supported on both numbers and strings.</span></span>  
  
-   <span data-ttu-id="4a3a6-136">邏輯運算子 (AND、OR、NOT)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-136">Logical operators (AND, OR, NOT).</span></span> <span data-ttu-id="4a3a6-137">IF 和 WHILE 陳述式支援 OR 和 NOT，但是 WHERE 或 HAVING 子句則不支援。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-137">OR and NOT are supported in IF and WHILE statements but not in WHERE or HAVING clauses.</span></span>  
  
-   <span data-ttu-id="4a3a6-138">位元運算子 ~、&、| 和 ^</span><span class="sxs-lookup"><span data-stu-id="4a3a6-138">Bitwise operators ~, &, |, and ^</span></span>  
  
##  <a name="built-in-functions-in-natively-compiled-stored-procedures"></a><a name="bfncsp"></a><span data-ttu-id="4a3a6-139">原生編譯預存程式中的內建函數</span><span class="sxs-lookup"><span data-stu-id="4a3a6-139">Built-in Functions in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="4a3a6-140">記憶體最佳化資料表上的預設條件約束和原生編譯預存程序中，支援下列函數。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-140">The following functions are supported in default constraints on memory-optimized tables and in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="4a3a6-141">數學函數：ACOS、ASIN、ATAN、ATN2、COS、COT、DEGREES、EXP、LOG、LOG10、PI、POWER、RADIANS、RAND、SIN、SQRT、SQUARE 和 TAN</span><span class="sxs-lookup"><span data-stu-id="4a3a6-141">Math Functions: ACOS, ASIN, ATAN, ATN2, COS, COT, DEGREES, EXP, LOG, LOG10, PI, POWER, RADIANS, RAND, SIN, SQRT, SQUARE, and TAN</span></span>  
  
-   <span data-ttu-id="4a3a6-142">日期函數：CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME 和 YEAR。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-142">Date Functions: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME, and YEAR.</span></span>  
  
-   <span data-ttu-id="4a3a6-143">字串函數：LEN、LTRIM、RTRIM 和 SUBSTRING</span><span class="sxs-lookup"><span data-stu-id="4a3a6-143">String Functions: LEN, LTRIM, RTRIM, and SUBSTRING</span></span>  
  
-   <span data-ttu-id="4a3a6-144">Identity 函數：SCOPE_IDENTITY</span><span class="sxs-lookup"><span data-stu-id="4a3a6-144">Identity Function: SCOPE_IDENTITY</span></span>  
  
-   <span data-ttu-id="4a3a6-145">NULL 函式：ISNULL</span><span class="sxs-lookup"><span data-stu-id="4a3a6-145">NULL functions: ISNULL</span></span>  
  
-   <span data-ttu-id="4a3a6-146">Uniqueidentifier 函式：NEWID 和 NEWSEQUENTIALID</span><span class="sxs-lookup"><span data-stu-id="4a3a6-146">Uniqueidentifier functions: NEWID and NEWSEQUENTIALID</span></span>  
  
-   <span data-ttu-id="4a3a6-147">錯誤函數：ERROR_LINE、ERROR_MESSAGE、ERROR_NUMBER、ERROR_PROCEDURE、ERROR_SEVERITY 和 ERROR_STATE</span><span class="sxs-lookup"><span data-stu-id="4a3a6-147">Error Functions: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE</span></span>  
  
-   <span data-ttu-id="4a3a6-148">轉換：CAST 和 CONVERT。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-148">Conversions: CAST and CONVERT.</span></span> <span data-ttu-id="4a3a6-149">不支援 Unicode 和非 Unicode 字元字串 (n(var)char 和 (var)char) 之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-149">Conversions between Unicode and non-Unicode character strings (n(var)char and (var)char) are not supported.</span></span>  
  
-   <span data-ttu-id="4a3a6-150">系統函式：@@rowcount。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-150">System Functions: @@rowcount.</span></span> <span data-ttu-id="4a3a6-151">原生編譯預存程序內的陳述式會更新 @@rowcount，您可以在原生編譯預存程序中使用 @@rowcount，來判斷該原生編譯預存程序內最後執行之陳述式所影響的資料列數。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-151">Statements inside natively compiled stored procedures update @@rowcount and you can use @@rowcount in a natively compiled stored procedure to determine the number of rows affected by the last statement executed within that natively compiled stored procedure.</span></span> <span data-ttu-id="4a3a6-152">不過，@@rowcount 會在原生編譯預存程序開始及結束執行時重設為 0。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-152">However, @@rowcount is reset to 0 at the start and at the end of the execution of a natively compiled stored procedure.</span></span>  
  
##  <a name="query-surface-area-in-natively-compiled-stored-procedures"></a><a name="qsancsp"></a><span data-ttu-id="4a3a6-153">原生編譯預存程式中的查詢介面區</span><span class="sxs-lookup"><span data-stu-id="4a3a6-153">Query Surface Area in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="4a3a6-154">支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="4a3a6-154">The following are supported:</span></span>  
  
-   <span data-ttu-id="4a3a6-155">BETWEEN</span><span class="sxs-lookup"><span data-stu-id="4a3a6-155">BETWEEN</span></span>  
  
-   <span data-ttu-id="4a3a6-156">資料行名稱別名 (使用 AS 或 = 語法)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-156">Column name aliases (using either AS or = syntax).</span></span>  
  
-   <span data-ttu-id="4a3a6-157">只有 SELECT 查詢支援 CROSS JOIN 和 INNER JOIN。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-157">CROSS JOIN and INNER JOIN, supported only with SELECT queries.</span></span>  
  
-   <span data-ttu-id="4a3a6-158">選取清單中支援運算式，如果使用支援的運算子，則會在[&#40;transact-sql&#41;子句的位置](/sql/t-sql/queries/where-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-158">Expressions are supported in SELECT list and [WHERE &#40;Transact-SQL&#41;](/sql/t-sql/queries/where-transact-sql) clause if they use a supported operator.</span></span> <span data-ttu-id="4a3a6-159">如需目前支援的運算子清單，請參閱 [Supported Operators](#so) 。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-159">See [Supported Operators](#so) for the list of currently-supported operators.</span></span>  
  
-   <span data-ttu-id="4a3a6-160">篩選器述詞 IS [NOT] NULL</span><span class="sxs-lookup"><span data-stu-id="4a3a6-160">Filter predicate IS [NOT] NULL</span></span>  
  
-   <span data-ttu-id="4a3a6-161">FROM \<memory optimized table></span><span class="sxs-lookup"><span data-stu-id="4a3a6-161">FROM \<memory optimized table></span></span>  
  
-   <span data-ttu-id="4a3a6-162">支援[GROUP BY &#40;transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql) ，以及彙總函式 AVG、COUNT、COUNT_BIG、MIN、MAX 和 SUM。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-162">[GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) is supported, along with the aggregate functions AVG, COUNT, COUNT_BIG, MIN, MAX, and SUM.</span></span> <span data-ttu-id="4a3a6-163">nvarchar、char、varchar、varchar、varbinary 和 binary 類型不支援 MIN 和 MAX。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-163">MIN and MAX are not supported for types nvarchar, char, varchar, varchar, varbinary, and binary.</span></span> <span data-ttu-id="4a3a6-164">如果 ORDER BY 清單中的運算式逐字出現在 GROUP BY 清單中，則[order By 子句 &#40;transact-sql&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)就會受到[Group by &#40;transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql)的支援。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-164">[ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) is supported with [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) if an expression in the ORDER BY list appears verbatim in the GROUP BY list.</span></span> <span data-ttu-id="4a3a6-165">例如，支援 GROUP BY a + b ORDER BY a + b，但不支援 GROUP BY a, b ORDER BY a + b。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-165">For example, GROUP BY a + b ORDER BY a + b is supported, but GROUP BY a, b ORDER BY a + b is not.</span></span>  
  
-   <span data-ttu-id="4a3a6-166">HAVING，受限於 WHERE 子句相同的運算式限制。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-166">HAVING, subject to the same expression limitations as the WHERE clause.</span></span>  
  
-   <span data-ttu-id="4a3a6-167">INSERT VALUES (每個陳述式一個資料列) 和 INSERT SELECT</span><span class="sxs-lookup"><span data-stu-id="4a3a6-167">INSERT VALUES (one row per statement) and INSERT SELECT</span></span>  
  
-   <span data-ttu-id="4a3a6-168">排序依據<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4a3a6-168">ORDER BY <sup>1</sup></span></span>  
  
-   <span data-ttu-id="4a3a6-169">未參考資料行的述詞。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-169">Predicates not referencing a column.</span></span>  
  
-   <span data-ttu-id="4a3a6-170">SELECT、UPDATE 和 DELETE</span><span class="sxs-lookup"><span data-stu-id="4a3a6-170">SELECT, UPDATE, and DELETE</span></span>  
  
-   <span data-ttu-id="4a3a6-171">前<sup>1</sup>名</span><span class="sxs-lookup"><span data-stu-id="4a3a6-171">TOP <sup>1</sup></span></span>  
  
-   <span data-ttu-id="4a3a6-172">SELECT 清單中的變數指派。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-172">Variable assignment in the SELECT list.</span></span>  
  
-   <span data-ttu-id="4a3a6-173">WHERE .。。和</span><span class="sxs-lookup"><span data-stu-id="4a3a6-173">WHERE ... AND</span></span>  
  
 <span data-ttu-id="4a3a6-174"><sup>1</sup>原生編譯的預存程式支援 ORDER BY 和 TOP，但有一些限制：</span><span class="sxs-lookup"><span data-stu-id="4a3a6-174"><sup>1</sup> ORDER BY and TOP are supported in natively compiled stored procedures, with some restrictions:</span></span>  
  
-   <span data-ttu-id="4a3a6-175">不支援 `DISTINCT` 或 `SELECT` 子句中的 `ORDER BY`。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-175">There is no support for `DISTINCT` in the `SELECT` or `ORDER BY` clause.</span></span>  
  
-   <span data-ttu-id="4a3a6-176">不支援 `WITH TIES` 子句中的 `PERCENT` 或 `TOP`。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-176">There is no support for `WITH TIES` or `PERCENT` in the `TOP` clause.</span></span>  
  
-   <span data-ttu-id="4a3a6-177">在 `TOP` 子句中使用常數時，`ORDER BY` 與 `TOP` 結合不可大於 8,192。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-177">`TOP` combined with `ORDER BY` does not support more than 8,192 when using a constant in the `TOP` clause.</span></span> <span data-ttu-id="4a3a6-178">如果查詢包含聯結或彙總函數，這個限制可能會降低。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-178">This limit may be lowered in case the query contains joins or aggregate functions.</span></span> <span data-ttu-id="4a3a6-179">(例如，如果有一個聯結 (兩個資料表)，限制為 4,096 個資料列。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-179">(For example, with one join (two tables), the limit is 4,096 rows.</span></span> <span data-ttu-id="4a3a6-180">如果使用兩個聯結 (三個資料表)，限制為 2,730 個資料列)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-180">With two joins (three tables), the limit is 2,730 rows.)</span></span>  
  
     <span data-ttu-id="4a3a6-181">您可以在變數中儲存資料列數，以取得大於 8,192 的結果。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-181">You can obtain results greater than 8,192 by storing the number of rows in a variable:</span></span>  
  
    ```sql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) ... FROM ... ORDER BY ...  
    ```  
  
 <span data-ttu-id="4a3a6-182">不過，與使用變數相較，`TOP` 子句中的常數會產生較好的效能。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-182">However, a constant in the `TOP` clause results in better performance compared to using a variable.</span></span>  
  
 <span data-ttu-id="4a3a6-183">這些限制不適用於記憶體最佳化資料表上解譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存取。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-183">These restrictions do not apply to interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access on memory-optimized tables.</span></span>  
  
##  <a name="auditing"></a><a name="auditing"></a> <span data-ttu-id="4a3a6-184">稽核</span><span class="sxs-lookup"><span data-stu-id="4a3a6-184">Auditing</span></span>  
 <span data-ttu-id="4a3a6-185">原生編譯預存程序中支援程序層級稽核。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-185">Procedure level auditing is supported in natively compiled stored procedures.</span></span> <span data-ttu-id="4a3a6-186">不支援陳述式層級稽核。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-186">Statement level auditing is not supported.</span></span>  
  
 <span data-ttu-id="4a3a6-187">如需有關稽核的詳細資訊，請參閱＜ [建立伺服器稽核和資料庫稽核規格](../security/auditing/create-a-server-audit-and-database-audit-specification.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-187">For more information about auditing, see [Create a Server Audit and Database Audit Specification](../security/auditing/create-a-server-audit-and-database-audit-specification.md).</span></span>  
  
##  <a name="table-query-and-join-hints"></a><a name="tqh"></a><span data-ttu-id="4a3a6-188">資料表、查詢和聯結提示</span><span class="sxs-lookup"><span data-stu-id="4a3a6-188">Table, Query, and Join Hints</span></span>  
 <span data-ttu-id="4a3a6-189">支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="4a3a6-189">The following are supported:</span></span>  
  
-   <span data-ttu-id="4a3a6-190">在資料表提示語法或查詢的 [OPTION 子句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) 中的 INDEX、FORCESCAN 和 FORCESEEK 提示。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-190">INDEX, FORCESCAN, and FORCESEEK hints, either in table hints syntax or in [OPTION Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) of the query.</span></span>  
  
-   <span data-ttu-id="4a3a6-191">FORCE ORDER</span><span class="sxs-lookup"><span data-stu-id="4a3a6-191">FORCE ORDER</span></span>  
  
-   <span data-ttu-id="4a3a6-192">內部迴圈聯結</span><span class="sxs-lookup"><span data-stu-id="4a3a6-192">INNER LOOP JOIN</span></span>  
  
-   <span data-ttu-id="4a3a6-193">OPTIMIZE FOR</span><span class="sxs-lookup"><span data-stu-id="4a3a6-193">OPTIMIZE FOR</span></span>  
  
 <span data-ttu-id="4a3a6-194">如需詳細資訊，請參閱[transact-sql&#41;的提示 &#40;](/sql/t-sql/queries/hints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-194">For more information, see [Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql).</span></span>  
  
##  <a name="limitations-on-sorting"></a><a name="los"></a> <span data-ttu-id="4a3a6-195">排序的限制</span><span class="sxs-lookup"><span data-stu-id="4a3a6-195">Limitations on Sorting</span></span>  
 <span data-ttu-id="4a3a6-196">在使用 [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) 和一個 [ORDER BY 子句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) 的查詢中，您可以排序 8000 多個資料列。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-196">You can sort greater than 8,000 rows in a query that uses [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) and an [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).</span></span> <span data-ttu-id="4a3a6-197">但是沒有 [ORDER BY 子句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)，[TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) 最多只能排序 8000 個資料列 (如果有聯結則資料列更少)。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-197">However, without [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) can sort up to 8,000 rows (fewer rows if there are joins).</span></span>  
  
 <span data-ttu-id="4a3a6-198">如果查詢同時使用 [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) 運算子和一個 [ORDER BY 子句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)，TOP 運算子最多可以指定 8192 個資料列。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-198">If your query uses both the [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) operator and an [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), you can specify up to 8192 rows for the TOP operator.</span></span> <span data-ttu-id="4a3a6-199">如果您指定超過 8192 個資料列，則會收到錯誤訊息：**訊息 41398，層級 16，狀態 1、程序 *\<procedureName>* ，行 *\<lineNumber>* TOP 運算子可傳回最多 8192 個資料列；要求的數目為 *\<number>* 。**</span><span class="sxs-lookup"><span data-stu-id="4a3a6-199">If you specify more than 8192 rows you get the error message: **Msg 41398, Level 16, State 1, Procedure *\<procedureName>*, Line *\<lineNumber>* The TOP operator can return a maximum of 8192 rows; *\<number>* was requested.**</span></span>  
  
 <span data-ttu-id="4a3a6-200">如果您沒有 TOP 子句，則可以使用 ORDER BY 排序任意數目的資料列。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-200">If you do not have a TOP clause, you can sort any number of rows with ORDER BY.</span></span>  
  
 <span data-ttu-id="4a3a6-201">如果您未使用 ORDER BY 子句，則可以使用任何整數值搭配 TOP 運算子。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-201">If you do not use an ORDER BY clause, you can use any integer value with the TOP operator.</span></span>  
  
 <span data-ttu-id="4a3a6-202">使用 TOP N = 8192 的範例：編譯</span><span class="sxs-lookup"><span data-stu-id="4a3a6-202">Example with TOP N = 8192: Compiles</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="4a3a6-203">使用 TOP N > 8192 的範例：無法編譯。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-203">Example with TOP N > 8192: Fails to compile.</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="4a3a6-204">8192 資料列限制只適用於 `TOP N` ，其中 `N` 是常數，如前面的範例中所示。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-204">The 8192 row limitation only applies to `TOP N` where `N` is a constant, as in the preceding examples.</span></span>  <span data-ttu-id="4a3a6-205">如果您需要讓 `N` 大於 8192，可以將值指派給變數，並使用該變數搭配 `TOP`。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-205">If you need `N` greater than 8192 you can assign the value to a variable and use that variable with `TOP`.</span></span>  
  
 <span data-ttu-id="4a3a6-206">使用變數的範例：編譯</span><span class="sxs-lookup"><span data-stu-id="4a3a6-206">Example using a variable: Compiles</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="4a3a6-207">**傳回資料列的限制：** 有兩種情況可能會減少 TOP 運算子能夠傳回的資料列數目：</span><span class="sxs-lookup"><span data-stu-id="4a3a6-207">**Limitations on rows returned:** There are two cases where that can potentially reduce the number of rows that can be returned by the TOP operator:</span></span>  
  
-   <span data-ttu-id="4a3a6-208">在查詢中使用 JOIN。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-208">Using JOINs in the query.</span></span>  <span data-ttu-id="4a3a6-209">JOIN 對限制的影響取決於查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-209">The influence of JOINs on the limitation depends on the query plan.</span></span>  
  
-   <span data-ttu-id="4a3a6-210">使用彙總函式或參考彙總 ORDER BY 子句中的函式。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-210">Using aggregate functions or references to aggregate functions in the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="4a3a6-211">計算 TOP N 中最差情況下支援之最大值 N 的公式是： `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`。</span><span class="sxs-lookup"><span data-stu-id="4a3a6-211">The formula to calculate a worst case maximum supported N in TOP N is: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3a6-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a3a6-212">See Also</span></span>  
 <span data-ttu-id="4a3a6-213">[原生編譯的預存程序](natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4a3a6-213">[Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="4a3a6-214">原生編譯預存程序的移轉問題</span><span class="sxs-lookup"><span data-stu-id="4a3a6-214">Migration Issues for Natively Compiled Stored Procedures</span></span>](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
