---
title: MSSQLSERVER_10537 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b1baccad5236bd8c1a71024b7dd542cc9d11cbd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702961"
---
# <a name="mssqlserver_10537"></a><span data-ttu-id="bc213-102">MSSQLSERVER_10537</span><span class="sxs-lookup"><span data-stu-id="bc213-102">MSSQLSERVER_10537</span></span>
    
## <a name="details"></a><span data-ttu-id="bc213-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bc213-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc213-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bc213-104">Product Name</span></span>|<span data-ttu-id="bc213-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bc213-105">SQL Server</span></span>|  
|<span data-ttu-id="bc213-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bc213-106">Event ID</span></span>|<span data-ttu-id="bc213-107">10537</span><span class="sxs-lookup"><span data-stu-id="bc213-107">10537</span></span>|  
|<span data-ttu-id="bc213-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bc213-108">Event Source</span></span>|<span data-ttu-id="bc213-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bc213-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bc213-110">元件</span><span class="sxs-lookup"><span data-stu-id="bc213-110">Component</span></span>|<span data-ttu-id="bc213-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bc213-111">SQLEngine</span></span>|  
|<span data-ttu-id="bc213-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bc213-112">Symbolic Name</span></span>|<span data-ttu-id="bc213-113">PG_DUP_ENABLED</span><span class="sxs-lookup"><span data-stu-id="bc213-113">PG_DUP_ENABLED</span></span>|  
|<span data-ttu-id="bc213-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bc213-114">Message Text</span></span>|<span data-ttu-id="bc213-115">無法啟用計畫指南 '%.\*ls'，因為啟用的計畫指南 '%.\*ls' 中包含相同範圍和起始位移值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="bc213-115">Cannot enable plan guide '%.\*ls' because the enabled plan guide '%.\*ls' contains the same scope and starting offset value as the statement.</span></span> <span data-ttu-id="bc213-116">請停用現有的計畫指南後，再啟用指定的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="bc213-116">Disable the existing plan guide before enabling the specified plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bc213-117">說明</span><span class="sxs-lookup"><span data-stu-id="bc213-117">Explanation</span></span>  
 <span data-ttu-id="bc213-118">現有的計畫指南與指定之計畫指南中的陳述式包含相同範圍和起始位移值。</span><span class="sxs-lookup"><span data-stu-id="bc213-118">An existing plan guide contains the same scope and starting offset value as the statement in the specified plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bc213-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bc213-119">User Action</span></span>  
 <span data-ttu-id="bc213-120">請停用現有的計畫指南後，再啟用指定的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="bc213-120">Disable the existing plan guide before enabling the specified plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc213-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc213-121">See Also</span></span>  
 <span data-ttu-id="bc213-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bc213-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="bc213-123">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="bc213-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="bc213-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bc213-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
