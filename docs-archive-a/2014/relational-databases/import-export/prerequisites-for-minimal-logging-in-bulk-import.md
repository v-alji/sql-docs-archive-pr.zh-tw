---
title: 大量匯入採用最低限度記錄的必要條件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- minimal logging [SQL Server]
- logged bulk copy [SQL Server]
- logs [SQL Server], minimal logging
- minimally logged operations [SQL Server]
- bulk importing [SQL Server], minimal logging
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4711e25dcfcc99e14894e47166638673c61a6831
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708405"
---
# <a name="prerequisites-for-minimal-logging-in-bulk-import"></a><span data-ttu-id="8a247-102">大量匯入中最低限度記錄的先決條件</span><span class="sxs-lookup"><span data-stu-id="8a247-102">Prerequisites for Minimal Logging in Bulk Import</span></span>
  <span data-ttu-id="8a247-103">如果是完整復原模式之下的資料庫，則大量匯入執行的所有資料列插入作業，都會完整記錄在交易記錄中。</span><span class="sxs-lookup"><span data-stu-id="8a247-103">For a database under the full recovery model, all row-insert operations that are performed by bulk import are fully logged in the transaction log.</span></span> <span data-ttu-id="8a247-104">若使用完整復原模式，大型的資料匯入作業可能會使交易記錄檔很快就填滿。</span><span class="sxs-lookup"><span data-stu-id="8a247-104">Large data imports can cause the transaction log to fill rapidly if the full recovery model is used.</span></span> <span data-ttu-id="8a247-105">相較之下，在簡單復原模式或大量記錄復原模式之下，大量匯入作業的最少記錄會減少大量匯入作業填滿記錄空間的機會。</span><span class="sxs-lookup"><span data-stu-id="8a247-105">In contrast, under the simple recovery model or bulk-logged recovery model, minimal logging of bulk-import operations reduces the possibility that a bulk-import operation will fill the log space.</span></span> <span data-ttu-id="8a247-106">最低限度記錄也比完整記錄更有效率。</span><span class="sxs-lookup"><span data-stu-id="8a247-106">Minimal logging is also more efficient than full logging.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a247-107">大量記錄復原模式的設計目的，是要在大量匯入作業期間暫時取代完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="8a247-107">The bulk-logged recovery model is designed to temporarily replace the full recovery model during large bulk operations.</span></span>  
  
## <a name="table-requirements-for-minimally-logging-bulk-import-operations"></a><span data-ttu-id="8a247-108">最低限度記錄大量匯入作業的資料表需求</span><span class="sxs-lookup"><span data-stu-id="8a247-108">Table Requirements for Minimally Logging Bulk-Import Operations</span></span>  
 <span data-ttu-id="8a247-109">使用最低限度記錄時，目標資料表必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="8a247-109">Minimal logging requires that the target table meets the following conditions:</span></span>  
  
-   <span data-ttu-id="8a247-110">資料表未被複寫。</span><span class="sxs-lookup"><span data-stu-id="8a247-110">The table is not being replicated.</span></span>  
  
-   <span data-ttu-id="8a247-111">已指定資料表鎖定 (使用 TABLOCK)。</span><span class="sxs-lookup"><span data-stu-id="8a247-111">Table locking is specified (using TABLOCK).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8a247-112">雖然在最低限度記錄的大量匯入作業期間，交易記錄檔中不會記錄資料插入，但每當有新的範圍配置到資料表時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 仍會記錄範圍配置。</span><span class="sxs-lookup"><span data-stu-id="8a247-112">Although data insertions are not logged in the transaction log during a minimally logged bulk-import operation, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] still logs extent allocations each time a new extent is allocated to the table.</span></span>  
  
-   <span data-ttu-id="8a247-113">資料表不是記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="8a247-113">Table is not a memory-optimized table.</span></span>  
  
 <span data-ttu-id="8a247-114">資料表是否能產生最低限度記錄，還需視資料表是否已建立索引而定，若已建立索引，則需考量資料表是否為空白：</span><span class="sxs-lookup"><span data-stu-id="8a247-114">Whether minimal logging can occur for a table also depends on whether the table is indexed and, if so, whether the table is empty:</span></span>  
  
-   <span data-ttu-id="8a247-115">若資料表沒有索引，則資料頁會使用最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="8a247-115">If the table has no indexes, data pages are minimally logged.</span></span>  
  
-   <span data-ttu-id="8a247-116">若資料表沒有叢集索引，但有一或多個非叢集索引，則資料頁會一律使用最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="8a247-116">If the table has no clustered index but has one or more nonclustered indexes, data pages are always minimally logged.</span></span> <span data-ttu-id="8a247-117">但索引頁的記錄方式，則取決於資料表是否空白：</span><span class="sxs-lookup"><span data-stu-id="8a247-117">How index pages are logged, however, depends on whether the table is empty:</span></span>  
  
    -   <span data-ttu-id="8a247-118">若資料表空白，則索引頁會使用最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="8a247-118">If the table is empty, index pages are minimally logged.</span></span>  
  
    -   <span data-ttu-id="8a247-119">若資料表不是空白，則索引頁會使用完整記錄。</span><span class="sxs-lookup"><span data-stu-id="8a247-119">If table is non-empty, index pages are fully logged.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8a247-120">若一開始您以空白資料表與多個批次來進行大量匯入資料，則在第一個批次中，索引頁與資料頁都會使用最低限度記錄，但從第二個批次開始，就只有資料頁會使用最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="8a247-120">If you start with an empty table and bulk import the data in multiple batches, both index and data pages are minimally logged for the first batch, but beginning with the second batch, only data pages are minimally logged.</span></span>  
  
-   <span data-ttu-id="8a247-121">若資料表有叢集索引但為空白，則資料頁與索引頁都會使用最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="8a247-121">If the table has a clustered index and is empty, both data and index pages are minimally logged.</span></span> <span data-ttu-id="8a247-122">相對地，若資料表有叢集索引且並非空白，則不論復原模式為何，資料頁與索引頁都會使用完整記錄。</span><span class="sxs-lookup"><span data-stu-id="8a247-122">In contrast, if a table has a clustered index and is non-empty, data pages and index pages are both fully logged regardless of the recovery model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8a247-123">若一開始您以空白資料表與批次來進行大量匯入資料，則在第一個批次中，索引頁與資料頁都會使用最低限度記錄，但從第二個批次開始，只有資料頁會使用大量記錄。</span><span class="sxs-lookup"><span data-stu-id="8a247-123">If you start with an empty table and bulk import the data in batches, both index and data pages are minimally logged for the first batch, but from the second batch onwards, only data pages are bulk logged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a247-124">啟用異動複寫時，即使在大量記錄復原模式下也會完整記錄 BULK INSERT 作業。</span><span class="sxs-lookup"><span data-stu-id="8a247-124">When transactional replication is enabled, BULK INSERT operations are fully logged even under the Bulk Logged recovery model.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8a247-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="8a247-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="8a247-126">檢視或變更資料庫的復原模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8a247-126">View or Change the Recovery Model of a Database &#40;SQL Server&#41;</span></span>](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="8a247-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a247-127">See Also</span></span>  
 <span data-ttu-id="8a247-128">[復原模式 &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8a247-128">[Recovery Models &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="8a247-129">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="8a247-129">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="8a247-130">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a247-130">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="8a247-131">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a247-131">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="8a247-132">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a247-132">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="8a247-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a247-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="8a247-134">[資料表提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span><span class="sxs-lookup"><span data-stu-id="8a247-134">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span></span>  
 [<span data-ttu-id="8a247-135">INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8a247-135">INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/insert-transact-sql)  
  
  
