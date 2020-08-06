---
title: MSSQL_ENG003165 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003165 error
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1702588ba6ac1beeb33b87a7afc7fc330271559
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584425"
---
# <a name="mssql_eng003165"></a><span data-ttu-id="dc9ab-102">MSSQL_ENG003165</span><span class="sxs-lookup"><span data-stu-id="dc9ab-102">MSSQL_ENG003165</span></span>
    
## <a name="message-details"></a><span data-ttu-id="dc9ab-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="dc9ab-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc9ab-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dc9ab-104">Product Name</span></span>|<span data-ttu-id="dc9ab-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dc9ab-105">SQL Server</span></span>|  
|<span data-ttu-id="dc9ab-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dc9ab-106">Event ID</span></span>|<span data-ttu-id="dc9ab-107">3165</span><span class="sxs-lookup"><span data-stu-id="dc9ab-107">3165</span></span>|  
|<span data-ttu-id="dc9ab-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="dc9ab-108">Event Source</span></span>|<span data-ttu-id="dc9ab-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dc9ab-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dc9ab-110">元件</span><span class="sxs-lookup"><span data-stu-id="dc9ab-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="dc9ab-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dc9ab-111">Symbolic Name</span></span>||  
|<span data-ttu-id="dc9ab-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dc9ab-112">Message Text</span></span>|<span data-ttu-id="dc9ab-113">資料庫 '%ls' 已還原，不過在還原/移除複寫時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-113">Database '%ls' was restored; however, an error was encountered while replication was being restored/removed.</span></span> <span data-ttu-id="dc9ab-114">資料庫已保持離線。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-114">The database has been left offline.</span></span> <span data-ttu-id="dc9ab-115">請參閱《SQL Server 線上叢書》中的主題＜MSSQL_ENG003165＞。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-115">See the topic MSSQL_ENG003165 in SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dc9ab-116">說明</span><span class="sxs-lookup"><span data-stu-id="dc9ab-116">Explanation</span></span>  
 <span data-ttu-id="dc9ab-117">如果在還原複寫資料庫的備份時出現錯誤，將引發此錯誤：</span><span class="sxs-lookup"><span data-stu-id="dc9ab-117">This error is raised if a problem occurs restoring a backup of a replicated database:</span></span>  
  
-   <span data-ttu-id="dc9ab-118">如果將備份還原至執行備份的資料庫和伺服器，此錯誤表示複寫設定無法正確還原。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-118">If the backup is being restored to the same database and server on which it was taken, the error indicates that replication settings could not be restored properly.</span></span>  
  
-   <span data-ttu-id="dc9ab-119">如果將備份還原至不同的資料庫或伺服器，此錯誤表示複寫設定無法正確移除 (依預設，如果資料庫或伺服器不同，將移除複寫設定)。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-119">If the backup is being restored to a different database or server, the error indicates that replication settings could not be removed properly (by default, replication settings are removed if the database or server is different).</span></span>  
  
 <span data-ttu-id="dc9ab-120">此錯誤可能是由於，還原的資料庫與包含複寫中繼資料的一個或多個系統資料庫 ( **msdb**、 **master**或散發資料庫) 之間狀態不符而導致。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-120">The error is probably the result of a mismatch between the state of the restored database and one or more system databases that contain replication metadata: **msdb**, **master**, or the distribution database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dc9ab-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dc9ab-121">User Action</span></span>  
 <span data-ttu-id="dc9ab-122">若要解決此問題：</span><span class="sxs-lookup"><span data-stu-id="dc9ab-122">To resolve this issue:</span></span>  
  
1.  <span data-ttu-id="dc9ab-123">請執行 ALTER DATABASE 以使資料庫連線；例如： `ALTER DATABASE AdventureWorks SET ONLINE`。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-123">Execute ALTER DATABASE to bring the database online; for example: `ALTER DATABASE AdventureWorks SET ONLINE`.</span></span> <span data-ttu-id="dc9ab-124">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-124">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span> <span data-ttu-id="dc9ab-125">如果您要保留複寫設定，請移至步驟 2。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-125">If you want to preserve replication settings, go to step 2.</span></span> <span data-ttu-id="dc9ab-126">如果沒有，請移至步驟 3。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-126">If not, go to step 3.</span></span>  
  
2.  <span data-ttu-id="dc9ab-127">執行 [sp_restoredbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-127">Execute [sp_restoredbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql).</span></span> <span data-ttu-id="dc9ab-128">如果此預存程序成功執行，則還原完成。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-128">If this stored procedure executes successfully, the restore is complete.</span></span> <span data-ttu-id="dc9ab-129">如果未成功執行，請移至步驟 3。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-129">If it does not execute successfully, go to step 3.</span></span>  
  
3.  <span data-ttu-id="dc9ab-130">執行 [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 以移除所有複寫設定。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-130">Execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove all replication settings.</span></span>  
  
     <span data-ttu-id="dc9ab-131">必要時請重新設定複寫。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-131">Reconfigure replication if necessary.</span></span> <span data-ttu-id="dc9ab-132">如果您已根據建議編寫了複寫拓撲的指令碼，請使用指令碼以重新設定拓撲。</span><span class="sxs-lookup"><span data-stu-id="dc9ab-132">If you have scripted the replication topology as recommended, use scripts to reconfigure the topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc9ab-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc9ab-133">See Also</span></span>  
 <span data-ttu-id="dc9ab-134">[SQL Server 資料庫的備份與還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="dc9ab-134">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="dc9ab-135">[備份及還原複寫的資料庫](administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="dc9ab-135">[Back Up and Restore Replicated Databases](administration/back-up-and-restore-replicated-databases.md) </span></span>  
 [<span data-ttu-id="dc9ab-136">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="dc9ab-136">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
