---
title: 高可用性方案 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], solutions
- Database Engine [SQL Server], availability
- database availability [SQL Server]
- availability [SQL Server]
- server availability [SQL Server]
ms.assetid: b2eda634-0f8e-4703-801b-7ba895544ff5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 83e7dde423fadcc0cd7d4d34dd4fd05b460cf453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595600"
---
# <a name="high-availability-solutions-sql-server"></a><span data-ttu-id="68f4e-102">高可用性解決方案 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="68f4e-102">High Availability Solutions (SQL Server)</span></span>
  <span data-ttu-id="68f4e-103">本主題會介紹幾個可增進伺服器或資料庫可用性的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 高可用性解決方案。</span><span class="sxs-lookup"><span data-stu-id="68f4e-103">This topic introduces several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] high-availability solutions that improve the availability of servers or databases.</span></span> <span data-ttu-id="68f4e-104">高可用性解決方案可遮蔽硬體或軟體失敗所造成的影響，並維護應用程式的可用性，進而讓使用者的停機時間減至最少。</span><span class="sxs-lookup"><span data-stu-id="68f4e-104">A high-availability solution masks the effects of a hardware or software failure and maintains the availability of applications so that the perceived downtime for users is minimized.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68f4e-105">如需支援所指定高可用性解決方案之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的相關資訊，請參閱 [SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)的＜高可用性 (AlwaysOn)＞一節。</span><span class="sxs-lookup"><span data-stu-id="68f4e-105">For information about which editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support a given high availability solution, see the "High Availability (AlwaysOn)" section of [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
<span data-ttu-id="68f4e-106"> ( # RecommendedSolutions) </span><span class="sxs-lookup"><span data-stu-id="68f4e-106">(#RecommendedSolutions)</span></span>  
  
##  <a name="overview-of-sql-server-high-availability-solutions"></a><a name="TermsAndDefinitions"></a><span data-ttu-id="68f4e-107">SQL Server 高可用性解決方案的總覽</span><span class="sxs-lookup"><span data-stu-id="68f4e-107">Overview of SQL Server High-Availability Solutions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="68f4e-108">提供幾個選項用於建立伺服器或資料庫的高可用性。</span><span class="sxs-lookup"><span data-stu-id="68f4e-108">provides several options for creating high availability for a server or database.</span></span> <span data-ttu-id="68f4e-109">高可用性選項包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="68f4e-109">The high-availability options include the following:</span></span>  
  
 <span data-ttu-id="68f4e-110">AlwaysOn 容錯移轉叢集執行個體</span><span class="sxs-lookup"><span data-stu-id="68f4e-110">AlwaysOn Failover Cluster Instances</span></span>  
 <span data-ttu-id="68f4e-111">AlwaysOn 容錯移轉叢集實例是 alwayson 供應專案的一部分，它會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 利用 Windows Server 容錯移轉叢集 (WSFC) 功能，透過伺服器實例層級的冗余來提供本機高可用性-*容錯移轉叢集實例* (FCI) 。</span><span class="sxs-lookup"><span data-stu-id="68f4e-111">As part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn offering, AlwaysOn Failover Cluster Instances leverages Windows Server Failover Clustering (WSFC) functionality to provide local high availability through redundancy at the server-instance level-a *failover cluster instance* (FCI).</span></span> <span data-ttu-id="68f4e-112">FCI 是跨 Windows Server 容錯移轉叢集 (WSFC) 節點且可能跨多個子網路安裝的單一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="68f4e-112">An FCI is a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is installed across Windows Server Failover Clustering (WSFC) nodes and, possibly, across multiple subnets.</span></span> <span data-ttu-id="68f4e-113">在網路上，FCI 看似單一電腦上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，但是 FCI 提供容錯移轉，可以在目前的 WSFC 節點無法使用時，從該節點容錯移轉到另一個節點。</span><span class="sxs-lookup"><span data-stu-id="68f4e-113">On the network, an FCI appears to be an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on a single computer, but the FCI provides failover from one WSFC node to another if the current node becomes unavailable.</span></span>  
  
 <span data-ttu-id="68f4e-114">如需詳細資訊，請參閱 [AlwaysOn 容錯移轉叢集執行個體 (SQL Server)](windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="68f4e-114">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] <span data-ttu-id="68f4e-115">是 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 所導入的企業級高可用性災害復原方案，讓您可將一或多個使用者資料庫的可用性最大化。</span><span class="sxs-lookup"><span data-stu-id="68f4e-115">is an enterprise-level high-availability and disaster recovery solution introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to enable you to maximize availability for one or more user databases.</span></span> [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] <span data-ttu-id="68f4e-116">要求 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須位於 Windows Server 容錯移轉叢集 (WSFC) 節點上。</span><span class="sxs-lookup"><span data-stu-id="68f4e-116">requires that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances reside on Windows Server Failover Clustering (WSFC) nodes.</span></span> <span data-ttu-id="68f4e-117">如需詳細資訊，請參閱[AlwaysOn 可用性群組 (SQL Server) ](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="68f4e-117">For more information, see [AlwaysOn Availability Groups (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68f4e-118">FCI 可以利用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 提供資料庫層級的遠端災害復原。</span><span class="sxs-lookup"><span data-stu-id="68f4e-118">An FCI can leverage [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] to provide remote disaster recovery at the database level.</span></span> <span data-ttu-id="68f4e-119">如需詳細資訊，請參閱[容錯移轉叢集和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="68f4e-119">For more information, see [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).</span></span>  
  
 <span data-ttu-id="68f4e-120">資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="68f4e-120">Database mirroring</span></span>  
 > [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="68f4e-121">我們建議您改用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="68f4e-121">We recommend that you use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="68f4e-122">資料庫鏡像是支援近乎瞬間的容錯移轉，進而提高資料庫可用性的方案。</span><span class="sxs-lookup"><span data-stu-id="68f4e-122">Database mirroring is a solution to increase database availability by supporting almost instantaneous failover.</span></span> <span data-ttu-id="68f4e-123">資料庫鏡像可用以維護實際執行的資料庫 (稱為 *「主體資料庫」*) 所對應的單一待命資料庫 (或稱 *「鏡像資料庫」*)。</span><span class="sxs-lookup"><span data-stu-id="68f4e-123">Database mirroring can be used to maintain a single standby database, or *mirror database*, for a corresponding production database that is referred to as the *principal database*.</span></span> <span data-ttu-id="68f4e-124">如需詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="68f4e-124">For more information, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="68f4e-125">記錄傳送</span><span class="sxs-lookup"><span data-stu-id="68f4e-125">Log shipping</span></span>  
 <span data-ttu-id="68f4e-126">記錄傳送就像 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 與資料庫鏡像一樣，都是在資料庫層級運作。</span><span class="sxs-lookup"><span data-stu-id="68f4e-126">Like [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] and database mirroring, log shipping operates at the database level.</span></span> <span data-ttu-id="68f4e-127">您可以使用記錄傳送來針對單一實際執行資料庫 (稱為「主要資料庫」**) 維護一個或多個暖待命資料庫 (稱為「次要資料庫」**)。</span><span class="sxs-lookup"><span data-stu-id="68f4e-127">You can use log shipping to maintain one or more warm standby databases (referred to as *secondary databases*) for a single production database that is referred to as the *primary database*.</span></span> <span data-ttu-id="68f4e-128">如需記錄傳送作業的相關資訊，請參閱[關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="68f4e-128">For more information about log shipping, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
##  <a name="recommended-solutions-for-using-sql-server-to-protect-data"></a><a name="RecommendedSolutions"></a> <span data-ttu-id="68f4e-129">使用 SQL Server 保護資料的建議方案</span><span class="sxs-lookup"><span data-stu-id="68f4e-129">Recommended Solutions for Using SQL Server to Protect Data</span></span>  
 <span data-ttu-id="68f4e-130">為您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境提供資料保護的建議如下：</span><span class="sxs-lookup"><span data-stu-id="68f4e-130">Our recommendation for providing data protection for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment are as follows:</span></span>  
  
-   <span data-ttu-id="68f4e-131">對於透過協力廠商共用磁碟方案 (SAN) 的資料保護，我們建議您使用 AlwaysOn 容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="68f4e-131">For data protection through a third-party shared disk solution (a SAN), we recommend that you use AlwaysOn Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="68f4e-132">對於透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的資料保護，我們建議您使用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="68f4e-132">For data protection through [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], we recommend that you use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="68f4e-133">如果您執行不支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]版本，建議使用記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="68f4e-133">If you are running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that does not support [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], we recommend log shipping.</span></span> <span data-ttu-id="68f4e-134">如需支援 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的相關資訊，請參閱 [SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)的＜高可用性 (AlwaysOn)＞一節。</span><span class="sxs-lookup"><span data-stu-id="68f4e-134">For information about which editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], see the "High Availability (AlwaysOn)" section of [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f4e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68f4e-135">See Also</span></span>  
 <span data-ttu-id="68f4e-136">[SQL Server 的 Windows Server 容錯移轉叢集 &#40;WSFC&#41;](windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="68f4e-136">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 <span data-ttu-id="68f4e-137">[資料庫鏡像：互通性與共存性 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="68f4e-137">[Database Mirroring: Interoperability and Coexistence &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md) </span></span>  
 [<span data-ttu-id="68f4e-138">SQL Server 2014 中已被取代的 Database Engine 功能</span><span class="sxs-lookup"><span data-stu-id="68f4e-138">Deprecated Database Engine Features in SQL Server 2014</span></span>](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
