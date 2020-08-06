---
title: 手動容錯移轉資料庫鏡像工作階段 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c04ea4908ccbc4cfe4f6bb3606347dd444ef416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592196"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="85670-102">手動容錯移轉資料庫鏡像工作階段 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="85670-102">Manually Fail Over a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="85670-103">鏡像資料庫已同步處理時 (亦即，資料庫為 SYNCHRONIZED 狀態時)，資料庫擁有者可以初始化至鏡像伺服器的手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="85670-103">When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server.</span></span> <span data-ttu-id="85670-104">手動容錯移轉只能從主體伺服器中起始。</span><span class="sxs-lookup"><span data-stu-id="85670-104">Manual failover can be initiated only from the principal server.</span></span>  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a><span data-ttu-id="85670-105">手動容錯移轉資料庫鏡像工作階段</span><span class="sxs-lookup"><span data-stu-id="85670-105">To manually fail over a database mirroring session</span></span>  
  
1.  <span data-ttu-id="85670-106">連接到主體伺服器。</span><span class="sxs-lookup"><span data-stu-id="85670-106">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="85670-107">將資料庫內容設定為 **master** 資料庫：</span><span class="sxs-lookup"><span data-stu-id="85670-107">Set the database context to the **master** database:</span></span>  
  
     `USE master;`  
  
3.  <span data-ttu-id="85670-108">在主體伺服器上發出下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="85670-108">Issue the following statement on the principal server:</span></span>  
  
     <span data-ttu-id="85670-109">[ALTER DATABASE 資料庫名稱](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) \*\* SET PARTNER FAILOVER，其中「資料庫名稱」\*\* 是鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="85670-109">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET PARTNER FAILOVER, where *database_name* is the mirrored database.</span></span>  
  
     <span data-ttu-id="85670-110">如此可將鏡像伺服器立即轉換為主體角色。</span><span class="sxs-lookup"><span data-stu-id="85670-110">This initiates an immediate transition of the mirror server to the principal role.</span></span>  
  
 <span data-ttu-id="85670-111">在先前的主體伺服器上，用戶端與資料庫的連接會中斷，進行中的交易則會回復。</span><span class="sxs-lookup"><span data-stu-id="85670-111">On the former principal, clients are disconnected from the database and in-flight transactions are rolled back.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85670-112">在容錯移轉發生時，凡是已利用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器準備好但尚未認可的交易，都會在資料庫完成容錯移轉後視為已中止。</span><span class="sxs-lookup"><span data-stu-id="85670-112">Transactions that have been prepared by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator but are still not committed when a failover occurs are considered aborted after the database has failed over.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85670-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85670-113">See Also</span></span>  
 <span data-ttu-id="85670-114">[ALTER DATABASE 資料庫鏡像 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="85670-114">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="85670-115">[手動故障切換資料庫鏡像會話 &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="85670-115">[Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="85670-116">資料庫鏡像工作階段期間的角色切換 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="85670-116">Role Switching During a Database Mirroring Session &#40;SQL Server&#41;</span></span>](role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
