---
title: MSSQL_ENG014005 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d820fd26cceee72b0d08204d6f6ce73a76508e9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585310"
---
# <a name="mssql_eng014005"></a><span data-ttu-id="7f173-102">MSSQL_ENG014005</span><span class="sxs-lookup"><span data-stu-id="7f173-102">MSSQL_ENG014005</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7f173-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="7f173-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f173-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7f173-104">Product Name</span></span>|<span data-ttu-id="7f173-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7f173-105">SQL Server</span></span>|  
|<span data-ttu-id="7f173-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7f173-106">Event ID</span></span>|<span data-ttu-id="7f173-107">14005</span><span class="sxs-lookup"><span data-stu-id="7f173-107">14005</span></span>|  
|<span data-ttu-id="7f173-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7f173-108">Event Source</span></span>|<span data-ttu-id="7f173-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7f173-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7f173-110">元件</span><span class="sxs-lookup"><span data-stu-id="7f173-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7f173-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7f173-111">Symbolic Name</span></span>||  
|<span data-ttu-id="7f173-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7f173-112">Message Text</span></span>|<span data-ttu-id="7f173-113">無法卸除發行集。</span><span class="sxs-lookup"><span data-stu-id="7f173-113">Could not drop publication.</span></span> <span data-ttu-id="7f173-114">有它的訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="7f173-114">A subscription exists to it.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7f173-115">說明</span><span class="sxs-lookup"><span data-stu-id="7f173-115">Explanation</span></span>  
 <span data-ttu-id="7f173-116">您已嘗試卸除具有一個或多個關聯訂閱的發行集。</span><span class="sxs-lookup"><span data-stu-id="7f173-116">You have tried to drop a publication which has one or more associated subscriptions.</span></span> <span data-ttu-id="7f173-117">發行集僅在沒有關聯的訂閱時方可卸除。</span><span class="sxs-lookup"><span data-stu-id="7f173-117">A publication can only be dropped if there are no associated subscriptions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7f173-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7f173-118">User Action</span></span>  
 <span data-ttu-id="7f173-119">先卸除訂閱，然後再卸除發行集。</span><span class="sxs-lookup"><span data-stu-id="7f173-119">Drop the subscriptions before dropping the publication.</span></span> <span data-ttu-id="7f173-120">如果使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 卸除發行集，您可以選擇在卸除發行集之前自動卸除所有關聯的訂閱。</span><span class="sxs-lookup"><span data-stu-id="7f173-120">If you use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to drop the publication, it will give you the option to automatically drop all associated subscriptions before dropping the publication.</span></span> <span data-ttu-id="7f173-121">如果使用預存程序，則必須先明確地卸除訂閱。</span><span class="sxs-lookup"><span data-stu-id="7f173-121">If you use stored procedures, you must explicitly drop the subscriptions first.</span></span> <span data-ttu-id="7f173-122">如需相關資訊，請參閱 [Delete a Push Subscription](delete-a-push-subscription.md) 及 [Delete a Pull Subscription](delete-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="7f173-122">For more information, see [Delete a Push Subscription](delete-a-push-subscription.md) and [Delete a Pull Subscription](delete-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="7f173-123">如果發行集不存在訂閱，或者在建立發行集時出現此錯誤，可能有之前的訂閱在移除時未完全清除。</span><span class="sxs-lookup"><span data-stu-id="7f173-123">If no subscriptions appear to exist for the publication or if you see this error when you create a publication, you might have a previous subscription that was not completely cleaned up when it was removed.</span></span> <span data-ttu-id="7f173-124">在資料庫上執行 [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，以移除與複寫相關的所有物件與設定。</span><span class="sxs-lookup"><span data-stu-id="7f173-124">Execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) on the database to remove all objects and settings related to replication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f173-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f173-125">See Also</span></span>  
 [<span data-ttu-id="7f173-126">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="7f173-126">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
