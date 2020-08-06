---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 00d08f4555f38b61661a917ba94c023f9dd6c4a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702958"
---
# <a name="mssqlserver_10536"></a><span data-ttu-id="c451d-102">MSSQLSERVER_10536</span><span class="sxs-lookup"><span data-stu-id="c451d-102">MSSQLSERVER_10536</span></span>
    
## <a name="details"></a><span data-ttu-id="c451d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c451d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c451d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c451d-104">Product Name</span></span>|<span data-ttu-id="c451d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c451d-105">SQL Server</span></span>|  
|<span data-ttu-id="c451d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c451d-106">Event ID</span></span>|<span data-ttu-id="c451d-107">10536</span><span class="sxs-lookup"><span data-stu-id="c451d-107">10536</span></span>|  
|<span data-ttu-id="c451d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c451d-108">Event Source</span></span>|<span data-ttu-id="c451d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c451d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c451d-110">元件</span><span class="sxs-lookup"><span data-stu-id="c451d-110">Component</span></span>|<span data-ttu-id="c451d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c451d-111">SQLEngine</span></span>|  
|<span data-ttu-id="c451d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c451d-112">Symbolic Name</span></span>|<span data-ttu-id="c451d-113">PG_TOO_MANY_STMTS</span><span class="sxs-lookup"><span data-stu-id="c451d-113">PG_TOO_MANY_STMTS</span></span>|  
|<span data-ttu-id="c451d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c451d-114">Message Text</span></span>|<span data-ttu-id="c451d-115">無法建立計畫指南 '%.\*ls'，因為指定的 `@plan_handle` 所對應的批次或模組中包含超過 1000 個適合的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c451d-115">Cannot create plan guide '%.\*ls' because the batch or module corresponding to the specified `@plan_handle` contains more than 1000 eligible statements.</span></span> <span data-ttu-id="c451d-116">請為批次或模組中的每個陳述式分別指定 `statement_start_offset` 值，以各建立一個計畫指南。</span><span class="sxs-lookup"><span data-stu-id="c451d-116">Create a plan guide for each statement in the batch or module by specifying a `statement_start_offset` value for each statement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c451d-117">說明</span><span class="sxs-lookup"><span data-stu-id="c451d-117">Explanation</span></span>  
 <span data-ttu-id="c451d-118">指定的 `@plan_handle` 所對應的批次或模組中包含超過 1000 個適合的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c451d-118">The batch or module corresponding to the specified `@plan_handle` contains more than 1000 eligible statements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c451d-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c451d-119">User Action</span></span>  
 <span data-ttu-id="c451d-120">請為批次或模組中的每個陳述式分別指定 `statement_start_offset` 值，以各建立一個計畫指南。</span><span class="sxs-lookup"><span data-stu-id="c451d-120">Create a plan guide for each statement in the batch or module by specifying a `statement_start_offset` value for each statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c451d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c451d-121">See Also</span></span>  
 <span data-ttu-id="c451d-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c451d-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="c451d-123">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="c451d-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="c451d-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c451d-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
