---
title: 資料庫鏡像或 AlwaysOn 可用性群組 (SQL Server) 不支援跨資料庫交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- cross-database transactions [SQL Server]
- transactions [database mirroring]
- Availability Groups [SQL Server], interoperability
- troubleshooting [SQL Server], cross-database transactions
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a0e23e073375c8f00317003635df8ec0b69883cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708642"
---
# <a name="cross-database-transactions-not-supported-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a><span data-ttu-id="3bc17-102">資料庫鏡像或 AlwaysOn 可用性群組不支援跨資料庫交易 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3bc17-102">Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="3bc17-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]或資料庫鏡像皆不支援跨資料庫交易和分散式交易。</span><span class="sxs-lookup"><span data-stu-id="3bc17-103">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] or by database mirroring.</span></span> <span data-ttu-id="3bc17-104">這是因為無法確保交易不可部分完成性/完整性，原因如下：</span><span class="sxs-lookup"><span data-stu-id="3bc17-104">This is because transaction atomicity/integrity cannot be guaranteed for the following reasons:</span></span>  
  
-   <span data-ttu-id="3bc17-105">對於跨資料庫交易：每個資料庫都會獨立認可。</span><span class="sxs-lookup"><span data-stu-id="3bc17-105">For cross-database transactions: Each database commits independently.</span></span> <span data-ttu-id="3bc17-106">因此，即使資料庫是在單一可用性群組中，在某個資料庫認可交易之後，但在另一個資料庫認可交易之前可能會發生容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="3bc17-106">Therefore, even for databases in a single availability group, a failover could occur after one database commits a transaction but before the other database does.</span></span> <span data-ttu-id="3bc17-107">對於資料庫鏡像，此問題更為複雜，因為在容錯移轉之後，鏡像資料庫通常與另一個資料庫位於不同的伺服器執行個體，即使兩個資料庫是在相同的兩個夥伴之間建立鏡像，也無法確保這兩個資料庫會同時容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="3bc17-107">For database mirroring this issue is compounded because after a failover, the mirrored database is typically on a different server instance from the other database, and  even if both databases are mirrored between the same two partners, there is no guarantee that both databases will fail over at the same time.</span></span>  
  
-   <span data-ttu-id="3bc17-108">對於分散式交易：在容錯移轉之後，新的主體伺服器/主要複本無法連接到先前主體伺服器/主要複本上的分散式交易協調器。</span><span class="sxs-lookup"><span data-stu-id="3bc17-108">For distributed transactions: After a failover, the new principal server/primary replica is unable to connect to the distributed transaction coordinator on the previous principal server/primary replica.</span></span> <span data-ttu-id="3bc17-109">因此，新的主體伺服器/主要複本無法取得交易狀態。</span><span class="sxs-lookup"><span data-stu-id="3bc17-109">Therefore, the new principal server/primary replica cannot obtain the transaction status.</span></span>  
  
 <span data-ttu-id="3bc17-110">下列資料庫鏡像範例將說明如何發生邏輯不一致的情況。</span><span class="sxs-lookup"><span data-stu-id="3bc17-110">The following database mirroring example illustrates how a logical inconsistency could occur.</span></span> <span data-ttu-id="3bc17-111">在此範例中，應用程式會使用跨資料庫交易來插入兩個資料列：其中一個資料列會插入鏡像資料庫 A 中的資料表，而另一個資料列則插入另一個資料庫 B 中的資料表。然後，資料庫 A 會在具有自動容錯移轉的高安全性模式下進行鏡像。</span><span class="sxs-lookup"><span data-stu-id="3bc17-111">In this example, an application uses a cross-database transaction to insert two rows of data: one row is inserted into a table in a mirrored database, A, and the other row is inserted into a table in another database, B. Database A is being mirrored in high-safety mode with automatic failover.</span></span> <span data-ttu-id="3bc17-112">認可交易時，資料庫 A 會無法使用，而鏡像工作階段便自動容錯移轉至資料庫 A 的鏡像。</span><span class="sxs-lookup"><span data-stu-id="3bc17-112">While the transaction is being committed, database A becomes unavailable, and the mirroring session automatically fails over to the mirror of database A.</span></span>  
  
 <span data-ttu-id="3bc17-113">容錯移轉之後，在資料庫 B 上認可跨資料庫交易可能會成功，但不見得能順利在容錯移轉資料庫上認可。</span><span class="sxs-lookup"><span data-stu-id="3bc17-113">After the failover, the cross-database transaction might be successfully committed on database B but not on the failed-over database.</span></span> <span data-ttu-id="3bc17-114">如果資料庫 A 的原始主體伺服器在故障之前尚未將跨資料庫交易的記錄傳送至鏡像伺服器，就可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="3bc17-114">This would occur if the original principal server for database A had not sent the log for the cross-database transaction to the mirror server before the failure.</span></span> <span data-ttu-id="3bc17-115">容錯移轉之後，該筆交易不會存在新主體伺服器上。</span><span class="sxs-lookup"><span data-stu-id="3bc17-115">After the failover, that transaction would not exist on the new principal server.</span></span> <span data-ttu-id="3bc17-116">資料庫 A 和 B 會成為不一致，因為插入資料庫 B 的資料仍維持完整，但是插入資料庫 A 的資料已經遺失。</span><span class="sxs-lookup"><span data-stu-id="3bc17-116">Databases A and B would become inconsistent, because the data inserted in database B remains intact, but the data inserted in database A has been lost.</span></span>  
  
 <span data-ttu-id="3bc17-117">使用 MS DTC 交易時可能也會發生類似的狀況。</span><span class="sxs-lookup"><span data-stu-id="3bc17-117">A similar scenario can occur while using a MS DTC transaction.</span></span> <span data-ttu-id="3bc17-118">例如，在容錯移轉之後，新的主體會連絡 MS DTC。</span><span class="sxs-lookup"><span data-stu-id="3bc17-118">For example, after failover, the new principal contacts MS DTC.</span></span> <span data-ttu-id="3bc17-119">不過，MS DTC 並不了解新的主體伺服器，而且它會結束「準備認可」的所有交易，因為它認為這些交易已在其他資料庫中認可。</span><span class="sxs-lookup"><span data-stu-id="3bc17-119">But MS DTC has no knowledge of the new principal server, and it terminates any transactions that are "preparing to commit," which are considered committed in other databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3bc17-120">搭配 DTC 使用資料庫鏡像或可用性群組不會導致不支援 SQL Server 安裝。</span><span class="sxs-lookup"><span data-stu-id="3bc17-120">Using Database Mirroring or Availability Groups together with DTC does not result in an unsupported SQL Server installation.</span></span> <span data-ttu-id="3bc17-121">不過，如果資料庫是資料庫鏡像工作階段或可用性群組的一部分，且 DTC 同時用於此資料庫，則 Microsoft 只會調查與搭配 DTC 使用資料庫鏡像或可用性群組無關的支援問題。</span><span class="sxs-lookup"><span data-stu-id="3bc17-121">If, however, a database is part of a Database Mirroring session or an Availability Group and DTC is also used in the database, support issues will be investigated by Microsoft only if unrelated to the combined use of Database Mirroring or Availability Groups with DTC.</span></span>  
  
  
