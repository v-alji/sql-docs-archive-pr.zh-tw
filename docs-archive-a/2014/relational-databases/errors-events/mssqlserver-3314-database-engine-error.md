---
title: MSSQLSERVER_3314 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3314 (Database Engine error)
ms.assetid: f3a5ca6a-b502-4cab-b3b1-4bc753763fa9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff3b891b438f71d70f5dd62174eae2c5a07d29a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598908"
---
# <a name="mssqlserver_3314"></a><span data-ttu-id="c8b29-102">MSSQLSERVER_3314</span><span class="sxs-lookup"><span data-stu-id="c8b29-102">MSSQLSERVER_3314</span></span>
    
## <a name="details"></a><span data-ttu-id="c8b29-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c8b29-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8b29-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c8b29-104">Product Name</span></span>|<span data-ttu-id="c8b29-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c8b29-105">SQL Server</span></span>|  
|<span data-ttu-id="c8b29-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c8b29-106">Event ID</span></span>|<span data-ttu-id="c8b29-107">3314</span><span class="sxs-lookup"><span data-stu-id="c8b29-107">3314</span></span>|  
|<span data-ttu-id="c8b29-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c8b29-108">Event Source</span></span>|<span data-ttu-id="c8b29-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c8b29-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c8b29-110">元件</span><span class="sxs-lookup"><span data-stu-id="c8b29-110">Component</span></span>|<span data-ttu-id="c8b29-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c8b29-111">SQLEngine</span></span>|  
|<span data-ttu-id="c8b29-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c8b29-112">Symbolic Name</span></span>|<span data-ttu-id="c8b29-113">ERR_LOG_RID2</span><span class="sxs-lookup"><span data-stu-id="c8b29-113">ERR_LOG_RID2</span></span>|  
|<span data-ttu-id="c8b29-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c8b29-114">Message Text</span></span>|<span data-ttu-id="c8b29-115">恢復資料庫 '%.\*ls' 已記錄的作業時，記錄識別碼 %S_LSN 發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8b29-115">During undoing of a logged operation in database '%.\*ls', an error occurred at log record ID %S_LSN.</span></span> <span data-ttu-id="c8b29-116">一般而言，之前是將該錯誤記錄為 Windows 事件記錄檔服務的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8b29-116">Typically, the specific failure is logged previously as an error in the Windows Event Log service.</span></span> <span data-ttu-id="c8b29-117">請從備份中還原資料庫或檔案，或修復資料庫。</span><span class="sxs-lookup"><span data-stu-id="c8b29-117">Restore the database or file from a backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c8b29-118">說明</span><span class="sxs-lookup"><span data-stu-id="c8b29-118">Explanation</span></span>  
 <span data-ttu-id="c8b29-119">這是恢復復原的積存錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8b29-119">This is a rollup error for undo recovery.</span></span> <span data-ttu-id="c8b29-120">這個錯誤已經將資料庫置於 SUSPECT 狀態。</span><span class="sxs-lookup"><span data-stu-id="c8b29-120">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="c8b29-121">主要檔案群組以及可能還有其他檔案群組都有疑問，而且可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="c8b29-121">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="c8b29-122">資料庫在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動期間無法復原，因此無法使用。</span><span class="sxs-lookup"><span data-stu-id="c8b29-122">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="c8b29-123">需要使用者動作來解決問題。</span><span class="sxs-lookup"><span data-stu-id="c8b29-123">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="c8b29-124">請注意，如果這個錯誤發生於 **tempdb**， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體會關閉。</span><span class="sxs-lookup"><span data-stu-id="c8b29-124">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c8b29-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c8b29-125">User Action</span></span>  
 <span data-ttu-id="c8b29-126">當嘗試啟動伺服器執行個體或復原資料庫時，存在於系統上的暫時性狀況會引發這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8b29-126">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="c8b29-127">每當您嘗試啟動資料庫時所發生的永久性失敗也會造成這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8b29-127">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="c8b29-128">如需原因的相關資訊，請檢查 Windows 事件記錄檔，尋找指示特定失敗的先前錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8b29-128">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="c8b29-129">如需有關此 3314 錯誤發生原因的詳細資訊，請檢查 Windows 事件記錄檔，尋找指出特定失敗的先前錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8b29-129">For information about the cause of this occurrence of error 3314, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="c8b29-130">適當的使用者動作取決於 Windows 事件記錄檔中的資訊指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤是由暫時性狀況或永久性失敗所造成。</span><span class="sxs-lookup"><span data-stu-id="c8b29-130">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="c8b29-131">如需有關疑難排解錯誤 3314 之使用者動作的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="c8b29-131">For information about the user actions for troubleshooting error 3314, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b29-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8b29-132">See Also</span></span>  
 <span data-ttu-id="c8b29-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8b29-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="c8b29-134">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8b29-134">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="c8b29-135">[完整資料庫還原 &#40;簡單復原模式&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="c8b29-135">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="c8b29-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="c8b29-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="c8b29-137">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c8b29-137">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
