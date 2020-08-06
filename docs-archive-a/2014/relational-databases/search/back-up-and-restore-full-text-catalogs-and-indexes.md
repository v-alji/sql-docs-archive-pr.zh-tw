---
title: 備份並還原全文檢索目錄與索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], backing up
- full-text search [SQL Server], back up and restore
- recovery [full-text search]
- backups [SQL Server], full-text indexes
- full-text indexes [SQL Server], restoring
- restore operations [full-text search]
ms.assetid: 6a4080d9-e43f-4b7b-a1da-bebf654c1194
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c0df49c03325da375427c6566799f374fcc9dd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599447"
---
# <a name="back-up-and-restore-full-text-catalogs-and-indexes"></a><span data-ttu-id="d6c2f-102">備份並還原全文檢索目錄與索引。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-102">Back Up and Restore Full-Text Catalogs and Indexes</span></span>
  <span data-ttu-id="d6c2f-103">本主題說明如何備份和還原在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中建立的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-103">This topic explains how to back up and restore full-text indexes created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d6c2f-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，全文檢索目錄是邏輯概念，而且不會位於檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the full-text catalog is a logical concept and does not reside in a filegroup.</span></span> <span data-ttu-id="d6c2f-105">因此，若要備份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的全文檢索目錄，您必須識別包含屬於此目錄之全文檢索索引的每個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-105">Therefore, to back up a full-text catalog in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must identify every filegroup that contains a full-text index that belongs to the catalog.</span></span> <span data-ttu-id="d6c2f-106">然後，您必須逐一備份這些檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-106">Then you must back up those filegroups, one by one.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d6c2f-107">您可以在升級 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 資料庫時，匯入全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-107">It is possible to import full-text catalogs when upgrading a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database.</span></span> <span data-ttu-id="d6c2f-108">每個匯入的全文檢索目錄都是其檔案群組中的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-108">Each imported full-text catalog is a database file in its own filegroup.</span></span> <span data-ttu-id="d6c2f-109">若要備份匯入的目錄，只要備份其檔案群組即可。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-109">To back up an imported catalog, simply back up its filegroup.</span></span> <span data-ttu-id="d6c2f-110">如需詳細資訊，請參閱《 [線上叢書》中的](https://go.microsoft.com/fwlink/?LinkID=121052)備份和還原 SQL Server 2008 全文檢索目錄 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-110">For more information, see [Backing Up and Restoring Full-Text Catalogs](https://go.microsoft.com/fwlink/?LinkID=121052), in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Books Online.</span></span>  
  
##  <a name="backing-up-the-full-text-indexes-of-a-full-text-catalog"></a><a name="backingup"></a> <span data-ttu-id="d6c2f-111">備份全文檢索目錄的全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="d6c2f-111">Backing Up the Full-Text Indexes of a Full-Text Catalog</span></span>  
  
###  <a name="finding-the-full-text-indexes-of-a-full-text-catalog"></a><a name="Find_FTIs_of_a_Catalog"></a> <span data-ttu-id="d6c2f-112">尋找全文檢索目錄的全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="d6c2f-112">Finding the Full-Text Indexes of a Full-Text Catalog</span></span>  
 <span data-ttu-id="d6c2f-113">您可以使用下列 [SELECT](/sql/t-sql/queries/select-transact-sql) 陳述式 (從 [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) 和 [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) 目錄檢視中選取資料行) 來擷取全文檢索索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-113">You can retrieve the properties of the full-text indexes by using the following [SELECT](/sql/t-sql/queries/select-transact-sql) statement, which selects columns from the [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) and [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) catalog views.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @TableID int;  
SET @TableID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product'));  
SELECT object_name(@TableID), i.is_enabled, i.change_tracking_state,   
   i.has_crawl_completed, i.crawl_type, c.name as fulltext_catalog_name   
   FROM sys.fulltext_indexes i, sys.fulltext_catalogs c   
   WHERE i.fulltext_catalog_id = c.fulltext_catalog_id;  
GO  
```  
  

  
###  <a name="finding-the-filegroup-or-file-that-contains-a-full-text-index"></a><a name="Find_FG_of_FTI"></a> <span data-ttu-id="d6c2f-114">尋找包含全文檢索索引的檔案群組或檔案</span><span class="sxs-lookup"><span data-stu-id="d6c2f-114">Finding the Filegroup or File That Contains a Full-Text Index</span></span>  
 <span data-ttu-id="d6c2f-115">建立全文檢索索引時，它會放置於下列其中一個位置：</span><span class="sxs-lookup"><span data-stu-id="d6c2f-115">When a full-text index is created, it is placed in one of the following locations:</span></span>  
  
-   <span data-ttu-id="d6c2f-116">使用者指定的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-116">A user-specified filegroup.</span></span>  
  
-   <span data-ttu-id="d6c2f-117">與基底資料表或檢視表相同的檔案群組 (若為非資料分割資料表)。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-117">The same filegroup as base table or view, for a nonpartitioned table.</span></span>  
  
-   <span data-ttu-id="d6c2f-118">主要檔案群組 (若為資料分割資料表)。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-118">The primary filegroup, for a partitioned table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6c2f-119">如需建立全文檢索索引的相關資訊，請參閱[建立及管理全文檢索索引](create-and-manage-full-text-indexes.md)和 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-119">For information about creating a full-text index, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) and [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="d6c2f-120">若要針對某個資料表或檢視表尋找全文檢索索引的檔案群組，請使用下列查詢，其中 *object_name* 是資料表或檢視表的名稱：</span><span class="sxs-lookup"><span data-stu-id="d6c2f-120">To find the filegroup of full-text index on a table or view, use the following query, where *object_name* is the name of the table or view:</span></span>  
  
```  
SELECT name FROM sys.filegroups f, sys.fulltext_indexes i   
   WHERE f.data_space_id = i.data_space_id   
      and i.object_id = object_id('object_name');  
GO  
  
```  
  

  
###  <a name="backing-up-the-filegroups-that-contain-full-text-indexes"></a><a name="Back_up_FTIs_of_FTC"></a> <span data-ttu-id="d6c2f-121">備份包含全文檢索索引的檔案群組</span><span class="sxs-lookup"><span data-stu-id="d6c2f-121">Backing Up the Filegroups That Contain Full-Text Indexes</span></span>  
 <span data-ttu-id="d6c2f-122">尋找包含全文檢索目錄之索引的檔案群組之後，您必須備份每個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-122">After you find the filegroups that contain the indexes of a full-text catalog, you need back up each of the filegroups.</span></span> <span data-ttu-id="d6c2f-123">在備份程序期間，您可能無法卸除或加入全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-123">During the backup process, full-text catalogs may not be dropped or added.</span></span>  
  
 <span data-ttu-id="d6c2f-124">檔案群組的第一個備份必須是完整檔案備份。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-124">The first backup of a filegroup must be a full file backup.</span></span> <span data-ttu-id="d6c2f-125">建立檔案群組的完整檔案備份之後，您就可以透過建立一系列的一個或多個差異檔案備份 (以完整檔案備份為基礎)，僅備份檔案群組中的變更。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-125">After you have created a full file backup for a filegroup, you could back up only the changes in a filegroup by creating a series of one or more differential file backups that are based on the full file backup.</span></span>  
  
 <span data-ttu-id="d6c2f-126">**備份檔案與檔案群組**</span><span class="sxs-lookup"><span data-stu-id="d6c2f-126">**To back up files and filegroups**</span></span>  
  
-   [<span data-ttu-id="d6c2f-127">備份檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d6c2f-127">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="d6c2f-128">BACKUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6c2f-128">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  

  
##  <a name="restoring-a-full-text-index"></a><a name="Restore_FTI"></a> <span data-ttu-id="d6c2f-129">還原全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="d6c2f-129">Restoring a Full-Text Index</span></span>  
 <span data-ttu-id="d6c2f-130">還原備份的檔案群組就會還原全文檢索索引檔案，以及檔案群組中的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-130">Restoring a backed-up filegroup restores the full-text index files, as well as the other files in the filegroup.</span></span> <span data-ttu-id="d6c2f-131">根據預設，檔案群組會還原至備份檔案群組所在的磁碟位置。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-131">By default, the filegroup is restored to the disk location on which the filegroup was backed up.</span></span>  
  
 <span data-ttu-id="d6c2f-132">如果建立備份時，全文檢索索引資料表已在線上，而且正在進行母體擴展，就會在還原之後繼續進行母體擴展。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-132">If a full-text indexed table was online and a population was running when the backup was created, the population is resumed after the restore.</span></span>  
  
 <span data-ttu-id="d6c2f-133">**還原檔案群組**</span><span class="sxs-lookup"><span data-stu-id="d6c2f-133">**To restore a filegroup**</span></span>  
  
-   [<span data-ttu-id="d6c2f-134">還原檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d6c2f-134">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="d6c2f-135">以覆蓋現有檔案的方式還原檔案與檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d6c2f-135">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="d6c2f-136">將檔案還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d6c2f-136">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="d6c2f-137">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6c2f-137">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  

  
## <a name="see-also"></a><span data-ttu-id="d6c2f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6c2f-138">See Also</span></span>  
 <span data-ttu-id="d6c2f-139">[管理及監視伺服器執行個體的全文檢索搜尋](manage-and-monitor-full-text-search-for-a-server-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d6c2f-139">[Manage and Monitor Full-Text Search for a Server Instance](manage-and-monitor-full-text-search-for-a-server-instance.md) </span></span>  
 [<span data-ttu-id="d6c2f-140">升級全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="d6c2f-140">Upgrade Full-Text Search</span></span>](upgrade-full-text-search.md)  
  
  
