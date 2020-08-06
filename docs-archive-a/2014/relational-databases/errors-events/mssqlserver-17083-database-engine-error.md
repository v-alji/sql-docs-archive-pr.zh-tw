---
title: MSSQLSERVER_17083 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17083 (Database Engine error)
ms.assetid: 6c83737d-0531-4fd9-88f6-2da5a150532d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 598cf9b0182178aa13a6d8b965ac10bedaaf5d15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598937"
---
# <a name="mssqlserver_17083"></a><span data-ttu-id="ce4ae-102">MSSQLSERVER_17083</span><span class="sxs-lookup"><span data-stu-id="ce4ae-102">MSSQLSERVER_17083</span></span>
    
## <a name="details"></a><span data-ttu-id="ce4ae-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ce4ae-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce4ae-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ce4ae-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="ce4ae-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ce4ae-105">Event ID</span></span>|<span data-ttu-id="ce4ae-106">17083</span><span class="sxs-lookup"><span data-stu-id="ce4ae-106">17083</span></span>|  
|<span data-ttu-id="ce4ae-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ce4ae-107">Event Source</span></span>|<span data-ttu-id="ce4ae-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ce4ae-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ce4ae-109">元件</span><span class="sxs-lookup"><span data-stu-id="ce4ae-109">Component</span></span>|<span data-ttu-id="ce4ae-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ce4ae-110">SQLEngine</span></span>|  
|<span data-ttu-id="ce4ae-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ce4ae-111">Symbolic Name</span></span>|<span data-ttu-id="ce4ae-112">P3_HEKATON_NOT_ATOMIC</span><span class="sxs-lookup"><span data-stu-id="ce4ae-112">P3_HEKATON_NOT_ATOMIC</span></span>|  
|<span data-ttu-id="ce4ae-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ce4ae-113">Message Text</span></span>|<span data-ttu-id="ce4ae-114">原生編譯之預存程序的主體必須是 ATOMIC 區塊。</span><span class="sxs-lookup"><span data-stu-id="ce4ae-114">The body of a natively compiled stored procedure must be an ATOMIC block.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ce4ae-115">說明</span><span class="sxs-lookup"><span data-stu-id="ce4ae-115">Explanation</span></span>  
 <span data-ttu-id="ce4ae-116">原生編譯之預存程序的主體沒有 ATOMIC 區塊。</span><span class="sxs-lookup"><span data-stu-id="ce4ae-116">The body of a natively compiled stored procedure did not have an ATOMIC block.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ce4ae-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ce4ae-117">User Action</span></span>  
 <span data-ttu-id="ce4ae-118">原生編譯的預存程序必須包含 ATOMIC 區塊。</span><span class="sxs-lookup"><span data-stu-id="ce4ae-118">A natively compiled stored procedure must contain an ATOMIC block.</span></span> <span data-ttu-id="ce4ae-119">例如：</span><span class="sxs-lookup"><span data-stu-id="ce4ae-119">For example:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 <span data-ttu-id="ce4ae-120">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="ce4ae-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce4ae-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce4ae-121">See Also</span></span>  
 [<span data-ttu-id="ce4ae-122">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="ce4ae-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
