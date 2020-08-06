---
title: MSSQLSERVER_10507 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a80e48948c03b370c07742fabbb3cf8eb3e74315
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706542"
---
# <a name="mssqlserver_10507"></a><span data-ttu-id="7fda3-102">MSSQLSERVER_10507</span><span class="sxs-lookup"><span data-stu-id="7fda3-102">MSSQLSERVER_10507</span></span>
    
## <a name="details"></a><span data-ttu-id="7fda3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7fda3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7fda3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7fda3-104">Product Name</span></span>|<span data-ttu-id="7fda3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7fda3-105">SQL Server</span></span>|  
|<span data-ttu-id="7fda3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7fda3-106">Event ID</span></span>|<span data-ttu-id="7fda3-107">10507</span><span class="sxs-lookup"><span data-stu-id="7fda3-107">10507</span></span>|  
|<span data-ttu-id="7fda3-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7fda3-108">Event Source</span></span>|<span data-ttu-id="7fda3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7fda3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7fda3-110">元件</span><span class="sxs-lookup"><span data-stu-id="7fda3-110">Component</span></span>|<span data-ttu-id="7fda3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7fda3-111">SQLEngine</span></span>|  
|<span data-ttu-id="7fda3-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7fda3-112">Symbolic Name</span></span>|<span data-ttu-id="7fda3-113">PG_STMT_DOES_NOT_MATCH</span><span class="sxs-lookup"><span data-stu-id="7fda3-113">PG_STMT_DOES_NOT_MATCH</span></span>|  
|<span data-ttu-id="7fda3-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7fda3-114">Message Text</span></span>|<span data-ttu-id="7fda3-115">無法建立計畫指南 '%.\*ls'，因為 `@stmt` 和 `@module_or_batch` 或是 `@plan_handle` 和 `@statement_start_offset` 所指定的陳述式不符合指定的模組或批次中的任何陳述式。</span><span class="sxs-lookup"><span data-stu-id="7fda3-115">Cannot create plan guide '%.\*ls' because the statement specified by `@stmt` and `@module_or_batch`, or by `@plan_handle` and `@statement_start_offset`, does not match any statement in the specified module or batch.</span></span> <span data-ttu-id="7fda3-116">請將值修改為與模組或批次中的陳述式相符。</span><span class="sxs-lookup"><span data-stu-id="7fda3-116">Modify the values to match a statement in the module or batch.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7fda3-117">說明</span><span class="sxs-lookup"><span data-stu-id="7fda3-117">Explanation</span></span>  
 <span data-ttu-id="7fda3-118">指定之模組或批次中的陳述式無法與指定的陳述式或陳述式位移值相符。</span><span class="sxs-lookup"><span data-stu-id="7fda3-118">A statement in the specified module or batch could not be matched to the specified statement or statement offset value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7fda3-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7fda3-119">User Action</span></span>  
 <span data-ttu-id="7fda3-120">請將指定的參數值修改為與模組或批次中的陳述式相符。</span><span class="sxs-lookup"><span data-stu-id="7fda3-120">Modify the specified parameter values to match a statement in the module or batch.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fda3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fda3-121">See Also</span></span>  
 <span data-ttu-id="7fda3-122">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="7fda3-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="7fda3-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7fda3-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="7fda3-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7fda3-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
