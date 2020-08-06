---
title: AlwaysOn 可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- secondary replicas, see Availability Groups [SQL Server]
- availability [SQL Server]
- AlwaysOn [SQL Server], see Availability Groups [SQL Server]
- Availability Groups [SQL Server]
ms.assetid: aa427606-8422-4656-b205-c9e665ddc8c1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 169d720868a4c721e5f409e97971047ec7b04483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595293"
---
# <a name="always-on-availability-groups-sql-server"></a><span data-ttu-id="cedc6-102">AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cedc6-102">Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="cedc6-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 功能是提供資料庫鏡像之企業級替代方案的高可用性與災害復原解決方案。</span><span class="sxs-lookup"><span data-stu-id="cedc6-103">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature is a high-availability and disaster-recovery solution that provides an enterprise-level alternative to database mirroring.</span></span> <span data-ttu-id="cedc6-104">在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]中導入的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 可讓企業將一組使用者資料庫的可用性提高到最大程度。</span><span class="sxs-lookup"><span data-stu-id="cedc6-104">Introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] maximizes the availability of a set of user databases for an enterprise.</span></span> <span data-ttu-id="cedc6-105">*可用性群組*支援一組可一起容錯移轉之離散化使用者資料庫（稱為「*可用性資料庫*」（availability database））的容錯移轉環境。</span><span class="sxs-lookup"><span data-stu-id="cedc6-105">An *availability group* supports a failover environment for a discrete set of user databases, known as *availability databases*, that fail over together.</span></span> <span data-ttu-id="cedc6-106">可用性群組支援一組讀寫的主要資料庫，以及一到八組對應的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="cedc6-106">An availability group supports a set of read-write primary databases and one to eight sets of corresponding secondary databases.</span></span> <span data-ttu-id="cedc6-107">此外，您可以將次要資料庫用於唯讀存取及/或某些備份作業。</span><span class="sxs-lookup"><span data-stu-id="cedc6-107">Optionally, secondary databases can be made available for read-only access and/or some backup operations.</span></span>  
  
 <span data-ttu-id="cedc6-108">可用性群組會在可用性複本層級容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="cedc6-108">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="cedc6-109">容錯移轉不是因資料庫問題 (例如資料庫因為資料檔案遺失而變得可疑、資料庫刪除或交易記錄損毀) 而造成的。</span><span class="sxs-lookup"><span data-stu-id="cedc6-109">Failovers are not caused by database issues such as a database becoming suspect due to a loss of a data file, deletion of a database, or corruption of a transaction log.</span></span>  
  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="cedc6-110">優點</span><span class="sxs-lookup"><span data-stu-id="cedc6-110">Benefits</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="cedc6-111">提供了一組豐富的選項，可改善資料庫可用性並實現改善的資源使用方式。</span><span class="sxs-lookup"><span data-stu-id="cedc6-111">provides a rich set of options that improve database availability and that enable improved resource use.</span></span> <span data-ttu-id="cedc6-112">關鍵元件如下：</span><span class="sxs-lookup"><span data-stu-id="cedc6-112">The key components are as follows:</span></span>  
  
-   <span data-ttu-id="cedc6-113">最多支援九個可用性複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-113">Supports up to nine availability replicas.</span></span> <span data-ttu-id="cedc6-114">*「可用性複本」* (Availability Replica) 是特定 SQL Server 執行個體所裝載之可用性群組的具現化，其中維護屬於可用性群組之每個可用性資料庫的本機複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-114">An *availability replica* is an instantiation of an availability group that is hosted by a specific instance of SQL Server and maintains a local copy of each availability database that belongs to the availability group.</span></span> <span data-ttu-id="cedc6-115">每個可用性群組都支援一個主要複本和最多八個次要複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-115">Each availability group supports one primary replica and up to eight secondary replicas.</span></span> <span data-ttu-id="cedc6-116">如需詳細資訊，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-116">For more information, see [Overview of Always On Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="cedc6-117">每個可用性複本都必須位在單一 Windows Server 容錯移轉叢集 (WSFC) 叢集的不同節點。</span><span class="sxs-lookup"><span data-stu-id="cedc6-117">Each availability replica must reside on a different node of a single Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="cedc6-118">如需可用性群組的必要條件、限制和建議的詳細資訊，請參閱[Always On 可用性群組的必要條件、限制和建議。SQL Server;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-118">For more information about prerequisites, restrictions, and recommendations for availability groups, see [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups;SQL Server;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="cedc6-119">支援替代可用性模式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cedc6-119">Supports alternative availability modes, as follows:</span></span>  
  
    -   <span data-ttu-id="cedc6-120">*非同步認可模式*。</span><span class="sxs-lookup"><span data-stu-id="cedc6-120">*Asynchronous-commit mode*.</span></span> <span data-ttu-id="cedc6-121">這種可用性模式是一種當可用性複本分散距離相當遠時仍可正常運作的災害復原方案。</span><span class="sxs-lookup"><span data-stu-id="cedc6-121">This availability mode is a disaster-recovery solution that works well when the availability replicas are distributed over considerable distances.</span></span>  
  
    -   <span data-ttu-id="cedc6-122">*同步認可模式*。</span><span class="sxs-lookup"><span data-stu-id="cedc6-122">*Synchronous-commit mode*.</span></span> <span data-ttu-id="cedc6-123">這種可用性模式強調的是高可用性和資料保護而非效能，但是相對地增加了交易延遲。</span><span class="sxs-lookup"><span data-stu-id="cedc6-123">This availability mode emphasizes high availability and data protection over performance, at the cost of increased transaction latency.</span></span> <span data-ttu-id="cedc6-124">給定的可用性群組最多可支援三個同步認可的可用性複本，包括目前的主要複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-124">A given availability group can support up to three synchronous-commit availability replicas, including the current primary replica.</span></span>  
  
     <span data-ttu-id="cedc6-125">如需詳細資訊，請參閱[可用性模式。Always On 可用性群組;](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-125">For more information, see [Availability Modes;Always On Availability Groups;](availability-modes-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="cedc6-126">支援許多可用性群組容錯移轉形式：自動容錯移轉、規劃的手動容錯移轉 (通常只稱為「手動容錯移轉」)，以及強制手動容錯移轉 (通常只稱為「強制容錯移轉」)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-126">Supports several forms of availability-group failover:  automatic failover, planned manual failover (generally referred as simply "manual failover"), and forced manual failover (generally referred as simply "forced failover").</span></span> <span data-ttu-id="cedc6-127">如需詳細資訊，請參閱[容錯移轉和容錯移轉模式。Always On 可用性群組;](failover-and-failover-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-127">For more information, see [Failover and Failover Modes;Always On Availability Groups;](failover-and-failover-modes-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="cedc6-128">可讓您將給定的可用性複本設定為支援下列其中一種或兩種使用中次要功能：</span><span class="sxs-lookup"><span data-stu-id="cedc6-128">Enables you to configure a given availability replica to support either or both of the following active-secondary capabilities:</span></span>  
  
    -   <span data-ttu-id="cedc6-129">唯讀連接存取，讓複本的唯讀連接能夠在以次要複本的方式執行時存取並讀取其資料庫。</span><span class="sxs-lookup"><span data-stu-id="cedc6-129">Read-only connection access which enables read-only connections to the replica to access and read its databases when it is running as a secondary replica.</span></span> <span data-ttu-id="cedc6-130">如需詳細資訊，請參閱使用中[次要資料庫：可讀取的次要複本;Always On 可用性群組](https://msdn.microsoft.com/library/ff878253.aspx)) 。</span><span class="sxs-lookup"><span data-stu-id="cedc6-130">For more information, see [Active Secondaries: Readable Secondary Replicas;Always On Availability Groups](https://msdn.microsoft.com/library/ff878253.aspx)).</span></span>  
  
    -   <span data-ttu-id="cedc6-131">以次要複本的方式執行時，針對其資料庫執行備份作業。</span><span class="sxs-lookup"><span data-stu-id="cedc6-131">Performing backup operations on its databases when it is running as a secondary replica.</span></span> <span data-ttu-id="cedc6-132">如需詳細資訊，請參閱使用中[次要資料庫：次要複本上的備份](https://msdn.microsoft.com/library/ff878253.aspx)) 。</span><span class="sxs-lookup"><span data-stu-id="cedc6-132">For more information, see [Active Secondaries: Backup on Secondary Replicas](https://msdn.microsoft.com/library/ff878253.aspx)).</span></span>  
  
     <span data-ttu-id="cedc6-133">利用使用中次要功能可透過更善用次要硬體資源，改善 IT 效率並降低成本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-133">Using active secondary capabilities improves your IT efficiency and reduce cost through better resource utilization of secondary hardware.</span></span> <span data-ttu-id="cedc6-134">此外，透過將讀取意圖應用程式和備份作業卸載至次要複本，有助於提高主要複本的效能。</span><span class="sxs-lookup"><span data-stu-id="cedc6-134">In addition, offloading read-intent applications and backup jobs to secondary replicas helps to improve performance on the primary replica.</span></span>  
  
-   <span data-ttu-id="cedc6-135">支援每個可用性群組的可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="cedc6-135">Supports an availability group listener for each availability group.</span></span> <span data-ttu-id="cedc6-136">*「可用性群組接聽程式」* (Availability Group Listener) 是用戶端可連接的伺服器名稱，以便存取 AlwaysOn 可用性群組之主要或次要複本中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="cedc6-136">An *availability group listener* is a server name to which clients can connect in order to access a database in a primary or secondary replica of an AlwaysOn availability group.</span></span> <span data-ttu-id="cedc6-137">可用性群組接聽程式會將內送連接導向至主要複本或唯讀次要複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-137">Availability group listeners direct incoming connections to the primary replica or to a read-only secondary replica.</span></span> <span data-ttu-id="cedc6-138">接聽程式會在可用性群組容錯移轉之後提供快速應用程式容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="cedc6-138">The listener provides fast application failover after an availability group fails over.</span></span> <span data-ttu-id="cedc6-139">如需詳細資訊，請參閱[可用性群組接聽程式、用戶端連接和應用程式容錯移轉。SQL Server;](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-139">For more information, see [Availability Group Listeners, Client Connectivity, and Application Failover;SQL Server;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
-   <span data-ttu-id="cedc6-140">支援彈性容錯移轉原則，以便有效控制可用性群組容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="cedc6-140">Supports a flexible failover policy for greater control over availability-group failover.</span></span> <span data-ttu-id="cedc6-141">如需詳細資訊，請參閱[容錯移轉和容錯移轉模式。Always On 可用性群組;](failover-and-failover-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-141">For more information, see [Failover and Failover Modes; Always On Availability Groups;](failover-and-failover-modes-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="cedc6-142">支援防止頁面損毀的自動頁面修復。</span><span class="sxs-lookup"><span data-stu-id="cedc6-142">Supports automatic page repair for protection against page corruption.</span></span> <span data-ttu-id="cedc6-143">如需詳細資訊，請參閱[可用性群組和資料庫鏡像的自動修復頁面 &#40;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-143">For more information, see [Automatic Page Repair &#40;For Availability Groups and Database Mirroring;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="cedc6-144">支援加密和壓縮，可提供安全且高效能的傳輸方式。</span><span class="sxs-lookup"><span data-stu-id="cedc6-144">Supports encryption and compression, which provide a secure, high performing transport.</span></span>  
  
-   <span data-ttu-id="cedc6-145">提供一組整合式工具，可簡化可用性群組的部署和管理作業，包括：</span><span class="sxs-lookup"><span data-stu-id="cedc6-145">Provides an integrated set of tools to simplify deployment and management of availability groups, including:</span></span>  
  
    -   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="cedc6-146">DDL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cedc6-146">DDL statements for creating and managing availability groups.</span></span> <span data-ttu-id="cedc6-147">如需詳細資訊，請參閱[Always On 可用性群組的 Transact-sql 語句總覽;SQL Server;](transact-sql-statements-for-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-147">For more information, see [Overview of Transact-SQL Statements for Always On Availability Group;SQL Server;](transact-sql-statements-for-always-on-availability-groups.md).</span></span>  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="cedc6-148">工具，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cedc6-148">tools, as follows:</span></span>  
  
        -   <span data-ttu-id="cedc6-149">[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 會建立及設定可用性群組。</span><span class="sxs-lookup"><span data-stu-id="cedc6-149">The [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] creates and configures an availability group.</span></span> <span data-ttu-id="cedc6-150">在某些環境中，此精靈還可以自動準備次要資料庫並且為每個資料庫啟動資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="cedc6-150">In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them.</span></span> <span data-ttu-id="cedc6-151">如需詳細資訊，請參閱[使用新增可用性群組對話方塊。SQL Server Management Studio;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-151">For more information, see [Use the New Availability Group Dialog Box;SQL Server Management Studio;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md).</span></span>  
  
        -   <span data-ttu-id="cedc6-152">[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)]會將一個或多個主要資料庫加入至現有可用性群組。</span><span class="sxs-lookup"><span data-stu-id="cedc6-152">The [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] adds one or more primary databases to an existing availability group.</span></span> <span data-ttu-id="cedc6-153">在某些環境中，此精靈還可以自動準備次要資料庫並且為每個資料庫啟動資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="cedc6-153">In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them.</span></span> <span data-ttu-id="cedc6-154">如需詳細資訊，請參閱 [使用將資料庫加入至可用性群組精靈 (SQL Server)](availability-group-add-database-to-group-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-154">For more information, see [Use the Add Database to Availability Group Wizard (SQL Server)](availability-group-add-database-to-group-wizard.md).</span></span>  
  
        -   <span data-ttu-id="cedc6-155">[!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 會將一個或多個次要複本加入至現有可用性群組。</span><span class="sxs-lookup"><span data-stu-id="cedc6-155">The [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] adds one or more secondary replicas to an existing availability group.</span></span> <span data-ttu-id="cedc6-156">在某些環境中，此精靈還可以自動準備次要資料庫並且為每個資料庫啟動資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="cedc6-156">In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them.</span></span> <span data-ttu-id="cedc6-157">如需詳細資訊，請參閱[使用將複本加入至可用性群組 Wizard。SQL Server Management Studio;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-157">For more information, see [Use the Add Replica to Availability Group Wizard;SQL Server Management Studio;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
        -   <span data-ttu-id="cedc6-158">[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]會起始可用性群組的手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="cedc6-158">The [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] initiates a manual failover on an availability group.</span></span> <span data-ttu-id="cedc6-159">根據您指定為容錯移轉目標之次要複本的組態和狀態，此精靈可以執行規劃的手動容錯移轉或強制手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="cedc6-159">Depending on the configuration and state of the secondary replica that you specify as the failover target, the wizard can perform either a planned or forced manual failover.</span></span> <span data-ttu-id="cedc6-160">如需詳細資訊，請參閱[使用故障切換可用性群組嚮導。SQL Server Management Studio;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-160">For more information, see [Use the Fail Over Availability Group Wizard;SQL Server Management Studio;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
    -   <span data-ttu-id="cedc6-161">[!INCLUDE[ssAoDash](../../../includes/ssaodash-md.md)] 會監視 AlwaysOn 可用性群組、可用性複本和可用性資料庫，以及評估 AlwaysOn 原則的結果。</span><span class="sxs-lookup"><span data-stu-id="cedc6-161">The [!INCLUDE[ssAoDash](../../../includes/ssaodash-md.md)] monitors AlwaysOn availability groups, availability replicas, and availability databases and evaluates results for AlwaysOn policies.</span></span> <span data-ttu-id="cedc6-162">如需詳細資訊，請參閱[使用 AlwaysOn 儀表板;SQL Server Management Studio;](use-the-always-on-dashboard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-162">For more information, see [Use the AlwaysOn Dashboard;SQL Server Management Studio;](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
    -   <span data-ttu-id="cedc6-163">[物件總管詳細資料] 窗格會顯示現有可用性群組的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="cedc6-163">The Object Explorer Details pane displays basic information about existing availability groups.</span></span> <span data-ttu-id="cedc6-164">如需詳細資訊，請參閱[使用物件總管詳細資料監視可用性群組;SQL Server Management Studio;](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-164">For more information, see [Use the Object Explorer Details to Monitor Availability Group;SQL Server Management Studio;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="cedc6-165">PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="cedc6-165">PowerShell cmdlets.</span></span> <span data-ttu-id="cedc6-166">如需詳細資訊，請參閱[Always On 可用性群組的 PowerShell Cmdlet 總覽;SQL 服務;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-166">For more information, see [Overview of PowerShell Cmdlets for Always On Availability Groups;SQL Serve;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="cedc6-167">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="cedc6-167">Terms and Definitions</span></span>  
 <span data-ttu-id="cedc6-168">可用性群組</span><span class="sxs-lookup"><span data-stu-id="cedc6-168">availability group</span></span>  
 <span data-ttu-id="cedc6-169">一組一起容錯移轉之資料庫 (「可用性資料庫」\*\*) 的容器。</span><span class="sxs-lookup"><span data-stu-id="cedc6-169">A container for a set of databases, *availability databases*, that fail over together.</span></span>  
  
 <span data-ttu-id="cedc6-170">可用性資料庫</span><span class="sxs-lookup"><span data-stu-id="cedc6-170">availability database</span></span>  
 <span data-ttu-id="cedc6-171">屬於可用性群組的資料庫。</span><span class="sxs-lookup"><span data-stu-id="cedc6-171">A database that belongs to an availability group.</span></span> <span data-ttu-id="cedc6-172">對於每個可用性資料庫而言，可用性群組會維護單一讀寫複本 (「主要資料庫」**) 以及一到八個唯讀複本 (「次要資料庫」**)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-172">For each availability database, the availability group maintains a single read-write copy (the *primary database*) and one to eight read-only copies (*secondary databases*).</span></span>  
  
 <span data-ttu-id="cedc6-173">「主要伺服器」</span><span class="sxs-lookup"><span data-stu-id="cedc6-173">primary database</span></span>  
 <span data-ttu-id="cedc6-174">可用性資料庫的讀寫複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-174">The read-write copy of an availability database.</span></span>  
  
 <span data-ttu-id="cedc6-175">次要資料庫</span><span class="sxs-lookup"><span data-stu-id="cedc6-175">secondary database</span></span>  
 <span data-ttu-id="cedc6-176">可用性資料庫的唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-176">A read-only copy of an availability database.</span></span>  
  
 <span data-ttu-id="cedc6-177">「可用性複本」</span><span class="sxs-lookup"><span data-stu-id="cedc6-177">availability replica</span></span>  
 <span data-ttu-id="cedc6-178">特定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體所裝載之可用性群組的具現化，它會維護屬於可用性群組之每個可用性資料庫的本機副本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-178">An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and maintains a local copy of each availability database that belongs to the availability group.</span></span> <span data-ttu-id="cedc6-179">有兩種類型的可用性複本存在：單一 *「主要複本」* 以及一到八個 *「次要複本」*。</span><span class="sxs-lookup"><span data-stu-id="cedc6-179">Two types of availability replicas exist: a single *primary replica* and one to eight *secondary replicas*.</span></span>  
  
 <span data-ttu-id="cedc6-180">「主要複本」</span><span class="sxs-lookup"><span data-stu-id="cedc6-180">primary replica</span></span>  
 <span data-ttu-id="cedc6-181">可用性複本，該複本可讓主要資料庫用於用戶端的讀寫連接，同時也將每個主要資料庫的交易記錄檔記錄傳送到每個次要複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-181">The availability replica that makes the primary databases available for read-write connections from clients and, also, sends transaction log records for each primary database to every secondary replica.</span></span>  
  
 <span data-ttu-id="cedc6-182">次要複本</span><span class="sxs-lookup"><span data-stu-id="cedc6-182">secondary replica</span></span>  
 <span data-ttu-id="cedc6-183">可用性複本，該複本會維護每個可用性資料庫的次要副本，並且當做可用性群組的潛在容錯移轉目標。</span><span class="sxs-lookup"><span data-stu-id="cedc6-183">An availability replica that maintains a secondary copy of each availability database, and serves as a potential failover targets for the availability group.</span></span> <span data-ttu-id="cedc6-184">(選擇性) 可支援以唯讀方式存取次要資料庫的次要複本，可以支援在次要資料庫上建立備份。</span><span class="sxs-lookup"><span data-stu-id="cedc6-184">Optionally, a secondary replica can support read-only access to secondary databases can support creating backups on secondary databases.</span></span>  
  
 <span data-ttu-id="cedc6-185">可用性群組接聽程式</span><span class="sxs-lookup"><span data-stu-id="cedc6-185">availability group listener</span></span>  
 <span data-ttu-id="cedc6-186">用戶端可連接的伺服器名稱，以便存取 AlwaysOn 可用性群組之主要或次要複本中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="cedc6-186">A server name to which clients can connect in order to access a database in a primary or secondary replica of an Always On availability group.</span></span> <span data-ttu-id="cedc6-187">可用性群組接聽程式會將內送連接導向至主要複本或唯讀次要複本。</span><span class="sxs-lookup"><span data-stu-id="cedc6-187">Availability group listeners direct incoming connections to the primary replica or to a read-only secondary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cedc6-188">如需詳細資訊，請參閱[AlwaysOn 可用性群組的總覽。SQL 服務;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-188">For more information, see [Overview of AlwaysOn Availability Groups;SQL Serve;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="interoperability-and-coexistence-with-other-database-engine-features"></a><a name="Interoperability"></a> <span data-ttu-id="cedc6-189">與其他 Database Engine 功能的互通性和共存性</span><span class="sxs-lookup"><span data-stu-id="cedc6-189">Interoperability and Coexistence with Other Database Engine Features</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="cedc6-190">可搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的下列功能或元件使用：</span><span class="sxs-lookup"><span data-stu-id="cedc6-190">can be used with the following features or components of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="cedc6-191">關於變更資料捕獲;SQL Server;</span><span class="sxs-lookup"><span data-stu-id="cedc6-191">About Change Data Capture;SQL Server;</span></span>](../../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
-   [<span data-ttu-id="cedc6-192">關於變更追蹤;SQL 服務;</span><span class="sxs-lookup"><span data-stu-id="cedc6-192">About Change Tracking;SQL Serve;</span></span>](../../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
-   [<span data-ttu-id="cedc6-193">自主資料庫</span><span class="sxs-lookup"><span data-stu-id="cedc6-193">Contained databases</span></span>](../../../relational-databases/databases/contained-databases.md)  
  
-   [<span data-ttu-id="cedc6-194">資料庫加密</span><span class="sxs-lookup"><span data-stu-id="cedc6-194">Database encryption</span></span>](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
-   [<span data-ttu-id="cedc6-195">資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="cedc6-195">Database snapshots</span></span>](database-snapshots-with-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="cedc6-196">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="cedc6-196">FILESTREAM</span></span>](../../../relational-databases/blob/filestream-sql-server.md)  
  
-   [<span data-ttu-id="cedc6-197">FileTable</span><span class="sxs-lookup"><span data-stu-id="cedc6-197">FileTable</span></span>](../../../relational-databases/blob/filetables-sql-server.md)  
  
-   [<span data-ttu-id="cedc6-198">記錄傳送</span><span class="sxs-lookup"><span data-stu-id="cedc6-198">Log shipping</span></span>](../../log-shipping/about-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="cedc6-199">遠端 Blob 存放區 (RBS)</span><span class="sxs-lookup"><span data-stu-id="cedc6-199">Remote Blob Store (RBS)</span></span>](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
-   [<span data-ttu-id="cedc6-200">複寫</span><span class="sxs-lookup"><span data-stu-id="cedc6-200">Replication</span></span>](../../install-windows/install-sql-server-replication.md)  
  
-   [<span data-ttu-id="cedc6-201">Service Broker</span><span class="sxs-lookup"><span data-stu-id="cedc6-201">Service Broker</span></span>](../../configure-windows/sql-server-service-broker.md)  
  
-   [<span data-ttu-id="cedc6-202">SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="cedc6-202">SQL Server Agent</span></span>](../../../ssms/agent/sql-server-agent.md)  
  
-   [<span data-ttu-id="cedc6-203">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="cedc6-203">Reporting Services</span></span>](reporting-services-with-always-on-availability-groups-sql-server.md)  
  
> [!WARNING]  
>  <span data-ttu-id="cedc6-204">如需搭配使用其他功能的限制和限制的相關資訊 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，請參閱[Always On 可用性群組：互通性;SQL Server;](always-on-availability-groups-interoperability-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cedc6-204">For information about restrictions and limitations for using other features with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], see [Always On Availability Groups: Interoperability;SQL Server;](always-on-availability-groups-interoperability-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="cedc6-205">相關工作</span><span class="sxs-lookup"><span data-stu-id="cedc6-205">Related Tasks</span></span>  
  
-   [<span data-ttu-id="cedc6-206">具有 Always On 可用性群組的消費者入門;SQL Server;</span><span class="sxs-lookup"><span data-stu-id="cedc6-206">Getting Started with Always On Availability Groups;SQL Server;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="cedc6-207">相關內容</span><span class="sxs-lookup"><span data-stu-id="cedc6-207">Related Content</span></span>  
  
-   <span data-ttu-id="cedc6-208">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="cedc6-208">**Blogs:**</span></span>  
  
     [<span data-ttu-id="cedc6-209">SQL Server Always On 小組 Blog：官方 SQL Server AlwaysOn 小組的 Blog</span><span class="sxs-lookup"><span data-stu-id="cedc6-209">SQL Server Always On Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="cedc6-210">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="cedc6-210">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="cedc6-211">**影片：**</span><span class="sxs-lookup"><span data-stu-id="cedc6-211">**Videos:**</span></span>  
  
     <span data-ttu-id="cedc6-212">[Microsoft SQL Server Code-Named "Denali" Always On Series,Part 1:Introducing the Next Generation High Availability Solution](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302) (Microsoft SQL Server Code-Named "Denali" Always On 系列第 1 部分：新一代高可用性解決方案簡介)</span><span class="sxs-lookup"><span data-stu-id="cedc6-212">[Microsoft SQL Server Code-Named "Denali" Always On Series,Part 1: Introducing the Next Generation High Availability Solution](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)</span></span>  
  
     [<span data-ttu-id="cedc6-213">Microsoft SQL Server 程式碼名稱 "Denali" Always On 系列，第2部分：使用 AlwaysOn 建立要徑任務的高可用性解決方案</span><span class="sxs-lookup"><span data-stu-id="cedc6-213">Microsoft SQL Server Code-Named "Denali" Always On Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="cedc6-214">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="cedc6-214">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="cedc6-215">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="cedc6-215">Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="cedc6-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cedc6-216">See Also</span></span>  
 <span data-ttu-id="cedc6-217">[Always On 可用性群組的總覽;SQL Server;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cedc6-217">[Overview of Always On Availability Groups;SQL Server;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="cedc6-218">[AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="cedc6-218">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="cedc6-219">[設定 Always On 可用性群組的伺服器實例;SQL Server;](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cedc6-219">[Configuration of a Server Instance for Always On Availability Groups;SQL Server;](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="cedc6-220">[建立和設定可用性群組;SQL Server;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cedc6-220">[Creation and Configuration of Availability Groups;SQL Server;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="cedc6-221">[可用性群組的管理;SQL Server;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cedc6-221">[Administration of an Availability Group;SQL Server;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="cedc6-222">[監視可用性群組 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cedc6-222">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="cedc6-223">[Always On 可用性群組的 Transact-sql 語句總覽;SQL Server;](transact-sql-statements-for-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="cedc6-223">[Overview of Transact-SQL Statements for Always On Availability Groups;SQL Server;](transact-sql-statements-for-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="cedc6-224">概述適用于 AlwaysOn 可用性群組的 PowerShell Cmdlet;SQL Server;</span><span class="sxs-lookup"><span data-stu-id="cedc6-224">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups;SQL Server;</span></span>](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
