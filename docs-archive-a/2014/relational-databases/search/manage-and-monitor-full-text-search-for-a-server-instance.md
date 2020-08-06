---
title: 管理及監視伺服器執行個體的全文檢索搜尋 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], about
- full-text search [SQL Server], server management
ms.assetid: 2733ed78-6d33-4bf9-94da-60c3141b87c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1ba4b2f081047f25fa775e0c8754caa4ce643e70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702602"
---
# <a name="manage-and-monitor-full-text-search-for-a-server-instance"></a><span data-ttu-id="b0249-102">管理及監視伺服器執行個體的全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="b0249-102">Manage and Monitor Full-Text Search for a Server Instance</span></span>
  <span data-ttu-id="b0249-103">伺服器執行個體的全文檢索管理包括：</span><span class="sxs-lookup"><span data-stu-id="b0249-103">Full-text administration for a server instance includes:</span></span>  
  
-   <span data-ttu-id="b0249-104">系統管理工作，例如管理 FDHOST 啟動器服務 (MSSQLFDLauncher)、重新啟動篩選背景程式主機處理序 (如果您變更了服務帳戶認證的話)、設定整個伺服器的全文檢索屬性，以及備份全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="b0249-104">System management tasks such as managing the FDHOST Launcher service (MSSQLFDLauncher), restarting filter daemon host process if you change the service account credentials, configuring server-wide full-text properties, and backing up full-text catalogs.</span></span> <span data-ttu-id="b0249-105">舉例來說，您可以在伺服器層級中指定預設的全文檢索語言，以與整個伺服器執行個體的預設語言進行區隔。</span><span class="sxs-lookup"><span data-stu-id="b0249-105">At the server level, for example, you can specify a default full-text language that differs from the default language of the server instance as a whole.</span></span>  
  
-   <span data-ttu-id="b0249-106">設定全文檢索語言元件 (斷詞工具和字幹分析器、同義字檔案，以及停用字詞和停用字詞表)。</span><span class="sxs-lookup"><span data-stu-id="b0249-106">Configuring full-text linguistic components (word breakers and stemmers, thesaurus file, and stopwords and stoplists).</span></span>  
  
-   <span data-ttu-id="b0249-107">設定全文檢索搜尋的使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0249-107">Configuring a user database for full-text search.</span></span> <span data-ttu-id="b0249-108">這項作業包括針對資料庫建立一個或多個全文檢索目錄，以及針對您想要執行全文檢索查詢的每個資料表或索引檢視表定義全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="b0249-108">This involves creating one or more full-text catalogs for the database and defining a full-text index on each table or indexed view on which you want to execute full-text queries.</span></span>  
  
##  <a name="viewing-or-changing-server-properties-for-full-text-search"></a><a name="props"></a> <span data-ttu-id="b0249-109">檢視或變更全文檢索搜尋的伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="b0249-109">Viewing or Changing Server Properties for Full-Text Search</span></span>  
 <span data-ttu-id="b0249-110">您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]執行個體的全文檢索屬性。</span><span class="sxs-lookup"><span data-stu-id="b0249-110">You can view the full-text properties of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-view-and-change-server-properties-for-full-text-search"></a><span data-ttu-id="b0249-111">檢視與變更全文檢索搜尋的伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="b0249-111">To view and change server properties for full-text search</span></span>  
  
1.  <span data-ttu-id="b0249-112">在物件總管中，以滑鼠右鍵按一下伺服器，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="b0249-112">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b0249-113">在 [伺服器屬性]  對話方塊中，按一下 [進階]  頁面檢視全文檢索搜尋的相關伺服器資訊。</span><span class="sxs-lookup"><span data-stu-id="b0249-113">In the **Server Properties** dialog box, click the **Advanced** page to view server information about full-text search.</span></span> <span data-ttu-id="b0249-114">全文檢索屬性如下所示：</span><span class="sxs-lookup"><span data-stu-id="b0249-114">The full-text properties are as follows:</span></span>  
  
    -   <span data-ttu-id="b0249-115">**預設全文檢索語言**</span><span class="sxs-lookup"><span data-stu-id="b0249-115">**Default Full-Text Language**</span></span>  
  
         <span data-ttu-id="b0249-116">指定全文檢索索引資料行的預設語言。</span><span class="sxs-lookup"><span data-stu-id="b0249-116">Specifies a default language for full-text indexed columns.</span></span> <span data-ttu-id="b0249-117">全文檢索索引資料的語言分析相依於資料所用的語言。</span><span class="sxs-lookup"><span data-stu-id="b0249-117">Linguistic analysis of full-text indexed data is dependent on the language of the data.</span></span> <span data-ttu-id="b0249-118">這個選項的預設值是伺服器使用的語言。</span><span class="sxs-lookup"><span data-stu-id="b0249-118">The default value of this option is the language of the server.</span></span> <span data-ttu-id="b0249-119">如需所顯示設定的對應語言，請參閱 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b0249-119">For the language that corresponds to the displayed setting, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span>  
  
    -   <span data-ttu-id="b0249-120">**全文檢索升級選項**</span><span class="sxs-lookup"><span data-stu-id="b0249-120">**Full-Text Upgrade Option**</span></span>  
  
         <span data-ttu-id="b0249-121">這個伺服器屬性會控制將資料庫從 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 升級到更新版本時，要如何移轉全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="b0249-121">This server property controls how full-text indexes are migrated when upgrading a database from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] to a later version.</span></span> <span data-ttu-id="b0249-122">這個屬性適用於以下方式的升級：附加資料庫、還原資料庫備份、還原檔案備份，或是使用複製資料庫精靈複製資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0249-122">This property applies to upgrading by attaching a database, restoring a database backup, restoring a file backup, or copying the database by using the Copy Database Wizard.</span></span>  
  
         <span data-ttu-id="b0249-123">替代方案如下所示：</span><span class="sxs-lookup"><span data-stu-id="b0249-123">The alternatives are as follows:</span></span>  
  
         <span data-ttu-id="b0249-124">**匯入**</span><span class="sxs-lookup"><span data-stu-id="b0249-124">**Import**</span></span>  
         <span data-ttu-id="b0249-125">匯入全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="b0249-125">Full-text catalogs are imported.</span></span> <span data-ttu-id="b0249-126">一般而言，匯入的速度明顯比重建的速度更快。</span><span class="sxs-lookup"><span data-stu-id="b0249-126">Typically, import is significantly faster than rebuild.</span></span> <span data-ttu-id="b0249-127">例如，只有使用一個 CPU 時，匯入的執行速度大約比重建的速度快 10 倍。</span><span class="sxs-lookup"><span data-stu-id="b0249-127">For example, when using only one CPU, import runs about 10 times faster than rebuild.</span></span> <span data-ttu-id="b0249-128">不過，匯入的全文檢索目錄並不會使用 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]中導入的新增強化斷詞工具，所以您最後可能會想要重建全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="b0249-128">However, an imported full-text catalog does not use the new and enhanced word breakers introduced in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], so you might want to rebuild your full-text catalogs eventually.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b0249-129">重建可以在多執行緒模式中執行，而且如果有 10 個以上的 CPU 可用，當您允許重建使用所有 CPU 時，重建的執行速度可能會比匯入的速度更快。</span><span class="sxs-lookup"><span data-stu-id="b0249-129">Rebuild can run in multi-threaded mode, and if more than 10 CPUs are available, rebuild might run faster than import if you allow rebuild to use all of the CPUs.</span></span>  
  
         <span data-ttu-id="b0249-130">如果無法使用全文檢索目錄，將會重建關聯的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="b0249-130">If a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="b0249-131">只有針對 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 資料庫才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="b0249-131">This option is available for only [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] databases.</span></span>  
  
         <span data-ttu-id="b0249-132">**重建**</span><span class="sxs-lookup"><span data-stu-id="b0249-132">**Rebuild**</span></span>  
         <span data-ttu-id="b0249-133">全文檢索目錄會使用新的增強斷詞工具重建。</span><span class="sxs-lookup"><span data-stu-id="b0249-133">Full-text catalogs are rebuilt using the new and enhanced word breakers.</span></span> <span data-ttu-id="b0249-134">重建索引可能要花一些時間，而且在升級之後可能需要相當多的 CPU 和記憶體。</span><span class="sxs-lookup"><span data-stu-id="b0249-134">Rebuilding indexes can take awhile, and a significant amount of CPU and memory might be required after the upgrade.</span></span>  
  
         <span data-ttu-id="b0249-135">**重設**</span><span class="sxs-lookup"><span data-stu-id="b0249-135">**Reset**</span></span>  
         <span data-ttu-id="b0249-136">重設全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="b0249-136">Full-text catalogs are reset.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="b0249-137">全文檢索目錄檔案會遭到移除，但是全文檢索目錄和全文檢索索引的中繼資料則會保留。</span><span class="sxs-lookup"><span data-stu-id="b0249-137">full-text catalog files are removed, but the metadata for full-text catalogs and full-text indexes is retained.</span></span> <span data-ttu-id="b0249-138">在升級之後，所有的全文檢索索引都會停用變更追蹤，而且不會自動啟動搜耙。</span><span class="sxs-lookup"><span data-stu-id="b0249-138">After being upgraded, all full-text indexes are disabled for change tracking and crawls are not started automatically.</span></span> <span data-ttu-id="b0249-139">當您在升級完成之後手動發出完整母體擴展之前，此目錄將會維持空白狀態。</span><span class="sxs-lookup"><span data-stu-id="b0249-139">The catalog will remain empty until you manually issue a full population, after the upgrade completes.</span></span>  
  
         <span data-ttu-id="b0249-140">如需選擇全文檢索升級選項的詳細資訊，請參閱[升級全文檢索搜尋](upgrade-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="b0249-140">For information about choosing a full-text upgrade option, see [Upgrade Full-Text Search](upgrade-full-text-search.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b0249-141">也可以使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)**upgrade_option** 動作來設定全文檢索升級選項。</span><span class="sxs-lookup"><span data-stu-id="b0249-141">The full-text upgrade option can also be set by using the [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)**upgrade_option** action.</span></span>  
  
##  <a name="viewing-additional-full-text-server-properties"></a><a name="metadata"></a> <span data-ttu-id="b0249-142">檢視其他全文檢索伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="b0249-142">Viewing Additional Full-Text Server Properties</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="b0249-143">函數可用來取得全文檢索搜尋之各種伺服器層級屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b0249-143">functions can be used to obtain the value of various server-level properties of full-text search.</span></span> <span data-ttu-id="b0249-144">這項資訊可用於管理和疑難排解全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="b0249-144">This information is useful for administrating and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="b0249-145">下表列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 伺服器執行個體的全文檢索屬性及其相關的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 函數。</span><span class="sxs-lookup"><span data-stu-id="b0249-145">The following table lists full-text properties of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server instance and their related [!INCLUDE[tsql](../../../includes/tsql-md.md)] functions.</span></span>  
  
|<span data-ttu-id="b0249-146">屬性</span><span class="sxs-lookup"><span data-stu-id="b0249-146">Property</span></span>|<span data-ttu-id="b0249-147">描述</span><span class="sxs-lookup"><span data-stu-id="b0249-147">Description</span></span>|<span data-ttu-id="b0249-148">函式</span><span class="sxs-lookup"><span data-stu-id="b0249-148">Function</span></span>|  
|--------------|-----------------|--------------|  
|`IsFullTextInstalled`|<span data-ttu-id="b0249-149">全文檢索元件是否會與目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體一起安裝。</span><span class="sxs-lookup"><span data-stu-id="b0249-149">Whether the full-text component is installed with the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="b0249-150">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="b0249-150">FULLTEXTSERVICEPROPERTY</span></span>](/sql/t-sql/functions/fulltextserviceproperty-transact-sql)<br /><br /> [<span data-ttu-id="b0249-151">SERVERPROPERTY</span><span class="sxs-lookup"><span data-stu-id="b0249-151">SERVERPROPERTY</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)|  
|`LoadOSResources`|<span data-ttu-id="b0249-152">作業系統斷詞工具和篩選是否已註冊並搭配這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體使用。</span><span class="sxs-lookup"><span data-stu-id="b0249-152">Whether operating system word breakers and filters are registered and used with this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="b0249-153">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="b0249-153">FULLTEXTSERVICEPROPERTY</span></span>|  
|`VerifySignature`|<span data-ttu-id="b0249-154">指定全文檢索引擎是否只載入已簽署的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="b0249-154">Specifies whether only signed binaries are loaded by the Full-Text Engine.</span></span>|<span data-ttu-id="b0249-155">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="b0249-155">FULLTEXTSERVICEPROPERTY</span></span>|  
  
##  <a name="monitoring-full-text-search-activity"></a><a name="monitor"></a> <span data-ttu-id="b0249-156">監視全文檢索搜尋活動</span><span class="sxs-lookup"><span data-stu-id="b0249-156">Monitoring Full-Text Search Activity</span></span>  
 <span data-ttu-id="b0249-157">在伺服器執行個體上監視全文檢索搜尋活動時，許多動態管理檢視與函數相當有用。</span><span class="sxs-lookup"><span data-stu-id="b0249-157">Several dynamic management views and functions are useful monitoring full-text search activity on a server instance.</span></span>  
  
 <span data-ttu-id="b0249-158">**若要檢視有關包含進行中母體擴展活動之全文檢索目錄的資訊**</span><span class="sxs-lookup"><span data-stu-id="b0249-158">**To view information about the full-text catalogs with in-progress population activity**</span></span>  
  
-   [<span data-ttu-id="b0249-159">sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b0249-159">sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-active-catalogs-transact-sql)  
  
 <span data-ttu-id="b0249-160">**若要檢視篩選背景程式主機處理序的目前活動**</span><span class="sxs-lookup"><span data-stu-id="b0249-160">**To view current activity of a filter daemon host process**</span></span>  
  
-   [<span data-ttu-id="b0249-161">sys.dm_fts_fdhosts &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b0249-161">sys.dm_fts_fdhosts &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-fdhosts-transact-sql)  
  
 <span data-ttu-id="b0249-162">**若要檢視有關進行中索引母體擴展的資訊**</span><span class="sxs-lookup"><span data-stu-id="b0249-162">**To view information about in-progress index populations**</span></span>  
  
-   [<span data-ttu-id="b0249-163">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b0249-163">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)  
  
 <span data-ttu-id="b0249-164">**若要檢視在記憶體集區中當做搜耙或搜耙範圍一部分使用的記憶體緩衝區**</span><span class="sxs-lookup"><span data-stu-id="b0249-164">**To view memory buffers in a memory pool that are used as part of a crawl or crawl range.**</span></span>  
  
-   [<span data-ttu-id="b0249-165">sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b0249-165">sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)  
  
 <span data-ttu-id="b0249-166">**檢視可供全文檢索搜耙或全文檢索搜耙範圍之全文檢索收集程式元件使用的共用記憶體集區**</span><span class="sxs-lookup"><span data-stu-id="b0249-166">**To view the shared memory pools available to the full-text gatherer component for a full-text crawl or a full-text crawl range**</span></span>  
  
-   [<span data-ttu-id="b0249-167">sys.dm_fts_memory_pools &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b0249-167">sys.dm_fts_memory_pools &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)  
  
 <span data-ttu-id="b0249-168">**檢視有關每個全文檢索索引批次的資訊**</span><span class="sxs-lookup"><span data-stu-id="b0249-168">**To view information about each full-text indexing batch**</span></span>  
  
-   [<span data-ttu-id="b0249-169">sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b0249-169">sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-outstanding-batches-transact-sql)  
  
 <span data-ttu-id="b0249-170">**檢視有關與進行中母體擴展相關之特定範圍的資訊**</span><span class="sxs-lookup"><span data-stu-id="b0249-170">**To view information about the specific ranges related to an in-progress population**</span></span>  
  
-   [<span data-ttu-id="b0249-171">sys.dm_fts_population_ranges &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b0249-171">sys.dm_fts_population_ranges &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-population-ranges-transact-sql)  
  
  
