---
title: MSSQLSERVER_10533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccef25bc8f594cb6ea0b60aefab838ef27cda6f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596059"
---
# <a name="mssqlserver_10533"></a><span data-ttu-id="8ec51-102">MSSQLSERVER_10533</span><span class="sxs-lookup"><span data-stu-id="8ec51-102">MSSQLSERVER_10533</span></span>
    
## <a name="details"></a><span data-ttu-id="8ec51-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8ec51-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ec51-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8ec51-104">Product Name</span></span>|<span data-ttu-id="8ec51-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8ec51-105">SQL Server</span></span>|  
|<span data-ttu-id="8ec51-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8ec51-106">Event ID</span></span>|<span data-ttu-id="8ec51-107">10533</span><span class="sxs-lookup"><span data-stu-id="8ec51-107">10533</span></span>|  
|<span data-ttu-id="8ec51-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8ec51-108">Event Source</span></span>|<span data-ttu-id="8ec51-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8ec51-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8ec51-110">元件</span><span class="sxs-lookup"><span data-stu-id="8ec51-110">Component</span></span>|<span data-ttu-id="8ec51-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8ec51-111">SQLEngine</span></span>|  
|<span data-ttu-id="8ec51-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8ec51-112">Symbolic Name</span></span>|<span data-ttu-id="8ec51-113">PG_NAME_TOO_BIG</span><span class="sxs-lookup"><span data-stu-id="8ec51-113">PG_NAME_TOO_BIG</span></span>|  
|<span data-ttu-id="8ec51-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8ec51-114">Message Text</span></span>|<span data-ttu-id="8ec51-115">無法建立計畫指南 '%.\*ls'，因為計畫指南名稱超出允許的最大字元數 124 個字元。</span><span class="sxs-lookup"><span data-stu-id="8ec51-115">Cannot create plan guide '%.\*ls' because the plan guide name exceeds 124 characters, the maximum number allowed.</span></span> <span data-ttu-id="8ec51-116">請指定少於 125 個字元的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ec51-116">Specify a name that contains fewer than 125 characters.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8ec51-117">說明</span><span class="sxs-lookup"><span data-stu-id="8ec51-117">Explanation</span></span>  
 <span data-ttu-id="8ec51-118">計畫指南名稱超出允許的最大字元數 124 個字元。</span><span class="sxs-lookup"><span data-stu-id="8ec51-118">The plan guide name exceeds 124 characters, the maximum number allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8ec51-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8ec51-119">User Action</span></span>  
 <span data-ttu-id="8ec51-120">請指定少於 125 個字元的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ec51-120">Specify a name that contains fewer than 125 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec51-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ec51-121">See Also</span></span>  
 <span data-ttu-id="8ec51-122">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="8ec51-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="8ec51-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ec51-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="8ec51-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8ec51-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
