---
title: MSSQLSERVER_10531 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6230c046a9eb7b900377888c59a3a492f2b89f73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699745"
---
# <a name="mssqlserver_10531"></a><span data-ttu-id="e44d9-102">MSSQLSERVER_10531</span><span class="sxs-lookup"><span data-stu-id="e44d9-102">MSSQLSERVER_10531</span></span>
    
## <a name="details"></a><span data-ttu-id="e44d9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e44d9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e44d9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e44d9-104">Product Name</span></span>|<span data-ttu-id="e44d9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e44d9-105">SQL Server</span></span>|  
|<span data-ttu-id="e44d9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e44d9-106">Event ID</span></span>|<span data-ttu-id="e44d9-107">10531</span><span class="sxs-lookup"><span data-stu-id="e44d9-107">10531</span></span>|  
|<span data-ttu-id="e44d9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e44d9-108">Event Source</span></span>|<span data-ttu-id="e44d9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e44d9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e44d9-110">元件</span><span class="sxs-lookup"><span data-stu-id="e44d9-110">Component</span></span>|<span data-ttu-id="e44d9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e44d9-111">SQLEngine</span></span>|  
|<span data-ttu-id="e44d9-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e44d9-112">Symbolic Name</span></span>|<span data-ttu-id="e44d9-113">PG_NO_ELIGIBLE_STMT</span><span class="sxs-lookup"><span data-stu-id="e44d9-113">PG_NO_ELIGIBLE_STMT</span></span>|  
|<span data-ttu-id="e44d9-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e44d9-114">Message Text</span></span>|<span data-ttu-id="e44d9-115">無法從快取建立計畫指南 '%.\*ls'，因為使用者沒有所需的權限。</span><span class="sxs-lookup"><span data-stu-id="e44d9-115">Cannot create plan guide '%.\*ls' from cache because the user does not have adequate permissions.</span></span> <span data-ttu-id="e44d9-116">請將 VIEW SERVER STATE 權限授予建立計畫指南的使用者。</span><span class="sxs-lookup"><span data-stu-id="e44d9-116">Grant the VIEW SERVER STATE permission to the user creating the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e44d9-117">說明</span><span class="sxs-lookup"><span data-stu-id="e44d9-117">Explanation</span></span>  
 <span data-ttu-id="e44d9-118">使用者沒有足夠的權限，無法從計畫快取建立指定的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="e44d9-118">The user does not have adequate permissions to create the specified plan guide from the plan cache.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e44d9-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e44d9-119">User Action</span></span>  
 <span data-ttu-id="e44d9-120">請將 VIEW SERVER STATE 權限授予建立計畫指南的使用者。</span><span class="sxs-lookup"><span data-stu-id="e44d9-120">Grant VIEW SERVER STATE permission to the user creating the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44d9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e44d9-121">See Also</span></span>  
 <span data-ttu-id="e44d9-122">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="e44d9-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="e44d9-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e44d9-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="e44d9-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e44d9-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
