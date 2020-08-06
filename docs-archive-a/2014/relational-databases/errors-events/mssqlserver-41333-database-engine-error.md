---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ba3cfc9627b4b44c3c9eccc620fb16bb94b861b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701230"
---
# <a name="mssqlserver_41333"></a><span data-ttu-id="aa510-102">MSSQLSERVER_41333</span><span class="sxs-lookup"><span data-stu-id="aa510-102">MSSQLSERVER_41333</span></span>
    
## <a name="details"></a><span data-ttu-id="aa510-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aa510-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa510-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aa510-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="aa510-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aa510-105">Event ID</span></span>|<span data-ttu-id="aa510-106">41333</span><span class="sxs-lookup"><span data-stu-id="aa510-106">41333</span></span>|  
|<span data-ttu-id="aa510-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="aa510-107">Event Source</span></span>|<span data-ttu-id="aa510-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aa510-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aa510-109">元件</span><span class="sxs-lookup"><span data-stu-id="aa510-109">Component</span></span>|<span data-ttu-id="aa510-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aa510-110">SQLEngine</span></span>|  
|<span data-ttu-id="aa510-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aa510-111">Symbolic Name</span></span>|<span data-ttu-id="aa510-112">CROSS_CONTAINER_ISOLATION_FAILURE</span><span class="sxs-lookup"><span data-stu-id="aa510-112">CROSS_CONTAINER_ISOLATION_FAILURE</span></span>|  
|<span data-ttu-id="aa510-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aa510-113">Message Text</span></span>|<span data-ttu-id="aa510-114">下列交易必須在快照集隔離下，存取記憶體最佳化資料表和原生編譯的預存程序:RepeatableRead 交易、Serializable 交易，以及存取未在 RepeatableRead 或 Serializable 隔離中進行記憶體最佳化之資料表的交易。</span><span class="sxs-lookup"><span data-stu-id="aa510-114">The following transactions must access memory optimized tables and natively compiled stored procedures under snapshot isolation: RepeatableRead transactions, Serializable transactions, and transactions that access tables that are not memory optimized in RepeatableRead or Serializable isolation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aa510-115">說明</span><span class="sxs-lookup"><span data-stu-id="aa510-115">Explanation</span></span>  
 <span data-ttu-id="aa510-116">針對在磁碟基礎的交易和 XTP 交易之間較高的隔離等級使用者，有些限制。</span><span class="sxs-lookup"><span data-stu-id="aa510-116">There are restrictions against the user of the higher isolation levels between disk based transactions and XTP transactions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aa510-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aa510-117">User Action</span></span>  
 <span data-ttu-id="aa510-118">請勿嘗試在記憶體最佳化的資料表 (和原生編譯程序) 和磁碟基礎的資料表上執行高等級的隔離作業。</span><span class="sxs-lookup"><span data-stu-id="aa510-118">Don't attempt high level isolation operations on memory-optimized tables (and natively compiled procedures) and disk based tables.</span></span>  
  
 <span data-ttu-id="aa510-119">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="aa510-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa510-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa510-120">See Also</span></span>  
 [<span data-ttu-id="aa510-121">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="aa510-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
