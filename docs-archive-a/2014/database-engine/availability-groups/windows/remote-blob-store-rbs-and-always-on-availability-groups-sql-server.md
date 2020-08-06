---
title: 遠端 Blob 存放區 (RBS) 和 AlwaysOn 可用性群組 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12a11162d286731b2b510a9051183e6c3025b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593609"
---
# <a name="remote-blob-store-rbs-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="dc1ba-102">遠端 BLOB 存放區 (RBS) 及 AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dc1ba-102">Remote Blob Store (RBS) and AlwaysOn Availability Groups (SQL Server)</span></span>
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]<span data-ttu-id="dc1ba-103">可以為遠端 Blob 存放區提供高可用性和嚴重損壞修復解決方案， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [ (RBS) ](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) blob 物件 (blob) 。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-103">can provide a high-availability and disaster recovery solution for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][Remote Blob Store (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) BLOB objects (blobs).</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="dc1ba-104">會透過將儲存在可用性資料庫中的任何 RBS 中繼資料和結構描述複寫到次要複本，予以保護。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-104">protects any RBS metadata and schemas stored in an availability database by replicating them to the secondary replicas.</span></span> <span data-ttu-id="dc1ba-105">這是 SharePoint 內容資料庫。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-105">This is the SharePoint Content Database.</span></span> <span data-ttu-id="dc1ba-106">一般而言， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分開儲存此 RBS 中繼資料與 BLOB。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-106">Generally speaking, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stores this RBS metadata independently from the blob.</span></span>  
  
 <span data-ttu-id="dc1ba-107">RBD BLOB 資料的保護取決於 BLOB 存放區位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc1ba-107">The protection for RBD BLOB data depends on the BLOB Store Location, as follows:</span></span>  
  
|<span data-ttu-id="dc1ba-108">BLOB 存放區位置</span><span class="sxs-lookup"><span data-stu-id="dc1ba-108">BLOB Store Location</span></span>|<span data-ttu-id="dc1ba-109">可用性群組可保護此 BLOB 資料？</span><span class="sxs-lookup"><span data-stu-id="dc1ba-109">Can Availability Groups Protect This BLOB Data?</span></span>|  
|-------------------------|-----------------------------------------------------|  
|<span data-ttu-id="dc1ba-110">包含 RBS 中繼資料的相同資料庫 (使用 RBS 遠端 FILESTREAM 提供者所儲存)</span><span class="sxs-lookup"><span data-stu-id="dc1ba-110">The same database that contains the RBS metadata  (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="dc1ba-111">是</span><span class="sxs-lookup"><span data-stu-id="dc1ba-111">Yes</span></span>|  
|<span data-ttu-id="dc1ba-112">在相同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上的另一個資料庫 (使用 RBS 遠端 FILESTREAM 提供者所儲存)</span><span class="sxs-lookup"><span data-stu-id="dc1ba-112">Another database in the same instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="dc1ba-113">是</span><span class="sxs-lookup"><span data-stu-id="dc1ba-113">Yes</span></span><br /><br /> <span data-ttu-id="dc1ba-114">我們建議您在包含 RBS 中繼資料之資料庫的同一個可用性群組中放置此資料庫。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-114">We recommend that you put this database in the same availability group as the database that contains the RBS metadata.</span></span>|  
|<span data-ttu-id="dc1ba-115">在不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上的另一個資料庫 (使用 RBS 遠端 FILESTREAM 提供者所儲存)</span><span class="sxs-lookup"><span data-stu-id="dc1ba-115">Another database in a different instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="dc1ba-116">是</span><span class="sxs-lookup"><span data-stu-id="dc1ba-116">Yes</span></span><br /><br /> <span data-ttu-id="dc1ba-117">此資料庫必須位於個別的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-117">This database must be in a separate availability group.</span></span>|  
|<span data-ttu-id="dc1ba-118">協力廠商 BLOB 存放區</span><span class="sxs-lookup"><span data-stu-id="dc1ba-118">A third-party BLOB store</span></span>|<span data-ttu-id="dc1ba-119">否</span><span class="sxs-lookup"><span data-stu-id="dc1ba-119">No</span></span><br /><br /> <span data-ttu-id="dc1ba-120">為了保護此 BLOB 資料，請使用 BLOB 存放區提供者的高可用性機制。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-120">To protect this BLOB data, use the high-availability mechanisms of the BLOB store provider.</span></span>|  
  
##  <a name="limitations"></a><a name="Limitations"></a> <span data-ttu-id="dc1ba-121">限制</span><span class="sxs-lookup"><span data-stu-id="dc1ba-121">Limitations</span></span>  
  
-   <span data-ttu-id="dc1ba-122">RBS 維護程式在主要複本上需要為目標。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-122">RBS maintainers need to be targeted on the primary replica.</span></span>  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="dc1ba-123">建議</span><span class="sxs-lookup"><span data-stu-id="dc1ba-123">Recommendations</span></span>  
  
-   <span data-ttu-id="dc1ba-124">使用可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-124">Use an availability group listener.</span></span> <span data-ttu-id="dc1ba-125">如需詳細資訊，請參閱[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="dc1ba-125">For more information, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="dc1ba-126">相關內容</span><span class="sxs-lookup"><span data-stu-id="dc1ba-126">Related Content</span></span>  
  
-   <span data-ttu-id="dc1ba-127">[維護遠端 BLOB 存放區](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (在《 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 線上叢書》中)</span><span class="sxs-lookup"><span data-stu-id="dc1ba-127">[Maintaining Remote BLOB Store](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Books Online)</span></span>  
  
-   <span data-ttu-id="dc1ba-128">[執行 RBS 維護程式](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (部落格)</span><span class="sxs-lookup"><span data-stu-id="dc1ba-128">[Running RBS Maintainer](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (blog)</span></span>  
  
-   <span data-ttu-id="dc1ba-129">[使用 FILESTREAM 提供者設定遠端 BLOB 儲存 (RBS) (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (部落格)</span><span class="sxs-lookup"><span data-stu-id="dc1ba-129">[Configure Remote BLOB Storage (RBS) with the FILESTREAM provider (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (blog)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1ba-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc1ba-130">See Also</span></span>  
 <span data-ttu-id="dc1ba-131">[AlwaysOn 用戶端連線性 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dc1ba-131">[AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md) </span></span>  
 [<span data-ttu-id="dc1ba-132">遠端 Blob 存放區 &#40;RBS&#41; &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dc1ba-132">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  
