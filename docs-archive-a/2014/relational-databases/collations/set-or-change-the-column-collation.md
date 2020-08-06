---
title: 設定或變更資料行定序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8211569b6ce83faaec043e5eb527a60f0ddab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606901"
---
# <a name="set-or-change-the-column-collation"></a><span data-ttu-id="673d1-102">設定或變更資料行定序</span><span class="sxs-lookup"><span data-stu-id="673d1-102">Set or Change the Column Collation</span></span>
  <span data-ttu-id="673d1-103">您可以透過為資料表中特定資料行指定不同的定序並使用下列其中一種方法，覆寫 `char`、`varchar`、`text`、`nchar`、`nvarchar` 和 `ntext` 資料的資料庫定序：</span><span class="sxs-lookup"><span data-stu-id="673d1-103">You can override the database collation for `char`, `varchar`, `text`, `nchar`, `nvarchar`, and `ntext` data by specifying a different collation for a specific column of a table and using one of the following:</span></span>  
  
-   <span data-ttu-id="673d1-104">[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 和 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)的 COLLATE 子句。</span><span class="sxs-lookup"><span data-stu-id="673d1-104">The COLLATE clause of [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) and [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span> <span data-ttu-id="673d1-105">例如：</span><span class="sxs-lookup"><span data-stu-id="673d1-105">For example:</span></span>  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="673d1-106">.</span><span class="sxs-lookup"><span data-stu-id="673d1-106">.</span></span> <span data-ttu-id="673d1-107">如需詳細資訊，請參閱 [定序與 Unicode 支援](collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="673d1-107">For more information, [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="673d1-108">`Column.Collation`在管理物件中使用屬性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) 。</span><span class="sxs-lookup"><span data-stu-id="673d1-108">Using the `Column.Collation` property in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="673d1-109">如果目前下列任何一個項目參考資料行定序的話，就無法變更其定序：</span><span class="sxs-lookup"><span data-stu-id="673d1-109">You cannot change the collation of a column that is currently referenced by any one of the following:</span></span>  
  
-   <span data-ttu-id="673d1-110">計算資料行</span><span class="sxs-lookup"><span data-stu-id="673d1-110">A computed column</span></span>  
  
-   <span data-ttu-id="673d1-111">索引</span><span class="sxs-lookup"><span data-stu-id="673d1-111">An index</span></span>  
  
-   <span data-ttu-id="673d1-112">散發統計資料，不論是自動產生或由 CREATE STATISTICS 陳述式產生</span><span class="sxs-lookup"><span data-stu-id="673d1-112">Distribution statistics, either generated automatically or by the CREATE STATISTICS statement</span></span>  
  
-   <span data-ttu-id="673d1-113">CHECK 條件約束</span><span class="sxs-lookup"><span data-stu-id="673d1-113">A CHECK constraint</span></span>  
  
-   <span data-ttu-id="673d1-114">FOREIGN KEY 條件約束</span><span class="sxs-lookup"><span data-stu-id="673d1-114">A FOREIGN KEY constraint</span></span>  
  
 <span data-ttu-id="673d1-115">當您使用 **tempdb**時， [COLLATE](/sql/t-sql/statements/collations) 子句會包含 *database_default* 選項，將暫存資料表中的資料行指定為使用連線的目前使用者資料庫預設定序，而非 **tempdb**的定序。</span><span class="sxs-lookup"><span data-stu-id="673d1-115">When you work with **tempdb**, the [COLLATE](/sql/t-sql/statements/collations) clause includes a *database_default* option to specify that a column in a temporary table uses the collation default of the current user database for the connection instead of the collation of **tempdb**.</span></span>  
  
## <a name="collations-and-text-columns"></a><span data-ttu-id="673d1-116">定序與 text 資料行</span><span class="sxs-lookup"><span data-stu-id="673d1-116">Collations and text Columns</span></span>  
 <span data-ttu-id="673d1-117">您可以插入或更新 `text` 資料行的值，該資料行定序與資料庫預設定序的字碼頁不同。</span><span class="sxs-lookup"><span data-stu-id="673d1-117">You can insert or update values in a `text` column whose collation is different from the code page of the default collation of the database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="673d1-118">以隱含方式將該值轉換為資料行定序。</span><span class="sxs-lookup"><span data-stu-id="673d1-118">implicitly converts the values to the collation of the column.</span></span>  
  
## <a name="collations-and-tempdb"></a><span data-ttu-id="673d1-119">定序與 tempdb</span><span class="sxs-lookup"><span data-stu-id="673d1-119">Collations and tempdb</span></span>  
 <span data-ttu-id="673d1-120">**tempdb** 資料庫在每次 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動時建置，且預設定序與 **model** 資料庫相同。</span><span class="sxs-lookup"><span data-stu-id="673d1-120">The **tempdb** database is built every time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started and has the same default collation as the **model** database.</span></span> <span data-ttu-id="673d1-121">通常與執行個體的預設定序相同。</span><span class="sxs-lookup"><span data-stu-id="673d1-121">This is typically the same as the default collation of the instance.</span></span> <span data-ttu-id="673d1-122">如果建立使用者資料庫，並指定與 **model**不同的預設定序，使用者資料庫的預設定序就會與 **tempdb**不同。</span><span class="sxs-lookup"><span data-stu-id="673d1-122">If you create a user database and specify a different default collation than **model**, the user database has a different default collation than **tempdb**.</span></span> <span data-ttu-id="673d1-123">所有暫存預存程序或暫存資料表會在 **tempdb**中建立及儲存。</span><span class="sxs-lookup"><span data-stu-id="673d1-123">All temporary stored procedures or temporary tables are created and stored in **tempdb**.</span></span> <span data-ttu-id="673d1-124">這表示暫存資料表中所有隱含的資料行，與暫存預存程序中所有可強迫的常數、變數與參數，都會與建在永久資料表和預存程序中的同等物件具有不同的定序。</span><span class="sxs-lookup"><span data-stu-id="673d1-124">This means that all implicit columns in temporary tables and all coercible-default constants, variables, and parameters in temporary stored procedures have collations that are different from comparable objects created in permanent tables and stored procedures.</span></span>  
  
 <span data-ttu-id="673d1-125">這將造成使用者自訂資料庫與系統資料庫物件之間的定序不相符。</span><span class="sxs-lookup"><span data-stu-id="673d1-125">This could lead to problems with a mismatch in collations between user-defined databases and system database objects.</span></span> <span data-ttu-id="673d1-126">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體使用 Latin1_General_CS_AS 定序，而您執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="673d1-126">For example, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the Latin1_General_CS_AS collation and you execute the following statements:</span></span>  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 <span data-ttu-id="673d1-127">在此系統中， **tempdb** 資料庫使用 Latin1_General_CS_AS 定序與字碼頁 1252，而 `TestDB` 和 `TestPermTab.Col1` 使用 `Estonian_CS_AS` 定序與字碼頁 1257。</span><span class="sxs-lookup"><span data-stu-id="673d1-127">In this system, the **tempdb** database uses the Latin1_General_CS_AS collation with code page 1252, and `TestDB` and `TestPermTab.Col1` use the `Estonian_CS_AS` collation with code page 1257.</span></span> <span data-ttu-id="673d1-128">例如：</span><span class="sxs-lookup"><span data-stu-id="673d1-128">For example:</span></span>  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 <span data-ttu-id="673d1-129">承上例， **tempdb** 資料庫使用 Latin1_General_CS_AS 定序，而 `TestDB` 和 `TestTab.Col1` 則使用 `Estonian_CS_AS` 定序。</span><span class="sxs-lookup"><span data-stu-id="673d1-129">With the previous example, the **tempdb** database uses the Latin1_General_CS_AS collation, and `TestDB` and `TestTab.Col1` use the `Estonian_CS_AS` collation.</span></span> <span data-ttu-id="673d1-130">例如：</span><span class="sxs-lookup"><span data-stu-id="673d1-130">For example:</span></span>  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 <span data-ttu-id="673d1-131">因為 **tempdb** 使用預設伺服器定序，而 `TestPermTab.Col1` 使用不同的定序，所以 SQL Server 會傳回此錯誤訊息：「無法解析等於作業中，'Latin1_General_CI_AS_KS_WS' 與 'Estonian_CS_AS' 之間的定序衝突」。</span><span class="sxs-lookup"><span data-stu-id="673d1-131">Because **tempdb** uses the default server collation and `TestPermTab.Col1` uses a different collation, SQL Server returns this error: "Cannot resolve collation conflict between 'Latin1_General_CI_AS_KS_WS' and 'Estonian_CS_AS' in equal to operation."</span></span>  
  
 <span data-ttu-id="673d1-132">為避免此錯誤，您可以使用以下任一種替代方法：</span><span class="sxs-lookup"><span data-stu-id="673d1-132">To prevent the error, you can use one of the following alternatives:</span></span>  
  
-   <span data-ttu-id="673d1-133">指定暫存資料表的資料行使用使用者資料庫的預設定序，而不使用 **tempdb**的預設定序。</span><span class="sxs-lookup"><span data-stu-id="673d1-133">Specify that the temporary table column use the default collation of the user database, not **tempdb**.</span></span> <span data-ttu-id="673d1-134">這使得暫存資料表可配合多個資料庫中格式類似的資料表 (如果系統有這樣的需求)。</span><span class="sxs-lookup"><span data-stu-id="673d1-134">This enables the temporary table to work with similarly formatted tables in multiple databases, if that is required of your system.</span></span>  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   <span data-ttu-id="673d1-135">為 `#TestTempTab` 資料行指定正確的定序：</span><span class="sxs-lookup"><span data-stu-id="673d1-135">Specify the correct collation for the `#TestTempTab` column:</span></span>  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="673d1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="673d1-136">See Also</span></span>  
 <span data-ttu-id="673d1-137">[設定或變更伺服器定序](set-or-change-the-server-collation.md) </span><span class="sxs-lookup"><span data-stu-id="673d1-137">[Set or Change the Server Collation](set-or-change-the-server-collation.md) </span></span>  
 <span data-ttu-id="673d1-138">[設定或變更資料庫定序](set-or-change-the-database-collation.md) </span><span class="sxs-lookup"><span data-stu-id="673d1-138">[Set or Change the Database Collation](set-or-change-the-database-collation.md) </span></span>  
 [<span data-ttu-id="673d1-139">定序與 Unicode 支援</span><span class="sxs-lookup"><span data-stu-id="673d1-139">Collation and Unicode Support</span></span>](collation-and-unicode-support.md)  
  
  
