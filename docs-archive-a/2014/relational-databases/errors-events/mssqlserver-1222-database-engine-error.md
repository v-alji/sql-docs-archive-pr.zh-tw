---
title: MSSQLSERVER_1222 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac3fe9314386836633a11f17d6775c75019de93a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584556"
---
# <a name="mssqlserver_1222"></a><span data-ttu-id="06200-102">MSSQLSERVER_1222</span><span class="sxs-lookup"><span data-stu-id="06200-102">MSSQLSERVER_1222</span></span>
    
## <a name="details"></a><span data-ttu-id="06200-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="06200-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06200-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="06200-104">Product Name</span></span>|<span data-ttu-id="06200-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="06200-105">SQL Server</span></span>|  
|<span data-ttu-id="06200-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="06200-106">Event ID</span></span>|<span data-ttu-id="06200-107">1222</span><span class="sxs-lookup"><span data-stu-id="06200-107">1222</span></span>|  
|<span data-ttu-id="06200-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="06200-108">Event Source</span></span>|<span data-ttu-id="06200-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="06200-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="06200-110">元件</span><span class="sxs-lookup"><span data-stu-id="06200-110">Component</span></span>|<span data-ttu-id="06200-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="06200-111">SQLEngine</span></span>|  
|<span data-ttu-id="06200-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="06200-112">Symbolic Name</span></span>|<span data-ttu-id="06200-113">LK_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="06200-113">LK_TIMEOUT</span></span>|  
|<span data-ttu-id="06200-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="06200-114">Message Text</span></span>|<span data-ttu-id="06200-115">鎖定要求的逾時期間已過。</span><span class="sxs-lookup"><span data-stu-id="06200-115">Lock request time out period exceeded.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="06200-116">說明</span><span class="sxs-lookup"><span data-stu-id="06200-116">Explanation</span></span>  
 <span data-ttu-id="06200-117">其他交易鎖定必要資源的時間比這項查詢可以等候的時間還長。</span><span class="sxs-lookup"><span data-stu-id="06200-117">Another transaction held a lock on a required resource longer than this query could wait for it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="06200-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="06200-118">User Action</span></span>  
 <span data-ttu-id="06200-119">執行下列工作來減少問題：</span><span class="sxs-lookup"><span data-stu-id="06200-119">Perform the following tasks to alleviate the problem:</span></span>  
  
1.  <span data-ttu-id="06200-120">如果可以的話，請找出鎖定必要資源的交易。</span><span class="sxs-lookup"><span data-stu-id="06200-120">Locate the transaction that is holding the lock on the required resource, if possible.</span></span> <span data-ttu-id="06200-121">使用 **sys.dm_os_waiting_tasks** 和 **sys.dm_tran_locks** 動態管理檢視。</span><span class="sxs-lookup"><span data-stu-id="06200-121">Use **sys.dm_os_waiting_tasks** and **sys.dm_tran_locks** dynamic management views.</span></span>  
  
2.  <span data-ttu-id="06200-122">如果交易仍然鎖定資源，請依適當情況結束該交易。</span><span class="sxs-lookup"><span data-stu-id="06200-122">If the transaction is still holding the lock, terminate that transaction if appropriate.</span></span>  
  
3.  <span data-ttu-id="06200-123">重新執行查詢。</span><span class="sxs-lookup"><span data-stu-id="06200-123">Execute the query again.</span></span>  
  
 <span data-ttu-id="06200-124">如果這項錯誤經常發生，請變更鎖定逾時期限，或請修改造成問題的交易，以縮短這些交易鎖定資源的時間。</span><span class="sxs-lookup"><span data-stu-id="06200-124">If this error occurs frequently change the lock time-out period or modify the offending transactions so that they hold the lock for less time.</span></span>  
  
  
