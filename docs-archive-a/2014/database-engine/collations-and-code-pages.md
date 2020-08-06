---
title: 定序和字碼頁 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c626dcac-0474-432d-acc0-cfa643345372
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab904771fa8ac4acf25a624cbf3e1139f7e96434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597364"
---
# <a name="collations-and-code-pages"></a><span data-ttu-id="3413b-102">定序和字碼頁</span><span class="sxs-lookup"><span data-stu-id="3413b-102">Collations and Code Pages</span></span>
  [!INCLUDE[hek_2](../includes/hek-2-md.md)] <span data-ttu-id="3413b-103">對於記憶體最佳化的資料表中 (var)Char 資料行支援的字碼頁以及用於索引和原生編譯預存程序中支援的定序有一些限制。</span><span class="sxs-lookup"><span data-stu-id="3413b-103">has restrictions on supported code pages for (var)char columns in memory-optimized tables and supported collations used in indexes and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="3413b-104">(var)char 值的字碼頁會判斷字元與資料表中儲存的位元組表示法之間的對應。</span><span class="sxs-lookup"><span data-stu-id="3413b-104">The code page for a (var)char value determines the mapping between characters and the byte representation that is stored in the table.</span></span> <span data-ttu-id="3413b-105">例如，在 Windows Latin 1 字碼頁 (也就是 1252；[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 預設值) 中，字元 'a' 對應到 0x61 位元組。</span><span class="sxs-lookup"><span data-stu-id="3413b-105">For example, with the Windows Latin 1 code page (1252; the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] default), the character 'a' corresponds to the byte 0x61.</span></span>  
  
 <span data-ttu-id="3413b-106">(var)char 值的字碼頁是由與這個值相關的定序所決定。</span><span class="sxs-lookup"><span data-stu-id="3413b-106">The code page of a (var)char value is determined by the collation associated with the value.</span></span> <span data-ttu-id="3413b-107">例如，SQL_Latin1_General_CP1_CI_AS 定序有相關聯的字碼頁 1252。</span><span class="sxs-lookup"><span data-stu-id="3413b-107">For example, the collation SQL_Latin1_General_CP1_CI_AS has the associated code page 1252.</span></span>  
  
 <span data-ttu-id="3413b-108">值的定序可能是從資料庫定序繼承而來，也可能是使用 COLLATE 關鍵字明確指定。</span><span class="sxs-lookup"><span data-stu-id="3413b-108">The collation of a value is either inherited from the database collation, or can be specified explicitly using the COLLATE keyword.</span></span> <span data-ttu-id="3413b-109">如果資料庫包含記憶體最佳化資料表或原生編譯預存程序，則資料庫定序無法變更。</span><span class="sxs-lookup"><span data-stu-id="3413b-109">Database collation cannot be changed if the database contains memory-optimized tables or natively compiled stored procedures.</span></span> <span data-ttu-id="3413b-110">下列範例會設定資料庫定序及建立資料表，該資料表的資料行有不同的定序。</span><span class="sxs-lookup"><span data-stu-id="3413b-110">The following example sets the database collation and creates a table, which has a column with a different collation.</span></span> <span data-ttu-id="3413b-111">資料庫使用不區分大小寫的 Latin 定序。</span><span class="sxs-lookup"><span data-stu-id="3413b-111">The database uses Latin case-insensitive collation.</span></span>  
  
 <span data-ttu-id="3413b-112">只有當索引使用 BIN2 定序時，才能建立於字串資料行中。</span><span class="sxs-lookup"><span data-stu-id="3413b-112">Indexes can only be created on string columns if they use a BIN2 collation.</span></span> <span data-ttu-id="3413b-113">LastName 變數會使用 BIN2 定序。</span><span class="sxs-lookup"><span data-stu-id="3413b-113">The LastName variable uses BIN2 collation.</span></span> <span data-ttu-id="3413b-114">FirstName 會使用資料庫預設值，也就是 CI_AS (不區分大小寫、區分腔調字)。</span><span class="sxs-lookup"><span data-stu-id="3413b-114">FirstName uses the database default, which is CI_AS (case-insensitive, accent-sensitive).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3413b-115">您無法針對不使用 BIN2 定序的索引字串資料行使用排序依據或群組依據。</span><span class="sxs-lookup"><span data-stu-id="3413b-115">You cannot use order by or group by on index string columns that do not use BIN2 collation.</span></span>  
  
```sql  
CREATE DATABASE IMOLTP  
  
ALTER DATABASE IMOLTP ADD FILEGROUP IMOLTP_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP ADD FILE( NAME = 'IMOLTP_mod' , FILENAME = 'c:\data\IMOLTP_mod') TO FILEGROUP IMOLTP_mod;  
--GO  
  
--  set the database collations  
ALTER DATABASE IMOLTP COLLATE Latin1_General_100_CI_AS  
GO  
  
--  
USE IMOLTP   
GO  
  
-- create a table with collation  
CREATE TABLE Employees (  
  EmployeeID int NOT NULL ,   
  LastName nvarchar(20) COLLATE Latin1_General_100_BIN2 NOT NULL INDEX IX_LastName NONCLUSTERED,   
  FirstName nvarchar(10) NOT NULL ,  
  CONSTRAINT PK_Employees PRIMARY KEY NONCLUSTERED HASH(EmployeeID)  WITH (BUCKET_COUNT=1024)  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_AND_DATA)  
GO  
```  
  
 <span data-ttu-id="3413b-116">記憶體最佳化的資料表和原生編譯的預存程序會套用以下限制：</span><span class="sxs-lookup"><span data-stu-id="3413b-116">The following restrictions apply to memory-optimized tables and natively compiled stored procedures:</span></span>  
  
-   <span data-ttu-id="3413b-117">記憶體最佳化資料表中的 (var)char 資料行必須使用字碼頁 1252 定序。</span><span class="sxs-lookup"><span data-stu-id="3413b-117">(var)char columns in memory-optimized tables must use code page 1252 collation.</span></span> <span data-ttu-id="3413b-118">這項限制並不適用於 n(var)char 資料行。</span><span class="sxs-lookup"><span data-stu-id="3413b-118">This restriction does not apply to n(var)char columns.</span></span> <span data-ttu-id="3413b-119">下列程式碼會擷取所有 1252 定序：</span><span class="sxs-lookup"><span data-stu-id="3413b-119">The following code retrieves all 1252 collations:</span></span>  
  
    ```sql  
    -- all supported collations for (var)char columns in memory-optimized tables  
    select * from sys.fn_helpcollations()  
    where collationproperty(name, 'codepage') = 1252;  
    ```  
  
     <span data-ttu-id="3413b-120">如果您需要儲存非拉丁字元，請使用 n(var)char 資料行。</span><span class="sxs-lookup"><span data-stu-id="3413b-120">If you need to store non-Latin characters, use n(var)char columns.</span></span>  
  
-   <span data-ttu-id="3413b-121">(n)(var)char 資料行上的索引只能使用 BIN2 定序來指定 (請參閱第一個範例)。</span><span class="sxs-lookup"><span data-stu-id="3413b-121">Indexes on (n)(var)char columns can only be specified with BIN2 collations (see the first example).</span></span> <span data-ttu-id="3413b-122">下列查詢會擷取所有支援的 BIN2 定序：</span><span class="sxs-lookup"><span data-stu-id="3413b-122">The following query retrieves all supported BIN2 collations:</span></span>  
  
    ```sql  
    -- all supported collations for indexes on memory-optimized tables and   
    -- comparison/sorting in natively compiled stored procedures  
    select * from sys.fn_helpcollations() where name like '%BIN2'  
    ```  
  
     <span data-ttu-id="3413b-123">如果您透過解譯的 [!INCLUDE[tsql](../includes/tsql-md.md)] 存取資料表，您可以使用 `COLLATE` 關鍵字來透過運算式或排序作業變更定序。</span><span class="sxs-lookup"><span data-stu-id="3413b-123">If you access the table through interpreted [!INCLUDE[tsql](../includes/tsql-md.md)], you can use the `COLLATE` keyword to change the collation with expressions or sort operations.</span></span> <span data-ttu-id="3413b-124">請參閱最後一個範例當做這個情況的範例。</span><span class="sxs-lookup"><span data-stu-id="3413b-124">See the last example for a sample of this.</span></span>  
  
-   <span data-ttu-id="3413b-125">如果資料庫定序不是字碼頁 1252 定序，則原生編譯預存程序無法使用 (var)char 類型的參數、區域變數或字串常數。</span><span class="sxs-lookup"><span data-stu-id="3413b-125">Natively compiled stored procedures cannot use parameters, local variables, or string constants of (var)char type if the database collation is not a code page 1252 collation.</span></span>  
  
-   <span data-ttu-id="3413b-126">原生編譯的預存程序中的所有運算式和排序作業都必須使用 BIN2 定序。</span><span class="sxs-lookup"><span data-stu-id="3413b-126">All expressions and sort operations inside natively compiled stored procedures must use BIN2 collations.</span></span> <span data-ttu-id="3413b-127">其含意為，所有的比較與排序作業都是根據字元的 Unicode 字碼指標 (二進位表示法)。</span><span class="sxs-lookup"><span data-stu-id="3413b-127">The implication is that all comparisons and sort operations are based on the Unicode code points of the characters (binary representations).</span></span> <span data-ttu-id="3413b-128">例如，所有排序都區分大小寫 ('Z' 排列在 'a' 之前)。</span><span class="sxs-lookup"><span data-stu-id="3413b-128">For example all sorting is case sensitive ('Z' comes before 'a').</span></span> <span data-ttu-id="3413b-129">如有需要，請使用解譯的 [!INCLUDE[tsql](../includes/tsql-md.md)] 進行不區分大小寫的排序和比較。</span><span class="sxs-lookup"><span data-stu-id="3413b-129">If necessary, use interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] for case-insensitive sorting and comparison.</span></span>  
  
-   <span data-ttu-id="3413b-130">原生編譯的預存程序中不支援 UTF-16 資料截斷。</span><span class="sxs-lookup"><span data-stu-id="3413b-130">Truncation of UTF-16 data is not supported inside natively compiled stored procedures.</span></span> <span data-ttu-id="3413b-131">這表示 n (var) char (*n*) 值無法轉換成類型 n (var) char (*i* ，*如果定*  <  序有) 屬性 *，則*_SC。</span><span class="sxs-lookup"><span data-stu-id="3413b-131">This means that n(var)char(*n*) values cannot be converted to type n(var)char(*i*), if *i* < *n*, if the collation has _SC property.</span></span> <span data-ttu-id="3413b-132">例如，以下範例不受支援：</span><span class="sxs-lookup"><span data-stu-id="3413b-132">For example, the following is not supported:</span></span>  
  
    ```sql  
    -- column definition using an _SC collation  
     c2 nvarchar(200) collate Latin1_General_100_CS_AS_SC not null   
    -- assignment to a smaller variable, requiring truncation  
     declare @c2 nvarchar(100) = '';  
     select @c2 = c2  
    ```  
  
     <span data-ttu-id="3413b-133">字串操作函數，例如 LEN、SUBSTRING、LTRIM 和具有 UTF-16 資料的 RTRIM，在原生方式編譯預存程序中都不受支援。</span><span class="sxs-lookup"><span data-stu-id="3413b-133">String manipulation functions, such as LEN, SUBSTRING, LTRIM, and RTRIM with UTF-16 data are not supported inside natively compiled stored procedures.</span></span> <span data-ttu-id="3413b-134">您無法對有 _SC 定序的 n(var)char 值使用這些字串操作函數。</span><span class="sxs-lookup"><span data-stu-id="3413b-134">You cannot use these string manipulation functions for n(var)char values that have an _SC collation.</span></span>  
  
     <span data-ttu-id="3413b-135">使用大到足以避免截斷的類型來宣告變數。</span><span class="sxs-lookup"><span data-stu-id="3413b-135">Declare variables using types that are large enough to avoid truncation.</span></span>  
  
 <span data-ttu-id="3413b-136">下列範例顯示 In-Memory OLTP 中定序限制的部分影響及因應措施。</span><span class="sxs-lookup"><span data-stu-id="3413b-136">The following example shows some of the implications and workarounds for the collation limitations in In-Memory OLTP.</span></span> <span data-ttu-id="3413b-137">此範例使用上面指定的 Employees 資料表。</span><span class="sxs-lookup"><span data-stu-id="3413b-137">The example uses the Employees table specified above.</span></span> <span data-ttu-id="3413b-138">這個範例會列出所有員工。</span><span class="sxs-lookup"><span data-stu-id="3413b-138">This sample list all employees .</span></span> <span data-ttu-id="3413b-139">請注意在 LastName 中，因為使用二進位定序，所以大寫名稱會排在小寫前面。</span><span class="sxs-lookup"><span data-stu-id="3413b-139">Notice that for LastName, due to the binary collation, the upper case names are sorted before lower case.</span></span> <span data-ttu-id="3413b-140">因此，'Thomas' 會排在 'nolan' 前面，因為大寫字母具有較低的字碼指標。</span><span class="sxs-lookup"><span data-stu-id="3413b-140">Therefore, 'Thomas' comes before 'nolan' because upper case characters have lower code points.</span></span> <span data-ttu-id="3413b-141">FirstName 具有不區分大小寫的定序。</span><span class="sxs-lookup"><span data-stu-id="3413b-141">FirstName has a case-insensitive collation.</span></span> <span data-ttu-id="3413b-142">因此，排序是根據英文字母，而不是字元的字碼指標。</span><span class="sxs-lookup"><span data-stu-id="3413b-142">So, sorting is by letter of the alphabet, not code point of the characters.</span></span>  
  
```sql  
-- insert a number of values  
INSERT Employees VALUES (1,'thomas', 'john')  
INSERT Employees VALUES (2,'Thomas', 'rupert')  
INSERT Employees VALUES (3,'Thomas', 'Jack')  
INSERT Employees VALUES (4,'Thomas', 'annie')  
INSERT Employees VALUES (5,'nolan', 'John')  
GO  
  
-- ===========  
SELECT EmployeeID, LastName, FirstName FROM Employees  
ORDER BY LastName, FirstName  
GO  
  
-- ===========  
-- specify collation: sorting uses case-insensitive collation, thus 'nolan' comes before 'Thomas'  
SELECT * FROM Employees  
ORDER BY LastName COLLATE Latin1_General_100_CI_AS, FirstName  
GO  
  
-- ===========  
-- retrieve employee by Name  
-- must use BIN2 collation for comparison in natively compiled stored procedures  
CREATE PROCEDURE usp_EmployeeByName @LastName nvarchar(20), @FirstName nvarchar(10)  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = N'us_english'  
)  
  SELECT EmployeeID, LastName, FirstName FROM dbo.Employees  
  WHERE   
    LastName = @LastName AND  
    FirstName COLLATE Latin1_General_100_BIN2 = @FirstName  
  
END  
GO  
  
-- this does not return any rows, as EmployeeID 1 has first name 'john', which is not equal to 'John' in a binary collation  
EXEC usp_EmployeeByName 'thomas', 'John'  
  
-- this retrieves EmployeeID 1  
EXEC usp_EmployeeByName 'thomas', 'john'  
```  
  
## <a name="see-also"></a><span data-ttu-id="3413b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3413b-143">See Also</span></span>  
 [<span data-ttu-id="3413b-144">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="3413b-144">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
