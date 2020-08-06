---
title: SQL Server 資料庫的備份與還原 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], see restoring [SQL Server]
- backups [SQL Server]
- restoring databases [SQL Server]
- backup [SQL Server], see backing up [SQL Server]
- databases [SQL Server], restoring
- backing up databases [SQL Server]
- restore [SQL Server], see restoring [SQL Server]
- disaster recovery [SQL Server], see backing up [SQL Server]
- backing up [SQL Server]
- Database Engine [SQL Server], backups
- databases [SQL Server], backups
ms.assetid: 570a21b3-ad29-44a9-aa70-deb2fbd34f27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec2104219d98ed3cb97bfbb8993a3c28d45841c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606939"
---
# <a name="back-up-and-restore-of-sql-server-databases"></a><span data-ttu-id="0e44d-102">SQL Server 資料庫的備份與還原</span><span class="sxs-lookup"><span data-stu-id="0e44d-102">Back Up and Restore of SQL Server Databases</span></span>
  <span data-ttu-id="0e44d-103">此主題描述備份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的優點、基本備份和還原詞彙，並介紹 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的備份和還原策略，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份和還原的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="0e44d-103">This topic describes the benefits of backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, basic backup and restore terms, and introduces backup and restore strategies for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and security considerations for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore.</span></span>  
  
 <span data-ttu-id="0e44d-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的備份和還原元件提供基本的防護措施，可保護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中所儲存的重要資料。</span><span class="sxs-lookup"><span data-stu-id="0e44d-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore component provides an essential safeguard for protecting critical data stored in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="0e44d-105">若要將重大資料遺失的風險降至最低，您必須備份資料庫，以定期保存您對資料所做的修改。</span><span class="sxs-lookup"><span data-stu-id="0e44d-105">To minimize the risk of catastrophic data loss, you need to back up your databases to preserve modifications to your data on a regular basis.</span></span> <span data-ttu-id="0e44d-106">規劃完善的備份和還原策略有助於保護資料庫，以防止各種失敗所導致的資料遺失。</span><span class="sxs-lookup"><span data-stu-id="0e44d-106">A well-planned backup and restore strategy helps protect databases against data loss caused by a variety of failures.</span></span> <span data-ttu-id="0e44d-107">藉由還原一組備份並復原資料庫來測試您的策略，以做好有效因應災害的準備。</span><span class="sxs-lookup"><span data-stu-id="0e44d-107">Test your strategy by restoring a set of backups and then recovering your database to prepare you to respond effectively to a disaster.</span></span>  
  
 <span data-ttu-id="0e44d-108">除了儲存備份的本機儲存體之外，SQL Server 也支援備份至與還原自 Azure Blob 儲存體服務。</span><span class="sxs-lookup"><span data-stu-id="0e44d-108">In addition to local storage for storing the backups, SQL Server also supports backup to and restore from the Azure Blob Storage Service.</span></span> <span data-ttu-id="0e44d-109">如需詳細資訊，請參閱 [SQL Server 備份及還原與 Azure Blob 儲存體服務](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-109">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  

  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="0e44d-110">優點</span><span class="sxs-lookup"><span data-stu-id="0e44d-110">Benefits</span></span>  
  
-   <span data-ttu-id="0e44d-111">備份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫、針對備份執行測試還原程序，並將備份的複本儲存在安全的異地位置，即可避免可能發生的重大資料遺失。</span><span class="sxs-lookup"><span data-stu-id="0e44d-111">Backing up your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, running test restores procedures on your backups, and storing copies of backups in a safe, off-site location protects you from potentially catastrophic data loss.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0e44d-112">這是可靠地保護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="0e44d-112">This is the only way to reliably protect your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data.</span></span>  
  
     <span data-ttu-id="0e44d-113">使用有效的資料庫備份，就可以從多種失敗中復原資料，例如：</span><span class="sxs-lookup"><span data-stu-id="0e44d-113">With valid backups of a database, you can recover your data from many failures, such as:</span></span>  
  
    -   <span data-ttu-id="0e44d-114">媒體錯誤。</span><span class="sxs-lookup"><span data-stu-id="0e44d-114">Media failure.</span></span>  
  
    -   <span data-ttu-id="0e44d-115">使用者錯誤 (例如不小心卸除資料表)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-115">User errors, for example, dropping a table by mistake.</span></span>  
  
    -   <span data-ttu-id="0e44d-116">硬體故障 (例如，磁碟機損壞或伺服器永久損毀)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-116">Hardware failures, for example, a damaged disk drive or permanent loss of a server.</span></span>  
  
    -   <span data-ttu-id="0e44d-117">天然災害。</span><span class="sxs-lookup"><span data-stu-id="0e44d-117">Natural disasters.</span></span> <span data-ttu-id="0e44d-118">藉由對 Azure Blob 儲存體服務使用 SQL Server 備份，就可以在與內部部署位置不同的區域建立異地備份，以便在發生影響內部部署位置的天然災害事件時使用。</span><span class="sxs-lookup"><span data-stu-id="0e44d-118">By using SQL Server Backup to Azure Blob storage service, you can create an off-site backup in a different region than your on-premises location, to use in the event of a natural disaster affecting your on-premises location.</span></span>  
  
-   <span data-ttu-id="0e44d-119">此外，資料庫備份對於例行管理很有用，例如，將資料庫從一部伺服器複製到另一部伺服器、設定 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 或資料庫鏡像，以及封存。</span><span class="sxs-lookup"><span data-stu-id="0e44d-119">Additionally, backups of a database are useful for routine administrative purposes, such as copying a database from one server to another, setting up [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] or database mirroring, and archiving.</span></span>  
  

  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="0e44d-120">元件和概念</span><span class="sxs-lookup"><span data-stu-id="0e44d-120">Components and Concepts</span></span>  
 <span data-ttu-id="0e44d-121">備份 (back up) [動詞]</span><span class="sxs-lookup"><span data-stu-id="0e44d-121">back up [verb]</span></span>  
 <span data-ttu-id="0e44d-122">將資料或記錄檔記錄從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫或其交易記錄複製至備份裝置 (例如磁碟)，以建立資料備份或記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0e44d-122">Copies the data or log records from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.</span></span>  
  
 <span data-ttu-id="0e44d-123">備份 (backup) [名詞]</span><span class="sxs-lookup"><span data-stu-id="0e44d-123">backup [noun]</span></span>  
 <span data-ttu-id="0e44d-124">失敗後可用來還原和復原資料的資料複本。</span><span class="sxs-lookup"><span data-stu-id="0e44d-124">A copy of data that can be used to restore and recover the data after a failure.</span></span> <span data-ttu-id="0e44d-125">資料庫備份也可用來將資料庫的複本還原到新位置。</span><span class="sxs-lookup"><span data-stu-id="0e44d-125">Backups of a database can also be used to restore a copy the database to a new location.</span></span>  
  
 <span data-ttu-id="0e44d-126">備份裝置</span><span class="sxs-lookup"><span data-stu-id="0e44d-126">backup device</span></span>  
 <span data-ttu-id="0e44d-127">寫入 SQL Server 備份並從中進行還原的磁碟或磁帶裝置。</span><span class="sxs-lookup"><span data-stu-id="0e44d-127">A disk or tape device to which SQL Server backups are written and from which they can be restored.</span></span> <span data-ttu-id="0e44d-128">SQL Server 備份也可以寫入 Azure Blob 儲存體服務，而且會使用 **URL** 格式來指定備份檔案的目的地和名稱。</span><span class="sxs-lookup"><span data-stu-id="0e44d-128">SQL Server backups can also be written to an Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file..</span></span> <span data-ttu-id="0e44d-129">如需詳細資訊，請參閱 [SQL Server 備份及還原與 Azure Blob 儲存體服務](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-129">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="0e44d-130">備份媒體</span><span class="sxs-lookup"><span data-stu-id="0e44d-130">backup media</span></span>  
 <span data-ttu-id="0e44d-131">已寫入一個或多個備份的一個或多個磁帶或磁碟檔案。</span><span class="sxs-lookup"><span data-stu-id="0e44d-131">One or more tapes or disk files to which one or more backup have been written.</span></span>  
  
 <span data-ttu-id="0e44d-132">資料備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-132">data backup</span></span>  
 <span data-ttu-id="0e44d-133">整個資料庫 (資料庫備份)、部分資料庫 (部分備份) 或是一組資料檔案或檔案群組 (檔案備份) 中資料的備份。</span><span class="sxs-lookup"><span data-stu-id="0e44d-133">A backup of data in a complete database (a database backup), a partial database ( a partial backup), or a set of data files or filegroups (a file backup).</span></span>  
  
 <span data-ttu-id="0e44d-134">資料庫備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-134">database backup</span></span>  
 <span data-ttu-id="0e44d-135">資料庫的備份。</span><span class="sxs-lookup"><span data-stu-id="0e44d-135">A backup of a database.</span></span> <span data-ttu-id="0e44d-136">完整資料庫備份代表備份完成時的整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="0e44d-136">Full database backups represent the whole database at the time the backup finished.</span></span> <span data-ttu-id="0e44d-137">差異資料庫備份僅包含自其最近的完整資料庫備份以來，對資料庫所做的變更。</span><span class="sxs-lookup"><span data-stu-id="0e44d-137">Differential database backups contain only changes made to the database since its most recent full database backup.</span></span>  
  
 <span data-ttu-id="0e44d-138">差異備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-138">differential backup</span></span>  
 <span data-ttu-id="0e44d-139">一種資料備份，是以整個或部分資料庫或一組資料檔案或檔案群組 (差異基底) 的最新完整備份為基礎，而且只包含自該基底以來變更的資料。</span><span class="sxs-lookup"><span data-stu-id="0e44d-139">A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the differential base) and that contains only the data that has changed since that base.</span></span>  
  
 <span data-ttu-id="0e44d-140">完整備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-140">full backup</span></span>  
 <span data-ttu-id="0e44d-141">一種資料備份，包含特定資料庫或一組檔案群組或檔案中的所有資料，也包含足以讓這個資料復原的記錄。</span><span class="sxs-lookup"><span data-stu-id="0e44d-141">A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.</span></span>  
  
 <span data-ttu-id="0e44d-142">記錄備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-142">log backup</span></span>  
 <span data-ttu-id="0e44d-143">交易記錄的備份，包含先前的記錄備份中未備份的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="0e44d-143">A backup of transaction logs that includes all log records that were not backed up in a previous log backup.</span></span> <span data-ttu-id="0e44d-144">(完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="0e44d-144">(full recovery model)</span></span>  
  
 <span data-ttu-id="0e44d-145">recover</span><span class="sxs-lookup"><span data-stu-id="0e44d-145">recover</span></span>  
 <span data-ttu-id="0e44d-146">將資料庫回復為穩定且一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="0e44d-146">To return a database to a stable and consistent state.</span></span>  
  
 <span data-ttu-id="0e44d-147">recovery</span><span class="sxs-lookup"><span data-stu-id="0e44d-147">recovery</span></span>  
 <span data-ttu-id="0e44d-148">讓資料庫進入交易一致狀態的資料庫啟動階段或含復原之還原的階段。</span><span class="sxs-lookup"><span data-stu-id="0e44d-148">A phase of database startup or of a restore with recovery that brings the database into a transaction-consistent state.</span></span>  
  
 <span data-ttu-id="0e44d-149">復原模式</span><span class="sxs-lookup"><span data-stu-id="0e44d-149">recovery model</span></span>  
 <span data-ttu-id="0e44d-150">控制資料庫上交易記錄維護的資料庫屬性。</span><span class="sxs-lookup"><span data-stu-id="0e44d-150">A database property that controls transaction log maintenance on a database.</span></span> <span data-ttu-id="0e44d-151">復原模式共有三種：簡單、完整和大量記錄。</span><span class="sxs-lookup"><span data-stu-id="0e44d-151">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="0e44d-152">資料庫的復原模式決定其備份和還原需求。</span><span class="sxs-lookup"><span data-stu-id="0e44d-152">The recovery model of database determines its backup and restore requirements.</span></span>  
  
 <span data-ttu-id="0e44d-153">還原</span><span class="sxs-lookup"><span data-stu-id="0e44d-153">restore</span></span>  
 <span data-ttu-id="0e44d-154">一個多階段的程序，它會將指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份中的所有資料和記錄頁面複製到指定的資料庫中，然後藉由套用所記錄的變更取得前面時段的資料，向前復原備份中記錄的所有交易。</span><span class="sxs-lookup"><span data-stu-id="0e44d-154">A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.</span></span>  
  

  
##  <a name="introduction-to-backup-and-restore-strategies"></a><a name="BnrStrategies"></a><span data-ttu-id="0e44d-155">備份與還原策略簡介</span><span class="sxs-lookup"><span data-stu-id="0e44d-155">Introduction to Backup and Restore Strategies</span></span>  
 <span data-ttu-id="0e44d-156">備份和還原資料作業必須依特定環境自訂，而且也必須使用可用的資源。</span><span class="sxs-lookup"><span data-stu-id="0e44d-156">Backing up and restoring data must be customized to a particular environment and must work with the available resources.</span></span> <span data-ttu-id="0e44d-157">因此，為了可靠地使用備份和還原作業進行復原，您需要擬定備份和還原策略。</span><span class="sxs-lookup"><span data-stu-id="0e44d-157">Therefore, a reliable use of backup and restore for recovery requires a backup and restore strategy.</span></span> <span data-ttu-id="0e44d-158">設計良好的備份和還原策略可充分提高資料可用性，並使資料損失降至最少，同時考慮到您的特定業務需求。</span><span class="sxs-lookup"><span data-stu-id="0e44d-158">A well-designed backup and restore strategy maximizes data availability and minimizes data loss, while considering your particular business requirements.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0e44d-159">請將資料庫和備份放置於不同的裝置上。</span><span class="sxs-lookup"><span data-stu-id="0e44d-159">Place the database and backups on separate devices.</span></span> <span data-ttu-id="0e44d-160">否則，如果包含資料庫的裝置故障，備份將無法使用。</span><span class="sxs-lookup"><span data-stu-id="0e44d-160">Otherwise, if the device containing the database fails, your backups will be unavailable.</span></span> <span data-ttu-id="0e44d-161">將資料和備份放置於不同的裝置也可以針對寫入備份和資料庫生產使用強化 I/O 效能。</span><span class="sxs-lookup"><span data-stu-id="0e44d-161">Placing the data and backups on separate devices also enhances the I/O performance for both writing backups and the production use of the database.</span></span>  
  
 <span data-ttu-id="0e44d-162">備份和還原策略包含備份部分與還原部分。</span><span class="sxs-lookup"><span data-stu-id="0e44d-162">A backup and restore strategy contains a backup portion and a restore portion.</span></span> <span data-ttu-id="0e44d-163">策略的備份部分定義備份的類型和頻率、所需硬體的本質和速度、測試備份的方法，以及儲存備份媒體的位置與方法 (包括安全性考量)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-163">The backup part of the strategy defines the type and frequency of backups, the nature and speed of the hardware that is required for them, how backups are to be tested, and where and how backup media is to be stored (including security considerations).</span></span> <span data-ttu-id="0e44d-164">策略的還原部分定義誰負責執行還原，以及應該如何執行還原，以達到資料庫可用性並將資料損失降到最低的目標。</span><span class="sxs-lookup"><span data-stu-id="0e44d-164">The restore part of the strategy defines who is responsible for performing restores and how restores should be performed to meet your goals for availability of the database and for minimizing data loss.</span></span> <span data-ttu-id="0e44d-165">建議您寫下備份和還原程序，並將文件的副本保留在執行書中。</span><span class="sxs-lookup"><span data-stu-id="0e44d-165">We recommend that you document your backup and restore procedures and keep a copy of the documentation in your run book.</span></span>  
  
 <span data-ttu-id="0e44d-166">設計有效的備份和還原策略需要仔細計畫、實作及測試。</span><span class="sxs-lookup"><span data-stu-id="0e44d-166">Designing an effective backup and restore strategy requires careful planning, implementation, and testing.</span></span> <span data-ttu-id="0e44d-167">測試是必要的。</span><span class="sxs-lookup"><span data-stu-id="0e44d-167">Testing is required.</span></span> <span data-ttu-id="0e44d-168">在利用還原策略中包含的所有備份組合順利完成還原之前，您還稱不上有備份策略。</span><span class="sxs-lookup"><span data-stu-id="0e44d-168">You do not have a backup strategy until you have successfully restored backups in all the combinations that are included in your restore strategy.</span></span> <span data-ttu-id="0e44d-169">您必須考慮各種因素。</span><span class="sxs-lookup"><span data-stu-id="0e44d-169">You must consider a variety of factors.</span></span> <span data-ttu-id="0e44d-170">這些選項包括：</span><span class="sxs-lookup"><span data-stu-id="0e44d-170">These include the following:</span></span>  
  
-   <span data-ttu-id="0e44d-171">您的組織對於資料庫的生產目標，特別是對資料可用性以及保護資料免於遺失的需求。</span><span class="sxs-lookup"><span data-stu-id="0e44d-171">The production goals of your organization for the databases, especially the requirements for availability and protection of data from loss.</span></span>  
  
-   <span data-ttu-id="0e44d-172">您的每一個資料庫的本質：其大小、使用模式、內容本質及資料需求等等。</span><span class="sxs-lookup"><span data-stu-id="0e44d-172">The nature of each of your databases: its size, its usage patterns, the nature of its content, the requirements for its data, and so on.</span></span>  
  
-   <span data-ttu-id="0e44d-173">相關資源的限制，例如：硬體、人員、儲存備份媒體的空間、儲存媒體的實體安全性等等。</span><span class="sxs-lookup"><span data-stu-id="0e44d-173">Constraints on resources, such as: hardware, personnel, space for storing backup media, the physical security of the stored media, and so on.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0e44d-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁碟儲存格式在 64 位元與 32 位元環境下都相同。</span><span class="sxs-lookup"><span data-stu-id="0e44d-174">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="0e44d-175">因此，備份與還原可在 32 位元和 64 位元環境中運作。</span><span class="sxs-lookup"><span data-stu-id="0e44d-175">Therefore, backup and restore work across 32-bit and 64-bit environments.</span></span> <span data-ttu-id="0e44d-176">在其中一種環境中執行之伺服器執行個體上建立的備份可還原至另一種環境中執行的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0e44d-176">A backup created on a server instance running in one environment can be restored on a server instance that runs in the other environment.</span></span>  
  

  
### <a name="impact-of-the-recovery-model-on-backup-and-restore"></a><span data-ttu-id="0e44d-177">復原模式對備份和還原的影響</span><span class="sxs-lookup"><span data-stu-id="0e44d-177">Impact of the Recovery Model on Backup and Restore</span></span>  
 <span data-ttu-id="0e44d-178">備份和還原作業是在復原模式的內容中發生。</span><span class="sxs-lookup"><span data-stu-id="0e44d-178">Backup and restore operations occur within the context of a recovery model.</span></span> <span data-ttu-id="0e44d-179">復原模式是控制交易記錄管理方式的資料庫屬性。</span><span class="sxs-lookup"><span data-stu-id="0e44d-179">A recovery model is a database property that controls how the transaction log is managed.</span></span> <span data-ttu-id="0e44d-180">此外，資料庫的復原模式也將決定資料庫所支援的備份類型與還原實例。</span><span class="sxs-lookup"><span data-stu-id="0e44d-180">Also, the recovery model of a database determines what types of backups and what restore scenarios are supported for the database.</span></span> <span data-ttu-id="0e44d-181">一般而言，資料庫會使用完整復原模式或簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="0e44d-181">Typically a database uses either the simple recovery model or the full recovery model.</span></span> <span data-ttu-id="0e44d-182">完整復原模式可以藉由在大量作業之前切換到大量記錄復原模式，補充其功能。</span><span class="sxs-lookup"><span data-stu-id="0e44d-182">The full recovery model can be supplemented by switching to the bulk-logged recovery model before bulk operations.</span></span> <span data-ttu-id="0e44d-183">如需這些復原模式及其對交易記錄管理之影響的簡介，請參閱[交易記錄 &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-183">For an introduction to these recovery models and how they affect transaction log management, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="0e44d-184">資料庫復原模式的最佳選擇視您的商務需求而定。</span><span class="sxs-lookup"><span data-stu-id="0e44d-184">The best choice of recovery model for the database depends on your business requirements.</span></span> <span data-ttu-id="0e44d-185">若要避免管理交易記錄，並簡化備份和還原，請使用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="0e44d-185">To avoid transaction log management and simplify backup and restore, use the simple recovery model.</span></span> <span data-ttu-id="0e44d-186">若要將遺失工作的風險降到最低 (但會耗用管理負擔成本)，請使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="0e44d-186">To minimize work-loss exposure, at the cost of administrative overhead, use the full recovery model.</span></span> <span data-ttu-id="0e44d-187">如需復原模式對備份與還原之影響的資訊，請參閱 [備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-187">For information about the effect of recovery models on backup and restore, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
### <a name="design-the-backup-strategy"></a><span data-ttu-id="0e44d-188">設計備份策略</span><span class="sxs-lookup"><span data-stu-id="0e44d-188">Design the Backup Strategy</span></span>  
 <span data-ttu-id="0e44d-189">在為特定資料庫選擇符合商務需求的復原模式之後，您必須規劃並實作對應的備份策略。</span><span class="sxs-lookup"><span data-stu-id="0e44d-189">After you have selected a recovery model that meets your business requirements for a specific database, you have to plan and implement a corresponding backup strategy.</span></span> <span data-ttu-id="0e44d-190">最佳備份策略取決於各種因素，其中特別重要的是下列項目：</span><span class="sxs-lookup"><span data-stu-id="0e44d-190">The optimal backup strategy depends on a variety of factors, of which the following are especially significant:</span></span>  
  
-   <span data-ttu-id="0e44d-191">應用程式每天必須花多少時間來存取資料庫？</span><span class="sxs-lookup"><span data-stu-id="0e44d-191">How many hours a day do applications have to access the database?</span></span>  
  
     <span data-ttu-id="0e44d-192">如果可預測離峰期間，則建議您排定該期間內完整資料庫備份的作業時程。</span><span class="sxs-lookup"><span data-stu-id="0e44d-192">If there is a predictable off-peak period, we recommend that you schedule full database backups for that period.</span></span>  
  
-   <span data-ttu-id="0e44d-193">可能發生變更和更新的頻率為何？</span><span class="sxs-lookup"><span data-stu-id="0e44d-193">How frequently are changes and updates likely to occur?</span></span>  
  
     <span data-ttu-id="0e44d-194">如果經常變更，請考慮下列作法：</span><span class="sxs-lookup"><span data-stu-id="0e44d-194">If changes are frequent, consider the following:</span></span>  
  
    -   <span data-ttu-id="0e44d-195">在簡單復原模式下，請考慮在完整資料庫備份之間排程差異備份。</span><span class="sxs-lookup"><span data-stu-id="0e44d-195">Under the simple recovery model, consider scheduling differential backups between full database backups.</span></span> <span data-ttu-id="0e44d-196">差異備份只會擷取最後一次完整資料庫備份之後所發生的變更。</span><span class="sxs-lookup"><span data-stu-id="0e44d-196">A differential backup captures only the changes since the last full database backup.</span></span>  
  
    -   <span data-ttu-id="0e44d-197">在完整復原模式下，您應排程經常的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0e44d-197">Under the full recovery model, you should schedule frequent log backups.</span></span> <span data-ttu-id="0e44d-198">在完整備份之間排定差異備份，可減少您在還原資料後必須還原的記錄備份數目，從而減少還原時間。</span><span class="sxs-lookup"><span data-stu-id="0e44d-198">Scheduling differential backups between full backups can reduce restore time by reducing the number of log backups you have to restore after restoring the data.</span></span>  
  
-   <span data-ttu-id="0e44d-199">變更可能會發生在資料庫的一小部分，還是資料庫的大部分？</span><span class="sxs-lookup"><span data-stu-id="0e44d-199">Are changes likely to occur in only a small part of the database or in a large part of the database?</span></span>  
  
     <span data-ttu-id="0e44d-200">如果是大型資料庫，且其變更集中於檔案或檔案群組部分，則部分備份及 (或) 檔案備份可能十分有用。</span><span class="sxs-lookup"><span data-stu-id="0e44d-200">For a large database in which changes are concentrated in a part of the files or filegroups, partial backups and or file backups can be useful.</span></span> <span data-ttu-id="0e44d-201">如需詳細資訊，請參閱[部分備份 &#40;SQL Server&#41;](partial-backups-sql-server.md) 和[完整檔案備份 &#40;SQL Server&#41;](full-file-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-201">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md) and [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="0e44d-202">完整資料庫備份需要多少磁碟空間？</span><span class="sxs-lookup"><span data-stu-id="0e44d-202">How much disk space will a full database backup require?</span></span>  
  
     <span data-ttu-id="0e44d-203">如需詳細資訊，請參閱本節後面的[估計完整資料庫備份的大小](#EstimateDbBuSize)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-203">For more information, see [Estimating the Size of a Full Database Backup](#EstimateDbBuSize), later in this section.</span></span>  
  
####  <a name="estimate-the-size-of-a-full-database-backup"></a><a name="EstimateDbBuSize"></a><span data-ttu-id="0e44d-204">估計完整資料庫備份的大小</span><span class="sxs-lookup"><span data-stu-id="0e44d-204">Estimate the Size of a Full Database Backup</span></span>  
 <span data-ttu-id="0e44d-205">在實作備份和還原策略前，您必須估計完整資料庫備份將使用多少磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="0e44d-205">Before you implement a backup and restore strategy, you should estimate how much disk space a full database backup will use.</span></span> <span data-ttu-id="0e44d-206">備份作業會將資料庫中的資料複製到備份檔中。</span><span class="sxs-lookup"><span data-stu-id="0e44d-206">The backup operation copies the data in the database to the backup file.</span></span> <span data-ttu-id="0e44d-207">備份僅包含資料庫中的實際資料，而不包含任何未使用的空間。</span><span class="sxs-lookup"><span data-stu-id="0e44d-207">The backup contains only the actual data in the database and not any unused space.</span></span> <span data-ttu-id="0e44d-208">因此，備份通常會比資料庫本身還小。</span><span class="sxs-lookup"><span data-stu-id="0e44d-208">Therefore, the backup is usually smaller than the database itself.</span></span> <span data-ttu-id="0e44d-209">您可以使用 **sp_spaceused** 系統預存程序來估計完整資料庫備份的大小。</span><span class="sxs-lookup"><span data-stu-id="0e44d-209">You can estimate the size of a full database backup by using the **sp_spaceused** system stored procedure.</span></span> <span data-ttu-id="0e44d-210">如需詳細資訊，請參閱 [sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-210">For more information, see [sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql).</span></span>  
  
### <a name="schedule-backups"></a><span data-ttu-id="0e44d-211">排程備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-211">Schedule Backups</span></span>  
 <span data-ttu-id="0e44d-212">執行備份作業對進行中的交易影響最小，所以可以在一般作業過程中執行備份作業。</span><span class="sxs-lookup"><span data-stu-id="0e44d-212">Performing a backup operation has minimal effect on transactions that are running; therefore, backup operations can be run during regular operations.</span></span> <span data-ttu-id="0e44d-213">您可以執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份，並且將實際執行工作負載受到的影響降至最低。</span><span class="sxs-lookup"><span data-stu-id="0e44d-213">You can perform a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup with minimal effect on production workloads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e44d-214">如需備份期間之並行限制的資訊，請參閱 [備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0e44d-214">For information about concurrency restrictions during backup, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
 <span data-ttu-id="0e44d-215">決定您需要的備份類型以及執行每一類型所需的頻率之後，建議您將一般備份排程為資料庫之資料庫維護計畫的一部分。</span><span class="sxs-lookup"><span data-stu-id="0e44d-215">After you decide what types of backups you require and how frequently you have to perform each type, we recommend that you schedule regular backups as part of a database maintenance plan for the database.</span></span> <span data-ttu-id="0e44d-216">如需有關維護計畫以及如何為資料庫備份和記錄備份建立這些計畫的詳細資訊，請參閱＜ [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0e44d-216">For information about maintenance plans and how to create them for database backups and log backups, see [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
### <a name="test-your-backups"></a><span data-ttu-id="0e44d-217">測試備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-217">Test Your Backups</span></span>  
 <span data-ttu-id="0e44d-218">在您完成備份的測試之前，還不能算是具備還原策略。</span><span class="sxs-lookup"><span data-stu-id="0e44d-218">You do not have a restore strategy until you have tested your backups.</span></span> <span data-ttu-id="0e44d-219">您務必要將資料庫副本還原到測試系統，以針對每個資料庫完整測試備份策略。</span><span class="sxs-lookup"><span data-stu-id="0e44d-219">It is very important to thoroughly test your backup strategy for each of your databases by restoring a copy of the database onto a test system.</span></span> <span data-ttu-id="0e44d-220">您必須測試還原您要使用的每個備份類型。</span><span class="sxs-lookup"><span data-stu-id="0e44d-220">You must test restoring every type of backup that you intend to use.</span></span>  
  
 <span data-ttu-id="0e44d-221">建議您維護每個資料庫的作業手冊。</span><span class="sxs-lookup"><span data-stu-id="0e44d-221">We recommend that you maintain an operations manual for each database.</span></span> <span data-ttu-id="0e44d-222">這份作業手冊應記載備份位置、備份裝置名稱 (如果有的話)，以及還原測試備份所需的時間量。</span><span class="sxs-lookup"><span data-stu-id="0e44d-222">This operations manual should document the location of the backups, backup device names (if any), and the amount of time that is required to restore the test backups.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0e44d-223">相關工作</span><span class="sxs-lookup"><span data-stu-id="0e44d-223">Related Tasks</span></span>  
  
### <a name="scheduling-backup-jobs"></a><span data-ttu-id="0e44d-224">排程備份作業</span><span class="sxs-lookup"><span data-stu-id="0e44d-224">Scheduling Backup Jobs</span></span>  
  
-   [<span data-ttu-id="0e44d-225">建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="0e44d-225">Create a Maintenance Plan</span></span>](../maintenance-plans/create-a-maintenance-plan.md)  
  
-   [<span data-ttu-id="0e44d-226">建立作業</span><span class="sxs-lookup"><span data-stu-id="0e44d-226">Create a Job</span></span>](../../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="0e44d-227">排程作業</span><span class="sxs-lookup"><span data-stu-id="0e44d-227">Schedule a Job</span></span>](../../ssms/agent/schedule-a-job.md)  
  
### <a name="working-with-backup-devices-and-backup-media"></a><span data-ttu-id="0e44d-228">使用備份裝置和備份媒體</span><span class="sxs-lookup"><span data-stu-id="0e44d-228">Working with Backup Devices and Backup Media</span></span>  
  
-   [<span data-ttu-id="0e44d-229">定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-229">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-230">定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-230">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-231">指定磁碟或磁帶作為備份目的地 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-231">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-232">刪除備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-232">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-233">設定備份的到期日 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-233">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-234">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-234">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-235">檢視備份組中的資料和記錄檔 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-235">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-236">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-236">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-237">從裝置還原備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-237">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
### <a name="creating-backups"></a><span data-ttu-id="0e44d-238">建立備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-238">Creating Backups</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e44d-239">如果是部分備份或只複製備份，就必須分別搭配 PARTIAL 或 COPY_ONLY 選項來使用 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0e44d-239">For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL or COPY_ONLY option, respectively.</span></span>  
  
 <span data-ttu-id="0e44d-240">**使用 SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="0e44d-240">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="0e44d-241">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-241">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-242">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-242">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-243">備份檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-243">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-244">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-244">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="0e44d-245">**使用 Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="0e44d-245">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="0e44d-246">使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-246">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="0e44d-247">資料庫損毀時備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-247">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-248">在備份或還原期間啟用或停用備份總和檢查碼 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-248">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-249">指定在發生錯誤後備份或還原作業應該繼續還是停止 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-249">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  

  
### <a name="restoring-data-backups"></a><span data-ttu-id="0e44d-250">還原資料備份</span><span class="sxs-lookup"><span data-stu-id="0e44d-250">Restoring Data Backups</span></span>  
 <span data-ttu-id="0e44d-251">**使用 SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="0e44d-251">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="0e44d-252">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-252">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="0e44d-253">將資料庫還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-253">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-254">還原差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-254">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-255">還原檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-255">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
 <span data-ttu-id="0e44d-256">**使用 Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="0e44d-256">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="0e44d-257">在簡單復原模式下還原資料庫備份 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-257">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="0e44d-258">在完整復原模式下將資料庫還原至失敗點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-258">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="0e44d-259">以覆蓋現有檔案的方式還原檔案與檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-259">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-260">將檔案還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-260">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-261">還原 master 資料庫 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-261">Restore the master Database &#40;Transact-SQL&#41;</span></span>](restore-the-master-database-transact-sql.md)  
  

  
### <a name="restoring-transaction-logs-full-recovery-model"></a><span data-ttu-id="0e44d-262">還原交易記錄 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="0e44d-262">Restoring Transaction Logs (Full Recovery Model)</span></span>  
 <span data-ttu-id="0e44d-263">**使用 SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="0e44d-263">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="0e44d-264">還原資料庫至標示的交易 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-264">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="0e44d-265">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-265">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="0e44d-266">將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-266">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
 <span data-ttu-id="0e44d-267">**使用 Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="0e44d-267">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="0e44d-268">將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-268">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  

  
### <a name="additional-restore-tasks"></a><span data-ttu-id="0e44d-269">其他還原工作</span><span class="sxs-lookup"><span data-stu-id="0e44d-269">Additional Restore Tasks</span></span>  
 <span data-ttu-id="0e44d-270">**使用 Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="0e44d-270">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="0e44d-271">重新啟動中斷的還原作業 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-271">Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;</span></span>](restart-an-interrupted-restore-operation-transact-sql.md)  
  
-   [<span data-ttu-id="0e44d-272">在不還原資料的情況下復原資料庫 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-272">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="0e44d-273">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e44d-273">See Also</span></span>  
 <span data-ttu-id="0e44d-274">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e44d-274">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="0e44d-275">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e44d-275">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="0e44d-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e44d-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0e44d-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e44d-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="0e44d-278">[備份與還原 Analysis Services 資料庫](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) </span><span class="sxs-lookup"><span data-stu-id="0e44d-278">[Backup and Restore of Analysis Services Databases](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) </span></span>  
 <span data-ttu-id="0e44d-279">[備份並還原全文檢索目錄與索引。](../search/back-up-and-restore-full-text-catalogs-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="0e44d-279">[Back Up and Restore Full-Text Catalogs and Indexes](../search/back-up-and-restore-full-text-catalogs-and-indexes.md) </span></span>  
 <span data-ttu-id="0e44d-280">[備份及還原複寫的資料庫](../replication/administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="0e44d-280">[Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md) </span></span>  
 <span data-ttu-id="0e44d-281">[交易記錄 &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e44d-281">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="0e44d-282">[復原模式 &#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e44d-282">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 [<span data-ttu-id="0e44d-283">媒體集、媒體家族與備份組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e44d-283">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
