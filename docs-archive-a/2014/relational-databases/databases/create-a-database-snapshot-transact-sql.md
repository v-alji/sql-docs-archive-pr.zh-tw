---
title: 建立資料庫快照集 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], creating
ms.assetid: 187fbba3-c555-4030-9bdf-0f01994c5230
author: stevestein
ms.author: sstein
ms.openlocfilehash: bae68c2d507e1dd3809e76a9d842b765d72234e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709585"
---
# <a name="create-a-database-snapshot-transact-sql"></a><span data-ttu-id="dd014-102">建立資料庫快照集 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dd014-102">Create a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="dd014-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是建立 [!INCLUDE[tsql](../../includes/tsql-md.md)]資料庫快照集的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="dd014-103">The only way to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshot is to use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="dd014-104">不支援建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-104">does not support the creation of database snapshots.</span></span>  
  
-   <span data-ttu-id="dd014-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="dd014-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dd014-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="dd014-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="dd014-107">安全性</span><span class="sxs-lookup"><span data-stu-id="dd014-107">Security</span></span>](#Security)  
  
     [<span data-ttu-id="dd014-108">最佳做法：命名資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-108">Best Practice: Naming Database Snapshots</span></span>](#Naming)  
  
-   <span data-ttu-id="dd014-109">**若要建立資料庫快照集，請使用：**  [transact-sql](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="dd014-109">**To create a database snapshot, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dd014-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="dd014-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="dd014-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="dd014-111">Prerequisites</span></span>  
 <span data-ttu-id="dd014-112">可使用任何復原模式的來源資料庫必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="dd014-112">The source database, which can use any recovery model, must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="dd014-113">伺服器執行個體必須執行支援資料庫快照集的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="dd014-113">The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports database snapshot.</span></span> <span data-ttu-id="dd014-114">如需中資料庫快照集支援的詳細資訊 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="dd014-114">For information about support for database snapshots in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="dd014-115">除非來源資料庫是資料庫鏡像工作階段中的鏡像資料庫，否則該資料庫必須處於線上狀態。</span><span class="sxs-lookup"><span data-stu-id="dd014-115">The source database must be online, unless the database is a mirror database within a database mirroring session.</span></span>  
  
-   <span data-ttu-id="dd014-116">若要在鏡像資料庫上建立資料庫快照集，資料庫必須處於同步處理的[鏡像狀態](../../database-engine/database-mirroring/mirroring-states-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dd014-116">To create a database snapshot on a mirror database, the database must be in the synchronized[mirroring state](../../database-engine/database-mirroring/mirroring-states-sql-server.md).</span></span>  
  
-   <span data-ttu-id="dd014-117">來源資料庫無法設定為可擴充的共用資料庫。</span><span class="sxs-lookup"><span data-stu-id="dd014-117">The source database cannot be configured as a scalable shared database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dd014-118">如需其他重要考量的資訊，請參閱 [資料庫快照集 &#40;SQL Server&#41;](database-snapshots-sql-server.md)資料庫快照集的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="dd014-118">For information about other significant considerations, see [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="dd014-119">建議</span><span class="sxs-lookup"><span data-stu-id="dd014-119">Recommendations</span></span>  
 <span data-ttu-id="dd014-120">本節討論下列最佳作法：</span><span class="sxs-lookup"><span data-stu-id="dd014-120">This section discusses the following best practices:</span></span>  
  
-   [<span data-ttu-id="dd014-121">最佳做法：命名資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-121">Best Practice: Naming Database Snapshots</span></span>](#Naming)  
  
-   [<span data-ttu-id="dd014-122">最佳做法：限制資料庫快照集的數目</span><span class="sxs-lookup"><span data-stu-id="dd014-122">Best Practice: Limiting the Number of Database Snapshots</span></span>](#Limiting_Number)  
  
-   [<span data-ttu-id="dd014-123">最佳做法：用戶端連線到資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-123">Best Practice: Client Connections to a Database Snapshot</span></span>](#Client_Connections)  
  
####  <a name="best-practice-naming-database-snapshots"></a><a name="Naming"></a> <span data-ttu-id="dd014-124">最佳做法：命名資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-124">Best Practice: Naming Database Snapshots</span></span>  
 <span data-ttu-id="dd014-125">建立快照集之前，務必先考慮如何命名快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-125">Before creating snapshots, it is important to consider how to name them.</span></span> <span data-ttu-id="dd014-126">每個資料庫快照集都需要一個唯一的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="dd014-126">Each database snapshot requires a unique database name.</span></span> <span data-ttu-id="dd014-127">為了方便管理，快照集的名稱可加入用於識別資料庫的資訊，例如：</span><span class="sxs-lookup"><span data-stu-id="dd014-127">For administrative ease, the name of a snapshot can incorporate information that identifies the database, such as:</span></span>  
  
-   <span data-ttu-id="dd014-128">來源資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd014-128">The name of the source database.</span></span>  
  
-   <span data-ttu-id="dd014-129">表明新名稱是用於快照集的指示。</span><span class="sxs-lookup"><span data-stu-id="dd014-129">An indication that the new name is for a snapshot.</span></span>  
  
-   <span data-ttu-id="dd014-130">建立快照集的日期和時間、序號或其他資訊 (例如一天中的時間)，以便區隔給定資料庫上的循序快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-130">The creation date and time of the snapshot, a sequence number, or some other information, such as time of day, to distinguish sequential snapshots on a given database.</span></span>  
  
 <span data-ttu-id="dd014-131">例如，假設 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫有一系列的快照集，</span><span class="sxs-lookup"><span data-stu-id="dd014-131">For example, consider a series of snapshots for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="dd014-132">三個每日快照集依據 24 小時制，以 6 小時為間隔，從早上 6 點</span><span class="sxs-lookup"><span data-stu-id="dd014-132">Three daily snapshots are created at 6-hour intervals between 6 A.M.</span></span> <span data-ttu-id="dd014-133">到下午 6 點間分別建立。</span><span class="sxs-lookup"><span data-stu-id="dd014-133">and 6 P.M., based on a 24-hour clock.</span></span> <span data-ttu-id="dd014-134">每個每日快照集在卸除並被相同名稱的新快照集取代之前，會先保留 24 小時。</span><span class="sxs-lookup"><span data-stu-id="dd014-134">Each daily snapshot is kept for 24 hours before being dropped and replaced by a new snapshot of the same name.</span></span> <span data-ttu-id="dd014-135">注意下列快照集名稱，每個都表示時間 (小時)，而非日期：</span><span class="sxs-lookup"><span data-stu-id="dd014-135">Note that each snapshot name indicates the hour, but not the day:</span></span>  
  
```  
AdventureWorks_snapshot_0600  
AdventureWorks_snapshot_1200  
AdventureWorks_snapshot_1800  
```  
  
 <span data-ttu-id="dd014-136">或者，如果每天建立這些每日快照集的時間會變動，則最好採用一個較籠統的命名慣例，例如：</span><span class="sxs-lookup"><span data-stu-id="dd014-136">Alternatively, if the creation time of these daily snapshots varies from day to day, a less precise naming convention might be preferable, for example:</span></span>  
  
```  
AdventureWorks_snapshot_morning  
AdventureWorks_snapshot_noon  
AdventureWorks_snapshot_evening  
```  
  
####  <a name="best-practice-limiting-the-number-of-database-snapshots"></a><a name="Limiting_Number"></a> <span data-ttu-id="dd014-137">最佳做法：限制資料庫快照集的數目</span><span class="sxs-lookup"><span data-stu-id="dd014-137">Best Practice: Limiting the Number of Database Snapshots</span></span>  
 <span data-ttu-id="dd014-138">隨時間建立一系列的快照集，可擷取來源資料庫的循序快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-138">Creating a series of snapshots over time captures sequential snapshots of the source database.</span></span> <span data-ttu-id="dd014-139">每個快照集都會一直保存到確實卸除該快照集為止。</span><span class="sxs-lookup"><span data-stu-id="dd014-139">Each snapshot persists until it is explicitly dropped.</span></span> <span data-ttu-id="dd014-140">因為每個快照集都會隨著原始頁面更新而不斷成長，所以您可能想要在建立新快照集之後，刪除較早的快照集，以節省磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="dd014-140">Because each snapshot will continue to grow as original pages are updated, you may want to conserve disk space by deleting an older snapshot after creating a new snapshot.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd014-141">若要還原為資料庫快照集，您需要刪除該資訊庫中的任何其他快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-141">If you want to revert to a database snapshot, you need to delete any other snapshots from that database.</span></span>  
  
####  <a name="best-practice-client-connections-to-a-database-snapshot"></a><a name="Client_Connections"></a> <span data-ttu-id="dd014-142">最佳做法：用戶端連線到資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-142">Best Practice: Client Connections to a Database Snapshot</span></span>  
 <span data-ttu-id="dd014-143">若要使用資料庫快照集，用戶端需要知道去哪裡尋找。</span><span class="sxs-lookup"><span data-stu-id="dd014-143">To use a database snapshot, clients need to know where to find it.</span></span> <span data-ttu-id="dd014-144">正在建立或刪除某個資料庫快照集時，使用者仍可讀取其他快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-144">Users can read from one database snapshot while another is being created or deleted.</span></span> <span data-ttu-id="dd014-145">但是，當您以新的快照集取代現有的快照集時，必須將用戶端重新導向至新的快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-145">However, when you substitute a new snapshot for an existing one, you need to redirect clients to the new snapshot.</span></span> <span data-ttu-id="dd014-146">使用者可以利用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，手動連接到資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-146">Users can manually connect to a database snapshot by means of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="dd014-147">但是，若要支援實際執行環境，您應該建立程式設計方案，將撰寫報表的用戶端明確導向至資料庫最新的資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-147">However, to support a production environment, you should create a programmatic solution that transparently directs report-writing clients to the latest database snapshot of the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dd014-148">Security</span><span class="sxs-lookup"><span data-stu-id="dd014-148">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dd014-149">權限</span><span class="sxs-lookup"><span data-stu-id="dd014-149">Permissions</span></span>  
 <span data-ttu-id="dd014-150">能夠建立資料庫的任何使用者都可以建立資料庫快照集，不過若要建立鏡像資料庫的快照集，您必須是 **sysadmin** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="dd014-150">Any user who can create a database can create a database snapshot; however, to create a snapshot of a mirror database, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="how-to-create-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dd014-151">如何建立資料庫快照集 (使用 Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dd014-151">How to Create a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="dd014-152">**若要建立資料庫快照集**</span><span class="sxs-lookup"><span data-stu-id="dd014-152">**To create a database snapshot**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd014-153">如需此程序的範例，請參閱本節稍後的 [範例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="dd014-153">For an example of this procedure, see [Examples (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="dd014-154">根據來源資料庫的目前大小，確定您擁有足夠的磁碟空間可存放資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-154">Based on the current size of the source database, ensure that you have sufficient disk space to hold the database snapshot.</span></span> <span data-ttu-id="dd014-155">資料庫快照集的大小上限為快照集建立時的來源資料庫大小。</span><span class="sxs-lookup"><span data-stu-id="dd014-155">The maximum size of a database snapshot is the size of the source database at snapshot creation.</span></span> <span data-ttu-id="dd014-156">如需詳細資訊，請參閱[檢視資料庫快照集的疏鬆檔案大小 &#40;Transact-SQL&#41;](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="dd014-156">For more information, see [View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="dd014-157">在使用 AS SNAPSHOT OF 子句的檔案上，發出 CREATE DATABASE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="dd014-157">Issue a CREATE DATABASE statement on the files using the AS SNAPSHOT OF clause.</span></span> <span data-ttu-id="dd014-158">建立快照集必須指定來源資料庫之每個資料庫檔案的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="dd014-158">Creating a snapshot requires specifying the logical name of every database file of the source database.</span></span> <span data-ttu-id="dd014-159">語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd014-159">The syntax is as follows:</span></span>  
  
     <span data-ttu-id="dd014-160">CREATE DATABASE *database_snapshot_name*</span><span class="sxs-lookup"><span data-stu-id="dd014-160">CREATE DATABASE *database_snapshot_name*</span></span>  
  
     <span data-ttu-id="dd014-161">開啟</span><span class="sxs-lookup"><span data-stu-id="dd014-161">ON</span></span>  
  
     <span data-ttu-id="dd014-162">(</span><span class="sxs-lookup"><span data-stu-id="dd014-162">(</span></span>  
  
     <span data-ttu-id="dd014-163">NAME =*logical_file_name*,</span><span class="sxs-lookup"><span data-stu-id="dd014-163">NAME =*logical_file_name*,</span></span>  
  
     <span data-ttu-id="dd014-164">FILENAME ='*os_file_name*'</span><span class="sxs-lookup"><span data-stu-id="dd014-164">FILENAME ='*os_file_name*'</span></span>  
  
     <span data-ttu-id="dd014-165">) [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="dd014-165">) [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="dd014-166">AS SNAPSHOT OF *source_database_name*</span><span class="sxs-lookup"><span data-stu-id="dd014-166">AS SNAPSHOT OF *source_database_name*</span></span>  
  
     <span data-ttu-id="dd014-167">[;]</span><span class="sxs-lookup"><span data-stu-id="dd014-167">[;]</span></span>  
  
     <span data-ttu-id="dd014-168">其中 *source_\*\*database_name* 是來源資料庫，*logical_file_name* 是參考檔案時 SQL Server 中所使用的邏輯名稱，*os_file_name* 是建立檔案時作業系統所使用的路徑和檔案名稱，而 *database_snapshot_name* 是要還原資料庫的目標快照集名稱。</span><span class="sxs-lookup"><span data-stu-id="dd014-168">Where *source_\*\*database_name* is the source database, *logical_file_name i*s the logical name used in SQL Server when referencing the file, *os_file_name* is the path and file name used by the operating system when you create the file, and *database_snapshot_name* is the name of the snapshot to which you want to revert the database.</span></span> <span data-ttu-id="dd014-169">如需此語法的完整描述，請參閱 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)資料庫快照集的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="dd014-169">For a full description of this syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd014-170">建立資料庫快照集時，CREATE DATABASE 陳述式中不允許記錄檔、離線檔案、還原檔案與無用檔案。</span><span class="sxs-lookup"><span data-stu-id="dd014-170">When you create a database snapshot, log files, offline files, restoring files, and defunct files are not allowed in the CREATE DATABASE statement.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="dd014-171">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dd014-171">Examples (Transact-SQL)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd014-172">用於範例中的 `.ss` 副檔名可自行決定。</span><span class="sxs-lookup"><span data-stu-id="dd014-172">The `.ss` extension used in the examples is arbitrary.</span></span>  
  
 <span data-ttu-id="dd014-173">本區段包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="dd014-173">This section contains the following examples:</span></span>  
  
-   <span data-ttu-id="dd014-174">A.</span><span class="sxs-lookup"><span data-stu-id="dd014-174">A.</span></span> [<span data-ttu-id="dd014-175">在 AdventureWorks 資料庫上建立快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-175">Creating a snapshot on the AdventureWorks database</span></span>](#Creating_on_AW)  
  
-   <span data-ttu-id="dd014-176">B.</span><span class="sxs-lookup"><span data-stu-id="dd014-176">B.</span></span> [<span data-ttu-id="dd014-177">在 Sales 資料庫上建立快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-177">Creating a snapshot on the Sales database</span></span>](#Creating_on_Sales)  
  
####  <a name="a-creating-a-snapshot-on-the-adventureworks-database"></a><a name="Creating_on_AW"></a> <span data-ttu-id="dd014-178">A.</span><span class="sxs-lookup"><span data-stu-id="dd014-178">A.</span></span> <span data-ttu-id="dd014-179">在 AdventureWorks 資料庫上建立快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-179">Creating a snapshot on the AdventureWorks database</span></span>  
 <span data-ttu-id="dd014-180">此範例會在 `AdventureWorks` 資料庫上建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="dd014-180">This example creates a database snapshot on the `AdventureWorks` database.</span></span> <span data-ttu-id="dd014-181">快照集名稱 `AdventureWorks_dbss_1800`與疏鬆檔案的檔案名稱 `AdventureWorks_data_1800.ss`，表示建立時間是 6 P.M (1800 小時)。</span><span class="sxs-lookup"><span data-stu-id="dd014-181">The snapshot name, `AdventureWorks_dbss_1800`, and the file name of its sparse file, `AdventureWorks_data_1800.ss`, indicate the creation time, 6 P.M (1800 hours).</span></span>  
  
```  
CREATE DATABASE AdventureWorks_dbss1800 ON  
( NAME = AdventureWorks_Data, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data\AdventureWorks_data_1800.ss' )  
AS SNAPSHOT OF AdventureWorks;  
GO  
```  
  
####  <a name="b-creating-a-snapshot-on-the-sales-database"></a><a name="Creating_on_Sales"></a> <span data-ttu-id="dd014-182">B.</span><span class="sxs-lookup"><span data-stu-id="dd014-182">B.</span></span> <span data-ttu-id="dd014-183">在 Sales 資料庫上建立快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-183">Creating a snapshot on the Sales database</span></span>  
 <span data-ttu-id="dd014-184">此範例會在 `sales_snapshot1200`資料庫上建立資料庫快照集 `Sales` 。</span><span class="sxs-lookup"><span data-stu-id="dd014-184">This example creates a database snapshot, `sales_snapshot1200`, on the `Sales` database.</span></span> <span data-ttu-id="dd014-185">此資料庫是在[建立資料庫 &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)中的「建立含有檔案群組的資料庫」範例中所建立。</span><span class="sxs-lookup"><span data-stu-id="dd014-185">This database was created in the example, "Creating a database that has filegroups," in [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
```  
--Creating sales_snapshot1200 as snapshot of the  
--Sales database:  
CREATE DATABASE sales_snapshot1200 ON  
( NAME = SPri1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri1dat_1200.ss'),  
( NAME = SPri2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri2dt_1200.ss'),  
( NAME = SGrp1Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\mssql\data\SG1Fi1dt_1200.ss'),  
( NAME = SGrp1Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG1Fi2dt_1200.ss'),  
( NAME = SGrp2Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi1dt_1200.ss'),  
( NAME = SGrp2Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi2dt_1200.ss')  
AS SNAPSHOT OF Sales;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="dd014-186">相關工作</span><span class="sxs-lookup"><span data-stu-id="dd014-186">Related Tasks</span></span>  
  
-   [<span data-ttu-id="dd014-187">檢視資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dd014-187">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="dd014-188">將資料庫還原成資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="dd014-188">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="dd014-189">卸除資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dd014-189">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="dd014-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd014-190">See Also</span></span>  
 <span data-ttu-id="dd014-191">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dd014-191">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="dd014-192">資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dd014-192">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
