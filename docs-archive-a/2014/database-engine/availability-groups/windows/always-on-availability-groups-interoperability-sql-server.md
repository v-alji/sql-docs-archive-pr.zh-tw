---
title: AlwaysOn 可用性群組：互通性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bbd9de348b2e36feefd7efea52dee0b8c13a9f34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592255"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a><span data-ttu-id="d05cb-102">AlwaysOn 可用性群組：互通性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d05cb-102">Always On Availability Groups: Interoperability (SQL Server)</span></span>
  <span data-ttu-id="d05cb-103">本主題記錄 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中其他 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]功能的互通性。</span><span class="sxs-lookup"><span data-stu-id="d05cb-103">This topic documents interoperability of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] with other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a><span data-ttu-id="d05cb-104">與 AlwaysOn 可用性群組互通的功能</span><span class="sxs-lookup"><span data-stu-id="d05cb-104">Features That Interoperate with AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="d05cb-105">下表列出與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 互通的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="d05cb-105">The following table lists [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features that interoperate with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d05cb-106">**[詳細資訊]** 資料行中的連結表示有適用於所指功能的互通性考量。</span><span class="sxs-lookup"><span data-stu-id="d05cb-106">A link in the **More Information** column indicates that interoperability considerations exist for a given feature.</span></span>  
  
|<span data-ttu-id="d05cb-107">特徵</span><span class="sxs-lookup"><span data-stu-id="d05cb-107">Feature</span></span>|<span data-ttu-id="d05cb-108">相關資訊</span><span class="sxs-lookup"><span data-stu-id="d05cb-108">More Information</span></span>|  
|-------------|----------------------|  
|<span data-ttu-id="d05cb-109">變更資料擷取</span><span class="sxs-lookup"><span data-stu-id="d05cb-109">Change data capture</span></span>|[<span data-ttu-id="d05cb-110">複寫、變更追蹤、變更資料捕獲，以及 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-110">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)|  
|<span data-ttu-id="d05cb-111">Change tracking</span><span class="sxs-lookup"><span data-stu-id="d05cb-111">Change tracking</span></span>|[<span data-ttu-id="d05cb-112">複寫、變更追蹤、變更資料捕獲，以及 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-112">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)|  
|<span data-ttu-id="d05cb-113">自主資料庫</span><span class="sxs-lookup"><span data-stu-id="d05cb-113">Contained databases</span></span>|[<span data-ttu-id="d05cb-114">自主資料庫與 AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d05cb-114">Contained Databases with AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="d05cb-115">資料庫加密</span><span class="sxs-lookup"><span data-stu-id="d05cb-115">Database encryption</span></span>|[<span data-ttu-id="d05cb-116">具有 AlwaysOn 可用性群組 &#40;SQL Server 的加密資料庫&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-116">Encrypted Databases with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="d05cb-117">資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="d05cb-117">Database snapshots</span></span>|[<span data-ttu-id="d05cb-118">具有 AlwaysOn 可用性群組 &#40;SQL Server 的資料庫快照集&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-118">Database Snapshots with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="d05cb-119">FILESTREAM 與 FileTable</span><span class="sxs-lookup"><span data-stu-id="d05cb-119">FILESTREAM and FileTable</span></span>|[<span data-ttu-id="d05cb-120">FILESTREAM 和 FileTable 與 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-120">FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="d05cb-121">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="d05cb-121">Full-text search</span></span>|<span data-ttu-id="d05cb-122">注意：全文檢索索引與 AlwaysOn 次要資料庫同步。</span><span class="sxs-lookup"><span data-stu-id="d05cb-122">Note: Full-Text indexes are synchronized with AlwaysOn secondary databases.</span></span>|  
|<span data-ttu-id="d05cb-123">記錄傳送</span><span class="sxs-lookup"><span data-stu-id="d05cb-123">Log shipping</span></span>|[<span data-ttu-id="d05cb-124">從記錄傳送遷移至 AlwaysOn 可用性群組 &#40;SQL Server 的必要條件&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-124">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|<span data-ttu-id="d05cb-125">遠端 Blob 存放區 (RBS)</span><span class="sxs-lookup"><span data-stu-id="d05cb-125">Remote Blob Store (RBS)</span></span>|[<span data-ttu-id="d05cb-126">遠端 Blob 存放區 &#40;RBS&#41; 和 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-126">Remote Blob Store &#40;RBS&#41; and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="d05cb-127">複寫[設定 AlwaysOn 可用性群組 (SQL Server 的複寫) ](configure-replication-for-always-on-availability-groups-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="d05cb-127">Replication[Configure Replication for AlwaysOn Availability Groups (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)</span></span><br /><br /> [<span data-ttu-id="d05cb-128">維護 AlwaysOn 發行集資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-128">Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;</span></span>](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [<span data-ttu-id="d05cb-129">複寫、變更追蹤、變更資料捕獲，以及 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-129">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [<span data-ttu-id="d05cb-130">複寫訂閱者及 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-130">Replication Subscribers and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="d05cb-131">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="d05cb-131">Analysis Services</span></span>|[<span data-ttu-id="d05cb-132">Analysis Services 與 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="d05cb-132">Analysis Services with AlwaysOn Availability Groups</span></span>](analysis-services-with-always-on-availability-groups.md)|  
|<span data-ttu-id="d05cb-133">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="d05cb-133">Reporting Services</span></span>|<span data-ttu-id="d05cb-134">利用唯讀次要複本做為報表資料來源，減少主要讀寫複本上的負載。</span><span class="sxs-lookup"><span data-stu-id="d05cb-134">Utilize read only secondary replicas as a reporting data source and reduce the load on your primary read-write replica.</span></span><br /><br /> [<span data-ttu-id="d05cb-135">具有 AlwaysOn 可用性群組 &#40;SQL Server 的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-135">Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="d05cb-136">Service Broker</span><span class="sxs-lookup"><span data-stu-id="d05cb-136">Service Broker</span></span>|[<span data-ttu-id="d05cb-137">具有 AlwaysOn 可用性群組 &#40;SQL Server 的 Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-137">Service Broker with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](service-broker-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="d05cb-138">SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="d05cb-138">SQL Server Agent</span></span>||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a><span data-ttu-id="d05cb-139">無法與 AlwaysOn 可用性群組互通的功能</span><span class="sxs-lookup"><span data-stu-id="d05cb-139">Features that Do Not Interoperate with AlwaysOn Availability Groups</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="d05cb-140">無法與下列功能互通：</span><span class="sxs-lookup"><span data-stu-id="d05cb-140">does not interoperate with the following features:</span></span>  
  
-   <span data-ttu-id="d05cb-141">跨資料庫交易/分散式交易</span><span class="sxs-lookup"><span data-stu-id="d05cb-141">Cross-database transactions/distributed transactions</span></span>  
  
     <span data-ttu-id="d05cb-142">如需這類交易不受支援之原因的相關資訊，請參閱[資料庫鏡像或 AlwaysOn 可用性群組不支援跨資料庫交易 &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="d05cb-142">For information about why such transactions are not supported, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="d05cb-143">資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="d05cb-143">Database mirroring</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="d05cb-144">相關內容</span><span class="sxs-lookup"><span data-stu-id="d05cb-144">Related Content</span></span>  
  
-   <span data-ttu-id="d05cb-145">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="d05cb-145">**Blogs:**</span></span>  
  
     [<span data-ttu-id="d05cb-146">移轉指南：從先前叢集和鏡像部署移轉至 SQL Server 2012 容錯移轉叢集和可用性群組</span><span class="sxs-lookup"><span data-stu-id="d05cb-146">Migration Guide: Migrating to SQL Server 2012 Failover Clustering and Availability Groups from Prior Clustering and Mirroring Deployments</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [<span data-ttu-id="d05cb-147">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="d05cb-147">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="d05cb-148">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="d05cb-148">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="d05cb-149">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="d05cb-149">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="d05cb-150">移轉指南：從結合資料庫鏡像與記錄傳送的先前部署移轉至 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="d05cb-150">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span></span>](https://msdn.microsoft.com/library/jj635217)  
  
     [<span data-ttu-id="d05cb-151">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="d05cb-151">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="d05cb-152">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="d05cb-152">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="d05cb-153">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="d05cb-153">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="d05cb-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d05cb-154">See Also</span></span>  
 <span data-ttu-id="d05cb-155">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d05cb-155">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="d05cb-156">AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;</span><span class="sxs-lookup"><span data-stu-id="d05cb-156">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
