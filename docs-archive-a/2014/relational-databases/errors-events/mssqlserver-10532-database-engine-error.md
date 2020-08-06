---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26ab34c319eff62737eae337828247fdfd7e901b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707582"
---
# <a name="mssqlserver_10532"></a><span data-ttu-id="9c20c-102">MSSQLSERVER_10532</span><span class="sxs-lookup"><span data-stu-id="9c20c-102">MSSQLSERVER_10532</span></span>
    
## <a name="details"></a><span data-ttu-id="9c20c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9c20c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c20c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9c20c-104">Product Name</span></span>|<span data-ttu-id="9c20c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9c20c-105">SQL Server</span></span>|  
|<span data-ttu-id="9c20c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9c20c-106">Event ID</span></span>|<span data-ttu-id="9c20c-107">10532</span><span class="sxs-lookup"><span data-stu-id="9c20c-107">10532</span></span>|  
|<span data-ttu-id="9c20c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9c20c-108">Event Source</span></span>|<span data-ttu-id="9c20c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9c20c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9c20c-110">元件</span><span class="sxs-lookup"><span data-stu-id="9c20c-110">Component</span></span>|<span data-ttu-id="9c20c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9c20c-111">SQLEngine</span></span>|  
|<span data-ttu-id="9c20c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9c20c-112">Symbolic Name</span></span>|<span data-ttu-id="9c20c-113">PG_NO_ELIGIBLE_STMT</span><span class="sxs-lookup"><span data-stu-id="9c20c-113">PG_NO_ELIGIBLE_STMT</span></span>|  
|<span data-ttu-id="9c20c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9c20c-114">Message Text</span></span>|<span data-ttu-id="9c20c-115">無法建立計畫指南 '%.\*ls'，因為 `@plan_handle` 指定的批次或模組中未包含適用於計畫指南的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9c20c-115">Cannot create plan guide '%.\*ls' because the batch or module specified by `@plan_handle` does not contain a statement that is eligible for a plan guide.</span></span> <span data-ttu-id="9c20c-116">請為 `@plan_handle` 指定其他值。</span><span class="sxs-lookup"><span data-stu-id="9c20c-116">Specify a different value for `@plan_handle`.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9c20c-117">說明</span><span class="sxs-lookup"><span data-stu-id="9c20c-117">Explanation</span></span>  
 <span data-ttu-id="9c20c-118">`@plan_handle` 指定的批次或模組中未包含適用於計畫指南的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9c20c-118">The batch or module specified by `@plan_handle` does not contain a statement that is eligible for a plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9c20c-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9c20c-119">User Action</span></span>  
 <span data-ttu-id="9c20c-120">請為 `@plan_handle` 指定其他值。</span><span class="sxs-lookup"><span data-stu-id="9c20c-120">Specify a different value for `@plan_handle`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c20c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c20c-121">See Also</span></span>  
 <span data-ttu-id="9c20c-122">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="9c20c-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="9c20c-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9c20c-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="9c20c-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9c20c-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
