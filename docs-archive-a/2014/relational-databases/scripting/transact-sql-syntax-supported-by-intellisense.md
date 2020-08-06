---
title: IntelliSense 所支援的 Transact-SQL 語法
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL IntelliSense
- IntelliSense [SQL Server], Transact-SQL syntax
ms.assetid: 194e8f4f-fd7e-4f32-a169-f23531128004
author: rothja
ms.author: jroth
ms.openlocfilehash: b3d34fc79dd7817e64b34b61083415477860ce97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702666"
---
# <a name="transact-sql-syntax-supported-by-intellisense"></a><span data-ttu-id="51b5e-102">IntelliSense 所支援的 Transact-SQL 語法</span><span class="sxs-lookup"><span data-stu-id="51b5e-102">Transact-SQL Syntax Supported by IntelliSense</span></span>
  <span data-ttu-id="51b5e-103">此主題描述 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中 IntelliSense 所支援的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]陳述式和語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-103">This topic describes the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and syntax elements that are supported by IntelliSense in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="statements-supported-by-intellisense"></a><span data-ttu-id="51b5e-104">IntelliSense 所支援的陳述式</span><span class="sxs-lookup"><span data-stu-id="51b5e-104">Statements Supported by IntelliSense</span></span>  
 <span data-ttu-id="51b5e-105">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，IntelliSense 僅支援最常用的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="51b5e-105">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], IntelliSense supports only the most commonly used [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="51b5e-106">某些一般的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器條件可能會讓 IntelliSense 無法運作。</span><span class="sxs-lookup"><span data-stu-id="51b5e-106">Some general [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor conditions might prevent IntelliSense from functioning.</span></span> <span data-ttu-id="51b5e-107">如需詳細資訊，請參閱[疑難排解 IntelliSense &#40;SQL Server Management Studio&#41;](troubleshooting-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="51b5e-107">For more information, see [Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;](troubleshooting-intellisense.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51b5e-108">IntelliSense 不適用於已加密的資料庫物件，例如已加密的預存程序或使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="51b5e-108">IntelliSense is not available for encrypted database objects, such as encrypted stored procedures or user-defined functions.</span></span> <span data-ttu-id="51b5e-109">參數說明和快速資訊不適用於擴充預存程序和 CLR 整合使用者定義型別的參數。</span><span class="sxs-lookup"><span data-stu-id="51b5e-109">Parameter help and Quick Info are not available for the parameters of extended stored procedures and CLR Integration user-defined types.</span></span>  
  
### <a name="select-statement"></a><span data-ttu-id="51b5e-110">SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="51b5e-110">SELECT Statement</span></span>  
 <span data-ttu-id="51b5e-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器會針對 SELECT 陳述式中的下列語法元素提供 IntelliSense 支援：</span><span class="sxs-lookup"><span data-stu-id="51b5e-111">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor provides IntelliSense support for the following syntax elements in the SELECT statement:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51b5e-112">SELECT</span><span class="sxs-lookup"><span data-stu-id="51b5e-112">SELECT</span></span>|<span data-ttu-id="51b5e-113">WHERE</span><span class="sxs-lookup"><span data-stu-id="51b5e-113">WHERE</span></span>|  
|<span data-ttu-id="51b5e-114">FROM</span><span class="sxs-lookup"><span data-stu-id="51b5e-114">FROM</span></span>|<span data-ttu-id="51b5e-115">排序依據</span><span class="sxs-lookup"><span data-stu-id="51b5e-115">ORDER BY</span></span>|  
|<span data-ttu-id="51b5e-116">HAVING</span><span class="sxs-lookup"><span data-stu-id="51b5e-116">HAVING</span></span>|<span data-ttu-id="51b5e-117">UNION</span><span class="sxs-lookup"><span data-stu-id="51b5e-117">UNION</span></span>|  
|<span data-ttu-id="51b5e-118">FOR</span><span class="sxs-lookup"><span data-stu-id="51b5e-118">FOR</span></span>|<span data-ttu-id="51b5e-119">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="51b5e-119">GROUP BY</span></span>|  
|<span data-ttu-id="51b5e-120">頂端</span><span class="sxs-lookup"><span data-stu-id="51b5e-120">TOP</span></span>|<span data-ttu-id="51b5e-121">OPTION (hint)</span><span class="sxs-lookup"><span data-stu-id="51b5e-121">OPTION (hint)</span></span>|  
  
### <a name="additional-transact-sql-statements-that-are-supported"></a><span data-ttu-id="51b5e-122">其他支援的 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="51b5e-122">Additional Transact-SQL Statements That Are Supported</span></span>  
 <span data-ttu-id="51b5e-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器也會針對下表所顯示的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式提供 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="51b5e-123">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor also provides IntelliSense support for [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are shown in the following table.</span></span>  
  
|<span data-ttu-id="51b5e-124">Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="51b5e-124">Transact-SQL statement</span></span>|<span data-ttu-id="51b5e-125">支援的語法</span><span class="sxs-lookup"><span data-stu-id="51b5e-125">Syntax supported</span></span>|  
|-----------------------------|----------------------|  
|[<span data-ttu-id="51b5e-126">INSERT</span><span class="sxs-lookup"><span data-stu-id="51b5e-126">INSERT</span></span>](/sql/t-sql/statements/insert-transact-sql)|<span data-ttu-id="51b5e-127">所有語法，但 *execute_statement* 子句除外。</span><span class="sxs-lookup"><span data-stu-id="51b5e-127">All syntax, except the *execute_statement* clause.</span></span>|  
|[<span data-ttu-id="51b5e-128">UPDATE</span><span class="sxs-lookup"><span data-stu-id="51b5e-128">UPDATE</span></span>](/sql/t-sql/queries/update-transact-sql)|<span data-ttu-id="51b5e-129">所有語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-129">All syntax.</span></span>|  
|[<span data-ttu-id="51b5e-130">DELETE</span><span class="sxs-lookup"><span data-stu-id="51b5e-130">DELETE</span></span>](/sql/t-sql/statements/delete-transact-sql)|<span data-ttu-id="51b5e-131">所有語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-131">All syntax.</span></span>|  
|[<span data-ttu-id="51b5e-132">聲明@local_variable</span><span class="sxs-lookup"><span data-stu-id="51b5e-132">DECLARE @local_variable</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)|<span data-ttu-id="51b5e-133">所有語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-133">All syntax.</span></span>|  
|[<span data-ttu-id="51b5e-134">設定@local_variable</span><span class="sxs-lookup"><span data-stu-id="51b5e-134">SET @local_variable</span></span>](/sql/t-sql/language-elements/set-local-variable-transact-sql)|<span data-ttu-id="51b5e-135">所有語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-135">All syntax.</span></span>|  
|[<span data-ttu-id="51b5e-136">執行</span><span class="sxs-lookup"><span data-stu-id="51b5e-136">EXECUTE</span></span>](/sql/t-sql/language-elements/execute-transact-sql)|<span data-ttu-id="51b5e-137">可執行使用者定義的預存程序、系統預存程序、使用者定義的函數以及系統函數。</span><span class="sxs-lookup"><span data-stu-id="51b5e-137">Execution of user-defined stored procedures, system stored procedures, user-defined functions, and system functions.</span></span>|  
|[<span data-ttu-id="51b5e-138">CREATE TABLE</span><span class="sxs-lookup"><span data-stu-id="51b5e-138">CREATE TABLE</span></span>](/sql/t-sql/statements/create-table-transact-sql)|<span data-ttu-id="51b5e-139">所有語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-139">All syntax.</span></span>|  
|[<span data-ttu-id="51b5e-140">CREATE VIEW</span><span class="sxs-lookup"><span data-stu-id="51b5e-140">CREATE VIEW</span></span>](/sql/t-sql/statements/create-view-transact-sql)|<span data-ttu-id="51b5e-141">所有語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-141">All syntax.</span></span>|  
|[<span data-ttu-id="51b5e-142">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="51b5e-142">CREATE PROCEDURE</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)|<span data-ttu-id="51b5e-143">所有語法，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="51b5e-143">All syntax, with the following exceptions:</span></span><br /><br /> <span data-ttu-id="51b5e-144">EXTERNAL NAME 子句沒有任何 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="51b5e-144">There is no IntelliSense support for the EXTERNAL NAME clause.</span></span><br /><br /> <span data-ttu-id="51b5e-145">在 AS 子句中，IntelliSense 僅支援本主題所列的陳述式和語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-145">In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.</span></span>|  
|[<span data-ttu-id="51b5e-146">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="51b5e-146">ALTER PROCEDURE</span></span>](/sql/t-sql/statements/alter-procedure-transact-sql)|<span data-ttu-id="51b5e-147">所有語法，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="51b5e-147">All syntax, with the following exceptions:</span></span><br /><br /> <span data-ttu-id="51b5e-148">EXTERNAL NAME 子句沒有任何 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="51b5e-148">There is no IntelliSense support for the EXTERNAL NAME clause.</span></span><br /><br /> <span data-ttu-id="51b5e-149">在 AS 子句中，IntelliSense 僅支援本主題所列的陳述式和語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-149">In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.</span></span>|  
|[<span data-ttu-id="51b5e-150">使用</span><span class="sxs-lookup"><span data-stu-id="51b5e-150">USE</span></span>](/sql/t-sql/language-elements/use-transact-sql)|<span data-ttu-id="51b5e-151">所有語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-151">All syntax.</span></span>|  
  
## <a name="intellisense-in-supported-statements"></a><span data-ttu-id="51b5e-152">支援陳述式中的 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="51b5e-152">IntelliSense in Supported Statements</span></span>  
 <span data-ttu-id="51b5e-153">當下列語法元素用於其中一個支援的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 陳述式時， [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢編輯器中的 IntelliSense 便支援這些元素：</span><span class="sxs-lookup"><span data-stu-id="51b5e-153">IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports the following syntax elements when they are used in one of the supported [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
-   <span data-ttu-id="51b5e-154">所有聯結類型，包括 APPLY</span><span class="sxs-lookup"><span data-stu-id="51b5e-154">All join types, including APPLY</span></span>  
  
-   <span data-ttu-id="51b5e-155">PIVOT 和 UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="51b5e-155">PIVOT and UNPIVOT</span></span>  
  
-   <span data-ttu-id="51b5e-156">下列資料庫物件的參考：</span><span class="sxs-lookup"><span data-stu-id="51b5e-156">References to the following database objects:</span></span>  
  
    -   <span data-ttu-id="51b5e-157">資料庫和結構描述</span><span class="sxs-lookup"><span data-stu-id="51b5e-157">Databases and schemas</span></span>  
  
    -   <span data-ttu-id="51b5e-158">資料表、檢視、資料表值函式和資料表運算式</span><span class="sxs-lookup"><span data-stu-id="51b5e-158">Tables, views, table-valued functions, and table expressions</span></span>  
  
    -   <span data-ttu-id="51b5e-159">資料行</span><span class="sxs-lookup"><span data-stu-id="51b5e-159">Columns</span></span>  
  
    -   <span data-ttu-id="51b5e-160">程序和程序參數</span><span class="sxs-lookup"><span data-stu-id="51b5e-160">Procedures and procedure parameters</span></span>  
  
    -   <span data-ttu-id="51b5e-161">純量函數和純量運算式</span><span class="sxs-lookup"><span data-stu-id="51b5e-161">Scalar functions and scalar expressions</span></span>  
  
    -   <span data-ttu-id="51b5e-162">區域變數</span><span class="sxs-lookup"><span data-stu-id="51b5e-162">Local variables</span></span>  
  
    -   <span data-ttu-id="51b5e-163">通用資料表運算式 (CTE)</span><span class="sxs-lookup"><span data-stu-id="51b5e-163">Common table expressions (CTE)</span></span>  
  
-   <span data-ttu-id="51b5e-164">只在指令碼或批次的 CREATE 或 ALTER 陳述式中參考，但是由於指令碼或批次尚未執行而不存在資料庫中的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="51b5e-164">Database objects that are referenced only in CREATE or ALTER statements in the script or batch, but which do not exist in the database because the script or batch has not yet been run.</span></span> <span data-ttu-id="51b5e-165">這些物件如下所示：</span><span class="sxs-lookup"><span data-stu-id="51b5e-165">These objects are as follows:</span></span>  
  
    -   <span data-ttu-id="51b5e-166">已經在指令碼或批次的 CREATE TABLE 或 CREATE PROCEDURE 陳述式中指定的資料表和程序。</span><span class="sxs-lookup"><span data-stu-id="51b5e-166">Tables and procedures that have been specified in a CREATE TABLE or CREATE PROCEDURE statement in the script or batch.</span></span>  
  
    -   <span data-ttu-id="51b5e-167">已經在指令碼或批次的 ALTER TABLE 或 ALTER PROCEDURE 陳述式中指定的資料表和程序變更。</span><span class="sxs-lookup"><span data-stu-id="51b5e-167">Changes to tables and procedures that have been specified in an ALTER TABLE or ALTER PROCEDURE statement in the script or batch.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51b5e-168">在執行 CREATE VIEW 陳述式之前，IntelliSense 不適用於 CREATE VIEW 陳述式的資料行。</span><span class="sxs-lookup"><span data-stu-id="51b5e-168">IntelliSense is not available for the columns of a CREATE VIEW statement until the CREATE VIEW statement has been executed.</span></span>  
  
 <span data-ttu-id="51b5e-169">當先前所列的元素用於 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式時，系統就不會針對它們提供 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="51b5e-169">IntelliSense is not provided for the previously listed elements when they are used in other [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="51b5e-170">例如，用於 SELECT 陳述式的資料行名稱具有 IntelliSense 支援，但用於 CREATE FUNCTION 陳述式的資料行則沒有。</span><span class="sxs-lookup"><span data-stu-id="51b5e-170">For example, there is IntelliSense support for column names that are used in a SELECT statement, but not for columns that are used in the CREATE FUNCTION statement.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="51b5e-171">範例</span><span class="sxs-lookup"><span data-stu-id="51b5e-171">Examples</span></span>  
 <span data-ttu-id="51b5e-172">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼或批次中， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中的 IntelliSense 僅支援本主題所列的陳述式和語法。</span><span class="sxs-lookup"><span data-stu-id="51b5e-172">Within a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or batch, IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports only the statements and syntax that are listed in this topic.</span></span> <span data-ttu-id="51b5e-173">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼範例將說明 IntelliSense 所支援的陳述式和語法元素。</span><span class="sxs-lookup"><span data-stu-id="51b5e-173">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] code examples show what statements and syntax elements IntelliSense supports.</span></span> <span data-ttu-id="51b5e-174">例如，在下列批次中，當 `SELECT` 陳述式只有本身的編碼時，IntelliSense 便適用於此陳述式，但是當 `SELECT` 包含在 `CREATE FUNCTION` 陳述式內部時，則不適用。</span><span class="sxs-lookup"><span data-stu-id="51b5e-174">For example, in the following batch, IntelliSense is available for the `SELECT` statement when it is coded by itself, but not when the `SELECT` is contained in a `CREATE FUNCTION` statement.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE Name LIKE N'Road-250%' and Color = N'Red';  
GO  
CREATE FUNCTION Production.ufn_Red250 ()  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT Name  
    FROM AdventureWorks2012.Production.Product  
    WHERE Name LIKE N'Road-250%'  
      AND Color = N'Red'  
);GO  
```  
  
 <span data-ttu-id="51b5e-175">這項功能也會套用至 CREATE PROCEDURE 或 ALTER PROCEDURE 陳述式之 AS 子句中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式集合。</span><span class="sxs-lookup"><span data-stu-id="51b5e-175">This functionality also applies to the sets of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the AS clause of a CREATE PROCEDURE or ALTER PROCEDURE statement.</span></span>  
  
 <span data-ttu-id="51b5e-176">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼或批次中，IntelliSense 支援已經在 CREATE 或 ALTER 陳述式中指定的物件。但是，由於陳述式尚未執行，所以這些物件不存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="51b5e-176">Within a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or batch, IntelliSense supports objects that have been specified in a CREATE or ALTER statement; however, these objects do not exist in the database because the statements have not been executed.</span></span> <span data-ttu-id="51b5e-177">例如，您可能會在查詢編輯器中輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="51b5e-177">For example, you might enter the following code in the Query Editor:</span></span>  
  
```  
USE MyTestDB;  
GO  
CREATE TABLE MyTable  
    (PrimaryKeyCol   INT PRIMARY KEY,  
    FirstNameCol      NVARCHAR(50),  
   LastNameCol       NVARCHAR(50));  
GO  
SELECT   
```  
  
 <span data-ttu-id="51b5e-178">在您輸入 `SELECT`之後，IntelliSense 就會列出 **[PrimaryKeyCol]**、 **[FirstNameCol]** 和 **[LastNameCol]** 當做選取清單中的可能元素，即使該指令碼尚未執行而且 `MyTable` 尚未存在 `MyTestDB`中也一樣。</span><span class="sxs-lookup"><span data-stu-id="51b5e-178">After you type `SELECT`, IntelliSense lists **PrimaryKeyCol**, **FirstNameCol**, and **LastNameCol** as possible elements in the select list, even if the script has not been executed and `MyTable` does not yet exist in `MyTestDB`.</span></span>  
  
  
