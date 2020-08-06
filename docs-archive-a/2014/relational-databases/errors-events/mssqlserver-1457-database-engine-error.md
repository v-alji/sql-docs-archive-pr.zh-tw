---
title: MSSQLSERVER_1457 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c30ee6149c95d93bdaf1d2877f5fe1871a575ec1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598959"
---
# <a name="mssqlserver_1457"></a><span data-ttu-id="e3395-102">MSSQLSERVER_1457</span><span class="sxs-lookup"><span data-stu-id="e3395-102">MSSQLSERVER_1457</span></span>
    
## <a name="details"></a><span data-ttu-id="e3395-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e3395-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3395-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e3395-104">Product Name</span></span>|<span data-ttu-id="e3395-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e3395-105">SQL Server</span></span>|  
|<span data-ttu-id="e3395-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e3395-106">Event ID</span></span>|<span data-ttu-id="e3395-107">1457</span><span class="sxs-lookup"><span data-stu-id="e3395-107">1457</span></span>|  
|<span data-ttu-id="e3395-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e3395-108">Event Source</span></span>|<span data-ttu-id="e3395-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e3395-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e3395-110">元件</span><span class="sxs-lookup"><span data-stu-id="e3395-110">Component</span></span>|<span data-ttu-id="e3395-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e3395-111">SQLEngine</span></span>|  
|<span data-ttu-id="e3395-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e3395-112">Symbolic Name</span></span>|<span data-ttu-id="e3395-113">DBM_PAGE_UNDO_PENDING</span><span class="sxs-lookup"><span data-stu-id="e3395-113">DBM_PAGE_UNDO_PENDING</span></span>|  
|<span data-ttu-id="e3395-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e3395-114">Message Text</span></span>|<span data-ttu-id="e3395-115">鏡像資料庫 '%.\*ls' 的同步處理已中斷，導致資料庫成為不一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="e3395-115">Synchronization of the mirror database, '%.\*ls', was interrupted, leaving the database in an inconsistent state.</span></span> <span data-ttu-id="e3395-116">ALTER DATABASE 命令失敗。</span><span class="sxs-lookup"><span data-stu-id="e3395-116">The ALTER DATABASE command failed.</span></span> <span data-ttu-id="e3395-117">請確定鏡像資料庫有備份且在線上，然後重新連接鏡像伺服器執行個體，讓鏡像資料庫能夠完成同步處理。</span><span class="sxs-lookup"><span data-stu-id="e3395-117">Ensure that the mirror database is back up and online, and then reconnect the mirror server instance and allow the mirror database to finish synchronizing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e3395-118">說明</span><span class="sxs-lookup"><span data-stu-id="e3395-118">Explanation</span></span>  
 <span data-ttu-id="e3395-119">此訊息表示 ALTER DATABASE *database_name* SET PARTNER OFF 陳述式失敗。</span><span class="sxs-lookup"><span data-stu-id="e3395-119">This messages indicates that the ALTER DATABASE *database_name* SET PARTNER OFF statement has failed.</span></span> <span data-ttu-id="e3395-120">嘗試移除資料庫鏡像失敗，導致鏡像資料庫的同步處理中斷。</span><span class="sxs-lookup"><span data-stu-id="e3395-120">The failed attempt to remove database mirroring interrupted synchronization of the mirror database.</span></span> <span data-ttu-id="e3395-121">資料庫的狀態不一致。</span><span class="sxs-lookup"><span data-stu-id="e3395-121">The database is in an inconsistent state.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e3395-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e3395-122">User Action</span></span>  
 <span data-ttu-id="e3395-123">若要解決此錯誤，可以採取下列其中一個動作︰</span><span class="sxs-lookup"><span data-stu-id="e3395-123">To resolve this error, you can take either of the following actions:</span></span>  
  
-   <span data-ttu-id="e3395-124">還原鏡像伺服器與主體伺服器之間的連絡，讓鏡像資料庫進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="e3395-124">Restore contact between the mirror server and the principal server to allow for the mirror database to synchronize.</span></span>  
  
-   <span data-ttu-id="e3395-125">卸除鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="e3395-125">Drop the mirror database.</span></span>  
  
     <span data-ttu-id="e3395-126">卸除鏡像資料庫之後，您就可以從備份建立新的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="e3395-126">After you drop the mirror database, you can create a new mirror database from backups.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e3395-127">只有在 SET PARTNER OFF 陳述式失敗之後，才能在鏡像仍為啟用狀態的情況下卸除鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="e3395-127">You can drop the mirror database when mirroring is still enabled only after a failed SET PARTNER OFF statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3395-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3395-128">See Also</span></span>  
 <span data-ttu-id="e3395-129">[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e3395-129">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="e3395-130">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e3395-130">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="e3395-131">[設定資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e3395-131">[Setting Up Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="e3395-132">[移除資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e3395-132">[Removing Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="e3395-133">準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e3395-133">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
  
