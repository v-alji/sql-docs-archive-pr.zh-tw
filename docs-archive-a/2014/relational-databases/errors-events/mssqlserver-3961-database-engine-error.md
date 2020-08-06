---
title: MSSQLSERVER_3961 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f55be9288b3c2e559633d0f67709829466fc8815
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599517"
---
# <a name="mssqlserver_3961"></a><span data-ttu-id="fa7d3-102">MSSQLSERVER_3961</span><span class="sxs-lookup"><span data-stu-id="fa7d3-102">MSSQLSERVER_3961</span></span>
    
## <a name="details"></a><span data-ttu-id="fa7d3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fa7d3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa7d3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fa7d3-104">Product Name</span></span>|<span data-ttu-id="fa7d3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fa7d3-105">SQL Server</span></span>|  
|<span data-ttu-id="fa7d3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fa7d3-106">Event ID</span></span>|<span data-ttu-id="fa7d3-107">3961</span><span class="sxs-lookup"><span data-stu-id="fa7d3-107">3961</span></span>|  
|<span data-ttu-id="fa7d3-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="fa7d3-108">Event Source</span></span>|<span data-ttu-id="fa7d3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fa7d3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fa7d3-110">元件</span><span class="sxs-lookup"><span data-stu-id="fa7d3-110">Component</span></span>|<span data-ttu-id="fa7d3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fa7d3-111">SQLEngine</span></span>|  
|<span data-ttu-id="fa7d3-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fa7d3-112">Symbolic Name</span></span>|<span data-ttu-id="fa7d3-113">XACT_METADATA_INVALID</span><span class="sxs-lookup"><span data-stu-id="fa7d3-113">XACT_METADATA_INVALID</span></span>|  
|<span data-ttu-id="fa7d3-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fa7d3-114">Message Text</span></span>|<span data-ttu-id="fa7d3-115">資料庫 '%.\*ls' 中的快照集隔離交易失敗，因為這個交易啟動之後，另一個並行交易的 DDL 陳述式修改了此陳述式存取的物件。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-115">Snapshot isolation transaction failed in database '%.\*ls' because the object accessed by the statement has been modified by a DDL statement in another concurrent transaction since the start of this transaction.</span></span>  <span data-ttu-id="fa7d3-116">因為中繼資料並未建立版本，因此不允許此情況發生。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-116">It is disallowed because the metadata is not versioned.</span></span> <span data-ttu-id="fa7d3-117">如果與快照集隔離混合，中繼資料的並行更新可能會導致不一致的問題。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-117">A concurrent update to metadata can lead to inconsistency if mixed with snapshot isolation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fa7d3-118">說明</span><span class="sxs-lookup"><span data-stu-id="fa7d3-118">Explanation</span></span>  
 <span data-ttu-id="fa7d3-119">如果您要查詢快照隔離下的中繼資料，而且有並行 DDL 陳述式會更新在快照隔離下受到存取的中繼資料，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-119">This error can occur if you are querying metadata under snapshot isolation and there is a concurrent DDL statement that updates the metadata that is being accessed under snapshot isolation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fa7d3-120">不支援中繼資料的版本控制。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-120">does not support versioning of metadata.</span></span> <span data-ttu-id="fa7d3-121">基於這個理由，可在快照隔離下執行的明確交易之中執行的 DDL 作業會受到限制。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-121">For this reason, there are restrictions on what DDL operations can be performed within an explicit transaction running under snapshot isolation.</span></span> <span data-ttu-id="fa7d3-122">根據定義，隱含交易是單一陳述式，即便使用 DDL 陳述式，也能強制執行快照集隔離的語意。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-122">An implicit transaction, by definition, is a single statement which makes it possible to enforce the semantics of snapshot isolation even with DDL statements.</span></span> <span data-ttu-id="fa7d3-123">在 BEGIN TRANSACTION 陳述式之後，不允許在快照隔離下執行下列 DDL 陳述式：ALTER TABLE、CREATE INDEX、CREATE XML INDEX、ALTER INDEX、DROP INDEX、DBCC REINDEX、ALTER PARTITION FUNCTION、ALTER PARTITION SCHEME 或是任何通用語言執行平台 (CLR) DDL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-123">The following DDL statements are not permitted under snapshot isolation after a BEGIN TRANSACTION statement: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME, or any common language runtime (CLR) DDL statement.</span></span> <span data-ttu-id="fa7d3-124">在隱含交易內使用快照集隔離時，這些陳述式會受到允許。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-124">These statements are permitted when you are using snapshot isolation within implicit transactions.</span></span> <span data-ttu-id="fa7d3-125">根據定義，隱含交易是單一陳述式，即便使用 DDL 陳述式，也能強制執行快照集隔離的語意。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-125">An implicit transaction, by definition, is a single statement which makes it possible to enforce the semantics of snapshot isolation even with DDL statements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fa7d3-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fa7d3-126">User Action</span></span>  
 <span data-ttu-id="fa7d3-127">將快照隔離等級變更為非快照隔離等級，例如在查詢中繼資料之前認可的讀取。</span><span class="sxs-lookup"><span data-stu-id="fa7d3-127">Change the snapshot isolation level to a non-snapshot isolation level such as read committed before querying metadata.</span></span>  
  
  
