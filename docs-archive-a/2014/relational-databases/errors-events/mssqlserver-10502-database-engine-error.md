---
title: MSSQLSERVER_10502 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eeec3a3adf318cadc96501938f8a5565f1c07670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585488"
---
# <a name="mssqlserver_10502"></a><span data-ttu-id="52cac-102">MSSQLSERVER_10502</span><span class="sxs-lookup"><span data-stu-id="52cac-102">MSSQLSERVER_10502</span></span>
    
## <a name="details"></a><span data-ttu-id="52cac-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="52cac-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52cac-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="52cac-104">Product Name</span></span>|<span data-ttu-id="52cac-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="52cac-105">SQL Server</span></span>|  
|<span data-ttu-id="52cac-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="52cac-106">Event ID</span></span>|<span data-ttu-id="52cac-107">10502</span><span class="sxs-lookup"><span data-stu-id="52cac-107">10502</span></span>|  
|<span data-ttu-id="52cac-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="52cac-108">Event Source</span></span>|<span data-ttu-id="52cac-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="52cac-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="52cac-110">元件</span><span class="sxs-lookup"><span data-stu-id="52cac-110">Component</span></span>|<span data-ttu-id="52cac-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="52cac-111">SQLEngine</span></span>|  
|<span data-ttu-id="52cac-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="52cac-112">Symbolic Name</span></span>|<span data-ttu-id="52cac-113">PG_DUP_FOUND</span><span class="sxs-lookup"><span data-stu-id="52cac-113">PG_DUP_FOUND</span></span>|  
|<span data-ttu-id="52cac-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="52cac-114">Message Text</span></span>|<span data-ttu-id="52cac-115">無法建立計畫指南 '%.\*ls'，因為 @stmt 和 @module_or_batch 或是 @plan_handle 和 @statement_start_offset 所指定的陳述式與資料庫中現有的計畫指南 '%.\*ls' 相符。</span><span class="sxs-lookup"><span data-stu-id="52cac-115">Cannot create plan guide '%.\*ls' because the statement specified by @stmt and @module_or_batch, or by @plan_handle and @statement_start_offset, matches the existing plan guide '%.\*ls' in the database.</span></span> <span data-ttu-id="52cac-116">請卸除現有計畫指南後，再建立新的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="52cac-116">Drop the existing plan guide before creating the new plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="52cac-117">說明</span><span class="sxs-lookup"><span data-stu-id="52cac-117">Explanation</span></span>  
 <span data-ttu-id="52cac-118">指定之陳述式的計畫指南已存在。</span><span class="sxs-lookup"><span data-stu-id="52cac-118">A plan guide exists for the specified statement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="52cac-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="52cac-119">User Action</span></span>  
 <span data-ttu-id="52cac-120">請卸除現有計畫指南後，再建立新的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="52cac-120">Drop the existing plan guide before creating the new plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cac-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52cac-121">See Also</span></span>  
 <span data-ttu-id="52cac-122">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="52cac-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="52cac-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="52cac-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="52cac-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52cac-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
