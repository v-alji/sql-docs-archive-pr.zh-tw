---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 10e187223a3f35b4b21ede6965e3c9efea2e30c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699631"
---
# <a name="mssqlserver_41368"></a><span data-ttu-id="f67e6-102">MSSQLSERVER_41368</span><span class="sxs-lookup"><span data-stu-id="f67e6-102">MSSQLSERVER_41368</span></span>
    
## <a name="details"></a><span data-ttu-id="f67e6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f67e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f67e6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f67e6-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="f67e6-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f67e6-105">Event ID</span></span>|<span data-ttu-id="f67e6-106">41368</span><span class="sxs-lookup"><span data-stu-id="f67e6-106">41368</span></span>|  
|<span data-ttu-id="f67e6-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f67e6-107">Event Source</span></span>|<span data-ttu-id="f67e6-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f67e6-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f67e6-109">元件</span><span class="sxs-lookup"><span data-stu-id="f67e6-109">Component</span></span>|<span data-ttu-id="f67e6-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f67e6-110">SQLEngine</span></span>|  
|<span data-ttu-id="f67e6-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f67e6-111">Symbolic Name</span></span>|<span data-ttu-id="f67e6-112">SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="f67e6-112">SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="f67e6-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f67e6-113">Message Text</span></span>|<span data-ttu-id="f67e6-114">只有自動認可交易才支援使用 READ COMMITTED 隔離等級來存取記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="f67e6-114">Accessing memory optimized tables using the READ COMMITTED isolation level is supported only for autocommit transactions.</span></span> <span data-ttu-id="f67e6-115">明確或隱含交易則不支援。</span><span class="sxs-lookup"><span data-stu-id="f67e6-115">It is not supported for explicit or implicit transactions.</span></span> <span data-ttu-id="f67e6-116">為使用資料表提示例如 WITH (SNAPSHOT) 的記憶體最佳化資料表，提供支援的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="f67e6-116">Provide a supported isolation level for the memory optimized table using a table hint, such as WITH (SNAPSHOT).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f67e6-117">說明</span><span class="sxs-lookup"><span data-stu-id="f67e6-117">Explanation</span></span>  
 <span data-ttu-id="f67e6-118">只有自動認可交易支援使用 READ COMMITTED 隔離等級存取記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="f67e6-118">Accessing memory-optimized tables using the READ COMMITTED isolation level is supported only for autocommit transactions.</span></span> <span data-ttu-id="f67e6-119">如需詳細資訊，請參閱 [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f67e6-119">For more information, see [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).</span></span>  
  
 <span data-ttu-id="f67e6-120">如果您存取記憶體最佳化的資料表是透過以 BEGIN TRANSACTION 啟動的明確交易，或是透過 IMPLICIT_TRANSACTIONS 設為 ON 的隱含交易，便不支援 READ COMMITTED 隔離等級。</span><span class="sxs-lookup"><span data-stu-id="f67e6-120">When accessing a memory-optimized table from an explicit transaction that was started with BEGIN TRANSACTION, or from an implicit transaction, if IMPLICIT_TRANSACTIONS is set to ON, the READ COMMITTED isolation level is not supported.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f67e6-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f67e6-121">User Action</span></span>  
 <span data-ttu-id="f67e6-122">透過明確或隱含 READ COMMITTED 交易存取記憶體最佳化的資料表時，請使用快照集 (SNAPSHOT) 存取資料表。</span><span class="sxs-lookup"><span data-stu-id="f67e6-122">When accessing a memory-optimized table from an explicit or implicit READ COMMITTED transaction, use SNAPSHOT to access the table.</span></span> <span data-ttu-id="f67e6-123">若要達成此目的，請使用資料表提示搭配 (快照集)  (如需詳細資訊，請參閱[具有記憶體優化資料表之交易隔離等級的方針](../in-memory-oltp/memory-optimized-tables.md)) 或將資料庫選項 MEMORY_OPTIMIZED_ELE加值稅E_TO_SNAPSHOT 設定為 ON (以取得詳細資訊，請參閱[ALTER database SET 選項 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)) 。</span><span class="sxs-lookup"><span data-stu-id="f67e6-123">This can be achieved by using the table hint WITH (SNAPSHOT) (for more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md)) or by setting the database option MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT to ON (for more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67e6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f67e6-124">See Also</span></span>  
 [<span data-ttu-id="f67e6-125">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="f67e6-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
