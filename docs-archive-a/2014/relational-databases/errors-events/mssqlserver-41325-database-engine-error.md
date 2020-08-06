---
title: MSSQLSERVER_41325 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41325 (Database Engine error)
ms.assetid: 97c6a8bb-139a-44f3-9ed5-f46d047e8ed3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a512d7db6529876259d889d04aabf3d07747cafe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701227"
---
# <a name="mssqlserver_41325"></a><span data-ttu-id="517ef-102">MSSQLSERVER_41325</span><span class="sxs-lookup"><span data-stu-id="517ef-102">MSSQLSERVER_41325</span></span>
    
## <a name="details"></a><span data-ttu-id="517ef-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="517ef-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="517ef-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="517ef-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="517ef-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="517ef-105">Event ID</span></span>|<span data-ttu-id="517ef-106">41325</span><span class="sxs-lookup"><span data-stu-id="517ef-106">41325</span></span>|  
|<span data-ttu-id="517ef-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="517ef-107">Event Source</span></span>|<span data-ttu-id="517ef-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="517ef-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="517ef-109">元件</span><span class="sxs-lookup"><span data-stu-id="517ef-109">Component</span></span>|<span data-ttu-id="517ef-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="517ef-110">SQLEngine</span></span>|  
|<span data-ttu-id="517ef-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="517ef-111">Symbolic Name</span></span>|<span data-ttu-id="517ef-112">HK_TX_COMMIT_SR_VALIDATION</span><span class="sxs-lookup"><span data-stu-id="517ef-112">HK_TX_COMMIT_SR_VALIDATION</span></span>|  
|<span data-ttu-id="517ef-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="517ef-113">Message Text</span></span>|<span data-ttu-id="517ef-114">目前的交易無法認可，因為可序列化驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="517ef-114">The current transaction failed to commit due to a serializable validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="517ef-115">說明</span><span class="sxs-lookup"><span data-stu-id="517ef-115">Explanation</span></span>  
 <span data-ttu-id="517ef-116">交易發生驗證失敗，現在注定要失敗。</span><span class="sxs-lookup"><span data-stu-id="517ef-116">The transaction encountered a validation failure and is now doomed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="517ef-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="517ef-117">User Action</span></span>  
 <span data-ttu-id="517ef-118">請重試失敗的交易。</span><span class="sxs-lookup"><span data-stu-id="517ef-118">Retry the failed transaction.</span></span> <span data-ttu-id="517ef-119">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="517ef-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517ef-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="517ef-120">See Also</span></span>  
 [<span data-ttu-id="517ef-121">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="517ef-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
