---
title: 資料庫鏡像和全文檢索目錄 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- full-text catalogs [SQL Server], database mirroring
- catalogs [SQL Server], database mirroring
ms.assetid: e34072ae-fe8a-462d-bb03-02fa0987f793
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 39929f4bed6edbd1e8ec5c1b72dbe8f7aefeec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593573"
---
# <a name="database-mirroring-and-full-text-catalogs-sql-server"></a><span data-ttu-id="9aa68-102">資料庫鏡像和全文檢索目錄 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9aa68-102">Database Mirroring and Full-Text Catalogs (SQL Server)</span></span>
  <span data-ttu-id="9aa68-103">若要建立具有全文檢索目錄之資料庫的鏡像，請如往常使用備份來建立主體資料庫的完整資料庫備份，然後還原備份，以將該資料庫複製到鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="9aa68-103">To mirror a database that has a full-text catalog, use backup as usual to create a full database backup of the principal database, and then restore the backup to copy the database to the mirror server.</span></span> <span data-ttu-id="9aa68-104">如需詳細資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa68-104">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
## <a name="full-text-catalog-and-indexes-before-failover"></a><span data-ttu-id="9aa68-105">容錯移轉之前的全文檢索目錄和索引</span><span class="sxs-lookup"><span data-stu-id="9aa68-105">Full-Text Catalog and Indexes Before Failover</span></span>  
 <span data-ttu-id="9aa68-106">在新建立的鏡像資料庫中，全文檢索目錄仍然和備份資料庫當時的目錄相同。</span><span class="sxs-lookup"><span data-stu-id="9aa68-106">In a newly created mirror database, the full-text catalog is the same as when the database was backed up.</span></span> <span data-ttu-id="9aa68-107">資料庫鏡像啟動之後，DDL 陳述式 (CREATE FULLTEXT CATALOG、ALTER FULLTEXT CATALOG、DROP FULLTEXT CATALOG) 所做的任何目錄層級變更都會記錄下來，並且傳送到鏡像伺服器，以便在鏡像資料庫上重新執行。</span><span class="sxs-lookup"><span data-stu-id="9aa68-107">After database mirroring starts, any catalog-level changes that were made by DDL statements (CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG) are logged and sent to the mirror server to be replayed on the mirror database.</span></span> <span data-ttu-id="9aa68-108">不過，索引層級變更不會在鏡像資料庫上重現，因為並未將它記錄到主體伺服器上。</span><span class="sxs-lookup"><span data-stu-id="9aa68-108">However, index-level changes are not reproduced on the mirror database because it is not logged on to the principal server.</span></span> <span data-ttu-id="9aa68-109">因此，當全文檢索目錄的內容在主體資料庫上變更時，並不會在鏡像資料庫上同步處理全文檢索目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="9aa68-109">Therefore, as the contents of the full-text catalog change on the principal database, the contents of the full-text catalog on the mirror database are unsynchronized.</span></span>  
  
## <a name="full-text-indexes-after-failover"></a><span data-ttu-id="9aa68-110">容錯移轉之後的全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="9aa68-110">Full-Text Indexes After Failover</span></span>  
 <span data-ttu-id="9aa68-111">容錯移轉之後，在新的主體伺服器上為全文檢索索引執行完整搜耙，對下列情況可能有其必要，而且很有幫助：</span><span class="sxs-lookup"><span data-stu-id="9aa68-111">After a failover, a full crawl of a full-text index on the new principal server might be required or useful in the following situations:</span></span>  
  
-   <span data-ttu-id="9aa68-112">如果關閉全文檢索索引上的變更追蹤功能，您必須使用下列陳述式，在該索引上啟動完整搜耙：</span><span class="sxs-lookup"><span data-stu-id="9aa68-112">If change-tracking is turned OFF on a full text index, you must start a full crawl on that index by using the following statement:</span></span>  
  
     <span data-ttu-id="9aa68-113">ALTER FULLTEXT INDEX ON *table_name* START FULL POPULATION</span><span class="sxs-lookup"><span data-stu-id="9aa68-113">ALTER FULLTEXT INDEX ON *table_name* START FULL POPULATION</span></span>  
  
-   <span data-ttu-id="9aa68-114">如果全文檢索索引設定為自動變更追蹤，全文檢索索引便會自動同步處理。</span><span class="sxs-lookup"><span data-stu-id="9aa68-114">If a full-text index is configured for automatic change tracking, the full-text index is automatically synchronized.</span></span> <span data-ttu-id="9aa68-115">不過，同步處理會稍微減緩全文檢索效能。</span><span class="sxs-lookup"><span data-stu-id="9aa68-115">However, synchronization slows full-text performance somewhat.</span></span> <span data-ttu-id="9aa68-116">如果效能太慢，則可以將變更追蹤功能設為關閉後再重設為自動，藉以引起完整搜耙：</span><span class="sxs-lookup"><span data-stu-id="9aa68-116">If performance is too slow, you can cause a full crawl by setting change tracking off and then resetting it to automatic:</span></span>  
  
    -   <span data-ttu-id="9aa68-117">若要將變更追蹤設定為關閉：</span><span class="sxs-lookup"><span data-stu-id="9aa68-117">To set change tracking off:</span></span>  
  
         <span data-ttu-id="9aa68-118">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="9aa68-118">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING OFF</span></span>  
  
    -   <span data-ttu-id="9aa68-119">若要將變更追蹤設定為自動：</span><span class="sxs-lookup"><span data-stu-id="9aa68-119">To set on automatic change tracking to automatic:</span></span>  
  
         <span data-ttu-id="9aa68-120">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="9aa68-120">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING AUTO</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9aa68-121">若要查看自動變更追蹤是否已開啟，您可以使用 [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) 函數來查詢資料表的 **TableFullTextBackgroundUpdateIndexOn** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9aa68-121">To see whether auto change tracking is on, you can use the [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) function to query the **TableFullTextBackgroundUpdateIndexOn** property of the table.</span></span>  
  
 <span data-ttu-id="9aa68-122">如需詳細資訊，請參閱 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9aa68-122">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9aa68-123">在容錯移轉後啟動搜耙，以及在還原作業後啟動搜耙，這兩者的運作方式完全相同。</span><span class="sxs-lookup"><span data-stu-id="9aa68-123">Starting a crawl after failover works the same as starting a crawl after a restore.</span></span>  
  
## <a name="after-forcing-service"></a><span data-ttu-id="9aa68-124">在強制服務之後</span><span class="sxs-lookup"><span data-stu-id="9aa68-124">After Forcing Service</span></span>  
 <span data-ttu-id="9aa68-125">在將服務強制移轉到鏡像伺服器 (可能發生資料遺失) 之後，會啟動完整搜耙。</span><span class="sxs-lookup"><span data-stu-id="9aa68-125">After service is forced to the mirror server (with possible data loss), start a full crawl.</span></span> <span data-ttu-id="9aa68-126">啟動完整搜耙所使用的方法將視全文檢索索引是否啟用變更追蹤而定。</span><span class="sxs-lookup"><span data-stu-id="9aa68-126">The method to use for starting a full crawl depends on whether the full-text index is change tracked.</span></span> <span data-ttu-id="9aa68-127">如需詳細資訊，請參閱本主題前面的「容錯移轉之後的全文檢索索引」。</span><span class="sxs-lookup"><span data-stu-id="9aa68-127">For more information, see "Full-Text Indexes After Failover," earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa68-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9aa68-128">See Also</span></span>  
 <span data-ttu-id="9aa68-129">[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9aa68-129">[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="9aa68-130">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9aa68-130">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="9aa68-131">[DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9aa68-131">[DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="9aa68-132">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9aa68-132">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="9aa68-133">備份並還原全文檢索目錄與索引</span><span class="sxs-lookup"><span data-stu-id="9aa68-133">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](../../relational-databases/indexes/indexes.md)  
  
  
