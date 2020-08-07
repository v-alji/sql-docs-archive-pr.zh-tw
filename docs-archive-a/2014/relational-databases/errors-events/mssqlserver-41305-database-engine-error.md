---
title: MSSQLSERVER_41305 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9c00e20ec220d7fcee0da4e99c2ef35817dae67f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597144"
---
# <a name="mssqlserver_41305"></a><span data-ttu-id="64657-102">MSSQLSERVER_41305</span><span class="sxs-lookup"><span data-stu-id="64657-102">MSSQLSERVER_41305</span></span>
    
## <a name="details"></a><span data-ttu-id="64657-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="64657-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64657-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="64657-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="64657-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="64657-105">Event ID</span></span>|<span data-ttu-id="64657-106">41305</span><span class="sxs-lookup"><span data-stu-id="64657-106">41305</span></span>|  
|<span data-ttu-id="64657-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="64657-107">Event Source</span></span>|<span data-ttu-id="64657-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="64657-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="64657-109">元件</span><span class="sxs-lookup"><span data-stu-id="64657-109">Component</span></span>|<span data-ttu-id="64657-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="64657-110">SQLEngine</span></span>|  
|<span data-ttu-id="64657-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="64657-111">Symbolic Name</span></span>|<span data-ttu-id="64657-112">HK_TX_COMMIT_RR_VALIDATION</span><span class="sxs-lookup"><span data-stu-id="64657-112">HK_TX_COMMIT_RR_VALIDATION</span></span>|  
|<span data-ttu-id="64657-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="64657-113">Message Text</span></span>|<span data-ttu-id="64657-114">目前的交易無法認可，因為可重複的讀取驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="64657-114">The current transaction failed to commit due to a repeatable read validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="64657-115">說明</span><span class="sxs-lookup"><span data-stu-id="64657-115">Explanation</span></span>  
 <span data-ttu-id="64657-116">交易發生驗證失敗，現在注定要失敗。</span><span class="sxs-lookup"><span data-stu-id="64657-116">The transaction encountered a validation failure and is now doomed.</span></span>  
  
 <span data-ttu-id="64657-117">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="64657-117">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="64657-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="64657-118">User Action</span></span>  
 <span data-ttu-id="64657-119">請重試失敗的交易。</span><span class="sxs-lookup"><span data-stu-id="64657-119">Retry the failed transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64657-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64657-120">See Also</span></span>  
 [<span data-ttu-id="64657-121">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="64657-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
