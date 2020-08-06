---
title: 記憶體內部 OLTP 的 Transact-SQL 支援 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: rothja
ms.author: jroth
ms.openlocfilehash: bf3708a258e3bb97231e45b10bea2c59351a06a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708337"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a><span data-ttu-id="448d9-102">記憶體中 OLTP 的 Transact-SQL 支援</span><span class="sxs-lookup"><span data-stu-id="448d9-102">Transact-SQL Support for In-Memory OLTP</span></span>
  <span data-ttu-id="448d9-103">您可以使用任何 Transact-SQL 查詢或 DML 陳述式 (SELECT、INSERT、UPDATE 或 DELETE)、特定陳述式及 SQL 模組 (例如預存程序、資料表值函數、純量函數、觸發程序和檢視表) 來存取記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="448d9-103">You can access memory-optimized tables using any Transact-SQL query or DML statement (SELECT, INSERT, UPDATE, or DELETE), ad hoc statement, and SQL module such as stored procedures, table-value functions, scalar functions, triggers, and views.</span></span> <span data-ttu-id="448d9-104">如需詳細資訊，請參閱[使用已解讀的 Transact-sql 存取記憶體優化資料表](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="448d9-104">For more information see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).</span></span>  
  
 <span data-ttu-id="448d9-105">只參考記憶體最佳化資料表的預存程序，可以原生方式編譯為機器碼，且通常能夠為解譯的 (以磁碟為基礎的) 預存程序，帶來顯著的效能提升。</span><span class="sxs-lookup"><span data-stu-id="448d9-105">Stored procedures that only reference memory-optimized tables can be natively compiled into machine code and typically provide significant performance gains over interpreted (disk-based) stored procedures.</span></span> <span data-ttu-id="448d9-106">若要最佳化記憶體最佳化資料表的存取，請使用原生編譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="448d9-106">For optimized access to memory-optimized tables use natively compiled stored procedures.</span></span> <span data-ttu-id="448d9-107">如需詳細資訊，請參閱[原生編譯的預存程序](natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="448d9-107">For more information, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="448d9-108">建立與修改資料庫物件 (DDL 陳述式) 前，需修改下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="448d9-108">When creating and modifying database objects (DDL statements), the following statements have been modified:</span></span>  
  
-   <span data-ttu-id="448d9-109">[ALTER Database File 和 Filegroup 選項 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (參閱 `MEMORY_OPTIMIZED_DATA`) </span><span class="sxs-lookup"><span data-stu-id="448d9-109">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (see `MEMORY_OPTIMIZED_DATA`)</span></span>  
  
-   <span data-ttu-id="448d9-110">[建立資料庫 &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) (參閱 `MEMORY_OPTIMIZED_DATA`) </span><span class="sxs-lookup"><span data-stu-id="448d9-110">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) (see `MEMORY_OPTIMIZED_DATA`)</span></span>  
  
-   <span data-ttu-id="448d9-111">[CREATE PROCEDURE &#40;transact-sql&#41;](/sql/t-sql/statements/create-procedure-transact-sql) (參閱、、 `NATIVE_COMPILATION` `SCHEMABINDING` `EXECUTE AS` 和 `BEGIN ATOMIC`) </span><span class="sxs-lookup"><span data-stu-id="448d9-111">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) (see `NATIVE_COMPILATION`, `SCHEMABINDING`, `EXECUTE AS`, and `BEGIN ATOMIC`)</span></span>  
  
-   <span data-ttu-id="448d9-112">[CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql) (參閱、、 `MEMORY_OPTIMIZED` 、 `DURABILITY` `BUCKET_COUNT` `INDEX` 和 `HASH`) </span><span class="sxs-lookup"><span data-stu-id="448d9-112">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) (see `MEMORY_OPTIMIZED`, `DURABILITY`, `BUCKET_COUNT`, `INDEX`, and `HASH`)</span></span>  
  
-   <span data-ttu-id="448d9-113">[CREATE TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql) (參閱、、 `MEMORY_OPTIMIZED` `BUCKET_COUNT` `INDEX` 和 `HASH`) </span><span class="sxs-lookup"><span data-stu-id="448d9-113">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) (see `MEMORY_OPTIMIZED`, `BUCKET_COUNT`, `INDEX`, and `HASH`)</span></span>  
  
-   <span data-ttu-id="448d9-114">[DECLARE @local_variable &#40;transact-sql&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (請參閱 `NULL`  |  `NOT NULL`) </span><span class="sxs-lookup"><span data-stu-id="448d9-114">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (see `NULL` | `NOT NULL`)</span></span>  
  
 <span data-ttu-id="448d9-115">記憶體最佳化資料表支援 `PRIMARY KEY` 和 `NOT NULL` 條件約束。</span><span class="sxs-lookup"><span data-stu-id="448d9-115">Memory-optimized tables support `PRIMARY KEY` and `NOT NULL` constraints.</span></span> <span data-ttu-id="448d9-116">如需執行不受支援之條件約束的詳細資訊，請參閱[遷移 Check 和 Foreign Key 條件約束](../../database-engine/migrating-check-and-foreign-key-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="448d9-116">For information on implementing unsupported constraints, see [Migrating Check and Foreign Key Constraints](../../database-engine/migrating-check-and-foreign-key-constraints.md).</span></span>  
  
 <span data-ttu-id="448d9-117">如需不支援功能的詳細資訊，請參閱[記憶體內部 OLTP 不支援 Transact-SQL 建構](transact-sql-constructs-not-supported-by-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="448d9-117">For information on unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="448d9-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="448d9-118">In This Section</span></span>  
  
-   [<span data-ttu-id="448d9-119">支援的資料類型</span><span class="sxs-lookup"><span data-stu-id="448d9-119">Supported Data Types</span></span>](supported-data-types-for-in-memory-oltp.md)  
  
-   [<span data-ttu-id="448d9-120">使用解譯的 Transact-SQL 存取記憶體最佳化的資料表</span><span class="sxs-lookup"><span data-stu-id="448d9-120">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [<span data-ttu-id="448d9-121">記憶體內部 OLTP 的系統檢視表、預存程序、DMV 和等候類型</span><span class="sxs-lookup"><span data-stu-id="448d9-121">System Views, Stored Procedures, DMVs and Wait Types for In-Memory OLTP</span></span>](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a><span data-ttu-id="448d9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="448d9-122">See Also</span></span>  
 <span data-ttu-id="448d9-123">[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="448d9-123">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 <span data-ttu-id="448d9-124">[原生編譯預存程序的移轉問題](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="448d9-124">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 <span data-ttu-id="448d9-125">[支援的 SQL Server 功能](unsupported-sql-server-features-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="448d9-125">[Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="448d9-126">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="448d9-126">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
