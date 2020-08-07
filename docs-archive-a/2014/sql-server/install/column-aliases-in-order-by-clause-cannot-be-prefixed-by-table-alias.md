---
title: ORDER BY 子句中的資料行別名不能以資料表別名作為前置詞 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 44333d778753a2f8761d32d181681b798e3bc409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595495"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a><span data-ttu-id="b362a-102">ORDER BY 子句中資料行別名的前置詞不可以是資料表別名</span><span class="sxs-lookup"><span data-stu-id="b362a-102">Column aliases in ORDER BY clause cannot be prefixed by table alias</span></span>
  <span data-ttu-id="b362a-103">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本中，ORDER BY 子句中資料行別名的前置詞不可以是資料表別名。</span><span class="sxs-lookup"><span data-stu-id="b362a-103">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later, column aliases in the ORDER BY clause cannot be prefixed by the table alias.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b362a-104">元件</span><span class="sxs-lookup"><span data-stu-id="b362a-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b362a-105">描述</span><span class="sxs-lookup"><span data-stu-id="b362a-105">Description</span></span>  
 <span data-ttu-id="b362a-106">例如，下列查詢可在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中執行，但在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中則會傳回錯誤：</span><span class="sxs-lookup"><span data-stu-id="b362a-106">For example, the following query executes in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], but returns an error in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 <span data-ttu-id="b362a-107">[!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] 不會將 `p.l` 子句中的 `ORDER BY` 比對成資料表中的有效資料行。</span><span class="sxs-lookup"><span data-stu-id="b362a-107">The [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] does not match `p.l` in the `ORDER BY` clause to a valid column in the table.</span></span>  
  
### <a name="exception"></a><span data-ttu-id="b362a-108">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b362a-108">Exception</span></span>  
 <span data-ttu-id="b362a-109">如果在 ORDER BY 子句中指定的前置資料行別名是指定資料表中的有效資料行名稱，則查詢會在無錯誤的情況下執行。但是，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，陳述式的語意可能不同。</span><span class="sxs-lookup"><span data-stu-id="b362a-109">If the prefixed column alias that is specified in the ORDER BY clause is a valid column name in the specified table, the query executes without error; in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the semantics of the statement might be different.</span></span> <span data-ttu-id="b362a-110">例如，在下列陳述式中指定的資料行別名 (`id`) 是 `sysobjects` 資料表中的有效資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="b362a-110">For example, the column alias (`id`) specified in the following statement is a valid column name in the `sysobjects` table.</span></span> <span data-ttu-id="b362a-111">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，當該陳述式執行時，`CAST` 作業會在排序結果集之後執行。</span><span class="sxs-lookup"><span data-stu-id="b362a-111">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], when the statement executes, the `CAST` operation is performed after the result set is sorted.</span></span> <span data-ttu-id="b362a-112">這表示 `name` 資料行會用於排序作業中。</span><span class="sxs-lookup"><span data-stu-id="b362a-112">This means the `name` column is used in the sort operation.</span></span> <span data-ttu-id="b362a-113">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中，`CAST` 作業會在排序作業之前進行。</span><span class="sxs-lookup"><span data-stu-id="b362a-113">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the `CAST` operation occurs before the sort operation.</span></span> <span data-ttu-id="b362a-114">這表示 `id` 資料行會用於排序作業中，並以非預期的順序傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="b362a-114">This means the `id` column in the table is used in the sort operation and returns the result set in an unexpected order.</span></span>  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a><span data-ttu-id="b362a-115">更正動作</span><span class="sxs-lookup"><span data-stu-id="b362a-115">Corrective Action</span></span>  
 <span data-ttu-id="b362a-116">請使用下列其中一種方式，修改在 ORDER BY 子句中使用以資料表別名當做前置詞之資料行別名的查詢：</span><span class="sxs-lookup"><span data-stu-id="b362a-116">Modify queries that use column aliases prefixed by table aliases in the ORDER BY clause in either of the following ways:</span></span>  
  
-   <span data-ttu-id="b362a-117">請盡量不要為 ORDER BY 子句中的資料行別名加上前置詞。</span><span class="sxs-lookup"><span data-stu-id="b362a-117">Do not prefix the column alias in the ORDER BY clause, if possible.</span></span>  
  
-   <span data-ttu-id="b362a-118">使用資料行名稱物來取代資料行別名。</span><span class="sxs-lookup"><span data-stu-id="b362a-118">Replace the column alias with the column name.</span></span>  
  
 <span data-ttu-id="b362a-119">例如，在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中，下列兩個查詢會在無錯誤的情況下執行：</span><span class="sxs-lookup"><span data-stu-id="b362a-119">For example, both of the following queries execute without error in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a><span data-ttu-id="b362a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b362a-120">See Also</span></span>  
 <span data-ttu-id="b362a-121">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b362a-121">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b362a-122">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="b362a-122">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
