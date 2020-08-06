---
title: 具有 AlwaysOn 可用性群組 (SQL Server) 的資料庫快照集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 7432da1c-ce2f-4cd9-af41-54c97744166b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1e4307653b5b8150d71019a373ee073d15123f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705438"
---
# <a name="database-snapshots-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="4ce70-102">資料庫快照集與 AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4ce70-102">Database Snapshots with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="4ce70-103">您可以在可用性群組的主要或次要資料庫上建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="4ce70-103">You can create a database snapshot on an primary or secondary database in an availability group.</span></span> <span data-ttu-id="4ce70-104">複本角色必須是不在 RESOLVING 狀態的 PRIMARY 或 SECONDARY。</span><span class="sxs-lookup"><span data-stu-id="4ce70-104">The replica role must be either PRIMARY or SECONDARY, not in the RESOLVING state.</span></span>  
  
 <span data-ttu-id="4ce70-105">當您建立資料庫快照集時，建議資料庫同步處理狀態為 SYNCHRONIZING 或 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="4ce70-105">We recommend that the database synchronization state be SYNCHRONIZING or SYNCHRONIZED when you create a database snapshot.</span></span> <span data-ttu-id="4ce70-106">但是，當資料庫同步處理狀態為 NOT SYNCHRONIZING 時，可以建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="4ce70-106">However, database snapshots can be created when the database synchronization state is NOT SYNCHRONIZING.</span></span>  
  
 <span data-ttu-id="4ce70-107">如果次要複本與主要複本中斷連接 (DISCONNECTED)，則此次要複本上的資料庫快照集應該繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4ce70-107">A database snapshot on a secondary replica should continue to work if the replica is DISCONNECTED from the primary replica.</span></span>  
  
 <span data-ttu-id="4ce70-108">某些 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 情況會導致來源資料庫及其資料庫快照集重新啟動，暫時中斷使用者連接。</span><span class="sxs-lookup"><span data-stu-id="4ce70-108">Some [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] conditions cause both the source database and its database snapshots to be restarted, temporarily disconnecting users.</span></span> <span data-ttu-id="4ce70-109">這些情況如下：</span><span class="sxs-lookup"><span data-stu-id="4ce70-109">These conditions are as follows:</span></span>  
  
-   <span data-ttu-id="4ce70-110">主要複本變更角色，無論是因為目前主要複本離線並且在相同伺服器執行個體上恢復連線狀態，還是因為可用性群組容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="4ce70-110">The primary replica changes roles, whether because the current primary replica goes off line and comes back online on the same server instance or because the availability group fails over.</span></span>  
  
-   <span data-ttu-id="4ce70-111">資料庫進入次要角色。</span><span class="sxs-lookup"><span data-stu-id="4ce70-111">The database enters the secondary role.</span></span>  
  
 <span data-ttu-id="4ce70-112">如果裝載資料庫快照集的可用性複本容錯移轉，資料庫快照集會保留在其建立所在的伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="4ce70-112">If the availability replica that hosts database snapshots is failed over, the database snapshots remain on the server instance where they were created.</span></span> <span data-ttu-id="4ce70-113">使用者可以在容錯移轉後繼續使用快照集。如果效能是您的環境中的顧慮，我們建議您只在設定為手動容錯移轉模式的次要複本所裝載的次要資料庫上建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="4ce70-113">Users can continue to use the snapshots after the failover.If performance is a concern in your environment, we recommend that you create database snapshots only on secondary databases that are hosted by a secondary replica that is configured for manual failover mode.</span></span>  <span data-ttu-id="4ce70-114">如果您曾經將可用性群組手動容錯移轉到此次要複本，則可以在其他次要複本上建立一組新的資料庫快照集，將用戶端重新導向至這些新的資料庫快照集，並且從目前主要資料庫上卸除所有資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="4ce70-114">If you ever manually fail over the availability group to this secondary replica, you can create a new set of database snapshots on another secondary replica, redirect clients to the new database snapshots, and drop all of the database snapshots from the now primary databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce70-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ce70-115">See Also</span></span>  
 <span data-ttu-id="4ce70-116">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4ce70-116">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="4ce70-117">資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4ce70-117">Database Snapshots &#40;SQL Server&#41;</span></span>](../../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
