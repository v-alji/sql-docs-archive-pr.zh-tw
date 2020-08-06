---
title: 資料庫鏡像：互通性與共存性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 057392842974c3342fc57d0ec113f8b1bb58b9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594690"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a><span data-ttu-id="1b96d-102">資料庫鏡像：互通性與共存性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1b96d-102">Database Mirroring: Interoperability and Coexistence (SQL Server)</span></span>
  <span data-ttu-id="1b96d-103">資料庫鏡像可與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的下列功能或元件搭配使用：</span><span class="sxs-lookup"><span data-stu-id="1b96d-103">Database mirroring can be used with the following features or components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="1b96d-104">AlwaysOn 容錯移轉叢集執行個體 (SQL Server 容錯移轉叢集)</span><span class="sxs-lookup"><span data-stu-id="1b96d-104">AlwaysOn Failover Cluster Instances (SQL Server Failover Clustering)</span></span>](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [<span data-ttu-id="1b96d-105">異動資料擷取與變更追蹤</span><span class="sxs-lookup"><span data-stu-id="1b96d-105">Change data capture (and change tracking)</span></span>](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [<span data-ttu-id="1b96d-106">資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="1b96d-106">Database snapshots</span></span>](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [<span data-ttu-id="1b96d-107">全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="1b96d-107">Full-text catalogs</span></span>](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [<span data-ttu-id="1b96d-108">記錄傳送</span><span class="sxs-lookup"><span data-stu-id="1b96d-108">Log shipping</span></span>](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="1b96d-109">複寫</span><span class="sxs-lookup"><span data-stu-id="1b96d-109">Replication</span></span>](database-mirroring-and-replication-sql-server.md)  
  
 <span data-ttu-id="1b96d-110">資料庫鏡像不會與下列項目交互操作：</span><span class="sxs-lookup"><span data-stu-id="1b96d-110">Database mirroring does not interoperate with the following:</span></span>  
  
-   <span data-ttu-id="1b96d-111">跨資料庫交易/分散式交易</span><span class="sxs-lookup"><span data-stu-id="1b96d-111">Cross-database transactions/distributed transactions</span></span>  
  
     <span data-ttu-id="1b96d-112">如需這類交易不受支援之原因的相關資訊，請參閱[資料庫鏡像或 AlwaysOn 可用性群組不支援跨資料庫交易 &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="1b96d-112">For information about why such transactions are not supported, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1b96d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b96d-113">See Also</span></span>  
 [<span data-ttu-id="1b96d-114">資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1b96d-114">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
