---
title: MSSQLSERVER_41302 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 751dac91378c002a7e6c6c619ddaf12be8173400
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594576"
---
# <a name="mssqlserver_41302"></a><span data-ttu-id="deb6a-102">MSSQLSERVER_41302</span><span class="sxs-lookup"><span data-stu-id="deb6a-102">MSSQLSERVER_41302</span></span>
    
## <a name="details"></a><span data-ttu-id="deb6a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="deb6a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="deb6a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="deb6a-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="deb6a-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="deb6a-105">Event ID</span></span>|<span data-ttu-id="deb6a-106">41302</span><span class="sxs-lookup"><span data-stu-id="deb6a-106">41302</span></span>|  
|<span data-ttu-id="deb6a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="deb6a-107">Event Source</span></span>|<span data-ttu-id="deb6a-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="deb6a-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="deb6a-109">元件</span><span class="sxs-lookup"><span data-stu-id="deb6a-109">Component</span></span>|<span data-ttu-id="deb6a-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="deb6a-110">SQLEngine</span></span>|  
|<span data-ttu-id="deb6a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="deb6a-111">Symbolic Name</span></span>|<span data-ttu-id="deb6a-112">WRITE_WRITE_CONFLICT</span><span class="sxs-lookup"><span data-stu-id="deb6a-112">WRITE_WRITE_CONFLICT</span></span>|  
|<span data-ttu-id="deb6a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="deb6a-113">Message Text</span></span>|<span data-ttu-id="deb6a-114">目前交易嘗試更新自從此交易啟動以來已經更新的記錄。</span><span class="sxs-lookup"><span data-stu-id="deb6a-114">The current transaction attempted to update a record that has been updated since this transaction started.</span></span> <span data-ttu-id="deb6a-115">交易已中止。</span><span class="sxs-lookup"><span data-stu-id="deb6a-115">The transaction was aborted.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="deb6a-116">說明</span><span class="sxs-lookup"><span data-stu-id="deb6a-116">Explanation</span></span>  
 <span data-ttu-id="deb6a-117">交易發生寫入/寫入衝突，陳述式已結束。</span><span class="sxs-lookup"><span data-stu-id="deb6a-117">The transaction encountered a write/write conflict and the statement terminated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="deb6a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="deb6a-118">User Action</span></span>  
 <span data-ttu-id="deb6a-119">稍後在其他交易中重試作業。</span><span class="sxs-lookup"><span data-stu-id="deb6a-119">Retry the operation later in a different transaction.</span></span> <span data-ttu-id="deb6a-120">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="deb6a-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb6a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deb6a-121">See Also</span></span>  
 [<span data-ttu-id="deb6a-122">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="deb6a-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
