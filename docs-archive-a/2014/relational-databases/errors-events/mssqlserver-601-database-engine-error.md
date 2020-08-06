---
title: MSSQLSERVER_601 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "601"
helpviewer_keywords:
- 601 (Database Engine error)
ms.assetid: 2039cc0a-9a43-4369-a04a-935e384388b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 459a983d72a91e628e8cc33636d3abd81998f1d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606356"
---
# <a name="mssqlserver_601"></a><span data-ttu-id="cf86d-102">MSSQLSERVER_601</span><span class="sxs-lookup"><span data-stu-id="cf86d-102">MSSQLSERVER_601</span></span>
    
## <a name="details"></a><span data-ttu-id="cf86d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cf86d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf86d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cf86d-104">Product Name</span></span>|<span data-ttu-id="cf86d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cf86d-105">SQL Server</span></span>|  
|<span data-ttu-id="cf86d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cf86d-106">Event ID</span></span>|<span data-ttu-id="cf86d-107">601</span><span class="sxs-lookup"><span data-stu-id="cf86d-107">601</span></span>|  
|<span data-ttu-id="cf86d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cf86d-108">Event Source</span></span>|<span data-ttu-id="cf86d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cf86d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cf86d-110">元件</span><span class="sxs-lookup"><span data-stu-id="cf86d-110">Component</span></span>|<span data-ttu-id="cf86d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cf86d-111">SQLEngine</span></span>|  
|<span data-ttu-id="cf86d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cf86d-112">Symbolic Name</span></span>||  
|<span data-ttu-id="cf86d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cf86d-113">Message Text</span></span>|<span data-ttu-id="cf86d-114">由於資料移動而無法繼續用 NOLOCK 掃描。</span><span class="sxs-lookup"><span data-stu-id="cf86d-114">Could not continue scan with NOLOCK due to data movement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf86d-115">說明</span><span class="sxs-lookup"><span data-stu-id="cf86d-115">Explanation</span></span>  
 <span data-ttu-id="cf86d-116">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 無法繼續執行查詢，因為另一項交易已更新或刪除它嘗試讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="cf86d-116">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot continue executing the query because it is trying to read data that was updated or deleted by another transaction.</span></span> <span data-ttu-id="cf86d-117">此查詢使用的是 NOLOCK 鎖定提示或 READ UNCOMMITTED 交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="cf86d-117">The query is using either the NOLOCK locking hint or the READ UNCOMMITTED transaction isolation level.</span></span>  
  
 <span data-ttu-id="cf86d-118">一般都會拒絕存取其他交易正在變更的資料，原因是資料已加上鎖定。</span><span class="sxs-lookup"><span data-stu-id="cf86d-118">Typically, access to data that is being changed by another transaction is denied because of locks put on the data.</span></span> <span data-ttu-id="cf86d-119">不過，NOLOCK 鎖定提示和 READ UNCOMMITTED 交易隔離等級可以讓查詢讀取其他交易鎖定的資料。</span><span class="sxs-lookup"><span data-stu-id="cf86d-119">However, the NOLOCK locking hint and READ UNCOMMITTED transaction isolation level let a query read data that is locked by another transaction.</span></span> <span data-ttu-id="cf86d-120">這稱為中途讀取 (dirty read)，因為您可以讀取尚未認可且日後可能變更的值。</span><span class="sxs-lookup"><span data-stu-id="cf86d-120">This is referred to as a dirty read because you can read values that have not yet been committed and that are subject to change.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf86d-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cf86d-121">User Action</span></span>  
 <span data-ttu-id="cf86d-122">這項錯誤會取消查詢。</span><span class="sxs-lookup"><span data-stu-id="cf86d-122">This error cancels the query.</span></span> <span data-ttu-id="cf86d-123">請重新送出查詢或移除 NOLOCK 鎖定提示。</span><span class="sxs-lookup"><span data-stu-id="cf86d-123">Either resubmit the query or remove the NOLOCK locking hint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf86d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf86d-124">See Also</span></span>  
 <span data-ttu-id="cf86d-125">[MSSQLSERVER_605](mssqlserver-605-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="cf86d-125">[MSSQLSERVER_605](mssqlserver-605-database-engine-error.md) </span></span>  
 <span data-ttu-id="cf86d-126">[資料表提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span><span class="sxs-lookup"><span data-stu-id="cf86d-126">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span></span>  
 <span data-ttu-id="cf86d-127">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cf86d-127">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="cf86d-128">SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cf86d-128">SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)  
  
  
