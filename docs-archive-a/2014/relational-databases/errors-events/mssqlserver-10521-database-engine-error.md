---
title: MSSQLSERVER_10521 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c034bd13e212b9b39bfd348353d59e23fc748079
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699748"
---
# <a name="mssqlserver_10521"></a><span data-ttu-id="b34d8-102">MSSQLSERVER_10521</span><span class="sxs-lookup"><span data-stu-id="b34d8-102">MSSQLSERVER_10521</span></span>
    
## <a name="details"></a><span data-ttu-id="b34d8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b34d8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b34d8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b34d8-104">Product Name</span></span>|<span data-ttu-id="b34d8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b34d8-105">SQL Server</span></span>|  
|<span data-ttu-id="b34d8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b34d8-106">Event ID</span></span>|<span data-ttu-id="b34d8-107">10521</span><span class="sxs-lookup"><span data-stu-id="b34d8-107">10521</span></span>|  
|<span data-ttu-id="b34d8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b34d8-108">Event Source</span></span>|<span data-ttu-id="b34d8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b34d8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b34d8-110">元件</span><span class="sxs-lookup"><span data-stu-id="b34d8-110">Component</span></span>|<span data-ttu-id="b34d8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b34d8-111">SQLEngine</span></span>|  
|<span data-ttu-id="b34d8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b34d8-112">Symbolic Name</span></span>|<span data-ttu-id="b34d8-113">PG_PARAM_NEEDED</span><span class="sxs-lookup"><span data-stu-id="b34d8-113">PG_PARAM_NEEDED</span></span>|  
|<span data-ttu-id="b34d8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b34d8-114">Message Text</span></span>|<span data-ttu-id="b34d8-115">無法建立計畫指南 '%.\*ls'，因為已將 `@type` 指定為 '%ls'，而且參數 '%ls' 為 NULL，</span><span class="sxs-lookup"><span data-stu-id="b34d8-115">Cannot create plan guide '%.\*ls' because `@type` was specified as '%ls' and the parameter '%ls' is NULL.</span></span> <span data-ttu-id="b34d8-116">但這種類型要求參數必須為非 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="b34d8-116">This type requires a non-NULL value for the parameter.</span></span> <span data-ttu-id="b34d8-117">請為參數指定非 NULL 值，或將參數類型變更為允許 NULL 值的類型。</span><span class="sxs-lookup"><span data-stu-id="b34d8-117">Specify a non-NULL value for the parameter, or change the type to one that allows a NULL value for the parameter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b34d8-118">說明</span><span class="sxs-lookup"><span data-stu-id="b34d8-118">Explanation</span></span>  
 <span data-ttu-id="b34d8-119">在 `@type` 中指定的類型要求指定的參數必須為非 NULL 值，但是卻提供了 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="b34d8-119">The type specified in `@type` requires a non-NULL value for the specified parameter; however a NULL value was supplied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b34d8-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b34d8-120">User Action</span></span>  
 <span data-ttu-id="b34d8-121">請為參數指定非 NULL 值，或將參數類型變更為允許 NULL 值的類型。</span><span class="sxs-lookup"><span data-stu-id="b34d8-121">Specify a non-NULL value for the parameter, or change the type to one that allows a NULL value for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b34d8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b34d8-122">See Also</span></span>  
 <span data-ttu-id="b34d8-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b34d8-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="b34d8-124">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="b34d8-124">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="b34d8-125">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b34d8-125">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
