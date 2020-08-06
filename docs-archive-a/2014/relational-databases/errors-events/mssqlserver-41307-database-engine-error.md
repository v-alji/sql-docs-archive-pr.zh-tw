---
title: MSSQLSERVER_41307 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41307 (Database Engine error)
ms.assetid: 56f56410-b07d-4379-b01c-702c95761070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 98407a65d5529fd73bccc638df11167131bd9f8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702933"
---
# <a name="mssqlserver_41307"></a><span data-ttu-id="662e9-102">MSSQLSERVER_41307</span><span class="sxs-lookup"><span data-stu-id="662e9-102">MSSQLSERVER_41307</span></span>
    
## <a name="details"></a><span data-ttu-id="662e9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="662e9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="662e9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="662e9-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="662e9-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="662e9-105">Event ID</span></span>|<span data-ttu-id="662e9-106">41307</span><span class="sxs-lookup"><span data-stu-id="662e9-106">41307</span></span>|  
|<span data-ttu-id="662e9-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="662e9-107">Event Source</span></span>|<span data-ttu-id="662e9-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="662e9-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="662e9-109">元件</span><span class="sxs-lookup"><span data-stu-id="662e9-109">Component</span></span>|<span data-ttu-id="662e9-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="662e9-110">SQLEngine</span></span>|  
|<span data-ttu-id="662e9-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="662e9-111">Symbolic Name</span></span>|<span data-ttu-id="662e9-112">HK_HEKATON_ROW_LIMIT</span><span class="sxs-lookup"><span data-stu-id="662e9-112">HK_HEKATON_ROW_LIMIT</span></span>|  
|<span data-ttu-id="662e9-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="662e9-113">Message Text</span></span>|<span data-ttu-id="662e9-114">已超過記憶體最佳化資料表的 *number* 個位元組資料列大小限制。</span><span class="sxs-lookup"><span data-stu-id="662e9-114">The row size limit of *number* bytes for memory optimized tables has been exceeded.</span></span> <span data-ttu-id="662e9-115">請簡化資料表定義。</span><span class="sxs-lookup"><span data-stu-id="662e9-115">Please simplify the table definition.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="662e9-116">說明</span><span class="sxs-lookup"><span data-stu-id="662e9-116">Explanation</span></span>  
 <span data-ttu-id="662e9-117">記憶體最佳化資料表的資料列大小限制為 8,060 個位元組。</span><span class="sxs-lookup"><span data-stu-id="662e9-117">The row size limit for memory optimized tables is 8,060 bytes.</span></span> <span data-ttu-id="662e9-118">如需詳細資訊，請參閱 [記憶體最佳化資料表中的資料表和資料列大小](../in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="662e9-118">For more information, see [Table and Row Size in Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span> <span data-ttu-id="662e9-119">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="662e9-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662e9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="662e9-120">See Also</span></span>  
 [<span data-ttu-id="662e9-121">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="662e9-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
