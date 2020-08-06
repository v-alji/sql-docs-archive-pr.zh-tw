---
title: 重建索引工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reindex.f1
- reindex
helpviewer_keywords:
- Rebuild Index Task dialog box
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
author: rothja
ms.author: jroth
ms.openlocfilehash: bc9d7c85a72c34cee1ef7af8cb4b4f25f918a3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594520"
---
# <a name="rebuild-index-task-maintenance-plan"></a><span data-ttu-id="0a43a-102">重建索引工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="0a43a-102">Rebuild Index Task (Maintenance Plan)</span></span>
  <span data-ttu-id="0a43a-103">使用 [重建索引工作] 對話方塊，以新的填滿因數重新建立資料庫資料表上的索引。</span><span class="sxs-lookup"><span data-stu-id="0a43a-103">Use the **Rebuild Index Task** dialog to re-create the indexes on the tables in the database with a new fill factor.</span></span> <span data-ttu-id="0a43a-104">填滿因數會決定索引中每頁的空白數量，以配合未來擴充需要。</span><span class="sxs-lookup"><span data-stu-id="0a43a-104">The fill factor determines the amount of empty space on each page in the index, to accommodate future expansion.</span></span> <span data-ttu-id="0a43a-105">將資料加入資料表時，因為沒有維護填滿因數，所以可用空間都會填滿。</span><span class="sxs-lookup"><span data-stu-id="0a43a-105">As data is added to the table, the free space fills because the fill factor is not maintained.</span></span> <span data-ttu-id="0a43a-106">重新組織資料與索引頁面可以重新建立可用空間。</span><span class="sxs-lookup"><span data-stu-id="0a43a-106">Reorganizing data and index pages can re-establish the free space.</span></span>  
  
 <span data-ttu-id="0a43a-107">[重建索引工作] 會使用 ALTER INDEX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a43a-107">The **Rebuild Index Task** uses the ALTER INDEX statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0a43a-108">選項。</span><span class="sxs-lookup"><span data-stu-id="0a43a-108">Options</span></span>  
 <span data-ttu-id="0a43a-109">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="0a43a-109">**Connection**</span></span>  
 <span data-ttu-id="0a43a-110">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="0a43a-110">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="0a43a-111">**新增**</span><span class="sxs-lookup"><span data-stu-id="0a43a-111">**New**</span></span>  
 <span data-ttu-id="0a43a-112">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="0a43a-112">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="0a43a-113">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0a43a-113">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="0a43a-114">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="0a43a-114">**Databases**</span></span>  
 <span data-ttu-id="0a43a-115">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a43a-115">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="0a43a-116">**所有資料庫**</span><span class="sxs-lookup"><span data-stu-id="0a43a-116">**All databases**</span></span>  
  
     <span data-ttu-id="0a43a-117">產生維護計畫，針對所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫執行維護工作，但 tempdb 除外。</span><span class="sxs-lookup"><span data-stu-id="0a43a-117">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="0a43a-118">**所有系統資料庫**</span><span class="sxs-lookup"><span data-stu-id="0a43a-118">**All system databases**</span></span>  
  
     <span data-ttu-id="0a43a-119">產生維護計畫，針對每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行維護工作，但 tempdb 除外。</span><span class="sxs-lookup"><span data-stu-id="0a43a-119">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="0a43a-120">不會針對使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="0a43a-120">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="0a43a-121">**所有使用者資料庫**</span><span class="sxs-lookup"><span data-stu-id="0a43a-121">**All user databases**</span></span>  
  
     <span data-ttu-id="0a43a-122">產生維護計畫，針對所有使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="0a43a-122">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="0a43a-123">不會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行任何維護工作。</span><span class="sxs-lookup"><span data-stu-id="0a43a-123">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="0a43a-124">**這些特定的資料庫**</span><span class="sxs-lookup"><span data-stu-id="0a43a-124">**These specific databases**</span></span>  
  
     <span data-ttu-id="0a43a-125">產生維護計畫，只針對選取的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="0a43a-125">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="0a43a-126">如果選擇此選項，則必須在清單中至少選取一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a43a-126">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a43a-127">維護計畫只針對相容性層級設為 80 (含) 以上的資料庫來執行。</span><span class="sxs-lookup"><span data-stu-id="0a43a-127">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="0a43a-128">不會顯示相容性層級設為 70 或更低的資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a43a-128">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="0a43a-129">**Object**</span><span class="sxs-lookup"><span data-stu-id="0a43a-129">**Object**</span></span>  
 <span data-ttu-id="0a43a-130">限制 [選取範圍] 格線僅顯示資料表、檢視或兩者。</span><span class="sxs-lookup"><span data-stu-id="0a43a-130">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="0a43a-131">**選取範圍**</span><span class="sxs-lookup"><span data-stu-id="0a43a-131">**Selection**</span></span>  
 <span data-ttu-id="0a43a-132">指定受此工作影響的資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="0a43a-132">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="0a43a-133">[物件] 方塊中的 **[資料表和檢視]** 為選取狀態時無法使用。</span><span class="sxs-lookup"><span data-stu-id="0a43a-133">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
 <span data-ttu-id="0a43a-134">**使用預設的可用空間量重新組織頁面**</span><span class="sxs-lookup"><span data-stu-id="0a43a-134">**Reorganize pages with the default amount of free space**</span></span>  
 <span data-ttu-id="0a43a-135">將資料庫中的資料表索引卸除，並以建立索引時指定的填滿因數重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="0a43a-135">Drop the indexes on the tables in the database and re-create them with the fill factor that was specified when the indexes were created.</span></span>  
  
 <span data-ttu-id="0a43a-136">**將每頁可用空間百分比變更為**</span><span class="sxs-lookup"><span data-stu-id="0a43a-136">**Change free space per page percentage to**</span></span>  
 <span data-ttu-id="0a43a-137">將資料庫中的資料表索引卸除，並以新的、自動計算的填滿因數重新建立它們，以在索引頁面上保留指定的可用空間。</span><span class="sxs-lookup"><span data-stu-id="0a43a-137">Drop the indexes on the tables in the database and re-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages.</span></span> <span data-ttu-id="0a43a-138">百分比愈高，在索引頁面上保留的可用空間就愈多，而索引也愈大。</span><span class="sxs-lookup"><span data-stu-id="0a43a-138">The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows.</span></span> <span data-ttu-id="0a43a-139">有效的數值範圍為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="0a43a-139">Valid values are from 0 through 100.</span></span>  
  
 <span data-ttu-id="0a43a-140">**在 tempdb 中排序結果**</span><span class="sxs-lookup"><span data-stu-id="0a43a-140">**Sort results in tempdb**</span></span>  
 <span data-ttu-id="0a43a-141">使用 `SORT_IN_TEMPDB` 選項，決定在索引建立期間產生的中繼排序結果要暫時儲存的位置。</span><span class="sxs-lookup"><span data-stu-id="0a43a-141">Use the `SORT_IN_TEMPDB`option, which determines where the intermediate sort results, generated during index creation, are temporarily stored.</span></span> <span data-ttu-id="0a43a-142">如果排序作業不是必要項目，或是可以在記憶體中執行排序，則會忽略 `SORT_IN_TEMPDB`選項。</span><span class="sxs-lookup"><span data-stu-id="0a43a-142">If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB`option is ignored.</span></span>  
  
 <span data-ttu-id="0a43a-143">**重新索引時，索引保持在線上**</span><span class="sxs-lookup"><span data-stu-id="0a43a-143">**Keep index online while reindexing**</span></span>  
 <span data-ttu-id="0a43a-144">使用 `ONLINE` 選項，而這個選項可讓使用者在索引作業期間存取基礎資料表或叢集索引資料以及任何相關的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="0a43a-144">Use the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a43a-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有版本都無法使用線上索引作業。</span><span class="sxs-lookup"><span data-stu-id="0a43a-145">Online index operations are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0a43a-146">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="0a43a-146">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="0a43a-147">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="0a43a-147">**View T-SQL**</span></span>  
 <span data-ttu-id="0a43a-148">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a43a-148">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a43a-149">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="0a43a-149">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="0a43a-150">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="0a43a-150">New Connection Dialog Box</span></span>  
 <span data-ttu-id="0a43a-151">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="0a43a-151">**Connection name**</span></span>  
 <span data-ttu-id="0a43a-152">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a43a-152">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="0a43a-153">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="0a43a-153">**Select or enter a server name**</span></span>  
 <span data-ttu-id="0a43a-154">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a43a-154">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="0a43a-155">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="0a43a-155">**Refresh**</span></span>  
 <span data-ttu-id="0a43a-156">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="0a43a-156">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="0a43a-157">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="0a43a-157">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="0a43a-158">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="0a43a-158">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="0a43a-159">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="0a43a-159">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="0a43a-160">使用 Windows 驗證連接 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a43a-160">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="0a43a-161">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="0a43a-161">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="0a43a-162">使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 驗證，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a43a-162">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="0a43a-163">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0a43a-163">This option is not available.</span></span>  
  
 <span data-ttu-id="0a43a-164">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0a43a-164">**User name**</span></span>  
 <span data-ttu-id="0a43a-165">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="0a43a-165">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="0a43a-166">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0a43a-166">This option is not available.</span></span>  
  
 <span data-ttu-id="0a43a-167">**密碼**</span><span class="sxs-lookup"><span data-stu-id="0a43a-167">**Password**</span></span>  
 <span data-ttu-id="0a43a-168">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="0a43a-168">Provide a password to use when authenticating.</span></span> <span data-ttu-id="0a43a-169">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0a43a-169">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a43a-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a43a-170">See Also</span></span>  
 <span data-ttu-id="0a43a-171">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a43a-171">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="0a43a-172">[DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a43a-172">[DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) </span></span>  
 <span data-ttu-id="0a43a-173">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a43a-173">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="0a43a-174">[索引的 SORT_IN_TEMPDB 選項](../indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="0a43a-174">[SORT_IN_TEMPDB Option For Indexes](../indexes/indexes.md) </span></span>  
 <span data-ttu-id="0a43a-175">[線上索引作業的指導方針](../indexes/guidelines-for-online-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="0a43a-175">[Guidelines for Online Index Operations](../indexes/guidelines-for-online-index-operations.md) </span></span>  
 <span data-ttu-id="0a43a-176">[線上索引作業如何運作](../indexes/how-online-index-operations-work.md) </span><span class="sxs-lookup"><span data-stu-id="0a43a-176">[How Online Index Operations Work](../indexes/how-online-index-operations-work.md) </span></span>  
 [<span data-ttu-id="0a43a-177">線上執行索引作業</span><span class="sxs-lookup"><span data-stu-id="0a43a-177">Perform Index Operations Online</span></span>](../indexes/perform-index-operations-online.md)  
  
  
