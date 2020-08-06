---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 439d282f18490a4353d6528276eaf7e4231c503b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699730"
---
# <a name="mssqlserver_10535"></a><span data-ttu-id="77382-102">MSSQLSERVER_10535</span><span class="sxs-lookup"><span data-stu-id="77382-102">MSSQLSERVER_10535</span></span>
    
## <a name="details"></a><span data-ttu-id="77382-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="77382-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77382-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="77382-104">Product Name</span></span>|<span data-ttu-id="77382-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="77382-105">SQL Server</span></span>|  
|<span data-ttu-id="77382-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="77382-106">Event ID</span></span>|<span data-ttu-id="77382-107">10535</span><span class="sxs-lookup"><span data-stu-id="77382-107">10535</span></span>|  
|<span data-ttu-id="77382-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="77382-108">Event Source</span></span>|<span data-ttu-id="77382-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="77382-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="77382-110">元件</span><span class="sxs-lookup"><span data-stu-id="77382-110">Component</span></span>|<span data-ttu-id="77382-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="77382-111">SQLEngine</span></span>|  
|<span data-ttu-id="77382-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="77382-112">Symbolic Name</span></span>|<span data-ttu-id="77382-113">PG_NO_PLAN</span><span class="sxs-lookup"><span data-stu-id="77382-113">PG_NO_PLAN</span></span>|  
|<span data-ttu-id="77382-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="77382-114">Message Text</span></span>|<span data-ttu-id="77382-115">無法建立計畫指南 '%.\*ls'，因為在計畫快取中找不到指定計畫控制代碼的對應計畫。</span><span class="sxs-lookup"><span data-stu-id="77382-115">Cannot create plan guide '%.\*ls' because a plan was not found in the plan cache that corresponds to the specified plan handle.</span></span> <span data-ttu-id="77382-116">請指定快取的計畫控制代碼。</span><span class="sxs-lookup"><span data-stu-id="77382-116">Specify a cached plan handle.</span></span> <span data-ttu-id="77382-117">如需快取的計畫控制代碼清單，請查詢 sys.dm_exec_query_stats 動態管理檢視。</span><span class="sxs-lookup"><span data-stu-id="77382-117">For a list of cached plan handles, query the sys.dm_exec_query_stats dynamic management view.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="77382-118">說明</span><span class="sxs-lookup"><span data-stu-id="77382-118">Explanation</span></span>  
 <span data-ttu-id="77382-119">在計畫快取中找不到指定計畫控制代碼的對應計畫。</span><span class="sxs-lookup"><span data-stu-id="77382-119">A plan was not found in the plan cache that corresponds to the specified plan handle.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="77382-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="77382-120">User Action</span></span>  
 <span data-ttu-id="77382-121">請指定快取的計畫控制代碼。</span><span class="sxs-lookup"><span data-stu-id="77382-121">Specify a cached plan handle.</span></span> <span data-ttu-id="77382-122">如需快取的計畫控制代碼清單，請查詢 sys.dm_exec_query_stats 動態管理檢視。</span><span class="sxs-lookup"><span data-stu-id="77382-122">For a list of cached plan handles, query the sys.dm_exec_query_stats dynamic management view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77382-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77382-123">See Also</span></span>  
 <span data-ttu-id="77382-124">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77382-124">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span></span>  
 [<span data-ttu-id="77382-125">sys.dm_exec_query_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="77382-125">sys.dm_exec_query_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
