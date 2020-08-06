---
title: 移除資料庫鏡像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- stopping database mirroring [SQL Server]
- removing database mirroring [SQL Server]
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8044fcef9d9f9bfc1fb41c1faa17b76c827da5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701794"
---
# <a name="removing-database-mirroring-sql-server"></a><span data-ttu-id="f712c-102">移除資料庫鏡像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f712c-102">Removing Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="f712c-103">資料庫擁有者可隨時在夥伴上手動停止資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="f712c-103">The database owner can manually stop a database mirroring session at any time, at either partner.</span></span>  
  
## <a name="impact-of-removing-mirroring"></a><span data-ttu-id="f712c-104">移除鏡像的影響</span><span class="sxs-lookup"><span data-stu-id="f712c-104">Impact of Removing Mirroring</span></span>  
 <span data-ttu-id="f712c-105">移除鏡像後，就會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="f712c-105">When mirroring is removed, the following occurs:</span></span>  
  
-   <span data-ttu-id="f712c-106">夥伴之間以及每個夥伴與見證之間的關聯性會永久中斷 (若有任何關聯性存在的話)。</span><span class="sxs-lookup"><span data-stu-id="f712c-106">The relationship between the partners and between each partner and the witness breaks permanently, if any relationship exists.</span></span>  
  
     <span data-ttu-id="f712c-107">若工作階段停止時夥伴伺服器正在與其他夥伴伺服器通訊，則會立即在這兩台電腦上中斷其關係。</span><span class="sxs-lookup"><span data-stu-id="f712c-107">If the partners are communicating with each other when the session is stopped, their relationship is immediately broken on both computers.</span></span> <span data-ttu-id="f712c-108">如果夥伴伺服器並未在通訊 (停止時資料庫正處於 DISCONNECTED 狀態)，則會立即在停止鏡像的夥伴伺服器上中斷關係；如果其他夥伴伺服器嘗試要重新連接，則會發現資料庫鏡像工作階段已結束。</span><span class="sxs-lookup"><span data-stu-id="f712c-108">If the partners are not communicating (the database is in a DISCONNECTED state at the time of stopping), the relationship is broken immediately on the partner from which mirroring is stopped; when the other partner tries to reconnect, it discovers that the database mirroring session has ended.</span></span>  
  
-   <span data-ttu-id="f712c-109">與暫停工作階段不同，鏡像工作階段的相關資訊會被卸除。</span><span class="sxs-lookup"><span data-stu-id="f712c-109">Information about the mirroring session is dropped, unlike when pausing a session.</span></span> <span data-ttu-id="f712c-110">也會移除主體資料庫和鏡像資料庫上的鏡像。</span><span class="sxs-lookup"><span data-stu-id="f712c-110">Mirroring is removed on both the principal database and the mirror database.</span></span> <span data-ttu-id="f712c-111">在 **sys.databases** 中，**mirroring_state** 資料行和所有其他鏡像資料行都會設定為 NULL。</span><span class="sxs-lookup"><span data-stu-id="f712c-111">In **sys.databases**, the **mirroring_state** column and all other mirroring columns are set to NULL.</span></span> <span data-ttu-id="f712c-112">如需詳細資訊，請參閱 [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f712c-112">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
-   <span data-ttu-id="f712c-113">每個夥伴伺服器執行個體都會保有個別的資料庫副本。</span><span class="sxs-lookup"><span data-stu-id="f712c-113">Each partner server instance is left with a separate copy of the database.</span></span>  
  
-   <span data-ttu-id="f712c-114">因為鏡像資料庫是利用 RESTORE WITH NORECOVERY 建立的，所以它會處於 RESTORING 狀態 (請參閱 **sys.databases** 的 **state**資料行)。</span><span class="sxs-lookup"><span data-stu-id="f712c-114">The mirror database is left in the RESTORING state (see the **state** column of **sys.databases**), because the mirror database was created by using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="f712c-115">此時，您可卸除先前的鏡像資料庫，或利用 WITH RECOVERY 予以還原。</span><span class="sxs-lookup"><span data-stu-id="f712c-115">At this point, you can drop the former mirror database or restore it using WITH RECOVERY.</span></span> <span data-ttu-id="f712c-116">當您復原資料庫時，因為復原會啟動新的復原分岔，所以與先前的主體資料庫有所差異。</span><span class="sxs-lookup"><span data-stu-id="f712c-116">When you recover the database, it will have diverged from the former principal database because the recovery starts a new recovery fork.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f712c-117">若要在停止工作階段之後繼續鏡像，您就必須建立新的資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="f712c-117">To continue mirroring after stopping a session, you must establish a new database mirroring session.</span></span> <span data-ttu-id="f712c-118">若要在停止鏡像之後建立記錄備份，您必須在重新啟動鏡像之前將它套用到鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="f712c-118">If you create a log backup after stopping mirroring, you must apply it to the mirror database before restarting mirroring.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f712c-119">相關工作</span><span class="sxs-lookup"><span data-stu-id="f712c-119">Related Tasks</span></span>  
 <span data-ttu-id="f712c-120">**若要移除資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="f712c-120">**To remove database mirroring**</span></span>  
  
-   [<span data-ttu-id="f712c-121">移除資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f712c-121">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
 <span data-ttu-id="f712c-122">**若要啟動資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="f712c-122">**To start database mirroring**</span></span>  
  
-   [<span data-ttu-id="f712c-123">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f712c-123">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="f712c-124">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f712c-124">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="f712c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f712c-125">See Also</span></span>  
 <span data-ttu-id="f712c-126">[ALTER DATABASE 資料庫鏡像 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="f712c-126">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="f712c-127">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f712c-127">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="f712c-128">[暫停與繼續資料庫鏡像 &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f712c-128">[Pausing and Resuming Database Mirroring &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="f712c-129">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f712c-129">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
