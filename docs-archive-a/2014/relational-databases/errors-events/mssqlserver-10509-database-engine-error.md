---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73194c7da553bf27acb78d8c4e7d71bc93f457d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708421"
---
# <a name="mssqlserver_10509"></a><span data-ttu-id="aa1cc-102">MSSQLSERVER_10509</span><span class="sxs-lookup"><span data-stu-id="aa1cc-102">MSSQLSERVER_10509</span></span>
    
## <a name="details"></a><span data-ttu-id="aa1cc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aa1cc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa1cc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aa1cc-104">Product Name</span></span>|<span data-ttu-id="aa1cc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aa1cc-105">SQL Server</span></span>|  
|<span data-ttu-id="aa1cc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aa1cc-106">Event ID</span></span>|<span data-ttu-id="aa1cc-107">10509</span><span class="sxs-lookup"><span data-stu-id="aa1cc-107">10509</span></span>|  
|<span data-ttu-id="aa1cc-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aa1cc-108">Event Source</span></span>|<span data-ttu-id="aa1cc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aa1cc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aa1cc-110">元件</span><span class="sxs-lookup"><span data-stu-id="aa1cc-110">Component</span></span>|<span data-ttu-id="aa1cc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aa1cc-111">SQLEngine</span></span>|  
|<span data-ttu-id="aa1cc-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aa1cc-112">Symbolic Name</span></span>|<span data-ttu-id="aa1cc-113">PG_INVALID_STMT</span><span class="sxs-lookup"><span data-stu-id="aa1cc-113">PG_INVALID_STMT</span></span>|  
|<span data-ttu-id="aa1cc-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aa1cc-114">Message Text</span></span>|<span data-ttu-id="aa1cc-115">無法建立計畫指南 '%.\*ls'，因為 `@stmt` 或 `@statement_start_offset` 所指定的陳述式中含有語法錯誤或不適用於計畫指南。</span><span class="sxs-lookup"><span data-stu-id="aa1cc-115">Cannot create plan guide '%.\*ls' because the statement specified by `@stmt` or `@statement_start_offset` either contains a syntax error or is ineligible for use in a plan guide.</span></span> <span data-ttu-id="aa1cc-116">請提供單一有效 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，或批次中陳述式的有效開始位置。</span><span class="sxs-lookup"><span data-stu-id="aa1cc-116">Provide a single valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a valid starting position of the statement within the batch.</span></span> <span data-ttu-id="aa1cc-117">若要取得有效開始位置，請查詢 sys.dm_exec_query_stats 動態管理函數中的 statement_start_offset 資料行。</span><span class="sxs-lookup"><span data-stu-id="aa1cc-117">To obtain a valid starting position, query the statement_start_offset column in the sys.dm_exec_query_stats dynamic management function.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aa1cc-118">說明</span><span class="sxs-lookup"><span data-stu-id="aa1cc-118">Explanation</span></span>  
 <span data-ttu-id="aa1cc-119">`@stmt` 或 `@statement_start_offset` 所指定的陳述式中含有語法錯誤或不適用於計畫指南。</span><span class="sxs-lookup"><span data-stu-id="aa1cc-119">The statement specified by `@stmt` or `@statement_start_offset` either contains a syntax error or is ineligible for use in a plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aa1cc-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aa1cc-120">User Action</span></span>  
 <span data-ttu-id="aa1cc-121">請提供單一有效 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，或批次中陳述式的有效開始位置。</span><span class="sxs-lookup"><span data-stu-id="aa1cc-121">Provide a single valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a valid starting position of the statement within the batch.</span></span> <span data-ttu-id="aa1cc-122">若要取得有效開始位置，請查詢 sys.dm_exec_query_stats 動態管理函數中的 statement_start_offset 資料行。</span><span class="sxs-lookup"><span data-stu-id="aa1cc-122">To obtain a valid starting position, query the statement_start_offset column in the sys.dm_exec_query_stats dynamic management function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa1cc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa1cc-123">See Also</span></span>  
 <span data-ttu-id="aa1cc-124">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aa1cc-124">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="aa1cc-125">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="aa1cc-125">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="aa1cc-126">[dm_exec_query_stats &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aa1cc-126">[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) </span></span>  
 [<span data-ttu-id="aa1cc-127">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aa1cc-127">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
