---
title: 備份壓縮 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], backup compression
- backup compression [SQL Server], about backup compression
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- backing up [SQL Server], backup compression
- backup compression [SQL Server]
ms.assetid: 05bc9c4f-3947-4dd4-b823-db77519bd4d2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3291a858d8ef037e7cca92eb2e6abb19aec4da8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592076"
---
# <a name="backup-compression-sql-server"></a><span data-ttu-id="91de1-102">備份壓縮 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91de1-102">Backup Compression (SQL Server)</span></span>
  <span data-ttu-id="91de1-103">本主題會說明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份的壓縮，包括限制、壓縮備份的效能取捨、備份壓縮的組態及壓縮比率。</span><span class="sxs-lookup"><span data-stu-id="91de1-103">This topic describes the compression of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups, including restrictions, performance trade-off of compressing backups, the configuration of backup compression, and the compression ratio.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91de1-104">如需支援備份壓縮之版本的資訊 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="91de1-104">For information which editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support backup compression, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="91de1-105">每個 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 版本與更新版本都可以還原壓縮的備份。</span><span class="sxs-lookup"><span data-stu-id="91de1-105">Every edition of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later can restore a compressed backup.</span></span>  
  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="91de1-106">優點</span><span class="sxs-lookup"><span data-stu-id="91de1-106">Benefits</span></span>  
  
-   <span data-ttu-id="91de1-107">由於壓縮的備份小於相同資料的未壓縮備份，所以壓縮備份通常需要更少的裝置 I/O 而且通常會大幅提升備份速度。</span><span class="sxs-lookup"><span data-stu-id="91de1-107">Because a compressed backup is smaller than an uncompressed backup of the same data, compressing a backup typically requires less device I/O and therefore usually increases backup speed significantly.</span></span>  
  
     <span data-ttu-id="91de1-108">如需詳細資訊，請參閱本主題稍後介紹的＜ [壓縮備份的效能影響](#PerfImpact)＞。</span><span class="sxs-lookup"><span data-stu-id="91de1-108">For more information, see [Performance Impact of Compressing Backups](#PerfImpact), later in this topic.</span></span>  
  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="91de1-109">限制</span><span class="sxs-lookup"><span data-stu-id="91de1-109">Restrictions</span></span>  
 <span data-ttu-id="91de1-110">下列限制適用於壓縮的備份：</span><span class="sxs-lookup"><span data-stu-id="91de1-110">The following restrictions apply to compressed backups:</span></span>  
  
-   <span data-ttu-id="91de1-111">壓縮和未壓縮的備份無法在媒體集中並存。</span><span class="sxs-lookup"><span data-stu-id="91de1-111">Compressed and uncompressed backups cannot co-exist in a media set.</span></span>  
  
-   <span data-ttu-id="91de1-112">舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法讀取壓縮的備份。</span><span class="sxs-lookup"><span data-stu-id="91de1-112">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot read compressed backups.</span></span>  
  
-   <span data-ttu-id="91de1-113">NTbackup 無法與壓縮的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份共用磁帶。</span><span class="sxs-lookup"><span data-stu-id="91de1-113">NTbackups cannot share a tape with compressed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span>  
  
  
##  <a name="performance-impact-of-compressing-backups"></a><a name="PerfImpact"></a> <span data-ttu-id="91de1-114">壓縮備份的效能影響</span><span class="sxs-lookup"><span data-stu-id="91de1-114">Performance Impact of Compressing Backups</span></span>  
 <span data-ttu-id="91de1-115">根據預設，壓縮會大幅增加 CPU 使用量，而且壓縮程序所耗用的額外 CPU 可能會對並行作業造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="91de1-115">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="91de1-116">因此，您可能會想要在其 CPU 使用量由[資源管理員](../resource-governor/resource-governor.md)限制的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="91de1-116">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by[Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="91de1-117">如需詳細資訊，請參閱本主題稍後介紹的＜ [使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="91de1-117">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
 <span data-ttu-id="91de1-118">若要全盤了解備份 I/O 效能，您可以透過評估下列效能計數器種類，隔離往返裝置之間的備份 I/O：</span><span class="sxs-lookup"><span data-stu-id="91de1-118">To obtain a good picture of your backup I/O performance, you can isolate the backup I/O to or from devices by evaluating the following sorts of performance counters:</span></span>  
  
-   <span data-ttu-id="91de1-119">Windows I/O 效能計數器，例如實體磁碟計數器</span><span class="sxs-lookup"><span data-stu-id="91de1-119">Windows I/O performance counters, such as the physical-disk counters</span></span>  
  
-   <span data-ttu-id="91de1-120">**SQLServer:Backup Device** 物件的 [Device Throughput Bytes/sec](../performance-monitor/sql-server-backup-device-object.md) 計數器</span><span class="sxs-lookup"><span data-stu-id="91de1-120">The **Device Throughput Bytes/sec** counter of the [SQLServer:Backup Device](../performance-monitor/sql-server-backup-device-object.md) object</span></span>  
  
-   <span data-ttu-id="91de1-121">**SQLServer:Databases** 物件的 [Backup/Restore Throughput/sec](../performance-monitor/sql-server-databases-object.md) 計數器</span><span class="sxs-lookup"><span data-stu-id="91de1-121">The **Backup/Restore Throughput/sec** counter of the [SQLServer:Databases](../performance-monitor/sql-server-databases-object.md) object</span></span>  
  
 <span data-ttu-id="91de1-122">如需有關 Windows 計數器的詳細資訊，請參閱 Windows 說明。</span><span class="sxs-lookup"><span data-stu-id="91de1-122">For information about Windows counters, see Windows help.</span></span> <span data-ttu-id="91de1-123">如需如何使用 SQL Server 計數器的相關資訊，請參閱 [使用 SQL Server 物件](../performance-monitor/use-sql-server-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="91de1-123">For information about how to work with SQL Server counters, see [Use SQL Server Objects](../performance-monitor/use-sql-server-objects.md).</span></span>  
  
  
##  <a name="calculate-the-compression-ratio-of-a-compressed-backup"></a><a name="CompressionRatio"></a> <span data-ttu-id="91de1-124">計算壓縮備份的壓縮率</span><span class="sxs-lookup"><span data-stu-id="91de1-124">Calculate the Compression Ratio of a Compressed Backup</span></span>  
 <span data-ttu-id="91de1-125">若要計算備份的壓縮率，請使用 **backupset** 記錄資料表的 **backup_size** 和 [compressed_backup_size](/sql/relational-databases/system-tables/backupset-transact-sql) 資料行中的備份值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="91de1-125">To calculate the compression ratio of a backup, use the values for the backup in the **backup_size** and **compressed_backup_size** columns of the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) history table, as follows:</span></span>  
  
 <span data-ttu-id="91de1-126">**backup_size**：**compressed_backup_size**</span><span class="sxs-lookup"><span data-stu-id="91de1-126">**backup_size**:**compressed_backup_size**</span></span>  
  
 <span data-ttu-id="91de1-127">例如，壓縮比 3:1 表示您節省了大約 66% 的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="91de1-127">For example, a 3:1 compression ratio indicates that you are saving about 66% on disk space.</span></span> <span data-ttu-id="91de1-128">若要針對這些資料行進行查詢，您可以使用下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="91de1-128">To query on these columns, you can use the following Transact-SQL statement:</span></span>  
  
```  
SELECT backup_size/compressed_backup_size FROM msdb..backupset;  
```  
  
 <span data-ttu-id="91de1-129">壓縮備份的壓縮比取決於已經壓縮的資料。</span><span class="sxs-lookup"><span data-stu-id="91de1-129">The compression ratio of a compressed backup depends on the data that has been compressed.</span></span> <span data-ttu-id="91de1-130">有許多因素可能會影響取得的壓縮比。</span><span class="sxs-lookup"><span data-stu-id="91de1-130">A variety of factors can impact the compression ratio obtained.</span></span> <span data-ttu-id="91de1-131">主要的因素包括：</span><span class="sxs-lookup"><span data-stu-id="91de1-131">Major factors include:</span></span>  
  
-   <span data-ttu-id="91de1-132">資料的類型。</span><span class="sxs-lookup"><span data-stu-id="91de1-132">The type of data.</span></span>  
  
     <span data-ttu-id="91de1-133">字元資料的壓縮比較其他資料類型要高。</span><span class="sxs-lookup"><span data-stu-id="91de1-133">Character data compresses more than other types of data.</span></span>  
  
-   <span data-ttu-id="91de1-134">頁面上資料列之間的資料一致性。</span><span class="sxs-lookup"><span data-stu-id="91de1-134">The consistency of the data among rows on a page.</span></span>  
  
     <span data-ttu-id="91de1-135">一般而言，如果某個頁面包含許多資料列，而且其中某個欄位包含相同的值，則系統可能會針對該值進行大幅壓縮。</span><span class="sxs-lookup"><span data-stu-id="91de1-135">Typically, if a page contains several rows in which a field contains the same value, significant compression might occur for that value.</span></span> <span data-ttu-id="91de1-136">反之，如果某個資料庫包含隨機資料或者每個頁面僅包含單一大型資料列，則壓縮的備份幾乎會與未壓縮的備份一樣大。</span><span class="sxs-lookup"><span data-stu-id="91de1-136">In contrast, for a database that contains random data or that contains only one large row per page, a compressed backup would be almost as large as an uncompressed backup.</span></span>  
  
-   <span data-ttu-id="91de1-137">資料是否經過加密。</span><span class="sxs-lookup"><span data-stu-id="91de1-137">Whether the data is encrypted.</span></span>  
  
     <span data-ttu-id="91de1-138">加密資料的壓縮比大幅低於對等的未加密資料。</span><span class="sxs-lookup"><span data-stu-id="91de1-138">Encrypted data compresses significantly less than equivalent unencrypted data.</span></span> <span data-ttu-id="91de1-139">如果使用透明資料加密來加密整個資料庫，則壓縮備份可能不會大幅縮減其大小 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="91de1-139">If transparent data encryption is used to encrypt an entire database, compressing backups might not reduce their size by much, if at all.</span></span>  
  
-   <span data-ttu-id="91de1-140">資料庫是否經過壓縮。</span><span class="sxs-lookup"><span data-stu-id="91de1-140">Whether the database is compressed.</span></span>  
  
     <span data-ttu-id="91de1-141">如果資料庫已壓縮，壓縮備份可能不會大幅縮減其大小 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="91de1-141">If the database is compressed, compressing backups might not reduce their size by much, if at all.</span></span>  
  
  
##  <a name="allocation-of-space-for-the-backup-file"></a><a name="Allocation"></a> <span data-ttu-id="91de1-142">配置備份檔案的空間</span><span class="sxs-lookup"><span data-stu-id="91de1-142">Allocation of Space for the Backup File</span></span>  
 <span data-ttu-id="91de1-143">對於壓縮備份，最後備份檔案的大小取決於資料可壓縮的程度，但是在備份作業完成之前，無法得知這項資訊。</span><span class="sxs-lookup"><span data-stu-id="91de1-143">For compressed backups, the size of the final backup file depends on how compressible the data is, and this is unknown before the backup operation finishes.</span></span>  <span data-ttu-id="91de1-144">因此，根據預設，使用壓縮備份資料庫時，Database Engine 會針對備份檔案使用預先配置的演算法。</span><span class="sxs-lookup"><span data-stu-id="91de1-144">Therefore, by default, when backing up a database using compression, the Database Engine uses a pre-allocation algorithm for the backup file.</span></span> <span data-ttu-id="91de1-145">此演算法預先為備份檔案配置了預先定義的資料庫大小百分比。</span><span class="sxs-lookup"><span data-stu-id="91de1-145">This algorithm pre-allocates a predefined percentage of the size of the database for the backup file.</span></span> <span data-ttu-id="91de1-146">如果在備份作業期間需要更多空間，Database Engine 會增加檔案大小。</span><span class="sxs-lookup"><span data-stu-id="91de1-146">If more space is needed during the backup operation, the Database Engine grows the file.</span></span> <span data-ttu-id="91de1-147">如果最後的大小小於配置的空間，在備份作業結束時，Database Engine 會將檔案縮小為最後的實際備份大小。</span><span class="sxs-lookup"><span data-stu-id="91de1-147">If the final size is less than the allocated space, at the end of the backup operation, the Database Engine shrinks the file to the actual final size of the backup.</span></span>  
  
 <span data-ttu-id="91de1-148">若要讓備份檔案只依照需要增加至最終大小，請使用追蹤旗標 3042。</span><span class="sxs-lookup"><span data-stu-id="91de1-148">To allow the backup file to grow only as needed to reach its final size, use trace flag 3042.</span></span> <span data-ttu-id="91de1-149">追蹤旗標 3042 會導致備份作業略過預設備份壓縮預先配置演算法。</span><span class="sxs-lookup"><span data-stu-id="91de1-149">Trace flag 3042 causes the backup operation to bypass the default backup compression pre-allocation algorithm.</span></span> <span data-ttu-id="91de1-150">如果您只要配置壓縮備份所需的實際大小，藉以節省空間，這個追蹤旗標就很有用。</span><span class="sxs-lookup"><span data-stu-id="91de1-150">This trace flag is useful if you need to save on space by allocating only the actual size required for the compressed backup.</span></span> <span data-ttu-id="91de1-151">不過，使用此追蹤旗標可能會導致效能稍微降低 (可能會增加備份作業的持續時間)。</span><span class="sxs-lookup"><span data-stu-id="91de1-151">However, using this trace flag might cause a slight performance penalty (a possible increase in the duration of the backup operation).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="91de1-152">相關工作</span><span class="sxs-lookup"><span data-stu-id="91de1-152">Related Tasks</span></span>  
  
-   [<span data-ttu-id="91de1-153">設定備份壓縮 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="91de1-153">Configure Backup Compression &#40;SQL Server&#41;</span></span>](backup-compression-sql-server.md)  
  
-   [<span data-ttu-id="91de1-154">檢視或設定 backup compression default 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="91de1-154">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
-   [<span data-ttu-id="91de1-155">使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91de1-155">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="91de1-156">DBCC TRACEON &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91de1-156">DBCC TRACEON &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)  
  
-   [<span data-ttu-id="91de1-157">DBCC TRACEOFF &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91de1-157">DBCC TRACEOFF &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceoff-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="91de1-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91de1-158">See Also</span></span>  
 <span data-ttu-id="91de1-159">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91de1-159">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="91de1-160">追蹤旗標 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91de1-160">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
