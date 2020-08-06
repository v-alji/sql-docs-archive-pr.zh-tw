---
title: 資料庫功能 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 04518abb-8581-47c8-a601-ee9136c3c0eb
author: rothja
ms.author: jroth
ms.openlocfilehash: 56b9f9ba9cc6e11ea82b822ae10b31710c8617b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597163"
---
# <a name="database-features"></a><span data-ttu-id="7e5e1-102">資料庫功能</span><span class="sxs-lookup"><span data-stu-id="7e5e1-102">Database Features</span></span>
  <span data-ttu-id="7e5e1-103">本節包含與資料庫相關聯的功能和工作、資料庫物件、資料類型及用於處理或管理資料的機制。</span><span class="sxs-lookup"><span data-stu-id="7e5e1-103">This section contains the features and tasks associated with databases, database objects, data types, and the mechanisms used to work with or manage data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e5e1-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="7e5e1-104">In This Section</span></span>  
  
|||
|--|--|
|[<span data-ttu-id="7e5e1-105">資料庫</span><span class="sxs-lookup"><span data-stu-id="7e5e1-105">Databases</span></span>](databases/databases.md)|[<span data-ttu-id="7e5e1-106">SQL Server 資料庫的備份與還原</span><span class="sxs-lookup"><span data-stu-id="7e5e1-106">Back Up and Restore of SQL Server Databases</span></span>](backup-restore/back-up-and-restore-of-sql-server-databases.md)|  
|[<span data-ttu-id="7e5e1-107">資料表</span><span class="sxs-lookup"><span data-stu-id="7e5e1-107">Tables</span></span>](tables/tables.md)|[<span data-ttu-id="7e5e1-108">序號</span><span class="sxs-lookup"><span data-stu-id="7e5e1-108">Sequence Numbers</span></span>](sequence-numbers/sequence-numbers.md)|[<span data-ttu-id="7e5e1-109">資料的大量匯入及匯出 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-109">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](import-export/bulk-import-and-export-of-data-sql-server.md)|  
|[<span data-ttu-id="7e5e1-110">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-110">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp/in-memory-oltp-in-memory-optimization.md)|[<span data-ttu-id="7e5e1-111">DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="7e5e1-111">DDL Triggers</span></span>](triggers/ddl-triggers.md)|[<span data-ttu-id="7e5e1-112">資料壓縮</span><span class="sxs-lookup"><span data-stu-id="7e5e1-112">Data Compression</span></span>](data-compression/data-compression.md)|  
|[<span data-ttu-id="7e5e1-113">索引數</span><span class="sxs-lookup"><span data-stu-id="7e5e1-113">Indexes</span></span>](indexes/indexes.md)|[<span data-ttu-id="7e5e1-114">DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="7e5e1-114">DML Triggers</span></span>](triggers/dml-triggers.md)|[<span data-ttu-id="7e5e1-115">Transact-SQL 中的 OLE Automation 物件</span><span class="sxs-lookup"><span data-stu-id="7e5e1-115">OLE Automation Objects in Transact-SQL</span></span>](stored-procedures/ole-automation-objects-in-transact-sql.md)|  
|[<span data-ttu-id="7e5e1-116">分割資料表與索引</span><span class="sxs-lookup"><span data-stu-id="7e5e1-116">Partitioned Tables and Indexes</span></span>](partitions/partitioned-tables-and-indexes.md)|[<span data-ttu-id="7e5e1-117">同義字 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-117">Synonyms &#40;Database Engine&#41;</span></span>](synonyms/synonyms-database-engine.md)|[<span data-ttu-id="7e5e1-118">事件通知</span><span class="sxs-lookup"><span data-stu-id="7e5e1-118">Event Notifications</span></span>](service-broker/event-notifications.md)|  
|[<span data-ttu-id="7e5e1-119">檢視</span><span class="sxs-lookup"><span data-stu-id="7e5e1-119">Views</span></span>](views/views.md)|[<span data-ttu-id="7e5e1-120">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-120">XML Data &#40;SQL Server&#41;</span></span>](xml/xml-data-sql-server.md)|[<span data-ttu-id="7e5e1-121">效能的監視與微調</span><span class="sxs-lookup"><span data-stu-id="7e5e1-121">Monitor and Tune for Performance</span></span>](performance/monitor-and-tune-for-performance.md)|  
|[<span data-ttu-id="7e5e1-122">預存程序 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-122">Stored Procedures &#40;Database Engine&#41;</span></span>](stored-procedures/stored-procedures-database-engine.md)|[<span data-ttu-id="7e5e1-123">空間資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-123">Spatial Data &#40;SQL Server&#41;</span></span>](spatial/spatial-data-sql-server.md)||  
|[<span data-ttu-id="7e5e1-124">搜尋 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-124">Search &#40;SQL Server&#41;</span></span>](../database-engine/search-sql-server.md)|[<span data-ttu-id="7e5e1-125">二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-125">Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;</span></span>](blob/binary-large-object-blob-data-sql-server.md)||  
|[<span data-ttu-id="7e5e1-126">使用者定義的函式</span><span class="sxs-lookup"><span data-stu-id="7e5e1-126">User-Defined Functions</span></span>](user-defined-functions/user-defined-functions.md)|[<span data-ttu-id="7e5e1-127">資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="7e5e1-127">Data-tier Applications</span></span>](data-tier-applications/data-tier-applications.md)||  
|[<span data-ttu-id="7e5e1-128">統計資料</span><span class="sxs-lookup"><span data-stu-id="7e5e1-128">Statistics</span></span>](statistics/statistics.md)|[<span data-ttu-id="7e5e1-129">交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-129">The Transaction Log &#40;SQL Server&#41;</span></span>](logs/the-transaction-log-sql-server.md)||  
|[<span data-ttu-id="7e5e1-130">計畫指南</span><span class="sxs-lookup"><span data-stu-id="7e5e1-130">Plan Guides</span></span>](performance/plan-guides.md)|[<span data-ttu-id="7e5e1-131">資料庫檢查點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e1-131">Database Checkpoints &#40;SQL Server&#41;</span></span>](logs/database-checkpoints-sql-server.md)||  
  
  
