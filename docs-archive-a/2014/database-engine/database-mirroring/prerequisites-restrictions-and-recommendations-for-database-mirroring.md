---
title: 資料庫鏡像的必要條件、限制和建議事項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- partners [SQL Server]
- database mirroring [SQL Server], prerequisites
- database mirroring [SQL Server], recommendations
- database mirroring [SQL Server], restrictions
- database mirroring [SQL Server], planning
- database mirroring [SQL Server], about database mirroring
ms.assetid: fdcf2251-9895-44c6-b81e-768fef32e732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dc29dbdc8432a4abd197a2a1a3f15b6ff5f6d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701836"
---
# <a name="prerequisites-restrictions-and-recommendations-for-database-mirroring"></a><span data-ttu-id="9976b-102">資料庫鏡像的必要條件、限制和建議事項</span><span class="sxs-lookup"><span data-stu-id="9976b-102">Prerequisites, Restrictions, and Recommendations for Database Mirroring</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="9976b-103">請改用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9976b-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="9976b-104">本主題描述設定資料庫鏡像的必要條件和建議事項。</span><span class="sxs-lookup"><span data-stu-id="9976b-104">This topic describes the prerequisites and recommendations for setting up database mirroring.</span></span> <span data-ttu-id="9976b-105">如需資料庫鏡像的簡介，請參閱 [資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-105">For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9976b-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁碟儲存格式在 64 位元與 32 位元環境下都相同。</span><span class="sxs-lookup"><span data-stu-id="9976b-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="9976b-107">因此，資料庫鏡像工作階段可以結合 32 位元環境下執行的伺服器執行個體與 64 位元環境下執行的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9976b-107">Therefore, a database mirroring session can combine server instances that run in a 32-bit environment and server instances that run in a 64-bit environment.</span></span>  
  

  
##  <a name="support-for-database-mirroring"></a><a name="DbmSupport"></a><span data-ttu-id="9976b-108">資料庫鏡像支援</span><span class="sxs-lookup"><span data-stu-id="9976b-108">Support For Database Mirroring</span></span>  
 <span data-ttu-id="9976b-109">如需 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中資料庫鏡像支援的相關資訊，請參閱 [SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-109">For information about support for database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="9976b-110">請注意，資料庫鏡像適用於任何支援的資料庫相容性層級。</span><span class="sxs-lookup"><span data-stu-id="9976b-110">Note that database mirroring works with any supported database compatibility level.</span></span> <span data-ttu-id="9976b-111">如需支援的相容性層級相關資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="9976b-111">For information about the supported compatibility levels, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  

  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="9976b-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="9976b-112">Prerequisites</span></span>  
  
-   <span data-ttu-id="9976b-113">如果要建立鏡像工作階段，則夥伴伺服器和見證伺服器 (如果有的話) 必須在相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本上執行。</span><span class="sxs-lookup"><span data-stu-id="9976b-113">For a mirroring session to be established, the partners and the witness, if any, must be running on the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="9976b-114">兩個夥伴 (亦即，主體伺服器和鏡像伺服器) 必須都在執行相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="9976b-114">The two partners, that is the principal server and mirror server, must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9976b-115">見證 (如果有的話) 可在任一版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上執行，只要該版本支援資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="9976b-115">The witness, if any, can run on any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports database mirroring.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9976b-116">您可以將做為鏡像工作階段夥伴的伺服器執行個體升級為最新版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9976b-116">You can upgrade server instances that are partners in a mirroring session to a more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9976b-117">如需詳細資訊，請參閱 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-117">For more information, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).</span></span>  
  
-   <span data-ttu-id="9976b-118">資料庫必須使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="9976b-118">The database must use the full recovery model.</span></span> <span data-ttu-id="9976b-119">簡單與大量記錄復原模式不支援資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="9976b-119">The simple and bulk-logged recovery models do not support database mirroring.</span></span> <span data-ttu-id="9976b-120">因此，鏡像資料庫的大量作業永遠都是完整記錄作業。</span><span class="sxs-lookup"><span data-stu-id="9976b-120">Therefore, bulk operations are always fully logged for a mirrored database.</span></span> <span data-ttu-id="9976b-121">如需復原模式的相關資訊，請參閱[復原模式 &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-121">For information about recovery models, see [Recovery Models &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9976b-122">確認鏡像伺服器有足夠的磁碟空間可用於鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="9976b-122">Verify that the mirror server has sufficient disk space for the mirror database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9976b-123">如需如何在複寫資料庫上使用資料庫鏡像的相關資訊，請參閱[資料庫鏡像和複寫 &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-123">For information about how to use database mirroring on a replicated database, see [Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9976b-124">在鏡像伺服器上建立鏡像資料庫時，請確定您使用 WITH NORECOVERY 指定了相同的資料庫名稱來還原主體資料庫的備份。</span><span class="sxs-lookup"><span data-stu-id="9976b-124">When you are creating the mirror database on the mirror server, make sure that you restore the backup of the principal database specifying the same database name WITH NORECOVERY.</span></span> <span data-ttu-id="9976b-125">另外，您還必須再一次使用 WITH NORECOVERY 來套用該備份完成之後建立的所有記錄備份。</span><span class="sxs-lookup"><span data-stu-id="9976b-125">Also, all log backups that were created after that backup was taken must also be applied, again WITH NORECOVERY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9976b-126">如果資料庫鏡像已停止，您必須先將主體資料庫上建立的所有後續記錄備份套用到鏡像資料庫，然後才能重新啟動鏡像。</span><span class="sxs-lookup"><span data-stu-id="9976b-126">If database mirroring has been stopped, before you can restart it, any subsequent log backups taken on the principal database must be applied to the mirror database.</span></span>  
  

  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9976b-127">限制</span><span class="sxs-lookup"><span data-stu-id="9976b-127">Restrictions</span></span>  
  
-   <span data-ttu-id="9976b-128">只有使用者資料庫可進行鏡像。</span><span class="sxs-lookup"><span data-stu-id="9976b-128">Only user databases can be mirrored.</span></span> <span data-ttu-id="9976b-129">您無法鏡像處理 **master**、 **msdb**、 **tempdb**或 **model** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9976b-129">You cannot mirror the **master**, **msdb**, **tempdb**, or **model** databases.</span></span>  
  
-   <span data-ttu-id="9976b-130">鏡像資料庫不能在資料庫鏡像工作階段期間重新命名。</span><span class="sxs-lookup"><span data-stu-id="9976b-130">A mirrored database cannot be renamed during a database mirroring session.</span></span>  
  
-   <span data-ttu-id="9976b-131">資料庫鏡像不支援 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="9976b-131">Database mirroring does not support FILESTREAM.</span></span> <span data-ttu-id="9976b-132">不能在主體伺服器上建立 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="9976b-132">A FILESTREAM filegroup cannot be created on the principal server.</span></span> <span data-ttu-id="9976b-133">不能針對包含 FILESTREAM 檔案群組的資料庫設定資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="9976b-133">Database mirroring cannot be configured for a database that contains FILESTREAM filegroups.</span></span>  
  
-   <span data-ttu-id="9976b-134">在 32 位元系統上，因為每個資料庫鏡像工作階段所耗用的工作者執行緒數目有限制，所以資料庫鏡像最多可以為每一個伺服器執行個體支援約 10 個資料庫。</span><span class="sxs-lookup"><span data-stu-id="9976b-134">On a 32-bit system, database mirroring can support a maximum of about 10 databases per server instance because of the numbers of worker threads that are consumed by each database mirroring session.</span></span>  
  
-   <span data-ttu-id="9976b-135">跨資料庫交易或分散式交易不支援資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="9976b-135">Database mirroring is not supported with either cross-database transactions or distributed transactions.</span></span> <span data-ttu-id="9976b-136">如需詳細資訊，請參閱[資料庫鏡像或 AlwaysOn 可用性群組不支援跨資料庫交易 &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-136">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  

  
##  <a name="recommendations-for-configuring-partner-servers"></a><a name="RecommendationsForPartners"></a><span data-ttu-id="9976b-137">設定夥伴伺服器的建議</span><span class="sxs-lookup"><span data-stu-id="9976b-137">Recommendations for Configuring Partner Servers</span></span>  
  
-   <span data-ttu-id="9976b-138">夥伴伺服器應該在可相比而且可以處理相同工作負載的系統上執行。</span><span class="sxs-lookup"><span data-stu-id="9976b-138">The partners should run on comparable systems that can handle identical workloads.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9976b-139">如果您打算使用具有自動容錯移轉的高安全性模式，則每個容錯移轉夥伴的正常負載應該少於 50% 以下的 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="9976b-139">If you plan to use high-safety mode with automatic failover, the normal load on each failover partner should be less than 50 percent of the CPU.</span></span> <span data-ttu-id="9976b-140">如果您的工作負載使 CPU 超載，容錯移轉夥伴可能無法在鏡像工作階段中對其他伺服器執行個體發出 ping 命令，</span><span class="sxs-lookup"><span data-stu-id="9976b-140">If your work load overloads the CPU, a failover partner might be unable to ping the other server instances in the mirroring session.</span></span> <span data-ttu-id="9976b-141">進而導致不必要的容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="9976b-141">This causes a unnecessary failover.</span></span> <span data-ttu-id="9976b-142">如果您無法將 CPU 使用量保持在 50% 以下，我們建議您使用不含自動容錯移轉的高安全性模式或高效能模式。</span><span class="sxs-lookup"><span data-stu-id="9976b-142">If you cannot keep the CPU usage under 50 percent, we recommend that you use either high-safety mode without automatic failover or high-performance mode.</span></span>  
  
-   <span data-ttu-id="9976b-143">如果可行的話，鏡像資料庫的路徑 (包括磁碟機代號) 應該要和主體資料庫的路徑完全相同。</span><span class="sxs-lookup"><span data-stu-id="9976b-143">If possible, the path (including the drive letter) of the mirror database should be identical to the path of the principal database.</span></span> <span data-ttu-id="9976b-144">如果檔案配置必須不同，您必須在 RESTORE 陳述式中包含 MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="9976b-144">You must include the MOVE option in the RESTORE statement if the file layouts must differ.</span></span> <span data-ttu-id="9976b-145">例如，如果主體資料庫位於磁碟機 'F:'，但是鏡像系統缺少 F: 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9976b-145">For example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9976b-146">在建立鏡像資料庫時，如果您移動資料庫檔案，則稍後必須暫停鏡像，否則可能無法將檔案加入資料庫。</span><span class="sxs-lookup"><span data-stu-id="9976b-146">If you move the database files when you create the mirror database, you might be unable to add files to the database later without mirroring being suspended.</span></span>  
  
-   <span data-ttu-id="9976b-147">鏡像工作階段中的所有伺服器執行個體都應該使用相同的主要字碼頁和定序。</span><span class="sxs-lookup"><span data-stu-id="9976b-147">All of the server instances in a mirroring session should use the same master code page and collation.</span></span> <span data-ttu-id="9976b-148">如果有差異，可能會在鏡像設定期間發生問題。</span><span class="sxs-lookup"><span data-stu-id="9976b-148">Differences can cause a problem during mirroring setup.</span></span>  
  
-   <span data-ttu-id="9976b-149">另外，也可以估計容錯移轉資料庫的時間，確定系統組態將會提供所需的效能。</span><span class="sxs-lookup"><span data-stu-id="9976b-149">Optionally, estimate the time to fail over a database, to make sure that the system configuration will provide the performance you require.</span></span> <span data-ttu-id="9976b-150">如需詳細資訊，請參閱 [預估角色切換期間的服務中斷時間 &#40;資料庫鏡像&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)的程序交換。</span><span class="sxs-lookup"><span data-stu-id="9976b-150">For more information, see [Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="9976b-151">為達最佳效能，請為鏡像使用專用的網路介面卡 (NIC)。</span><span class="sxs-lookup"><span data-stu-id="9976b-151">For best performance, use a dedicated network adapter (network interface card) for mirroring.</span></span>  
  
-   <span data-ttu-id="9976b-152">關於廣域網路 (WAN) 對於高安全性模式的資料庫鏡像而言是否可靠，我們不提供任何建議。</span><span class="sxs-lookup"><span data-stu-id="9976b-152">We make no recommendations about whether a wide-area network (WAN) is reliable enough for database mirroring in high-safety mode.</span></span> <span data-ttu-id="9976b-153">如果您決定在 WAN 上使用高安全性模式，則將見證伺服器加入工作階段時要小心謹慎，因為可能會發生不必要的自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="9976b-153">If you decide to use high-safety mode over a WAN, be cautious about how you add a witness to the session, because unwanted automatic failovers can occur.</span></span> <span data-ttu-id="9976b-154">如需詳細資訊，請參閱本主題稍後的 [部署資料庫鏡像的建議](#RecommendationsForDeploying)。</span><span class="sxs-lookup"><span data-stu-id="9976b-154">For more information, see [Recommendations for Deploying Database Mirroring](#RecommendationsForDeploying), later in this topic.</span></span>  
  

  
##  <a name="recommendations-for-deploying-database-mirroring"></a><a name="RecommendationsForDeploying"></a><span data-ttu-id="9976b-155">部署資料庫鏡像的建議</span><span class="sxs-lookup"><span data-stu-id="9976b-155">Recommendations for Deploying Database Mirroring</span></span>  
 <span data-ttu-id="9976b-156">最佳資料庫鏡像效能是使用非同步作業所取得。</span><span class="sxs-lookup"><span data-stu-id="9976b-156">Optimal database mirroring performance is obtained by using asynchronous operation.</span></span> <span data-ttu-id="9976b-157">當使用同步作業之鏡像工作階段的工作負載產生大量交易記錄資料時，效能可能會變慢。</span><span class="sxs-lookup"><span data-stu-id="9976b-157">A mirroring session that uses synchronous operation might experience slowed performance when its workload generates large amounts of transaction log data.</span></span>  
  
 <span data-ttu-id="9976b-158">在測試環境中，適合瀏覽所有作業模式，以評估資料庫鏡像的效能。</span><span class="sxs-lookup"><span data-stu-id="9976b-158">In test environments, it is appropriate to explore all the operating modes to evaluate how database mirroring performs.</span></span> <span data-ttu-id="9976b-159">然而，在實際環境中部署鏡像之前，必須先了解網路如何在實際環境中運作。</span><span class="sxs-lookup"><span data-stu-id="9976b-159">However, before you deploy mirroring into a production environment, make sure that you understand how the network functions in the real world.</span></span>  
  
 <span data-ttu-id="9976b-160">具有自動容錯移轉的高安全性模式是針對具有專用連接或相當簡單之網路組態的高服務網路所設計，可讓可能發生的網路失敗來源減至最少。</span><span class="sxs-lookup"><span data-stu-id="9976b-160">High-safety mode with automatic failover is designed for a high-service network that has either a dedicated connection or a fairly simple network configuration that minimizes the sources of possible network failures.</span></span> <span data-ttu-id="9976b-161">具有自動容錯移轉的高安全性模式一定需要這類高品質網路環境，而且建議所有資料庫鏡像工作階段都使用這類環境。</span><span class="sxs-lookup"><span data-stu-id="9976b-161">Such a high-quality network environment is necessary for high-safety mode with automatic failover and is recommended for all database mirroring sessions.</span></span> <span data-ttu-id="9976b-162">不過，高效能模式和不含自動容錯移轉的高安全性模式則較不受網路可靠性的影響。</span><span class="sxs-lookup"><span data-stu-id="9976b-162">However, high-performance mode and high-safety mode without automatic failover are much less affected by network reliability.</span></span>  
  
 <span data-ttu-id="9976b-163">因此，若為實際執行環境，建議您遵守下列部署指導方針：</span><span class="sxs-lookup"><span data-stu-id="9976b-163">Therefore, for production environments we recommend that you adhere to the following deployment guidelines:</span></span>  
  
1.  <span data-ttu-id="9976b-164">以非同步、高效能模式開始執行。</span><span class="sxs-lookup"><span data-stu-id="9976b-164">Start running in asynchronous, high-performance mode.</span></span> <span data-ttu-id="9976b-165">這個模式對網路環境最不敏感，而且會提供瀏覽鏡像運作方式的最佳組態。</span><span class="sxs-lookup"><span data-stu-id="9976b-165">This mode is the least sensitive to the network environment and provides the best configuration for exploring how mirroring works.</span></span> <span data-ttu-id="9976b-166">我們建議您以非同步的方式執行系統，除非您非常確信您的頻寬可支援鏡像，而且已具備了環境中鏡像設定和非同步模式效能的完整知識。</span><span class="sxs-lookup"><span data-stu-id="9976b-166">We recommend that you run your system asynchronously until you are confident that your bandwidth supports mirroring and you have developed an understanding of mirroring setup and of the performance of asynchronous mode in your environment.</span></span> <span data-ttu-id="9976b-167">如需詳細資訊，請參閱 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-167">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9976b-168">在整個測試中，建議您監視工作階段，以找出讓資料庫鏡像失敗的網路錯誤。</span><span class="sxs-lookup"><span data-stu-id="9976b-168">Throughout testing, we recommend that you monitor your sessions for network errors that cause database mirroring to fail.</span></span> <span data-ttu-id="9976b-169">如需有關可能之失敗來源的詳細資訊，請參閱＜ [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9976b-169">For more information about potential sources of failure, see [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md).</span></span> <span data-ttu-id="9976b-170">如需如何監視資料庫鏡像的相關資訊，請參閱[監視資料庫鏡像 &#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-170">For information about how to monitor database mirroring, see [Monitoring Database Mirroring &#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="9976b-171">當您確信非同步作業符合您的商務需求時，可能會想要嘗試同步作業來提升資料保護。</span><span class="sxs-lookup"><span data-stu-id="9976b-171">When you are confident that asynchronous operation is meeting the business needs, you might want to try synchronous operation to improve your data protection.</span></span> <span data-ttu-id="9976b-172">當您測試同步鏡像如何在環境中運作時，建議您先測試不含自動容錯移轉的高安全性模式。</span><span class="sxs-lookup"><span data-stu-id="9976b-172">When you test how synchronous mirroring works in your environment, we recommend that first you test high-safety mode without automatic failover.</span></span> <span data-ttu-id="9976b-173">這項測試的主要目的是要了解同步作業如何影響資料庫效能。</span><span class="sxs-lookup"><span data-stu-id="9976b-173">The primary purpose of this testing is to see how synchronous operation affects the database performance.</span></span> <span data-ttu-id="9976b-174">如需詳細資訊，請參閱 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="9976b-174">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
3.  <span data-ttu-id="9976b-175">等候啟用自動容錯移轉，直到您確信不含自動容錯移轉的高安全性模式已符合商務需求，而且網路錯誤不會導致失敗為止。</span><span class="sxs-lookup"><span data-stu-id="9976b-175">Wait to enable automatic failover until you are confident that high-safety mode without automatic failover is meeting the business needs and that network errors are not causing failures.</span></span> <span data-ttu-id="9976b-176">如需詳細資訊，請參閱 [資料庫鏡像工作階段期間的角色切換 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)版本都可使用見證伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9976b-176">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="9976b-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9976b-177">See Also</span></span>  
 <span data-ttu-id="9976b-178">[設定資料庫鏡像 &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9976b-178">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="9976b-179">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="9976b-179">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="9976b-180">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9976b-180">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="9976b-181">疑難排解資料庫鏡像組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9976b-181">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
