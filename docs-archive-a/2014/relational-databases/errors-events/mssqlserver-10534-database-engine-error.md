---
title: MSSQLSERVER_10534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 793bb0bf5048e30624d9566f65e7c6752bd14386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699739"
---
# <a name="mssqlserver_10534"></a><span data-ttu-id="73f66-102">MSSQLSERVER_10534</span><span class="sxs-lookup"><span data-stu-id="73f66-102">MSSQLSERVER_10534</span></span>
    
## <a name="details"></a><span data-ttu-id="73f66-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="73f66-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73f66-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="73f66-104">Product Name</span></span>|<span data-ttu-id="73f66-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="73f66-105">SQL Server</span></span>|  
|<span data-ttu-id="73f66-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="73f66-106">Event ID</span></span>|<span data-ttu-id="73f66-107">10534</span><span class="sxs-lookup"><span data-stu-id="73f66-107">10534</span></span>|  
|<span data-ttu-id="73f66-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="73f66-108">Event Source</span></span>|<span data-ttu-id="73f66-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="73f66-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="73f66-110">元件</span><span class="sxs-lookup"><span data-stu-id="73f66-110">Component</span></span>|<span data-ttu-id="73f66-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="73f66-111">SQLEngine</span></span>|  
|<span data-ttu-id="73f66-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="73f66-112">Symbolic Name</span></span>|<span data-ttu-id="73f66-113">PG_INVALID_PARAMS</span><span class="sxs-lookup"><span data-stu-id="73f66-113">PG_INVALID_PARAMS</span></span>|  
|<span data-ttu-id="73f66-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="73f66-114">Message Text</span></span>|<span data-ttu-id="73f66-115">無法建立計畫指南 '%.\*ls'，因為指定的 `@params` 值無效。</span><span class="sxs-lookup"><span data-stu-id="73f66-115">Cannot create plan guide '%.\*ls' because the value specified for `@params` is invalid.</span></span> <span data-ttu-id="73f66-116">請以 *parameter_name parameter_type* 格式指定值，或指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="73f66-116">Specify the value in the form *parameter_name parameter_type*, or specify NULL.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="73f66-117">說明</span><span class="sxs-lookup"><span data-stu-id="73f66-117">Explanation</span></span>  
 <span data-ttu-id="73f66-118">針對 `@params` 指定的值無效。</span><span class="sxs-lookup"><span data-stu-id="73f66-118">The value specified for `@params` is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="73f66-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="73f66-119">User Action</span></span>  
 <span data-ttu-id="73f66-120">請以 *parameter_name parameter_type* 格式指定值，或指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="73f66-120">Specify the value in the form *parameter_name parameter_type*, or specify NULL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f66-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73f66-121">See Also</span></span>  
 <span data-ttu-id="73f66-122">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="73f66-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="73f66-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73f66-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="73f66-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73f66-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
