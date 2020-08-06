---
title: MSSQLSERVER_17066 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c2bc421fb969e4f24e49871ff97047be9040ae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598943"
---
# <a name="mssqlserver_17066"></a><span data-ttu-id="c7315-102">MSSQLSERVER_17066</span><span class="sxs-lookup"><span data-stu-id="c7315-102">MSSQLSERVER_17066</span></span>
    
## <a name="details"></a><span data-ttu-id="c7315-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7315-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7315-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c7315-104">Product Name</span></span>|<span data-ttu-id="c7315-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c7315-105">SQL Server</span></span>|  
|<span data-ttu-id="c7315-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c7315-106">Event ID</span></span>|<span data-ttu-id="c7315-107">17066</span><span class="sxs-lookup"><span data-stu-id="c7315-107">17066</span></span>|  
|<span data-ttu-id="c7315-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c7315-108">Event Source</span></span>|<span data-ttu-id="c7315-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c7315-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c7315-110">元件</span><span class="sxs-lookup"><span data-stu-id="c7315-110">Component</span></span>|<span data-ttu-id="c7315-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c7315-111">SQLEngine</span></span>|  
|<span data-ttu-id="c7315-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c7315-112">Symbolic Name</span></span>|<span data-ttu-id="c7315-113">SQLASSERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="c7315-113">SQLASSERT_ONLY</span></span>|  
|<span data-ttu-id="c7315-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c7315-114">Message Text</span></span>|<span data-ttu-id="c7315-115">SQL Server 判斷提示:檔案: \<%s>，行 = %d 失敗的判斷提示 = '%s'。</span><span class="sxs-lookup"><span data-stu-id="c7315-115">SQL Server Assertion: File: \<%s>, line=%d Failed Assertion = '%s'.</span></span> <span data-ttu-id="c7315-116">此錯誤可能與時間有關。</span><span class="sxs-lookup"><span data-stu-id="c7315-116">This error may be timing-related.</span></span> <span data-ttu-id="c7315-117">如果重新執行陳述式之後仍然發生此錯誤，請使用 DBCC CHECKDB 來檢查資料庫的結構完整性，或重新啟動伺服器以確定記憶體中的資料結構並未損毀。</span><span class="sxs-lookup"><span data-stu-id="c7315-117">If the error persists after rerunning the statement, use DBCC CHECKDB to check the database for structural integrity, or restart the server to ensure in-memory data structures are not corrupted.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c7315-118">說明</span><span class="sxs-lookup"><span data-stu-id="c7315-118">Explanation</span></span>  
 <span data-ttu-id="c7315-119">這項錯誤可能是由暫時性的時間相關錯誤所造成，或由記憶體中或磁碟內存的資料損毀所造成。</span><span class="sxs-lookup"><span data-stu-id="c7315-119">This error can be caused by transient, timing-related errors, or by in-memory or on-disk data corruption.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c7315-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c7315-120">User Action</span></span>  
 <span data-ttu-id="c7315-121">請重新執行導致引發此例外狀況的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c7315-121">Rerun the statement that caused the exception to fire.</span></span> <span data-ttu-id="c7315-122">如果此錯誤是由時間相關的事件所造成，此錯誤可能不會再次發生。</span><span class="sxs-lookup"><span data-stu-id="c7315-122">If the error was caused by a timing-related event, the error may not recur.</span></span> <span data-ttu-id="c7315-123">如果持續發生此問題，請執行 DBCC CHECKDB 來檢查是否有磁碟內存的損毀。</span><span class="sxs-lookup"><span data-stu-id="c7315-123">If the problem persists, run DBCC CHECKDB to  check for on-disk corruption.</span></span> <span data-ttu-id="c7315-124">重新啟動伺服器，以便確保記憶體中的資料結構並未損毀。</span><span class="sxs-lookup"><span data-stu-id="c7315-124">Restart the server to ensure that the in-memory data structures are not corrupted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7315-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7315-125">See Also</span></span>  
 [<span data-ttu-id="c7315-126">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7315-126">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
