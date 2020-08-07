---
title: MSSQLSERVER_3414 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3414 (Database Engine error)
ms.assetid: f25852f9-b91c-4356-b817-78bec9ec8db4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aecaf2a920552b8ea66804600fa8bd4168175e53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598901"
---
# <a name="mssqlserver_3414"></a><span data-ttu-id="c1213-102">MSSQLSERVER_3414</span><span class="sxs-lookup"><span data-stu-id="c1213-102">MSSQLSERVER_3414</span></span>
    
## <a name="details"></a><span data-ttu-id="c1213-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c1213-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1213-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c1213-104">Product Name</span></span>|<span data-ttu-id="c1213-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c1213-105">SQL Server</span></span>|  
|<span data-ttu-id="c1213-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c1213-106">Event ID</span></span>|<span data-ttu-id="c1213-107">3414</span><span class="sxs-lookup"><span data-stu-id="c1213-107">3414</span></span>|  
|<span data-ttu-id="c1213-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c1213-108">Event Source</span></span>|<span data-ttu-id="c1213-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c1213-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c1213-110">元件</span><span class="sxs-lookup"><span data-stu-id="c1213-110">Component</span></span>|<span data-ttu-id="c1213-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c1213-111">SQLEngine</span></span>|  
|<span data-ttu-id="c1213-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c1213-112">Symbolic Name</span></span>|<span data-ttu-id="c1213-113">REC_GIVEUP</span><span class="sxs-lookup"><span data-stu-id="c1213-113">REC_GIVEUP</span></span>|  
|<span data-ttu-id="c1213-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c1213-114">Message Text</span></span>|<span data-ttu-id="c1213-115">復原時發生錯誤，導致資料庫 '%.\*ls' (資料庫識別碼 %d) 無法重新啟動。</span><span class="sxs-lookup"><span data-stu-id="c1213-115">An error occurred during recovery, preventing the database '%.\*ls' (database ID %d) from restarting.</span></span> <span data-ttu-id="c1213-116">請診斷並修正復原錯誤，或者從已知完好的備份還原。</span><span class="sxs-lookup"><span data-stu-id="c1213-116">Diagnose the recovery errors and fix them, or restore from a known good backup.</span></span> <span data-ttu-id="c1213-117">如果不能更正或預期錯誤，請連絡技術支援部門。</span><span class="sxs-lookup"><span data-stu-id="c1213-117">If errors are not corrected or expected, contact Technical Support.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c1213-118">說明</span><span class="sxs-lookup"><span data-stu-id="c1213-118">Explanation</span></span>  
 <span data-ttu-id="c1213-119">已復原指定的資料庫，但是因為復原期間發生錯誤而無法啟動。</span><span class="sxs-lookup"><span data-stu-id="c1213-119">The specified database was recovered, but failed to start, because errors occurred during recovery.</span></span> <span data-ttu-id="c1213-120">這個錯誤已經將資料庫置於 SUSPECT 狀態。</span><span class="sxs-lookup"><span data-stu-id="c1213-120">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="c1213-121">主要檔案群組以及可能還有其他檔案群組都有疑問，而且可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="c1213-121">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="c1213-122">資料庫在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動期間無法復原，因此無法使用。</span><span class="sxs-lookup"><span data-stu-id="c1213-122">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="c1213-123">需要使用者動作來解決問題。</span><span class="sxs-lookup"><span data-stu-id="c1213-123">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="c1213-124">請注意，如果這個錯誤發生於 **tempdb**， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體會關閉。</span><span class="sxs-lookup"><span data-stu-id="c1213-124">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c1213-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c1213-125">User Action</span></span>  
 <span data-ttu-id="c1213-126">當嘗試啟動伺服器執行個體或復原資料庫時，存在於系統上的暫時性狀況會引發這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1213-126">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="c1213-127">每當您嘗試啟動資料庫時所發生的永久性失敗也會造成這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1213-127">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="c1213-128">如需原因的相關資訊，請檢查 Windows 事件記錄檔，尋找指示特定失敗的先前錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1213-128">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="c1213-129">如需此 3314 錯誤發生原因的詳細資訊，請檢查 Windows 事件記錄檔，尋找指出特定失敗的先前錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1213-129">For information about the cause of this occurrence of error 3414, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="c1213-130">適當的使用者動作取決於 Windows 事件記錄檔中的資訊指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤是由暫時性狀況或永久性失敗所造成。</span><span class="sxs-lookup"><span data-stu-id="c1213-130">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="c1213-131">如需疑難排解錯誤 3314 之使用者動作的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="c1213-131">For information about the user actions for troubleshooting error 3414, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1213-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1213-132">See Also</span></span>  
 <span data-ttu-id="c1213-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c1213-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="c1213-134">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c1213-134">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="c1213-135">[完整資料庫還原 &#40;簡單復原模式&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="c1213-135">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="c1213-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="c1213-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="c1213-137">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c1213-137">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
