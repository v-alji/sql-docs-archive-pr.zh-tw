---
title: MSSQLSERVER_10539 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd1f190b8f5d3ab9755409bdd034fa374ea5314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699712"
---
# <a name="mssqlserver_10539"></a><span data-ttu-id="ff59f-102">MSSQLSERVER_10539</span><span class="sxs-lookup"><span data-stu-id="ff59f-102">MSSQLSERVER_10539</span></span>
    
## <a name="details"></a><span data-ttu-id="ff59f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ff59f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff59f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ff59f-104">Product Name</span></span>|<span data-ttu-id="ff59f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ff59f-105">SQL Server</span></span>|  
|<span data-ttu-id="ff59f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ff59f-106">Event ID</span></span>|<span data-ttu-id="ff59f-107">10539</span><span class="sxs-lookup"><span data-stu-id="ff59f-107">10539</span></span>|  
|<span data-ttu-id="ff59f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ff59f-108">Event Source</span></span>|<span data-ttu-id="ff59f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ff59f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ff59f-110">元件</span><span class="sxs-lookup"><span data-stu-id="ff59f-110">Component</span></span>|<span data-ttu-id="ff59f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ff59f-111">SQLEngine</span></span>|  
|<span data-ttu-id="ff59f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ff59f-112">Symbolic Name</span></span>|<span data-ttu-id="ff59f-113">PG_NO_PLAN_FOR_STMT</span><span class="sxs-lookup"><span data-stu-id="ff59f-113">PG_NO_PLAN_FOR_STMT</span></span>|  
|<span data-ttu-id="ff59f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ff59f-114">Message Text</span></span>|<span data-ttu-id="ff59f-115">無法從快取建立計畫指南 '%.\*ls'，因為起始位移為 %d 的陳述式無法使用查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="ff59f-115">Cannot create plan guide '%.\*ls' from cache because a query plan is not available for the statement with start offset %d.</span></span> <span data-ttu-id="ff59f-116">如果陳述式相依於尚未建立的資料庫物件，就可能發生這種問題。</span><span class="sxs-lookup"><span data-stu-id="ff59f-116">This problem can occur if the statement depends on database objects that have not yet been created.</span></span> <span data-ttu-id="ff59f-117">請確定是否所有必要的資料庫物件都存在，並先建立計畫指南後再執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="ff59f-117">Make sure that all necessary database objects exist, and execute the statement before creating the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ff59f-118">說明</span><span class="sxs-lookup"><span data-stu-id="ff59f-118">Explanation</span></span>  
 <span data-ttu-id="ff59f-119">具有指定之起始位移的陳述式無法使用計畫快取中的查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="ff59f-119">A query plan is not available in the plan cache for the statement with the specified starting offset.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ff59f-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ff59f-120">User Action</span></span>  
 <span data-ttu-id="ff59f-121">請確定是否所有必要的資料庫物件都存在，並先建立計畫指南後再執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="ff59f-121">Make sure that all necessary database objects exist, and execute the statement before creating the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff59f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff59f-122">See Also</span></span>  
 [<span data-ttu-id="ff59f-123">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ff59f-123">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
