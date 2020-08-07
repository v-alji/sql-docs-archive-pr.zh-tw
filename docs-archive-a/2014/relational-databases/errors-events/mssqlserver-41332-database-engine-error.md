---
title: MSSQLSERVER_41332 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72a87838673f07f7a40596517ab54533d944e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597877"
---
# <a name="mssqlserver_41332"></a><span data-ttu-id="f83aa-102">MSSQLSERVER_41332</span><span class="sxs-lookup"><span data-stu-id="f83aa-102">MSSQLSERVER_41332</span></span>
    
## <a name="details"></a><span data-ttu-id="f83aa-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f83aa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f83aa-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f83aa-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="f83aa-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f83aa-105">Event ID</span></span>|<span data-ttu-id="f83aa-106">41332</span><span class="sxs-lookup"><span data-stu-id="f83aa-106">41332</span></span>|  
|<span data-ttu-id="f83aa-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f83aa-107">Event Source</span></span>|<span data-ttu-id="f83aa-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f83aa-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f83aa-109">元件</span><span class="sxs-lookup"><span data-stu-id="f83aa-109">Component</span></span>|<span data-ttu-id="f83aa-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f83aa-110">SQLEngine</span></span>|  
|<span data-ttu-id="f83aa-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f83aa-111">Symbolic Name</span></span>|<span data-ttu-id="f83aa-112">SQL_SNAPSHOT_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="f83aa-112">SQL_SNAPSHOT_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="f83aa-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f83aa-113">Message Text</span></span>|<span data-ttu-id="f83aa-114">工作階段 TRANSACTION ISOLATION LEVEL 設為 SNAPSHOT 時，無法存取或建立記憶體最佳化資料表和原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="f83aa-114">Memory optimized tables and natively compiled stored procedures cannot be accessed or created when the session TRANSACTION ISOLATION LEVEL is set to SNAPSHOT.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f83aa-115">說明</span><span class="sxs-lookup"><span data-stu-id="f83aa-115">Explanation</span></span>  
 <span data-ttu-id="f83aa-116">交易會以快照集隔離等級啟動，然後嘗試使用不相容的功能。</span><span class="sxs-lookup"><span data-stu-id="f83aa-116">The transaction was started in snapshot isolation level and then attempted to use an incompatible feature.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f83aa-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f83aa-117">User Action</span></span>  
 <span data-ttu-id="f83aa-118">以不同的隔離等級啟動交易。</span><span class="sxs-lookup"><span data-stu-id="f83aa-118">Start the transaction with a different isolation level.</span></span> <span data-ttu-id="f83aa-119">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="f83aa-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83aa-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f83aa-120">See Also</span></span>  
 [<span data-ttu-id="f83aa-121">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="f83aa-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
