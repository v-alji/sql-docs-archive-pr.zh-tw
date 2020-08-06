---
title: MSSQLSERVER_207 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 207 (Database Engine error)
ms.assetid: d1ab00c7-0331-437a-84fe-bae53b82feec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd6044c08ecd5a73f539bfbc1139d6257c2db9d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698260"
---
# <a name="mssqlserver_207"></a><span data-ttu-id="c848b-102">MSSQLSERVER_207</span><span class="sxs-lookup"><span data-stu-id="c848b-102">MSSQLSERVER_207</span></span>
    
## <a name="details"></a><span data-ttu-id="c848b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c848b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c848b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c848b-104">Product Name</span></span>|<span data-ttu-id="c848b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c848b-105">SQL Server</span></span>|  
|<span data-ttu-id="c848b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c848b-106">Event ID</span></span>|<span data-ttu-id="c848b-107">207</span><span class="sxs-lookup"><span data-stu-id="c848b-107">207</span></span>|  
|<span data-ttu-id="c848b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c848b-108">Event Source</span></span>|<span data-ttu-id="c848b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c848b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c848b-110">元件</span><span class="sxs-lookup"><span data-stu-id="c848b-110">Component</span></span>|<span data-ttu-id="c848b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c848b-111">SQLEngine</span></span>|  
|<span data-ttu-id="c848b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c848b-112">Symbolic Name</span></span>|<span data-ttu-id="c848b-113">SQ_BADCOL</span><span class="sxs-lookup"><span data-stu-id="c848b-113">SQ_BADCOL</span></span>|  
|<span data-ttu-id="c848b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c848b-114">Message Text</span></span>|<span data-ttu-id="c848b-115">無效的資料行名稱 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="c848b-115">Invalid column name '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c848b-116">說明</span><span class="sxs-lookup"><span data-stu-id="c848b-116">Explanation</span></span>  
 <span data-ttu-id="c848b-117">這項查詢錯誤可能是由於下列其中一個問題所造成。</span><span class="sxs-lookup"><span data-stu-id="c848b-117">This query error can be caused by one of the following problems.</span></span>  
  
-   <span data-ttu-id="c848b-118">資料行名稱拼字錯誤，或者資料行不存在任何指定的資料表中。</span><span class="sxs-lookup"><span data-stu-id="c848b-118">The column name is misspelled or the column does not exist in any of the specified tables.</span></span>  
  
-   <span data-ttu-id="c848b-119">資料庫的定序會區分大小寫，而且查詢中指定之資料行名稱的大小寫不符合資料表中定義之資料行的大小寫。</span><span class="sxs-lookup"><span data-stu-id="c848b-119">The collation of the database is case-sensitive and the case of the column name specified in the query does not match the case of the column defined in the table.</span></span> <span data-ttu-id="c848b-120">例如，如果資料庫中含有區分大小寫的定序，當資料表中的資料行定義為 **LastName**時，以 **Lastname** 或 **lastname** 的形式查詢此資料行會導致系統傳回錯誤 207，因為資料行名稱不符。</span><span class="sxs-lookup"><span data-stu-id="c848b-120">For example, when a column is defined in a table as **LastName** and the database uses a case-sensitive collation, queries that refer to the column as **Lastname** or **lastname** will cause error 207 to return because the column name does not match.</span></span>  
  
-   <span data-ttu-id="c848b-121">在 SELECT 子句中定義的資料行別名由其他子句 (例如 WHERE 或 GROUP BY 子句) 所參考。</span><span class="sxs-lookup"><span data-stu-id="c848b-121">A column alias, defined in the SELECT clause, is referenced in another clause such as a WHERE or GROUP BY clause.</span></span> <span data-ttu-id="c848b-122">例如，下列查詢會在 SELECT 子句中定義資料行別名 `Year`，並且在 GROUP BY 子句中參考它。</span><span class="sxs-lookup"><span data-stu-id="c848b-122">For example, the following query defines the column alias `Year` in the SELECT clause and refers to it in the GROUP BY clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year, SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY Year;  
    ```  
  
     <span data-ttu-id="c848b-123">這則範例會因查詢子句的邏輯處理順序而傳回錯誤 207。</span><span class="sxs-lookup"><span data-stu-id="c848b-123">Due to the order in which query clauses are logically processed, the example returns error 207.</span></span> <span data-ttu-id="c848b-124">處理順序如下：</span><span class="sxs-lookup"><span data-stu-id="c848b-124">The processing order is as follows:</span></span>  
  
    1.  <span data-ttu-id="c848b-125">FROM</span><span class="sxs-lookup"><span data-stu-id="c848b-125">FROM</span></span>  
  
    2.  <span data-ttu-id="c848b-126">開啟</span><span class="sxs-lookup"><span data-stu-id="c848b-126">ON</span></span>  
  
    3.  <span data-ttu-id="c848b-127">JOIN</span><span class="sxs-lookup"><span data-stu-id="c848b-127">JOIN</span></span>  
  
    4.  <span data-ttu-id="c848b-128">WHERE</span><span class="sxs-lookup"><span data-stu-id="c848b-128">WHERE</span></span>  
  
    5.  <span data-ttu-id="c848b-129">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="c848b-129">GROUP BY</span></span>  
  
    6.  <span data-ttu-id="c848b-130">WITH CUBE 或 WITH ROLLUP</span><span class="sxs-lookup"><span data-stu-id="c848b-130">WITH CUBE or WITH ROLLUP</span></span>  
  
    7.  <span data-ttu-id="c848b-131">HAVING</span><span class="sxs-lookup"><span data-stu-id="c848b-131">HAVING</span></span>  
  
    8.  <span data-ttu-id="c848b-132">SELECT</span><span class="sxs-lookup"><span data-stu-id="c848b-132">SELECT</span></span>  
  
    9. <span data-ttu-id="c848b-133">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="c848b-133">DISTINCT</span></span>  
  
    10. <span data-ttu-id="c848b-134">排序依據</span><span class="sxs-lookup"><span data-stu-id="c848b-134">ORDER BY</span></span>  
  
    11. <span data-ttu-id="c848b-135">頂端</span><span class="sxs-lookup"><span data-stu-id="c848b-135">TOP</span></span>  
  
     <span data-ttu-id="c848b-136">由於處理 SELECT 子句之前尚未定義資料行別名，因此在處理 GROUP BY 子句時別名名稱是未知的。</span><span class="sxs-lookup"><span data-stu-id="c848b-136">Because a column alias is not defined until the SELECT clause is processed, the alias name is unknown when the GROUP BY clause is processed.</span></span>  
  
-   <span data-ttu-id="c848b-137">當 *<merge_matched>* 子句參考了來源資料表中的資料行，但是 WHEN NOT MATCHED BY SOURCE 子句中的來源資料表沒有傳回任何資料列時，MERGE 陳述式就會引發這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="c848b-137">The MERGE statement raises this error when the *<merge_matched>* clause references columns in the source table but no rows are returned by the source table in the WHEN NOT MATCHED BY SOURCE clause.</span></span> <span data-ttu-id="c848b-138">發生此錯誤的原因是，沒有任何資料列傳回給查詢時，系統無法存取來源資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="c848b-138">The error occurs because the columns in the source table cannot be accessed when no rows are returned to the query.</span></span> <span data-ttu-id="c848b-139">例如，如果無法存取來源資料表的 `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1`，子句 `Col1` 可能會導致陳述式失敗。</span><span class="sxs-lookup"><span data-stu-id="c848b-139">For example, the clause `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` may cause the statement to fail if `Col1` in the source table is inaccessible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c848b-140">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c848b-140">User Action</span></span>  
 <span data-ttu-id="c848b-141">請確認下列資訊並依適當情況更正陳述式。</span><span class="sxs-lookup"><span data-stu-id="c848b-141">Verify the following information and correct the statement as appropriate.</span></span>  
  
-   <span data-ttu-id="c848b-142">資料行名稱存在資料表中，而且拼字正確。</span><span class="sxs-lookup"><span data-stu-id="c848b-142">The column name exists in the table and is spelled correctly.</span></span> <span data-ttu-id="c848b-143">下列範例會查詢 **sys.columns** 目錄檢視，以便傳回給定資料表的所有資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="c848b-143">The following example queries the **sys.columns** catalog view to return all column names for a given table.</span></span>  
  
    ```  
    SELECT name FROM sys.columns WHERE object_id = OBJECT_ID('schema_name.table_name');  
    ```  
  
-   <span data-ttu-id="c848b-144">資料庫定序是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c848b-144">The case sensitivity of the database collation.</span></span> <span data-ttu-id="c848b-145">下列陳述式會傳回指定之資料庫的定序。</span><span class="sxs-lookup"><span data-stu-id="c848b-145">The following statement returns the collation of the specified database.</span></span>  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     <span data-ttu-id="c848b-146">定序名稱中的縮寫 CS 表示定序會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c848b-146">The abbreviation CS in the collation name indicates the collation is case-sensitive.</span></span> <span data-ttu-id="c848b-147">例如，Latin1_General_CS_AS 是區分大小寫而且區分腔調字的定序。</span><span class="sxs-lookup"><span data-stu-id="c848b-147">For example, Latin1_General_CS_AS is a case-sensitive and accent-sensitive collation.</span></span> <span data-ttu-id="c848b-148">請將資料行名稱修改成符合資料表中定義之資料行名稱的大小寫。</span><span class="sxs-lookup"><span data-stu-id="c848b-148">Modify the column name to match the case of the column name as it is defined in the table.</span></span>  
  
-   <span data-ttu-id="c848b-149">資料行別名的參考方式不正確。</span><span class="sxs-lookup"><span data-stu-id="c848b-149">A column alias is referenced incorrectly.</span></span> <span data-ttu-id="c848b-150">請在正確的子句中重複定義別名的運算式或使用衍生資料表，藉此修改陳述式。</span><span class="sxs-lookup"><span data-stu-id="c848b-150">Modify the statement by repeating the expression that defines the alias in the appropriate clause or by using a derived table.</span></span> <span data-ttu-id="c848b-151">下列範例會在 GROUP BY 子句中重複定義 `Year` 別名的運算式。</span><span class="sxs-lookup"><span data-stu-id="c848b-151">The following example repeats the expressions that define the `Year` alias in the GROUP BY clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year ,SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY DATEPART(yyyy,OrderDate);  
    ```  
  
     <span data-ttu-id="c848b-152">下列範例會使用衍生資料表，讓別名名稱可供查詢中的其他子句使用。</span><span class="sxs-lookup"><span data-stu-id="c848b-152">The following example uses a derived table to make the alias name available to other clauses in the query.</span></span> <span data-ttu-id="c848b-153">請注意，別名 `Year` 定義於 FROM 子句中 (優先處理)，因此會讓別名可用於查詢中的其他子句。</span><span class="sxs-lookup"><span data-stu-id="c848b-153">Notice that the alias `Year` is defined in the FROM clause, which is processed first, and so makes the alias available for use in other clauses in the query.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT d.Year, SUM(TotalDue) AS Total  
    FROM (SELECT DATEPART(yyyy,OrderDate) AS Year, TotalDue  
          FROM Sales.SalesOrderHeader)AS d  
    GROUP BY Year;  
    ```  
  
-   <span data-ttu-id="c848b-154">MERGE 陳述式中的 WHEN NOT MATCHED BY SOURCE 子句參考了可存取的值。</span><span class="sxs-lookup"><span data-stu-id="c848b-154">The WHEN NOT MATCHED BY SOURCE clause in the MERGE statement refers to a value that can be accessed.</span></span> <span data-ttu-id="c848b-155">請修改 MERGE 陳述式，讓 WHEN NOT MATCHED BY SOURCE 子句中的來源資料表至少會傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="c848b-155">Modify the MERGE statement so that at least one row is returned by the source table in the WHEN NOT MATCHED BY SOURCE clause.</span></span> <span data-ttu-id="c848b-156">例如，您可能必須加入或修訂針對該子句所指定的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="c848b-156">For example, you might need to add or revise the search condition specified for the clause.</span></span> <span data-ttu-id="c848b-157">或者，您也可以修改子句，以便指定沒有參考來源資料表的值。</span><span class="sxs-lookup"><span data-stu-id="c848b-157">Alternatively, you can modify the clause to specify a value that does not reference the source table.</span></span> <span data-ttu-id="c848b-158">例如： `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>` 。</span><span class="sxs-lookup"><span data-stu-id="c848b-158">For example, `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c848b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c848b-159">See Also</span></span>  
 <span data-ttu-id="c848b-160">[MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c848b-160">[MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql) </span></span>  
 <span data-ttu-id="c848b-161">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c848b-161">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span></span>  
 <span data-ttu-id="c848b-162">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c848b-162">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="c848b-163">UPDATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c848b-163">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
