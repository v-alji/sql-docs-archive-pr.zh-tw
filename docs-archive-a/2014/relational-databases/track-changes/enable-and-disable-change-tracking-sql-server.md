---
title: 啟用和停用變更追蹤 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], disabling
- data changes [SQL Server]
- change tracking [SQL Server], enabling
- tracking data changes [SQL Server]
- change tracking [SQL Server], configuring
- data [SQL Server], changing
ms.assetid: 1c92ec7e-ae53-4498-8bfd-c66a42a24d54
author: rothja
ms.author: jroth
ms.openlocfilehash: 402c63ae03df14e3a725fbc440575f5233d502f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594955"
---
# <a name="enable-and-disable-change-tracking-sql-server"></a><span data-ttu-id="28931-102">啟用和停用變更追蹤 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="28931-102">Enable and Disable Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="28931-103">此主題描述如何針對資料庫和資料表啟用及停用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-103">This topic describes how to enable and disable change tracking for a database and a table.</span></span>  
  
## <a name="enable-change-tracking-for-a-database"></a><span data-ttu-id="28931-104">為資料庫啟用變更追蹤</span><span class="sxs-lookup"><span data-stu-id="28931-104">Enable Change Tracking for a Database</span></span>  
 <span data-ttu-id="28931-105">在您可以使用變更追蹤之前，必須先在資料庫層級啟用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-105">Before you can use change tracking, you must enable change tracking at the database level.</span></span> <span data-ttu-id="28931-106">下列範例將示範如何使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)來啟用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-106">The following example shows how to enable change tracking by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(CHANGE_RETENTION = 2 DAYS, AUTO_CLEANUP = ON)  
```  
  
 <span data-ttu-id="28931-107">您也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 資料庫屬性 &#40;變更追蹤頁面&#41; [資料庫屬性 &amp;#40;變更追蹤頁面&amp;#41;](../databases/database-properties-changetracking-page.md) 中的變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-107">You can also enable change tracking in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="28931-108">當您啟用變更追蹤時，可以指定 CHANGE_RETENTION 和 AUTO_CLEANUP 選項，而且您可以在啟用變更追蹤之後的任何時間變更這些值。</span><span class="sxs-lookup"><span data-stu-id="28931-108">You can specify the CHANGE_RETENTION and AUTO_CLEANUP options when you enable change tracking, and you can change the values at any time after change tracking is enabled.</span></span>  
  
 <span data-ttu-id="28931-109">變更保留值會指定保存變更追蹤資訊的期間。</span><span class="sxs-lookup"><span data-stu-id="28931-109">The change retention value specifies the time period for which change tracking information is kept.</span></span> <span data-ttu-id="28931-110">早於此期間的變更追蹤資訊會定期遭到移除。</span><span class="sxs-lookup"><span data-stu-id="28931-110">Change tracking information that is older than this time period is removed periodically.</span></span> <span data-ttu-id="28931-111">當您設定這個值時，應該考量應用程式與資料庫資料表同步處理的頻率。</span><span class="sxs-lookup"><span data-stu-id="28931-111">When you are setting this value, you should consider how often applications will synchronize with the tables in the database.</span></span> <span data-ttu-id="28931-112">指定的保留期間至少必須與同步處理之間的期間上限一樣長。</span><span class="sxs-lookup"><span data-stu-id="28931-112">The specified retention period must be at least as long as the maximum time period between synchronizations.</span></span> <span data-ttu-id="28931-113">如果應用程式在較長的間隔上取得變更，所傳回的結果可能會不正確，因為變更資訊的某部分可能已遭到移除。</span><span class="sxs-lookup"><span data-stu-id="28931-113">If an application obtains changes at longer intervals, the results that are returned might be incorrect because some of the change information has probably been removed.</span></span> <span data-ttu-id="28931-114">為了避免取得不正確的結果，應用程式可以使用 CHANGE_TRACKING_MIN_VALID_VERSION 系統函數來判斷同步處理之間的間隔是否已經過長。</span><span class="sxs-lookup"><span data-stu-id="28931-114">To avoid obtaining incorrect results, an application can use the CHANGE_TRACKING_MIN_VALID_VERSION system function to determine whether the interval between synchronizations has been too long.</span></span>  
  
 <span data-ttu-id="28931-115">您可以使用 AUTO_CLEANUP 選項來啟用或停用移除老舊變更追蹤資訊的清除工作。</span><span class="sxs-lookup"><span data-stu-id="28931-115">You can use the AUTO_CLEANUP option to enable or disable the cleanup task that removes old change tracking information.</span></span> <span data-ttu-id="28931-116">當有暫時性的問題阻礙應用程式同步處理時，這樣的處理方式會很實用，而且在問題解決之前，必須先暫停用來移除早於保留期間之變更追蹤資訊的程序。</span><span class="sxs-lookup"><span data-stu-id="28931-116">This can be useful when there is a temporary problem that prevents applications from synchronizing and the process for removing change tracking information older than the retention period must be paused until the problem is resolved.</span></span>  
  
 <span data-ttu-id="28931-117">如果是使用變更追蹤的任何資料庫，請注意以下事項：</span><span class="sxs-lookup"><span data-stu-id="28931-117">For any database that uses change tracking, be aware of the following:</span></span>  
  
-   <span data-ttu-id="28931-118">若要使用變更追蹤，資料庫相容性層級必須設定為 90 以上 (含)。</span><span class="sxs-lookup"><span data-stu-id="28931-118">To use change tracking, the database compatibility level must be set to 90 or greater.</span></span> <span data-ttu-id="28931-119">如果資料庫的相容性層級低於 90，您也可以設定變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-119">If a database has a compatibility level of less than 90, you can configure change tracking.</span></span> <span data-ttu-id="28931-120">不過，用來取得變更追蹤資訊的 CHANGETABLE 函數將會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="28931-120">However, the CHANGETABLE function, which is used to obtain change tracking information, will return an error.</span></span>  
  
-   <span data-ttu-id="28931-121">若要確保所有變更追蹤資訊都一致，使用快照隔離是最簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="28931-121">Using snapshot isolation is the easiest way for you to help ensure that all change tracking information is consistent.</span></span> <span data-ttu-id="28931-122">基於這個原因，我們強烈建議您將資料庫的快照隔離設定為 ON。</span><span class="sxs-lookup"><span data-stu-id="28931-122">For this reason, we strongly recommend that snapshot isolation be set to ON for the database.</span></span> <span data-ttu-id="28931-123">如需詳細資訊，請參閱[使用變更追蹤 &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="28931-123">For more information, see [Work with Change Tracking &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md).</span></span>  
  
## <a name="enable-change-tracking-for-a-table"></a><span data-ttu-id="28931-124">為資料表啟用變更追蹤</span><span class="sxs-lookup"><span data-stu-id="28931-124">Enable Change Tracking for a Table</span></span>  
 <span data-ttu-id="28931-125">您必須針對您要追蹤的每一個資料表啟用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-125">Change tracking must be enabled for each table that you want tracked.</span></span> <span data-ttu-id="28931-126">啟用變更追蹤時，系統會針對資料表中受到 DML 作業影響的所有資料列維護變更追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="28931-126">When change tracking is enabled, change tracking information is maintained for all rows in the table that are affected by a DML operation.</span></span>  
  
 <span data-ttu-id="28931-127">下列範例示範如何使用 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)，為資料表啟用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-127">The following example shows how to enable change tracking for a table by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
```sql  
ALTER TABLE Person.Contact  
ENABLE CHANGE_TRACKING  
WITH (TRACK_COLUMNS_UPDATED = ON)  
```  
  
 <span data-ttu-id="28931-128">您也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 資料庫屬性 &#40;變更追蹤頁面&#41; [資料庫屬性 &amp;#40;變更追蹤頁面&amp;#41;](../databases/database-properties-changetracking-page.md) 中的變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-128">You can also enable change tracking for a table in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="28931-129">當 TRACK_COLUMNS_UPDATED 選項設定為 ON 時， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會將哪些資料行已更新的相關額外資訊儲存到內部變更追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="28931-129">When the TRACK_COLUMNS_UPDATED option is set to ON, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] stores extra information about which columns were updated to the internal change tracking table.</span></span> <span data-ttu-id="28931-130">資料行追蹤只能讓應用程式同步處理已經更新的那些資料行。</span><span class="sxs-lookup"><span data-stu-id="28931-130">Column tracking can enable an application to synchronize only those columns that were updated.</span></span> <span data-ttu-id="28931-131">這樣可以改善效率與效能。</span><span class="sxs-lookup"><span data-stu-id="28931-131">This can improve efficiency and performance.</span></span> <span data-ttu-id="28931-132">但是，由於維護資料行追蹤資訊會增加額外的儲存負擔，所以此選項預設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="28931-132">However, because maintaining column tracking information adds some extra storage overhead, this option is set to OFF by default.</span></span>  
  
## <a name="disable-change-tracking-for-a-database-or-table"></a><span data-ttu-id="28931-133">為資料庫或資料表停用變更追蹤</span><span class="sxs-lookup"><span data-stu-id="28931-133">Disable Change Tracking for a Database or Table</span></span>  
 <span data-ttu-id="28931-134">在可以針對資料庫將變更追縱設定為 OFF 之前，必須先針對所有變更追蹤的資料表停用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-134">Change tracking must first be disabled for all change-tracked tables before change tracking can be set to OFF for the database.</span></span> <span data-ttu-id="28931-135">若要判斷已針對資料庫啟用變更追蹤的資料表，請使用 [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="28931-135">To determine the tables that have change tracking enabled for a database, use the [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) catalog view.</span></span>  
  
 <span data-ttu-id="28931-136">當資料庫中沒有任何資料表追蹤變更時，您可以為此資料庫停用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-136">When no tables in a database track changes, you can disable change tracking for the database.</span></span> <span data-ttu-id="28931-137">下列範例將示範如何使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)，為資料庫停用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-137">The following example shows how to disable change tracking for a database by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF  
```  
  
 <span data-ttu-id="28931-138">下列範例示範如何使用 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)，為資料表停用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="28931-138">The following example shows how to disable change tracking for a table by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
```sql  
ALTER TABLE Person.Contact  
DISABLE CHANGE_TRACKING;  
```  
  
## <a name="see-also"></a><span data-ttu-id="28931-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28931-139">See Also</span></span>  
 <span data-ttu-id="28931-140">[資料庫屬性 &#40;變更追蹤頁面&#41;](../databases/database-properties-changetracking-page.md) </span><span class="sxs-lookup"><span data-stu-id="28931-140">[Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) </span></span>  
 <span data-ttu-id="28931-141">[ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="28931-141">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="28931-142">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span><span class="sxs-lookup"><span data-stu-id="28931-142">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span></span>  
 <span data-ttu-id="28931-143">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span><span class="sxs-lookup"><span data-stu-id="28931-143">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span></span>  
 <span data-ttu-id="28931-144">[追蹤資料變更 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="28931-144">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="28931-145">[關於變更追蹤 &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="28931-145">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="28931-146">[使用變更資料 &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="28931-146">[Work with Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span></span>  
 [<span data-ttu-id="28931-147">管理變更追蹤 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28931-147">Manage Change Tracking &#40;SQL Server&#41;</span></span>](manage-change-tracking-sql-server.md)  
  
  
