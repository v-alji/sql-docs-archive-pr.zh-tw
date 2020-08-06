---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cf45a117dcda0827672c6072c603a1fc0866a33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599509"
---
# <a name="mssqlserver_41359"></a><span data-ttu-id="84cd4-102">MSSQLSERVER_41359</span><span class="sxs-lookup"><span data-stu-id="84cd4-102">MSSQLSERVER_41359</span></span>
    
## <a name="details"></a><span data-ttu-id="84cd4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="84cd4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84cd4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="84cd4-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="84cd4-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="84cd4-105">Event ID</span></span>|<span data-ttu-id="84cd4-106">41359</span><span class="sxs-lookup"><span data-stu-id="84cd4-106">41359</span></span>|  
|<span data-ttu-id="84cd4-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="84cd4-107">Event Source</span></span>|<span data-ttu-id="84cd4-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="84cd4-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="84cd4-109">元件</span><span class="sxs-lookup"><span data-stu-id="84cd4-109">Component</span></span>|<span data-ttu-id="84cd4-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="84cd4-110">SQLEngine</span></span>|  
|<span data-ttu-id="84cd4-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="84cd4-111">Symbolic Name</span></span>|<span data-ttu-id="84cd4-112">SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="84cd4-112">SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="84cd4-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="84cd4-113">Message Text</span></span>|<span data-ttu-id="84cd4-114">當資料庫選項 READ_COMMITTED_SNAPSHOT 設為 ON 時，使用 READ COMMITTED 隔離等級來存取記憶體最佳化資料表的查詢無法存取磁碟基礎的資料表。</span><span class="sxs-lookup"><span data-stu-id="84cd4-114">A query that accesses memory optimized tables using the READ COMMITTED isolation level, cannot access disk based tables when the database option READ_COMMITTED_SNAPSHOT is set to ON.</span></span> <span data-ttu-id="84cd4-115">為使用資料表提示例如 WITH (SNAPSHOT) 的記憶體最佳化資料表，提供支援的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="84cd4-115">Provide a supported isolation level for the memory optimized table using a table hint, such as WITH (SNAPSHOT).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="84cd4-116">說明</span><span class="sxs-lookup"><span data-stu-id="84cd4-116">Explanation</span></span>  
 <span data-ttu-id="84cd4-117">READ_COMMITTED_SNAPSHOT=ON 的資料庫不支援存取記憶體最佳化資料表和磁碟基礎之資料表的交易。</span><span class="sxs-lookup"><span data-stu-id="84cd4-117">The database with READ_COMMITTED_SNAPSHOT=ON does not support the transactions that access both memory-optimized tables and disk based tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="84cd4-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="84cd4-118">User Action</span></span>  
 <span data-ttu-id="84cd4-119">針對使用資料表層級提示 (例如 WITH (SNAPSHOT)) 的記憶體最佳化資料表，將 READ_COMMITTED_SNAPSHOT 設為 OFF 或提供支援的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="84cd4-119">Set READ_COMMITTED_SNAPSHOT to OFF or supply a supported isolation level for the memory-optimized table using a table-level hint, such as WITH (SNAPSHOT).</span></span> <span data-ttu-id="84cd4-120">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="84cd4-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cd4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84cd4-121">See Also</span></span>  
 [<span data-ttu-id="84cd4-122">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="84cd4-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
