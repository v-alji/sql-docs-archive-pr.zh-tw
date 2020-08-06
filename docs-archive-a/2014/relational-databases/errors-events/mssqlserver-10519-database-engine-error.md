---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ec584649842f787b1de9d2ea6d161aea6970250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705153"
---
# <a name="mssqlserver_10519"></a><span data-ttu-id="528ae-102">MSSQLSERVER_10519</span><span class="sxs-lookup"><span data-stu-id="528ae-102">MSSQLSERVER_10519</span></span>
    
## <a name="details"></a><span data-ttu-id="528ae-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="528ae-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="528ae-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="528ae-104">Product Name</span></span>|<span data-ttu-id="528ae-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="528ae-105">SQL Server</span></span>|  
|<span data-ttu-id="528ae-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="528ae-106">Event ID</span></span>|<span data-ttu-id="528ae-107">10519</span><span class="sxs-lookup"><span data-stu-id="528ae-107">10519</span></span>|  
|<span data-ttu-id="528ae-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="528ae-108">Event Source</span></span>|<span data-ttu-id="528ae-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="528ae-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="528ae-110">元件</span><span class="sxs-lookup"><span data-stu-id="528ae-110">Component</span></span>|<span data-ttu-id="528ae-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="528ae-111">SQLEngine</span></span>|  
|<span data-ttu-id="528ae-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="528ae-112">Symbolic Name</span></span>|<span data-ttu-id="528ae-113">PG_INCOMPATIBLE_STMT_AND_HINTS</span><span class="sxs-lookup"><span data-stu-id="528ae-113">PG_INCOMPATIBLE_STMT_AND_HINTS</span></span>|  
|<span data-ttu-id="528ae-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="528ae-114">Message Text</span></span>|<span data-ttu-id="528ae-115">無法建立計畫指南 '%.\*ls'，因為無法將 `@hints` 中指定的提示套用至 `@stmt` 或 `@statement_start_offset` 指定的陳述式。</span><span class="sxs-lookup"><span data-stu-id="528ae-115">Cannot create plan guide '%.\*ls' because the hints specified in `@hints` cannot be applied to the statement specified by either `@stmt` or `@statement_start_offset`.</span></span> <span data-ttu-id="528ae-116">請確認提示能否套用至陳述式。</span><span class="sxs-lookup"><span data-stu-id="528ae-116">Verify that the hints can be applied to the statement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="528ae-117">說明</span><span class="sxs-lookup"><span data-stu-id="528ae-117">Explanation</span></span>  
 <span data-ttu-id="528ae-118">無法將 `@hints` 中指定的提示套用至 `@stmt` 或 `@statement_start_offset` 指定的陳述式。</span><span class="sxs-lookup"><span data-stu-id="528ae-118">The hints specified in `@hints` cannot be applied to the statement specified by either `@stmt` or `@statement_start_offset`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="528ae-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="528ae-119">User Action</span></span>  
 <span data-ttu-id="528ae-120">請指定能夠套用至陳述式的提示。</span><span class="sxs-lookup"><span data-stu-id="528ae-120">Specify hints that can be applied to the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528ae-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="528ae-121">See Also</span></span>  
 <span data-ttu-id="528ae-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="528ae-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="528ae-123">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="528ae-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="528ae-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="528ae-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
