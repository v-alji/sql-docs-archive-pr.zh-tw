---
title: MSSQLSERVER_1203 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1203 (Database Engine error)
ms.assetid: 33a35f00-98c8-46c6-b432-544b326b6117
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cea816a60ccd1b90d849194766edebd2d64d0b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598440"
---
# <a name="mssqlserver_1203"></a><span data-ttu-id="a269d-102">MSSQLSERVER_1203</span><span class="sxs-lookup"><span data-stu-id="a269d-102">MSSQLSERVER_1203</span></span>
    
## <a name="details"></a><span data-ttu-id="a269d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a269d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a269d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a269d-104">Product Name</span></span>|<span data-ttu-id="a269d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a269d-105">SQL Server</span></span>|  
|<span data-ttu-id="a269d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a269d-106">Event ID</span></span>|<span data-ttu-id="a269d-107">1203</span><span class="sxs-lookup"><span data-stu-id="a269d-107">1203</span></span>|  
|<span data-ttu-id="a269d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a269d-108">Event Source</span></span>|<span data-ttu-id="a269d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a269d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a269d-110">元件</span><span class="sxs-lookup"><span data-stu-id="a269d-110">Component</span></span>|<span data-ttu-id="a269d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a269d-111">SQLEngine</span></span>|  
|<span data-ttu-id="a269d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a269d-112">Symbolic Name</span></span>|<span data-ttu-id="a269d-113">LK_NOT</span><span class="sxs-lookup"><span data-stu-id="a269d-113">LK_NOT</span></span>|  
|<span data-ttu-id="a269d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a269d-114">Message Text</span></span>|<span data-ttu-id="a269d-115">處理序識別碼 %d 嘗試解除鎖定不是它所擁有的資源: %.\*ls。</span><span class="sxs-lookup"><span data-stu-id="a269d-115">Process ID %d attempted to unlock a resource it does not own: %.\*ls.</span></span> <span data-ttu-id="a269d-116">請重試交易，因為這種錯誤可能是時間狀況造成的。</span><span class="sxs-lookup"><span data-stu-id="a269d-116">Retry the transaction, because this error may be caused by a timing condition.</span></span> <span data-ttu-id="a269d-117">如果問題仍然存在，請連絡資料庫管理員。</span><span class="sxs-lookup"><span data-stu-id="a269d-117">If the problem persists, contact the database administrator.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a269d-118">說明</span><span class="sxs-lookup"><span data-stu-id="a269d-118">Explanation</span></span>  
 <span data-ttu-id="a269d-119">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在執行一些不同於平常後置處理清除的活動，並且發現它嘗試要解除鎖定的特定頁面已經解除鎖定時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="a269d-119">This error occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is engaged in some activity other than ordinary post-processing cleanup and it finds that a particular page that it is trying to unlock is already unlocked.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="a269d-120">可能的原因</span><span class="sxs-lookup"><span data-stu-id="a269d-120">Possible Causes</span></span>  
 <span data-ttu-id="a269d-121">造成這個錯誤的根本原因，可能與受影響的資料庫內部的結構問題有關。</span><span class="sxs-lookup"><span data-stu-id="a269d-121">The underlying cause of this error may be related to structural problems within the affected database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a269d-122">會管理頁面的鎖定與解除鎖定，以維護多使用者環境中的並行控制。</span><span class="sxs-lookup"><span data-stu-id="a269d-122">manages the acquisition and release of pages to maintain concurrency control in the multiuser environment.</span></span> <span data-ttu-id="a269d-123">這個機制是透過使用各種不同可識別目前頁面及鎖定類型的內部鎖定來維護。</span><span class="sxs-lookup"><span data-stu-id="a269d-123">This mechanism is maintained by using various internal lock structures that identify the page and the type of lock present.</span></span> <span data-ttu-id="a269d-124">處理受影響的頁面時會進行鎖定，處理完成之後便會解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="a269d-124">Locks are acquired for processing of affected pages and released when the processing is finished.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a269d-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a269d-125">User Action</span></span>  
 <span data-ttu-id="a269d-126">針對物件所屬的資料庫執行 DBCC CHECKDB。</span><span class="sxs-lookup"><span data-stu-id="a269d-126">Execute DBCC CHECKDB against the database in which the object belongs.</span></span> <span data-ttu-id="a269d-127">如果 DBCC CHECKDB 回報沒有錯誤，請嘗試重新建立連接並執行命令。</span><span class="sxs-lookup"><span data-stu-id="a269d-127">If DBCC CHECKDB reports no errors, try to reestablish the connection and execute the command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a269d-128">如果執行包含其中一個 REPAIR 子句的 DBCC CHECKDB 後無法更正問題，或者您不確定包含 REPAIR 子句的 DBCC CHECKDB 對資料有何效果，請與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="a269d-128">If you are executing DBCC CHECKDB with one of the REPAIR clauses does not correct the index problem, or if you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider.</span></span>  
  
  
