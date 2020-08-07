---
title: MSSQLSERVER_41365 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1382a6395f1929a5d5552113e07376bcbf80bf35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597143"
---
# <a name="mssqlserver_41365"></a><span data-ttu-id="1ac3a-102">MSSQLSERVER_41365</span><span class="sxs-lookup"><span data-stu-id="1ac3a-102">MSSQLSERVER_41365</span></span>
    
## <a name="details"></a><span data-ttu-id="1ac3a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1ac3a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1ac3a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1ac3a-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="1ac3a-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1ac3a-105">Event ID</span></span>|<span data-ttu-id="1ac3a-106">41365</span><span class="sxs-lookup"><span data-stu-id="1ac3a-106">41365</span></span>|  
|<span data-ttu-id="1ac3a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="1ac3a-107">Event Source</span></span>|<span data-ttu-id="1ac3a-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1ac3a-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1ac3a-109">元件</span><span class="sxs-lookup"><span data-stu-id="1ac3a-109">Component</span></span>|<span data-ttu-id="1ac3a-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1ac3a-110">SQLEngine</span></span>|  
|<span data-ttu-id="1ac3a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1ac3a-111">Symbolic Name</span></span>|<span data-ttu-id="1ac3a-112">HK_MERGE_SCHEDULE_ERROR</span><span class="sxs-lookup"><span data-stu-id="1ac3a-112">HK_MERGE_SCHEDULE_ERROR</span></span>|  
|<span data-ttu-id="1ac3a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1ac3a-113">Message Text</span></span>|<span data-ttu-id="1ac3a-114">未排程資料庫 %.\*ls 上交易範圍 [%ld, %ld] 的合併要求。</span><span class="sxs-lookup"><span data-stu-id="1ac3a-114">Merge request for transaction range [%ld, %ld] on database %.\*ls was not scheduled.</span></span> <span data-ttu-id="1ac3a-115">代表範圍的檢查點檔案無法用於合併或是正在進行合併的一部分。</span><span class="sxs-lookup"><span data-stu-id="1ac3a-115">The checkpoint files representing the range are either not available for merge or part of an ongoing merge.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1ac3a-116">說明</span><span class="sxs-lookup"><span data-stu-id="1ac3a-116">Explanation</span></span>  
 <span data-ttu-id="1ac3a-117">代表範圍的檢查點檔案無法用於合併或是正在進行合併的一部分。</span><span class="sxs-lookup"><span data-stu-id="1ac3a-117">The checkpoint files representing the range are either not available for merge or part of an ongoing merge.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1ac3a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1ac3a-118">User Action</span></span>  
 <span data-ttu-id="1ac3a-119">為合併/等候提供較佳的交易範圍，然後重新發出相同的要求。</span><span class="sxs-lookup"><span data-stu-id="1ac3a-119">Provide a better transaction range for merge/wait before issuing the same request again.</span></span> <span data-ttu-id="1ac3a-120">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac3a-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac3a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ac3a-121">See Also</span></span>  
 [<span data-ttu-id="1ac3a-122">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="1ac3a-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
