---
title: 備份概觀 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], backing up data
- backups [SQL Server]
- database backups [SQL Server]
- backup types [SQL Server]
- data backups [SQL Server]
- backing up tables [SQL Server]
- database restores [SQL Server], backups
- backing up [SQL Server], about backing up
- restoring [SQL Server], backup types
- backups [SQL Server], about
- backups [SQL Server], table-level backups unsupported
ms.assetid: 09a6e0c2-d8fd-453f-9aac-4ff24a97dc1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60fbd0341c4e29c6f98cc4d5fe5a2cfabc9b703f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606931"
---
# <a name="backup-overview-sql-server"></a><span data-ttu-id="7e5e3-102">Backup Overview (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7e5e3-102">Backup Overview (SQL Server)</span></span>
  <span data-ttu-id="7e5e3-103">本主題介紹 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份元件。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-103">This topic introduces the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup component.</span></span> <span data-ttu-id="7e5e3-104">備份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫對於保護資料非常重要。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-104">Backing up your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is essential for protecting your data.</span></span> <span data-ttu-id="7e5e3-105">此討論涵蓋備份類型和備份限制。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-105">This discussion covers backup types, and backup restrictions.</span></span> <span data-ttu-id="7e5e3-106">本主題同時介紹 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份裝置和備份媒體。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-106">The topic also introduces [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices and backup media.</span></span>  
  
 <span data-ttu-id="7e5e3-107">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="7e5e3-107">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="7e5e3-108">元件和概念</span><span class="sxs-lookup"><span data-stu-id="7e5e3-108">Components and Concepts</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="7e5e3-109">備份壓縮</span><span class="sxs-lookup"><span data-stu-id="7e5e3-109">Backup Compression</span></span>](#BackupCompression)  
  
-   [<span data-ttu-id="7e5e3-110">SQL Server 在備份作業上的限制</span><span class="sxs-lookup"><span data-stu-id="7e5e3-110">Restrictions on Backup Operations in SQL Server</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="7e5e3-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="7e5e3-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="7e5e3-112">元件和概念</span><span class="sxs-lookup"><span data-stu-id="7e5e3-112">Components and Concepts</span></span>  
 <span data-ttu-id="7e5e3-113">備份 (back up) [動詞]</span><span class="sxs-lookup"><span data-stu-id="7e5e3-113">back up [verb]</span></span>  
 <span data-ttu-id="7e5e3-114">將資料或記錄檔記錄從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫或其交易記錄複製至備份裝置 (例如磁碟)，以建立資料備份或記錄備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-114">Copies the data or log records from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.</span></span>  
  
 <span data-ttu-id="7e5e3-115">備份 (backup) [名詞]</span><span class="sxs-lookup"><span data-stu-id="7e5e3-115">backup [noun]</span></span>  
 <span data-ttu-id="7e5e3-116">失敗後可用來還原和復原資料的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料副本。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-116">A copy of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data that can be used to restore and recover the data after a failure.</span></span> <span data-ttu-id="7e5e3-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料備份會在資料庫層級或者一個或多個資料庫檔案或檔案群組層級建立。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-117">A backup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data is created at the level of a database or one or more of its files or filegroups.</span></span> <span data-ttu-id="7e5e3-118">無法建立資料表層級備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-118">Table-level backups cannot be created.</span></span> <span data-ttu-id="7e5e3-119">除了資料備份之外，完整復原模式也需要建立交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-119">In addition to data backups, the full recovery model requires creating backups of the transaction log.</span></span>  
  
 [<span data-ttu-id="7e5e3-120">復原模式</span><span class="sxs-lookup"><span data-stu-id="7e5e3-120">recovery model</span></span>](recovery-models-sql-server.md)  
 <span data-ttu-id="7e5e3-121">控制資料庫上交易記錄維護的資料庫屬性。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-121">A database property that controls transaction log maintenance on a database.</span></span> <span data-ttu-id="7e5e3-122">復原模式共有三種：簡單、完整和大量記錄。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-122">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="7e5e3-123">資料庫的復原模式決定其備份和還原需求。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-123">The recovery model of database determines its backup and restore requirements.</span></span>  
  
 [<span data-ttu-id="7e5e3-124">還原</span><span class="sxs-lookup"><span data-stu-id="7e5e3-124">restore</span></span>](restore-and-recovery-overview-sql-server.md)  
 <span data-ttu-id="7e5e3-125">一個多階段的程序，它會將指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份中的所有資料和記錄頁面複製到指定的資料庫中，然後藉由套用所記錄的變更取得前面時段的資料，向前復原備份中記錄的所有交易。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-125">A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.</span></span>  
  
 <span data-ttu-id="7e5e3-126">**備份類型**</span><span class="sxs-lookup"><span data-stu-id="7e5e3-126">**Types of Backups**</span></span>  
  
 [<span data-ttu-id="7e5e3-127">僅複製備份</span><span class="sxs-lookup"><span data-stu-id="7e5e3-127">copy-only backup</span></span>](copy-only-backups-sql-server.md)  
 <span data-ttu-id="7e5e3-128">不受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一般備份順序影響的特殊用途備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-128">A special-use backup that is independent of the regular sequence of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span>  
  
 <span data-ttu-id="7e5e3-129">資料備份</span><span class="sxs-lookup"><span data-stu-id="7e5e3-129">data backup</span></span>  
 <span data-ttu-id="7e5e3-130">整個資料庫 (資料庫備份)、部分資料庫 (部分備份) 或是一組資料檔案或檔案群組 (檔案備份) 中資料的備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-130">A backup of data in a complete database (a database backup), a partial database (a partial backup), or a set of data files or filegroups (a file backup).</span></span>  
  
 [<span data-ttu-id="7e5e3-131">資料庫備份</span><span class="sxs-lookup"><span data-stu-id="7e5e3-131">database backup</span></span>](full-database-backups-sql-server.md)  
 <span data-ttu-id="7e5e3-132">資料庫的備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-132">A backup of a database.</span></span> <span data-ttu-id="7e5e3-133">完整資料庫備份代表備份完成時的整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-133">Full database backups represent the whole database at the time the backup finished.</span></span> <span data-ttu-id="7e5e3-134">差異資料庫備份僅包含自其最近的完整資料庫備份以來，對資料庫所做的變更。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-134">Differential database backups contain only changes made to the database since its most recent full database backup.</span></span>  
  
 [<span data-ttu-id="7e5e3-135">差異備份</span><span class="sxs-lookup"><span data-stu-id="7e5e3-135">differential backup</span></span>](full-database-backups-sql-server.md)  
 <span data-ttu-id="7e5e3-136">一種資料備份，是以整個或部分資料庫或一組資料檔案或檔案群組 (「差異基底」) 的最新完整備份為基礎，而且只包含自差異基底以來變更的資料範圍。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-136">A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the *differential base*) and that contains only the data extents that have changed since the differential base.</span></span>  
  
 <span data-ttu-id="7e5e3-137">差異部分備份僅記錄自上一次部分備份後在檔案群組中變更過的資料範圍，稱為差異基底。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-137">A differential partial backup records only the data extents that have changed in the filegroups since the previous partial backup, known as the base for the differential.</span></span>  
  
 <span data-ttu-id="7e5e3-138">完整備份</span><span class="sxs-lookup"><span data-stu-id="7e5e3-138">full backup</span></span>  
 <span data-ttu-id="7e5e3-139">一種資料備份，包含特定資料庫或一組檔案群組或檔案中的所有資料，也包含足以讓這個資料復原的記錄。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-139">A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.</span></span>  
  
 [<span data-ttu-id="7e5e3-140">記錄備份</span><span class="sxs-lookup"><span data-stu-id="7e5e3-140">log backup</span></span>](transaction-log-backups-sql-server.md)  
 <span data-ttu-id="7e5e3-141">交易記錄的備份，包含先前的記錄備份中未備份的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-141">A backup of transaction logs that includes all log records that were not backed up in a previous log backup.</span></span> <span data-ttu-id="7e5e3-142">(完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="7e5e3-142">(full recovery model)</span></span>  
  
 [<span data-ttu-id="7e5e3-143">檔案備份</span><span class="sxs-lookup"><span data-stu-id="7e5e3-143">file backup</span></span>](full-file-backups-sql-server.md)  
 <span data-ttu-id="7e5e3-144">一個或多個資料庫檔案或檔案群組的備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-144">A backup of one or more database files or filegroups.</span></span>  
  
 [<span data-ttu-id="7e5e3-145">部分備份</span><span class="sxs-lookup"><span data-stu-id="7e5e3-145">partial backup</span></span>](partial-backups-sql-server.md)  
 <span data-ttu-id="7e5e3-146">僅包含資料庫中某些檔案群組中的資料，包括主要檔案群組、每個讀取/寫入檔案群組，以及任何選擇性指定之唯讀檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-146">Contains data from only some of the filegroups in a database, including the data in the primary filegroup, every read/write filegroup, and any optionally-specified read-only files.</span></span>  
  
 <span data-ttu-id="7e5e3-147">**備份媒體詞匯和定義**</span><span class="sxs-lookup"><span data-stu-id="7e5e3-147">**Backup Media Terms and Definitions**</span></span>  
  
 [<span data-ttu-id="7e5e3-148">備份裝置</span><span class="sxs-lookup"><span data-stu-id="7e5e3-148">backup device</span></span>](backup-devices-sql-server.md)  
 <span data-ttu-id="7e5e3-149">寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份並從中進行還原的磁碟或磁帶裝置。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-149">A disk or tape device to which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups are written and from which they can be restored.</span></span> <span data-ttu-id="7e5e3-150">SQL Server 備份也可以寫入 Azure Blob 儲存體服務，而且會使用 **URL** 格式來指定備份檔案的目的地和名稱。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-150">SQL Server backups can also be written to an Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file..</span></span> <span data-ttu-id="7e5e3-151">如需詳細資訊，請參閱 [SQL Server 備份及還原與 Azure Blob 儲存體服務](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-151">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 [<span data-ttu-id="7e5e3-152">備份媒體</span><span class="sxs-lookup"><span data-stu-id="7e5e3-152">backup media</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="7e5e3-153">已寫入一個或多個備份的一個或多個磁帶或磁碟檔案。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-153">One or more tapes or disk files to which one or more backup have been written.</span></span>  
  
 [<span data-ttu-id="7e5e3-154">備份組</span><span class="sxs-lookup"><span data-stu-id="7e5e3-154">backup set</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="7e5e3-155">透過成功的備份作業，加入至媒體集的備份內容。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-155">The backup content that is added to a media set by a successful backup operation.</span></span>  
  
 [<span data-ttu-id="7e5e3-156">媒體家族</span><span class="sxs-lookup"><span data-stu-id="7e5e3-156">media family</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="7e5e3-157">在單一非鏡像裝置上或媒體集的一組鏡像裝置上所建立的備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-157">Backups created on a single nonmirrored device or a set of mirrored devices in a media set</span></span>  
  
 [<span data-ttu-id="7e5e3-158">媒體集</span><span class="sxs-lookup"><span data-stu-id="7e5e3-158">media set</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="7e5e3-159">按順序排列的備份媒體集合 (磁帶或磁碟檔案)，由一個或多個備份作業使用固定的備份裝置類型與數量寫入。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-159">An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span>  
  
 [<span data-ttu-id="7e5e3-160">鏡像媒體集</span><span class="sxs-lookup"><span data-stu-id="7e5e3-160">mirrored media set</span></span>](mirrored-backup-media-sets-sql-server.md)  
 <span data-ttu-id="7e5e3-161">多份媒體集副本 (鏡像)。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-161">Multiple copies (mirrors) of a media set.</span></span>  
  
##  <a name="backup-compression"></a><a name="BackupCompression"></a><span data-ttu-id="7e5e3-162">備份壓縮</span><span class="sxs-lookup"><span data-stu-id="7e5e3-162">Backup Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="7e5e3-163">和更新版本支援壓縮備份，而 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更新版本可以還原壓縮的備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-163">and later versions support compressing backups, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions can restore a compressed backup.</span></span> <span data-ttu-id="7e5e3-164">如需詳細資訊，請參閱[備份壓縮 &#40;SQL Server&#41;](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-164">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>  
  
##  <a name="restrictions-on-backup-operations-in-sql-server"></a><a name="Restrictions"></a><span data-ttu-id="7e5e3-165">SQL Server 中的備份作業限制</span><span class="sxs-lookup"><span data-stu-id="7e5e3-165">Restrictions on Backup Operations in SQL Server</span></span>  
 <span data-ttu-id="7e5e3-166">可在資料庫仍在線上運作以及正在使用中的時候進行備份。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-166">Backup can occur while the database is online and being used.</span></span> <span data-ttu-id="7e5e3-167">不過，會有下列限制：</span><span class="sxs-lookup"><span data-stu-id="7e5e3-167">However, the following restrictions exist.</span></span>  
  
### <a name="offline-data-cannot-be-backed-up"></a><span data-ttu-id="7e5e3-168">無法備份離線資料</span><span class="sxs-lookup"><span data-stu-id="7e5e3-168">Offline Data Cannot Be Backed Up</span></span>  
 <span data-ttu-id="7e5e3-169">隱含或明確參考離線資料的任何備份作業都會失敗。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-169">Any backup operation that implicitly or explicitly references data that is offline fails.</span></span> <span data-ttu-id="7e5e3-170">一些典型的例子如下：</span><span class="sxs-lookup"><span data-stu-id="7e5e3-170">Some typical examples include the following:</span></span>  
  
-   <span data-ttu-id="7e5e3-171">要求進行完整資料庫備份，但資料庫的一個檔案群組為離線狀態。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-171">You request a full database backup, but one filegroup of the database is offline.</span></span> <span data-ttu-id="7e5e3-172">因為所有檔案群組是明確納入在完整資料庫備份中，所以此作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-172">Because all filegroups are implicitly included in a full database backup, this operation fails.</span></span>  
  
     <span data-ttu-id="7e5e3-173">若要備份這個資料庫，您可以使用檔案備份，並且指定只限在線上的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-173">To back up this database, you can use a file backup and specify only the filegroups that are online.</span></span>  
  
-   <span data-ttu-id="7e5e3-174">您要求進行部分備份，但讀取/寫入檔案群組處於離線狀態。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-174">You request a partial backup, but a read/write filegroup is offline.</span></span> <span data-ttu-id="7e5e3-175">因為部分備份需要所有的讀取/寫入檔案群組，所以此作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-175">Because all read/write filegroups are required for a partial backup, the operation fails.</span></span>  
  
-   <span data-ttu-id="7e5e3-176">要求進行特定檔案的檔案備份，但其中一個檔案不在線上。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-176">You request a file backup of specific files, but one of the files is not online.</span></span> <span data-ttu-id="7e5e3-177">該作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-177">The operation fails.</span></span> <span data-ttu-id="7e5e3-178">若要備份線上檔案，您可以省略檔案清單中的離線檔案，然後重複該作業。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-178">To back up the online files, you can omit the offline file from the file list and repeat the operation.</span></span>  
  
 <span data-ttu-id="7e5e3-179">一般而言，即使有一個或多個資料檔案無法使用，記錄備份都會成功。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-179">Typically, a log backup succeeds even if one or more data files are unavailable.</span></span> <span data-ttu-id="7e5e3-180">不過，如果在大量記錄復原模式下變更任何包含大量記錄的檔案，則必須所有檔案都在線上，才能讓備份成功。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-180">However, if any file contains bulk-logged changes made under the bulk-logged recovery model, all the files must be online for the backup to succeed.</span></span>  
  
### <a name="concurrency-restrictions-during-backup"></a><span data-ttu-id="7e5e3-181">備份期間的並行限制</span><span class="sxs-lookup"><span data-stu-id="7e5e3-181">Concurrency Restrictions During Backup</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7e5e3-182">利用線上備份處理序，使您能夠在資料庫處於使用狀態時備份資料庫。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-182">uses an online backup process to allow for a database backup while the database is still being used.</span></span> <span data-ttu-id="7e5e3-183">在備份期間，您可以執行大部分的作業；例如，在備份作業期間，您可以執行 INSERT、UPDATE 或 DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-183">During a backup, most operations are possible; for example, INSERT, UPDATE, or DELETE statements are allowed during a backup operation.</span></span> <span data-ttu-id="7e5e3-184">不過，如果試圖在建立或刪除資料庫檔案過程中啟動備份作業，則備份作業會等候到建立或刪除作業完成，或備份逾時為止。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-184">However, if you try to start a backup operation while a database file is being created or deleted, the backup operation waits until the create or delete operation is finished or the backup times out.</span></span>  
  
 <span data-ttu-id="7e5e3-185">資料庫備份或交易記錄備份期間所無法執行的作業包括：</span><span class="sxs-lookup"><span data-stu-id="7e5e3-185">Operations that cannot run during a database backup or transaction log backup include the following:</span></span>  
  
-   <span data-ttu-id="7e5e3-186">檔案管理作業，例如，含有 ADD FILE 或 REMOVE FILE 選項的 ALTER DATABASE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-186">File-management operations such as the ALTER DATABASE statement with either the ADD FILE or REMOVE FILE options.</span></span>  
  
-   <span data-ttu-id="7e5e3-187">壓縮資料庫或壓縮檔案的作業。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-187">Shrink database or shrink file operations.</span></span> <span data-ttu-id="7e5e3-188">其中包括自動壓縮作業。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-188">This includes auto-shrink operations.</span></span>  
  
-   <span data-ttu-id="7e5e3-189">如果在備份作業進行當中試圖建立或刪除資料庫檔案，建立或刪除作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-189">If you try to create or delete a database file while a backup operation is in progress, the create or delete operation fails.</span></span>  
  
 <span data-ttu-id="7e5e3-190">如果備份作業與檔案管理或壓縮作業重疊，便會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-190">If a backup operation overlaps with a file-management operation or shrink operation, a conflict occurs.</span></span> <span data-ttu-id="7e5e3-191">不論哪一個衝突的作業先開始，第二項作業都會等候第一項作業設定的鎖定逾時(逾時期間由工作階段逾時設定控制)。如果在逾時期間解除鎖定，第二項作業就會繼續下去。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-191">Regardless of which of the conflicting operation began first, the second operation waits for the lock set by the first operation to time out. (The time-out period is controlled by a session time-out setting.) If the lock is released during the time-out period, the second operation continues.</span></span> <span data-ttu-id="7e5e3-192">如果鎖定逾時，第二項作業就會失敗。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-192">If the lock times out, the second operation fails.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7e5e3-193">相關工作</span><span class="sxs-lookup"><span data-stu-id="7e5e3-193">Related Tasks</span></span>  
 <span data-ttu-id="7e5e3-194">**若要使用備份裝置和備份媒體**</span><span class="sxs-lookup"><span data-stu-id="7e5e3-194">**To work with backup devices and backup media**</span></span>  
  
-   [<span data-ttu-id="7e5e3-195">定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-195">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-196">定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-196">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-197">指定磁碟或磁帶作為備份目的地 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-197">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-198">刪除備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-198">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-199">設定備份的到期日 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-199">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-200">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-200">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-201">檢視備份組中的資料和記錄檔 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-201">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-202">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-202">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-203">從裝置還原備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-203">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-204">教學課程：SQL Server 備份及還原至 Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="7e5e3-204">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
 <span data-ttu-id="7e5e3-205">**若要建立備份**</span><span class="sxs-lookup"><span data-stu-id="7e5e3-205">**To create a backup**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e5e3-206">如果是部分備份或只複製備份，就必須分別搭配 PARTIAL 或 COPY_ONLY 選項來使用 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7e5e3-206">For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL or COPY_ONLY option, respectively.</span></span>  
  
-   [<span data-ttu-id="7e5e3-207">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-207">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-208">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-208">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-209">備份檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-209">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-210">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-210">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-211">資料庫損毀時備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-211">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-212">在備份或還原期間啟用或停用備份總和檢查碼 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-212">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [<span data-ttu-id="7e5e3-213">指定在發生錯誤後備份或還原作業應該繼續還是停止 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-213">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
-   [<span data-ttu-id="7e5e3-214">使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-214">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="7e5e3-215">教學課程：SQL Server 備份及還原至 Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="7e5e3-215">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e5e3-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e5e3-216">See Also</span></span>  
 <span data-ttu-id="7e5e3-217">[SQL Server 資料庫的備份與還原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="7e5e3-217">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="7e5e3-218">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e5e3-218">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="7e5e3-219">[維護計畫](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="7e5e3-219">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 <span data-ttu-id="7e5e3-220">[交易記錄 &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e5e3-220">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="7e5e3-221">復原模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5e3-221">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
