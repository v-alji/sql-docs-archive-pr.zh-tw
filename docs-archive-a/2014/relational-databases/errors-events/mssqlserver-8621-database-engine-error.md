---
title: MSSQLSERVER_8621 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48c36cf936475e3deea37a172c7dc59f88d0a31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597859"
---
# <a name="mssqlserver_8621"></a><span data-ttu-id="78791-102">MSSQLSERVER_8621</span><span class="sxs-lookup"><span data-stu-id="78791-102">MSSQLSERVER_8621</span></span>
    
## <a name="details"></a><span data-ttu-id="78791-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="78791-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78791-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="78791-104">Product Name</span></span>|<span data-ttu-id="78791-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="78791-105">SQL Server</span></span>|  
|<span data-ttu-id="78791-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="78791-106">Event ID</span></span>|<span data-ttu-id="78791-107">8621</span><span class="sxs-lookup"><span data-stu-id="78791-107">8621</span></span>|  
|<span data-ttu-id="78791-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="78791-108">Event Source</span></span>|<span data-ttu-id="78791-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="78791-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="78791-110">元件</span><span class="sxs-lookup"><span data-stu-id="78791-110">Component</span></span>|<span data-ttu-id="78791-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="78791-111">SQLEngine</span></span>|  
|<span data-ttu-id="78791-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="78791-112">Symbolic Name</span></span>|<span data-ttu-id="78791-113">OPTIMIZER_STACK_OVERFLOW_ERR</span><span class="sxs-lookup"><span data-stu-id="78791-113">OPTIMIZER_STACK_OVERFLOW_ERR</span></span>|  
|<span data-ttu-id="78791-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="78791-114">Message Text</span></span>|<span data-ttu-id="78791-115">查詢處理器在查詢最佳化期間已用完堆疊空間。</span><span class="sxs-lookup"><span data-stu-id="78791-115">The query processor ran out of stack space during query optimization.</span></span> <span data-ttu-id="78791-116">請簡化查詢。</span><span class="sxs-lookup"><span data-stu-id="78791-116">Please simplify the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="78791-117">說明</span><span class="sxs-lookup"><span data-stu-id="78791-117">Explanation</span></span>  
 <span data-ttu-id="78791-118">展開的查詢大小是造成這項錯誤最有可能的原因。</span><span class="sxs-lookup"><span data-stu-id="78791-118">The size of the expanded query is the most likely cause of the error.</span></span> <span data-ttu-id="78791-119">展開的查詢會取代原始查詢中其參照的每個檢視、計算資料行、[!INCLUDE[tsql](../../includes/tsql-md.md)] 函數與一般資料表運算式的定義，以及串聯式動作，例如更新次要索引、檢視和觸發程序。</span><span class="sxs-lookup"><span data-stu-id="78791-119">The expanded query substitutes into the original query the definitions of each of the views, computed columns, [!INCLUDE[tsql](../../includes/tsql-md.md)] functions, and common table expressions it references, as well as cascading actions like updating secondary indexes, views, and triggers.</span></span>  
  
 <span data-ttu-id="78791-120">最有可能的情況是查詢的某個維度很大；例如，檢視定義參考的資料表數目，或是純量運算式非常大。</span><span class="sxs-lookup"><span data-stu-id="78791-120">Most likely the query is large in some dimension; for example, the number of tables referenced by view definitions, or a very large scalar expression.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="78791-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="78791-121">User Action</span></span>  
 <span data-ttu-id="78791-122">依據最大的維度，將該查詢分割成多項查詢，藉以簡化查詢。</span><span class="sxs-lookup"><span data-stu-id="78791-122">Simplify the query by breaking the query into multiple queries along the largest dimension.</span></span> <span data-ttu-id="78791-123">請先移除實際上不需要的任何查詢元素，然後嘗試新增暫存資料表，並將查詢分割成兩項查詢。</span><span class="sxs-lookup"><span data-stu-id="78791-123">First remove any query elements that are not really necessary, then try adding a temp table and splitting the query in two.</span></span>  <span data-ttu-id="78791-124">只將查詢的某個部分移到子查詢、函數或一般資料表運算式並不夠，因為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 編譯器會重新合併這些元素。</span><span class="sxs-lookup"><span data-stu-id="78791-124">Merely moving a part of the query to a subquery, function, or common table expression is insufficient because they get recombined by the [!INCLUDE[tsql](../../includes/tsql-md.md)] compiler.</span></span>  
  
  
