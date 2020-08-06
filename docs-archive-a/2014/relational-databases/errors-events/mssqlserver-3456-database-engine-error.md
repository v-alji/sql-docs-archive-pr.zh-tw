---
title: MSSQLSERVER_3456 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3456 (Database Engine error)
ms.assetid: d11b2b2c-3ae4-4023-b82f-05b561bfacce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f13316bdd3147bb0ad63c8d4a2fb18f1fce74006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701245"
---
# <a name="mssqlserver_3456"></a><span data-ttu-id="5312e-102">MSSQLSERVER_3456</span><span class="sxs-lookup"><span data-stu-id="5312e-102">MSSQLSERVER_3456</span></span>
    
## <a name="details"></a><span data-ttu-id="5312e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5312e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5312e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5312e-104">Product Name</span></span>|<span data-ttu-id="5312e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5312e-105">SQL Server</span></span>|  
|<span data-ttu-id="5312e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5312e-106">Event ID</span></span>|<span data-ttu-id="5312e-107">3456</span><span class="sxs-lookup"><span data-stu-id="5312e-107">3456</span></span>|  
|<span data-ttu-id="5312e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="5312e-108">Event Source</span></span>|<span data-ttu-id="5312e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5312e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5312e-110">元件</span><span class="sxs-lookup"><span data-stu-id="5312e-110">Component</span></span>|<span data-ttu-id="5312e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5312e-111">SQLEngine</span></span>|  
|<span data-ttu-id="5312e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5312e-112">Symbolic Name</span></span>|<span data-ttu-id="5312e-113">REC_REDOLSNMISMATCH</span><span class="sxs-lookup"><span data-stu-id="5312e-113">REC_REDOLSNMISMATCH</span></span>|  
|<span data-ttu-id="5312e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5312e-114">Message Text</span></span>|<span data-ttu-id="5312e-115">無法重做資料庫 '%.\*ls' (資料庫識別碼 %d) 中頁面 %S_PGID 上交易識別碼 %S_XID 的記錄 %S_LSN。</span><span class="sxs-lookup"><span data-stu-id="5312e-115">Could not redo log record %S_LSN, for transaction ID %S_XID, on page %S_PGID, database '%.\*ls' (database ID %d).</span></span> <span data-ttu-id="5312e-116">頁面：LSN = %S_LSN，類型 = %ld。</span><span class="sxs-lookup"><span data-stu-id="5312e-116">Page: LSN = %S_LSN, type = %ld.</span></span> <span data-ttu-id="5312e-117">記錄:OpCode = %ld，內容 %ld，PrevPageLSN: %S_LSN。</span><span class="sxs-lookup"><span data-stu-id="5312e-117">Log: OpCode = %ld, context %ld, PrevPageLSN: %S_LSN.</span></span> <span data-ttu-id="5312e-118">請從資料庫的備份還原或修復資料庫。</span><span class="sxs-lookup"><span data-stu-id="5312e-118">Restore from a backup of the database, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5312e-119">說明</span><span class="sxs-lookup"><span data-stu-id="5312e-119">Explanation</span></span>  
 <span data-ttu-id="5312e-120">還原作業無法重做交易記錄。</span><span class="sxs-lookup"><span data-stu-id="5312e-120">The restore operation was unable to redo the transaction log.</span></span> <span data-ttu-id="5312e-121">這個錯誤已經將資料庫置於 SUSPECT 狀態。</span><span class="sxs-lookup"><span data-stu-id="5312e-121">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="5312e-122">主要檔案群組以及可能還有其他檔案群組都有疑問，而且可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="5312e-122">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="5312e-123">資料庫在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動期間無法復原，因此無法使用。</span><span class="sxs-lookup"><span data-stu-id="5312e-123">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="5312e-124">需要使用者動作來解決問題。</span><span class="sxs-lookup"><span data-stu-id="5312e-124">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="5312e-125">請注意，如果這個錯誤發生於 **tempdb**， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體會關閉。</span><span class="sxs-lookup"><span data-stu-id="5312e-125">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5312e-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5312e-126">User Action</span></span>  
 <span data-ttu-id="5312e-127">當嘗試啟動伺服器執行個體或復原資料庫時，存在於系統上的暫時性狀況會引發這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="5312e-127">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="5312e-128">每當您嘗試啟動資料庫時所發生的永久性失敗也會造成這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="5312e-128">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="5312e-129">如需原因的相關資訊，請檢查 Windows 事件記錄檔，尋找指示特定失敗的先前錯誤。</span><span class="sxs-lookup"><span data-stu-id="5312e-129">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="5312e-130">如需此 3456 錯誤發生原因的詳細資訊，請檢查 Windows 事件記錄檔，尋找指出特定失敗的先前錯誤。</span><span class="sxs-lookup"><span data-stu-id="5312e-130">For information about the cause of this occurrence of error 3456, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="5312e-131">適當的使用者動作取決於 Windows 事件記錄檔中的資訊指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤是由暫時性狀況或永久性失敗所造成。</span><span class="sxs-lookup"><span data-stu-id="5312e-131">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="5312e-132">如需為錯誤 3456 疑難排解之使用者動作的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="5312e-132">For information about the user actions for troubleshooting error 3456, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5312e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5312e-133">See Also</span></span>  
 <span data-ttu-id="5312e-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5312e-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="5312e-135">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5312e-135">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="5312e-136">[完整資料庫還原 &#40;簡單復原模式&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="5312e-136">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="5312e-137">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="5312e-137">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="5312e-138">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5312e-138">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
