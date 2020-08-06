---
title: 資料庫快照集 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- static database views
- snapshots [SQL Server database snapshots]
- source databases [SQL Server]
- snapshots [SQL Server database snapshots], about database snapshots
- database snapshots [SQL Server]
- read-only database views
- database snapshots [SQL Server], about database snapshots
ms.assetid: 00179314-f23e-47cb-a35c-da6f180f86d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a0fa9b6cee2287d4e6060d4cb39f34d909e7db9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709574"
---
# <a name="database-snapshots-sql-server"></a><span data-ttu-id="f9a82-102">資料庫快照集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f9a82-102">Database Snapshots (SQL Server)</span></span>
  <span data-ttu-id="f9a82-103">資料庫快照集是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫 (「來源資料庫」) 的唯讀、靜態檢視。</span><span class="sxs-lookup"><span data-stu-id="f9a82-103">A database snapshot is a read-only, static view of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database (the *source database*).</span></span> <span data-ttu-id="f9a82-104">資料庫快照集會與快照集建立時的來源資料庫維持交易的一致性。</span><span class="sxs-lookup"><span data-stu-id="f9a82-104">The database snapshot is transactionally consistent with the source database as of the moment of the snapshot's creation.</span></span> <span data-ttu-id="f9a82-105">資料庫快照集一律會與其來源資料庫位於相同的伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="f9a82-105">A database snapshot always resides on the same server instance as its source database.</span></span> <span data-ttu-id="f9a82-106">當來源資料庫更新時，資料庫快照集也會更新。</span><span class="sxs-lookup"><span data-stu-id="f9a82-106">As the source database is updated, the database snapshot is updated.</span></span> <span data-ttu-id="f9a82-107">因此，資料庫快照集存在越久，就越有可能用光其可用的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="f9a82-107">Therefore, the longer a database snapshot exists, the more likely it is to use up its available disk space.</span></span>  
  
 <span data-ttu-id="f9a82-108">給定來源資料庫中可以存在多個快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-108">Multiple snapshots can exist on a given source database.</span></span> <span data-ttu-id="f9a82-109">每個資料庫快照集會一直保存，直到資料庫擁有者明確卸除為止。</span><span class="sxs-lookup"><span data-stu-id="f9a82-109">Each database snapshot persists until it is explicitly dropped by the database owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9a82-110">資料庫快照集與快照集備份、交易的快照隔離或快照複寫無關。</span><span class="sxs-lookup"><span data-stu-id="f9a82-110">Database snapshots are unrelated to snapshot backups, snapshot isolation of transactions, or snapshot replication.</span></span>  
  
 <span data-ttu-id="f9a82-111">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="f9a82-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="f9a82-112">功能概觀</span><span class="sxs-lookup"><span data-stu-id="f9a82-112">Feature Overview</span></span>](#FeatureOverview)  
  
-   [<span data-ttu-id="f9a82-113">資料庫快照集的優點</span><span class="sxs-lookup"><span data-stu-id="f9a82-113">Benefits of Database Snapshots</span></span>](#Benefits)  
  
-   [<span data-ttu-id="f9a82-114">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="f9a82-114">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="f9a82-115">資料庫快照集的必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="f9a82-115">Prerequisites for and Limitations on Database Snapshots</span></span>](#LimitationsRequirements)  
  
-   [<span data-ttu-id="f9a82-116">相關工作</span><span class="sxs-lookup"><span data-stu-id="f9a82-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="feature-overview"></a><a name="FeatureOverview"></a> <span data-ttu-id="f9a82-117">功能概觀</span><span class="sxs-lookup"><span data-stu-id="f9a82-117">Feature Overview</span></span>  
 <span data-ttu-id="f9a82-118">資料庫快照集是在資料頁層級上操作的。</span><span class="sxs-lookup"><span data-stu-id="f9a82-118">Database snapshots operate at the data-page level.</span></span> <span data-ttu-id="f9a82-119">在第一次修改來源資料庫的頁面之前，系統就會將原始頁面從來源資料庫複製到快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-119">Before a page of the source database is modified for the first time, the original page is copied from the source database to the snapshot.</span></span> <span data-ttu-id="f9a82-120">快照集會儲存原始頁面，保留快照集建立時已存在的資料記錄。</span><span class="sxs-lookup"><span data-stu-id="f9a82-120">The snapshot stores the original page, preserving the data records as they existed when the snapshot was created.</span></span> <span data-ttu-id="f9a82-121">第一次進行修改的每一頁，都會重複相同的處理序。</span><span class="sxs-lookup"><span data-stu-id="f9a82-121">The same process is repeated for every page that is being modified for the first time.</span></span> <span data-ttu-id="f9a82-122">對於使用者而言，資料庫快照集似乎不會改變，因為資料庫快照集上的讀取作業一定是存取原始資料頁 (不管原始資料頁位於何處)。</span><span class="sxs-lookup"><span data-stu-id="f9a82-122">To the user, a database snapshot appears never to change, because read operations on a database snapshot always access the original data pages, regardless of where they reside.</span></span>  
  
 <span data-ttu-id="f9a82-123">快照集在儲存所複製的原始頁面時，會使用一個或多個 *「疏鬆檔案」* (Sparse file)。</span><span class="sxs-lookup"><span data-stu-id="f9a82-123">To store the copied original pages, the snapshot uses one or more *sparse files*.</span></span> <span data-ttu-id="f9a82-124">一開始，疏鬆檔案其實是一個空白檔案，沒有包含使用者資料，也尚未配置磁碟空間來存放使用者資料。</span><span class="sxs-lookup"><span data-stu-id="f9a82-124">Initially, a sparse file is an essentially empty file that contains no user data and has not yet been allocated disk space for user data.</span></span> <span data-ttu-id="f9a82-125">隨著來源資料庫中有越來越多頁面更新，檔案大小也跟著成長。</span><span class="sxs-lookup"><span data-stu-id="f9a82-125">As more and more pages are updated in the source database, the size of the file grows.</span></span> <span data-ttu-id="f9a82-126">下圖說明兩個相反的更新模式，對於快照集大小的影響。</span><span class="sxs-lookup"><span data-stu-id="f9a82-126">The following figure illustrates the effects of two contrasting update patterns on the size of a snapshot.</span></span> <span data-ttu-id="f9a82-127">更新模式 A 所反映的環境，在快照集的生命期限內，只有 30% 的原始頁面有更新。</span><span class="sxs-lookup"><span data-stu-id="f9a82-127">Update pattern A reflects an environment in which only 30 percent of the original pages are updated during the life of the snapshot.</span></span> <span data-ttu-id="f9a82-128">更新模式 B 所反映的環境，在快照集的生命期限內，有 80% 的原始頁面有更新。</span><span class="sxs-lookup"><span data-stu-id="f9a82-128">Update pattern B reflects an environment in which 80 percent of the original pages are updated during the life of the snapshot.</span></span>  
  
 <span data-ttu-id="f9a82-129">![替代的更新模式和快照集大小](../../database-engine/media/dbview-04.gif "替代的更新模式和快照集大小")</span><span class="sxs-lookup"><span data-stu-id="f9a82-129">![Alternative update patterns and snapshot size](../../database-engine/media/dbview-04.gif "Alternative update patterns and snapshot size")</span></span>  
  
##  <a name="benefits-of-database-snapshots"></a><a name="Benefits"></a> <span data-ttu-id="f9a82-130">資料庫快照集的優點</span><span class="sxs-lookup"><span data-stu-id="f9a82-130">Benefits of Database Snapshots</span></span>  
  
-   <span data-ttu-id="f9a82-131">快照集可以用於報表用途。</span><span class="sxs-lookup"><span data-stu-id="f9a82-131">Snapshots can be used for reporting purposes.</span></span>  
  
     <span data-ttu-id="f9a82-132">用戶端可查詢資料庫快照集，方便根據快照集建立時的資料來撰寫報表。</span><span class="sxs-lookup"><span data-stu-id="f9a82-132">Clients can query a database snapshot, which makes it useful for writing reports based on the data at the time of snapshot creation.</span></span>  
  
-   <span data-ttu-id="f9a82-133">維護報表產生的歷程記錄資料。</span><span class="sxs-lookup"><span data-stu-id="f9a82-133">Maintaining historical data for report generation.</span></span>  
  
     <span data-ttu-id="f9a82-134">快照集可對特定時間點的資料提供使用者存取。</span><span class="sxs-lookup"><span data-stu-id="f9a82-134">A snapshot can extend user access to data from a particular point in time.</span></span> <span data-ttu-id="f9a82-135">例如，您可以在指定期間 (如財務季度) 結束時，建立資料庫快照集以供之後的報表使用。</span><span class="sxs-lookup"><span data-stu-id="f9a82-135">For example, you can create a database snapshot at the end of a given time period (such as a financial quarter) for later reporting.</span></span> <span data-ttu-id="f9a82-136">接著，您可以在快照集執行期末報表。</span><span class="sxs-lookup"><span data-stu-id="f9a82-136">You can then run end-of-period reports on the snapshot.</span></span> <span data-ttu-id="f9a82-137">如果磁碟空間容許的話，還可以永遠維持期末快照集，針對這些期間查詢結果；例如，調查組織效能。</span><span class="sxs-lookup"><span data-stu-id="f9a82-137">If disk space permits, you can also maintain end-of-period snapshots indefinitely, allowing queries against the results from these periods; for example, to investigate organizational performance.</span></span>  
  
-   <span data-ttu-id="f9a82-138">使用為了可用性用途而維護的鏡像資料庫，以卸載報表。</span><span class="sxs-lookup"><span data-stu-id="f9a82-138">Using a mirror database that you are maintaining for availability purposes to offload reporting.</span></span>  
  
     <span data-ttu-id="f9a82-139">將資料庫快照集與資料庫鏡像一起使用，可讓您存取鏡像伺服器上的資料以供報表使用。</span><span class="sxs-lookup"><span data-stu-id="f9a82-139">Using database snapshots with database mirroring permits you to make the data on the mirror server accessible for reporting.</span></span> <span data-ttu-id="f9a82-140">此外，在鏡像資料庫上執行查詢，可以釋放主體伺服器上的資源。</span><span class="sxs-lookup"><span data-stu-id="f9a82-140">Additionally, running queries on the mirror database can free up resources on the principal.</span></span> <span data-ttu-id="f9a82-141">如需詳細資訊，請參閱 [資料庫鏡像和資料庫快照集 &#40;SQL Server&#41;](database-snapshots-sql-server.md)(Sparse file)。</span><span class="sxs-lookup"><span data-stu-id="f9a82-141">For more information, see [Database Mirroring and Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f9a82-142">保護資料以防發生管理疏失。</span><span class="sxs-lookup"><span data-stu-id="f9a82-142">Safeguarding data against administrative error.</span></span>  
  
-   <span data-ttu-id="f9a82-143">在來源資料庫發生使用者錯誤的情況下，您可以將來源資料庫還原為建立給定資料庫快照集時所處的狀態。</span><span class="sxs-lookup"><span data-stu-id="f9a82-143">In the event of a user error on a source database, you can revert the source database to the state it was in when a given database snapshot was created.</span></span> <span data-ttu-id="f9a82-144">您只會失去建立快照集之後的資料庫更新資料。</span><span class="sxs-lookup"><span data-stu-id="f9a82-144">Data loss is confined to updates to the database since the snapshot's creation.</span></span>  
  
     <span data-ttu-id="f9a82-145">例如，在進行主要更新工作之前 (例如大量更新或結構描述變更)，在資料庫上建立資料庫快照集可保護資料。</span><span class="sxs-lookup"><span data-stu-id="f9a82-145">For example, before doing major updates, such as a bulk update or a schema change, create a database snapshot on the database protects data.</span></span> <span data-ttu-id="f9a82-146">如果發生錯誤，您可以將資料庫還原為快照集，利用快照集進行復原。</span><span class="sxs-lookup"><span data-stu-id="f9a82-146">If you make a mistake, you can use the snapshot to recover by reverting the database to the snapshot.</span></span> <span data-ttu-id="f9a82-147">就此用途而言，還原可能遠比從備份還原快；不過，還原之後就不能再向前復原。</span><span class="sxs-lookup"><span data-stu-id="f9a82-147">Reverting is potentially much faster for this purpose than restoring from a backup; however, you cannot roll forward afterward.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f9a82-148">離線或損毀的資料庫不能還原。</span><span class="sxs-lookup"><span data-stu-id="f9a82-148">Reverting does not work in an offline or corrupted database.</span></span> <span data-ttu-id="f9a82-149">因此，建立定期備份和測試還原計畫是保護資料庫的必要措施。</span><span class="sxs-lookup"><span data-stu-id="f9a82-149">Therefore, taking regular backups and testing your restore plan are necessary to protect a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9a82-150">資料庫快照集相依於來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9a82-150">Database snapshots are dependent on the source database.</span></span> <span data-ttu-id="f9a82-151">因此，使用資料庫快照集還原資料庫，並非備份和還原策略的替代方案。</span><span class="sxs-lookup"><span data-stu-id="f9a82-151">Therefore, using database snapshots for reverting a database is not a substitute for your backup and restore strategy.</span></span> <span data-ttu-id="f9a82-152">基本上還是請您執行所有排程備份。</span><span class="sxs-lookup"><span data-stu-id="f9a82-152">Performing all your scheduled backups remains essential.</span></span> <span data-ttu-id="f9a82-153">如果您必須將來源資料庫還原到您建立資料庫快照集當時的時間點，請實作可讓您執行此作業的備份原則。</span><span class="sxs-lookup"><span data-stu-id="f9a82-153">If you must restore the source database to the point in time at which you created a database snapshot, implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="f9a82-154">保護資料以防使用者有所疏失。</span><span class="sxs-lookup"><span data-stu-id="f9a82-154">Safeguarding data against user error.</span></span>  
  
     <span data-ttu-id="f9a82-155">定期建立資料庫快照集，可減輕因重大的使用者錯誤 (例如卸除的資料表) 所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="f9a82-155">By creating database snapshots on a regular basis, you can mitigate the impact of a major user error, such as a dropped table.</span></span> <span data-ttu-id="f9a82-156">如需更高階的保護，您可以建立一系列資料庫快照集，所涵蓋的時間長度足以辨識出大多數使用者造成的錯誤，並對之作出回應。</span><span class="sxs-lookup"><span data-stu-id="f9a82-156">For a high level of protection, you can create a series of database snapshots spanning enough time to recognize and respond to most user errors.</span></span> <span data-ttu-id="f9a82-157">例如，視您的磁碟資源而定，您可能會在 24 小時的間隔內，維護 6 到 12 個回復快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-157">For instance, you might maintain 6 to 12 rolling snapshots spanning a 24-hour interval, depending on your disk resources.</span></span> <span data-ttu-id="f9a82-158">接著，每建立一個新的快照集，就會刪除最舊的快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-158">Then, each time a new snapshot is created, the earliest snapshot can be deleted.</span></span>  
  
    -   <span data-ttu-id="f9a82-159">若要復原使用者造成的錯誤，您可以將資料庫還原為錯誤發生之前的快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-159">To recover from a user error, you can revert the database to the snapshot immediately before the error.</span></span> <span data-ttu-id="f9a82-160">就此用途而言，還原可能遠比從備份還原快；不過，還原之後就不能再向前復原。</span><span class="sxs-lookup"><span data-stu-id="f9a82-160">Reverting is potentially much faster for this purpose than restoring from a backup; however, you cannot roll forward afterward.</span></span>  
  
    -   <span data-ttu-id="f9a82-161">或者，可以利用快照集中的資訊，手動重新建構卸除的資料表，或其他遺失的資料。</span><span class="sxs-lookup"><span data-stu-id="f9a82-161">Alternatively, you may be able to manually reconstruct a dropped table or other lost data from the information in a snapshot.</span></span> <span data-ttu-id="f9a82-162">例如，您可以將快照集中的資料大量複製到資料庫中，並手動將資料合併到資料庫內。</span><span class="sxs-lookup"><span data-stu-id="f9a82-162">For instance, you could bulk copy the data out of the snapshot into the database and manually merge the data back into the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9a82-163">使用資料庫快照集的理由，會決定資料庫上同時要有幾個快照集、建立新快照集的頻率，以及保留快照集的時間長度。</span><span class="sxs-lookup"><span data-stu-id="f9a82-163">Your reasons for using database snapshots determine how many concurrent snapshots you need on a database, how frequently to create a new snapshot, and how long to keep it.</span></span>  
  
-   <span data-ttu-id="f9a82-164">管理測試資料庫</span><span class="sxs-lookup"><span data-stu-id="f9a82-164">Managing a test database</span></span>  
  
     <span data-ttu-id="f9a82-165">在測試環境中，在每一回測試開始時，對資料庫重複執行測試通訊協定以包含相同資料，是很有幫助的。</span><span class="sxs-lookup"><span data-stu-id="f9a82-165">In a testing environment, it can be useful when repeatedly running a test protocol for the database to contain identical data at the start of each round of testing.</span></span> <span data-ttu-id="f9a82-166">在執行第一回之前，應用程式開發人員或測試人員可以在測試資料庫上建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-166">Before running the first round, an application developer or tester can create a database snapshot on the test database.</span></span> <span data-ttu-id="f9a82-167">在每一回測試執行之後，可還原資料庫快照集，使資料庫快速回到它先前的狀態。</span><span class="sxs-lookup"><span data-stu-id="f9a82-167">After each test run, the database can be quickly returned to its prior state by reverting the database snapshot.</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="f9a82-168">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="f9a82-168">Terms and Definitions</span></span>  
 <span data-ttu-id="f9a82-169">database snapshot</span><span class="sxs-lookup"><span data-stu-id="f9a82-169">database snapshot</span></span>  
 <span data-ttu-id="f9a82-170">資料庫 (來源資料庫) 在交易上一致的唯讀、靜態檢視。</span><span class="sxs-lookup"><span data-stu-id="f9a82-170">A transactionally consistent, read-only, static view of a database (the source database).</span></span>  
  
 <span data-ttu-id="f9a82-171">來源資料庫</span><span class="sxs-lookup"><span data-stu-id="f9a82-171">source database</span></span>  
 <span data-ttu-id="f9a82-172">若是資料庫快照集，則為快照集建立所在的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9a82-172">For a database snapshot, the database on which the snapshot was created.</span></span> <span data-ttu-id="f9a82-173">資料庫快照集相依於來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9a82-173">Database snapshots are dependent on the source database.</span></span> <span data-ttu-id="f9a82-174">資料庫的快照集必須與資料庫位於相同的伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="f9a82-174">The snapshots of a database must be on the same server instance as the database.</span></span> <span data-ttu-id="f9a82-175">而且，如果該資料庫因某種原因而變成無法使用，則其所有資料庫快照集也會變成無法使用。</span><span class="sxs-lookup"><span data-stu-id="f9a82-175">Furthermore, if that database becomes unavailable for any reason, all of its database snapshots also become unavailable.</span></span>  
  
 <span data-ttu-id="f9a82-176">疏鬆檔案</span><span class="sxs-lookup"><span data-stu-id="f9a82-176">sparse file</span></span>  
 <span data-ttu-id="f9a82-177">NTFS 檔案系統提供的檔案，比其他方式需要更少磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="f9a82-177">A file provided by the NTFS file system that requires much less disk space than would otherwise be needed.</span></span> <span data-ttu-id="f9a82-178">疏鬆檔案可用來儲存複製到資料庫快照集的頁面。</span><span class="sxs-lookup"><span data-stu-id="f9a82-178">A sparse file is used to store pages copied to a database snapshot.</span></span> <span data-ttu-id="f9a82-179">初次建立時，疏鬆檔案所佔的磁碟空間很小。</span><span class="sxs-lookup"><span data-stu-id="f9a82-179">When first created, a sparse file takes up little disk space.</span></span> <span data-ttu-id="f9a82-180">當資料寫入資料庫快照集時，NTFS 也會逐漸將磁碟空間配置到對應的疏鬆檔案。</span><span class="sxs-lookup"><span data-stu-id="f9a82-180">As data is written to a database snapshot, NTFS allocates disk space gradually to the corresponding sparse file.</span></span>  
  
##  <a name="prerequisites-for-and-limitations-on-database-snapshots"></a><a name="LimitationsRequirements"></a> <span data-ttu-id="f9a82-181">資料庫快照集的必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="f9a82-181">Prerequisites for and Limitations on Database Snapshots</span></span>  
 <span data-ttu-id="f9a82-182">**本節內容：**</span><span class="sxs-lookup"><span data-stu-id="f9a82-182">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="f9a82-183">先決條件</span><span class="sxs-lookup"><span data-stu-id="f9a82-183">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="f9a82-184">對來源資料庫的限制</span><span class="sxs-lookup"><span data-stu-id="f9a82-184">Limitations on the Source Database</span></span>](#LimitsOnSourceDb)  
  
-   [<span data-ttu-id="f9a82-185">資料庫快照集的限制</span><span class="sxs-lookup"><span data-stu-id="f9a82-185">Limitations on Database Snapshots</span></span>](#LimitsOnDbSS)  
  
-   [<span data-ttu-id="f9a82-186">磁碟空間需求</span><span class="sxs-lookup"><span data-stu-id="f9a82-186">Disk Space Requirements</span></span>](#DiskSpace)  
  
-   [<span data-ttu-id="f9a82-187">含離線檔案群組的資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="f9a82-187">Database Snapshots with Offline Filegroups</span></span>](#OfflineFGs)  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f9a82-188">必要條件</span><span class="sxs-lookup"><span data-stu-id="f9a82-188">Prerequisites</span></span>  
 <span data-ttu-id="f9a82-189">可使用任何復原模式的來源資料庫必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="f9a82-189">The source database, which can use any recovery model, must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="f9a82-190">伺服器執行個體必須在支援資料庫快照集的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本上執行。</span><span class="sxs-lookup"><span data-stu-id="f9a82-190">The server instance must be running on an edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that supports database snapshots.</span></span> <span data-ttu-id="f9a82-191">如需詳細資訊，請參閱＜ [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f9a82-191">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="f9a82-192">除非來源資料庫是資料庫鏡像工作階段中的鏡像資料庫，否則該資料庫必須處於線上狀態。</span><span class="sxs-lookup"><span data-stu-id="f9a82-192">The source database must be online, unless the database is a mirror database within a database mirroring session.</span></span>  
  
-   <span data-ttu-id="f9a82-193">您可以在可用性群組的任何主要或次要資料庫上建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-193">You can create a database snapshot on any primary or secondary database in an availability group.</span></span> <span data-ttu-id="f9a82-194">複本角色必須是不在 RESOLVING 狀態的 PRIMARY 或 SECONDARY。</span><span class="sxs-lookup"><span data-stu-id="f9a82-194">The replica role must be either PRIMARY or SECONDARY, not in the RESOLVING state.</span></span>  
  
     <span data-ttu-id="f9a82-195">當您建立資料庫快照集時，建議資料庫同步處理狀態為 SYNCHRONIZING 或 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="f9a82-195">We recommend that the database synchronization state be SYNCHRONIZING or SYNCHRONIZED when you create a database snapshot.</span></span> <span data-ttu-id="f9a82-196">但是，當資料庫同步處理狀態為 NOT SYNCHRONIZING 時，可以建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-196">However, database snapshots can be created when the database synchronization state is NOT SYNCHRONIZING.</span></span>  
  
     <span data-ttu-id="f9a82-197">如需詳細資訊，請參閱[資料庫快照集與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f9a82-197">For more information, see [Database Snapshots with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f9a82-198">若要在鏡像資料庫上建立資料庫快照集，資料庫必須處於「已同步處理」的鏡像狀態。</span><span class="sxs-lookup"><span data-stu-id="f9a82-198">To create a database snapshot on a mirror database, the database must be in the SYNCHRONIZED mirroring state.</span></span>  
  
-   <span data-ttu-id="f9a82-199">來源資料庫無法設定為可擴充的共用資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9a82-199">The source database cannot be configured as a scalable shared database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9a82-200">所有復原模式都支援資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-200">All recovery models support database snapshots.</span></span>  
  
###  <a name="limitations-on-the-source-database"></a><a name="LimitsOnSourceDb"></a> <span data-ttu-id="f9a82-201">對來源資料庫的限制</span><span class="sxs-lookup"><span data-stu-id="f9a82-201">Limitations on the Source Database</span></span>  
 <span data-ttu-id="f9a82-202">只要資料庫快照集存在，快照集的來源資料庫就會有下列限制：</span><span class="sxs-lookup"><span data-stu-id="f9a82-202">As long as a database snapshot exists, the following limitations exist on the snapshot's source database:</span></span>  
  
-   <span data-ttu-id="f9a82-203">資料庫無法卸除、卸離或還原。</span><span class="sxs-lookup"><span data-stu-id="f9a82-203">The database cannot be dropped, detached, or restored.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9a82-204">來源資料庫的備份可照常運作，不受資料庫快照集的影響。</span><span class="sxs-lookup"><span data-stu-id="f9a82-204">Backing up the source database works normally; it is unaffected by database snapshots.</span></span>  
  
-   <span data-ttu-id="f9a82-205">效能會降低，這是因為每次更新頁面時，都會對快照集執行寫入時複製作業，因而導致來源資料庫上的 I/O 增加。</span><span class="sxs-lookup"><span data-stu-id="f9a82-205">Performance is reduced, due to increased I/O on the source database resulting from a copy-on-write operation to the snapshot every time a page is updated.</span></span>  
  
-   <span data-ttu-id="f9a82-206">無法從來源資料庫或任何快照集卸除檔案。</span><span class="sxs-lookup"><span data-stu-id="f9a82-206">Files cannot be dropped from the source database or from any snapshots.</span></span>  
  
###  <a name="limitations-on-database-snapshots"></a><a name="LimitsOnDbSS"></a> <span data-ttu-id="f9a82-207">資料庫快照集的限制</span><span class="sxs-lookup"><span data-stu-id="f9a82-207">Limitations on Database Snapshots</span></span>  
 <span data-ttu-id="f9a82-208">下列限制適用於資料庫快照集：</span><span class="sxs-lookup"><span data-stu-id="f9a82-208">The following limitations apply to database snapshots:</span></span>  
  
-   <span data-ttu-id="f9a82-209">建立及保留資料庫快照集的伺服器執行個體必須與來源資料庫相同。</span><span class="sxs-lookup"><span data-stu-id="f9a82-209">A database snapshot must be created and remain on the same server instance as the source database.</span></span>  
  
-   <span data-ttu-id="f9a82-210">資料庫快照集永遠會處理完整的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9a82-210">Database snapshots always work on an entire database.</span></span>  
  
-   <span data-ttu-id="f9a82-211">資料庫快照集相依於來源資料庫，且不是備援儲存體。</span><span class="sxs-lookup"><span data-stu-id="f9a82-211">Database snapshots are dependent on the source database and are not redundant storage.</span></span> <span data-ttu-id="f9a82-212">資料庫快照集無法防止磁碟錯誤或其他類型的損毀。</span><span class="sxs-lookup"><span data-stu-id="f9a82-212">They do not protect against disk errors or other types of corruption.</span></span> <span data-ttu-id="f9a82-213">因此，使用資料庫快照集還原資料庫，並非備份和還原策略的替代方案。</span><span class="sxs-lookup"><span data-stu-id="f9a82-213">Therefore, using database snapshots for reverting a database is not a substitute for your backup and restore strategy.</span></span> <span data-ttu-id="f9a82-214">基本上還是請您執行所有排程備份。</span><span class="sxs-lookup"><span data-stu-id="f9a82-214">Performing all your scheduled backups remains essential.</span></span> <span data-ttu-id="f9a82-215">如果您必須將來源資料庫還原到您建立資料庫快照集當時的時間點，請實作可讓您執行此作業的備份原則。</span><span class="sxs-lookup"><span data-stu-id="f9a82-215">If you must restore the source database to the point in time at which you created a database snapshot, implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="f9a82-216">當來源資料庫上更新過的頁面發送到快照集時，如果快照集正好用光了磁碟空間，或遇到一些其他錯誤，快照集會變成有疑問，因此必須刪除。</span><span class="sxs-lookup"><span data-stu-id="f9a82-216">When a page getting updated on the source database is pushed to a snapshot, if the snapshot runs out of disk space or encounters some other error, the snapshot becomes suspect and must be deleted.</span></span>  
  
-   <span data-ttu-id="f9a82-217">快照集是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f9a82-217">Snapshots are read-only.</span></span> <span data-ttu-id="f9a82-218">因為它們是唯讀的，所以無法升級。</span><span class="sxs-lookup"><span data-stu-id="f9a82-218">Since they are read only, they cannot be upgraded.</span></span> <span data-ttu-id="f9a82-219">因此，預期資料庫快照集在升級之後是無法使用的。</span><span class="sxs-lookup"><span data-stu-id="f9a82-219">Therefore, database snapshots are not expected to be viable after an upgrade.</span></span>  
  
-   <span data-ttu-id="f9a82-220">您無法為 **model**、 **master**與 **tempdb** 資料庫製作快照。</span><span class="sxs-lookup"><span data-stu-id="f9a82-220">Snapshots of the **model**, **master**, and **tempdb** databases are prohibited.</span></span>  
  
-   <span data-ttu-id="f9a82-221">您無法變更資料庫快照集檔案的任何規格。</span><span class="sxs-lookup"><span data-stu-id="f9a82-221">You cannot change any of the specifications of the database snapshot files.</span></span>  
  
-   <span data-ttu-id="f9a82-222">您無法從資料庫快照集卸除檔案。</span><span class="sxs-lookup"><span data-stu-id="f9a82-222">You cannot drop files from a database snapshot.</span></span>  
  
-   <span data-ttu-id="f9a82-223">您無法備份或還原資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-223">You cannot back up or restore database snapshots.</span></span>  
  
-   <span data-ttu-id="f9a82-224">您無法附加或卸離資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-224">You cannot attach or detach database snapshots.</span></span>  
  
-   <span data-ttu-id="f9a82-225">您無法在 FAT32 檔案系統或 RAW 磁碟分割上建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-225">You cannot create database snapshots on FAT32 file system or RAW partitions.</span></span> <span data-ttu-id="f9a82-226">資料庫快照集所使用的疏鬆檔案都由 NTFS 檔案系統提供。</span><span class="sxs-lookup"><span data-stu-id="f9a82-226">The sparse files used by database snapshots are provided by the NTFS file system.</span></span>  
  
-   <span data-ttu-id="f9a82-227">資料庫快照集不支援全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="f9a82-227">Full-text indexing is not supported on database snapshots.</span></span> <span data-ttu-id="f9a82-228">全文檢索目錄不會從來源資料庫傳播。</span><span class="sxs-lookup"><span data-stu-id="f9a82-228">Full-text catalogs are not propagated from the source database.</span></span>  
  
-   <span data-ttu-id="f9a82-229">資料庫快照集在建立快照集時，會繼承其來源資料庫的安全性限制。</span><span class="sxs-lookup"><span data-stu-id="f9a82-229">A database snapshot inherits the security constraints of its source database at the time of snapshot creation.</span></span> <span data-ttu-id="f9a82-230">因為快照集是唯讀的，所以無法變更所繼承的權限，而且對來源進行的權限變更都無法反映在現有的快照集中。</span><span class="sxs-lookup"><span data-stu-id="f9a82-230">Because snapshots are read-only, inherited permissions cannot be changed and permission changes made to the source will not be reflected in existing snapshots.</span></span>  
  
-   <span data-ttu-id="f9a82-231">快照集永遠反映出快照集建立時的檔案群組狀態：線上檔案群組保持線上狀態、離線檔案群組保持離線狀態。</span><span class="sxs-lookup"><span data-stu-id="f9a82-231">A snapshot always reflects the state of filegroups at the time of snapshot creation: online filegroups remain online, and offline filegroups remain offline.</span></span> <span data-ttu-id="f9a82-232">如需詳細資訊，請參閱本主題稍後的「含離線檔案群組的資料庫快照集」。</span><span class="sxs-lookup"><span data-stu-id="f9a82-232">For more information, see "Database Snapshots with Offline Filegroups" later in this topic.</span></span>  
  
-   <span data-ttu-id="f9a82-233">如果來源資料庫變成 RECOVERY_PENDING，其資料庫快照集可能會無法存取。</span><span class="sxs-lookup"><span data-stu-id="f9a82-233">If a source database becomes RECOVERY_PENDING, its database snapshots may become inaccessible.</span></span> <span data-ttu-id="f9a82-234">不過，在解決來源資料庫的問題之後，其快照集應該就可以使用了。</span><span class="sxs-lookup"><span data-stu-id="f9a82-234">After the issue on the source database is resolved, however, its snapshots should become available again.</span></span>  
  
-   <span data-ttu-id="f9a82-235">唯讀檔案群組以及壓縮檔案群組不支援還原，</span><span class="sxs-lookup"><span data-stu-id="f9a82-235">Reverting is unsupported for read-only filegroups and for compressed filegroups.</span></span> <span data-ttu-id="f9a82-236">嘗試還原包含這兩種檔案群組類型的資料庫都會失敗。</span><span class="sxs-lookup"><span data-stu-id="f9a82-236">Attempts to revert a database containing either of these types of filegroups fail.</span></span>  
  
-   <span data-ttu-id="f9a82-237">在記錄傳送組態中，只能在主要資料庫上建立資料庫快照集，不能在次要資料庫上建立。</span><span class="sxs-lookup"><span data-stu-id="f9a82-237">In a log shipping configuration, database snapshots can be created only on the primary database, not on a secondary database.</span></span> <span data-ttu-id="f9a82-238">如果在主要伺服器執行個體和次要伺服器執行個體之間切換角色，您必須先卸除所有的資料庫快照集，然後才能將主要資料庫設定為次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9a82-238">If you switch roles between the primary server instance and a secondary server instance, you must drop all the database snapshots before you can set the primary database up as a secondary database.</span></span>  
  
-   <span data-ttu-id="f9a82-239">資料庫快照集無法設定為可擴充的共用資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9a82-239">A database snapshot cannot be configured as a scalable shared database.</span></span>  
  
-   <span data-ttu-id="f9a82-240">資料庫快照集不支援 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="f9a82-240">FILESTREAM filegroups are not supported by database snapshots.</span></span> <span data-ttu-id="f9a82-241">如果 FILESTREAM 檔案群組存在來源資料庫中，它們就會在其資料庫快照集中標示為離線，而且這些資料庫快照集無法用於還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9a82-241">If FILESTREAM filegroups exist in a source database, they are marked as offline in its database snapshots, and the database snapshots cannot be used for reverting the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9a82-242">針對資料庫快照集執行的 SELECT 陳述式不得指定 FILESTREAM 資料行，否則將會傳回下列錯誤訊息： `Could not continue scan with NOLOCK due to data movement.`</span><span class="sxs-lookup"><span data-stu-id="f9a82-242">A SELECT statement that is executed on a database snapshot must not specify a FILESTREAM column; otherwise, the following error message will be returned: `Could not continue scan with NOLOCK due to data movement.`</span></span>  
  
-   <span data-ttu-id="f9a82-243">如果唯讀快照集上的統計資料遺漏或過時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會在 tempdb 中建立及維護暫時性統計資料。</span><span class="sxs-lookup"><span data-stu-id="f9a82-243">When statistics on a read-only snapshot are missing or stale, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] creates and maintains temporary statistics in tempdb.</span></span> <span data-ttu-id="f9a82-244">如需詳細資訊，請參閱[統計資料](../statistics/statistics.md)。</span><span class="sxs-lookup"><span data-stu-id="f9a82-244">For more information, see [Statistics](../statistics/statistics.md).</span></span>  
  
###  <a name="disk-space-requirements"></a><a name="DiskSpace"></a> <span data-ttu-id="f9a82-245">磁碟空間需求</span><span class="sxs-lookup"><span data-stu-id="f9a82-245">Disk Space Requirements</span></span>  
 <span data-ttu-id="f9a82-246">資料庫快照集會耗用磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="f9a82-246">Database snapshots consume disk space.</span></span> <span data-ttu-id="f9a82-247">如果資料庫快照集用光磁碟空間，它會標示為有疑問，因此必須卸除</span><span class="sxs-lookup"><span data-stu-id="f9a82-247">If a database snapshot runs out of disk space, it is marked as suspect and must be dropped.</span></span> <span data-ttu-id="f9a82-248">(不過，來源資料庫不受影響，其上的動作會繼續正常執行)。但是，與資料庫的完整副本相比，快照集的空間利用率仍算是很有效率了。</span><span class="sxs-lookup"><span data-stu-id="f9a82-248">(The source database, however, is not affected; actions on it continue normally.) Compared to a full copy of a database, however, snapshots are highly space efficient.</span></span> <span data-ttu-id="f9a82-249">快照集所需儲存空間，只要足夠儲存那些在存留時間內會有變更的頁面即可。</span><span class="sxs-lookup"><span data-stu-id="f9a82-249">A snapshot requires only enough storage for the pages that change during its lifetime.</span></span> <span data-ttu-id="f9a82-250">通常，快照集只會保存一段有限的時間，所以其大小不會是大問題。</span><span class="sxs-lookup"><span data-stu-id="f9a82-250">Generally, snapshots are kept for a limited time, so their size is not a major concern.</span></span>  
  
 <span data-ttu-id="f9a82-251">不過，您保存快照集的時間越長，就越有可能用光可用空間。</span><span class="sxs-lookup"><span data-stu-id="f9a82-251">The longer you keep a snapshot, however, the more likely it is to use up available space.</span></span> <span data-ttu-id="f9a82-252">疏鬆檔案的成長大小上限，就是建立快照集時對應來源資料庫檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="f9a82-252">The maximum size to which a sparse file can grow is the size of the corresponding source database file at the time of the snapshot creation.</span></span>  
  
 <span data-ttu-id="f9a82-253">若資料庫快照集用盡磁碟空間，則必須刪除 (卸除) 快照集。</span><span class="sxs-lookup"><span data-stu-id="f9a82-253">If a database snapshot runs out of disk space, it must be deleted (dropped).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9a82-254">除了檔案空間以外，資料庫快照集耗用的資源數量大致上與資料庫相同。</span><span class="sxs-lookup"><span data-stu-id="f9a82-254">Except for file space, a database snapshot consumes roughly as many resources as a database.</span></span>  
  
###  <a name="database-snapshots-with-offline-filegroups"></a><a name="OfflineFGs"></a> <span data-ttu-id="f9a82-255">含離線檔案群組的資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="f9a82-255">Database Snapshots with Offline Filegroups</span></span>  
 <span data-ttu-id="f9a82-256">當您嘗試執行下列任一動作時，來源資料庫中的離線檔案群組會影響到資料庫快照集：</span><span class="sxs-lookup"><span data-stu-id="f9a82-256">Offline filegroups in the source database affect database snapshots when you try to do any of the following:</span></span>  
  
-   <span data-ttu-id="f9a82-257">建立快照集</span><span class="sxs-lookup"><span data-stu-id="f9a82-257">Create a snapshot</span></span>  
  
     <span data-ttu-id="f9a82-258">來源資料庫具有一個或多個離線檔案群組時，快照集會在這些檔案群組離線的狀態下順利建立。</span><span class="sxs-lookup"><span data-stu-id="f9a82-258">When a source database has one or more offline filegroups, snapshot creation succeeds with the filegroups offline.</span></span> <span data-ttu-id="f9a82-259">但是，系統並不會為離線檔案群組建立疏鬆檔案。</span><span class="sxs-lookup"><span data-stu-id="f9a82-259">Sparse files are not created for the offline filegroups.</span></span>  
  
-   <span data-ttu-id="f9a82-260">使檔案群組離線</span><span class="sxs-lookup"><span data-stu-id="f9a82-260">Take a filegroup offline</span></span>  
  
     <span data-ttu-id="f9a82-261">您可以使來源資料庫中的檔案離線。</span><span class="sxs-lookup"><span data-stu-id="f9a82-261">You can take a file offline in the source database.</span></span> <span data-ttu-id="f9a82-262">不過，如果建立快照集時，檔案群組是在線上，則在資料庫快照集中該檔案群組仍保持在線上。</span><span class="sxs-lookup"><span data-stu-id="f9a82-262">However, the filegroup remains online in database snapshots if it was online when the snapshot was created.</span></span> <span data-ttu-id="f9a82-263">如果建立快照集後查詢的資料已變更，其原始資料頁仍可從快照集中存取。</span><span class="sxs-lookup"><span data-stu-id="f9a82-263">If the queried data has changed since snapshot creation, the original data page will be accessible in the snapshot.</span></span> <span data-ttu-id="f9a82-264">不過，若想使用查詢從快照集存取檔案群組中的未修改資料，可能會失敗並發生輸入/輸出 (I/O) 錯誤。</span><span class="sxs-lookup"><span data-stu-id="f9a82-264">However, queries that use the snapshot to access unmodified data in the filegroup are likely to fail with input/output (I/O) errors.</span></span>  
  
-   <span data-ttu-id="f9a82-265">使檔案群組上線</span><span class="sxs-lookup"><span data-stu-id="f9a82-265">Bring a filegroup online</span></span>  
  
     <span data-ttu-id="f9a82-266">您不能使擁有任何資料庫快照集之資料庫中的檔案群組上線。</span><span class="sxs-lookup"><span data-stu-id="f9a82-266">You cannot bring a filegroup online in a database that has any database snapshots.</span></span> <span data-ttu-id="f9a82-267">如果檔案群組在建立快照集時為離線狀態，或在有資料庫快照集存在時使檔案群組離線，檔案群組將保持離線狀態。</span><span class="sxs-lookup"><span data-stu-id="f9a82-267">If a filegroup is offline at the time of snapshot creation or is taken offline while a database snapshot exists, the filegroup remains offline.</span></span> <span data-ttu-id="f9a82-268">這是因為將檔案恢復上線涉及還原檔案，而如果資料庫上有資料庫快照集存在，就不能還原檔案。</span><span class="sxs-lookup"><span data-stu-id="f9a82-268">This is because bringing a file back online involves restoring it, which is not possible if a database snapshot exists on the database.</span></span>  
  
-   <span data-ttu-id="f9a82-269">將來源資料庫還原到快照集</span><span class="sxs-lookup"><span data-stu-id="f9a82-269">Revert the source database to the snapshot</span></span>  
  
     <span data-ttu-id="f9a82-270">若要將來源資料庫還原到資料庫快照集，所有檔案群組都必須在線上，但建立快照集時已離線的檔案群組除外。</span><span class="sxs-lookup"><span data-stu-id="f9a82-270">Reverting a source database to a database snapshot requires that all of the filegroups are online except for filegroups that were offline when the snapshot was created.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f9a82-271">相關工作</span><span class="sxs-lookup"><span data-stu-id="f9a82-271">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f9a82-272">建立資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f9a82-272">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="f9a82-273">檢視資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9a82-273">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="f9a82-274">檢視資料庫快照集的疏鬆檔案大小 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f9a82-274">View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;</span></span>](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="f9a82-275">將資料庫還原成資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="f9a82-275">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="f9a82-276">卸除資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f9a82-276">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="f9a82-277">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9a82-277">See Also</span></span>  
 [<span data-ttu-id="f9a82-278">資料庫鏡像和資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9a82-278">Database Mirroring and Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
