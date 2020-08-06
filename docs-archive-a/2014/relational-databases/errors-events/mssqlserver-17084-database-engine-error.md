---
title: MSSQLSERVER_17084 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59b0fc3e0884ddd89809767a068b937b5c145f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598932"
---
# <a name="mssqlserver_17084"></a><span data-ttu-id="87fa3-102">MSSQLSERVER_17084</span><span class="sxs-lookup"><span data-stu-id="87fa3-102">MSSQLSERVER_17084</span></span>
    
## <a name="details"></a><span data-ttu-id="87fa3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="87fa3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87fa3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="87fa3-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="87fa3-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="87fa3-105">Event ID</span></span>|<span data-ttu-id="87fa3-106">17084</span><span class="sxs-lookup"><span data-stu-id="87fa3-106">17084</span></span>|  
|<span data-ttu-id="87fa3-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="87fa3-107">Event Source</span></span>|<span data-ttu-id="87fa3-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="87fa3-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="87fa3-109">元件</span><span class="sxs-lookup"><span data-stu-id="87fa3-109">Component</span></span>|<span data-ttu-id="87fa3-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="87fa3-110">SQLEngine</span></span>|  
|<span data-ttu-id="87fa3-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="87fa3-111">Symbolic Name</span></span>|<span data-ttu-id="87fa3-112">P3_ATOMIC_WITH_MISSING_OPTION</span><span class="sxs-lookup"><span data-stu-id="87fa3-112">P3_ATOMIC_WITH_MISSING_OPTION</span></span>|  
|<span data-ttu-id="87fa3-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="87fa3-113">Message Text</span></span>|<span data-ttu-id="87fa3-114">BEGIN ATOMIC 陳述式的 WITH 子句必須指定選項 '%ls' 的值。</span><span class="sxs-lookup"><span data-stu-id="87fa3-114">The WITH clause of BEGIN ATOMIC statement must specify a value for the option '%ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="87fa3-115">說明</span><span class="sxs-lookup"><span data-stu-id="87fa3-115">Explanation</span></span>  
 <span data-ttu-id="87fa3-116">BEGIN ATOMIC 陳述式的 WITH 子句未指定選項的值。</span><span class="sxs-lookup"><span data-stu-id="87fa3-116">The WITH clause of BEGIN ATOMIC statement did not specify a value for an option.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="87fa3-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="87fa3-117">User Action</span></span>  
 <span data-ttu-id="87fa3-118">`ATOMIC` 區塊需要 `WITH` 選項 `TRANSACTION ISOLATION LEVEL` 和 `LANGUAGE` 的值。</span><span class="sxs-lookup"><span data-stu-id="87fa3-118">`ATOMIC` blocks require values for the `WITH` options `TRANSACTION ISOLATION LEVEL` and `LANGUAGE`.</span></span> <span data-ttu-id="87fa3-119">例如：</span><span class="sxs-lookup"><span data-stu-id="87fa3-119">For example::</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 <span data-ttu-id="87fa3-120">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="87fa3-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fa3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87fa3-121">See Also</span></span>  
 [<span data-ttu-id="87fa3-122">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="87fa3-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
